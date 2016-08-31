---
title: "iOS- és OS X-beállítás | Azure RMS"
description: "Az iOS- és OS X-alkalmazások az RMS SDK 4.2-t használva képesek integrált adatvédelmet alkalmazni az alkalmazásokban az AAD RM segítségével."
keywords: 
author: bruceperlerms
manager: mbaldwin
ms.date: 08/24/2016
ms.topic: article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: b31e5b72-e65e-450a-b1b8-d46e81e9fb34
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 024a29d7c7db2e4c0578a95c93e22f8e7a5b173e
ms.openlocfilehash: 65c5b290278405152d0377a686886ff5be14b52b


---

# iOS- és OS X-beállítás

Az iOS- és OS X-alkalmazások a Microsoft Rights Management SDK 4.2-t használva képesek integrált adatvédelmet alkalmazni az alkalmazásokban az Azure Rights Management (Azure RMS) segítségével.

Ez a témakör végigvezeti egy környezet felépítésének lépésein a saját új alkalmazásai létrehozásához.

**Megjegyzés**  Ez az SDK nem támogatja az iPod Touch készüléket.


-   [Előfeltételek](#prerequisites)
-   [Nem kötelező megadni](#optional)
-   [A fejlesztési környezet konfigurálása](#configuring-your-development-environment)
-   [Lásd még:](#see-also)

## Előfeltételek

A fejlesztői rendszerhez a következő szoftvereket javasoljuk:

-   Minden iOS-fejlesztéshez OS X rendszer szükséges.
-   Xcode 6.0 és újabb verziók

    Az Xcode elérhető a [Mac App Store](https://developer.apple.com/technologies/mac/) áruházban.

-   Az MS RMS SDK 4.2 csomag iOS és OS X rendszerekhez. További információ: [Get started](get-started.md) (Első lépések).

    Ez az SDK az iOS 7.0 és az OS X 10.8 vagy újabb verzióin végzett fejlesztéshez alkalmas.

-   Hitelesítési könyvtár: az [Azure AD Authentication Library (ADAL)](https://msdn.microsoft.com/library/jj573266.aspx) használatát javasoljuk. Használhatók azonban az Oauth 2.0-t támogató hitelesítési könyvtárak is.

    További információ: [ADAL for iOS](https://github.com/MSOpenTech/azure-activedirectory-library-for-ios) (ADAL az iOS rendszerhez) vagy [ADAL for OS X](https://github.com/MSOpenTech/azure-activedirectory-library-for-ios/tree/OSXUniversal) (ADAL az OS X rendszerhez)

Az [Újdonságok](release-notes.md) témakörben elolvashatja az API-frissítésekkel, a kibocsátási megjegyzésekkel és a gyakori kérdésekkel (GYIK) kapcsolatos információkat.

## Nem kötelező megadni

A felhasználói felületi kódtár újrahasznosítható felhasználói felületet biztosít azon fejlesztők számára használati és védelmi műveletekhez, akik nem kívánják a saját egyéni felhasználói felületüket létrehozni – [UI Library and Sample app for iOS](https://github.com/AzureAD/rms-sdk-ui-for-ios) (Felhasználói felületi kódtár és mintaalkalmazás iOS rendszerhez).

## A fejlesztési környezet konfigurálása

-   Új projekt létrehozásához kattintson a **File** (Fájl) menüben a **New** (Új), majd a **Project** (Projekt) elemre.
-   Válassza a **Single View Application** (Egynézetes alkalmazás) lehetőséget.

    ![Új projekt létrehozása](../media/iOS-Project.png)

-   Adja meg az új projekt nevét és azonosítóját.

    ![A projekt elnevezése](../media/iOS-project-options.png)

-   Kattintson a **Next** (Tovább) gombra, és válassza ki a projekt helyét.
-   Az **MSRightsManagement** keretrendszert úgy adhatja az iOS-keretrendszerekhez, ha az SDK telepítőmappában található .framework mappát a **Project Navigator** (Projektkezelő) **Frameworks** (Keretrendszerek) szakaszába húzza.

    ![Hely beállítása](../media/ios-add-dependencies-01a.png)

-   Válassza a **Create groups for any added folders** (Csoportok létrehozása bármely hozzáadott mappához) választógombot, és törölje a **Copy items into destination group's folder (if needed)** (Elemek másolása a célcsoport mappájába (ha szükséges)) jelölőnégyzet jelölését.

    Ez a művelet megtartja az SDK telepítőmappa hivatkozását ahelyett, hogy létrehozna egy másolatot.

    ![Hivatkozás beállítása az SDK telepítőmappához](../media/iOS-create-groups.png)

-   Az MS RMS SDK 4.2 készletet úgy adhatja hozzá az erőforráscsomaghoz, ha az MSRightsManagement.framework/Resources mappában található MSRightsManagementResources.bundle fájlt a Projektkezelő **Frameworks** (Keretrendszerek) szakaszába húzza.

    ![Erőforráscsomag hozzáadása](../media/iOS-add-resource-bundle-02a.png)

-   Ahogyan a Keretrendszer másolása során is tette, válassza a **Create groups for any added folders** (Csoportok létrehozása bármely hozzáadott mappához) választógombot, és törölje a **Copy items into destination group's folder (if needed)** (Elemek másolása a célcsoport mappájába (ha szükséges)) jelölőnégyzet jelölését.
-   Az SDK egyéb keretrendszerekre támaszkodik, beleértve a következőket: **CoreData**, **MessageUI**, **SystemConfiguration**, **Libresolv** és **Security**. Ezen keretrendszerek hozzáadásához lépjen a **Linked Frameworks and Libraries** (Csatolt keretrendszerek és könyvtárak) szakaszra a cél **Summary** (Összegzés) paneljén, majd bontsa ki a szakaszt, és adja hozzá őket.

    A **UIKit** és a **Foundation** keretrendszer kötelező, és általában alapértelmezés szerint jelen van.

    ![Erőforrások hozzáadása](../media/iOS-add-libraries.png)

-   Adja hozzá az **-ObjC** jelzőt az **Más csatoló jelzőkhöz** a célpont **Létrehozási beállításaiban**.

    ![Létrehozási beállítások hozzáadása](../media/iOS-linker-flags.png)

-   A **Project Navigator** Projektkezelő felületének most ehhez a fához hasonlóan kell kinéznie.

    ![Projekt áttekintése](../media/iOS-verify-setup-01a.png)

-   Most már készen áll a saját új iOS-/OS X-alkalmazásai létrehozására.

### Lásd még:

* [Első lépések](get-started.md)

* [Újdonságok](release-notes.md)

* [Fejlesztői kifejezések és fogalmak](core-concepts.md)

* [iOS/OS X API-referencia](/rights-management/sdk/4.2/api/ios/ios)

 

 






<!--HONumber=Aug16_HO4-->


