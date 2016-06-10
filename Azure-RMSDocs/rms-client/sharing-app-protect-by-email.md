---
# required metadata

title: E-mailben megosztott fájlok védelmének biztosítása a Rights Management megosztóalkalmazással | Azure RMS
description:
keywords:
author: cabailey
manager: mbaldwin
ms.date: 05/09/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 4c1cd1d3-78dd-4f90-8b37-dcc9205a6736

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: esaggese
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# E-mailben megosztott fájl védelme a Rights Management megosztóalkalmazással

*A következőkre vonatkozik: Active Directory tartalomvédelmi szolgáltatások, Azure Rights Management, Windows 10, Windows 7 SP1, Windows 8, Windows 8.1*

Amikor védetté tesz egy e-mailben megosztott fájlt, az alkalmazás létrehozza az eredeti fájl egy új verzióját. Az eredeti fájl védelem nélküli marad, az új verzió pedig védett lesz, és a rendszer automatikusan csatolja az elküldendő e-mailhez.

Bizonyos esetekben (a Microsoft Word, Excel és PowerPoint alkalmazással létrehozott fájlok esetén) az RMS megosztóalkalmazás két változatot hoz létre a fájlból, amelyeket csatol az e-mailhez. A fájl második verziója **.ppdf** fájlnévkiterjesztéssel rendelkezik, és a fájl PDF-árnyékmásolata. A fájl ezen változata biztosítja, hogy a címzettek mindig el tudják olvasni a fájlt, akkor is, ha nincs telepítve a gépükre az alkalmazás azon változata, amellyel a fájlt létrehozták. Ez a helyzet gyakran áll elő olyankor, amikor a címzettek mobileszközökön olvassák az e-mailjeiket, és szeretnék megtekinteni azok mellékleteit is. A fájl megnyitásához kizárólag az RMS megosztóalkalmazásra van szükségük. Ezt követően elolvashatják a csatolt fájlt, de nem tudják megváltoztatni, amíg meg nem nyitják annak másik változatát valamilyen az RMS-t támogató alkalmazással.

Ha a szervezete az Azure RMS-t használja, a következő megosztásával követheti a védett fájlokat:

-   Válassza ki azt a lehetőséget, amellyel e-mailt kap, ha valaki megpróbálkozik ezen védett mellékletek megnyitásával. A fájl megnyitására tett kísérletekről minden esetben értesítést kap arról, hogy ki és mikor próbálta megnyitni a fájlt, és hogy sikerrel járt-e (sikeres volt-e a hitelesítése) vagy nem.

-   Használja a dokumentációkövetési webhelyet. Leállíthatja a fájl megosztását is, ha visszavonja az elérését a dokumentumkövetési webhelyen. További információkért lásd: [Dokumentumok nyomon követése és visszavonása az RMS-megosztó alkalmazás használata során](sharing-app-track-revoke.md).

## Outlook használata: E-mailben megosztott fájl védelme

1.  Hozza létre az e-mail üzenetet, majd csatolja a fájlt. Ezt követően kattintson az **Üzenet** lap **RMS** csoportjának **Védett megosztás** elemére, majd kattintson újra a **Védett megosztás** elemre:

    ![Outlook bővítmény az RMS megosztóalkalmazáshoz](../media/ADRMS_MSRMSApp_SP_OutlookToolbar.png)

    Ha nem látja ezt a gombot, annak valószínű oka az, hogy az RMS megosztóalkalmazás nincs telepítve a számítógépre, nem a legújabb változata van telepítve, vagy a számítógépet újra kell indítani a telepítés befejezéséhez. További információ a megosztóalkalmazás telepítésével kapcsolatban: [Download and install the Rights Management sharing application](install-sharing-app.md) (A Rights Management megosztóalkalmazás letöltése és telepítése)..

2.  A [védett megosztás párbeszédablakban](sharing-app-dialog-box.md) adja meg azokat a beállításokat, amelyeket a fájlhoz használni szeretne, majd kattintson az **Azonnali küldés** gombra..

### További lehetőségek egy e-mailben megosztott fájl védelmére
A védett fájlok Outlookkal történő megosztása mellett a következő alternatív megoldásokat is igénybe veheti:

-   Fájlkezelőből: Ez a módszer minden fájl esetében működik.

-   Office-alkalmazásból: Ez a módszer az RMS megosztóalkalmazás által az Office-bővítménnyel támogatott alkalmazások esetén használható, ha látja az **RMS** csoportot a menüszalagon.

#### Fájlkezelő vagy Office-alkalmazás használata: E-mailben megosztott fájl védelme

1.  Használja az alábbi lehetőségek egyikét:

    -   Fájlkezelő esetén: Kattintson a jobb gombbal a fájlra, válassza a **Védelem az RMS-sel**, majd a **Védett megosztás** menüpontot:

        ![Védett menüpontok megosztása](../media/ADRMS_MSRMSApp_ShareProtectedMenu.png)

    -   Office-alkalmazások (Word, Excel és PowerPoint) esetén: Először győződjön meg róla, hogy mentette a fájlt. Ezt követően kattintson a **Kezdőlap** **RMS** csoportjának **Védett megosztás** elemére, majd kattintson újra a **Védett megosztás** elemre:

        ![Office eszköztár bővítmény](../media/ADRMS_MSRMSApp_SP_OfficeToolbar.png)

    Ha nem látja ezeket a védelmi lehetőségeket, annak valószínű oka az, hogy az RMS megosztóalkalmazás nincs telepítve a számítógépre, nem a legújabb változata van telepítve, vagy a számítógépet újra kell indítani a telepítés befejezéséhez. További információ a megosztóalkalmazás telepítésével kapcsolatban: [Download and install the Rights Management sharing application](install-sharing-app.md) (A Rights Management megosztóalkalmazás letöltése és telepítése)..

2.  A [védett megosztás párbeszédablakban](sharing-app-dialog-box.md) adja meg azokat a beállításokat, amelyeket a fájlhoz használni szeretne, majd kattintson a **Küldés** gombra..

3.  Rövid időre megjelenhet egy párbeszédpanel, amely közli, hogy a fájl védetté tétele folyamatban van, majd egy e-mail-üzenetet láthat, amely közli a címzettekkel, hogy a mellékleteket a Microsoft RMS védi, és hogy a használatához be kell jelentkezniük. Amikor a hivatkozásra kattintanak a bejelentkezéshez, láthatják azon utasításokat és hivatkozásokat, amelyekkel megnyithatják a védett mellékletet.

    Például:

    ![E-mail-üzenet az Azure RMS-hez](../media/ADRMS_MSRMSApp_EmailMessage.PNG)

    Szeretné megtudni, hogy [Mi az az automatikusan létrehozott .ppdf-fájl?](sharing-app-dialog-box.md#what-s-the-ppdf-file-that-s-automatically-created-)

4.  Választható: Bármit módosíthat ebben az e-mail-üzenetben. Például hozzáadhatja vagy módosíthatja az üzenet tárgyát vagy szövegét.

    > [!WARNING]
    > Bár hozzáadhat és eltávolíthat személyeket ebből az e-mail-üzenetből, ez nem módosítja a melléklet **védett megosztás** párbeszédpanelén megadott engedélyeit. Ha szeretné módosítani ezeket az engedélyeket, például szeretné egy új személynek engedélyezni a fájl megnyitását, zárja be az e-mailt mentés vagy küldés nélkül, és térjen vissza az 1. lépéshez.

5.  Küldje el az e-mailt.

## Példák és egyéb útmutatók
A Rights Management megosztóalkalmazás használatát szemléltető egyéb példák és útmutatók a Rights Management megosztóalkalmazás felhasználói útmutatójának következő szakaszaiban találhatók:

-   [Példák az RMS-megosztó alkalmazás használatára](sharing-app-user-guide.md#examples-for-using-the-rms-sharing-application)

-   [Művelet](sharing-app-user-guide.md#what-do-you-want-to-do-)

## Lásd még:
[A Rights Management megosztóalkalmazás felhasználói útmutatója](sharing-app-user-guide.md)


<!--HONumber=May16_HO2-->


