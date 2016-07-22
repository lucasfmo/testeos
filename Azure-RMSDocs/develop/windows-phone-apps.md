---
title: "Windows Phone-beállítás | Azure RMS"
description: "A Windows Phone rendszerre készült alkalmazások a Microsoft Rights Management SDK 4.2 használatával integrált adatvédelmet tudnak biztosítani az alkalmazásokban."
keywords: 
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: e25a446e-b977-4736-9c65-7711171fb0e1
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 90552435666b8f25c893fcffe8c8cf3355a5942d
ms.openlocfilehash: 136d6e9d0c45a9779f87e32eed8288fe8ee3a622


---

# Windows Phone-beállítás


A Windows Phone rendszerre készült alkalmazások a Microsoft Rights Management SDK 4.2 használatával integrált adatvédelmet tudnak biztosítani az alkalmazásokban az Azure Active Directory Rights Management (AAD RM) segítségével.

Ez a témakör végigvezeti egy környezet felépítésének lépésein a saját új alkalmazásai létrehozásához.

-   [Előfeltételek](#prerequisites)
-   [A fejlesztési környezet konfigurálása](#configuring_your_development_environment)
-   [Lásd még:](#see_also)

## Előfeltételek


A fejlesztői rendszeren a következő szoftverekkel kell rendelkeznie:

-   A [Windows 8.1](http://windows.microsoft.com/en-US/windows-8/meet) operációs rendszer.
-   [Windows Phone 8.1-es fejlesztőeszközök (SDK)](http://dev.windowsphone.com/en-us/downloadsdk)
-   Microsoft [Visual Studio 2012](http://www.microsoft.com/visualstudio/eng/products/visual-studio-overview)vagy újabb, vagy a Visual Studio Express 2012, amelyet a Windows Phone SDK 8.0/8.1 tartalmaz
-   A Windows Phone-hoz készült MS RMS SDK 4.2 csomag. További információ: [Első lépések](get-started.md).
-   Hitelesítési tár: Javasoljuk az [Azure AD Authentication Library](https://msdn.microsoft.com/en-us/library/jj573266.aspx) használatát, de használhat más hitelesítési tárakat is.

Az [Újdonságok](release-notes.md) témakörben elolvashatja az API-frissítésekkel, az eszközzel és a környezettel, a kibocsátási megjegyzésekkel és a gyakori kérdésekkel (GYIK) kapcsolatos információkat.

Tekintse át a [Windows Phone-fejlesztés](https://msdn.microsoft.com/en-us/library/windowsphone/develop/ff402535.aspx) útmutatóban szereplő információkat a Windows Phone fejlesztői központban.

## A fejlesztési környezet konfigurálása


-   Nyissa meg a *Visual Studiót*.
-   Kattintson a **Fájl** elemre. Kattintson a **File** (Fájl) menüben a **New** (Új), majd a **Project** (Projekt) elemre.
-   A **New Project** (Új projekt) párbeszédpanelen válassza a **Visual C\#**, majd a **Blank App (Windows Phone)** (Üres alkalmazás (Windows Phone)) elemet, és kattintson az **OK** gombra.

    ![Új projekt létrehozása](../media/wpsetup-newproj.png)

-   A Megoldáskezelőben kattintson a jobb gombbal a projektjére, majd válassza ki a **Hivatkozás hozzáadása** elemet a **Hivatkozás hozzáadása** párbeszédpanel megnyitásához.

    ![Hivatkozás hozzáadása](../media/wpsetup-addref.png)

-   Kattintson a **Tallózás** elemre a **Hivatkozás hozzáadása** párbeszédpanel bal alsó sarkában, és válassza ki a *Microsoft.RightsManagment.dll* fájlt abból a mappából, amelybe kibontotta a csomagot.
-   **Felügyelt alkalmazások** – Felügyelt alkalmazás létrehozásához hozzá kell adnia ezt a hivatkozást. Válassza a **Windows 8.1**-&gt;**Extensions** (Bővítmények) elemet, és jelölje be a **Windows Visual C++ Runtime Package for Windows** (Windows Visual C++ futásidejű csomag a Windowshoz) jelölőnégyzetet

    ![Bővítmények hozzáadása](../media/wpsetup-refmngr.png)

-   **Képességek hozzáadása** – Az alkalmazásnak az SDK használatához szüksége lesz az „Internet (Ügyfél és kiszolgáló)” képességre. A képesség felvételéhez nyissa meg a projekten belül a *Package.appxmanifest* fájlt, majd navigáljon a **Capabilities** (Képességek) lapra a felvételhez.

Most már készen áll a saját új Windows Phone-alkalmazásai létrehozására.

### Lásd még:

[Első lépések](get-started.md)

[Újdonságok](release-notes.md)

[Alapfogalmak](core-concepts.md)

[Windows Phone-fejlesztés](https://msdn.microsoft.com/en-us/library/windowsphone/develop/ff402535.aspx)

[Windows API-referencia](/rights-management/sdk/4.2/api/winrt/Microsoft.RightsManagement)

[Visual Studio 2012](http://www.microsoft.com/visualstudio/eng/products/visual-studio-overview)

[Windows Phone SDK](http://dev.windowsphone.com/en-us/downloadsdk)

 

 






<!--HONumber=Jul16_HO3-->


