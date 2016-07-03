---
title: "AD RMS-kiszolgáló | Azure RMS"
description: "A Rights Management Services (RMS) kiszolgáló-összetevőt számos, a Microsoft Internet Information Services szolgáltatásban futó webes szolgáltatás megvalósítja."
keywords: 
author: bruceperlerms
manager: mbaldwin
ms.date: 06/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 17B05780-B0EF-4805-8304-52DCDEB3AADB
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 56d0538243af49580f24c701ad5097b30f3059b0
ms.openlocfilehash: 2b7c99e3adafde7140d7997364ec2643ba79a2ac


---

# Kiszolgáló

Ez a témakör az RMS-kiszolgáló célját és funkcióit ismerteti az Azure-ra és a Windows Serverre vonatkozóan.

**Azure RMS** – az Azure Rights Management szolgáltatás használatáról a következő témakörben olvasható tájékoztatás: [A szolgáltatásalkalmazás alkalmassá tétele a felhőalapú RMS használatára](how-to-use-file-api-with-aadrm-cloud.md).

> [!IMPORTANT] 
> Azt javasoljuk, hogy az alkalmazás fejlesztését és tesztelését az Azure RMS-sel végezze.

**Windows Server** – Helyszíni kiszolgálók esetében szerepkörként hozzáadva telepítheti és konfigurálhatja az RMS szolgáltatást a Windows Server 2008-tól kezdődően. Az ennél régebbi operációs rendszerekre való telepítéséhez töltse le a szolgáltatást a Microsoft letöltőközpontjából: [Microsoft Windows tartalomvédelmi szolgáltatások Service Pack 2 szervizcsomaggal](http://www.microsoft.com/download/en/details.aspx?id=4909).

A számos telepített webes szolgáltatás közül az alábbiak fontosak a Windows Serveren futó RMS-kiszolgálóra történő alkalmazásfejlesztéshez.

| Szolgáltatás | Leírás |
|---------|-------------|
| Administration | Üzemelteti az RMS szolgáltatás kezelését lehetővé tévő felügyeleti webhelyet. A szolgáltatás legfelső szintű tanúsítási és licencelési kiszolgálókon fut. Az Active Directory Rights Management Services parancsprogram-kezelési API segítségével írhat felügyeleti parancsprogramokat.|
| Fióktanúsítás |Az RMS-tanúsítványhierarchiában lévő számítógépeket azonosító géptanúsítványokat, valamint a felhasználókat az adott számítógépekhez társító jogosultságifiók-tanúsítványokat hoz létre. További információ: Activating a Computer (Számítógép aktiválása) és Activating a User (Felhasználó aktiválása).<p><p>Ez a szolgáltatás a legfelső szintű tanúsítási kiszolgálón fut. |
|Licencek | Kibocsát egy *végfelhasználói licencszerződést*. A szolgáltatás legfelső szintű tanúsítási és licencelési kiszolgálókon fut.|
|Közzététel | Létrehoz egy *kiállítási licencet*. Ez meghatározza azokat a házirendeket, amelyek számba vehetők egy végfelhasználói licencszerződésben. További információk: [Creating an Issuance License](https://msdn.microsoft.com/library/Aa362355) (Kiállítási licenc létrehozása).<p><p>A szolgáltatás legfelső szintű tanúsítási és licencelési kiszolgálókon fut.|
|Előtanúsítás | Lehetővé teszi, hogy egy kiszolgáló egy felhasználó nevében *jogosultságifiók-tanúsítványt* (RAC) kérjen. A szolgáltatás legfelső szintű tanúsítási és licencelési kiszolgálókon fut.|
|Szolgáltatáslokátor | Biztosítja az Active Directory számára a fióktanúsítási, licencelési és közzétételi szolgáltatások URL-címét, hogy könnyen megtalálhatók legyenek az RMS-ügyfelek számára. A szolgáltatás legfelső szintű tanúsítási és licencelési kiszolgálókon fut.|

## Kapcsolódó témakörök ##
* [Áttekintés](ad-rms-overview.md)
* [Microsoft Internet Information Services](http://www.iis.net/overview)
* [A szolgáltatásalkalmazás alkalmassá tétele a felhőalapú RMS használatára](how-to-use-file-api-with-aadrm-cloud.md)
* [Microsoft Windows tartalomvédelmi szolgáltatások Service Pack 2 szervizcsomaggal](http://www.microsoft.com/download/en/details.aspx?id=4909)
* [Active Directory Rights Management Services parancsprogram-kezelési API](https://msdn.microsoft.com/library/Bb968797)
* [Activating a Computer (Számítógép aktiválása)](https://msdn.microsoft.com/library/Cc530377)
* [Activating a User (Felhasználó aktiválása)](https://msdn.microsoft.com/library/Cc530378)
* [Creating an Issuance License (Kiállítási licenc létrehozása)](https://msdn.microsoft.com/library/Aa362355)

 

 



<!--HONumber=Jun16_HO4-->


