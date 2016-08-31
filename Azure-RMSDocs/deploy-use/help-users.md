---
title: "Útmutatás nyújtása a felhasználók számára a fájlok védelméhez az Azure Rights Management használatával | Azure RMS"
description: "Az Azure Rights Management szervezeti üzembe helyezését és konfigurálását követően a következőképpen nyújthat segítséget és útmutatást a felhasználóknak, rendszergazdáknak és az ügyfélszolgálatnak."
author: cabailey
manager: mbaldwin
ms.date: 06/09/2016
ms.topic: article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 58f9a6ff-4121-4c8c-9865-1bb290604ad2
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 26b043f1f9e7a1e0cd00c2f31c28f7d6685f0232
ms.openlocfilehash: 329b9cb2fd6507638924f836eb6dffe8ffca43d1


---

# Útmutatás nyújtása a felhasználók számára a fájlok védelméhez az Azure Rights Management használatával

>*A következőkre vonatkozik: Azure Rights Management, Office 365*

Az Azure Rights Management szervezeti üzembe helyezését és konfigurálását követően a következőképpen nyújthat segítséget és útmutatást a felhasználóknak, rendszergazdáknak és az ügyfélszolgálatnak:

-   **Információk végfelhasználóknak:**

    Tudassa a felhasználókkal, hogy mikor és hogyan kell védelemmel ellátni a bizalmas információkat tartalmazó dokumentumokat és e-maileket. Amikor csak lehetséges, ezt a meglévő munkafolyamataikhoz kapcsolódóan ismertesse, hogy a teljesen új folyamatok megismerése helyett egy számukra már ismerős folyamatba építhessék be a további lépéseket. Mindenképpen ismertesse velük az adott vállalat szempontjából tapasztalható előnyöket (és kockázatokat), továbbá nyújtson útmutatást arra vonatkozóan, hogy mikor kell védelemmel ellátniuk a fájlokat és e-maileket. Ha konfigurálta az [egyéni sablonokat](configure-custom-templates.md), lássa el őket az arra vonatkozó utasításokkal, hogy melyiket válasszák ki, ha a sablon neve és leírása nem elegendő számukra a megfelelő sablon kiválasztásához.

    > [!TIP]
    > Mintavideók végfelhasználók számára:
    >
    > -   [Az Azure RMS által nyújtott felhasználói élmény](http://channel9.msdn.com/Series/Information-Protection/Azure-RMS-user-experience)
    > -   [Azure RMS dokumentumkövetés és visszavonás](http://channel9.msdn.com/Series/Information-Protection/Azure-RMS-Document-Tracking-and-Revocation)

-   **Információk rendszergazdáknak:**

    Egyes alkalmazások a rendszergazdák által konfigurált házirendeket és beállításokat használva automatikus adatvédelmet alkalmaznak. Lehetséges, hogy az ilyen alkalmazásokra vonatkozóan utasításokkal kell ellátnia az ezeket az alkalmazásokat és szolgáltatásokat felügyelő rendszergazdákat. További információ:[ Hogyan támogatják a különböző alkalmazások az Azure Rights Managementet?](../understand-explore/applications-support.md) és [Alkalmazások konfigurálása az Azure Rights Managementhez](configure-applications.md).

-   **Információk az ügyfélszolgálatnak:**

    Az ügyfélszolgálat számára az egyik leghasznosabb eszköz az [RMS elemző](https://www.microsoft.com/en-us/download/details.aspx?id=46437). Az eszközt az ügyfélszolgálat munkatársai futtathatják Azure RMS rendszergazdai beállítással, a felhasználókat pedig kérhetik, hogy Azure RMS felhasználói beállítással futtassák azt. Ez az eszköz nem csupán a problémák azonosításában segít, de ki is javítja az észlelt problémákat, illetve, ha ez nem sikerül, nyomkövetési naplókat rögzít.

    Ha hiteles kérelem érkezik a védett dokumentumokhoz való teljes jogosultságú hozzáférésre vonatkozóan, például a jogi részlegtől vagy egy alkalmazott felettesétől az alkalmazott távozását követően, győződjön meg róla, hogy az ügyfélszolgálat a [felügyelői funkció](configure-super-users.md) használatával eléri a kérelmezéshez szükséges folyamatokat.

    Az alábbiakban néhány tipikus, a felhasználók által jelentett problémát láthat:

    -   **Bejelentkezési segítség:**

        Előfordulhat, hogy a rendszer hitelesítő adatokat kér a felhasználótól, ha az Azure RMS-nek hitelesítenie kell a felhasználót, de nem érhetők el a gyorsítótárazott hitelesítő adatok. Ez a felhasználó munkahelyi vagy iskolai fiókja és jelszava, amely az Office 365-bérlőhöz vagy az Azure Active Directory-bérlőhöz tartozik. Ez nem lehet egy Microsoft-fiók (korábban Microsoft Live ID) vagy a felhasználó személyes e-mail-fiókja, mert ezek használatát az Azure RMS jelenleg nem támogatja. Lássa el a megfelelő utasításokkal a felhasználókat és az ügyfélszolgálatot arra vonatkozóan, hogy melyik fiók szükséges a hitelesítő adatok megadásakor, ha ezeket az alkalmazásokat az Azure RMS szolgáltatással használják.

    -   **Tartalomvédelemmel vagy a tartalom felhasználásával kapcsolatos problémák:**

        Győződjön meg róla, hogy a felhasználók rendelkeznek az általuk használt alkalmazásra vonatkozó megfelelő utasításokkal, és hogy az Azure RMS által támogatott alkalmazásokat és eszközöket használnak. A támogatott alkalmazásokkal és eszközökkel kapcsolatos további információért lásd: [Az Azure Rights Management követelményei](../get-started/requirements-azure-rms.md).

        Ha a felhasználók hibát észlelnek a tartalmak védelme vagy felhasználása során, kérje meg őket az [RMS elemző](https://www.microsoft.com/en-us/download/details.aspx?id=46437) Azure RMS-felhasználóként történő futtatására.

        Ha a felhasználók meg tudják nyitni a védett tartalmakat, de nem rendelkeznek a számukra szükséges jogosultságokkal, kérje meg őket az [RMS elemző](https://www.microsoft.com/en-us/download/details.aspx?id=46437) Azure RMS-felhasználóként történő futtatására, valamint a sablonok letöltésére és megtekintésére. Így meggyőződhetnek róla, hogy a sablonokat sikeresen letöltötték, valamint ellenőrizhetik a sablonok által biztosított jogosultságokat. Lehetséges, hogy a problémát az okozza, hogy a felhasználó nem tagja a sablonhoz konfigurált megfelelő csoportnak, vagy a sablont újra kell konfigurálni a felhasználó számára.

A következő, alkalmazásspecifikus információkkal kapcsolatos szakaszban leírtakkal segíthet a felhasználóknak a bizalmas dokumentumok és e-mailek védelmében.

## Adatvédelem a Windows Microsoft Rights Management megosztóalkalmazással
A Rights Management (RMS) megosztóalkalmazás az Office 2010-zel rendelkező felhasználók számára szükséges a tartalomvédelemhez és a védett tartalmak felhasználásához, de a használata javasolt minden, az Azure RMS szolgáltatást támogató számítógépen és mobileszközözön.

Azonkívül, hogy egyszerűbbé teszi a fontos dokumentumok védelmét, az RMS megosztóalkalmazás lehetővé teszi a felhasználók számára a védett dokumentumok nyomon követését, és szükség esetén a hozzáférés visszavonását.

Az alkalmazás Windows rendszerű számítógépeken való használatára vonatkozó útmutatásért lásd [a Rights Management megosztóalkalmazás felhasználói útmutatóját](../rms-client/sharing-app-user-guide.md).

Mobileszközök esetén: [A Microsoft Rights Management megosztóalkalmazás mobilplatformokra kiadott verziójával kapcsolatos gyakori kérdések](http://technet.microsoft.com/dn451248).

> [!TIP]
> Általános példa képernyőfelvételekkel: [A felhasználók biztonságosan oszthatják meg a mellékleteket a mobilfelhasználókkal](../understand-explore/what-admins-users-see.md#users-safely-share-attachments-with-mobile-users).

## Adatvédelem használata Office 365-tel, Office 2016-tal és Office 2013-mal
Ha használja az Azure RMS szolgáltatást, de nem telepítette a Rights Management megosztóalkalmazást, a felhasználók nem látják a **Védett megosztás** gombot a menüszalagon, sem pedig **Helyi védelem** lehetőséget a Fájlkezelőben, ami egyszerűbbé tenné számukra a fájlok védelmét. Ezeknek a felhasználóknak az alábbiakhoz hasonló utasításokat kell követniük.

> [!TIP]
> Alkalmazásspecifikus súgókért és az adott alkalmazásokra vonatkozó, adatvédelemmel kapcsolatos utasításokért végezzen egy keresést, melynek kulcsszavai az **IRM**, illetve az alkalmazás neve és verziószáma.

#### Dokumentumvédelem a Word 2013-ban

1.  Hozzon létre egy új dokumentumot a Microsoft Wordben.

2.  Kattintson a **Fájl** menüben az **Információ**, **Dokumentumvédelem**, majd a **Hozzáférés korlátozása** lehetőségre. Ezután válasszon ki egy sablont a megfelelő használati jogok gyors alkalmazásához, vagy a **Hozzáférés korlátozása** lehetőség kiválasztását követően válassza ki saját kezűleg a kívánt használati jogokat.

    > [!NOTE]
    > Ha első alkalommal használja a Rights Managementet, kapcsolatba fog lépni az [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] szolgáltatással, és meg kell adnia a hitelesítő adatokat az Office IRM-ügyfél konfigurálásához.

3.  Mentse a dokumentumot.

Más felhasználók csak a hitelesítést követően nyithatják meg a dokumentumot. Ha nem jogosultak a megnyitására, a dokumentum nem nyílik meg. Ha jogosultak a megnyitására, a dokumentum az adott felhasználóhoz megadott korlátozott használati jogokkal nyílik meg. Például egy „Csak megtekintésre” jogosult felhasználó még akkor sem szerkesztheti vagy mentheti a dokumentumot, ha azt előtte másik helyre másolták. A használati jogok a dokumentum tetején, egy korlátozási szalagcímben jelennek meg. A szalagcím megjelenítheti a dokumentumra alkalmazott engedélyeket, vagy tartalmazhat egy hivatkozást is a megjelenítésükhöz.

#### E-mail-üzenetek védelme az Outlook 2013-ban és az Exchange Online-ban

1.  Hozzon létre az Outlookban egy új, a szervezeten belüli címzettel rendelkező e-mail-üzenetet.

2.  Kattintson a **BEÁLLÍTÁSOK** lapon az **Engedély** elemre, és válassza ki az egyik lehetőséget. Például: **Nem továbbítandó**, **&lt;Vállalat neve&gt; – Bizalmas** vagy **&lt;Vállalat neve&gt; – Bizalmas, csak megtekintésre**.

3.  Küldje el az üzenetet.

A védett dokumentumok megtekintéséhez hasonlóan a címzettek csak a hitelesítést követően nyithatják meg az e-mail-üzenetet. Ha jogosultak a megtekintésére, az e-mail-üzenet az adott felhasználóhoz megadott korlátozott használati jogokkal nyílik meg. Például, ha a **Nem továbbítandó** lehetőséget választotta ki, a Továbbítás gomb nem érhető el a szalagon.

#### E-mail-üzenetek védelme az Outlook Web App használatával

1.  Hozzon létre az Outlook Web App alatt egy új, a szervezeten belüli címzettel rendelkező e-mail-üzenetet.

2.  Kattintson a **…**, majd az **engedély beállítása** elemre, és válassza ki az egyik lehetőséget. Például: **Nem továbbítandó**, **Nem küldhető válasz mindenkinek**, **&lt;Vállalat neve&gt; – Bizalmas** vagy **&lt;Vállalat neve&gt; – Bizalmas, csak megtekintésre**.

3.  Küldje el az üzenetet.

A védett dokumentumok megtekintéséhez hasonlóan a címzettek csak a hitelesítést követően nyithatják meg az e-mail-üzenetet. Ha jogosultak a megtekintésére, az e-mail-üzenet az adott felhasználóhoz megadott korlátozott használati jogokkal nyílik meg. Például, ha a **Nem küldhető válasz mindenkinek** lehetőséget választotta ki, a **VÁLASZ MINDENKINEK** gomb nem érhető el az üzenetablakban.





<!--HONumber=Aug16_HO4-->


