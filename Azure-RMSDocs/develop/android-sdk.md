---
title: "Android-beállítás | Azure RMS"
description: "Az Android rendszerre készült alkalmazások a Microsoft Rights Management SDK 4.2 használatával integrált információvédelmet tudnak biztosítani az alkalmazásokban."
keywords: 
author: bruceperlerms
manager: mbaldwin
ms.date: 08/24/2016
ms.topic: article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 986f6932-159b-4791-bd1a-7640a83ee792
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 024a29d7c7db2e4c0578a95c93e22f8e7a5b173e
ms.openlocfilehash: 72196edd630a1934f2c0b6e755771039fceaa795


---

# Android-beállítás

Az Android rendszerre készült alkalmazások a Microsoft Rights Management SDK 4.2-t használva képesek integrált adatvédelmet biztosítani az alkalmazásokban az Azure Active Directory Rights Management (AAD RM) segítségével.

Ez a témakör végigvezeti egy környezet felépítésének lépésein a saját új alkalmazásai létrehozásához.

-   [Előfeltételek](#prerequisites)
-   [Nem kötelező megadni](#optional)
-   [A fejlesztési környezet konfigurálása](#configuring-your-development-environment_)
-   [Lásd még:](#see-also)

## Előfeltételek

A fejlesztői rendszerhez a következő szoftvereket javasoljuk:

-   Windows vagy OS X operációs rendszer az [Eclipse](http://www.oracle.com/technetwork/java/javase/downloads/jre7-downloads-1880261.html) fejlesztői környezet futtatásához.
-   Ez az útmutató feltételezi, hogy Ön az Eclipse SDK Eclipse Juno 4.2-es vagy újabb verzióját használja alapértelmezett telepítés mellett.
-   Java (Java 1.6-os vagy újabb verzió).
-   [Android Developer Tools (ADT) beépülő modul](http://developer.android.com/sdk/installing/index.html). MEGJEGYZÉS – A telepítés befejezéséhez a rendszer az Eclipse újraindítását kérheti.

     

-   Az Androidhoz készült MS RMS SDK 4.2 csomag. További információ: [Első lépések](get-started.md).

    Ez az SDK az Android 4.0.3-as (15. szintű API) vagy újabb rendszerekre való fejlesztéshez alkalmas.

-   Hitelesítési könyvtár: Az [Azure AD Authentication Library (ADAL)](https://msdn.microsoft.com/library/jj573266.aspx) használatát javasoljuk. Használhatók azonban az Oauth 2.0-t támogató hitelesítési könyvtárak is.

    További információ: [ADAL Androidhoz](https://github.com/MSOpenTech/azure-activedirectory-library-for-android)

    **Megjegyzés** Ha az alkalmazása nem az ADAL könyvtárat használja OAuth 2.0-hitelesítési könyvtárként, tekintse át a következő Android útmutatót: [Some SecureRandom Thoughts](http://android-developers.blogspot.com/2013/08/some-securerandom-thoughts.html) (Néhány gondolat a SecureRandom-ról).

     

Az [Újdonságok](release-notes.md) témakörben elolvashatja az API-frissítésekkel, a kibocsátási megjegyzésekkel és a gyakori kérdésekkel (GYIK) kapcsolatos információkat.

## Nem kötelező megadni

A felhasználói felületi kódtár újrahasznosítható felhasználói felületet biztosít azon fejlesztők számára használati és védelmi műveletekhez, akik nem kívánják a saját egyéni felhasználói felületüket létrehozni – [Felhasználói felületi kódtár és mintaalkalmazás Android rendszerhez](https://github.com/AzureAD/rms-sdk-ui-for-android).

## A fejlesztési környezet konfigurálása

**Megjegyzés** MS RMS SDK 4.2 előzetes kiadás: Ebben az előzetes kiadásban a képernyőképek még nincsenek frissítve, így még nem mutatják a com/microsoft/protection útvonal változását a com/microsoft/rightsmanagment útvonalra. A szöveg azonban már frissült.

 
-   Nyissa meg az Eclipse fejlesztői környezetet.
-   Új Android-alkalmazás projekt létrehozásához kattintson a **File** (Fájl) menüben a **New** (Új), majd a **Project** (Projekt) elemre, majd válassza az **Android Application Project** (Android-alkalmazás projekt) lehetőséget.

    ![Új Android-alkalmazás létrehozása](../media/Android-setup-01c.png)

-   Adja meg az alkalmazás nevét. A projektnevet és a csomagnevet az alkalmazás neve alapján tölti ki a rendszer.
-   Kattintson a **Next** (Tovább) gombra, és válassza ki, hol szeretné létrehozni a munkaterületet.

    ![Az alkalmazás nevének megadása](../media/Android-setup-02a.jpg)

-   Kattintson a **Next** (Tovább) gombra, és válasszon egy ikont az alkalmazás számára.

    ![Alkalmazás ikonjának kiválasztása](../media/Android-setup-03.png)

-   A tevékenység létrehozásához kattintson a **Next** (Tovább) gombra, és válassza a **Blank Activity** (Üres tevékenység) lehetőséget.

    ![A tevékenység létrehozása](../media/Android-setup-04.png)

-   Kattintson a **Next** (Tovább) gombra, és nevezze el a tevékenységet. Meghagyhatja a *MainActivity* nevet alapértelmezett névként az *activity\_main* elrendezésnévvel.

    ![A tevékenység elnevezése](../media/Android-setup-05a.jpg)

-   Kattintson a **Befejezés**gombra.

    ![A létrehozás befejezése](../media/Android-setup-06.jpg)

-   Létrejött a projekt a *MainActivity.java* fő tevékenységosztállyal együtt.

**Hivatkozás az SDK-ra**

-   Lépjen abba a mappába, ahová az *adrms\_android\_sdk.zip* fájlt kicsomagolta. Az „SDK > com > microsoft > rightsmanagement” mappában győződjön meg arról, hogy nem írásvédett a *.classpath*, a *.project* és a *project.properties* fájl.
-   Az SDK-ra való hivatkozáshoz importálnia kell azt a munkaterületre.

    Kattintson az Eclipse-ben a **File** (Fájl) elemre. A **File** (Fájl) menüben kattintson az **Import** (Importálás) elemre. Az **Import** (Importálás) párbeszédpanelen válassza az **Android / Existing Android Code into Workspace** (Android / Meglévő Android kód a munkaterületre) lehetőséget.

    ![Importálás a munkaterületre](../media/Android-setup-07.png)

-   Kattintson a **Tovább**gombra. Válassza ki azt a mappát, ahová az *adrms\_android\_sdk.zip* fájlt kicsomagolta. Az SDK-nak **com.microsoft.rightsmanagement** néven kell megjelennie a listában.

    ![Navigálás a mappához és annak kijelölése](../media/Android-setup-08c.jpg)

-   Amikor a **Finish** (Befejezés) gombra kattint, az SDK projekt megjelenik a korábban létrehozott alkalmazás testvéreként.

    ![Az SDK projekt az alkalmazás testvéreként jelenik meg](../media/Android-setup-09.jpg)

-   Kattintson a jobb gombbal a **Project** (Projekt) ikonra, és tekintse meg a projekt tulajdonságait.
-   Lépjen az **Android** lapra.
-   Kattintson az **Add** (Hozzáadás) gombra, majd jelölje ki a munkaterületről a *com.microsoft.rightsmanagement* könyvtárat.

    ![A könyvtár hozzáadása](../media/Android-setup-10b.jpg)

-   Kattintson az **OK**gombra.

    Mivel az MS RMS SDK 4.2 csatlakozik az AAD RM-hez, az alkalmazás számára biztosítani kell a következőket: **INTERNET** és **ACCESS\_NETWORK\_STATE**. Ehhez nyissa meg az *AndroidManifest.xml* fájlt a projekt gyökerében.

    Az engedélyek hozzáadásához kattintson az **Add** (Hozzáadás) gombra, majd válassza a **Uses Permissions** (Engedélyeket használ) lehetőséget.

    ![Engedélyek hozzáadása](../media/Android-setup-11d.jpg)

-   A jegyzékkel kapcsolatos lépést ellenőrizheti a jegyzék a szövegszerkesztő nézetben való megtekintésével. Ellenőrizze, hogy megjelennek-e az alábbi sorok:


    <uses-sdk      android:minSdkVersion="15"      android:targetSdkVersion="19"/> <uses-permission android:name="android.permission.INTERNET"/> <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE"/> <uses-permission/>


**Megjegyzés** Az SDK az *android.support.v4*-et használja

-   Most már készen áll a saját új Android-alkalmazásai létrehozására.

### Lásd még:

[Első lépések](get-started.md)

[Újdonságok](release-notes.md)

[Fejlesztői kifejezések és fogalmak](core-concepts.md)

[Android API-referencia](android-namespaces.md)

 

 



<!--HONumber=Aug16_HO4-->


