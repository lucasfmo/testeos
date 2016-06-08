---
# required metadata

title: ADAL-hitelesítés RMS-kompatiblis alkalmazásokhoz | Azure RMS
description: Az ADAL hitelesítési folyamatának ismertetése
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
** Ez az SDK-tartalom nem naprakész. Ideiglenesen arra kérjük, keresse fel az MSDN webhelyén található dokumentáció [aktuális verzióját](https://msdn.microsoft.com/library/windows/desktop/hh535290(v=vs.85).aspx). **
# ADAL-hitelesítés RMS-kompatiblis alkalmazásokhoz

Az RMS-ügyfél 2.1-es verziója mostantól magában foglalja az Azure ADAL-t használó alkalmazások Azure RMS-sel történő hitelesítésének lehetőségét.

Az alkalmazásnak a Microsoft Online bejelentkezési segéd helyett az ADAL-hitelesítés használatára való frissítésével Ön és ügyfelei az alábbiakra lesznek képesek:

- Többtényezős hitelesítés használata.
- Az RMS 2.1 ügyfél telepítése rendszergazdai jogosultságok nélkül a számítógépen.
- Az alkalmazás tanúsítása a Windows 10-re.

## A hitelesítési folyamat két megközelítése

Ez a témakör a hitelesítési folyamat két megközelítését ismerteti, a megfelelő programkódpéldákkal kiegészítve.

- **Belső hitelesítés** – Az RMS SDK által kezelt OAuth-hitelesítés. Ezt a megközelítést akkor használja, ha azt szeretné, hogy az RMS-ügyfél egy ADAL-hitelesítési üzenetet jelenítsen meg, ha hitelesítésre van szükség. Az alkalmazás konfigurálásával kapcsolatos további részleteket a „Belső hitelesítés” című szakaszban találja.

> [!NOTE] Ha az Ön alkalmazása jelenleg a bejelentkezési segéddel kiegészített AD RMS SDK 2.1-et használja, az alkalmazás áttelepítési útvonalaként a belső hitelesítési módszer használatát ajánljuk.

- **Külső hitelesítés** – Az alkalmazás által kezelt OAuth-hitelesítés. Ezt a megközelítést akkor használja, ha azt szeretné, hogy az alkalmazása kezelje az OAuth-hitelesítést. Ezzel a megközelítéssel az RMS-ügyfél egy, az alkalmazás által meghatározott visszahívást intéz, ha hitelesítésre van szükség. Részletes példákat a „Külső hitelesítés” című szakaszban talál, a jelen témakör végén.

> [!NOTE] A külső hitelesítés nem feltétlenül jelenti a felhasználóváltás lehetőségét is: az RMS-ügyfél ugyanis mindig az alapértelmezett felhasználót veszi alapul egy adott RMS-bérlő esetében.

### Belső hitelesítés

A következőkre lesz szüksége:

- Egy [Microsoft Azure-előfizetés](https://azure.microsoft.com/en-us/) (az ingyenes próbaverzió is elegendő).
- Egy Microsoft Azure Rights Management-előfizetés (az [egyéni RMS-felhasználók](https://technet.microsoft.com/en-us/library/dn592127.aspx) ingyenes fiókja is elegendő).

> [!NOTE] Érdeklődjön informatikai rendszergazdájánál, hogy rendelkezik-e Microsoft Azure Rights Management-előfizetéssel, és kérje meg a rendszergazdáját az alábbi lépések végrehajtására. Amennyiben az Ön szervezte nem rendelkezik előfizetéssel, kérje meg informatikai rendszergazdáját egy előfizetés létrehozására. Továbbá ajánlatos, hogy informatikai rendszergazdája egy munkahelyi vagy iskolai fiókkal végezze el a regisztrációt Microsoft-fiók (pl. Hotmail-fiók) használata helyett.

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

- Majd kattintson a portál aljának közepén található **HOZZÁADÁS** gombra.

![A HOZZÁADÁS kiválasztása](../media/AddAppBtn.png)

- Az üzenetnél válassza **A szerveztem által fejlesztett alkalmazás hozzáadása** lehetőséget.

![A szerveztem által fejlesztett alkalmazás hozzáadása kiválasztása](../media/AddAnAppPick.png)

- Adja meg az alkalmazás nevét a **NATÍV ÜGYFÉLALKALMAZÁS** kiválasztását követően, majd kattintson a **Tovább** gombra.

![Az alkalmazás elnevezése](../media/TellUsInput.png)

- Adjon hozzá egy átirányítási URI azonosítót, és kattintson a Tovább gombra. Az átirányítási URI azonosítónak érvényesnek és egyedinek kell lennie a címtár esetében. Használhat például egy, a következőhöz hasonló azonosítót: `com.mycompany.myapplication://authorize`.

![Átirányítási URI hozzáadása](../media/RedirectURI.png)

- Válassza ki az alkalmazását a címtárban, majd kattintson a **KONFIGURÁLÁS** gombra.

![A KONFIGURÁLÁS kiválasztása](../media/ConfigYourApp.png)

>[!NOTE] Másolja ki, és mentse az **ÜGYFÉL-AZONOSÍTÓ** és az **ÁTIRÁNYÍTÁSI URI** értékét az RMS-ügyfél későbbi konfigurálásához.

- Görgessen az alkalmazásbeállítások aljára, és kattintson az **Alkalmazás hozzáadása** gombra az **egyéb alkalmazások engedélyei** pont alatt.

![Az Alkalmazás hozzáadása kiválasztása](../media/PermissionsToOtherBtn.png)

- Ezután adja hozzá a `00000012-0000-0000-c000-000000000000` GUID azonosítót a **KEZDŐÉRTÉK** szerkesztési mezőhöz, és kattintson az Ellenőrzés gombra.

![A GUID azonosító hozzáadása](../media/AddGUID.png)

- Kattintson a **Microsoft Rights Management** mellett található Plusz (+) gombra.

![A + gomb kiválasztása](../media/ChoosePlusBtn.png)

- Ezután válassza a párbeszédpanel bal alsó sarkában található pipajelet.

![A pipajel kiválasztása](../media/ChooseCheck.png)

- Ezt követően már készen áll, hogy hozzáadjon egy függőséget az Azure RMS-alkalmazásához. A függőség hozzáadásához jelölje be az új **Microsoft Rights Management Services** bejegyzést az **egyéb alkalmazások engedélyei** pont alatt, és válassza a **Védett tartalom létrehozása és annak elérése a felhasználók által** jelölőnégyzetet a **Delegált engedélyek** legördülő lista alatt.

![Engedélyek beállítása](../media/AddDependency.png)

- A változtatások megőrzéséhez mentse az alkalmazást a portál aljának közepén található **MENTÉS** ikon kiválasztásával.

![A MENTÉS kiválasztása](../media/SaveApplication.png)

- Ezt követően már készen áll alkalmazása az RMS SDK 2.1 által biztosított belső ADAL-hitelesítés használatához történő konfigurálására. Az RMS-ügyfél konfiguráláshoz rögtön az [IpcInitialize](/rights-management/sdk/2.1/api/win/IpcInitialize) hívása után adjon hozzá egy [IpcSetGlobalProperty](/rights-management/sdk/2.1/api/win/IpcSetGlobalProperty)-hívást. A következő kódrészletet mintaként használhatja.


    IpcInitialize();

    IPC_AAD_APPLICATION_ID applicationId = { 0 };   applicationId.cbSize = sizeof(IPC_AAD_APPLICATION_ID);   applicationId.wszClientId = L"az-AAD-által-az-alkalmazásához-megadott-GUID-(zárójelek-nélkül)";   applicationId.wszRedirectUri = L"az-AAD-által-az-alkalmazásához-megadott-URI://authorize";

    HRESULT hr = IpcSetGlobalProperty(IPC_EI_APPLICATION_ID, &amp;applicationId);

    if (FAILED(hr)) {    //hibakezelés   }

### Külső hitelesítés

- A saját hitelesítési tokenek kezeléséhez az alábbi programkódot használhatja mintaként.


    extern HRESULT GetADALToken(LPVOID pContext, const IPC_NAME_VALUE_LIST&amp; Parameters, __out wstring wstrToken) throw();

    HRESULT GetLicenseKey(PCIPC_BUFFER pvLicense, __in LPVOID pContextForAdal, __out IPC_KEY_HANDLE &amp;hKey) { IPC_OAUTH2_CALLBACK pfGetADALToken =         [](LPVOID pvContext, PIPC_NAME_VALUE_LIST pParameters, IPC_AUTH_TOKEN_HANDLE* phAuthToken) -&gt; HRESULT { wstring wstrToken; HRESULT hr = GetADALToken(pvContext, *pParameters, wstrToken); return SUCCEEDED(hr) ? IpcCreateOAuth2Token(wstrToken.c_str(), OUT phAuthToken) : hr; };

      IPC_OAUTH2_CALLBACK_INFO callbackCredentialContext =
      {
          sizeof(IPC_OAUTH2_CALLBACK_INFO),
          pfGetADALToken,
          pContextForAdal
      };

      IPC_CREDENTIAL credentialContext =
      {
          IPC_CREDENTIAL_TYPE_OAUTH2,
          NULL
      };
      credentialContext.pcOAuth2 = &amp;callbackCredentialContext;

      IPC_PROMPT_CTX promptContext =
      {
        sizeof(IPC_PROMPT_CTX),
        NULL,
        IPC_PROMPT_FLAG_SILENT | IPC_PROMPT_FLAG_HAS_USER_CONSENT,
        NULL,
        &amp;credentialContext
      };

      hKey = 0L;
      return IpcGetKey(pvLicense, 0, &amp;promptContext, NULL, &amp;hKey);
  }

### Kapcsolódó témakörök
- [Adattípusok](/rights-management/sdk/2.1/api/win/Data%20types)
- [Környezet tulajdonságai](/rights-management/sdk/2.1/api/win/Environment%20properties)
- [IpcCreateOAuth2Token](/rights-management/sdk/2.1/api/win/IpcCreateOAuth2Token)
- [IpcGetKey](/rights-management/sdk/2.1/api/win/IpcGetKey)
- [IpcInitialize](/rights-management/sdk/2.1/api/win/IpcInitialize)
- [IPC_CREDENTIAL](/rights-management/sdk/2.1/api/win/IPC\_CREDENTIAL)
- [IPC_NAME_VALUE_LIST](/rights-management/sdk/2.1/api/win/IPC\_NAME\_VALUE\_LIST)
- [IPC_OAUTH2_CALLBACK_INFO](/rights-management/sdk/2.1/api/win/IPC\_OAUTH2\_CALLBACK\_INFO)
- [IPC_PROMPT_CTX](/rights-management/sdk/2.1/api/win/IPC\_PROMPT\_CTX)
- [IPC_AAD_APPLICATION_ID](/rights-management/sdk/2.1/api/win/IPC\_AAD\_APPLICATION\_ID)


<!--HONumber=Jun16_HO1-->


