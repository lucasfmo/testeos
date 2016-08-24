---
title: "Felhasználó által felügyelt megoldás – a bérlőkulcs életciklusához kapcsolódó műveletek | Azure RMS"
description: 
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 08/17/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: c5b19c59-812d-420c-9c54-d9776309636c
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 437afd88efebd9719a3db98f8ab0ae07403053f7
ms.openlocfilehash: 9bff4e1380dfa3fabab1e8cb9317f3dd31b05a77


---


# Felhasználó által felügyelt megoldás: a bérlőkulcs életciklusához kapcsolódó műveletek

*A következőkre vonatkozik: Azure Rights Management, Office 365*

Ha Ön kezeli az Azure Rights Management bérlőkulcsát (a saját kulcs használata avagy BYOK-forgatókönyv szerint), az alábbi szakaszok áttekintésével további információhoz juthat azon életciklus-műveletekkel kapcsolatban, amelyek ehhez a topológiához kapcsolódnak.

## A bérlőkulcs visszavonása
Az Azure Key Vaultban lehetősége van az Azure RMS-bérlőkulcsot tartalmazó kulcstartó engedélyeinek módosítására, hogy az Azure RMS szolgáltatás már ne férhessen hozzá a kulcshoz. Ugyanakkor ha ezt végrehajtja, senki nem tudja majd megnyitni a korábban az Azure RMS által védett dokumentumokat és e-mail üzeneteket.

Az Azure RMS-előfizetés lemondásakor az Azure RMS nem használja tovább a bérlői kulcsot, és nincs szükség külön felhasználói beavatkozásra.


## A bérlői kulcs kulcsismétlése
A kulcsismétlést kulcsváltásnak is nevezik. Csak akkor hajtsa végre a bérlői kulcs kulcsismétlését, ha arra valóban szükség van. A régebbi ügyfélprogramok, például az Office 2010, nem képesek zökkenőmentesen kezelni a kulcsváltozásokat. Ebben az esetben törölnie kell az RMS-állapotot a számítógépeken csoportházirend vagy egy azzal egyenértékű módszer használatával. Előfordulhatnak azonban olyan események, amelyek a bérlői kulcs kulcsismétlésére kényszerítik. Példa:

-   A vállalatot kettő vagy több vállalatra osztották fel. A bérlői kulcs kulcsismétlésekor az új vállalat nem fog hozzáférni az alkalmazottak által közzétett új tartalmakhoz. A régi tartalmakat továbbra is elérheti, ha rendelkezik a régi bérlői kulcs másolatával.

-   Úgy véli, hogy a bérlőkulcs főpéldányát (az Ön birtokában lévő példányt) feltörték.

A bérlőkulcs kulcsismétlésekor az új tartalmakat az új bérlőkulcs segítségével lehet védelemmel ellátni. Ez szakaszosan történik, így bizonyos ideig egyes új tartalmaknak még a régi bérlői kulcs biztosít védelmet. A korábban védelemmel ellátott tartalmakat továbbra is a régi bérlői kulcs fogja védeni. A forgatókönyv támogatása érdekében az Azure RMS megőrzi a régi bérlőkulcsot, hogy az licenceket adhasson ki a régi tartalmakhoz.

Ha kulcsismétlést szeretne végrehajtani a bérlőkulcs esetében, először az Azure RMS-bérlőkulcson kell elvégeznie ezt a műveletet a Key Vaultban. Ezt követően futtassa ismét a kulcs új URL-címének megadásához szükséges Add-AadrmKeyVaultKey parancsmagot.

## A bérlőkulcs biztonsági mentése és helyreállítása
A felhasználó felelőssége, hogy a bérlőkulcs biztonsági mentéséről gondoskodjon. Ha a bérlőkulcsot Thales HSM-ben hozta létre, a kulcs biztonsági mentéséhez egyszerűen készítsen biztonsági másolatot a tokenekre bontott kulcsfájlról, a világfájlról és a rendszergazdai kártyákról.

Mivel a kulcs átviteléhez [Az Azure Rights Management-bérlőkulcs tervezése és megvalósítása](../plan-design/plan-implement-tenant-key.md) című cikk [A saját kulcs használatának (BYOK) megvalósítása](../plan-design/plan-implement-tenant-key.md#implementing-your-azure-rights-management-tenant-key) szakaszában ismertetett eljárásokat követte, az Azure Key Vault megőrzi a tokenekre bontott kulcsfájlt a szolgáltatási csomópontok meghibásodása elleni védelem érdekében. A fájl adott Azure-régió vagy -példány biztonsági világához van kötve. Ez azonban nem tekinthető teljes körű teljes biztonsági mentésnek. Ha például valamikor szüksége lesz a kulcs egyszerű szöveges másolatának a használatára a Thales HSM-en kívül, az Azure Key Vault nem fogja tudni lekérni a kulcsot, mert az csak egy nem helyreállítható példánnyal rendelkezik.

## A bérlőkulcs exportálása
Ha a BYOK használata mellett döntött, nem exportálhatja a bérlőkulcsot az Azure Key Vaultból vagy az Azure RMS-ből. Az Azure Key Vaultban található példány nem állítható helyre. 

## Válasz a biztonsági szabályok megsértésére
Még a legerősebb biztonsági rendszerek sem lehetnek teljesek a biztonsági szabályok megsértésére reagáló folyamat nélkül. A bérlői kulcsot feltörhetik vagy ellophatják. A kulcs kiváló védelme ellenére is jelentkezhetnek biztonsági rések a HSM-technológia aktuális generációjában vagy a jelenlegi kulcshosszúságokhoz vagy algoritmusokhoz kapcsolódóan.

A Microsoftnál külön csapat foglalkozik azzal, hogy reagáljon a vállalat termékeiben és szolgáltatásaiban észlelt biztonsági eseményekre. Amint hiteles bejelentés érkezik egy eseményről, a csapat megkezdi a hatókör, az alapvető ok és a szükséges beavatkozások körének felmérését. Ha az esemény érinti az Ön eszközeit, a Microsoft az előfizetéskor megadott címre küldött e-mailben értesíti az Azure RMS bérlői rendszergazdákat.

Ha megsértették a biztonsági szabályokat, az Ön vagy a Microsoft által végrehajtható legmegfelelőbb lépés attól függ, hogy a biztonsági incidens mi mindent érint. A Microsoft együtt fog működni Önnel a folyamat során. Az alábbi táblázat néhány jellemező helyzetet és az azokra adott valószínű választ ismerteti, jóllehet a tényleges válasz a vizsgálat során feltárt információk összességétől függ.

|Esemény leírása|Várható válasz|
|------------------------|-------------------|
|A bérlői kulcs kiszivárgott.|Hajtsa végre a bérlői kulcs kulcsismétlését. Lásd: [A bérlőkulcs kulcsismétlése](#re-key-your-tenant-key).|
|Jogosulatlan személy vagy kártevő szerzett jogosultságokat a bérlői kulcs használatára, maga a kulcs azonban nem szivárgott ki.|A bérlői kulcs kulcsismétlése ebben az esetben nem célravezető megoldás, és elemezni kell a probléma alapvető okát. Ha egy folyamat vagy szoftverhiba miatt szerezhetett hozzáférést a jogosulatlan személy, arra a problémára kell megoldást találni.|
|Biztonsági rést észleltek a HSM technológia aktuális generációjában.|A Microsoftnak frissítenie kell a HSM-eket. Ha okkal feltételezhető, hogy a biztonsági rés hozzáférhetővé tette a kulcsokat, a Microsoftnak minden ügyfelet fel fog szólítania a bérlőkulcsok megújítására.|
|Biztonsági rést észleltek az RSA-algoritmusban vagy a kulcshosszúságban, vagy találgatásos támadások váltak számítási szempontból megvalósíthatóvá.|A Microsoftnak frissítenie kell az Azure Key Vaultot vagy az Azure RMS-t az új algoritmusok és az ellenállóbb, nagyobb kulcshosszúságok támogatására, és fel kell szólítania az ügyfeleit a bérlői kulcsok megújítására.|





<!--HONumber=Aug16_HO3-->


