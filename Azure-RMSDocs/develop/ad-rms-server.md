---
# required metadata

title: AD RMS-kiszolgáló | Azure RMS
description: A Rights Management Services (RMS) kiszolgáló-összetevőt számos, a Microsoft Internet Information Services szolgáltatásban futó webes szolgáltatás megvalósítja.
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 17B05780-B0EF-4805-8304-52DCDEB3AADB
# optional metadata

#ROBOTS:
audience: developer
#ms.devlang:
ms.reviewer: shubhamp
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# AD RMS-kiszolgáló

Ez a témakör az RMS-kiszolgáló célját és funkcióit ismerteti.

A Rights Management Services (RMS) kiszolgáló-összetevőt számos, a [Microsoft Internet Information Services](http://www.iis.net/overview) (IIS) szolgáltatásban futó webes szolgáltatás megvalósítja. Ezenkívül a felhőalapú megvalósítást is használhatja az Azure RMS szolgáltatásai révén. További információ az Azure Rights Management szolgáltatás használatáról: [Enable your service application to work with cloud based RMS](how-to-use-file-api-with-aadrm-cloud.md) (A szolgáltatásalkalmazás alkalmassá tétele a felhőalapú RMS használatára).

Helyszíni kiszolgálók esetén a Windows Server 2008-tól kezdődően az RMS szolgáltatást szerepkörként hozzáadva telepítheti és konfigurálhatja. A szolgáltatás ennél régebbi operációs rendszerekre való telepítéséhez töltse azt le a Microsoft letöltőközpontjából: [Microsoft Windows tartalomvédelmi szolgáltatások Service Pack 2 szervizcsomaggal](http://www.microsoft.com/download/en/details.aspx?id=4909).

A számos telepített webes szolgáltatás közül az alábbiak fontosak az alkalmazásfejlesztéshez.

**Felügyelet** – Üzemelteti az RMS szolgáltatás kezelését lehetővé tévő felügyeleti webhelyet. A szolgáltatás legfelső szintű tanúsítási és licencelési kiszolgálókon fut. Az [Active Directory Rights Management Services parancsfájlkezelési API](https://msdn.microsoft.com/library/Bb968797) segítségével írhat felügyeleti parancsfájlokat.

**Fiókazonosítás** – Az RMS-tanúsítványhierarchiában lévő számítógépeket azonosító géptanúsítványokat, valamint a felhasználókat az adott számítógépekhez társító jogosultságifiók-tanúsítványokat hoz létre. További információ: [Activating a User](https://msdn.microsoft.com/library/Cc530378) (Felhasználók aktiválása).

Ez a szolgáltatás a legfelső színtű tanúsítási kiszolgálón fut.

**Licencelés** – Egy végfelhasználói licencet ad ki, amely lehetővé teszi a végfelhasználóknak a védett tartalmak felhasználását. A szolgáltatás legfelső szintű tanúsítási és licencelési kiszolgálókon fut.

**Közzététel** – Létrehoz egy [Creating an Issuance License](https://msdn.microsoft.com/library/Aa362355) (Kiállítási licenc létrehozása). A szolgáltatás legfelső szintű tanúsítási és licencelési kiszolgálókon fut.

**Előhitelesítés** – Lehetővé teszi, hogy egy kiszolgáló egy felhasználó nevében jogosultságifiók-tanúsítványt (RAC) kérjen. Az RAC az RMS aktiválásából származó géptanúsítványok segítségével köti a felhasználói fiókokat adott számítógépekhez vagy számítógépcsoportokhoz, és lehetővé teszi, hogy a fogyasztók felhasználhassák a védett tartalmakat. A szolgáltatás legfelső szintű tanúsítási és licencelési kiszolgálókon fut.

**Szolgáltatáskereső** – Biztosítja az Active Directory számára a fióktanúsítási, a licencelési és a közzétételi szolgáltatások URL-címét, hogy azok könnyen megtalálhatók legyenek az RMS-ügyfelek számára. A szolgáltatás legfelső szintű tanúsítási és licencelési kiszolgálókon fut.

 

## Kapcsolódó témakörök ##
* [Áttekintés](ad-rms-overview.md)
* [Microsoft Internet Information Services](http://www.iis.net/overview)
* [Enable your service application to work with cloud based RMS (A szolgáltatásalkalmazás alkalmassá tétele a felhőalapú RMS használatára)](how-to-use-file-api-with-aadrm-cloud.md)
* [Microsoft Windows tartalomvédelmi szolgáltatások Service Pack 2 szervizcsomaggal](http://www.microsoft.com/download/en/details.aspx?id=4909)
* [Active Directory Rights Management Services parancsfájlkezelési API](https://msdn.microsoft.com/library/Bb968797)
* [Activating a Computer (Számítógép aktiválása)](https://msdn.microsoft.com/library/Cc530377)
* [Activating a User (Felhasználó aktiválása)](https://msdn.microsoft.com/library/Cc530378)
* [Creating an Issuance License (Kiállítási licenc létrehozása)](https://msdn.microsoft.com/library/Aa362355)

 

 


<!--HONumber=Apr16_HO4-->


