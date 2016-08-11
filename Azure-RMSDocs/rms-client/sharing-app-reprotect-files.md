---
title: "A Rights Management szolgáltatásban védetté tett fájlok engedélyeinek módosítása | Azure RMS"
description: "A Rights Management szolgáltatás által védetté tett fájlok engedélyeit az adott fájl ismételt védelmével., majd azon felhasználók listájának és a számukra megadott engedélyek megadásával módosíthatja, akik hozzáféréssel rendelkezhetnek az adott fájlhoz."
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 08/03/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 5ac121b3-d7a0-40e4-8fe7-90bf4cf796f1
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ba029e48b540fda8474eba83322c531ff3daa7b3
ms.openlocfilehash: a123338e34a8c4585a01782a473a400ecb58f166


---

# A Rights Management szolgáltatásban védetté tett fájlok engedélyeinek módosítása

*A következőkre vonatkozik: Active Directory tartalomvédelmi szolgáltatások, Azure Rights Management, Windows 10, Windows 7 SP1, Windows 8, Windows 8.1*

A Rights Management szolgáltatás által védetté tett fájlok engedélyeit az adott fájl ismételt védelmével., majd azon felhasználók listájának és a számukra megadott engedélyek megadásával módosíthatja, akik hozzáféréssel rendelkezhetnek az adott fájlhoz.

> [!IMPORTANT]
> Ezzel nem lépésenkénti módosítást, hanem teljes cserét hajt végre. Az összes kívánt engedély beállításával hatékony új védelemmel látja el a fájlt.
> 
>  Ha egy fájl védelme például úgy van beállítva, hogy csak a marketingosztály munkatársai nyithatják meg, de azt szeretné, hogy az értékesítési osztályon dolgozók is hozzáférhessenek, új védelemmel kell ellátni a fájlt.
>
> Hasonlóképpen, ha hozzá szeretne adni vagy el szeretne távolítani egy engedélyt, nem elég csak a hozzáadni vagy eltávolítani kívánt engedélyt meghatározni, hanem az adott személyekhez tartozó összes engedélyt meg kell adnia.

Ha az ismételt védelemmel ellátni kívánt fájlnak Ön a tulajdonosa (például Ön látta el eredetileg védelemmel a megosztóalkalmazással), automatikusan rendelkezik az új védelem beállításához szükséges engedélyekkel. Ha nem Ön a fájl tulajdonosa, előfordulhat, hogy nem rendelkezik a szükséges engedélyekkel. Ez a védett fájlhoz aktuálisan beállított engedélyektől függ. A fájlok védelmének újbóli beállításához [Teljes hozzáférés](../deploy-use/configure-usage-rights.md#usage-rights-and-descriptions) használati jog szükséges.

Ha például valaki a Rights Management megosztóalkalmazás segítségével védelemmel látta el a fájlt, valamint engedélyt állított be egy olyan csoporthoz, amelynek Ön is a tagja, és a csoporthoz rendelte a **Társtulajdonos** egyéni engedélyt, akkor ismételten védetté teheti a fájlt. Ha azonban a fájl tulajdonosa nem állított be engedélyt Önhöz vagy a csoportjához, illetve a **Felülvizsgáló – Megtekintés és szerkesztés** egyéni engedélyt adta meg vagy egy olyan sablont, amely nem engedélyezi az engedélyek eltávolítását, akkor nem tudja új védelemmel ellátni a fájlt. Ha szeretné gyorsan megállapítani, hogy rendelkezik-e engedéllyel egy fájl ismételt védelméhez, próbálja végrehajtani a műveletet.

Ha szeretné eltávolítani az összes engedélyt, és így a fájl védelmét is, olvassa el a [Fájl védelmének eltávolítása](sharing-app-remove-protection.md) című témakört.

## Fájlok ismételt védelemmel történő ellátása helyben

1.  A Fájlkezelőben válassza ki a fájlt, amelyet védetté szeretne tenni. Kattintson a jobb gombbal, válassza a **Védelem az RMS-sel**, majd a **Helyi védelem** menüpontot. Példa:

    ![Helyszíni védelem menüpont](../media/ADRMS_MSRMSApp_SP_CompanyDefined.png)

    > [!NOTE]
    > Ha nem látja a **Védelem az RMS-sel** lehetőséget, akkor az RMS megosztóalkalmazás valószínűleg nem lett telepítve a számítógépre, vagy a számítógépet újra kell indítani a telepítés befejezéséhez. További információ az RMS megosztóalkalmazás telepítésével kapcsolatban: [Download and install the Rights Management sharing application](install-sharing-app.md) (A Rights Management megosztóalkalmazás letöltése és telepítése).

2.  Tegye a következők valamelyikét:

    -   Válasszon ki egy házirend-sablont: ezek előre meghatározott engedélyek, amelyek általában korlátozzák a hozzáférést és használatot a szervezet dolgozói számára. Ha például a szervezet neve „Contoso, Ltd”, a következőt láthatja: **Contoso, Ltd – Bizalmas, csak megtekintésre**. Ha az első alkalommal lát el védelemmel fájlt a számítógépen, először **A vállalat által megadott engedélyek** elemet kell választania a sablonok letöltéséhez.

        Amikor legközelebb a **Helyi védelem** lehetőségre kattint, legfeljebb 10 választható sablont fog látni. Ha több mint 10 sablon érhető el, és a kívánt sablon nem jelenik meg, kattintson **A vállalat által megadott engedélyek** lehetőségre az összes sablon letöltéséhez és megtekintéséhez.

        Egy házirendsablon kiválasztásakor egyszerre több fájlt vagy egy mappát is védetté tehet. Egy mappa kiválasztásakor a mappában lévő fájlok automatikusan a védeni kívánt fájlok közé kerülnek, azonban a mappában létrehozott új fájlok nem lesznek védettek.

    -   Válassza az **Egyéni engedélyek** lehetőséget: akkor válassza ezt a lehetőséget, ha a sablonok nem nyújtanak olyan szintű védelmet, amelyre szüksége van, illetve ha önállóan kívánja megadni a védelmi beállításokat. Adja meg a fájlra vonatkozóan használni kívánt beállításokat a [Védelem hozzáadása párbeszédpanelen](sharing-app-dialog-box.md), majd kattintson az **Alkalmaz** parancsra.

3. Ha nincs engedélye a fájl védelmének újbóli beállításához, a rendszer üzenetben értesíti arról, hogy **nem lehet védetté tenni a tartalmat**, valamint megadja annak a személynek (a dokumentum tulajdonosának) az e-mail-címét, akitől kérheti az engedélyek módosítását.

    Ha rendelkezik a fájl védelmének újbóli beállításához szükséges engedélyekkel, rövid időre megjelenhet egy párbeszédpanel, amely közli, hogy a fájl védetté tétele folyamatban van, majd a fókusz visszahelyeződik a Fájlkezelőre. Ezzel védetté tette a kijelölt fájlt vagy fájlokat, és a rendszer mentette a módosításokat. 

> [!NOTE]
> Mielőtt ismételt védelemmel láthatná el a fájlt, az RMS-nek meg kell győződnie arról, hogy Ön jogosult a művelet végrehajtására, amit a felhasználónév és a jelszó ellenőrzésével végez el. Bizonyos esetekben a rendszer ezt gyorsítótárazhatja, és ekkor nem kéri a hitelesítő adatok megadását. Más esetekben kérni fogja a hitelesítő adatok megadását.
>
> Ha a szervezete nem használja az Azure Rights Management (Azure RMS) vagy az AD RMS szolgáltatást, kérhet egy ingyenes fiókot, amely elfogadja a hitelesítő adatait, hogy használhassa az RMS által védett fájlokat:
>
> -   A fiók kéréséhez kattintson az [RMS egyéni felhasználók számára](http://go.microsoft.com/fwlink/?LinkId=309469) szolgáltatás igénylésére szolgáló hivatkozásra.
>
>     Amikor regisztrál, ne a személyes, hanem a vállalati e-mail címét adja meg. Ha azért iratkozik fel, mert egy védett mellékletet kapott e-mailben, ugyanazt az e-mail címet használja, amelyre Önnek az e-mailt küldték.
> -   További információ: [RMS for Individuals and Azure Rights Management](../understand-explore/rms-for-individuals.md) (RMS egyéni felhasználók számára és Azure Rights Management).

## Ismételt védelem beállítása e-mailben elküldött fájlhoz

Ha egy e-mailben elküldött fájl engedélyeit szeretné módosítani:

- **Fájl olvasásának engedélyezése több személy számára**: Az [E-mailben megosztott fájl védelme](sharing-app-protect-by-email.md) című témakörben ismertetett útmutatót követve küldje el a fájlt e-mailben a kívánt felhasználóknak.

- **A fájl engedélyeinek módosítása**: Az [E-mailben megosztott fájl védelme](sharing-app-protect-by-email.md) című témakör útmutatását követve küldje el ismét a fájlt, majd válassza ki az új engedélyeket. 

    Mivel az e-mailben eredetileg elküldött fájl korábbi engedélyeit nem tudja eltávolítani, csak helyettesítheti azokat az új engedélyekkel, érdemes visszavonni az előzőleg elküldött fájlt, így a címzettek többé nem tudják megnyitni a dokumentum azon verzióját. A fájl visszavonásához akkor érdemes folyamodni, ha szigorúbb engedélyeket szeretne hozzáadni (például egyes felhasználóknak meg szeretné tiltani a fájl elérését vagy szerkesztését).

    Az e-mailben elküldött fájlok visszavonásáról további információt a [Dokumentumok nyomon követése és visszavonása](sharing-app-track-revoke.md) című témakörben talál.


## Példák és egyéb útmutatók
A Rights Management megosztóalkalmazás használatát szemléltető egyéb példák és útmutatók a Rights Management megosztóalkalmazás felhasználói útmutatójának következő szakaszaiban találhatók:

-   [Példák az RMS-megosztó alkalmazás használatára](sharing-app-user-guide.md#examples-for-using-the-rms-sharing-application)

-   [Művelet](sharing-app-user-guide.md#what-do-you-want-to-do)

## Lásd még:
[A Rights Management megosztóalkalmazás felhasználói útmutatója](sharing-app-user-guide.md)



<!--HONumber=Aug16_HO1-->


