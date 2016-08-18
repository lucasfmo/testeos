---
title: "Címkék törlése és átrendezése az Azure Information Protectionben | Azure Rights Management"
description: 
author: cabailey
manager: mbaldwin
ms.date: 08/10/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: ae0f603f-a632-4ac5-a3f7-6358d4255eff
translationtype: Human Translation
ms.sourcegitcommit: b2263c212a1b869b778767493645f10ad821828f
ms.openlocfilehash: 3b4066c8e5770e6f4a502ecaebfd961400e9df2d


---

# Címkék törlése és átrendezése az Azure Information Protectionben

>*A következőkre vonatkozik: az Azure Information Protection előzetes verziója*

**[ Előzetes információ, a tartalma változhat. ]**

Az Information Protection menüsávján megjelenő címkéket törölheti vagy átrendezheti az Azure Information Protection-házirend konfigurálásával.

![Címkék törlése és átrendezése az Azure Information Protection-házirendben](../media/info-protect-contextmenu.png)

A címkék törlése helyett le is tilthatja azokat, így megtartja azok konfigurációját, de nem fognak megjelenni az Information Protection menüsávjában.

A címkéket célszerű logikai sorrendben rendezni az Information Protection menüsávján. A címkéket például rendezheti növekvő bizalmassági szint szerint, így a felhasználók a legkevésbé bizalmas címkét látják elsőként, és a leginkább bizalmasat utolsóként. Az [alapértelmezett házirend](configure-policy-default.md) ezt a konfigurációt használja.

> [!IMPORTANT]
>Ha olyan [feltételeket](configure-policy-classification.md) rendel a címkékhez, amelyek több címkére is vonatkozhatnak, a címkéket a legkevésbé bizalmastól a leginkább bizalmasig kell rendeznie. Ezzel biztosítja azt, hogy a feltételek értékelésekor a program a leginkább bizalmas címkét alkalmazza.


A módosítások végrehajtásához kövesse az alábbi utasításokat.

1. Ha még nem tette meg, jelentkezzen be az [Azure Portalra](https://portal.azure.com), majd lépjen az **Azure Information Protection** panelre. 
    
    A Központ menüben kattintson a **Tallózás** gombra, és kezdje el begépelni az **Information** szót a Szűrő mezőbe. Válassza az **Azure Information Protection** lehetőséget.

2. Az **Azure Information Protection** panelen végezze el az alábbi műveletek egyikét attól függően, hogy törölni, letiltani vagy átrendezni szeretné a címkéket:

    - Címke törlése: Kattintson a jobb gombbal a törölni kívánt címkére, vagy válassza ki a helyi menüt (**...**), majd kattintson a **Delete this label** (Címke törlése), végül pedig a **Yes** (Igen) lehetőségre. Ezután kattintson a **Save** (Mentés) gombra. 

    - Címke letiltása: Jelölje ki a letiltani kívánt címkét. A **Label** (Címke) panelen az **Enabled** (Engedélyezve) lehetőségnél kattintson az **Off** (Ki) elemre, majd a **Save** (Mentés) gombra.

    - Címke átrendezése: Kattintson a jobb gombbal az átrendezni kívánt címkére, vagy válassza ki a helyi menüt (**...**), majd kattintson többször a **Move up** (Eltolás felfelé) vagy a **Move down** (Eltolás lefelé) lehetőségre, amíg a címke a megfelelő helyre nem kerül. Ezután kattintson a **Save** (Mentés) gombra. 

3. A módosításokat az **Azure Information Protection** panel **Publish** (Közzététel) lehetőségével teheti elérhetővé a felhasználóknak.

## További lépések

További információt az Azure Information Protection-házirend konfigurálásáról a [Szervezet házirendjeinek konfigurálása](configure-policy.md#configuring-your-organization-s-policy) szakasz hivatkozásai között találhat.  





<!--HONumber=Aug16_HO2-->


