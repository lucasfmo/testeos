---
# required metadata

title: Fájl védelme egy eszközön (helyi védelem) a Rights Management megosztóalkalmazással | Azure RMS
description:
keywords:
author: cabailey
manager: mbaldwin
ms.date: 05/09/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 33920329-5247-4f6c-8651-6227afb4a1fa

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: esaggese
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Készüléken lévő fájlok védelme (helyben történő védelem) a Rights Management

*A következőkre vonatkozik: Active Directory tartalomvédelmi szolgáltatások, Azure Rights Management, Windows 10, Windows 7 SP1, Windows 8, Windows 8.1*

Ha helyileg tesz védetté egy fájlt, azzal lecseréli az eredeti, nem védett fájlt. Ha ezután a helyén hagyja a fájlt, egy másik mappába vagy eszközre másolja, vagy megosztja azt a mappát, amelyikben a fájl található, a fájl akkor is védett marad. A védett fájlt emellett csatolhatja e-mail-üzenethez, jóllehet a védett fájlokat ajánlott közvetlenül a Fájlkezelőből vagy egy Office-alkalmazásból megosztani e-mailben (lásd: [E-mailben megosztott fájl védelme a Rights Management megosztóalkalmazással](sharing-app-protect-by-email.md)).).

> [!TIP]
> Ha hibába ütközik, amikor megkísérel védelemmel ellátni egy fájlt, tekintse meg az [FAQ for Microsoft Rights Management Sharing Application for Windows](http://go.microsoft.com/fwlink/?LinkId=303971) (A Windows rendszerhez készült Microsoft Rights Management megosztóalkalmazással kapcsolatos gyakori kérdések) című témakört..

## Fájl védelme egy eszközön (helyi védelem)

1.  A Fájlkezelőben válassza ki a fájlt, amelyet védetté szeretne tenni. Kattintson a jobb gombbal, válassza a **Védelem az RMS-sel**, majd a **Helyi védelem** menüpontot. Példa:

    ![Helyszíni védelem menüpont](../media/ADRMS_MSRMSApp_SP_CompanyDefined.png)

    > [!NOTE]
    > Ha nem látja a **Védelem az RMS-sel** lehetőséget, akkor az RMS megosztóalkalmazás valószínűleg nem lett telepítve a számítógépre, vagy a számítógépet újra kell indítani a telepítés befejezéséhez. További információ az RMS megosztóalkalmazás telepítésével kapcsolatban: [Download and install the Rights Management sharing application](install-sharing-app.md) (A Rights Management megosztóalkalmazás letöltése és telepítése)..

2.  Tegye a következők valamelyikét:

    -   Válasszon ki egy házirend-sablont: ezek előre meghatározott engedélyek, amelyek általában korlátozzák a hozzáférést és használatot a szervezet dolgozói számára. Ha például a szervezet neve „Contoso, Ltd”, a következőt láthatja: **Contoso, Ltd – Bizalmas, csak megtekintésre**. Ha az első alkalommal lát el védelemmel fájlt a számítógépen, először **A vállalat által megadott engedélyek** elemet kell választania a sablonok letöltéséhez.

        Amikor legközelebb a **Helyi védelem** lehetőségre kattint, legfeljebb 10 választható sablont fog látni. Ha több mint 10 sablon érhető el, és a kívánt sablon nem jelenik meg, kattintson **A vállalat által megadott engedélyek** lehetőségre az összes sablon letöltéséhez és megtekintéséhez.

        Egy házirendsablon kiválasztásakor egyszerre több fájlt vagy egy mappát is védetté tehet. Egy mappa kiválasztásakor a mappában lévő fájlok automatikusan a védeni kívánt fájlok közé kerülnek, azonban a mappában létrehozott új fájlok nem lesznek védettek.

    -   Válassza az **Egyéni engedélyek** lehetőséget: akkor válassza ezt a lehetőséget, ha a sablonok nem nyújtanak olyan szintű védelmet, amelyre szüksége van, illetve ha önállóan kívánja megadni a védelmi beállításokat. Adja meg a fájlra vonatkozóan használni kívánt beállításokat a [védelem hozzáadása párbeszédpanelen](sharing-app-dialog-box.md), majd kattintson az **Alkalmaz** parancsra..

3.  Rövid időre megjelenhet egy párbeszédpanel, amely közli, hogy a fájl védetté tétele folyamatban van, majd a fókusz visszahelyeződik a Fájlkezelőre. Ezzel védetté tette a kijelölt fájl vagy fájlokat. Bizonyos esetekben (amikor a védelem hozzáadása megváltoztatja a fájlnévkiterjesztést) a Fájlkezelőben az eredeti fájl helyére egy új fájl kerül, amely a Rights Management védelmi zárolási ikonjával jelenik meg. Példa:

    ![Az RMS megosztóalkalmazás zárolási ikonjával jelölt védett fájl](../media/ADRMS_MSRMSApp_Pfile.png)

Ha később el kell távolítania egy fájl védelmét: [Fájl védelmének eltávolítása a Rights Management megosztóalkalmazással](sharing-app-remove-protection.md).

## Példák és egyéb útmutatók
A Rights Management megosztóalkalmazás használatát szemléltető egyéb példák és útmutatók a Rights Management megosztóalkalmazás felhasználói útmutatójának következő szakaszaiban találhatók:

-   [Példák az RMS-megosztó alkalmazás használatára](sharing-app-user-guide.md#examples-for-using-the-rms-sharing-application)

-   [Művelet](sharing-app-user-guide.md#what-do-you-want-to-do-)

## Lásd még:
[A Rights Management megosztóalkalmazás felhasználói útmutatója](sharing-app-user-guide.md)


<!--HONumber=May16_HO2-->


