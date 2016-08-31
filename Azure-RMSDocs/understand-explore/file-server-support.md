---
title: "File servers that run Windows Server and use File Classification Infrastructure (FCI) (A Windows Server rendszert futtató és a fájlbesorolási infrastruktúrát (FCI) használó fájlkiszolgálók) | Azure RMS"
description: "Amikor konfigurálja a Windows Server rendszert a fájlbesorolási infrastruktúra használatára, ez a Fájlkiszolgálói erőforrás-kezelő funkció képes megvizsgálni a helyi fájlokat, és meghatározni, hogy tartalmaznak-e azok érzékeny adatokat. Az ezen feltételeknek megfelelő fájlokat a rendszergazda által meghatározott besorolási tulajdonságoknak megfelelő címkékkel látja el a program. Ezek után a fájlbesorolási infrastruktúra automatikus műveleteket végez a besorolásnak megfelelően. Az egyik ilyen művelet az információvédelem biztosítása az Azure Rights Management használatával, és a Rights Management-összekötő (más néven RMS-összekötő) üzembe helyezése. Ezek után az Azure RMS automatikusan védelmet biztosít az Office-fájlok számára."
author: cabailey
manager: mbaldwin
ms.date: 08/24/2016
ms.topic: article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 8fdad425-5daf-4ce1-822f-9d2fb0b87df1
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 024a29d7c7db2e4c0578a95c93e22f8e7a5b173e
ms.openlocfilehash: 3ba4230674d387c100752f2e8698010afc8773b2


---


# File servers that run Windows Server and use File Classification Infrastructure (FCI) (A Windows Server rendszert futtató és a fájlbesorolási infrastruktúrát (FCI) használó fájlkiszolgálók)

>*A következőkre vonatkozik: Azure Rights Management, Office 365*


Amikor konfigurálja a Windows Server rendszert a fájlbesorolási infrastruktúra használatára, ez a Fájlkiszolgálói erőforrás-kezelő funkció képes megvizsgálni a helyi fájlokat, és meghatározni, hogy tartalmaznak-e azok érzékeny adatokat. Az ezen feltételeknek megfelelő fájlokat a rendszergazda által meghatározott besorolási tulajdonságoknak megfelelő címkékkel látja el a program. Ezek után a fájlbesorolási infrastruktúra automatikus műveleteket végez a besorolásnak megfelelően. Az egyik ilyen művelet az információvédelem biztosítása az [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] használatával, és a Rights Management-összekötő (más néven RMS-összekötő) üzembe helyezése. Ezek után az Azure RMS automatikusan védelmet biztosít az Office-fájlok számára.

Az összes fájltípus védelméhez ne az RMS-összekötőt használja, hanem futtasson egy, az [RMS Protection eszköz](https://www.microsoft.com/en-us/download/details.aspx?id=47256) parancsmagjait használó Windows PowerShell-parancsprogramot.

A besorolási házirendek teljes mértékben konfigurálhatók és nagy mértékben bővíthetők, így megelőzheti a jogosulatlan és a jogosult felhasználók által okozott esetleges adatszivárgást. Még a hálózati rendszergazdák által okozott adatszivárgás kockázatának csökkentésében is segíthet, mivel olyan házirendeket állíthat be, amelyek nem igénylik a rendszergazdák hozzáférését a fájlokhoz.

Az Office-fájlokhoz tartozó RMS-összekötő üzembe helyezésével és konfigurációjával kapcsolatos utasításokért lásd: [Az Azure Rights Management-összekötő telepítése](../deploy-use/deploy-rms-connector.md).

Útmutatás a Windows PowerShell-parancsprogram használatáról az összes fájltípushoz: [RMS-védelem és Windows Server fájlbesorolási infrastruktúra &#40;FCI&#41;](../rms-client/configure-fci.md).



## További lépések
Most, hogy már érti, hogyan támogatják az alkalmazások és a szolgáltatások az Azure RMS szolgáltatást, talán érdekelheti az Azure RMS és a Rights Management helyszíni verziójának, az Active Directory tartalomvédelmi szolgáltatásoknak (AD RMS) az összehasonlítása. A funkciók, követelmények és biztonsági vezérlők összehasonlításával kapcsolatban lásd: [Az Azure Rights Management és az AD RMS összehasonlítása](compare-azure-rms-ad-rms.md).





<!--HONumber=Aug16_HO4-->


