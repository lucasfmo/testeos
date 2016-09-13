---
title: "A Rights Management megosztóalkalmazás letöltése és telepítése | Azure RMS"
description: "A Windows RMS megosztóalkalmazás interaktív telepítésének útmutatója, hogy biztonságosan megoszthasson dokumentumokat másokkal."
author: cabailey
manager: mbaldwin
ms.date: 08/25/2016
ms.topic: article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 2bf09690-9dba-43b7-9e0a-0110915d4081
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 44541b6fe2567d23174b26cb42fec0731f5d3f58
ms.openlocfilehash: b01896dc49a6c581427393f9e3fc21dbbd235238


---

# A Rights Management megosztóalkalmazás letöltése és telepítése

>*A következőkre vonatkozik: Active Directory tartalomvédelmi szolgáltatások, Azure Rights Management, Windows 10, Windows 7 SP1, Windows 8, Windows 8.1*

Az RMS-megosztó alkalmazás telepítéséhez nem kell helyi rendszergazdának lennie, azonban ha nem az, és az Office 2010-et használja, akkor korlátozásokba ütközhet. További információért tekintse meg a jelen oldal [Ha Ön nem helyi rendszergazda, és Office 2010-et használ](#if-you-are-not-a-local-administrator-and-use-office-2010) című szakaszát.

## A Rights Management megosztóalkalmazás letöltése és telepítése

1.  Lépjen a Microsoft webhelyének [Microsoft Rights Management](http://go.microsoft.com/fwlink/?LinkId=303970) lapjára.

2.  A **Számítógépek** részen kattintson az **RMS alkalmazás Windows rendszerhez** ikonra, és mentse a Microsoft Rights Management megosztóalkalmazás telepítésére szolgáló **Setup.exe** fájlt.

3.  Kattintson duplán a letöltött Setup.exe fájlra. Ha a rendszer a folytatás megerősítését kéri, kattintson az **Igen** gombra.

4.  **A Microsoft RMS telepítése** lapon kattintson a **Tovább** gombra, és várja meg a telepítés befejezését.

    > [!NOTE]
    > Az RMS-megosztó alkalmazáshoz legalább a Microsoft .NET-keretrendszer 4.0-ás verziója szükséges. A telepítő ellenőrzi, hogy a keretrendszer telepítve van-e. Ha nincs, megjelenik egy hivatkozást tartalmazó üzenet, amely a telepítést kéri.

5.  A telepítés befejezése után kattintson az **Újraindítás** gombra a számítógép újraindításához és a telepítés befejezéséhez. Vagy kattintson a **Bezárás** gombra, és indítsa újra később a számítógépet a telepítés befejezéséhez.

Készen áll a fájlok védelmének és a mások által védetté tett fájlok olvasásának megkezdésére.

## Ha Ön nem helyi rendszergazda, és Office 2010-et használ
Ha bejelentkezik számítógépére, de nem rendelkezik rendszergazdai jogokkal, és a telepítő az Office 2010 jelenlétét észleli, akkor megjelenik egy figyelmeztető üzenet, miszerint egyes forgatókönyvek nem fognak működni ezzel a konfigurációval. A forgatókönyvek a következők:

-   Ha a szervezet az RMS helyileg telepített verziója helyett az Azure RMS-t használja:

    -   Az Office tartalomvédelmi szolgáltatással (IRM) kapcsolatos funkciói nem lesznek elérhetőek. Ilyen például az e-mailekre vonatkozó **Nem továbbítandó** beállítás, vagy a **Hozzáférés korlátozása** engedélyek, amelyeket a Word és az Excel **Fájl** menüjében adhat meg. Használhatja a menüszalag Védett megosztás beállítását, és a helyi menük beállításait a Fájlkezelőben.

-   Ha a szervezet az Azure RMS helyett az RMS helyileg telepített verzióját használja:

    -   Ha egy másik szervezet alkalmazottjától az Azure RMS segítségével védett dokumentumokat kap, nem fogja tudni elolvasni őket.

Ha Ön nem helyi rendszergazda, és Office 365-öt vagy Office 2013-at használ, akkor az üzenet nem jelenik meg, és a leírt forgatókönyvek is támogatottak.

A telepítést ezen korlátozások ismeretében folytathatja. A telepítést le is állíthatja, és újra futtathatja a **Futtatás rendszergazdaként** beállítással a Setup.exe futtatásakor a 3. lépésben, vagy felkérhet egy rendszergazdát a telepítésre. A rendszergazdák [parancsfájlok írásával](sharing-app-admin-guide.md#automatic-deployment-for-the-microsoft-rights-management-sharing-application) tehetik lehetővé a telepítés automatikus végrehajtását.

## Példák és egyéb útmutatók
A Rights Management megosztóalkalmazás használatát szemléltető egyéb példák és útmutatók a Rights Management megosztóalkalmazás felhasználói útmutatójának következő szakaszaiban találhatók:

-   [Példák az RMS-megosztó alkalmazás használatára](sharing-app-user-guide.md#examples-for-using-the-rms-sharing-application)

-   [Művelet](sharing-app-user-guide.md#what-do-you-want-to-do)

## Lásd még:
[A Rights Management megosztóalkalmazás felhasználói útmutatója](sharing-app-user-guide.md)




<!--HONumber=Aug16_HO4-->


