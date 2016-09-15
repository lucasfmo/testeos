---
title: "Az Azure Rights Management követelményei | Azure RMS"
description: "Határozza meg az előfeltételeket, mielőtt a szervezetében üzembe helyezi a Microsoft Azure Rights Managementet (Azure RMS)."
author: cabailey
manager: mbaldwin
ms.date: 08/25/2016
ms.topic: get-started-article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: dc78321d-d759-4653-8818-80da74b6cdeb
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 81426cf43f31625c6e83d443fa925f6426eb89da
ms.openlocfilehash: 9bd75b44541f51b39315a898417ebe5d3b562cf9


---

# Az Azure Rights Management követelményei

>*A következőkre vonatkozik: Azure Rights Management, Office 365*


Mielőtt a szervezetében üzembe helyezi a Microsoft Azure Rights Managementet (Azure RMS), győződjön meg róla, hogy rendelkezik a következő előfeltételekkel. Ezután az [Azure Rights Management deployment roadmap](../plan-design/deployment-roadmap.md) (Azure Rights Management üzembe helyezési menetrend) használatával elvégezheti a Rights Management központi telepítését a szervezete számára.

|Követelmény|További információ|
|---------------|--------------------|
|RMS felhőalapú előfizetés|A szervezetének rendelkeznie kell egy, az RMS-t támogató felhőalapú előfizetéssel.<br /><br />További licencelési információk: [Az Azure RMS-t támogató felhőalapú előfizetések](requirements-subscriptions.md).|
|Azure AD-címtár|A szervezetének rendelkeznie kell egy Azure Active Directoryval, amely támogatja az RMS felhasználóhitelesítését. Emellett, ha felhasználói fiókjait a helyszíni címtárából (AD DS) kívánja használni, a címtár-integrációt is be kell állítania.<br /><br />Az Azure RMS a többtényezős hitelesítést (MFA) is támogatja, ha Ön rendelkezik a szükséges ügyfélszoftverrel és a megfelelően konfigurált, MFA-kompatibilis infrastruktúrával.<br /><br />További tudnivalók: [Azure AD-címtár](requirements-azure-ad.md).|
|Ügyféleszközök|A felhasználóknak olyan ügyféleszközzel (számítógép vagy mobileszköz) kell rendelkezniük, amely az RMS-t támogató operációs rendszert futtat.<br /><br />További tudnivalók: [Client devices that support Azure RMS](requirements-client-devices.md) (Az Azure RMS-t támogató ügyféleszközök).|
|Alkalmazások|Az ügyfeleknek az RMS-t támogató alkalmazásokat kell futtatniuk.<br /><br />További tudnivalók: [Az Azure RMS-t támogató alkalmazások](requirements-applications.md).|
|Az internethez és a függő felhőszolgáltatásokhoz való kapcsolódást támogató infrastruktúra|Ha rendelkezik olyan tűzfallal vagy hasonló beavatkozó hálózati eszközzel, amelyet be kell állítani a megadott kapcsolatok engedélyezéséhez, olvassa el [Az Office 365 URL-címei és IP-címtartományai](https://support.office.com/en-US/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2) című témakör [Office 365-portál és megosztott](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2#BKMK_Portal-identity) szakaszának **Azure Rights Management (RMS)** szolgáltatásról szóló részét.<br /><br />Az ebben az Office-cikkben szereplő útmutatások segítségével nyomon követheti az információk változását, ha feliratkozik a megfelelő RSS-hírcsatornára.<br /><br />Az Office-cikkben szereplő információkon felül az Azure RMS esetében az alábbiak is érvényesek:<br /><br />– Ne állítsa le a TLS ügyfél–szolgáltatás kapcsolatot (pl. a csomag szintjén végzett vizsgálat végrehajtásához). Ha így tenne, azzal megszüntetné a tanúsítvány rögzítését, amelyet az RMS-ügyfelek a Microsoft által felügyelt hitelesítésszolgáltatókkal együtt az Azure RMS szolgáltatással való kommunikációjuk biztosítására használnak.<br /><br />– Ha olyan webproxyt használ, amelyhez hitelesítés szükséges, akkor konfigurálnia kell az integrált Windows-hitelesítés használatára a felhasználó Active Directory bejelentkezési hitelesítési adataival.|

Ha az Azure RMS szolgáltatást helyszíni kiszolgálóval szeretné használni, az alábbi termékek támogatottak:

-   Exchange Server

-   SharePoint Server

-   Windows Server fájlkiszolgálók, amelyek támogatják a fájlbesorolási infrastruktúrát

A forgatókönyv további Azure RMS-követelményeivel kapcsolatos tudnivalókat [Az Azure RMS-t támogató helyszíni kiszolgálók](requirements-servers.md) szakaszt.

> [!IMPORTANT]
> Az alábbi telepítési forgatókönyv nem támogatott:
> 
> -   Az AD RMS és az Azure RMS párhuzamos futtatása ugyanazon a szervezeten belül, kivéve az áttelepítés idejére a [Migrating from AD RMS to Azure Rights Management](../plan-design/migrate-from-ad-rms-to-azure-rms.md) (AD RMS rendszerről Azure Rights Management rendszerre történő áttelepítés) című szakaszban leírtak szerint.
> 
> Létezik egy támogatott áttelepítési útvonal az [AD RMS rendszerről az Azure RMS rendszerre](http://technet.microsoft.com/library/Dn858447.aspx), és egy az [Azure RMS rendszerről az AD RMS rendszerre](http://msdn.microsoft.com/library/azure/dn629429.aspx). Ha telepíti az Azure RMS rendszert, majd úgy dönt, hogy már nem szeretné használni ezt a felhőszolgáltatást, tekintse meg a [Decommissioning and Deactivating Azure Rights Management](../deploy-use/decommission-deactivate.md) (Az Azure Rights Management leszerelése és inaktiválása) című szakaszt.






<!--HONumber=Aug16_HO4-->

