---
title: "Az Azure Rights Management-összekötő telepítése és konfigurálása | Azure RMS"
description: "Az Azure Rights Management (RMS)-összekötő telepítésekor és konfigurálásakor vegye figyelembe a következőket. Ezek az eljárások egybevágnak Az Azure Rights Management-összekötő üzembe helyezése című témakör 1-4. lépésével."
author: cabailey
manager: mbaldwin
ms.date: 06/27/2016
ms.topic: article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 4fed9d4f-e420-4a7f-9667-569690e0d733
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 26b043f1f9e7a1e0cd00c2f31c28f7d6685f0232
ms.openlocfilehash: 9160188f6e905db7ef95365a0cc5cfbcb7522101


---

# Az Azure Rights Management-összekötő telepítése és konfigurálása

>*A következőkre vonatkozik: Azure Rights Management, Office 365*

Az Azure Rights Management (RMS)-összekötő telepítésekor és konfigurálásakor vegye figyelembe a következőket. Ezek az eljárások egybevágnak [Az Azure Rights Management-összekötő üzembe helyezése](deploy-rms-connector.md) című témakör 1-4. lépésével.

Mielőtt hozzákezd, mindenképpen tekintse át és ellenőrizze az üzembe helyezés [előfeltételeit](deploy-rms-connector.md#prerequisites-for-the-rms-connector).


## Az RMS-összekötő telepítése

1.  Azonosítsa számítógépeket (legalább kettőt), amelyek az RMS-összekötőt fogják futtatni. Meg kell felelniük az előfeltételekben szereplő minimális specifikációnak.

    > [!NOTE]
    > Bérlőnként (Office 365- vagy Azure AD-bérlő) egy RMS-összekötőt fog telepíteni (amely több kiszolgálóból áll a magas rendelkezésre állás érdekében). Az Active Directory RMS-sel ellentétben nem kell minden erdőbe RMS-összekötőt telepítenie.

2.  Töltse le az RMS-összekötő forrásfájljait a [Microsoft letöltőközpontból](http://go.microsoft.com/fwlink/?LinkId=314106).

    Az RMS-összekötő telepítéséhez töltse le az RMSConnectorSetup.exe fájlt.

    Továbbá:

    -   Ha később egy 32 bites számítógépen akarja konfigurálni az összekötőt, töltse le a RMSConnectorAdminToolSetup_x86.exe fájlt is.

    -   Ha a beállításjegyzék-beállítások konfigurálásának automatizálásához az RMS-összekötő kiszolgáló konfigurációs eszközét kívánja használni a helyszíni kiszolgálón, töltse le a GenConnectorConfig.ps1 fájlt is.

3.  Az RMS-összekötő telepítéséhez választott számítógépen futtassa az **RMSConnectorSetup.exe** fájlt Rendszergazdai jogosultságokkal.

4.  A Microsoft Rights Management-összekötő Beállítás lapjának Kezdőlapján válassza **A Microsoft Rights Management-összekötő telepítése a számítógépre** lehetőséget, majd kattintson a **Tovább** gombra.

5.  Olvassa el és fogadja el az RMS-összekötő licencfeltételeit, majd kattintson a **Tovább** gombra.

A folytatáshoz adjon meg egy fiókot és egy jelszót az RMS-összekötő konfigurálásához.

## Hitelesítő adatok megadása
Az RMS-összekötő konfigurálása előtt meg kell adnia egy olyan fiók hitelesítő adatait, amely megfelelő jogosultságokkal rendelkezik az RMS-összekötő konfigurálásához. Például megadhatja az **admin@contoso.com** fiókot, majd a hozzá tartozó jelszót.

A jelszó esetében karakter korlátozások vannak érvényben. Nem használhat olyan jelszót, amely a következő karakterek bármelyikét tartalmazza: és jel (**&**); nyitó szögletes zárójel (**[**); záró szögletes zárójel (**]**); egyenes idézőjel (**"**); aposztróf (**'**). Ha a jelszó tartalmazza ezek bármelyikét, az RMS-összekötő hitelesítése sikertelen lesz, és azt a hibaüzenetet kapja, hogy a felhasználónév és jelszó kombinációja helytelen, még akkor is, ha más esetekben sikeresen be tud jelentkezni velük. Ha ez az Ön jelszava esetében fennáll, akkor használjon egy másik fiókot, amelynek a jelszava nem tartalmazza a fenti különleges karakterek egyikét sem, vagy állítsa vissza úgy, hogy ne tartalmazza azokat.

Ha emellett [beléptető vezérlőket](activate-service.md#configuring-onboarding-controls-for-a-phased-deployment) vezetett be, győződjön meg arról, hogy a megadott fiók képes a tartalmak védelmére. Ha például a tartalmak védelmének képességét az „informatikai részleg” csoportra korlátozta, az itt megadott fióknak a csoport tagjának kell lennie. Ha nem az, a következő hibaüzenetet kapja: **A felügyeleti szolgáltatás és a szervezet helyének felderítésére tett kísérlet meghiúsult. Győződjön meg arról, hogy a Microsoft Rights Management szolgáltatás engedélyezve van a szervezetéhez.**

Olyan fiókot használhat, amely rendelkezik az alábbi jogosultságok egyikével:

-   **A bérlő globális rendszergazdája**: olyan fiók, amely az Office 365-bérlő vagy az Azure AD-bérlő globális rendszergazdája.

-   **Az Azure Rights Management globális rendszergazdája**: olyan fiók az Azure Active Directoryban, amelyhez az Azure RMS globális rendszergazdai szerepkört rendelték.

-   **Az Azure Rights Management-összekötő rendszergazdája**: olyan fiók az Azure Active Directoryban, amely jogot kapott az RMS-összekötő telepítésére és felügyeletére a szervezeten belül.

    > [!NOTE]
    > Az Azure Rights Management globális rendszergazda és az Azure Rights Management-összekötő rendszergazda szerepkört az Azure RMS [Add-AadrmRoleBasedAdministrator](https://msdn.microsoft.com/library/dn629417.aspx) parancsmag segítségével rendelik a fiókokhoz.
    > 
    > Az RMS-összekötő legkevesebb jogosultsággal való futtatásához hozzon létre egy külön fiókot erre a célra, majd rendelje hozzá az Azure RMS-összekötő rendszergazda szerepkörét a következőképpen:
    >
    > 1.  Ha még nem tette volna meg, töltse le és telepítse a Windows PowerShellt a Rights Managementhez. További információkért lásd: [Az Azure Rights Managementhez készült Windows PowerShell telepítése](install-powershell.md).
    >
    >     A **Futtatás rendszergazdaként** paranccsal indítsa el a Windows PowerShellt, majd a [Connect-AadrmService](https://msdn.microsoft.com/library/azure/dn629415.aspx) parancsot használva csatlakozzon az Azure RMS szolgáltatáshoz:
    >
    >     ```
    >     Connect-AadrmService                   //provide Office 365 tenant administrator or Azure RMS global administrator credentials
    >     ```
    > 2.  Ezután futtassa az [Add-AadrmRoleBasedAdministrator](https://msdn.microsoft.com/library/azure/dn629417.aspx) parancsot, amelyhez az alábbi paraméterek csak az egyikét használja:
    >
    >     ```
    >     Add-AadrmRoleBasedAdministrator -EmailAddress <email address> -Role "ConnectorAdministrator"
    >     ```
    >
    >     ```
    >     Add-AadrmRoleBasedAdministrator -ObjectId <object id> -Role "ConnectorAdministrator"
    >     ```
    >
    >     ```
    >     Add-AadrmRoleBasedAdministrator -SecurityGroupDisplayName <group Name> -Role "ConnectorAdministrator"
    >     ```
    >     Írja be például a következőt: **Add-AadrmRoleBasedAdministrator -EmailAddress melisa@contoso.com -Role "ConnectorAdministrator"**
    >
    >     Bár ezek a parancsok az összekötő-rendszergazdai szerepkör hozzárendelését végzik el, helyette a GlobalAdministrator szerepkört is használhatja.

Az RMS-összekötő telepítési folyamata során megtörténik az összes előfeltételként megadott szoftver érvényesítése és telepítése, az Internet Information Services (IIS) telepítése, ha még nincs telepítve, valamint az összekötő szoftver telepítése és konfigurálása. Ezenfelül megtörténik az Azure RMS előkészítése a konfigurálásra az alábbiak létrehozásával:

-   Egy olyan kiszolgálókat tartalmazó üres táblázat, amelyek jogosultak az összekötő használatára az Azure RMS-sel való kommunikációhoz. A táblázathoz később adhat hozzá kiszolgálókat.

-   Egy biztonsági jogkivonat-készlet az összekötőhöz, amelyek engedélyezik az Azure RMS-re vonatkozó műveleteket. A jogkivonatokat a rendszer az Azure RMS-ből tölti le, és a helyi számítógép beállításjegyzékébe telepíti. A rendszer a védelmükhöz az adatvédelem alkalmazásprogramozási felületét (a DPAPI-t) és a helyi rendszerfiók hitelesítő adatait használja.

A varázsló utolsó lapján tegye a következőket, majd kattintson a **Befejezés** gombra:

-   Ha ezt az összekötőt telepíti először, ebben az esetben ne válassza ki a **Launch connector administrator console to authorize servers** (Összekötő-felügyeleti konzol indítása a kiszolgálók engedélyezéséhez) beállítást. A második (vagy az utolsó) RMS-összekötő telepítését követően válassza ki ezt a beállítást. Ehelyett futtassa újra a varázslót legalább egy másik számítógépen. Legalább két összekötőt telepítenie kell.

-   A második (vagy az utolsó) RMS-összekötő telepítését követően válassza ki az **Összekötő-felügyeleti konzol indítása a kiszolgálók engedélyezéséhez** lehetőséget.

> [!TIP]
> Ekkor ellenőrzési tesztet hajthat végre annak megállapítására, hogy az RMS-összekötő webszolgáltatásai működőképesek-e:
>
> -   Egy webböngészőből csatlakozzon a következőhöz: **http://&lt;összekötő_címe&gt;/_wmcs/certification/servercertification.asmx**, ahol az *&lt;összekötő_címe&gt;* helyére a telepített RMS-összekötő kiszolgálójának címe vagy neve kerül. A sikeres csatlakozást követően a **ServerCertificationWebService** lap jelenik meg.

Ha el kell távolítania az RMS-összekötőt, futtassa újból a varázslót, majd válassza ki az eltávolítási lehetőséget.

## Az RMS-összekötő használatának engedélyezése a kiszolgálók számára
Ha már legalább két számítógépre telepítette az RMS-összekötőt, készen áll az annak használatára beállítani kívánt kiszolgálók és szolgáltatások engedélyezésére. Lehet szó például Exchange Server 2013 vagy SharePoint Server 2013 kiszolgálókról

E kiszolgálók megadásához futtassa az RMS-összekötőfelügyelőt, majd adjon hozzá bejegyzéseket az engedélyezett kiszolgálók listájához. Akkor futtathatja ezt az eszközt, ha kiválasztja az **Összekötő-felügyeleti konzol indítása a kiszolgálók engedélyezéséhez** beállítást a Microsoft Rights Management-összekötő Beállítás varázslójának végén, vagy a varázslótól függetlenül indítja el azt.

E kiszolgálók engedélyezésekor fontolja meg az alábbiakat:

-   A hozzáadott kiszolgálók speciális jogosultságokat kapnak. Az összekötők konfigurálása során az Exchange Server-szerepkörhöz társított összes fiók [felügyelő szerepkör](configure-super-users.md) jogosultságot kap az Azure RMS-ben, amely az RMS-bérlő teljes tartalmához hozzáférést biztosít. Ha szükséges, a felügyelő funkció ekkor automatikusan engedélyezve lesz. A jogosultságok kiterjesztéséből eredő biztonsági kockázat elkerülése érdekében ügyeljen arra, hogy kizárólag azokat a fiókokat adja meg, amelyeket a szervezet Exchange-kiszolgálói használnak. Az FCI-t használó, SharePoint-kiszolgálóként vagy fájlkiszolgálóként konfigurált összes kiszolgáló normál felhasználói jogosultságokat kap.

-   Egyetlen bevitel során több kiszolgálót is hozzáadhat egy Active Directory biztonsági vagy terjesztési csoport, esetleg egy olyan szolgáltatásfiók formájában, amelyet egynél több kiszolgáló használ. E konfiguráció használatakor a kiszolgálócsoport tagjai ugyanazt az RMS-tanúsítványokat kapják, a bármelyikük által védelemmel ellátott tartalmak tekintetében pedig valamennyien tulajdonosokká válnak. Az adminisztratív terhek minimalizálása érdekében javasolt e konfigurációt az egyes kiszolgálók helyett egyedi csoportok esetében használni a szervezet Exchange-kiszolgálóinak vagy egy SharePoint-kiszolgálófarm engedélyezéséhez.

Az **Összekötő használatára jogosult kiszolgálók** lapon kattintson a **Hozzáadás** gombra.

> [!NOTE]
> A kiszolgálók engedélyezése az Azure RMS-ben egyenértékű konfigurációnak felel meg az AD RMS-konfiguráció esetében az NTFS-jogosultságok manuális megadásával a ServerCertification.asmx számára a szolgáltatás vagy a kiszolgáló számítógépfiókjai esetében, illetve a felügyelői jogosultságok manuális megadásával az Exchange-fiókok számára. Az összekötőn nem szükséges NTFS-jogokat alkalmazni a ServerCertification.asmx fájlra.


### Kiszolgáló hozzáadása az engedélyezett kiszolgálók listájához
Az **Allow a server to utilize the connector** (Összekötő használatának engedélyezése egy kiszolgáló számára) oldalon adja meg az objektum nevét, vagy tallózással keresse meg az engedélyezni kívánt objektumot.

Fontos, hogy a megfelelő objektum legyen engedélyezve. Az összekötő használatára kijelölt kiszolgáló esetében a helyszíni szolgáltatást (például Exchange vagy SharePoint) futtató fiókot kell kijelölni engedélyezésre. Ha például az adott szolgáltatás konfigurált szolgáltatásfiókként fut, adja hozzá annak nevét a listához. Ha az adott szolgáltatás Helyi rendszerként fut, adja hozzá a számítógép-objektum nevét (például SERVERNAME$). Ajánlott létrehozni egy olyan csoportot, amely tartalmazza ezeket a fiókokat, majd az egyes kiszolgálók nevei helyett ezt a csoportot megadni.

További információk a különböző kiszolgálói szerepkörökről:

-   Exchange szoftvert futtató kiszolgálók esetén meg kell adnia egy biztonsági csoportot. Ehhez használhatja az alapértelmezett csoportot (**Exchange-kiszolgálók**), amelyet az Exchange automatikusan hoz létre, és amely az erdőben található összes Exchange-kiszolgálót kezeli.

-   SharePointot futtató kiszolgálók esetén:

    -   Ha a SharePoint 2010-kiszolgáló Helyi rendszerként történő futtatásra van konfigurálva (nem használ szolgáltatásfiókot), manuálisan hozzon létre biztonsági csoportot az Active Directory tartományi szolgáltatásokban, majd adja hozzá a jelen konfigurációban a kiszolgálóhoz tartozó számítógépnév-objektumot ehhez a csoporthoz.

    -   Ha a SharePoint-kiszolgáló egy szolgáltatásfiók használatára van konfigurálva (SharePoint 2010 esetén ez az ajánlott, SharePoint 2016 és SharePoint 2013 esetén pedig az egyetlen lehetőség), tegye a következőket:

        1.  Adja hozzá a SharePoint központi felügyeleti szolgáltatást futtató szolgáltatásfiókot, hogy engedélyezze a SharePoint számára annak felügyeleti konzoljáról történő konfigurálását.

        2.  Adja hozzá a SharePoint-alkalmazáskészlethez konfigurált fiókot.

        > [!TIP]
        > Ha ez a két fiók eltérő, az adminisztratív terhek minimalizálása érdekében fontolja meg egyetlen, mindkét fiókot tartalmazó csoport létrehozását.

-   A fájlbesorolási infrastruktúrát használó fájlkiszolgálók esetében a kapcsolódó szolgáltatások Helyi rendszer fiókként futnak, így a fájlkiszolgálókhoz (például SERVERNAME$) tartozó számítógépfiókot vagy az adott számítógépfiókokat tartalmazó csoportot engedélyeznie kell.

Ha befejezte a kiszolgálók hozzáadását a listához, kattintson a **Bezárás** gombra.

Ha még nem tette meg, a telepített RMS-összekötő kiszolgálóinak terheléselosztását most kell konfigurálnia, valamint meg kell fontolnia e kiszolgálók és a most engedélyezett kiszolgálók közötti kapcsolat esetében a HTTPS használatát.

## Terheléselosztás és magas rendelkezésre állás konfigurálása
Az RMS-összekötő második vagy utolsó példányának telepítését követően adja meg az összekötő URL-címéhez tartozó kiszolgálónevet, és konfiguráljon egy terheléselosztási rendszert.

Az összekötő URL-címéhez tartozó kiszolgálónév a felügyelt névtéren belül bármely név lehet. Létrehozhat például egy bejegyzést a DNS-rendszerében a **rmsconnector.contoso.com** címhez, majd konfigurálhatja azt a terheléselosztási rendszerében megadott IP-cím használatára. A névhez nem tartoznak speciális követelmények, és nem kell azt konfigurálni magukon az összekötő-kiszolgálókon sem. Nincs szükség a név internetes feloldására, kivéve, ha az Exchange- és a SharePoint-kiszolgálók az összekötővel az interneten kommunikálnak.

> [!IMPORTANT]
> Javasoljuk, hogy az Exchange- és SharePoint-kiszolgálók ezen összekötő használatára történő konfigurálását követően ne módosítsa a nevet, mivel ellenkező esetben törölni kell az összes IRM-konfigurációt a kiszolgálókról, majd újra kell konfigurálni azokat.

A név DNS-ben történő létrehozását és IP-címre történő konfigurálását követően konfigurálja a terheléselosztást arra a címre, amely az adatforgalmat az összekötő-kiszolgálók felé irányítja át. E célra bármely olyan IP-alapú terheléselosztó használható, amely magában foglalja a Windows Server Hálózati terheléselosztás (NLB) szolgáltatását. További információk: [Terheléselosztás üzembe helyezési útmutatója](http://technet.microsoft.com/library/cc754833%28v=WS.10%29.aspx).

Az NLB-fürt konfigurálásához használja az alábbi beállításokat:

-   Portok: 80 (HTTP) vagy 443 (HTTPS)

    A HTTP és a HTTPS használatának eldöntéséről bővebben a következő szakaszban olvashat.

-   Affinitás: Nincs

-   Elosztási módszer: Egyenlő

Az elosztott terhelésű rendszer (illetve az RMS-összekötő szolgáltatást futtató kiszolgálók) számára megadott név a szervezet RMS-összekötőjének a neve, amelyet a későbbiekben a helyszíni kiszolgálók Azure RMS használatára történő konfigurálásához fog használni.

## Az RMS-összekötő konfigurálása HTTPS használatára
> [!NOTE]
> Ez a konfigurációs lépés opcionális, de végrehajtása további biztonsági intézkedésként javasolt.

Habár a TLS vagy az SSL használata opcionális az RMS-összekötő esetében, alkalmazása HTTP-alapú, biztonsági szempontból érzékeny szolgáltatások esetében javasolt. E konfigurációval hitelesíti az összekötőt futtató kiszolgálókat az összekötőt használó Exchange- és SharePoint-kiszolgálókra. Ezen felül az e kiszolgálókról az összekötőre elküldött összes adat titkosítva lesz.

Ahhoz, hogy az RMS-összekötőt futtató valamennyi kiszolgálón engedélyezni tudja az RMS-összekötő számára a TLS használatát, telepítsen olyan kiszolgálói hitelesítési tanúsítványt, amely tartalmazza az összekötőnek adandó nevet. Ha például a DNS-ben megadott RMS-összekötő neve **rmsconnector.contoso.com**, telepítsen egy olyan kiszolgálói hitelesítési tanúsítványt, amely a tanúsítvány tárgyaként tartalmazza az **rmsconnector.contoso.com** címet köznapi névként. Esetleg adja meg az **rmsconnector.contoso.com** címet a tanúsítvány alternatív nevében DNS-értékként. A tanúsítványnak nem kell tartalmaznia a kiszolgáló nevét. Ezt követően, az IIS-ben kösse ezt a tanúsítványt az alapértelmezett webhelyhez.

Ha a HTTPS lehetőséget használja, győződjön meg arról, hogy az összekötőt futtató összes kiszolgáló rendelkezik olyan érvényes kiszolgálóhitelesítési tanúsítvánnyal, amely az Exchange- és SharePoint-kiszolgálók által megbízhatónak minősített legfelső szintű hitelesítésszolgáltatóhoz kötődik. Ezenkívül ha az összekötő-kiszolgálókhoz tartozó tanúsítványokat kibocsátó hitelesítésszolgáltató (CA) visszavonttanúsítvány-listát (CRL-t) állít ki, az Exchange- és a SharePoint-kiszolgálóknak le kell tudniuk tölteni ezt a CRL-t.

> [!TIP]
> Az alábbi információk és forrásanyagok a kiszolgálóhitelesítési tanúsítvány lekéréséhez és telepítéséhez, valamint ennek a tanúsítványnak az IIS-ben az alapértelmezett webhelyhez történő kötéséhez nyújtanak segítséget:
>
> -   Ha e kiszolgálóhitelesítési tanúsítványok telepítéséhez Active Directory tanúsítványszolgáltatásokat (AD CS) és vállalati hitelesítésszolgáltatót (CA) vesz igénybe, duplikálhatja, majd használhatja a webkiszolgáló tanúsítványsablonját is. E tanúsítványsablon a tanúsítvány tulajdonosának neveként **A kérelem tartalmazza** értéket használja, ami azt jelenti, hogy a tanúsítvány lekérésekor megadhatja a tanúsítvány tulajdonosának nevéhez vagy a tulajdonos alternatív nevéhez tartozó RMS-összekötőnév FQDN-jét.
> -   Ha önálló hitelesítésszolgáltatót használ, vagy a tanúsítványt egy másik vállalattól vásárolja, tekintse meg a TechNet [Web Server (IIS)](http://technet.microsoft.com/library/cc753433%28v=ws.10%29.aspx) (Webkiszolgáló (IIS)) dokumentációs könyvtárának [Configuring Internet Server Certificates (IIS 7)](http://technet.microsoft.com/library/cc731977%28v=ws.10%29.aspx) (Internetes kiszolgálói tanúsítványok konfigurálása (IIS7)) fejezetét.
> -   Az IIS konfigurálásához a tanúsítvány használatára tekintse meg a TechNet [Web Server (IIS)](http://technet.microsoft.com/library/cc753433%28v=ws.10%29.aspx) (Webkiszolgáló (IIS)) dokumentációs könyvtárának [Add a Binding to a Site (IIS 7)](http://technet.microsoft.com/library/cc731692.aspx) (Kötés hozzáadása egy webhelyhez (IIS 7)) fejezetét.

## RMS-összekötő konfigurálása webes proxykiszolgáló számára
Ha az összekötő-kiszolgálók olyan hálózaton vannak telepítve, amely nem rendelkezik közvetlen internetkapcsolattal, és a kimenő internet-hozzáféréshez tartozó webes proxykiszolgálót manuálisan kell konfigurálni, az RMS-összekötőhöz tartozó kiszolgálókon konfigurálnia kell a beállításjegyzéket.

#### Az RMS-összekötő konfigurálása webes proxykiszolgáló használatára

1.  Az RMS-összekötőt futtató összes kiszolgálón nyisson meg egy beállításszerkesztőt, például a Regedit alkalmazást.

2.  Navigáljon a következőhöz: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\AADRM\Connector**

3.  Adja hozzá a **ProxyAddress** karakterláncot, és az ehhez az értékhez tartozó adat legyen a következő: **http://&lt;MyProxyDomainOrIPaddress&gt;:&lt;MyProxyPort&gt;**

    Például: **http://proxyserver.contoso.com:8080**

4.  Zárja be a beállításszerkesztőt, majd indítsa újra a kiszolgálót, vagy az IIS újraindításához használja az IISReset parancsot.

## Az RMS-összekötőfelügyelő eszköz telepítése rendszergazdai számítógépeken
Az RMS-összekötőfelügyelő eszközt olyan számítógépről is futtathatja, amelyen nincs telepítve az RMS-összekötő, ha a számítógép megfelel az alábbi követelményeknek:

-   A következő rendszereket futtató, fizikai vagy virtuális számítógép: Windows Server 2012 vagy Windows Server 2012 R2 (minden kiadás), Windows Server 2008 R2 vagy Windows Server 2008 R2 Service Pack 1 (minden kiadás), Windows 8.1, Windows 8 vagy Windows 7.

-   Legalább 1 GB RAM.

-   Legalább 64 GB lemezterület.

-   Legalább egy hálózati csatoló.

-   Internet-hozzáférés tűzfalon (vagy webproxyn) keresztül.

Az RMS-összekötőfelügyelő telepítéséhez futtassa az alábbi fájlokat:

-   32 bites számítógép esetén: RMSConnectorAdminToolSetup_x86.exe

-   64 bites számítógép esetén: RMSConnectorSetup.exe

Ha még nem töltötte le ezeket a fájlokat, a [Microsoft letöltőközpontból](http://go.microsoft.com/fwlink/?LinkId=314106) letöltheti őket.


## További lépések
Az RMS-összekötő telepítését és konfigurálását követően készen áll, hogy a helyszíni kiszolgálókat annak használatára konfigurálja. Ugorjon a következő témakörre: [Kiszolgálók konfigurálása az Azure Rights Management-összekötő használatához](configure-servers-rms-connector.md).


<!--HONumber=Aug16_HO4-->


