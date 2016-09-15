---
title: Konfiguracja w systemach iOS i OS X | Azure RMS
description: "Aplikacje systemów iOS i OS X mogą używać zestawu RMS SDK 4.2 w celu włączenia zintegrowanej ochrony informacji w aplikacjach za pomocą usługi AAD RM."
keywords: 
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: b31e5b72-e65e-450a-b1b8-d46e81e9fb34
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: a0659fda129f6de5e7b52c89f4d1f9d73d11df45
ms.openlocfilehash: bdc173fb9cb9b749d75b08df3cc9554acd6f6386


---

# Konfiguracja w systemach iOS i OS X

Aplikacje systemów iOS i OS X mogą używać zestawu Microsoft Rights Management SDK 4.2 w celu włączenia zintegrowanej ochrony informacji w aplikacjach za pomocą usługi Azure Rights Management (Azure RMS).

Ten temat zawiera informacje pomocne przy konfigurowaniu środowiska do tworzenia własnych, nowych aplikacji.

**Uwaga: ** ten zestaw SDK nie obsługuje urządzenia iPod Touch.


-   [Wymagania wstępne](#prerequisites)
-   [Opcjonalne](#optional)
-   [Konfigurowanie środowiska deweloperskiego](#configuring-your-development-environment)
-   [Zobacz też](#see-also)

## Wymagania wstępne

Zalecamy stosowanie następującego oprogramowania na platformie programistycznej:

-   System OS X jest wymagany w przypadku wszystkich aplikacji projektowanych dla systemu iOS.
-   Środowisko Xcode 6.0 lub nowsze

    Środowisko Xcode jest dostępne w sklepie [Mac App Store](https://developer.apple.com/technologies/mac/).

-   Pakiet MS RMS SDK 4.2 dla systemów iOS i OS X. Aby uzyskać więcej informacji, zobacz [Rozpoczynanie pracy](get-started.md).

    Ten zestaw SDK umożliwia tworzenie aplikacji dla systemu iOS 7.0 oraz OS X 10.8 i nowszych.

-   Biblioteka uwierzytelniania: firma Microsoft zaleca stosowanie biblioteki [Azure AD Authentication Library (ADAL)](https://msdn.microsoft.com/library/jj573266.aspx). Można jednak stosować także inne biblioteki uwierzytelniania obsługujące protokół OAuth 2.0.

    Aby uzyskać więcej informacji, zobacz [ADAL for iOS](https://github.com/MSOpenTech/azure-activedirectory-library-for-ios) (Biblioteka ADAL dla systemu iOS) lub [ADAL for OS X](https://github.com/MSOpenTech/azure-activedirectory-library-for-ios/tree/OSXUniversal) (Biblioteka ADAL dla systemu OS X).

Temat [Nowości](release-notes.md) zawiera informacje na temat aktualizacji interfejsu API, informacje o wersji i często zadawane pytania.

## Opcjonalne

Nasza biblioteka interfejsów użytkownika udostępnia interfejs wielokrotnego użytku do operacji konsumenckich i zabezpieczających dla deweloperów, którzy nie chcą tworzyć własnego interfejsu użytkownika — [Biblioteka interfejsów użytkownika i przykładowa aplikacja dla systemu iOS](https://github.com/AzureAD/rms-sdk-ui-for-ios).

## Konfigurowanie środowiska deweloperskiego

-   Aby utworzyć nowy projekt, w menu **File** (Plik) kliknij pozycję **New** (Nowy), a następnie kliknij pozycję **Project** (Projekt).
-   Wybierz pozycję **Single View Application** (Aplikacja pojedynczego widoku).

    ![Tworzenie nowego projektu](../media/iOS-Project.png)

-   Wprowadź nazwę i identyfikator nowego projektu.

    ![Wprowadzanie nazwy projektu](../media/iOS-project-options.png)

-   Kliknij przycisk **Next** (Dalej) i wybierz lokalizację projektu.
-   Aby dodać strukturę **MSRightsManagement** dla systemu iOS, przeciągnij folder .framework z folderu instalacyjnego zestawu SDK do sekcji **Frameworks** (Struktury) w obszarze **Project Navigator** (Nawigator projektu).

    ![Ustawianie lokalizacji](../media/ios-add-dependencies-01a.png)

-   Wybierz przycisk **Create groups for any added folders** (Utwórz grupy dla wszystkich dodanych folderów) i wyczyść pole wyboru **Copy items into destination group's folder (if needed)** (Skopiuj elementy do folderu grupy docelowej [w razie potrzeby]).

    Pozwala to na utworzenie odwołania do folderu instalacyjnego zestawu SDK zamiast tworzenia kopii.

    ![Ustawianie odwołania do folderu instalacyjnego zestawu SDK](../media/iOS-create-groups.png)

-   Aby dodać zestaw MS RMS SDK 4.2 dla pakietu zasobów, przeciągnij plik MSRightsManagementResources.bundle z folderu MSRightsManagement.framework/Resources do sekcji **Frameworks** (Struktury) w obszarze nawigatora projektu.

    ![Dodawanie pakietu zasobów](../media/iOS-add-resource-bundle-02a.png)

-   Podobnie jak podczas kopiowania struktury, wybierz przycisk **Create groups for any added folders** (Utwórz grupy dla wszystkich dodanych folderów) i wyczyść pole wyboru **Copy items into destination group's folder (if needed)** (Skopiuj elementy do folderu grupy docelowej [w razie potrzeby]).
-   Ten zestaw SDK korzysta z innych platform, na przykład: **CoreData**, **MessageUI**, **SystemConfiguration**, **Libresolv** i **Security**. Aby je dodać, przejdź do sekcji **Linked Frameworks and Libraries** (Połączone struktury i biblioteki) w okienku **Summary** (Podsumowanie) w obszarze docelowym i rozwiń ją.

    Platformy **UIKit** i **Foundation** są wymagane i zazwyczaj domyślnie dostępne.

    ![Dodawanie zasobów](../media/iOS-add-libraries.png)

-   Dodaj flagę **-ObjC** w sekcji **Other Linker Flags** (Inne flagi konsolidatora) w **ustawieniach kompilacji** w obszarze docelowym.

    ![Dodawanie ustawień kompilacji](../media/iOS-linker-flags.png)

-   Po wykonaniu tych czynności obszar **nawigatora projektu** powinien wyglądać jak na poniższej ilustracji.

    ![Przegląd projektu](../media/iOS-verify-setup-01a.png)

-   Teraz można przystąpić do tworzenia własnych aplikacji dla systemu iOS/OS X.

### Zobacz też

* [Wprowadzenie](get-started.md)

* [Co nowego](release-notes.md)

* [Terminy i pojęcia dla deweloperów](core-concepts.md)

* [Dokumentacja interfejsu API dla systemu iOS/OS X](/rights-management/sdk/4.2/api/ios/ios)

 

 






<!--HONumber=Aug16_HO3-->


