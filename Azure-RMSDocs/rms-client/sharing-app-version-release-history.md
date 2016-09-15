---
title: "Aplikacja do udostępniania usługi Rights Management&colon; historia wersji | Azure RMS"
description: 
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 07/13/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 6751bd90-959f-4eba-91ed-6588ac983762
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: e1b7dedd8556f3ccdb1642681cc4e1e5b1d09ccf
ms.openlocfilehash: ee2860da964b52bc41c0aea219110453f024b954


---

# Aplikacja do udostępniania usługi Rights Management: historia wersji

*Dotyczy: Active Directory Rights Management, Azure Rights Management, Windows 10, Windows 7 z dodatkiem SP1, Windows 8, Windows 8.1*

Zespół pracujący nad usługą Rights Management regularnie aktualizuje aplikację do udostępniania usługi Rights Management w celu wprowadzenia poprawek i dodania nowych funkcji. Poniższe informacje pozwalają dowiedzieć się, co wprowadzono lub zmieniono w poszczególnych wydaniach. Najnowsza wersja jest wyświetlana na początku listy.

W zestawieniu nie uwzględniono wersji sprzed 1 stycznia 2015 r.

> [!NOTE]
> Opinie i pytania dotyczące aplikacji do udostępniania usługi RMS należy przesyłać pocztą e-mail na adres [AskIPTeam](mailto:AskIPTeam@microsoft.com?subject=RMS%20sharing%20app:%20Feedback%20or%20question).

## Wersja 1.0.2217.0

**Wydana**: 2016-07-13

**Poprawki**:

- Użytkownicy w organizacjach korzystających z usług federacyjnych i uwierzytelniania wieloskładnikowego nie otrzymują już błędu 0x800704DC podczas chronienia zawartości.



## Wersja 1.0.2191.0
**Wydana**: 2016-06-16

**Poprawki**:

- Witryna śledzenia dokumentów zawiera obecnie prawidłową liczbę widoków dla każdego śledzonego dokumentu.

- Szablony dla wszystkich ustawień regionalnych są teraz wyświetlane jako dostępne dla użytkowników.

- Po użyciu chronionej zawartości dla pliku programu PowerPoint zmiany w lokalnej wersji pliku są teraz zapisywane poprawnie.

- Niewielka liczba drobnych usterek i usprawnień dla komunikatów o błędach.


## Wersja 1.0.2004.0
**Wydana**: 2015-12-11

**Poprawki**:

-   Tylko właściciel pliku i osoby z poziomem uprawnień **Współwłaściciel** mogą wyłączyć ochronę plików. Dotychczas ochronę plików mógł wyłączyć właściciel pliku i osoby z poziomem uprawnień **Współautor** lub **Współwłaściciel**.

-   Natywna ochrona plików **tif** (oprócz plików tiff) umożliwia wygenerowanie pliku **ptif** tylko do odczytu chronionego przez usługi RMS.

-   Ulepszenia komunikatów o błędach (dokładność i zrozumiałość).

-   Większa wydajność szyfrowania i odszyfrowywania zawartości.

**Nowe funkcje**:

-   Obsługa instalacji przez osoby niebędące administratorami, umożliwiająca standardowym użytkownikom instalowanie aplikacji RMS sharing.

    Istnieją pewne ograniczenia dotyczące standardowych użytkowników korzystających z pakietu Office 2010. Aby uzyskać więcej informacji, zobacz instrukcje dla użytkowników w sekcji [Jeśli nie jesteś administratorem lokalnym i używasz pakietu Office 2010](install-sharing-app.md#if-you-are-not-a-local-administrator-and-use-office-2010) w temacie [Pobieranie i instalowanie aplikacji do udostępniania usługi Microsoft Rights Management](install-sharing-app.md).

## Wersja 1.0.1908.0
**Wydana**: 2015-09-16

**Poprawki**:

-   Obsługa uwierzytelniania wieloskładnikowego (MFA, multi-factor authentication) dla usług Azure RMS, zapewniająca również niezależność aplikacji, które używają nowoczesnego uwierzytelniania, od Asystenta logowania firmy Microsoft.

    Aby uzyskać więcej informacji, zobacz sekcję [Usługi Multi-Factor Authentication (MFA) i Azure RMS](../get-started/requirements-azure-ad.md#multi-factor-authentication-mfa-and-azure-rms) w temacie [Wymagania dotyczące usługi Azure Rights Management](../get-started/requirements-azure-rms.md).

## Wersja 1.0.1784.0
**Wydana**: 2015-07-30

**Poprawki**:

-   Domyślny interwał odświeżania szablonów zasad praw został zmniejszony z 7 dni do 1 dnia.

-   Niewielka liczba regresji i drobnych usterek.

## Wersja 1.0.1770.0
**Wydana**: 2015-04-25

**Poprawki**:

-   Obecnie tylko właściciel i współwłaściciele mogą wyłączyć ochronę. Współautorzy nie mogą wyłączyć ochrony.

-   Obecnie można chronić pliki w udziale sieciowym.

**Nowe funkcje**:

-   Obsługa śledzenia i odwoływania dokumentów. Aby uzyskać więcej informacji, zobacz [Śledzenie i odwoływanie dokumentów podczas używania aplikacji do udostępniania usługi RMS](sharing-app-track-revoke.md).

-   Obsługa szablonów podczas wybierania pozycji **Udostępnij chronione**:

    -   Obecnie można wybierać szablony.

    -   Zamiast suwaka wyświetlane jest pole listy, które zawiera szablony i uprawnienia niestandardowe.

    -   Opcje **Zezwalaj na użycie na wszystkich urządzeniach** i **Wymuś ograniczenia użycia** nie są już wyświetlane. Zamiast tego domyślnie wybierana jest opcja **Ochrona ogólna** zależnie do typu pliku.

    Aby uzyskać więcej informacji, zobacz [Opcje okien dialogowych aplikacji do udostępniania usługi Rights Management](sharing-app-dialog-box.md).

## Wersja 1.0.1667.0
**Wydana**: 2015-01-19

**Poprawki**:

-   Obsługa czcionek języka chińskiego w przeglądarce plików PPDF aplikacji RMS sharing.

-   Ulepszona obsługa błędów i komunikatów.

-   Rozwiązano problem dotyczący automatycznych powiadomień o aktualizacji wysyłanych po udostępnieniu nowej wersji aplikacji do pobrania.

**Nowe funkcje**:

-   **Obsługa wielu domen poczty e-mail w danej organizacji**: Jeśli korzystasz z usług AD RMS i użytkownicy w Twojej organizacji mają kilka domen poczty e-mail, ta aktualizacja pozwala użytkownikom korzystać z zawartości chronionej przez użytkowników w innych domenach w Twojej organizacji. Aby uzyskać więcej informacji, zobacz sekcję [Tylko usługi AD RMS: obsługa wielu domen poczty e-mail w danej organizacji](sharing-app-admin-guide.md#ad-rms-only-support-for-multiple-email-domains-within-your-organization) w [Przewodniku administratora aplikacji do udostępniania usługi Rights Management](sharing-app-admin-guide.md).




<!--HONumber=Jul16_HO3-->


