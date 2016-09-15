---
title: Tworzenie aplikacji | Azure RMS
description: "Instrukcje dotyczące tworzenia aplikacja za pomocą zestawu RMS SDK 2.1."
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

# Tworzenie aplikacji

Ten temat zawiera podstawowe wskazówki dotyczące kluczowych aspektów aplikacji z obsługą usługi RMS i może służyć jako podstawa tworzenia aplikacji.

## Wprowadzenie

Wskazówki zawarte w tym temacie bazują na prostej aplikacji, IPCHelloWorld, która pomaga w poznaniu podstawowych pojęć i kodu aplikacji obsługującej prawa. Możesz pobrać pełną przykładową aplikację IPCHelloWorld jako plik [Webinar_Collateral.zip](https://connect.microsoft.com/site1170/Downloads/DownloadDetails.aspx?DownloadID=42440) z witryny Microsoft Connect.

> [!Note] 
> Projekt IPCHelloWorld został już skonfigurowany dla zestawu Rights Management Services SDK 2.1. Informacje o sposobie konfigurowania nowego projektu do korzystania z zestawu RMS SDK 2.1 zawiera temat [Konfigurowanie programu Visual Studio](how-to-configure-a-visual-studio-project-to-use-the-ad-rms-sdk-2-0.md).

## Ładowanie biblioteki MSIPC.dll

Przed wywołaniem dowolnej funkcji zestawu RMS SDK 2.1 należy najpierw wywołać funkcję [IpcInitialize](/rights-management/sdk/2.1/api/win/functions#msipc_ipcinitialize) w celu załadowania biblioteki MSIPC.dll.

        C++
        hr = IpcInitialize();
        if (FAILED(hr)) {
          wprintf(L"Failed to initialize MSIPC. Are you sure the runtime is installed?\n");
          goto exit;
        }

## Wyliczanie szablonów

Szablon usług RMS definiuje zasady stosowane do ochrony danych, czyli definiuje użytkowników, którzy mogą uzyskiwać dostęp do danych, i ich prawa. Szablony usług RMS są instalowane na serwerze usług RMS.

Następujący fragment kodu wylicza dostępne szablony usług RMS z domyślnego serwera usług RMS.

      C++
      hr = IpcGetTemplateList(NULL, 0, 0, NULL, NULL, &pcTil);

      if (FAILED(hr)) {
        DisplayError(L"IpcGetTemplateList failed", hr);
        goto exit;
      }

To wywołanie pobiera szablony usług RMS zainstalowane na domyślnym serwerze i ładuje wyniki do struktury [IPC_TIL](/rights-management/sdk/2.1/api/win/ipc_til#msipc_ipc_til) wskazywanej przez zmienną *pcTil*, a następnie wyświetla szablony.

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

## Serializowanie licencji

Przed rozpoczęciem ochrony danych należy przeprowadzić serializację licencji i pobrać klucz zawartości. Klucz zawartości jest używany do szyfrowania poufnych danych. Serializowana licencja jest zwykle dołączana do zaszyfrowanych danych i jest używana przez konsumenta chronionych danych. Konsument musi wywołać funkcję [IpcGetKey](/rights-management/sdk/2.1/api/win/functions#msipc_ipcgetkey) przy użyciu serializowanej licencji, aby pobrać klucz zawartości w celu odszyfrowania zawartości i pobrania zasad skojarzonych z zawartością.

Dla uproszczenia należy użyć pierwszego szablonu usług RMS zwróconego przez funkcję [IpcGetTemplateList](/rights-management/sdk/2.1/api/win/functions#msipc_ipcgettemplatelist), aby serializować licencję.

Normalnie należy użyć okna dialogowego interfejsu użytkownika w celu umożliwienia użytkownikowi wybrania odpowiedniego szablonu.

      C++
      hr = IpcSerializeLicense((LPCVOID)pcTil->aTi[0].wszID, IPC_SL_TEMPLATE_ID,
        0, NULL, &hContentKey, &pSerializedLicense);

      if (FAILED(hr)) {
        DisplayError(L"IpcSerializeLicense failed", hr);
        goto exit;
      }

Po wykonaniu tego działania dysponujesz kluczem zawartości *hContentKey* i serializowaną licencją *pSerializedLicense*, którą należy dołączyć do chronionych danych.


## Ochrona danych

Teraz możesz przystąpić do szyfrowania poufnych danych przy użyciu funkcji [IpcEncrypt](/rights-management/sdk/2.1/api/win/functions#msipc_ipcencrypt). Po pierwsze należy zapytać funkcję **IpcEncrypt** o rozmiar zaszyfrowanych danych.

      C++
      cbText = (DWORD)(sizeof(WCHAR)*(wcslen(wszText)+1));
      hr = IpcEncrypt(hContentKey, 0, TRUE, (PBYTE)wszText, cbText,
        NULL, 0, &cbEncrypted);

      if (FAILED(hr)) {
        DisplayError(L"IpcEncrypt failed", hr);
        goto exit;
      }

W tym przypadku element wszText zawiera zwykły tekst, który zostanie objęty ochroną. Funkcja [IpcEncrypt](/rights-management/sdk/2.1/api/win/functions#msipc_ipcencrypt) zwraca rozmiar zaszyfrowanych danych w parametrze *cbEncrypted*.

Teraz przydziel pamięć dla zaszyfrowanych danych.

      C++
      pbEncrypted = (PBYTE)LocalAlloc(LPTR, cbEncrypted);

      if (NULL == pbEncrypted) {
        wprintf(L"Out of memory\n");
        goto exit;
      }

Na koniec możesz przeprowadzić właściwe szyfrowanie.

      C++
      hr = IpcEncrypt(hContentKey, 0, TRUE, (PBYTE)wszText, cbText,
        pbEncrypted, cbEncrypted, &cbEncrypted);

      if (FAILED(hr)) {
        DisplayError(L"IpcEncrypt failed", hr);
        goto exit;
      }

Po wykonaniu tego działania dysponujesz zaszyfrowanymi danymi, *pbEncrypted*, oraz serializowaną licencją, *pSerializedLicense*, która będzie używana przez konsumentów do odszyfrowania danych.

## Obsługa błędów

W tej przykładowej aplikacji do obsługi błędów używana jest funkcja *DisplayError*.

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

Funkcja *DisplayError* używa funkcji [IpcGetErrorMessageText](/rights-management/sdk/2.1/api/win/functions#msipc_ipcgeterrormessagetext) w celu pobrania komunikatu o błędzie z odpowiedniego kodu błędu i wysłania go do wyjścia standardowego.

## Czyszczenie

Przed zakończeniem pracy należy także zwolnić wszystkie przydzielone zasoby.

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

## Tematy pokrewne

- [Wskazówki i informacje dla deweloperów](developer-notes.md)
- [IpcEncrypt](/rights-management/sdk/2.1/api/win/functions#msipc_ipcencrypt)
- [IpcGetErrorMessageText](/rights-management/sdk/2.1/api/win/functions#msipc_ipcgeterrormessagetext)
- [IpcGetKey](/rights-management/sdk/2.1/api/win/functions#msipc_ipcgetkey)
- [IpcGetTemplateList](/rights-management/sdk/2.1/api/win/functions#msipc_ipcgettemplatelist)
- [IpcInitialize](/rights-management/sdk/2.1/api/win/functions#msipc_ipcinitialize)
- [IPC_TIL](/rights-management/sdk/2.1/api/win/ipc_til#msipc_ipc_til)
- [Webinar_Collateral.zip](https://connect.microsoft.com/site1170/Downloads/DownloadDetails.aspx?DownloadID=42440)



<!--HONumber=Jul16_HO4-->


