---
# required metadata

title: Mit látnak a rendszergazdák és a felhasználók? | Azure RMS
description:
keywords:
author: cabailey
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 013e0eb4-49a7-4e81-9e4d-f56c0ceb017f

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: esaggese
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---


# Az Azure RMS működés közben: Mit látnak a rendszergazdák és a felhasználók?

*A következőkre vonatkozik: Azure Rights Management, Office 365*

Ez a cikk tipikus példákat mutat be arról, hogy a rendszergazdák és a felhasználók hogyan látják és hogyan használhatják az Azure Rights Management (Azure RMS) szolgáltatást a bizalmas vagy titkos információk megvédésének elősegítése érdekében.

> [!NOTE]
> Az összes példában, amelyben az Azure RMS védelemmel látja el az adatokat, a tartalomtulajdonos továbbra is teljes hozzáféréssel rendelkezik az adatokhoz (a fájlokhoz vagy e-mailekhez), még akkor is, ha az alkalmazott védelem olyan csoport számára biztosít hozzáférést, amelynek a tulajdonos nem tagja, vagy ha a védelem lejárati dátummal rendelkezik.
>
> Hasonló módon az IT-csoport bármikor, korlátozás nélkül hozzáférhet a védett adatokhoz a Rights Management felügyelői funkciója révén, amely delegált hozzáférést biztosít a megadott jogosult felhasználók vagy szolgáltatások számára. Emellett az IT-csoport nyomon követheti és felügyelheti a védet adatok felhasználását – például ki és mikor fér hozzá az adatokhoz.

Az RMS-t működés közben bemutató képernyőfelvételekért és videókért tekintse meg a következőket: [A Microsoft Rights Management szolgáltatások portálja](http://www.microsoft.com/rms) és [A Microsoft Rights Management (RMS) csapat blogja](http://blogs.technet.com/b/rms).

## A Rights Management aktiválása és konfigurálása
Bár a Windows PowerShell használatával is aktiválhatja és konfigurálhatja az Azure RMS-t, ez mégis a felügyeleti portálon keresztül végezhető el a legkönnyebben. Amint aktiválta a szolgáltatást, két alapértelmezett sablon válik elérhetővé, amelyek segítségével a rendszergazdák és a felhasználók gyorsan és egyszerűen láthatják el adatvédelemmel a fájlokat. Emellett a további funkciók és beállítások hozzáadása érdekében saját egyéni sablonokat is létrehozhat.

![MIT LÁTNAK A RENDSZERGAZDÁK AZ 1. LÉPÉSBEN?](../media/AzRMS_StoryboardActivate_small1.png)


**MIT LÁTNAK A RENDSZERGAZDÁK AZ 1. LÉPÉSBEN:** Az RMS aktiválásához használhatja az Office 365 felügyeleti központot (első kép) vagy a klasszikus Azure portált (második kép).<br /><br />Csupán egyetlen kattintással aktiválhatja, egy másikkal pedig megerősítheti. Ettől kezdve a szervezetében lévő rendszergazdák és felhasználók számára engedélyezve van az adatvédelem.

---

![MIT LÁTNAK A RENDSZERGAZDÁK A 2. LÉPÉSBEN?](../media/AzRMS_TemplatesPortal_small.png)

**MIT LÁTNAK A RENDSZERGAZDÁK A 2. LÉPÉSBEN:** Az aktiválás után két jogmegadási sablon válik automatikusan elérhetővé a szervezet számára. Az egyik sablon csak olvasási (a nevében a **Csak bizalmas megtekintésre** kifejezés szerepel), a másik pedig olvasási és módosítási hozzáférést biztosít (**Bizalmas**).).

Ha ezeket a sablonokat alkalmazzák a fájlokra és e-mailekre, akkor korlátozzák a szervezetben lévő felhasználók hozzáférését. Ez egy igen gyors és egyszerű módja annak, hogy megakadályozza a vállalati adatok kiszivárogtatását a szervezeten kívüli személyek számára.

> [!TIP]
> Könnyen felismerheti az alapértelmezett sablonokat, mivel automatikusan a szervezet nevét tartalmazó előtaggal lesznek ellátva. A jelen példában **VanArsdel, Ltd**

Ha nem szeretné, hogy a felhasználók láthassák ezeket a sablonokat, vagy saját sablonokat szeretne létrehozni, a klasszikus Azure portálon megteheti. Ahogy az a képen is látszik, a varázsló végigvezeti az egyéni sablonok létrehozási folyamatának lépésein.

---

![MIT LÁTNAK A RENDSZERGAZDÁK A 3. LÉPÉSBEN?](../media/AzRMS_TemplatesSettings3.png)

**MIT LÁTNAK A RENDSZERGAZDÁK A 3. LÉPÉSBEN:** Ha saját sablonok létrehozása mellett dönt, többek között a következő konfigurációs beállítások állnak rendelkezésére: offline hozzáférés, lejárati beállítások és a sablon azonnali közzétételének (a Rights Managementet támogató alkalmazásokban való megjelenítésének) lehetősége.

---

![MIT LÁTNAK A RENDSZERGAZDÁK A 4. LÉPÉSBEN?](../media/AzRMS_TemplatesPortal_ExplorerWord3.png)

**MIT LÁTNAK A FELHASZNÁLÓK A 4. LÉPÉSBEN:** A sablonok közzétételének eredményeképpen a felhasználók kiválaszthatják őket az olyan alkalmazásokban, mint például a Fájlkezelő vagy a Microsoft Word:

- A felhasználók kiválaszthatják a **VanArsdel, Ltd – Bizalmas** alapértelmezett sablont. Így csak a VanArsdel szervezet dolgozói nyithatják meg és használhatják a dokumentumot, még akkor is, ha később megkapja e-mailben egy szervezeten kívüli személy is, vagy nyilvános helyre mentik.

- A felhasználók kiválaszthatják a rendszergazda által létrehozott **Értékesítés és marketing – Csak olvasásra és nyomtatásra** sablont. Így a fájl nemcsak a szervezeten kívüli személyek számára lesz hozzáférhetetlen, hanem az Értékesítési és marketing osztályon kívüli dolgozók számára is. Továbbá a jogosult dolgozók is csak olvasási és nyomtatási, és nem teljes jogosultsággal rendelkeznek a dokumentumhoz. Nem módosíthatják és nem másolhatják például a dokumentum egyes részeit.

---

**További információ erről a forgatókönyvről:**

- Részletes útmutatásért lásd: [Activating Azure Rights Management](../deploy-use/activate-service.md) (Az Azure Rights Management aktiválása) és [Configuring custom templates for Azure Rights Management](../deploy-use/configure-custom-templates.md) (Egyéni sablonok konfigurálása az Azure Rights Management szolgáltatáshoz).

- Ha útmutatást szeretne nyújtani a felhasználóknak a fontos vállalati fájlok védelme kapcsán, tekintse meg a következőt: [Helping users to protect files by using Azure Rights Management](../deploy-use/help-users.md) (Útmutatás nyújtása a felhasználók számára a fájlok védelméhez az Azure Rights Management használatával)..

A következőkben néhány példát tekinthet meg arról, hogyan alkalmazhatja a sablonokat a rendszergazda a fájlok és e-mailek adatvédelmének automatikus konfigurálására.

## Fájlok automatikus védelme a Windows Server rendszert és a Fájlbesorolási infrastruktúrát futtató fájlkiszolgálókon

Ez a példa bemutatja, hogyan használhatja az Azure RMS-t a fájlok automatikus védelmére a legalább Windows Server 2012 rendszert futtató és a Fájlbesorolási infrastruktúra használatára konfigurált fájlkiszolgálókon.

Számos módon lehet besorolási értéket rendelni egy fájlhoz. Megvizsgálhatja például a fájlok tartalmát, és annak megfelelően alkalmazhat beépített besorolásokat, úgymint Titkosítás vagy Személyes azonosításra alkalmas adat. Ebben a példában viszont a rendszergazda a **Marketing** egyéni besorolást hozta létre, amelyet a rendszer automatikusan alkalmaz az összes, a **Marketingpromóciók** mappába mentett felhasználói dokumentumra. Bár a mappa védelmét a Marketing csoport hozzáférését korlátozó NTFS-engedélyek biztosítják, a rendszergazda tudja, hogy ezek az engedélyek elvesznek, ha a csoport egyik tagja áthelyezi vagy továbbküldi a fájlokat. Ilyen esetben a fájlokban szereplő adatokhoz illetéktelen felhasználó is hozzáférhet.

![MIT LÁTNAK A RENDSZERGAZDÁK AZ 1. LÉPÉSBEN?](../media/AzRMS_FCI_ConnectorSmall.png)

**MIT LÁTNAK A RENDSZERGAZDÁK AZ 1. LÉPÉSBEN:** A rendszergazda telepíti és konfigurálja a Rights Management- (RMS-) összekötőt, amely közvetítőként működik a helyszíni kiszolgálók és az Azure RMS között.

---

![MIT LÁTNAK A RENDSZERGAZDÁK A 2. LÉPÉSBEN?](../media/AzRMS_ExampleFCI_ConfigurationSmall.png)

**MIT LÁTNAK A RENDSZERGAZDÁK A 2. LÉPÉSBEN:** A rendszergazda konfigurálja a besorolási szabályokat és feladatokat a fájlkiszolgálón, hogy a **Marketing és promóció** mappában lévő összes felhasználói fájl besorolása automatikusan **Marketing** legyen, az RMS-titkosítás védelmével.

Az első példában létrehozott egyéni RMS-sablont választja, amely az Értékesítési és Marketingrészleg tagjainak hozzáférését korlátozza: **Értékesítés és marketing – Csak olvasásra és nyomtatásra**.

Ennek eredményeképpen a mappában lévő összes dokumentum automatikusan a Marketing besorolással lesz konfigurálva, az Értékesítés és marketing RMS-sablon pedig védelmet biztosít számukra.

---

![MIT LÁTNAK A RENDSZERGAZDÁK A 3. LÉPÉSBEN?](../media/AzRMS_FCI_EmailSmall.png)

**MIT LÁTNAK A RENDSZERGAZDÁK A 3. LÉPÉSBEN:** Hogyan gátolja meg az RMS, hogy olyan személyek kezébe kerüljenek az adatok, akik nem rendelkeznek hozzáféréssel a bizalmas vagy titkos információkhoz?

- A Marketingrészlegen dolgozó Janet e-mailben továbbít egy bizalmas jelentést a Marketingpromóciók mappából. A jelentés új termékjellemzőket és hirdetési terveket tartalmaz, és egy olyan munkatárs kérte, aki jelenleg üzleti úton van. Janet viszont véletlenül nem a megfelelő személynek küldi el – nem vette észre, hogy tévesen egy hasonló nevű, de más vállalatnál dolgozó személyt jelölt ki.<br><br>
A címzett nem tudja elolvasni a bizalmas jelentést, mert nem tagja az Értékesítés és marketing csoportnak.

---

**További információ erről a forgatókönyvről:**

- Részletes útmutatásért lásd: [Deploying the Azure Rights Management connector](../deploy-use/deploy-rms-connector.md) (Az Azure Rights Management-összekötő telepítése).

## E-mailek automatikus védelme az Exchange Online és az adatveszteség-megelőzési házirendek segítségével

Az előző példából kiderült, hogyan tudja automatikusan megvédeni a bizalmas információkat tartalmazó fájlokat. De mi van akkor, ha az információt nem egy fájl, hanem egy e-mail üzenet tartalmazza? Ekkor következnek az Exchange Online adatveszteség-megelőzési (DLP) házirendek, amelyek az adatvédelem alkalmazására kérik a felhasználókat (Házirendtippek használatával), vagy automatikusan alkalmazzák azokat helyettük (átviteli szabályok használatával).

Ebben a példában a rendszergazda konfigurál egy házirendet, hogy a szervezet megfeleljen az Egyesült Államok személyes azonosításra alkalmas adatokra vonatkozó szabályozásainak, de a szabályok egyéb megfelelőségi szabályozásokhoz vagy az Ön által meghatározott egyéni szabályokhoz is konfigurálhatók.

![MIT LÁTNAK A RENDSZERGAZDÁK AZ 1. LÉPÉSBEN?](../media/AzRMS_DLPExample1.png)

**MIT LÁTNAK A RENDSZERGAZDÁK AZ 1. LÉPÉSBEN:** Az Exchange felügyeleti központban az **Egyesült Államok Személyes azonosításra alkalmas adatok (PII)** nevű Exchange-sablon használatával a rendszergazda egy új DLP-házirendet hozhat létre és konfigurálhat. Ez a sablon a társadalombiztosítási és jogosítványszámokhoz hasonló információkat keres az e-mail üzenetekben.

A szabályok úgy vannak konfigurálva, hogy az ilyen adatokat tartalmazó és a szervezeten kívülre küldött e-mailek automatikusan tartalomvédetté váljanak az RMS-sablon használatával, amely kizárólag a vállalat alkalmazottaira korlátozza a hozzáférést.

A jelen esetben a szabály az egyik alapértelmezett sablon, az első példában szereplő **VanArsdel, Ltd – Bizalmas** használatára van konfigurálva. De azt is láthatja, hogy a választható sablonok között szerepel bármely Ön által létrehozott egyéni sablon, valamint egy **No Do Forward** (Nincs továbbítás) lehetőség, amely az Exchange-re vonatkozik.

---

![MIT LÁTNAK A RENDSZERGAZDÁK A 2. LÉPÉSBEN?](../media/AzRMS_DLPUnprotectedEmail_small.png)

**MIT LÁTNAK A FELHASZNÁLÓK A 2. LÉPÉSBEN:** A toborzó ír egy e-mail üzentet, amely egy nemrégiben felvett alkalmazott társadalombiztosítási számát tartalmazza. Elküldi ezt az üzentet Sherrie-nek, aki az emberi erőforrások részlegen dolgozik.

---

![MIT LÁTNAK A RENDSZERGAZDÁK A 3. LÉPÉSBEN?](../media/AzRMS_DLPProtectedEmail_small.png)

**MIT LÁTNAK A RENDSZERGAZDÁK A 3. LÉPÉSBEN:** Ha ezt az e-mailt egy szervezeten kívüli személynek küldik vagy továbbítják, a DLP-szabály automatikusan alkalmazza a tartalomvédelmet.

Amint az e-mail elhagyja a szervezet infrastruktúráját, megtörténik a titkosítása, így az üzenetben szereplő társadalombiztosítási szám átvitel közben vagy a címzett postaládájában nem lesz olvasható. A címzett nem tudja elolvasni az üzenetet, hacsak nem a VanArsdel alkalmazottja.

---

**További információ erről a forgatókönyvről:**

-   További információkat arról, hogyan működik együtt az Azure RMS és az Exchange Online a [How applications support Azure Rights Management](applications-support.md) (Hogyan támogatják a különböző alkalmazások az Azure Rights Managementet?) témakör [Exchange Online and Exchange Server](office-apps-services-support.md#exchange-online-and-exchange-server) (Exchange Online és Exchange Server) című szakaszában talál.

-   Részletes útmutatásért az Exchange Online Azure RMS-hez való konfigurálásához lásd: [Exchange Online: IRM Configuration](../deploy-use/configure-office365.md#exchange-online-irm-configuration) (Exchange Online: IRM konfiguráció) szakasz, [Configuring applications for Azure Rights Management](../deploy-use/configure-applications.md) (Alkalmazások konfigurálása az Azure Rights Managementhez) témakör.

## A fájlok automatikus védelme a SharePoint Online és a védett könyvtárak segítségével

Ez a szakasz bemutatja, hogyan védheti meg egyszerűen a dokumentumokat a SharePoint Online és a védett könyvtárak használatával.

Ebben a példában a Contoso SharePoint-rendszergazdája minden részleg számára létrehozott egy könyvtárat, amelyet a dokumentumok központi tárolására, valamint szerkesztési és verziókövetési célokra használnak. Van például egy könyvtár az Értékesítés, egy a Marketing, egy az Emberi erőforrások stb. számára. Ha egy új dokumentumot töltenek fel vagy hoznak létre az egyik védett mappában, akkor a dokumentum örökli a könyvtár védelmét (nincs szükség jogmegadási sablon kiválasztására). Így a dokumentum akkor is folyamatos védelem alatt áll, ha kikerül a SharePoint-könyvtárból.

![MIT LÁTNAK A RENDSZERGAZDÁK AZ 1. LÉPÉSBEN?](../media/AzRMS_StoryboardSPO_small1.png)

**MIT LÁTNAK A RENDSZERGAZDÁK AZ 1. LÉPÉSBEN:** A rendszergazda engedélyezi a tartalomvédelmi szolgáltatást a SharePoint-webhely számára.

---

![MIT LÁTNAK A RENDSZERGAZDÁK A 2. LÉPÉSBEN?](../media/AzRMS_StoryboardSPO_small2.png)

**MIT LÁTNAK A RENDSZERGAZDÁK A 2. LÉPÉSBEN:** Ezután engedélyezi a tartalomvédelmet a könyvtár számára. Bár vannak további lehetőségek is, ez az egyszerű beállítás a legtöbb esetben elegendő.

Mostantól a könyvtárból letöltött dokumentumokat a tartalomvédelem automatikus védelemmel látja el, és öröklik a könyvtárhoz konfigurált védelmet.

---

![MIT LÁTNAK A RENDSZERGAZDÁK A 3. LÉPÉSBEN?](../media/AzRMS_StoryboardSPO_small3.png)

**MIT LÁTNAK A FELHASZNÁLÓK A 3. LÉPÉSBEN:** Ha valaki az értékesítési részlegről megtekinti a könyvtárban lévő értékesítési jelenést, a fent lévő információs szalagcím alapján egyértelműen meg tudja állapítani, hogy ez egy védett dokumentum korlátozott hozzáféréssel.

A dokumentum védelme akkor is megmarad, ha a felhasználó átnevezi, máshova menti vagy megosztja e-mailben. Nem számít, mi a fájl neve, hol tárolják vagy megosztották-e e-mailben, csak az értékesítési részleg dolgozói tudják elolvasni.

---

**További információ erről a forgatókönyvről:**

-   További információkat arról, hogyan működik együtt az Azure RMS és a SharePoint a [How applications support Azure Rights Management](applications-support.md) (Hogyan támogatják a különböző alkalmazások az Azure Rights Managementet?) témakör [SharePoint Online and SharePoint Server](office-apps-services-support.md#sharepoint-online-and-sharepoint-server) (SharePoint Online és SharePoint Server) című szakaszában talál.

-   Részletes útmutatás a SharePoint Azure RMS-hez való konfigurálásához: [SharePoint Online and OneDrive for Business: IRM Configuration (SharePoint Online és OneDrive Vállalati verzió: IRM konfigurálása)](../deploy-use/configure-office365.md#sharepoint-online-and-onedrive-for-business-irm-configuration) szakasz a [Configuring Applications for Azure Rights Management (Alkalmazások konfigurálása az Azure Rights Managementhez)](../deploy-use/configure-applications.md) témakörben..

## A felhasználók biztonságosan oszthatják meg a mellékleteket a mobilfelhasználókkal

Az előző példák azt szemléltették, hogy a rendszergazdák hogyan tudnak automatikus adatvédelmet alkalmazni a bizalmas adatokon. Bizonyos esetekben viszont előfordulhat, hogy a felhasználóknak maguknak kell alkalmazniuk a védelmet. Ha például másik szervezethez tartozó partnerekkel dolgoznak együtt, akkor vagy olyan egyéni engedélyekre, illetve beállításokra van szükségük, amelyek nincsenek meghatározva a sablonokban, vagy alkalmi helyzetekre, amelyeket az előző példák nem fednek le. Ezekben a helyzetekben a felhasználók maguk alkalmazhatják az RMS-sablonokat, vagy egyéni engedélyeket hozhatnak létre.

Ez a példa szemlélteti, hogy a felhasználók hogyan tudnak egyszerűen megosztani egy dokumentumot egy másik vállalathoz tartozó munkatárssal úgy, hogy a dokumentum védelme megmaradjon, de a címzett biztosan el tudja olvasni, akár népszerű mobileszközről is. Ez a forgatókönyv a Rights Management megosztóalkalmazást használja, amelyet automatikusan telepíthet a szervezetében lévő Windows rendszerű számítógépekre. A felhasználók maguk is telepíthetik.

Ebben a példában a Contoso dolgozója, Ágnes e-mailben elküld egy bizalmas Word-dokumentumot Bálintnak, aki a Fabrikam alkalmazottja. Bálint az iPadjén olvassa el a dokumentumot, de ugyanezt könnyedén megtehette volna egy iPhone, egy Android táblagép vagy telefon, egy Mac-számítógép, illetve egy Windows-telefon vagy -számítógép segítségével is.

![MIT LÁTNAK A FELHASZNÁLÓK AZ 1. LÉPÉSBEN](../media/AzRMS_StoryboardEmail_small1.png)

**MIT LÁTNAK A FELHASZNÁLÓK AZ 1. LÉPÉSBEN:** Ágnes a Windows rendszerű számítógépén létrehoz egy szabványos e-mail üzenetet, és csatol hozzá egy dokumentumot.

A menüszalag **Védett megosztás** elemére kattint, amely betölti a **védett megosztás** párbeszédpanelt az RMS-megosztóalkalmazásból.

Ágnes azt szeretné, hogy Bálint csak megtekinteni és szerkeszteni tudja a dokumentumot, másolni vagy nyomtatni ne, úgyhogy a **REVIEWER – View and Edit (VÉLEMÉNYEZŐ – Megtekintés és szerkesztés)** lehetőséget választja. Azt is szeretné, ha e-mail értesítést kapna, amikor valaki megpróbálja megnyitni a dokumentumot, továbbá hogy később szükség esetén visszavonhassa a dokumentumot, és ez azonnali hatállyal érvénybe is lépjen.

---

![MIT LÁTNAK A FELHASZNÁLÓK A 2. LÉPÉSBEN](../media/AzRMS_StoryboardEmail_small2.png)

**MIT LÁTNAK A FELHASZNÁLÓK A 2. LÉPÉSBEN:** Bálint megtekinti az e-mailt az iPadjén.

Ágnes üzenetén és a mellékleten kívül az e-mail utasításokat is tartalmaz, amelyek követésével Bálint feliratkozik, és letölti az RMS-megosztóalkalmazást az iPad készülékére.

---

![MIT LÁTNAK A FELHASZNÁLÓK A 3. LÉPÉSBEN](../media/AzRMS_StoryboardEmail_small3.png)

**MIT LÁTNAK A FELHASZNÁLÓK A 3. LÉPÉSBEN:** Bálint most már meg tudja nyitni a mellékletet. Először be kell jelentkeznie, hogy megerősítse, ő az illetékes címzett.

Amikor Bálint megtekinti a dokumentumot, látja a korlátozott hozzáférésre vonatkozó információt is, amelyből megtudja, hogy megtekintheti és szerkesztheti a dokumentumot, de nem másolhatja vagy nyomtathatja ki.

---

![MIT LÁTNAK A FELHASZNÁLÓK A 4. LÉPÉSBEN](../media/AzRMS_StoryboardEmail_small4.png)

**MIT LÁTNAK A FELHASZNÁLÓK A 4. LÉPÉSBEN** Ágnes kap egy e-mail üzenetet, amelyből megtudja, hogy Bálint sikeresen megnyitotta az elküldött dokumentumot, valamint a megnyitás időpontját is.

Ha Bálint a melléklettel együtt továbbküldi az e-mailt, mások számára is elérhető helyre menti vagy elfogják a hálózaton, mások nem fogják tudni elolvasni a dokumentumot.

---

**További információ erről a forgatókönyvről:**

- A részletes útmutatást lásd: [Protect a file that you share by email](../rms-client/sharing-app-protect-by-email.md) (E-mailben megosztott fájl védelme) és [View and use files that have been protected](../rms-client/sharing-app-view-use-files.md) (Védett fájlok megtekintése és használata) [A Rights Management megosztóalkalmazás felhasználói útmutatójában](../rms-client/sharing-app-user-guide.md).

- A [Quick start tutorial for Azure Rights Management](../get-started/quick-start-tutorial.md) (Azure Rights Management gyors üzembe helyezési oktatóanyag) részletes útmutatást nyújt a forgatókönyvhöz.

## További lépések

Most, hogy a példákon keresztül láthatta, mire képes az Azure RMS, talán az is érdekelheti, hogyan képes minderre. Az Azure RMS működésével kapcsolatos műszaki információkért lásd: [Az Azure RMS működése](how-does-it-work.md)


<!--HONumber=Apr16_HO4-->


