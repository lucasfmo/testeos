---
title: "A bérlőkulcs létrehozása és átvitele – az interneten keresztül | Azure RMS"
description: 
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 1bff9b06-8c5a-4b1d-9962-6668219210e6
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 67129d6cdac124947fc07aa4d42523686227752e
ms.openlocfilehash: 7ec87b63b31d0b41c93dab7998df63e208308811


---


# Generate and transfer your tenant key – over the Internet (A bérlőkulcs létrehozása és átvitele – az interneten keresztül)

*A következőkre vonatkozik: Azure Rights Management, Office 365*

Ha úgy döntött, hogy [Ön szeretné felügyelni a saját bérlőkulcsát](plan-implement-tenant-key.md#choose-your-tenant-key-topology-managed-by-microsoft-the-default-or-managed-by-you-byok) és azt az interneten keresztül szeretné továbbítani ahelyett, hogy fel kelljen keresnie egy Microsoft-létesítményt a személyes átadáshoz, kövesse a következő eljárásokat:


## Az internetre kapcsolódó munkaállomás előkészítése
Az internetre kapcsolódó munkaállomás előkészítéséhez végezze el a következő 3 lépést:

-   [1. lépés: Az Azure Rights Managementhez készült Windows PowerShell telepítése](#step-1-install-windows-powershell-for-azure-rights-management)

-   [2. lépés: Az Azure Active Directory-bérlőazonosító beszerzése](#step-2-get-your-azure-active-directory-tenant-id)

-   [3. lépés: A BYOK eszközkészlet letöltése](#step-3-download-the-byok-toolset)

### 1. lépés: Az Azure Rights Managementhez készült Windows PowerShell telepítése
Az internetre kapcsolódó munkaállomáson töltse le és telepítse az Azure Rights Managementhez készült Windows PowerShell-modult.

> [!NOTE]
> Ha a Windows PowerShell-modult már korábban letöltötte, a következő parancs futtatásával ellenőrizze, hogy a verziószáma legalább 2.1.0.0-e: `(Get-Module aadrm -ListAvailable).Version`

A telepítési utasításokat [Az Azure Rights Managementhez készült Windows PowerShell telepítése](../deploy-use/install-powershell.md) című cikk tartalmazza.

### 2. lépés: Az Azure Active Directory-bérlőazonosító beszerzése
Indítsa el a Windows PowerShellt a **Futtatás rendszergazdaként** lehetőséggel, majd futtassa a következő parancsokat:

-   A [Connect-AadrmService](http://msdn.microsoft.com/library/windowsazure/dn629415.aspx) parancsmagot használva csatlakozzon az Azure RMS szolgáltatáshoz:

    ```
    Connect-AadrmService
    ```
    A kérésre adja meg a [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] bérlői rendszergazdai hitelesítő adatait (jellemzően egy olyan fiókot fog használni, amely globális rendszergazda az Azure Active Directoryben vagy az Office 365-ben).

-   A [Get-AadrmConfiguration](http://msdn.microsoft.com/library/windowsazure/dn629410.aspx) parancsmag használatával jelenítse meg a bérlője konfigurációját:

    ```
    Get-AadrmConfiguration
    ```
    A kimenetből mentse a GUID azonosítót az első sorból (BPOSId). Ez az Ön Azure Active Directory-bérlőazonosítója, amelyre később, a bérlőkulcs feltöltésének előkészítésekor szükség lesz.

-   A [Disconnect-AadrmService](http://msdn.microsoft.com/library/windowsazure/dn629416.aspx) parancsmaggal bontsa a kapcsolatot az Azure RMS szolgáltatással, amíg készen nem áll a kulcs feltöltésére:

    ```
    Disconnect-AadrmService
    ```

Ne zárja be a Windows PowerShell ablakát.

### 3. lépés: A BYOK eszközkészlet letöltése
Nyissa meg a Microsoft letöltőközpontot, és töltse le a régiójának megfelelő [BYOK eszközkészletet](http://go.microsoft.com/fwlink/?LinkId=335781):

|Régió|Csomag neve|
|----------|----------------|
|Észak-Amerika|AzureRMS-BYOK-tools-UnitedStates.zip|
|Európa|AzureRMS-BYOK-tools-Europe.zip|
|Ázsia|AzureRMS-BYOK-tools-AsiaPacific.zip|
Az eszközkészlet a következőket tartalmazza:

-   Egy kulcscserekulcs- (KEK-) csomag, amelynek a neve **BYOK-KEK-pkg-**-vel kezdődik.

-   Egy biztonságivilág-csomag, amelynek a neve **BYOK-SecurityWorld-pkg-**-vel kezdődik.

-   Egy **verifykeypackage.py** nevű Python-parancsfájl.

-   Egy parancssori végrehajtható fájl (**KeyTransferRemote.exe**), egy metaadatfájl (**KeyTransferRemote.exe.config**) és kapcsolódó DLL-fájlok.

-   Egy Visual C++ terjeszthető csomag (**vcredist_x64.exe**).

Másolja a csomagot egy USB-meghajtóra vagy más hordozható tárolóeszközre.

## Prepare your disconnected workstation (A kapcsolat nélküli munkaállomás előkészítése)
A kapcsolat nélküli (sem az internethez, sem a belső hálózathoz nem kapcsolódó) munkaállomás előkészítéséhez végezze el a következő 2 lépést:

-   [1. lépés: A kapcsolat nélküli munkaállomás előkészítése a Thales HSM-mel](#step-1-prepare-the-disconnected-workstation-with-thales-hsm)

-   [2. lépés: A BYOK eszközkészlet telepítése a kapcsolat nélküli munkaállomáson](#step-2-install-the-byok-toolset-on-the-disconnected-workstation)

### 1. lépés: A kapcsolat nélküli munkaállomás előkészítése a Thales HSM-mel
Telepítse a kapcsolat nélküli munkaállomáson az nCipher (Thales) támogatószoftvert egy Windows-számítógépen, majd csatoljon a számítógéphez egy Thales HSM-et.

Győződjön meg róla, hogy a Thales-eszközök az elérési útján találhatók **(%nfast_home%\bin** and **%nfast_home%\python\bin**). Adja meg például a következőt:

```
set PATH=%PATH%;”%nfast_home%\bin”;”%nfast_home%\python\bin”
```
További információkért tekintse át a Thales HSM-hez mellékelt felhasználói útmutatót, vagy keresse fel a Thales webhelyén az Azure RMS-ekkel kapcsolatos oldalt a következő címen: [http://www.thales-esecurity.com/msrms/cloud](http://www.thales-esecurity.com/msrms/cloud).

### 2. lépés: A BYOK eszközkészlet telepítése a kapcsolat nélküli munkaállomáson
Másolja át a BYOK eszközkészletcsomagot az USB-meghajtóról vagy egyéb hordozható tárolóeszközről, majd tegye a következőket:

1.  Csomagolja ki a letöltött csomagban található fájlokat egy tetszőleges mappába.

2.  Ebből a könyvtárból futtassa a vcredist_x64.exe fájlt.

3.  Kövesse az útmutatást a Visual Studio 2012 szoftverhez készült Visual C++ futtatókörnyezeti összetevők telepítéséhez.

## A bérlőkulcs létrehozása
A kapcsolat nélküli munkaállomáson kövesse a következő 3 lépést a saját bérlőkulcsa létrehozásához:

-   [1. lépés: Biztonsági világ létrehozása](#step-1-create-a-security-world)

-   [2. lépés: A letöltött csomag ellenőrzése](#step-2-validate-the-downloaded-package)

-   [3. lépés: Új kulcs létrehozása](#step-3-create-a-new-key)

### 1. lépés: Biztonsági világ létrehozása
Indítson el egy parancssort, és futtassa a Thales új világot létrehozó programját.

```
new-world.exe --initialize --cipher-suite=DLf1024s160mRijndael --module=1 --acs-quorum=2/3
```
Ez a program létrehoz egy **biztonságivilág**-fájlt az %NFAST_KMDATA%\local\world címen, amely a C:\ProgramData\nCipher\Key Management Data\local mappának felel meg. A kvórumhoz különböző értékeket is használhat, de a mi példánkban három üres kártyát és mindegyikhez egy PIN-kódot kell megadnia. Ezután bármelyik két kártyának rendszergazdai hozzáférésre lesz szüksége a biztonsági világhoz (a megadott kvórum alapján).  Ezek a kártyák lesznek az új biztonsági világ **rendszergazdai kártyakészlete**. Ezen a ponton mindegyik ACS-kártyához megadhat egy jelszót vagy PIN-kódot, vagy megadhatja őket később egy paranccsal is.

> [!TIP]
> A HSM aktuális konfigurációs állapotát az `nkminfo` paranccsal ellenőrizheti.

Ezután tegye a következőket:

1.  Telepítse a Thales CNG-szolgáltatót a Thales dokumentációjában leírt módon, majd konfigurálja azt az új biztonsági világ használatára.

2.  Készítsen biztonsági másolatot a világfájlról az **%nfast_kmdata%\local** címre. Helyezze biztonságba és biztosítson védelmet a világfájl, valamint a rendszergazdai kártyák és PIN-kódjaik számára, és gondoskodjon róla, hogy senki ne férhessen hozzá egynél több kártyához.

### 2. lépés: A letöltött csomag ellenőrzése
Ezen lépés végrehajtása nem kötelező, de ajánlott a következők ellenőrzéséhez:

-   Az eszközkészletben található kulcscserekulcs egy eredeti Thales HSM-en lett létrehozva.

-   Az Azure RMS biztonsági világának az eszközkészletben található kivonata egy eredeti Thales HSM-en lett létrehozva.

-   A kulcscserekulcs nem exportálható.

> [!NOTE]
> A letöltött csomag ellenőrzéséhez a HSM-nek csatlakoztatva és bekapcsolva kell lennie, és rendelkeznie kell egy biztonsági világgal (például azzal, amelyet Ön épp most hozott létre).

#### A letöltött csomag ellenőrzése

1.  Futtassa a verifykeypackage.py parancsfájlt az alábbiak egyikének beírásával, az Ön régiójától függően:

    -   Észak-Amerika esetében:

        ```
        python verifykeypackage.py -k BYOK-KEK-pkg-NA-1 -w BYOK-SecurityWorld-pkg-NA-1
        ```

    -   Európa esetében:

        ```
        python verifykeypackage.py -k BYOK-KEK-pkg-EU-1 -w BYOK-SecurityWorld-pkg-EU-1
        ```

    -   Ázsia esetében:

        ```
        python verifykeypackage.py -k BYOK-KEK-pkg-AP-1 -w BYOK-SecurityWorld-pkg-AP-1
        ```

    > [!TIP]
    > A Thales szoftver tartalmaz egy Python-fordítót az %NFAST_HOME%\python\bin címen

2.  Győződjön meg róla, hogy a következő, az ellenőrzés sikerességét jelző eredményt látja: **Result:  SUCCESS**

A parancsfájl ellenőrzi az aláírói láncot egészen a Thales-gyökérkulcsig. Ennek a gyökérkulcsnak a kivonata be van ágyazva a parancsfájlba, az értékének pedig a következőnek kell lennie: **59178a47 de508c3f 291277ee 184f46c4 f1d9c639**. Ezt az értéket külön, a [Thales webhelyére](http://www.thalesesec.com/) ellátogatva is ellenőrizheti.

Most már készen áll arra, hogy létrehozzon egy új kulcsot, amely az Ön RMS-bérlőkulcsa lesz.

### 3. lépés: Új kulcs létrehozása
Hozzon létre egy CNG-kulcsot a Thales **generatekey** és **cngimport** programjai használatával.

A kulcs létrehozásához futtassa a következő parancsot:

```
generatekey --generate simple type=RSA size=2048 protect=module ident=contosokey plainname=contosokey nvram=no pubexp=
```
A parancs futtatásakor használja a következő utasításokat:

-   A **protect** paramétert a **module** értékre kell állítani, ahogyan az ábrán látható. Ez egy modul által védett kulcsot hoz létre. A BYOK eszközkészlet nem támogatja az OCS által védett kulcsokat.

-   A kulcs méretét illetően 2048 bit javasolt, de az AD RMS-ről Azure RMS-re áttérő ügyfelek számára az 1024 bites RSA-kulcsok is támogatottak.

-   Cserélje le a *contosokey* értéket az **ident** és a **plainname** esetében bármilyen tetszőleges karakterláncra. Az adminisztratív terhek és a hibalehetőségek minimalizálása érdekében javasoljuk, hogy mindkettőhöz azonos értéket használjon, amely csupa kisbetűs karaktert tartalmaz.

-   A példában a pubexp üresen maradt (alapértelmezett érték), de megadhat specifikus értékeket is. További információt a Thales dokumentációjában talál.

Ezután futtassa a következő parancsot a kulcs importálásához a CNG-be:

```
cngimport --import -M --key=contosokey --appname=simple contosokey
```
A parancs futtatásakor használja a következő utasításokat:

-   Cserélje le a *contosokey* értéket ugyanarra az értékre, amelyet az [1. lépés: Biztonsági világ létrehozása](#step-1-create-a-security-world) lépésnél adott meg *A bérlőkulcs létrehozása* szakaszban.

-   Használja az **-M** kapcsolót, hogy a kulcs megfeleljen ennek a forgatókönyvnek. Enélkül a létrejött kulcs egy felhasználóspecifikus kulcs lesz a jelenlegi felhasználó részére.

-   Az **appname** paraméter a kulcsfájlban jelentett alkalmazásnév. Ha követte ezeket az utasításokat az új kulcs létrehozásához, használhatja a parancsban látható simple értéket. Azonban ha egy meglévő, HSM által védett kulcsot telepít át az AD RMS-ről Azure RMS-re való áttérés keretében, adja meg a meglévő nevét ennél a parancsnál és mindazon további parancsoknál, amelyek szintén használják az appname paramétert.

Ez a parancs egy tokenekre bontott kulcsfájlt hoz létre az %NFAST_KMDATA%\local mappában, amelynek a neve a **key_caping`_`** előtaggal kezdődik, amelyet egy SID követ. Például: **key_caping_machine--801c1a878c925fd9df4d62ba001b94701c039e2fb**. Ez a fájl egy titkosított kulcsot tartalmaz.

> [!TIP]
> A kulcsai aktuális konfigurációs állapotát az `nkminfo –k` paranccsal tekintheti meg.

Készítsen erről a tokenekre bontott kulcsfájlról egy biztonsági másolatot egy biztonságos helyre.

> [!IMPORTANT]
> Miután később átvitte a kulcsát az Azure RMS-re, a Microsoft nem tudja ezt a kulcsot visszaexportálni Önnek, ezért rendkívül fontos, hogy biztonsági másolatot készítsen a kulcsáról és a biztonsági világáról. A kulcs biztonsági másolatának elkészítésével kapcsolatos útmutatásért és az ajánlott eljárásokért lépjen kapcsolatba a Thalesszel.

Most már készen áll arra, hogy a bérlőkulcsát átvigye az Azure RMS szolgáltatásba.

## Prepare your tenant key for transfer (A bérlőkulcs előkészítése az átvitelre)
A kapcsolat nélküli munkaállomáson kövesse a következő 4 lépést a bérlőkulcs előkészítéséhez:

-   [1. lépés: Másolat készítése a kulcsról korlátozott engedélyekkel](#step-1-create-a-copy-of-your-key-with-reduced-permissions)

-   [2. lépés: A kulcs új másolatának vizsgálata](#step-2-inspect-the-new-copy-of-the-key)

-   [3. lépés: A kulcs titkosítása a Microsoft kulcscserekulcsával](#step-3-encrypt-your-key-by-using-microsoft-s-key-exchange-key)

-   [4. lépés: A kulcsátviteli csomag másolása az internetre kapcsolódó munkaállomásra](#step-4-copy-your-key-transfer-package-to-the-internet-connected-workstation)

### 1. lépés: Másolat készítése a kulcsról korlátozott engedélyekkel
A bérlőkulccsal kapcsolatos engedélyek korlátozásához tegye a következőket:

-   A régiójától függően egy parancssorból futtassa az alábbiak egyikét:

    -   Észak-Amerika esetében:

        ```
        KeyTransferRemote.exe -ModifyAcls -KeyAppName simple -KeyIdentifier contosokey -ExchangeKeyPackage BYOK-KEK-pkg-NA-1 -NewSecurityWorldPackage BYOK-SecurityWorld-pkg-NA-1
        ```

    -   Európa esetében:

        ```
        KeyTransferRemote.exe -ModifyAcls -KeyAppName simple -KeyIdentifier contosokey -ExchangeKeyPackage BYOK-KEK-pkg-EU-1 -NewSecurityWorldPackage BYOK-SecurityWorld-pkg-EU-1
        ```

    -   Ázsia esetében:

        ```
        KeyTransferRemote.exe -ModifyAcls -KeyAppName simple -KeyIdentifier contosokey -ExchangeKeyPackage BYOK-KEK-pkg-AP-1 -NewSecurityWorldPackage BYOK-SecurityWorld-pkg-AP-1
        ```

A parancs futtatásakor cserélje le a *contosokey* értéket ugyanarra az értékre, amelyet az [1. lépés: Biztonsági világ létrehozása](#step-1-create-a-security-world) lépésnél adott meg *A bérlőkulcs létrehozása* című szakaszban.

A rendszer arra fogja kérni, hogy csatlakoztassa a biztonsági világhoz tartozó ACS-kártyáit, és adja meg a hozzájuk tartozó jelszót vagy PIN-kódot, ha beállított ilyet.

A parancs végrehajtása után a **Result: SUCCESS** eredmény jelenik meg, és a bérlőkulcs korlátozott engedélyekkel rendelkező másolata a key_xferacId_*&lt;contosokey&gt;* nevű fájlban található.

### 2. lépés: A kulcs új másolatának vizsgálata
Opcionálisan futtathatja a Thales segédprogramokat az új bérlőkulcs minimális engedélyeinek megerősítéséhez:

-   aclprint.py:

    ```
    "%nfast_home%\bin\preload.exe" -m 1 -A xferacld -K contosokey "%nfast_home%\python\bin\python" "%nfast_home%\python\examples\aclprint.py"
    ```

-   kmfile-dump.exe:

    ```
    "%nfast_home%\bin\kmfile-dump.exe" "%NFAST_KMDATA%\local\key_xferacld_contosokey"
    ```

A parancs futtatásakor cserélje le a *contosokey* értéket ugyanarra az értékre, amelyet az [1. lépés: Biztonsági világ létrehozása](#step-1-create-a-security-world) lépésnél adott meg *A bérlőkulcs létrehozása* című szakaszban.

### 3. lépés: A kulcs titkosítása a Microsoft kulcscserekulcsával
A régiójától függően futtassa a következő parancsok egyikét:

-   Észak-Amerika esetében:

    ```
    KeyTransferRemote.exe -Package -KeyIdentifier contosokey -ExchangeKeyPackage BYOK-KEK-pkg-NA-1 -NewSecurityWorldPackage BYOK-SecurityWorld-pkg-NA-1 -TenantBposId GUID -KeyFriendlyName ContosoFirstkey
    ```

-   Európa esetében:

    ```
    KeyTransferRemote.exe -Package -KeyIdentifier contosokey -ExchangeKeyPackage BYOK-KEK-pkg-EU-1 -NewSecurityWorldPackage BYOK-SecurityWorld-pkg-EU-1 -TenantBposId GUID -KeyFriendlyName ContosoFirstkey
    ```

-   Ázsia esetében:

    ```
    KeyTransferRemote.exe -Package -KeyIdentifier contosokey -ExchangeKeyPackage BYOK-KEK-pkg-AP-1 -NewSecurityWorldPackage BYOK-SecurityWorld-pkg-AP-1 -TenantBposId GUID -KeyFriendlyName ContosoFirstkey
    ```

A parancs futtatásakor használja a következő utasításokat:

-   Cserélje le a *contosokey* értéket arra az azonosítóra, amelyet a kulcs létrehozásához használt az [1. lépés: Biztonsági világ létrehozása](#step-1-create-a-security-world) lépésben *A bérlőkulcs létrehozása* szakaszban.

-   Cserélje le a *GUID* azonosítót arra az Azure Active Directory-bérlőazonosítóra, amelyet a [2. lépés: Az Azure Active Directory-bérlőazonosító beszerzése](#step-2-get-your-azure-active-directory-tenant-id) lépésben szerzett *Az internetre kapcsolódó munkaállomás előkészítése* című szakaszban.

-   Cserélje le a *ContosoFirstKey* értéket arra a címkére, amelyet a kimeneti fájl neveként kíván használni.

Ez a sikeres befejeződéskor a **Result: SUCCESS** eredményt jeleníti meg, és egy új fájl jön létre a jelenlegi mappában a következő névvel: TransferPackage-*ContosoFirstkey*.byok

### 4. lépés: A kulcsátviteli csomag másolása az internetre kapcsolódó munkaállomásra
Egy USB-meghajtó vagy egyéb hordozható tárolóeszköz használatával másolja az előző lépésből származó kimeneti fájlt (KeyTransferPackage-*ContosoFirstkey*.byok) az internetre kapcsolódó munkaállomásra.

> [!NOTE]
> Tegyen biztonsági intézkedéseket a fájl védelme érdekében, mert az tartalmazza az Ön titkos kulcsát.

## Transfer your tenant key to Azure RMS (A bérlőkulcs átvitele az Azure RMS szolgáltatásba)
Az internetre kapcsolódó munkaállomáson kövesse a következő 3 lépést az új bérlőkulcs az Azure RMS-re való átviteléhez:

-   [1. lépés: Csatlakozás az Azure RMS-hez](#step-1-connect-to-azure-rms)

-   [2. lépés: A kulcscsomag feltöltése](#step-2-upload-the-key-package)

-   [3. lépés: A bérlőkulcsok számba vétele – szükség esetén](#step-3-enumerate-your-tenant-keys-as-needed)

### 1. lépés: Csatlakozás az Azure RMS-hez
Térjen vissza a Windows PowerShell ablakába, majd írja be a következőt:

1.  Csatlakozzon újra az [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] szolgáltatáshoz:

    ```
    Connect-AadrmService
    ```

2.  Használja a [Get-AadrmKeys](http://msdn.microsoft.com/library/windowsazure/dn629420.aspx) parancsmagot a jelenlegi bérlőkulcs-konfigurációja megtekintéséhez:

    ```
    Get-AadrmKeys
    ```

### 2. lépés: A kulcscsomag feltöltése
Használja az [Add-AadrmKeys](http://msdn.microsoft.com/library/windowsazure/dn629418.aspx) parancsmagot a kapcsolat nélküli munkaállomásról átmásolt kulcsátviteli csomag feltöltéséhez:

```
Add-AadrmKey –KeyFile <PathToPackageFile> -Verbose
```
> [!WARNING]
> E művelet végrehajtását meg kell erősítenie. Fontos, hogy tisztában legyen vele: ez a művelet nem vonható vissza. Ha feltölt egy bérlőkulcsot, az automatikusan az Ön szervezetének elsődleges bérlőkulcsa lesz, és a felhasználók ezt a kulcsot fogják használni a dokumentumok és fájlok védelméhez.

Ha a feltöltés sikeres volt, a következő üzenetet látja majd: **The Rights management service successfully added the key** (A tartalomvédelmi szolgáltatás sikeresen hozzáadta a kulcsot).

Ez a módosítás csak némi késéssel propagálódik az összes [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)]-adatközpontba.

### 3. lépés: A bérlőkulcsok számba vétele – szükség esetén
Használja ismét a Get-AadrmKeys parancsmagot a bérlőkulcsa változásainak megtekintésére, illetve ha a bérlőkulcsai listáját szeretné megtekinteni. A bérlőkulcsok között megjelenik a kezdeti, a Microsoft által létrehozott bérlőkulcs, és minden egyéb később hozzáadott bérlőkulcs:

```
Get-AadrmKeys
```
Az **Active** (Aktív) állapotúként megjelölt bérlőkulcs az, amelyet az Ön szervezete jelenleg használ a dokumentumok és fájlok védelmére.

Ezennel befejezte a saját kulcs használatának interneten keresztüli megvalósításához szükséges összes lépést, és folytathatja a bérlőkulcs tervezésének és megvalósításának következő lépéseivel.


> [!div class="button"]
[További lépések >>](plan-implement-tenant-key.md#next-steps)





<!--HONumber=Jul16_HO3-->


