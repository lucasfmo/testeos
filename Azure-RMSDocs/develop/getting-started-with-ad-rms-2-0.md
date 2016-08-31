---
title: "Első lépések | Azure RMS"
description: "Az RMS SDK 2.1 platform segítségével a fejlesztők olyan alkalmazásokat készíthetnek, amelyek az RMS adatvédelmét használják."
keywords: 
author: bruceperlerms
manager: mbaldwin
ms.date: 06/28/2016
ms.topic: article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 728113C9-FCF9-4280-BE1D-6AF5C15E449E
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 5d2339ece646fc51410186d43facdea28ac8fdfe
ms.openlocfilehash: 0f50bc77ba7a7f730dda5ef278f21a8d6f0311c4


---
# Első lépések

A Rights Management Services SDK 2.1 platform segítségével a fejlesztők olyan alkalmazásokat készíthetnek, amelyek az RMS adatvédelmét használják egy RMS-kiszolgáló vagy az Azure RMS révén. A platform kezeli az olyan összetett biztonsági eljárásokat, mint a kulcskezelés, a titkosítás és a visszafejtés, valamint egyszerűsített API-val segíti a könnyű alkalmazásfejlesztést.

## Ismerkedés az RMS SDK 2.1 szolgáltatással

Ez a témakör ismerteti a folyamatot, amellyel beállíthatja és futtathatja tartalomvédelemmel kompatibilis alkalmazását tesztkörnyezetben. Az alábbi témakörök a fejlesztési környezet beállítását ismertetik, és abban a sorrendben vannak felsorolva, amelyben a feladatokat ajánlott elvégezni.

## A szakasz tartalma

| Témakör | Leírás |
|-------|-------------|
| [Release Notes (Kibocsátási megjegyzések)](release-notes-rtm.md) | Ez a témakör fontos információkat tartalmaz az RMS SDK 2.1 jelenlegi és korábbi kiadásaival kapcsolatban.|
| [Az SDK telepítése](install-the-rms-sdk.md) | Ez a témakör végigvezeti a fejlesztői eszközök telepítésén.|
| [A Visual Studio konfigurálása](how-to-configure-a-visual-studio-project-to-use-the-ad-rms-sdk-2-0.md) | Ez a témakör a Visual Studio projekteknek az RMS SDK 2.1 használatára való konfigurálására vonatkozó utasításokat tartalmaz.|
| [Az alkalmazás fejlesztése](developing-your-application.md) | Ez a témakör alapvető útmutatással szolgál az RMS-kompatibilis alkalmazások legfontosabb aspektusairól, erre építkezve elkezdheti saját alkalmazásának fejlesztését.|
| [Az alkalmazás tesztelése](how-to-set-up-your-test-environment.md) |Ez a témakör az alkalmazás tesztelésének előkészítéséhez ad útmutatást.|
| [Éles üzembe helyezés](deploying-your-application.md) |Ez a témakör végigvezeti a tartalomvédelemmel kompatibilis alkalmazás üzembe helyezési lehetőségein.|


Próbálja ki az RMS SDK 2.1 használatát a következő témakörök útmutatása alapján:

- [Az SDK telepítése](install-the-rms-sdk.md)
- [A Visual Studio konfigurálása](how-to-configure-a-visual-studio-project-to-use-the-ad-rms-sdk-2-0.md)
- [Az alkalmazás fejlesztése](developing-your-application.md)
- [Az alkalmazás tesztelése](how-to-set-up-your-test-environment.md)
- [Éles üzembe helyezés](deploying-your-application.md)

### Miért érdemes az RMS SDK 2.1-et használni a tartalmak védelmére?

Azoknak a fejlesztőknek, akik RMS-támogatást kívánnak hozzáadni új és meglévő alkalmazásaikhoz, az RMS SDK 2.1 megkönnyíti a következőket:

-   Felügyelhető, kompatibilis és robusztus alkalmazások készítése, amelyek észlelik az RMS-t.
-   A felhasználói adatok állandó titkosítása. Az adatok a környezettől, az eszköztől és az operációs rendszertől függetlenül titkosítva maradnak.
-   A használati korlátozások széles választékának érvényesítése, például a bizalmas adatokról készített képernyőfelvételek megakadályozása.
-   A vállalat által felügyelt adatvédelmi szabályzatok támogatása.
-   Az elérhetővé váló új hitelesítési mechanizmusok és titkosítási algoritmusok támogatása.

Az RMS SDK 2.1 számos fontos ügyfél- és kiszolgálóplatformot támogat. További információ: [Támogatott platformok](supported-platforms.md).

## Alapelvek

**Egyszerűség** – Az AD RMS SDK 1.0 visszajelzései és használati mintáinak elemzéséből származó adatok alapján a legbonyolultabb programozási feladatok egyszerűbbé és automatikussá váltak. Az RMS SDK 2.1-es verziójával készített RMS-alkalmazásokhoz általában 5–10-szer kevesebb sornyi RMS-kód szükséges, mint az AD RMS SDK 1.0-s verziójával készített RMS-alkalmazásokhoz.
**Egyszeri megírás** – Az RMS SDK 2.1-es alkalmazások nem igényelnek kódváltoztatást vagy újrafordítást ahhoz, hogy működjenek a legújabb RMS-szolgáltatásokkal. Az új RMS-szolgáltatások rögtön elérhetővé válnak a meglévő alkalmazásban, amint hozzáadják őket az RMS-kiszolgálóhoz.
**Konzisztencia** – Az RMS SDK 2.1 megkönnyíti az olyan alkalmazások írását, amelyek minden alkalommal megfelelnek a különböző RMS-konfigurációknak. Jelentősen lecsökkenti továbbá az RMS felhasználói felületet, amelyet az alkalmazás fejlesztőjének létre kell hoznia. Ezzel segíti az egységes megjelenést és működést, valamint a felhasználói képzés szükségességét is csökkenti.

## Kapcsolódó témakörök

* [RMS fejlesztői útmutató](developers-guide.md)
* [AD RMS Developer's Corner (AD RMD fejlesztői blog)](http://blogs.msdn.com/b/rms/)

 

 



<!--HONumber=Aug16_HO4-->


