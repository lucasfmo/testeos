---
title: "Azure Information Protection gyors üzembe helyezési útmutató – 3. lépés | Azure Rights Management"
description: "Egy bevezető oktatóanyag 3. lépése, amellyel gyorsan kipróbálhatja a szervezeténél a Microsoft Azure Information Protection szolgáltatást csupán 4, 15 percnél gyorsabban végrehajtható lépésben."
author: cabailey
manager: mbaldwin
ms.date: 07/29/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 209815b9-81c9-430c-a82f-32cac991449b
translationtype: Human Translation
ms.sourcegitcommit: 93444affe94b280db2c9e4e2960c6902e491dec6
ms.openlocfilehash: 65596a71b07e830377c55dc04b7187251315a634


---

# 3. lépés: Az Azure Information Protection-ügyfél telepítése 

>*A következőkre vonatkozik: az Azure Information Protection előzetes verziója*

**[ Előzetes információ, a tartalma változhat. ]**

E lépés során telepíteni kell az Azure Information Protection-ügyfelet, hogy az előzőekben konfigurált szabályzatot letölthesse egy Windows rendszerű számítógépre, és megjeleníthesse a címkéket egy Office-alkalmazásban. 

1. [Töltse le az Azure Information Protection-ügyfelet](https://www.microsoft.com/en-us/download/details.aspx?id=53018) a Microsoft letöltőközpontból egy olyan számítógépre, melyen telepítve van az Office (de nincs megnyitva a Word). 

2. Futtassa az **AZInfoProtection.exe** fájlt, és kövesse az ügyfél telepítéséhez szükséges lépéseket.

    Ebben az oktatóanyagban nem számít, ha egy bemutató szabályzatot telepít, mivel az előző lépés során létrehozott házirend az Azure-portálról letöltve felülírja a most telepített bemutató szabályzatot. Akkor is érdemes a bemutató szabályzatot telepíteni, ha csak szeretné kipróbálni az alapértelmezett címkéket anélkül, hogy kapcsolódna az Azure Information Protection szolgáltatáshoz. 

3. Indítsa el a Word alkalmazást, és nyisson meg egy új, üres dokumentumot az ügyfél telepítésének ellenőrzéséhez. Egyelőre ne mentse a dokumentumot. Ha a rendszer kéri, adja meg globális rendszergazdai fiókjának felhasználónevét és jelszavát. A dokumentum betöltése után két újdonságot vehet észre:

    - A **Kezdőlap** lapon megjelent egy új, **Protection** nevű csoport és a **Protect** (Védelem) nevű gomb.

        Kattintson a **Protect** > **Help and feedback** (Védelem > Súgó és visszajelzés) lehetőségre, és a megnyíló **Microsoft Azure Information Protection** párbeszédpanelen erősítse meg ügyfélállapotát. Ekkor megjelenik **Information Protection policy is installed** (Az Information Protection-szabályzat telepítése befejeződött) üzenet, és a legutóbbi kapcsolat ideje. Győződjön meg arról, hogy a megfelelő bérlő felhasználóneve jelenik meg.

    - A menüszalag alatt megjelenik az Information Protection menüsávja. A sávon található a **Sensitivity** (Érzékenység) címe és az alapértelmezett címke (ebben az esetben az **Internal** (Belső) címke). 


![Azure Information Protection gyors üzembe helyezési útmutató – 3. lépés: A telepített ügyfél](../media/word2013-callouts.png)

Most már elvégezheti az utolsó lépést, a besorolás, a címkézés és a védelem működésének ellenőrzését.

|Ha további információra van szüksége|További információ|
|--------------------------------|--------------------------|
|Az ügyfél telepítése|[Az Azure Information Protection-ügyfél telepítése](info-protect-client.md)|


>[!div class="step-by-step"]
[&#171; 2. lépés](infoprotect-tutorial-step2.md)
[4. lépés &#187;](infoprotect-tutorial-step4.md)


<!--HONumber=Jul16_HO5-->


