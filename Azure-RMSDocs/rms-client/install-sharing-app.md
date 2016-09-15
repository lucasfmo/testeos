---
title: "Pobieranie i instalowanie aplikacji do udostępniania usługi Rights Management | Azure RMS"
description: 
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 05/09/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 2bf09690-9dba-43b7-9e0a-0110915d4081
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: c611fa8a846612fed238e59e5077be67f6f9531a
ms.openlocfilehash: 5ec740b4de63c90c9713916dcf104316e727498b


---

# Pobieranie i instalowanie aplikacji do udostępniania usługi Microsoft Rights Management

*Dotyczy: Active Directory Rights Management, Azure Rights Management, Windows 10, Windows 7 z dodatkiem SP1, Windows 8, Windows 8.1*

Aby zainstalować aplikację RMS sharing, nie trzeba być administratorem lokalnym. Jeśli nim nie jesteś i korzystasz z pakietu Office 2010, obowiązują jednak pewne ograniczenia. Aby uzyskać więcej informacji, zobacz sekcję [Jeśli nie jesteś administratorem lokalnym i używasz pakietu Office 2010](#if-you-are-not-a-local-administrator-and-use-office-2010) w dalszej części tej strony.

## Aby pobrać i zainstalować aplikację do udostępniania usługi Rights Management

1.  Przejdź do strony usługi [Microsoft Rights Management](http://go.microsoft.com/fwlink/?LinkId=303970) w witrynie firmy Microsoft w sieci Web.

2.  W sekcji **Komputery** kliknij ikonę **aplikacji RMS dla systemu Windows** i zapisz plik **Setup.exe**, aby zainstalować aplikację do udostępniania usługi Microsoft Rights Management.

3.  Kliknij dwukrotnie pobrany plik Setup.exe. Jeśli zostanie wyświetlony monit o kontynuowanie, kliknij pozycję **Tak**.

4.  Na stronie **Instalacja usług Microsoft RMS** kliknij pozycję **Dalej** i poczekaj na zakończenie instalacji.

    > [!NOTE]
    > Aplikacja RMS sharing wymaga programu Microsoft .NET Framework w wersji co najmniej 4.0. Instalator sprawdza, czy ten program jest zainstalowany, a jeśli nie jest — zostanie wyświetlony komunikat z linkiem umożliwiającym jego zainstalowanie.

5.  Po zakończeniu instalacji kliknij pozycję **Uruchom ponownie**, aby ponownie uruchomić komputer i ukończyć instalację. Możesz również kliknąć pozycję **Zamknij**, aby uruchomić komputer ponownie później i ukończyć instalację.

Teraz możesz już chronić swoje pliki i otwierać pliki chronione udostępnione przez innych.

## Jeśli nie jesteś administratorem lokalnym i używasz pakietu Office 2010
Jeśli zalogujesz się na komputerze, nie mając lokalnych praw administracyjnych, a Instalator wykryje, że jest zainstalowany pakiet Office 2010, zobaczysz ostrzeżenie informujące, że w tej sytuacji niektóre działania nie są możliwe. Scenariusze są następujące:

-   Jeśli organizacja używa usług Azure RMS zamiast lokalnej wersji usług RMS:

    -   Funkcje zarządzania prawami do informacji (IRM) pakietu Office nie będą dostępne. Dotyczy to na przykład opcji **Nie przekazuj** w przypadku wiadomości e-mail oraz uprawnień związanych z **ograniczeniami dostępu**, ustawianymi w menu **Plik** w programach Word i Excel. Można użyć opcji Udostępnij chronioną zawartość, dostępnej na wstążce, oraz opcji wyświetlanych po kliknięciu prawym przyciskiem myszy w Eksploratorze plików.

-   Jeśli w danej organizacji jest używana lokalna wersja usług RMS, a nie usługi Azure RMS:

    -   Nie można odczytywać dokumentów chronionych wysłanych przez osoby z organizacji korzystającej z usługi Azure RMS.

Jeśli nie jesteś administratorem lokalnym i używasz usługi Office 365 lub pakietu Office 2013, nie zobaczysz tego komunikatu (te scenariusze są obsługiwane).

Możesz kontynuować instalację, uwzględniając te znane ograniczenia. Możesz też zatrzymać instalację i ponownie ją uruchomić, korzystając z opcji **Uruchom jako administrator** podczas uruchamiania pliku Setup.exe w kroku 3, albo poprosić administratora o zainstalowanie aplikacji za Ciebie. Administrator może [użyć skryptu instalacji](sharing-app-admin-guide.md#automatic-deployment-for-the-microsoft-rights-management-sharing-application), tak aby aplikacja została zainstalowana automatycznie.

## Przykłady i inne instrukcje
Aby uzyskać instrukcje i przykłady dotyczące korzystania z aplikacji do udostępniania usługi Rights Management, zapoznaj się z następującymi sekcjami podręcznika użytkownika aplikacji do udostępniania usługi Rights Management:

-   [Przykłady korzystania z aplikacji RMS sharing](sharing-app-user-guide.md#examples-for-using-the-rms-sharing-application)

-   [Co chcesz zrobić?](sharing-app-user-guide.md#what-do-you-want-to-do-)

## Zobacz też
[Podręcznik użytkownika aplikacji do udostępniania usługi Rights Management](sharing-app-user-guide.md)




<!--HONumber=Jun16_HO4-->


