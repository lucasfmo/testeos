---
title: "Áttelepítés AD RMS-ről Azure Rights Managementre – 1. fázis | Azure RMS"
description: "Az AD RMS-ről Azure Rights Managementre (Azure RMS) történő áttelepítés 1. szakasza, benne az AD RMS-ről Azure Rights Managementre történő áttelepítés 1-4. lépése."
author: cabailey
manager: mbaldwin
ms.date: 08/25/2016
ms.topic: article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 5a189695-40a6-4b36-afe6-0823c94993ef
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ada00b6f6298e7d359c73eb38dfdac169eacb708
ms.openlocfilehash: 6a4b80ed44f149116d22efb7781503f5b157f369


---

# 1. áttelepítési fázis: Az AD RMS kiszolgálóoldali konfigurációja

>*A következőkre vonatkozik: Active Directory Rights Management Services, Azure Rights Management*

Az alábbi, 1. fázisra vonatkozó információk segítséget nyújtanak az AD RMS-ről az Azure Rights Managementre (Azure RMS) való áttelepítésben. Ezek az eljárások megfelelnek az [Áttelepítés AD RMS-ről Azure Rights Managementre](migrate-from-ad-rms-to-azure-rms.md) 1–4. lépésének.


## 1. lépés: Az Azure RMS kezelésfelügyeleti eszközeinek letöltése
Nyissa meg a Microsoft letöltőközpontot, és töltse le az [Azure Rights Management Administration Tool](https://go.microsoft.com/fwlink/?LinkId=257721) eszközt, amelynek része az Azure RMS felügyeleti modul a Windows PowerShellhez.

Telepítse az eszközt. Az utasítások itt találhatók: [Az Azure Rights Managementhez készült Windows PowerShell telepítése](../deploy-use/install-powershell.md).

> [!NOTE]
> Ha a Windows PowerShell-modult már korábban letöltötte, a következő parancs futtatásával ellenőrizze, hogy a verziószáma legalább 2.5.0.0-e: `(Get-Module aadrm -ListAvailable).Version`

## 2. lépés Konfigurációs adatok exportálása az AD RMS-ből és importálása az AD RMS-be
Ez a lépés is egy kétlépéses folyamat:

1.  Exportálja a konfigurációs adatokat az AD RMS-ből a megbízható közzétételi tartományok (TPD-k) exportálásával egy .xml fájlba. Ez a folyamat minden áttelepítés esetében azonos.

2.  Importálja a konfigurációs adatokat az Azure RMS szolgáltatásba. Ez a lépés többféle folyamattal is végrehajtható attól függően, hogy milyen a jelenlegi AD RMS telepítési konfigurációja és az Azure RMS-bérlőkulcs előnyben részesített topológiája.

### Konfigurációs adatok exportálása az AD RMS-ből

> [!IMPORTANT]
> A folyamat elvégzése előtt győződjön meg arról, hogy az AD RMS-kiszolgálók 2. titkosítási módban futnak, ugyanis ez az Azure RMS egyik követelménye.
> 
> A titkosítási mód ellenőrzése:
> 
> - Windows Server 2012 R2 és Windows 2012 esetében: az AD RMS-fürt tulajdonságai > **Általános** lap. 
> 
> - Az AD RMS minden támogatott verzióján: Az [RMS Analyzer](https://www.microsoft.com/en-us/download/details.aspx?id=46437) és az **AD RMS-rendszergazda** lehetőség segítségével megtekintheti a titkosítási módot **az RMS szolgáltatás adatai** között.
> 
> Győződjön meg arról, hogy a titkosítási mód a **2** értékre van állítva. Ha az érték nincs megfelelően beállítva, kövesse az [AD RMS Cryptographic Modes](https://technet.microsoft.com/library/hh867439(v=ws.10).aspx) (Az AD RMS titkosítási módjai) című témakör útmutatását.


Végezze el a következő folyamatot az összes AD RMS-fürthöz az összes megbízható közzétételi tartományhoz, amely a szervezete által használt védett adatokat tartalmaz. A lépést nem szükséges elvégezni a csak licencelési fürtök esetében.

#### A konfigurációs adatok (megbízható közzétételi tartományok információi) exportálása

1.  Jelentkezzen be az AD RMS-fürtbe AD RMS rendszergazdai engedélyekkel rendelkező felhasználóként.

2.  Az AD RMS felügyeleti konzoljában (**Active Directory Rights Management Services (Active Directory tartalomvédelmi szolgáltatások)**) bontsa ki az AD RMS-fürt nevét, bontsa ki a **Trust Policies (Megbízhatósági házirendek)** elemet, majd kattintson az **Trusted Publishing Domains (Megbízható közzétételi tartományok)** lehetőségre.

3.  Az eredmények ablaktáblájában válassza ki a megbízható közzétételi tartományt, majd a Műveletek ablaktáblában kattintson az **Export Trusted Publishing Domain (Megbízható közzétételi tartomány exportálása)** lehetőségre.

4.  Az **Export Trusted Publishing Domain (Megbízható közzétételi tartomány exportálása)** párbeszédablakban:

    -   Kattintson a **Save As (Mentés másként)** gombra, és mentsen a kiválasztott elérési útra és fájlnévvel. Ügyeljen arra, hogy adja hozzá a **.xml** kiterjesztést a fájlnév végéhez (ezt a program nem egészíti ki automatikusan).

    -   Adjon meg egy erős jelszót, és erősítse meg. Jegyezze meg ezt a jelszót, mert szükség lesz rá, amikor a konfigurációs adatokat importálja az Azure RMS szolgáltatásba.

    -   Ne pipálja be azt a jelölőnégyzetet, amellyel a megbízható tartomány fájlját az RMS 1.0-ás verziójának megfelelő formátumban menti.

Miután exportálta az összes megbízható közzétételi tartományt, megkezdheti az adatok importálását az Azure RMS-be.

### Konfigurációs adatok importálása az Azure RMS szolgáltatásba
Az erre a lépésre vonatkozó pontos eljárások attól függően változnak, hogy milyen a jelenlegi AD RMS telepítési konfigurációja és az Azure RMS-bérlőkulcs előnyben részesített topológiája.

A jelenlegi AD RMS-telepítés a következő konfigurációk egyikét fogja használni a kiszolgálólicenc-tanúsítványhoz (más néven SLC-kulcshoz):

-   Jelszavas védelem az AD RMS adatbázisban. Ez az alapértelmezett beállítás.

-   HSM-es védelem Thales hardveres biztonsági modul (HSM) használatával.

-   HSM-es védelem a Thalestől különböző szállítótól származó hardveres biztonsági modul (HSM) használatával.

-   Jelszavas védelem külső titkosítási szolgáltató használatával.

> [!NOTE]
> További információk a hardveres védelem AD RMS szolgáltatással történő használatáról: [Using AD RMS with Hardware Security Modules (Az AD RMS használata hardveres biztonsági modulokkal)](http://technet.microsoft.com/library/jj651024.aspx).

A két lehetséges Azure RMS-bérlőkulcstopológia a következő: Microsoft által felügyelt bérlőkulcs (**Microsoft által felügyelt**) vagy Ön által, az Azure Key Vaultban felügyelt bérlőkulcs (**ügyfél által felügyelt**). Ha Ön kezeli a saját Azure RMS-bérlőkulcsát, ezt „saját kulcs használata” (BYOK) módnak is hívják. Ehhez Thales hardveres biztonsági modul (HSM) szükséges. További információt a [Planning and implementing your Azure Rights Management tenant key](plan-implement-tenant-key.md) (Az Azure Rights Management-bérlőkulcs tervezése és megvalósítása) című cikkben talál.

> [!IMPORTANT]
> Az Exchange Online jelenleg nem kompatibilis a BYOK használatával az Azure RMS-ben.  Ha BYOK módot szeretne használni az áttelepítés után és az Exchange Online-t is használni kívánja, mindenképpen tájékozódjon arról, hogy ez milyen módon csökkenti az Exchange Online IRM-funkcionalitását. Tekintse át [A BYOK díjszabása és korlátozásai](byok-price-restrictions.md) című szakaszt, amely segítséget nyújt az Ön által végzett áttelepítéshez leginkább megfelelő Azure RMS-bérlőkulcstopológia kiválasztásához.

A következő táblázat segítségével megállapíthatja, melyik eljárást használja az áttelepítéshez. A listában nem szereplő kombinációk nem támogatottak.

|Jelenlegi AD RMS-telepítés|Kiválasztott Azure RMS-bérlőkulcstopológia|Áttelepítési utasítások|
|-----------------------------|----------------------------------------|--------------------------|
|Jelszavas védelem az AD RMS adatbázisban|Microsoft által felügyelt|Tekintse meg a **Szoftveres védelemmel ellátott kulcs áttelepítése szoftveres védelemmel rendelkező kulccsá** eljárást a táblázat után.<br /><br />Ez a legegyszerűbb áttelepítési út. Mindössze annyit igényel, hogy átvigye a konfigurációs adatait az Azure RMS-be.|
|HSM-es védelem Thales nShield hardveres biztonsági modul (HSM) használatával|Felhasználó által felügyelt (BYOK)|Tekintse meg a **HSM által védett kulcs áttelepítése HSM által védett kulccsá** eljárást a táblázat után.<br /><br />Az Azure Key Vault BYOK eszközkészletére, valamint három további lépésre lesz szüksége ahhoz, hogy a helyi HSM-ből az Azure Key Vault HSM-ekbe helyezze a kulcsot, engedélyezze a bérlőkulcs elérését az Azure RMS számára, végül pedig átvigye a konfigurálási adatokat Azure RMS-be.|
|Jelszavas védelem az AD RMS adatbázisban|Felhasználó által felügyelt (BYOK)|Lásd a **Szoftveres védelemmel ellátott kulcs áttelepítése HSM által védett kulccsá** eljárást a táblázat után.<br /><br />Az Azure Vault BYOK eszközkészletére, valamint négy további lépésre lesz szüksége a szoftverkulcs kinyeréséhez és importálásához egy helyszíni HSM-be, a kulcs átviteléhez az helyszíni HSM-ből az Azure RMS HSM-ekbe, a Key Vault adatainak áthelyezéséhez az Azure RMS-be, végül a konfigurációs adatok átviteléhez az Azure RMS-be.|
|HSM-es védelem a Thalestől különböző szállítótól származó hardveres biztonsági modul (HSM) használatával|Felhasználó által felügyelt (BYOK)|Lépjen kapcsolatba az Ön által használt HSM szállítójával, hogy megtudja, hogyan viheti át a kulcsot erről a HSM-ről egy Thales nShield hardveres biztonsági modulra (HSM). Ezután kövesse a **HSM által védett kulcs áttelepítése HSM által védett kulccsá** eljárás útmutatóját a táblázat után.|
|Jelszavas védelem külső titkosítási szolgáltató használatával|Felhasználó által felügyelt (BYOK)|Lépjen kapcsolatba az Ön által használt titkosítási szolgáltató szállítójával, hogy megtudja, hogyan viheti át a kulcsát egy Thales nShield hardveres biztonsági modulra (HSM). Ezután kövesse a **HSM által védett kulcs áttelepítése HSM által védett kulccsá** eljárás útmutatóját a táblázat után.|
Mielőtt megkezdi ezeket az eljárásokat, győződjön meg arról, hogy el tudja érni a korábban, a megbízható közzétételi tartományok exportálásakor létrehozott .xml fájlokat. Ezeket például egy USB-meghajtóra mentheti, amelyet átvisz az AD RMS-kiszolgálóról az internethez kapcsolódó munkaállomásra.

> [!NOTE]
> A fájlok tárolási módjától függetlenül használja az ajánlott biztonsági eljárásokat a védelmükhöz, mert az adatok között található a titkos kulcs is.


A 2. lépés elvégzéséhez válassza ki az áttelepítési útvonalának megfelelő utasításokat: 


- [Szoftveres védelemmel ellátott kulcs áttelepítése szoftveres védelemmel rendelkező kulccsá](migrate-softwarekey-to-softwarekey.md)
- [HSM által védett kulcs áttelepítése HSM által védett kulccsá](migrate-hsmkey-to-hsmkey.md)
- [Szoftveres védelemmel ellátott kulcs áttelepítése HSM által védett kulccsá](migrate-softwarekey-to-hsmkey.md)


## 3. lépés. Az RMS-bérlő aktiválása
Az ebben a lépésben ismertetett utasítások mindegyike megtalálható az [Activating Azure Rights Management](../deploy-use/activate-service.md) (Az Azure Rights Management aktiválása) című cikkben.


> [!TIP]
> Ha rendelkezik Office 365-előfizetéssel, az Azure RMS szolgáltatást az Office 365 felügyeleti központjából vagy a klasszikus Azure-portálon keresztül aktiválhatja. Javasoljuk, hogy a klasszikus Azure-portált használja, mert a következő lépés végrehajtása is ezen a felügyeleti portálon keresztül történik.

**Mi a teendő, ha az Azure RMS-bérlőt már aktiválták?** Ha az Azure RMS szolgáltatást már aktiválták a szervezete számára, előfordulhat, hogy a felhasználók a meglévő AD RMS-kulcsok (és sablonok) helyett már használták tartalomvédelemre az Azure RMS-t automatikusan létrehozott bérlőkulccsal (és az alapértelmezett sablonokkal). Ez a jól felügyelt, intraneten található számítógépek esetében nem valószínű, mert azokat automatikusan konfigurálják az AD RMS-infrastruktúrához. Megtörténhet azonban a munkacsoport-számítógépeken vagy az intranethez csak ritkán kapcsolódó számítógépeken. Sajnos ezeket a számítógépeket nehéz azonosítani, ezért nem javasolt aktiválni a szolgáltatást azelőtt, hogy a konfigurációs adatokat importálja az AD RMS-ből.

Ha az Azure RMS-bérlőt már aktiválták, és azonosítani tudja ezeket a számítógépeket, mindenképp futtassa a számítógépeken a CleanUpRMS_RUN_Elevated.cmd parancsfájlt az 5. lépésben leírtak szerint. A parancsfájl futtatása a felhasználói környezet újrainicializálására kényszeríti a számítógépeket, ezért letöltik a frissített bérlőkulcsot és az importált sablonokat.

Ha az áttelepítés után is használni kívánt egyéni sablonokat hozott létre, azokat is exportálnia és importálnia kell. Ezt az eljárást a következő lépés ismerteti. 

## 4. lépés. Importált sablonok konfigurálása
Mivel az importált sablonok alapértelmezett állapota **archivált**, az állapotot **közzétettre** kell módosítani, ha azt szeretné, hogy a felhasználók használni tudják ezeket a sablonokat az Azure RMS szolgáltatással.

Az AD RMS szolgáltatásból importált sablonok kinézete és viselkedése pont olyan, mint a klasszikus Azure-portálon létrehozottaké. Ha módosítani szeretné az importált sablonok közzétételét, hogy a felhasználók lássák és az alkalmazásokból kiválaszthassák azokat, olvassa el az [Egyéni sablonok konfigurálása az Azure Rights Management szolgáltatáshoz](../deploy-use/configure-custom-templates.md) című témakört.

Az újonnan importált sablonokat közzétételén kívül csak két olyan fontos módosítás van a sablonokkal kapcsolatban, amelyet érdemes lehet végrehajtania az áttelepítés folytatása előtt. Az áttelepítési folyamat egységes felhasználói környezetének biztosítása érdekében ekkor még ne módosítsa az importált sablonokat, és ne tegye közzé az Azure RMS szolgáltatáshoz tartozó két alapértelmezett sablont, illetve ne hozzon létre új sablonokat. Inkább várja meg az áttelepítési folyamat befejezését és az AD RMS-kiszolgálók leszerelését.

Ebben a lépésben az alábbi sablonmódosításokra lehet szükség:

- Ha az áttelepítés előtt létrehozott egyéni sablonokat az Azure RMS-ben, akkor egyedileg kell azokat exportálnia és importálnia.

- Ha az AD RMS-sablonok a **BÁRKI** csoportot használták, egyedileg kell felvennie az azzal egyenértékű csoportot és a jogosultságokat.

## A követendő eljárás, ha egyéni sablonokat hozott létre az áttelepítés előtt

Ha egyéni sablonokat hozott létre az áttelepítés előtt, akár az Azure RMS aktiválását megelőzően, akár azt követően, ezek a sablonok az áttelepítés után nem lesznek elérhetőek a felhasználók számára akkor sem, ha **Közzétéve** értékre voltak beállítva. Az elérhetővé tételükhöz a következőket kell tennie: 

1. Azonosítsa a sablonokat, és jegyezze fel a sablonazonosítójukat a [Get-AadrmTemplate](https://msdn.microsoft.com/library/dn727079.aspx) futtatását követően. 

2. Exportálja a sablonokat az Azure RMS PowerShell parancsmag ([Export-AadrmTemplate](https://msdn.microsoft.com/library/dn727078.aspx)) használatával.

3. Importálja a sablonokat az Azure RMS PowerShell parancsmag ([Import-AadrmTemplate](https://msdn.microsoft.com/library/dn727077.aspx)) használatával.

Ezt követően ugyanúgy teheti közzé vagy archiválhatja ezeket a sablonokat, mint az áttelepítés után létrehozott összes többi sablont.


## A követendő eljárás, ha az AD RMS-sablonok a **BÁRKI** csoportot használták

Mivel a rendszer automatikusan eltávolítja a **BÁRKI** csoportot a sablonok Azure RMS-be történő importálásakor, ha az AD RMS-ben lévő sablonok ezt a csoportot használták, az importált sablonokhoz egyedileg kell felvennie az azzal egyenértékű csoportot vagy felhasználókat, valamint ugyanazokat a jogosultságokat. Az egyenértékű csoport neve az Azure RMS esetében: **AllStaff-7184AB3F-CCD1-46F3-8233-3E09E9CF0E66@<bérlő_neve>.onmicrosoft.com**. Ez a csoport például a következőképpen nézheti ki a Contoso esetében: **AllStaff-7184AB3F-CCD1-46F3-8233-3E09E9CF0E66@contoso.onmicrosoft.com**.

Ha nem biztos benne, hogy az AD RMS-sablonjai tartalmazzák a BÁRKI csoportot, az alábbi Windows PowerShell-parancsfájlminta használatával azonosíthatja ezeket a sablonokat. További információk a Windows PowerShell AD RMS szolgáltatással történő használatáról: [Using Windows PowerShell to Administer AD RMS (Az AD RMS felügyelete a Windows PowerShell használatával)](https://technet.microsoft.com/library/ee221079%28v=ws.10%29.aspx).

A szervezete automatikusan létrehozott csoportját úgy tekintheti meg, hogy az egyik alapértelmezett jogosultságmegadási sablont a klasszikus Azure-portálra másolja, majd azonosítja a **FELHASZNÁLÓNEVET** a **JOGOSULTSÁGOK** oldalon. Ugyanakkor a klasszikus portálon nem adhatja hozzá ezt a csoportot manuálisan létrehozott vagy importált sablonhoz. Ehhez a következő Azure RMS PowerShell-beállítások egyikét kell használnia:

-   A [New-AadrmRightsDefinition](https://msdn.microsoft.com/library/azure/dn727080.aspx) PowerShell-parancsmag használatával határozza meg az „AllStaff” csoportot és jogosultságokat jogosultságdefiníciós objektumként, majd futtassa újra a parancsot az olyan további csoportok vagy felhasználók esetében, amelyek már rendelkeznek jogosultságokkal az eredeti sablonban a BÁRKI csoporton felül. Végül adja hozzá mindezen jogosultságdefiníciós objektumokat a sablonokhoz a [Set-AadrmTemplateProperty](https://msdn.microsoft.com/library/azure/dn727076.aspx) parancsmag használatával.

-   Az [Export-AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727078.aspx) parancsmag használatával exportálja a sablont egy .XML fájlba, amelyet szerkesztve hozzáadhatja az „AllStaff” csoportot és jogosultságokat a meglévő csoportokhoz és jogosultságokhoz, majd az [Import-AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727077.aspx) parancsmag használatával importálja vissza a módosítást az Azure RMS szolgáltatásba.

> [!NOTE]
> Az „AllStaff” egyenértékű csoport nem pontosan ugyanaz, mint a BÁRKI csoport az AD RMS-ben. Az „AllStaff” csoport az Azure-bérlőhöz tartozó összes felhasználót, míg a BÁRKI csoport az összes olyan hitelesített felhasználót tartalmazza, amelyek a szervezeten kívül lehetnek.
> 
> Lehetséges, hogy a két csoport közti különbség miatt külső felhasználókat is fel kell vennie az „AllStaff” csoporton felül. A csoportokhoz tartozó külső e-mail-címeket a rendszer jelenleg nem támogatja.


### Windows PowerShell-parancsfájlpélda a BÁRKI csoportot tartalmazó AD RMS-sablonok azonosításához
Ez a szakasz azt a parancsfájlpéldát tartalmazza, amelynek segítségével az előző szakaszban leírtaknak megfelelően azonosíthatja a BÁRKI csoportot tartalmazó AD RMS-sablonokat.

**Jogi nyilatkozat:** Ez a parancsfájlpélda semmilyen standard támogatási program vagy szolgáltatás esetében nem támogatott a Microsoft által. A parancsfájlpéldát „JELEN ÁLLAPOTÁBAN”, bármiféle jótállás vállalása nélkül biztosítjuk.

```
import-module adrmsadmin 

New-PSDrive -Name MyRmsAdmin -PsProvider AdRmsAdmin -Root https://localhost -Force 

$ListofTemplates=dir MyRmsAdmin:\RightsPolicyTemplate

foreach($Template in $ListofTemplates) 
{ 
                $templateID=$Template.id

                $rights = dir MyRmsAdmin:\RightsPolicyTemplate\$Templateid\userright

     $templateName=$Template.DefaultDisplayName 

        if ($rights.usergroupname -eq "anyone")

                         {
                           $templateName = $Template.defaultdisplayname

                           write-host "Template " -NoNewline

                           write-host -NoNewline $templateName -ForegroundColor Red

                           write-host " contains rights for " -NoNewline

                           write-host ANYONE  -ForegroundColor Red
                         }
 } 
Remove-PSDrive MyRmsAdmin -force
```


## További lépések
Ugrás ide: [2. fázis: Ügyféloldali konfiguráció](migrate-from-ad-rms-phase2.md).




<!--HONumber=Aug16_HO4-->


