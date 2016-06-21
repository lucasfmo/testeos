---
# required metadata

title: Fejlesztői útmutató és információk | Azure RMS
description: Ez a témakör néhány fontos fejlesztési forgatókönyvre vonatkozó konkrét útmutatást ismertet.
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

# Fejlesztői útmutató és információk

Ez a szakasz néhány fontos fejlesztési forgatókönyvre vonatkozó konkrét útmutatást, valamint az SDK-val történő fejlesztéssel kapcsolatos általános információt ismertet. A jelen szakaszban található forgatókönyvek a Rights Management Services SDK 2.1 jelen kiadásához tartoznak, és a későbbi kiadásoknál megváltozhatnak.
- [Útmutató: az ADAL-hitelesítés használata](how-to-use-adal-authentication.md) – Hitelesítés az Azure RMS-sel az ADAL-hitelesítést (Azure Active Directory Authentication Library) használó alkalmazás esetén.
- [Útmutató: Explicit tulajdonosi jogosultságok hozzáadása](add-explicit-owner-rights.md) – Az alkalmazásának hozzá kell adnia a &quot;Tulajdonos&quot; jogot a teljesen újonnan létrehozott licenchez ([IpcCreateLicenseFromScratch](/rights-management/sdk/2.1/api/win/functions#msipc_ipccreatelicensefromscratch)).
- [Útmutató: Tartalomvédelemmel kompatibilis alkalmazások hibakeresése](debugging-applications-that-use-ad-rms.md) – Ez a témakör az alkalmazás hibakeresését és a Windows eseménynaplójának használatát ismerteti.
- [Útmutató: a dokumentumkövetés és -visszavonás engedélyezése](tracking-content.md) – Ez a témakör alapvető útmutatást nyújt a tartalmak dokumentumkövetésének megvalósításához, továbbá kódpéldákat biztosít a metaadatok frissítéséhez és a **Használat követése** gomb létrehozásához a saját alkalmazása számára.
- [Útmutató: E-mail-értesítések engedélyezése](how-to-enable-email-notification.md) – Az e-mail-értesítések lehetővé teszik, hogy a védett tartalom tulajdonosa értesítést kapjon, ha hozzáfértek tartalmához.
- [Útmutató: A szolgáltatásalkalmazás alkalmassá tétele a felhőalapú RMS használatára](how-to-use-file-api-with-aadrm-cloud.md) – Ez a témakör a szolgáltatásalkalmazás Azure Rights Management használatához végzett beállításának lépéseit ismerteti.
- [Útmutató: az RMS-kiszolgáló telepítése és konfigurálása](how-to-install-and-configure-an-rms-server.md) – Ez a témakör az RMS-kiszolgálóhoz vagy az Azure RMS-hez való csatlakozás lépéseit tartalmazza a tartalomvédelemmel kompatibilis alkalmazás teszteléséhez.
- [Útmutató: Az API biztonsági mód beállítás)](setting-the-api-security-mode-api-mode.md) – Az [IpcSetGlobalProperty](/rights-management/sdk/2.1/api/win/functions#msipc_ipcsetglobalproperty) funkció használatával kiválaszthatja, hogy melyik biztonsági módban fusson a File API alkalmazás.
- [Útmutató: A titkosítási beállítások használata](working-with-encryption.md) – Ebben a témakörben megismerkedhet titkosítási csomagjainkkal, valamint a használatukat bemutató kódrészleteket találhat.
- [Alkalmazástípusok](application-types.md) – Ez a témakör azokat az alkalmazástípusokat ismerteti, amelyeket létre lehet hozni tartalomvédelemmel kompatibilisként.
- [A File API konfigurálása](file-api-configuration.md) – A File API működése konfigurálható a beállításjegyzék beállításain keresztül.
- [Támogatott fájlformátumok](supported-file-formats.md) – A File API a natív és a Pfile formátumokat támogatja
- [Támogatott platformok](supported-platforms.md) – Ez a témakör ismerteti az RMS SDK 2.1 által támogatott ügyfél- és kiszolgálóplatformokat.
- [A használattal kapcsolatos korlátozások](understanding-usage-restrictions.md) – Minden RMS-kompatibilis alkalmazásnak ki kell kényszerítenie a használattal kapcsolatos korlátozásokat.
- [A használattal kapcsolatos korlátozás – referencia](usage-restriction-reference.md) – A használattal kapcsolatos korlátozásokat az ebben a témakörben felsorolt állandók határozzák meg.

 
## Kapcsolódó témakörök ##
* [Áttekintés](ad-rms-overview.md)
 

 


<!--HONumber=Jun16_HO2-->


