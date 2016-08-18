---
title: "Dokumentumok nyomon követése és visszavonása az RMS megosztóalkalmazás használata során | Azure RMS"
description: 
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 08/10/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 61f349ce-bdd2-45c1-acc5-bc83937fb187
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: e9ad2e518b4a7dac608572eb5eb2d99bbda4754e
ms.openlocfilehash: 4c757494a1fe948ed26b32f86844f7b5896c919b


---

# Dokumentumok nyomon követése és visszavonása az RMS-megosztó alkalmazás használata során

*A következőkre vonatkozik: Azure Rights Management, Windows 10, Windows 7 SP1, Windows 8, Windows 8.1*

Miután az RMS megosztóalkalmazás használatával ellátta védelemmel a dokumentumokat, és a szervezet az Azure Rights Managementet használja az Active Directory tartalomvédelmi szolgáltatások helyett, nyomon követheti, hogy a felhasználók hogyan használják a védett dokumentumokat. Ha szükséges, visszavonhatja a dokumentumokhoz való hozzáférést, ha meg szeretné szüntetni a megosztásukat. Ehhez használja a **dokumentumkövetési webhelyet**, amelyhez Windows rendszerű számítógépekről, Mac számítógépekről, sőt táblagépekről és mobiltelefonokról is hozzáférhet.

<div style="padding-top: 56.25%; position: relative; width: 100%;">
<iframe style="position: absolute;top: 0;left: 0;right: 0;bottom: 0;" width="100%" height="100%" src="https://channel9.msdn.com/Series/Information-Protection/Azure-RMS-Document-Tracking-and-Revocation/player" frameborder="0" allowfullscreen></iframe>
</div>

A webhely megnyitását követően jelentkezzen be a dokumentumok nyomon követéséhez. Ha a szervezet rendelkezik [a dokumentumok nyomon követését és visszavonását támogató előfizetéssel](https://technet.microsoft.com/dn858608.aspx), és kapott licencet ehhez az előfizetéshez, akkor megtekintheti, hogy ki próbálta megnyitni a védelemmel ellátott fájlokat, illetve hogy sikerrel jártak-e (sikeresen hitelesítették-e magukat) vagy sem. Minden egyes alkalmat megtekinthet, amikor megpróbáltak hozzáférni a dokumentumhoz, és azt is, hogy ez hol történt. Továbbá:

-   Ha szeretné megszüntetni egy dokumentum megosztását: Kattintson a **Revoke access** (Hozzáférés visszavonása) parancsra, tekintse meg, hogy mennyi ideig lesz még elérhető a dokumentum, és döntse el, hogy tájékoztatja a felhasználókat a korábban megosztott dokumentumhoz történő hozzáférés visszavonásáról, és küld-e nekik egyéni üzenetet. Amikor visszavon egy dokumentumot, az nem törli a megosztott dokumentumot, a jogosultsággal rendelkező felhasználók azonban nem nyithatják meg a továbbiakban.

-   Ha az Excelbe szeretne exportálni: Kattintson az **Exportálás CSV-fájlba** lehetőségre, így módosíthatja az adatokat és létrehozhat saját nézeteket és diagramokat.

-   Ha e-mail-értesítéseket szeretne konfigurálni: Kattintson a **Beállítások** lehetőségre, és adja meg, hogyan és mikor szeretne e-mailt kapni a dokumentumhoz történő hozzáféréskor.

- Ha megosztott dokumentumokat szeretne nyomon követtetni vagy visszavonatni: Az Azure RMS rendszergazdái a Felügyelet ikonra kattintva tudják nyomon követtetni vagy visszavonatni a dokumentumokat. Ez az ikon csak rendszergazdák számára jelenik meg.

-   Ha kérdései vannak, vagy visszajelzést szeretne biztosítani a dokumentumkövetési webhellyel kapcsolatban: Kattintson a Súgó ikonra a [FAQ for Document Tracking](http://go.microsoft.com/fwlink/?LinkId=523977) (Dokumentumkövetéssel kapcsolatos gyakori kérdések) című témakör megnyitásához.

## Az Office használata a dokumentumkövetési webhely eléréséhez

-   A Word, Excel és PowerPoint Office-alkalmazások esetén: A **Kezdőlap** **RMS** csoportjában kattintson a **Védett megosztás** elemre, majd a **Használat követése** parancsra.

    ![Office-alkalmazások használatának nyomon követése az RMS megosztóalkalmazás használatakor ](../media/ADRMS_MSRMSApp_OfficeToolbarTrackUsage.png)

-   Outlook: A **Kezdőlap** **RMS** csoportjában kattintson a **Használat követése** parancsra:

    ![A Használat követése parancs választása az Outlookban az RMS megosztóalkalmazás használatakor ](../media/ADRMS_MSRMSApp_OutlookTrackUsage.png)

Ha nem látja ezeket az RMS-beállítási lehetőségeket, akkor valószínű, hogy az RMS megosztóalkalmazás nincs telepítve a számítógépre, nem a legújabb változata van telepítve, vagy a számítógépet újra kell indítani a telepítés befejezéséhez. További információ a megosztóalkalmazás telepítésével kapcsolatban: [A Rights Management megosztóalkalmazás letöltése és telepítése](install-sharing-app.md).

> [!NOTE] 
> Ha az [Azure Information Protection-ügyfél](../information-protection/info-protect-client.md) előzetes verzióját, a 1.0.233-s vagy későbbi verziót telepítette, a dokumentumkövetési webhely a **Védelem** gomb használatával is elérhető: 
> 
> - Office-alkalmazásban a **Kezdőlap** **Védelem** csoportjában kattintson a **Védelem** > **Használat követése** lehetőségre. 

### A dokumentumok nyomon követésének és visszavonásának egyéb módjai
A Windows rendszerű számítógépen tárolt dokumentumoknak az Office-alkalmazások használatával történő nyomon követése mellett az alábbi lehetőségeket is használhatja:

-   **Webböngésző használata**: Ez a módszer minden támogatott eszköz esetén használható.

-   **A Fájlkezelő használata**: Ez a módszer Windows rendszerű számítógépeken használható.

-   **Az Outlookban létrehozott e-mail-üzenet használata**: Ez a módszer Windows rendszerű számítógépeken használható.

#### Webböngésző használata a dokumentumkövetési webhely elérésére

-   Nyissa meg a [dokumentumkövetési webhelyet](http://go.microsoft.com/fwlink/?LinkId=529562) egy támogatott böngészővel.

    Támogatott böngészők: Javasoljuk az Internet Explorer legalább 10-es verziójának használatát, a dokumentumkövetési webhely megnyitásához azonban az alábbi böngészők bármelyike használható:

    -   Internet Explorer: legalább 10-es verzió,

    -   Internet Explorer 9 legalább MS12-037-el: összesítő biztonsági frissítőcsomag az Internet Explorerhez: 2012. június 12.,

    -   Mozilla Firefox: legalább 12-es verzió,

    -   Apple Safari 5: legalább 5-ös verzió,

    -   Google Chrome: legalább 18-as verzió.

#### A Fájlkezelő használata a dokumentumkövetési webhely elérésére

-   Kattintson a jobb gombbal a fájlra, válassza a **Védelem az RMS-sel**, majd a **Használat követése** menüpontot:

    ![A Használat követése parancs választása a Fájlkezelőben az RMS megosztóalkalmazás használatakor](../media/ADRMS_MSRMSApp_ExplorerTrackUsage.png)

#### Az Outlookban létrehozott e-mail-üzenet használata a dokumentumkövetési webhely elérésére

-   Az e-mail-üzenet **Üzenet** lapjának **RMS** csoportjában kattintson a **Védett megosztás**, majd a **Használat követése** elemre:

    ![A Használat követése parancs választása az Outlookban az RMS megosztóalkalmazás használatakor](../media/ADRMS_MSRMSApp_OutlookMessageTrackUsage.png)

## Példák és egyéb útmutatók
A Rights Management megosztóalkalmazás használatát szemléltető egyéb példák és útmutatók a Rights Management megosztóalkalmazás felhasználói útmutatójának következő szakaszaiban találhatók:

-   [Példák az RMS-megosztó alkalmazás használatára](sharing-app-user-guide.md#examples-for-using-the-rms-sharing-application)

-   [Művelet](sharing-app-user-guide.md#what-do-you-want-to-do)

## Lásd még:
[A Rights Management megosztóalkalmazás felhasználói útmutatója](sharing-app-user-guide.md)



<!--HONumber=Aug16_HO2-->


