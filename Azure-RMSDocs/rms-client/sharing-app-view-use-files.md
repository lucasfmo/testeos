---
# required metadata

title: A Rights Management szolgáltatásban védetté tett fájlok megtekintése és használata | Azure RMS
description:
keywords:
author: cabailey
manager: mbaldwin
ms.date: 05/09/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: e5fa4666-6906-405a-9e0c-2c52d4cd27c8

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: esaggese
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# A Rights Management szolgáltatásban védetté tett fájlok megtekintése és használata

*A következőkre vonatkozik: Active Directory tartalomvédelmi szolgáltatások, Azure Rights Management, Windows 10, Windows 7 SP1, Windows 8, Windows 8.1*

Ha [telepítve van a számítógépen a Rights Management (RMS) megosztóalkalmazás](install-sharing-app.md), a védett fájlok megtekintéséhez nem kell mást tennie, mint duplán kattintani a kívánt fájlra. A fájl lehet egy e-mail melléklete, vagy megjelenhet a Fájlkezelőben is.

> [!NOTE]
> Mielőtt megtekinthetné a védett fájlt, az RMS-nek meg kell győződnie arról, hogy Ön jogosult erre, amit a felhasználónév és a jelszó ellenőrzésével végez el. Bizonyos esetekben a rendszer ezt gyorsítótárazhatja, és ekkor nem kéri a hitelesítő adatok megadását. Más esetekben kérni fogja a hitelesítő adatok megadását.
>
> Ha a szervezete nem használja az Azure Rights Management (Azure RMS) vagy az AD RMS szolgáltatást, kérhet egy ingyenes fiókot, amely elfogadja a hitelesítő adatait, hogy megnyithasson RMS használatával védetté tett fájlokat.
>
> -   A fiók kéréséhez kattintson az [RMS egyéni felhasználók számára](http://go.microsoft.com/fwlink/?LinkId=309469) szolgáltatás igényléséhez használható hivatkozásra..
>
>     Amikor regisztrál, ne a személyes, hanem a vállalati e-mail címét adja meg. Ha azért iratkozik fel, mert egy védett mellékletet kapott e-mailben, ugyanazt az e-mail címet használja, amelyre Önnek az e-mailt küldték.
> -   További információ: [RMS for Individuals and Azure Rights Management](../understand-explore/rms-for-individuals.md) (RMS egyéni felhasználók számára és Azure Rights Management)..

## Védett fájl megtekintése
A Fájlkezelőben vagy a mellékletet tartalmazó e-mail üzenetben kattintson duplán a védett fájlra, és amikor az alkalmazás kéri, adja meg a hitelesítő adatait.

Ha a fájlnak két verzióját látja, de eltérő fájlnévkiterjesztésekkel, csak akkor nyissa meg a .ppdf kiterjesztésű fájlt, ha a másik fájlt nem lehet megnyitni. Ha a .ppdf verziót sem tudja megnyitni, először telepítse az [RMS megosztóalkalmazást](install-sharing-app.md), amely képes megnyitni a .ppdf fájlnévkiterjesztéssel rendelkező fájlokat.

> [!NOTE]
> További információ: „[Mi az az automatikusan létrehozott .ppdf-fájl?](sharing-app-dialog-box.md#what-s-the-ppdf-file-that-s-automatically-created-)”.

A fájlok a védettségük típusától függően nyílnak meg, a védettségük pedig a fájlnévkiterjesztés alapján határozható meg. A fájlok megnyitását a rendszer naplózhatja, mindaddig, amíg a fájlok védelme meg nem szűnik. Ha a fájlt e-mail mellékletként küldték, a feladó e-mailben értesítést kaphat a fájl minden egyes megnyitásakor.

- **A fájl *.pfile* fájlnévkiterjesztéssel rendelkezik**

    A fájlt általános védelemmel látták el.

    Amikor megnyitja a fájlt, a megosztóalkalmazás **védett fájl** párbeszédpanelje nyílik meg, amely tájékoztatja arról, hogy ki látta el védelemmel a fájlt, és arra kéri, hogy tartsa tiszteletben a társtulajdonosi engedélyeket. Kattintson a **Megnyitás** gombra a fájl elolvasásához.

    ![E-mailben megosztott pfile fájl párbeszédpanelje az RMS-megosztóalkalmazás használatakor](../media/ADRMS_MSRMSApp_PfilePermission.png)

- **A fájl *.ppdf* fájlnévkiterjesztéssel rendelkezik, vagy védelemmel ellátott szöveg- vagy képfájl (például *.ptxt* vagy *.pjpg*).)**

    A fájlt natív módon, írásvédett másolatként tették védetté.

    A fájl az RMS-megosztó alkalmazással együtt települő megjelenítőben nyílik meg. Ez a fájl írásvédett, még akkor is, ha más helyre menti, vagy átnevezi.

- **Egyéb fájlnévkiterjesztések**

    A fájlt natív módon tették védetté.

    A fájl az eredeti kiterjesztéséhez társított alkalmazásban nyílik meg, és a fájl elején megjelenik egy korlátozásról tájékoztató szalagcím. A szalagcím megjelenítheti a fájlra alkalmazott engedélyeket, vagy tartalmazhat egy hivatkozást is a megjelenítésükhöz. Az alábbi tájékoztatást láthatja például, amikor is **Az engedélyek korlátozottak** elemre kell kattintania a fájlra alkalmazott tényleges engedélyek és a fájlhoz hozzáféréssel rendelkező személyek megtekintéséhez:

    ![Korlátozott hozzáférés szalagcím védett fájl esetében](../media/ADRMS_MSRMSApp_RestrictedAccess.png)



A Rights Management által támogatott fájlnévkiterjesztések teljes listájáért tekintse meg a [Rights Management sharing application administrator guide](sharing-app-admin-guide.md) (A Rights Management megosztóalkalmazás rendszergazdai kézikönyve) [Supported file types and file name extensions](sharing-app-admin-guide-technical.md#supported-file-types-and-file-name-extensions) (Támogatott fájltípusok és fájlnévkiterjesztések) című szakaszát. Ha a fájlnévkiterjesztést a lista nem tartalmazza, használjon egy webes keresőt annak meghatározásához, hogy másik alkalmazás támogatja-e a kiterjesztést.

> [!NOTE]
> Miután meggyőződött arról, hogy fájlt a Rights Management védi, de a fájl nem nyitható meg, töltse le és használja az [RMS elemző eszközt](https://www.microsoft.com/en-us/download/details.aspx?id=46437). Kövesse az eszköz utasításait a számítógép azon problémáinak ellenőrzésére, amelyek megakadályozhatják a védett dokumentum megnyitását.

## A védett fájlok használata (például szerkesztése vagy nyomtatása)
Ha a védett fájl megnyitása után az elolvasásánál többet szeretne tenni (például szerkeszteni, másolni vagy kinyomtatni), kövesse a fájlnévkiterjesztésnek megfelelő utasításokat:

- **A fájl *.pfile* fájlnévkiterjesztéssel rendelkezik**

    Mentse a megnyitott fájlt olyan fájlnévkiterjesztéssel, amely a használni kívánt alkalmazáshoz van hozzárendelve.

    Ha például a fájl document.vsdx.pfile néven lett védetté téve, tekintse meg a fájlt, és a Fájlkezelőben mentse document.vsdx néven.

    Az új fájl már nem védett. Ha védelemmel szeretné ellátni, azt manuálisan kell megtennie. Útmutatás: [Protect a file on a device (protect in-place) by using the Rights Management sharing application](sharing-app-protect-in-place.md) (Fájl védelme egy eszközön (helyi védelem) a Rights Management megosztóalkalmazással)..

- **A fájl *.ppdf* fájlnévkiterjesztéssel rendelkezik, vagy védelemmel ellátott szöveg- vagy képfájl (például *.ptxt* vagy *.pjpg*).)**

    A fájlt csak megtekintheti, és ha átnevezi vagy áthelyezi, a fájl védett marad.

- **Egyéb fájlnévkiterjesztések**

    Ezeknek a fájloknak a használatához az eszközének rendelkeznie kell olyan alkalmazással, amely együttműködik a tartalomvédelmi (Rights Management) szolgáltatással. Ezeket az alkalmazásokat RMS-kompatibilis alkalmazásoknak nevezzük. Rights Management-kompatibilis alkalmazások például az Office 2016, az Office 2013 és az Office 2010 alkalmazásai (a Word, az Excel, a PowerPoint és az Outlook). Ugyanakkor a nem Microsoft-alkalmazások, például más szoftvergyártók vagy saját üzletági alkalmazásai is kompatibilisek lehetnek a tartalomvédelmi szolgáltatással.

    A tartalomvédelmi szolgáltatással kompatibilis alkalmazások meg tudják nyitni a más RMS-kompatibilis alkalmazásokban védetté tett fájlokat. Továbbá megőrzik a fájlokra alkalmazott védelmet, még a fájl szerkesztése, illetve más néven vagy más helyre történő mentése esetén is. Ezek az alkalmazások lehetővé teszik, hogy a fájlt az aktuálisan érvényes engedélyeinek megfelelően használja, így ha Ön rendelkezik engedéllyel a fájl használatára, akkor azt megteheti. Előfordulhat például, hogy szerkesztheti a fájlt, de kinyomtatni már nem tudja.


## Példák és egyéb útmutatók
A Rights Management megosztóalkalmazás használatát szemléltető egyéb példák és útmutatók a Rights Management megosztóalkalmazás felhasználói útmutatójának következő szakaszaiban találhatók:

-   [Példák az RMS-megosztó alkalmazás használatára](sharing-app-user-guide.md#examples-for-using-the-rms-sharing-application)

-   [Művelet](sharing-app-user-guide.md#what-do-you-want-to-do-)

## Lásd még:
[A Rights Management megosztóalkalmazás felhasználói útmutatója](sharing-app-user-guide.md)


<!--HONumber=May16_HO2-->


