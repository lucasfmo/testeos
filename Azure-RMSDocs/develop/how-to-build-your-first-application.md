---
title: "IPCHelloWorld — przykładowa aplikacja | Azure RMS"
description: "Ten temat zawiera instrukcje dotyczące tworzenia przykładowej aplikacji obsługującej prawa."
keywords: 
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 581451A2-9558-4D0D-9D01-BEAB282C5A83
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ac6afddc2b39d6209ef1b89d8d84011942cdba5a
ms.openlocfilehash: e75ec6c04afd171552697f79deb33ad2cfe2c4e1


---
** Zawartość tego zestawu SDK jest nieaktualna. Tymczasem należy korzystać z [bieżącej wersji](https://msdn.microsoft.com/library/windows/desktop/hh535290(v=vs.85).aspx) dokumentacji w witrynie MSDN. **
# IPCHelloWorld — przykładowa aplikacja

Ten temat zawiera instrukcje dotyczące tworzenia przykładowej aplikacji obsługującej prawa.

Ta prosta aplikacja, IPCHelloWorld, pomaga w poznaniu podstawowych pojęć i kodu aplikacji obsługującej prawa.

Pobierz aplikację przykładową, [Webinar\_Collateral.zip](https://connect.microsoft.com/site1170/Downloads/DownloadDetails.aspx?DownloadID=42440), z witryny Microsoft Connect. Pozostałe elementy do pobrania w witrynie zostały zintegrowane tutaj dla Twojej wygody.

**Uwaga** Projekt IPCHelloWorld został już skonfigurowany dla zestawu Rights Management Services SDK 2.1. Informacje o sposobie konfigurowania nowego projektu do korzystania z zestawu RMS SDK 2.1 zawiera temat [Konfigurowanie programu Visual Studio](how-to-configure-a-visual-studio-project-to-use-the-ad-rms-sdk-2-0.md).

 
W poniższych częściach omówiono kluczowe kroki aplikacji i elementy, które należy poznać.

## Ładowanie biblioteki MSIPC.dll

Przed wywołaniem dowolnej funkcji zestawu RMS SDK 2.1 należy najpierw wywołać funkcję [**IpcInitialize**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcinitialize) w celu załadowania biblioteki MSIPC.dll.



    hr = IpcInitialize();

    if (FAILED(hr))
    {
      wprintf(L"Failed to initialize MSIPC. Are you sure the runtime is installed?\n");
      goto exit;
    }



## Wyliczanie szablonów

Szablon usług RMS definiuje zasady stosowane do ochrony danych, czyli definiuje użytkowników, którzy mogą uzyskiwać dostęp do danych, i ich prawa. Szablony usług RMS są instalowane na serwerze usług RMS.

Następujący fragment kodu wylicza dostępne szablony usługi RMS z domyślnego serwera usługi RMS.



    hr = IpcGetTemplateList(NULL, 0, 0, NULL, NULL, &pcTil);

    if (FAILED(hr))
    {
      DisplayError(L"IpcGetTemplateList failed", hr);
      goto exit;
    }



To wywołanie pobiera szablony usługi RMS zainstalowane na domyślnym serwerze i ładuje wyniki do struktury [**IPC\_TIL**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcinitialize) wskazywanej przez zmienną *pcTil*, a następnie wyświetla szablony.



    if (0 == pcTil->cTi)
    {
      wprintf(L"* No templates configured for your RMS server * \n\n");
      wprintf(L"\\------------------------------------------------------\n\n");
      goto exit;
    }

    for (DWORD dw = 0; dw < pcTil->cTi; dw++)
    {
      wprintf(L"Template #%d:\n", dw);
      wprintf(L"    Name:         %s\n", pcTil->aTi[dw].wszName);
      wprintf(L"    Issued by:    %s\n", pcTil->aTi[dw].wszIssuerDisplayName);
      wprintf(L"    Description:  %s\n", pcTil->aTi[dw].wszDescription);
      wprintf(L"\n");
    }



## Serializacja licencji

Przed rozpoczęciem ochrony danych należy przeprowadzić serializację licencji i pobrać klucz zawartości. Klucz zawartości jest używany do szyfrowania poufnych danych. Serializowana licencja jest zwykle dołączana do zaszyfrowanych danych i jest używana przez konsumenta chronionych danych. Konsument musi wywołać funkcję [**IpcGetKey**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcgetkey) przy użyciu serializowanej licencji, aby pobrać klucz zawartości w celu odszyfrowania zawartości i pobrania zasad skojarzonych z zawartością.

Dla uproszczenia należy użyć pierwszego szablonu RMS zwróconego przez funkcję [**IpcGetTemplateList**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcgettemplatelist), aby serializować licencję.

Normalnie należy użyć okna dialogowego interfejsu użytkownika w celu umożliwienia użytkownikowi wybrania odpowiedniego szablonu.



    hr = IpcSerializeLicense((LPCVOID)pcTil->aTi[0].wszID, IPC_SL_TEMPLATE_ID,
    0, NULL, &hContentKey, &pSerializedLicense);

    if (FAILED(hr))
    {
      DisplayError(L"IpcSerializeLicense failed", hr);
      goto exit;
    }



Po wykonaniu tego działania dysponujesz kluczem zawartości *hContentKey* i serializowaną licencją *pSerializedLicense*, którą należy dołączyć do chronionych danych.

## Ochrona danych

Teraz można przystąpić do szyfrowania poufnych danych przy użyciu funkcji [**IpcEncrypt**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcencrypt). Po pierwsze należy zapytać funkcję **IpcEncrypt** o rozmiar zaszyfrowanych danych.



    cbText = (DWORD)(sizeof(WCHAR)*(wcslen(wszText)+1));
    hr = IpcEncrypt(hContentKey, 0, TRUE, (PBYTE)wszText, cbText,
    NULL, 0, &cbEncrypted);

    if (FAILED(hr)) {
      DisplayError(L"IpcEncrypt failed", hr);
      goto exit;
    }



W tym przypadku element *wszText* zawiera zwykły tekst, który zostanie objęty ochroną. Funkcja [**IpcEncrypt**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcencrypt) zwraca rozmiar zaszyfrowanych danych w parametrze *cbEncrypted*.

Teraz przydziel pamięć dla zaszyfrowanych danych.



    pbEncrypted = (PBYTE)LocalAlloc(LPTR, cbEncrypted);

    if (NULL == pbEncrypted) {
      wprintf(L"Out of memory\n");
      goto exit;
    }


Na koniec możesz przeprowadzić właściwe szyfrowanie.



    hr = IpcEncrypt(hContentKey, 0, TRUE, (PBYTE)wszText, cbText,
    pbEncrypted, cbEncrypted, &cbEncrypted);

    if (FAILED(hr)) {
      DisplayError(L"IpcEncrypt failed", hr);
      goto exit;
    }


Po wykonaniu tego działania dysponujesz zaszyfrowanymi danymi, *pbEncrypted*, oraz serializowaną licencją, *pSerializedLicense*, która będzie używana przez konsumentów do odszyfrowania danych.

## Obsługa błędów

W tej przykładowej aplikacji do obsługi błędów używana jest funkcja **DisplayError**.



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


Funkcja **DisplayError** używa funkcji [**IpcGetErrorMessageText**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcgeterrormessagetext) w celu pobrania komunikatu o błędzie z odpowiedniego kodu błędu i wysłania go do wyjścia standardowego.

## Czyszczenie

Przed zakończeniem pracy należy także zwolnić wszystkie przydzielone zasoby.



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

* [Uwagi dla deweloperów](developer-notes.md)
* [Konfigurowanie programu Visual Studio](how-to-configure-a-visual-studio-project-to-use-the-ad-rms-sdk-2-0.md)
* [**IpcEncrypt**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcencrypt)
* [**IpcGetErrorMessageText**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcgeterrormessagetext)
* [**IpcGetKey**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcgetkey)
* [**IpcGetTemplateList**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcgettemplatelist)
* [**IpcInitialize**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcinitialize)
* [**IPC\_TIL**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcinitialize)
* [Webinar\_Collateral.zip](https://connect.microsoft.com/site1170/Downloads/DownloadDetails.aspx?DownloadID=42440)
 

 



<!--HONumber=Jun16_HO4-->


