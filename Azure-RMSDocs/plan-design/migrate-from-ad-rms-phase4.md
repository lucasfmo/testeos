---
# required metadata

title: Áttelepítés AD RMS-ről Azure Rights Managementre – 4. fázis | Azure RMS
description:
keywords:
author: cabailey
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: d51e7bdd-2e5c-4304-98cc-cf2e7858557d


# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: esaggese
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# 4. áttelepítési fázis: Áttelepítés utáni feladatok

*A következőkre vonatkozik: Active Directory Rights Management Services, Azure Rights Management*


Az alábbi, 4. fázisra vonatkozó információk segítséget nyújtanak az AD RMS-ről az Azure Rights Managementre (Azure RMS) való áttelepítésben. Ezek az eljárások megfelelnek az [Áttelepítés AD RMS-ről Azure Rights Managementre](migrate-from-ad-rms-to-azure-rms.md) 8–9. lépésének..


## 8. lépés Az AD RMS leszerelése

Választható lehetőség: Távolítsa el a szolgáltatási csatlakozási pontot (SCP) az Active Directoryból, hogy a számítógépek ne deríthessék fel a helyszíni tartalomvédelmi infrastruktúrát. Ez a beállításjegyzékben konfigurált átirányítás miatt választható elem (például az áttelepítési parancsfájl futtatásával). A szolgáltatási csatlakozási pont eltávolításához használja a [tartalomvédelmi szolgáltatások felügyeleti eszközkészletének](http://www.microsoft.com/download/details.aspx?id=1479) AD SCP-regisztrációs eszközét..

Figyelje az AD RMS-kiszolgálók tevékenységeit, például a [rendszerállapot-jelentések kérelmei](https://technet.microsoft.com/library/ee221012%28v=ws.10%29.aspx), a [ServiceRequest-tábla](http://technet.microsoft.com/library/dd772686%28v=ws.10%29.aspx) vagy a [védett tartalmakhoz való felhasználói hozzáférések naplózása](http://social.technet.microsoft.com/wiki/contents/articles/3440.ad-rms-frequently-asked-questions-faq.aspx) segítségével. Ha meggyőződött róla, hogy az RMS-ügyfelek már nem folytatnak kommunikációt ezekkel a kiszolgálókkal, és hogy az ügyfelek sikeresen használják az Azure RMS-t, eltávolíthatja az AD RMS kiszolgálói szerepkört ezekről a kiszolgálókról. Ha dedikált kiszolgálókat használ, érdemes először elővigyázatosságból leállítani a kiszolgálókat egy időre, és meggyőződni arról, hogy nincsenek-e olyan jelentett problémák, amelyek a szolgáltatás folytonosságához a kiszolgálók újraindítását igénylik, mialatt megvizsgálja, hogy az ügyfelek miért nem használják az Azure RMS-t.

Az AD RMS-kiszolgálók leszerelése után érdemes megragadni a lehetőséget a sablonok áttekintésére a klasszikus Azure-portálon. Egyesítheti őket, hogy a felhasználók kevesebb lehetőségből választhassanak, újrakonfigurálhatja őket, sőt, új sablonokat is létrehozhat. Ez az alkalom az alapértelmezett sablonok közzétételére is megfelelő. További információ: [Configuring custom templates for Azure Rights Management](../deploy-use/configure-custom-templates.md) (Egyéni sablonok konfigurálása az Azure Rights Management szolgáltatáshoz).

## 9. lépés Kulcsismétlés végrehajtása az Azure RMS-bérlőkulcs esetében
Erre a lépésre akkor van szükség az áttelepítés befejezésekor, ha az AD RMS üzembe helyezése 1. RMS-titkosítási módban történt, mivel a kulcsismétlés egy 2. RMS-titkosítási módot használó új bérlőkulcsot hoz létre. Az Azure RMS 1. titkosítási móddal történő használata csak az áttelepítési folyamat alatt támogatott.

Ez a lépés ugyan választható, de akkor is ajánlott az áttelepítés befejezésekor, ha a futtatást 2. RMS-titkosítási módban végezte, mert ez hozzájárul az Azure RMS-bérlőkulcs védelméhez az AD RMS-kulccsal kapcsolatos esetleges biztonsági problémák esetén. Amikor kulcsismétlést (más néven „kulcsváltást”) hajt végre az Azure RMS-bérlőkulcson, a rendszer létrehoz egy új kulcsot, és archiválja az eredetit. Mivel azonban az egyik kulcsról a másikra való áttérés nem azonnal, hanem néhány hét alatt megy végbe, ne várja meg, amíg felmerül az eredeti kulccsal kapcsolatos probléma gyanúja, hanem az áttelepítés befejezésekor egyből végezze el a kulcsismétlést az RMS-bérlőkulcson.

Kulcsismétlés végrehajtása az Azure RMS-bérlőkulcs esetében:

-   Ha a Microsoft által felügyelt RMS-bérlőkulccsal rendelkezik: hívja fel a Microsoft ügyfél-támogatási szolgálatát (CSS), és igazolja, hogy Ön az RMS-bérlői rendszergazda.

-   Ha saját maga által felügyelt RMS-bérlőkulccsal (BYOK) rendelkezik: a BYOK-eljárás megismétlésével állítson elő és hozzon létre egy új kulcsot az interneten vagy személyesen.

További információk az RMS-bérlőkulcs felügyeletével kapcsolatban: [Operations for Your Azure Rights Management Tenant Key](../deploy-use/operations-tenant-key.md) (Az Azure Rights Management bérlőkulcsával kapcsolatos műveletek)..

## További lépések

Most, hogy befejezte az áttelepítést, tekintse át az [üzembe helyezési menetrendet](deployment-roadmap.md) a többi elvégzendő üzembe helyezési feladat beazonosítása érdekében.



<!--HONumber=Apr16_HO4-->


