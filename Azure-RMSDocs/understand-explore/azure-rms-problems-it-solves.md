---
# required metadata

title: Milyen problémákat képes megoldani az Azure RMS? | Azure RMS
description:
keywords:
author: cabailey
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: b551c62d-5ac6-4359-85b3-90693e77b37f

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: esaggese
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---


# Milyen problémákat képes megoldani az Azure RMS?

*A következőkre vonatkozik: Azure Rights Management, Office 365*

A következő táblázat segítségével azonosíthatja az üzleti követelményeit, vagy a szervezeténél esetleg felmerülő problémákat, illetve hogy miként kezelheti ezeket az RMS.

|Követelmény vagy probléma|Az Azure RMS általi megoldás|
|--------------------------|-----------------------|
|Az összes fájltípus védelme|√ A Rights Management korábbi implementációiban csak az Office-fájlok voltak védhetők, natív védelemmel. Mostantól az [általános védelem](../rms-client/sharing-app-dialog-box.md#what-s-the-difference-between-generic-protection-and-built-in-native-protection-) azt jelenti, hogy minden fájltípus támogatott.|
|Bárhol megvédheti a fájljait|√ Ha egy fájlt ment egy helyre ([védelem helyben](../rms-client/sharing-app-protect-in-place.md)), a fájl védett marad akkor is, ha egy informatikai felügyelet nélküli helyre, például egy felhőalapú tárolási szolgáltatásba lett másolva.|
|Fájlok biztonságos megosztása e-mailben|√ Ha egy fájlt e-mailben oszt meg, ([védett megosztás](../rms-client/sharing-app-protect-by-email.md)), a fájl egy e-mail-üzenethez csatolt mellékletként kap védelmet, az e-mailben a védett mellékletek megnyitására vonatkozó utasításokkal. Az e-mail szövege nincs titkosítva, így a címzett mindig el tudja olvasni az utasításokat. Viszont mivel a mellékelt dokumentum védett, csak a jogosult felhasználók nyithatják meg, még akkor is, ha továbbítják a dokumentumot másoknak.|
|Naplózás és figyelés|√ [Naplózhatja és figyelheti](../deploy-use/log-analyze-usage.md) a védett fájlokat még akkor is, ha a fájlok kívül kerülnek a szervezet határain.<br /><br />Tegyük fel, hogy a Contoso, Ltd. munkatársa. A Fabrikam, Inc. három munkatársával dolgozik közös projekten. Elküld ennek a három személynek egy védett, írásvédelemmel ellátott dokumentumot. Az Azure RMS naplózása a következő információkat biztosítja:<br /><br />Megnyitották-e a Fabrikam kijelölt alkalmazottai a dokumentumot, és mikor?<br /><br />Megpróbálták-e (sikertelenül) megnyitni a dokumentumot nem kijelölt személyek? Például azért, mert olyan megosztott helyre lett továbbítva vagy mentve, amelyhez mások is hozzáférhetnek.<br /><br />Megpróbálták-e (sikertelenül) a kijelölt személyek kinyomtatni vagy módosítani a dokumentumot?|
|Támogatás minden elterjedt eszközhöz, nem csak a Windows-számítógépekhez|√ A [támogatott eszközök](../get-started/requirements-client-devices.md) közé tartoznak többek között:<br /><br />Windows rendszerű számítógépek és telefonok<br /><br />Mac számítógépek<br /><br />iOS rendszerű táblagépek és telefonok<br /><br />Android rendszerű táblagépek és telefonok|
|Támogatás vállalatok közötti együttműködéshez|√ Mivel az Azure RMS egy felhőszolgáltatás, nincs szükség a megbízhatóságok kifejezett konfigurálására más szervezetekkel, mielőtt megosztanának azokkal a védett tartalmat. Ha már rendelkeznek Office 365- vagy Azure AD-címtárral, a szervezetek közötti együttműködés automatikusan támogatott. Ha nem, a felhasználók regisztrálhatnak az ingyenes [RMS egyéni felhasználók számára](rms-for-individuals.md) előfizetésre.|
|Támogatás helyszíni szolgáltatásokhoz és az Office 365-höz|√ Az [Office 365 szolgáltatás zökkenőmentes](office-apps-services-support.md) integrálása mellett az [RMS-összekötő](../deploy-use/deploy-rms-connector.md) telepítése esetén használhatja az Azure RMS-t az alábbi helyszíni szolgáltatásokkal:<br /><br />Exchange Server<br /><br />SharePoint Server<br /><br />Fájlbesorolási infrastruktúrát futtató Windows Server|
|Egyszerű aktiválás|√ [A Rights Management szolgáltatás aktiválása](../deploy-use/activate-service.md) a felhasználók számára csupán néhány kattintás a klasszikus Azure-portálon.|
|Lehetőség a szervezeten belüli igény szerinti méretezésre|√ Mivel az Azure RMS felhőszolgáltatásként fut, és biztosítja az Azure rugalmasságát méretezhetőség tekintetében, nem kell kiosztania vagy telepítenie további helyszíni kiszolgálókat.|
|Lehetőség egyszerű és rugalmas házirendek létrehozására|√ A [testre szabott jogmegadási sablonok](../deploy-use/configure-custom-templates.md) gyors és egyszerű megoldást kínálnak a rendszergazdák számára a házirendek alkalmazásához, valamint a felhasználók számára, hogy a megfelelő szintű védelmet alkalmazzák minden dokumentumra, és korlátozzák a szervezeten belüli személyek hozzáférését.<br /><br />Ha például egy egész vállalatot érintő dokumentumot mindenkivel meg szeretne osztani, alkalmazhat egy írásvédettséget biztosító házirendet az összes belső munkatársra. Ezután, egy bizalmasabb dokumentumnál (pl. egy pénzügyi jelentésnél) korlátozhatja a hozzáférést csak a vezetőségre.|
|Széleskörű alkalmazástámogatás|√ Az Azure RMS szoros integrációt biztosít a Microsoft Office-alkalmazásokkal és -szolgáltatásokkal, és kiterjeszti egyéb alkalmazásokra a támogatást az RMS megosztóalkalmazás használatával.<br /><br />√ A [Microsoft Rights Management SDK](../develop/developers-guide.md#software-development-kits) API-kat biztosít a belső fejlesztők és a szoftverforgalmazók számára az Azure RMS-t támogató egyéni alkalmazások megírásához.<br /><br />További információk: [Other applications that support the RMS APIs](api-support.md) (Egyéb, az RMS API-kat támogató alkalmazások).|
|Az informatikai részlegnek az ellenőrzése alatt kell tartania az adatokat|√ A szervezetek dönthetnek úgy, hogy a saját bérlőkulcsukat kezelik, a „[saját kulcs használata](../plan-design/plan-implement-tenant-key.md)” (BYOK) megoldást használják, és a saját bérlőkulcsukat hardveres biztonsági modulokban (HSM) tárolják.<br /><br />√ Támogatott a naplózás és a [használatnaplózás](../deploy-use/log-analyze-usage.md), így üzleti elemzéseket készíthet, figyelheti a visszaéléseket, és elvégezhet (ha adatszivárgás történt) törvényszéki elemzéseket is.<br /><br />√ A [felügyelői funkció](../deploy-use/configure-super-users.md) használatával elérhető delegált hozzáférés biztosítja, hogy az informatikai részleg mindig hozzáférhessen a védett tartalomhoz, meg ha a dokumentumot egy, azóta a szervezetből kilépő alkalmazott is látta el védelemmel. A társközi titkosítási megoldások ezzel szemben kockázatot jelentenek a vállalati adatok elérése felett gyakorolt irányítás elvesztése szempontjából.<br /><br />√ A helyszíni Active Directory-fiókok egy közös identitásának támogatásához szinkronizálhatja [csak az Azure RMS-hez szükséges címtárattribútumokat](/active-directory/active-directory-aadconnectsync-attributes-synchronized#azure-rms) egy [címtár-szinkronizálási eszköz](/active-directory/active-directory-hybrid-identity-design-considerations-tools-comparison), például az Azure AD Connect használatával.<br /><br />√ Az AD FS segítségével engedélyezheti az egyszeri bejelentkezést a jelszavak felhőbe való replikálása nélkül.<br /><br />√ A szervezeteknek mindig lehetőségük nyílik abbahagyni az Azure RMS használatát anélkül, hogy elveszítenék a korábban Azure RMS-sel védett tartalmat. Információk a leszerelési lehetőségekről: [Az Azure Rights Management leszerelése és deaktiválása](../deploy-use/decommission-deactivate.md). Továbbá azok a szervezetek, ahol telepítve vannak az Active Directory tartalomvédelmi szolgáltatások (AD RMS) a korábban AD RMS által védett adatokhoz való hozzáférés elvesztése nélkül [válthatnak Azure RMS-re](../plan-design/migrate-from-ad-rms-to-azure-rms.md).|
> [!TIP]
> Ha ismeri a Rights Management helyszíni verzióját, az Active Directory tartalomvédelmi szolgáltatásokat (AD RMS), érdekelheti a [az Azure Rights Management és az AD RMS összehasonlító](compare-azure-rms-ad-rms.md) táblázata is..

## Biztonsági, megfelelőségi és szabályozási követelmények
Az Azure RMS a következő biztonsági, megfelelőségi és szabályozási követelményeket támogatja:

√ Iparági szabványos kriptográfia használata és a FIPS 140-2 szabvány támogatása. További információk: [Az Azure RMS által használt titkosítási funkciók: Algoritmusok és kulcshosszok](how-does-it-work.md#cryptographic-controls-used-by-azure-rms-algorithms-and-key-lengths).

√ A Thales hardveres biztonsági modulok (HSM-ek) támogatása a bérlőkulcs Microsoft Azure-adatközpontokban való tárolásához. Az Azure RMS különböző biztonsági világot használ az Észak-Amerikában, az EMEA (Európa, a Közel-Kelet és Afrika) régióban, illetve Ázsiában található adatközpontjaihoz, ezért a kulcsait csak a saját régiójában használhatja.

√ Tanúsítással rendelkezik a következőkhöz:

-   ISO/IEC 27001:2013 (tartalmazza a következőt: [ISO/IEC 27018](http://azure.microsoft.com/blog/2015/02/16/azure-first-cloud-computing-platform-to-conform-to-isoiec-27018-only-international-set-of-privacy-controls-in-the-cloud/))

-   SOC 2 SSAE 16/ISAE 3402 igazolások

-   HIPAA BAA

-   EU-s mintafeltételek

-   FedRAMP az Azure Active Directory in Office 365 tanúsítvány részeként, a FedRAMP Agency Authority által kiadva, HHS általi üzemeltetésre

-   1. szintű PCI DSS

További információ ezekről a külső tanúsítványokról: [Azure biztonsági és adatkezelési központ](http://azure.microsoft.com/support/trust-center/compliance/).

## További lépések

Az Azure RMS működését (akár rendszergazdák, akár felhasználók oldaláról nézve) [Az Azure RMS működés közben](what-admins-users-see.md) című szakaszból ismerheti meg..

Az Azure RMS működésével kapcsolatos további műszaki információkat [Az Azure RMS működése](how-does-it-work.md) című cikkben találja. 

<!--HONumber=Apr16_HO4-->


