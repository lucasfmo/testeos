---
title: "Útmutató&#58; Hiba- és teljesítménynaplózás engedélyezése | Azure RMS"
description: "A Microsoft Rights Management SDK 4.2 egyetlen eszköztulajdonságon keresztül kezeli a diagnosztikát és a teljesítménynaplókat."
keywords: 
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: F5AD3826-2292-4A25-AF5C-D17D083F5742
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 79e58b8092ea7cb057229d4c464d79f3694296e6
ms.openlocfilehash: 5faea360de8aa9ecb82abf25b5c1392d52d0afad


---

# Útmutató: Hiba- és teljesítménynaplózás engedélyezése
A Microsoft Rights Management SDK 4.2 egyetlen eszköztulajdonságon keresztül kezeli a diagnosztikát és a teljesítménynaplókat.

## Áttekintés ##
A felhasználói élmény és a hibaelhárítás javítása érdekében engedélyezheti az automatikus diagnosztikát és a teljesítménynaplók feltöltését a Microsoft webhelyre. A felhasználók adatvédelme érdekében az alkalmazás fejlesztőjeként a felhasználó beleegyezését kell kérnie az automatikus naplózás engedélyezése előtt.

Két tulajdonságon keresztül vezérli a naplózást.

-   Engedélyezze a naplózást az **IpcCustomerExperienceDataCollectionEnabled** tulajdonságon keresztül. A beállítás az eszköz-visszaállítások során nem vész el.
-   A következő beállításokkal vezérelheti a naplózási szintet az **IpcLogLevel** tulajdonságon keresztül.

    * 1 - Részletes
    * 2 - Tájékoztató
    * 3 - Figyelmeztetés
    * 4 - Hiba
    * 5 - Kritikus

Az összes következő példakódrészletben a hívó alkalmazás állíthatja be vagy kérheti le a tulajdonságot.

### Android ###
Automatikus naplózás engedélyezése

    SharedPreferences preferences = PreferenceManager.getDefaultSharedPreferences(context);
    SharedPreferences.Editor editor = preferences.edit();
    editor.putBoolean(&quot;IpcCustomerExperienceDataCollectionEnabled&quot;, true);
    editor.commit();

Aktuális naplózásvezérlő jelző beállításának lekérése

    SharedPreferences preferences = PreferenceManager.getDefaultSharedPreferences(context);
    Boolean isLogUploadEnabled = preferences.getBoolean(&quot;IpcCustomerExperienceDataCollectionEnabled&quot;, false);

## iOS ##
Automatikus naplózás engedélyezése

    NSUserDefaults \*prefs = [NSUserDefaults standardUserDefaults];
        [prefs setBool:FALSE forKey:@&quot;IpcCustomerExperienceDataCollectionEnabled”];
        [[NSUserDefaults standardUserDefaults] synchronize];

Aktuális naplózásvezérlő jelző beállításának lekérése

    [[NSUserDefaults standardUserDefaults] boolForKey:@&quot;IpcCustomerExperienceDataCollectionEnabled&quot;];

Naplózási szint vezérlésének beállítása

    NSUserDefaults \*prefs = [NSUserDefaults standardUserDefaults];
      [prefs setInteger:1 forKey:@&quot;IpcLogLevel”];
      [[NSUserDefaults standardUserDefaults] synchronize];

A naplózási szint vezérlési beállításának lekérése

    [[NSUserDefaults standardUserDefaults] boolForKey:@&quot;IpcLogLevel&quot;];
 

## Windows ##
Automatikus naplózás engedélyezése

    CustomerExperienceConfiguration::Option = CustomerExperienceOptions::LoggingEnabledNow;

Az opcionális beállításokról további információért lásd: [CustomerExperienceOptions](/rights-management/sdk/4.2/api/winrt/Microsoft.RightsManagement#msipcthin2_customerexperienceoptions).

Aktuális naplózásvezérlő jelző beállításának lekérése

    CustomerExperienceOptions loggingOption = CustomerExperienceConfiguration::Option;


**Megjegyzés** – A fenti Windows kódrészletek C++ nyelvben vannak. A C\# nyelvhez frissítse a szintaxist a „.” karakterrel a ‘::’ helyett.

**Linux / C++** – Ez az SDK alapvető naplózással rendelkezik, amely a többi platformhoz képest kevésbé átfogó. További információt az [RMS SDK for portable C++](https://github.com/AzureAD/rms-sdk-for-cpp#troubleshooting) kód a „README.md” fájljának **Troubleshooting** (Hibaelhárítás) szakaszban talál.

 

 



<!--HONumber=Jun16_HO4-->


