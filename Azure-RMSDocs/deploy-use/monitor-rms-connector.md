---
# required metadata

title: Az Azure Rights Management-összekötő megfigyelése | Azure RMS
description:
keywords:
author: cabailey
manager: mbaldwin
ms.date: 06/09/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 8a1b3e54-f788-4f84-b9d7-5d5079e50b4e

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: esaggese
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Az Azure Rights Management-összekötő megfigyelése

*A következőkre vonatkozik: Azure Rights Management, Windows Server 2012, Windows Server 2012 R2*

Az RMS-összekötő telepítése és konfigurálása után az alábbi módszerekkel és információkkal megfigyelheti az összekötőt és a vállalati Azure RMS-használatot.

## Az alkalmazás eseménynapló-bejegyzései

Az RMS-összekötő az alkalmazás eseménynaplójában rögzíti a bejegyzéseket a **Microsoft RMS-összekötő** számára. 

Például olyan tájékoztató eseményeket, mint az ID 1000, amely megerősíti, hogy az összekötő-szolgáltatás elindult, az ID 1002, amely jelzi, hogy a kiszolgáló sikeresen csatlakozott az RMS-összekötőhöz, vagy az ID 1004, amely minden alkalommal megjelenik, ha az összekötő letölti az engedélyezett fiókok listáját (minden fiók listázva van). 

Ha még nem konfigurálta HTTPS-használatra az összekötőt, a 2002-es azonosítójú figyelmeztetés fog megjelenni, amely azt jelzi, hogy az ügyfél nem biztonságos (HTTP) kapcsolatot használ.

Ha az összekötő nem tud kapcsolódni az Azure RMS-hez, valószínűleg a 3001-es számú hibaüzenet fog megjelenni. Ez például egy DNS-problémának, vagy az RMS-összekötőt futtató kiszolgáló(k) internetkapcsolata hiányának is lehet az eredménye. 

> [!TIP] A webproxy beállításai gyakori okai annak, hogy az RMS-összekötő kiszolgálói nem tudnak kapcsolódni az Azure RMS-hez.

Ahogyan az eseménynapló-bejegyzéseknél, további részletekért itt is tekintse meg az üzenet részleteit.

Az eseménynaplónak az összekötő üzembe helyezésekor való ellenőrzése mellett célszerű rendszeresen ellenőrizni a figyelmeztetéseket és a hibákat. Például előfordulhat, hogy az összekötő kezdetben az elvárásoknak megfelelően működik, de más rendszergazdák megváltoztathatják a függő beállításokat. Például egy másik rendszergazda megváltoztatja a webes proxykiszolgáló beállításait úgy, hogy az RMS-összekötő kiszolgálói nem tudnak hozzáférni az internethez (3001-es számú hibaüzenet), vagy eltávolítja egy számítógép fiókját az egyik összekötő-használatra engedélyezett csoportból (2001-es számú figyelmeztetés).

## Teljesítményszámlálók

Az RMS-összekötő a telepítéskor automatikusan létrehoz teljesítményszámlálókat a **Microsoft Rights Management-összekötőhöz**, amelyek segíthetnek megfigyelni az Azure RMS összekötővel való használatának teljesítményét. 

Például ha rendszeresen tapasztal késést dokumentumok vagy e-mailek védelme esetén, illetve a védett dokumentumok vagy e-mailek megnyitásakor, a teljesítményszámlálók segítenek meghatározni, hogy a késés az összekötő vagy az Azure RMS feldolgozási idejéből, vagy hálózati késésekből származik. A késés helyének azonosításához azokat a számlálókat keresse, amelyek tartalmazzák az **összekötő feldolgozási idejének**, a **szolgáltatás válaszidejének**, és az **összekötő válaszidejének** átlagos számait. Például: **az összekötő átlagos válaszideje a sikeres kötegelt licenckérésekhez**.

Ha nemrégiben hozzáadott új kiszolgálói fiókokat az összekötőhöz, érdemes **Az utolsó házirendfrissítés óta eltelt idő** számlálóját figyelni ahhoz, hogy megállapítsa, hogy az összekötő letöltötte-e a listát a frissítés óta, vagy várakozni kell még (akár 15 percet).

## RMS-elemző

Az RMS-elemző eszköz segít figyelemmel kísérni az összekötő állapotát és azonosítani a konfigurációs problémákat.

Ha még nem töltötte le ezt az eszközt, megtalálhatja a [Letöltőközpontban](https://www.microsoft.com/en-us/download/details.aspx?id=46437), majd telepítheti bármelyik, internet-hozzáféréssel rendelkező, az RMS-összekötőhöz csatlakozni képes számítógépre. Futtassa az eszközt, és az **üdvözlőlapon** válassza ki az **Azure RMS-összekötő** lehetőséget.

További információt és útmutatást a letöltési oldal **Részletek** és a **Telepítése útmutató** szakaszaiban találhat.

## Naplózás

A használatnaplózással azonosíthatja, hogy mikor használják, illetve látják el védelemmel az e-maileket és a dokumentumokat. Ha ezt az RMS-összekötővel végzi, a naplófájlok felhasználóazonosítójának mezője fogja tartalmazni az RMS-összekötő telepítésekor automatikusan létrehozott egyszerű szolgáltatásnevet.

További információ: [Az Azure Rights Management használatának naplózása és elemzése](log-analyze-usage.md).

Ha részletesebb naplózást kíván végezni diagnosztikai célokkal, használja a Windows Sysinternals [Debugview](http://go.microsoft.com/fwlink/?LinkID=309277) alkalmazását, és engedélyezze a nyomkövetést az RMS-összekötőben az IIS Alapértelmezett oldala web.config fájljának módosításával. Tegye a következőt:

1. Keresse meg a web.config fájlt a **%programfiles%\Microsoft Rights Management-összekötő\Webszolgáltatás** helyen.

2. Keresse meg a következő sort:

        <trace enabled="false" requestLimit="10" pageOutput="false" traceMode="SortByTime" localOnly="true"/>

3. Cserélje le a sort erre:

        <trace enabled="true" requestLimit="10" pageOutput="false" traceMode="SortByTime" localOnly="true"/>

4.  Állítsa le és indítsa el az IIS-t a nyomkövetés aktiválásához. 

5.  Ha sikerült rögzíteni a kívánt nyomokat, állítsa vissza a 3. lépés sorát az eredetire, majd állítsa le és indítsa újra az IIS-t.



<!--HONumber=Jun16_HO2-->


