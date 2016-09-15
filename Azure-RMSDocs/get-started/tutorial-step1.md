---
title: "Azure RMS gyors üzembe helyezési útmutató – 1. lépés | Azure RMS"
description: "Az első lépése annak az oktatóanyagnak, amellyel gyorsan kipróbálhatja a szervezeténél a Microsoft Azure Rights Managementet csupán öt, 15 percnél gyorsabban végrehajtható lépéssel."
keywords: 
author: Cabailey
manager: mbaldwin
ms.date: 06/29/2016
ms.topic: get-started-article
ms.prod: 
ms.service: rights-management
ms.assetid: 7c4798e6-34a0-4c3f-a47f-505764ddf322
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 26b043f1f9e7a1e0cd00c2f31c28f7d6685f0232
ms.openlocfilehash: c00264e6c8b99d95e8eedf9b91781484611880c3


---



# Azure RMS gyors üzembe helyezés – 1. lépés: A Rights Management szolgáltatás aktiválása

>*A következőkre vonatkozik: Azure Rights Management, Office 365*


Ugrás ide: 
> [!div class="op_single_selector"]
- [Bevezetés](quick-start-tutorial.md)
- [1. lépés: Az Azure RMS aktiválása](tutorial-step1.md)
- [2. lépés: Az RMS megosztóalkalmazás telepítése](tutorial-step2.md)
- [3. lépés: A bizalmas dokumentum elküldése e-mailben](tutorial-step3.md)
- [4. lépés: A címzett elolvassa a dokumentumot](tutorial-step4.md)
- [5. lépés: A dokumentum nyomon követése](tutorial-step5.md)


![Azure RMS gyors üzembe helyezési útmutató – 1. lépés](../media/AzRMS_QuickStartSteps1.PNG)

A szolgáltatás alapértelmezés szerint akkor is le van tiltva, ha rendelkezik az Azure Rights Managementet támogató előfizetéssel. A szolgáltatás aktiválásához használhatja az Office 365 Felügyeleti központot vagy a klasszikus Azure-portált:

-   Ha olyan Office 365-előfizetéssel rendelkezik, amely tartalmazza az Azure Rights Managementet, illetve olyan Office 365-előfizetéssel, amely nem tartalmazza az Azure Rights Managementet, de rendelkezik Azure RMS Premium előfizetéssel: **Használja az Office 365 Felügyeleti központot**.

-   Ha nem rendelkezik Office 365-előfizetéssel: **Használja a klasszikus Azure-portált**.

![Útmutató 1. lépésének pillanatképei](../media/AzRMS_Tutorial_1_Screenshots.png)

### A Rights Management aktiválása a klasszikus Office 365 Felügyeleti központban

> [!NOTE]
> Ha az Office 365 felügyeleti központjának klasszikus verziója helyett az **Office 365 felügyeleti központ előzetes verzióját** használja, követheti [Az Azure Rights Management aktiválása az Office 365 Felügyeleti központ előzetes verziójából](../deploy-use/activate-office365-preview.md) dokumentumban leírt utasításokat is, vagy átválthat a klasszikus verzióra, és használhatja ezeket az utasításokat. A váltáshoz a bejelentkezés után kattintson a **Kezdőlap** lapon az **Ugrás a régi felügyeleti központra** lehetőségre.

1.  Nyissa meg az [Office 365 portált](https://portal.office.com/), és jelentkezzen be Office 365 globális rendszergazdai fiókjával.

2.  Ha az Office 365 Felügyeleti központ nem jelenik meg automatikusan, kattintson az alkalmazás indítóikonjára a bal felső sarokban, és válassza a **Rendszergazda** elemet. A **Rendszergazda** csempe csak az Office 365-rendszergazdák számára jelenik meg.

    > [!TIP]
    > A Felügyeleti központtal kapcsolatos segítségért tekintse meg [Az Office 365 Felügyeleti központ bemutatása – rendszergazdai súgó](https://support.office.com/article/About-the-Office-365-admin-center-Admin-Help-58537702-d421-4d02-8141-e128e3703547) című témakört.

3.  A bal oldali panelen bontsa ki a **SZOLGÁLTATÁS BEÁLLÍTÁSAI** elemet.

4.  Kattintson a **Rights Management** elemre.

5.  A **RIGHTS MANAGEMENT** lapon kattintson a **Kezelés** parancsra.

6.  A **rights management** lapon kattintson az **aktiválás** gombra.

7.  Amikor megjelenik a **Szeretné aktiválni a Rights Management szolgáltatást?** kérdés, kattintson az **aktiválás** gombra.

Ekkor megjelenik **A Rights Management aktiválva van** üzenet és az inaktiválására szolgáló lehetőség (előfordulhat, hogy manuálisan kell frissítenie a lapot).

Ekkor ne kattintson a **speciális funkciók** elemre. Ezzel megnyitná a klasszikus Azure-portált, ahol sablonokat konfigurálhat, amelyekre azonban nincs szükség ehhez az oktatóanyaghoz. Helyette zárja be az Office 365 Felügyeleti központot.

### A Rights Management aktiválása a klasszikus Azure portálon

1.  Nyissa meg az [klasszikus Azure-portált](http://go.microsoft.com/fwlink/p/?LinkID=275081), és jelentkezzen be Azure Active Directory globális rendszergazdai fiókjával.

2.  A bal oldali panelen kattintson az **ACTIVE DIRECTORY** elemre.

3.  Az **Active Directory** lapon kattintson a **RIGHTS MANAGEMENT** gombra.

4.  Jelölje ki a [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] kezelni kívánt könyvtárát, kattintson az **ACTIVATE** (AKTIVÁLÁS) gombra, majd erősítse meg a műveletet.

A **RIGHTS MANAGEMENT STATUS** (RIGHTS MANAGEMENT ÁLLAPOT) értékének **Active** (Aktív) értékűnek kell lennie, és az **ACTIVATE** (AKTIVÁLÁS) lehetőséget a **DEACTIVATE** (INAKTIVÁLÁS) lehetőség váltja fel.

Jóllehet konfigurálhat más beállításokat a Rights Management számára a portálon, ezek azonban nem szükségesek ehhez az oktatóanyaghoz, így bezárhatja a klasszikus Azure-portált.

Az első lépéshez mást nem kell tennie. A szolgáltatás aktiválása megtörtént, így a szervezet felhasználó elláthatják védelemmel a fontos és bizalmas dokumentumokat. Éles környezetben célszerű korlátozni, hogy kezdetben ki teheti ezt meg, majd szakaszosan bővíteni a jogosultak körét. Ez azonban nem szükséges a jelen oktatóanyag esetén.

Jóllehet az oktatóanyag nem tér ki erre, éles környezet esetén valószínűleg egyéni sablonokat is konfigurálna. A sablonok megkönnyítik a felhasználók számára a megfelelő beállítások gyors alkalmazását, amikor védelemmel kell ellátniuk fájlokat. Amikor aktiválja a Rights Managementet, automatikusan 2 alapértelmezett sablont kap, amelyeket vélhetően ki kell egészítenie a saját egyéni sablonjaival egy éles környezetben. Mivel sablonokra nincs szükség ebben az oktatóanyagban, készen áll a következő lépésre.

|Ha további információra van szüksége|További információ|
|--------------------------------|--------------------------|
|Információk a Rights Management aktiválásával és azzal kapcsolatban, hogy ki láthat el védelemmel fájlokat és e-maileket, ha a szolgáltatás aktív|[Az Azure Rights Management aktiválása](../deploy-use/activate-service.md)|
|Információk az alapértelmezett sablonokkal és az új, egyéni sablonok létrehozásával kapcsolatban|[Az Azure Rights Management egyéni sablonok konfigurálása](../deploy-use/configure-custom-templates.md)|


>[!div class="step-by-step"]
[« Bevezetés](quick-start-tutorial.md)
[2. lépés »](tutorial-step2.md)


<!--HONumber=Aug16_HO4-->

