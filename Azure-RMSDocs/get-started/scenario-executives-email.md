---
title: "Forgatókönyv – Jogosultságokhoz kötött információk biztonságos cseréje vezetői szinten | Azure RMS"
description: "Ez a forgatókönyv és a támogató felhasználói dokumentáció az Azure Rights Managementet használja ahhoz, hogy a vezetők biztonságosan küldhessenek e-maileket és e-mailes mellékleteket egymásnak, és a házirendek automatikusan korlátozzák a vezetők hozzáférését anélkül, hogy speciális műveleteket kellene végezniük."
author: cabailey
manager: mbaldwin
ms.date: 08/25/2016
ms.topic: get-started-article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: e18cf5df-859e-4028-8d19-39b0842df33d
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 81426cf43f31625c6e83d443fa925f6426eb89da
ms.openlocfilehash: 1ec54b54197471f8cccaf6ae83ae8e592da30cae


---

# Forgatókönyv – Jogosultságokhoz kötött információk biztonságos cseréje vezetői szinten

>*A következőkre vonatkozik: Azure Rights Management, Office 365*

Ez a forgatókönyv és a támogató felhasználói dokumentáció az Azure Rights Managementet használja ahhoz, hogy a vezetők biztonságosan küldhessenek e-maileket és e-mailes mellékleteket egymásnak, és a házirendek automatikusan korlátozzák a vezetők hozzáférését anélkül, hogy speciális műveleteket kellene végezniük. Az e-mailt és a mellékleteit az Azure Rights Management automatikusan védelemmel látja el.

Szükség esetén egy kivételt adhat a szabályhoz, például a DNP („Ne védje”) rövidítést az e-mail-üzenet tárgyához, hogy a vezetők ezt használhassák, ha nem védett e-mailt kell küldeniük más vezetőknek, például ha át szeretnék nézni azt, mielőtt másoknak továbbítanák.

Az utasítások a következő körülmények között alkalmazhatók:

-   A vezetők bizalmas információkat oszthatnak meg egymással, amelyek másokkal nem megoszthatóak.

-   A vezetőknek nem kell semmi mást tenniük ezen e-mailek küldésekor, csak a személyes e-mail-cím helyett a munkahelyi e-mail-címre kell küldeniük azokat.

-   A vezetők saját kezűleg felülbírálhatják a szabályt, ha nem védett e-mail-üzenetet kell küldeniük más vezetőknek.

## Üzembe helyezési utasítások
![Rendszergazdai utasítások az Azure RMS gyors üzembe helyezéséhez](../media/AzRMS_AdminBanner.png)

Ellenőrizze, hogy a következő feltételek teljesülnek-e, majd kövesse a támogató eljárásokra vonatkozó utasításokat, mielőtt továbblépne a felhasználói dokumentációra.

## A forgatókönyv követelményei
Ahhoz, hogy a forgatókönyv utasításai működjenek, az alábbiaknak kell teljesülniük:

|Követelmény|Ha további információra van szüksége|
|---------------|--------------------------------|
|Előkészítette a fiókokat és a csoportokat az Office 365 vagy az Azure Active Directory számára:<br /><br />– A **Vezetők** nevű levelezési csoport, és az összes vezető tagja ennek a csoportnak<br /><br />– Az **RMS-rendszergazdák** nevű levelezési csoport, amelynek az Azure RMS konfigurálását végző összes rendszergazda a tagja.|[Az Azure Rights Management előkészítése](https://technet.microsoft.com/library/jj585029.aspx)|
|Az Azure Rights Management-bérlőkulcsát a Microsoft felügyeli; nem a BYOK módot használja|[Planning and implementing your Azure Rights Management tenant key (Az Azure Rights Management-bérlőkulcs tervezése és megvalósítása)](https://technet.microsoft.com/library/dn440580.aspx)|
|Az Azure Rights Management aktiválása megtörtént|[Az Azure Rights Management aktiválása](https://technet.microsoft.com/library/jj658941.aspx)|
|Ezen konfigurációk egyike:<br /><br />– Az Exchange Online engedélyezve van az Azure Rights Managementhez<br /><br />– Az RMS-összekötő telepítve és konfigurálva van a helyszíni Exchange-hez|Az Exchange Online esetében lásd a [Configuring Applications for Azure Rights Management](https://technet.microsoft.com/library/jj585031.aspx) (Alkalmazások konfigurálása az Azure Rights Managementhez) című témakör **Exchange Online: IRM Configuration** (Exchange Online: IRM konfiguráció) szakaszát.<br /><br />Helyszíni Exchange esetében: [Deploying the Azure Rights Management connector (Az Azure Rights Management-összekötő üzembe helyezése)](https://technet.microsoft.com/library/dn375964.aspx)|
|Konfigurált egy egyéni sablont az alábbiakban leírtak alapján.|[Az Azure Rights Management egyéni sablonok konfigurálása](https://technet.microsoft.com/library/dn642472.aspx)|
|Konfigurált egy átvitelvédelmi szabályt az IRM-hez, az ebben a cikkben később ismertetetteknek megfelelően|Exchange Online esetén: [Create a Transport Protection Rule](https://technet.microsoft.com/library/dd302432.aspx) (Átvitelvédelmi szabály létrehozása).<br /><br />Exchange 2013 esetén: [Create a Transport Protection Rule](https://technet.microsoft.com/library/dd302432%28v=exchg.150%29.asp) (Átvitelvédelmi szabály létrehozása).<br /><br />Exchange 2010 esetén: [Create a Transport Protection Rule](https://technet.microsoft.com/en-us/library/dd302432%28v=exchg.141%29.aspx) (Átvitelvédelmi szabály létrehozása).|

### Az egyéni sablon konfigurálása vezetők számára

1.  Hozzon létre egy új egyéni sablon az Azure Rights Management szolgáltatásban a klasszikus Azure-portálon az alábbi értékekkel és beállításokkal:

    -   Név: **Vezetők**

    -   Jogosultságok: Biztosítson a **Vezetők** levelezési csoportnak **Társtulajdonos** jogosultságokat.

    -   Hatókör: Jelölje ki a **Vezetők** levelezési csoportot és az **RMS-rendszergazdák** levelezési csoportot.

2.  Tegye közzé az új sablont.

3.  Csak Exchange Online esetén: Frissítse a sablonokat az Exchange Online Windows PowerShell-parancsával:

    ```
    Import-RMSTrustedPublishingDomain -Name "RMS Online -1" -RefreshTemplates -RMSOnline
    ```

### Az IRM átviteli szabályának konfigurálása

-   A táblázatban hivatkozott Exchange-dokumentációt használja az eljárással kapcsolatos információk beszerzéséért az átviteli szabály a következő beállításokkal történő létrehozásához:

    -   Név: **A Vezetők sablonok alkalmazása a vezetői e-mailekre**

    -   Adja meg a **Vezetők** csoportot a szabály és a további feltétel küldőjeként és címzettjeként.

    -   A művelethez válassza a **Jogvédelem alkalmazása az üzenetre a következővel** lehetőséget, majd válassza a bekonfigurált **Vezetők** sablont.

    -   Adja hozzá a **DNP** kivételt (amely a „Ne védje” rövidítése), vagy válassza ki a kivételt azonosító, a tárgyba foglalni kívánt szavakat.

    -   Győződjön meg róla, hogy a szabály a **Kényszerítésre** legyen konfigurálva.

## A felhasználói dokumentáció utasításai
Hacsak nem szeretné megadni a **DNP** vagy a választott szavak vagy kifejezések az e-mail tárgyában történő használatának utasításait, nincs a felhasználók felé adható eljárási utasítás ezzel a forgatókönyvvel kapcsolatban, mert a vezetőktől és a vezetőknek küldött védett e-mailek nem igényelik vezetői műveletek végrehajtását. Az e-mail-üzenetek és a mellékletek automatikusan védve lesznek, így csak a Vezetők csoport tagjai érhetik el ezeket.

Érdemes azonban tájékoztatnia a vezetőket és az ügyfélszolgálatot arról, hogy ezek az e-mailek automatikusan védve vannak, illetve hogyan korlátozhatja ez az e-mailek használatát. Mások például nem olvashatják el azokat, ha az e-maileket vagy mellékleteket később másoknak továbbítják. Ha konfigurálta a DNP (vagy annak megfelelő) kivételt, győződjön meg róla, hogy az ügyfélszolgálat tud a konfigurációról, hogy a vezetők felülbírálhassák a szabályokat egy Exchange-rendszergazda beavatkozása nélkül.

Az alábbi sablont használva másolja és illessze be a bejelentést a végfelhasználóknak szóló üzenetbe, és hajtsa végre ezeket a módosításokat a környezetnek megfelelően:

1.  Cserélje le a *&lt;Szervezet neve&gt;* szöveg előfordulásait a saját szervezetének nevére.

2.  Ha másik karakterláncot választ a kivételhez, és nem a DNP-t, annak megfelelően cserélje le ezt az értéket és a magyarázatot.

3.  Cserélje le az *&lt;emailtartomány&gt;* szöveget a szervezete e-mailes tartománynevével.

4.  Cserélje le a *&lt;kapcsolattartás adatok&gt;* szöveget azokra az utasításokra, amelyeket követve a felhasználók elérhetik az ügyfélszolgálatot (pl. webhelyhivatkozások, e-mail címek vagy telefonszámok).

5.  Hajtsa végre a bejelentés további kívánt módosításait, majd küldje el a felhasználóknak.

A példadokumentációban látható, hogyan jelenik meg a bejelentés a felhasználók számára a testre szabást követően.

![Felhasználói dokumentációs sablon az Azure RMS gyors üzembe helyezéséhez](../media/AzRMS_UsersBanner.png)

### Informatikai bejelentés: A &lt;Szervezet neve&gt; vezetői e-mailjei mostantól automatikus védelemmel vannak ellátva
Mostantól, ha e-maileket küld egy másik &lt;szervezet neve&gt;-vezetőnek a vállalaton belül, a rendszer automatikusan védelemmel látja el az e-maileket és a mellékletek tartalmát, így csak a vállalat más vezetői érhetik el azokat az információk elolvasásához, a kinyomtatáshoz, a másoláshoz és egyéb műveletekhez. Ez a korlátozás akkor is érvényes, ha másoknak továbbít e-mail-üzeneteket, vagy menti a mellékleteket. Ez a védelem segít meggátolni a bizalmas adatok elvesztését.

Vegye figyelembe, hogy ha azt szeretné, hogy a &lt;szervezet neve&gt; vezetőin kívüli személyek is elolvashassák és szerkeszthessék az ilyen e-mailekben küldött információkat, számukra egy külön e-mailt kell küldenie. Illetve az automatikus védelem letiltásához beírhatja a **DNP** betűket (a „Ne védje” rövidítéseként) bárhová, az e-mail-üzenet tárgyába.

Amikor bizalmas vállalati adatokat küld egy másik &lt;szervezet neve&gt;-vezetőnek, ne feledje, hogy a munkahelyi e-mail-címére küldje azt (*név*@&lt;emailtartomány&gt;), és ne a személyes e-mail-címére.

**Segítségre van szüksége?**

-   Lépjen kapcsolatba az ügyfélszolgálattal: &lt;kapcsolattartási adatok&gt;

### Példa felhasználói dokumentációra
![Példa felhasználói dokumentációra az Azure RMS gyors üzembe helyezéséhez](../media/AzRMS_ExampleBanner.png)

#### Informatikai bejelentés: A VanArsdel vezetői e-mailjei mostantól automatikus védelemmel vannak ellátva
Mostantól, ha e-maileket küld egy másik VanArsdel-vezetőnek a vállalaton belül, a rendszer automatikusan védelemmel látja el az e-maileket és a mellékletek tartalmát, így csak a vállalat más vezetői érhetik el azokat az információk elolvasásához, a kinyomtatáshoz, a másoláshoz és egyéb műveletekhez. Ez a korlátozás akkor is érvényes, ha másoknak továbbít e-mail-üzeneteket, vagy menti a mellékleteket. Ez a védelem segít meggátolni a bizalmas adatok elvesztését.

Vegye figyelembe, hogy ha azt szeretné, hogy a VanArsdel vezetőin kívüli személyek is elolvashassák és szerkeszthessék az ilyen e-mailekben küldött információkat, számukra egy külön e-mailt kell küldenie. Illetve az automatikus védelem letiltásához beírhatja a **DNP** betűket (a „Ne védje” rövidítéseként) bárhová, az e-mail-üzenet tárgyába.

Amikor bizalmas vállalati adatokat küld egy másik VanArsdel-vezetőnek, ne feledje, hogy a munkahelyi e-mail-címére küldje azt (*név*@vanarsdelltd.com), és ne a személyes e-mail-címére.

**Segítségre van szüksége?**

-   Kapcsolatfelvétel az ügyfélszolgálattal: helpdesk@vanarsdelltd.com




<!--HONumber=Aug16_HO4-->


