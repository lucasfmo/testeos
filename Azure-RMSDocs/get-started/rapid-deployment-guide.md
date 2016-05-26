---
# required metadata

title: Gyors üzembe helyezési útmutató az Azure Rights Management szolgáltatáshoz | Azure RMS
description:
keywords:
author: cabailey
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: c994d616-cff6-4930-9228-a7f7d198a160

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: esaggese
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Gyors üzembe helyezési útmutató az Azure Rights Management szolgáltatáshoz

*A következőkre vonatkozik: Azure Rights Management, Office 365*

A jelen útmutatóban foglaltak és az **Üzembe helyezés és használat** szakasz konfigurációs információinak figyelembevételével még gyorsabban helyezheti üzembe és veheti használatba az Azure Rights Management (Azure RMS) szolgáltatást, meghatározott forgatókönyvek listájából kiválasztva a megvalósítandó változatot.

E forgatókönyvek a rendszergazdai utasításokat és a hozzájuk tartozó végfelhasználói dokumentációt egyaránt tartalmazzák. A dokumentáció (utasítások vagy bejelentések) végfelhasználóknak történő átadása előtt az üzleti követelményeknek és a meglévő munkafolyamatoknak megfelelően testre kell szabnia azt. A végfelhasználói dokumentáció lehetséges végső kinézetét egy példa utasításkészlet vagy bejelentés szemlélteti.

Minden forgatókönyvhöz tartozik követelménylista, szükség szerint további információkat elérhetővé tevő hivatkozásokkal kiegészítve, így e megoldásokat egymástól függetlenül, bármilyen sorrendben üzembe helyezheti.

Az itt felsorolt forgatókönyvek a legnépszerűbbekből mutatnak ízelítőt. Mivel az Azure RMS a szervezeteken belül és között is számos megvalósítási forgatókönyv szerint használható adatvédelmi célokra, ugyanazon modell használatával saját forgatókönyvek is megadhatók és üzembe helyezhetők saját környezetében, saját felhasználói számára. Az egyes forgatókönyvek előtérbe helyezésével a telepített Azure RMS jobban illeszkedik üzleti céljaihoz. Ezenkívül tapasztalatunk szerint a forgatókönyv-specifikus utasításokat a felhasználók szigorúbban és szisztematikusabban követik, mint például egy bizalmas dokumentumok védelme címmel ellátott általános útmutatást.

Mielőtt ezeket a megoldásokat a felhasználók rendelkezésére bocsátja, lehetséges, hogy széles körű bejelentést kíván majd tenni a végfelhasználók számára, amelyben tudatja velük, hogy a vállalati adatok védelme érdekében bizonyos változások lépnek életbe, ami részükről is bizonyos változásokat igényelhet. Az alábbi táblázatot követően erre látható példa.

> [!NOTE] Ha ezzel az útmutatóval kapcsolatban bármilyen kérdése vagy megjegyzése van, használja az oldal visszajelzési funkcióját, vagy küldjön e-mail üzenetet az [AskIPTeam@Microsoft.com](mailto:%20askipteam@microsoft.com?subject=Rapid%20Deployment%20Guide%20feedback) címre.

## Azure RMS-forgatókönyvek
Az Azure RMS adott üzleti problémákra történő minél gyorsabb alkalmazásának elősegítése érdekében válassza ki az üzleti céljaihoz leginkább illeszkedő forgatókönyveket, és szükség szerint építse be azokat tevékenységébe.



**Küldjön biztonságosan egy Office-fájlt tartalmazó e-mailt egy másik szervezet felhasználóinak, az üzenet elérése nyomon követésének aktiválása mellett (vállalatok közötti együttműködés)**

Példák:

- Árlista, útmutató vagy kiadási terv küldése egy ügyfélnek

- Munkautasítás vagy marketing-specifikáció küldése egy szállítónak

- Ajánlat vagy ajánlatkérés (RFQ) küldése egy partnernek

Lásd: [Forgatókönyv – Office-fájl megosztása egy másik szervezet felhasználóival](scenario-share-office-file-externally.md)

**Biztosítsa, hogy a SharePoint-könyvtárban tárolt dokumentumok feletti ellenőrzés az Ön kezében maradjon**

Példák:

- Szervezeti táblázatok és jelentések

- Csoportközi együttműködés tervezési dokumentumok és egyéb termékek esetében

Lásd: [Forgatókönyv – A SharePointban tárolt dokumentumok feletti ellenőrzés megtartása](scenario-sharepoint.md)

**A vezetők biztonságosan küldhetnek egymásnak jogosultságokhoz kötött információkat e-mailben**

Példák:

- Beszerzési tervek megosztása

- Jogi problémák megvitatása vagy terjesztése

- Információk lehetséges elbocsátásokról és egyéb érzékeny témákról

Lásd: [Forgatókönyv – Jogosultságokhoz kötött információk biztonságos cseréje vezetői szinten](scenario-executives-email.md)

**Egy fájlkiszolgálón található összes fájl automatikus védelemmel történő ellátása**

Példák:

- Házon belül tartandó CAD-dokumentumok a szellemi tulajdon védelme érdekében

- Marketingtervek és időpontok titkosítása a nyilvánosság elől a versenyelőny megőrzése érdekében

Lásd: [Forgatókönyv – Fájlkiszolgáló-megosztáson található fájlok ellátása védelemmel](scenario-fci.md)

**A legbizalmasabb, nagy üzleti jelentőséggel bíró dokumentumok erős védelemmel történő ellátása**

Példák:

- A vállalat egyedi, receptekkel vagy képletekkel kapcsolatos információi

- Magas besorolási szintű átvételi vagy egyesülési tervek

- Természeti erőforrások feltárási adatai

Lásd: [Forgatókönyv – A legértékesebb fájlok védelmének biztosítása](scenario-secure-most-valuable-files.md)

**Bizalmas vállalati e-mailek és mellékletek biztonságos küldése**

Példák:

- A vállalat stratégiai céljai

- Szervezeti diagramok, átszervezési hírek vagy előléptetés-bejelentések

- A vállalati házirenddel kapcsolatos információk

Lásd: [Forgatókönyv – Bizalmas vállalati e-mail küldése](scenario-company-confidential-email.md)

**A munkamappákban lévő Office-fájlok állandó védelemmel történő ellátása**

Példák:

- Bizalmas vállalati projektekhez tartozó dokumentumok helyi szerkesztése

- Helyileg létrehozott, érzékeny vagy jelentős üzleti hatású adatokat tartalmazó táblázatok

- Helyileg tárolt, még elkészítés alatt álló PowerPoint-bemutatók, amelyeknek nem szabad kiszivárogniuk vagy véletlen megosztás során vállalaton kívüli személyek tudomására jutniuk a véglegesítés előtt

Lásd: [Forgatókönyv – Munkahelyi mappák konfigurálása az állandó védelemhez](scenario-work-folders.md)




## Bevezetés előtti hirdetmény a felhasználók számára
Az alábbi kommunikációs üzeneteket használhatja példaként a felhasználók értesítésére, hogy az Azure RMS telepítése változásokat von maga után. Másolja be az alábbi szöveget abba az e-mailbe, amelyet a szervezet egyik vezetőségi tagja (lehetőleg a vezérigazgató) elküld az összes felhasználónak. Fontoljon meg minden olyan szövegváltoztatást, amelynek révén az üzenetet még relevánsabbá teheti a felhasználók és a szervezete számára.

![Példa a felhasználói dokumentáció szalagcímére az Azure RMS gyors telepítéséhez kapcsolódóan](../media/AzRMS_ExampleBanner.png)

### Az adataink védelme érdekében végzett változások
Gondolt valaha arra, hogy egy, a partnereinek tévedésből küldött dokumentum hozzáférését blokkolja? Szerette volna valaha tudni, hogy mely ügyfelei olvasták el a legutóbb kiküldött termékismertetőket? Igényli, hogy bizalmas termékinformációk megosztása során elkerülhesse az illetéktelen személyekkel kapcsolatos aggodalmait?

Mindezek hamarosan lehetségessé válnak, mivel az informatikai osztály a vállalat adatvédelmi megoldásaként a Microsoft Azure Rights Management (Azure RMS) megvalósítását lehetővé tevő változások bevezetéséről döntött. E megoldások zöme automatikusan alkalmazza a szükséges védelmet, anélkül, hogy bármi egyebet kellene tennünk. Egyes változások azonban felhasználói oldalon is változásokat vonnak maguk után, ezekben az esetekben pedig az informatikai osztály információk és utasítások, illetve ügyfélszolgálati támogatás formájában nyújt támogatást a felmerülő kérdések és problémák tisztázásához.

Például a megosztott dokumentumok nyomon követéséhez (és szükség esetén visszahívásához) a következő dokumentumkövető oldalt használhatja majd:

![Azure RMS dokumentumkövetési képernyőfelvételek](../media/AzRMS_Tutorial_5_Screenshots.png)

Ha kíváncsi ennek működésére, tekintse meg a következő 2 perces videót: [Azure RMS dokumentumkövetés és visszavonás](https://channel9.msdn.com/Series/Information-Protection/Azure-RMS-Document-Tracking-and-Revocation)

A szervezet egyik legértékesebb vagyontárgya az információ – az általunk létrehozott, tárolt és a napi rendszerességgel használt adatok. Ezek biztosítanak számunkra versenyelőnyt és tesznek minket sikeressé. Éppen ezért lényeges, hogy megőrizzük az adataink feletti ellenőrzés képességéket, és biztosítsuk, hogy jogosulatlan személyek ne férhessenek azokhoz hozzá.

A megvalósított megoldásokkal megvédhetjük értékes adatainkat, és eszközöket biztosítanak számunkra, hogy megőrizzük az adatok feletti ellenőrzési képességünket. Köszönjük együttműködését a változások megvalósítása során.



<!--HONumber=May16_HO2-->


