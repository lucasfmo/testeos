---
title: "Jak włączyć śledzenie i odwoływanie dokumentów | Azure RMS"
description: "Podstawowe wskazówki dotyczące implementowania śledzenia dokumentów"
keywords: 
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: F5089765-9D94-452B-85E0-00D22675D847
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
experimental: true
experiment_id: priyamo-test-20160729
translationtype: Human Translation
ms.sourcegitcommit: 0d853f99c0a7855354492c508c5c382ceb489a18
ms.openlocfilehash: fb51e2e1438716431a4d8a6e07878c69f428933f


---

# Śledzenie zawartości

# Instrukcje: włączanie śledzenia i odwoływania dokumentów

W tym temacie przedstawiono podstawowe wskazówki dotyczące implementowania śledzenia dokumentu z zawartością oraz przykładowy kod służący do aktualizacji metadanych i tworzenia przycisku **Śledź użycie** na potrzeby aplikacji.

## Procedura implementacji śledzenia dokumentów

Kroki 1 i 2 umożliwiają włączenie śledzenia dokumentów. Krok 3 umożliwia użytkownikom aplikacji przejście do witryny śledzenia dokumentów, w której można śledzić i odwoływać chronione dokumenty.

1. Dodawanie metadanych śledzenia dokumentów
2. Rejestrowanie dokumentu za pomocą usługi RMS
3. Dodawanie przycisku Śledź użycie do aplikacji

Szczegóły implementacji dla tej procedury.

## 1. Dodawanie metadanych śledzenia dokumentów

Śledzenie dokumentów jest funkcją systemu Rights Management. Przez dodanie określonych metadanych podczas procesu włączania ochrony dokumentu można zarejestrować dokument w portalu usługi śledzenia, który zapewnia kilka opcji śledzenia.

Korzystając z poniższych interfejsów API, można dodać/zaktualizować licencję na zawartość przy użyciu metadanych śledzenia dokumentów.


Z perspektywy operacyjnej śledzenie dokumentów wymaga tylko właściwości **nazwy zawartości** i **typu powiadomienia**.


- [IpcCreateLicenseMetadataHandle](/rights-management/sdk/2.1/api/win/functions#msipc_ipccreatelicensemetadatahandle)
- [IpcSetLicenseMetadataProperty](/rights-management/sdk/2.1/api/win/functions#msipc_ipcsetlicensemetadataproperty)

  Oczekujemy, że ustawisz wszystkie właściwości metadanych. Poniżej przedstawiono właściwości posortowane według typu.

  Aby uzyskać więcej informacji, zobacz [License metadata property types](/rights-management/sdk/2.1/api/win/constants#msipc_license_metadata_property_types) (Typy właściwości metadanych licencji).

  - **IPC_MD_CONTENT_PATH**

    Ta właściwość umożliwia zidentyfikowanie śledzonego dokumentu. Jeśli nie można podać pełnej ścieżki, wystarczy podać nazwę pliku.

  - **IPC_MD_CONTENT_NAME**

    Ta właściwość umożliwia zidentyfikowanie nazwy śledzonego dokumentu.

  - **IPC_MD_NOTIFICATION_TYPE**

    Ta właściwość umożliwia określenie, kiedy powiadomienie zostanie wysłane. Aby uzyskać więcej informacji, zobacz Typ powiadomienia.

  - **IPC_MD_NOTIFICATION_PREFERENCE**

    Ta właściwość umożliwia określenie typu powiadomienia. Aby uzyskać więcej informacji, zobacz Preferencje powiadamiania.

  - **IPC_MD_DATE_MODIFIED**

    Zalecamy ustawienie tej daty za każdym razem, gdy użytkownik kliknie pozycję Zapisz.

  - **IPC_MD_DATE_CREATED**

    Ta właściwość umożliwia ustawienie daty utworzenia pliku.

- [IpcSerializeLicenseWithMetadata](/rights-management/sdk/2.1/api/win/functions#msipc_ipcserializelicensemetadata)

Dodaj metadane do pliku lub strumienia za pomocą odpowiedniego z poniższych interfejsów API.

- [IpcfEncryptFileWithMetadata](/rights-management/sdk/2.1/api/win/functions#msipc_ipcfencryptfilewithmetadata)
- [IpcfEncryptFileStreamWithMetadata](/rights-management/sdk/2.1/api/win/functions#msipc_ipcfencryptfilestreamwithmetadata)

Na koniec zarejestruj śledzony dokument w systemie śledzenia przy użyciu poniższego interfejsu API.

- [IpcRegisterLicense](/rights-management/sdk/2.1/api/win/functions#msipc_ipcregisterlicense)


## 2. Rejestrowanie dokumentu za pomocą usługi RMS

Oto fragment kodu będący przykładem ustawienia metadanych śledzenia dokumentu i wywołania w celu przeprowadzenia rejestracji w systemie śledzenia.

      C++
      HRESULT hr = S_OK;
      LPCWSTR wszOutputFile = NULL;
      wstring wszWorkingFile;
      IPC_LICENSE_METADATA md = {0};

      md.cbSize = sizeof(IPC_LICENSE_METADATA);
      md.dwNotificationType = IPCD_CT_NOTIFICATION_TYPE_ENABLED;
      md.dwNotificationPreference = IPCD_CT_NOTIFICATION_PREF_DIGEST;
      //file origination date, current time for this example
      md.ftDateCreated = GetCurrentTime();
      md.ftDateModified = GetCurrentTime();

      LOGSTATUS_EX(L"Encrypt file with official template...");

      hr =IpcfEncryptFileWithMetadata( wszWorkingFile.c_str(),
                               m_wszTestTemplateID.c_str(),
                               IPCF_EF_TEMPLATE_ID,
                               0,
                               NULL,
                               NULL,
                               &md,
                               &wszOutputFile);

     /* This will contain the serialized license */
     PIPC_BUFFER pSerializedLicense;

     /* the context to use for the call */
     PCIPC_PROMPT_CTX pContext;

     wstring wstrContentName(“MyDocument.txt”);
     bool sendLicenseRegistrationNotificationEmail = FALSE;

     hr = IpcRegisterLicense( pSerializedLicense,
                        0,
                        pContext,
                        wstrContentName.c_str(),
                        sendLicenseRegistrationNotificationEmail);

## Dodawanie przycisku **Śledź użycie** do aplikacji

Aby dodać element interfejsu użytkownika **Śledź użycie** do aplikacji, wystarczy użyć jednego z następujących formatów adresów URL:

- Używanie identyfikatora zawartości
  - Pobierz identyfikator zawartości przy użyciu elementu [IpcGetLicenseProperty](/rights-management/sdk/2.1/api/win/functions#msipc_ipcgetlicenseproperty) lub [IpcGetSerializedLicenseProperty](/rights-management/sdk/2.1/api/win/functions#msipc_ipcgetserializedlicenseproperty), jeśli licencja jest zserializowana, i użyj właściwości licencji **IPC_LI_CONTENT_ID**. Aby uzyskać więcej informacji, zobacz [License property types](/rights-management/sdk/2.1/api/win/constants#msipc_license_property_types) (Typy właściwości licencji).
  - W przypadku metadanych **ContentId** i **Issuer** użyj następującego formatu: `https://track.azurerms.com/#/{ContentId}/{Issuer}`

    Przykład: `https://track.azurerms.com/#/summary/05405df5-8ad6-4905-9f15-fc2ecbd8d0f7/janedoe@microsoft.com`

- Jeśli nie masz dostępu do tych metadanych (tj. sprawdzasz niechronioną wersję dokumentu), możesz użyć elementu **Content_Name** w następującym formacie: `https://track.azurerms.com/#/?q={ContentName}`

  Przykład: https://track.azurerms.com/#/?q=Secret!.txt

Klient musi otworzyć odpowiedni adres URL w przeglądarce. Uwierzytelnianie i przekierowanie zostanie przeprowadzone przez portal śledzenia dokumentów usługi RMS.

## Tematy pokrewne

* [Typy właściwości metadanych licencji](/rights-management/sdk/2.1/api/win/constants#msipc_license_metadata_property_types)
* [Preferencje powiadamiania](/rights-management/sdk/2.1/api/win/constants#msipc_notification_preference)
* [Typ powiadomienia](/rights-management/sdk/2.1/api/win/constants#msipc_notification_type)
* [IpcCreateLicenseMetadataHandle](/rights-management/sdk/2.1/api/win/functions#msipc_ipccreatelicensemetadatahandle)
* [IpcSetLicenseMetadataProperty](/rights-management/sdk/2.1/api/win/functions#msipc_ipcsetlicensemetadataproperty)
* [IpcSerializeLicenseWithMetadata](/rights-management/sdk/2.1/api/win/functions#msipc_ipcserializelicensemetadata)
* [IpcfEncryptFileWithMetadata](/rights-management/sdk/2.1/api/win/functions#msipc_ipcfencryptfilewithmetadata)
* [IpcfEncryptFileStreamWithMetadata](/rights-management/sdk/2.1/api/win/functions#msipc_ipcfencryptfilestreamwithmetadata)
* [IpcRegisterLicense](/rights-management/sdk/2.1/api/win/functions#msipc_ipcregisterlicense)

 



<!--HONumber=Jul16_HO5-->


