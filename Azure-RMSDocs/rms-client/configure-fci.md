---
title: "RMS-védelem és Windows Server fájlbesorolási infrastruktúra (FCI) | Azure RMS"
description: "A cikk utasításokat és egy parancsfájlt tartalmaz a Rights Management (RMS)-ügyfél RMS Protection eszközzel való használatához, amellyel konfigurálható a Fájlkiszolgálói erőforrás-kezelő és a fájlbesorolási infrastruktúra (FCI)."
author: cabailey
manager: mbaldwin
ms.date: 06/14/2016
ms.topic: article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 9aa693db-9727-4284-9f64-867681e114c9
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 26b043f1f9e7a1e0cd00c2f31c28f7d6685f0232
ms.openlocfilehash: 431eb994070391a78b0b8e34b1afb668f0981f0f


---

# RMS-védelem és Windows Server fájlbesorolási infrastruktúra (FCI)

>*A következőkre vonatkozik: Azure Rights Management, Windows Server 2012, Windows Server 2012 R2*

A cikk utasításokat és egy parancsfájlt tartalmaz a Rights Management (RMS)-ügyfél RMS Protection eszközzel való használatához, amellyel konfigurálható a Fájlkiszolgálói erőforrás-kezelő és a fájlbesorolási infrastruktúra (FCI).

A megoldás lehetővé teszi egy Windows Server rendszert futtató fájlkiszolgálón lévő mappában található összes fájl, illetve a megadott feltételnek megfelelő fájlok automatikus védelmét. Például olyan fájlokét, amelyek besorolásuk szerint bizalmas információt tartalmaznak. A megoldás az Azure Rights Management (Azure RMS) segítségével védi a fájlokat, ezért ennek a technológiának telepítve kell lennie a szervezetén belül.

> [!NOTE]
> Bár az Azure RMS tartalmaz egy [összekötőt](../deploy-use/deploy-rms-connector.md), amely támogatja a fájlbesorolási infrastruktúrát, a megoldás csak a natív védelmet támogatja – pl. Office-fájlokét.
> 
> A besorolási infrastruktúrával rendelkező összes fájltípus támogatásához a Windows PowerShell **RMS Protection** modulját kell használnia, ahogy az a cikkből is kiderül. Az RMS Protection parancsmagok az RMS-megosztóalkalmazáshoz hasonlóan az általános és a natív védelmet is támogatják, amely azt jelenti, hogy minden fájl védelme biztosítható. További információt a [Rights Management sharing application administrator guide](sharing-app-admin-guide.md) (Rendszergazdai útmutató a Rights Management megosztóalkalmazáshoz) [Levels of protection – native and generic](sharing-app-admin-guide-technical.md#levels-of-protection-native-and-generic) (Védelmi szintek – natív és általános) című szakaszában találhat.

Az alábbi utasítások a Windows Server 2012 R2 vagy a Windows Server 2012 rendszerekre vonatkoznak. Ha a Windows egyéb támogatott verzióit futtatja, előfordulhat, hogy az Ön operációs rendszerének verziója és a jelen cikkben leírt verzió közötti különbségek miatt át kell ültetnie néhány lépést.

## Az Azure RMS védelem és Windows Server fájlbesorolási infrastruktúra (FCI) előfeltételei
Előfeltételek az utasítások elvégzéséhez:

-   Minden egyes fájlkiszolgálón, amelyen a File Resource Manager (Fájlerőforrás-kezelő) eszközt a fájlbesorolási infrastruktúrával fogja futtatni, az alábbiaknak kell teljesülnie:

    -   A Fájlszolgáltatások egyik szerepkör-szolgáltatásaként telepítette a Fájlerőforrás-kezelőt.

    -   Azonosított egy helyi mappát, amely a Rights Management használatával védeni kívánt fájlokat tartalmazza. Például: C:\FileShare.

    -   Telepítette az RMS Protection eszközt, az eszközre és az Azure RMS-re vonatkozó előfeltételekkel együtt (pl. az RMS-ügyfél, illetve az egyszerű szolgáltatás fiókja). További információ: [RMS Protection parancsmagok](https://msdn.microsoft.com/library/azure/mt433195.aspx).

    -   Ha módosítani szeretné egy megadott fájlnév-kiterjesztés RMS-védelmének (általános vagy natív) alapértelmezett szintjét, akkor szerkesztette a beállításjegyzéket a [File API configuration](https://msdn.microsoft.com/library/dn197834%28v=vs.85%29.aspx) (Fájl API konfiguráció) oldalon leírtak szerint.

    -   Internetkapcsolattal rendelkezik, és ha szükséges, a proxykiszolgáló konfigurálva van. Példa: `netsh winhttp import proxy source=ie`

-   Konfigurálta az Azure Rights Management telepítésének további előfeltételét az [about_RMSProtection_AzureRMS](https://msdn.microsoft.com/library/mt433202.aspx) szakaszban leírtak szerint. Pontosabban a következő értékeket tudja kapcsolni az Azure RMS-hez egy egyszerű szolgáltatás használatával:

    -   BposTenantId

    -   AppPrincipalId

    -   Szimmetrikus kulcs

-   Szinkronizálta a helyszíni Active Directory felhasználói fiókokat az Azure Active Directory vagy az Office 365 szolgáltatással, az e-mail címeket is beleértve. Ez minden olyan felhasználó esetében kötelező, akiknek valószínűleg hozzá kell majd férniük az FCI vagy az Azure RMS által védett fájlokhoz. Ha kihagyja ezt a lépést (pl. egy tesztkörnyezetben), akkor előfordulhat, hogy a felhasználók nem tudják elérni a fájlokat. Ha további információra van szüksége a fiók konfigurálásával kapcsolatban, tekintse meg a következő témakört: [Az Azure Rights Management előkészítése](../plan-design/prepare.md).

-   Azonosította a használni kívánt Rights Management-sablont, amely biztosítja a fájlok védelmét. A [Get-RMSTemplate](https://msdn.microsoft.com/library/azure/mt433197.aspx) használatával győződjön meg róla, hogy ismeri a sablon azonosítóját.

## A Fájlkiszolgálói erőforrás-kezelő FCI az Azure RMS védelmi szolgáltatáshoz történő konfigurálásának utasításai
A mappában lévő összes fájl automatikus védelméhez kövesse ezeket az utasításokat. Egyéni feladatként használjon Windows PowerShell parancsfájlt. Végezze el a következő eljárásokat az alábbi sorrendben:

1.  Mentse a Windows PowerShell-parancsfájlt

2.  Hozzon létre egy besorolási tulajdonságot a Rights Management (RMS) részére

3.  Hozzon létre egy besorolási szabályt (Besorolás RMS-hez)

4.  Konfigurálja a besorolási ütemezést

5.  Hozzon létre egy fájlkezelési feladatot (Fájlok védelme RMS használatával)

6.  Tesztelje a konfigurációt a szabály és a feladat manuális futtatásával

Az utasítások végrehajtása után a kijelölt mappa összes fájlja az RMS egyéni tulajdonság besorolást kapja, és a Rights Management védelme alá kerül. Ha egy olyan összetettebb konfigurációt szeretne, amely bizonyos fájloknak szelektív védelmet biztosít, másoknak pedig nem, akkor létrehozhat vagy használhat egy eltérő besorolási tulajdonságot és szabályt is, amely csak a megadott fájlokat védő fájlkezelési feladattal rendelkezik.

### Mentse a Windows PowerShell-parancsfájlt

1.  Másolja az Azure RMS védelemhez használt [Windows PowerShell-parancsfájl](fci-script.md) tartalmát a Fájlkiszolgálói erőforrás-kezelővel. Illessze be a parancsfájl tartalmát, és adja az **RMS-Protect-FCI.ps1** nevet a fájlnak a számítógépén.

2.  Nézze át a parancsfájlt, és hajtsa végre a következő módosításokat:

    -   Keresse meg az alábbi karakterláncot, és cserélje le a saját AppPrincipalId azonosítójára, amelyet a [Set-RMSServerAuthentication](https://msdn.microsoft.com/library/mt433199.aspx) parancsmaggal használ az Azure RMS-hez való csatlakozáshoz:

        ```
        <enter your AppPrincipalId here>
        ```
        A parancsfájl például így nézhet ki:

        `[Parameter(Mandatory = $false)]`

        `[Parameter(Mandatory = $false)]             [string]$AppPrincipalId = "b5e3f76a-b5c2-4c96-a594-a0807f65bba4",`

    -   Keresse meg az alábbi karakterláncot, és cserélje le a saját szimmetrikus kulcsára, amelyet a [Set-RMSServerAuthentication](https://msdn.microsoft.com/library/mt433199.aspx) parancsmaggal használ az Azure RMS-hez való csatlakozáshoz:

        ```
        <enter your key here>
        ```
        A parancsfájl például így nézhet ki:

        `[Parameter(Mandatory = $false)]`

        `[string]$SymmetricKey = "zIeMu8zNJ6U377CLtppkhkbl4gjodmYSXUVwAO5ycgA="`

    -   Keresse meg az alábbi karakterláncot, és cserélje le a saját BposTenantId (bérlő azonosító) azonosítójára, amelyet a [Set-RMSServerAuthentication](https://msdn.microsoft.com/library/mt433199.aspx) parancsmaggal használ az Azure RMS-hez való csatlakozáshoz:

        ```
        <enter your BposTenantId here>
        ```
        A parancsfájl például így nézhet ki:

        `[Parameter(Mandatory = $false)]`

        `[string]$BposTenantId = "23976bc6-dcd4-4173-9d96-dad1f48efd42",`

    -   Ha a kiszolgálója a Windows Server 2012 rendszert futtatja, előfordulhat, hogy manuálisan kell betöltenie az RMSProtection modult a parancsfájl elején. Adja hozzá az alábbi parancsot (vagy egy azzal megegyezőt, ha a „Program Files” mappa nem a C: meghajtón található):

        ```
        Import-Module "C:\Program Files\WindowsPowerShell\Modules\RMSProtection\RMSProtection.dll"
        ```

3.  Írja alá a parancsfájlt. Ha nem írja alá a parancsfájlt (biztonságosabb), akkor konfigurálni kell a Windows PowerShellt az azt futtató kiszolgálókon. Futtasson például egy Windows PowerShell-munkamenetet a **Futtatás rendszergazdaként** beállítással, és írja be a következőt: **Set-ExecutionPolicy RemoteSigned**. Ez a konfiguráció azonban minden, ezen a kiszolgálón tárolt, nem aláírt parancsfájl futását engedélyezi (kevésbé biztonságos).

    További információkat a Windows PowerShell-parancsfájlokról a PowerShell dokumentációs könyvtárban talál: [about_Signing](https://technet.microsoft.com/library/hh847874.aspx).

4.  Mentse a fájlokat helyileg az összes olyan fájlkiszolgálón, amely a fájlbesorolási infrastruktúrával fogja futtatni a Fájlerőforrás-kezelőt. Például mentse a fájlt a következő helyre: **C:\RMS-Protection**. Biztosítsa a fájlt NTFS-engedélyek használatával, hogy illetéktelen felhasználók ne módosíthassák a fájlt.

Most már készen áll a Fájlkiszolgálói erőforrás-kezelő konfigurálására.

### Hozzon létre egy besorolási tulajdonságot a Rights Management (RMS) részére

-   Hozzon létre egy új helyi tulajdonságot a File Server Resource Manager (Fájlkiszolgálói erőforrás-kezelő) Classification Management (Besoroláskezelés) területén:

    -   **Név**: Írja be a következőt: **RMS**

    -   **Leírás**:   Írja be a következőt: **Rights Management védelem**

    -   **Tulajdonság típus**: Válassza a következőt: **Igen/Nem**

    -   **Érték**: Válassza a következőt: **Igen**

Most már létrehozható egy besorolási szabály, amely ezt a tulajdonságot használja.

### Hozzon létre egy besorolási szabályt (Besorolás RMS-hez)

-   Új besorolási szabály létrehozása:

    -   Az **Általános** lapon:

        -   **Név**: Írja be a következőt: **Besorolás RMS-hez**

        -   **Engedélyezve**: Tartsa meg az alapértelmezett értéket, vagyis jelölje be a jelölőnégyzetet.

        -   **Leírás**: Írja be a következőt: **A &lt;mappanév&gt; mappában lévő összes fájl besorolása a Rights Managementhez**.

            Cserélje le a *&lt;mappanevet&gt;* a választott mappanévre. Például: **A C:\FileShare mappában lévő összes fájl besorolása a Rights Managementhez**

        -   **Hatókör**: Adja hozzá a kiválasztott mappát. Például: **C:\FileShare**.

            Ne jelölje be a jelölőnégyzeteket.

    -   A **Besorolás** lapon:

    -   **Besorolási mód**: Válassza a **Mappaosztályozó** lehetőséget

    -   **Tulajdonság** neve: Válassza az **RMS** lehetőséget

    -   Tulajdonság **értéke**: Válassza az **Igen** lehetőséget.

Bár manuálisan is futtathat besorolási szabályokat, a folyamatban lévő műveletek esetében érdemes a szabályt inkább ütemezés szerint futtatni, hogy az új fájlok az RMS-tulajdonság szerint legyenek besorolva.

### Konfigurálja a besorolási ütemezést

-   Az **Automatikus besorolás** lapon:

    -   **Rögzített ütemezés engedélyezése**: Jelölje be ezt a jelölőnégyzetet.

    -   Konfigurálja az összes besorolási szabály futtatásának ütemezését, az új szabályt is beleértve, a fájlok RMS-tulajdonság szerinti besorolásához.

    -   **Új fájlok folyamatos besorolásának engedélyezése**: Jelölje be ezt a jelölőnégyzetet az új fájlok besorolásához.

    -   Választható lehetőség: Végezzen el bármilyen egyéb tetszés szerinti módosítást, például a jelentések és értesítések beállításainak konfigurálását.

Ezzel befejezte a besorolás konfigurálását. Készen áll a kezelési feladat konfigurálására a fájlok RMS-védelemmel való ellátásához.

### Hozzon létre egy fájlkezelési feladatot (Fájlok védelme RMS használatával)

-   A **Fájlkezelési feladatok** menüben hozzon létre egy új fájlkezelési feladatot:

    -   Az **Általános** lapon:

        -   **Feladat neve**: Írja be a következőt: **Fájlok védelme az RMS használatával**

        -   Hagyja bejelölve az **Engedélyezés** jelölőnégyzetet.

        -   **Leírás**: Írja be a következőt: **A &lt;mappanév&gt; mappában lévő fájlok védelme a Rights Management és egy sablon révén Windows PowerShell parancsfájl használatával.**

            Cserélje le a *&lt;mappanevet&gt;* a választott mappanévre. Például: **A C:\FileShare mappában lévő fájlok védelme a Rights Management és egy sablon révén Windows PowerShell parancsfájl használatával**

        -   **Hatókör**: Jelölje ki a kiválasztott mappát. Például: **C:\FileShare**.

            Ne jelölje be a jelölőnégyzeteket.

    -   A **Művelet** lapon:

        -   **Típus**: Válassza a következőt: **Egyéni**

        -   **Végrehajtható**: Adja meg az alábbiakat:

            ```
            C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe
            ```
            Ha a Windows nem a C: meghajtón található, akkor módosítsa az elérési utat vagy keresse meg a fájlt.

        -   **Argumentum**: Adja meg az alábbiakat. Az &lt;elérési út&gt; és a &lt;sablon azonosító&gt; helyére a saját értékeit írja be:

            ```
            -Noprofile -Command "<path>\RMS-Protect-FCI.ps1 -File '[Source File Path]' -TemplateID <template GUID> -OwnerMail [Source File Owner Email]"
            ```
            Ha például a C:\RMS-Protection mappába másolta a parancsfájlt, és az előfeltételekben azonosított sablon az e6ee2481-26b9-45e5-b34a-f744eacd53b0, akkor adja meg a következőt:

            `-Noprofile -Command "C:\RMS-Protection\RMS-Protect-FCI.ps1 -File '[Source File Path]' -TemplateID e6ee2481-26b9-45e5-b34a-f744eacd53b0 -OwnerMail [Source File Owner Email]"`

            Ebben a parancsban a **[Forrásfájl elérési útja]** és a **[Forrásfájl tulajdonosának e-mail címe]** egyaránt FCI-specifikus változók, ezért ugyanolyan formában írja be azokat, ahogy a fenti parancsban megjelennek. Az FCI az elsőt a mappában lévő azonosított fájl automatikus megadására, a másodikat pedig az azonosított fájl megnevezett Tulajdonosa e-mail címének automatikus beszerzésére használja. Ez a parancs a mappában lévő összes fájl esetében megismétlődik, amely a jelen példában a C:\FileShare mappában lévő összes olyan fájlt jelenti, amely még az RMS fájlbesorolási tulajdonsággal is rendelkezik.

            > [!NOTE]
            > Az **-OwnerMail [Forrásfájl tulajdonosának e-mail címe]** paraméter és érték biztosítja, hogy a fájl eredeti tulajdonosa legyen a Rights Management tulajdonos a fájl védelemmel való ellátása után is. Ez biztosítja, hogy az eredeti fájltulajdonos minden Rights Management joggal rendelkezzen a saját fájljaihoz. Ha egy tartományi felhasználó hoz létre fájlokat, akkor a rendszer automatikusan lekéri az e-mail címet az Active Directoryból a fájl Tulajdonos tulajdonságában szereplő felhasználói fiók neve alapján. Ehhez a fájlkiszolgálónak ugyanabba a tartományba vagy megbízható tartományba kell tartoznia, mint a felhasználónak.
            > 
            > Lehetőség szerint az eredeti tulajdonosokat rendelje a védett dokumentumokhoz annak biztosítása érdekében, hogy a felhasználók továbbra is teljes hozzáféréssel rendelkezzenek az általuk létrehozott fájlokhoz. Ha viszont a fentiek szerint a [Forrásfájl tulajdonosának e-mail címe] változót használja, de a fájl tulajdonosaként nem tartományi felhasználó van meghatározva (pl. a fájlt helyi fiókkal hozták létre, tehát tulajdonosként SYSTEM jelenik meg), akkor a parancsfájl futtatása sikertelen lesz.
            > 
            > Az olyan fájlokat, amelyeknek nem tartományi felhasználó a tulajdonosa, maga is másolhatja vagy mentheti tartományi felhasználóként, így ezeknek Ön válik tulajdonosává. Amennyiben rendelkezik a megfelelő jogosultságokkal, manuálisan is módosíthatja a tulajdonost.  Ehelyett azt is megteheti, hogy a [Forrásfájl tulajdonosának e-mail címe] változó helyett megad egy adott e-mail címet (például a sajátját vagy az informatikai részleg csoportcímét), ami azt jelenti, hogy a parancsfájl által védett összes fájl ezt az e-mail címet fogja használni az új felhasználó meghatározásához.

    -   **A parancs futtatása a következőként**: Válassza a következőt: **Helyi rendszer**

    -   A **Feltétel** lapon:

        -   **Tulajdonság**: Válassza a következőt: **RMS**

        -   **Operátor**: Válassza a következőt: **Egyenlő**

        -   **Érték**: Válassza a következőt: **Igen**

    -   Az **Ütemezés** lapon:

        -   **Futtatás a következő időpontban**: Konfigurálja a kívánt ütemezést.

            Hagyjon bőséges időt a parancsfájl végrehajtására. Bár a megoldás a mappában lévő összes fájlt védelemmel látja el, a parancsfájl minden alkalommal lefut egyszer az összes fájl esetében. Bár ez hosszabb időt vesz igénybe, mint az összes fájl egyszerre történő védelme, amelyet az RMS Protection eszköz támogat, a fájlonkénti FCI konfiguráció sokkal hatékonyabb. A védett fájlok például különböző tulajdonosokkal rendelkezhetnek (megtartják az eredeti tulajdonost) a [Forrásfájl tulajdonosának e-mail címe] változó használatakor, és ha később úgy módosítaná a konfigurációt, hogy a mappa összes fájlja helyett szelektíven alkalmaz védelmet egyes fájlokra, akkor erre a fájlonkénti műveletre lesz szüksége.

        -   **Folyamatos futtatás új fájlokon**: Jelölje be ezt a jelölőnégyzetet.

### Tesztelje a konfigurációt a szabály és a feladat manuális futtatásával

1.  Futtassa a besorolási szabályt:

    1.  Kattintson a **Besorolási szabályok** &gt; **Besorolás futtatása az összes szabállyal** parancsra

    2.  Kattintson a **Várakozás a besorolás befejezésére** lehetőségre, majd az **OK** gombra.

2.  Várjon, amíg bezáródik a **Besorolás futtatása** párbeszédpanel, majd tekintse meg az eredményeket az automatikusan megjelenő jelentésben. A **Tulajdonságok** mezőben az **1** értéknek és a mappában lévő fájlok számának kell megjelennie. Erősítse meg a Fájlkezelő használatával és a kiválasztott mappában lévő fájlok tulajdonságainak ellenőrzésével. A **Besorolás** lapon a tulajdonságnév **RMS**, az **Érték** pedig **Igen** kell, hogy legyen.

3.  Futtassa a fájlkezelési feladatot:

    1.  Kattintson a **Fájlkezelési feladatok** &gt; **Fájlok védelme az RMS használatával** &gt; **A fájlkezelési feladat futtatása most** lehetőségre

    2.  Kattintson a **Várakozás a feladat befejezésére** lehetőségre, majd az **OK** gombra.

4.  Várjon, amíg bezáródik a **Fájlkezelési feladat futtatása** párbeszédpanel, majd tekintse meg az eredményeket az automatikusan megjelenő jelentésben. A kiválasztott mappában lévő fájlok számának a **Fájlok** mezőben kell megjelennie. Ellenőrizze, hogy a kiválasztott mappában lévő fájlok most már RMS-védelemmel vannak-e ellátva. Ha a kiválasztott mappa például a C:\FileShare, írja be a következőt egy Windows PowerShell munkamenetbe, és ellenőrizze, hogy egy fájl állapota se legyen **Nem védett**:

    ```
    foreach ($file in (Get-ChildItem -Path C:\FileShare -Force | where {!$_.PSIsContainer})) {Get-RMSFileStatus -f $file.PSPath}
    ```
    > [!TIP]
    > Néhány hibaelhárítási tipp:
    > 
    > -   Ha a jelentésben **0** látható a mappában lévő fájlok száma helyett, az arra utal, hogy a parancsfájl nem futott le. Először ellenőrizze magát a parancsfájlt. Ehhez töltse be a parancsfájlt egy Windows PowerShell integrált parancsprogram-kezelési környezetbe (ISE) a tartalmának érvényesítéséhez, majd próbálja meg futtatni, hogy kiderüljön, megjelennek-e hibák. Megadott argumentumok hiányában a parancsfájl megpróbál egy Azure RMS-hez csatlakozni és elvégezni a hitelesítést.
    > 
    >     -   Ha a parancsfájl azt jelenti, hogy nem tudott csatlakozni az Azure RMS-hez, ellenőrizze a parancsfájlban megadott egyszerű szolgáltatás fiókjához megjelenített értékeket.  Az egyszerű szolgáltatás fiókjának létrehozásával kapcsolatos további információk: [about_RMSProtection_AzureRMS](https://msdn.microsoft.com/library/mt433202.aspx).
    >     -   Ha a parancsfájl azt jelenti, hogy sikeresen csatlakozott az Azure RMS-hez, következő lépésként a [Get-RMSTemplate](https://msdn.microsoft.com/library/mt433197.aspx) közvetlenül a kiszolgálón lévő Windows PowerShellből való futtatásával ellenőrizze, hogy képes-e megtalálni a megadott sablont. Eredményként az Ön által megadott sablont kell visszakapnia.
    > -   Ha a parancsfájl önmagában hiba nélkül fut a Windows PowerShell ISE-ben, próbálja meg az alábbiak szerint futtatni egy PowerShell munkamenetből, amelyben megad egy védeni kívánt fájlnevet, de kihagyja az -OwnerEmail paramétert:
    > 
    >     ```
    >     powershell.exe -Noprofile -Command "<path>\RMS-Protect-FCI.ps1 -File '<full path and name of a file>' -TemplateID <template GUID>"
    >     ```
    >     -   Ha a parancsfájl sikeresen fut a Windows PowerShell munkamenetben, ellenőrizze a **Végrehajtható** és az **Argumentum** bejegyzéseket a fájlkezelési feladat műveletében.  Ha megadta az **-OwnerEmail [Forrásfájl tulajdonosának e-mail címe]** paramétert, próbálkozzon az eltávolításával.
    > 
    >         Ha a fájlkezelési feladat sikeresen működik az **-OwnerEmail [Forrásfájl tulajdonosának e-mail címe]** paraméter nélkül, ellenőrizze, hogy a nem védett fájlok tulajdonosaként tartományi felhasználó jelenik-e meg, és nem **SYSTEM**.  Ehhez a fájl tulajdonságainak **Biztonság** lapján kattintson a **Speciális** elemre. A **Tulajdonos** érték közvetlenül a fájl **Név** értéke után jelenik meg. Ellenőrizze azt is, hogy a fájlkiszolgáló megegyező tartományban vagy megbízható tartományban legyen, hogy kikereshesse a felhasználó e-mail címét az Active Directory tartományi szolgáltatásokból.
    > -   Ha a jelentésben megfelelő számú fájl szerepel, de nem védettek, akkor próbálja meg manuális védelemmel ellátni a fájlokat a [Protect-RMSFile](https://msdn.microsoft.com/library/azure/mt433201.aspx) parancsmag használatával. Ellenőrizze, hogy így megjelennek-e hibák.

Ha meggyőződött róla, hogy a feladatok megfelelően futnak, bezárhatja a Fájlerőforrás-kezelőt. Az új fájlok automatikusan védelmemmel lesznek ellátva, ami az ütemezett feladatok futásakor ismét megtörténik. A fájlok ismételt védelmével biztosítható, hogy a sablon esetleges módosításai alkalmazva legyenek a fájlokra.


## Az utasítások módosítása a fájlok szelektív védelme érdekében
Ha az előző utasítások működnek, akkor igen könnyen módosíthatók egy kifinomultabb konfiguráció elérése céljából. Például ugyanazzal a parancsfájllal biztosíthat védelmet a fájloknak, de csak a személyes azonosításra alkalmas adatokat tartalmazó fájlokra vonatkozóan, vagy esetleg kiválaszthat egy szigorúbb jogokat biztosító sablont.

Ehhez használja az egyik beépített besorolási tulajdonságot (pl. **Személyes azonosításra alkalmas adatok**), vagy hozzon létre új saját tulajdonságot. Ezután hozzon létre egy új szabályt, amely ezt a tulajdonságot használja. Például kiválaszthatja a **Tartalombesorolót**, majd a **Magas** értékkel rendelkező **Személyes azonosításra alkalmas adatok** tulajdonságot, és konfigurálhat egy karakterláncot vagy kifejezési mintát, amely azonosítja a tulajdonsághoz (pl. a „**Születési idő**” karakterlánc) konfigurálandó fájlt.

Most már csak annyit kell tennie, hogy létrehoz egy új fájlkezelési feladatot, amely ugyanazt a parancsfájlt használja esetleg egy másik sablonnal, majd konfigurálja az imént konfigurált besorolási tulajdonságra vonatkozó feltételt. Például az előzőleg konfigurált feltétel (**RMS** tulajdonság, **Egyenlő**, **Igen**) helyett válassza a **Személyes azonosításra alkalmas adatok** tulajdonságot, amelyben az **Operátor** értéke **Egyenlő**, az **Érték** pedig **Magas** legyen.




<!--HONumber=Aug16_HO4-->


