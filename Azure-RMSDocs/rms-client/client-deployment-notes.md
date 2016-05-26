---
# required metadata

title: RMS-ügyfél üzembe helyezésével kapcsolatos megjegyzések | Azure RMS
description:
keywords:
author: cabailey
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 03cc8c6f-3b63-4794-8d92-a5df4cdf598f

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: esaggese
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# RMS-ügyfél üzembe helyezésével kapcsolatos megjegyzések

*A következőkre vonatkozik: Active Directory tartalomvédelmi szolgáltatások, Azure Rights Management, Windows 7 SP1, Windows 8, Windows 8.1, Windows Server 2008, Windows Server 2008 R2, Windows Server 2012, Windows Server 2012 R2, Windows Vista*

A tartalomvédelmi szolgáltatások ügyfélprogramjának (RMS-ügyfél) 2. verziója más néven MSIPC ügyfélként is ismert. Ez egy olyan, Windows rendszerű számítógépeken futó szoftver, amely kommunikál a helyszíni vagy a felhőben található Microsoft Rights Management-szolgáltatásokkal, ezzel segítve az alkalmazásokon és eszközökön áthaladó információk hozzáférésének és felhasználásának védelmét, a szervezet határain belül és a felügyelt határokon kívül is. A [Windows Rights Management megosztóalkalmazásával](sharing-app-windows.md) beszerezhető RMS-ügyfél [választható letöltésként](http://www.microsoft.com/download/details.aspx?id=38396) is elérhető, amely – a hozzá tartozó licencszerződés tudomásul vétele és elfogadása után – szabadon együtt terjeszthető harmadik féltől származó szoftverekkel, hogy az ügyfelek képesek legyenek a tartalmak védelmére és a Rights Management-szolgáltatások által védett tartalmak felhasználására.


## Az RMS-ügyfél terjesztése
Az RMS-ügyfél szabadon terjeszthető és mellékelhető más alkalmazásokhoz vagy IT-megoldásokhoz. Ha Ön egy alkalmazásfejlesztő vagy megoldásszolgáltató, és szeretné terjeszteni az RMS-ügyfelet, két lehetőség közül választhat:

-   Ajánlott: Ágyazza be az RMS-ügyfél telepítőjét az alkalmazása telepítőjébe, és futtassa azt csendes módban (a **/quiet** kapcsolóval, amelynek részletes ismertetése a következő szakaszban olvasható).

-   Tegye az RMS-ügyfelet a saját alkalmazása előfeltételévé. Ennél a lehetőségnél előfordulhat, hogy a felhasználókat további információkkal kell ellátnia az ügyfél beszerzésével és telepítésével, illetve a számítógépeik frissítésével kapcsolatban, mielőtt használni kezdhetik az Ön alkalmazását.

## Az RMS-ügyfél telepítése
Az RMS-ügyfelet egy **setup_msipc_***<arch>***.exe** nevű végrehajtható telepítőfájl tartalmazza, ahol a *<arch>* értéke **x86** (32 bites ügyfélszámítógépek esetén) vagy **x64** (64 bites ügyfélszámítógépek esetén). A 64 bites (x64) telepítőcsomag egyaránt telepít egy 32 bites futtatási környezetű végrehajtható fájt a 64 bites operációs rendszeren futó 32 bites alkalmazásokkal való kompatibilitás érdekében, valamint egy 64 bites futtatási környezetű végrehajtható fájlt a natív 64 bites alkalmazások támogatásához. A 32 bites (x86) telepítő nem fog futni egy 64 bites Windows telepítés alatt.

> [!NOTE]
> Az RMS-ügyfél telepítéséhez emelt szintű jogosultságok szükségesek, például a helyi számítógépen a Rendszergazdák csoport tagjának kell lennie.

Az RMS-ügyfelet az alábbi módokon telepítheti:

-   **Csendes mód.** A parancssori opciók közül a **/quiet** kapcsoló használatával beavatkozás nélkül telepítheti számítógépekre az RMS-ügyfelet. A következő példa az RMS-ügyfél csendes módban történő telepítését mutatja egy 64 bites ügyfélszámítógépre:

    ```
    setup_msipc_x64.exe /quiet
    ```

-   **Interaktív mód.** Az RMS-ügyfél telepítése egy grafikus felhasználói felületen alapuló telepítőprogrammal is elvégezhető, amelyet az RMS-ügyfél telepítővarázslója biztosít. Ehhez kattintson duplán az RMS-ügyfél telepítőcsomagjára (**setup_msipc_***<arch>***.exe**) abban a mappában, amelyikbe a helyi számítógépére másolta vagy letöltötte azt.

## Kérdések és válaszok az RMS-ügyféllel kapcsolatban
A következő szakasz az RMS-ügyfél verziójával kapcsolatos gyakori kérdéseket és az azokra adott válaszokat tartalmazza.

### Mely operációs rendszerek támogatják az RMS-ügyfelet?
Az RMS-ügyfelet a következő operációs rendszerek támogatják:

|Windows Server operációs rendszer|Ügyféloldali Windows operációs rendszer|
|-----------------------------------|-----------------------------------|
|Windows Server 2012 R2|Windows 8.1|
|Windows Server 2012|Windows 8|
|Windows Server 2008 R2|Windows 7, legalább Service Pack 1-gyel|
|Windows Server 2008 (csak AD RMS esetén)|Windows Vista, legalább Service Pack 2-vel (csak AD RMS esetén)|

### Mely processzorok vagy platformok támogatják az RMS-ügyfelet?
Az RMS-ügyfelet az x86- és x64-platformok is támogatják.

### Hova lesz telepítve az RMS-ügyfél?
Alapértelmezés szerint az RMS-ügyfél a %ProgramFiles%\Active Directory Rights Management Services Client 2 mappába lesz telepítve.<minor version number>.

### Mely kiegészítő fájlok tartoznak az RMS-ügyfélszoftverhez?
A következő fájlok lesznek telepítve a számítógépre az RMS-ügyfélszoftver részeként:

-   Msipc.dll

-   Ipcsecproc.dll

-   Ipcsecproc_ssp.dll

-   MSIPCEvents.man

Ezen fájlok mellett az RMS-ügyfél a többnyelvű kezelőfelület (MUI) támogatófájljait is telepíti, 44 nyelven. A támogatott nyelvek ellenőrzéséhez futtassa le az RMS-ügyfél telepítőjét, és a telepítés befejeztével nézze át az alapértelmezett elérési út alatt található többnyelvű támogatási mappák tartalmát.

### Ha egy támogatott operációs rendszert telepítek, abba az RMS-ügyfél alapértelmezés szerint beletartozik?
Nem. Az RMS-ügyfél ezen verziója választható letöltésként lett terjesztve, amelyet különállóan lehet telepíteni a Microsoft Windows operációs rendszer támogatott verzióit futtató számítógépekre.

### Az RMS-ügyfél automatikusan frissül a Microsoft Update szolgáltatáson keresztül?
Ha az RMS-ügyfelet a csendes lehetőség használatával telepíti, akkor az ügyfél örökli a jelenlegi Microsoft Update-beállításokat. Ha az RMS-ügyfelet a grafikus felhasználói felületen alapuló telepítőprogrammal telepíti, akkor a telepítővarázsló felkínálja a Microsoft Update engedélyezésének lehetőségét.

## Az RMS-ügyfél beállításai
A következő szakasz az RMS-ügyfél beállításaival kapcsolatos információkat tartalmazza. Ezek az információk akkor lehetnek hasznosak, ha problémák adódnak az RMS-ügyfelet használó alkalmazásokkal vagy szolgáltatásokkal.

> [!NOTE]
> Egyes beállítások attól függenek, hogy az RMS-kompatibilis alkalmazás ügyfélmódú alkalmazásként fut-e (pl. Microsoft Word és Outlook, vagy az RMS megosztóalkalmazás), vagy kiszolgálói módúként (pl. SharePoint és Exchange).  A következő táblázatokban ezek a beállítások **Ügyfélmód** és **Kiszolgáló üzemmód** néven szerepelnek.

### Hol tárolja az RMS-ügyfél az ügyfélszámítógépeken a licenceket?
Az RMS-ügyfél a licenceket a helyi lemezen tárolja, valamint bizonyos információkat a Windows beállításjegyzékében is gyorsítótáraz.

|Leírás|Az ügyfél üzemmód elérési útjai|A kiszolgáló üzemmód elérési útjai|
|---------------|---------------------|---------------------|
|A licenc tárolási helye|%localappdata%\Microsoft\MSIPC|%allusersprofile%\Microsoft\MSIPC\Server\*<SID>*\|
|A sablon tárolási helye|%localappdata%\Microsoft\MSIPC\Templates|%allusersprofile%\Microsoft\MSIPC\Server\Templates\*<SID>*\|
|Beállításjegyzékbeli hely|HKEY_CURRENT_USER<br /> \Software<br /> \Classes<br /> \Local Settings<br /> \Software<br /> \Microsoft<br /> \MSIPC|HKEY_CURRENT_USER<br /> \Software<br /> \Microsoft<br /> \MSIPC<br /> \Server<br /> \*<SID>*|
> [!NOTE]
> A *<SID>* a kiszolgálóalkalmazást futtató fiók biztonságos azonosítója (SID). Például, ha az alkalmazás a beépített hálózati szolgáltatásfiók alatt fut, cserélje le az *<SID>* értékét a fiók jól ismert SID-értékével (S-1-5-20).

### Az RMS-ügyfél Windows-beállításjegyzékbeli beállításai
Az RMS-ügyfél néhány beállításának megadása vagy módosítása Windows-beállításkulcsok használatával is történhet. Például RMS-kompatibilis, az AD RMS-kiszolgálókkal kommunikáló alkalmazásokkal foglalkozó rendszergazdaként elképzelhető, hogy frissíteni kívánja a vállalati szolgáltatási helyszínt (felülírva a közzétételre jelenleg kiválasztott AD RMS-kiszolgálót) az ügyfélszámítógépnek az Active Directory-topológiában elfoglalt jelenlegi helyétől függően. Vagy esetleg engedélyezni kívánja az RMS-nyomkövetést az ügyfélszámítógépen egy RMS-kompatibilis alkalmazással kapcsolatos probléma megoldása érdekében. A következő táblázat alapján beazonosíthatja a beállításjegyzék azon beállításait, amelyeket az RMS-ügyfélre vonatkozóan megváltoztathat.

|Feladat|Beállítások|
|--------|------------|
|Csak AD RMS esetén: Ügyfélszámítógép vállalati szolgáltatási helyszínének frissítése|Frissítse a következő beállításkulcsokat:<br /><br />HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\ServiceLocation\EnterpriseCertification<br />REG_SZ: default<br /><br />**Érték:**<http or https>:// *RMS_fürt_neve*/_wmcs/Certification<br /><br />HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\ServiceLocation\EnterprisePublishing<br />REG_SZ: default<br /><br />**Érték:** <http or https>:// *RMS_fürt_neve*/_wmcs/Licensing|
|Nyomkövetés engedélyezése és letiltása|Frissítse a következő beállításkulcsot:<br /><br />HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC<br />REG_DWORD: Trace<br /><br />**Érték:** 1 a nyomkövetés engedélyezéséhez, 0 a nyomkövetés letiltásához (alapértelmezett)|
|A sablonok napokban mért frissítési gyakoriságának megváltoztatása|A következő beállításértékek határozták meg, hogy a sablonok milyen gyakran frissülnek a felhasználó számítógépén, ha a TemplateUpdateFrequencyInSeconds érték nincs megadva.  Ha ezen értékek egyike sincs megadva, az alapértelmezett frissítési gyakoriság a sablonok letöltésére az RMS-ügyfelet (1.0.1784.0-s verzió) használó alkalmazások esetében 1 nap. Az ennél korábbi verziók esetében az alapértelmezett gyakoriság 7 nap.<br /><br />**Ügyfélmód:**<br /><br />HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC<br />REG_DWORD: TemplateUpdateFrequency<br /><br />**Érték:** Egész szám, amely meghatározza a letöltések között eltelt napok számát (legalább 1).<br /><br />**Kiszolgáló üzemmód:**<br /><br />HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\Server\*<SID>*<br />REG_DWORD: TemplateUpdateFrequency<br /><br />**Érték:** Egész szám, amely meghatározza a letöltések között eltelt napok számát (legalább 1).|
|A sablonok másodpercekben mért frissítési gyakoriságának módosítása<br /><br />Fontos: Ha ez az érték meg van adva, a rendszer a sablonok frissítésének napokban megadott értékét figyelmen kívül hagyja. A kettő közül csak az egyiket adja meg.|A következő beállításértékek határozzák meg, hogy a sablonok milyen gyakran frissülnek a felhasználó számítógépén. Ha sem ezen érték, sem a napokban megadott érték (TemplateUpdateFrequency) nincs megadva, az alapértelmezett frissítési gyakoriság a sablonok letöltésére az RMS-ügyfelet (1.0.1784.0 verzió) használó alkalmazások esetében 1 nap. Az ennél korábbi verziók esetében az alapértelmezett gyakoriság 7 nap.<br /><br />**Ügyfélmód:**<br /><br />HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC<br />REG_DWORD: TemplateUpdateFrequencyInSeconds<br /><br />**Érték:** Egész szám, amely meghatározza a letöltések között eltelt másodpercek számát (legalább 1).<br /><br />**Kiszolgáló üzemmód:**<br /><br />HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\Server\*<SID>*<br />REG_DWORD: TemplateUpdateFrequencyInSeconds<br /><br />**Érték:** Egész szám, amely meghatározza a letöltések között eltelt másodpercek számát (legalább 1).|
|Csak AD RMS esetén: A sablonok azonnali letöltése a következő közzétételi kérelemkor|A tesztelés és értékelés során hasznos, ha az RMS-ügyfelet úgy állítja be, hogy a lehető leghamarabb letöltse a sablonokat. Ehhez távolítsa el a következő beállításkulcsot, és az RMS-ügyfél a TemplateUpdateFrequency beállításban megadott időtartam kivárása helyett a következő közzétételi kérelemkor azonnal le fogja tölteni a sablonokat:<br /><br />HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC\<kiszolgáló_neve>\Template<br /><br />**Megjegyzés**: <Server Name> Rendelkezhet külső (corprights.contoso.com) és belső (corprights) URL-címekkel, ezáltal két külön bejegyzéssel is.|
|Csak AD RMS esetén: Az összevont hitelesítés támogatásának engedélyezése|Ha az RMS-ügyfélszámítógép egy AD RMS-fürthöz összevont megbízhatóság használatával csatlakozik, be kell állítania az összevonási kezdőtartományt.<br /><br />HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\Federation<br />REG_SZ: FederationHomeRealm<br /><br />**Érték:** Ez a beállításjegyzékbeli bejegyzésérték az összevonási szolgáltatás egységes erőforrás-azonosítója (URI-ja; például „https://fs-01.contoso.com”).|
|Csak AD RMS esetén: A felhasználói adatbevitelhez űrlapalapú hitelesítést igénylő partner összevonási kiszolgálók támogatása|Alapértelmezés szerint az RMS-ügyfél csendes módban működik, és nincs szükség felhasználói adatbevitelre. Azonban lehetséges, hogy a partner összevonási kiszolgálók a konfigurációjuk szerint felhasználói adatbevitelt kérnek, például űrlapalapú adatbevitel formájában. Ez esetben az RMS-ügyfelet a csendes mód figyelmen kívül hagyására kell beállítania, hogy az összevont hitelesítési űrlap megjelenjen egy böngészőablakban, és a felhasználónak hitelesítenie kelljen magát.<br /><br />HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\Federation<br />REG_DWORD: EnableBrowser<br /><br />**Megjegyzés**: Ha az összevonási kiszolgáló az űrlapalapú hitelesítés használatára van konfigurálva, akkor a kulcs mindenképpen szükséges. Ha az összevonási kiszolgáló a Windows beépített hitelesítés használatára van konfigurálva, akkor a kulcs nem szükséges.|
|Csak AD RMS esetén: Az ILS-szolgáltatás adatfelhasználásának letiltása|Alapértelmezés szerint az RMS-ügyfél engedélyezi az ILS-szolgáltatás által védett tartalmak felhasználását, de a következő beállításkulccsal az ügyfél e szolgáltatás blokkolására is beállítható. Ha a beállításkulcs az ILS-szolgáltatás blokkolására van beállítva, az ILS-szolgáltatás által védett tartalom megnyitására vagy használatára tett bármilyen kísérlet a következő hibaüzenetet eredményezi:<br />HRESULT_FROM_WIN32(ERROR_ACCESS_DISABLED_BY_POLICY)<br /><br />HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC<br />REG_DWORD: **DisablePassportCertification**<br /><br />**Érték**: 1 az ILS-használat blokkolásához, 0 az ILS-használat engedélyezéséhez (alapértelmezett)|

### Az RMS-ügyfél sablonterjesztésének felügyelete
A sablonok megkönnyítik a felhasználók és a rendszergazdák számára a Rights Management-védelem alkalmazását, és az RMS-ügyfél automatikusan letölti a sablonokat az RMS-kiszolgálóiról vagy RMS-szolgáltatásáról. Ha a sablonokat a következő mappába helyezi, az RMS-ügyfél nem fog az alapértelmezett helyéről sablonokat letölteni, hanem ehelyett az ebbe a mappába helyezett sablonokat tölti le. Lehetséges, hogy az ügyfél továbbra is letölt majd sablonokat más elérhető RMS-kiszolgálókról.

**Ügyfélmód:** %localappdata%\Microsoft\MSIPC\UnmanagedTemplates

**Kiszolgáló üzemmód:** %allusersprofile%\Microsoft\MSIPC\Server\UnmanagedTemplates\*<SID>*

Amikor ezt a mappát használja, semmilyen különleges elnevezési kikötés nincs azon túlmenően, hogy a sablonokat az RMS-kiszolgálónak vagy RMS-szolgáltatásnak kell kiállítania, és .xml kiterjesztéssel kell rendelkezniük. Például mind a Contoso-Confidential.xml, mind a Contoso-ReadOnly.xml érvényes nevek.

## Csak AD RMS esetén: Az RMS-ügyfél korlátozása a megbízható AD RMS-kiszolgálók használatára
Az RMS-ügyfelet korlátozhatja kizárólag adott, megbízható AD RMS-kiszolgálók használatára, ha a helyi számítógépek Windows beállításjegyzékén végrehajtja a következő módosításokat.

**Az RMS-ügyfél megbízható AD RMS-kiszolgálók használatára való korlátozásának engedélyezése**

-   HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\TrustedServers\
    REG_DWORD: AllowTrustedServersOnly

    **Érték:** Nullától eltérő érték megadásakor az RMS-ügyfél kizárólag olyan megadott kiszolgálókban fog megbízni, amelyek be vannak állítva a TrustedServers (Megbízható kiszolgálók) listán és az Azure Rights Management-szolgáltatásban.

**Tagok hozzáadása a megbízható AD RMS-kiszolgálók listájához**

-   HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\TrustedServers\
    REG_SZ: *<URL_vagy_állomásnév>*

    **Érték:** Az alábbi beállításkulcs helyén megadott karakterlánc-értékeket megadhatja DNS tartománynév-formátumban (például „**adrms.contoso.com**”), vagy megbízható kiszolgálók teljes URL-címeként is (például „**https://adrms.contoso.com**”). Ha a megadott URL **https://** előtaggal kezdődik, az RMS-ügyfél SSL vagy TLS használatával fog a megadott AD RMS-kiszolgálóhoz csatlakozni.

## RMS-szolgáltatásészlelés
Az RMS-szolgáltatásészlelés engedélyezi az RMS-ügyfél számára, hogy ellenőrizze, melyik RMS-kiszolgálóval kell kommunikálnia a tartalmak levédése előtt. A szolgáltatásészlelés akkor is megtörténhet, amikor az RMS-ügyfél védett tartalmakat használ fel, ez azonban kevésbé valószínű, mivel a tartalmakhoz csatolt házirend tartalmazza az előnyben részesített RMS-kiszolgálót vagy RMS-szolgáltatást, és az ügyfél csak akkor futtatja le a szolgáltatásészlelést, ha ezekhez nem tud csatlakozni.

A szolgáltatásészlelés először egy helyszíni Rights Management- (AD RMS-) verziót keres. Ha nem talál ilyet, akkor a szolgáltatásészlelés automatikusan keresni kezdi a Rights Management (Azure RMS) felhőbeli verzióját.

Helyszíni telepítés utáni szolgáltatásészleléskor az RMS-ügyfél a következőket ellenőrzi:

1.  A helyi számítógép Windows beállításjegyzéke: Ha a beállításjegyzékben meg vannak adva a szolgáltatásészlelés beállításai, először ezeket próbálja meg használni.  Alapértelmezés szerint ezek a beállítások nincsenek megadva a beállításjegyzékben.

2.  Active Directory tartományi szolgáltatások: Egy, a tartományhoz csatlakozó számítógép szolgáltatáskapcsolati pontot (SCP) kér az Active Directorytól. Ha az SCP regisztrálva van, az RMS-ügyfél megkapja használatra az RMS-kiszolgáló URL-címét.

### Csak AD RMS esetén: Kiszolgálóoldali szolgáltatásészlelés engedélyezése az Active Directory használatával
Ha a fiókja megfelelő jogosultságokkal rendelkezik (vállalati rendszergazda és az AD RMS-kiszolgáló helyi rendszergazdája), az AD RMS-gyökérfürtkiszolgáló telepítésekor automatikusan regisztrálhat egy szolgáltatáskapcsolati pontot (SCP). Ha már létezik az erdőben egy SCP, azt először törölnie kell, mielőtt egy újat regisztrálhatna.

Az AD RMS telepítése után a következő eljárással regisztrálhat és törölhet SCP-ket. Kezdés előtt győződjön meg róla, hogy a fiókja rendelkezik a megfelelő jogosultságokkal (vállalati rendszergazda és az AD RMS-kiszolgáló helyi rendszergazdája).

#### Az AD RMS szolgáltatásészlelés engedélyezése egy SCP regisztrálásával az Active Directoryban

1.  Nyissa meg az Active Directory Management Services kezelőpultját az AD RMS-kiszolgálón:

    -   Ha Windows Server 2008 R2 vagy Windows Server 2008 rendszert használ, kattintson a **Start** gombra, a **Felügyeleti eszközök**, majd az **Active Directory Rights Management Services** elemre..

    -   Ha Windows Server 2012 R2 vagy Windows Server 2012 rendszert használ, a Kiszolgálókezelőben kattintson az **Eszközök**, majd az **Active Directory Rights Management Services** elemre..

2.  Az AD RMS konzolon kattintson a jobb gombbal az AD RMS-fürtre, majd kattintson a **Tulajdonságok** elemre..

3.  Kattintson a **Szolgáltatáskapcsolódási pont** lapra.

4.  Jelölje be a **Szolgáltatáskapcsolódási pont módosítása** jelölőnégyzetet.

5.  Válassza a **Szolgáltatáskapcsolódási pont beállítása a jelenlegi tanúsítási fürtre** lehetőséget, majd kattintson az **OK** gombra..

### Az ügyféloldali szolgáltatásészlelés engedélyezése a Windows beállításjegyzékkel
Az SCP használatának alternatívájaként, illetve létező SCP hiányában az ügyfélszámítógép beállításjegyzékét is beállíthatja úgy, hogy az RMS-ügyfél megtalálja a saját AD RMS-kiszolgálóját.

#### Az ügyféloldali AD RMS-szolgáltatásészlelés engedélyezése a Windows beállításjegyzékben

1.  Nyissa meg a Windows beállításszerkesztőjét a Regedit.exe paranccsal.

    -   Az ügyfélszámítógépen írja be a Futtatás ablakba a **regedit** kifejezést, majd nyomja le az Enter billentyűt a Beállításszerkesztő megnyitásához.

2.  A Beállításszerkesztőben keresse meg a következőt: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC**.

    > [!IMPORTANT]
    > Ha 32 bites alkalmazást futtat egy 64 bites számítógépen, az elérési út a következő lesz: 
    > **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\MSIPC**

3.  A ServiceLocation alkulcs létrehozásához kattintson a jobb gombbal az **MSIPC** elemre, vigye a mutatót az **Új** elemre, kattintson a **Kulcs** lehetőségre, majd írja be a **ServiceLocation** kifejezést..

4.  Az EnterpriseCertification alkulcs létrehozásához kattintson a jobb gombbal a **ServiceLocaton** elemre, vigye a mutatót az **Új** elemre, kattintson a **Kulcs** lehetőségre, majd írja be az **EnterpriseCertification** kifejezést..

5.  A vállalati tanúsítvány URL-címének beállításához kattintson duplán az **(Alapértelmezett)** értékre az **EnterpriseCertification** alkulcs alatt, majd amikor megjelenik a **Karakterlánc szerkesztése** párbeszédpanel, az **Érték** mezőbe írja be a következőt: <http or https>://*AD RMS_fürt_neve*/_wmcs/Certification, majd kattintson az **OK** gombra..

6.  Az EnterprisePublishing alkulcs létrehozásához kattintson a jobb gombbal a **ServiceLocaton** elemre, vigye a mutatót az **Új** elemre, kattintson a **Kulcs** lehetőségre, majd írja be az EnterprsePublishing kifejezést.

7.  A vállalati közzététel URL-címének beállításához kattintson duplán az **(Alapértelmezett)** értékre az **EnterprisePublishing** alkulcs alatt, majd amikor megjelenik a **Karakterlánc szerkesztése** párbeszédablak, az **Érték** mezőbe írja be a következőt: <http or https>://*AD RMS_fürt_neve*/_wmcs/Licensing, majd kattintson az **OK** gombra..

8.  Zárja be a Beállításszerkesztőt.

Ha az RMS-ügyfél nem talál SCP-t az Active Directory lekérdezésével, és az a beállításjegyzékben sincs megadva, akkor az AD RMS felé irányuló szolgáltatásészlelési hívások meghiúsulnak.

### Licenckiszolgálói forgalom átirányítása
Bizonyos esetekben a szolgáltatás észlelése alatt szükség lehet a forgalom átirányítására, mint például két szervezet egyesítésekor, amikor az egyik szervezet régi licenckiszolgálóját kivonják a forgalomból, és az ügyfeleket egy új licenckiszolgálóra kell átirányítani. Vagy áttelepítést kell végezni az AD RMS-ről az Azure RMS-re. A licencelési átirányítás engedélyezéséhez kövesse a következő eljárást.

#### Az RMS-licencátirányítás engedélyezése a Windows beállításjegyzékben

1.  Nyissa meg a Windows beállításszerkesztőjét a Regedit.exe paranccsal.

    -   Az ügyfélszámítógépen a Futtatás ablakba írja be a **regedit** kifejezést, majd nyomja le az Enter billentyűt a Beállításszerkesztő megnyitásához.

2.  A Beállításszerkesztőben keresse meg az alábbiak egyikét:

    -   Egy x64-platformon futó 64 bites Office esetén: HKLM\SOFTWARE\Microsoft\MSIPC\Servicelocation

    -   Egy x64-platformon futó 32 bites Office esetén: HKLM\SOFTWARE\Wow6432Node\Microsoft\MSIPC\Servicelocation

3.  Hozzon létre egy LicensingRedirection alkulcsot. Ehhez kattintson a jobb gombbal a **ServiceLocaton** elemre, vigye a mutatót az **Új** elemre, kattintson a **Kulcs** lehetőségre, majd írja be a **LicensingRedirection** kifejezést..

4.  A licencátirányítás beállításához kattintson a jobb gombbal a **LicensingRedirection** alkulcsra, vigye a mutatót az **Új** elemre, majd válassza a **Karakterlánc** lehetőséget.  A **Név** mezőben adja meg az előző kiszolgálólicencelési URL-címet, az **Érték** mezőben pedig az új kiszolgálólicencelési URL-címet.

    Például ahhoz, hogy a Contoso.com kiszolgálójáról átirányítsa a licencelést a Fabrikam.com kiszolgálójára, a következő értékeket kellene megadnia:

    **Név:** https://contoso.com/_wmcs/licensing

    **Érték:** https://fabrikam.com/_wmcs/licensing

    > [!NOTE]
    > Ha a régi licencelési kiszolgáló intranetes és extranetes URL-címekkel is rendelkezik, akkor a LicensingRedirection kulcsnál mindkét URL-címhez új név-érték megfeleltetést kell beállítani.

5.  Ismételje meg az előző lépést az összes átirányítani kívánt kiszolgálónál.

6.  Zárja be a Beállításszerkesztőt.



<!--HONumber=May16_HO1-->


