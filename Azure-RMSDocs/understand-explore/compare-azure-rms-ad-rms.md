---
title: "Az Azure Rights Management és az AD RMS összehasonlítása | Azure RMS"
description: 
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 07/13/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 8123bd62-1814-4d79-b306-e20c1a00e264
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 67129d6cdac124947fc07aa4d42523686227752e
ms.openlocfilehash: ce79ec40cbd8ca3796a17920d27dc3872cd40842


---

# Az Azure Rights Management és az AD RMS összehasonlítása

*A következőkre vonatkozik: Active Directory Rights Management Services, Azure Rights Management, Office 365*

Ha ismeri vagy korábban már telepítette az Active Directory tartalomvédelmi szolgáltatásokat (AD RMS), talán kíváncsi, hogyan viszonyul ahhoz az [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] (Azure RMS) a funkciók és a követelmények tekintetében. 

A főbb eltérések az Azure RMS-hez képest:

- **Nincs szükség kiszolgálói infrastruktúrára:** Az AD RMS-sel szemben Azure RMS nem igényel további kiszolgálókat és PKI-tanúsítványokat, mert a Microsoft Azure gondoskodik minderről. Ennek köszönhetően ez a felhőmegoldás gyorsabban telepíthető, és egyszerűbben karbantartható.

- **Felhőalapú hitelesítés:** Az Azure RMS Azure AD-t használ a hitelesítéshez – mind a belső felhasználók, mind más szervezetek felhasználói esetén. Ez azt jelenti, hogy a mobil felhasználók akkor is hitelesíthetők, ha nem csatlakoznak a belső hálózathoz, és egyszerűbb megosztani a védett tartalmat más szervezetek felhasználóival. Számos szervezet már rendelkezik felhasználói fiókkal az Azure AD-ban, mert már futtatják az Azure-szolgáltatásokat, vagy rendelkeznek Office 365-tel. De ha nem is így lenne, az RMS egyéni felhasználók számára lehetővé teszi ingyenes fiók létrehozását. Az AD RMS által védett tartalom másik szervezettel való megosztásához kifejezett megbízhatósági viszonyt kell konfigurálnia az egyes szervezetekkel.

- **Mobileszközök beépített támogatása:** Azure RMS esetében nincs szükség a környezet módosítására a mobileszközök és Mac gépek használatának támogatásához. AD RMS esetében ezen eszközök támogatásához telepítenie kell a mobileszköz-bővítményt, konfigurálnia kell az AD FS-t az összevonáshoz, és létre kell hoznia további rekordokat a nyilvános DNS-szolgáltatáshoz.

- **Alapértelmezett sablonok:** Az Azure RMS két alapértelmezett sablont hoz létre, amint aktiválódik a szolgáltatás, ezáltal különösen könnyű azonnal védelmet biztosítani a fontos adatok számára. Az AD RMS esetében nincsenek alapértelmezett sablonok.

- **Részlegszintű sablonok:** Az Azure RMS konfigurációs beállításként támogatja a részlegszintű sablonokat a további létrehozott sablonokhoz. A beállítás segítségével megadható, hogy mely felhasználók láthatják a sablont az ügyfélalkalmazásaikban (például az Office-alkalmazásokban). Így egyszerűbben tudják kiválasztani a különböző felhasználói csoportokhoz megadott megfelelő házirendeket. Az AD RMS nem támogatja a részlegszintű sablonokat.

- **Dokumentumkövetés, visszavonás és e-mailes értesítés:** Az Azure RMS támogatja ezeket a funkciókat az RMS megosztóalkalmazáson keresztül, az AD RMS viszont nem.


Ezenfelül, mivel az Azure RMS egy felhőszolgáltatás, új funkciókat biztosít, és gyorsabban alkalmazhatók a javításai, mint egy helyszíni, kiszolgálóalapú megoldás. Az AD RMS-hez nincs tervben új szolgáltatások megjelentetése a Windows Server 2016 rendszerben.

A további részletek és eltérések megismeréséhez használja az alábbi táblázatot, ahol egymás mellett tekintheti át az Azure RMS és az AD RMS szolgáltatásait és előnyeit. Ha a biztonsággal kapcsolatos összehasonlító kérdései vannak, tekintse meg a jelen cikk [Titkosítási funkciók aláíráshoz és titkosításhoz](compare-azure-rms-ad-rms.md#cryptographic-controls-for-signing-and-encryption) című szakaszát.

> [!NOTE]
> Az összehasonlítás megkönnyítése érdekében [Az Azure Rights Management követelményei](../get-started/requirements-azure-rms.md) szakaszból itt is feltüntettünk néhány információt. Használja a forrást pontosabb támogatásért és verzióinformációkért a következővel kapcsolatban: [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)].

|Azure RMS|AD RMS|
|-----------------------------------------------------------------------------------------|--------------------------------------------------------|
|Támogatja a tartalomvédelmi szolgáltatási (IRM) képességeket a Microsoft Online szolgáltatásaiban, például az Exchange Online-ban, a SharePoint Online-ban, valamint az Office 365-ben.<br /><br />Emellett támogatja a helyszíni Microsoft kiszolgálói termékeket, például az Exchange Servert, a SharePoint Servert, valamint a Windows Servert és fájlbesorolási infrastruktúrát (FCI) futtató fájlkiszolgálókat.|Támogatja a helyszíni Microsoft kiszolgálói termékeket, például az Exchange Servert, a SharePoint Servert, valamint a Windows Servert és fájlbesorolási infrastruktúrát (FCI) futtató fájlkiszolgálókat.|
|Implicit megbízhatóságot tesz lehetővé a szervezetek és bármely szervezet felhasználói között. Ez azt jelenti, hogy a védett tartalmakat az azonos és a különböző szervezetekbe tartozó felhasználók is megoszthatják egymással, ha van a birtokukban [!INCLUDE[o365_1](../includes/o365_1_md.md)] vagy [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)], vagy egyéni felhasználóként feliratkoznak az RMS szolgáltatásra.|A megbízhatóságokat a két szervezetet összekötő közvetlen kapcsolatokban explicit módon meg kell határozni, vagy megbízható felhasználói tartományok (TUD-k) használatával, vagy pedig összevont megbízhatóságokkal, amelyek az Active Directory összevonási szolgáltatások (AD FS) használatával hozhatók létre.|
|Két alapvető jogosultsági házirendsablont biztosít, amelyek korlátozzák a saját szervezete tartalmainak elérését. Az egyik sablon a védett tartalmak esetében csak olvasási jogosultságot biztosít, a másik pedig írási vagy módosítási jogosultságot is.<br /><br />Létrehozhatók saját egyéni sablonok, köztük csak a felhasználók egy része számára látható részlegszintű sablonok is. További információ: [Configuring custom templates for Azure Rights Management](../deploy-use/configure-custom-templates.md) (Egyéni sablonok konfigurálása az Azure Rights Management szolgáltatáshoz).<br /><br />Emellett, amennyiben a sablonok nem elegendőek, a felhasználók meghatározhatják a saját engedélykészleteiket is.|Alapértelmezett jogosultsági házirendsablonok nincsenek. Ezeket Önnek kell létrehoznia és közzétennie. További információ: [AD RMS Policy Template Considerations](http://go.microsoft.com/fwlink/?LinkId=154765) (Az AD RMS házirendsablonjainak szempontjai).<br /><br />Emellett, amennyiben a sablonok nem elegendőek, a felhasználók meghatározhatják a saját engedélykészleteiket is.|
|A Microsoft Office minimális támogatott verziója az Office 2010, amelyhez az [RMS megosztóalkalmazás](../rms-client/sharing-app-windows.md) szükséges.<br /><br />Mac Microsoft Office:<br /><br />– Mac Microsoft Office 2016: Támogatott<br /><br />– Mac Microsoft Office 2011: Nem támogatott|A Microsoft Office minimális támogatott verziója az Office 2007.<br /><br />Mac Microsoft Office:<br /><br />– Mac Microsoft Office 2016: Támogatott<br /><br />– Mac Microsoft Office 2011: Támogatott|
|Támogatja az [RMS megosztóalkalmazást](../rms-client/sharing-app-windows.md) windowsos és Mac számítógépeken, valamint mobileszközökön.<br /><br />Emellett az RMS megosztóalkalmazás a következőket támogatja:<br /><br />– Megosztás másik szervezethez tartozó személyekkel.<br /><br />– E-mail-értesítések, amelyek jelzik a küldőnek, ha valaki megpróbál megnyitni egy védett mellékletet.<br /><br />– Dokumentumkövető oldal, amely lehetőséget nyújt a felhasználóknak a dokumentumok visszavonására.|Támogatja az [RMS megosztóalkalmazást](../rms-client/sharing-app-windows.md) windowsos és Mac számítógépeken, valamint mobileszközökön. Mindazonáltal a megosztás nem támogatja a másik szervezet tagjaival való megosztást, az e-mail-értesítéseket, a dokumentumkövető oldalt és a dokumentumok felhasználók általi visszavonásának lehetőségét.|
|Az RMS megosztóalkalmazás használatával minden fájltípus ellátható [natív vagy általános védelemmel](../rms-client/sharing-app-admin-guide-technical.md#levels-of-protection-native-and-generic).<br /><br />Más alkalmazások esetén tanulmányozza át az [Azure RMS-követelmények: Alkalmazások](../get-started/requirements-applications.md) című témakörben található táblázatot.|Az RMS megosztóalkalmazás használatával minden fájltípus ellátható [natív vagy általános védelemmel](../rms-client/sharing-app-admin-guide-technical.md#levels-of-protection-native-and-generic).<br /><br />Más alkalmazások esetén tanulmányozza át az [Azure RMS-követelmények: Alkalmazások](../get-started/requirements-applications.md) című témakörben található táblázatot.|
|A Windows-ügyfél minimális támogatott verziója a Windows 7.|A Windows-ügyfél minimális támogatott verziója a Windows Vista Service Pack 2.|
|A mobileszköz-támogatás kiterjed a Windows Phone, Android, iOS és Windows RT rendszerű készülékekre.<br /><br />Szintén támogatott az Exchange ActiveSync IRM-jét használó e-mailes támogatás minden olyan mobileszköz-platformon, amely támogatja ezt a protokollt.|A mobileszköz-támogatás kiterjed a Windows Phone, Android, iOS és Windows RT rendszerű készülékekre, és az [Active Directory Rights Management Services mobileszköz-bővítmény](http://technet.microsoft.com/library/dn673574.aspx) szükséges hozzá.<br /><br />Az Exchange ActiveSync IRM-jét használó e-mailes támogatás minden olyan mobileszköz-platformon támogatott, amely támogatja ezt a protokollt.|
|Támogatja a többtényezős hitelesítést (MFA) számítógépeken és mobileszközökön.<br /><br />További információ: [Multi-factor authentication (MFA) and Azure RMS](../get-started/requirements-azure-ad.md#multi-factor-authentication-mfa-and-azure-rms) (Többtényezős hitelesítés (MFA) és az Azure RMS).|Támogatja az intelligens kártyás hitelesítést, ha az IIS konfigurálva van a tanúsítványok kérésére.|
|További konfiguráció nélkül támogatja a 2. titkosítási módot, amely nagyobb biztonságú kulcshosszokat és titkosítási algoritmusokat kínál.<br /><br />További tudnivalókért lásd a jelen cikk [Titkosítási funkciók aláíráshoz és titkosításhoz](#cryptographic-controls-for-signing-and-encryption) című szakaszát, illetve az [AD RMS Cryptographic Modes](http://go.microsoft.com/fwlink/?LinkId=266659) (Az AD RMS titkosítási módjai) című témakört.|Alapértelmezés szerint támogatja az 1. titkosítási módot, és további konfiguráció után támogatja a nagyobb biztonságot nyújtó 2. titkosítási módot.<br /><br />További tudnivalókért lásd a jelen cikk [Titkosítási funkciók aláíráshoz és titkosításhoz](#cryptographic-controls-for-signing-and-encryption) című szakaszát, illetve az [AD RMS Cryptographic Modes](http://go.microsoft.com/fwlink/?LinkId=266659) (Az AD RMS titkosítási módjai) című témakört.|
|Támogatja az AD RMS-ről, valamint szükség esetén az AD RMS-re történő áttelepítést:<br /><br />- [Áttelepítés AD RMS-ről Azure Rights Managementre](../plan-design/migrate-from-ad-rms-to-azure-rms.md)<br /><br />- [Az Azure Rights Management leszerelése és deaktiválása](../deploy-use/decommission-deactivate.md)|Támogatja az Azure RMS-ről, valamint az Azure RMS-re történő áttelepítést:<br /><br />- [Az Azure Rights Management leszerelése és deaktiválása](../deploy-use/decommission-deactivate.md)<br /><br />- [Áttelepítés AD RMS-ről Azure Rights Managementre](../plan-design/migrate-from-ad-rms-to-azure-rms.md)|
|A tartalmak védelméhez RMS-licencre van szükség. Az Azure RMS által védett (akár egy másik szervezet felhasználóitól származó) tartalmak felhasználásához nincs szükség RMS-licencre.<br /><br />További információk: [Az Azure RMS-t támogató felhőalapú előfizetések](../get-started/requirements-subscriptions.md).|A tartalmak védelméhez és az AD RMS által védett tartalmak felhasználásához RMS-licencre van szükség.<br /><br />Az AD RMS-licenceléssel kapcsolatos további általános információkat a [Client Access Licenses and Management Licenses](https://www.microsoft.com/en-us/Licensing/product-licensing/client-access-license.aspx) (Ügyféllicencek és felügyeleti licencek) című részben talál, konkrét információkért pedig lépjen kapcsolatba Microsoft-partnerével vagy Microsoft-képviselőjével.|

## Titkosítási funkciók aláíráshoz és titkosításhoz
[!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] ///a nyilvános kulcstitkosításhoz mindig RSA 2048-at, az aláírási műveletekhez pedig SHA 256-ot használ. Összehasonlításképp az AD RMS az RSA 1024 és az RSA 2048, aláírási műveletekhez pedig az SHA 1 vagy az SHA 256 használatát támogatja.

Az [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] és az AD RMS egyaránt AES 128-at használ a szimmetrikus titkosításhoz.

[!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] ///megfelel a FIPS 140-2 szabványnak, akár a Microsoft hozza létre és felügyeli a bérlőkulcsát (alapértelmezés szerint), akár a felhasználó felügyeli azt (BYOK). További információk a bérlőkulcs felügyeletéről: [Planning and implementing your Azure Rights Management tenant key](../plan-design/plan-implement-tenant-key.md) (Az Azure Rights Management-bérlőkulcs tervezése és megvalósítása).

## További lépések
Ha az AD RMS-ről Azure RMS-re szeretne áttelepítést végezni, olvassa el a következőt: [Áttelepítés AD RMS-ről Azure Rights Managementre](../plan-design/migrate-from-ad-rms-to-azure-rms.md).





<!--HONumber=Jul16_HO3-->


