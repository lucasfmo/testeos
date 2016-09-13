---
title: "Azure Information Protection – gyors üzembe helyezési útmutató – 1. lépés | Azure Rights Management"
description: "Egy bevezető oktatóanyag 1. lépése, amellyel gyorsan kipróbálhatja a szervezetnél a Microsoft Azure Information Protection szolgáltatást csupán 4, 15 percnél gyorsabban végrehajtható lépésben."
author: cabailey
manager: mbaldwin
ms.date: 07/291/2016
ms.topic: article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: f6dbb143-96f7-4a9c-8208-be9280d69de9
translationtype: Human Translation
ms.sourcegitcommit: da0145444a7d0abb6407ed2ccbb581d4dcdd10d6
ms.openlocfilehash: 38bc0f85acad64d56ef92078ded37a3367c72f10


---

# 1. lépés: A Rights Management szolgáltatás aktiválása
 
>*A következőkre vonatkozik: az Azure Information Protection előzetes verziója*

**[ Előzetes információ, a tartalma változhat. ]**

> [!NOTE]
>Ha csak az adatok besorolását szeretné elvégezni, és nem szeretné azokat az Azure Rights Managementtel védeni, vagy ha már aktiválta a bérlő számára az Azure Rights Management szolgáltatást, lépjen a [következő lépésre](infoprotect-tutorial-step2.md). 

Az Azure Rights Management szolgáltatás aktiválásával besorolásuk után védelemmel láthatja el a legbizalmasabb dokumentumokat és fájlokat. A szolgáltatás aktiválásához használhatja az Office 365 Felügyeleti központot vagy a klasszikus Azure portált:

-   Ha olyan Office 365-előfizetéssel rendelkezik, amely tartalmazza az Azure Rights Managementet, illetve olyan Office 365-előfizetéssel, amely nem tartalmazza az Azure Rights Managementet, de rendelkezik Azure RMS Premium előfizetéssel: **Használja az Office 365 Felügyeleti központot**.

-   Ha nem rendelkezik Office 365-előfizetéssel: **Használja a klasszikus Azure-portált**.

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

Ekkor ne kattintson a **speciális funkciók** elemre. Ezzel megnyitná a klasszikus Azure portált, ahol egyéni sablonokat konfigurálhat, amelyekre azonban nincs szükség ehhez az oktatóanyaghoz. Helyette zárja be az Office 365 Felügyeleti központot.

### A Rights Management aktiválása a klasszikus Azure portálon

1.  Nyissa meg az [klasszikus Azure-portált](http://go.microsoft.com/fwlink/p/?LinkID=275081), és jelentkezzen be Azure Active Directory globális rendszergazdai fiókjával.

2.  A bal oldali panelen kattintson az **ACTIVE DIRECTORY** elemre.

3.  Az **Active Directory** lapon kattintson a **RIGHTS MANAGEMENT** gombra.

4.  Jelölje ki a [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] kezelni kívánt könyvtárát, kattintson az **ACTIVATE** (AKTIVÁLÁS) gombra, majd erősítse meg a műveletet.

A **RIGHTS MANAGEMENT STATUS** (RIGHTS MANAGEMENT ÁLLAPOT) értékének **Active** (Aktív) értékűnek kell lennie, és az **ACTIVATE** (AKTIVÁLÁS) lehetőséget a **DEACTIVATE** (INAKTIVÁLÁS) lehetőség váltja fel.

Jóllehet konfigurálhat más beállításokat a Rights Management számára a portálon, ezek azonban nem szükségesek ehhez az oktatóanyaghoz, így bezárhatja a klasszikus Azure-portált.

Az első lépéshez mást nem kell tennie. Az Azure Rights Management szolgáltatás aktiválása sikeresen megtörtént, így az oktatóanyag későbbi szakaszaiban az egyik alapértelmezett Azure Rights Management-sablont választva védelemmel láthatja el a Confidential (Bizalmas) besorolású dokumentumokat és e-maileket.

Éles környezet esetében valószínűleg egyéni sablonokat szeretne majd konfigurálni a két alapértelmezett Azure Rights Management-sablon mellett vagy helyett. Mivel egyéni sablonokra ehhez az oktatóanyaghoz nincs szükség, készen áll a második lépésre.

|Ha további információra van szüksége|További információ|
|--------------------------------|--------------------------|
|Tudnivalók a Rights Management aktiválásáról|[Az Azure Rights Management aktiválása](../deploy-use/activate-service.md)|
|Információk az alapértelmezett sablonokkal és az új, egyéni sablonok létrehozásával kapcsolatban|[Az Azure Rights Management egyéni sablonok konfigurálása](../deploy-use/configure-custom-templates.md)|

>[!div class="step-by-step"]
[&#171; Bevezetés](infoprotect-quick-start-tutorial.md)
[2. lépés &#187;](infoprotect-tutorial-step2.md)



<!--HONumber=Aug16_HO4-->


