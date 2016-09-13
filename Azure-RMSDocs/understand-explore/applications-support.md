---
title: "Hogyan támogatják a különböző alkalmazások az Azure Rights Managementet? | Azure RMS"
description: "Ismerje meg, hogyan biztosíthatnak védelmet a szervezet adatai számára a leggyakoribb végfelhasználói alkalmazások (például az Office-alkalmazások: Word, Excel, PowerPoint és Outlook) és -szolgáltatások (például Exchange és SharePoint) a Microsoft Azure Rights Management használatával."
author: cabailey
manager: mbaldwin
ms.date: 08/25/2016
ms.topic: article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 2cdc7bde-4044-4021-b887-11476f99afd9
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 43429b44c019144744f39a1f92f144d315c2024c
ms.openlocfilehash: 00f64e1d22f9e3aba302dcef43d2041a4e4c9fab


---

# Hogyan támogatják a különböző alkalmazások az Azure Rights Managementet?

>*A következőkre vonatkozik: Azure Rights Management, Office 365*

Az alábbi információk segítségével megismerheti, hogyan biztosíthatnak védelmet a szervezet adatai számára a leggyakoribb végfelhasználói alkalmazások (például az Office-alkalmazások: Word, Excel, PowerPoint és Outlook) és szolgáltatások (például Exchange és SharePoint) a Microsoft [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] használatával. 
> [!NOTE]
> Az [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] (Azure RMS) által támogatott alkalmazások és verziók ellenőrzéséhez lásd: [Az Azure Rights Management követelményei](../get-started/requirements-azure-rms.md).

Néhány esetben az információvédelem automatikusan megvalósul a konfigurált házirendek alapján. Ez történik például a SharePoint-tárak, a besorolt fájlok és az Exchange átviteli szabályok esetében. Más esetekben az információvédelmet a felhasználóknak kell alkalmazniuk alkalmazásaikban egy sablon kiválasztásával vagy adott beállítások bejelölésével. Ez történik például akkor, ha a felhasználók e-mail-üzenetben osztanak meg egy fájlt, vagy ha helyben védenek egy fájlt úgy, hogy korlátozzák bizonyos felhasználók vagy a szervezeten kívüli felhasználók hozzáférését.

A sablonok egyszerűbbé teszik a felhasználók (és a házirendeket szabályozó rendszergazdák) számára, hogy a megfelelő szintű védelmet alkalmazzák, és korlátozzák a szervezeten belüli személyek hozzáférését. Habár az [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] két alapértelmezett sablont is tartalmaz, érdemes egyéni sablonokat létrehozni az egyedi beállítások megadásával eltöltött idő csökkentése érdekében. További információ: [Configuring custom templates for Azure Rights Management](../deploy-use/configure-custom-templates.md) (Egyéni sablonok konfigurálása az Azure Rights Management szolgáltatáshoz).

Győződjön meg róla, hogy ellátja a felhasználókat utasításokkal és útmutatókkal arra vonatkozóan, hogyan és mikor kell az információvédelmet megvalósítani azokban az esetekben, amikor a felhasználóknak ezt maguknak kell megtenniük. Az utasításoknak az általuk használt alkalmazásokra és verziókra, illetve azok használati módjára kell vonatkozniuk, az információvédelem alkalmazásának feltételeiről szóló útmutatónak pedig az adott tevékenységi körhöz kell igazodnia. További információ: [Útmutatás nyújtása a felhasználók számára a fájlok védelméhez az Azure Rights Management használatával](../deploy-use/help-users.md).

Információ arról, hogyan konfigurálhatja ezeket az alkalmazásokat az Azure RMS-hez: [Alkalmazások konfigurálása az Azure Rights Managementhez](../deploy-use/configure-applications.md).

> [!TIP]
> Az Azure RMS-t használó alkalmazások példái és pillanatképei: [Az Azure RMS működés közben: Mit látnak a rendszergazdák és a felhasználók](what-admins-users-see.md).

A keresési szolgáltatások többféleképpen integrálhatók a Rights Managementtel. Példa: 

- Az Exchange Online és az Exchange Server szolgáltatásoldali indexelést használ, így a felhasználó RMS által védett e-mailjei automatikusan megjelennek a keresési eredményekben. 

- A SharePoint Online és a SharePoint Server csak a letöltött fájlokat látja el RMS-védelemmel, így az indexelést és a keresési eredményeket nem érinti ez a dokumentumvédelmi megoldás. Azonban ha egy olyan dokumentuma van, amelyet a SharePointban kíván tárolni, de nem szeretné, hogy megjelenjen a keresési eredményekben, a SharePointra való feltöltés előtt lássa el RMS-védelemmel a fájlt.

- A Windows asztali keresés megosztott indexet használ az eszköz különböző felhasználói között, így a védett dokumentumokban tárolt adatok biztonsága érdekében nem indexeli az RMS-védelemmel ellátott fájlokat. Ez azt jelenti, hogy bár a keresési eredményeiben nem jelennek meg a védett fájlok, biztos lehet abban is, hogy a bizalmas adatokat tartalmazó fájljai a számítógépét használó vagy ahhoz csatlakozó többi felhasználó keresési eredményeiben sem fognak szerepelni. 



## További lépések

Tudjon meg többet arról, hogyan támogatják a következők az Azure RMS-t:

-   [RMS-megosztóalkalmazás Windows és mobil platformokra](sharing-app-support.md)

-   [Office-alkalmazások és -szolgáltatások](office-apps-services-support.md)

-   [File servers that run Windows Server and use File Classification Infrastructure (FCI) (A Windows Server rendszert futtató és a fájlbesorolási infrastruktúrát (FCI) használó fájlkiszolgálók)](file-server-support.md)

-   [Other applications that support the RMS APIs (Egyéb, az RMS API-kat támogató alkalmazások)](api-support.md)




<!--HONumber=Aug16_HO4-->


