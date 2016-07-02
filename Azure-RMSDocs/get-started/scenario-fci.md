---
title: "Forgatókönyv – Fájlkiszolgáló-megosztáson található fájlok ellátása védelemmel | Azure RMS"
description: 
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 05/20/2016
ms.topic: get-started-article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 283c7db3-5730-439e-a215-40a1088ed506
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 332e102cb27854314b93a71bfeae82a95c9a7812
ms.openlocfilehash: c16098a2d0fe41748280704716a2eeef8921a6fa


---

# Forgatókönyv – Fájlkiszolgáló-megosztáson található fájlok ellátása védelemmel

*A következőkre vonatkozik: Azure Rights Management, Office 365*

Ez a forgatókönyv és támogatási felhasználói dokumentáció az Azure Rights Management használatával tömeges védelmet valósít meg minden védelemmel ellátni kívánt fájl számára egy fájlkiszolgálón, amellyel biztosíthatja, hogy csak a szervezet alkalmazottai érhessék el a fájlokat, még abban az esetben is, ha azokat az informatikai részleg felügyelete alá nem tartozó tárolóra másolják és mentik el, vagy e-mail üzenetben küldik el másoknak.

Ezek az utasítások azt az alapértelmezett sablont használják, amely a használati jogosultságok mindegyikével rendelkező alkalmazottakra korlátozza a hozzáférést. Szükség esetén azonban tovább korlátozhatja a hozzáférést és a használati jogosultságokat egy egyéni sablon konfigurálásával az alapértelmezett sablon használata helyett.

Az utasítások a következő körülmények között alkalmazhatók:

-   Minden fájltípust védeni kíván, nem csak az Office-fájlokat. Azon fájlok, amelyeket az Azure RMS natív módon nem képes védelemmel ellátni, általános védelemmel fognak rendelkezni.

-   A megadott útvonalon található összes fájl (az almappákat is beleértve) védelemmel lesz ellátva.

-   Minden fájl védelmének újbóli alkalmazása rendszeresen megtörténik annak érdekében, hogy a jogmegadási sablon módosításai alkalmazva legyenek a védett fájlokra.

## Üzembe helyezési utasítások
![Rendszergazdai utasítások az Azure RMS gyors üzembe helyezéséhez](../media/AzRMS_AdminBanner.png)

Ellenőrizze, hogy a következő feltételek teljesülnek-e, majd kövesse a támogató eljárásokra vonatkozó utasításokat, mielőtt továbblépne a felhasználói dokumentációra.

## A forgatókönyv követelményei
Ahhoz, hogy a forgatókönyv utasításai működjenek, az alábbiaknak kell teljesülniük:

|Követelmény|Ha további információra van szüksége|
|---------------|--------------------------------|
|Az Azure Rights Management aktiválása megtörtént|[Az Azure Rights Management aktiválása](https://technet.microsoft.com/library/jj658941.aspx)|
|Szinkronizálta a helyszíni Active Directory felhasználói fiókokat az Azure Active Directory vagy az Office 365 szolgáltatással, az e-mail címeket is beleértve. Ez minden olyan felhasználó esetében kötelező, akiknek valószínűleg hozzá kell majd férniük az FCI vagy az Azure Rights Management által védett fájlokhoz.|[Az Azure Rights Management előkészítése](https://technet.microsoft.com/library/jj585029.aspx)|
|A következők egyike:<br /><br />– Alapértelmezett sablon használata az összes felhasználóra vonatkozóan: nem archiválta a &lt;szervezet neve&gt; – Bizalmas alapértelmezett sablont.<br /><br />– Ha egyéni sablont kíván használni adott felhasználókra vonatkozóan: létrehozta és közzétette ezt az egyéni sablont.|[Az Azure Rights Management egyéni sablonok konfigurálása](https://technet.microsoft.com/library/dn642472.aspx)|
|A Windows Microsoft Rights Management megosztóalkalmazás üzembe lett helyezve a felhasználók Windows rendszerű számítógépén.|[A Microsoft Rights Management megosztóalkalmazás automatikus központi telepítése](https://technet.microsoft.com/library/dn339003%28v=ws.10%29.aspx)|
|Letöltötte az RMS Protection eszközt, és konfigurálta az Azure RMS-hez kapcsolódó előfeltételeket.|Az eszköz letöltésével és az előfeltételekkel kapcsolatos utasítások: [RMS Protection Cmdlets](https://msdn.microsoft.com/library/mt433195.aspx) (RMS Protection-parancsmagok).<br /><br />Az Azure RMS további előfeltételeinek, például az egyszerű szolgáltatásfiók konfigurálása: [about_RMSProtection_AzureRMS](https://msdn.microsoft.com/library/mt433202.aspx)|

### Fájlszerver konfigurálása az összes fájl védelemmel való ellátására az Azure RMS és a fájlbesorolási infrastruktúrát használó Fájlkiszolgálói erőforrás-kezelő használatával

1.  Indítson el egy Windows PowerShell-munkamenetet. A munkamenetet nem kell rendszergazdaként futtatnia.

2.  Hajtsa végre a hitelesítést az Azure RMS-ben:

    ```
    Set-RMSServerAuthentication
    ```
    Amikor a rendszer felszólítja, adja meg az RMS Protection-parancsmagok előfeltételeként létrehozott egyszerű szolgáltatásfiók értékeit.

3.  Futtassa az alábbi parancsot a fájlok védelméhez használni kívánt sablon azonosítójának meghatározásához:

    ```
    Get-RMSTemplate
    ```
    A hozzáférést a használati jogosultságok mindegyikével rendelkező alkalmazottakra korlátozó alapértelmezett sablon használatához keresse meg a **&lt;szervezet neve&gt; – Bizalmas** nevű sablont. Például: **VanArsdel, Ltd – Bizalmas**.

4.  Kövesse az [RMS Protection with Windows Server File Classification Infrastructure (FCI)](https://technet.microsoft.com/library/mt601315%28v=ws.10%29.aspx) (RMS-védelem és Windows Server fájlbesorolási infrastruktúra (FCI)) című témakör utasításait.

    Ezek az utasítások tartalmaznak egy Windows PowerShell-parancsfájlt, amelyet egyéni végrehajtható fájlként futtathat a Fájlkiszolgálói erőforrás-kezelőben. Az utasítások arra is kitérnek, hogyan ellenőrizheti, hogy az Azure Rights Management ténylegesen ellátta-e védelemmel a fájlokat.

## A felhasználói dokumentáció utasításai
Ha csak Office-fájlokat látott el védelemmel, vélhetőleg nem kell majd utasításokat adnia felhasználók számára a védett fájlokkal kapcsolatban. Amikor az engedéllyel rendelkező felhasználók megnyitják ezeket a dokumentumokat, azok megnyitása a szokásos módon történik az Office-ban azzal a különbséggel, hogy a felhasználóktól kérheti a rendszer a hitelesítési adataikat, továbbá valószínűleg látni fogják a dokumentum védett állapotáról tájékoztató információs sávot a dokumentum tetején.

Ha a védett fájlok **.ppdf** fájlnévkiterjesztéssel rendelkeznek, vagy védelemmel ellátott szöveg- vagy képfájlok (például **.ptxt** vagy **.pjpg** fájlnévkiterjesztéssel rendelkeznek), akkor a fájlok írásvédettek és nem szerkeszthetők. A felhasználók megtekinthetik a fájlokat az RMS megosztóalkalmazás megjelenítőjével, amelyet a rendszer automatikusan betölt ezen fájltípusok esetén. A fájlokat natív módon védi az Azure RMS, és az alkalmazott sablon minden házirend-beállítását alkalmazza rájuk a használati jogosultságok kivételével, mivel a fájlok írásvédettek. Nem valószínű, hogy felhasználói utasítások megadására lesz szüksége ebben a forgatókönyvben, ha nem tervezi ezen fájltípusok védelmét, érdemes azonban figyelmeztetnie az ügyfélszolgálatot, hogy esetleg el kell magyarázniuk a felhasználóknak, miért nem szerkeszthetik ezeket a fájlokat.

Ha a védett fájlok **.pfile** fájlnévkiterjesztéssel rendelkeznek, a felhasználók megtekinthetik a fájlokat, ha azonban szerkeszteni is szeretnék a tartalmukat és menteni a módosításokat, akkor az eredeti fájlnéven kell menteniük a fájlokat (el kell távolítaniuk a .pfile fájlnévkiterjesztést). Ezeket a fájlokat általános módon védi az Azure RMS, és nem tudja érvényesíteni az alkalmazott sablon minden házirend-beállítását a fájlokra vonatkozóan, ami azzal jár, hogy elveszik a védelem, ha a fájlt új néven mentik. Ebben a forgatókönyvben utasításokat kell majd adni a felhasználóknak.

Az alábbi sablon használatával másolja és illessze be a végfelhasználóknak szóló utasításokat, hogy tisztában legyenek az általánosan védett fájlok szerkesztésének módjával. Hajtsa végre az alábbi módosításokat a környezetnek megfelelően:

-   Cserélje le a *&lt;fájltípus&gt;* és a *&lt;fájlkiszolgáló-megosztás&gt;* kifejezést az általános védelemmel ellátni kívánt fájlok típusával, illetve a fájlkiszolgáló-megosztás nevével.

-   Cserélje le a *&lt;szervezet neve&gt;* kifejezést a szervezetnek az alapértelmezett Azure Rights Management-sablonokban használt nevére.

-   Cserélje le a *&lt;szervezet neve&gt;* kifejezést a szervezet nevére.

-   Cserélje le az *&lt;Útmutató a fájl mentéséhez és a .pfile fájlnévkiterjesztés eltávolításához&gt;* kifejezést az adott fájltípusra vonatkozó alkalmazás-specifikus utasításokkal.

-   Cserélje le a kapcsolattartás adatokat azokra az utasításokra, amelyeket követve a felhasználók elérhetik az ügyfélszolgálatot (például webhelyre mutató hivatkozások, e-mail címek vagy telefonszámok).

-   Hajtsa végre az utasítások további kívánt módosításait, majd küldje el azokat a felhasználóknak.

A példadokumentációban látható, hogyan jelennek meg ezek az utasítások a felhasználók számára a testre szabást követően.

![Felhasználói dokumentációs sablon az Azure RMS gyors üzembe helyezéséhez](../media/AzRMS_UsersBanner.png)

### &lt;Fájltípus&gt; szerkesztése a &lt;fájlkiszolgáló-megosztáson&gt;

1.  Kattintson duplán a fájlra a megnyitásához. Előfordulhat, hogy a rendszer felszólítja a hitelesítő adatainak megadására.

2.  Egy **védett fájl** párbeszédpanelt lát a Microsoft Rights Management megosztóalkalmazásban, amely arra kéri, hogy tartsa tiszteletben a **&lt;szervezet neve&gt; – Bizalmas** engedélyeit. Ez azt jelenti, hogy ne ossza meg ezt a dokumentumot más, a &lt;szervezet neve&gt; szervezetnek nem dolgozó személyekkel.

3.  Kattintson a **Megnyitás** gombra.

4.  A fájl szerkesztéséhez először mentse el a fájlt, majd távolítsa el a .pfile fájlnévkiterjesztést.

    -   &lt;Utasítások a fájl mentésére és a .pfile fájlnévkiterjesztés eltávolítására vonatkozóan&gt;

5.  A fájlt mostantól a megszokott módon szerkesztheti és mentheti.

A fájlt a rendszer rendszeresen újra ellátja védelemmel, aminek során ismét hozzáadja a .pfile fájlnévkiterjesztést, ezért meg kell ismételnie ezeket a lépéseket.

**Segítségre van szüksége?**

-   További információ:

    -   [Védett fájlok megtekintése és használata](https://technet.microsoft.com/library/dn574741%28v=ws.10%29)

-   Lépjen kapcsolatba az ügyfélszolgálattal:

    -   *&lt;kapcsolattartási adatok&gt;*

### Példa testre szabott felhasználói dokumentációra
![Példa felhasználói dokumentációra az Azure RMS gyors üzembe helyezéséhez](../media/AzRMS_ExampleBanner.png)

#### CAD-rajzok szerkesztése a ProjectNextGen megosztásban

1.  Kattintson duplán a fájlra a megnyitásához. Előfordulhat, hogy a rendszer felszólítja a hitelesítő adatainak megadására.

2.  Egy **védett fájl** párbeszédpanelt lát a Microsoft Rights Management megosztóalkalmazásban, amely arra kéri, hogy tartsa tiszteletben a **VanArsdel, Ltd – Bizalmas** engedélyeit. Ez azt jelenti, hogy ne ossza meg ezt a dokumentumot más, a VanArsdel, Ltd vállalatnak nem dolgozó személyekkel.

3.  Kattintson a **Megnyitás** gombra.

4.  A fájl szerkesztéséhez először mentse el a fájlt, majd távolítsa el a .pfile fájlnévkiterjesztést.

    -   **Fájl** &gt; **Mentés másként**

    -   Törölje a **.pfile** kiterjesztést a fájlnév végéről, majd kattintson az **OK** gombra.

5.  A fájlt mostantól a megszokott módon szerkesztheti és mentheti.

A fájlt a rendszer rendszeresen újra ellátja védelemmel, aminek során ismét hozzáadja a .pfile fájlnévkiterjesztést, ezért meg kell ismételnie ezeket a lépéseket.

**Segítségre van szüksége?**

-   További információ:

    -   [Védett fájlok megtekintése és használata](https://technet.microsoft.com/library/dn574741%28v=ws.10%29)

-   Kapcsolatfelvétel az ügyfélszolgálattal: helpdesk@vanarsdelltd.com




<!--HONumber=Jun16_HO4-->


