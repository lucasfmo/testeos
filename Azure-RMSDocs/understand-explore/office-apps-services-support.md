---
title: "Office-alkalmazások és -szolgáltatások | Azure RMS"
description: "A végfelhasználói Office-alkalmazások (például Word, Excel, PowerPoint és Outlook) és az Office-szolgáltatások (például Exchange és SharePoint) a Microsoft Azure Rights Management segítségével védelmet biztosíthatnak a szervezet adatai számára."
author: cabailey
manager: mbaldwin
ms.date: 09/06/2016
ms.topic: article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 388e67cd-c16f-4fa0-a7bb-ffe0def2be81
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: f0871436caef79187349d700d190564b08cc9e46
ms.openlocfilehash: 1e1a52e637671d857fac22c51a635e726fa99b01


---


# Office-alkalmazások és -szolgáltatások

>*A következőkre vonatkozik: Azure Rights Management, Office 365*

A végfelhasználói Office-alkalmazások (például Word, Excel, PowerPoint és Outlook) és az Office-szolgáltatások (például Exchange és SharePoint) a Microsoft Azure Rights Management segítségével védelmet biztosíthatnak a szervezet adatai számára.

## Office alkalmazások: Word, Excel, PowerPoint, Outlook
Ezek az alkalmazások natív módon támogatják a Rights Managementet a tartalomvédelmi szolgáltatás (IRM) alkalmazása révén, valamint lehetővé teszik a felhasználók számára, hogy mentett dokumentumaikat vagy elküldendő e-mail üzeneteiket védelemmel lássák el. A felhasználók sablonokat vagy a Word, Excel és PowerPoint esetében nagymértékben testre szabott beállításokat alkalmazhatnak a hozzáférési, jogosultsági, illetve használati korlátozásokhoz. 

A felhasználók például beállíthatnak egy adott Word-dokumentumot úgy, hogy az kizárólag a szervezeten belüli személyek számára legyen elérhető, vagy meghatározhatják, hogy egy Excel-számolótábla a fájl szerkeszthető vagy írásvédett legyen-e, illetve letilthatják annak kinyomtatását. Időérzékeny fájlok esetében lejárati idő adható meg (közvetlenül a felhasználó által vagy sablon alkalmazásával), amelytől kezdve a fájl már nem lesz hozzáférhető. Az Outlook-felhasználók az adatszivárgás megakadályozása érdekében a sablonválasztás mellett választhatják a **Nem továbbítandó** beállítást is.

## Az Exchange Online és az Exchange Server
Az Exchange Online vagy az Exchange Server használatakor tartalomvédelmi szolgáltatás (IRM) integrációt alkalmazhat, amelynek révén további védelmi megoldások válnak elérhetővé:

-   **Exchange ActiveSync IRM**, amelynek révén a mobileszközök képesek védelemmel ellátni, illetve fogadni védett e-mail üzeneteket.

-   Az **Outlook Web App** RMS-támogatása az Outlook-ügyfélhez hasonlóan van megvalósítva, így a felhasználók e-mail üzeneteiket sablonok vagy egyedi beállítások segítségével láthatják el védelemmel, valamint elolvashatják és használhatják a részükre elküldött, védelemmel ellátott e-mail üzeneteket.

-   **Védelmi szabályok**, amelyek esetében az Outlook-felhasználók számára a rendszergazda RMS-sablonok automatikus alkalmazását állítja be a megadott címzettekhez érkező e-mail üzenetekre. Amikor például a felhasználók belső e-maileket küldenek a jogi osztály számára, azokat kizárólag a jogi osztály tagjai tudják elolvasni, és azok nem továbbíthatók. A felhasználók elküldés előtt megtekinthetik az e-mail üzeneteik esetében alkalmazott védelmet, és eltávolíthatják azt, ha nem ítélik szükségesnek. Az e-maileket a rendszer a küldés előtt titkosítja. További információk az Exchange könyvtár [Outlook Protection Rules](https://technet.microsoft.com/library/dd638178%28v=exchg.150%29.aspx) (Outlook védelmi szabályok) és [Create an Outlook Protection Rule](https://technet.microsoft.com/library/dd638196%28v=exchg.150%29.aspx) (Outlook védelmi szabály létrehozása) című részeiben találhatók.

-   **Átviteli szabályok**, amelyek esetében a rendszergazda RMS-sablonok automatikus alkalmazását állítja be az e-mail üzenetekre, olyan tulajdonságok alapján, mint például a küldő, a címzett, az üzenet tárgya és tartalma. Ezek elvben a védelmi szabályokhoz hasonlóan működnek, az ügyfelek számára azonban nem teszik lehetővé a védelem eltávolítását, alkalmazhatóak az Outlook Web Accessre és a mobileszközökről elküldött e-mail üzenetekre, és az ügyfél részéről történő elküldést megelőzően nem titkosítják az e-mail üzeneteket. További információk az Exchange könyvtár [Create a Transport Protection Rule](https://technet.microsoft.com/library/dd302432.aspx) (Átvitel-védelmi szabály létrehozása) című részében találhatók.

-   **Adatveszteség-megelőzési (DLP) házirendek**, amelyek az e-mail üzenetek szűréséhez, valamint a bizalmas és érzékeny tartalmakhoz (például személyes vagy hitelkártya-adatokhoz) kapcsolódó adatvesztés megelőzése érdekében használatos feltételkészleteket tartalmaznak. Házirendtippek az érzékeny adatok észlelése esetén használhatók, felhívva a felhasználók figyelmét, hogy az e-mail üzenetben foglalt információk alapján adatvédelmi intézkedésre lehet szükség. További információk az Exchange könyvtár [Data Loss Prevention](https://technet.microsoft.com/library/jj150527%28v=exchg.150%29.aspx) (Adatveszteség-megelőzés) című részében találhatók.

-   **Office 365 üzenettitkosítás**, amely átviteli szabályokat használ a titkosított e-mailek elküldéséhez a vállalaton kívüli címzetteknek, az e-mailek elolvasása pedig az Outlook Web Apphez hasonló böngészőfelületen történik. A vállalat titkosított e-mailjei esetében testre szabhatja a felelősséget kizáró nyilatkozat és a fejléc szövegét, valamint a vállalat logóját is megjelenítheti. További információk az Office webhelyének [Office 365 Message Encryption](https://office.microsoft.com/o365-message-encryption-FX104179182.aspx) (Office 365-üzenetek titkosítása) című részében találhatók.

Exchange Server használata esetén az RMS-összekötő telepítésével alkalmazhatóvá válnak az [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] adatvédelmi funkciói, amely a helyszíni kiszolgálók és az RMS-felhőszolgáltatás közötti közvetítőként működik. További információk: [Deploying the Azure Rights Management connector](../deploy-use/deploy-rms-connector.md) (Az Azure Rights Management-összekötő telepítése).

## SharePoint Online és SharePoint Server
SharePoint Online vagy SharePoint Server használatakor tartalomvédelmi szolgáltatás (IRM) integrációt alkalmazhat, amelynek segítségével a rendszergazdák védelemmel láthatják el a listákat és a könyvtárakat. Így ha a felhasználó lefoglal egy dokumentumot, annak védelme biztosított, tehát kizárólag a megadott adatvédelmi házirend szerint jogosult személyek tekinthetik meg és használhatják a fájlt. A fájl például lehet írásvédett, letilthatja a szövegének másolását, helyi másolat létrehozását vagy nyomtatását.

Listák és könyvtárak esetében az adatvédelmi beállításokat mindig a rendszergazda, soha nem a végfelhasználó adja meg. Azok alkalmazása pedig az adott tároló összes dokumentumának lista- vagy könyvtárszintjén történik, nem az egyes fájlok esetében.  SharePoint Online használata esetén a felhasználók OneDrive vállalati verziójú könyvtáraikat IRM-védelemmel is elláthatják.

Először az IRM szolgáltatást engedélyezni kell a SharePointhoz. Ezt követően tartalomvédelmi szolgáltatásokat alkalmazhat az adott könyvtáron. A SharePoint Online és a OneDrive vállalati verziójának esetében a felhasználók OneDrive vállalati verziójú könyvtáraikra is alkalmazhatnak tartalomvédelmi szolgáltatásokat. A SharePoint nem használ jogmegadási sablonokat, bár egyes SharePoint konfigurációs beállítások megadása közel hasonlóan működik a sablonokban megadott beállításokhoz.

SharePoint Server használata esetén az RMS-összekötő telepítésével alkalmazhatóvá válnak az [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] adatvédelmi funkciói, amely a helyszíni kiszolgálók és az RMS-felhőszolgáltatás közötti közvetítőként működik. További információk: [Az Azure Rights Management-összekötő telepítése](../deploy-use/deploy-rms-connector.md).

> [!NOTE]
> Az IRM SharePointtal való alkalmazása esetében jelenleg bizonyos korlátozások érvényesek:
> 
> -   A klasszikus Azure-portálon kezelt, alapértelmezett vagy egyéni sablonok nem használhatók.
> -   A védett PDF-fájlokhoz tartozó, .PPDF fájlnév-kiterjesztésű fájlok nem támogatottak. A .PDF fájlnév-kiterjesztésű és natív RMS-védelemmel ellátott fájlok a natív RMS-támogatással ellátott PDF-olvasók használata esetén támogatottak.

Az Azure RMS használati korlátozásokat és adattitkosítást alkalmaz a dokumentumokra azok SharePointról történő letöltésekor, a dokumentumok SharePointban történő első létrehozásakor vagy a könyvtárba történő feltöltésekor azonban nem. A dokumentumok letöltés előtt alkalmazott védelméről a SharePoint dokumentációjának [Data Encryption in OneDrive for Business and SharePoint Online](https://technet.microsoft.com/library/dn905447.aspx) (Adattitkosítás a OneDrive vállalati verzió és a SharePoint Online esetében) fejezetében olvashat.

Az Azure RMS SharePointtal való alkalmazásáról bővebben az Office blogjának alábbi bejegyzésében olvashat: [What’s New with Information Rights Management in SharePoint and SharePoint Online](http://blogs.office.com/2012/11/09/whats-new-with-information-rights-management-in-sharepoint-and-sharepoint-online/) (A SharePoint és a SharePoint Online tartalomvédelmi szolgáltatásainak újdonságai)

## További lépések

Információk az egyéb alkalmazások és szolgáltatások Azure Rights Management-támogatásáról: [Hogyan támogatják a különböző alkalmazások az Azure Rights Managementet?](applications-support.md)


<!--HONumber=Sep16_HO1-->


