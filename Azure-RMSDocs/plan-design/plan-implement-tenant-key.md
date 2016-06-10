---
# required metadata

title: Az Azure Rights Management-bérlőkulcs tervezése és megvalósítása | Azure RMS
description:
keywords:
author: cabailey
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: f0d33c5f-a6a6-44a1-bdec-5be1bc8e1e14

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: esaggese
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Planning and implementing your Azure Rights Management tenant key (Az Azure Rights Management-bérlőkulcs tervezése és megvalósítása)

*A következőkre vonatkozik: Azure Rights Management, Office 365*

A jelen cikkben található információk segítségével megtervezheti és kezelheti a tartalomvédelmi szolgáltatásbeli (RMS-) bérlőkulcsát az Azure RMS szolgáltatáshoz. Például ahelyett, hogy a Microsoft felügyelné a bérlőkulcsát (alapértelmezett beállítás), Ön is felügyelheti a saját bérlőkulcsát, hogy az megfeleljen a szervezetére vonatkozó speciális szabályozásoknak.  A saját bérlőkulcs felügyelete más néven a saját kulcs használata (BYOK).

> [!NOTE]
> Az RMS-bérlőkulcsot más néven kiszolgálólicenc-tanúsítványnak (SLC-kulcsnak) is nevezzük. Az Azure RMS minden, az Azure RMS szolgáltatásra előfizető szervezet számára fenntart egy vagy több kulcsot. Ha a szervezetben valamilyen kulcsot használnak az RMS-hez (felhasználói kulcs, számítógépkulcs, dokumentumtitkosítási kulcs), az titkosítási lánccal kapcsolódik az RMS-bérlőkulcshoz.

**Áttekintés:** A következő táblázat segít kiválasztani az Ön számára ajánlott bérlőkulcs-topológiát. További információt a további dokumentációkban talál.

Ha az Azure RMS-t egy, a Microsoft által felügyelt bérlőkulccsal telepíti, később bármikor BYOK-ra válthat. Azonban jelenleg nem lehetséges a BYOK módszerről a Microsoft általi felügyeletre állítani az Azure RMS-bérlőkulcsokat.

|Üzleti követelmény|Ajánlott bérlőkulcs-topológia|
|------------------------|-----------------------------------|
|Az Azure RMS telepítése gyorsan, anélkül, hogy speciális hardverre lenne szükség|Microsoft által felügyelt|
|Teljes körű IRM-funkciókra van szükség az Exchange Online-ban az Azure RMS mellett|Microsoft által felügyelt|
|A kulcsok saját kezű létrehozása és védelmük biztosítása egy hardveres biztonsági modulban (HSM)|BYOK<br /><br />Ez a konfiguráció jelenleg korlátozott IRM-funkciókat eredményez az Exchange Online-ban. További információk: [A BYOK díjszabása és korlátozásai](byok-price-restrictions.md).|

## A bérlőkulcs-topológia kiválasztása: a Microsoft által felügyelt (alapértelmezés) vagy saját felügyeletű (BYOK)
Döntse el, melyik bérlőkulcs-topológia a legjobb az Ön szervezete számára. Alapértelmezés szerint az Azure RMS hozza létre a bérlőkulcsot és felügyeli a bérlőkulcs-életciklus legtöbb területét. Ez a legegyszerűbb lehetőség, amely a legkisebb adminisztratív teherrel jár. A legtöbb esetben Önnek nem is kell róla tudnia, hogy rendelkezik bérlőkulccsal. Egyszerűen csak regisztrál az Azure RMS-re, a kulcskezelési folyamat fennmaradó részét pedig a Microsoft elintézi.

Alternatív megoldásként teljes körű felügyeletet is gyakorolhat a bérlőkulcsa fölött, beleértve a bérlőkulcs létrehozását és a fő példány tárolását a helyszínen. Ez a forgatókönyv más néven a saját kulcs használata (BYOK). Ha ezt választja, a következők történnek:

1.  Létrehozza a saját bérlőkulcsát a helyszínen, a saját informatikai házirendjeinek megfelelően.

2.  A bérlőkulcsot biztonságos módon továbbítja a saját tulajdonában lévő hardveres biztonsági modulról (HSM) a Microsoft által birtokolt és felügyelt HSM-ekre. A folyamat során a bérlőkulcs soha nem kerül a hardveres védelem határain kívülre.

3.  Amikor elküldi a bérlőkulcsot a Microsoftnak, annak védelmét Thales HSM-ek biztosítják. A Microsoft és a Thales együttműködése biztosítja, hogy az Ön bérlőkulcsát ne lehessen kinyerni a Microsoft HSM-jeiről.

Választható lehetőségként az Azure RMS közel valós idejű használati naplóiban nyomon követheti a bérlőkulcsa használatának pontos módját és idejét.

> [!NOTE]
> További védelmi intézkedésként az Azure RMS különböző biztonsági világot használ az Észak-Amerikában, az EMEA (Európa, a Közel-Kelet és Afrika) régióban, illetve az Ázsiában található adatközpontjaihoz. A saját felügyeletű bérlőkulcsok annak a régiónak a biztonsági világához vannak kötve, amelyben az RMS-bérlő regisztrálva lett. Például egy európai ügyfél bérlőkulcsát nem lehet észak-amerikai vagy ázsiai adatközpontokban felhasználni.

## A bérlőkulcsok életciklusa
Ha úgy dönt, hogy a bérlőkulcsát a Microsoft felügyeli, a Microsoft a kulcs életciklusához kapcsolódó legtöbb műveletet elvégzi. Ha azonban Ön felügyeli a saját bérlőkulcsát, az Ön felelőssége lesz számos, a kulcs életciklusához kapcsolódó művelet, valamint néhány további eljárás elvégzése.

Az alábbi ábrák bemutatják és összehasonlítják a két lehetőséget. Az első ábra azt mutatja, milyen kicsi adminisztratív teher hárul Önre az alapértelmezett beállítás szerint, amikor a bérlőkulcsot a Microsoft felügyeli.

![Azure RMS-bérlőkulcs életciklusa – a Microsoft felügyeli, ez az alapértelmezett beállítás](../media/RMS_BYOK_cloud.png)

A második ábra azt mutatja, milyen további lépések szükségesek abban az esetben, ha a bérlőkulcsot Ön felügyeli.

![Azure RMS-bérlőkulcs életciklusa – a felhasználó felügyeli, saját kulcs használata](../media/RMS_BYOK_onprem.png)

Ha úgy dönt, hogy a bérlőkulcsát a Microsoft felügyelje, a kulcs létrehozásához semmilyen további műveletet nem kell elvégeznie, és rögtön a [További lépések](plan-implement-tenant-key.md#next-steps) című szakasszal folytathatja..

Ha úgy dönt, hogy a bérlőkulcsot Ön felügyeli, további információkért olvassa el a következő szakaszokat.

## Az Azure Rights Management-bérlőkulcs megvalósítása

Az ebben a szakaszban található információkat és eljárásokat akkor használhatja, ha a bérlőkulcs saját kezű létrehozása és felügyelete, azaz a BYOK forgatókönyv mellett döntött:


> [!IMPORTANT]
> Ha már használatba vette az [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] szolgáltatást (vagyis az aktiválva van) és egyes felhasználói az Office 2010-et használják, a következő eljárások futtatása előtt lépjen kapcsolatba a Microsoft ügyféltámogatási szolgálatával (CSS). A forgatókönyvtől és a követelményektől függően így is használhatja a BYOK-t, de csak bizonyos korlátozásokkal vagy további lépések végrehajtása után.
> 
> Akkor is vegye fel a kapcsolatos a CSS-sel, ha a szervezete speciális házirendeket használ a kulcsok felügyeletéhez.

### A BYOK előfeltételei
A következő táblázat felsorolja a saját kulcs használata (BYOK) előfeltételeit.

|Követelmény|További információ|
|---------------|--------------------|
|Az Azure RMS-t támogató előfizetés.|További információ az elérhető előfizetésekkel kapcsolatban: [Az Azure RMS-t támogató felhőalapú előfizetések](../get-started/requirements-subscriptions.md)..|
|Ne használja az RMS-t egyéni felhasználók számára vagy az Exchange Online-hoz. Vagy ha mégis használja az Exchange Online-t, tudomásul veszi és elfogadja a BYOK ezzel a konfigurációval való használatával járó korlátozásokat.|További információ a BYOK-ra vonatkozó jelenlegi korlátozásokkal kapcsolatban: [A BYOK díjszabása és korlátozásai](byok-price-restrictions.md)..<br /><br />**Fontos**: A BYOK jelenleg nem kompatibilis az Exchange Online-nal.|
|Thales HSM, intelligens kártyák és támogatószoftver.<br /><br />**Megjegyzés**: Ha AD RMS-ről tér át Azure RMS-re a szoftverkulcs hardverkulcsra váltásával, akkor a Thales-illesztőprogramok legalább 11.62-es verziójával kell rendelkeznie.|Szükség van egy Thales hardveres biztonsági modulhoz való hozzáférésre és a Thales HSM-ek működtetéséhez szükséges alapvető ismeretekre. Tekintse meg a [Thales hardveres biztonsági modullal kapcsolatos oldalt](http://www.thales-esecurity.com/msrms/buy) a kompatibilis modellek listájáért vagy HSM vásárlásához, ha még nem rendelkezik ilyennel.|
|Ha bérlőkulcsát az interneten kívánja továbbítani ahelyett, hogy személyesen el kelljen mennie az amerikai Redmondba, ahhoz 3 követelményt kell teljesítenie:<br /><br />1. követelmény: Egy internetkapcsolattal nem rendelkező x64-es munkaállomás, amelyen legalább a Windows 7 operációs rendszer, valamint a Thales nShield szoftver 11.62-es vagy újabb verziója fut.<br /><br />Ha ez a munkaállomás Windows 7-et futtat, [telepítse a Microsoft .NET-keretrendszer 4.5-öt](http://go.microsoft.com/fwlink/?LinkId=225702)..<br /><br />2. követelmény: Egy internetkapcsolattal rendelkező munkaállomás, amely legalább Windows 7 operációs rendszert futtat.<br /><br />3. követelmény: Egy USB-meghajtó vagy más hordozható tárolóeszköz, amelyen legalább 16 MB szabad tárhely található.|Ezen előfeltételeket nem kell teljesíteni, ha Redmondba utazik és személyesen adja át a bérlőkulcsát.<br /><br />Biztonsági okokból javasoljuk, hogy az első munkaállomás ne csatlakozzon hálózathoz. Ez azonban nem szoftveres követelmény.<br /><br />Megjegyzés: A következő utasításokban erre az első munkaállomásra **kapcsolat nélküli munkaállomásként** hivatkozunk..<br /><br />Ezenfelül ha a bérlőkulcsa éles hálózathoz használható, javasoljuk, hogy az eszközkészlet letöltésére és a bérlőkulcs feltöltésére egy második, különálló munkaállomást használjon. Tesztelési célokra azonban használhatja az első munkaállomást is.<br /><br />Megjegyzés: A következő utasításokban erre a második munkaállomásra **internetre kapcsolódó munkaállomásként** hivatkozunk..|

A bérlőkulcs létrehozására és használatba vételére vonatkozó eljárások attól függenek, hogy a műveleteket az interneten keresztül vagy személyesen kívánja elvégezni:

-   **Az interneten keresztül:** Ez néhány további konfigurációs lépést igényel, például egy eszközkészlet és Windows PowerShell-parancsmagok letöltését és használatát. Azonban a bérlőkulcs továbbításához nem kell fizikailag egy Microsoft-létesítményben tartózkodnia. A biztonságot a következő módszerek garantálják:

    -   A bérlőkulcsot egy kapcsolat nélküli munkaállomáson hozza létre, ezzel is csökkentve a támadási felületet.

    -   A bérlőkulcs titkosítását egy kulcscserekulcs (KEK) biztosítja, és ez egészen az Azure RMS HSM-jeire való átvitelig titkosítva marad. Az eredeti munkaállomást kizárólag a bérlőkulcs titkosított verziója hagyja el.

    -   Egy eszköz úgy állítja be a bérlőkulcs tulajdonságait, hogy azok a bérlőkulcsot az Azure RMS biztonsági világához kötik. Így miután az Azure RMS HSM-jei megkapják és visszafejtik a bérlőkulcsot, csak ezek a HSM-ek tudják használni. A bérlőkulcsot nem lehet exportálni. Ezt a kötést a Thales HSM-ek kényszerítik ki.

    -   A bérlőkulcs titkosításához használt kulcscserekulcs (KEK) az Azure RMS HSM-jein belül jön létre, és nem exportálható. A HSM-ek biztosítják, hogy a KEK-nek nem létezhet titkosítatlan verziója a HSM-eken kívül. Emellett az eszközkészlet egy, a Thales által kiadott igazolást tartalmaz arról, hogy a KEK nem exportálható, és egy eredeti, a Thales által gyártott HSM-en lett létrehozva.

    -   Az eszközkészlet egy, a Thales által kiadott igazolást tartalmaz arról is, hogy az Azure RMS biztonsági világ szintén egy eredeti, a Thales által gyártott HSM-en lett létrehozva. Így Ön megbizonyosodhat arról, hogy a Microsoft eredeti hardvereket használ.

    -   A Microsoft minden egyes földrajzi régióban külön KEK-eket és biztonsági világot használ, ami garantálja, hogy az Ön bérlőkulcsa csak az abban a régióban fekvő adatközpontokban használható, ahol titkosítva lett. Például egy európai ügyfél bérlőkulcsát nem lehet észak-amerikai vagy ázsiai adatközpontokban felhasználni.

    > [!NOTE]
    > A bérlőkulcs biztonságosan haladhat át nem megbízható számítógépeken és hálózatokon, mivel titkosítva van és hozzáférés-vezérlési szintű engedélyek biztosítják a védelmét, így csak az Ön HSM-jein, illetve a Microsoft az Azure RMS-hez használt HSM-jein használható. A biztonsági intézkedéseket az eszközkészletben található parancsfájlok segítségével ellenőrizheti, ennek működéséről a Thales oldalán olvashat bővebben: [Hardware Key management in the RMS Cloud](https://www.thales-esecurity.com/knowledge-base/white-papers/hardware-key-management-in-the-rms-cloud) (Hardverkulcs kezelése az RMS-felhőben)..

-   **Személyesen:** Ehhez fel kell vennie a kapcsolatot a Microsoft ügyféltámogatási szolgálatával, hogy időpontot egyeztessen az Azure RMS-kulcs átvitelére. Bérlőkulcsa az Azure RMS biztonsági világába való átviteléhez fel kell keresnie a Microsoft irodáját, amely az egyesült államokbeli Redmondban (Washington államban) található.

Az útmutató megtekintéséhez döntse el, hogy a bérlőkulcsot az interneten keresztül vagy személyesen fogja létrehozni és átvinni: 

- [Az interneten keresztül](generate-tenant-key-internet.md)
- [Személyesen](generate-tenant-key-in-person.md)


## További lépések

Miután megtervezte, és ha szükséges, létrehozta a bérlőkulcsot, tegye az alábbiakat:

1.  Kezdje meg a bérlőkulcs használatát:

    -   Ha még nem tette meg, most aktiválnia kell a Rights Management szolgáltatást, hogy a szervezete használatba vehesse az RMS-t. A felhasználók azonnal megkezdik az Ön bérlőkulcsának használatát (akár a Microsoft, akár Ön felügyeli azt).

        További információ az aktiválásról: [Activating Azure Rights Management](../deploy-use/activate-service.md) (Az Azure Rights Management aktiválása)..

    -   Ha már aktiválta a Rights Managementet, és később döntött a saját bérlőkulcsának felügyelete mellett, a felhasználók fokozatosan állnak át a régi bérlőkulcsról az újra, és ez a lépcsőzetes átállás eltarthat néhány hétig. A régi bérlőkulccsal védett dokumentumok és fájlok hozzáférhetők maradnak a jogosult felhasználók számára.

2.  Fontolja meg a használati naplózás alkalmazását, amely az RMS által végrehajtott minden egyes tranzakciót naplóz.

    Ha úgy döntött, hogy Ön felügyeli a bérlőkulcsot, a napló a bérlőkulcs használatára vonatkozó információkat is tartalmaz. A következő példában egy Excelben megjelenő naplófájl látható, amelyben a **Decrypt** és a **SignDigest** kérelemtípusok mutatják, hogy a bérlőkulcs használatban van.

    ![Naplófájl az Excelben bérlőkulcs használata mellett](../media/RMS_Logging.gif)

    További információ a használati naplózásról: [Az Azure Rights Management használatának naplózása és elemzése](../deploy-use/log-analyze-usage.md)..

3.  Tartsa karban a bérlőkulcsot.

    További információk: [Operations for Your Azure Rights Management Tenant Key)](../deploy-use/operations-tenant-key.md) (Az Azure Rights Management bérlőkulcsával kapcsolatos műveletek..



<!--HONumber=Apr16_HO4-->


