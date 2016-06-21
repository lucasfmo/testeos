---
# required metadata

title: Az alkalmazás központi telepítése | Azure RMS
description: Ez a témakör ismerteti a tartalomvédelemmel kompatibilis alkalmazás üzembe helyezési lehetőségeit, és részletesen le is írja a folyamatokat.
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 4B785564-6839-49ED-A243-E2A6DFF88B2E
# optional metadata

#ROBOTS:
audience: developer
#ms.devlang:
ms.reviewer: shubhamp
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Üzembe helyezés üzem előtti környezetben


Ez a témakör ismerteti a tartalomvédelemmel kompatibilis alkalmazás üzembe helyezési lehetőségeit, és részletesen le is írja a folyamatokat.

## Üzemi használatra szóló licencszerződés kérése

 Mielőtt kiadna egy, a Rights Management Services SDK 2.1 segítségével létrehozott alkalmazást, üzemi használatra szóló licencszerződést kell kötnie üzemi környezetben is használható tanúsítvány beszerzéséhez.

> [!IMPORTANT]
> Ha az ügyfélalkalmazást Azure-alapú RMS rendszerrel szeretné futtatni, saját bérlőket kell létrehoznia. További információért lásd: [Azure RMS-követelmények: Az Azure RMS-t támogató felhőalapú előfizetések](../get-started/requirements-subscriptions.md).
> További információ az Azure RMS futtatásáról: [A szolgáltatásalkalmazás alkalmassá tétele a felhőalapú RMS használatára](how-to-use-file-api-with-aadrm-cloud.md).

A tanúsítványt üzemi használatra szóló licencszerződés igénylésével szerezheti meg.

Írjon az [RMLA@microsoft.com](mailto:rmla@microsoft.com) címre egy e-mail-üzenetet a következő információkkal:

- A vállalat teljes neve
- A vállalat fizikai címe (beleértve a város, az állam, az ország, illetve a régió nevét, valamint az irányítószámot)
- A vállalat postacíme (beleértve a város, az állam, az ország, illetve a régió nevét, valamint az irányítószámot)
- A vállalat telefon- és faxszáma
- A vállalat URL-címe
- Ország vagy régió, amelyben a céget bejegyezték
- Az alkalmazás vagy termék neve
- A kérelmet benyújtó személy vezetékneve és keresztneve
- A kérelmet benyújtó személy címe vagy beosztása
- A kérelmet benyújtó személy e-mail-címe

Az e-mail-fiók megadása nem kötelező, azonban a jelentkezési folyamat jellemzően e-mailben folytatott kommunikációval zajlik. A Microsoft Outlook.com webhelyen ingyenes e-mail-fiókot hozhat létre. Ha nem rendelkezik fiókkal, és nem is szeretne létrehozni egyet, akkor a következő címre küldheti el géppel írt jelentkezését:

      Active Directory Rights Management License Agreements (ADRMLA)

      Microsoft Corporation

      One Microsoft Way

      Redmond, WA 98052-6399

A szerződés kérelmezésekor a következőket tegye:
- Az adatokat angolul adja meg, úgy, ahogy a szerződésben kell megjelenniük.
- Minden szükséges adatot küldjön el. A hiányzó vagy hiányos adatok késleltethetik a kérelem feldolgozását.

Az Active Directory tartalomvédelmi szolgáltatások licencszerződéseivel (ADRMLA) foglalkozó csapat három munkanapon belül válaszol az e-mailben elküldött kérelmekre. Ha a kérelmet postai úton küldte el, hosszabb időt vesz igénybe. A válasz tartalmazza a licencszerződési űrlapot és a további utasításokat. A szerződés minden oldalát olvassa el, írja alá és juttassa vissza az ADRMLA csapatnak. Ne módosítsa a betűtípust és ne formázza újra a licencszerződés bekezdéseit.

Kövesse az ADRMLA csapat által megadott utasításokat. Az utasítások felsorolják, hogy milyen digitális információk szükségesek a tanúsítvány kérelmezéséhez. Ha pontosan követi az utasításokat, azzal elkerülheti a késedelmeket.

Ha elkészült a tanúsítvány, az ADRMLA csapat továbbítja azt Önnek. Kérjük, vegye figyelembe, hogy akár 15 munkanapot is igénybe vehet, amíg az ADRMLA csapat elküldi Önnek e-mailben a tanúsítványt, ha pedig a kommunikáció postai úton történik, akkor még többet.


## A Rights Management Services-ügyfél 2.1-es verziójának telepítési lehetőségei és követelményei

Az RMS SDK 2.1 használata miatt a végfelhasználó gépére telepíteni kell az Active Directory Rights Management Services ügyfelének 2.1-es verzióját.

### RMS-ügyfél 2.1

Az RMS-ügyfél 2.1-es verziója ügyfélszámítógépeken való használatra készült, hogy segítséget nyújtson a helyszíni vagy Microsoft-adatközpontba telepített, tartalomvédelmet használó alkalmazásokon áthaladó információk elérésének és használatának védelméhez.

Az RMS-ügyfél 2.1-es verziója nem összetevője a Windows operációs rendszernek. Az RMS-ügyfél 2.1-es verziója választható letöltésként érhető el, amely a hozzá tartozó licencszerződés tudomásul vétele és elfogadása után ingyenesen terjeszthető a harmadik felek szoftvereivel, hogy az ügyfelek hozzáférhessenek a környezetben található RMS-kiszolgálók használata és telepítése által védett tartalmakhoz.


> [!IMPORTANT] Az AD RMS-ügyfél 2.1-es verziója architektúrafüggő, és meg kell egyeznie a cél operációs rendszer architektúrájával.


## Az RMS-ügyfél 2.1-es verziójával kapcsolatos telepítési döntések

-   **Az RMS-ügyfél 2.1-es verziójának terjesztése**

    Az ajánlott módszer az RMS-ügyfél telepítőcsomagjának mellékelése az alkalmazáshoz vagy megoldáshoz a kívánt telepítési technológiával. Az RMS-ügyfél szabadon terjeszthető és mellékelhető más alkalmazásokhoz vagy IT-megoldásokhoz.

    Az RMS-ügyfél 2.1-es verziója a hozzá tartozó telepítővel interaktív módon, illetve beavatkozás nélkül is telepíthető. Az integráció lépései a következők:

    -   Az AD RMS-ügyfél 2.1 telepítőjének letöltése
    -   Az RMS-ügyfél 2.1 telepítőjének integrálása az alkalmazástelepítőbe

    Két jó példa az RMS-ügyfél 2.1-es verziójának alkalmazásba való integrálására az RMS SDK 2.1 telepítőcsomag és a jogvédett mappák kezelőcsomagja. A módszer megismeréséhez próbálja meg önállóan telepíteni őket.

-   **Az RMS-ügyfél 2.1-es verziójának meghatározása saját alkalmazás telepítési előfeltételeként**

    Ebben az esetben olyan előfeltételt hoz létre, amellyel az alkalmazás telepítése meghiúsul, ha a végfelhasználó gépén nem található meg az RMS-ügyfél 2.1-es verziója.

    Ha az ügyfél nem található, megjelenik egy hibaüzenet, amely tájékoztatja a felhasználót, hogy honnan töltheti le az RMS-ügyfél 2.1-es verzióját.

    Ha az ügyfél megtalálható, folytatódhat az alkalmazás telepítése.

## Az Azure Rights Management szolgáltatások engedélyezése az alkalmazással

> [!NOTE]
> Ha a hitelesítéshez áttelepíttette az alkalmazást az új ADAL-modellre, akkor nem kell telepítenie a bejelentkezési segédet. További információ: [ADAL-hitelesítés RMS-kompatibilis alkalmazásokhoz](adal-auth.md).
> Igény szerint **tanúsíthatja is alkalmazását a Windows 10-hez** – Ha a Microsoft Online bejelentkezési segéd helyett az alkalmazást az ADAL-hitelesítés használatára szeretné beállítani, akkor Ön és felhasználói: – Többtényezős hitelesítést vehetnek igénybe – Rendszergazdai jogosultságok nélkül telepíthetik az RMS-ügyfél 2.1-es verzióját a számítógépen


Ahhoz, hogy a végfelhasználó használni tudja az Azure Rights Management szolgáltatások előnyeit, telepítenie kell az *Online Services bejelentkezési segédet*. Az alkalmazás fejlesztőjeként nem tudhatja, hogy a végfelhasználó az RMS-t (helyszíni) vagy az Azure Rights Management szolgáltatásokat (felhőszolgáltatás) fogja-e használni.


> [!IMPORTANT]
> Ha az RMS SDK 2.1 ügyfélalkalmazását az Azure RMS szolgáltatással szeretné futtatni, saját bérlőket kell létrehoznia. További információért lásd: [Azure RMS-követelmények: Az Azure RMS-t támogató felhőalapú előfizetések](../get-started/requirements-subscriptions.md).

-   Töltse le a [Microsoft Online Services bejelentkezési segédet](http://www.microsoft.com/en-us/download/details.aspx?id=28177) a Microsoft letöltőközpontjából.
-   Győződjön meg arról, hogy a tartalomvédelemmel kompatibilis alkalmazás telepítője ellenőrzi a szolgáltatás előfeltételeinek teljesülését.
-   Saját teszteléshez és az online szolgáltatás végfelhasználók általi használatához tekintse meg a [Configuring Rights Management](https://TechNet.Microsoft.Com/en-us/library/jj585002.aspx) (A Rights Management konfigurálása) című TechNet-témakört.

További információk az alkalmazás alkalmassá tételéről az RMS használatára az Azure Rights Management szolgáltatásokhoz: [Enable your service application to work with cloud based RMS](how-to-use-file-api-with-aadrm-cloud.md) (Az alkalmazás alkalmassá tétele a felhőalapú RMS használatára).

## Kapcsolódó témakörök

* [Microsoft Online Services bejelentkezési segéd](http://www.microsoft.com/en-us/download/details.aspx?id=28177)
* [Configuring Rights Management (A Rights Management konfigurálása)](https://TechNet.Microsoft.Com/en-us/library/jj585002.aspx)
* [Enable your application to work with cloud based RMS (Az alkalmazás alkalmassá tétele a felhőalapú RMS használatára)](how-to-use-file-api-with-aadrm-cloud.md)
 

 


<!--HONumber=Jun16_HO2-->


