---
title: "A Rights Management megosztóalkalmazás műszaki áttekintése | Azure RMS"
description: "A Microsoft Rights Management megosztóalkalmazás a Microsoft Windows rendszerre és más platformokra opcionálisan letölthető alkalmazás, amely a következő funkciókkal rendelkezik."
author: cabailey
manager: mbaldwin
ms.date: 07/15/2016
ms.topic: article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: f7b13fa4-4f8e-489a-ba46-713d7a79f901
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 26b043f1f9e7a1e0cd00c2f31c28f7d6685f0232
ms.openlocfilehash: d5e1c7969d2125c4f66d6dcea3bde0c81a7de1f3


---


# A Microsoft Rights Management megosztóalkalmazás műszaki áttekintése és védelmi adatai

>*A következőkre vonatkozik: Active Directory tartalomvédelmi szolgáltatások, Azure Rights Management, Windows 10, Windows 7 SP1, Windows 8, Windows 8.1*


A Microsoft Rights Management megosztóalkalmazás a Microsoft Windows rendszerre és más platformokra opcionálisan letölthető alkalmazás, amely a következő funkciókkal rendelkezik:

-   Egyetlen fájl vagy több fájl csoportos védelme, valamint egy kiválasztott mappában található összes fájl védelme.

-   Teljes támogatást nyújt bármely fájltípus védelméhez, valamint beépített nézőkét biztosít a leggyakrabban használt szöveg- és képfájltípusokhoz.

-   Az RMS-védelmet nem támogató fájlok általános védelme.

-   Teljes kompatibilitás az Office Information Rights Management (IRM) használatával védett fájlokkal.

-   Teljes kompatibilitás a Fájlbesorolási infrastruktúrával (FCI) védett PDF-fájlokkal és a támogatott PDF-szerkesztőeszközökkel.

A Microsoft Rights Management megosztóalkalmazás az új [AD RMS-ügyfél 2.1 futtatókörnyezetet](http://www.microsoft.com/download/details.aspx?id=38396) használja. Az AD RMS 2.1 adottságait kihasználó Microsoft Rights Management megosztóalkalmazás egyszerű védelmet és fogyasztói élményt biztosít a végfelhasználóknak.

Az RMS 2013. októberi kibocsátása óta natív módon védheti dokumentumait az Office 2010 használatával, és elküldheti azokat más vállalatoknál dolgozóknak, akik az Azure RMS használatával tekinthetik meg az így kapott dokumentumokat. Továbbá ebben a kiadásban, ha az AD RMS-t a 2. titkosítási módban alkalmazza, használhatja az RMS-t egyéni felhasználók számára, és felhasználhatja más, Azure RMS-t használó vállalatok felhasználóinak tartalmait. További információ a 2. titkosítási módról: [AD RMS Cryptographic Modes](http://technet.microsoft.com/library/hh867439%28v=ws.10%29.aspx) (AD RMS titkosítási módok).

Telepítési információk: [A Microsoft Rights Management megosztóalkalmazás automatikus központi telepítése](sharing-app-admin-guide.md#automatic-deployment-for-the-microsoft-rights-management-sharing-application)

## Védelmi szintek – natív és általános
A Microsoft Rights Management megosztóalkalmazás két különböző szintű védelmet támogat, amelyek részleteit az alábbi táblázat tartalmazza.

|Védelem típusa|Natív|Általános|
|----------------------|----------|-----------|
|Leírás|A szöveg- és képfájlok, a Microsoft Office (Word, Excel, PowerPoint) fájlok, a .pdf fájlok és az egyéb, AD RMS-t támogató fájltípusok esetében a natív védelem erős szintű védelmet biztosít, amelybe beletartozik a titkosítás és a jogok (engedélyek) érvényesítése is.|Minden más alkalmazás és fájltípus esetében általános szintű védelem biztosított, ami magában foglalja a .pfile típusú fájlbeágyazást, valamint a hitelesítést, amellyel ellenőrizhető, hogy egy felhasználó jogosult-e a fájl megnyitására.|
|Protection|A fájlok teljesen titkosítottak, a védelem pedig a következő módokon érvényesül:<br /><br />– A fájlt e-mailben megkapó, vagy a fájlhoz fájl- vagy megosztási engedélyekkel hozzáférő felhasználóknak sikeresen hitelesíteniük kell magukat a védett fájl megtekintése előtt.<br /><br />– Ezenkívül ha a tartalmat egy IP-megtekintőben (a védett szöveg- és képfájlok esetében) vagy egy társított alkalmazásban (minden más támogatott fájltípus esetében) jelenítik meg, a fájl védelem alá helyezésekor a rendszer a tartalom tulajdonosa által beállított használati engedélyeket és házirendet is érvényesíti.|A fájlvédelem a következő módokon érvényesül:<br /><br />– A fájl megnyitásához szükséges engedéllyel és hozzáféréssel rendelkező ügyfeleknek sikeresen hitelesíteniük kell magukat a védett fájl megtekintése előtt. Ha a hitelesítés sikertelen, a fájl nem nyitható meg.<br /><br />– Megjelennek a fájl védelem alá helyezésekor a tartalom tulajdonosa által beállított használati engedélyek és a házirend, amelyekből a hitelesített felhasználók megismerhetik az alkalmazni kívánt használati házirendet.<br /><br />– Naplózásra kerül minden alkalom, amikor a hitelesített felhasználók megnyitnak vagy elérnek egy fájlt, azonban a támogatást nem biztosító alkalmazások nem érvényesítenek használati jogokat.|
|Fájltípusonkénti alapértelmezés|A következő fájltípusokhoz tartozó alapértelmezett szintű védelem:<br /><br />– Szöveg- és képfájlok<br /><br />– Microsoft Office-fájlok (Word, Excel, PowerPoint)<br /><br />– Portable document format (.pdf)<br /><br />További információt a következő szakaszban találhat: [Támogatott fájltípusok és fájlnévkiterjesztések](#supported-file-types-and-file-name-extensions).|Ez az alapértelmezett védelem minden más fájltípus esetében (például .vsdx, .rtf stb.), amelyet a teljes védelem nem támogat.|
Az RMS megosztóalkalmazás által beállított alapértelmezett védelmi szint megváltoztatható. Az alapértelmezett védelmi szint átállítható natívról általánosra, általánosról natívra, és akár meg is tilthatja, hogy az RMS megosztóalkalmazás bármilyen védelmet beállítson. További tudnivalókat a jelen dokumentum [A fájlok alapértelmezett védelmi szintjének módosítása](#changing-the-default-protection-level-of-files) című szakaszában találhat.

## Támogatott fájltípusok és fájlnévkiterjesztések
Az alábbi táblázat a Microsoft Rights Management megosztóalkalmazás által natívan támogatott fájlokat ismerteti. E fájltípusok esetében az eredeti fájlnévkiterjesztés a natív védelem alkalmazása esetén megváltozik, és a fájlok írásvédettekké válnak.

Továbbá, amikor az RMS megosztóalkalmazás natív védelmet biztosít egy olyan Word-, Excel- vagy PowerPoint-fájlnak, amelyet a felhasználók megosztással védenek, akkor ez a művelet automatikusan létrehoz egy második fájlt, amely az eredeti fájl másolata ugyanazon a fájlnéven, csak **.ppdf** fájlnévkiterjesztéssel¹. A fájl ezen változata biztosítja, hogy az RMS megosztóalkalmazást telepített címzettek mindig meg tudják nyitni a natív védelemmel védett fájlokat.

Az általános védelemmel ellátott fájlok esetében az eredeti fájlnévkiterjesztés mindig .pfile fájlnévkiterjesztésre változik.

> [!WARNING]
> Ha olyan tűzfalakat, webes proxykat vagy biztonsági szoftvereket használ, amelyek a fájlnévkiterjesztés alapján hajtanak végre bizonyos műveleteket, lehet, hogy be kell azokat állítania, hogy engedélyezzék ezeket az új fájlnévkiterjesztéseket.

|Eredeti fájlnévkiterjesztés|Az RMS-védelemmel ellátott fájl fájlnévkiterjesztése|
|--------------------------------|-------------------------------------|
|.txt|.ptxt|
|.xml|.pxml|
|.jpg|.pjpg|
|.jpeg|.ppng|
|.pdf|.ppdf|
|.png|.ppng|
|.tif|.ptif|
|.tiff|.ptiff|
|.bmp|.pbmp|
|.gif|.pgif|
|.giff|.pgiff|
|.jpe|.pjpe|
|.jfif|.pjfif|
|.jt|.pjt|
¹ PDF Rendering Powered by Foxit (Foxit PDF-elrendezés). Copyright © 2003–2014 by Foxit Corporation.

Az alábbi táblázat azokat a fájltípusokat ismerteti, amelyeket a Microsoft Rights Management megosztóalkalmazás natív módon támogat a Microsoft Office 2016, az Office 2013 és az Office 2010 alkalmazáscsomagban. E fájlok esetében a fájlnévkiterjesztés az RMS-védelem alkalmazása esetén is ugyanaz marad.

|Az Office által támogatott fájltípusok|Az Office által támogatott fájltípusok|
|----------------------------------|----------------------------------|
|.doc<br /><br />.docm<br /><br />.docx<br /><br />.dot<br /><br />.dotm<br /><br />.dotx<br /><br />.potm<br /><br />.potx<br /><br />.pps<br /><br />.ppsm<br /><br />.ppsx<br /><br />.ppt<br /><br />.pptm|.pptx<br /><br />.thmx<br /><br />.xla<br /><br />.xlam<br /><br />.xls<br /><br />.xlsb<br /><br />.xlt<br /><br />.xlsm<br /><br />.xlsx<br /><br />.xltm<br /><br />.xltx<br /><br />.xps|

### A fájlok alapértelmezett védelmi szintjének módosítása
S beállításjegyzék módosításával lehet megváltoztatni azt, hogy az RMS megosztóalkalmazás hogyan védje a fájlokat. Beállíthatja például, hogy a natív védelmet támogató fájlokat általános védelemmel védje az RMS megosztóalkalmazás.

Néhány ok arra, hogy miért érdemes ezt elvégezni:

-   Hogy biztosan minden felhasználó meg tudja nyitni a fájlt mobil eszközön.

-   Hogy biztosan minden felhasználó meg tudja nyitni a fájlt akkor is, ha nincs olyan alkalmazása, amely támogatja a natív védelmet.

-   Ha olyan védelmi rendszert szeretne használni, amely a fájlnévkiterjesztés alapján hajt végre bizonyos műveleteket, és beállítható ugyan a .pfile fájlnévkiterjesztés elfogadására, de arra nem, hogy több fájlnévkiterjesztés esetében is elfogadja a natív védelmet.

Ehhez hasonlóan beállíthatja az RMS megosztóalkalmazást úgy, hogy natív védelmet alkalmazzon azokra a fájlokra, amelyek alapértelmezés szerint általános védelmet kapnának. Ez akkor lehet hasznos, ha az RMS API-kat támogató alkalmazása van – például egy belső fejlesztők által írt üzleti alkalmazás vagy egy független szoftverfejlesztőtől vásárolt alkalmazás.

Az RMS megosztóalkalmazás beállítható úgy is, hogy blokkolja a fájlok védelmét (azaz se natív, se általános védelmet ne alkalmazzon). Erre akkor lehet például szükség, ha egy automatikus alkalmazásnak vagy szolgáltatásnak kell megnyitnia egy adott fájlt, hogy feldolgozza annak tartalmát. Ha blokkolja egy fájltípus védelmét, a felhasználók nem használhatják az RMS megosztóalkalmazást az adott fájltípusú fájlok védelmére. Ha mégis megpróbálják, akkor egy üzenet jelenik meg, amely arról tájékoztatja őket, hogy a rendszergazda nem engedélyezi a védelmet, így a fájlvédelmi műveletet vissza kell vonniuk.

Ha azt szeretné beállítani, hogy az RMS megosztóalkalmazás általános fájlvédelmet alkalmazzon az összes olyan fájlra, amely alapértelmezés szerint natív védelmet kapna, az alábbi módosítást kell végrehajtania a beállításjegyzékben:

1.  **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\RMSSharingApp\FileProtection**: Hozzon létre egy * nevű új kulcsot.

    Ez a beállítást az összes fájlnévkiterjesztést jelöli.

2.  Az újonnan hozzáadott HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\RMSSharingApp\FileProtection\\\\* kulcsban hozzon létre egy új karakterláncértéket (REG_SZ) **Encryption** néven, amelynek adatértéke **Pfile**.

    Ennek a beállításnak a hatására az RMS megosztóalkalmazás általános védelmet fog alkalmazni.

E két beállítás hatására az RMS megosztóalkalmazás általános védelmet alkalmaz minden olyan fájlra, amelynek van fájlnévkiterjesztése. Ha ez a cél, akkor további beállításokra nincs is szükség. Adott fájltípusokat megadhat azonban kivételként, hogy azok mégis natív védelmet kapjanak. Ehhez további három beállításjegyzék-bejegyzést kell módosítania fájltípusonként:

1.  **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\RMSSharingApp\FileProtection**: Adjon hozzá egy új kulcsot, amelynek neve megegyezik a fájlnév kiterjesztésével (az előtte álló pont nélkül).

    A .docx fájlnév-kiterjesztésű fájlok esetén például hozzon létre egy **DOCX** nevű kulcsot.

2.  Az újonnan hozzáadott fájltípuskulcsban (például **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\RMSSharingApp\FileProtection\DOCX**) hozzon létre egy új DWORD értéket **AllowPFILEEncryption** néven, amelynek értéke **0**.

3.  Az újonnan hozzáadott fájltípuskulcsban (például **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\RMSSharingApp\FileProtection\DOCX**) hozzon létre egy új karakterláncértéket **Encryption** néven, amelynek értéke **Native**.

E beállítások eredményeként minden fájl általános védelmet kap, kivéve a .docx fájlnév-kiterjesztésűeket, amelyekre natív védelmet alkalmaz az RMS megosztóalkalmazás.

Ismételje meg a fenti három lépést minden olyan fájltípus esetében, amelyet kivételként szeretne meghatározni, mert támogatják a natív védelmet, és azt szeretné, hogy az RMS megosztóalkalmazás ne általános védelemmel lássa el őket.

Más forgatókönyvek esetében is végrehajthat hasonló beállításjegyzék-módosításokat, ha módosítja az alábbi értékeket támogató **Encryption** karakterlánc értékét:

-   **Pfile**: Általános védelem

-   **Native**: Natív védelem

-   **Off**: Védelem tiltása

## Lásd még:
[A Rights Management megosztóalkalmazás felhasználói útmutatója](sharing-app-user-guide.md)




<!--HONumber=Aug16_HO4-->


