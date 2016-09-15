---
title: "Az Azure Rights Management terminológiája | Azure RMS"
description: "Nem biztos egy, a Microsoft Azure RMS szolgáltatással összefüggésben használt szó, kifejezés vagy mozaikszó jelentésében? Itt megtalálhatja a kifejezetten az Azure RMS szolgáltatással kapcsolatos, illetve a Rights Management szolgáltatás kontextusában saját jelentéssel bíró kifejezések és rövidítések meghatározását."
author: cabailey
manager: mbaldwin
ms.date: 08/10/2016
ms.topic: get-started-article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 742877bf-26f5-40e3-b1f7-8475e7c3ce11
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: c7b194493073bcd76fa7a7d06bb31a7811e8cc3e
ms.openlocfilehash: cb30347efd062b0f1c74a029efc747d277c817f3


---

# Az Azure Rights Management terminológiája

>*A következőkre vonatkozik: Azure Rights Management, Office 365*

Nem biztos egy, a Microsoft [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] (Azure RMS) szolgáltatással összefüggésben használt szó, kifejezés vagy mozaikszó jelentésében? Itt megtalálhatja a kifejezetten az Azure RMS szolgáltatással kapcsolatos, illetve az [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] szolgáltatás kontextusában saját jelentéssel bíró kifejezések és rövidítések meghatározását.

|Kifejezés|Meghatározás|
|--------|--------------|
|AADRM|Az Azure Rights Management Windows PowerShell-moduljának neve, ami az [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] korábbi nevének nem hivatalos rövidítéséből származik, amikor a szolgáltatást még (Windows) Azure Active Directory Rights Managementnek hívták.|
|aktiválás|Az [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] szolgáltatás engedélyezése, aminek köszönhetően egy szervezet adatvédelemmel láthatja el a dokumentumait és e-mail-üzeneteit. Ez a művelet az Exchange Online-ban és a SharePoint Online-ban is engedélyezi a tartalomvédelmi funkciókat.|
|Active Directory tartalomvédelmi szolgáltatások|Gyakori rövidítése az *AD RMS*.<br /><br />Olyan Windows Server-szerepkör, amely titkosítás és házirend segítségével biztosítja a dokumentumok, fájlok és e-mailek adatvédelmét.|
|AD RMS|Lásd: *Active Directory tartalomvédelmi szolgáltatások*|
|Azure Information Protection|A jelenleg előzetes verzióban elérhető szolgáltatás besorolással, címkézéssel és védelemmel biztosítja a dokumentumok és e-mailek biztonságát. Az Azure Rights Management titkosítási, identitási és engedélyezési szabályzatok segítségével szolgáltatja a megfelelő védelmet.|
|Azure Rights Management|Gyakori rövidítése az *Azure RMS*.<br /><br />Olyan Azure-szolgáltatás, amely titkosítás és házirend segítségével biztosítja a dokumentumok, fájlok és e-mailek adatvédelmét.  Más néven: *Azure Rights Management szolgáltatás*. Korábbi nevén:<br /><br />- *Windows Azure Active Directory Rights Management:* Gyakori rövidítése a Windows Azure AD Rights Management szolgáltatás.<br /><br />- *RMS Online:* Az eredetileg javasolt név, amely esetenként hibaüzenetekben és naplófájlbejegyzésekben jelenik meg.|
|Azure RMS|Lásd: *Azure Rights Management*|
|BYOK|Lásd: *saját kulcs használata*.|
|saját kulcs használata|Gyakori rövidítése a *BYOK*.<br /><br />Olyan szervezetek által választott konfigurációs és topológiabeállítás, amelyek saját kezűleg szeretnék létrehozni és felügyelni az [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] szolgáltatáshoz tartozó bérlőkulcsukat.|
|tartalomkulcs|Az RMS-kompatibilis alkalmazások által létrehozott egyedi kulcs, ami a [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] használatával védett egyes dokumentumokhoz vagy e-mailekhez tartozik, és hozzájárul az információfelfedés kockázatának csökkentéséhez.|
|felhasználás|Egy fájl zárolásának feloldása olvasásra vagy használatra, ha a fájl [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)]-védelemmel van ellátva.|
|inaktiválás|A tartalomvédelmi szolgáltatás letiltása, hogy a szervezet többé ne használhassa az [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] szolgáltatást.|
|részlegszintű sablon|Olyan, az ügyfél által létrehozott jogmegadási sablon (egyéni sablon), amely a konfigurációjából fakadóan csak bizonyos felhasználók (nem pedig a szervezet összes felhasználója) számára látható.|
|kompatibilis alkalmazások|A tartalomvédelmet natív módon támogató alkalmazások, többek között olyan Office-alkalmazások, mint például a Word és az Excel. A független szoftverszállítók (ISV-k) és fejlesztők is írhatnak a [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] szolgáltatást natív módon támogató alkalmazásokat.|
|vállalati szintű tartalomvédelem|Iparági szabványnak megfelelő, általános kifejezés, amelyet olyan termékekre és megoldásokra használnak, amelyek a szervezetek számára lehetővé teszik a bizalmas vagy értékes információk titkosítási és házirend-alapú engedélyezési eszközök együttes alkalmazásával történő védelmét. A Microsoft Rights Management például egy vállalati szintű tartalomvédelmi (ERM) megoldás.|
|ERM|Lásd: *vállalati szintű tartalomvédelem*.|
|általános védelem|A védelem olyan szintje, amely bármilyen fájltípust titkosít, és meggátolja a jogosulatlan személyeket a fájl megnyitásában. A fájl a megnyitás után titkosítatlan, és használható a [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] szolgáltatást natív módon támogató alkalmazásban.|
|HYOK|Lásd: *saját tulajdonú kulcs*.|
|saját tulajdonú kulcs|Gyakori rövidítése a *HYOK* (hold your own key).<br /><br />Olyan szervezetek által választott konfigurációs és topológiabeállítás, amelyek saját kezűleg szeretnék létrehozni és a helyszínen tárolni a kulcsot, általában szabályozási vagy megfelelőségi előírások miatt.|
|adatvédelem|Időnként előforduló rövidítése az *IP*.<br /><br />Iparági szabványnak megfelelő, általános kifejezés, amely az adatok és fájlok jogosulatlan hozzáférés elleni védelmére vonatkozik, ami azután is érvényes, hogy e-mail vagy megosztás útján az adatok és fájlok a szervezet határain kívülre kerülnek. A Microsoft Rights Management például egy adatvédelmi (IP) megoldás.|
|Tartalomvédelmi szolgáltatás|Gyakori rövidítése az *IRM*.<br /><br />Office-szolgáltatásokkal (pl. Exchange-kiszolgáló, Word és SharePoint Online) kapcsolatban használt kifejezés, amely a tartalomvédelem támogatásának képességére utal.|
|IRM|Lásd: *tartalomvédelmi szolgáltatás*.|
|MSDRM|Esetenként előforduló utalás az RMS-ügyfél 1.0-s verziójára, amelyet már az újabb RMS-ügyfél, az MSIPC váltott le. A régebbi ügyfél támogatja az RMS SDK 1.0-val fejlesztett alkalmazások, illetve az Office 2010 és Office 2007, az Exchange 2010 és Exchange 2013, valamint a SharePoint 2010 és SharePoint 2007 szoftverek használatát.|
|MSIPC|Esetenként előforduló utalás az RMS-ügyfél 2.0-s verziójára, amely a régebbi RMS-ügyfelet, az MSIPC-t váltotta le. Az újabb ügyfél támogatja az RMS SDK 2.0-val fejlesztett alkalmazások, illetve az Office 2016, az Office 2013 és a SharePoint 2013 szoftverek, valamint az RMS megosztóalkalkalmazás használatát.|
|natív védelem|A védelem olyan, minden kompatibilis alkalmazásban elérhető szintje, amely megakadályozza a fájlok jogosulatlan személyek általi megnyitását, emellett szigorúbb házirendek (például írásvédett és nem nyomtatható) érvényesítését teszi lehetővé. Továbbá ez a védelem akkor sem szűnik meg, ha a fájlt más személyeknek továbbítják, vagy mások számára hozzáférhető nyilvános helyre mentik.|
|.pfile|Az összes olyan fájlhoz tartozó fájlnévkiterjesztés, amelyek számára a tartalomvédelem általános védelmet nyújt.|
|.ppdf|A tartalomvédelem által létrehozott fájlnévkiterjesztés, amelyet a szolgáltatás egy e-mailben megosztott fájl (Word, Excel, PowerPoint vagy PDF) PDF-másolatának készítésekor automatikusan hoz létre, hogy a fájl minden eszközön olvasható (de nem szerkeszthető) legyen.|
|jogosultsági szint|A használati jogosultságok olyan logikus csoportosítása, amely a végfelhasználók és rendszergazdák számára megkönnyíti a szerepköralapú konfigurációs beállítások kiválasztását. Például: Felülvizsgáló és Társszerző.|
|védelem|Tartalomvédelmi vezérlők alkalmazása fájlokon vagy e-mail-üzeneteken titkosítási, identitás- és hozzáférés-vezérlési házirendek segítségével az adatok védelme érdekében.|
|közzététel|A fájlok jogosulatlan hozzáférések és használat elleni védelme.|
|Rights Management-összekötő|Kimenőproxy-továbbító, amely a helyszíni szolgáltatásokra (pl. Exchange-kiszolgáló és SharePoint) telepítve az Azure Rights Management használatával megvalósított adatvédelemre szolgál.|
|Rights Management services (Tartalomvédelmi szolgáltatások)|Általános kifejezés, amely egyaránt vonatkozik a [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] ([!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)]) felhőalapú és a [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] (AD RMS) helyszíni verzióira.|
|Rights Management megosztóalkalmazás:|Egy opcionálisan letölthető alkalmazás Windows rendszerre és a legnépszerűbb mobileszközökre, amely támogatja a helyi és e-mailben történő biztonságos fájlmegosztást.|
|RMS|Lásd: *Tartalomvédelmi szolgáltatások*|
|RMS-összekötő|Lásd: *Rights Management-összekötő*.|
|RMS egyéni felhasználók számára|Ingyenes [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)]-verzió az Office 365- vagy Azure Active Directory-előfizetéssel nem rendelkező szervezetek felhasználói számára.|
|RMS-megosztóalkalmazás|Lásd: *Rights Management megosztóalkalmazás*|
|felügyelő|Messzemenően megbízható rendszergazdák csoportja, akik visszafejthetik és hozzáférhetnek azokhoz a fájlokhoz, amelyeket a szervezet tartalomvédelemmel látott el. Általában ez a szintű hozzáférés szükséges a jogi adatfeltáráshoz és a naplózási csapatok számára.|
|bérlőkulcs|Más néven kiszolgálólicenc-tanúsítványnak (SLC-kulcsnak) is nevezzük.<br /><br />A szervezethez tartozó egyedi kulcs, amely végső soron biztosítja az ehhez a bérlőkulcshoz kapcsolódó összes [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] titkosítási funkciót.|
|védelem feloldása|A tartalomvédelmi vezérlők eltávolítása olyan fájlokról vagy e-mail-üzenetekről, amelyeken az adatok védelme érdekében titkosítási, identitás- és hozzáférés-vezérlési házirendeket alkalmaztak.|
|használati licenc|A [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] szolgáltatással védett fájlt vagy e-mail-üzenetet megnyitó felhasználó számára biztosított, adott dokumentumra vonatkozó tanúsítvány. A tanúsítvány az adott felhasználó a fájlra vagy e-mail-üzenetre vonatkozó jogosultságait, a tartalom titkosításához használt titkosítási kulcsot, valamint a dokumentum házirendjében meghatározott további hozzáférési korlátozásokat tartalmazza.|






<!--HONumber=Aug16_HO4-->


