---
title: "Az Azure RMS működése | Azure RMS"
description: "Az Azure RMS működésével kapcsolatos egyik lényeges tudnivaló, hogy az Azure Rights Management szolgáltatás (és a Microsoft) nem látja és nem tárolja az adatait a tartalomvédelmi szolgáltatás folyamatának részeként. A védett információkat a rendszer sosem küldi el vagy tárolja az Azure-ban, kivéve ha kifejezetten ott tárolja, vagy olyan felhőszolgáltatást használ, amely az Azure-ban tárolja őket. Az Azure RMS egyszerűen csak olvashatatlanná teszi a dokumentumban szereplő adatokat mindenki számára, aki nem jogosult felhasználó vagy szolgáltatás."
author: cabailey
manager: mbaldwin
ms.date: 06/02/2016
ms.topic: article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: ed6c964e-4701-4663-a816-7c48cbcaf619
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 26b043f1f9e7a1e0cd00c2f31c28f7d6685f0232
ms.openlocfilehash: 527af70532f390330fdb65bc27b04bb366289748


---


# Az Azure RMS működése – technikai részletek

>*A következőkre vonatkozik: Azure Rights Management, Office 365*

Az Azure RMS működésével kapcsolatos egyik lényeges tudnivaló, hogy az Azure Rights Management szolgáltatás (és a Microsoft) nem látja és nem tárolja az adatait a tartalomvédelmi szolgáltatás folyamatának részeként. A védett információkat a rendszer sosem küldi el vagy tárolja az Azure-ban, kivéve ha kifejezetten ott tárolja, vagy olyan felhőszolgáltatást használ, amely az Azure-ban tárolja őket. Az Azure RMS egyszerűen csak olvashatatlanná teszi a dokumentumban szereplő adatokat mindenki számára, aki nem jogosult felhasználó vagy szolgáltatás:

-   Az adatok az alkalmazás szintjén vannak titkosítva, és tartalmaznak egy házirendet, amely meghatározza az adott dokumentum jogosult használatát.

-   Ha egy védett dokumentumot hiteles felhasználó használ vagy jogosult szolgáltatás dolgoz fel, a rendszer visszafejti a dokumentumban szereplő adatokat, és érvényesíti a házirendben meghatározott jogosultságokat.

Az alábbi képen látható, hogy ez a folyamat hogyan működik magas szinten. A titkos képletet tartalmazó dokumentumot védelemmel látják el, majd egy arra jogosult felhasználó vagy szolgáltatás sikeresen megnyitja. A dokumentumot tartalomkulcs védi (a képen zöld kulccsal ábrázolva). Ez minden egyes dokumentum esetében egyedi, és a fájlfejlécben található, ahol az RMS-bérlő gyökérkulcsa védi (a képen piros kulccsal ábrázolva). A bérlőkulcs előállítását és felügyeletét végezheti a Microsoft, de saját kezűleg is elvégezheti a bérlőkulcs előállítását és felügyeletét.

A védelmi folyamat során, amikor az Azure RMS a titkosítást, visszafejtést, engedélyezést és a korlátozások érvényesítését végzi, a rendszer egyszer sem küldi el a titkos képletet az Azure-nak.

![A fájlok védelme az Azure RMS szolgáltatással](../media/AzRMS_SecretColaFormula_final.png)

A fájlvédelem működésének részletes leírását a jelen cikk [Az Azure RMS működésének bemutatása: Első használat, tartalomvédelem, a tartalom felhasználása](#walkthrough-of-how-azure-rms-works-first-use-content-protection-content-consumption) című szakaszában olvashatja.

Az Azure RMS által használt algoritmusok és kulcshosszok technikai részleteit a következő szakasz tartalmazza.

## Az Azure RMS által használt titkosítási funkciók: Algoritmusok és kulcshosszok
Ha az RMS működését nem is kell ismernie, előfordulhat, hogy az általa használt titkosítási funkciókat ismertetve bizonyítania kell, hogy a védelem megfelel az iparági szabványoknak.


|Titkosítási funkciók|Az Azure RMS-ben betöltött szerep|
|-|-|
|Algoritmus: AES<br /><br />Kulcshossz: 128 bites és 256 bites [[1]](#footnote-1)|Dokumentumvédelem|
|Algoritmus: RSA<br /><br />Kulcshossz: 2048 bites|Kulcsvédelem|
|SHA-256|Tanúsítvány-aláírás|

###### 1. lábjegyzet 

A Rights Management megosztóalkalmazás 256 bitet használ az általános védelemhez és a natív védelemhez, ha a fájl .ppdf fájlnévkiterjesztéssel rendelkezik, illetve védett szöveg- vagy képfájl (például .ptxt vagy .pjpg).

A titkosítási kulcsok tárolásának és védelmének módja:

- Az Azure RMS az általa védett egyes dokumentumokhoz vagy e-mailekhez egyszeres AES-kulcsot („tartalomkulcsot”) hoz létre, amely a dokumentumba ágyazva érhető el annak különböző verzióiban. 

- A tartalomkulcsot a szervezet RSA-kulcsa („Azure RMS-bérlőkulcs”) védi a dokumentum házirendjének részeként, amelyen a dokumentum szerzőjének aláírása is szerepel. Ez a bérlőkulcs azonos a szervezet Azure RMS által védett dokumentumai és e-mailjei esetében. A kulcsot csak egy Azure RMS-rendszergazda módosíthatja, ha a szervezet ügyfél által felügyelt bérlőkulcsot használ („saját kulcs használata”, más néven BYOK). 

    Ez a Microsoft online szolgáltatásaiban védett bérlőkulcs ellenőrzött környezetben, szigorú felügyelet alatt áll. Ha ügyfél által felügyelt bérlőkulcsot (BYOK) használ, a biztonságot tovább fokozza a fejlett hardveres biztonsági modulok (HSM-ek) használata az egyes Azure-régiókban, a kulcsok bármilyen körülmények között történő kinyerésének, exportálásának vagy megosztásának képessége nélkül. További információ a bérlőkulcsról és a BYOK-ról: [Az Azure Rights Management-bérlőkulcs tervezése és megvalósítása](../plan-design/plan-implement-tenant-key.md).

- A Windows rendszerű eszközre küldött licencek és tanúsítványok védelmét az ügyfél eszközéhez tartozó titkos kulcs látja el, amelyet a rendszer akkor hoz létre, amikor először használják az Azure RMS szolgáltatást az eszközön. A titkos kulcsot pedig az ügyfélen található DPAPI védi, amely egy, a felhasználó jelszavából származtatott kulcs használatával őrzi a titkos adatokat. A mobileszközökön a rendszer csak egyszer használja a kulcsokat, és mivel ezeket nem tárolják az ügyfeleken, az eszközön nem szükséges védelemmel ellátni őket. 



## Az Azure RMS működésének bemutatása: Első használat, tartalomvédelem, a tartalom felhasználása
Az Azure RMS működésének pontosabb megértéséhez tekintse át az [Azure RMS szolgáltatás aktiválását](../deploy-use/activate-service.md) követő tipikus folyamatot, amikor a felhasználó először használja az RMS szolgáltatást a Windows-számítógépen (**a felhasználói környezet inicializálása** vagy rendszerindítás néven ismert folyamat), **tartalomvédelmet hajt végre** (egy dokumentumon vagy e-mailen), majd **felhasználja** (megnyitja és használja) a korábban mások által védelemmel ellátott tartalmakat.

A felhasználói környezet inicializálását követően a felhasználó védelemmel láthatja el a dokumentumokat, vagy felhasználhatja a védett dokumentumok tartalmát az adott számítógépen.

> [!NOTE]
> Ha a felhasználó egy másik Windows-számítógépet kezd el használni, vagy ha egy másik felhasználó használja ugyanazt a Windows-számítógépet, az inicializálási folyamatot meg kell ismételni.

### A felhasználói környezet inicializálása
Mielőtt a felhasználó egy Windows-számítógépen védelemmel láthatja el a tartalmakat, vagy védett tartalmakat használhat fel, elő kell készíteni a felhasználói környezetet az eszközön. Ez egy egyszeri folyamat, amely automatikusan, felhasználói beavatkozás nélkül megy végbe, amikor a felhasználó tartalomvédelem végrehajtására vagy védett tartalom felhasználására tesz kísérletet.

![RMS-ügyfél aktiválása – 1. lépés](../media/AzRMS.png)

**Mi történik az 1. lépésben?** A számítógépen található RMS-ügyfél először csatlakozik az Azure RMS szolgáltatáshoz, majd a felhasználó Azure Active Directory-fiókját használva elvégzi a hitelesítését.

Ha a felhasználó fiókja össze van vonva az Azure Active Directoryval, a hitelesítés automatikusan végbemegy, és a felhasználónak nem kell megadnia hitelesítő adatokat.

![RMS-ügyfél aktiválása – 2. lépés](../media/AzRMS_useractivation2.png)

**Mi történik a 2. lépésben?** A felhasználó hitelesítését követően a rendszer automatikusan átirányítja a kapcsolatot a szervezet RMS-bérlőjéhez, amely kiadja a felhasználó Azure RMS-ben történő hitelesítéséhez szükséges tanúsítványokat, amelyek birtokában a felhasználó kapcsolat nélküli állapotban tartalmakat védhet le, és felhasználhatja a védett tartalmakat.

Az Azure RMS tárolja a felhasználói tanúsítvány másolatát, így ha a felhasználó egy másik eszközt használ, a tanúsítványok ugyanazokkal a kulcsokkal létrehozhatók.

### Tartalomvédelem
Amikor a felhasználó védelemmel lát el egy dokumentumot, az RMS-ügyfél a következő műveleteket hajtja végre a nem védett dokumentumon:

![RMS-dokumentumvédelem – 1. lépés](../media/AzRMS_documentprotection1.png)

**Mi történik az 1. lépésben?** Az RMS-ügyfél létrehoz egy véletlenszerű kulcsot (a tartalomkulcsot), és ezt a kulcsot használva titkosítja a dokumentumot az AES szimmetrikus titkosítási algoritmussal.

![RMS-dokumentumvédelem – 2. lépés](../media/AzRMS_documentprotection2.png)

**Mi történik a 2. lépésben?** Az RMS-ügyfél ezután sablon alapján vagy dokumentumspecifikus jogosultságokat megadva létrehoz egy, a dokumentumhoz tartozó házirendet tartalmazó tanúsítványt. Ez a házirend tartalmazza a különböző felhasználók vagy csoportok jogosultságait, valamint az esetleges további korlátozásokat (pl. lejárati dátum).

Az RMS-ügyfél ezután a felhasználói környezet inicializálásakor kapott szervezeti kulccsal titkosítja a házirendet és a szimmetrikus tartalomkulcsot. Az RMS-ügyfél emellett alá is írja a házirendet a felhasználói környezet inicializálásakor kapott felhasználói tanúsítvánnyal.

![RMS-dokumentumvédelem – 3. lépés](../media/AzRMS_documentprotection3.png)

**Mi történik a 3. lépésben?** Végül az RMS-ügyfél beágyazza a házirendet egy korábban titkosított törzsű dokumentumba, aminek eredményeképp létrejön egy védett dokumentum.

Ez a dokumentum bárhol tárolható, illetve bármilyen módszerrel megosztható, és a titkosított dokumentum házirendje sohasem változik.

### Tartalom felhasználása
Amikor a felhasználó használni szeretne egy védett dokumentumot, az RMS-ügyfél először hozzáférést kér az Azure RMS szolgáltatáshoz:

![RMS-dokumentumfelhasználás – 1. lépés](../media/AzRMS_documentconsumption1.png)

**Mi történik az 1. lépésben?** A hitelesített felhasználó elküldi a dokumentum házirendjét és a felhasználó tanúsítványait az Azure RMS szolgáltatásnak. A szolgáltatás elvégzi a házirend visszafejtését és értékelését, majd létrehozza a dokumentumra vonatkozó jogosultságok listáját (ha a felhasználó rendelkezik jogosultságokkal).

![RMS-dokumentumfelhasználás – 2. lépés](../media/AzRMS_documentconsumption2.png)

**Mi történik a 2. lépésben?** A szolgáltatás ezt követően kiolvassa az AES-tartalomkulcsot a visszafejtett házirendből. A rendszer ezután titkosítja a kulcsot a kérelemmel együtt kapott felhasználói nyilvános RSA-kulccsal.

Az újratitkosított tartalomkulcsot a rendszer ezután beágyazza egy, a felhasználói jogosultságok listáját tartalmazó titkosított használati licencbe, amelyet ezután visszaküld az RMS-ügyfélnek.

![RMS-dokumentumfelhasználás – 3. lépés](../media/AzRMS_documentconsumption3.png)

**Mi történik a 3. lépésben?** Végül az RMS-ügyfél a saját felhasználói titkos kulcsával visszafejti a titkosított használati licencet. Ezután az RMS-ügyfél elvégezheti a dokumentumtörzs szükséges visszafejtését, és megjelenítheti a képernyőn.

Az ügyfél a jogosultságok listáját is visszafejti, és átadja őket az alkalmazásnak, amely érvényesíti az adott jogosultságokat az alkalmazás felhasználói felületén.

### Változatok
A fenti bemutatók a szokásos forgatókönyvet ismertetik, ennek azonban több változata is lehet:

-   **Mobileszközök:** Amikor mobileszközök védenek vagy használnak fel fájlokat az Azure RMS szolgáltatás használatával, a folyamatok sokkal egyszerűbbek. A mobileszközök esetében először nem zajlik le az inicializálási folyamat, mert az egyes (tartalomvédelmi vagy tartalomfelhasználási) tranzakciók függetlenek egymástól. Csakúgy, mint a Windows-számítógépek, a mobileszközök csatlakoznak az Azure RMS szolgáltatáshoz, és elvégzik a hitelesítést. Tartalomvédelem esetén a mobileszközök elküldenek egy házirendet, az Azure RMS pedig közzétételi licencet és szimmetrikus kulcsot küld nekik a dokumentum védelméhez. A tartalmak felhasználása esetén a mobileszközök az Azure RMS szolgáltatáshoz történő csatlakozás és hitelesítés során elküldik a dokumentum-házirendet az Azure RMS szolgáltatásnak, és használati licencet igényelnek a dokumentum felhasználásához. Válaszként az Azure RMS elküldi a szükséges kulcsokat és korlátozásokat a mobileszközöknek. Mindkét folyamat TLS használatával védi a kulcscserét és a további kommunikációt.

-   **RMS-összekötő:** Az Azure RMS és az RMS-összekötő együttes használata esetén a folyamat változatlan marad. Az egyetlen különbség, hogy az összekötő továbbítóként működik a helyszíni szolgáltatások (például az Exchange-kiszolgáló és a SharePoint-kiszolgáló) és az Azure RMS között. Maga az összekötő semmilyen műveletet nem hajt végre (pl. a felhasználói környezet inicializálását, titkosítást vagy visszafejtést). Csupán továbbítja a kommunikációt, ami egyébként az AD RMS-kiszolgálóra irányulna, és kezeli a fordítást az egyes oldalakon használt protokollok között. Ez a forgatókönyv az Azure RMS helyszíni szolgáltatásokkal történő használatát teszi lehetővé.

-   **Általános védelem (.pfile):** Ha az Azure RMS általános védelemmel lát el egy fájlt, a tartalomvédelmi folyamat alapvetően azonos, azzal a kivétellel, hogy az RMS-ügyfél létrehoz egy, az összes jogosultságot biztosító házirendet. A fájl titkosítását a felhasználáskor a rendszer a célalkalmazásnak történő továbbítás előtt visszafejti. Ez az eljárás az összes fájlt védi, még akkor is, ha nem támogatják natívan az RMS-t.

-   **Védett PDF (.ppdf):** Amikor az Azure RMS natív védelmet biztosít egy Office-fájl számára, létrehoz egy másolatot is a fájlról, és ugyanazon a módon védi. Az egyetlen különbség, hogy a fájlmásolat PPDF formátumban lesz. Ezt a formátumot az RMS megosztóalkalmazás meg tudja nyitni írásvédett módban. Ez az eljárás lehetővé teszi a védett fájlok e-mailben való küldését, mert biztosítható, hogy a címzett akkor is meg tudja tekinteni őket egy mobileszközön, ha az eszközre nem lett az Office-fájlokat natívan támogató alkalmazás telepítve.

## További lépések

Az Azure RMS-ről a **Megismerés és felfedezés** szakaszban találhat további információkat. A [Hogyan támogatják a különböző alkalmazások az Azure Rights Managementet](applications-support.md) című cikkből például megtudhatja, hogyan biztosíthatnak tartalomvédelmi megoldást a meglévő alkalmazásai az Azure RMS-sel integrálva. 

[Az Azure Rights Management terminológiája](../get-started/terminology.md) cikket áttekintve megismerheti az Azure RMS konfigurálása és használata során előkerülő fogalmakat, és a telepítés megkezdése előtt mindenképp érdemes megtekinteni [Az Azure Rights Management követelményei](../get-started/requirements-azure-rms.md) című fejezetet is. Ha rögtön kipróbálná a szolgáltatást, használja az [Azure Rights Management gyors üzembe helyezési oktatóanyagot](../get-started/quick-start-tutorial.md).

Ha készen áll az Azure RMS központi telepítésére a szervezeténél, az [Azure Rights Management deployment roadmap](../plan-design/deployment-roadmap.md) (Azure Rights Management üzembe helyezési menetrend) felkeresésével megismerheti a telepítés lépéseit, valamint ugyanitt megtalálja az útmutatókra mutató hivatkozásokat is.

> [!TIP]
> További információért és segítségért használja az [Azure Rights Management – információ és támogatás](../get-started/information-support.md) című szakaszban található forrásanyagokat és hivatkozásokat.



<!--HONumber=Aug16_HO4-->


