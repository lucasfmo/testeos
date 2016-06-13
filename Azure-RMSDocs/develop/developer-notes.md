---
# required metadata

title: Megjegyzések fejlesztők számára | Azure RMS
description: Ez a témakör ismertet néhány fontos fejlesztési forgatókönyvre vonatkozó konkrét útmutatást. 
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 5A9F04FD-0FCD-482F-8671-36FE93B783B0
# optional metadata

#ROBOTS:
audience: developer
#ms.devlang:
ms.reviewer: shubhamp
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Megjegyzések fejlesztők számára

Ez a szakasz ismertet néhány fontos fejlesztési forgatókönyvre vonatkozó konkrét útmutatást. A jelen szakaszban található forgatókönyvek a Rights Management Services SDK 2.1 jelen kiadásához tartoznak, és a későbbi kiadásoknál megváltozhatnak.

- [Add explicit owner rights (Explicit tulajdonosi jogosultságok hozzáadása)](add-explicit-owner-rights.md) – Alkalmazásának hozzá kell adnia a &quot;Tulajdonos&quot; jogot a teljesen újonnan létrehozott licenchez ([IpcCreateLicenseFromScratch](/rights-management/sdk/2.1/api/win/functions#msipc_ipccreatelicensefromscratch)).
- [Common error conditions and solutions (Gyakori hibaállapotok és a megoldások)](common-error-conditions-and-solutions.md) – Az RMS SDK 2.1 fejlesztői eszközök használatakor esetleg előforduló leggyakoribb hibaüzenetek.
- [Enabling email notification (E-mail-értesítések engedélyezése)](how-to-enable-email-notification.md) – Az e-mail-értesítések lehetővé teszik, hogy a védett tartalom tulajdonosa értesítést kapjon, ha hozzáfértek tartalmához.
- [File API configuration (A File API konfigurálása)](file-api-configuration.md) – A File API működése konfigurálható a beállításjegyzék beállításain keresztül.
- [IPCHelloWorld - an example application (IPCHelloWorld – egy mintaalkalmazás)](how-to-build-your-first-application.md) – Ez a témakör egy tartalomvédelemmel kompatibilis mintaalkalmazás létrehozásának utasításait tartalmazza.
- [Setting the API security mode (Az API biztonsági mód beállítása)](setting-the-api-security-mode-api-mode.md) – Az [IpcSetGlobalProperty](/rights-management/sdk/2.1/api/win/functions#msipc_ipcsetglobalproperty) funkció használatával kiválaszthatja, hogy melyik biztonsági módban fusson a File API alkalmazás.
- [Supported file formats (Támogatott fájlformátumok)](supported-file-formats.md) – A File API a natív és a Pfile formátumokat támogatja.
- [Tracking content (Tartalom nyomon követése)](tracking-content.md) – Ez a témakör az RMS SDK 2.1 eszközzel védett tartalmak dokumentumkövetésének bevezetésére szolgáló alapvető útmutatást tartalmazza.
- [Working with encryption (A titkosítás használata)](working-with-encryption.md) – Ebben a témakörben megismerkedhet titkosítási csomagjainkkal, valamint a használatukat bemutató kódrészleteket találhat.

 

## Kapcsolódó témakörök ##
* [Áttekintés](ad-rms-overview.md)
* [Használati útmutató](how-to-use-msipc.md)
 

 


<!--HONumber=Apr16_HO4-->


