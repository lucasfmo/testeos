---
title: "RMS egyéni felhasználók számára létrehozott szolgáltatásfiókok rendszergazdai felügyelete | Azure RMS"
description: "Ha nem szeretné a szervezeténél levő RMS egyéni felhasználók számára előfizetést fizetős előfizetéssé alakítani, akkor az alábbi módokon felügyelheti az Azure Active Directoryban levő felhasználói fiókokat, amelyeket a szervezeténél hoztak létre."
author: cabailey
manager: mbaldwin
ms.date: 08/24/2016
ms.topic: article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: a83880d0-f0f9-4a32-9e00-2f6635d7cc8d
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 43429b44c019144744f39a1f92f144d315c2024c
ms.openlocfilehash: eb86c9e4f83fcf42599145b10ad8f021e40c208f


---



# How administrators can control the accounts created for RMS for individuals (RMS egyéni felhasználók számára szolgáltatásfiókok rendszergazdai felügyelete)

>*A következőkre vonatkozik: Azure Rights Management*


Ha nem szeretné a szervezeténél levő RMS egyéni felhasználók számára előfizetést fizetős előfizetéssé alakítani, akkor az alábbi módokon felügyelheti az Azure címtárban levő felhasználói fiókokat, amelyeket a szervezeténél hoztak létre:

-   Implementálhat címtár-integrációs megoldásokat az Azure Active Directoryhoz és az Active Directory tartományi szolgáltatásokhoz. Szinkronizálhatja a fiókokat és a jelszavakat, hogy a felhasználóknak ne kelljen új fiókokat létrehoznia a Rights Management használatához, és a helyszíni jelszóházirendek vonatkoznak az új Azure felhasználói fiókokra is. A jelszavakat is szinkronizálhatja, hogy a felhasználóknak ne kelljen új jelszót megjegyezniük a Rights Management használatához.

-   Megakadályozhatja, hogy a felhasználók regisztráljanak az Azure Rights Management RMS egyéni felhasználók számára előfizetéssel való használatára. A legtöbb esetben ebből nem származik sok előnye, mert a felhasználók vagy védelem nélkül osztják meg a fájlokat (ez pedig kockázatot jelenthet a vállalat számára), vagy másféle védelmi mechanizmust alkalmaznak, amely nem biztosítja az informatikai részleg számára az adatok elérésének lehetőségét. Ha viszont meg szeretné akadályozni, hogy a felhasználók regisztráljanak az RMS egyéni felhasználók számára szolgáltatás használatára, tegye az alábbiak egyikét, miután saját tulajdonba vette a szervezete címtárát az Azure szolgáltatásban:

    -   Megakadályozhatja, hogy a felhasználók regisztráljanak önkiszolgáló előfizetésekre (ilyen pl. az RMS egyéni felhasználók számára).  Jelenleg ezt nem állíthatja be szolgáltatás szerint; a beállítás vonatkozik az összes Azure-előfizetésre, amely önkiszolgáló folyamatokat használ. Ehhez állítsa az **AllowAdHocSubscriptions** paramétert hamisra az Azure Active Directory Windows PowerShell-moduljának [Set-MsolCompanySettings](http://technet.microsoft.com/library/dn194127.aspx) parancsmagjával. Például: **Set-MsolCompanySettings -AllowAdHocSubscriptions $false**

    -   Megakadályozhatja, hogy a felhasználók létrehozzanak egy új fiókot az Azure szolgáltatásban, azaz csak azok a felhasználók iratkozhatnak fel önkiszolgáló előfizetésekre (mint például az RMS egyéni felhasználók számára), akiknek már van Azure-fiókjuk.  Ehhez állítsa az **AllowEmailVerifiedUsers** paramétert hamisra az Azure Active Directory Windows PowerShell-moduljának [Set-MsolCompanySettings](http://technet.microsoft.com/library/dn194127.aspx) parancsmagjával. Például: **Set-MsolCompanySettings -AllowEmailVerifiedUsers $false -AllowAdHocSubscriptions $true**

    -   Szinkronizálhatja az Active Directory tartományi szolgáltatások infrastruktúrát Azure Active Directory címtárral. Ezzel a művelettel megakadályozhatja, hogy új fiókok jöjjenek létre, amikor a felhasználók önkiszolgáló előfizetésekre (pl. RMS egyéni felhasználók számára) regisztrálnak, és törölheti vagy letilthatja az Azure címtárban korábban létrehozott fiókokat.

Az Azure címtár felhasználói fiókjainak kezeléséhez, vagy a felhasználók RMS egyéni felhasználók számára szolgáltatásra való regisztrációjának megakadályozásához rendelkeznie kell egy Azure-előfizetéssel, és a címtár tulajdonosának kell lennie. Ha még nem rendelkezik Azure előfizetéssel, hozzájuthat díjmentesen. Ha automatikusan kapott egy címtárat az önkiszolgáló folyamat során, vegye saját tulajdonba a létrehozásához használt tartományt. Ha már van egy címtára az Azure szolgáltatásban, de a felhasználók megadtak egy új, a szervezetében használt tartományt, egyesítse azt a tartományt a meglévő címtárával. További információkat a [Mi az Azure Önkiszolgáló regisztráció?](https://azure.microsoft.com/documentation/articles/active-directory-self-service-signup/) című cikkben talál


## További lépések

Ha a felhasználók létre tudják hozni a rendszergazdák helyett a fiókjaikat a RMS egyéni felhasználók számára regisztrációhoz az Azure Active Directory címtárban, hogyan tudhatja meg, hogy elvégezték-e a feladatot?  Lásd: [Annak ellenőrzése, hogy a felhasználók regisztráltak-e az egyéni felhasználók számára készült RMS szolgáltatásra](rms-for-individuals-identify-sign-up.md).



<!--HONumber=Aug16_HO4-->


