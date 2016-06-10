---
# required metadata

title: A Rights Management megosztóalkalmazás felhasználói útmutatója | Azure RMS
description:
keywords:
author: cabailey
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: eaf6d02c-aa36-4915-856e-49bb71ab1484

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: esaggese
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# A Rights Management megosztóalkalmazás felhasználói útmutatója

*A következőkre vonatkozik: Active Directory tartalomvédelmi szolgáltatások, Azure Rights Management, Windows 10, Windows 7 SP1, Windows 8, Windows 8.1*

A Windowshoz készült Microsoft Rights Management (RMS) megosztóalkalmazás segítségével megakadályozhatja fontos dokumentumainak és képeinek jogosulatlan megtekintését, még akkor is, ha elküldi őket e-mailben, vagy egy másik eszközre menti. Ezenkívül az alkalmazás lehetővé teszi azoknak a fájloknak a megnyitását és használatát is, amelyeket mások ugyanezzel a tartalomvédelmi technológiával tettek védetté.

Mindehhez csupán egy számítógépre van szüksége, amelyen egy legalább Service Pack 1 szervizcsomaggal bővített Windows 7 fut. Ezt követően [töltse le a Microsoft webhelyéről ezt az ingyenes alkalmazást, és telepítse](http://go.microsoft.com/fwlink/?LinkId=303970) .

Ha olyan kérdései merülnek fel, amelyekre a jelen útmutató nem ad választ, tekintse meg a [FAQ for Microsoft Rights Management Sharing Application for Windows](http://go.microsoft.com/fwlink/?LinkId=303971) (A Windows rendszerhez készült Microsoft Rights Management megosztóalkalmazással kapcsolatos gyakori kérdések) című témakört. Ez az oldal hibaelhárítási információt is tartalmaz, ha hibákba ütközne.

## Példák az RMS-megosztó alkalmazás használatára
Íme néhány példa arra, hogy miként védheti meg fájljait az RMS megosztóalkalmazás használatával.

|Cél|Útmutatás|
|----------------|------------------|
|**… Pénzügyi adatokat szeretnék biztonságosan megosztani egy megbízható, másik szervezetnél dolgozó személlyel.**<br /><br />Együttműködik egy partnervállalattal, és szeretné elküldeni nekik e-mailben az előre jelzett értékesítési adatokat egy Excel-táblázatban. Azt szeretné, ha meg tudnák tekinteni a számokat, de nem tudnák azokat módosítani.|Az Excel menüszalagján kattintson a **Védett megosztás** gombra, írja be annak a két személynek a nevét, akivel együttműködik a partnervállalatnál, válassza a **Megtekintő – Csak megtekintés** lehetőséget, és kattintson a **Küldés** gombra..<br /><br />Amikor az e-mail megérkezik a partnervállalathoz, csak az e-mail címzettjei tekinthetik meg a táblázatot, és nem menthetik, szerkeszthetik, nyomtathatják ki vagy továbbíthatják azt.<br /><br />Lépésről lépésre: [E-mailben megosztott fájl védelme a Rights Management megosztóalkalmazással](sharing-app-protect-by-email.md).|
|**… Szeretnék biztonságosan elküldeni e-mailben egy dokumentumot valakinek, aki iOS-eszközt használ.**<br /><br />Szeretne elküldeni egy szigorúan bizalmas dokumentumot a munkatársának, akiről tudja, hogy rendszeresen ellenőrzi az e-maileket az iOS-eszközén.|A Fájlkezelőben kattintson a jobb gombbal a fájlra, és válassza a **Védett megosztás** parancsot. fájl elküldése mellékletként a munkatársnak.<br /><br />A címzett megkapja az e-mailt iOS-eszközén. Mivel nem rendelkezik az iPad és iPhone készülékekhez készült Office csomaggal, az e-mailben található hivatkozásra kattint, amely ismerteti a számára a megosztóalkalmazás letöltését, telepíti az iOS-eszközökhöz készült verziót, majd megtekinti a dokumentumot¹.<br /><br />Lépésről lépésre: [E-mailben megosztott fájl védelme a Rights Management megosztóalkalmazással](sharing-app-protect-by-email.md).|
|**… Szeretnék utánanézni, hogy ki és mikor nyitotta meg a védett dokumentumaimat, és ha szükséges, visszavonni a hozzáférést.**<br /><br />Lehetséges beszállítóival biztonságosan megosztott egy bizalmas tervdokumentumot, és most szeretné látni, hogy ki, mikor és honnan fért hozzá. Később, miután az egyik beszállító megkapja az üzletet, szeretné visszavonni a hozzáférést az eredeti dokumentumhoz, hogy a korábbi megosztás résztvevői ne tudják elolvasni.|Miután megosztott egy dokumentumot e-mailben, nyissa meg a [dokumentumkövetési webhelyet](http://go.microsoft.com/fwlink/?LinkId=529562) annak ellenőrzésére, hogy ki és mikor fért hozzá a dokumentumhoz. Amikor szeretné megszüntetni a megosztást, válassza a hozzáférés visszavonása lehetőséget.<br /><br />Lépésről lépésre: [Dokumentumok nyomon követése és visszavonása az RMS megosztóalkalmazás használata során](sharing-app-track-revoke.md).|
|**… Szeretnék elolvasni egy e-mailben kapott mellékletet, amely e-mailben biztonságosan megosztott fájlmellékletként érkezett, de nem tudom, mert a vállalatom nem használja a Rights Management szolgáltatást.**<br /><br />Az e-mailt olyasvalaki küldte, akiben megbízik, mivel régebben már kötöttek üzletet, és feltételezi, hogy egy új üzleti lehetőséggel kapcsolatos információkat küldött.|Kövesse az e-mailben szereplő utasításokat, és kattintson a hivatkozásra a Microsoft Rights Management szolgáltatásra való feliratkozáshoz. A Microsoft ellenőrzi, hogy a szervezet nem rendelkezik az Azure Rights Managementet tartalmazó előfizetéssel, elküld egy e-mailt az ingyenes regisztrációs folyamat végrehajtásához, amit követően bejelentkezhet az új fiókkal. Kattintson az e-mailben a második hivatkozásra a Rights Management megosztóalkalmazás telepítéséhez. Ezt követően meg tudja nyitni az e-mail mellékletét, amelyben az új üzleti lehetőségről olvashat.<br /><br />Lépésről lépésre: [A Rights Management szolgáltatásban védetté tett fájlok megtekintése és használata](sharing-app-view-use-files.md).|
|**… Szeretném védetté tenni a bizalmas vállalati fájlokat a laptopomon, hogy a vállalatomon kívüli személyek ne férhessenek hozzájuk.**<br /><br />Sokat utazik, és a laptopján egy gyakran használt mappát és az abban lévő fájlokat védetté kell tennie a jogosulatlan hozzáféréssel szemben.|Telepítve van az RMS-megosztó alkalmazás a laptopján. A Fájlkezelőben egy sablon használatával gyorsan védetté tudja tenni a fájlokat. Ha ellopják a laptopját, nyugodt maradhat afelől, hogy a vállalatán kívüli személyek nem férhetnek hozzá ezekhez a dokumentumokhoz.<br /><br />Lépésről lépésre: [Fájl védelme egy eszközön (helyi védelem) a Rights Management megosztóalkalmazással](sharing-app-protect-in-place.md).|
¹ PDF Rendering Powered by Foxit (Foxit PDF-elrendezés). Copyright © 2003–2014 by Foxit Corporation.

## Művelet
> [!NOTE]
> További műszaki információt (például a támogatott fájltípusokkal és az alkalmazás vállalati hálózatra történő telepítésével kapcsolatban) a [Rights Management sharing application administrator guide](sharing-app-admin-guide.md) (A Rights Management megosztóalkalmazás rendszergazdai kézikönyve) című témakörben tekinthet meg..

-   [A megosztóalkalmazás letöltése és telepítése](install-sharing-app.md)

-   [Eszközön lévő fájl védelme (helyi védelem)](sharing-app-protect-in-place.md)

-   [E-mailben megosztott fájl védelme](sharing-app-protect-by-email.md)

-   [Dokumentumok nyomon követése és visszavonása](sharing-app-track-revoke.md)

-   [Védett fájlok megtekintése és használata](sharing-app-view-use-files.md)

-   [Fájl védelmének eltávolítása](sharing-app-remove-protection.md)

-   [Billentyűparancsok használata](sharing-app-keyboard-shortcuts.md)

-   [Beállítások megadása a párbeszédpanelen](sharing-app-dialog-box.md)





<!--HONumber=Apr16_HO4-->


