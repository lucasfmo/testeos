---
title: "Porady&#58; włączanie rejestrowania błędów i wydajności | Azure RMS"
description: "Zestaw Microsoft Rights Management SDK 4.2 zarządza przekazywaniem dzienników diagnostyki i wydajności za pośrednictwem pojedynczej właściwości urządzenia."
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

# Porady: włączanie rejestrowania błędów i wydajności
Zestaw Microsoft Rights Management SDK 4.2 zarządza przekazywaniem dzienników diagnostyki i wydajności za pośrednictwem pojedynczej właściwości urządzenia.

## Przegląd ##
Włączenie automatycznego przekazywania dzienników diagnostyki i wydajności do firmy Microsoft pozwala zwiększyć komfort pracy użytkowników i usprawnić rozwiązywanie problemów. Aby chronić prywatność użytkowników, przed włączeniem automatycznego rejestrowania deweloper aplikacji musi poprosić użytkownika o zgodę.

Do zarządzania rejestrowaniem służą dwie właściwości.

-   Można włączyć rejestrowanie za pośrednictwem właściwości **IpcCustomerExperienceDataCollectionEnabled**. To ustawienie jest zachowywane po zresetowaniu urządzenia.
-   Poziomem rejestrowania można sterować za pośrednictwem właściwości **IpcLogLevel** przy użyciu poniższych ustawień.

    * 1 — pełny
    * 2 — informacyjny
    * 3 — ostrzeżenie
    * 4 — błąd
    * 5 — krytyczny

W każdym z poniższych przykładowych fragmentów kodu aplikacja wywołująca może ustawić właściwość lub wykonać zapytanie dotyczące tej właściwości.

### Android ###
Włączanie automatycznego rejestrowania

    SharedPreferences preferences = PreferenceManager.getDefaultSharedPreferences(context);
    SharedPreferences.Editor editor = preferences.edit();
    editor.putBoolean(&quot;IpcCustomerExperienceDataCollectionEnabled&quot;, true);
    editor.commit();

Pobieranie bieżącego ustawienia flagi kontroli rejestrowania

    SharedPreferences preferences = PreferenceManager.getDefaultSharedPreferences(context);
    Boolean isLogUploadEnabled = preferences.getBoolean(&quot;IpcCustomerExperienceDataCollectionEnabled&quot;, false);

## iOS ##
Włączanie automatycznego rejestrowania

    NSUserDefaults \*prefs = [NSUserDefaults standardUserDefaults];
        [prefs setBool:FALSE forKey:@&quot;IpcCustomerExperienceDataCollectionEnabled”];
        [[NSUserDefaults standardUserDefaults] synchronize];

Pobieranie bieżącego ustawienia flagi kontroli rejestrowania

    [[NSUserDefaults standardUserDefaults] boolForKey:@&quot;IpcCustomerExperienceDataCollectionEnabled&quot;];

Ustawianie kontroli poziomu dziennika

    NSUserDefaults \*prefs = [NSUserDefaults standardUserDefaults];
      [prefs setInteger:1 forKey:@&quot;IpcLogLevel”];
      [[NSUserDefaults standardUserDefaults] synchronize];

Pobieranie ustawienia kontroli poziomu dziennika

    [[NSUserDefaults standardUserDefaults] boolForKey:@&quot;IpcLogLevel&quot;];
 

## Windows ##
Włączanie automatycznego rejestrowania

    CustomerExperienceConfiguration::Option = CustomerExperienceOptions::LoggingEnabledNow;

Więcej informacji o ustawieniach opcjonalnych można znaleźć w sekcji dotyczącej elementu [CustomerExperienceOptions](/rights-management/sdk/4.2/api/winrt/Microsoft.RightsManagement#msipcthin2_customerexperienceoptions).

Pobieranie bieżącego ustawienia flagi kontroli rejestrowania

    CustomerExperienceOptions loggingOption = CustomerExperienceConfiguration::Option;


**Uwaga:** kod przedstawiony powyżej jest napisany w języku C++. Dla języka C\# uaktualnij składnię, używając „.” zamiast „::”.

**Linux / C++:** ten zestaw SDK udostępnia podstawowe funkcje rejestrowania, ale nie są one tak zaawansowane jak w przypadku innych platform. Aby uzyskać więcej informacji, zobacz sekcję dotyczącą **rozwiązywania problemów** związanych z plikiem „README.md” na stronie [RMS SDK for portable C++](https://github.com/AzureAD/rms-sdk-for-cpp#troubleshooting) (Zestaw RMS SDK dla przenośnego kodu C++).

 

 



<!--HONumber=Jul16_HO3-->


