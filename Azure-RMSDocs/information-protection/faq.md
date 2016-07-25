---
title: "Gyakori kérdések az Azure Information Protection előzetes kiadásáról | Azure Information Protection"
description: 
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 07/20/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 4b595b6a-7eb0-4438-b49a-686431f95ddd
ms.reviewer: adhall
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: e60cd910a8e995a2681d7eb87a13f815183d9124
ms.openlocfilehash: 846578a84df383821a64d32ce6dd69290a5fdee9


---

# Gyakori kérdések az Azure Information Protection előzetes kiadásáról

*A következőkre vonatkozik: Azure Information Protection előzetes kiadása*

Kérdése van az Azure Information Protection előzetes kiadásával kapcsolatban?  Itt választ kaphat rá. 

Ez a lista várhatóan gyakran frissül, mivel egyes információk átkerülnek a fő dokumentációba, valamint az ügyfelektől kapott új kérdéseket is hozzáadunk. 

## Mire használható az Azure Information Protection, és milyen korlátozások vonatkoznak rá jelenleg?

Ez az előzetes kiadás egy Information Protection elnevezésű sávval bővíti a Microsoft Office-alkalmazásokat, amelyen megtekinthetők és módosíthatók az adatokhoz hozzárendelt besorolási címkék. A besorolás elvégezhető manuálisan, a kapott ajánlás szerint, vagy automatikusan is. A megadott besorolások esetében az Azure Rights Management-sablon használható az adatok védelmére.  

A besorolási címkék és a viselkedés az Azure-portálon konfigurálható. Az alapértelmezett beépített házirendek segítségével nagyon gyorsan kiértékelheti az Azure Information Protectiont, vagy az igényeinek megfelelő saját házirendeket állíthat össze. Módosíthatja a színeket, a neveket és a felhasználók számára látható besorolási címkék sorrendjét. Beállíthatja az elemleírásokat és a besorolás vizuális jelölését, például a fejlécet, láblécet vagy vízjelet.

Tekintse meg a gyors üzembe helyezési oktatóanyag néhány perces gyakorlati bemutatóját: [Azure Information Protection gyors üzembe helyezési oktatóanyaga](infoprotect-quick-start-tutorial.md).

Ne feledje, hogy az előzetes kiadásban kipróbálhatja az új **Premium P2 szolgáltatáscsomagot**, és néhány speciális funkció, például az automatikus és az ajánlott címkézés nem feltétlenül érhető el magától értetődően a jelenlegi csomagjában. A különböző szolgáltatáscsomagokkal (Azure Information Protection Premium P1 és Azure Information Protection Premium P2) kapcsolatos információ a következő blogbejegyzésben található: [Introducing Enterprise Mobility + Security](https://blogs.technet.microsoft.com/enterprisemobility/2016/07/07/introducing-enterprise-mobility-security/) (A nagyvállalati mobilitás és adatvédelem bevezetése).

Erre az előzetes kiadásra az alábbi korlátozások vonatkoznak. Kövesse figyelemmel a [nagyvállalati mobilitással és biztonsággal foglalkozó blogot](https://blogs.technet.microsoft.com/enterprisemobility/?product=azure-rights-management-services) és a [Yammer-helyet](https://www.yammer.com/askipteam/#/threads/inGroup?type=in_group&feedId=8652489&view=all), mert itt jelentjük be a további funkciók és képességek elérhetővé válásának időpontját:

- A besorolás és a címkézés nincs központilag naplózva.

- Csak angol nyelvű címkenevek és elemleírások adhatók meg.

- Az automatikus besorolás feltételei csak kifejezések vagy minták lehetnek.

- A Windows Fájlkezelőben nem lehet fájlokat besorolni.

- A mobileszközökre (iOS és Android) és Mac számítógépekre készült Office-alkalmazások, valamint az Office Web Apps (Office Online) még nem támogatottak.

- Nincs integráció az Exchange Online-nal és a SharePoint Online-nal.

- Az SDK nem érhető el partnerek és a fejlesztők számára.

## Milyen előfizetésre van szükség az Azure Information Protection kipróbálásához?

Az előzetes kiadáshoz bármelyik előfizetést használhatja, amennyiben az tartalmazza az Azure Rights Managementet. Az Azure Information Protection minden régióban elérhető. Az előfizetési lehetőségekről további információt és az ingyenes próbaverzió hivatkozásait az [Azure RMS követelmények: Az Azure RMS-t támogató felhőalapú előfizetések](../get-started/requirements-subscriptions.md) című cikkben találja.

Rendelkeznie kell Azure-előfizetéssel ahhoz, hogy konfigurálni tudja az Azure Information Protection-házirendeket az Azure-portálon. Ha a szervezete még nem rendelkezik Azure-előfizetéssel, akkor igényelhet egy ingyenes próbaverziót: Keresse fel az [Ismerkedés az Azure szolgáltatással](https://account.windowsazure.com/organization) oldalt, és kövesse az utasításokat.

Az előfizetés követelményeinek esetleges változásairól szóló bejelentések a [nagyvállalati mobilitással és biztonsággal foglalkozó blogban](https://blogs.technet.microsoft.com/enterprisemobility/?product=azure-rights-management-services) jelennek meg.

## Ha az Azure Information Protection előzetes kiadása most nyilvánosan elérhető, miért nem található az Azure-portálon?

Jelenleg az alábbi hivatkozást kell megnyitnia az Azure Information Protection megjelenítéséhez a portálon: https://portal.azure.com/?Microsoft_Azure_InformationProtection=true

Ezután a menüben kattintson a **Tallózás** gombra, és kezdje el begépelni az "Information Protection" szöveget a Szűrő mezőbe. A találatokban kattintson az **Azure Information Protection** elemre.

## Szükséges-e globális rendszergazda az Azure Information Protection előzetes kiadásának kipróbálásához?

Az előzetes kiadásban, és csakis abban az Azure által hitelesített bármely felhasználó láthatja és konfigurálhatja a bérlőjének Azure Information Protection-házirendjét az Azure-portálon.

Ha a bemutató házirend telepítését választja az [Azure Information Protection-ügyfél](https://www.microsoft.com/en-us/download/details.aspx?id=53018) telepítésekor, akkor még a portálra sem kell bejelentkeznie az előzetes kiadás kipróbálásához. A bemutató házirend helyileg telepíteni az Azure Information Protection alapértelmezett házirendjét, így kipróbálhatja a dokumentumok és e-mailek címkézését, a címkék módosításához vagy újak hozzáadásához azonban be kell jelentkeznie az Azure-portálon. 

Ha védelemmel szeretné ellátni a besorolt és címkézett dokumentumokat és e-maileket, de még nem aktiválta az Azure Rights Managementet, akkor az aktiválási folyamathoz különleges rendszergazdai jogosultságok szükségesek. További információ: [Globális rendszergazdának kell lenni az Azure RMS konfigurálásához, vagy átadható a feladat más rendszergazdáknak?](../get-started/faqs.md#do-you-need-to-be-a-global-admin-to-configure-azure-rms-or-can-i-delegate-to-other-administrators)


## Helyi és hibrid környezetekben támogatott az Azure Information Protection?

Az Azure Information Protection egy felhőalapú megoldás. Ha a hibrid környezetek iránt érdeklődik, lépjen kapcsolatba az Information Protection-csapattal az askipteam@microsoft.com e-mail címen.

## Milyen ügyfélplatformokat és az alkalmazásokat támogat az Azure Information Protection?

Ez már dokumentált, és frissülni fog az [Azure Information Protection követelményeiben](requirements-azure-infoprotect.md).


## Hogyan szerzik be a számítógépek a házirendinformációkat az Azure Information Protectiontől, és milyen gyakran frissülnek?

Minden alkalommal, amikor a felhasználó megnyit egy Office-alkalmazást, az Azure Information Protection-ügyfél ellenőrzi, hogy elérhető-e az Azure Information Protection-házirend újabb verziója. Ha van újabb verzió, az ügyfél letölti, mégpedig az adatvédelem érdekében HTTPS-kapcsolat használatával. 

Ha az alkalmazás már be van töltve az Azure Information Protection-házirend frissítésekor, be kell zárnia, és újra meg kell nyitnia az alkalmazást a házirend a legújabb verziójának beolvasásához.

## Hol tárolhatók fájlok az Azure Information Protectionben? 

Mivel az Azure Information Protection állandó címkéket és védelmet alkalmaz a fájlokra és az e-mailekre, nem számít, hol tárolja a fájlokat.

## Csak az új adatok sorolhatók be, vagy a meglévők is?

Az Azure Information Protection-házirendműveletek a dokumentumok mentésekor és az e-mail elküldésekor lépnek érvénybe, és az új tartalomra és a meglévő tartalom változásaira egyaránt vonatkoznak. 

Ha mentett fájlokat szeretne besorolni, egyszerűen nyissa meg és mentse őket az adott Office-alkalmazásban. 

Jelenleg csoportosan nem vizsgálhatja és alkalmazhatja a besorolást, és egyesével kell megnyitnia és mentenie a dokumentumokat a megfelelő Office-alkalmazásban. 

## Az Azure Information Protection csak besorolásra használható, és nem lehet vele titkosítást vagy a használati jogokra vonatkozó korlátozást előírni?

Igen. Csak olyan Azure Information Protection-házirendet lehet konfigurálni, amely címkét ad hozzá. Tulajdonképpen várhatóan ez lesz a leggyakoribb eset a központi telepítési hálózatokban, amelyekben csak azok a dokumentumokhoz vagy e-mailekhez kell védelmet beállítani, amelyek különleges adatkezelést igényelnek.

## Hogyan működik az automatikus besorolás?

Az Azure-portálon előre meghatározott mintákat használhat, ilyen például a „Credit card numbers” (Hitelkártyaszámok) vagy az „USA Social Security Number” (USA-beli társadalombiztosítási azonosító). Egyéni karakterláncot vagy mintát is megadhat az automatikus besorolás feltételeként.

Az [Azure Information Protection gyors üzembe helyezési oktatóanyagában](infoprotect-quick-start-tutorial.md) talál példákat. 

A besorolás pontossága attól függ, hogyan konfigurálja a besorolási szabályt, amely feltételeken alapul. A feltételekben jelenleg szövegminták és reguláris kifejezések adhatók meg. Az előzetes kiadásban elérhető egyes beállítások ismertetése és a teszteléshez ajánlott példák a [Description of content matching for our pre-define Information types](https://www.yammer.com/askipteam/#/Threads/show?threadId=737163344) (Az előre megadott adattípusokhoz tartozó tartalom megfeleltetésének ismertetése) című Yammer-bejegyzésben találhatók. A vizsgálat a dokumentum mentésekor, illetve az e-mail elküldésekor történik.

A legjobb felhasználói élmény és az üzletmenet folytonosságának biztosítása érdekében javasoljuk, hogy ne a teljesen automatikus műveletekkel kezdjen, hanem adjon javaslatokat a felhasználóknak. Ekkor eldönthetik, hogy elfogadják-e a címkézési vagy adatvédelmi műveletet, vagy felülbírálják a javaslatot.   

## Van-e lehetőség rá, hogy az automatikus besorolás használata helyett az Azure Information Protection kérje meg a felhasználókat, hogy maguk sorolják be a fájlokat? 

Igen. Az Azure-portálon állíthatja be, hogy automatikus besorolást szeretne használni, vagy javaslatot szeretne adni a felhasználóknak. Ez utóbbihoz a **Select how this label is applied: automatically or recommended to user** (Válassza ki, hogyan legyen alkalmazva a címke: automatikusan vagy a felhasználónak javasolva) beállításban válassza a **Recommended ** (Javasolt) értéket.

Az [Azure Information Protection gyors üzembe helyezési oktatóanyagában](infoprotect-quick-start-tutorial.md) talál példákat.

## Kötelezővé lehet-e tenni az összes dokumentum besorolását?

Igen. Ha elő szeretné írni a felhasználóknak, hogy minden fájlt soroljanak be azok mentésekor, az Azure-portálon a **All documents and emails must have a label** (Minden dokumentumnak és e-mailnek rendelkeznie kell címkével) beállításban adja meg a **Be** értéket. 

## Eltávolítható a fájl besorolása?

Igen. A fájl besorolásának eltávolításához nyissa meg a fájlt a megfelelő Office-alkalmazásban, kattintson az **Edit label** (Címke szerkesztése) ikonra az Information Protection sávon, kattintson a **Remove label** (Címke eltávolítása) ikonra, végül az **OK** gombbal erősítse meg a műveletet. 


## Kérhető-e a felhasználóktól, hogy indokolják meg a besorolási szint módosítását?

Igen. Ha azt szeretné, hogy a felhasználók indokolják meg a besorolás módosítását, az Azure-portálon **Users must provide justification when lowering the sensitivity level** (A felhasználóknak indokolniuk kell a tartalmi szint csökkentését) beállításban adja meg a **Be** értéket. Ha így tesznek, a művelet és az indoklás bekerül a helyi Windows-eseménynaplójukba: **Alkalmazás** > **Microsoft Azure Information Protection**.

## Hogyan állítható be automatikus védelem a tartalomra a besorolás után?

Az Azure-portálon választhat egy Azure Rights Management-sablont a tartalom automatikusan védelméhez a megadott besorolási szintnek megfelelően.

Az [Azure Information Protection gyors üzembe helyezési oktatóanyagában](infoprotect-quick-start-tutorial.md) talál példákat.

## Rendelkezhet-e egy fájl két különböző besorolással?

Ha szükséges, létrehozhat alárendelt címkéket az adott tartalomcímke alkategóriáinak pontosabb jellemzésére. Például a **Titkos** egyszerű címke tartalmazhat olyan alárendelt címkéket, mint a **Titkos – jogi** és a **Titkos – pénzügyi**. Ezután különböző vizuális besorolási jelölést és különböző Rights Management-sablonokat alkalmazhat a különböző alárendelt címkékre.

Noha jelenleg mindkét szinten beállíthatók vizuális jelek, védelem és feltételek, alárendelt szintek használatakor ezek a beállítások csak az alárendelt szintjén adhatók meg. Ha a szülő címke és annak alárendelt szintje azonos beállításokkal rendelkezik, akkor az alárendelt szint beállításai élveznek elsőbbséget.

## Hogyan integrálhatók a DLP-megoldások és más alkalmazások az Azure Information Protectionnel?

Mivel Azure Information Protection állandó metaadatokat használ a besoroláshoz, amelyek titkosítatlan szövegcímkét is tartalmaznak, ezt az információt a DLP-megoldások és más alkalmazások is olvashatják. A fájlokban ezek a metaadatok egyéni tulajdonságokban vannak tárolva, az e-mailekben pedig fejlécben.

## Hogyan működik a dokumentumkövetés és a visszavonás az Azure Information Protection esetében?

Az Azure Information Protection használatával besorolt és védett fájlok esetén a dokumentumkövetés ugyanúgy működik, mint jelenleg az Azure Rights Managementnél. További információ: [Dokumentumok nyomon követése és visszavonása az RMS-megosztó alkalmazás használatakor](../rms-client/sharing-app-track-revoke.md).

## Hogyan kényszeríti ki az Azure Information Protection beállított házirendeket?

Ha a dokumentumot egy Azure Rights Management-sablon védi, először hitelesíti a felhasználót, biztosítva, hogy legyen jogosultsága a dokumentumhoz, azután az alkalmazás kikényszeríti a használati jogok házirendjét. 

## Hogyan használja az Azure Information Protection az Azure Active Directoryt?

Az Azure Information Protection az Azure Active Directory használatával hitelesíti a felhasználókat.

## Szabályozható, hogy mely felhasználók használhatják az Azure Information Protectiont a tartalom besorolására és védelmére?

Az Azure Information Protection-ügyfél terjesztésének szabályozásával korlátozhatja, hogy mely felhasználók sorolhatják be és védhetik le az adatokat. 

Az Azure Information Protection által besorolt fájlokat és e-maileket bármely felhasználó használhatja vagy szerkesztheti, akár telepítette az Azure Information Protection-ügyfelet, akár nem. 

## Hogyan jelezhetem a problémákat vagy küldhetek visszajelzést az előzetes kiadással kapcsolatban?

Ha problémát észlel az előzetes kiadás használatakor, az Office-alkalmazás **Kezdőlap** lapján, a **Védelem** csoportban kattintson a **Védelem**, majd a **Súgó és visszajelzés** lehetőségre. Az **Microsoft Azure Information Protection** párbeszédpanelen kattintson a **Visszajelzés küldése** elemre. Ezzel e-mailt küld az Information Protection-csapatnak, és automatikusan csatolja a naplófájlokat a számítógépről a probléma diagnosztizálása érdekében. 

Ha kérdése van, vagy visszajelzést szeretne küldeni, használja az [Azure Information Protection Yammer-helyét](https://www.yammer.com/askipteam/#/threads/inGroup?type=in_group&feedId=8652489&view=all). 

## Mit tehetek, ha a fentiekben nem szerepel a kérdésem?

Először ellenőrizze, hogy a kérdés nem található-e meg a nagyvállalati mobilitással és biztonsággal foglalkozó blogon, az [Azure Information Protection előzetes kiadásának bejelentésében](https://blogs.technet.microsoft.com/enterprisemobility/2016/07/12/azure-information-protection-public-preview-available-now/).

Ezután a [Yammer-helyen](https://www.yammer.com/askipteam/#/threads/inGroup?type=in_group&feedId=8652489&view=all) ellenőrizze, hogy esetleg feltette-e már valaki ugyanezt a kérdést. Ha nem, tegye fel a kérdését itt.







<!--HONumber=Jul16_HO3-->


