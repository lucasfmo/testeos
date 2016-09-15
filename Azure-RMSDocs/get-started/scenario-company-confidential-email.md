---
title: "Scenariusz — wysyłanie wiadomości e-mail zawierających poufne dane firmy | Usługa Azure RMS"
description: 
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 05/20/2016
ms.topic: get-started-article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 950799e9-2289-48c7-b95a-f54a8ead520a
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 332e102cb27854314b93a71bfeae82a95c9a7812
ms.openlocfilehash: b6f3b06485dda81be2a36035fea7477f4061a8e9


---

# Scenariusz — wysyłanie wiadomości e-mail zawierających poufne dane firmy

*Dotyczy usług: Azure Rights Management, Office 365*

W tym scenariuszu i uzupełniającej dokumentacji użytkownika usługa Azure Rights Management ma na celu zapewnienie tego, aby każdy użytkownik w organizacji mógł bezpiecznie wysyłać wiadomości e-mail, których treść nie powinna być odczytywana poza organizacją. Na przykład ktoś może przekazywać wiadomość e-mail osobie w innej organizacji lub na osobiste konto e-mail. Wiadomości e-mail i załączniki będą chronione za pomocą usługi Azure Rights Management oraz szablonu, który użytkownicy wybiorą z klienta poczty e-mail.

Najprostszy sposób realizacji tego scenariusza polega na użyciu wbudowanych, domyślnych szablonów, w których dostęp do treści jest automatycznie przyznawany wszystkim użytkownikom w organizacji. W razie potrzeby można jednak wprowadzić ostrzejsze ograniczenia, tworząc szablon niestandardowy, który umożliwia dostęp tylko podgrupie użytkowników lub wprowadza inne ograniczenia, takie jak uprawnienie tylko do odczytu lub data wygaśnięcia, albo powoduje wyłączenie przycisku Prześlij dalej w kliencie poczty e-mail.

> [!IMPORTANT]
> Chociaż w tym scenariuszu można usunąć z konfigurowanego szablonu niestandardowego prawo do **przekazywania**, co spowoduje wyłączenie przycisku Prześlij dalej w kliencie poczty e-mail, ta konfiguracja nie zapobiega udostępnianiu przez użytkowników wiadomości e-mail innym autoryzowanym użytkownikom. Adresat może zapisać wiadomość e-mail (i załączniki), a następnie udostępnić informacje za pomocą innych mechanizmów udostępniania.
> 
> Na przykład Robert wysyła wiadomość e-mail do Alicji przy użyciu szablonu niestandardowego, w którym niestandardowe prawa zapisywania pliku i edytowania zawartości zostały przypisane grupie Marketing i który nie obejmuje prawa przekazywania wiadomości. Chociaż Alicja nie może przesłać wiadomości e-mail do innych osób, może zapisać tę wiadomość e-mail wraz z załącznikami na dysku USB lub w udziale serwera plików i każdy członek grupy Marketing, który ma dostęp do tych plików, będzie mógł je przeczytać i edytować. Użytkownicy, którzy nie należą do grupy Marketing, nie będą mogli wyświetlić zawartości.

Podane tu instrukcje mają zastosowanie w następujących okolicznościach:

-   Dowolny użytkownik w organizacji chce udostępniać informacje innym osobom w organizacji, ale informacje te nie mogą być udostępniane poza organizacją.

-   Informacje przeznaczone do udostępnienia mogą być zawarte w wiadomości e-mail lub załączniku.

-   Użytkownicy muszą ręcznie wybrać szablon w kliencie poczty e-mail.

## Instrukcje dotyczące wdrażania
![Instrukcje dla administratora dotyczące szybkiego wdrażania usługi Azure RMS](../media/AzRMS_AdminBanner.png)

Zanim przejdziesz do dokumentacji użytkownika, upewnij się, że zostały spełnione następujące wymagania.

## Wymagania dotyczące tego scenariusza
Aby wykonać instrukcje dotyczące tego scenariusza, należy spełnić następujące wymagania:

|Wymaganie|Jeśli potrzebujesz dodatkowych informacji|
|---------------|--------------------------------|
|Zostały przygotowane konta i grupy dla usługi Office 365 lub Azure Active Directory.|[Przygotowanie do wdrożenia usługi Azure Rights Management](https://technet.microsoft.com/library/jj585029.aspx)|
|Klucz dzierżawy usługi Azure Rights Management jest zarządzany przez firmę Microsoft. Nie jest używana funkcja BYOK.|[Planowanie i wdrażanie klucza dzierżawy usługi Azure Rights Management](https://technet.microsoft.com/library/dn440580.aspx)|
|Usługa Azure Rights Management została aktywowana.|[Aktywacja usługi Azure Rights Management](https://technet.microsoft.com/library/jj658941.aspx)|
|Jedna z poniższych opcji:<br /><br />– Włączono obsługę usługi Azure Rights Management w usłudze Exchange Online.<br /><br />– Łącznik usługi RMS został zainstalowany i skonfigurowany do współdziałania z lokalną instalacją programu Exchange.|W przypadku usługi Exchange Online: zobacz sekcję **Exchange Online: konfiguracja usługi IRM** w temacie [Konfigurowanie aplikacji dla usługi Azure Rights Management](https://technet.microsoft.com/library/jj585031.aspx).<br /><br />W przypadku lokalnego programu Exchange: [Wdrażanie łącznika usługi Azure Rights Management](https://technet.microsoft.com/library/dn375964.aspx)|
|Domyślny szablon **&lt;organizacja&gt; — poufne** usługi Azure Rights Management nie został zarchiwizowany. Alternatywnie: został w tym celu skonfigurowany szablon niestandardowy, ponieważ potrzebne są bardziej restrykcyjne ustawienia lub tylko podgrupa użytkowników w organizacji powinna mieć możliwość odczytu chronionych wiadomości e-mail.|[Konfigurowanie szablonów niestandardowych usługi Azure Management Rights](https://technet.microsoft.com/library/dn642472.aspx)<br /><br />Porada: jeśli potrzebne są bardziej restrykcyjne ustawienia dotyczące zasad użytkowania obejmujące wszystkich użytkowników w organizacji, należy skopiować, a następnie edytować jeden z domyślnych szablonów, zamiast tworzyć szablon od podstaw.<br /><br />W tym scenariuszu zaktualizowane szablony nie są natychmiast odświeżane w klientach poczty e-mail. Aby uzyskać odpowiednie informacje, sprawdź sekcję [Odświeżanie szablonów dla użytkowników](https://technet.microsoft.com/library/dn642472.aspx) w artykule dotyczącym konfigurowania szablonów.|
|Użytkownicy, którzy wysyłają chronione wiadomości e-mail, korzystają z programu Outlook 2013 lub Outlook 2016 bądź z usługi Outlook Web Access.<br /><br />Użytkownicy, którzy otrzymują te wiadomości e-mail, korzystają z klienta poczty e-mail, który obsługuje usługę Azure Rights Management.|Można korzystać z programu Outlook 2010, ale należy [zainstalować aplikację do udostępniania usługi Rights Management dla systemu Windows](https://technet.microsoft.com/library/dn339003.aspx) i odpowiednio zmienić instrukcje użytkownika.<br /><br />Listę klientów poczty e-mail, które obsługują usługę Azure Rights Management, można znaleźć w kolumnie **Wiadomości e-mail** w tabeli [Funkcje urządzeń klienckich](https://technet.microsoft.com/library/dn655136.aspx) w temacie [Wymagania dotyczące usługi Azure Rights Management](https://technet.microsoft.com/library/dn655136.aspx)|

## Instrukcje w dokumentacji użytkownika
Przy użyciu następującego szablonu skopiuj i wklej instrukcje dla użytkownika do wiadomości dla użytkowników końcowych, po czym wprowadź poniższe zmiany, aby odzwierciedlić charakter lokalnego środowiska:

1.  Zastąp wszystkie wystąpienia zmiennej *&lt;nazwa organizacji&gt;* nazwą swojej organizacji.

2.  Zastąp wszystkie wystąpienia zmiennej *&lt;nazwa organizacji — poufne&gt;* nazwą swojego szablonu domyślnego lub niestandardowego.

3.  Zastąp zrzuty ekranu, tak aby pokazywały nazwy szablonów Twojej organizacji.

4.  Zastąp *&lt;dane kontaktowe&gt;* instrukcjami dla użytkowników dotyczącymi sposobu kontaktowania się z działem pomocy technicznej, na przykład podaj link do witryny sieci Web, adres e-mail lub numer telefonu.

5.  **Dodatkowe zmiany, które możesz wprowadzić:**

    -   Jeśli z praktycznego punktu widzenia lepiej jest ograniczyć instrukcje do jednego klienta poczty e-mail, weź takie rozwiązanie pod uwagę w celu uproszczenia procedury i usuń pozostałe instrukcje.

    -   Jeśli korzystasz z szablonu niestandardowego, a nie sugerowanego szablonu domyślnego, skoryguj odpowiednio następujące elementy zawartości:

        -   Określ precyzyjnie tytuł.

        -   Określ użytkowników lub grupy do wyboru w kroku 1.

        -   Podaj nazwę szablonu niestandardowego w kroku 2.

        -   Zmodyfikuj końcowy akapit, aby wyjaśnić, jakim ograniczeniom będą podlegać adresaci.

6.  Wprowadź wszelkie inne zmiany, które chcesz uwzględnić w tym zestawie instrukcji, a następnie wyślij go do wybranych użytkowników.

7.  Ponieważ niektórzy klienci nie obsługują usługi Rights Management, może być konieczne udzielenie wskazówek i zaleceń adresatom chronionych wiadomości e-mail. Treść tych informacji będzie zależała od urządzeń i aplikacji poczty e-mail, które są używane w organizacji oraz Twoich indywidualnych preferencji. Na przykład możesz sformułować zalecenie, aby użytkownicy systemu iOS odczytywali chronione wiadomości e-mail w programie Outlook dla urządzeń iPad i iPhone zamiast w macierzystym kliencie poczty systemu iOS.

    Więcej informacji o klientach poczty e-mail można znaleźć w kolumnie **Wiadomości e-mail** w tabeli [Funkcje urządzeń klienckich](https://technet.microsoft.com/library/dn655136.aspx) w temacie [Wymagania dotyczące usługi Azure Rights Management](https://technet.microsoft.com/library/dn655136.aspx).

W przykładowej dokumentacji przedstawiono potencjalny wygląd odpowiednio dostosowanych instrukcji, które zobaczą użytkownicy.

![Dokumentacja użytkownika dotycząca szablonów na potrzeby szybkiego wdrażania usługi Azure RMS](../media/AzRMS_UsersBanner.png)

### Jak przy użyciu programu Outlook wysyłać wiadomości e-mail zawierające poufne dane firmy

1.  W programie Outlook utwórz nową wiadomość e-mail, dodaj potrzebne załączniki, a następnie wybierz użytkowników lub grupy w organizacji *&lt;nazwa organizacji&gt;*.

2.  Na karcie **Opcje** kliknij pozycję **Uprawnienie**, a następnie wybierz polecenie **&lt;nazwa organizacji — poufne&gt;**:

    ![Zrzut ekranu — jak przy użyciu programu Outlook wysyłać wiadomości e-mail zawierające poufne dane firmy](../media/AzRMS_OutlookTemplate.PNG)

3.  Wyślij wiadomość.

### Jak wysyłać wiadomości e-mail zawierające poufne dane firmy przy użyciu programu Outlook Web App

1.  W programie Outlook Web App utwórz nową wiadomość e-mail, dodaj potrzebne załączniki, a następnie wybierz z książki adresowej użytkowników lub grupy w organizacji *&lt;nazwa organizacji&gt;*.

2.  Kliknij menu **…**, kliknij polecenie **Ustaw uprawnienia**, a następnie wybierz opcję **&lt;nazwa organizacji — poufne&gt;**:

    ![Zrzut ekranu — jak przy użyciu programu Outlook Web App wysyłać wiadomości e-mail zawierające poufne dane firmy](../media/AzRMS_OWATemplate.png)

3.  Wyślij wiadomość.

Gdy osoba podana w wierszu **Do**, **DW** lub **UDW** otrzyma tę wiadomość e-mail, zanim będzie mogła ją odczytać, może zostać poproszona o uwierzytelnienie, aby potwierdzić, że jest użytkownikiem z organizacji *&lt;nazwa organizacji&gt;*. Później użytkownicy nie będą otrzymywali takich monitów, ponieważ zostali już uwierzytelnieni.

Adresaci wiadomości e-mail będą mogli ją przesłać do innych osób, ale tylko użytkownicy z organizacji *&lt;nazwa organizacji&gt;* będą mogli ją odczytać. Dołączony dokument pakietu Office będzie podlegał takiej samej ochronie, nawet jeśli załącznik zostanie zapisany pod inną nazwą w innej lokalizacji. Pomyślnie uwierzytelnieni użytkownicy mogą jednak skopiować i wkleić albo wydrukować zawartość wiadomości e-mail lub załącznika. Jeśli potrzebujesz bardziej restrykcyjnej ochrony, która zapobiegnie takim działaniom, skontaktuj się z działem pomocy technicznej.

**Potrzebujesz pomocy?**

-   Skontaktuj się z działem pomocy technicznej:

    -   *&lt;dane kontaktowe&gt;*

### Przykładowa niestandardowa dokumentacja użytkownika
![Przykładowa dokumentacja użytkownika dotycząca szybkiego wdrażania usługi Azure RMS](../media/AzRMS_ExampleBanner.png)

#### Jak przy użyciu programu Outlook wysyłać wiadomości e-mail zawierające poufne dane firmy

1.  W programie Outlook utwórz nową wiadomość e-mail, dodaj potrzebne załączniki, a następnie wybierz użytkowników lub grupy w organizacji VanArsdel.

2.  Na karcie **OPCJE** kliknij pozycję **Uprawnienie**, a następnie wybierz polecenie **VanArsdel, Ltd — poufne**:

    ![Zrzut ekranu — jak przy użyciu programu Outlook wysyłać wiadomości e-mail zawierające poufne dane firmy](../media/AzRMS_OutlookTemplate.PNG)

3.  Wyślij wiadomość.

#### Jak wysyłać wiadomości e-mail zawierające poufne dane firmy przy użyciu programu Outlook Web App

1.  W programie Outlook Web App utwórz nową wiadomość e-mail, dodaj potrzebne załączniki, a następnie wybierz z książki adresowej użytkowników lub grupy w organizacji VanArsdel.

2.  Kliknij menu **…**, kliknij polecenie **Ustaw uprawnienia**, a następnie wybierz opcję **VanArsdel, Ltd — poufne**:

    ![Zrzut ekranu — jak przy użyciu programu Outlook Web App wysyłać wiadomości e-mail zawierające poufne dane firmy](../media/AzRMS_OWATemplate.png)

3.  Wyślij wiadomość.

Gdy osoba podana w wierszu **Do**, **DW** lub **UDW** otrzyma tę wiadomość e-mail, zanim będzie mogła ją odczytać, może zostać poproszona o uwierzytelnienie, aby potwierdzić, że jest użytkownikiem w organizacji VanArsdel, Ltd. Później użytkownicy nie będą otrzymywali takich monitów, ponieważ zostali już uwierzytelnieni.

Adresaci wiadomości e-mail będą mogli ją przesłać do innych osób, ale tylko użytkownicy z organizacji VanArsdel będą mogli ją odczytać. Dołączony dokument pakietu Office będzie podlegał takiej samej ochronie, nawet jeśli załącznik zostanie zapisany pod inną nazwą w innej lokalizacji. Pomyślnie uwierzytelnieni użytkownicy mogą jednak skopiować i wkleić albo wydrukować zawartość wiadomości e-mail lub załącznika. Jeśli potrzebujesz bardziej restrykcyjnej ochrony, która zapobiegnie takim działaniom, skontaktuj się z działem pomocy technicznej.

**Potrzebujesz pomocy?**

-   Skontaktuj się z działem pomocy technicznej:

    -   Adres e-mail: helpdesk@vanarsdelltd.com




<!--HONumber=Jul16_HO3-->


