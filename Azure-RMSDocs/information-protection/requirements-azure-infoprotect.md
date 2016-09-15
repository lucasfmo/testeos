---
title: "Az Azure Information Protection használati követelményei | Azure RMS"
description: "Határozza meg a szükséges előfeltételeket, ha ki szeretné próbálni az Azure Information Protection előzetes kiadását."
author: cabailey
manager: mbaldwin
ms.date: 08/29/2016
ms.topic: get-started-article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: aa4353e5-c5b0-47f6-a6f9-87d13e8f075f
ms.reviewer: eymanor
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ba6887a5c9bab18867d07cfc98e8416bf102c211
ms.openlocfilehash: 85bed6554140525fabc1ab863e3196ac5a37366b


---

# Az Azure Information Protection használati követelményei

>*A következőkre vonatkozik: az Azure Information Protection előzetes verziója*

**[ Előzetes információ, a tartalma változhat. ]**

Ha ki szeretné próbálni az Azure Information Protection előzetes kiadását, győződjön meg arról, hogy teljesíti az alábbi előfeltételeket. 

|Követelmény|További információ|
|---------------|--------------------|
|Az Azure Rights Managementet tartalmazó Office 365-előfizetés|Például Office 365 E3, E4 vagy E5 előfizetés.<br /><br />Az előfizetési lehetőségekről további információt és az ingyenes próbaverziók hivatkozásait az Azure RMS-követelmények dokumentációjának [Office 365-előfizetések](../get-started/requirements-subscriptions.md#office-365-subscription) című szakaszában találja.|
|Azure AD-címtár|A szervezetnek rendelkeznie kell egy Azure Active Directory-címtárral, amely támogatja az Azure RMS és az Azure Information Protection felhasználóhitelesítését. Emellett, ha felhasználói fiókjait a helyszíni címtárából (AD DS) kívánja használni, a címtár-integrációt is be kell állítania.<br /><br />Az Azure RMS a többtényezős hitelesítést (MFA) is támogatja, ha Ön rendelkezik a szükséges ügyfélszoftverrel és a megfelelően konfigurált, MFA-kompatibilis infrastruktúrával.<br /><br />További információt az [Azure AD-címtár](../get-started/requirements-azure-ad.md) című témakörben talál. Az itt található, Azure RMS-re vonatkozó adatok az Azure Information Protection szolgáltatásra is érvényesek.|
|Ügyféleszközök|Az előzetes verzió a következő ügyféleszközökön támogatott:<br /><br />- Windows 10 (x86, x64)<br /><br />- Windows 8.1 (x86, x64)<br /><br />- Windows 8 (x86, x64)<br /><br />- Windows 7 SP 1 (x86, x64)<br /><br />Az adatok védelmekor használhatja ugyanazokat az Azure Rights Managementet támogató eszközöket (Windows, Mac, iOS, Android). Ezekről az eszközökről és a támogatott verziókról további információt az [Azure RMS-követelmények: Az Azure RMS-t támogató ügyféleszközök](../get-started/requirements-client-devices.md) című témakörben talál.|
|Alkalmazások|Az Azure Information Protection előzetes és általánosan rendelkezésre álló verziója is támogatja a következő Office-alkalmazásokban létrehozott fájlok és e-mailek címkézését és védelmét: **Word**, **Excel**, **PowerPoint** és **Outlook**. Az alábbi Office-csomagok támogatottak:<br /><br />- Office Professional Plus 2016<br /><br />- Office Professional Plus 2013 az 1. szervizcsomaggal<br /><br />- Office Professional Plus 2010<br /><br />Az általánosan rendelkezésre álló verzió megjelenése után a [nagyvállalati mobilitással és biztonsággal foglalkozó blogban](https://blogs.technet.microsoft.com/enterprisemobility/?product=azure-rights-management-services) közzétesszük majd az Azure Information Protection által támogatott további fájltípusokat (például PDF-, illetve hang-, videó- és képfájlok).|
|Az internethez és a függő felhőszolgáltatásokhoz való kapcsolódást támogató infrastruktúra|Ha rendelkezik olyan tűzfallal vagy hasonló beavatkozó hálózati eszközzel, amelyet be kell állítani a megadott kapcsolatok engedélyezésére, olvassa el [Az Office 365 URL-címei és IP-címtartományai](https://support.office.com/en-US/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2) című témakör [Office 365-portál és megosztott](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2#BKMK_Portal-identity) szakaszának **Azure Rights Management (RMS)** szolgáltatásról szóló részét.<br /><br />Továbbá:<br /><br />– Engedélyezze a HTTPS-forgalmat a TCP 443-as porton az **api.informationprotection.azure.com** felé.<br /><br />– Ne állítsa le a TLS ügyfél–szolgáltatás kapcsolatot (pl. a csomag szintjén végzett vizsgálat végrehajtásához). <br /><br />– Ha olyan webproxyt használ, amelyhez hitelesítés szükséges, akkor konfigurálnia kell az integrált Windows-hitelesítés használatára a felhasználó Active Directory bejelentkezési hitelesítési adataival.|

## További lépések

Ha megfelel a fenti követelményeknek, próbálja ki az Azure Information Protection konfigurálásáról és használatáról szóló, önállóan végigkövethető bemutatót: [Azure Information Protection – gyors üzembe helyezési útmutató](infoprotect-quick-start-tutorial.md).




<!--HONumber=Aug16_HO5-->

