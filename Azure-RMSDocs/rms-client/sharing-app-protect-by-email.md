---
title: "Ochrona plików udostępnianych pocztą e-mail za pomocą aplikacji do udostępniania usługi Rights Management | Azure RMS"
description: 
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 07/13/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 4c1cd1d3-78dd-4f90-8b37-dcc9205a6736
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 67129d6cdac124947fc07aa4d42523686227752e
ms.openlocfilehash: 13f44e93ee9c1c0583bd75121aec638fee09b748


---

# Ochrona plików udostępnianych pocztą e-mail za pomocą aplikacji do udostępniania usługi Rights Management

*Dotyczy: Active Directory Rights Management, Azure Rights Management, Windows 10, Windows 7 z dodatkiem SP1, Windows 8, Windows 8.1*

Włączenie ochrony pliku udostępnianego w wiadomości e-mail powoduje utworzenie nowej wersji oryginalnego pliku. Oryginalny plik pozostaje niechroniony, a jego nowa wersja jest chroniona i zostaje automatycznie dołączona do wysyłanej wiadomości e-mail.

W niektórych przypadkach (dotyczących plików utworzonych w programach Microsoft Word, Excel i PowerPoint) aplikacja RMS sharing tworzy dwie wersje pliku, które dołącza do wiadomości e-mail. Druga wersja pliku ma rozszerzenie nazwy pliku **ppdf** i stanowi kopię w tle pliku w formacie PDF. Dzięki tej udostępnieniu tej wersji pliku adresat może otworzyć plik, nawet jeśli nie ma zainstalowanej aplikacji, w której go utworzono. Taka sytuacja często dotyczy osób, które chcą otwierać załączniki wiadomości e-mail na urządzeniach przenośnych. Do otwierania takich plików wystarczy im aplikacja RMS sharing. Załączony pliki można otworzyć, ale nie można go zmienić, o ile druga wersja pliku nie zostanie otwarta w aplikacji obsługującej usługi RMS.

Jeśli organizacja używa usług Azure RMS, możesz monitorować pliki chronione za pomocą udostępniania:

-   Zaznacz opcję, dzięki której będziesz otrzymywać wiadomość e-mail, jeśli ktoś spróbuje otworzyć chronione załączniki. Za każdym razem, kiedy ktoś spróbuje otworzyć plik, dowiesz się, kto to był, kiedy to zrobił i czy mu się to udało (czy został pomyślnie uwierzytelniony).

-   Skorzystaj z witryny śledzenia dokumentów. Możesz nawet przerwać udostępnianie pliku, odwołując dostęp do niego w witrynie śledzenia dokumentów. Aby uzyskać więcej informacji, zobacz [Śledzenie i odwoływanie dokumentów podczas używania aplikacji do udostępniania usługi RMS](sharing-app-track-revoke.md).

## Używanie programu Outlook: aby chronić plik udostępniany pocztą e-mail

1.  Utwórz wiadomość e-mail i dołącz plik. Następnie na karcie **Wiadomość** w grupie **RMS** kliknij opcję **Udostępnij chronione**, a następnie ponownie kliknij opcję **Udostępnij chronione**:

    ![Dodatek dla programu Outlook dotyczący aplikacji RMS sharing](../media/ADRMS_MSRMSApp_SP_OutlookToolbar.png)

    Jeśli ten przycisk nie jest wyświetlony, możliwe, że aplikacja RMS sharing nie jest zainstalowana na danym komputerze, nie zainstalowano najnowszej wersji albo trzeba ponownie uruchomić komputer w celu ukończenia instalacji. Aby uzyskać więcej informacji na temat sposobu instalowania aplikacji do udostępniania, zobacz [Pobieranie i instalowanie aplikacji do udostępniania usługi Microsoft Rights Management](install-sharing-app.md).

2.  Określ odpowiednie opcje dla tego pliku w oknie dialogowym [Udostępnianie chronionej zawartości](sharing-app-dialog-box.md), a następnie kliknij pozycję **Wyślij teraz**.

### Inne metody ochrony pliku udostępnianego pocztą e-mail
Oprócz udostępniania pliku chronionego przy użyciu programu Outlook można także użyć następujących alternatyw:

-   W Eksploratorze plików: ta metoda działa w przypadku wszystkich plików.

-   W aplikacji pakietu Office: ta metoda działa w przypadku aplikacji obsługiwanych przez aplikację RMS sharing przy użyciu dodatku do pakietu Office umożliwiającego wyświetlanie grupy **RMS** na wstążce.

#### W Eksploratorze plików lub aplikacji pakietu Office: aby chronić plik udostępniany pocztą e-mail

1.  Skorzystaj z jednej z następujących opcji:

    -   W Eksploratorze plików: kliknij plik prawym przyciskiem myszy, wybierz polecenie **Chroń za pomocą usługi RMS**, a następnie wybierz pozycję **Udostępnij chronione**.

        ![Opcja menu Udostępnij chronione](../media/ADRMS_MSRMSApp_ShareProtectedMenu.png)

    -   W aplikacji pakietu Office (Word, Excel i PowerPoint): Upewnij się, że plik został zapisany. Następnie na karcie **Narzędzia główne** w grupie **RMS** kliknij pozycję **Udostępnij chronione**, a następnie ponownie kliknij pozycję **Udostępnij chronione**:

        ![Dodatek do paska narzędzi pakietu Office](../media/ADRMS_MSRMSApp_SP_OfficeToolbar.png)

    Jeśli opcje ochrony nie są wyświetlone, możliwe, że aplikacja RMS sharing nie jest zainstalowana na danym komputerze, nie zainstalowano najnowszej wersji albo trzeba ponownie uruchomić komputer w celu ukończenia instalacji. Aby uzyskać więcej informacji na temat sposobu instalowania aplikacji do udostępniania, zobacz [Pobieranie i instalowanie aplikacji do udostępniania usługi Microsoft Rights Management](install-sharing-app.md).

2.  Określ odpowiednie opcje dla tego pliku w oknie dialogowym [Udostępnianie chronionej zawartości](sharing-app-dialog-box.md), a następnie kliknij pozycję **Wyślij**.

3.  Przez chwilę może zostać wyświetlone okno dialogowe informujące, że plik jest chroniony, po czym zostanie wyświetlona utworzona automatycznie wiadomość e-mail informująca adresatów, że jej załączniki są chronione za pomocą usług Microsoft RMS i że muszą się oni zalogować. Po kliknięciu linku logowania adresat zobaczy instrukcje i linki umożliwiające otwarcie chronionego załącznika.

    Przykład:

    ![Wiadomość e-mail dotycząca usług Azure RMS](../media/ADRMS_MSRMSApp_EmailMessage.PNG)

    Czy zastanawiasz się, [co to za plik ppdf, który jest automatycznie tworzony?](sharing-app-dialog-box.md#what-s-the-ppdf-file-that-s-automatically-created)

4.  Opcjonalnie: Dowolne elementy wiadomości e-mail można zmienić. Można na przykład rozwinąć lub zmienić temat lub tekst wiadomości.

    > [!WARNING]
    > Wprawdzie można dodawać i usuwać adresatów wiadomości e-mail, ale nie ma to wpływu na uprawnienia do załącznika określone w oknie dialogowym **Udostępnianie chronionej zawartości**. Aby zmienić te uprawnienia (na przykład nadać nowej osobie uprawnienia do otwierania pliku), zamknij wiadomość e-mail bez zapisywania ani wysyłania i wróć do kroku 1.

5.  Wyślij wiadomość e-mail.

## Przykłady i inne instrukcje
Aby uzyskać instrukcje i przykłady dotyczące korzystania z aplikacji do udostępniania usługi Rights Management, zapoznaj się z następującymi sekcjami podręcznika użytkownika aplikacji do udostępniania usługi Rights Management:

-   [Przykłady korzystania z aplikacji RMS sharing](sharing-app-user-guide.md#examples-for-using-the-rms-sharing-application)

-   [Co chcesz zrobić?](sharing-app-user-guide.md#what-do-you-want-to-do)

## Zobacz też
[Podręcznik użytkownika aplikacji do udostępniania usługi Rights Management](sharing-app-user-guide.md)



<!--HONumber=Jul16_HO3-->


