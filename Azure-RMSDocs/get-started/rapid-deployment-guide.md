---
title: "Gyors üzembe helyezési útmutató az Azure Rights Management szolgáltatáshoz | Azure RMS"
description: "Útmutató az Azure Rights Management(Azure RMS) gyors telepítéséhez és használatához, amellyel védheti vállalata adatait. Kezdésképpen a meghatározott forgatókönyvek listájából válassza ki a megvalósítandó változatot."
author: cabailey
manager: mbaldwin
ms.date: 08/25/2016
ms.topic: get-started-article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: c994d616-cff6-4930-9228-a7f7d198a160
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 81426cf43f31625c6e83d443fa925f6426eb89da
ms.openlocfilehash: 715290d2417df3b386d8e5b8a784e964355d4e15


---

# Gyors üzembe helyezési útmutató az Azure Rights Management szolgáltatáshoz

>*A következőkre vonatkozik: Azure Rights Management, Office 365*

A jelen útmutatóban foglaltak és az **Üzembe helyezés és használat** szakasz konfigurációs információinak figyelembevételével még gyorsabban helyezheti üzembe és veheti használatba az Azure Rights Management (Azure RMS) szolgáltatást, meghatározott forgatókönyvek listájából kiválasztva a megvalósítandó változatot.

E forgatókönyvek a rendszergazdai utasításokat és a hozzájuk tartozó végfelhasználói dokumentációt egyaránt tartalmazzák. A dokumentáció (utasítások vagy bejelentések) végfelhasználóknak történő átadása előtt az üzleti követelményeknek és a meglévő munkafolyamatoknak megfelelően testre kell szabnia azt. A végfelhasználói dokumentáció lehetséges végső kinézetét egy példa utasításkészlet vagy bejelentés szemlélteti.

Minden forgatókönyvhöz tartozik követelménylista, szükség szerint további információkat elérhetővé tevő hivatkozásokkal kiegészítve, így e megoldásokat egymástól függetlenül, bármilyen sorrendben üzembe helyezheti.

Az itt felsorolt forgatókönyvek a legnépszerűbbekből mutatnak ízelítőt. Mivel az Azure RMS a szervezeteken belül és között is számos megvalósítási forgatókönyv szerint használható adatvédelmi célokra, ugyanazon modell használatával saját forgatókönyvek is megadhatók és üzembe helyezhetők saját környezetében, saját felhasználói számára. Az egyes forgatókönyvek előtérbe helyezésével a telepített Azure RMS jobban illeszkedik üzleti céljaihoz. Ezenkívül tapasztalatunk szerint a forgatókönyv-specifikus utasításokat a felhasználók szigorúbban és szisztematikusabban követik, mint például egy bizalmas dokumentumok védelme címmel ellátott általános útmutatást.

Mielőtt ezeket a megoldásokat a felhasználók rendelkezésére bocsátja, lehetséges, hogy széles körű bejelentést kíván majd tenni a végfelhasználók számára, amelyben tudatja velük, hogy a céges adatok védelme érdekében bizonyos változások lépnek életbe, ami részükről is bizonyos változásokat igényelhet. Az alábbi táblázatot követően erre látható példa.

> [!NOTE]
> Ha ezzel az útmutatóval kapcsolatban bármilyen kérdése vagy megjegyzése van, használja az oldal visszajelzési funkcióját, vagy küldjön e-mail üzenetet az [AskIPTeam@Microsoft.com](mailto:%20askipteam@microsoft.com?subject=Rapid%20Deployment%20Guide%20feedback) címre.

## Azure RMS-forgatókönyvek
Az Azure RMS adott üzleti problémákra történő minél gyorsabb alkalmazásának elősegítése érdekében válassza ki az üzleti céljaihoz leginkább illeszkedő forgatókönyveket, és szükség szerint építse be azokat tevékenységébe.



**Biztonságosan küldhet Office-fájlt tartalmazó e-mailt egy másik szervezet felhasználóinak, hiszen nyomon követheti a hozzáféréseket (vállalatok közötti együttműködés)**

Példák:

- Árlista, ütemterv vagy kiadásütemezés küldése egy ügyfélnek

- Megrendelés vagy marketingspecifikáció küldése egy szállítónak

- Ajánlat vagy ajánlatkérés (RFQ) küldése egy partnernek

Lásd: [Forgatókönyv – Office-fájl megosztása egy másik szervezet felhasználóival](scenario-share-office-file-externally.md)

**Biztosítsa, hogy a SharePoint-könyvtárban tárolt dokumentumok feletti ellenőrzés az Ön kezében maradjon**

Példák:

- Részlegek szerinti táblázatok és jelentések

- Csoportközi együttműködés tervezési dokumentumok és egyéb termékek esetében

Lásd: [Forgatókönyv – A SharePointban tárolt dokumentumok feletti ellenőrzés megtartása](scenario-sharepoint.md)

**A vezetők biztonságosan küldhetnek egymásnak bizalmas információkat e-mailben**

Példák:

- Beszerzési tervek megosztása

- Jogi problémák megvitatása vagy közzététele

- Információk lehetséges elbocsátásokról és egyéb érzékeny témákról

Lásd: [Forgatókönyv – Bizalmas információk biztonságos cseréje vezetői szinten](scenario-executives-email.md)

**Egy fájlkiszolgálón található összes fájl automatikus védelemmel történő ellátása**

Példák:

- Házon belül tartandó CAD-dokumentumok a szellemi tulajdon védelme érdekében

- Marketingtervek és időpontok titkosítása a nyilvánosság elől a versenyelőny megőrzése érdekében

Lásd: [Forgatókönyv – Fájlkiszolgáló-megosztáson található fájlok ellátása védelemmel](scenario-fci.md)

**A legbizalmasabb, nagy üzleti jelentőséggel bíró dokumentumok erős védelemmel történő ellátása**

Példák:

- A cég egyedi módszereivel vagy megoldásaival kapcsolatos információk

- Kiemelt felvásárlási vagy fúziós tervek

- Természeti erőforrások feltárási adatai

Lásd: [Forgatókönyv – A legértékesebb fájlok védelmének biztosítása](scenario-secure-most-valuable-files.md)

**Bizalmas céges e-mailek és mellékletek biztonságos küldése**

Példák:

- A cég stratégiai céljai

- Szervezeti diagramok, átszervezési hírek vagy előléptetés-bejelentések

- A céges házirenddel kapcsolatos információk

Lásd: [Forgatókönyv – Bizalmas céges e-mail küldése](scenario-company-confidential-email.md)

**A Munkahelyi mappákban lévő Office-fájlok állandó védelemmel történő ellátása**

Példák:

- Bizalmas céges projektekhez tartozó dokumentumok helyi szerkesztése

- Helyileg létrehozott, érzékeny vagy jelentős üzleti hatású adatokat tartalmazó táblázatok

- Helyileg tárolt, még elkészítés alatt álló PowerPoint-bemutatók, amelyeknek nem szabad kiszivárogniuk vagy véletlen megosztás során vállalaton kívüli személyek tudomására jutniuk a véglegesítés előtt

Lásd: [Forgatókönyv – Munkahelyi mappák konfigurálása az állandó védelemhez](scenario-work-folders.md)




## Bevezetés előtti hirdetmény a felhasználók számára
Az alábbi üzenetet használhatja mintaként, amikor értesíti a felhasználókat arról, hogy az Azure RMS bevezetése változásokat von maga után. Másolja be az alábbi szöveget abba az e-mailbe, amelyet a szervezet egyik vezetőségi tagja (lehetőleg a vezérigazgató) elküld az összes felhasználónak. Fontoljon meg minden olyan szövegváltoztatást, amelynek révén az üzenetet még relevánsabbá teheti a felhasználók és a szervezete számára.

![Példa a felhasználói dokumentáció szalagcímére az Azure RMS gyors telepítéséhez kapcsolódóan](../media/AzRMS_ExampleBanner.png)

### Az adataink védelme érdekében végzett változások
Került már valaha olyan helyzetbe, hogy a partnereinek tévedésből küldött dokumentum elérését blokkolnia kellett volna? Szerette volna valaha tudni, hogy mely ügyfelei olvasták el a legutóbb kiküldött termékismertetőket? Szeretné biztosan tudni, hogy a megosztott bizalmas termékinformációk semmiképp sem kerülnek illetéktelen személyekhez?

Mindezek hamarosan lehetségessé válnak, mivel az informatikai osztály a vállalat adatvédelmi megoldásaként a Microsoft Azure Rights Management (Azure RMS) megvalósítását lehetővé tevő változások bevezetéséről döntött. E megoldások zöme automatikusan alkalmazza a szükséges védelmet, anélkül, hogy bármi egyebet kellene tennünk. Egyes változások azonban felhasználói oldalon is változásokat vonnak maguk után, ezekben az esetekben pedig az informatikai osztály információk és utasítások, illetve ügyfélszolgálati támogatás formájában nyújt támogatást a felmerülő kérdések és problémák tisztázásához.

Például a megosztott dokumentumok nyomon követéséhez (és szükség esetén visszahívásához) a következő dokumentumkövető oldalt használhatja majd:

![Azure RMS dokumentumkövetési képernyőfelvételek](../media/AzRMS_Tutorial_5_Screenshots.png)

Ha kíváncsi ennek működésére, tekintse meg a következő kétperces videót: [Azure RMS – dokumentumkövetés és -visszavonás](https://channel9.msdn.com/Series/Information-Protection/Azure-RMS-Document-Tracking-and-Revocation)

A szervezet egyik legértékesebb vagyontárgya az információ – az általunk létrehozott, tárolt és a napi rendszerességgel használt adatok. Ezek biztosítanak számunkra versenyelőnyt és tesznek minket sikeressé. Éppen ezért lényeges, hogy megőrizzük az ellenőrzést az adataink felett, és biztosítsuk, hogy jogosulatlan személyek ne férhessenek azokhoz hozzá.

A bevezetés alatt álló megoldások biztosítják az értékes adatok védelmét, és eszközöket kínálnak az ellenőrzés megvalósításához. Köszönjük együttműködését a változások megvalósítása során.




<!--HONumber=Aug16_HO4-->


