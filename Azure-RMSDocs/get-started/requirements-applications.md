---
title: "Azure RMS-követelmények&#58; Alkalmazások | Azure RMS"
description: 
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 06/17/2016
ms.topic: get-started-article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 7b33bcb8-63da-46be-ad56-b06de97822fa
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: bb152f428c8e0b9a065035aaad2de6353265a562
ms.openlocfilehash: 61d18747011435773e16b3c8d2a8ac2104997484


---


# Azure RMS-követelmények: Alkalmazások

*A következőkre vonatkozik: Azure Rights Management, Office 365*


Az alábbi táblázat segítségével azonosíthatja a natív Azure RMS-támogatással rendelkező alkalmazásokat. Ez azt jelenti, hogy az RMS az RMS API-k használatával szorosan integrálva van az alkalmazásokba a használat korlátozása érdekében. Ezek az alkalmazások RMS-hez felkészített alkalmazásokként is ismertek.

Amennyiben másként nincs feltüntetve, a támogatott képességek az Azure RMS és az AD RMS esetében egyaránt érvényesek. Emellett az AD RMS támogatásához az iOS, Android, OS X és Windows Phone 8.1 rendszereken az [Active Directory Rights Management Services mobileszköz-bővítmény](https://technet.microsoft.com/library/dn673574.aspx) szükséges.

A táblázat oszlopaira vonatkozó információk:

-   **Védett PDF**: Olyan fájlok, amelyek a .ppdf fájlnévkiterjesztéssel rendelkeznek, vagy amelyek az Office- és PDF-fájlok e-mailben történő megosztása céljából jönnek létre automatikusan az RMS-megosztóalkalmazás használatával. Az RMS-megosztóalkalmazás tartalmaz egy olvasót a védett PDF-fájlokhoz. Korábban, az Azure RMS vagy AD RMS által védett PDF-fájlok létrehozása után ezeket a fájlokat a Foxit Reader vagy a Nitro Pro segítségével továbbra is olvashatta Windows, iOS vagy Android rendszerű eszközökön.

-   **E-mail:** A felsorolt levelezési ügyfelek képesek védelmet biztosítani magának az e-mail üzenetnek, amely a csatolt fájlokat is automatikusan védelemmel látja el. Ebben a forgatókönyvben az ügyfél előnézeti funkciója meg tudja jeleníteni a védett tartalmat (az üzentet és a mellékletet) a jogosult címzettek számára. Ha azonban maga az e-mail üzent nem védett, de a melléklet igen, az ügyfél előnézeti funkciója nem tudja megjeleníteni a védett mellékletet a jogosult címzettek számára.

-   **Egyéb fájltípusok**: A .txt, .xml, .jpg és .jpeg fájlnévkiterjesztéssel rendelkező szöveg- és képfájlok. Miután az RMS natív védelmet biztosít a fájlok számára, megváltozik a fájlnévkiterjesztésük, és csak olvashatóvá válnak. Az olyan fájlok, amelyeket nem lehet natív védelemmel ellátni, .pfile fájlnévkiterjesztést kapnak, miután az RMS általános védelmet biztosít számukra. További információk: [Rights Management sharing application administrator guide](../rms-client/sharing-app-admin-guide.md) (A Rights Management megosztóalkalmazás rendszergazdai kézikönyve).


|**Eszköz operációs rendszere**|Word, Excel, PowerPoint|Védett PDF|E-mail|Egyéb fájltípusok|
|-------------------------------|---------------------------|-----------------|---------|--------------------|
|**Windows**|Office 2010<br /><br />Office 2013<br /><br />Office 2016 <br /><br />Office-mobilealkalmazások (csak az Azure RMS esetében) [[1]](#footnote-1)<br /><br />Office Online [[2]](#footnote-2)|Gaaiho Doc<br /><br />GigaTrust asztali Adobe PDF-ügyfél<br /><br />Foxit Reader<br /><br />Nitro PDF-olvasó<br /><br />RMS-megosztóalkalmazás|Outlook 2010<br /><br />Outlook 2013<br /><br />Office 2016 <br /><br />Outlook Web App (OWA) [[3]](#footnote-3)<br /><br />Windows Posta [[4]](#footnote-4)|Windows RMS-megosztóalkalmazás: szöveg, kép, védett fájl<br /><br />Siemens JT2Go: JT-fájlok (csak Windows 10 esetén)|
|**iOS**|iPad és iPhone Office [[5]](#footnote-5)<br /><br />Office Online [[2]](#footnote-2)<br /><br />TITUS Docs|Foxit Reader<br /><br />RMS-meosztóalkalmazás [[1]](#footnote-1)<br /><br />TITUS Docs|Citrix WorxMail [[6]](#footnote-6)<br /><br />NitroDesk [[4]](#footnote-4)<br /><br />iPad és iPhone Outlook [[4]](#footnote-4)<br /><br />iOS OWA [[3]](#footnote-3)<br /><br />TITUS Mail|RMS-megosztóalkalmazás [[1]](#footnote-1): szöveg, képek, védett fájl<br /><br />TITUS Docs: védett fájl|
|**Android**|Android rendszerhez készült GigaTrust alkalmazás<br /><br />Office Online [[2]](#footnote-2)|Android rendszerhez készült GigaTrust alkalmazás<br /><br />Foxit Reader<br /><br />RMS-meosztóalkalmazás [[1]](#footnote-1)|9Folders [[4]](#footnote-4)<br /><br />Android rendszerhez készült GigaTrust alkalmazás [[4]](#footnote-4)<br /><br />Citrix WorxMail [[6]](#footnote-6)<br /><br />NitroDesk [[4]](#footnote-4)<br /><br />Outlook Android rendszerhez [[4]](#footnote-4)<br /><br />Android OWA [[3]](#footnote-3) és [[7]](#footnote-7)<br /><br />Samsung e-mail alkalmazás (S3 vagy újabb) [[7]](#footnote-7)<br /><br />TITUS Classification mobileszközökhöz|RMS-megosztóalkalmazás [[1]](#footnote-1): szöveg, képek, védett fájl|
|**OS X**|Office 2011 (csak AD RMS esetén)<br /><br />Mac Office 2016<br /><br />Office Online [[2]](#footnote-2)|Foxit Reader<br /><br />RMS-meosztóalkalmazás [[1]](#footnote-1)|Outlook 2011 (csak AD RMS esetén)<br /><br />Mac Outlook 2016<br /><br />Mac Outlook|RMS-megosztóalkalmazás [[1]](#footnote-1): szöveg, képek, védett fájl|
|**Windows 10 mobil verzió**|Office Mobile-alkalmazások (csak az Azure RMS esetében)[[1]](#footnote-1)|Nem támogatott|Citrix WorxMail [[6]](#footnote-6)<br /><br />Outlook Posta|Nem támogatott|
|**Windows RT**|Office 2013 RT<br /><br />Office Online [[2]](#footnote-2)|Nem támogatott|Outlook 2013 RT<br /><br />A Posta alkalmazás a Windowsban<br /><br />Windows Posta [[4]](#footnote-4)|Siemens JT2Go: JT-fájlok|
|**Windows Phone 8.1**|Office Mobile (csak AD RMS esetén)|RMS-meosztóalkalmazás [[1]](#footnote-1)|Outlook Mobile [[4]](#footnote-4)|RMS-megosztóalkalmazás [[1]](#footnote-1): szöveg, képek, védett fájl|
|**Blackberry 10**|Nem támogatott|Nem támogatott|Blackberry e-mail-alkalmazás [[4]](#footnote-4)|Nem támogatott|


###### 1. lábjegyzet
Támogatja a védett tartalmak megtekintését.

###### 2. lábjegyzet 
Támogatja a védett tartalmak megtekintését a SharePoint Online, a OneDrive Vállalati verzió és az Outlook Web Access esetében.

###### 3. lábjegyzet
Ha egy helyszíni Exchange-postaládával rendelkező címzett védett e-mailt kap, akkor a tartalmát csak e-mail ügyfélprogram, pl. az Outlook segítségével lehet megnyitni.  Ez a tartalom az nem nyitható meg az Outlook Web Access felületéről.

###### 4. lábjegyzet
Exchange ActiveSync IRM szolgáltatást használ, amelyet az Exchange-rendszergazdának kell engedélyeznie. A felhasználók a védett e-mail üzenetek esetében használhatják a megtekintés, válasz és válasz mindenkinek funkciókat, de maguk nem láthatják el védelemmel az új üzeneteket.

Ha egy helyszíni Exchange-postaládával rendelkező címzett védett e-mailt kap egy másik, Exchange szolgáltatást használó szervezettől, akkor a tartalmát csak email ügyfélprogram, pl. az Outlook segítségével lehet megnyitni.  Ez a tartalom nem nyitható meg az Exchange Active Sync IRM szolgáltatást használó eszközökön.

###### 5. lábjegyzet
Támogatja a védett dokumentumok megtekintését és szerkesztését. További információért tekintse meg az Office blog következő bejegyzését: [Azure Rights Management support comes to Office for iPad and iPhone](https://blogs.office.com/2015/07/22/azure-rights-management-support-comes-to-office-for-ipad-and-iphone-2/) (Az Azure Rights Management támogatás hamarosan az iPad és iPhone Office esetében is elérhető)

###### 6. lábjegyzet
További információért tekintse meg a Citrix [WorxMail termékdokumentációját](http://docs.citrix.com/en-us/worx-mobile-apps/10/xmob-worx-mail.html).

###### 7. lábjegyzet
További információért tekintse meg az Office blog következő bejegyzését: [OWA for Android now available on select devices](http://blogs.office.com/2014/06/11/owa-for-android-now-available-on-select-devices/) (Az Android OWA bizonyos eszközökön mostantól elérhető)

## További információk az Azure RMS Office-támogatásáról

Az Azure RMS szorosan be van építve a Word, Excel, PowerPoint és az Outlook alkalmazásokba, ahol erre a funkcióra gyakran hivatkoznak úgy, mint az adatok tartalomvédelmére (IRM). A következő Office-ügyfélverziók támogatják a fájlok és e-mailek Azure RMS segítségével történő védelmét:

- Office Professional Plus 2016

- Office Professional Plus 2013

- Office Professional Plus 2010

Az Office összes kiadása (az Office 2007 kivételével) támogatja a védett tartalmak felhasználását.

Azure RMS és Office Professional Plus 2010 vagy Office Professional 2010:

- A Windows Rights Management megosztóalkalmazást igényli

- Nem támogatott a Windows 10 esetében


## További információk a Rights Management megosztóalkalmazásról

További információkat a Rights Management megosztóalkalmazásról az alábbi forrásanyagokban talál:

-   [Rendszergazdai útmutató a Rights Management megosztóalkalmazáshoz](../rms-client/sharing-app-admin-guide.md)

-   [A Rights Management megosztóalkalmazás felhasználói útmutatója](../rms-client/sharing-app-user-guide.md)

További információkat a Rights Management megosztóalkalmazás mobilplatformokra kiadott verziójáról az alábbi forrásanyagokban talál:

-   Töltse le a megfelelő alkalmazást a [Microsoft Rights Management oldalon](http://go.microsoft.com/fwlink/?LinkId=303970) található hivatkozások használatával

-   Ha rendelkezik Microsoft Intune-nal, az alkalmazás telepítését és kezelését elvégezheti egy házirend által kezelt alkalmazással: 

    -   Az Intune által regisztrált iOS- és Android-eszközök esetén: [Configure and deploy mobile application management policies in the Microsoft Intune console](/intune/deploy-use/configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console) (Adatok védelme mobilalkalmazás-kezelési házirendekkel a Microsoft Intune segítségével)

    -   A nem az Intune által regisztrált Android-eszközök esetén: [Create and deploy mobile app management policies with Microsoft Intune](/intune/deploy-use/create-and-deploy-mobile-app-management-policies-with-microsoft-intune) (Mobilalkalmazás-felügyeleti szabályzatok létrehozása és telepítése Microsoft Intune-ban)

-   [A Microsoft Rights Management megosztóalkalmazás mobilplatformokra kiadott verziójával kapcsolatos gyakori kérdések](https://technet.microsoft.com/dn451248)



## További információ az Azure RMS-t támogató egyéb alkalmazásokról

A táblázatban szereplő alkalmazásokon kívül bármely olyan alkalmazás integrálható az Azure RMS-sel, amely támogatja az RMS API-kat, beleértve a következőket:

- Belső fejlesztésű, RMS SDK használatával írt üzletági alkalmazások

- RMS SDK használatával írt, szoftverszállítóktól származó alkalmazások

További információ az SDK-val kapcsolatban: [Microsoft Rights Management SDK](../develop/developers-guide.md).

## Az Azure RMS által nem támogatott alkalmazások

Az Azure RMS által jelenleg nem támogatott alkalmazások közé tartoznak a következők:

-   Mac Microsoft Office 2011

-   Microsoft OneDrive Vállalati verzió SharePoint Server 2013 rendszerre

-   XPS-megjelenítő
 
Emellett az RMS-megosztóalkalmazás az alábbi korlátozásokkal rendelkezik:

-   Windows rendszerű számítógépek esetében: legalább Windows 7 SP 1 rendszert igényel



## További lépések
Az egyéb követelményeket [Az Azure Rights Management követelményei](requirements-azure-rms.md) című témakörben tekintheti meg.

További információk arról, hogy hogyan támogatják a leggyakrabban használt alkalmazások az Azure RMS-t: [How applications support Azure Rights Management](../understand-explore/applications-support.md) (Hogyan támogatják a különböző alkalmazások az Azure Rights Managementet?).

Információk arról, hogy hogyan konfigurálhatja a leggyakrabban használt alkalmazásokat az Azure RMS-hez: [Configuring applications for Azure Rights Management](../deploy-use/configure-applications.md) (Alkalmazások konfigurálása az Azure Rights Managementhez).


<!--HONumber=Jun16_HO4-->


