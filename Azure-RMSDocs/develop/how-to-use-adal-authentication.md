---
title: "ADAL-hitelesítés RMS-kompatiblis alkalmazásokhoz | Azure RMS"
description: "Az ADAL hitelesítési folyamatának ismertetése"
keywords: "hitelesítés, RMS, ADAL"
author: bruceperlerms
manager: mbaldwin
ms.date: 06/28/2016
ms.topic: article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: f89f59b7-33d1-4ab3-bb64-1e9bda269935
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 5d2339ece646fc51410186d43facdea28ac8fdfe
ms.openlocfilehash: a2da0e0aedde09cbd834f731d1ddc25f9062336e


---

# Útmutató: az ADAL-hitelesítés használata

Hitelesítés az Azure RMS-sel az ADAL-hitelesítést (Azure Active Directory Authentication Library) használó alkalmazás esetén

Az alkalmazásnak a Microsoft Online bejelentkezési segéd helyett az ADAL-hitelesítés használatára való frissítésével Ön és ügyfelei az alábbiakra lesznek képesek:

- Többtényezős hitelesítés használata.
- Az RMS 2.1 ügyfél telepítése rendszergazdai jogosultságok nélkül a számítógépen.
- Az alkalmazás tanúsítása a Windows 10-re.

## A hitelesítési folyamat két megközelítése

Ez a témakör a hitelesítési folyamat két megközelítését ismerteti, a megfelelő programkódpéldákkal kiegészítve.

- **Belső hitelesítés** – Az RMS SDK által kezelt OAuth-hitelesítés.

  Ezt a megközelítést akkor használja, ha azt szeretné, hogy az RMS-ügyfél egy ADAL-hitelesítési üzenetet jelenítsen meg, ha hitelesítésre van szükség. Az alkalmazás konfigurálásával kapcsolatos további részleteket a „Belső hitelesítés” című szakaszban találja.

  > [!Note] 
  > Ha az Ön alkalmazása jelenleg a bejelentkezési segéddel kiegészített AD RMS SDK 2.1-et használja, az alkalmazás áttelepítési útvonalaként a belső hitelesítési módszer használatát ajánljuk.

- **Külső hitelesítés** – Az alkalmazás által kezelt OAuth-hitelesítés.

  Ezt a megközelítést akkor használja, ha azt szeretné, hogy az alkalmazása kezelje az OAuth-hitelesítést. Ezzel a megközelítéssel az RMS-ügyfél egy, az alkalmazás által meghatározott visszahívást intéz, ha hitelesítésre van szükség. Részletes példákat a „Külső hitelesítés” című szakaszban talál, a jelen témakör végén.

  > [!Note] 
  > A külső hitelesítés nem feltétlenül jelenti a felhasználóváltás lehetőségét is: az RMS-ügyfél ugyanis mindig az alapértelmezett felhasználót veszi alapul egy adott RMS-bérlő esetében.

## Belső hitelesítés

1. Konfigurálja az Azure-t [Az Azure RMS beállítása az ADAL-hitelesítéshez](adal-auth.md) című cikkben ismertetett lépésekkel, majd térjen vissza a következő alkalmazásinicializálási lépéshez.
2. Ezt követően már készen áll alkalmazása az RMS SDK 2.1 által biztosított belső ADAL-hitelesítés használatához történő konfigurálására.

Az RMS-ügyfél konfigurálásához rögtön az [IpcInitialize](/rights-management/sdk/2.1/api/win/functions#msipc_ipcinitialize) hívása után adjon hozzá egy [IpcSetGlobalProperty](/rights-management/sdk/2.1/api/win/functions#msipc_ipcsetglobalproperty) hívást. A következő kódrészletet mintaként használhatja.

      C++
      IpcInitialize();

      IPC_AAD_APPLICATION_ID applicationId = { 0 };
      applicationId.cbSize = sizeof(IPC_AAD_APPLICATION_ID);
      applicationId.wszClientId = L"GUID-provided-by-AAD-for-your-app-(no-brackets)";
      applicationId.wszRedirectUri = L"RedirectionUriWeProvidedAADForOurApp://authorize";
      HRESULT hr = IpcSetGlobalProperty(IPC_EI_APPLICATION_ID, &applicationId);
      if (FAILED(hr)) {
        //Handle the error
      }

## Külső hitelesítés

A saját hitelesítési jogkivonatok kezeléséhez az alábbi programkódot használhatja mintaként.
C++ extern HRESULT GetADALToken(LPVOID pContext, const IPC_NAME_VALUE_LIST& Parameters, __out wstring wstrToken) throw();

      HRESULT GetLicenseKey(PCIPC_BUFFER pvLicense, __in LPVOID pContextForAdal, __out IPC_KEY_HANDLE &hKey)
      {
          IPC_OAUTH2_CALLBACK pfGetADALToken =
          [](LPVOID pvContext, PIPC_NAME_VALUE_LIST pParameters, IPC_AUTH_TOKEN_HANDLE* phAuthToken) -> HRESULT
          {
              wstring wstrToken;
              HRESULT hr = GetADALToken(pvContext, *pParameters, wstrToken);
              return SUCCEEDED(hr) ? IpcCreateOAuth2Token(wstrToken.c_str(), OUT phAuthToken) : hr;
          };

          IPC_OAUTH2_CALLBACK_INFO callbackCredentialContext =
          {
              sizeof(IPC_OAUTH2_CALLBACK_INFO),
              pfGetADALToken,
              pContextForAdal
          };

          IPC_CREDENTIAL credentialContext =
          {
              IPC_CREDENTIAL_TYPE_OAUTH2,
              NULL
          };
          credentialContext.pcOAuth2 = &callbackCredentialContext;

          IPC_PROMPT_CTX promptContext =
          {
              sizeof(IPC_PROMPT_CTX),
              NULL,
              IPC_PROMPT_FLAG_SILENT | IPC_PROMPT_FLAG_HAS_USER_CONSENT,
              NULL,
              &credentialContext
          };

          hKey = 0L;
          return IpcGetKey(pvLicense, 0, &promptContext, NULL, &hKey);
      }

## Kapcsolódó témakörök

* [Adattípusok](/rights-management/sdk/2.1/api/win/data%20types)
* [Környezet tulajdonságai](/rights-management/sdk/2.1/api/win/environment%20properties#msipc_environment_properties)
* [IpcCreateOAuth2Token](/rights-management/sdk/2.1/api/win/functions#msipc_ipccreateoauth2token)
* [IpcGetKey](/rights-management/sdk/2.1/api/win/functions#msipc_ipcgetkey)
* [IpcInitialize](/rights-management/sdk/2.1/api/win/functions#msipc_ipcinitialize)
* [IPC_CREDENTIAL](/rights-management/sdk/2.1/api/win/IPC_CREDENTIAL)
* [IPC_NAME_VALUE_LIST](/rights-management/sdk/2.1/api/win/IPC_NAME_VALUE_LIST)
* [IPC_OAUTH2_CALLBACK_INFO](/rights-management/sdk/2.1/api/win/ipc_oauth2_callback_info#msipc_ipc_oath2_callback_info)
* [IPC_PROMPT_CTX](/rights-management/sdk/2.1/api/win/IPC_PROMPT_CTX)
* [IPC_AAD_APPLICATION_ID](/rights-management/sdk/2.1/api/win/ipc_aad_application_id#msipc_ipc_aad_application_id)



<!--HONumber=Aug16_HO4-->

