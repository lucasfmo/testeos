---
title: "Az Azure Rights Management előkészítése | Azure RMS"
description: "Ellenőrizze, hogy minden készen áll az Azure RMS telepítésére, beleértve a felhasználói fiókokat és a hitelesítésre váró csoportokat."
author: cabailey
manager: mbaldwin
ms.date: 08/25/2016
ms.topic: article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: afbca2d6-32a7-4bda-8aaf-9f93f5da5abc
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ada00b6f6298e7d359c73eb38dfdac169eacb708
ms.openlocfilehash: c5f22b4050779193042f3e6e059d8ca84e94b390


---

# Az Azure Rights Management előkészítése

>*A következőkre vonatkozik: Azure Rights Management, Office 365*

Miután regisztrált egy felhőalapú előfizetésre, és egy fiókon keresztül létrehozta a szervezetét a [!INCLUDE[o365_1](../includes/o365_1_md.md)] vagy az Azure Active Directory számára, máris engedélyezheti a [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] szolgáltatást.

Azonban mielőtt ezt megtenné, ellenőrizze, hogy rendelkezik-e az alábbiakkal:

-   A manuálisan létrehozott vagy az Active Directory tartományi szolgáltatásokból (AD DS) szinkronizált és automatikusan létrehozott felhasználói fiókok és csoportok a felhőben.

    A helyszíni fiókok és csoportok szinkronizálásakor nem minden tulajdonságot szükséges szinkronizálni. Azon attribútumok listáját, amelyeket kötelező szinkronizálni az Azure RMS-sel, az Azure Active Directory dokumentációjának az [Azure RMS című szakaszában](/active-directory/active-directory-aadconnectsync-attributes-synchronized#azure-rms) találja. A telepítés megkönnyítése érdekében javasoljuk, hogy az [Azure AD Connect](/active-directory/active-directory-aadconnectsync-whatis) segítségével csatlakoztassa a helyszíni címtárakat az Azure Active Directory-hoz, de bármilyen más címtár-szinkronizálási módszert is használhat, amellyel ugyanezt az eredményt éri el.

-   Levelezési csoportok a felhőben, amelyeket a Rights Managementtel fog használni. Ezek beépített vagy manuálisan létrehozott csoportok lehetnek olyan felhasználókkal, akik használni fogják a Rights Management szolgáltatást.

    Ha rendelkezik Exchange Online szolgáltatással, az Exchange Felügyeleti központ segítségével levelezési csoportokat hozhat létre és használhat. Ha rendelkezik AD DS szolgáltatással, és az Azure AD szolgáltatással szinkronizál, létrehozhat és használhat levelezési csoportokat, amelyek lehetnek biztonsági csoportok vagy terjesztési csoportok.

## A Rights Management engedélyezése
Alapértelmezés szerint a [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] le van tiltva, amikor regisztrálja az [!INCLUDE[o365_2](../includes/o365_2_md.md)]- vagy az Azure AD-fiókját. Aktiválja a szolgáltatást, ha azt szeretné, hogy a [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] engedélyezve legyen a szervezete számára. További információ: [Activating Azure Rights Management](../deploy-use/activate-service.md) (Az Azure Rights Management aktiválása).






<!--HONumber=Aug16_HO4-->


