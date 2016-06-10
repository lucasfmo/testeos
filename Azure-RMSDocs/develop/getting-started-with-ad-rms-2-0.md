---
# required metadata

title: Első lépések | Azure RMS
description: Az RMS SDK 2.1 platform segítségével a fejlesztők olyan alkalmazásokat készíthetnek, amelyek az RMS adatvédelmét használják.
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 728113C9-FCF9-4280-BE1D-6AF5C15E449E
# optional metadata

#ROBOTS:
audience: developer
#ms.devlang:
ms.reviewer: shubhamp
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---
** Ez az SDK-tartalom nem naprakész. Ideiglenesen arra kérjük, keresse fel az MSDN webhelyén található dokumentáció [aktuális verzióját](https://msdn.microsoft.com/library/windows/desktop/hh535290(v=vs.85).aspx). **
# Első lépések

A Rights Management Services SDK 2.1 platform segítségével a fejlesztők olyan alkalmazásokat készíthetnek, amelyek az RMS adatvédelmét használják. A platform kezeli az olyan összetett biztonsági gyakorlatokat, mint a kulcskezelés, a titkosítás és a visszafejtés, valamint egyszerűsített API-val segíti a könnyű alkalmazásfejlesztést.

## Getting started with RMS SDK 2.1 (Ismerkedés az RMS SDK 2.1 szolgáltatással)

Olvassa el az alábbi szakaszokat:

-   Miért érdemes az RMS SDK 2.1-et használni a tartalmak védelmére
-   Alapelvek

Próbálja ki az RMS SDK 2.1 használatát a következő témakörök útmutatása alapján:

-   [Az SDK telepítése](create-your-first-rights-aware-application.md)
-   [A tartalomvédelemmel kompatibilis alkalmazás tesztelése](running-your-first-application.md)
-   [IPCHelloWorld - an example application (IPCHelloWorld – mintaalkalmazás)](how-to-build-your-first-application.md)

Miután megtette az első lépéseket, tekintse meg néhány további [RMS-mintánkat](samples.md). Ezután is naprakész maradhat az [RMS Developer's Corner](http://blogs.msdn.com/b/rms/) (AD RMD fejlesztői blog) segítségével.

### Miért érdemes az RMS SDK 2.1-et használni a tartalmak védelmére

Azoknak a fejlesztőknek, akik RMS-támogatást kívánnak hozzáadni új és meglévő alkalmazásaikhoz, az RMS SDK 2.1 megkönnyíti a következőket:

-   Felügyelhető, kompatibilis és robusztus alkalmazások készítése, amelyek észlelik az RMS-t.
-   A felhasználói adatok állandó titkosítása. Az adatok a környezettől, az eszköztől és az operációs rendszertől függetlenül titkosítva maradnak.
-   A használati korlátozások széles választékának érvényesítése, például a bizalmas adatokról készített képernyőfelvételek megakadályozását.
-   A vállalat által felügyelt adatvédelmi szabályzatok támogatása.
-   Az elérhetővé váló új hitelesítési mechanizmusok és titkosítási algoritmusok támogatása.

Az RMS SDK 2.1 számos fontos ügyfél- és kiszolgálóplatformot támogat. További információ: [Támogatott platformok](supported-platforms.md).

## Alapelvek

**Egyszerűség** – Az AD RMS SDK 1.0 visszajelzéseit és használati mintáinak elemzéséből származó adatok alapján a legbonyolultabb programozási feladatok egyszerűbbé és automatikussá váltak. Az RMS SDK 2.1-es verziójával készített RMS-alkalmazásokhoz általában 5-10-szer kevesebb sornyi RMS-kód szükséges, mint az AD RMS SDK 1.0-s verziójával készített RMS-alkalmazásokhoz.
**Egyszeri írás** – Az RMS SDK 2.1-es alkalmazások nem igényelnek kódváltoztatást vagy újrafordítást ahhoz, hogy működjenek a legújabb RMS-szolgáltatásokkal. Az új RMS-szolgáltatások rögtön elérhetővé válnak a meglévő alkalmazásban, amint hozzáadják őket az RMS-kiszolgálóhoz.
**Konzisztencia** – Az RMS SDK 2.1 megkönnyíti az olyan alkalmazások írását, amelyek minden alkalommal megfelelnek a különböző RMS-konfigurációknak. Jelentősen lecsökkenti továbbá az RMS felhasználói felületet, amelyet az alkalmazás fejlesztőjének létre kell hoznia. Ezzel segíti az egységes megjelenést és működést, valamint a felhasználói képzés szükségességét is csökkenti.

## Kapcsolódó témakörök

* [AD RMS samples (AD RMS-minták)](samples.md)
* [AD RMS Developer's Corner (AD RMD fejlesztői blog)](http://blogs.msdn.com/b/rms/)
* [Az SDK telepítése](create-your-first-rights-aware-application.md)
* [IPCHelloWorld - an example application (IPCHelloWorld – mintaalkalmazás)](how-to-build-your-first-application.md)
* [Áttekintés](ad-rms-overview.md)
* [Támogatott platformok](supported-platforms.md)
* [A tartalomvédelemmel kompatibilis alkalmazás tesztelése](running-your-first-application.md)
 

 





<!--HONumber=Jun16_HO1-->


