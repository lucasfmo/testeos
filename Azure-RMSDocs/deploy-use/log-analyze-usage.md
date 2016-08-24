---
title: "Az Azure Rights Management használatának naplózása és elemzése | Azure RMS"
description: 
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 08/17/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: a735f3f7-6eb2-4901-9084-8c3cd3a9087e
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 437afd88efebd9719a3db98f8ab0ae07403053f7
ms.openlocfilehash: 28fed61b674112d2ebeb30a15a6f6217647e0b5f


---

# Az Azure Rights Management használatának naplózása és elemzése

*A következőkre vonatkozik: Azure Rights Management, Office 365*

A témakörben található információk segítségével megértheti az Azure Rights Management (Azure RMS) használatnaplózási szolgáltatásának alkalmazását. Az Azure Rights Management szolgáltatás képes a szervezet felé irányuló minden kérés naplózására, beleértve a felhasználóktól érkező kéréseket, a szervezet Rights Management-rendszergazdái által, valamint a Microsoft munkatársai által az Azure Rights Management telepítése során végrehajtott műveleteket is.

Ezek az Azure Rights Management-naplók a későbbiekben az alábbi üzleti forgatókönyvek támogatására használhatók:

-   **Üzleti elemzések készítése**

    Az Azure Rights Management által létrehozott naplók a kívánt tárhelyre (például adatbázisokba, online elemzésfeldolgozási (OLAP) rendszerekbe vagy MapReduce rendszerekbe) importálhatók az információk elemzése és jelentések készítése céljából. Így például azonosíthatóak az RMS-védelemmel ellátott adatokhoz hozzáférő személyek. Megadhatja, hogy mely RMS-védelemmel ellátott adatok, milyen eszközről és honnan legyenek elérhetők. Az írásvédett tartalmak hozzáférésének sikerességéről is meggyőződhet. Azt is megállapíthatja, hogy a korábban védelemmel ellátott, fontos dokumentumokat mely személyek olvasták.

-   **Visszaélés-figyelő**

    Az Azure Rights Management naplóinformációi csaknem valós időben érhetőek el, így folyamatosan nyomon tudja követni vállalatának Rights Management-használatát. A naplók 99,9%-a az RMS-kezdeményezésű művelet indításától számított 15 percen belül elérhető.

    Ha például figyelmeztetést szeretne kapni, amikor hirtelen több személy éri el az RMS-védelemmel ellátott adatokat a normál munkaidőn kívül, ami a versenytársak számára adatokat gyűjtő, rosszindulatú felhasználóra utalhat Vagy ha például ugyanaz a felhasználó rövid időn belül két különböző IP-címről kér le adatokat, ami az adott felhasználói fiók veszélyeztetettségére utalhat.

-   **Törvényszéki elemzés végrehajtása**

    Adatvesztés esetén vállalata valószínűleg tudni szeretné, hogy bizonyos dokumentumokhoz ki fért hozzá legutóbb, illetve egy gyanús személy milyen információkat érhetett el az utóbbi időben. Az ilyen típusú kérdéseket az Azure Rights Management és a naplózás segítségével meg tudja válaszolni, mivel a védett tartalmakat felhasználó személyek kizárólag Rights Management-licenc birtokában nyithatják meg az Azure Rights Management-védelemmel ellátott dokumentumokat és képeket, még abban az esetben is, ha ezek a fájlok e-mailben lettek áthelyezve, vagy egy USB-meghajtóra vagy egyéb tárolóeszközre lettek átmásolva. Mindez azt jelenti, hogy a Rights Management-naplók megbízható információforrásként szolgálnak a törvényszéki elemzések végrehajtásakor, ha adatait Azure Rights Management-védelemmel látja el.

> [!NOTE]
> Ha csupán az Azure Rights Management adminisztrációs feladatainak naplózása érdekli, és nem kívánja nyomon követni a felhasználók Rights Management-használatát, e célra az Azure Rights Management [Get-AadrmAdminLog](https://msdn.microsoft.com/library/azure/dn629430.aspx) Windows PowerShell-parancsmagját használhatja.
> 
> A klasszikus Azure-portált olyan magas szintű használati jelentések esetében is használhatja, mint például az **RMS összegzés**, az **Aktív RMS-felhasználók**, az **RMS eszközplatformok**, valamint az **RMS alkalmazáshasználat**. E jelentéseknek a klasszikus Azure-portálról történő eléréséhez kattintson az **Active Directory** elemre, jelöljön ki és nyisson meg egy könyvtárat, majd kattintson a **JELENTÉSEK** elemre,

Az Azure Rights Management használatnaplózásáról további információkat a következő részekben talál.

## Az Azure Rights Management használatnaplózásának engedélyezése
2016 februárjától az Azure Rights Management használatnaplózása alapértelmezés szerint valamennyi ügyfél számára engedélyezett. Ez minden olyan ügyfélre vonatkozik, aki Azure RMS szolgáltatását 2016 februárja előtt vagy után aktiválta. 

> [!NOTE]
> A naplók tárolásához, illetve a naplózási funkcióhoz nem kapcsolódik további költség.
> 
> 2016 februárja előtt az Azure RMS használatnaplózási funkciójának igénybevételéhez Azure-előfizetés és elegendő Azure-tárhely volt szükséges, azonban ez megváltozott.



## Az Azure Rights Management-használati naplók elérése és használata
Az Azure Rights Management az Azure-tárfiókba blobok sorozataként menti el a naplókat. Minden egyes blob egy vagy több naplóbejegyzést tartalmaz W3C bővített naplóformátumban. A blobok neveit számok jelölik a létrehozásuk sorrendjében. A jelen dokumentum későbbi szakaszában megtalálható, [Az Azure Rights Management használati naplók értelmezése](#how-to-interpret-your-azure-rights-management-usage-logs) részben további információk olvashatóak a naplók tartalmáról és azok létrehozásáról.

Az Azure Rights Management-műveletek végrehajtását követően a naplók tárfiókba kerülése hosszabb időt vehet igénybe. A naplók zöme 15 percen belül megjelenik. Javasolt a naplók helyi tárhelyre – például helyi mappába, adatbázisba vagy MapReduce tárolóba – történő letöltése.

A használati naplók letöltése a Windows PowerShellhez készült Azure RMS felügyeleti modullal történik. A telepítési utasításokért lásd: [Installing Windows PowerShell for Azure Rights Management](install-powershell.md) (Az Azure Rights Managementhez készült Windows PowerShell telepítése). Ha a Windows PowerShell-modult már korábban letöltötte, a következő parancs futtatásával ellenőrizze, hogy a verziószáma legalább **2.4.0.0**: `(Get-Module aadrm -ListAvailable).Version` 

### A használati naplók letöltése a PowerShell használatával

1.  **Futtatás rendszergazdaként** beállítással indítsa el a Windows PowerShellt, majd a [Connect-AadrmService](https://msdn.microsoft.com/library/azure/dn629415.aspx) parancsmagot használva csatlakozzon az Azure Rights Management szolgáltatáshoz:

    ```
    Connect-AadrmService
    ```
    
2.  Az egy adott dátumhoz tartozó naplók letöltéséhez futtassa a következő parancsot: 

    ```
    Get-AadrmUserLog -Path <location> -fordate <date>
    ```

    Például egy Logs elnevezésű mappa létrehozását követően az E meghajtón:
    
    * Az adott dátumhoz (például 2016. 02. 01.) tartozó naplók letöltéséhez futtassa a következő parancsot: `Get-AadrmUserLog -Path E:\Logs -fordate 2/1/2016`
    
    * Az adott dátumok közötti időszakhoz (például 2016. 02. 01. – 2016. 02. 14.) tartozó naplók letöltéséhez futtassa a következő parancsot: `Get-AadrmUserLog -Path E:\Logs -fromdate 2/1/2016 –todate 2/14/2016` 

Ha csak a nap van megadva, ahogy a jelen példában is szerepel, az időt a rendszer helyi idő szerint 00:00:00-ként értelmezi, majd azt UTC szerint konvertálja. Ha -fromdate vagy -todate paraméterekkel ad meg egy időtartamot (például: -fordate "2/1/2016 15:00:00"), akkor a dátumot és az időt a rendszer UTC szerint konvertálja. A Get-AadrmUserLog parancs használatával ezt követően lekérhetők a naplók az adott UTC szerinti időszakra.

Letöltési időszakként egy teljes napnál kevesebb nem adható meg.

Alapértelmezés szerint a parancsmag három szálat használ a naplók letöltéséhez. Ha nem áll rendelkezésre elegendő sávszélesség, és csökkenteni szeretné a naplók letöltéséhez szükséges időt, használja az 1–32 közötti értékeket támogató -NumberOfThreads paramétert. A következő parancs futtatásakor például a parancsmag 10 szálat származtat a naplók letöltéséhez: `Get-AadrmUserLog -Path E:\Logs -fromdate 2/1/2016 –todate 2/14/2016 -numberofthreads 10`


> [!TIP]
> A letöltött naplófájlokat egy CSV formátumú fájlba is összevonhatja a [Microsoft Log Parser](https://www.microsoft.com/download/details.aspx?id=24659) alkalmazásának használatával, amely a különböző ismert naplóformátumok közötti átváltásra használatos eszköz. Ezt az eszközt az adatok SYSLOG formátumba történő átváltásához vagy adatbázisba történő importáláshoz is használhatja. Az eszköz telepítését követően a `LogParser.exe /?` parancs futtatásával kérhet annak használatához segítséget vagy arról információkat. 
>
> Az alábbi parancs futtatásával például az összes adatot .log fájlformátumba importálhatja: `logparser –i:w3c –o:csv "SELECT * INTO AllLogs.csv FROM *.log"`

#### Ha manuálisan engedélyezte az Azure RMS használatnaplózást annak 2016. február 22-i módosítását megelőzően


Ha annak módosítását megelőzően is használta a használatnaplózást, a használati naplók az erre konfigurált Azure-tárfiókban megtalálhatóak. A naplózási szolgáltatás módosítása keretében a Microsoft nem másolja át a korábbi tárfiókban lévő naplókat az új, Azure RMS által felügyelt tárfiókba. A korábban létrehozott naplók kezeléséért a felhasználó felel, a régi naplókat pedig a [Get-AadrmUsageLog](https://msdn.microsoft.com/library/dn629401.aspx) parancsmag használatával töltheti le. Példa:

- Az összes elérhető napló letöltése az E:\logs mappába: `Get-AadrmUsageLog -Path "E:\Logs"`
    
- Adott blobtartomány letöltése: `Get-AadrmUsageLog –Path "E:\Logs" –FromCounter 1024 –ToCounter 2047`

Vegye figyelembe, hogy nem kell letöltenie a Get-AadrmUsageLog parancsmag használatával a naplókat, ha az alábbi körülmények bármelyike fennáll:

-  2016. február 22-én vagy azt megelőzően aktiválta az Azure Rights Management szolgáltatást, de nem engedélyezte a használatnaplózási funkciót.

- 2016. február 22-e után aktiválta az Azure Rights Management szolgáltatást.

## Az Azure Rights Management használati naplók értelmezése
Az Azure Rights Management használati naplók értelmezése során vegye figyelembe az alábbiakat.

### A naplók sorrendje
Az Azure Rights Management a naplókat blobok sorozataként menti. 

Minden egyes bejegyzés UTC időbélyeggel van ellátva. Mivel az Azure Rights Management több adatközpont számos kiszolgálóján fut egyszerre, a naplók sorrendje helytelennek tűnhet még abban az esetben is, ha azok időbélyegzőik szerint vannak rendezve. Az eltérés azonban kicsi, és jellemzően egy percen belül van. A legtöbb esetben a naplók elemzése szempontjából ez nem jelent problémát.

### A blob formátuma
Minden egyes blob W3C bővített naplóformátumban van. A következő két sorral kezdődnek:

**#Szoftver: RMS**

**#Verzió: 1.1**

Az elő sor megadja, hogy Azure Rights Management-naplókról van szó. A második sor azt adja meg, hogy a blob többi része az 1.1-es verzió specifikációját követi. Javasolt a blobok elemzését végző alkalmazásokkal ellenőriztetni ezt a két sort, mielőtt a blobok további részét értelmezni kezdené.

A harmadik sorban a tabulátorokkal elválasztott mezők nevei szerepelnek:

**#Mezők: dátum            idő            sorazonosító        kéréstípus           felhasználói azonosító       eredmény          korrelációs azonosító          tartalmi azonosító                tulajdonos e-mail címe           kiállító                     sablonazonosító             fájlnév                  kibocsátási dátum      ügyféladatok         ügyfél IP-címe            felügyeleti tevékenység            felhasználói szerep**

Az egymás utáni sorok egy-egy naplóbejegyzést képviselnek. A mezőkben szereplő értékek a megelőző sorban lévő értékek sorrendjét követik, és egymástól tabulátorokkal vannak elválasztva. Az egyes mezők értelmezéséhez a következő táblázat nyújt segítséget.

|Mező neve|W3C-adattípus|Leírás|Példaérték|
|--------------|-----------------|---------------|-----------------|
|dátum|Dátum|A kérés kiszolgálásának UTC szerinti dátuma.<br /><br />Az adat forrása a kérés kiszolgálójának helyi órája.|2013-06-25|
|időpont|Idő|A kérés kiszolgálásának UTC szerinti, 24 órás formátumban megadott időpontja.<br /><br />Az adat forrása a kérés kiszolgálójának helyi órája.|21:59:28|
|sorazonosító|Szöveg|A naplóbejegyzés egyedi GUID azonosítója. Ha nincs érték, a korrelációs azonosítóérték segítségével azonosíthatja a bejegyzést.<br /><br />Ez az érték a naplók összevonásakor vagy azok más formátumba történő másolásakor hasznos.|1c3fe7a9-d9e0-4654-97b7-14fafa72ea63|
|kéréstípus|Név|A lekért RMS API neve.|AcquireLicense|
|felhasználói azonosító|Karakterlánc|A kérés leadójának neve.<br /><br />Az érték szimpla idézőjelek között van. Az Ön által felügyelt bérlői kulcsból (BYOK) érkező hívások értéke **"**, amely akkor is érvényes, ha a kérések típusa „névtelen”.|‘joe@contoso.com’|
|eredmény|Karakterlánc|Ha a kérés kiszolgálása sikeresen megtörtént: „Sikeres”.<br /><br />Sikertelen kérés esetén a hiba típusa szimpla idézőjelek között szerepel.|'Sikeres'|
|korrelációs azonosító|Szöveg|Egy adott kérés esetében az RMS ügyfélnapló és kiszolgálónapló közös GUID azonosítója.<br /><br />Ez az érték az ügyfélpanaszok hibaelhárítása során lehet hasznos.|cab52088-8925-4371-be34-4b71a3112356|
|tartalmi azonosító|Szöveg|Kapcsos zárójelek közé írt GUID, amely azonosítja a védett tartalmat (például egy dokumentumot).<br /><br />A mezőben kizárólag AcquireLicense kéréstípus esetén szerepel érték, minden más esetben üres.|{bb4af47b-cfed-4719-831d-71b98191a4f2}|
|tulajdonos e-mail címe|Karakterlánc|A dokumentum tulajdonosának e-mail címe.|alice@contoso.com|
|kiállító|Karakterlánc|A dokumentum kiállítójának e-mail címe.|alice@contoso.com (vagy) FederatedEmail.4c1f4d-93bf-00a95fa1e042@contoso.onmicrosoft.com’|
|sablonazonosító|Karakterlánc|A dokumentum védelméhez használt sablon azonosítója.|{6d9371a6-4e2d-4e97-9a38-202233fed26e}|
|fájlnév|Karakterlánc|A védelemmel ellátott dokumentum fájlneve. <br /><br />Jelenleg néhány fájl (például az Office-dokumentumok) GUID azonosítóként jelenik meg a tényleges fájlnév helyett.|TopSecretDocument.docx|
|közzététel dátuma|Dátum|A dokumentum védelemmel történő ellátásának dátuma.|2015-10-15T21:37:00|
|ügyféladatok|Karakterlánc|Információk a kérést küldő ügyfélplatformról.<br /><br />A karakterlánc az alkalmazástól (például az operációs rendszertől vagy a böngészőtől) függően változik.|'MSIPC;version=1.0.623.47;AppName=WINWORD.EXE;AppVersion=15.0.4753.1000;AppArch=x86;OSName=Windows;OSVersion=6.1.7601;OSArch=amd64'|
|ügyfél IP-címe|Utca, házszám|A kérést küldő ügyfél IP-címe.|64.51.202.144|


#### A felhasználói azonosító mező kivételei
Bár a felhasználói azonosító mező általában meghatározza a kérést küldő felhasználót, két kivétel esetében az érték nem feleltethető meg valós felhasználónak:

-   A **'microsoftrmsonline@&lt;saját_bérlő_azonosítója&gt;.rms.&lt;régió&gt;.aadrm.com'** érték esetében.

    Ez azt jelzi, hogy a kérés küldője egy Office 365-szolgáltatás, például az Exchange Online vagy a SharePoint Online. A karakterláncban a *&lt;YourTenantID&gt;* érték a bérlőhöz tartozó GUID, a *&lt;region&gt;* értéke pedig az a régió, ahol a bérlőt regisztrálták. Például az **na** Észak-Amerikát, az **eu** Európát, az **ap** pedig Ázsiát jelzi.

-   RMS-összekötő használata esetén.

    Az összekötőről érkező kérések naplózása az **Aadrm_S-1-7-0** egyszerű szolgáltatásnévvel történik, amely automatikusan jön létre az RMS-összekötő telepítésekor.

#### Jellemző kéréstípusok
Az Azure Rights Management esetében számos kéréstípus létezik; az alábbi táblázatban a leggyakrabban használt kéréstípusok szerepelnek.

|Kéréstípus|Leírás|
|----------------|---------------|
|AcquireLicense|Egy ügyfél Windows-alapú gépről kér licencet egy RMS-védelemmel ellátott tartalomhoz.|
|AcquirePreLicense|Egy ügyfél – a felhasználó nevében – kér licencet egy RMS-védelemmel ellátott tartalomhoz.|
|AcquireTemplates|Sablonok beszerzését kezdeményezték sablonazonosító alapján|
|AcquireTemplateInformation|A sablon azonosítóinak beszerzését kezdeményezték a szolgáltatásból.|
|AddTemplate|Sablon hozzáadását kezdeményezték a klasszikus Azure-portálról.|
|AllDocsCsv|A dokumentumkövetési webhelyről kérés érkezett a CSV-fájl letöltésére a **Minden dokumentum** lapról.|
|BECreateEndUserLicenseV1|Végfelhasználói licenc létrehozását kezdeményezték egy mobileszközről.|
|BEGetAllTemplatesV1|Az összes sablon beszerzését kezdeményezték (a háttérben) egy mobileszközről.|
|Certify|Az ügyfél védelmi hitelesítést végez az adott tartalmon.|
|DeleteTemplateById|Sablon törlését kezdeményezték a klasszikus Azure-portálról egy sablonazonosító alapján.|
|DocumentEventsCsv|A dokumentumkövetési webhelyről kérés érkezett egyetlen dokumentum .CSV-fájljának letöltésére.|
|ExportTemplateById|Sablon exportálását kezdeményezték a klasszikus Azure-portálról egy sablonazonosító alapján.|
|FECreateEndUserLicenseV1|Az AcquireLicense kéréshez hasonló tartalommal bír, de mobileszközökről.|
|FECreatePublishingLicenseV1|Megfelel a Certify és a GetClientLicensorCert kérések kombinációjának egy mobileszközről küldve.|
|FEGetAllTemplates|A sablonok beszerzését kezdeményezték (az előtérben) egy mobileszközről.|
|FindServiceLocationsForUser|URL-címek lekérdezését kezdeményezték a Certify vagy az AcquireLicense kéréshez.|
|GetAllDocs|A dokumentumkövetési webhelyről kérés érkezett a **Minden dokumentum** lap betöltésére egy felhasználó számára, vagy az összes dokumentumban való keresésre a bérlő számára. Ez az érték a felügyeleti tevékenység és a felügyeleti szerep mezőknél használható:<br /><br />- a felügyeleti tevékenység értéke üres: Egy felhasználó a saját dokumentumaihoz tartozó **Minden dokumentum** lapot tekinti meg.<br /><br />- a felügyeleti tevékenység értéke igaz, a felhasználói szerep értéke üres: Egy rendszergazda megtekinti a bérlő minden dokumentumát.<br /><br />- a felügyeleti tevékenység értéke igaz, a felhasználói szerep értéke nem üres: Egy rendszergazda egy felhasználó **Minden dokumentum** lapját tekinti meg.|
|GetAllTemplates|Az összes sablon beszerzését kezdeményezték a klasszikus Azure-portálról.|
|GetClientLicensorCert|Az ügyfél (később tartalomvédelmi céllal felhasználni kívánt) közzétételi tanúsítványt kér le egy Windows-alapú számítógépről.|
|GetConfiguration|Azure PowerShell parancsmag beszerzését kezdeményezték az Azure RMS-bérlő konfigurációjának beszerzéséhez.|
|GetConnectorAuthorizations|Felhőből történő konfiguráció-beszerzési hívás érkezett az RMS-összekötőkről.|
|GetRecipients|A dokumentumkövetési webhelyről kérés érkezett egyetlen dokumentum listanézetének megnyitására.|
|GetSingle|A dokumentumkövetési webhelyről kérés érkezett **egyetlen dokumentum** oldalának megnyitására.|
|GetTenantFunctionalState|A klasszikus Azure-portál ellenőrzi, hogy az Azure RMS aktiválva van-e.|
|GetTemplateById|Egy sablon beszerzését kezdeményezték a klasszikus Azure-portálról egy sablonazonosító megadásával.|
|KeyVaultDecryptRequest|Az ügyfél az RMS-védelemmel ellátott tartalom visszafejtésére tesz kísérletet. Csak az ügyfél által az Azure Key Vaultban felügyelt bérlői kulcsra (BYOK) érvényes.|
|KeyVaultGetKeyInfoRequest|Ellenőrzi, hogy az Azure Key Vaultban az Azure RMS-bérlőkulcshoz megadott kulcs elérhető-e és nincs-e még használatban.|
|KeyVaultSignDigest|Ha az ügyfél által az Azure Key Vaultban felügyelt bérlői kulcsot (BYOK) aláírásra használják, a rendszer hívást kezdeményez. Ennek meghívása az AcquireLicence (vagy a FECreateEndUserLicenseV1), a Certify és a GetClientLicensorCert (vagy FECreatePublishingLicenseV1) kérések használatakor jellemzően egyszer történik meg.|
|KMSPDecrypt|Az ügyfél az RMS-védelemmel ellátott tartalom visszafejtésére tesz kísérletet. Csak az örökölt, ügyfél által felügyelt bérlői kulcsra (BYOK) érvényes.|
|KMSPSignDigest|Ha az örökölt, ügyfél által felügyelt bérlői kulcsot (BYOK) aláírásra használják, a rendszer hívást kezdeményez. Ennek meghívása az AcquireLicence (vagy a FECreateEndUserLicenseV1), a Certify és a GetClientLicensorCert (vagy FECreatePublishingLicenseV1) kérések használatakor jellemzően egyszer történik meg.|
|LoadEventsForMap|A dokumentumkövetési webhelyről kérés érkezett egyetlen dokumentum térképnézetének megnyitására.|
|LoadEventsForSummary|A dokumentumkövetési webhelyről kérés érkezett egyetlen dokumentum idősor nézetének megnyitására.|
|LoadEventsForTimeline|A dokumentumkövetési webhelyről kérés érkezett egyetlen dokumentum térképnézetének megnyitására.|
|ImportTemplate|Egy sablon importálását kezdeményezték a klasszikus Azure-portálról.|
|RevokeAccess|A dokumentumkövetési webhelyről kérés érkezett egy dokumentum visszavonására.|
|SearchUsers |A dokumentumkövetési webhelyről kérés érkezett felhasználók keresésére egy bérlőn belül.|
|ServerCertify|A kiszolgáló hitelesítését kezdeményezték egy RMS-kompatibilis ügyfélről (például SharePointról).|
|SetUsageLogFeatureState|A használatnaplózás engedélyezését kezdeményezték.|
|SetUsageLogStorageAccount|Az Azure RMS-naplók helyének megadását kezdeményezték.|
|UpdateNotificationSettings|A dokumentumkövetési webhelyről kérés érkezett egy dokumentum értesítési beállításainak módosítására.|
|UpdateTemplate|Egy meglévő sablon frissítését kezdeményezték a klasszikus Azure-portálról.|


## Referencia a Windows PowerShellhez
2016 februárjától kezdődően az Azure RMS használatnaplózásához szükséges egyetlen Windows PowerShell-parancsmag a [Get-AadrmUserLog](https://msdn.microsoft.com/library/azure/mt653941.aspx). 

Ezen változtatás előtt az alábbi, mára elavult parancsmagokra volt szükség az Azure RMS használati naplóihoz:  

-   [Disable-AadrmUsageLogFeature](https://msdn.microsoft.com/library/azure/dn629404.aspx)

-   [Enable-AadrmUsageLogFeature](https://msdn.microsoft.com/library/azure/dn629421.aspx)

-   [Get-AadrmUsageLog](https://msdn.microsoft.com/library/azure/dn629401.aspx)

-   [Get-AadrmUsageLogFeature](https://msdn.microsoft.com/library/azure/dn629425.aspx)

-   [Get-AadrmUsageLogLastCounterValue](https://msdn.microsoft.com/library/azure/dn629423.aspx)

-   [Get-AadrmUsageLogStorageAccount](https://msdn.microsoft.com/library/azure/dn629419.aspx)

-   [Set-AadrmUsageLogStorageAccount](https://msdn.microsoft.com/library/azure/dn629426.aspx)

Ha találhatók naplók az Azure-tárolóban az Azure RMS naplózását érintő változás előttről, letöltheti azokat a régebbi Get-AadrmUsageLog és Get-AadrmUsageLogLastCounterValue parancsmag használatával a szokásos módon. Az új használatnaplók azonban mind az új Azure RMS-tárolóra fognak írni, és a Get-AadrmUserLog segítségével kell letöltenie azokat.

További információ az Azure Rights Managementhez készült Windows PowerShell használatáról: [Administering Azure Rights Management by Using Windows PowerShell](administer-powershell.md) (Az Azure Rights Management felügyelete a Windows PowerShell használatával).






<!--HONumber=Aug16_HO3-->


