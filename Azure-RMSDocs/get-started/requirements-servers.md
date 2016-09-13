---
title: "Azure RMS-követelmények: Az Azure Rights Managementet támogató helyszíni kiszolgálók | Azure RMS"
description: "A helyszíni az Azure RMS-összekötő használata esetén az Azure RMS által támogatott kiszolgálói termékek azonosítása."
author: cabailey
manager: mbaldwin
ms.date: 08/25/2016
ms.topic: get-started-article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: e7d91f2d-d6a7-4c7e-821f-c94e4be9967d
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 81426cf43f31625c6e83d443fa925f6426eb89da
ms.openlocfilehash: 0f9f1dc09d1b0d831b1c96d25b7bb763086aa9c9


---


# Azure RMS-követelmények: Az Azure RMS-t támogató helyszíni kiszolgálók

>*A következőkre vonatkozik: Azure Rights Management, Office 365*

Az alábbi helyszíni kiszolgálótermékek támogatják az Azure RMS-t az Azure RMS-összekötő használatával, amely kommunikációs illesztőfelületként (továbbítóként) működik a helyszíni kiszolgálók és az Azure RMS között. Ez a konfiguráció emellett a címtár-szinkronizálás konfigurálását igényli az Active Directory-erdő és az Azure Active Directory között.

-   **Exchange Server**:

    -   Exchange Server 2016

    -   Exchange Server 2013

    -   Exchange Server 2010

-   **Office SharePoint Server**:

    -   Office SharePoint Server 2016

    -   Office SharePoint Server 2013

    -   Office SharePoint Server 2010

-   **File servers that run Windows Server and use File Classification Infrastructure (FCI)** (A Windows Server rendszert futtató és a fájlbesorolási infrastruktúrát (FCI) használó fájlkiszolgálók):

    -   Windows Server 2012 R2

    -   Windows Server 2012

    > [!NOTE]
    > Mivel a Windows Server 2008 R2 rendszert futtató fájlkiszolgálók nem rendelkeznek az RMS védelem alkalmazásához szükséges beépített fájlkezelési feladatművelettel, ebben a forgatókönyvben nem használhatja az RMS-összekötőt. Ha azonban konfigurál egy egyéni fájlkezelő feladatot, amely a fájlokat az Azure RMS használatával védeni képes végrehajtható vagy parancsfájlokat futtat, akkor ezeken az operációs rendszereken is használhatja a Fájlbesorolási infrastruktúrát és az Azure RMS-t. Például egy [RMS védelmi parancsmagokat](https://msdn.microsoft.com/library/azure/mt433195.aspx) használó Windows PowerShell parancsfájl.
    > 
    > A Windows Server újabb verzióit futtató kiszolgálókon is használhatja ezeket a parancsmagokat, amelyek ebben az esetben az összes fájltípust képesek védelemmel ellátni. Az RMS-összekötő csak az Office-fájlokat védi. Útmutatásért lásd: [RMS Protection with Windows Server File Classification Infrastructure &#40;FCI&#41;](../rms-client/configure-fci.md) (RMS-védelem és Windows Server fájlbesorolási infrastruktúra).

Az RMS-összekötő a Windows Server 2012 R2, a Windows Server 2012 és a Windows Server 2008 R2 rendszeren támogatott.

Az RMS-összekötő helyszíni kiszolgálókon való konfigurálásával kapcsolatos további információk: [Deploying the Azure Rights Management Connector](../deploy-use/deploy-rms-connector.md) (Az Azure Rights Management-összekötő telepítése).

## További lépések
Az egyéb követelményeket [Az Azure Rights Management követelményei](requirements-azure-rms.md) című témakörben tekintheti meg.



<!--HONumber=Aug16_HO4-->


