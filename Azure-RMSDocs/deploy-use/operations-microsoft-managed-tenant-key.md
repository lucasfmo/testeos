---
# required metadata

title: A Microsoft által felügyelt megoldás – a bérlői kulcs életciklusához kapcsolódó műveletek | Azure RMS
description:
keywords:
author: cabailey
manager: mbaldwin
ms.date: 06/14/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 3c48cda6-e004-4bbd-adcf-589815c56c55

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: esaggese
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---


# A Microsoft által felügyelt megoldás – a bérlői kulcs életciklusához kapcsolódó műveletek

*A következőkre vonatkozik: Azure Rights Management, Office 365*

Ha a Microsoft kezeli az Azure Rights Management bérlői kulcsát (ez az alapértelmezés), az alábbi szakaszok áttekintésével további információhoz juthat azon életciklus-műveletekkel kapcsolatban, amelyek ehhez a topológiához kapcsolódnak.

## A bérlői kulcs visszavonása
Az Azure RMS-előfizetés lemondásakor az Azure RMS nem használja tovább a bérlői kulcsot, és nincs szükség külön felhasználói beavatkozásra.

## A bérlői kulcs kulcsismétlése
A kulcsismétlést kulcsváltásnak is nevezik. Csak akkor hajtsa végre a bérlői kulcs kulcsismétlését, ha arra valóban szükség van. A régebbi ügyfélprogramok, például az Office 2010, nem képesek zökkenőmentesen kezelni a kulcsváltozásokat. Ebben az esetben törölnie kell az RMS-állapotot a számítógépeken csoportházirend vagy egy azzal egyenértékű módszer használatával. Előfordulhatnak azonban olyan események, amelyek a bérlői kulcs kulcsismétlésére kényszerítik. Példa:

-   A vállalatot kettő vagy több vállalatra osztották fel. A bérlői kulcs kulcsismétlésekor az új vállalat nem fog hozzáférni az alkalmazottak által közzétett új tartalmakhoz. A régi tartalmakat továbbra is elérheti, ha rendelkezik a régi bérlői kulcs másolatával.

-   Úgy véli, hogy a bérlői kulcs főpéldányát (az Ön birtokában lévő példányt) feltörték.

A bérlői kulcs kulcsismétléséhez [lépjen kapcsolatba a Microsoft támogatási szolgálatával](../get-started/information-support#to-contact-microsoft-support), és nyisson egy **Azure Rights Management támogatási esetet az Azure RMS-bérlőkulcs kulcsismétléséhez**. Igazolja, hogy Ön az Azure RMS bérlői rendszergazdája. A folyamat jóváhagyása több napig is eltarthat. A szolgáltatásra a szabványos támogatási díjak vonatkoznak; a bérlői kulcs kulcsismétlése nem ingyenes szolgáltatás.

A bérlői kulcs kulcsismétlésekor az új tartalmakat az új bérlői kulcs segítségével lehet védelemmel ellátni. Ez szakaszosan történik, így bizonyos ideig egyes új tartalmaknak még a régi bérlői kulcs biztosít védelmet. A korábban védelemmel ellátott tartalmakat továbbra is a régi bérlői kulcs fogja védeni. A forgatókönyv támogatása érdekében az Azure RMS megőrzi a régi bérlői kulcsot, hogy az licenceket adhasson ki a régi tartalmakhoz.

## A bérlői kulcs biztonsági mentése és helyreállítása
A Microsoft felelőssége, hogy a bérlői kulcs biztonsági mentéséről gondoskodjon, így Önnek semmit sem kell tennie.

## A bérlői kulcs exportálása
Az Azure RMS-konfiguráció és a bérlői kulcs exportálásához hajtsa végre a következő három lépés utasításait:

### 1. lépés: Exportálás kezdeményezése

-   Ehhez [forduljon a Microsoft támogatási szolgálatához](../get-started/information-support#to-contact-microsoft-support), ahol megnyithat egy **Azure RMS-kulcsexportálási kérelmet tartalmazó Azure Rights Management támogatási esetet**. Igazolja, hogy Ön az Azure RMS bérlői rendszergazdája. A folyamat jóváhagyása több napig is eltarthat. A szolgáltatásra a szabványos támogatási díjak vonatkoznak; a bérlői kulcs exportálása nem ingyenes szolgáltatás.

### 2. lépés: Várakozás az ellenőrzésre

-   A Microsoft ellenőrzi, hogy az RMS bérlői kulcs kiadására irányuló kérelem indokolt-e. A folyamat akár három hetet is igénybe vehet.

### 3. lépés: A CSS megadja a legfontosabb utasításokat

-   A Microsoft támogatási szolgálat (CSS) elküldi Önnek az Azure RMS-konfigurációt és a bérlői kulcsot egy titkosított, jelszóval védett, .tpd fájlnévkiterjesztésű fájlban. Ehhez a CSS először küldeni fog Önnek (az exportálást kezdeményező személynek) egy eszközt e-mailben. Az eszközt a következőképpen futtassa a parancssorból:

    ```
    AadrmTpd.exe -createkey
    ```
    Ez egy RSA-kulcspárt hoz létre, és a nyilvános és privát feleket fájlokként menti az aktuális mappába. Például: **PublicKey-FA29D0FE-5049-4C8E-931B-96C6152B0441.txt** és **PrivateKey-FA29D0FE-5049-4C8E-931B-96C6152B0441.txt**.

    Válaszoljon az ügyfélszolgálati támogatástól kapott e-mailre, és csatolja azt a fájlt, amelynek a neve a **PublicKey** karakterlánccal kezdődik. A CSS ezután küldeni fog egy .xml TPD-fájlt, amelyet az Ön RSA-kulcsával titkosítottak. A fájlt másolja ugyanabba a mappába, ahonnan az AadrmTpd eszközt eredetileg futtatta, majd futtassa ismét az eszközt a **PrivateKey** kezdetű fájl és az ügyfélszolgálati támogatástól kapott fájl használatával. Példa:

    ```
    AadrmTpd.exe -key PrivateKey-FA29D0FE-5049-4C8E-931B-96C6152B0441.txt -target TPD-77172C7B-8E21-48B7-9854-7A4CEAC474D0.xml
    ```
    A parancs két fájlt hoz létre: az egyik a titkosítatlan szöveges jelszót tartalmazza a jelszóval védett TPD-fájlhoz, a másik maga a jelszóval védett TPD-fájl. A kereszthivatkozások érdekében mindkettőnek ugyanazzal a GUID azonosítóval kell rendelkeznie, mint a nyilvános és a titkos kulcsfájloknak az AadrmTpd.exe -createkey parancs futtatásakor:

    -   Password-FA29D0FE-5049-4C8E-931B-96C6152B0441.txt

    -   ExportedTPD-FA29D0FE-5049-4C8E-931B-96C6152B0441.xml

    Készítsen biztonsági mentést ezekről a fájlokról, és tárolja őket biztonságosan, hogy a továbbiakban is vissza tudja fejteni a bérlői kulcs által védett tartalmakat. Emellett az AD RMS-re történő áttelepítésnél ezt a TPD-fájlt (az **ExportedTDP** kezdetű fájlt) importálhatja az AD RMS-kiszolgálójára.

### 4. lépés: folyamatos: a bérlői kulcs védelme

-   Miután megkapta a bérlői kulcsot, őrizze gondosan, mivel ha mások is hozzáférnek, visszafejthetik a kulccsal védett dokumentumokat.

    Ha azért exportálja a bérlői kulcsot, mert már nem szeretné használni az Azure RMS-t, akkor az ajánlott eljárás az RMS-bérlő inaktiválása. Ezt ne halassza a bérlői kulcs beszerzése utánra, mert ezzel az óvintézkedéssel minimalizálhatja a bérlői kulcs illetéktelen hozzáférésének következményeit. További útmutatás: [Az Azure Rights Management leszerelése és inaktiválása](decommission-deactivate.md).

## Válasz a biztonsági szabályok megsértésére
Még a legerősebb biztonsági rendszerek sem lehetnek teljesek a biztonsági szabályok megsértésére reagáló folyamat nélkül. A bérlői kulcsot feltörhetik vagy ellophatják. A kulcs kiváló védelme ellenére is jelentkezhetnek biztonsági rések a HSM-technológia aktuális generációjában vagy a jelenlegi kulcshosszúságokhoz vagy algoritmusokhoz kapcsolódóan.

A Microsoftnál külön csapat foglalkozik azzal, hogy reagáljon a vállalat termékeiben és szolgáltatásaiban észlelt biztonsági eseményekre. Amint hiteles bejelentés érkezik egy eseményről, a csapat megkezdi a hatókör, az alapvető ok és a szükséges beavatkozások körének felmérését. Ha az esemény érinti az Ön eszközeit, a Microsoft az előfizetéskor megadott címre küldött e-mailben értesíti az Azure RMS bérlői rendszergazdákat.

Ha megsértették a biztonsági szabályokat, az Ön vagy a Microsoft által végrehajtható legmegfelelőbb lépés a biztonsági incidens hatókörétől függ. A Microsoft együtt fog működni Önnel a folyamat során. Az alábbi táblázat néhány jellemező helyzetet és az azokra adott valószínű választ ismerteti, de a tényleges válasz a vizsgálat során feltárt információk összességétől függ.

|Esemény leírása|Várható válasz|
|------------------------|-------------------|
|A bérlői kulcs kiszivárgott.|Hajtsa végre a bérlői kulcs kulcsismétlését. Olvassa el ebben a cikkben [A bérlői kulcs kulcsismétlése](operations-tenant-key#re-key-your-tenant-key) című szakaszt.|
|Jogosulatlan személy vagy kártevő szerzett jogosultságokat a bérlői kulcs használatára, maga a kulcs azonban nem szivárgott ki.|A bérlői kulcs kulcsismétlése ebben az esetben nem célravezető megoldás, és elemezni kell a probléma alapvető okát. Ha egy folyamat vagy szoftverhiba miatt szerezhetett hozzáférést a jogosulatlan személy, arra a problémára kell megoldást találni.|
|Biztonsági rést észleltek az RSA-algoritmusban vagy a kulcshosszúságban, vagy találgatásos támadások váltak számítási szempontból megvalósíthatóvá.|A Microsoftnak frissítenie kell az Azure RMS-t az új algoritmusok és az ellenállóbb, hosszabb kulcshosszúságok támogatására, és fel kell szólítania az ügyfeleit a bérlői kulcsok megújítására.|




<!--HONumber=Jun16_HO2-->


