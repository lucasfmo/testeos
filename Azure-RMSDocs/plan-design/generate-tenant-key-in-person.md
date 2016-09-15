---
title: "Generate and transfer your tenant key – in person (A bérlőkulcs létrehozása és átvitele – személyesen) | Azure RMS"
description: 
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 3281e45e-cf69-4dc5-946b-3029851d3152
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 0f355da35dff62ecee111737eb1793ae286dc93e
ms.openlocfilehash: 1acc66e9a73b100268ed722391a0a87651c64abc


---

# Generate and transfer your tenant key – in person (A bérlőkulcs létrehozása és átvitele – személyesen)

*A következőkre vonatkozik: Azure Rights Management, Office 365*


Ha úgy döntött, hogy [saját bérlőkulcsot kezel](plan-implement-tenant-key.md#choose-your-tenant-key-topology-managed-by-microsoft-the-default-or-managed-by-you-byok-), és nem szeretné azt az interneten keresztül továbbítani, hanem inkább személyesen adná át, kövesse a következő eljárásokat.

## A bérlőkulcs létrehozása
A saját bérlőkulcsa létrehozásához kövesse a következő 3 lépést:

-   [1. lépés: A munkaállomás előkészítése a Thales HSM-mel](#step-1-prepare-a-workstation-with-thales-hsm)

-   [2. lépés: Biztonsági világ létrehozása](#step-2-create-a-security-world)

-   [3. lépés: Új kulcs létrehozása](#step-3-create-a-new-key)

### 1. lépés: A munkaállomás előkészítése a Thales HSM-mel
Telepítse az nCipher (Thales) támogatószoftvert egy Windows-számítógépen. Csatoljon a számítógéphez egy Thales HSM-et. Győződjön meg róla, hogy a Thales-eszközök az elérési úton találhatók. További információkért tekintse át a Thales HSM-hez mellékelt felhasználói útmutatót, vagy keresse fel a Thales webhelyén az Azure RMS-ekkel kapcsolatos oldalt a következő címen: [http://www.thales-esecurity.com/msrms/cloud](http://www.thales-esecurity.com/msrms/cloud).

### 2. lépés: Biztonsági világ létrehozása
Indítson el egy parancssort, és futtassa a Thales új világot létrehozó programját.

```
new-world.exe --initialize --cipher-suite=DLf1024s160mRijndael --module=1 --acs-quorum=2/3
```
Ez a program létrehoz egy **biztonságivilág**-fájlt az %NFAST_KMDATA%\local\world címen, amely a C:\ProgramData\nCipher\Key Management Data\local mappának felel meg. A kvórumhoz különböző értékeket is használhat, de a mi példánkban három üres kártyát és mindegyikhez egy PIN-kódot kell megadnia. Ezután bármelyik két kártya teljes hozzáférést biztosít a biztonsági világhoz.  Ezek a kártyák lesznek az új biztonsági világ **rendszergazdai kártyakészlete**.

Ezután tegye a következőket:

1.  Telepítse a Thales CNG-szolgáltatót a Thales dokumentációjában leírt módon, majd konfigurálja azt az új biztonsági világ használatára.

2.  Készítsen biztonsági másolatot a világfájlról. Helyezze biztonságba és biztosítson védelmet a világfájl, valamint a rendszergazdai kártyák és PIN-kódjaik számára, és gondoskodjon róla, hogy senki ne férhessen hozzá egynél több kártyához.

Most már készen áll arra, hogy létrehozzon egy új kulcsot, amely az Ön RMS-bérlőkulcsa lesz.

### 3. lépés: Új kulcs létrehozása
Hozzon létre egy CNG-kulcsot a Thales **generatekey** és **cngimport** programjai használatával.

A kulcs létrehozásához futtassa a következő parancsot:

```
generatekey --generate simple type=RSA size=2048 protect=module ident=contosokey plainname=contosokey nvram=no pubexp=
```
A parancs futtatásakor használja a következő utasításokat:

-   A **protect** paramétert a **module** értékre kell állítani, ahogyan az ábrán látható. Ez egy modul által védett kulcsot hoz létre. A BYOK eszközkészlet nem támogatja az OCS által védett kulcsokat.

-   A kulcs méretét illetően 2048 bit javasolt, de az AD RMS-ről Azure RMS-re áttérő ügyfelek számára az 1024 bites RSA-kulcsok is támogatottak.

-   Cserélje le a *contosokey* értéket az **ident** és a **plainname** esetében bármilyen tetszőleges karakterláncra. Az adminisztratív terhek és a hibalehetőségek minimalizálása érdekében javasoljuk, hogy mindkettőhöz azonos értéket használjon, amely csupa kisbetűs karaktert tartalmaz.

-   A példában a pubexp üresen maradt (alapértelmezett érték), de megadhat specifikus értékeket is. További információt a Thales dokumentációjában talál.

Ezután futtassa a következő parancsot a kulcs importálásához a CNG-be:

```
cngimport --import –M --key=contosokey --appname=simple contosokey
```
A parancs futtatásakor használja a következő utasításokat:

-   Cserélje le a *contosokey* értéket az 1. lépésben megadott értékre.

-   Használja az **-M** kapcsolót, hogy a kulcs megfeleljen ennek a forgatókönyvnek. Enélkül a létrejött kulcs egy felhasználóspecifikus kulcs lesz a jelenlegi felhasználó részére.

Ez a parancs egy tokenekre bontott kulcsfájlt hoz létre az %NFAST_KMDATA%\local mappában, amelynek a neve a **key_caping_`_`** előtaggal kezdődik, amelyet egy SID követ. Például: **key_caping_machine--801c1a878c925fd9df4d62ba001b94701c039e2fb**. Ez a fájl egy titkosított kulcsot tartalmaz.

Készítsen erről a tokenekre bontott kulcsfájlról egy biztonsági másolatot egy biztonságos helyre.

> [!IMPORTANT]
> Amikor később átviszi a kulcsot az Azure RMS-re, a Microsoft a kulcs egy nem helyreállítható példányával fog rendelkezni. Ez azt jelenti, hogy az Ön kulcsát a Microsoft HSM-jeiről senki nem tudja megszerezni. Így Ön kizárólagos felügyeletet gyakorolhat a bérlőkulcsa felett. Emiatt rendkívül fontos, hogy biztonsági másolatot készítsen a kulcsáról és a biztonsági világáról. A kulcs biztonsági másolatának elkészítésével kapcsolatos útmutatásért és az ajánlott eljárásokért lépjen kapcsolatba a Thalesszel.

Most már készen áll arra, hogy a bérlőkulcsát átvigye az Azure RMS szolgáltatásba.

## Transfer your tenant key to Azure RMS (A bérlőkulcs átvitele az Azure RMS szolgáltatásba)
Miután létrehozta a saját kulcsát, át kell azt vinnie az Azure RMS-re a használatba vétel előtt. A legmagasabb szintű biztonság érdekében ez az átvitel egy kézi művelet, amelynek elvégzéséhez fel kell keresnie a Microsoft irodáját, amely az egyesült államokbeli Redmondban (Washington állam) található. A folyamat teljesítéséhez kövesse a következő 3 lépést:

-   [1. lépés: A kulcs szállítása a Microsofthoz](#step-1-bring-your-key-to-microsoft)

-   [2. lépés: A kulcs átvitele az Azure RMS biztonsági világába](#step-2-transfer-your-key-to-the-azure-rms-security-world)

-   [3. lépés: Záró eljárások](#step-3-closing-procedures)

### 1. lépés: A kulcs szállítása a Microsofthoz

-   Vegye fel a kapcsolatot a Microsoft ügyféltámogatási szolgálatával, hogy időpontot egyeztessen az Azure RMS-kulcs átvitelére. Hozza el a következőket a Microsoft Redmondban található irodájába:

    -   A rendszergazdai kártyái kvóruma. Ha követte a korábban a [2. lépés: Biztonsági világ létrehozása](#step-2-create-a-security-world) lépésben szereplő utasításokat, ez a három kártya közül bármelyik kettő lehet.

    -   Az Ön rendszergazdai kártyájának és PIN-kódjainak (általában kettőnek, kártyánként egynek) a szállítására felhatalmazott személy.

    -   Az Ön biztonságivilág-fájlja (%NFAST_KMDATA%\local\world) egy USB-meghajtón.

    -   Az Ön tokenekre bontott kulcsfájlja egy USB-meghajtón.

### 2. lépés: A kulcs átvitele az Azure RMS biztonsági világába

1.  Amikor megérkezik a Microsofthoz, hogy végrehajtsa a kulcsa átvitelét, a következő történik:

    -   A Microsoft biztosít önnek egy kapcsolat nélküli munkaállomást, amely rendelkezik egy csatlakoztatott Thales HSM-mel, a Thales telepített szoftvereivel, valamint a C:\Temp\Destination mappában egy előre betöltött Azure RMS biztonságivilág-fájllal.

    -   Töltse be ezen a munkaállomáson a saját biztonságivilág-fájlját és tokenekre bontott kulcsfájlját az USB-meghajtóról a C:\Temp\Source mappába.

    -   Az Azure RMS operátorai biztonságos úton továbbítják a kulcsát az Azure RMS biztonsági világába a Thales segédprogramjai használatával.

    Ez a folyamat a következőhöz hasonlóan néz ki, ahol a példában látható key-xfer-im utolsó paramétere helyén az Ön tokenekre bontott kulcsfájljának a neve található:

    **C:\&gt; mk-reprogram.exe --owner c:\Temp\Destination add c:\Temp\Source**

    **C:\&gt; key-xfer-im.exe c:\Temp\Source c:\Temp\Destination --module c:\Temp\Source\key_caping_machine--801c1a878c925fd9df4d62ba001b94701c039e2fb**

2.  Az Mk-reprogram felkéri Önt és az Azure RMS operátorait, hogy csatlakoztassák a saját rendszergazdai kártyáikat, és adják meg a PIN-kódjaikat. Ezen parancsok eredményeként egy tokenekre bontott kulcsfájl jön létre a C:\Temp\Destination mappában, amely tartalmazza az Ön kulcsát, az Azure RMS biztonsági világa által védve.

### 3. lépés: Záró eljárások

-   Az Ön jelenlétében az Azure RMS operátorai a következőket végzik el:

    -   Futtatnak egy, a Microsoft és a Thales által közösen kifejlesztett eszközt, amely eltávolít két engedélyt: a kulcs helyreállítására és az engedélyek megváltoztatására vonatkozó engedélyt. Ezután az Ön kulcsának ezen példánya el lesz zárva az Azure RMS biztonsági világában. A Thales HSM-ek nem engedik az Azure RMS operátorai számára, hogy a rendszergazdai kártyáikkal helyreállítsák az Ön kulcsának az egyszerű szöveges példányát.

    -   Az eredményként létrejövő fájlt egy USB-meghajtóra másolják az Azure RMS szolgáltatásba való későbbi feltöltéshez.

    -   Visszaállítják a HSM gyári beállításait, és törlik a munkaállomás tartalmát.

Ezennel végrehajtotta a saját kulcs használatának személyesen történő megvalósításához szükséges utasításokat, és visszatérhet a szervezethez a bérlőkulcs tervezéséhez és megvalósításához szükséges további lépések megtételéhez.

> [!div class="button"]
[További lépések >>](plan-implement-tenant-key.md#next-steps)






<!--HONumber=Jun16_HO4-->


