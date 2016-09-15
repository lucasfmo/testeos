---
title: "Azure Information Protection gyors üzembe helyezési útmutató – 4. lépés | Azure Rights Management"
description: "Egy bevezető oktatóanyag 4. lépése, amellyel gyorsan kipróbálhatja a szervezeténél a Microsoft Azure Information Protection szolgáltatást csupán 4, 15 percnél gyorsabban végrehajtható lépésben."
author: cabailey
manager: mbaldwin
ms.date: 08/10/2016
ms.topic: article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 468748c1-49d6-4c3e-a612-9c584acdc782
translationtype: Human Translation
ms.sourcegitcommit: c9f9211e7c1dcf293caf81475515114b5433d6a7
ms.openlocfilehash: 6d93723a6f7aaffec8d18cf289bff0752b53a2c9


---

# 4. lépés: A besorolás, címkézés és védelem használata 

>*A következőkre vonatkozik: az Azure Information Protection előzetes verziója*

**[ Előzetes információ, a tartalma változhat. ]**

Az előző lépés során telepítette az Azure Information Protection-ügyfelet és megnyitott egy Word-dokumentumot. Az alábbiakban bemutatjuk, hogy a konfigurált szabályzattal milyen egyszerűen elvégezheti a dokumentum címkézését és védelmét.

A besorolás és a védelem a dokumentum mentésekor lép érvénybe, de előtte még a nem mentett dokumentumon ismertetjük a címkék elhelyezését és módosítását.

### Az alapértelmezett címke manuális módosítása:

- Az Information Protection menüsávon válassza a **Personal (Személyes)** címkét. Ekkor a rendszer felkéri, hogy adja meg a besorolási szint csökkentésének okát. Válassza **This file no longer requires that classification** (A fájlnak már nincs szüksége erre a besorolásra) lehetőséget, majd kattintson a **Confirm** (Megerősítés) gombra.  

    A **Sensitivity** (Érzékenység) ekkor **Personal** (Személyes) értékre módosul.

    ![Azure Information Protection gyors üzembe helyezési útmutató – 4. lépés: A besorolási szint csökkentésének okát igazoló ablak](../media/confirm-lowering.png)

### A besorolás teljes eltávolítása:

- Az Information Protection menüsávon kattintson a **Personal** elem mellett található **Edit label** (Címke szerkesztése) ikonra. Ekkor megjelennek az elérhető címkék. Ezúttal valamelyik címke helyett válassza a **Remove label** (Címke eltávolítása) ikont. A művelet megerősítéséhez kattintson az **OK** gombra, majd adja meg a művelet indokát.  

    A **Sensitivity** (Érzékenység) ezután **Not set** (Nincs beállítva) értékre módosul. Ez jelenik meg a felhasználók számára, ha nem állít be alapértelmezett címkét.

    ![Azure Information Protection gyors üzembe helyezési útmutató – 4. lépés: Besorolás eltávolítása](../media/sensitivity-not-set.png)


### A címkézésre és védelemre irányuló javaslatok megtekintése:

1. Írjon be a Word-dokumentumba egy érvényes hitelkártyaszámot, például: **4242-4242-4242-4242**. 

2. Mentse a dokumentumot (bármilyen néven, bármely helyre). 

3. Ekkor megjelenik a következő üzenet: **It is recommended to label this file as Confidential** (Javasoljuk, hogy a fájl címkéjét állítsa Bizalmas értékre). Kattintson a **Change now** (Módosítás) gombra.

    ![Azure Information Protection gyors üzembe helyezési útmutató – 4. lépés: Javaslat](../media/change-now.png)

    A szervezet nevének vízjele azonnal megjelenik a lapon, a láblécben pedig feltűnik a **Sensitivity: Confidential** (Érzékenység: Bizalmas) szöveg. 

    Ha korábban RMS-sablont alkalmazott, a dokumentumot a megadott Azure Rights Management-sablon is védi. Ha szeretné ellenőrizni az RMS-védelmet, kattintson a **Fájl** lapra, és tekintse át a **Dokumentumvédelem** adatait. Ha az alapértelmezett Confidential (Bizalmas) sablont használta, a rendszer jelzi, hogy a dokumentumot csak a belső felhasználók érhetik el (a szervezeten kívüli felhasználók nem tudják megnyitni), a tartalmát pedig nem lehet lemásolni, illetve kinyomtatni. Tulajdonosként Ön lemásolhatja és kinyomtathatja a dokumentumot, ha azonban e-mailben elküldi a szervezet egy másik felhasználójának, ő már nem tudja elvégezni ezeket a műveleteket.

> [!NOTE]
>Ha nem sikerül elvégezni a fenti lépéseket, a **Kezdőlap** lap **Protection** csoportjában kattintson a **Protect** (Védelem) > **Help and feedback** (Súgó és visszajelzés) lehetőségre. 
>
>A **Microsoft Azure Information Protection** párbeszédpanelen kattintson a **Send feedback** (Visszajelzés küldése) elemre. Ezzel e-mailt küld az Information Protection-csapatnak, és automatikusan csatolja a naplófájlokat a számítógépről a probléma diagnosztizálása érdekében.

##  További lépések

A fentiekben bemutattuk az alapértelmezett Azure Information Protection-szabályzatot, a személyre szabási lehetőségeket, valamint a Word-dokumentumok címkézésének módját. Próbáljon ki további beállításokat is, és kísérletezzen velük az Azure Information Protection szolgáltatást támogató többi Office-alkalmazásban (például: Excel, PowerPoint és Outlook). Ha az Azure Information Protection telepítésekor meg voltak nyitva ezek az alkalmazások, zárja be, majd nyissa meg őket újra, mielőtt használná velük az Azure Information Protection szolgáltatást.

Az Information Protection menüsávon például egy tetszőleges címre módosíthatja a **Sensitivity** (Érzékenység) alapértelmezett címét. Megváltoztathatja az elemleírásokat, valamint a címkék színét, sorrendjét és nevét. Új címkéket hozhat létre, és saját automatikus szabályokat határozhat meg. Személyre szabhatja a vízjeleket: megadhatja a méretüket és a színüket, illetve átlós helyzetből vízszintesre állíthatja őket.

Ne feledje, hogy az Excelben használt vízjelek csak Oldalkép és Nyomtatási kép nézetben, illetve kinyomtatva láthatók.

Ha az Azure-portálon módosítja az Information Protection-szabályzat beállításait, ne felejtse el **menteni**, majd **közzétenni** a szabályzatot. Mivel egyszerre több panelen hajtja végre a módosításokat, célszerű ellenőrizni, hogy egyik panelen sem aktív-e a **Mentés** gomb, ami nem mentett módosításokat jelent. Ha megnyitott Office-alkalmazás mellett tette közzé a módosításokat, zárja be az alkalmazást, majd nyissa meg újra, hogy a program letölthesse a legújabb szabályzatot.

Amikor elkészült a teszteléssel, javasoljuk, hogy tekintse át [az Azure Information Protection szolgáltatással kapcsolatos gyakori kérdéseket](faq.md).




<!--HONumber=Aug16_HO4-->


