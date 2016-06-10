---
# required metadata

title: Forgatókönyv – Office-fájl megosztása egy másik szervezet felhasználóival | Azure RMS
description:
keywords:
author: cabailey
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: c10a4d7b-f57a-4a43-b66e-477777be59cc

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: esaggese
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Forgatókönyv – Office-fájl megosztása egy másik szervezet felhasználóival

*A következőkre vonatkozik: Azure Rights Management, Office 365*

Ez a forgatókönyv és a kiegészítő felhasználói dokumentáció az Azure Rights Managementet használja, hogy a felhasználók biztonságosan küldhessenek e-mailen keresztül Office-fájlokat más szervezet felhasználóinak. Az Office-fájl például lehet Word-dokumentum, Excel-táblázat vagy PowerPoint-bemutató, amely egy partnereknek szóló árlistát, viszonteladók terméklistáját vagy potenciális vevők szállítási határidőinek listáját tartalmazza. Ha a felhasználók követik az utasításokat, az e-mail-üzenethez csatolt fájlt az Azure Rights Management védelemmel látja el.

Ez a forgatókönyv a következő körülmények között alkalmazható:

-   Az alkalmazottnak információt kell küldenie a szervezeten kívülre, e-mailen keresztül, Office-dokumentumot tartalmazó melléklet formájában.

-   A dokumentum nem nyilvános, de nem kizárólag belső használatra szánt információkat tartalmaz.

-   A címzett felhasználókkal szemben nem követelmény az információk további megosztása másokkal, azok kinyomtatása, vagy a saját dokumentációjukban történő felhasználása. Ha a fenti feltételek nem teljesülnek, módosíthatja a felhasználói utasításokat a csak megtekintési engedélyek más lehetőségekre történő módosításával, így engedélyezheti, hogy a címzett megváltoztathassa a mellékletet.

-   Az alkalmazottakról feltételezhető, hogy érdekli őket, hogy a külső felhasználó mikor nyitja meg a dokumentumot.

## Üzembe helyezési utasítások
![Rendszergazdai utasítások az Azure RMS gyors üzembe helyezéséhez](../media/AzRMS_AdminBanner.png)

Ellenőrizze, hogy a következő feltételek teljesülnek-e, mielőtt továbblépne a felhasználói dokumentációra.

## A forgatókönyv követelményei
Ahhoz, hogy a forgatókönyvre vonatkozó felhasználói utasítások működjenek, az alábbiaknak kell teljesülniük:

|Követelmény|Ha további információra van szüksége|
|---------------|--------------------------------|
|Előkészítette a fiókokat és a csoportokat az Office 365 vagy az Azure Active Directory számára|[Az Azure Rights Management előkészítése](https://technet.microsoft.com/library/jj585029.aspx)|
|Az Azure Rights Management aktiválása megtörtént|[Az Azure Rights Management aktiválása](https://technet.microsoft.com/library/jj658941.aspx)|
|A Windows Microsoft Rights Management megosztóalkalmazás üzembe lett helyezve a felhasználók Windows rendszerű számítógépén.|[A Microsoft Rights Management megosztóalkalmazás automatikus központi telepítése](https://technet.microsoft.com/library/dn339003%28v=ws.10%29.aspx)|
|A felhasználók az Office 2013 Outlook alkalmazásával rendelkeznek.|Ha a felhasználók Office 2010-zel rendelkeznek, a képernyőfelvételt cserélje le a megfelelő verzióra, hogy a kép megfeleljen annak, amit a felhasználók látnak.|
|Az Azure RMS-előfizetés tartalmazza a dokumentumok nyomon követését biztosító szolgáltatást.|Ha az Azure RMS-előfizetés nem tartalmazza a dokumentumok nyomon követését és visszavonását biztosító szolgáltatást, a felhasználók nem tudják majd végrehajtani a felhasználói utasítások mindegyik lépését. Ebben az esetben olyan előfizetést kell vásárolnia, amely támogatja ezeket a szolgáltatásokat, vagy módosítsa a felhasználói utasításokat, és távolítsa el a szolgáltatások használatára vonatkozó lépéseket.<br /><br />Az előfizetéssel járó támogatás ellenőrzése: [Comparison of Rights Management Services (RMS) Offerings](https://technet.microsoft.com/dn858608) (A Tartalomvédelmi szolgáltatásokra (RMS) vonatkozó ajánlatok összehasonlítása).|

## A felhasználói dokumentáció utasításai
Az alábbi sablon használatával másolja és illessze be a felhasználói utasításokat egy végfelhasználóknak szóló üzenetbe, és végezze el a módosításokat a környezetének megfelelő adatok érdekében:

1.  Cserélje le az *&lt;Office-dokumentumtípus nevét&gt;* arra a dokumentumtípusra, amelyet a felhasználók el fognak küldeni. Használjon a felhasználók munkafolyamataira jellemző és megszokott kifejezéseket. Ilyen lehet például az „árlista”, „szállítási idő” vagy „ajánlattétel” a „Word-dokumentum” vagy „Excel-táblázat” helyett. A megfelelő kifejezések használata növeli annak valószínűségét, hogy a felhasználók követni fogják az utasításokat a dokumentumok használata során.

2.  Cserélje le a *&lt;kapcsolattartás adatok&gt;* szöveget azokra az utasításokra, amelyeket követve a felhasználók elérhetik az ügyfélszolgálatot (pl. webhelyhivatkozások, e-mail címek vagy telefonszámok).

3.  **További megfontolandó módosítások:**

    -   Javasoljuk, hogy a 2. lépésben a **Megtekintő – Csak megtekintés** beállítást adja meg az engedélyekhez, amely a címzettek számára írásvédetté teszi a csatolt dokumentumot (az eredetit azonban nem). Ha ez a korlátozás nem felel meg az adott üzleti követelménynek, módosítsa ezt a beállítást más engedélykészletre. Ilyen lehet például a **Felülvizsgáló – Megtekintés és szerkesztés**.

    -   A 3. lépésben az **Azonnal vissza lehessen vonni a dokumentumokhoz való hozzáférést** beállítást javasoljuk, így nem lesz késleltetés, ha a felhasználók később visszavonják a dokumentumot, a beállítás megadása azonban azzal jár, hogy a címzettnek mindig rendelkeznie kell internetkapcsolattal a melléklet megnyitásához. A lépés végrehajtásához az is kell, hogy a dokumentumok nyomon követését és visszavonását támogató előfizetéssel rendelkezzen. Törölje ezt a lépést, ha a felhasználókra nem vonatkoztatható.

    -   A 4. lépésben az **E-mailt kérek a dokumentum megnyitási kísérleteiről** beállítás használatát javasoljuk. Ha a felhasználók nyomon követik a dokumentumokat a dokumentumkövető portál használatával, dönthet úgy, hogy az e-mailben küldött értesítés nem szükséges, és törölheti ezt a lépést.

    -   A lépések nem foglalják magukban a lejárati dátum beállítását. Ha az információk nem használhatók egy adott dátumot követően, adjon hozzá egy újabb lépést a megfelelő lejárati dátum (például az e-mail-üzenet elküldésétől számított 90 nap) beállítására.

    > [!NOTE] További információ a felhasználók által választható egyes beállításokkal kapcsolatban: [A Rights Management megosztóalkalmazás párbeszédpanel-beállításai](https://technet.microsoft.com/library/dn574738.aspx).

4.  Végezzen el bármilyen egyéb tetszés szerinti módosítást az utasításkészletre vonatkozóan, majd küldje el az érintett felhasználóknak.

A példadokumentációban látható, hogyan jelennek meg ezek az utasítások a felhasználók számára a testre szabást követően.

![Felhasználói dokumentációs sablon az Azure RMS gyors üzembe helyezéséhez](../media/AzRMS_UsersBanner.png)

### Office-dokumentumtípus &lt;nevének megosztása&gt;

1.  Hozza létre az e-mail-üzenetet az e-mail-cím vagy -címek megadásával, írja be az üzenetet, majd csatolja az *&lt;Office-dokumentumtípus neve&gt;* fájlt az e-mail-üzenethez. Ezt követően kattintson az **ÜZENET** lap **RMS** csoportjának **Védett megosztás** elemére, majd kattintson újra a **Védett megosztás** elemre:

    ![Office-dokumentum Outlookkal történő megosztását bemutató képernyőfelvétel](../media/AzRMSUserInstructions_ShareProtectedRibbon2013.png)

2.  A **Védett megosztás** párbeszédpanelen válassza a **Megtekintő – Csak megtekintés** beállítást:

    ![Védett megosztás párbeszédpanel – Megtekintő – Csak megtekintés](../media/AzRMS_SharedProtected_ViewerOnly.PNG)

3.  Jelölje be az **Azonnal vissza lehessen vonni a dokumentumokhoz való hozzáférést** jelölőnégyzetet:

    ![Védett megosztás párbeszédpanel – Azonnali visszavonás](../media/AzRMS_SharedProtected_InstantRevoke.PNG)

4.  Jelölje be az **E-mailt kérek a dokumentum megnyitási kísérleteiről** jelölőnégyzetet:

    ![Védett megosztás párbeszédpanel – E-mailt kérek](../media/AzRMS_SharedProtected_EmailMe.PNG)

5.  Kattintson az **Azonnali küldés** parancsra.

Ha egy, a **Címzett**, a **Másolatot kap** vagy a **Titkos másolat** sorban szereplő személy megkapja az e-mailt, egy üzenet is megjelenik, amely utasításokat tartalmaz arra vonatkozóan, hogyan olvashatja el a csatolt *&lt;Office-dokumentípus neve&gt;* fájlt. A címzettek számos eszközön, például iPaden, iPhone-on, Android rendszerű táblagépen és telefonon, Mac vagy Windows rendszerű számítógépen is elolvashatják a dokumentumot.

A [dokumentumkövető portál](https://track.azurerms.com/) használatával követheti nyomon, hogy a címzettek megnyitották-e az &lt;Office-dokumentumtípus neve&gt; fájlt, és ha igen, mikor. Ha szükségesnek érzi, telefonon is felveheti velük a kapcsolatot, miután látta, hogy megnyitották az &lt;Office-dokumentumtípus neve&gt; fájlt.

**Segítségre van szüksége?**

-   További információ:

    -   [E-mailben megosztott fájl védelme](https://technet.microsoft.com/library/dn574735%28v=ws.10%29.aspx)

    -   [Dokumentumok nyomon követése és visszavonása](https://technet.microsoft.com/library/dn986611.aspx)

-   Lépjen kapcsolatba az ügyfélszolgálattal:

    -   *&lt;kapcsolattartási adatok&gt;*

### Példa testre szabott felhasználói dokumentációra
![Példa felhasználói dokumentációra az Azure RMS gyors üzembe helyezéséhez](../media/AzRMS_ExampleBanner.png)

#### Árlista megosztása az ügyféllel

1.  Hozza létre az e-mail-üzenetet az ügyfél e-mail-címének vagy -címeinek a megadásával, írja be az üzenetet, majd csatolja a legújabb árlistát az e-mail-üzenethez. Ezt követően kattintson az **ÜZENET** lap **RMS** csoportjának **Védett megosztás** elemére, majd kattintson újra a **Védett megosztás** elemre:

    ![Office-dokumentum Outlookkal történő megosztását bemutató képernyőfelvétel](../media/AzRMSUserInstructions_ShareProtectedRibbon2013.png)

2.  A **Védett megosztás** párbeszédpanelen válassza a **Megtekintő – Csak megtekintés** beállítást:

    ![Védett megosztás párbeszédpanel – Megtekintő – Csak megtekintés](../media/AzRMS_SharedProtected_ViewerOnly.PNG)

3.  Jelölje be az **Azonnal vissza lehessen vonni a dokumentumokhoz való hozzáférést** jelölőnégyzetet:

    ![Védett megosztás párbeszédpanel – Azonnali visszavonás](../media/AzRMS_SharedProtected_InstantRevoke.PNG)

4.  Jelölje be az **E-mailt kérek a dokumentum megnyitási kísérleteiről** jelölőnégyzetet:

    ![Védett megosztás párbeszédpanel – E-mailt kérek](../media/AzRMS_SharedProtected_EmailMe.PNG)

5.  Kattintson az **Azonnali küldés** parancsra.

Ha egy, a **Címzett**, a **Másolatot kap** vagy a **Titkos másolat** sorban szereplő személy megkapja az e-mailt, egy üzenet is megjelenik, amely utasításokat tartalmaz arra vonatkozóan, hogyan olvashatja el a csatolt árlistát. A címzettek számos eszközön, például iPaden, iPhone-on, Android rendszerű táblagépen és telefonon, Mac vagy Windows rendszerű számítógépen is elolvashatják a dokumentumot.

A [dokumentumkövetési portál](https://track.azurerms.com/) használatával követheti nyomon, hogy a címzettek megnyitották-e az árlistát, és ha igen, mikor. Ha szükségesnek érzi, telefonon is felveheti velük a kapcsolatot, miután látta, hogy megnyitották az árlistát.

**Segítségre van szüksége?**

-   További információ:

    -   [E-mailben megosztott fájl védelme](https://technet.microsoft.com/library/dn574735%28v=ws.10%29.aspx)

    -   [Dokumentumok nyomon követése és visszavonása](https://technet.microsoft.com/library/dn986611.aspx)

-   Lépjen kapcsolatba az ügyfélszolgálattal:

    -   E-mail: helpdesk@vanarsdelltd.com



<!--HONumber=May16_HO2-->


