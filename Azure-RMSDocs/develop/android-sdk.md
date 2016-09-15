---
title: Konfiguracja systemu Android | Azure RMS
description: "Aplikacje systemu Android mogą korzystać z zestawu SDK 4.2 usług Microsoft Rights Management do włączenia zintegrowanej ochrony informacji w aplikacjach."
keywords: 
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 986f6932-159b-4791-bd1a-7640a83ee792
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 79397c82d9478cbd55630a376fe2d12f3873ebc4
ms.openlocfilehash: 4ff6328c0be4cd217390ee802e53e93c90f41c99


---

# Konfiguracja systemu Android

Aplikacje systemu Android mogą korzystać z zestawu SDK 4.2 usługi Microsoft Rights Management do włączenia zintegrowanej ochrony informacji w aplikacjach przy użyciu usługi Azure Active Directory Rights Management (AAD RM).

Ten temat zawiera informacje pomocne przy konfigurowaniu środowiska do tworzenia nowych własnych aplikacji.

-   [Wymagania wstępne](#prerequisites)
-   [Opcjonalne](#optional)
-   [Konfigurowanie środowiska deweloperskiego](#configuring-your-development-environment_)
-   [Zobacz też](#see-also)

## Wymagania wstępne

Zalecamy stosowanie następującego oprogramowania w systemie deweloperskim:

-   System operacyjny Windows lub OS X, umożliwiający uruchamianie środowiska deweloperskiego [Eclipse](http://www.oracle.com/technetwork/java/javase/downloads/jre7-downloads-1880261.html).
-   W tym przewodniku założono, że korzystasz z zestawu Eclipse SDK w wersji Eclipse Juno 4.2 lub nowszej i instalacji domyślnej.
-   Środowisko Java 1.6 lub nowsze.
-   [Dodatek Android Developer Tools (ADT) Plugin](http://developer.android.com/sdk/installing/index.html). UWAGA — Ukończenie instalacji może wymagać ponownego uruchomienia aplikacji Eclipse.

     

-   Pakiet SDK 4.2 usługi MS RMS dla systemu Android. Aby uzyskać więcej informacji, zobacz [Rozpoczynanie pracy](get-started.md).

    Ten zestaw SDK umożliwia tworzenie aplikacji dla systemu Android 4.0.3 (API level 15) i nowszych.

-   Biblioteka uwierzytelniania: firma Microsoft zaleca stosowanie biblioteki [Azure AD Authentication Library (ADAL)](https://msdn.microsoft.com/library/jj573266.aspx). Można jednak stosować także inne biblioteki uwierzytelniania obsługujące protokół OAuth 2.0.

    Aby uzyskać więcej informacji, zobacz [Biblioteka ADAL dla systemu Android](https://github.com/MSOpenTech/azure-activedirectory-library-for-android)

    **Uwaga**  Jeśli Twoja aplikacja nie będzie korzystać z biblioteki ADAL jako biblioteki uwierzytelniania OAuth 2.0, należy zapoznać się z przewodnikiem [Some SecureRandom Thoughts (Kilka przemyśleń na temat klasy SecureRandom)](http://android-developers.blogspot.com/2013/08/some-securerandom-thoughts.html) dla systemu Android.

     

Temat [Nowości](release-notes.md) zawiera informacje na temat aktualizacji interfejsu API, informacje o wersji i często zadawane pytania.

## Opcjonalne

Nasza biblioteka interfejsów użytkownika udostępnia interfejs wielokrotnego użytku do operacji konsumenckich i zabezpieczających dla deweloperów, którzy nie chcą tworzyć własnego interfejsu użytkownika — [Biblioteka interfejsów użytkownika i przykładowa aplikacja dla systemu Android](https://github.com/AzureAD/rms-sdk-ui-for-android).

## Konfigurowanie środowiska deweloperskiego

**Uwaga**  Wersja zapoznawcza zestawu SDK 4.2 usługi MS RMS: w tej wersji zapoznawczej nie uaktualniono zrzutów ekranu (nie zmieniono nazw ścieżek z com/microsoft/protection na com/microsoft/rightsmanagment). Tekst został jednak zaktualizowany.

 
-   Otwórz środowisko deweloperskie Eclipse.
-   Aby utworzyć nowy projekt aplikacji systemu Android, w menu **Plik** kliknij pozycję **New** (Nowy), kliknij pozycję **Project** (Projekt), a następnie wybierz pozycję **Android Application Project** (Projekt aplikacji dla systemu Android).

    ![Utwórz nową aplikację dla systemu Android](../media/Android-setup-01c.png)

-   Wpisz nazwę aplikacji. Nazwa projektu i pakietu jest wypełniana zgodnie z nazwą aplikacji.
-   Kliknij przycisk **Next** (Dalej) i wybierz miejsce utworzenia obszaru roboczego.

    ![Wpisz nazwę aplikacji](../media/Android-setup-02a.jpg)

-   Kliknij przycisk **Next** (Dalej) i wybierz ikonę aplikacji.

    ![Wybierz ikonę dla aplikacji](../media/Android-setup-03.png)

-   Kliknij przycisk **Next** (Dalej) i wybierz pozycję **Blank Activity** (Puste działanie), aby utworzyć działanie.

    ![Utwórz działanie](../media/Android-setup-04.png)

-   Kliknij przycisk **Next** (Dalej) i podaj nazwę działania. Możesz pozostawić nazwę domyślną *MainActivity* i nazwę układu *activity\_main*.

    ![Podaj nazwę działania](../media/Android-setup-05a.jpg)

-   Kliknij przycisk **Finish** (Zakończ).

    ![Zakończ tworzenie](../media/Android-setup-06.jpg)

-   Projekt zostanie utworzony wraz z klasą działania głównego *MainActivity.java*.

**Odwołania do zestawu SDK**

-   Przejdź do folderu, w którym wyodrębniono plik *adrms\_android\_sdk.zip*. W folderze „SDK > com > microsoft > rightsmanagement” upewnij się, że pliki *.classpath*, *.project* i *project.properties* nie są oznaczone jako tylko do odczytu.
-   Aby odwoływać się do zestawu SDK, należy zaimportować go do obszaru roboczego.

    W środowisku Eclipse kliknij pozycję **File** (Plik). W menu **File** (Plik) kliknij pozycję **Import** (Importuj). W oknie dialogowym **Import** wybierz opcję **Android / Existing Android Code into Workspace** (Android / istniejący kod Android do obszaru roboczego).

    ![Zaimportuj kod do obszaru roboczego](../media/Android-setup-07.png)

-   Kliknij przycisk **Next** (Dalej). Przejdź do folderu, w którym wyodrębniono plik *adrms\_android\_sdk.zip*. Zestaw SDK powinien być wyświetlany na liście jako **com.microsoft.rightsmanagement**.

    ![Przejdź do folderu](../media/Android-setup-08c.jpg)

-   Po kliknięciu przycisku **Finish** (Zakończ) projekt zestawu SDK jest wyświetlany jako element równorzędny utworzonej wcześniej aplikacji.

    ![Projekt zestawu SDK jest wyświetlany jako element równorzędny aplikacji](../media/Android-setup-09.jpg)

-   Kliknij prawym przyciskiem myszy ikonę **Project** (Projekt) i wyświetl właściwości projektu.
-   Przejdź na kartę **Android**.
-   Kliknij przycisk **Add** (Dodaj), a następnie wybierz bibliotekę *com.microsoft.rightsmanagement* z obszaru roboczego.

    ![Dodaj bibliotekę](../media/Android-setup-10b.jpg)

-   Kliknij przycisk **OK**.

    Zestaw SDK 4.2 usługi MS RMS łączy się z usługą AAD RM, w związku z czym aplikacja musi mieć uprawnienia **INTERNET** i **ACCESS\_NETWORK\_STATE**. W tym celu otwórz plik *AndroidManifest.xml* w folderze głównym projektu.

    Aby dodać uprawnienia, kliknij przycisk **Add** (Dodaj) i wybierz pozycję **Uses Permissions** (Używa uprawnień).

    ![Dodaj uprawnienia](../media/Android-setup-11d.jpg)

-   Krok manifestu można sprawdzić, wyświetlając manifest w widoku edytora tekstu. Upewnij się, że są wyświetlane następujące wiersze:


    <uses-sdk      android:minSdkVersion="15"      android:targetSdkVersion="19"/> <uses-permission android:name="android.permission.INTERNET"/> <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE"/> <uses-permission/>


**Uwaga**  Zestaw SDK używa uprawnienia *android.support.v4*

-   Teraz można przystąpić do tworzenia własnych nowych aplikacji dla systemu Android.

### Zobacz też

[Wprowadzenie](get-started.md)

[Co nowego](release-notes.md)

[Terminy i pojęcia dla deweloperów](core-concepts.md)

[Dokumentacja interfejsu API systemu Android](android-namespaces.md)

 

 



<!--HONumber=Jul16_HO4-->


