---
title: "Forgatókönyv – A SharePointban tárolt dokumentumok feletti ellenőrzés megtartása | Azure RMS"
description: "Ez a forgatókönyv és a kiegészítő felhasználói dokumentáció az Azure Rights Management használatával biztosítja a SharePointban tárolt Office-dokumentumok feletti ellenőrzés megtartását védett könyvtárak segítségével."
author: cabailey
manager: mbaldwin
ms.date: 08/25/2016
ms.topic: get-started-article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 1b6244c7-5ab9-4881-bc8f-6fa960390d89
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 81426cf43f31625c6e83d443fa925f6426eb89da
ms.openlocfilehash: 048eafc41dcd03c708dca5befbef4e4b9e7113c4


---

# Forgatókönyv – A SharePointban tárolt dokumentumok feletti ellenőrzés megtartása

>*A következőkre vonatkozik: Azure Rights Management, Office 365*

Ez a forgatókönyv és a kiegészítő felhasználói dokumentáció az Azure Rights Management használatával biztosítja a SharePointban tárolt Office-dokumentumok feletti ellenőrzés megtartását védett könyvtárak segítségével. A dokumentumok például automatikus védelmet élveznek a felhasználók általi véletlen vagy szándékos kiszivárogtatással szemben, a tartalmakhoz való hozzáférést pedig azok letöltését vagy szinkronizálását követően is letilthatja. A védelemmel ellátni kívánt fájlok a tervezési dokumentumokhoz, tervekhez vagy más termékekhez kapcsolódó belső együttműködés megteremtését szolgálhatják. Amikor védett könyvtárakat konfigurál a SharePoint számára, a könyvtárakban tárolt Office-fájlokat az Azure Rights Management fogja ellátni védelemmel.

Az utasítások a következő körülmények között alkalmazhatók:

-   Az alkalmazottak egy SharePoint-könyvtárban található Office-dokumentumok használatával osztják meg munkájukat és működnek együtt.

-   Az alkalmazottaknak nem kell beállítani vagy módosítani az engedélyeket, amelyeket egy rendszergazda állít be a könyvtár szintjén.

-   Az alkalmazottaknak nem kell megosztaniuk a dokumentumokat a szervezeten kívüli személyekkel.

## Üzembe helyezési utasítások
![Rendszergazdai utasítások az Azure RMS gyors üzembe helyezéséhez](../media/AzRMS_AdminBanner.png)

Ellenőrizze, hogy az alábbi feltételek teljesülnek, a támogatási eljárások pedig rendelkezésre állnak, mielőtt továbblépne a felhasználói dokumentációra.

## A forgatókönyv követelményei
Ahhoz, hogy a forgatókönyv működjön, az alábbiaknak kell teljesülniük:

|Követelmény|Ha további információra van szüksége|
|---------------|--------------------------------|
|Előkészítette a fiókokat és a csoportokat az Office 365 vagy az Azure Active Directory számára|[Az Azure Rights Management előkészítése](https://technet.microsoft.com/library/jj585029.aspx)|
|Az Azure Rights Management aktiválása megtörtént|[Az Azure Rights Management aktiválása](https://technet.microsoft.com/library/jj658941.aspx)|
|Ha a SharePoint Servert fogja használni: helyezze üzembe az RMS-összekötőt, és konfigurálja a SharePoint használatára|[Deploying the Azure Rights Management connector (Az Azure Rights Management-összekötő üzembe helyezése)](https://technet.microsoft.com/library/dn375964.aspx)|
|Konfigurálja védeni kívánt SharePoint-webhelyre vonatkozó engedélyeket|[Lista, tár, mappa, dokumentum vagy listatétel engedélyeinek kezelése](https://support.office.com/en-ca/article/Manage-permissions-for-a-list-library-folder-document-or-list-item-9d13e7df-a770-4646-91ab-e3c117fcef45)<br /><br />[Tartalomvédelmi szolgáltatás alkalmazása listában vagy tárban](http://office.microsoft.com/sharepoint-help/apply-information-rights-management-to-a-list-or-library-HA102891460.aspx)|
|Konfigurálja a SharePointot az IRM és védett könyvtárak használatára|[A tartalomvédelmi szolgáltatás (IRM) beállítása a SharePoint Felügyeleti központban](https://support.office.com/en-us/article/Set-up-Information-Rights-Management-IRM-in-SharePoint-admin-center-239ce6eb-4e81-42db-bf86-a01362fed65c)<br /><br />[Tartalomvédelmi szolgáltatás alkalmazása listában vagy tárban](http://office.microsoft.com/sharepoint-help/apply-information-rights-management-to-a-list-or-library-HA102891460.aspx)|

### A SharePoint-könyvtár konfigurálása az IRM-beállításokhoz

1.  Miután konfigurálta a SharePointot az IRM-szolgáltatás használatára, lépjen az Azure RMS használatával védeni kívánt SharePoint-könyvtárba. A webhely **Beállítások** &gt; **Tartalomvédelmi szolgáltatás (IRM)** lapján jelölje be a **Letöltési jogosultságok korlátozása a tárban** jelölőnégyzetet, adjon meg egy házirendnevet a rendszergazdák, illetve egy házirendleírást a felhasználók számára, majd kattintson a **BEÁLLÍTÁSOK MEGJELENÍTÉSE** parancsra.

2.  Jelölje be az alábbi jelölőnégyzeteket:

    -   **A tartalomvédelmi szolgáltatást nem támogató dokumentumok feltöltésének tiltása**

    -   Választható: **Csoportvédelem engedélyezése. Alapértelmezett csoport**, majd adja meg egy további olyan csoport nevét, amelynek esetleg részt kell vennie a könyvtárban tárolt dokumentumokon folytatott közös munkában, azonban ezt a SharePointon kívül teszi. Az értékesítési csoport például szerkesztési engedélyekkel rendelkezik a webhelyhez, és a csoport egyik tagja letölt egy dokumentumot, lemezre menti, majd elküldi e-mailben egy munkatársnak, aki nem tagja az értékesítési csoportnak. Ha a munkatárs tagja annak a csoportnak, amelyet itt megad, automatikusan örökli a webhely számára konfigurált engedélyeket, és szerkesztheti a dokumentumot.

        Ezen beállítás nélkül csak a SharePoint-könyvtárhoz hozzáféréssel rendelkező felhasználók dolgozhatnak együtt a dokumentumokon, és csak úgy, ha a dokumentumokat közvetlenül a SharePointból töltik le. Sok esetben ez a korlátozás megfelelő.

## A felhasználói dokumentáció utasításai
Nincs a felhasználóknak adható eljárási utasítás ezzel a forgatókönyvvel kapcsolatban, mert a védett könyvtárak nem igényelnek különösebb felhasználói műveleteket. Letöltésükkor a dokumentumok automatikusan védelmet kapnak azon engedélyek alapján, amelyeket a SharePoint-rendszergazda beállított a webhelyre vonatkozóan. Ennek ellenére tájékoztassa a felhasználókat erről a változásról, hogy tudják, mire számíthatnak, és tájékoztassa az ügyfélszolgálatot arról, hogy mely könyvtárak védettek, és ez hogyan korlátozhatja a dokumentumok használatát. A jelenlegi korlátozások miatt például a dokumentumok megnyithatók, azonban nem szerkeszthetők mobileszközökön. Ha konfigurálta a csoportvédelmet, tájékoztassa a felhasználókkal, hogy mely csoportok érhetik el és szerkeszthetik a dokumentumokat a SharePointon kívülről.

Az alábbi sablont használva másolja és illessze be a bejelentést a végfelhasználóknak szóló üzenetbe, és hajtsa végre ezeket a módosításokat a környezetnek megfelelően:

1.  Cserélje le a *&lt;SharePoint-könyvtár neve&gt;* minden előfordulását az Azure Rights Management számára konfigurált SharePoint-könyvtár nevére és hivatkozására. Ha a közlemény több védett könyvtárra is vonatkozik, módosítsa az utasításokat ennek megfelelően.

2.  Ha konfigurálta a **Csoportvédelem engedélyezése. Alapértelmezett csoport** beállítást, cserélje le a *&lt;csoportnév&gt;* karakterláncot a konfigurált csoport nevére, és indokolja meg, hogy mi az &lt;ok, amiért ez a csoport rendelkezik hozzáférési engedélyekkel a fájlokon nem a SharePoint-könyvtár használatával folytatott közös munkához&gt;. Ha nem konfigurálta ezt a beállítást, törölje ezt a mondatot.

3.  Cserélje le a *&lt;kapcsolattartás adatok&gt;* szöveget azokra az utasításokra, amelyeket követve a felhasználók elérhetik az ügyfélszolgálatot (pl. webhelyhivatkozások, e-mail címek vagy telefonszámok).

4.  Hajtsa végre a bejelentés további kívánt módosításait, majd küldje el a felhasználóknak.

A példadokumentációban látható, hogyan jelenik meg a bejelentés a felhasználók számára a testre szabást követően.

![Felhasználói dokumentációs sablon az Azure RMS gyors üzembe helyezéséhez](../media/AzRMS_UsersBanner.png)

### Informatikai bejelentés: a &lt;SharePoint-könyvtár neve&gt; SharePoint-webhely módosításai
A **&lt;SharePoint-könyvtár neve&gt;** SharePoint-webhely biztonságos együttműködésre lett konfigurálva. Mostantól csak a &lt;csoportnév&gt; csoport tagjai nyithatják meg ezeket a dokumentumokat erről a webhelyről, még akkor is, ha helyben menti vagy elküldi a dokumentumokat valaki másnak e-mailben. Kivételt jelentenek ez alól a &lt;csoportnév&gt; csoport tagjai, akikkel a letöltést követően megoszthatja a dokumentumokat, hogy &lt;ok, amiért ez a csoport rendelkezik hozzáférési engedélyekkel a fájlokon nem a SharePoint-könyvtár használatával folytatott közös munkához&gt;. Amikor szerkeszti a fájlokat, egy sárga tájékoztató sávot lát a dokumentum tetején, amely tájékoztatja arról, hogy a dokumentum védelmet élvez és ki férhet hozzá.

Ezen módosítás révén megőrizhetjük vállalatunk bizalmas adatainak biztonságát olyan személyekkel szemben, akik nem jogosultak az adatok megtekintésére. Ha mobileszköz használatával fér hozzá a dokumentumokhoz, megtekintheti azokat, a szerkesztésükhöz azonban asztali eszközt kell használnia.

Nem tölthet fel dokumentumokat a &lt;SharePoint-oldal neve&gt; webhelyre, ha azok nem támogatják a biztonságos együttműködést.

**Segítségre van szüksége?**

-   Lépjen kapcsolatba az ügyfélszolgálattal: &lt;kapcsolattartási adatok&gt;

### Példa felhasználói dokumentációra
![Példa felhasználói dokumentációra az Azure RMS gyors üzembe helyezéséhez](../media/AzRMS_ExampleBanner.png)

#### Informatikai bejelentés: az Értékesítési előrejelzések és jelentések webhely módosításai
Az **Értékesítési előrejelzések és jelentések** SharePoint-webhely biztonságos együttműködésre lett konfigurálva. Mostantól csak az Értékesítés és marketing csapat tagjai nyithatják meg ezeket a dokumentumokat erről a webhelyről, még akkor is, ha helyben menti vagy elküldi a dokumentumokat valaki másnak e-mailben. Kivételt jelentenek ez alól a Pénzügyi csapat tagjai, akikkel a letöltést követően megoszthatja a dokumentumokat, hogy kinyerhessék a havi előrejelzési adatokat. Amikor szerkeszti a fájlokat, egy sárga tájékoztató sávot lát a dokumentum tetején, amely tájékoztatja arról, hogy a dokumentum védelmet élvez és ki férhet hozzá.

Ezen módosítás révén megőrizhetjük vállalatunk bizalmas adatainak biztonságát olyan személyekkel szemben, akik nem jogosultak az adatok megtekintésére. Ha mobileszköz használatával fér hozzá a dokumentumokhoz, megtekintheti azokat, a szerkesztésükhöz azonban asztali eszközt kell használnia.

Nem tölthet fel dokumentumokat az Értékesítési előrejelzések és jelentések webhelyre, ha azok nem támogatják a biztonságos együttműködést.

**Segítségre van szüksége?**

-   Kapcsolatfelvétel az ügyfélszolgálattal: helpdesk@vanarsdelltd.com




<!--HONumber=Aug16_HO4-->


