---
# required metadata

title: Az Azure RMS beállítása az ADAL-hitelesítéshez | Azure RMS
description: Az Azure ADAL alapú hitelesítés konfigurálási lépéseinek ismertetése
keywords: authentication, RMS, ADAL
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: f89f59b7-33d1-4ab3-bb64-1e9bda269935

# optional metadata

#ROBOTS:
audience: developer
#ms.devlang:
ms.reviewer: shubhamp
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Az Azure RMS beállítása az ADAL-hitelesítéshez

Ez a témakör az Azure ADAL-alapú hitelesítés konfigurálásának lépéseit ismerteti.

## Az Azure-beli hitelesítés beállítása

A következőkre lesz szüksége:

- Egy [Microsoft Azure-előfizetés](https://azure.microsoft.com/en-us/) (az ingyenes próbaverzió is elegendő). További információ: [How users sign up for RMS for individuals](../understand-explore/rms-for-individuals-user-sign-up.md) (Útmutató az egyéni RMS-fiók regisztrációjához)
- Egy Microsoft Azure Rights Management-előfizetés (az [egyéni RMS-felhasználók](https://technet.microsoft.com/en-us/library/dn592127.aspx) ingyenes fiókja is elegendő).

> [!NOTE] Érdeklődjön informatikai rendszergazdájánál, hogy rendelkezik-e Microsoft Azure Rights Management-előfizetéssel, és kérje meg a rendszergazdáját az alábbi lépések végrehajtására. Amennyiben az Ön szervezte nem rendelkezik előfizetéssel, kérje meg informatikai rendszergazdáját egy előfizetés létrehozására. Továbbá ajánlatos, hogy informatikai rendszergazdája egy *munkahelyi vagy iskolai fiókkal* végezze el a regisztrációt, és ne *Microsoft-fiókot* (például Hotmail-fiókot) használjon.

A Microsoft Azure-regisztrációt követő lépések:

- Jelentkezzen be az [Azure felügyeleti portálra](https://manage.windowsazure.com) a szervezete nevében egy rendszergazdai jogosultságokkal rendelkező fiókkal.

![Azure-bejelentkezés](../media/AzurePortalLogin.png)

- Görgessen le a portál bal oldalán található **Active Directory** alkalmazásig.

![Az Active Directory kiválasztása](../media/AzureADPick.png)

- Ha még nem hozott létre egy címtárat, kattintson a portál bal alsó sarkában található **Új** gombra.

![Az ÚJ gomb kiválasztása](../media/AzureNewBtn.png)

- Kattintson a **Rights Management** fülre és ellenőrizze, hogy a **Rights Management-állapot** **Aktív**, **Ismeretlen** vagy **Nem engedélyezett** értékű-e. Ha az állapot **Inaktív**, kattintson a portál aljának közepén található **Aktiválás** gombra, és erősítse meg a módosítást.

![Az AKTIVÁLÁS kiválasztása](../media/RMTab.png)

- Ezután hozzon létre egy új *Natív alkalmazást* a címtárban. Ehhez válassza az Alkalmazások lehetőséget, majd a saját címtárát.

![ALKALMAZÁSOK kiválasztása](../media/CreateNativeApp.png)

- Majd kattintson a portál aljának közepén található **Hozzáadás** gombra.

![A HOZZÁADÁS kiválasztása](../media/AddAppBtn.png)

- Az üzenetnél válassza **A szerveztem által fejlesztett alkalmazás hozzáadása** lehetőséget.

![A szerveztem által fejlesztett alkalmazás hozzáadása kiválasztása](../media/AddAnAppPick.png)

- Adja meg az alkalmazás nevét a **NATÍV ÜGYFÉLALKALMAZÁS** kiválasztását követően, majd kattintson a **Tovább** gombra.

![Az alkalmazás elnevezése](../media/TellUsInput.png)

- Adjon hozzá egy átirányítási URI azonosítót, és kattintson a Tovább gombra.
  Az átirányítási URI azonosítónak érvényesnek és egyedinek kell lennie a címtár esetében. Használhat például egy, a következőhöz hasonló azonosítót: `com.mycompany.myapplication://authorize`.

![Átirányítási URI hozzáadása](../media/RedirectURI.png)

- Válassza ki az alkalmazását a címtárban, majd kattintson a **KONFIGURÁLÁS** gombra.

![A KONFIGURÁLÁS kiválasztása](../media/ConfigYourApp.png)

>[!NOTE] Másolja ki, és mentse az **ÜGYFÉL-AZONOSÍTÓ** és az **ÁTIRÁNYÍTÁSI URI** értékét az RMS-ügyfél későbbi konfigurálásához.

- Görgessen az alkalmazásbeállítások aljára, és kattintson az **Alkalmazás hozzáadása** gombra az **egyéb alkalmazások engedélyei** pont alatt.

>[!NOTE] A Windows Azure Active Directory esetében látható **delegált engedélyek** alapértelmezés szerint helyesek – csak egy beállítást szabad kiválasztani, és ez a beállítás a **Beléptetés és felhasználói profil olvasása**.

![Az Alkalmazás hozzáadása kiválasztása](../media/PermissionsToOtherBtn.png)

- Ezután adja hozzá a `00000012-0000-0000-c000-000000000000` GUID azonosítót a **KEZDŐÉRTÉK** szerkesztési mezőhöz, és kattintson az Ellenőrzés gombra.

![A GUID azonosító hozzáadása](../media/AddGUID.png)

- Kattintson a **Microsoft Rights Management** mellett található plusz gombra.

![A + gomb kiválasztása](../media/ChoosePlusBtn.png)

- Ezután válassza a párbeszédpanel bal alsó sarkában található pipajelet.

![A pipajel kiválasztása](../media/ChooseCheck.png)

- Ezt követően már készen áll, hogy hozzáadjon egy függőséget az Azure RMS-alkalmazásához. A függőség hozzáadásához jelölje be az új **Microsoft Rights Management Services** bejegyzést az **egyéb alkalmazások engedélyei** pont alatt, és válassza a **Védett tartalom létrehozása és annak elérése a felhasználók által** jelölőnégyzetet a **Delegált engedélyek** legördülő lista alatt.

![Engedélyek beállítása](../media/AddDependency.png)

- A változtatások megőrzéséhez mentse az alkalmazást a portál aljának közepén található **Mentés** ikon kiválasztásával.

![A MENTÉS kiválasztása](../media/SaveApplication.png)


<!--HONumber=Jun16_HO2-->


