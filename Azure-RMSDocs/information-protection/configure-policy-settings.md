---
title: "Az Azure Information Protection globális házirendbeállításainak konfigurálása | Azure Rights Management"
description: 
author: cabailey
manager: mbaldwin
ms.date: 08/08/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 629815c0-457d-4697-a4cc-df0e6cc0c1a6
translationtype: Human Translation
ms.sourcegitcommit: b2263c212a1b869b778767493645f10ad821828f
ms.openlocfilehash: 508161474bf6fd7406668de3976206947de254de


---

# Az Azure Information Protection globális házirendbeállításainak konfigurálása

>*A következőkre vonatkozik: az Azure Information Protection előzetes verziója*

**[ Előzetes információ, a tartalma változhat. ]**

Az Azure Information Protection-házirend három, minden felhasználóra és eszközre vonatkozó beállítással rendelkezik:

![Az Azure Information Protection-házirend globális beállításai](../media/info-protect-policy-settings.png)


A beállítások konfigurálása:

1. Ha még nem tette meg, jelentkezzen be az [Azure Portalra](https://portal.azure.com), majd lépjen az **Azure Information Protection** panelre. 
    
    A Központ menüben kattintson a **Tallózás** gombra, és kezdje el begépelni az **Information** szót a Szűrő mezőbe. Válassza az **Azure Information Protection** lehetőséget.

2. Az a **Azure Information Protection** panelen konfigurálja az alábbi globális beállításokat:

    - **All documents and emails must have a label** (Minden dokumentumnak és e-mailnek rendelkeznie kell egy címkével): Ha a beállítás **be van kapcsolva**, minden mentett dokumentumot és elküldött e-mailt kötelező címkével ellátni. A címkék a felhasználók által manuálisan, a [feltételek](configure-policy-classification.md) által automatikusan, vagy alapértelmezés szerint hozzárendelhetők a dokumentumokhoz (a **Select the default label** (Alapértelmezett címke kiválasztása) beállítással). 

    Ha egy felhasználó megpróbál elmenteni egy címke nélküli dokumentumot vagy elküldeni egy címke nélküli e-mailt, a rendszer figyelmezteti, hogy kötelező megadnia egy címkét:

    ![Azure Information Protection megjelenő üzenet, ha az új besorolás alacsonyabb](../media/info-protect-enforce-label.png)

    - **Alapértelmezett címke kiválasztása**: Ezzel a beállítással megadhatja a címke nélküli dokumentumokhoz és e-mailekhez rendelendő címkét. Alcímkével rendelkező címke nem adható meg alapértelmezettként. 

    - **Users must provide justification when lowering the sensitivity level** (A felhasználóknak meg kell indokolniuk az bizalmassági szint csökkentését): Ha ez a beállítás **be van kapcsolva**, és egy felhasználó alacsonyabb bizalmassági szintre állítja egy meglévő dokumentum vagy e-mail címkéjét (például **Secretről** (Titkos) **Publicre** (Nyilvános)), a rendszer indoklást kér a felhasználótól. A felhasználó például elmagyarázhatja, hogy a dokumentum már nem tartalmaz bizalmas adatokat. A művelet és az indoklás bekerül a helyi Windows-eseménynaplójukba: **Alkalmazás** > **Microsoft Azure Information Protection**.  

    ![Azure Information Protection megjelenő üzenet, ha az új besorolás alacsonyabb](../media/info-protect-lower-justification.png)

    Ez a beállítás nem alkalmazható az alcímkékre.

3. A módosítások mentéséhez kattintson a **Save** (Mentés) gombra.

4. A módosításokat a **Publish** lehetőséggel teheti elérhetővé a felhasználók számára.

## További lépések

További információt az Azure Information Protection-házirend konfigurálásáról a [Szervezet házirendjeinek konfigurálása](configure-policy.md#configuring-your-organization-s-policy) szakasz hivatkozásai között találhat.  












<!--HONumber=Aug16_HO2-->


