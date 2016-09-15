---
title: "Az Azure Rights Management-összekötő központi telepítése | Azure RMS"
description: "Információ az Azure Rights Management- (RMS-) összekötő telepítéséről, amely adatvédelmet biztosít a Microsoft Exchange Servert, Microsoft SharePoint Servert vagy Windows Servert és a Fájlkiszolgálói erőforrás-kezelő Fájlbesorolási infrastruktúra (FCI) képességét használó fájlkiszolgálókat használó meglévő helyszíni telepítéseknek."
author: cabailey
manager: mbaldwin
ms.date: 08/25/2016
ms.topic: article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 90e7e33f-9ecc-497b-89c5-09205ffc5066
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ad32910b482ca9d92b4ac8f3f123eda195db29cd
ms.openlocfilehash: 7569a53f035e3333ee7ee00cb83b83b3126a6eb1


---

# Deploying the Azure Rights Management connector (Az Azure Rights Management-összekötő üzembe helyezése)

>*A következőkre vonatkozik: Azure Rights Management, Windows Server 2012, Windows Server 2012 R2*

Ezzel az információval és útmutatóval telepítheti Az Azure Rights Management (RMS)-összekötőt. Ez az összekötő adatvédelmet biztosít a Microsoft Exchange Servert, Microsoft SharePoint Servert vagy Windows Servert és a Fájlkiszolgálói erőforrás-kezelő Fájlbesorolási infrastruktúra (FCI) képességét használó fájlkiszolgálókat használó meglévő helyszíni telepítéseknek.

> [!TIP]
> Képernyőképeket tartalmazó magas szintű példáért olvassa el [Az Azure RMS működés közben](../understand-explore/what-admins-users-see.md) című cikk [Fájlok automatikus védelme a Windows Server rendszert és a Fájlbesorolási infrastruktúrát futtató fájlkiszolgálókon](../understand-explore/what-admins-users-see.md#automatically-protecting-files-on-file-servers-running-windows-server-and-file-classification-infrastructure) szakaszát.

## A Microsoft Rights Management-összekötő áttekintése
A Microsoft Rights Management- (RMS-) összekötő segítségével gyorsan engedélyezheti a helyszíni kiszolgálók számára a tartalomvédelmi szolgáltatások (IRM) használatát a felhőalapú Microsoft Rights Management szolgáltatással (Azure RMS). Ezzel a funkcióval az informatikai részleg és a felhasználók egyszerűen védhetik a dokumentumokat és a képeket a szervezeten belül és kívül is, és nem kell további infrastruktúrát üzembe helyezniük, vagy megbízhatósági kapcsolatot létesíteniük más szervezetekkel. 

Akkor is használhatja ezt az összekötőt, ha a felhasználói egy része online szolgáltatásokhoz csatlakozik egy hibrid forgatókönyvben. Vegyük például, hogy a felhasználók egy részének postafiókja Exchange Online-t, egy másik részének postafiókja pedig Exchange Servert használ. Az RMS-összekötő telepítése után az összes felhasználó védheti és használhatja az e-maileket és a mellékleteket az Azure RMS segítségével, és az adatvédelem hibátlanul működik a két telepítési konfiguráció között.

Az RMS-összekötő egy kis erőforrásigénnyel rendelkező szolgáltatás, amely Windows Server 2012 R2, Windows Server 2012 vagy Windows Server 2008 R2 rendszert futtató helyszíni kiszolgálókon telepíthető. Az összekötőt fizikai számítógépeken kívül futtathatja virtuális gépeken is, beleértve az Azure IaaS virtuális gépeket. Az összekötő a telepítés és a konfigurálás után úgy működik, mint egy kommunikációs interfész (továbbító) a helyszíni kiszolgálók és a felhőszolgáltatás között.

Ha saját bérlőkulcsa van az Azure RMS-hez („saját kulcs használata” vagy BYOK-forgatókönyv), az RMS-összekötő és az azt használó helyszíni kiszolgálók nem férnek hozzá a biztonsági kulcsot tartalmazó hardveres biztonsági modulhoz (HSM). Ennek az az oka, hogy az összes bérlőkulcsot használó kriptográfiai művelet az Azure RMS-en, és nem a helyszíni kiszolgálókon zajlik.

![Az RMS-összekötő architektúrájának áttekintése](../media/RMS_connector.png)

Az RMS-összekötő az alábbi helyszíni kiszolgálókat támogatja: az Exchange Server, a SharePoint Server, valamint a Windows Servert futtató és egy mappa Office-dokumentumainak besorolásához és a vonatkozó házirendek alkalmazásához fájlbesorolási infrastruktúrát (FCI) használó fájlkiszolgálók. Ha az összes fájlt a fájlbesorolási infrastruktúra segítségével szeretné védeni, ne használja az RMS-összekötőt. Helyette [tartalomvédelmi parancsmagokat](https://msdn.microsoft.com/library/azure/mt433195.aspx) használjon.

> [!NOTE]
> Ezen helyszíni kiszolgálók támogatott verzióiért lásd: [Az Azure RMS-t támogató helyszíni kiszolgálók](..\get-started\requirements-servers.md).

Az RMS-összekötő tervezésekor, telepítésekor és konfigurálásakor vegye figyelembe a következőkben leírtakat. A folyamat befejezése után el kell végeznie a telepítés utáni konfigurálást, hogy a kiszolgálói használhassák az összekötőt.

-   [Az RMS-összekötő előfeltételei](deploy-rms-connector.md#prerequisites-for-the-rms-connector)

-   **1. lépés:** [Az RMS-összekötő telepítése](install-configure-rms-connector.md#installing-the-rms-connector)

-   **2. lépés:** [Hitelesítő adatok megadása](install-configure-rms-connector.md#entering-credentials)

-   **3. lépés:** [Az RMS-összekötő használatának engedélyezése a kiszolgálók számára](install-configure-rms-connector.md#authorizing-servers-to-use-the-rms-connector)

-   **4. lépés:** [Terheléselosztás és magas rendelkezésre állás konfigurálása](install-configure-rms-connector.md#configuring-load-balancing-and-high-availability)

-   Opcionális: [Az RMS-összekötő konfigurálása HTTPS használatára](install-configure-rms-connector.md#configuring-the-rms-connector-to-use-https)

-   Opcionális: [RMS-összekötő konfigurálása webes proxykiszolgáló számára](install-configure-rms-connector.md#configuring-the-rms-connector-for-a-web-proxy-server)

-   Opcionális: [Az RMS-összekötőfelügyelő eszköz telepítése rendszergazdai számítógépeken](install-configure-rms-connector.md#installing-the-rms-connector-administration-tool-on-administrative-computers)

-   **5. lépés:** [A kiszolgálók konfigurálása az RMS-összekötő használatára](configure-servers-rms-connector.md)

    -   [Exchange-kiszolgáló konfigurálása az összekötő használatára](configure-servers-rms-connector.md#configuring-an-exchange-server-to-use-the-connector)

    -   [SharePoint-kiszolgáló konfigurálása az összekötő használatára](configure-servers-rms-connector.md#configuring-a-sharepoint-server-to-use-the-connector)

    -   [Fájlbesorolási infrastruktúrát használó fájlkiszolgáló konfigurálása az összekötő használatára](configure-servers-rms-connector.md#configuring-a-file-server-for-file-classification-infrastructure-to-use-the-connector)


## Az RMS-összekötő előfeltételei
Az RMS-összekötő telepítése előtt ellenőrizze, hogy az alábbi követelmények teljesülnek-e.

|Követelmény|További információ|
|---------------|--------------------|
|A Rights Management szolgáltatás (RMS) aktiválása megtörtént|[Az Azure Rights Management aktiválása](activate-service.md)|
|Címtár-szinkronizálás a helyszíni Active Directory-erdők és az Azure Active Directory között|Az RMS aktiválása után az Azure Active Directoryt úgy kell konfigurálni, hogy az Active Directory-adatbázisban található felhasználókat és csoportokat használja.<br /><br />**Fontos:**: Ezt a címtár-szinkronizálási lépést akkor is el kell végeznie az RMS-összekötő működéséhez, ha csak egy teszthálózatot használ. Noha az Office 365 és az Azure Active Directoryt használhatja az Azure Active Directoryban manuálisan létrehozott fiókokkal, ennél az összekötőnél követelmény az Azure Active Directory-fiókjainak szinkronizálása az Active Directory tartományi szolgáltatásokkal. A manuális jelszó-szinkronizálás nem elegendő.<br /><br />További információkért lásd a következőket:<br /><br />[Helyszíni identitások integrálása az Azure Active Directoryval](/active-directory/active-directory-aadconnect)<br /><br />[Hibrid identitás: a címtár-integrációs eszközök összehasonlítása](/active-directory/active-directory-hybrid-identity-design-considerations-tools-comparison)|
|Nem kötelező, de ajánlott:<br /><br />Összevonás engedélyezése a helyszíni Active Directory és az Azure Active Directory között|Engedélyezheti az identitás-összevonást a helyszíni címtár és az Azure Active Directory között. Ez a konfiguráció zökkenőmentesebb felhasználói élményt tesz lehetővé az RMS szolgáltatásra való egyszeri bejelentkezés engedélyezése révén. Ha nem érhető el az egyszeri bejelentkezés, a felhasználóktól a rendszer bekéri a hitelesítő adataikat a tartalomvédett tartalmak használata előtt.<br /><br />Az Active Directory tartományi szolgáltatások és az Azure Active Directory közötti összevonás Active Directory összevonási szolgáltatásokkal (AD FS) való konfigurálásához a Windows Server-könyvtár [Ellenőrzőlista: Az egyszeri bejelentkezés megvalósítása és kezelése az AD FS-sel](http://technet.microsoft.com/library/jj205462.aspx) című cikkében talál útmutatást.|
|Legalább két tagszámítógép az RMS-összekötő telepítéséhez:<br /><br />– Egy 64 bites fizikai vagy virtuális számítógép, amely az alábbi operációs rendszerek egyikét futtatja: Windows Server 2012 R2, Windows Server 2012 vagy Windows Server 2008 R2.<br /><br />– Legalább 1 GB RAM.<br /><br />– Legalább 64 GB szabad lemezterület.<br /><br />– Legalább egy hálózati csatoló.<br /><br />– Internet-hozzáférés hitelesítést nem igénylő tűzfalon (vagy webproxyn) keresztül.<br /><br />– Egy olyan erdőben vagy tartományban kell lenniük, amely megbízhatósági kapcsolatban áll a szervezet más, az RMS-összekötővel használni kívánt, Exchange- vagy SharePoint-kiszolgálók telepítéseit tartalmazó erdőivel.|A hibatűrés és a magas szintű rendelkezésre állás érdekében legalább két számítógépre telepítenie kell az RMS-összekötőt.<br /><br />**Tipp:** Ha az Outlook Web Accesst, vagy Exchange ActiveSync IRM-et használó mobileszközöket használ, és fontos, hogy továbbra is hozzáférjen az Azure RMS által védett e-mailekhez és mellékletekhez, javasoljuk, hogy telepítsen egy terheléselosztással rendelkező összekötőkiszolgáló-csoportot a magas szintű rendelkezésre állás biztosítása érdekében.<br /><br />Az összekötő futtatásához nincs szükség dedikált kiszolgálókra, de nem telepítheti ugyanarra a számítógépre, ahol az összekötőt használó kiszolgálók vannak.<br /><br />**Fontos:** Ne telepítse az összekötőt Exchange Servert, SharePoint Servert vagy fájlbesorolási infrastruktúrához konfigurált fájlkiszolgálót futtató számítógépre, ha ezen szolgáltatások funkcióit szeretné az Azure RMS-sel használni. Emellett ne telepítse ezt az összekötőt tartományvezérlőkre.|

## További lépések

Olvassa el a következőt: [Az Azure Rights Management-összekötő telepítése és konfigurálása](install-configure-rms-connector.md).


<!--HONumber=Aug16_HO4-->


