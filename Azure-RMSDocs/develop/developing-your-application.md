---
title: "Az alkalmazás fejlesztése | Azure RMS"
description: "Az RMS SDK 2.1 készlettel történő alkalmazásfejlesztés útmutatója"
keywords: 
author: bruceperlerms
manager: mbaldwin
ms.date: 07/06/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 396A2C19-3A00-4E9A-9088-198A48B15289
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 79397c82d9478cbd55630a376fe2d12f3873ebc4
ms.openlocfilehash: e00af9b9b0a5f2d917ac96812e980505d4cfd347


---

# Az alkalmazás fejlesztése

Ez a témakör alapvető útmutatással szolgál az RMS-kompatibilis alkalmazások legfontosabb aspektusairól. Erre építkezve elkezdheti saját alkalmazásának fejlesztését.

## Bevezetés

A témakörben foglaltak az IPCHelloWorld mintaalkalmazáson alapulnak. Ez segít kiigazodni a tartalomvédelemmel kompatibilis alkalmazások alapvető fogalmai és kódrészletei között. A teljes IPCHellowWorld mintaalkalmazást letöltheti a Microsoft Connect webhelyről, a [Webinar_Collateral.zip](https://connect.microsoft.com/site1170/Downloads/DownloadDetails.aspx?DownloadID=42440) fájlban.

> [!Note] 
> Az IPCHelloWorld-projekt már konfigurálva van a Rights Management Services SDK 2.1 szolgáltatáshoz. További információért új projektek konfigurálásáról az RMS SDK 2.1 használatához tekintse meg a [Configure Visual Studio](how-to-configure-a-visual-studio-project-to-use-the-ad-rms-sdk-2-0.md) (A Visual Studio konfigurálása) című témakört.

## Az MSIPC.dll betöltése

Az RMS SDK 2.1 függvényeinek meghívása előtt a MSIPC.dll betöltéséhez először meg kell hívnia az [IpcInitialize](/rights-management/sdk/2.1/api/win/functions#msipc_ipcinitialize) függvényt.

        C++
        hr = IpcInitialize();
        if (FAILED(hr)) {
          wprintf(L"Failed to initialize MSIPC. Are you sure the runtime is installed?\n");
          goto exit;
        }

## Sablonok számbavétele

Az RMS-sablonok meghatározzák az adatvédelmi házirendet, például meghatározzák, hogy mely felhasználók férhetnek hozzá az adatokhoz és a jogosultságaikhoz. Az RMS-sablonok az RMS-kiszolgálóra vannak telepítve.

Az alábbi kódrészlet számba veszi az alapértelmezett RMS-kiszolgálóról elérhető RMS-sablonokat.

      C++
      hr = IpcGetTemplateList(NULL, 0, 0, NULL, NULL, &pcTil);

      if (FAILED(hr)) {
        DisplayError(L"IpcGetTemplateList failed", hr);
        goto exit;
      }

A hívás lekéri az alapértelmezett kiszolgálón telepített RMS-sablonokat, és betölti az eredményeket a *pcTil* változó által mutatott [IPC_TIL](/rights-management/sdk/2.1/api/win/ipc_til#msipc_ipc_til) szerkezetbe, majd megjeleníti a sablonokat.

      C++
      if (0 == pcTil->cTi) {
        wprintf(L"*** No templates configured for your RMS server ***\n\n");
        wprintf(L"\\------------------------------------------------------\n\n");
        goto exit;
      }

      for (DWORD dw = 0; dw < pcTil->cTi; dw++) {
        wprintf(L"Template #%d:\n", dw);
        wprintf(L"    Name:         %s\n", pcTil->aTi[dw].wszName);
        wprintf(L"    Description:  %s\n", pcTil->aTi[dw].wszDescription);
        wprintf(L"    Issued by:    %s\n", pcTil->aTi[dw].wszIssuerDisplayName);
        wprintf(L"\n");
      }

## Licenc szerializálása

Az adatok védelmének biztosítása előtt szerializálnia kell a licencet, és le kell kérnie egy tartalomkulcsot. A tartalomkulcs segítségével titkosíthatja a bizalmas adatokat. A szerializált licenc általában a titkosított adatokhoz van csatolva, és a védett adatok fogyasztója használja. A fogyasztónak a szerializált licenc segítségével meg kell hívnia az [IpcGetKey](/rights-management/sdk/2.1/api/win/functions#msipc_ipcgetkey) függvényt a tartalomkulcs lekéréséhez, hogy visszafejthesse a tartalmat, és lekérhesse a tartalomra vonatkozó házirendet.

Az egyszerűség kedvéért használja az [IpcGetTemplateList](/rights-management/sdk/2.1/api/win/functions#msipc_ipcgettemplatelist) által visszaküldött első RMS-sablont a licenc szerializálásához.

Ahhoz, hogy a felhasználó kiválaszthassa a kívánt sablont, általában egy felhasználói felületi párbeszédpanelt kellene használnia.

      C++
      hr = IpcSerializeLicense((LPCVOID)pcTil->aTi[0].wszID, IPC_SL_TEMPLATE_ID,
        0, NULL, &hContentKey, &pSerializedLicense);

      if (FAILED(hr)) {
        DisplayError(L"IpcSerializeLicense failed", hr);
        goto exit;
      }

Miután ezt elvégezte, a rendelkezésére áll a tartalomkulcs (*hContentKey*) és a szerializált licenc (*pSerializedLicense*), amelyet a védett adatokhoz kell csatolnia.


## Protecting data (Az adatok védelme)

Most már készen áll arra, hogy titkosítsa a bizalmas adatokat az [IpcEncrypt](/rights-management/sdk/2.1/api/win/functions#msipc_ipcencrypt) függvény segítségével. Először derítse ki az **IpcEncrypt** függvény segítségével, hogy mekkora lesz a titkosított adatok mérete.

      C++
      cbText = (DWORD)(sizeof(WCHAR)*(wcslen(wszText)+1));
      hr = IpcEncrypt(hContentKey, 0, TRUE, (PBYTE)wszText, cbText,
        NULL, 0, &cbEncrypted);

      if (FAILED(hr)) {
        DisplayError(L"IpcEncrypt failed", hr);
        goto exit;
      }

Itt a wszText tartalmazza a megvédeni kívánt egyszerű szöveget. Az [IpcEncrypt](/rights-management/sdk/2.1/api/win/functions#msipc_ipcencrypt) függvény visszaküldi a titkosított adatok méretét a *cbEncrypted* paraméterben.

Most lefoglalhatja a memóriát a titkosított adatokhoz.

      C++
      pbEncrypted = (PBYTE)LocalAlloc(LPTR, cbEncrypted);

      if (NULL == pbEncrypted) {
        wprintf(L"Out of memory\n");
        goto exit;
      }

Végezetül elvégezheti magát a titkosítást.

      C++
      hr = IpcEncrypt(hContentKey, 0, TRUE, (PBYTE)wszText, cbText,
        pbEncrypted, cbEncrypted, &cbEncrypted);

      if (FAILED(hr)) {
        DisplayError(L"IpcEncrypt failed", hr);
        goto exit;
      }

Miután ezt a lépést elvégezte, rendelkezésére állnak a titkosított adatok (*pbEncrypted*) és a szerializált licenc (*pSerializedLicense*), amelyet a fogyasztó használ az adatok visszafejtéséhez.

## Hibakezelés

A mintaalkalmazásban a hibaelhárítás a *DisplayError* függvény használatával történik.

      C++
      void DisplayError(LPCWSTR wszErrorInfo, HRESULT hrError)
      {
        LPCWSTR wszErrorMessageText = NULL;

        if (SUCCEEDED(IpcGetErrorMessageText(hrError, 0, &wszErrorMessageText))) {
          wprintf(L"%s: 0x%08X (%s)\n", wszErrorInfo, hrError, wszErrorMessageText);
        }
        else {
          wprintf(L"%s: 0x%08X\n", wszErrorInfo, hrError);
        }
      }

A *DisplayError* függvény az [IpcGetErrorMessageText](/rights-management/sdk/2.1/api/win/functions#msipc_ipcgeterrormessagetext) függvény használatával kéri le a hibaüzenetet a megfelelő hibakódból, majd kiírja a normál a kimenetbe.

## Tisztítás

A befejezés előtt fel kell szabadítania a lefoglalt erőforrásokat.

      C++
      if (NULL != pbEncrypted) {
        LocalFree((HLOCAL)pbEncrypted);
      }

      if (NULL != pSerializedLicense) {
        IpcFreeMemory((LPVOID)pSerializedLicense);
      }

      if (NULL != hContentKey) {
        IpcCloseHandle((IPC_HANDLE)hContentKey);
      }

      if (NULL != pcTil) {
        IpcFreeMemory((LPVOID)pcTil);
      }

## Kapcsolódó témakörök

- [Fejlesztői útmutató és információk](developer-notes.md)
- [IpcEncrypt](/rights-management/sdk/2.1/api/win/functions#msipc_ipcencrypt)
- [IpcGetErrorMessageText](/rights-management/sdk/2.1/api/win/functions#msipc_ipcgeterrormessagetext)
- [IpcGetKey](/rights-management/sdk/2.1/api/win/functions#msipc_ipcgetkey)
- [IpcGetTemplateList](/rights-management/sdk/2.1/api/win/functions#msipc_ipcgettemplatelist)
- [IpcInitialize](/rights-management/sdk/2.1/api/win/functions#msipc_ipcinitialize)
- [IPC_TIL](/rights-management/sdk/2.1/api/win/ipc_til#msipc_ipc_til)
- [Webinar_Collateral.zip](https://connect.microsoft.com/site1170/Downloads/DownloadDetails.aspx?DownloadID=42440)



<!--HONumber=Jul16_HO4-->


