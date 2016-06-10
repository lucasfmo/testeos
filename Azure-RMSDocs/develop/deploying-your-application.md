---
# required metadata

title: Az alkalmazás központi telepítése | Azure RMS
description: Ez a témakör ismerteti a tartalomvédelemmel kompatibilis alkalmazás üzembe helyezési lehetőségeit, és végig is vezeti Önt rajtuk
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

# Az alkalmazás üzembe helyezése


Ez a témakör ismerteti a tartalomvédelemmel kompatibilis alkalmazás üzembe helyezési lehetőségeit, és végig is vezeti Önt rajtuk.

> [!IMPORTANT]
> Először ajánlott a Rights Management Services SDK 2.1 alkalmazás az éles üzem előtti RMS környezetben egy RMS-kiszolgálóval tesztelni. Ha ezt követően azt szeretné, hogy az ügyfél használhassa az alkalmazást az Azure RMS szolgáltatással, a tesztelést abban a környezetben folytassa. További információ: [Enable your service application to work with cloud based RMS](how-to-use-file-api-with-aadrm-cloud.md) (A szolgáltatásalkalmazás alkalmassá tétele a felhőalapú RMS használatára).

 

## Az Active Directory Rights Management Services 2.1-es verziójú ügyfelének telepítési beállításai

Miután létrehozta a jegyzékfájlt éles tanúsítvánnyal, az alkalmazás készen áll az üzembe helyezésre. Az RMS SDK 2.1 használata miatt a végfelhasználó gépére telepíteni kell az Active Directory Rights Management Services ügyfelének 2.1-es verzióját.

### AD RMS-ügyfél 2.1

Az AD RMS-ügyfél 2.1 szoftvert az ügyfélszámítógépek számára tervezték, hogy segítséget nyújtson azon információk elérésének és használatának védelméhez, amelyek az RMS-t használó, a helyszínen vagy egy Microsoft adatközpontba telepített alkalmazásokon áramolnak át.

Az AD RMS-ügyfél 2.1-es verziója nem a Windows operációs rendszer összetevője. Az AD RMS-ügyfél 2.1-es verziója választható letöltésként érhető el, amely a hozzá tartozó licencszerződés tudomásul vétele és elfogadása után ingyenesen terjeszthető a harmadik felek szoftvereivel, hogy az ügyfelek hozzáférhessenek a környezetben található RMS-kiszolgálók használata és telepítése által védett tartalmakhoz.

> [!IMPORTANT]
> Az AD RMS-ügyfél 2.1-es verziója architektúrafüggő, és meg kell egyeznie a cél operációs rendszer architektúrájával.


## Az AD RMS-ügyfél 2.1-es verziójával kapcsolatos telepítési döntések

-   **Az AD RMS-ügyfél 2.1-es verziójának terjesztése**

    Az ajánlott módszer az RMS-ügyfél telepítőcsomagjának mellékelése az alkalmazáshoz vagy megoldáshoz a kívánt telepítési technológiával. Az RMS-ügyfél szabadon terjeszthető és mellékelhető más alkalmazásokhoz vagy IT-megoldásokhoz.

    Választhatja az AD RMS-ügyfél 2.1-es verziójának interaktív telepítését az AD RMS-ügyfél 2.1 telepítőjének indításával, vagy telepítheti beavatkozás nélkül is. Az integráció lépései a következők:

    -   Az AD RMS-ügyfél 2.1 telepítőjének letöltése
    -   Az AD RMS-ügyfél 2.1 telepítőjének integrálása az alkalmazástelepítőbe

    Két jó példa az AD RMS-ügyfél 2.1-es verziójának alkalmazásba való integrálására az RMS SDK 2.1 telepítőcsomag és a jogvédett mappák kezelőcsomagja. A módszer megértéséhez próbálja meg telepíteni őket.

-   **Az AD RMS-ügyfél 2.1-es verziójának meghatározása a saját alkalmazása telepítési előfeltételeként**

    Ebben az esetben olyan előfeltételt hoz létre, amely az alkalmazás sikertelen telepítését okozza, ha a végfelhasználó gépén nem található meg az AD RMS-ügyfél 2.1-es verziója.

    Ha az ügyfél nem található, megjelenik egy hibaüzenet, amely tájékoztatja a felhasználót, hogy honnan töltheti le az AD RMS-ügyfél 2.1-es verzióját

    Ha az ügyfél megtalálható, folytatódhat az alkalmazás telepítése.

## Az Azure Rights Management szolgáltatások engedélyezése az alkalmazással

> [!NOTE]
> Ha a hitelesítéshez áttelepíttette az alkalmazást az új ADAL modellre, akkor nem kell telepítenie az SIA-t. További információ: ADAL-hitelesítés RMS-kompatiblis alkalmazásokhoz.

- **Az alkalmazás tanúsítása a Windows 10-re**: Az alkalmazásnak a Microsoft Online bejelentkezési segéd helyett az ADAL-hitelesítés használatára való frissítésével Ön és ügyfelei az alábbiakra lesznek képesek:
  - Többtényezős hitelesítés használata.
  - Az RMS 2.1 ügyfél telepítése rendszergazdai jogosultságok nélkül a számítógépen.
 
  Ahhoz, hogy a végfelhasználó használni tudja az Azure Rights Management szolgáltatások előnyeit, telepítenie kell az *Online Services bejelentkezési segédet*. Az alkalmazás fejlesztőjeként nem tudhatja, hogy a végfelhasználó az RMS-t (helyszíni) vagy az Azure Rights Management szolgáltatásokat (felhőszolgáltatás) fogja-e használni.

> [!IMPORTANT]
> Az RMS SDK 2.1 ügyfélalkalmazás Azure RMS-sel történő futtatásához Azure RMS-bérlőt kell kérnie. Küldjön egy e-mailt az <rmcstbeta@microsoft.com> címre a bérlőkéréssel.

-   Töltse le a [Microsoft Online Services bejelentkezési segédet](http://www.microsoft.com/en-us/download/details.aspx?id=28177) a Microsoft letöltőközpontjából.
-   Győződjön meg arról, hogy a tartalomvédelemmel kompatibilis alkalmazás telepítője ellenőrzi a szolgáltatás előfeltételeinek teljesülését.
-   Saját teszteléshez és az online szolgáltatás végfelhasználók általi használatához tekintse meg a [Configuring Rights Management](https://TechNet.Microsoft.Com/en-us/library/jj585002.aspx) (A Rights Management konfigurálása) című TechNet-témakört.

További információk az alkalmazás alkalmassá tételéről az RMS használatára az Azure Rights Management szolgáltatásokhoz: [Enable your service application to work with cloud based RMS](how-to-use-file-api-with-aadrm-cloud.md) (Az alkalmazás alkalmassá tétele a felhőalapú RMS használatára).

## Kapcsolódó témakörök

* [Használati útmutató](how-to-use-msipc.md)
* [Microsoft Online Services bejelentkezési segéd](http://www.microsoft.com/en-us/download/details.aspx?id=28177)
* [Configuring Rights Management (A Rights Management konfigurálása)](https://TechNet.Microsoft.Com/en-us/library/jj585002.aspx)
* [Enable your application to work with cloud based RMS (Az alkalmazás alkalmassá tétele a felhőalapú RMS használatára)](how-to-use-file-api-with-aadrm-cloud.md)
 

 





<!--HONumber=Apr16_HO4-->


