---
# required metadata

title: Útmutató: A dokumentumkövetés és -visszavonás engedélyezése | Azure RMS
description: A dokumentumok nyomon követésének bevezetésére szolgáló alapvető útmutatás
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: F5089765-9D94-452B-85E0-00D22675D847
# optional metadata

#ROBOTS:
audience: developer
#ms.devlang:
ms.reviewer: shubhamp
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---
<<<<<<< HEAD

# Tartalom nyomon követése
=======
>>>>>>> 81ec5ddf5acf3de78d77c01ed95631e44d37fe6e

# Útmutató: A dokumentumkövetés és -visszavonás engedélyezése

Ez a témakör alapvető útmutatást nyújt a tartalmak dokumentumkövetésének megvalósításához, továbbá kódpéldákat biztosít a metaadatok frissítéséhez és a **Használat követése** gomb létrehozásához saját alkalmazása számára.

## A dokumentumkövetés megvalósításának lépései

Az 1. és 2. lépésben lehetővé teszi a dokumentum követését. A 3. lépésben lehetővé teszi, hogy az alkalmazás felhasználói hozzáférhessenek a dokumentumkövetési webhelyhez a védett dokumentumok nyomon követése és visszavonása céljából.

1. Dokumentumkövetési metaadatok hozzáadása
2. A dokumentum regisztrálása az RMS szolgáltatásban
3. A „Használat követése” gomb elhelyezése az alkalmazásban

A lépések megvalósításának részletei az alábbiakban olvashatók.

## 1. Dokumentumkövetési metaadatok hozzáadása

A dokumentumkövetés a Rights Management rendszer szolgáltatása. Ha adott metaadatokat ad hozzá a dokumentum védelmi folyamata során, a dokumentumok regisztrálhatók a nyomkövetési szolgáltatás portálján, amely több lehetőséget nyújt a nyomkövetésre.

Ezekkel az API-kkal adhat hozzá/frissíthet tartalomlicencet dokumentumkövető metaadatokkal.


Működés közben csak a **tartalom neve** és az **értesítés típusa** tulajdonság szükséges a dokumentumok nyomon követéséhez.


- [IpcCreateLicenseMetadataHandle](/rights-management/sdk/2.1/api/win/functions#msipc_ipccreatelicensemetadatahandle)
- [IpcSetLicenseMetadataProperty](/rights-management/sdk/2.1/api/win/functions#msipc_ipcsetlicensemetadataproperty)

  Elvárjuk, hogy beállítsa az összes metaadat-tulajdonságot. Az alábbiakban láthatja a típus szerinti listát.

  További információ: [Licenc metaadat-tulajdonságainak típusai](/rights-management/sdk/2.1/api/win/constants#msipc_license_metadata_property_types).

  - **IPC_MD_CONTENT_PATH**

    Ezzel azonosíthatja a követett dokumentumot. Ahol nincs lehetőség teljes elérési útra, csak adja meg a fájlnevet.

  - **IPC_MD_CONTENT_NAME**

    Ezzel azonosíthatja a követett dokumentum nevét.

  - **IPC_MD_NOTIFICATION_TYPE**

    Ezzel adhatja meg, hogy a rendszer mikor küldjön értesítést. További információt az „Értesítés típusa” című szakaszban találhat.

  - **IPC_MD_NOTIFICATION_PREFERENCE**

    Ezzel adhatja meg az értesítés típusát. További információt az „Értesítés beállítása” című szakaszban találhat.

  - **IPC_MD_DATE_MODIFIED**

    Érdemes ezt a dátumot minden alkalommal beállítani, amikor a felhasználó a Mentés gombra kattint.

  - **IPC_MD_DATE_CREATED**

    A fájl létrehozási dátumának beállítására szolgál

- [IpcSerializeLicenseWithMetadata](/rights-management/sdk/2.1/api/win/functions#msipc_ipcserializelicensemetadata)

Ezen API-k közül a megfelelővel adja hozzá a metaadatokat a fájlhoz vagy adatfolyamhoz.

- [IpcfEncryptFileWithMetadata](/rights-management/sdk/2.1/api/win/functions#msipc_ipcfencryptfilewithmetadata)
- [IpcfEncryptFileStreamWithMetadata](/rights-management/sdk/2.1/api/win/functions#msipc_ipcfencryptfilestreamwithmetadata)

Végül ezzel az API-val regisztrálja a követett dokumentumot a követőrendszerrel.

- [IpcRegisterLicense](/rights-management/sdk/2.1/api/win/functions#msipc_ipcregisterlicense)


## 2. A dokumentum regisztrálása az RMS szolgáltatásban

Itt láthat egy kódrészletet, amely a dokumentumkövető metaadatok beállításának és a követőrendszer regisztrálási hívásának példáját mutatja be.

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

## A **Használat követése** gomb elhelyezése az alkalmazásban

A **Használat követése** kezelőfelületi elem könnyen elhelyezhető az alkalmazásban – csak használja a következő URL-formátumok egyikét:

- Tartalomazonosító használata
  - Ha a licenc szerializált, az [IpcGetLicenseProperty](/rights-management/sdk/2.1/api/win/functions#msipc_ipcgetlicenseproperty) vagy az [IpcGetSerializedLicenseProperty](/rights-management/sdk/2.1/api/win/functions#msipc_ipcgetserializedlicenseproperty) függvénnyel kérje le a tartalomazonosítót, majd használja az **IPC_LI_CONTENT_ID** licenctulajdonságot. További információ: [Licenctulajdonság-típusok](/rights-management/sdk/2.1/api/win/constants#msipc_license_property_types).
  - A **ContentId** (tartalomazonosító) és az **Issuer** (kibocsátó) metaadatoknál használja a következő formátumot: `https://track.azurerms.com/#/{ContentId}/{Issuer}`

    Például: `https://track.azurerms.com/#/summary/05405df5-8ad6-4905-9f15-fc2ecbd8d0f7/janedoe@microsoft.com`

- Ha nem fér hozzá ezekhez a metaadatokhoz (azaz a dokumentum védelem nélküli verzióját vizsgálja), a **Content_Name** a következő formátumban is használható: `https://track.azurerms.com/#/?q={ContentName}`

  Például: https://track.azurerms.com/#/?q=Secret!.txt

Az ügyfélnek egyszerűen meg kell nyitnia egy böngészőt a megfelelő URL-lel. A hitelesítést és az esetlegesen szükséges átirányítást az RMS dokumentumkövető portál kezeli.

## Kapcsolódó témakörök

* [License metadata property types (Licenc metaadat-tulajdonságainak típusai)](/rights-management/sdk/2.1/api/win/constants#msipc_license_metadata_property_types)
* [Notification preference (Értesítés beállítása)](/rights-management/sdk/2.1/api/win/constants#msipc_notification_preference)
* [Notification type (Értesítés típusa)](/rights-management/sdk/2.1/api/win/constants#msipc_notification_type)
* [IpcCreateLicenseMetadataHandle](/rights-management/sdk/2.1/api/win/functions#msipc_ipccreatelicensemetadatahandle)
* [IpcSetLicenseMetadataProperty](/rights-management/sdk/2.1/api/win/functions#msipc_ipcsetlicensemetadataproperty)
* [IpcSerializeLicenseWithMetadata](/rights-management/sdk/2.1/api/win/functions#msipc_ipcserializelicensemetadata)
* [IpcfEncryptFileWithMetadata](/rights-management/sdk/2.1/api/win/functions#msipc_ipcfencryptfilewithmetadata)
* [IpcfEncryptFileStreamWithMetadata](/rights-management/sdk/2.1/api/win/functions#msipc_ipcfencryptfilestreamwithmetadata)
* [IpcRegisterLicense](/rights-management/sdk/2.1/api/win/functions#msipc_ipcregisterlicense)

 


<!--HONumber=Jun16_HO2-->


