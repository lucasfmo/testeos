---
title: "Fájl védelmének eltávolítása a Rights Management megosztóalkalmazással | Azure RMS"
description: "Egy olyan fájl védelmének eltávolításához (vagyis egy fájl védelmének feloldásához), amelyet korábban az RMS megosztóalkalmazás védett, válassza a Védelem eltávolítása lehetőséget a Fájlkezelőből."
author: cabailey
manager: mbaldwin
ms.date: 07/13/2016
ms.topic: article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: da95b938-eaad-4c83-a21e-ff1d4872aae4
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 26b043f1f9e7a1e0cd00c2f31c28f7d6685f0232
ms.openlocfilehash: b94cd999fef2186ddf67a0e6cebc3349a3586538


---

# Fájl védelmének eltávolítása a Rights Management megosztóalkalmazással

>*A következőkre vonatkozik: Active Directory tartalomvédelmi szolgáltatások, Azure Rights Management, Windows 10, Windows 7 SP1, Windows 8, Windows 8.1*

Egy olyan fájl védelmének eltávolításához (vagyis egy fájl védelmének feloldásához), amelyet korábban az RMS megosztóalkalmazás védett, válassza a **Védelem eltávolítása** lehetőséget a Fájlkezelőből.

> [!IMPORTANT]
> A védelem eltávolításához a fájl tulajdonosának kell lennie.

## Fájl védelmének eltávolítása

1.  A Fájlkezelőben kattintson a jobb gombbal a fájlra (például a Minta.ptxt fájlra), válassza a **Védelem az RMS-sel** elemet, és kattintson a **Helyi védelem**, majd a **Védelem eltávolítása** menüpontra:

    ![Védelem eltávolítása menüpont az RMS megosztóalkalmazáshoz](../media/ADRMS_MSRMSApp_RemoveProtection.png)

    Előfordulhat, hogy az alkalmazás kéri a hitelesítő adatok megadását.

Megjegyzés: Ha nem látja ezeket a beállítási lehetőségeket, akkor valószínű, hogy az RMS megosztóalkalmazás nincs telepítve a számítógépre, nem a legújabb változata van telepítve, vagy a számítógépet újra kell indítani a telepítés befejezéséhez. További információ a megosztóalkalmazás telepítésével kapcsolatban: [A Rights Management megosztóalkalmazás letöltése és telepítése](install-sharing-app.md).

A rendszer törli az eredeti védett fájlt (például a Minta.ptxt fájlt), és lecseréli egy ugyanolyan nevű, de nem védett fájlkiterjesztésű fájllal (például a Minta.txt fájllal).

## Példák és egyéb útmutatók
A Rights Management megosztóalkalmazás használatát szemléltető egyéb példák és útmutatók a Rights Management megosztóalkalmazás felhasználói útmutatójának következő szakaszaiban találhatók:

-   [Példák az RMS-megosztó alkalmazás használatára](sharing-app-user-guide.md#examples-for-using-the-rms-sharing-application)

-   [Művelet](sharing-app-user-guide.md#what-do-you-want-to-do)

## Lásd még:
[A Rights Management megosztóalkalmazás felhasználói útmutatója](sharing-app-user-guide.md)



<!--HONumber=Aug16_HO4-->


