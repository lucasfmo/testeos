---
# required metadata

title: Tartalom nyomon követése | Azure RMS
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

# Tartalom nyomon követése

Ez a témakör a Rights Management Services SDK 2.1 eszközzel védett tartalmak dokumentumkövetésének bevezetésére szolgáló alapvető útmutatást tartalmazza.

A dokumentumkövetés a Rights Management rendszer szolgáltatása. Ha adott metaadatokat ad hozzá a dokumentum védelmi folyamata során, a dokumentumok regisztrálhatók a nyomkövetési szolgáltatás portálján, amely több lehetőséget nyújt a nyomkövetésre.

Ezekkel az API-kkal adhat hozzá/frissíthet tartalomlicencet dokumentumkövető metaadatokkal.

-   [**IpcCreateLicenseMetadataHandle**](/rights-management/sdk/2.1/api/win/functions#msipc_ipccreatelicensemetadatahandle)
-   [**IpcSetLicenseMetadataProperty**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcsetlicensemetadataproperty)

    Elvárjuk, hogy beállítsa az összes metaadat-tulajdonságot. Az alábbiakban láthatja a típus szerinti listát.

    További információ: [**License metadata property types**](/rights-management/sdk/2.1/api/win/license%20metadata%20property%20types#msipc_license_metadata_property_types) (Licenc metaadat-tulajdonságainak típusai).

    -   **IPC\_MD\_CONTENT\_PATH**

        Ezzel azonosíthatja a követett dokumentumot. Ahol nincs lehetőség teljes elérési útra, csak adja meg a fájlnevet.

    -   **IPC\_MD\_CONTENT\_NAME**

        Ezzel azonosíthatja a követett dokumentum nevét.

    -   **IPC\_MD\_NOTIFICATION\_TYPE**

        Ezzel adhatja meg, hogy a rendszer mikor küldjön értesítést. További információkért lásd: [**Notification type**](/rights-management/sdk/2.1/api/win/notification%20type#msipc_notification_type) (Értesítés típusa).

    -   **IPC\_MD\_NOTIFICATION\_PREFERENCE**

        Ezzel adhatja meg az értesítés típusát. További információkért lásd: [**Notification preference**](/rights-management/sdk/2.1/api/win/constants#msipc_notification_preference) (Értesítés beállítása).

    -   **IPC\_MD\_DATE\_MODIFIED**

        Ajánlott megadni ezt a dátumot minden alkalommal, amikor a felhasználó a **Mentés** gombra kattint.

    -   **IPC\_MD\_DATE\_CREATED**

        A fájl eredetének dátuma.

-   [**IpcSerializeLicenseWithMetadata**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcserializelicensemetadata)

Ezen API-k közül a megfelelővel adja hozzá a metaadatokat a fájlhoz vagy adatfolyamhoz.

-   [**IpcfEncryptFileWithMetadata**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcfencryptfilewithmetadata)
-   [**IpcfEncryptFileStreamWithMetadata**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcfencryptfilestreamwithmetadata)

Végül ezzel az API-val regisztrálja a követett dokumentumot a követőrendszerrel.

-   [**IpcRegisterLicense**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcregisterlicense)

Itt láthat egy kódrészletet, amely a dokumentumkövető metaadatok beállításának és a követőrendszer regisztrálási hívásának példáját mutatja be.



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

    LOGSTATUS_EX(L&quot;Encrypt file with official template...&quot;);

    hr =IpcfEncryptFileWithMetadata(  wszWorkingFile.c_str(),
                                       m_wszTestTemplateID.c_str(),
                                       IPCF_EF_TEMPLATE_ID,
                                       0,
                                       NULL,
                                       NULL,
                                       &amp;md,
                                       &amp;wszOutputFile);

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


## Kapcsolódó témakörök


* [**License metadata property types (Licenc metaadat-tulajdonságainak típusai)**](/rights-management/sdk/2.1/api/win/license%20metadata%20property%20types#msipc_license_metadata_property_types)
* [**Notification preference (Értesítés beállítása)**](/rights-management/sdk/2.1/api/win/constants#msipc_notification_preference)
* [**Notification type (Értesítés típusa)**](/rights-management/sdk/2.1/api/win/notification%20type#msipc_notification_type)
* [**IpcCreateLicenseMetadataHandle**](/rights-management/sdk/2.1/api/win/functions#msipc_ipccreatelicensemetadatahandle)
* [**IpcSetLicenseMetadataProperty**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcsetlicensemetadataproperty)
* [**IpcSerializeLicenseWithMetadata**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcserializelicensemetadata)
* [**IpcfEncryptFileWithMetadata**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcfencryptfilewithmetadata)
* [**IpcfEncryptFileStreamWithMetadata**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcfencryptfilestreamwithmetadata)
* [**IpcRegisterLicense**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcregisterlicense)
 

 


<!--HONumber=May16_HO2-->


