---
title: "Azure Information Protection – gyors üzembe helyezési útmutató – 2. lépés | Azure Rights Management"
description: "Egy bevezető oktatóanyag 2. lépése, amellyel gyorsan kipróbálhatja a szervezetnél a Microsoft Azure Information Protection szolgáltatást csupán 4, 15 percnél gyorsabban végrehajtható lépésben."
author: cabailey
manager: mbaldwin
ms.date: 07/29/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 3bc193c2-0be0-4c8e-8910-5d2cee5b14f7
translationtype: Human Translation
ms.sourcegitcommit: cab45baf19af4ab548f5f112946d168d93a95d49
ms.openlocfilehash: fa17a5b18162ca7ca1ac0cf9a1052dd01d2057aa


---

# 2. lépés: Az Azure Information Protection-szabályzat konfigurálása és közzététele

>*A következőkre vonatkozik: az Azure Information Protection előzetes verziója*

**[ Előzetes információ, a tartalma változhat. ]**

Bár az Azure Information Protection alapértelmezett szabályzata konfiguráció nélkül is használható, az oktatóanyagban módosítjuk majd.

1. Jelentkezzen be az [Azure portálra](https://portal.azure.com).
 
2. A menüben kattintson a **Tallózás** gombra, és kezdje el begépelni az **Information** szót a Szűrő mezőbe. Válassza az **Azure Information Protection** lehetőséget.

- A megjelenő fő **Azure Information Protection** panelen található az automatikusan létrejött alapértelmezett Information Protection-szabályzat. Az alapértelmezett szabályzat a következő besorolási címkéket tartalmazza: **Personal** (Személyes), **Public** (Nyilvános), **Internal** (Belső), **Confidential** (Bizalmas) és **Secret** (Titkos). A címkék használatáról olvassa el a hozzájuk tartozó elemleírásokat. A **Secret** címkéhez két alárendelt címke is tartozik: **All-Employees** (Minden alkalmazott) és **My-Group** (Saját csoport). Ez jól szemlélteti, hogy egy besorolásnak alkategóriái is lehetnek.

- Az **Internal**, **Confidential** és **Secret** címkéhez alapértelmezés szerint vizuális jelölések tartoznak (például lábléc, fejléc vagy vízjel), azonban egyik címkéhez sincs beállítva védelem. Emellett nincs megadva a három globális beállítás, így nem szükséges minden dokumentumhoz és e-mailhez címkét adni. Nincs alapértelmezett címke sem, a felhasználóknak pedig nem kell megindokolniuk az érzékenységi szint csökkentését.

    ![Azure Information Protection – gyors üzembe helyezési útmutató – 3. lépés: Alapértelmezett szabályzat](../media/info-protect-policy.png)

A jelen oktatóanyagban módosítani fogjuk a globális beállítások némelyikét, hogy megfigyelhesse, hogyan működnek:

-  **Select the default label** (Alapértelmezett címke kiválasztása): Állítsa **Internal** (Belső) értékre.

- **Users must provide justification when lowering the sensitivity level** (A felhasználóknak meg kell indokolniuk az érzékenységi szint csökkentését): Állítsa **On** (Be) állásra.

Most a **Confidential** (Bizalmas) címke beállításait módosítjuk:

1. Kattintson a **Confidential** címkebejegyzésre.

2. A **Label: Confidential** (Címke: Bizalmas) panelen láthatók az egyes címkékhez elérhető beállítások. Hajtsa végre az alábbi módosításokat:

    a. Ha aktiválta az Azure Rights Managmentet, a **Set RMS template for protecting documents and emails containing this label** (RMS-sablon beállítása az ezt a címkét tartalmazó dokumentumok és e-mailek védelméhez) szakasznál megjelenik a **Select RMS template from** (RMS-sablon kiválasztása innen) beállítás: itt tartsa meg az alapértelmezett, **Azure RMS**-beállítást. Ez után a **Select RMS template** (RMS-sablon kiválasztása) területen kattintson a legördülő listára, és alapértelmezett sablonként válassza a **\<szervezet neve> - Confidential** (Bizalmas) lehetőséget. Ha a szervezet neve például VanArsdel, Ltd, keresse meg és válassza a **VanArsdel, Ltd - Confidential** elemet. Ha letiltotta ezt az alapértelmezett Azure Rights Management-sablont, válasszon egy másikat. Ha azonban részlegszintű sablont választ, győződjön meg arról, hogy az Ön fiókja is megtalálható a hatókörben.
    
    Ha nem aktiválta az Azure Rights Managementet, ez a beállítás nem érhető el.
    
    b. Állítsa a **Documents with this label have a watermark** (Az ezzel a címkével ellátott dokumentumok vízjellel jelenjenek meg) lehetőséget **On** (Be) állásra, majd adja meg a szervezet nevét a **Text** (Szöveg) mezőben. Például **VanArsdel, Ltd**. 
    
    c. Kattintson az **Add a new condition** (Új feltétel hozzáadása) hivatkozásra, majd a **Condition** (Feltétel) panelen válassza az alábbi lehetőségeket:
    
    - **Choose the type of condition** (A feltételtípus megadása): **Built-in** (Beépített)
    
    - **Select built-in** (Beépített feltétel kiválasztása): **Credit Card Number** (Hitelkártyaszám)
    
    - **Minimum number of occurrences** (Az előfordulások minimális száma): **1**
    
    - **Count occurrences with unique values only** (Csak az egyedi értékkel ellátott előfordulások száma): **bekapcsolva**
    
    - A **Save** (Mentés) gombra kattintva térjen vissza a **Label: Confidential** panelre.

3. A **Label: Confidential** panelen láthatja, hogy a **Credit Card Number** feltétel megjelent a **CONDITION NAME** (A FELTÉTEL NEVE) területen, és hogy az **OCCURRENCES** (ELŐFORDULÁSOK) paraméter értéke **1**.

4. **Select how this label is applied** (Válassza ki, hogyan legyen alkalmazva a címke): **Recommended** (Javasolt). Ezt a beállítást hagyja változatlanul.

5. Az **Enter notes for internal housekeeping** (Megjegyzések a belső karbantartáshoz) mezőbe írja be a **For testing purposes only** (Csak tesztelési célokra) mondatot.

6. A **Label: Confidential** panelen kattintson a **Save** gombra, majd a fő **Azure Information Protection** panelen szintén a **Save** gombra.

7. Elvégeztük a szükséges módosításokat és mentettük azokat. Következő lépésként elérhetővé kell tenni őket a felhasználók számára. Kattintson a **Publish** (Közzététel) lehetőségre, majd megerősítésként a **Yes** (Igen) gombra.

![Azure Information Protection – gyors üzembe helyezési útmutató – 3. lépés: Az alapértelmezett szabályzat konfigurálva](../media/info-protect-policy-configured.png)

Most bezárhatja az Azure portált, de ha nyitva hagyja, az oktatóanyag befejezése után akár további konfigurációs lehetőségeket is kipróbálhat.

Az útmutató második lépéseként megtekintette az alapértelmezett szabályzatot és elvégzett néhány módosítást. A következőkben telepíteni fogja az Azure Information Protection-ügyfelet.

|Ha további információra van szüksége|További információ|
|--------------------------------|--------------------------|
|A házirend konfigurációs beállításai|[Az Azure Information Protection-házirend konfigurálása](configure-policy.md)|


>[!div class="step-by-step"]
[&#171; 1. lépés](infoprotect-tutorial-step1.md)
[3. lépés &#187;](infoprotect-tutorial-step3.md)


<!--HONumber=Jul16_HO5-->


