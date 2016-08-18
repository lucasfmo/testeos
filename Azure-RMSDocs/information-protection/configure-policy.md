---
title: "Az Azure Information Protection-házirend konfigurálása | Azure RMS"
description: 
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 08/08/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: ba0e8119-886c-4830-bd26-f98fb14b2933
ms.reviewer: eymanor
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 781632c5a28377339431cd6537b1b9e11d0a3259
ms.openlocfilehash: 0e31053a83c30d8552cfb78914d0d13baac25f42


---

# Az Azure Information Protection-házirend konfigurálása

>*A következőkre vonatkozik: az Azure Information Protection előzetes verziója*

**[ Előzetes információ, a tartalma változhat. ]**

A besorolás, a címkézés és a védelem konfigurálásához először konfigurálnia kell az Azure Information Protection-házirendet. Ezt követően a házirend letöltődik minden olyan számítógépre, amelyen telepítve van az [Azure Information Protection-ügyfél](https://www.microsoft.com/en-us/download/details.aspx?id=53018).

Az Azure Information Protection-házirend konfigurálása az előzetes verzióban:

1. Jelentkezzen be az [Azure portálra](https://portal.azure.com).

2. Navigáljon az **Azure Information Protection** panelre: például a Központ menüben kattintson a **Tallózás** gombra, és kezdje el begépelni az **Information Protection** kifejezést a Szűrő mezőbe. A találatokban kattintson az **Azure Information Protection** elemre. 

    Ekkor megjelenik az **Azure Information Protection** panel, ahol konfigurálhatja az Azure Information Protection-házirendet, amely az alábbi elemeket tartalmazza:

    - A felhasználók Office-alkalmazásaiban megjelenő Information Protection menüsáv címe és elemleírása.

    - A dokumentumok és e-mailek besorolására használható címkék.

    - A besorolás kényszerítése a felhasználói dokumentumok mentésekor és e-mailek elküldésekor beállítás.

    - Az alapértelmezett címke kezdőpontként való használata a dokumentumok és e-mailek besorolásakor beállítás.

    - A felhasználóknak meg kell indokolniuk az eredetinél alacsonyabb bizalmassági szintű címke választását beállítás.


Az Azure Information Protection rendelkezik egy [alapértelmezett házirenddel](configure-policy-default.md), amely a **Személyes**, **Nyilvános**, **Belső**, **Bizalmas** és **Titkos** címkéket tartalmazza. Az alapértelmezett címkéket alkalmazhatja eredeti állapotukban, de személyre is szabhatja őket, vagy kitörlésük után újakat hozhat létre helyettük.

Az Azure Information Protection panelen végzett módosításokat a **Save** (Mentés) gombbal mentheti, a **Discard** (Elvetés) gombbal pedig visszaállíthatja azokat a legutóbb mentett állapotra. 

A módosítások elvégzése után kattintson a **Publish** (Közzététel) gombra. 

Az Azure Information Protection-ügyfél a támogatott Office-alkalmazások indításakor ellenőrzi, hogy történt-e módosítás, és letölti azokat az Azure Information Protection-házirendbe.

## A szervezeti házirend konfigurálása

Az alábbi témakörök segítségével konfigurálhatja az Azure Information Protection-házirendet:

- [The default Information Protection policy (Az alapértelmezett Information Protection-házirend)](configure-policy-default.md)

- [How to configure the global policy settings (A globális házirendbeállítások konfigurálása)](configure-policy-settings.md)

- [How to create a new label (Új címke létrehozása)](configure-policy-new-label.md)

- [How to delete or reorder a label (Címkék törlése és átrendezése)](configure-policy-delete-reorder.md)

- [How to change or customize an existing label (Meglévő címke módosítása és testreszabása)](configure-policy-change-label.md)

- [How to configure a label to apply protection (Címke konfigurálása az adatvédelemhez)](configure-policy-protection.md)

- [How to configure a label to apply visual markings (Címke konfigurálása vizuális megjelöléshez)](configure-policy-markings.md)

- [How to configure conditions for automatic and recommended classification (Automatikus és javasolt besorolási feltételek konfigurálása)](configure-policy-classification.md)

## További lépések

Az alapértelmezett házirend testreszabásáról és az Office-alkalmazásokban való viselkedésről az [Azure Information Protection – gyors üzembe helyezési útmutatóban](infoprotect-quick-start-tutorial.md) találhat példát.




<!--HONumber=Aug16_HO2-->


