---
title: "Ułatwienia dla użytkowników dotyczące ochrony plików za pomocą usługi Azure Rights Management | Azure RMS"
description: 
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 06/09/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 58f9a6ff-4121-4c8c-9865-1bb290604ad2
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b6dcd8bb1091e9c484e02042adbf993381581a9d
ms.openlocfilehash: d48616cb638522e6cda61e7ae96db9480fc14099


---

# Ułatwienia dla użytkowników dotyczące ochrony plików za pomocą usługi Azure Rights Management

*Dotyczy usług: Azure Rights Management, Office 365*

Po wdrożeniu i skonfigurowaniu usługi Azure Rights Management (Azure RMS) w Twojej organizacji należy zapewnić pomoc i wskazówki dla użytkowników, administratorów i działu pomocy technicznej:

-   **Informacje dla użytkowników końcowych:**

    Powiadom użytkowników, jak i kiedy należy chronić dokumenty i wiadomości e-mail zawierające informacje poufne. Jeśli to możliwe, podaj te informacje w odniesieniu do istniejących przepływów pracy, dzięki czemu użytkownicy będą mogli włączyć dodatkowe czynności do znanych sobie procesów, zamiast wprowadzać zupełnie nowe procesy. Poinformuj ich o korzyściach (i czynnikach ryzyka) specyficznych dla prowadzonej działalności, a także przekaż wskazówki dotyczące sytuacji, w których należy chronić pliki i wiadomości e-mail. Jeśli skonfigurowano [szablony niestandardowe](configure-custom-templates.md), udostępnij instrukcje dotyczące wyboru szablonów w przypadku, gdy nazwa i opis są niewystarczające.

    > [!TIP]
    > Przykładowe filmy dla użytkowników końcowych:
    >
    > -   [Środowisko użytkownika usługi Azure RMS](http://channel9.msdn.com/Series/Information-Protection/Azure-RMS-user-experience)
    > -   [Śledzenie i odwoływanie dokumentów w usłudze Azure RMS](http://channel9.msdn.com/Series/Information-Protection/Azure-RMS-Document-Tracking-and-Revocation)

-   **Informacje dla administratorów:**

    Niektóre aplikacje automatycznie stosują ochronę informacji przy użyciu zasad i ustawień skonfigurowanych przez administratorów. W przypadku tych aplikacji konieczne może być zapewnienie instrukcji dla innych administratorów, którzy zarządzają tymi aplikacjami i usługami. Aby uzyskać więcej informacji, zobacz [Jak aplikacje obsługują usługę Azure Rights Management](../understand-explore/applications-support.md) i [Konfigurowanie aplikacji do współdziałania z usługą Azure Rights Management](configure-applications.md).

-   **Informacje dla działu pomocy technicznej:**

    Jednym z najbardziej przydatnych narzędzi dla działu pomocy technicznej jest [RMS Analyzer](https://www.microsoft.com/en-us/download/details.aspx?id=46437). Operatorzy pomocy technicznej mogą uruchomić to narzędzie z opcją administratora usługi Azure RMS oraz mogą poprosić użytkowników o jego uruchomienie z opcją użytkownika usługi Azure RMS. Narzędzie może być pomocne nie tylko w identyfikowaniu problemów, ale także w rozwiązaniu problemów, które zostaną znalezione. W przypadku problemów nierozwiązanych umożliwia rejestrowanie informacji w dziennikach śledzenia.

    W przypadku uprawnionych żądań pełnych praw dostępu do dokumentów chronionych, na przykład żądania działu prawnego lub menedżera po odejściu pracownika z organizacji, upewnij się, że dział pomocy technicznej dysponuje procesami pozwalającymi na obsługę żądania za pomocą [funkcji administratora](configure-super-users.md) usługi Azure RMS.

    Oto niektóre typowe problemy zgłaszane przez użytkowników:

    -   **Pomoc dotycząca logowania:**

        Użytkownicy mogą otrzymać monit o wprowadzenie poświadczeń, gdy usługa Azure RMS wymaga uwierzytelnienia użytkownika i nie może użyć buforowanych poświadczeń. Należy użyć służbowego lub szkolnego konta użytkownika i hasła skojarzonego z dzierżawą usługi Office 365 lub dzierżawą usługi Azure Active Directory. Nie należy korzystać z konta Microsoft (dawniej identyfikator Microsoft Live ID) ani osobistego konta e-mail użytkownika, ponieważ nie są one obecnie obsługiwane przez usługę Azure RMS. Przekaż użytkownikom i działowi pomocy technicznej instrukcje dotyczące wyboru konta, którego należy użyć w przypadku wyświetlenia monitu o poświadczenia podczas korzystania z tych aplikacji razem z usługą Azure RMS.

    -   **Problemy dotyczące ochrony lub używania zawartości:**

        Upewnij się, że użytkownicy mają odpowiednie instrukcje dotyczące aplikacji, z których korzystają, oraz używają aplikacji i urządzeń, które są obsługiwane przez usługę Azure RMS. Aby uzyskać więcej informacji o obsługiwanych aplikacjach i urządzeniach, zobacz [Wymagania dotyczące usługi Azure Rights Management](../get-started/requirements-azure-rms.md).

        Jeśli użytkownik zaobserwuje błąd podczas próby ochrony lub korzystania z zawartości, poproś go o uruchomienie narzędzia [RMS Analyzer](https://www.microsoft.com/en-us/download/details.aspx?id=46437) jako użytkownik usługi Azure RMS.

        Jeśli użytkownik zgłasza, że może otworzyć chronioną zawartość, ale nie ma potrzebnych praw, poproś go o uruchomienie narzędzia [RMS Analyzer](https://www.microsoft.com/en-us/download/details.aspx?id=46437) jako użytkownik usługi Azure RMS oraz pobierz i wyświetl szablony. W ten sposób możesz potwierdzić, że szablony zostały pomyślnie pobrane przez użytkownika, oraz sprawdzić, jakie uprawnienia zapewniają te szablony. Problem może polegać na tym, że użytkownik nie należy do prawidłowej grupy, która jest skonfigurowana dla danego szablonu, lub że szablon wymaga ponownej konfiguracji dla użytkownika.

Skorzystaj z poniższych sekcji zawierających informacje dotyczące aplikacji, aby ułatwić użytkownikom ochronę ważnych dokumentów i wiadomości e-mail.

## Korzystanie z ochrony informacji przy użyciu aplikacji do udostępniania usług Rights Management
Aplikacja do udostępniania usług Rights Management (RMS) jest wymagana do ochrony i korzystania z zawartości chronionej w przypadku użytkowników pakietu Office 2010, ale jest także zalecana dla wszystkich komputerów i urządzeń przenośnych, które obsługują usługę Azure RMS.

Oprócz ułatwiania użytkownikom ochrony ważnych dokumentów aplikacja do udostępniania usługi RMS umożliwia śledzenie dokumentów, które zostały objęte ochroną, i w razie potrzeby odwołanie dostępu do nich.

Instrukcje dotyczące korzystania z tej aplikacji na komputerach z systemem Windows można znaleźć w [Podręczniku użytkownika aplikacji do udostępniania usług Rights Management](../rms-client/sharing-app-user-guide.md).

Aby uzyskać informacje dotyczące urządzeń przenośnych, zobacz [Często zadawane pytania dotyczące aplikacji do udostępniania usługi Microsoft Rights Management dla platform urządzeń przenośnych](http://technet.microsoft.com/dn451248).

> [!TIP]
> Przykładowy scenariusz wysokiego poziomu ze zrzutami ekranu można znaleźć w artykule [Użytkownicy bezpiecznie udostępniają załączniki użytkownikom mobilnym](../understand-explore/what-admins-users-see.md#users-safely-share-attachments-with-mobile-users).

## Korzystanie z ochrony informacji w usłudze Office 365 oraz w pakiecie Office 2016 lub Office 2013
Jeśli używasz usługi Azure RMS, a aplikacja do udostępniania usług Rights Management nie została zainstalowana, użytkownicy nie będą widzieli przycisku **Udostępnij chronione** na wstążce ani opcji **Włącz ochronę miejscową** w Eksploratorze plików, które ułatwiają ochronę plików. Tacy użytkownicy muszą wykonać instrukcje podobne do następujących:

> [!TIP]
> Aby znaleźć pomoc dotyczącą aplikacji i instrukcje korzystania z ochrony informacji przy użyciu tych aplikacji, wyszukaj ciąg **IRM** razem z nazwą i wersją aplikacji.

#### Aby chronić dokument w programie Word 2013

1.  W programie Microsoft Word utwórz nowy dokument.

2.  W menu **Plik** kliknij polecenie **Informacje**, po czym kliknij przycisk **Ochrona dokumentu**. Kliknij pozycję **Ogranicz dostęp**, a następnie wybierz szablon, aby szybko zastosować odpowiednie prawa użytkowania, lub wybierz opcję **Ogranicz dostęp** i wybierz prawa użytkowania samodzielnie.

    > [!NOTE]
    > Jeśli korzystasz z usług Rights Management po raz pierwszy, po uzyskaniu kontaktu z usługą [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] zostanie wyświetlony monit o podanie poświadczeń w celu skonfigurowania klienta IRM pakietu Office.

3.  Zapisz dokument.

Po otwarciu dokumentu przez innych użytkowników najpierw zostanie wykonane ich uwierzytelnienie. Jeśli użytkownik nie jest uprawniony do otwierania tego dokumentu, dokument nie zostanie otwarty. Jeśli użytkownik jest uprawniony do otwierania tego dokumentu, dokument zostanie otwarty z ograniczonymi prawami użytkowania określonymi dla danego użytkownika. Na przykład prawo użytkowania Tylko do wyświetlania nie zezwala na edycję lub zapis dokumentu przez użytkownika, nawet jeśli plik zostanie wcześniej skopiowany do innej lokalizacji. Prawa użytkowania są wyświetlane w górnej części dokumentu na transparencie informującym o ograniczeniach. Na transparencie mogą zostać wyświetlone uprawnienia zastosowane do dokumentu lub link umożliwiający ich wyświetlenie.

#### Aby chronić wiadomość e-mail przy użyciu programu Outlook 2013 i usługi Exchange Online

1.  W programie Outlook utwórz nową wiadomość e-mail zaadresowaną do odbiorcy w Twojej organizacji.

2.  Na karcie **OPCJE** kliknij pozycję **Uprawnienie**, a następnie wybierz opcję. Przykład: **Nie przesyłaj dalej**, **&lt;Nazwa firmy&gt; — Poufne** lub **&lt;Nazwa firmy&gt; — Poufne tylko do wyświetlania**.

3.  Wyślij wiadomość.

Podobnie jak w przypadku wyświetlania dokumentu chronionego, po otrzymaniu wiadomości e-mail adresaci zostają najpierw uwierzytelnieni. Jeśli użytkownik jest uprawniony do wyświetlenia wiadomości e-mail, zostanie ona otwarta z ograniczonymi prawami użytkowania, które zostały określone dla danego użytkownika. Na przykład, jeśli została wybrana opcja **Nie przesyłaj dalej**, na wstążce nie będzie dostępny przycisk Prześlij dalej.

#### Aby chronić wiadomość e-mail przy użyciu aplikacji Outlook Web App

1.  W aplikacji Outlook Web App utwórz nową wiadomość e-mail zaadresowaną do odbiorcy w Twojej organizacji.

2.  Kliknij pozycję **...**, kliknij pozycję **Ustaw uprawnienie**, a następnie wybierz opcję. Przykład: **Nie przesyłaj dalej**, **Nie odpowiadaj wszystkim**, **&lt;Nazwa firmy&gt; — Poufne** lub **&lt;Nazwa firmy&gt; — Poufne tylko do wyświetlania**.

3.  Wyślij wiadomość.

Podobnie jak w przypadku wyświetlania dokumentu chronionego, po otrzymaniu wiadomości e-mail adresaci zostają najpierw uwierzytelnieni. Jeśli użytkownik jest uprawniony do wyświetlenia wiadomości e-mail, zostanie ona otwarta z ograniczonymi prawami użytkowania, które zostały określone dla danego użytkownika. Na przykład, jeśli została wybrana opcja **Nie odpowiadaj wszystkim**, opcja **ODPOWIEDZ WSZYSTKIM** w oknie komunikatu jest niedostępna.





<!--HONumber=Jun16_HO4-->


