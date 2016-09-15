---
title: "Áttelepítés AD RMS-ről Azure Rights Managementre – 4. fázis | Azure RMS"
description: "Az AD RMS-ről Azure Rights Managementre (Azure RMS) történő áttelepítés 4. szakasza, benne az AD RMS-ről Azure Rights Managementre történő áttelepítés 8-9. lépése."
author: cabailey
manager: mbaldwin
ms.date: 08/17/2016
ms.topic: article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: d51e7bdd-2e5c-4304-98cc-cf2e7858557d
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ada00b6f6298e7d359c73eb38dfdac169eacb708
ms.openlocfilehash: 2f9c8d47d6b2eb719659c512ec6302c998e065a6


---

# 4. áttelepítési fázis: Áttelepítés utáni feladatok

>*A következőkre vonatkozik: Active Directory Rights Management Services, Azure Rights Management*


Az alábbi, 4. fázisra vonatkozó információk segítséget nyújtanak az AD RMS-ről az Azure Rights Managementre (Azure RMS) való áttelepítésben. Ezek az eljárások megfelelnek az [Áttelepítés AD RMS-ről Azure Rights Managementre](migrate-from-ad-rms-to-azure-rms.md) 8–9. lépésének.


## 8. lépés Az AD RMS leszerelése

Választható lehetőség: Távolítsa el a szolgáltatási csatlakozási pontot (SCP) az Active Directoryból, hogy a számítógépek ne deríthessék fel a helyszíni tartalomvédelmi infrastruktúrát. Ez a beállításjegyzékben konfigurált átirányítás miatt választható elem (például az áttelepítési parancsfájl futtatásával). A szolgáltatási csatlakozási pont eltávolításához használja a [tartalomvédelmi szolgáltatások felügyeleti eszközkészletének](http://www.microsoft.com/download/details.aspx?id=1479) AD SCP-regisztrációs eszközét.

Figyelje az AD RMS-kiszolgálók tevékenységeit, például a [rendszerállapot-jelentések kérelmei](https://technet.microsoft.com/library/ee221012%28v=ws.10%29.aspx), a [ServiceRequest-tábla](http://technet.microsoft.com/library/dd772686%28v=ws.10%29.aspx) vagy a [védett tartalmakhoz való felhasználói hozzáférések naplózása](http://social.technet.microsoft.com/wiki/contents/articles/3440.ad-rms-frequently-asked-questions-faq.aspx) segítségével. Ha meggyőződött róla, hogy az RMS-ügyfelek már nem folytatnak kommunikációt ezekkel a kiszolgálókkal, és hogy az ügyfelek sikeresen használják az Azure RMS-t, eltávolíthatja az AD RMS kiszolgálói szerepkört ezekről a kiszolgálókról. Ha dedikált kiszolgálókat használ, érdemes először elővigyázatosságból leállítani a kiszolgálókat egy időre, és meggyőződni arról, hogy nincsenek-e olyan jelentett problémák, amelyek a szolgáltatás folytonosságához a kiszolgálók újraindítását igénylik, mialatt megvizsgálja, hogy az ügyfelek miért nem használják az Azure RMS-t.

Az AD RMS-kiszolgálók leszerelése után érdemes megragadni a lehetőséget a sablonok áttekintésére a klasszikus Azure-portálon. Egyesítheti őket, hogy a felhasználók kevesebb lehetőségből választhassanak, újrakonfigurálhatja őket, sőt, új sablonokat is létrehozhat. Ez az alkalom az alapértelmezett sablonok közzétételére is megfelelő. További információ: [Configuring custom templates for Azure Rights Management](../deploy-use/configure-custom-templates.md) (Egyéni sablonok konfigurálása az Azure Rights Management szolgáltatáshoz).

## 9. lépés Kulcsismétlés végrehajtása az Azure RMS-bérlőkulcs esetében
Ez a lépés csak akkor alkalmazható, ha a Microsoft által felügyelt bérlőkulcs-topológiát választotta az ügyfél által felügyelt topológia (Azure Key Vaulttal használt BYOK) helyett.

Ez a lépés nem kötelező, de ajánlott abban az esetben, ha az Azure RMS-bérlőkulcsot a Microsoft felügyeli és az AD RMS-ből telepítette át. Ebben az esetben a kulcsismétlés végrehajtásával megvédheti az Azure RMS-bérlőkulcsot az AD RMS-kulccsal kapcsolatos lehetséges biztonsági problémáktól.

Amikor kulcsismétlést (más néven „kulcsváltást”) hajt végre az Azure RMS-bérlőkulcson, a rendszer létrehoz egy új kulcsot, és archiválja az eredetit. Mivel azonban az egyik kulcsról a másikra való áttérés nem azonnal, hanem néhány hét alatt megy végbe, ne várja meg, amíg felmerül az eredeti kulccsal kapcsolatos probléma gyanúja, hanem az áttelepítés befejezésekor egyből végezze el a kulcsismétlést az Azure RMS-bérlőkulcson.

Ha kulcsismétlést szeretne végrehajtani a Microsoft által kezelt Azure RMS-bérlőkulcson, [lépjen kapcsolatba a Microsoft támogatási szolgálatával](../get-started/information-support.md#to-contact-microsoft-support), és nyisson egy **Azure Rights Management támogatási esetet, amelyben kéri az Azure RMS-bérlőkulcs AD RMS-ből történő áttelepítése utáni kulcsismétlését**. Igazolja, hogy Ön az Azure RMS bérlői rendszergazdája. A folyamat jóváhagyása több napig is eltarthat. A szolgáltatásra a szabványos támogatási díjak vonatkoznak; a bérlői kulcs kulcsismétlése nem ingyenes szolgáltatás.


## További lépések

További információk az RMS-bérlőkulcs felügyeletével kapcsolatban: [Operations for Your Azure Rights Management Tenant Key](../deploy-use/operations-tenant-key.md) (Az Azure Rights Management bérlőkulcsával kapcsolatos műveletek).

Most, hogy befejezte az áttelepítést, tekintse át az [üzembe helyezési menetrendet](deployment-roadmap.md) a többi elvégzendő üzembe helyezési feladat beazonosítása érdekében.




<!--HONumber=Aug16_HO4-->


