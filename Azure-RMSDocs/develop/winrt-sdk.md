---
title: "Windows Áruház beállítása | Azure RMS"
description: "A Windows Áruházban elérhető alkalmazások a Microsoft Rights Management SDK 4.2 használatával integrált adatvédelmet tudnak biztosítani az alkalmazásokban."
keywords: 
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 2720aa0e-0d37-469f-be99-678bf95a9c51
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: f7dd88d90357c99c69fe4fdde67c1544595e02f8
ms.openlocfilehash: 0b8e0fb6d872506ac3529bd137286f0e8fa562ee


---

# Windows Áruház beállítása

A Windows Áruházban elérhető alkalmazások a Microsoft Rights Management SDK 4.2 használatával integrált adatvédelmet tudnak biztosítani az alkalmazásokban az Azure Active Directory Rights Management (AAD RM) segítségével.

Ez a témakör végigvezeti egy környezet felépítésének lépésein a saját új alkalmazásai létrehozásához.

-   [Előfeltételek](#prerequisites)
-   [Nem kötelező megadni](#optional)
-   [A fejlesztési környezet konfigurálása](#configuring-your-development-environment)
-   [Lásd még:](#see-also)

## Előfeltételek


A fejlesztői rendszeren a következő szoftverekkel kell rendelkeznie:

-   [Windows 8.1](http://windows.microsoft.com/en-US/windows-8/meet) operációs rendszer.
-   [Windows 8.1 rendszerhez készült Windows SDK](https://msdn.microsoft.com/windows/desktop/bg162891.aspx)
-   Microsoft [Visual Studio 2012](http://www.microsoft.com/visualstudio/eng/products/visual-studio-overview) vagy újabb, vagy a Visual Studio Express 2012, amelyet a Windows 8.0/8.1 rendszerhez készült Windows SDK tartalmaz.
-   Windows Áruházbeli alkalmazásokhoz készült MS RMS SDK 4.2 csomag. További információ: [Get started](get-started.md) (Első lépések).
-   Hitelesítési tár: Javasoljuk az [Azure AD Authentication Library](https://msdn.microsoft.com/en-us/library/jj573266.aspx) használatát, de használhat más hitelesítési tárakat is.

Az [Újdonságok](release-notes.md) témakörben elolvashatja az API-frissítésekkel, az eszközzel és a környezettel, a kibocsátási megjegyzésekkel és a gyakori kérdésekkel (GYIK) kapcsolatos információkat.

## Nem kötelező megadni

A felhasználói felületi kódtár újrahasznosítható felhasználói felületet biztosít azon fejlesztők számára használati és védelmi műveletekhez, akik nem kívánják a saját egyéni felhasználói felületüket létrehozni – [UI Library for Windows Store apps](https://github.com/AzureAD/rms-sdk-ui-for-windowsstore) (Felhasználói felületi Windows Áruházbeli alkalmazásokhoz). Windows Áruházbeli mintaalkalmazást is biztosítunk – [Windows Áruházbeli RMS-mintaalkalmazás](https://github.com/AzureADSamples/rms-samples-for-windowsstore).

## A fejlesztési környezet konfigurálása


-   Nyissa meg a Visual Studiót.
-   Kattintson a **File** (Fájl) menüben a **New** (Új), majd a **Project** (Projekt) elemre.
-   A **New Project** (Új projekt) párbeszédpanelen válassza a **Visual C\#**, majd a **Blank App (Windows)** (Üres alkalmazás (Windows)) elemet, és kattintson az **OK** gombra.

    ![Új projekt létrehozása](../media/winrtsetup-newproj.png)

-   A **Solution Explorer** (Megoldáskezelő) felületén kattintson a jobb gombbal a projektjére, majd válassza az **Add Reference** (Hivatkozás hozzáadása) elemet az **Add Reference** (Hivatkozás hozzáadása) párbeszédpanel megnyitásához.

    ![Hivatkozás hozzáadása](../media/winrtsetup-addref.png)

-   A **Hivatkozás hozzáadása** párbeszédpanelen kattintson a **Tallózás** lehetőségre, majd válassza ki a *Microsoft.RightsManagement.dll* fájlt, ami abban a mappában található, amelybe kibontotta a SDK-csomagot.
-   **Felügyelt alkalmazások** – Felügyelt alkalmazás létrehozásához hozzá kell adnia ezt a hivatkozást. Válassza a **Windows 8.1**-&gt;**Extensions** (Bővítmények) elemet, és jelölje be a **Windows Visual C++ Runtime Package for Windows** (Windows Visual C++ futásidejű csomag a Windowshoz) jelölőnégyzetet

    ![Bővítmények hozzáadása](../media/winrtsetup-refmngr.png)

-   **Képességek hozzáadása** – Az alkalmazásnak az SDK használatához szüksége lesz az „Internet (Ügyfél és kiszolgáló)” képességre. A képesség felvételéhez nyissa meg a projekten belül a *Package.appxmanifest* fájlt, majd navigáljon a **Capabilities** (Képességek) lapra a felvételhez.

Most már készen áll a saját új Windows Áruházbeli alkalmazásai létrehozására.

### Lásd még:

[Első lépések](get-started.md)

[Újdonságok](release-notes.md)

[Fejlesztői kifejezések és fogalmak](core-concepts.md)

[Windows 8](http://windows.microsoft.com/en-US/windows-8/meet)

[Visual Studio 2012](http://www.microsoft.com/visualstudio/eng/products/visual-studio-overview)

[Windows API-referencia](/rights-management/sdk/4.2/api/winrt/Microsoft.RightsManagement)



<!--HONumber=Jul16_HO2-->


