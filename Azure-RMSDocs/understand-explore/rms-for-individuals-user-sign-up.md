---
title: "Felhasználói regisztrálás módja az RMS egyéni felhasználók számára szolgáltatásban | Azure RMS"
description: "Az ingyenes fiók regisztrálásához a felhasználóknak meg kell adniuk a munkahelyi vagy iskolai e-mail címüket a Microsoft Rights Management oldalon."
author: cabailey
manager: mbaldwin
ms.date: 08/24/2016
ms.topic: article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: a60731bd-f78d-4f00-bb3e-354637b312ab
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 024a29d7c7db2e4c0578a95c93e22f8e7a5b173e
ms.openlocfilehash: a31005f3dce927db917cb0f2851916b8946da4ee


---

# Felhasználói regisztrálás módja az RMS egyéni felhasználók számára szolgáltatásban

>*A következőkre vonatkozik: Azure Rights Management*

Az ingyenes fiók regisztrálásához a felhasználóknak meg kell adniuk a munkahelyi vagy iskolai e-mail címüket a [Microsoft Rights Management oldalon](https://portal.aadrm.com/). 

A felhasználók általában úgy jutnak erre a regisztrációs oldalra, hogy védett mellékletet tartalmazó e-mail üzenetet kaptak, amely utasításokat tartalmaz a regisztrálás módjával kapcsolatban. A Microsoft választ küld e-mailben, és befejezhetik a regisztrációs folyamatot a fiókjuk létrehozásához szükséges adatok megadásával. A Microsoft visszaigazolást küld e-mailben, amely segítségével eljuthatnak arra az oldalra, ahonnan letölthetik a megosztóalkalmazást különböző eszközökhöz, illetve ezen végső e-mail tartalmazza a használati útmutatóra mutató hivatkozást is.

## Regisztrálás az RMS egyéni felhasználók számára szolgáltatásban

1.  A Windows vagy Mac számítógépen nyissa meg a [Microsoft Rights Management weblapot](https://portal.aadrm.com).

2.  Írja be szervezetének e-mail címét, például **esztert@contoso.com** vagy **e.barta@fabrikam.com**.

    > [!IMPORTANT]
    > Személyes e-mail fiókok megadása nem támogatott, ezért ne adjon meg Microsoft-fiókot (korábbi nevén Microsoft Live ID-fiókot) vagy más személyes fiókot, amelyet esetleg otthoni internetszolgáltatója biztosít.

3.  Kattintson az **Első lépések** elemre.

    A Microsoft az e-mail cím alapján ellenőrzi, hogy a szervezet rendelkezik-e már olyan [fizetős előfizetéssel, amely tartalmazza az Azure RMS](../get-started/requirements-subscriptions.md) szolgáltatást. Ha így van, akkor nincs szükség az RMS egyéni felhasználók számára szolgáltatásra, a rendszer azonnal belépteti és megszakítja az RMS egyéni felhasználók számára szolgáltatásra irányuló önkiszolgáló regisztrációt. Ha nem található fizetett előfizetés az Azure RMS szolgáltatáshoz, a következő lépéssel fogja folytatni.

4.  Várja meg a megadott e-mail címre küldött visszaigazoló üzenetet. Ennek feladója a Microsoft (DoNotReply@microsoft.com), a tárgya pedig **Microsoft RMS**.

5.  Az e-mail megérkezése után kattintson az utasításokban található hivatkozásra a regisztrációs folyamat befejezéséhez.

6.  A hivatkozás átirányítja egy új **Microsoft Rights Management** oldalra, amelyen meg kell adnia a fiókjára vonatkozó adatokat. Írja be az utónevét, vezetéknevét, adjon meg egy tetszőleges jelszót, és erősítse meg, válassza ki a lakhelyéül szolgáló országot (vagy ha az nem szerepel a listán, az ahhoz legközelebbi országot) a legördülő menüben, majd kattintson a **Létrehozás** elemre.

7.  Várja meg a Microsoft által küldött másik e-mail üzenetet, amely megerősíti, hogy fiókja használatra kész.

8.  Ha megkapta az e-mailt, kattintson a hivatkozásra a bejelentkezéshez és a megosztóalkalmazás letöltésére és telepítésére vonatkozó utasítások elolvasásához, vagy kattintson a Súgó hivatkozásra a megosztóalkalmazás használati útmutatójának elolvasásához.

Fiókja létrejött, így már készen áll fájlok védelmére, illetve a mások által védelemmel ellátott fájlok olvasására. Amikor a rendszer felszólítja a bejelentkezésre a fájlok védelemmel való ellátásához vagy a védett fájlok olvasásához, adja meg az RMS egyéni felhasználók számára szolgáltatásban regisztrált fiók létrehozásához használt e-mail címet és jelszót.

## A regisztrációs folyamat műszaki áttekintése
Az RMS egyéni felhasználók számára egy önkiszolgáló regisztrációs folyamatot használ, amelyet a Microsoft felhőalapú technológiáját használó más szolgáltatások is használnak a felhasználók hitelesítésére.

Ez történik a háttérben, amikor egy felhasználó regisztrál az RMS egyéni felhasználók számára szolgáltatásban, és a szervezet nem rendelkezik Office 365- vagy Azure-előfizetéssel, illetve ebből kifolyólag, a felhasználók hitelesítésére szolgáló címtárral az Azure szolgáltatásban:

1.  Amikor egy adott szervezet első felhasználója regisztrál az RMS egyéni felhasználók számára szolgáltatásban, a rendszer ellenőrzi, hogy az e-mail címben megadott tartománynévhez társítva lett-e már Azure-bérlő. Ha található meglévő bérlő, a rendszer automatikusan létrehoz egy új bérlőt és Azure-címtárat a szervezet számára, amely az első felhasználó fiókját tartalmazza. A fizetős Azure-előfizetéstől eltérően ez a fiók nem globális rendszergazda, hanem általános jogú felhasználó. Az új fiók a felhasználó által megadott e-mail címet és jelszót használja.

    > [!NOTE]
    > Bizonyos tartománynevek nem használhatók a címtár létrehozásához, ezért nem használhatók az RMS egyéni felhasználók számára szolgáltatáshoz. A blokkolt tartománynevek listája ebben a JavaScript Object Notation fájlban tekinthető meg: [http://portal.aadrm.com/content/blocked_domains.json](http://portal.aadrm.com/content/blocked_domains.json)

    Ha található meglévő bérlő, a rendszer ellenőrzi, hogy rendelkezik-e már Azure RMS-előfizetéssel. Ha nem található előfizetés, hozzáadható ingyenes előfizetés az RMS egyéni felhasználók számára szolgáltatáshoz.

2.  A szervezet megkapja az RMS egyéni felhasználók számára szolgáltatás előfizetését. Ezután az Azure hitelesítheti a felhasználót, aki védelemmel láthat el fájlokat, illetve olvashatja a mások által védelemmel ellátott fájlokat az Azure Rights Management használatával. A fájlok védelemmel való ellátásához és a védett fájlok olvasásához a felhasználónak RMS-kompatibilis alkalmazással kell rendelkeznie, ilyen például az ingyenes [Rights Management megosztóalkalmazás](../rms-client/sharing-app-windows.md).

3.  Amikor ugyanazon szervezet második felhasználója előfizetést igényel az RMS egyéni felhasználók számára szolgáltatáshoz, az új felhasználói fiókot a rendszer hozzáadja a korábban létrehozott Azure-címtárhoz a szervezet RMS egyéni felhasználók számára előfizetését használva. Ez a második felhasználó az első felhasználó számára elérhető műveletek mindegyikét végrehajtja (fájlok védelemmel való ellátása és védett fájlok olvasása), emellett pedig a két felhasználó könnyebben és biztonságosan együttműködhet, mivel gyorsan alkalmazhatnak alapértelmezett sablonokat, amelyek korlátozzák a szervezet Azure-címtárában található fiókokhoz való hozzáférést.

4.  A szervezet további felhasználói ugyanezt a mintát követik, a felhasználói fiókokat (az új felhasználók regisztrációjakor) a rendszer a szervezet Azure-címtárához adja hozzá. Minél több fiók található a címtárban, annál több felhasználó működhet együtt biztonságosan munkatársaival és partnereivel, és annál könnyebben lehet megelőzni, hogy jogosulatlan személyek olvassák azokat a fájlokat, amelyekhez nem rendelkeznek hozzáféréssel.

A folyamat során semmilyen költsége sem keletkezik a szervezetnek, és az informatikai részlegnek sincs feladata ezzel kapcsolatban. Az informatikai részleg azonban megteheti az alábbiak bármelyik:

-   **A fiókok és a regisztrációs folyamat felügyelete**: Az informatikai rendszergazdák saját tulajdonukba vehetik az Azure szolgáltatásban automatikusan létrehozott címtárakat és fiókokat. Ezután a fiókokat címtár-integrációs megoldások megvalósításával felügyelhetik, ilyen például a jelszó-szinkronizálás és az egyszeri bejelentkezés. Emellett megakadályozhatják, hogy a felhasználók fiókokat hozzanak létre vagy regisztráljanak az RMS egyéni felhasználók számára szolgáltatásában.

    További információ: [Egyéni felhasználók számára létrehozott RMS-szolgáltatásfiókok rendszergazdai felügyelete](rms-for-individuals-take-control.md).

-   **Rights Management kezelése**: A rendszergazdák átalakíthatják a szervezet RMS egyéni felhasználók számára előfizetését az Azure Rights Management szolgáltatást is tartalmazó fizetős előfizetéssé. Amikor erre sor kerül, a meglévő Azure-címtárat és -fiókokat megőrzi a rendszer, így az RMS egyéni felhasználók számára szolgáltatást használó meglévő felhasználók számára zökkenőmentes lesz az átmenet. A felhasználók által korábban védelemmel ellátott fájlok védelmét továbbra is biztosítják ugyanazon házirendek, és a fájlok használatára engedélyt kapott személyek továbbra is a megszokott módon használhatják a fájlokat.

    Ha ezt a megoldást választja, a szervezet képes lesz integrálni a Rights Management szolgáltatást a munkafolyamatokba, szolgáltatásokba és adattárjaiba. Emellett kezelheti is a Rights Management szolgáltatást, mivel rendelkezni fog a szervezet Azure Rights Management-bérlőkulcsával. Az alábbiakat teheti a továbbiakban:

    -   Konfigurálhatja az Exchange és a SharePoint szolgáltatást az Azure Rights Management támogatására, még akkor is, ha helyi környezetben futnak. Az Exchange és a SharePoint szolgáltatást a rendszer natív módon támogatja az online szolgáltatások esetén, helyszíni kiszolgálók esetén pedig egy összekötő biztosít támogatást a számukra. További információkért tekintse át a következőket:

        -   Az Exchange Online és a SharePoint Online szolgáltatással foglalkozó szakaszok az [Office 365: Configuration for clients and online services](../deploy-use/configure-office365.md) (Office 365: Konfigurálás ügyfelek és online szolgáltatások számára) című témakörben.

        -   [Deploying the Azure Rights Management connector (Az Azure Rights Management-összekötő üzembe helyezése)](../deploy-use/deploy-rms-connector.md)

    -   Elektronikus felderítés hajthat végre a vállalat tulajdonában lévő adatokon, így feloldhatja a Rights Management használatával védett fájlok titkosítását, ha szükséges. További információ: [Felügyelők konfigurálása az Azure Rights Management és a felderítési szolgáltatások vagy az adat-helyreállítás számára](../deploy-use/configure-super-users.md).

    -   Naplózhatja a Rights Management használatához kapcsolódó szervezeti tevékenységeket. Ez nagyon hatékony eljárás, mert nemcsak azt figyelheti, hogy mely fájlok élveznek védelmet, és kinek sikerül a védett fájlokhoz hozzáférnie, de azonosíthatja azon jogosulatlan személyek potenciálisan gyanús viselkedését is, akik a védett fájlokhoz próbálnak hozzáférni. További információ: [Az Azure Rights Management használatának naplózása és elemzése](../deploy-use/log-analyze-usage.md).

    -   Biztosíthatja a felhasználók számára védett dokumentumaik nyomon követését és visszavonását, amennyiben az [Azure RMS-előfizetés](https://technet.microsoft.com/dn858608) támogatja ezeket a szolgáltatásokat. További információ: [A fájlok nyomon követése és visszavonása](../rms-client/sharing-app-track-revoke.md) című rész [Az RMS-megosztóalkalmazás használati útmutatója](../rms-client/sharing-app-user-guide.md) című témakörben.

    -   BYOK-megoldást valósíthat meg, hogy Azure Rights Management-bérlőkulcsot a helyszínen hozza létre a rendszer a informatikai házirendek alapján, majd biztonságosan eljuttassa azt a Microsoft számára hardveres biztonsági modul (HSM) használatával. További információ: [Az Azure Rights Management-bérlőkulcs tervezése és megvalósítása](../plan-design/plan-implement-tenant-key.md).


## További lépések
Lásd: [Egyéni RMS-felhasználók számára készült fiókok rendszergazdai felügyelete](rms-for-individuals-take-control.md).





<!--HONumber=Aug16_HO4-->


