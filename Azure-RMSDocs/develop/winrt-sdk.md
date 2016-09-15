---
title: Konfiguracja Sklepu Windows | Azure RMS
description: "Aplikacje ze Sklepu Windows mogą używać zestawu Microsoft Rights Management SDK 4.2 do włączenia zintegrowanej ochrony informacji w aplikacji."
keywords: 
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 2720aa0e-0d37-469f-be99-678bf95a9c51
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.sourcegitcommit: f7dd88d90357c99c69fe4fdde67c1544595e02f8
ms.openlocfilehash: 0b8e0fb6d872506ac3529bd137286f0e8fa562ee


---

# Konfiguracja Sklepu Windows

Aplikacje ze Sklepu Windows mogą używać zestawu Microsoft Rights Management SDK 4.2 do włączenia zintegrowanej ochrony informacji w aplikacji przy użyciu usługi Azure Active Directory Rights Management (AAD RM).

Ten temat zawiera informacje pomocne przy konfigurowaniu środowiska do tworzenia własnych, nowych aplikacji.

-   [Wymagania wstępne](#prerequisites)
-   [Opcjonalne](#optional)
-   [Konfigurowanie środowiska deweloperskiego](#configuring-your-development-environment)
-   [Zobacz też](#see-also)

## Wymagania wstępne


Musisz mieć następujące oprogramowanie w systemie deweloperskim:

-   System operacyjny [Windows 8.1](http://windows.microsoft.com/en-US/windows-8/meet)
-   [Zestaw Windows SDK dla systemu Windows 8.1](https://msdn.microsoft.com/windows/desktop/bg162891.aspx)
-   Program Microsoft [Visual Studio 2012](http://www.microsoft.com/visualstudio/eng/products/visual-studio-overview) lub nowszy albo program Visual Studio Express 2012 uwzględniony w zestawie Windows SDK dla systemu Windows 8.0/8.1
-   Zestaw MS RMS SDK 4.2 dla aplikacji ze Sklepu Windows. Aby uzyskać więcej informacji, zobacz [Rozpoczynanie pracy](get-started.md).
-   Biblioteka uwierzytelniania: firma Microsoft zaleca stosowanie biblioteki [Azure AD Authentication Library](https://msdn.microsoft.com/en-us/library/jj573266.aspx), ale można korzystać z innych bibliotek uwierzytelniania.

Temat [Nowości](release-notes.md) zawiera informacje dotyczące aktualizacji interfejsu API, urządzeń i środowiska oraz informacje o wersji i często zadawane pytania.

## Opcjonalne

Biblioteka interfejsów użytkownika firmy Microsoft udostępnia interfejs wielokrotnego użytku do operacji konsumenckich i zabezpieczających dla deweloperów, którzy nie chcą tworzyć własnego niestandardowego interfejsu użytkownika — [Biblioteka interfejsów użytkownika dla aplikacji ze Sklepu Windows](https://github.com/AzureAD/rms-sdk-ui-for-windowsstore). Firma Microsoft udostępnia również przykładową aplikację ze Sklepu Windows — [Przykładowa aplikacja dla Sklepu Windows korzystająca z usługi RMS](https://github.com/AzureADSamples/rms-samples-for-windowsstore).

## Konfigurowanie środowiska deweloperskiego


-   Otwórz program Visual Studio.
-   Kliknij menu **Plik**, kliknij pozycję **Nowy**, a następnie kliknij pozycję **Projekt**.
-   W oknie dialogowym **Nowy projekt** kliknij pozycję **Visual C\#**, wybierz pozycję **Pusta aplikacja (Windows)**, a następnie kliknij przycisk **OK**.

    ![Tworzenie nowego projektu](../media/winrtsetup-newproj.png)

-   W **Eksploratorze rozwiązań** kliknij projekt prawym przyciskiem myszy, a następnie wybierz pozycję **Dodaj odwołanie**, aby otworzyć okno dialogowe **Dodawanie odwołania**.

    ![Dodawanie odwołania](../media/winrtsetup-addref.png)

-   W oknie dialogowym **Dodawanie odwołania** kliknij przycisk **Przeglądaj** i wybierz plik *Microsoft.RightsManagement.dll* znajdujący się w folderze, do którego wyodrębniono zestaw SDK.
-   **Aplikacje zarządzane** — To odwołanie należy dodać w przypadku tworzenia aplikacji zarządzanej. Wybierz pozycje **Windows 8.1**-&gt;**Rozszerzenia** i zaznacz pole wyboru **Windows Visual C++ Runtime Package for Windows**.

    ![Dodawanie rozszerzeń](../media/winrtsetup-refmngr.png)

-   **Dodawanie możliwości** — Aby korzystać z zestawu SDK, aplikacja musi mieć możliwość „Internet (klient i serwer)”. Aby dodać tę możliwość do aplikacji, otwórz plik *Package.appxmanifest* w projekcie i przejdź do karty **Możliwości**.

Teraz możesz przystąpić do tworzenia własnych nowych aplikacji dla Sklepu Windows.

### Zobacz też

[Wprowadzenie](get-started.md)

[Co nowego](release-notes.md)

[Terminy i pojęcia dla deweloperów](core-concepts.md)

[Windows 8](http://windows.microsoft.com/en-US/windows-8/meet)

[Visual Studio 2012](http://www.microsoft.com/visualstudio/eng/products/visual-studio-overview)

[Dokumentacja interfejsu API systemu Windows](/rights-management/sdk/4.2/api/winrt/Microsoft.RightsManagement)



<!--HONumber=Jul16_HO2-->


