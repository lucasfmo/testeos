---
# required metadata

title: Azure RMS gyors üzembe helyezési útmutató – 2. lépés | Azure RMS
description: A második lépése annak az oktatóanyagnak, amellyel gyorsan kipróbálhatja a szervezeténél a Microsoft Azure Rights Managementet csupán öt, 15 percnél gyorsabban végrehajtható lépéssel.
keywords:
author: cabailey
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: f32cf2f3-29e2-429c-a0fd-b16cc482484a

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: esaggese
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---



# Azure RMS gyors üzembe helyezés – 2. lépés: A Rights Management megosztóalkalmazás telepítése

*A következőkre vonatkozik: Azure Rights Management, Office 365*


Ugrás ide: 
> [!div class="op_single_selector"]
- [Bevezetés](quick-start-tutorial.md)
- [1. lépés: Az Azure RMS aktiválása](tutorial-step1.md)
- [2. lépés: Az RMS megosztóalkalmazás telepítése](tutorial-step2.md)
- [3. lépés: A bizalmas dokumentum elküldése e-mailben](tutorial-step3.md)
- [4. lépés: A címzett elolvassa a dokumentumot](tutorial-step4.md)
- [5. lépés: A dokumentum nyomon követése](tutorial-step5.md)


![Azure RMS gyors üzembe helyezési útmutató 2. lépés](../media/AzRMS_QuickStartSteps2.PNG)

A Rights Management megosztóalkalmazás (más néven az „RMS megosztóalkalmazás”) nem előfeltétele az Azure Rights Management használatának, de ajánlott kiegészítője az Azure Rights Managementet támogató összes számítógépnek és mobileszköznek. Az RMS megosztóalkalmazás az Office-alkalmazásokba integrálható egy Office-bővítmény telepítésével, így a felhasználók könnyedén, közvetlenül a menüszalagról védelemmel láthatják el a fájlokat. Az összes fájltípus védelmét is lehetővé teszi, és általános védelmet nyújt az olyan fájltípusokhoz, amelyeket az Azure Rights Management nem támogat natív módon, valamint egy dokumentumkövető webhelyet is biztosít a felhasználók számára, amelyen követhetik és visszavonhatják a védett fájlokat. Ebben az oktatóanyagban a későbbiekben használni fogjuk a dokumentumkövetést.

Ez az alkalmazás ingyenesen letölthető, és éles környezetekhez egy parancsfájlvezérelt telepítést biztosít. Ám ebben az oktatóanyagban helyileg telepítjük.

![Útmutató 2. lépésének képernyőképei](../media/AzRMS_Tutorial_2_Screenshots.png)

### A Rights Management megosztóalkalmazás letöltése és telepítése

1.  Lépjen a Microsoft webhelyének [Microsoft Rights Management](http://go.microsoft.com/fwlink/?LinkId=303970) lapjára.

2.  A **Számítógépek** szakaszban kattintson az **RMS alkalmazás Windows rendszerhez** ikonra, és mentse a **Setup.exe** fájlt a Microsoft Rights Management megosztóalkalmazás telepítéséhez.

3.  Helyi telepítéshez egy rendszergazdai fiókkal kell futtatnia a letöltött Setup.exe fájlt. Ha a rendszer a folytatás megerősítését kéri, kattintson az **Igen** gombra.

4.  **A Microsoft RMS telepítése** lapon kattintson a **Tovább** gombra, és várja meg a telepítés befejezését.

5.  A telepítés befejezése után kattintson az **Újraindítás** gombra, ha a rendszer kéri a számítógép újraindítását, vagy kattintson a **Bezárás** gombra a telepítés befejezéséhez.

Mostantól készen áll a csak az adott személyekkel megosztani kívánt információkat tartalmazó fájlok védelmére.

|Ha további információra van szüksége|További információ|
|--------------------------------|--------------------------|
|A Windows Rights Management megosztóalkalmazás helyi telepítésének információi és felhasználói utasítások|[A Rights Management megosztóalkalmazás felhasználói útmutatója](../rms-client/sharing-app-user-guide.md)|
|A Windows Rights Management megosztóalkalmazás parancsfájlalapú telepítésének információi és további műszaki adatok|[Rendszergazdai útmutató a Rights Management megosztóalkalmazáshoz](../rms-client/sharing-app-admin-guide.md)|
|A natív védelem és a általános védelem közötti különbségek megértése|[Mi a különbség az általános védelem és a beépített (natív) védelem között?](../rms-client/sharing-app-dialog-box.md#what-s-the-difference-between-generic-protection-and-built-in-native-protection-)|


>[!div class="step-by-step"] [« 1. lépés](quick-start-tutorial.md)
[3. lépés »](tutorial-step3.md)

<!--HONumber=May16_HO2-->


