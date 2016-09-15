---
title: "Uwierzytelnianie ADAL dla aplikacji z obsługą usługi RMS| Azure RMS"
description: "Zawiera opis procesu uwierzytelniania przy użyciu biblioteki ADAL"
keywords: uwierzytelnianie, RMS, ADAL
author: bruceperlerms
manager: mbaldwin
ms.date: 06/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: f89f59b7-33d1-4ab3-bb64-1e9bda269935
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 4c3625676c7e794ef133c75881f666bae80e0513
ms.openlocfilehash: 9200ea44671776ced8781c1e13e71871f5bdf014


---

# Instrukcje: korzystanie z uwierzytelniania ADAL

Uwierzytelnianie w usłudze Azure RMS dla aplikacji z użyciem biblioteki Azure Active Directory Authentication Library (ADAL).

Aktualizacja aplikacji umożliwiająca korzystanie z uwierzytelniania ADAL zamiast asystenta logowania usługi online firmy Microsoft zapewnia następujące możliwości:

- Korzystanie z uwierzytelniania wieloskładnikowego
- Instalowanie klienta usługi RMS 2.1 bez wymogu posiadania uprawnień administracyjnych na komputerze
- Certyfikowanie aplikacji dla systemu Windows 10

## Dwa podejścia do uwierzytelniania

W tym temacie przedstawiono dwie metody uwierzytelniania wraz z odpowiednimi przykładami kodu.

- **Uwierzytelnianie wewnętrzne** — uwierzytelnianie OAuth zarządzane przez zestaw RMS SDK.

  Tej metody należy użyć, jeśli klient RMS ma wyświetlać monit o uwierzytelnienie ADAL w przypadku, gdy wymagane jest uwierzytelnienie. Aby uzyskać szczegółowe informacje na temat konfigurowania aplikacji, zobacz część „Uwierzytelnianie wewnętrzne”.

  > [!Note] 
  > Jeśli aplikacja używa aktualnie zestawu SDK usług AD RMS w wersji 2.1 z asystentem logowania, zalecane jest użycie metody uwierzytelniania wewnętrznego jako ścieżki migracji aplikacji.

- **Uwierzytelnianie zewnętrzne** — uwierzytelnianie OAuth zarządzane przez aplikację.

  Tej metody należy użyć, jeśli aplikacja ma zarządzać własnym uwierzytelnianiem OAuth. W przypadku tego podejścia klient RMS wykonuje wywołanie zwrotne określone w aplikacji, gdy jest wymagane uwierzytelnienie. Szczegółowy przykład znajduje się w części „Uwierzytelnianie zewnętrzne” na końcu tego tematu.

  > [!Note] 
  > Uwierzytelnianie zewnętrzne nie oznacza możliwości zmiany użytkowników — w kliencie RMS zawsze używany jest domyślny użytkownik dla danej dzierżawy RMS.

## Uwierzytelnianie wewnętrzne

1. Wykonaj procedurę konfiguracji platformy Azure przedstawioną w artykule [Konfigurowanie usługi Azure RMS na potrzeby uwierzytelniania ADAL](adal-auth.md), a następnie wróć do poniższego kroku inicjowania aplikacji.
2. Teraz możesz przystąpić do konfigurowania aplikacji do korzystania z wewnętrznego uwierzytelniania ADAL zapewnianego w ramach zestawu RMS SDK 2.1.

Aby skonfigurować klienta usługi RMS, dodaj wywołanie do właściwości [IpcSetGlobalProperty](/rights-management/sdk/2.1/api/win/functions#msipc_ipcsetglobalproperty) bezpośrednio po wywołaniu elementu [IpcInitialize](/rights-management/sdk/2.1/api/win/functions#msipc_ipcinitialize). Jako przykład może posłużyć poniższy fragment kodu.

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

## Uwierzytelnianie zewnętrzne

Poniższy kod stanowi przykład zarządzania własnymi tokenami uwierzytelniania.
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

## Tematy pokrewne

* [Typy danych](/rights-management/sdk/2.1/api/win/data%20types)
* [Właściwości środowiska](/rights-management/sdk/2.1/api/win/environment%20properties#msipc_environment_properties)
* [IpcCreateOAuth2Token](/rights-management/sdk/2.1/api/win/functions#msipc_ipccreateoauth2token)
* [IpcGetKey](/rights-management/sdk/2.1/api/win/functions#msipc_ipcgetkey)
* [IpcInitialize](/rights-management/sdk/2.1/api/win/functions#msipc_ipcinitialize)
* [IPC_CREDENTIAL](/rights-management/sdk/2.1/api/win/IPC_CREDENTIAL)
* [IPC_NAME_VALUE_LIST](/rights-management/sdk/2.1/api/win/IPC_NAME_VALUE_LIST)
* [IPC_OAUTH2_CALLBACK_INFO](/rights-management/sdk/2.1/api/win/ipc_oauth2_callback_info#msipc_ipc_oath2_callback_info)
* [IPC_PROMPT_CTX](/rights-management/sdk/2.1/api/win/IPC_PROMPT_CTX)
* [IPC_AAD_APPLICATION_ID](/rights-management/sdk/2.1/api/win/ipc_aad_application_id#msipc_ipc_aad_application_id)



<!--HONumber=Jul16_HO3-->


