---
title: "Újdonságok és kibocsátási megjegyzések | Azure RMS"
description: "Az alábbiakban megismerheti az RMS SDK ezen új verziójával kapcsolatos fontos változtatásokat és szolgáltatásokat."
keywords: 
author: bruceperlerms
manager: mbaldwin
ms.date: 06/16/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 4fa1c686-b00b-4734-9abb-141ce582a6af
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 79397c82d9478cbd55630a376fe2d12f3873ebc4
ms.openlocfilehash: 8de1886adf322439721274e23452af75b4db2e00


---

# Újdonságok és kibocsátási megjegyzések

## Újdonságok
A Microsoft Rights Management SDK 4.2-es verziója az egyszerűség és rugalmasság új szintjére emeli az alkalmazásfejlesztés RMS általi támogatását. A jelen témakör ismerteti az RMS SDK ezen új verziójával kapcsolatos fontos változtatásokat és szolgáltatásokat.

-   [2016. júniusi újdonságok](#new-for-June-2016)
-   [2015. decemberi frissítés](#december-2015-update)
-   [2015. júliusi frissítés – Linux-/C++-fejlesztés támogatása](#july-2015-update-adds-support-for-linux-c-developm)
-   [2015. májusi frissítés – Naplózás vezérlésének hozzáadása](#may-2015-update-adds-logging-control)
-   [2015. februári frissítés – Windows Áruházbeli alkalmazások támogatása](#february-2015-update-adds-windows-store-application-support)
-   [2015. januári frissítés – WinPhone platform támogatása](#january-2015-update-adds-winphone-platform-support)
-   [2014. októberi frissítés – Frissítés a Microsoft RMS SDK 4.1-es verziójára](#october-2014-update-upgrade-to-microsoft-rms-sdk-4-1)
-   [Kibocsátási megjegyzések](#release-notes)
-   [Gyakori kérdések](#frequently-asked-questions)

### 2016. júniusi újdonságok

- **A modern hitelesítés támogatása** – Ezzel az Active Directory Authentication Library-alapú (ADAL-alapú) bejelentkezés biztosítható az RMS-kompatibilis alkalmazásokhoz. Lehetővé teszi olyan bejelentkezési módok használatát, mint a többtényezős hitelesítés (Multi-Factor Authentication, MFA), az SAML-alapú, RMS ügyfélalkalmazásokat használó külső identitásszolgáltatók, valamint az intelligenskártya- és tanúsítványalapú hitelesítés, és szükségtelenné teszi, hogy az RMS-kompatibilis alkalmazásoknak alapszintű hitelesítési protokollt kelljen használniuk.
- **A dokumentumkövetés támogatása** – A fejlesztők mostantól lehetővé tehetik a dokumentumkövetést, miközben védik a saját alkalmazásaikban lévő dokumentumokat. 
- Teljesítménnyel kapcsolatos fejlesztések
- Hibajavítások


### 2015. decemberi frissítés

Ezzel a kiadással az eszközök számára készült RMS SDK verzió a 4.2-es verzió lett, és az alábbiakkal bővült:

-   Dokumentumok nyomon követése, csak online RMS esetén, iOS/OS X és Android operációs rendszereken.

    Az iOS/OS X operációs rendszerrel kapcsolatos részletekért és használati útmutatásért tekintse meg az [**MSLicenseMetadata**](/rights-management/sdk/4.2/api/iOS/mslicensemetadata#msipcthin2_mslicensemetadata_class_objc) osztályt, amely nyomon követési információkat biztosít, illetve ismerteti dokumentumok nyomon követését biztosító szolgáltatás regisztrációs eljárását az [**MSUserPolicy**](/rights-management/sdk/4.2/api/iOS/iOS#msipcthin2_msuserpolicy_interface_objc) osztályra vonatkozóan. Hasonló újítások történtek az Android esetében a [**LicenseMetadata**](/rights-management/sdk/4.2/api/android/com.microsoft.rightsmanagement#msipcthin2_licensemetadata_interface_java) és a [**UserPolicy**](/rights-management/sdk/4.2/api/android/userpolicy) osztály tekintetében.

    A dokumentumok nyomon követését biztosító szolgáltatás részletes ismertetését a [**How to: Use document tracking**](how-to-use-document-tracking.md) (Útmutató: A dokumentumok nyomon követésének használata) című témakörben tekintheti meg.

-   Az Android API aszinkron verzióival párhuzamos szinkron módszerek:

    [**CustomProtectedInputStream.create szinkron módszer**](/rights-management/sdk/4.2/api/android/customprotectedinputstream#msipcthin2_customprotectedinputstream_create_synchronous_method_java)

    [**CustomProtectedOutputStream.create szinkron módszer**](/rights-management/sdk/4.2/api/android/customprotectedoutputstream#msipcthin2_customprotectedoutputstream_create_synchronous_method)

    [**ProtectedFileInputStream.create szinkron módszer**](/rights-management/sdk/4.2/api/android/protectedfileinputstream#msipcthin2_protectedfileinputstream_create_synchronous_method)

    [**ProtectedFileOutputStream.create szinkron módszer**](/rights-management/sdk/4.2/api/android/customprotectedoutputstream#msipcthin2_customprotectedoutputstream_create_synchronous_method)

    [**TemplateDescriptor.getTemplates szinkron módszer**](/rights-management/sdk/4.2/api/android/templatedescriptor#msipcthin2_templatedescriptor_gettemplates_synchronous_method_java)

    [**UserPolicy.acquire szinkron módszer**](/rights-management/sdk/4.2/api/android/userpolicy#msipcthin2_userpolicy_acquire_synchronous_method_java)

    [**UserPolicy.create (PolicyDescriptor…) szinkron módszer**](/rights-management/sdk/4.2/api/android/userpolicy#msipcthin2_userpolicy_create_policydescriptor_______synchronous_method_java)

    [**UserPolicy.create (TempalteDescriptor…) szinkron módszer**](/rights-management/sdk/4.2/api/android/userpolicy#msipcthin2_userpolicy_create_templatedescriptor_______synchronous_method_java)

-   Az Android API az új [**ProtectedBuffer**](/rights-management/sdk/4.2/api/android/com.microsoft.rightsmanagement#msipcthin2_protectedbuffer_class) osztállyal bővült.
-   A hibaüzenetekkel és a hibaelhárítással kapcsolatos élményt javító frissítések.
-   A titkosítási műveletek teljesítményének jelentős növelése.

### 2015. júliusi frissítés – Linux-/C++-fejlesztés támogatása

Ez a kiadás az alábbiakkal bővült:

-   RMS SDK 4.1 Linux-platformokhoz

    További információ: [Get started](get-started.md) (Első lépések).

### 2015. májusi frissítés – Naplózás vezérlésének hozzáadása

Ez a kiadás az alábbiak támogatásával bővült:

-   iOS

    Az alkalmazástitkosítás és -visszafejtés egymástól függetlenül és párhuzamosan is használható.

    További információ: [**MSProtector**](/rights-management/sdk/4.2/api/iOS/iOS#msipcthin2_msprotector_class_objc).

    Naplózási szint vezérlési beállításainak használata.

    További információ: [How to: Enable error and performance logging](enabling-logging.md) (Útmutató: Hiba- és teljesítménynaplózás engedélyezése).

    Gyorsítótár-kiürítés támogatása.

    További információ: [**MSProtection:resetStateWithCompletionBlock**](/rights-management/sdk/4.2/api/iOS/msprotection#msipcthin2_msprotection_resetstatewithcompletionblock_method_objc).

### 2015. februári frissítés – Windows Áruházbeli alkalmazások támogatása

Ez a kiadás a Windows Áruházbeli alkalmazások támogatásával bővült, továbbá egyenértékű funkciókat biztosít az RMS SDK 4.1 Windows Phone, Android és iOS/OS X számára készült kiadásával.

### 2015. januári frissítés – WinPhone platform támogatása

Ez a kiadás a Windows Phone operációs rendszer támogatásával bővült, továbbá egyenértékű funkciókat biztosít az RMS SDK 4.1 Android és iOS/OS X számára készült kiadásával.

### 2014. októberi frissítés – Frissítés a Microsoft RMS SDK 4.1-es verziójára

Az RMS SDK 4.1-es verziójú kiadásában az alábbi új szolgáltatások érhetők el a Google Android és az Apple iOS/OS X operációs rendszeréhez.

-   Android és iOS/OS X SDK API-bővítmények a *felhasználói hozzájárulás* feldolgozásához, ami lehetővé teszi az SDK működésének felhasználói megerősítését. Jelenleg a dokumentumok nyomon követését biztosító szolgáltatás és az ismeretlen AD RMS szolgáltatás URL-címének elérése hozzájárulási típusok támogatottak.

    További információért tekintse meg példaként a [**ConsentCallback felület**](/rights-management/sdk/4.2/api/android/com.microsoft.rightsmanagement#msipcthin2_consentcallback_interface_java) Android API-verzióját.

-   Elérhető lett az iOS 8 és OS X 10.10 (Yosemite) támogatása. Szükségessé vált továbbá néhány tulajdonságnév módosítása az Xcode 6 miatt.

    Például: az MSUserPolicy.name új neve az [**MSUserPolicy.policyName**](/rights-management/sdk/4.2/api/iOS/msuserpolicy#msipcthin2_msuserpolicy_name_property_objc) lett.

## Kibocsátási megjegyzések

Ez a szakasz olyan információkat ismertet a Microsoft Rights Management SDK 4.x API felületek jelenlegi és korábbi kiadásaival kapcsolatban, amelyekkel fejlesztőként érdemes tisztában lennie.

**AD RMS SDK 4.1 – Az iOS/OS X- és Android-platformok globálisan elérhető kiadásai**

-   **Az AD RMS támogatása** – az informatikai rendszergazdák használhatnak RMS-kompatibilis alkalmazásokat mobileszközökön az új AD RMS-kiszolgáló mobileszköz-bővítményeivel.
-   **Offline használat** – a végfelhasználók kapcsolat nélküli állapotban is hozzáférhetnek az RMS által védett adatokhoz.
-   **Elkülönített hitelesítés** – a fejlesztők használhatják saját hitelesítési tárukat az Azure RMS és AD RMS szolgáltatáshoz (vagy használhatják az ajánlott [Azure AD Authentication Library (ADAL)](https://MSDN.Microsoft.Com/library/jj573266.aspx) hitelesítési tárat).
-   **Elkülönített felhasználói felület** – a fejlesztők létrehozhatják saját felhasználói felületüket a dokumentumok védelemmel való ellátásához és az RMS által védett dokumentumok használatához.
-   **Újratervezett API** – a fejlesztők mostantól egy egyszerű és átlátható titkosítási és visszafejtési API felületet használhatnak, amely egységes RMS-működést és felhasználói élményt biztosít kevesebb ráfordítás mellett.

**Az összes platformra vonatkozóan**

-   Az RMS SDK 4.x API felületek nem *szálbiztosak*.

**Android**

-   Amikor egy mintaalkalmazást használ Amazon® Kindle eszközön .ptxt mellékletek megtekintéséhez, először le kell töltenie a fájlt annak megnyitása előtt.

    **Megoldás**: Ez egy ismert probléma, amelyet a későbbiekben kezelni fogunk.

-   Az SDK-t használó alkalmazás összeomolhat, ha a többpéldányos üzemmód engedélyezve lett.

    **Megoldás** – Győződjön meg róla, hogy az alkalmazás nem engedélyez többpéldányos hívásokat az Android API felé.

-   A [**ProtectedFileOutputStream**](/rights-management/sdk/4.2/api/android/protectedfileoutputstream#msipcthin2_protectedfileoutputstream_class_java)**.write(byte\[\] array, int offset, int length)** metódus az *array.length* értékétől eltérő hosszal történő használata esetén később nem használható fel a tartalom az SDK segítségével.

    **Megoldás** – Ez egy ismert probléma. Ennek kezeléséhez mindig adjon át a length paraméter értékével megegyező hosszértéket tartalmazó **byte \[\]** tömböt, vagy használja a [**ProtectedFileOutputStream**](/rights-management/sdk/4.2/api/android/protectedfileoutputstream#msipcthin2_protectedfileoutputstream_class_java)**.write(byte\[\] array)** metódust.

**iOS és OS X**

-   Két portugál nyelvjárást támogatnak az iOS és OS X rendszerekhez készült SDK-k. Egy hiba miatt azonban sajnos jelenleg nem támogatjuk teljes mértékben az 1. honosítást. Ezen hiba miatt a portugál nyelv nem élvez teljes támogatást. A szövegek legnagyobb részét lefordították, a felhasználói felületet azonban nem.

    1. Portugál

    2. portugál (Portugália)

**csak iOS esetén**

-   Az RMS SDK 4.x-es verziói nem jelenítik meg a hálózati aktivitás jelzőt.

    Ez egy ismert választható működés iOS esetén, az Apple Human Interface Guidelines irányelveinek megfelelően.

**Csak OS X esetén**

-   Az RMS SDK 4.x-es verziói nem jelenítik meg a hálózati aktivitás jelzőt.

    Ez egy ismert választható működés OS X esetén, az Apple Human Interface Guidelines irányelveinek megfelelően.

-   **Megoldás** – Használja az alábbi útmutatót többdokumentumos felülettel (MDI) rendelkező alkalmazásnak az OS X SDK használatával történő létrehozásához.

    Az alábbi metódusok nem futtathatók egyszerre. A végrehajtás befejezésének figyeléséhez használja a befejezési tömbön alapuló megközelítést.

    - [**protectedDataWithProtectedFile**](/rights-management/sdk/4.2/api/iOS/msprotecteddata#msipcthin2_msprotecteddata_protecteddatawithprotectedfile_completionblock_method_objc)
    - [**customProtectedDataWithPolicy**](/rights-management/sdk/4.2/api/iOS/mscustomprotecteddata#msipcthin2_mscustomprotecteddata_customprotecteddatawithpolicy_protecteddata_contentstartposition_contentsize_completionblock_method_objc)



**Megjegyzés** Az iOS API nem támogatja az MDI-alkalmazásokat.

## Gyakori kérdések

**Összes platform**

**K**: Nem találom az **Egyéni engedélyek** kiválasztási felületet a védelmi munkafolyamatban. Mi lehet ennek az oka?

**V**: Ez egy ismert probléma, amelyet a későbbiekben kezelni fogunk.

**K**: Hogyan vehetek rá új szervezeti bérlőket az SDK és a mintaalkalmazások kipróbálására?

**V**: Hitelesítő adatok igényléséhez az Azure AD RMS-tesztszervezetekhez írjon e-mailt az <rmcstbeta@microsoft.com> címre.

**K**: Nem található tesztelési hierarchiára vonatkozó ismertető a jelen dokumentációban. Mi lehet ennek az oka?

**V**: Nincsen tesztelési hierarchiára vonatkozó koncepció az új AD RMS SDK-k esetében. Minden esetben az éles hierarchiával fog dolgozni.

**K**: Az RMS SDK 2.1-es verziójában egy létrehozott jegyzékre volt szükség az információvédelmet megvalósító alkalmazások mindegyike esetén. Ez továbbra is igaz az SDK 4.0-ls és újabb verzióiban?

**V**: Nem, a Rights Management SDK 3.0-s és újabb verzióiban már nem szükséges a jegyzék.

**Android**

**K**: Milyen fejlesztési környezetekben lett tesztelve az SDK?

**V**: A Google API 15 és újabb verziót használó Eclipse Juno.

**K**: Hívhatom a cancel() megszakítási metódust az UI-szálból?
**V**: A cancel() metódust nem UI-szálból célszerű hívni, mivel megszakíthatja a hálózati kapcsolatot.

**iOS**

**K**: Mely platformok lettek tanúsítva az SDK-fejlesztéshez?

**V**: Xcode 5.0 iOS 7 és újabb rendszerrel.

**K**: Meghívtam a cancel() metódust egy műveletre vonatkozóan, mégis értesítést kaptam arról, hogy a művelet befejeződött. Mi lehet ennek az oka?

**V**: Nem minden műveletet lehet megszakítani, ezért a megszakítási művelet végrehajtása a lehetőségeknek megfelelően történik.

**OS X**

**K**: A mintaalkalmazás keretrendszere az Xcode 5-ös verziójához lett alakítva, használhatom az Xcode 4.6-os verzióját?

**V**: Az OS X SDK csak Xcode 4.6-os és újabb verziókkal, valamint OS X 10.8-as és újabb verziókkal használható.

 

 



<!--HONumber=Jul16_HO4-->


