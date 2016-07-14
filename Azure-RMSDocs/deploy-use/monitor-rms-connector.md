---
title: "Az Azure Rights Management-összekötő megfigyelése | Azure RMS"
description: 
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 07/08/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 8a1b3e54-f788-4f84-b9d7-5d5079e50b4e
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: f8e23e8bcbfb25092cb31f7af76d17239f3063a7
ms.openlocfilehash: 32c3c93d55bd82f45fa7a081e55ae7ebe8f5956f


---

# Az Azure Rights Management-összekötő megfigyelése

*A következőkre vonatkozik: Azure Rights Management, Windows Server 2012, Windows Server 2012 R2*

Az RMS-összekötő telepítése és konfigurálása után az alábbi módszerekkel és információkkal megfigyelheti az összekötőt és a vállalati Azure RMS-használatot.

## Az alkalmazás eseménynapló-bejegyzései

Az RMS-összekötő az alkalmazás eseménynaplójában rögzíti a bejegyzéseket a **Microsoft RMS-összekötő** számára. 

Például olyan tájékoztató eseményeket, mint az ID 1000, amely megerősíti, hogy az összekötő-szolgáltatás elindult, az ID 1002, amely jelzi, hogy a kiszolgáló sikeresen csatlakozott az RMS-összekötőhöz, vagy az ID 1004, amely minden alkalommal megjelenik, ha az összekötő letölti az engedélyezett fiókok listáját (minden fiók listázva van). 

Ha még nem konfigurálta HTTPS-használatra az összekötőt, a 2002-es azonosítójú figyelmeztetés fog megjelenni, amely azt jelzi, hogy az ügyfél nem biztonságos (HTTP) kapcsolatot használ.

Ha az összekötő nem tud kapcsolódni az Azure RMS-hez, valószínűleg a 3001-es számú hibaüzenet fog megjelenni. Ez például egy DNS-problémának, vagy az RMS-összekötőt futtató kiszolgáló(k) internetkapcsolata hiányának is lehet az eredménye. 

> [!TIP]
> A webproxy beállításai gyakori okai annak, hogy az RMS-összekötő kiszolgálói nem tudnak kapcsolódni az Azure RMS-hez.

Ahogyan az eseménynapló-bejegyzéseknél, további részletekért itt is tekintse meg az üzenet részleteit.

Az eseménynaplónak az összekötő üzembe helyezésekor való ellenőrzése mellett célszerű rendszeresen ellenőrizni a figyelmeztetéseket és a hibákat. Például előfordulhat, hogy az összekötő kezdetben az elvárásoknak megfelelően működik, de más rendszergazdák megváltoztathatják a függő beállításokat. Például egy másik rendszergazda megváltoztatja a webes proxykiszolgáló beállításait úgy, hogy az RMS-összekötő kiszolgálói nem tudnak hozzáférni az internethez (3001-es számú hibaüzenet), vagy eltávolítja egy számítógép fiókját az egyik összekötő-használatra engedélyezett csoportból (2001-es számú figyelmeztetés).

### Eseménynapló – azonosítók és leírások

Az alábbi szakaszok a lehetséges eseményazonosítók, leírások és egyéb adatok azonosításában nyújtanak segítséget.

-----

**1000**-es információ

**A Microsoft RMS-összekötő webszolgáltatás elindult.**

Ennek az eseménynek a naplózására akkor kerül sor, amikor először történik kísérlet az RMS-összekötő indítására.

----

**1001**-es információ

**A Microsoft RMS-összekötő webszolgáltatás leállt.**

Ennek az eseménynek a naplózására akkor kerül sor, amikor az RMS-összekötő normál működés következményként leáll. Ilyen például az IIS újraindítása vagy a számítógép leállítása. 

----

**1002**-es információ

**A Microsoft RMS-összekötőhöz való hozzáférés engedélyezve egy jogosult kiszolgáló számára.**

Ennek az eseménynek a naplózására akkor kerül sor, amikor egy helyszíni kiszolgálón lévő fiók először csatlakozik az RMS-összekötőhöz, miután a fiókot az Azure RMS rendszergazdája engedélyezte az RMS-összekötő felügyeleti eszközében. Az eseményhez tartozó üzenetben a SID azonosító, a fiók neve és a kapcsolatot létrehozó számítógép neve szerepel.

----

**1003**-as információ

**Az alábbi ügyféllel való kapcsolat nem biztonságos kapcsolatról (HTTP) biztonságos (HTTPS) kapcsolatra változott.**

Ennek az eseménynek a naplózására akkor kerül sor, amikor a helyszíni kiszolgáló RMS-összekötővel való kapcsolata HTTP (kevésbé biztonságos) kapcsolatról HTTPS (biztonságosabb) kapcsolatra változik. Az eseményhez tartozó üzenetben a SID azonosító, a fiók neve és a kapcsolatot létrehozó számítógép neve szerepel.

----

**1004**-es információ

**Az engedélyezett fiókok listája frissítve.**

Ennek az eseménynek a naplózására akkor kerül sor, amikor az RMS-összekötő letöltötte az RMS-összekötő használatára jogosult fiókok (meglévő fiókok és módosítások) legfrissebb listáját. A lista 15 percenként töltődik le, biztosítva, hogy az RMS-összekötő képes legyen kommunikálni az Azure RMS-sel.

----

**2000**-es figyelmeztetés

**A HTTP-környezetben az egyszerű felhasználónév hiányzik vagy érvénytelen. Ellenőrizze, hogy a Microsoft RMS-összekötő webhelyen le van-e tiltva a névtelen hitelesítés az IIS-ben, és csak a Windows-hitelesítés van-e engedélyezve.**

Ennek az eseménynek a naplózására akkor kerül sor, amikor az RMS-összekötő nem tudja egyedileg azonosítani a hozzá kapcsolódni próbáló fiókot. Ez lehet az IIS-hez nem megfelelően konfigurált névtelen hitelesítés eredménye, vagy a fiók nem megbízható erdőből származik.

----

**2001**-es figyelmeztetés

**Jogosulatlan hozzáférési kísérlet a Microsoft RMS-összekötőhöz.**

Ennek az eseménynek a naplózására akkor kerül sor, amikor egy fiók megpróbál csatlakozni az RMS-összekötőhöz, de a kísérlet meghiúsul. Ennek leggyakoribb oka, hogy a kapcsolatot megkísérlő fiók nem szerepel az engedélyezett fiókoknak az RMS-összekötő által az Azure RMS-ről letöltött listáján. Például a legújabb lista még nem lett letöltve (ez 15 percenként történik), vagy a fiók nem szerepel a listán. 

A másik ok lehet, ha az RMS-összekötő ugyanarra a kiszolgálóra lett telepítve, amely az összekötő használatára van beállítva. Ilyen például, ha az RMS-összekötőt az Exchange Servert futtató kiszolgálóra telepíti, és engedélyezi egy Exchange-fiók számára az összekötő használatát. Ez a konfiguráció nem támogatott, mert az RMS-összekötő nem tudja helyesen azonosítani a fiókot, amikor az megpróbál kapcsolódni.

Az eseményüzenet tartalmazza az RMS-összekötőhöz csatlakozni próbáló fiók és számítógép adatait:

- Ha az RMS-összekötőhöz csatlakozni próbáló fiók nem érvényes fiók, az RMS-összekötő felügyeleti eszköz segítségével veheti fel a hitelesített fiókok listájára. További információk arról, hogy mely fiókokat kell engedélyezni: [Kiszolgáló hozzáadása az engedélyezett kiszolgálók listájához](install-configure-rms-connector.md#add-a-server-to-the-list-of-allowed-servers). 

- Ha az RMS-összekötőhöz csatlakozni próbáló fiók ugyanazon a számítógépen található, mint az RMS-összekötő kiszolgálója, telepítse az összekötőt egy másik kiszolgálóra. Az összekötő előfeltételeivel kapcsolatos további információkért lásd: [Az RMS-összekötő előfeltételei]( deploy-rms-connector.md#prerequisites-for-the-rms-connector).

----

**2002**-es figyelmeztetés

**Az alább megnevezett ügyfél nem biztonságos (HTTP) kapcsolatot használ.**

Ennek az eseménynek a naplózására akkor kerül sor, amikor egy helyszíni kiszolgáló sikeresen kapcsolódott az RMS-összekötőhöz, de a (biztonságosabb) HTTPS kapcsolat helyett HTTP (kevésbé biztonságos) kapcsolatot használ. Az események naplózása fiókonként, nem kapcsolatonként történik. Az esemény akkor kerül be újra a naplóba, ha a fiók sikeresen váltott HTTPS kapcsolatra, majd visszaállt HTTP kapcsolat használatára.

Az eseményüzenetben a fiók SID azonosítója, a fiók neve és az RMS-összekötőhöz kapcsolódó számítógép neve szerepel.

Az RMS-összekötő HTTPS kapcsolatok használatára való beállítását lásd: [Az RMS-összekötő konfigurálása HTTPS használatára](install-configure-rms-connector.md#configuring-the-rms-connector-to-use-https).

----

**2003**-as figyelmeztetés

**Az engedélyek listája üres. A szolgáltatás mindaddig nem lesz használható, amíg az összekötő engedélylistáját fel nem töltik hitelesített felhasználókkal és csoportokkal.**

Ennek az eseménynek a naplózására akkor kerül sor, amikor az RMS-összekötőhöz nem tartozik engedélyezett fiókokat tartalmazó lista, ezért egy helyszíni kiszolgáló sem tud hozzá csatlakozni. Az RMS-összekötő 15 percenként tölti le a listát az Azure RMS-ről. 

A fiókok megadásához használja az RMS-összekötő felügyeleti eszközét. További információk: [Az RMS-összekötő használatának engedélyezése a kiszolgálók számára]( install-configure-rms-connector.md#authorizing-servers-to-use-the-rms-connector). 

----

**3000**-es hiba

**Kezeletlen kivétel történt a Microsoft RMS-összekötőben.**

Ez az esemény minden alkalommal a naplóba kerül, amikor az RMS-összekötő nem várt hibával találkozik. Az eseményüzenet tartalmazza a hiba adatait.

A hiba egyik lehetséges okát a következő szöveg azonosítja az eseményüzenetben: **A kérelem sikertelen, a válasz üres**. Ha ez a szöveg látható, lehetséges, hogy olyan hálózati eszközzel rendelkezik, amely a helyszíni kiszolgálók és az RMS-összekötő kiszolgálója közötti csomagokon SSL-ellenőrzést végez. Ez a funkció nem támogatott és sikertelen kommunikációt eredményez. Az eseménynaplóban ilyenkor a fenti üzenet jelenik meg.

----

**3001**-es hiba

**Kivétel történt az engedélyezési adatok letöltése során.**

Ennek az eseménynek a naplózására akkor kerül sor, amikor az RMS-összekötő nem tudja letölteni az RMS-összekötő használatára jogosult fiókok legfrissebb listáját. Az eseményüzenet tartalmazza a hiba adatait.



----

## Teljesítményszámlálók

Az RMS-összekötő a telepítéskor automatikusan létrehoz teljesítményszámlálókat a **Microsoft Rights Management-összekötőhöz**, amelyek segíthetnek megfigyelni az Azure RMS összekötővel való használatának teljesítményét. 

Például ha rendszeresen tapasztal késést dokumentumok vagy e-mailek védelme esetén, illetve a védett dokumentumok vagy e-mailek megnyitásakor, a teljesítményszámlálók segítenek meghatározni, hogy a késés az összekötő vagy az Azure RMS feldolgozási idejéből, vagy hálózati késésekből származik. A késés helyének azonosításához azokat a számlálókat keresse, amelyek tartalmazzák az **összekötő feldolgozási idejének**, a **szolgáltatás válaszidejének**, és az **összekötő válaszidejének** átlagos számait. Például: **az összekötő átlagos válaszideje a sikeres kötegelt licenckérésekhez**.

Ha nemrégiben hozzáadott új kiszolgálói fiókokat az összekötőhöz, érdemes **Az utolsó házirendfrissítés óta eltelt idő** számlálóját figyelni ahhoz, hogy megállapítsa, hogy az összekötő letöltötte-e a listát a frissítés óta, vagy várakozni kell még (akár 15 percet).

## RMS-elemző

Az RMS-elemző eszköz segít figyelemmel kísérni az összekötő állapotát és azonosítani a konfigurációs problémákat.

Ha még nem töltötte le ezt az eszközt, megtalálhatja a [Letöltőközpontban](https://www.microsoft.com/en-us/download/details.aspx?id=46437), majd telepítheti bármelyik, internet-hozzáféréssel rendelkező, az RMS-összekötőhöz csatlakozni képes számítógépre. Futtassa az eszközt, és az **üdvözlőlapon** válassza ki az **Azure RMS-összekötő** lehetőséget.

További információt és útmutatást a letöltési oldal **Részletek** és a **Telepítése útmutató** szakaszaiban találhat.

## Naplózás

A használatnaplózással azonosíthatja, hogy mikor használják, illetve látják el védelemmel az e-maileket és a dokumentumokat. Ha ez az RMS-összekötővel történik, a naplófájlok felhasználóazonosító mezője az RMS-összekötő számára automatikusan létrehozott **Aadrm_S-1-7-0** egyszerű szolgáltatásnevet tartalmazza.

További információ a használat naplózásáról: [Az Azure Rights Management használatának naplózása és elemzése](log-analyze-usage.md).

Ha részletesebb naplózást kíván végezni diagnosztikai célokkal, használja a Windows Sysinternals [Debugview](http://go.microsoft.com/fwlink/?LinkID=309277) alkalmazását, és engedélyezze a nyomkövetést az RMS-összekötőben az IIS Alapértelmezett oldala web.config fájljának módosításával. Tegye a következőt:

1. Keresse meg a web.config fájlt a **%programfiles%\Microsoft Rights Management-összekötő\Webszolgáltatás** helyen.

2. Keresse meg a következő sort:

        <trace enabled="false" requestLimit="10" pageOutput="false" traceMode="SortByTime" localOnly="true"/>

3. Cserélje le a sort erre:

        <trace enabled="true" requestLimit="10" pageOutput="false" traceMode="SortByTime" localOnly="true"/>

4.  Állítsa le és indítsa el az IIS-t a nyomkövetés aktiválásához. 

5.  Ha sikerült rögzíteni a kívánt nyomokat, állítsa vissza a 3. lépés sorát az eredetire, majd állítsa le és indítsa újra az IIS-t.




<!--HONumber=Jul16_HO2-->


