---
title: "Forgatókönyv – Munkahelyi mappák konfigurálása az állandó védelemhez | Azure RMS"
description: "Ez a forgatókönyv és a kiegészítő felhasználói dokumentáció az Azure Rights Managementet használja a Munkahelyi mappákban lévő Office-dokumentumok állandó védelemmel történő ellátására. A Munkahelyi mappák szerepkör-szolgáltatást használ a Windows Server rendszert futtató fájlkiszolgálók esetében, amely egységes módon biztosít a felhasználók számára hozzáférést a munkahelyi fájlokhoz személyes számítógépükről vagy eszközükről. Bár a Munkahelyi mappák saját titkosítást alkalmaz a fájlok védelmére, ez a védelem megszűnik, ha fájlokat áthelyezik a Munkahelyi mappák környezetén kívülre."
author: cabailey
manager: mbaldwin
ms.date: 08/24/2016
ms.topic: get-started-article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 1f189345-a69e-4bf5-8a45-eb0fe5bb542b
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 024a29d7c7db2e4c0578a95c93e22f8e7a5b173e
ms.openlocfilehash: ce61f22be934ec9817a22737417514468b5c6528


---

# Forgatókönyv – Munkahelyi mappák konfigurálása az állandó védelemhez

>*A következőkre vonatkozik: Azure Rights Management, Office 365*

Ez a forgatókönyv és a kiegészítő felhasználói dokumentáció az Azure Rights Managementet használja a [Munkahelyi mappákban](https://technet.microsoft.com/library/dn265974.aspx) lévő Office-dokumentumok állandó védelemmel történő ellátására. A Munkahelyi mappák szerepkör-szolgáltatást használ a Windows Server rendszert futtató fájlkiszolgálók esetében, amely egységes módon biztosít a felhasználók számára hozzáférést a munkahelyi fájlokhoz személyes számítógépükről vagy eszközükről. Bár a Munkahelyi mappák saját titkosítást alkalmaz a fájlok védelmére, ez a védelem megszűnik, ha fájlokat áthelyezik a Munkahelyi mappák környezetén kívülre. A felhasználók például másolatot készítenek a szinkronizált fájlokról, és egy olyan tárolóra mentik, amelyet nem az Ön informatikai részlege felügyel, vagy elküldik azokat másoknak.

Az Azure Rights Management által biztosított további védelem segít megelőzni a véletlen adatvesztést a szervezeten kívüli személyek hozzáférésének megakadályozása révén. Ehhez használhatja az egyik beépített, alapértelmezett jogmegadási sablont. A forgatókönyv alkalmazása előtt viszont gondolja át, hogy nem kell-e a felhasználóknak a szervezeten kívüli személyekkel is fájlokat megosztaniuk. Ilyen eset például, amikor egy felhasználó befejezi a munkát egy árlista vázlatán, e-mailben elküldi a végleges verziót egy másik szervezethez tartozó ügyfélnek. Ha az alapértelmezett Rights Management sablont használja a Munkahelyi mappákhoz, a másik szervezethez tartozó ügyfél nem tudja majd elolvasni az e-mailben kapott dokumentumot. Úgy tud megfelelni ennek a követelménynek, ha létrehoz egy egyéni sablont, amely lehetővé teszi a felhasználók számára egy új jogosultsági házirend alkalmazását a fájlokra, amely lecseréli az összes alkalmazottra vonatkozó eredeti korlátozást az e-mailben megadott személyekre vonatkozóra.

> [!NOTE]
> A forgatókönyvben dokumentált egyéni sablon használatakor – bár a felhasználók képesek szándékosan megosztani a fájlokat a sablonban nem meghatározott személyekkel – az Azure Rights Management használatával alkalmazott további védelem számos előnnyel jár. A további védelem megakadályozza a tartalom Munkahelyi mappákon kívülre helyezéséből eredő véletlen adatvesztést, mert a tartalom védve marad az illetéktelen felhasználókkal szemben, az aktívan nem használt és a továbbított adatok esetében egyaránt. Ilyen eset például, amikor egy felhasználó elveszít egy Munkahelyi mappákat alkalmazó eszközt, az eszközt ellopják vagy nem védett infrastruktúrán keresztül szinkronizálják a rajta lévő adatokat.
> 
> Ha egy felhasználó a Rights Management megosztóalkalmazás Védett megosztás funkciójával oszt meg tartalmakat egy másik szervezethez tartozó személlyel, akkor az a felhasználó lecseréli az eredeti védelmet a saját védelmi házirendjére. Ennek eredményeképp a tartalom továbbra is védve van az illetéktelen hozzáféréstől, és csak a felhasználó által megadott személyek férhetnek hozzá.

Ezt az állandó védelmet a felhasználók Munkahelyi mappáiban lévő összes Office-dokumentumra, illetve csak a bizalmas vagy az üzletmenetet jelentősen befolyásoló adatokra is alkalmazhatja.

Az utasítások a következő körülmények között alkalmazhatók:

-   Az állandó védelemmel ellátni kívánt Munkahelyi mappák fájljai Office-fájlok. Ezek a fájlok az Azure Rights Management használatával natív védelemmel láthatók el, és nem változik meg a fájlnév-kiterjesztésük, illetve a megnyitásukhoz nincs szükség egy másik munkamenetre.

-   Állandó védelemmel szeretné ellátni a Munkahelyi mappákban lévő összes Office-fájlt vagy a Windows Server Fájlkiszolgálói erőforrás-kezelőjének Fájlbesorolási infrastruktúrájával azonosított önálló fájlokat.

-   Ha mindenképp meg kell osztani a fájlokat olyan személyekkel, akik nincsenek megadva a jogmegadási sablonban (például egy másik szervezet felhasználói), akkor a felhasználóknak egy új jogházirendet kell alkalmazniuk az eredeti jogházirend védelem helyett.

## Üzembe helyezési utasítások
![Rendszergazdai utasítások az Azure RMS gyors üzembe helyezéséhez](../media/AzRMS_AdminBanner.png)

Ellenőrizze, hogy a következő feltételek teljesülnek-e, majd kövesse a támogató eljárásokra vonatkozó utasításokat, mielőtt továbblépne a felhasználói dokumentációra.

## A forgatókönyv követelményei
Ahhoz, hogy a forgatókönyv utasításai működjenek, az alábbiaknak kell teljesülniük:

|Követelmény|Ha további információra van szüksége|
|---------------|--------------------------------|
|Az Azure Rights Management aktiválása megtörtént|[Az Azure Rights Management aktiválása](https://technet.microsoft.com/library/jj658941.aspx)|
|Szinkronizálta a helyszíni Active Directory felhasználói fiókokat az Azure Active Directory vagy az Office 365 szolgáltatással, az e-mail címeket is beleértve. Ez minden Munkahelyi mappákat használó felhasználó esetében szükséges.|[Az Azure Rights Management előkészítése](https://technet.microsoft.com/library/jj585029.aspx)|
|A következők egyike:<br /><br />– Alapértelmezett sablon használata az összes felhasználó esetében, amely nem teszi lehetővé számukra egy új jogházirend létrehozását: Nem archiválta a **&lt;szervezet neve&gt; – Bizalmas** alapértelmezett sablont.<br /><br />– Alapértelmezett sablon használata, amely lehetővé teszi a felhasználók számára egy új jogházirend létrehozását: Az egyéni sablon létrehozásához használja az alábbi utasításokat.|[Az Azure Rights Management egyéni sablonok konfigurálása](https://technet.microsoft.com/library/dn642472.aspx)|
|Megtörtént a Rights Management-összekötő telepítése, a Windows Server számítógéphez való hitelesítése és az **FCI-kiszolgálóhoz** való konfigurálása.|[Deploying the Azure Rights Management connector (Az Azure Rights Management-összekötő üzembe helyezése)](https://technet.microsoft.com/library/dn375964.aspx)|
|A Windows Microsoft Rights Management megosztóalkalmazás üzembe lett helyezve a felhasználók Windows rendszerű számítógépén.|[A Microsoft Rights Management megosztóalkalmazás automatikus központi telepítése](https://technet.microsoft.com/library/dn339003%28v=ws.10%29.aspx)|

### Az egyéni jogmegadási sablon konfigurálása, hogy a felhasználók a szervezeten kívül is megoszthassanak Munkahelyi mappák-fájlokat

1.  Jelentkezzen be a klasszikus Azure-portálra, és keresse meg az Azure Rights Management sablonokat.

2.  Másolja a **&lt;szervezet neve&gt; – Bizalmas**sablont, majd adjon meg egy nevet és egy leírást ehhez a Munkahelyi mappák forgatókönyvhöz. A következőt javasoljuk:

    -   Név: **A Munkahelyi mappák által védett tartalom**

    -   Leírás: **A tartalmat a Munkahelyi mappák látja el védelemmel, és csak a vállalat alkalmazottai férhetnek hozzá. A szervezeten kívüli személyekkel való megosztáshoz csatolja a dokumentumot egy e-mail üzenethez, és használja a Védett megosztás funkciót.**

3.  A **JOGOK** lapon:

    -   Módosítsa a meglévő **Egyéni** jogokat a következőre: **Társtulajdonos**.

4.  A **KONFIGURÁLÁS** lapon:

    -   Ellenőrizze, hogy az **ÁLLAPOT** mező **KÖZZÉTÉTEL** értékre van-e állítva

    -   A **név és leírás** esetében törölje az olyan nyelvekre vonatkozó bejegyzéseket, amelyeket nem használja. A használt nyelv esetében frissítse a **NÉV** és **LEÍRÁS** mezőket, hogy egyezzenek a sablonhoz megadott névvel és leírással az adott nyelven.

5.  Mentse a sablont.

### A Munkahelyi mappák konfigurálása az Office-fájlok állandó védelemmel történő ellátására

1.  Vezesse be a Munkahelyi mappákat a felhasználók számára, hogy a helyileg mentett fájlok szinkronizálva legyenek egy *szinkronizálási megosztás* nevű fájlkiszolgáló-mappával. A fájlkiszolgálón lévő szinkronizálási megosztás nem lehet ugyanazon a kiszolgálón, amelyen a Rights Management-összekötő fut.

    Ez a megoldás a Fájl- és tárolási szolgáltatások szerepkörhöz a Munkahelyi mappák szerepkör-szolgáltatást igényli a Kiszolgálókezelőben. A fájlkiszolgálónak legalább Windows Server 2012 R2 rendszert kell futtatnia. A fájlkiszolgáló lehet helyszíni vagy Azure virtuális gép. További információk a Munkahelyi mappákkal kapcsolatban: [A Munkahelyi mappák áttekintése](https://technet.microsoft.com/library/dn265974.aspx).

    Üzembe helyezési utasítások: [A Munkahelyi mappák központi telepítése](https://technet.microsoft.com/library/dn528861.aspx). Győződjön meg arról, hogy az Azure Rights Management titkosítással együtt használandó beépített titkosítást jelöli ki (a **Munkahelyi mappák titkosítása**). Továbbá:

    -   Az SSL-tanúsítvány kötésének létrehozásakor az IIS-ben (4. lépés): Kösse a tanúsítványt az alapértelmezett webhely https-felületéhez a netsh paranccsal (az IIS felügyeleti konzolja helyett).

    -   Ha el szeretné kerülni, hogy a felhasználók a Munkahelyi mappákra vonatkozó **Hiba történt a biztonság házirendek alkalmazásakor** telepítési hibával találkozzanak, illetve hogy a tartományhoz csatlakoztatott számítógépeiken helyi rendszergazdának kelljen lenniük, tegye a következőt: Használja a [Set-SyncShare](https://technet.microsoft.com/library/dn296649%28v=wps.630%29.aspx) parancsmagot a PasswordAutolockExcludeDomain paraméterrel, és adja meg a tartományneveket, amelyekben a számítógépek megtalálhatók (pl. contoso.com).

2.  A Rights Management-összekötő konfigurálásának befejezése:

    1.  A Fájlkiszolgálói erőforrás-kezelő használatával hozzon létre egy fájlkezelési feladatot, amely a szinkronizálási megosztás mappát azonosítja hatókörként.

    2.  Válassza az **RMS-titkosítás** műveletet, majd válasszon egy sablont:

        -   Ha nem hozott létre egyéni sablont, mert nem szeretné, hogy a felhasználók a szervezeten kívüli személyekkel osszanak meg fájlokat, válassza a **&lt;szervezet neve&gt; – Bizalmas** sablonnevet. Például: **VanArsdel, Ltd – Bizalmas**.

        -   Ha a korábbi utasítások szerint létrehozott egy egyéni sablont, válassza ki. Például: **A Munkahelyi mappák által védett tartalom**.

    3.  Olyan ütemezést adjon meg, amely bőséges időt hagy az Azure Rights Management számára az Office-fájlok titkosítására, majd adja meg a **Folyamatos futtatás új fájlokon** beállítást.

3.  A konfiguráció manuális teszteléséhez győződjön meg arról, hogy a mappa tartalmaz néhány Office-fájlt, majd használja **A fájlkezelési feladat futtatása most** beállítást és válassza a **Várakozás a feladat befejezésére** beállítást.

    Várjon, amíg bezáródik a **Fájlkezelési feladat futtatása** párbeszédpanel, majd tekintse meg az eredményeket az automatikusan megjelenő jelentésben. A kiválasztott mappában lévő fájlok számának a **Fájlok** mezőben kell megjelennie. Ellenőrizze, hogy a kiválasztott mappában lévő fájlok most már az Azure Rights Management védelme alatt állnak-e. Például nyisson meg egy fájlt, és ellenőrizze, hogy látható-e az információs szalagcím a dokumentum tetején, amely a Rights Management-sablon nevét és leírását jeleníti meg.

4.  Ha amellett döntött, hogy szelektív védelemmel látja el a fájlokat a Fájlbesorolási infrastruktúra használatával, konfigurálja a besorolási szabályt és ütemezést, majd módosítsa a fájlkezelési feladatot úgy, hogy ezt a besorolási tulajdonságot is tartalmazza, mint feltételt.

## A felhasználói dokumentáció utasításai
Ha az Azure Rights Management által védett fájlokat nem kell megosztani a szervezeten kívüli személyekkel, akkor a Munkahelyi mappák használatára vonatkozó utasításokon felül nem szükséges továbbiakat is biztosítani a felhasználók számára. Amikor a felhasználók megnyitják az Azure Rights Management és az alapértelmezett sablon által védett fájlokat, azok a szokott módon nyílnak meg az Office alkalmazásban, azzal a különbséggel, hogy a rendszer hitelesítő adatokat kérhet a felhasználóktól, illetve megjelenít egy információs sávot a dokumentum tetején, amely tájékoztatást nyújt arról, hogy a tartalom kizárólag belső használatra szánt védett adatokat tartalmaz.

Ha a forgatókönyvben leírtak szerint konfigurálta az egyéni sablont, akkor a felhasználók az információs sávon láthatják a sablon leírását: **A tartalmat a Munkahelyi mappák látja el védelemmel, és csak a vállalat alkalmazottai férhetnek hozzá. A szervezeten kívüli személyekkel való megosztáshoz csatolja a dokumentumot egy e-mail üzenethez, és használja a Védett megosztás funkciót.**. Bár a leírás összefoglalja, hogy hogyan lehet fájlokat megosztani a szervezeten kívül, a felhasználóknak valószínűleg részletesebb utasításokra lesz szükségük, különösen az első néhány alkalommal. Az utólagos forgatókönyv támogatásához használja a következőre vonatkozó rendszergazdai és végfelhasználói utasításokat: [Forgatókönyv – Office-fájl megosztása egy másik szervezet felhasználóival](scenario-share-office-file-externally.md).

> [!TIP]
> Ha úgy dönt, hogy nem használja az egyéni sablont az utasításokban, mert nem szeretné, hogy a felhasználók az informatikai csoport felügyelete nélkül osszanak meg fájlokat a szervezeten kívül, akkor ezt hozza az ügyfélszolgálat tudomására. Ezáltal, ha a megosztási kérelem valóban indokolt, akkor a vállalat szempontjából legmegfelelőbb mechanizmus használatával lehet eljárni. Egy [felügyelő](https://technet.microsoft.com/library/mt147272.aspx) például beállíthat egy olyan új sablont a tartalomhoz, amely Teljes hozzáférési jogot biztosít a kérelmező felhasználó számára, aki így már használhatja a Védett megosztás funkciót.
> 
> Ha egy idő után arra lesz figyelmes, hogy számos hasonló kérelem érkezik, akkor meghatározhat egy saját, egyéni sablont a forgatókönyvhöz, amely csak bizonyos felhasználóknak (pl. menedzserek vagy az ügyfélszolgálat) biztosítja a Társtulajdonos lehetőséget, míg az általános felhasználók a Társszerző vagy az Ön által megfelelőnek gondolt [jogokat](https://technet.microsoft.com/library/mt169423.aspx) kapják meg.




<!--HONumber=Aug16_HO4-->


