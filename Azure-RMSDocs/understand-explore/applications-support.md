---
# required metadata

title: Hogyan támogatják a különböző alkalmazások az Azure Rights Managementet? | Azure RMS
description:
keywords:
author: cabailey
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 2cdc7bde-4044-4021-b887-11476f99afd9

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: esaggese
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Hogyan támogatják a különböző alkalmazások az Azure Rights Managementet?

*A következőkre vonatkozik: Azure Rights Management, Office 365*

Az alábbi információk segítségével megismerheti, hogyan biztosíthatnak védelmet a szervezet adatai számára a leggyakoribb végfelhasználói alkalmazások (például az Office-alkalmazások: Word, Excel, PowerPoint és Outlook) és szolgáltatások (például Exchange és SharePoint) a Microsoft [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] használatával. 
> [!NOTE]
> Az [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] (Azure RMS) által támogatott alkalmazások és verziók ellenőrzéséhez tekintse meg: [Az Azure Rights Management követelményei](../get-started/requirements-azure-rms.md)..

Néhány esetben az információvédelem automatikusan megvalósul a konfigurált házirendek alapján. Ez történik például a SharePoint-tárak, a besorolt fájlok és az Exchange átviteli szabályok esetében. Más esetekben az információvédelmet a felhasználóknak kell alkalmazniuk alkalmazásaikban egy sablon kiválasztásával vagy adott beállítások bejelölésével. Ez történik például akkor, ha a felhasználók e-mail-üzenetben osztanak meg egy fájlt, vagy ha helyben védenek egy fájlt úgy, hogy korlátozzák bizonyos felhasználók vagy a szervezeten kívüli felhasználók hozzáférését.

A sablonok egyszerűbbé teszik a felhasználók (és a házirendeket szabályozó rendszergazdák) számára, hogy a megfelelő szintű védelmet alkalmazzák, és korlátozzák a szervezeten belüli személyek hozzáférését. Habár az [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] két alapértelmezett sablont is tartalmaz, érdemes egyéni sablonokat létrehozni az egyedi beállítások megadásával eltöltött idő csökkentése érdekében. További információ: [Configuring custom templates for Azure Rights Management](../deploy-use/configure-custom-templates.md) (Egyéni sablonok konfigurálása az Azure Rights Management szolgáltatáshoz).

Győződjön meg róla, hogy ellátja a felhasználókat utasításokkal és útmutatókkal arra vonatkozóan, hogyan és mikor kell az információvédelmet megvalósítani azokban az esetekben, amikor a felhasználóknak ezt maguknak kell megtenniük. Az utasításoknak az általuk használt alkalmazásokra és verziókra, illetve azok használati módjára kell vonatkozniuk, az információvédelem alkalmazásának feltételeiről szóló útmutatónak pedig az adott tevékenységi körhöz kell igazodnia. További információk: [Útmutatás nyújtása a felhasználók számára a fájlok védelméhez az Azure Rights Management használatával](../deploy-use/help-users.md).

Információk arról, hogyan konfigurálhatja ezeket az alkalmazásokat az Azure RMS-hez: [Configuring applications for Azure Rights Management (Alkalmazások konfigurálása az Azure Rights Managementhez)](../deploy-use/configure-applications.md).

> [!TIP]
> Az Azure RMS-t használó alkalmazások példáiért és pillanatképeiért lásd: [Az Azure RMS működés közben: Mit látnak a rendszergazdák és a felhasználók](what-admins-users-see.md).

## További lépések

Tudjon meg többet arról, hogyan támogatják a következők az Azure RMS-t:

-   [RMS-megosztóalkalmazás Windows és mobil platformokra](sharing-app-support.md)

-   [Office-alkalmazások és -szolgáltatások](office-apps-services-support.md)

-   [File servers that run Windows Server and use File Classification Infrastructure (FCI) (A Windows Server rendszert futtató és a fájlbesorolási infrastruktúrát (FCI) használó fájlkiszolgálók)](file-server-support.md)

-   [Other applications that support the RMS APIs (Egyéb, az RMS API-kat támogató alkalmazások)](api-support.md)



<!--HONumber=Apr16_HO4-->


