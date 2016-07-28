---
title: "Gyakori kérdések az Azure Rights Management szolgáltatásról | Azure RMS"
description: 
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 07/13/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 71ce491f-41c1-4d15-9646-455a6eaa157d
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: e89c59716eef7fbdea415b41b1adfa54b0c16689
ms.openlocfilehash: bd53b73452f444ac8529a8b8b613e76d8cc234a1


---

# Gyakori kérdések az Azure Rights Management szolgáltatásról

*A következőkre vonatkozik: Azure Rights Management, Office 365*

Néhány gyakran feltett kérdés a Microsoft [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] (más néven Azure RMS) termékről:

## Mire van szükségem az Azure RMS telepítéséhez, és hogyan kezdjek hozzá?
Először tekintse meg [Az Azure Rights Management követelményei](requirements-azure-rms.md) című szakaszt, amely a felhőalapú előfizetési lehetőségekről, a helyszíni kiszolgálók Azure RMS-sel való használatáról, a jelenleg nem támogatott telepítési forgatókönyvekről, az Azure RMS-t támogató eszközökről és alkalmazásokról tartalmaz információkat, valamint megtalálható benne a tűzfalak és proxykiszolgálók esetlegesen szükséges konfigurálásához egy, az IP-címeket és a tartományneveket tartalmazó lista hivatkozása. 

Érdemes megtekinteni az **Első lépések ** és a **Megismerés és felfedezés** szakasz további cikkeit is annak alapszintű megértéséhez, hogy miként segíti az [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] a szervezeti adatok védelmét, hogyan működik együtt a különböző alkalmazásokkal, miben különbözik az Active Directory Rights Management helyszíni verziójától, továbbá az [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] termékkel kapcsolatos terminológia és rövidítések megismeréséhez.

Ezután a termék használatához használja az [Azure Rights Management üzembe helyezési menetrendet](../plan-design/deployment-roadmap.md).

## Az Azure RMS csak a felhőben tárolt fájlok védelmére alkalmas?
Nem, ez egy gyakori félreértés. Az Azure Rights Management szolgáltatás (és a Microsoft) nem tekinti meg és nem tárolja az adatait a tartalomvédelmi szolgáltatás folyamatának részeként. A védett információkat a rendszer sosem küldi el vagy tárolja az Azure-ban, kivéve ha kifejezetten ott tárolja, vagy olyan felhőszolgáltatást használ, amely az Azure-ban tárolja őket. 

További információkért tekintse meg [Az Azure RMS működése – technikai részletek](../understand-explore/how-does-it-work.md) című cikket, amelyből megtudhatja, hogyan véd az Azure RMS egy helyszínen létrehozott és tárolt titkos kólareceptet úgy, hogy az a helyszínen marad.

## Integrálhatom az Azure RMS-t a helyszíni kiszolgálóimmal?
Igen. Az Azure RMS integrálható a helyszíni kiszolgálókkal, például az Exchange Serverrel, valamint a SharePoint- és a Windows-fájlkiszolgálókkal. Ehhez a [Rights Management-összekötőt](../deploy-use/deploy-rms-connector.md) használhatja. Ha csak a fájlbesorolási infrastruktúrát (FCI) szeretné használni a Windows Serverrel, használhatja az [RMS tartalomvédelmi parancsmagokat](https://technet.microsoft.com/library/mt601315%28v=ws.10%29.aspx). Az Active Directory-tartományvezérlőket az Azure AD-val szinkronizálva és összevonva zökkenőmentesebb hitelesítési élmény biztosítható a felhasználók számára, például az [Azure AD Connect](http://azure.microsoft.com/documentation/articles/active-directory-aadconnect/) használata révén.

Az Azure RMS automatikusan létrehozza és kezeli az XrML-tanúsítványokat, ezért nem használ helyszíni PKI-t. Az Azure RMS tanúsítványhasználatáról [Az Azure RMS működése](../understand-explore/how-does-it-work.md) című cikk [Az Azure RMS működésének bemutatása: Első használat, tartalomvédelem, a tartalom felhasználása](../understand-explore/how-does-it-work.md#walkthrough-of-how-azure-rms-works-first-use-content-protection-content-consumption) című szakaszában találhat további információkat.

## Hol találhatók információk olyan külső cég által gyártott termékekről, amelyekbe beépül az Azure RMS?

Sok szoftvergyártó már rendelkezik olyan megoldásokkal vagy készül olyanokat létrehozni, amelyekbe beépül az Azure RMS – és a lista nagyon gyorsan bővül. Érdemes ellenőrizni a [nagyvállalati mobilitási és biztonsági blogot](https://blogs.technet.microsoft.com/enterprisemobility/?product=azure-rights-management-services), és beszerezni a legújabb frissítéseket a [Dan Plastina @TheRMSGuy](https://twitter.com/TheRMSGuy) helyről a Twitteren. Ha azonban konkrét kérdése van, küldjön e-mailt az adatvédelmi csapat részére az askipteam@microsoft.com címre.

## Van valamilyen felügyeleti csomag vagy hasonló figyelési mechanizmus az RMS-összekötőhöz?

Bár a Rights Management-összekötő naplózza az adatokat, figyelmeztetéseket és hibaüzeneteket az eseménynaplóba, nincs olyan felügyeleti csomag, amely figyelné ezeket az eseményeket. Az események listája és a hozzájuk tartozó leírások azonban a javításhoz szükséges intézkedéseket segítő bővebb információkkal együtt dokumentálva vannak [Az Azure Rights Management-összekötő megfigyelése](../deploy-use/monitor-rms-connector.md) című dokumentumban.

## Globális rendszergazdának kell lenni az Azure RMS konfigurálásához, vagy átadható a feladat más rendszergazdáknak?

Az Office 365-bérlő vagy az Azure AD-bérlő globális rendszergazdái nyilvánvalóan végre tudják hajtani az Azure RMS minden rendszergazdai feladatát. Ha azonban más felhasználóknak szeretne rendszergazdai engedélyeket adni, megteheti ezt az [Add-AadrmRoleBasedAdministrator](https://msdn.microsoft.com/library/dn629417.aspx) Azure RMS PowerShell-parancsmag használatával. A rendszergazdai szerepkört hozzárendelheti felhasználói fiókhoz vagy csoporthoz. Kétféle szerepkör van: **globális rendszergazda** és **összekötő-rendszergazda**. 

Amint a szerepkörnevek sugallják, az első engedélyezi az Azure Rights Management összes felügyeleti feladatának futtatását (anélkül, hogy más felhőalapú szolgáltatások globális rendszergazdájává is válnának egyben), míg a második szerepkör csak a Rights Management- (RMS-) összekötő futtatását teszi lehetővé.

Ügyeljen a következőkre:

- Az Office 365 és az Azure AD globális rendszergazdái használhatják a felügyeleti portálokat (az Office 365 felügyeleti központot, illetve a klasszikus Azure-portált) az Azure RMS konfigurálására. Az Azure RMS globális rendszergazdai szerepkört kapott felhasználóknak az Azure RMS PowerShell-parancsokat kell használniuk az Azure RMS konfigurálására. Az egyes feladatok elvégzésére legalkalmasabb parancsmagokat lásd: [Az Azure Rights Management felügyelete a Windows PowerShell használatával](../deploy-use/administer-powershell.md).

- Ha [regisztrációs vezérlőket](../deploy-use/activate-service.md#configuring-onboarding-controls-for-a-phased-deployment) állított be, az nem befolyásolja az Azure RMS felügyeletére való képességet, kivéve az RMS-összekötőt. Ha például úgy állított be regisztrációs vezérlőket, hogy a tartalomvédelmi képesség csak az „Informatikai részleg” csoportra korlátozódik, az RMS-összekötő telepítésére és konfigurálására használt fióknak ezen csoport tagjának kell lennie. 

- Az Azure RMS által védett dokumentumok és e-mailek védelmét az Azure RMS egyetlen rendszergazdája sem tudja automatikusan eltávolítani (a bérlő globális rendszergazdája és az Azure RMS egyetlen globális rendszergazdája sem). Csak az Azure RMS felügyelőiként kijelölt felhasználók tudják ezt megtenni, és csak akkor, ha a felügyelői funkció engedélyezve van. A bérlő globális rendszergazdája és bármely Azure RMS globális rendszergazda kinevezhet azonban felhasználókat felügyelővé, beleértve a saját fiókjukat is. Emellett a felügyelői funkciót is engedélyezhetik. Ezeket a műveleteket a rendszer az Azure RMS rendszergazdanaplójában rögzíti. További információkat a [Felügyelők konfigurálása az Azure Rights Management és a felderítési szolgáltatások vagy adat-helyreállítás számára](../deploy-use/configure-super-users.md) című témakör bevált biztonsági eljárásokkal foglalkozó szakaszában talál. 


## Hibrid telepítéssel rendelkezem: a felhasználók egy része Exchange Online-t, a másik részük Exchange Servert használ. Támogatja ezt az Azure RMS?
Teljes mértékben. Ráadásul a felhasználók zökkenőmentesen védhetik és használhatják a védett e-maileket és mellékleteket a két Exchange-környezet között. Ehhez a konfigurációhoz [aktiválja az Azure RMS-t](../deploy-use/activate-service.md), és [engedélyezze az IRM-et az Exchange Online-hoz](https://technet.microsoft.com/library/dn151475%28v=exchg.150%29.aspx), majd [telepítse és konfigurálja az RMS-összekötőt](../deploy-use/deploy-rms-connector.md) az Exchange Serverhez.

## Elérhető egy részletes útmutató az Exchange Online az Azure RMS használatára történő konfigurálásához?

Igen. Az [Exchange Online: az IRM konfigurálása](../deploy-use/configure-office365.md#exchange-online-irm-configuration) című szakaszban láthat egy, az Azure RMS használatát az Exchange Online számára lehetővé tevő jellemző parancskészletet, megtudhatja, miért nem mutatja azonnal az Outlook Web App az **Engedélyek beállítása** menü elemeit, és megtalálja az Azure RMS-sablonok módosításakor vagy frissítésekor futtatandó parancsot. 

## Ha éles környezetben telepítem az Azure RMS-t, akkor hozzá vagyok kötve a megoldáshoz, vagy kockáztatjuk az addig Azure RMS-sel védett tartalomhoz való hozzáférés elvesztését?
Nem, minden esetben megőrzi az adatok feletti ellenőrzési képességét, és továbbra is hozzáférhet azokhoz, még ha úgy is dönt, hogy nem szeretné tovább használni az Azure RMS-t. További információ: [Az Azure Rights Management leszerelése és deaktiválása](../deploy-use/decommission-deactivate.md).

Mielőtt azonban leszerelné az Azure RMS telepítését, örülnénk, ha megosztaná velünk, miért dönt így. Ha az Azure RMS nem felel meg az üzleti követelményeinek, lépjen kapcsolatba velünk, hogy megtudja, tervezünk-e a közeljövőben bevezetni új funkciókat, vagy tudunk-e valamilyen alternatívával szolgálni. Írjon egy e-mail-üzenetet az [AskIPTeam@Microsoft.com](mailto:askipteam@microsoft.com?subject=Planning%20to%20decommission%20Azure%20RMS) címre, és örömmel segítünk a műszaki és üzleti igényeinek felmérésében.

## Szabályozhatom, hogy melyik felhasználóim használhatják az Azure RMS-t tartalmak védelmére?
Igen, az Azure RMS rendelkezik az ehhez szükséges felhasználóregisztrációs vezérlőkkel. További információt az [Activating Azure Rights Management](../deploy-use/activate-service.md) (Az Azure Rights Management aktiválása) című cikk [Configuring onboarding controls for a phased deployment](../deploy-use/activate-service.md#configuring-onboarding-controls-for-a-phased-deployment) (Regisztrációs vezérlők konfigurálása szakaszos bevezetéshez) szakaszában találhat.

## Megakadályozhatom, hogy a felhasználók védett dokumentumokat osszanak meg adott szervezetekkel?
Az Azure RMS egyik legnagyobb előnye az, hogy anélkül támogatja a vállalatok közötti együttműködést, hogy explicit megbízhatósági viszonyokat kellene konfigurálnia minden egyes partnerszervezethez, mert az Azure AD gondoskodik a hitelesítésről.

Nincs olyan rendszergazdai beállítás, amely megakadályozná a felhasználókat abban, hogy titokban megosszanak dokumentumokat bizonyos szervezetekkel. Tegyük fel például, hogy blokkolni szeretne egy szervezetet, amelyben nem bízik meg, vagy amely a versenytársa. Nincs értelme megtiltani a felhasználók számára a védett dokumentumok elküldését ezekhez a szervezetekhez, mert a felhasználók akkor védelem nélkül osztanák meg a dokumentumokat, ami valószínűleg a legutolsó dolog, amit szeretne egy ilyen helyzetben. Ekkor például nem tudná azonosítani, ki oszt meg bizalmas vállalati dokumentumokat az adott szervezetek mely felhasználóival, márpedig az Azure RMS által védett dokumentumok (vagy e-mailek) esetében ez azonosítható.

## Amikor megosztok egy védett dokumentumot valakivel a vállalaton kívül, hogyan hitelesíti magát az a felhasználó?
Az Azure RMS a felhasználók hitelesítéséhez mindig egy Azure Active Directory-fiókot és egy társított e-mail-címet használ, így a vállalatok közötti együttműködés zökkenőmentesen zajlik a rendszergazdák nézőpontjából. Ha a másik szervezet Azure-szolgáltatásokat használ, a felhasználóknak már lesz fiókjuk Azure Active Directoryban, még akkor is, ha azok a fiókok helyszínen lettek létrehozva és vannak felügyelve, majd utána lettek szinkronizálva az Azure-ral. Ha a szervezet Office 365-tel rendelkezik, valójában az is Azure Active Directoryt használ a felhasználói fiókokhoz. Ha a felhasználó szervezete nem rendelkezik felügyelt Azure-fiókkal, a felhasználók regisztrálhatnak az [RMS egyéni felhasználók számára](../understand-explore/rms-for-individuals.md) szolgáltatásba, ami létrehoz egy nem felügyelt Azure-bérlőt és -címtárat a szervezethez, illetve egy fiókot a felhasználóhoz, hogy ez a felhasználó (és a későbbi felhasználók) aztán hitelesíthető legyen az Azure RMS-ben.

A fiókok hitelesítési módszere változó lehet attól függően, hogy a másik szervezet rendszergazdája hogyan konfigurálta az Azure Active Directory-fiókokat. Használhatnak például a fiókokhoz létrehozott jelszavakat, többtényezős hitelesítést (MFA), összevonást, vagy az Active Directory tartományi szolgáltatásokban létrehozott, majd az Azure Active Directoryval szinkronizált jelszavakat.

## A vállalatomon kívülről is hozzáadhatok felhasználókat egyéni sablonokhoz?
Igen. A végfelhasználók (és rendszergazdák) által alkalmazásokból kiválasztható egyéni sablonok létrehozásával az előre megadott házirendek megadása révén gyorssá és egyszerűvé teheti számukra az információvédelem alkalmazását. A sablonok egyik beállítása arra vonatkozik, hogy ki férhet hozzá a tartalomhoz, valamint megadhat felhasználókat és csoportokat a szervezetén belülről, és felhasználókat a szervezetén kívülről.

A szervezeten kívüli felhasználók megadásához vegye fel őket névjegyként egy olyan csoportba, amelyet a klasszikus Azure-portálon választott ki a sablonok konfigurálásakor; vagy lásd: [Az Azure Rights Managementhez készült Windows PowerShell](../deploy-use/install-powershell.md):

-   **Jogosultság-definíciós objektum használata sablon létrehozásához vagy frissítéséhez**.    Adja meg a külső e-mail-címeket és a jogaikat egy jogosultság-definíciós objektumban, amelyet a későbbiekben a sablon létrehozására vagy frissítésére használ majd. A jogosultság-definíciós objektumot úgy adhatja meg, ha a [New-AadrmRightsDefinition](https://msdn.microsoft.com/library/azure/dn727080.aspx) parancsmaggal létrehoz egy változót, majd megadja ezt a változót a -RightsDefinition paraméternek az [Add-AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727075.aspx) parancsmaggal (új sablon esetében) vagy a [Set-AadrmTemplateProperty](https://msdn.microsoft.com/library/azure/dn727076.aspx) parancsmaggal (ha egy létező sablont módosít). Ha viszont ezeket a felhasználókat egy létező sablonhoz adja, a sablon létező csoportjaihoz is meg kell határoznia jogosultság-definíciós objektumokat, nem csak a külső felhasználókhoz.

További információ az egyéni sablonokról: [Egyéni sablonok konfigurálása az Azure Rights Management szolgáltatáshoz](../deploy-use/configure-custom-templates.md).

## Együttműködik az Azure RMS az Azure AD dinamikus csoportjaival?
Egy Azure AD Premium-funkció segítségével dinamikus tagságot konfigurálhat csoportokhoz [attribútumalapú szabályok](https://azure.microsoft.com/documentation/articles/active-directory-accessmanagement-groups-with-advanced-rules/) megadásával. Amikor az Azure AD-ben létrehoz egy biztonsági csoportot, ez a csoporttípus támogatja a dinamikus tagságot, de nem támogatja e-mail-címek használatát, ezért nem használható Azure RMS-sel. Mostantól viszont létrehozhat egy új csoporttípust az Azure AD-ben, amely támogatja a dinamikus tagságot is és kompatibilis az e-mailekkel. Amikor hozzáad egy új csoportot a klasszikus Azure-portálhoz, kiválaszthatja az **Office 365 „előzetes verzió”** **CSOPORTTÍPUSÁT**. Mivel ez a csoport kompatibilis az e-mailekkel, használhatja az Azure RMS-sel.

Ahogy azt a beállítás neve is egyértelműen mutatja, ez az új csoporttípus még előzetes verzióként érhető el. Később további funkciók várhatók, amelyeket majd egy új dokumentáció is követ. Addig is meg akartunk győződni arról, hogy ez az új csoporttípus használható az Azure RMS-sel.


## Milyen eszközöket és milyen fájltípusokat támogat az Azure RMS?
A támogatott eszközök teljes listáját lásd: [Azure RMS-követelmények: Az Azure RMS-t támogató ügyféleszközök](../get-started/requirements-client-devices.md). Mivel jelenleg nem minden támogatott eszköz képes támogatni az összes RMS-funkciót, mindenképp nézze meg az [Azure RMS-követelmények: Alkalmazások](../get-started/requirements-applications.md) című cikkben szereplő táblázatot is.

Az Azure RMS minden fájltípust támogat. Szöveghez, képekhez, Microsoft Office- (Word-, Excel-, PowerPoint-) fájlokhoz, .pdf fájlokhoz és néhány más alkalmazás fájltípusa esetén az Azure RMS natív védelmet biztosít, amelynek része a titkosítás és az engedélyek (jogosultságok) kényszerítése is. Az általános védelem minden más alkalmazáshoz és fájltípushoz biztosítja a fájlbeágyazást és a hitelesítést, hogy ellenőrizhető legyen, hogy egy felhasználó jogosult-e a fájl megnyitására.

Az Azure RMS által natívan támogatott fájlnév-kiterjesztések listájáért tekintse meg a [Rights Management sharing application administrator guide](../rms-client/sharing-app-admin-guide.md) (A Rights Management megosztóalkalmazás rendszergazdai kézikönyve) [Supported file types and file name extensions](../rms-client/sharing-app-admin-guide-technical.md#supported-file-types-and-file-name-extensions) (Támogatott fájltípusok és fájlnévkiterjesztések) című szakaszát. A listán nem szereplő fájlnév-kiterjesztések az RMS megosztóalkalmazás használatával támogatottak, amely automatikusan általános védelmet alkalmaz ezekre a fájlokra.

## Ha megnyitok egy RMS által védett Office-dokumentumot, a kapcsolódó ideiglenes fájl is védve lesz az RMS által?

Nem. A fenti forgatókönyv alapján a kapcsolódó ideiglenes fájl nem tartalmaz információt az eredeti dokumentumról, hanem csak olyan adatokat, amelyeket a felhasználó ad meg a fájl megnyitása során. Az eredeti fájltól eltérően az ideiglenes fájlt értelemszerűen nem megosztásra tervezték, és ezért a helyi biztonsági intézkedések, például a BitLocker és az EFS által látható el védelemmel, és kizárólag az adott eszközön található meg.

## Mikor lesz támogatott az AD RMS-ről való áttelepítés?
Az Azure RMS eredetileg nem támogatta a Rights Management helyszíni telepítéséből (pl. AD RMS-ből) való áttelepítést. Most már azonban támogatja.

További információ: [Áttelepítés AD RMS-ről Azure Rights Managementre](../plan-design/migrate-from-ad-rms-to-azure-rms.md).

## Nagyon szeretnénk az Azure RMS-sel használni a BYOK-t, de megtudtuk, hogy nem kompatibilis az Exchange Online-nal. Mit tanácsolnak?
Emiatt a jelenlegi korlátozás miatt ne halassza el az Azure RMS bevezetését. Ha rendelkezik Exchange Online-nal, és saját kulcsot szeretne használni (BYOK), javasoljuk, hogy az Azure RMS-t az alapértelmezett kulcsfelügyeleti módban helyezze üzembe, amelyben a kulcsát a Microsoft állítja elő és kezeli. Így azonnal élhet a fontos fájlok és e-mailek védelmének összes előnyével, és később még mindig átválthat BYOK használatra (például, ha az Exchange Online már támogatni fogja a BYOK-t).

Ha viszont a vállalata házirendje előírja, hogy hardveres biztonsági modult (HSM) használjon, és az másképp blokkolná az Azure RMS bevezetését, egy másik lehetőség, hogy telepíti az Azure RMS-t BYOK-val most, az Exchange-hez korlátozott RMS-funkciókkal. További információt [Az Azure Rights Management-bérlőkulcs tervezése és megvalósítása](../plan-design/plan-implement-tenant-key.md) című cikk [A BYOK díjszabása és korlátozásai](../plan-design/byok-price-restrictions.md) című szakaszában találhat.

## Úgy tűnik, hogy a szolgáltatás, amire szükségem van, nem működik a SharePoint védett könyvtárainál – terveznek támogatást a szolgáltatásomhoz?
A SharePoint jelenleg az RMS által védett dokumentumok használatát IRM által védett könyvtárak segítségével támogatja, ez pedig nem támogatja az egyéni sablonokat, a dokumentumkövetést és néhány más képességet. További információt az [Office-alkalmazások és -szolgáltatások](../understand-explore/office-apps-services-support.md) című témakör [SharePoint Online és SharePoint Server](../understand-explore/office-apps-services-support.md#sharepoint-online-and-sharepoint-server) szakaszában talál.

Ha egy olyan konkrét funkció érdekli, amely még nem támogatott, mindenképp kövesse figyelemmel a [nagyvállalati mobilitási és biztonsági blogot](https://blogs.technet.microsoft.com/enterprisemobility/?product=azure-rights-management-services).

## Hogyan konfigurálhatom a OneDrive Vállalati verziót a SharePoint Online-hoz, hogy a felhasználók biztonságosan oszthassák meg a fájljaikat a vállalaton belüli és kívüli személyekkel is?
Alapértelmezés szerint Office 365-rendszergazdaként nem Ön konfigurálja ezt, hanem a felhasználók.

Ahogy az IRM-et is egy SharePoint-hely rendszergazdája engedélyezi és konfigurálja az általuk tulajdonolt SharePoint-könyvtárhoz, a OneDrive Vállalati verzió is úgy lett megtervezve, hogy a felhasználók engedélyezzék és konfigurálják az IRM-et a saját OneDrive Vállalati verziós könyvtárukhoz.  A PowerShell használatával viszont elvégezheti ezt a lépést a számukra. Útmutatásért tekintse meg az [Office 365: Konfigurálás ügyfelek és online szolgáltatások számára](../deploy-use/configure-office365.md) című cikk [SharePoint Online és OneDrive Vállalati verzió: az IRM konfigurálása](../deploy-use/configure-office365.md#sharepoint-online-and-onedrive-for-business-irm-configuration) szakaszát.

## Léteznek tippek vagy trükkök az RMS sikeres bevezetéséhez?
Számos környezet áttekintése, valamint az ügyfelekkel, partnerekkel, tanácsadókkal és támogatási mérnökökkel folytatott beszélgetések eredményeként a legfontosabb tippünk a következő: **egyszerű jogosultsági házirendeket tervezzen és helyezzen üzembe**.

Mivel az Azure RMS mindenki esetében támogatja a biztonságos megosztást, nyugodtan gondolkodhat nagyban az adatvédelem kiterjesztését illetően. A jogosultsági házirendekkel kapcsolatban viszont legyen kifejezetten konzervatív. Számos szervezetnél a legnagyobb üzleti hatást az adatszivárgás megakadályozása jelenti, ha az alapértelmezett jogmegadási sablont alkalmazzák, amely korlátozza a szervezete tagjainak elérhetőségét. Persze belemerülhet sokkal jobban is a részletekbe, ha szükséges – pl. megtilthatja az alkalmazottaknak a nyomtatást, a szerkesztést stb. A részletes korlátozásokat azonban inkább kivételként alkalmazza a valóban nagyobb szintű biztonságot igénylő dokumentumokhoz, és ne alkalmazza ezeket a korlátozóbb házirendeket rögtön az első nap, inkább tervezzen meg egy szakaszos bevezetést.

## Melyik szolgáltatások használhatók vagy nem használhatók az Azure RMS különböző előfizetéseivel?
Az Azure RMS-t támogató fizetett előfizetések esetében (Office 365, Azure RMS Premium és Nagyvállalati mobilitási csomag) vannak eltérések a támogatott RMS-szolgáltatások tekintetében. Ezen eltérések listáját a [Comparison of Rights Management Services (RMS) Offerings](http://technet.microsoft.com/dn858608) (A Tartalomvédelmi szolgáltatásokra (RMS) vonatkozó ajánlatok összehasonlítása) című szakaszban találja.

Az Azure RMS-t támogató ingyenes előfizetés (RMS egyéni felhasználók számára) támogatja az Azure RMS-sel védett tartalmak használatát. További információ: [RMS for Individuals and Azure Rights Management](../understand-explore/rms-for-individuals.md) (RMS egyéni felhasználók számára és Azure Rights Management).

## Honnan kaphatok technikai információkat az ingyenes Azure RMS-előfizetésről (RMS egyéni felhasználók számára) – hogyan működik például, hogyan felügyelhetők a fiókok, milyen tartományok nem használhatók?
Ezekre a kérdésekre az [RMS for Individuals and Azure Rights Management](../understand-explore/rms-for-individuals.md) (RMS egyéni felhasználók számára és Azure Rights Management) című cikkben és a kapcsolódó cikkekben találhat választ.

## Hogyan férhetek hozzá újra az olyan fájlokhoz, amelyeket egy olyan alkalmazott látott el védelemmel, aki kilépett a szervezetből?
Az Azure RMS felügyelői funkciója révén a jogosult felhasználók teljes tulajdonosi jogokat kapnak minden, a szervezet RMS-bérlője által biztosított összes használati licenchez. Ugyanez a funkció lehetővé teszi igény szerint a fájlok indexelését és vizsgálatát.

További információ: [Configuring super users for Azure Rights Management and discovery services or data recovery](../deploy-use/configure-super-users.md) (Felügyelők konfigurálása az Azure Rights Management és a felderítési szolgáltatások vagy adat-helyreállítás számára).

## Képes a Rights Management megakadályozni a képernyőképek rögzítését?
Azáltal, hogy nem biztosítja a **Másolás** [használati jogosultságot](../deploy-use/configure-usage-rights.md), a Rights Management képes megakadályozni a képernyőképek készítését számos, Windows (Windows 7, Windows 8.1, Windows 10, Windows Phone) és Android rendszert futtató platformon általánosan elterjedt képernyőrögzítő eszköz számára. Az iOS rendszer és a Mac gépek azonban egy alkalmazás számára sem engedélyezik a képernyőkép-készítés megakadályozását, és a böngészőkben (amikor például Outlook Web Appet és Office Online-t használ) sem akadályozható meg a képernyőképek rögzítése.

A képernyőképek rögzítésének tiltása segít megakadályozni titkos vagy bizalmas adatok véletlenül vagy hanyagságból való nyilvánosságra kerülését. Azonban számos módja van a képernyőn megjelenő adatok megosztásának, és a képernyőkép rögzítése csak egy ezek közül. Ha például egy felhasználó meg szeretné osztani a megjelenő információkat, készíthet egy képet arról a telefonja kamerájával, legépelheti újra az adatokat, vagy csak egyszerűen szóban továbbíthatja azt valakinek.

Ahogyan azt ezek a példák is mutatják, még ha minden platform és minden szoftver támogatná is a Rights Management API-kat a képernyőképek rögzítésének blokkolásában, a technológia önmagában kevés ahhoz, hogy megakadályozza a felhasználókat azon adatok megosztásában, amelyeket nem szabad továbbadniuk. A Rights Management segít biztonságossá tenni a fontos adatokat hitelesítés és használati házirendek segítségével, de ezen nagyvállalati tartalomkezelési megoldás mellé más szabályozásokra is szükség van. Implementálhat például fizikai biztonsági megoldásokat, gondosan szűrheti és megfigyelheti azokat, akik jogosultak hozzáférni a szervezet adataihoz, és képzéseket biztosíthat a felhasználók számára, hogy tisztában legyenek azzal, milyen adatokat nem szabad megosztaniuk.

## Mi a különbség a között, ha a felhasználó egy e-mail számára a „Nem továbbítandó” jelzéssel vagy a Továbbítási jogot nem tartalmazó sablonnal biztosít védelmet?

Neve és megjelenése ellenére a **Nem továbbítandó** nem a Továbbítási jog ellentéte, és nem is sablon. Ez egy olyan jogosultságkészlet, amely az e-mailek továbbítása mellett a mellékletek másolását, nyomtatását és mentését is korlátozza. A jogosultságokat nem a rendszergazda osztja ki statikusan, hanem a rendszer alkalmazza dinamikusan a felhasználókra a választott címzetteken keresztül. További információért lásd [A „Nem továbbítandó” beállítás e-mailekhez](../deploy-use/configure-usage-rights.md#do-not-forward-option-for-emails) című szakaszt a [Használati jogosultságok konfigurálása az Azure Rights Managementhez](../deploy-use/configure-usage-rights.md) című témakörben.

## Hol találok támogatási információkat az Azure RMS-hez – például a jogi tudnivalókat, a megfelelőségi információkat és a szolgáltatásszint-szerződéseket?
Az Azure RMS támogatja a többi szolgáltatást, és maga is más szolgáltatásokra támaszkodik. Ha az Azure RMS-hez kapcsolódó, de nem az Azure RMS szolgáltatás használatára vonatkozó információkat keres, tekintse meg az alábbi forrásanyagokat.

**Jogi tudnivalók és adatvédelem:**

-   Microsoft Azure-szerződéssel kapcsolatos információk: [Microsoft Azure-szerződés](http://azure.microsoft.com/support/legal/subscription-agreement/)

-   A Microsoft Azure adatvédelmével kapcsolatos információk: [Microsoft Azure adatvédelmi nyilatkozat](http://azure.microsoft.com/support/legal/privacy-statement/)

**Biztonság, megfelelőség és naplózás:**

Lásd a [Milyen problémákat képes megoldani az Azure RMS?](../understand-explore/azure-rms-problems-it-solves.md) című cikk [Biztonsági, megfelelőségi és szabályozási követelmények](../understand-explore/azure-rms-problems-it-solves.md#security-compliance-and-regulatory-requirements) című szakaszát. Továbbá:

-   Az Azure RMS külső tanúsítványaival kapcsolatban: [Microsoft Azure biztonsági és adatkezelési központ](http://azure.microsoft.com/support/trust-center/)

-   Információk a FIPS 140-ről: [A FIPS 140 érvényesítése](https://technet.microsoft.com/library/security/cc750357.aspx)

**Szolgáltatásiszint-szerződések:**

-   Az Azure RMS szolgáltatásiszint-szerződése kijelölt terület szerint: [Letöltés a Terméklicencelés keresési oldaláról](http://microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&amp;DocumentTypeId=37)

    - A 2016. márciusi észak-amerikai szolgáltatásiszint-szerződés letöltéséhez például kattintson az **OnlineSvcsConsolidatedSLA(WW)(English)(March2016)** elemre.

-   Az Azure Active Directory szolgáltatásiszint-szerződése: [Szolgáltatásiszint-szerződések](http://azure.microsoft.com/support/legal/sla/)

**Dokumentáció:**

-   Az Azure Active Directory dokumentációs oldala: [Azure Active Directory](http://azure.microsoft.com/documentation/services/active-directory/)

-   Azure Active Directory Library: [Azure Active Directory](https://msdn.microsoft.com/library/azure/mt168838.aspx)

-   Office 365-könyvtár: [Office 365](http://technet.microsoft.com/library/dn127064%28v=office.14%29.aspx)

## Mik a legújabb fejlemények az új besorolási és címkézési funkció kapcsán?

Ezek a funkciók már elérhetők az Azure Information Protection nyilvános előzetes verziójában. Próbálja ki, és tekintse meg az elérhető erőforrások listáját a [What is Azure Information Protection preview?](../information-protection/what-is-information-protection.md) (Mi az az Azure Information Protection előzetes verziója?) című témakörben.


## Úgy hallottam, nemsokára megjelenik az Azure RMS új verziója. Mikorra várható?

A műszaki dokumentáció nem tartalmaz a jövőbeli verziókkal kapcsolatos információkat. Az ilyen jellegű információkért és közleményekért érdemes ellenőrizni a [nagyvállalati mobilitási és biztonsági blogot](https://blogs.technet.microsoft.com/enterprisemobility/?product=azure-rights-management-services), és beszerezni a legújabb frissítéseket a [Dan Plastina @TheRMSGuy](https://twitter.com/TheRMSGuy) helyről a Twitteren. Ha egy Office-verzió érdekli, feltétlenül nézze meg az [Office-blogot](https://blogs.office.com/) is.

## Mit tehetek, ha a fentiekben nem szerepel a kérdésem?
Használja az [Information and support for Azure Rights Management](information-support.md) (Azure Rights Management – információ és támogatás) című szakaszban található hivatkozásokat és forrásanyagokat.

Elérhetők továbbá végfelhasználóknak tervezett gyakorikérdés-gyűjtemények.

-   [A Windows Rights Management megosztóalkalmazással kapcsolatos gyakori kérdések](https://technet.microsoft.com/dn467883)

-   [A Rights Management megosztóalkalmazás mobil és Mac rendszerű platformokra kiadott verziójával kapcsolatos gyakori kérdések](https://technet.microsoft.com/dn451248)

-   [A dokumentumkövetéssel kapcsolatos gyakori kérdések](http://go.microsoft.com/fwlink/?LinkId=523977)

Ez a gyakori kérdéseket tartalmazó oldal rendszeresen frissül. Az új elemek listája megtalálható a havi dokumentációfrissítési közleményekben a [nagyvállalati mobilitási és biztonsági blogon](https://blogs.technet.microsoft.com/enterprisemobility/?product=azure-rights-management-services).





<!--HONumber=Jul16_HO3-->


