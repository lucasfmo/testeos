---
title: "Forgatókönyv – A legértékesebb fájlok védelmének biztosítása | Azure RMS"
description: 
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 05/20/2016
ms.topic: get-started-article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 95f1844a-612c-4e67-bbe6-4b6b92295221
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 332e102cb27854314b93a71bfeae82a95c9a7812
ms.openlocfilehash: d4325fb8a0b27d0a8d4fd7451b9d11d10153ed8d


---

# Forgatókönyv – A legértékesebb fájlok védelmének biztosítása

*A következőkre vonatkozik: Azure Rights Management, Office 365*

Ez a forgatókönyv és támogatási felhasználói dokumentáció az Azure Rights Management használatával manuális és egyéni, a jogosulatlan hozzáférések elleni legmagasabb szintű védelmet valósít meg a legértékesebbeknek minősített fájlok számára. Ezek általában olyan fájlok, amelyekhez csak néhány személy férhet hozzá. A fájlok például a vállalat legfontosabb élelmiszertermékének receptjét vagy olyan felvásárlási terveket tartalmazhatnak, amelyek nem hozhatók nyilvánosságra egy adott időpont előtt.

Az utasítások a következő körülmények között alkalmazhatók:

-   Azonosította a védelemmel ellátni kívánt fájlokat.

-   A fájlok a Rights Management szolgáltatást támogató Office-fájlformátumuk valamelyikét használják. Ha a fájlok formátuma ettől eltérő (például CAD-fájlok), győződjön meg róla, hogy ezek a formátumok támogatják az Azure RMS szolgáltatást, illetve olyan alkalmazásokat helyezett üzembe, amelyek natív módon támogatják az Azure RMS szolgáltatást. További információ: [Hogyan támogatják a különböző alkalmazások az Azure Rights Managementet?](https://technet.microsoft.com/library/jj585004.aspx).

-   A fájlok szigorúan bizalmas, kényes információt tartalmaznak, amelyhez csak néhány személy férhet hozzá.

-   Az internetkapcsolat megkövetelése a fájlokhoz való egyes hozzáférések engedélyezéséhez elfogadható kompromisszum ezen személyek számára, mert ez a követelmény nagyobb biztonsággal jár.

-   Ezen személyekkel szemben nem követelmény az információk további megosztása másokkal, azonban módosíthatják az információkat és menthetik a módosításokat.

-   A rendszergazdának képesnek kell lennie annak nyomon követésére, hogy ki és mikor fér hozzá a fájlokhoz, illetve szükség esetén vissza kell tudnia vonnia a hozzáférést.

## Üzembe helyezési utasítások
![Rendszergazdai utasítások az Azure RMS gyors üzembe helyezéséhez](../media/AzRMS_AdminBanner.png)

Ellenőrizze, hogy a következő feltételek teljesülnek-e, majd kövesse a támogató eljárásokra vonatkozó utasításokat, mielőtt továbblépne a felhasználói dokumentációra.

## A forgatókönyv követelményei
Ehhez a forgatókönyvhöz az alábbiaknak kell teljesülniük:

|Követelmény|Ha további információra van szüksége|
|---------------|--------------------------------|
|Előkészítette a fiókokat és a csoportokat az Office 365 vagy az Azure Active Directory számára:<br /><br />– Az **Emelt szintű hozzáférés** nevű levelezési csoport, amely azt a néhány személyt tartalmazza, akik hozzáférhetnek a szigorúan bizalmas dokumentumokhoz.<br /><br />– Az **Informatikai megfelelőségi kezelők** nevű levelezési csoport, amely az elektronikus felderítés, figyelés és naplózás feladatokkal megbízott személyeket tartalmazza.<br /><br />– Az **RMS-rendszergazdák** nevű levelezési csoport, amelynek az Azure RMS konfigurálását végző összes rendszergazda a tagja.|[Az Azure Rights Management előkészítése](https://technet.microsoft.com/library/jj585029.aspx)|
|Az Azure Rights Management aktiválása megtörtént|[Az Azure Rights Management aktiválása](https://technet.microsoft.com/library/jj658941.aspx)|
|Konfigurált egy egyéni sablont az alábbiakban leírtak alapján.|[Az Azure Rights Management egyéni sablonok konfigurálása](https://technet.microsoft.com/library/dn642472.aspx)|
|A Rights Management megosztóalkalmazás üzembe lett helyezve a Windows rendszerű számítógépen, így helyben láthatja el védelemmel a fájlokat az alábbi szakaszban leírt módon.|[A Rights Management megosztóalkalmazás letöltése és telepítése](https://technet.microsoft.com/library/dn574734%28v=ws.10%29.aspx)|
|Az engedéllyel rendelkező felhasználók legalább az Office 2013-mal rendelkeznek.|Ha a felhasználók az Office 2010-zel rendelkeznek, telepíteniük kell a Rights Management megosztóalkalmazást is.|
|Az Azure RMS-előfizetés tartalmazza a dokumentumok nyomon követését biztosító szolgáltatást.|Ha Azure RMS-előfizetés nem tartalmazza a dokumentumok nyomon követését biztosító szolgáltatást, nem fogja tudni használni a dokumentumok nyomon követésére szolgáló oldalt, amelyen megtekintheti, ki fér hozzá ezen dokumentumokhoz, illetve szükség esetén visszavonhatja a hozzáférést. Ebben az esetben olyan előfizetést kell vásárolnia, amely tartalmazza a dokumentumok nyomon követését biztosító szolgáltatást, vagy el kell fogadnia ezt a korlátozást. Érdemes megfontolnia az Azure RMS [használatnaplózási](https://technet.microsoft.com/library/dn529121.aspx) képességeinek használatát, amelyek például információkat biztosítanak azzal kapcsolatban, hogy ki és mikor fért hozzá az egyes fájlokhoz, ami segítséget nyújt a potenciálisan gyanús viselkedés észleléséhez.<br /><br />Az előfizetéssel járó támogatás ellenőrzése: [Comparison of Rights Management Services (RMS) Offerings](https://technet.microsoft.com/dn858608) (A Tartalomvédelmi szolgáltatásokra (RMS) vonatkozó ajánlatok összehasonlítása).|

### Az egyéni sablon konfigurálása

1.  Hozzon létre egy új egyéni sablon az Azure Rights Management szolgáltatásban a klasszikus Azure-portálon az alábbi értékekkel és beállításokkal:

    -   Név: **Emelt szintű hozzáférés**

    -   Jogosultságok: Biztosítson a **Emelt szintű hozzáférés** levelezési csoportnak **Társszerző** jogosultságokat.

    -   Hatókör: Jelölje ki a **Emelt szintű hozzáférés** levelezési csoportot, az **Informatikai megfelelőségi kezelők** levelezési csoportot és az **RMS-rendszergazdák** levelezési csoportot.

    -   Offline hozzáférés: **A tartalom csak internetkapcsolat esetén érhető el**.

2.  Tegye közzé az új sablont.

### A fájlok védelemmel helyben történő ellátása

1.  A Fájlkezelőben lépjen a védelemmel ellátni kívánt fájlokat tartalmazó első mappára:

    -   Ha a mappában található összes fájlt védelemmel kívánja ellátni, jelölje ki a mappát.

    -   Ha csak néhány fájlt kíván védelemmel ellátni a mappában, jelölje ki védeni kívánt fájlokat.

2.  Kattintson a jobb gombbal, válassza a **Védelem az RMS-sel**, majd a **Helyi védelem** menüpontot.

3.  Válassza ki a **Emelt szintű hozzáférés** csoportot.

4.  Előfordulhat, hogy az alkalmazás kéri a hitelesítő adatok megadását. Várja meg a fájlok védelemmel való ellátását, majd kattintson a **Bezárás** elemre, ha megjelenik a **fájlok védelemmel való ellátását megerősítő** lap.

5.  Ha más mappákban további fájlokat kíván védelemmel ellátni, ismételje meg az 1–4. lépést minden mappára vonatkozóan.

További információ a fájlok helyi védelmével kapcsolatban: [Protect a file on a device (protect in-place) by using the Rights Management sharing application](https://technet.microsoft.com/library/dn574733%28v=ws.10%29.aspx) (Fájlok védelemmel ellátása az eszközökön (helyi védelem) a Rights Management megosztóalkalmazás használatával).

> [!TIP]
> Ha túl sok a védelemmel ellátni kívánt fájl ehhez a manuális eljáráshoz, fontolja meg az [RMS Protection eszköz](https://www.microsoft.com/en-us/download/details.aspx?id=47256) használatát a fájlok tömeges védelemmel való ellátásához a sablon segítségével.

### A fájlokhoz való hozzáférés figyelés és a hozzáférés visszavonása szükség esetén

1.  A Fájlkezelőben kattintson a jobb gombbal a védett fájlra, válassza a **Védelem az RMS-sel**, majd a **Használat követése** menüpontot.

2.  Ha a rendszer felszólítja, jelentkezzen be a dokumentumok nyomon követését biztosító webhely eléréséhez.

3.  Ellenőrizze, ki fért hozzá a fájlhoz és a többi védett fájlhoz, különös figyelmet fordítva a sikertelen próbálkozásokra, mert azok gyanús viselkedésre utalhatnak. Ha szükségesnek tartja, visszavonhatja a hozzáférést az egyes fájlok tekintetében.

## A felhasználói dokumentáció utasításai
Nincs a felhasználóknak adható konkrét utasítás ezzel a forgatókönyvvel kapcsolatban, mert a fájlok nem igényelnek különösebb felhasználói műveleteket. A fájlok védelmét Ön valósította meg, és azok figyelésének feladata is Önre hárul. Érdemes azonban tájékoztatnia a felhasználókat és támogatási csatornáit arról, hogy mely fájlok védettek, illetve hogyan korlátozhatja ez a dokumentumok használatát. Ha például egy engedéllyel rendelkező felhasználó nem rendelkezik internetkapcsolattal, nem lesz képes megnyitni a fájlt.

Az alábbi sablont használva másolja és illessze be a bejelentést a végfelhasználóknak szóló üzenetbe, és hajtsa végre ezeket a módosításokat:

1.  Adja meg a fájlok tényleges nevét, vagy használjon egyértelmű hivatkozást, amelyet megértenek az engedéllyel rendelkező felhasználók.

2.  Cserélje le a *&lt;kapcsolattartás adatait&gt;* azokra az utasításokra, amelyeket követve ezek a felhasználók elérhetik az ügyfélszolgálatot vagy az informatikai részleget egy olyan felsőbb szintű támogatási csatornán keresztül, amely megfelel ezen dokumentumok fontosságának. Adjon meg például egy éjjel-nappal hívható telefonszámot a nagy fontosságú támogatási hívások számára.

3.  Hajtsa végre a bejelentés további kívánt módosításait, majd küldje el a felhasználóknak.

A példadokumentációban látható, hogyan jelenik meg a bejelentés a felhasználók számára a testre szabást követően.

![Felhasználói dokumentációs sablon az Azure RMS gyors üzembe helyezéséhez](../media/AzRMS_UsersBanner.png)

### Informatikai bejelentés: A &lt;szervezet neve&gt; szigorúan bizalmas dokumentumainak védelme
Az alábbi fájlokat nagyon magas szintű védelemmel látták el, ezért csak &lt;korlátozott felhasználók&gt; férhetnek hozzá a fájlokhoz és módosíthatják azokat. A jogosulatlan hozzáférés elkerülése érdekében, az alkalmazása automatikusan kérni fogja az engedélyezést minden egyes alkalommal, amikor megnyitja ezeket a fájlokat, ezért mostantól internetkapcsolattal kell rendelkezni a fájlok eléréséhez, illetve a rendszer kérheti hitelesítő adatait:

-   &lt;1. szigorúan bizalmas dokumentum, típus vagy hely&gt;

-   &lt;2. szigorúan bizalmas dokumentum, típus vagy hely&gt;

-   &lt;3. szigorúan bizalmas dokumentum, típus vagy hely&gt;

**Segítségre van szüksége?**

-   Ha nem fér hozzá ezekhez a fájlokhoz vagy gyanús módosításokat észlel bennük, &lt;művelet és kapcsolattartási adatok&gt;.

#### Példa testre szabott felhasználói dokumentációra
![Példa felhasználói dokumentációra az Azure RMS gyors üzembe helyezéséhez](../media/AzRMS_ExampleBanner.png)

##### Informatikai bejelentés: A VanArsdel szigorúan bizalmas dokumentumainak védelme
Az alábbi fájlokat nagyon magas szintű védelemmel látták el, ezért csak a jelen e-mail címzett sorában szereplő felhasználók férhetnek hozzá a fájlokhoz és módosíthatják azokat. A jogosulatlan hozzáférés elkerülése érdekében, az alkalmazások automatikusan kérni fogják az engedélyezést minden egyes alkalommal, amikor megnyitja ezeket a fájlokat, ezért mostantól internetkapcsolattal kell rendelkezni a fájlok eléréséhez, illetve a rendszer kérheti hitelesítő adatait:

-   A „Merkúr” kódnév tervspecifikációi

-   A „Jupiter” kódnév tervspecifikációi

-   A „Szaturnusz” kódnév tervspecifikációi

-   A „Neptunusz” kódnév tervspecifikációi

**Segítségre van szüksége?**

-   Ha nem fér hozzá ezekhez a fájlokhoz vagy gyanús módosításokat észlel bennük, hívja az informatikai részleg által védett e-mail üzenetben küldött, éjjel-nappal elérhető, támogatáskérési vonalat.




<!--HONumber=Jun16_HO4-->


