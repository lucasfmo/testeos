---
title: "Az Azure Information Protection globális házirendbeállításainak konfigurálása | Azure Rights Management"
description: 
author: cabailey
manager: mbaldwin
ms.date: 07/29/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 629815c0-457d-4697-a4cc-df0e6cc0c1a6
translationtype: Human Translation
ms.sourcegitcommit: 93444affe94b280db2c9e4e2960c6902e491dec6
ms.openlocfilehash: 3b22cf76f03a4d36281db7e705359402dcbbde0e


---

# Az Azure Information Protection globális házirendbeállításainak konfigurálása

>*A következőkre vonatkozik: az Azure Information Protection előzetes verziója*

**[ Előzetes információ, a tartalma változhat. ]**

Az Azure Information Protection-házirend három, minden felhasználóra és eszközre vonatkozó beállítással rendelkezik:

![Az Azure Information Protection-házirend globális beállításai](../media/info-protect-policy-settings.png)


A beállítások konfigurálása:

1. Jelentkezzen be az [Azure portálra](https://portal.azure.com).
 
2. A menüben kattintson a **Tallózás** gombra, és kezdje el begépelni az **Information** szót a Szűrő mezőbe. Válassza az **Azure Information Protection** lehetőséget.

3. Az a **Azure Information Protection** panelen konfigurálja az alábbi globális beállításokat:

    - **All documents and emails must have a label** (Minden dokumentumnak és e-mailnek rendelkeznie kell egy címkével): Ha a beállítás **be van kapcsolva**, minden mentett dokumentumot és elküldött e-mailt kötelező címkével ellátni. A címkék a felhasználók által manuálisan, a [feltételek](configure-policy-classification.md) által automatikusan, vagy alapértelmezés szerint hozzárendelhetők a dokumentumokhoz (a **Select the default label** (Alapértelmezett címke kiválasztása) beállítással). 

    Ha egy felhasználó megpróbál elmenteni egy címke nélküli dokumentumot vagy elküldeni egy címke nélküli e-mailt, a rendszer figyelmezteti, hogy kötelező megadnia egy címkét:

    ![Azure Information Protection megjelenő üzenet, ha az új besorolás alacsonyabb](../media/info-protect-enforce-label.png)

    - **Alapértelmezett címke kiválasztása**: Ezzel a beállítással megadhatja a címke nélküli dokumentumokhoz és e-mailekhez rendelendő címkét. Alcímkével rendelkező címke nem adható meg alapértelmezettként. 

    - **Users must provide justification when lowering the sensitivity level** (A felhasználóknak meg kell indokolniuk az bizalmassági szint csökkentését): Ha ez a beállítás **be van kapcsolva**, és egy felhasználó alacsonyabb bizalmassági szintre állítja egy meglévő dokumentum vagy e-mail címkéjét (például **Secretről** (Titkos) **Publicre** (Nyilvános)), a rendszer indoklást kér a felhasználótól. A felhasználó például elmagyarázhatja, hogy a dokumentum már nem tartalmaz bizalmas adatokat. A művelet és az indoklás bekerül a helyi Windows-eseménynaplójukba: **Alkalmazás** > **Microsoft Azure Information Protection**.  

    ![Azure Information Protection megjelenő üzenet, ha az új besorolás alacsonyabb](../media/info-protect-lower-justification.png)

    Ez a beállítás nem alkalmazható az alcímkékre.

4. A módosítások mentéséhez kattintson a **Save** (Mentés) gombra.

5. A módosításokat a **Publish** lehetőséggel teheti elérhetővé a felhasználók számára.

## További lépések

További információt az Azure Information Protection-házirend konfigurálásáról a [Szervezet házirendjeinek konfigurálása](configure-policy.md#configuring-your-organization-s-policy) szakasz hivatkozásai között találhat.  












<!--HONumber=Jul16_HO5-->


