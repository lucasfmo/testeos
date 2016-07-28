---
title: "A Rights Management megosztóalkalmazás párbeszédpanel-beállításai | Azure RMS"
description: 
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 07/13/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 7b91ab30-6363-4929-bcbd-4dfbd05f644a
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 67129d6cdac124947fc07aa4d42523686227752e
ms.openlocfilehash: ed2ab42174ce5d83fd60ace1c394515db1450e3d


---

# A Rights Management megosztóalkalmazás párbeszédpanel-beállításai

*A következőkre vonatkozik: Active Directory tartalomvédelmi szolgáltatások, Azure Rights Management, Windows 10, Windows 7 SP1, Windows 8, Windows 8.1*

A jelen témakörben található információk segítségével megadhatja az RMS megosztóalkalmazás **Védelem hozzáadása** vagy **Védett megosztás** párbeszédpanelének beállításait. Ez a párbeszédpanel akkor jelenik meg, amikor [egy megosztani kívánt fájlt lát el védelemmel](sharing-app-protect-by-email.md), vagy [helyben lát el védelemmel egy fájlt](sharing-app-protect-in-place.md), és egyéni engedélyeket állít be.

> [!IMPORTANT]
> Ha a látott beállítási lehetőségek különböznek az itt dokumentált lehetőségektől, akkor valószínűleg nem az alkalmazás legújabb verziója van telepítve. A legújabb verziót a [Microsoft Rights Management](http://go.microsoft.com/fwlink/?LinkId=303970) weboldaláról töltheti le.
> 
> Honnan tudhatja meg, hogy a legújabb verzió van-e telepítve? Keresse meg a **Microsoft Rights Management megosztóalkalmazást** a Programok és szolgáltatások listában, és ellenőrizze a verziószámát. A táblázatban felsorolt beállítási lehetőségek megtekintéséhez és használatához a verziószámnak nagyobbnak kell lennie, mint **1.0.1770.0**. A letöltési oldalon ellenőrizheti a legújabb verziószámot.

A választható beállítások mellett az alábbi kérdések is foglalkoztathatják:

-   [Mi az az automatikusan létrehozott .ppdf-fájl?](#what-s-the-ppdf-file-that-s-automatically-created)

-   [Mi a különbség az általános védelem és a beépített (natív) védelem között?](#what-s-the-difference-between-generic-protection-and-built-in-native-protection)

|Beállítás|Leírás|
|----------|---------------|
|**FELHASZNÁLÓK**|Ha még nem adott meg e-mail-címet az Outlookban, írja be azon személyek e-mail-címét, akik számára lehetővé kívánja tenni a fájl megnyitását.<br /><br />Vegye figyelembe, hogy az RMS megosztóalkalmazás nem minden típusú e-mail-címet támogat.<br /><br />Ha a szervezet a Rights Management (AD RMS) helyszíni verzióját használja, a megadható e-mail-címek a szervezethez tartozó személyekre korlátozódnak. Ha ez az eset áll fenn, és külső e-mail-címeket próbál megadni, egy üzenet jelenik meg, amely arról tájékoztatja, hogy a vállalati konfiguráció kizárólag a vállalaton belül engedélyezi a védett tartalmak megosztását. <br /><br /> Ha a szervezet az Azure RMS-t használja, a megadott e-mail-címek tartozhatnak a saját, illetve más szervezetben dolgozó személyekhez is.<br /><br />Például: **janetm@contoso.com; p.dover@fabrikam.com**<br /><br />Az RMS megosztóalkalmazás jelenleg nem támogatja a személyes e-mail-címek használatát.|
|**Általános védelem**|Ha ezt a beállítást választja, a kijelölt fájl nem látható el natív védelemmel. További információkat itt talál: [Mi a különbség az általános védelem és a beépített (natív) védelem között?](#what-s-the-difference-between-generic-protection-and-built-in-native-protection) (a jelenlegi oldalon).|
|**Megtekintő – Csak megtekintés**<br /><br />**Felülvizsgáló – Megtekintés és szerkesztés**<br /><br />**Társszerző – Megtekintés, szerkesztés, másolás és nyomtatás**<br /><br />**Társtulajdonos – Minden engedély**<br /><br />Megjegyzés: ezen beállítások neve előtt egy kör ikon látható, amely egy földgömböt jelképez. Az ikon használata azt jelzi, hogy általában ezen beállítások valamelyikét kell választani, amikor a mellékletet egy másik szervezetben dolgozó személy számára küldi el.|Akkor válassza ezen beállítások valamelyikét, ha a védett dokumentumra vonatkozó jogosultságokat szeretne megadni. Az egyes beállításokra kattintva megtekintheti a leírásukat.<br /><br />Valamelyik beállítás kiválasztását követően kizárólag a **FELHASZNÁLÓK** részen meghatározott személyek rendelkeznek majd a dokumentum megnyitásához és használatához megadott jogosultságokkal. Hiába továbbítják például valaki másnak a dokumentumot, az nem fogja tudni megnyitni.|
|A rendszergazda által konfigurált házirendsablonok.<br /><br />Ha a például a vállalat neve Contoso, Ltd: **Contoso, Ltd – Bizalmas, csak megtekintésre**<br /><br />Megjegyzés: ezen beállítások neve előtt egy négyzet ikon látható, amely egy irodaépületet jelképez. Az ikon használata azt jelzi, hogy általában ezen beállítások valamelyikét kell választani, amikor a mellékletet a saját szervezetén belül dolgozó személy számára küldi el.|Amikor megosztja a dokumentumot a szervezetben dolgozó személyekkel, megjelennek a rendszergazda által konfigurált házirendsablonok. Akkor válassza ki ezen sablonok valamelyikét, ha a dokumentum nem osztható meg a szervezeten kívül.<br /><br />Ha egy ilyen beállítást választ ki, a rendszergazda határozza meg a dokumentumra vonatkozó jogosultságokat, illetve hogy ki nyithatja azt meg.|
|**A dokumentumok lejárati dátuma**|Ezt a lehetőséget csak időérzékeny fájlok esetében jelölje be, amelyeket a kiválasztott felhasználók a megadott dátumot követően nem fognak tudni megnyitni. Ön továbbra is megnyithatja az eredeti fájlt, azonban a megadott napon éjfél után (az aktuális időzóna szerint) más személyek nem tudják majd megnyitni a fájlt.<br /><br />Ez a beállítás nem érhető el, ha olyan házirendsablont választ, amelyet a rendszergazda konfigurált.|
|**E-mailt kérek a dokumentumok megnyitási kísérleteiről**|Megjegyzés: ez a beállítás jelenleg csak előzetes formában érhető el.<br /><br />Akkor válassza ezt a lehetőséget, ha e-mail értesítést szeretne kapni minden alkalomról, amikor valaki megpróbálja megnyitni az Ön által védetté tett dokumentumot. Az e-mailből megtudhatja, hogy ki és mikor próbálta megnyitni a dokumentumot, illetve hogy sikerrel járt-e.<br /><br />Ez a beállítás csak akkor érhető el, ha a szervezet az Azure RMS-t használja. Ha a szervezet a Rights Management (AD RMS) helyszíni verzióját használja, ez a beállítás nem jelenik meg.|
|**Azonnal vissza lehessen vonni a dokumentumokhoz való hozzáférést**|Akkor válassza ezt a beállítást, ha szüksége lehet a dokumentumok hozzáférésének későbbi visszavonására a dokumentumkövetési webhely használatával, és a visszavonásnak azonnal érvénybe kell lépnie. Ez a beállítás azonban azt eredményezi, hogy amíg a dokumentum hozzáférhető, addig a felhasználóknak a dokumentum olvasásához minden alkalommal internetkapcsolatra van szükségük. Előfordulhatnak olyan esetek, amikor a felhasználók nem tudják az internethez csatlakoztatni mobileszközüket, így nem tudják elolvasni a dokumentumot.<br /><br />Ha nem adja meg ezt a beállítást, a későbbiekben továbbra is visszavonhatja a dokumentum hozzáférését a dokumentumkövetési webhely használatával. Azonban mivel a felhasználók a dokumentum olvasásakor nem csatlakoznak folyamatosan az internethez, ezért előfordulhat, hogy a visszavonásról nem értesülnek azonnal, és egészen addig el tudják olvasni a fájlt, amíg a következő alkalommal hitelesítik magukat az Azure RMS-ben. Alapértelmezés szerint a felhasználók legfeljebb 30 napig olvashatják még el a védett dokumentumot a visszavonást követően, a rendszergazdák azonban módosíthatják ezt az értéket 30 napnál rövidebb vagy hosszabb időtartamra.<br /><br />Ez a beállítás csak akkor érhető el, ha a szervezet az Azure RMS-t használja. Ha a szervezet a Rights Management (AD RMS) helyszíni verzióját használja, ez a beállítás nem jelenik meg.|

## Mi a különbség az általános védelem és a beépített (natív) védelem között?

-   Az **általános védelemmel rendelkező fájlt** a jogosulatlan személyek nem tudják megnyitni. Miután azonban a jogosult személyek megnyitották a fájlt, továbbíthatják azt védelem nélkül más személyeknek, vagy olyan helyre menthetik, amelyhez mások is hozzáférhetnek. A jogosultak egy üzenetből megtudhatják, milyen engedélyeket kaptak a fájlhoz, és az üzenet az engedélyek tiszteletben tartására is megkéri őket, de ez a védelem nem kényszeríthető. Emellett ha egy fájlt általános védelemmel lát el, az engedélyeket nem lehet tovább korlátozni. Nem korlátozhatja például a tartalmat csak megtekintésre vagy a nyomtatás tiltására.

    > [!NOTE]
    > Az általános védelemmel ellátott fájlok fájlnévkiterjesztése mindig **.pfile**.

-   Ha azonban a Rights Management **beépített (natív) védelmét** használja olyan alkalmazásokkal, amelyek ezt lehetővé teszik (például Office-fájlokkal), a fájl védelme akkor sem szűnik meg, ha elküldik valaki másnak vagy egy másik helyen mentik. E fájlok védetté tételekor korlátozó engedélyeket is használhat, például csak olvashatóvá teheti a fájlokat, vagy engedélyezheti azok szerkesztését, miközben letiltja a nyomtatást vagy a másolást. Választhatja például a **Megtekintő – Csak megtekintés** beállítást, így a tartalom nem lesz szerkeszthető, nyomtatható vagy másolható.

További információt a [Rendszergazdai útmutató a Rights Management megosztóalkalmazáshoz](sharing-app-admin-guide.md) témakör [Védelmi szintek – natív és általános](sharing-app-admin-guide-technical.md#levels-of-protection-native-and-generic) című szakaszában talál.

## Mi az az automatikusan létrehozott .ppdf-fájl?

-   Amikor e-mailben oszt meg egy védett fájlt (védett megosztás), az RMS megosztóalkalmazás automatikusan létrehozza a Word-, Excel-, PowerPoint- vagy PDF-fájl **.ppdf** verzióját. Ez a fájl egy védett, csak olvasható verziója, amelyet csak a jogosult személyek nyithatnak meg és amely biztosítja, hogy a címzettek mindig elolvashatják a mellékletet, még akkor is, ha mobileszközükön nem található a Rights Management szolgáltatást natív módon támogató alkalmazás. Ha a címzetteknél telepítve van az RMS-megosztó alkalmazás, akkor el tudják olvasni a mellékletet.

    Ebben az esetben (egy általános védelemmel ellátott fájltól eltérően) kényszerített a használati korlátozás. A címzett nem fogja tudni elmenteni ezt a fájlverziót, és ha valakinek továbbítja a mellékletet, a dokumentumon érvényben maradnak az eredeti korlátozások. Kizárólag az arra jogosult személyek fogják tudni megnyitni a dokumentumot.

    > [!NOTE]
    > A védett megosztásnál (megosztás e-mailben) automatikusan létrejön, a helyben történő védelemnél azonban nem jön létre .ppdf fájl.

## Példák és egyéb útmutatók
A Rights Management megosztóalkalmazás használatát szemléltető egyéb példák és útmutatók a Rights Management megosztóalkalmazás felhasználói útmutatójának következő szakaszaiban találhatók:

-   [Példák az RMS-megosztó alkalmazás használatára](sharing-app-user-guide.md#examples-for-using-the-rms-sharing-application)

-   [Művelet](sharing-app-user-guide.md#what-do-you-want-to-do)

## Lásd még:
[A Rights Management megosztóalkalmazás felhasználói útmutatója](sharing-app-user-guide.md)




<!--HONumber=Jul16_HO3-->


