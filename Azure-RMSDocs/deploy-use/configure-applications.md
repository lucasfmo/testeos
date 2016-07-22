---
title: "Alkalmazások konfigurálása az Azure Rights Managementhez | Azure RMS"
description: 
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: ea09cbc5-b98b-444e-8b60-5bc3cb199c36
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 0f355da35dff62ecee111737eb1793ae286dc93e
ms.openlocfilehash: 8fe934c51e852791d19fbb336deaf9cd7be9817b


---

# Alkalmazások konfigurálása az Azure Rights Managementhez

*A következőkre vonatkozik: Azure Rights Management, Office 365*

> [!NOTE]
> Ez az információ azon informatikai rendszergazdáknak és tanácsadóknak szól, akik üzembe helyezték az Azure Rights Management eszközt. Ha a Rights Management adott használati módjáról vagy a védett fájlok megnyitásáról keres felhasználóknak szóló segítséget és információt, használja az alkalmazáshoz kapott súgót és útmutatást.
>
> Office alkalmazások esetén például kattintson a Súgó ikonra, és írjon be keresési kifejezéseket, például a **Rights Management** vagy az **IRM** kifejezést. Az RMS megosztóalkalmazás Windows rendszeren végzett használatával kapcsolatban lásd [a Rights Management megosztóalkalmazás felhasználói útmutatóját](../rms-client/sharing-app-user-guide.md).

Miután üzembe helyezte az Azure Rights Management (Azure RMS) eszközt a szervezet számára, a következő információkkal konfigurálhatja az alkalmazásokat és szolgáltatásokat az Azure RMS támogatásához. Ezekbe beletartoznak az Office alkalmazások, például a Word 2013 és a Word 2010, valamint olyan szolgáltatások, mint az Exchange Online (átviteli szabályok, adatveszteség-megelőzés, nem továbbítandó és üzenettitkosítás) és a SharePoint Online (védett könyvtárak). Információk arról, hogyan támogatják ezek az alkalmazások és szolgáltatások a Rights Management eszközt: [Hogyan támogatják a különböző alkalmazások az Azure Rights Managementet?](../understand-explore/applications-support.md).

> [!IMPORTANT]
> A támogatott verziókkal és egyéb követelményekkel kapcsolatos információkért lásd: [Az Azure Rights Management követelményei](../get-started/requirements-azure-rms.md).

-   [Office 365: Konfigurálás ügyfelek és online szolgáltatások számára](configure-office365.md)

    -   [Exchange Online: az IRM konfigurálása](configure-office365.md#exchange-online-irm-configuration)

    -   [SharePoint Online és OneDrive Vállalati verzió: az IRM konfigurálása](configure-office365.md#sharepoint-online-and-onedrive-for-business-irm-configuration)

- [Office alkalmazások: Az ügyfelek konfigurálása](configure-office-apps.md)

    -   [Office 2016 és Office 2013](configure-office-apps.md#office-2016-and-office-2013)

    -   [Office 2010](configure-office-apps.md#office-2010)

-   [Rights Management megosztóalkalmazás: Telepítés és konfigurálás ügyfelek esetén](configure-sharing-app.md)

    -   [A Windows RMS-megosztóalkalmazása: Telepítés és konfigurálás](configure-sharing-app.md#the-rms-sharing-application-for-windows-installation-and-configuration)

    -   [Az RMS megosztóalkalmazás mobil platformokhoz: Telepítés és felügyelet](configure-sharing-app.md#the-rms-sharing-application-for-mobile-platforms-installation-and-management)


A helyi kiszolgálók, például az Exchange Server és a SharePoint Server konfigurálásához lásd: [Az Azure Rights Management-összekötő üzembe helyezése](deploy-rms-connector.md).

> [!TIP]
> Az Azure RMS használatához konfigurált alkalmazások magas szintű példáiért és pillanatképeiért lásd: [Az Azure RMS működés közben: Mit látnak a rendszergazdák és a felhasználók](../understand-explore/what-admins-users-see.md).


Ezen alkalmazások és szolgáltatások mellett az RMS API-kat támogató egyéb alkalmazások is vannak. Ebbe a kategóriába olyan üzletági alkalmazások szerepelnek, amelyeket belső fejlesztésként készítettek az RMS SDK-val és olyan alkalmazások, amelyeket szoftverszállítók készítettek az RMS SDK-val. Ezen alkalmazások esetén kövesse az alkalmazáshoz kapott utasításokat.

## További lépések
Az Azure Rights Management eszközt támogató alkalmazások konfigurálása után az [Azure Rights Management üzembe helyezési menetrend](../plan-design/deployment-roadmap.md) segítségével ellenőrizheti, hogy vannak-e további konfigurációs lépések, amelyeket érdemes lehet megtenni, mielőtt a felhasználók és rendszergazdák megkezdik az [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] használatát. Ha nincsenek, a következő működési információk hasznosak lehetnek:

- [Verifying Azure Rights Management (Az Azure Rights Management ellenőrzése)](verify.md)

- [Útmutatás nyújtása a felhasználók számára a fájlok védelméhez az Azure Rights Management használatával](help-users.md)

- [Logging and analyzing Azure Rights Management (Az Azure Rights Management használatának naplózása és elemzése)](log-analyze-usage.md)

- [Operations for Your Azure Rights Management Tenant Key (Az Azure Rights Management bérlőkulcsával kapcsolatos műveletek)](operations-tenant-key.md)





<!--HONumber=Jul16_HO3-->


