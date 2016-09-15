---
title: "Scenariusz — bezpieczna wymiana zastrzeżonych informacji przez przedstawicieli kadry kierowniczej | Azure RMS"
description: 
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 05/20/2016
ms.topic: get-started-article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: e18cf5df-859e-4028-8d19-39b0842df33d
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: f7dd88d90357c99c69fe4fdde67c1544595e02f8
ms.openlocfilehash: def8b7e98fd55a3d028978ffc9f8e41e38a5622c


---

# Scenariusz — bezpieczna wymiana zastrzeżonych informacji przez przedstawicieli kadry kierowniczej

*Dotyczy usług: Azure Rights Management, Office 365*

W tym scenariuszu i pomocniczej dokumentacji użytkownika zastosowano usługę Azure Rights Management, aby umożliwić przedstawicielom kadry kierowniczej bezpieczną wymianę wiadomości e-mail i załączników oraz automatyczne ograniczenie dostępu do grona przedstawicieli kadry kierowniczej za pomocą zasad, bez wymagania podejmowania przez nich dodatkowych czynności. Wiadomości e-mail i wszystkie załączniki będą automatycznie chronione przez usługę Azure Rights Management.

W razie potrzeby do reguły można dodać wyjątek, na przykład tekst NCHR (skrót od „Niechroniona”) w temacie wiadomości e-mail, tak aby przedstawiciele kadry kierowniczej mogli korzystać z tej opcji w przypadku konieczności wysłania niechronionej wiadomości do swoich kolegów — na przykład w celu udostępnienia treści do wglądu przed wysłaniem wiadomości do innych osób.

Podane tu instrukcje mają zastosowanie w następujących okolicznościach:

-   Członkowie kadry kierowniczej wymieniają się poufnymi informacjami, które nie powinny być udostępniane innym osobom.

-   Wysyłając te wiadomości e-mail, członkowie kadry kierowniczej nie muszą wykonywać żadnych dodatkowych czynności. Jedynym wymaganiem jest wysłanie wiadomości na służbowy adres e-mail, a nie na adres prywatny.

-   W przypadku konieczności wysłania niechronionej wiadomości e-mail do innych przedstawicieli kierownictwa można samodzielnie wyłączyć tę regułę zabezpieczeń.

## Instrukcje dotyczące wdrażania
![Instrukcje dla administratora dotyczące szybkiego wdrażania usługi Azure RMS](../media/AzRMS_AdminBanner.png)

Przed przejściem do części dotyczącej dokumentacji użytkownika należy upewnić się, że zostały spełnione poniższe wymagania, i wykonać instrukcje zawarte w procedurach pomocniczych.

## Wymagania dotyczące tego scenariusza
Aby wykonać instrukcje dotyczące tego scenariusza, należy spełnić następujące wymagania:

|Wymaganie|Jeśli potrzebujesz dodatkowych informacji|
|---------------|--------------------------------|
|Zostały przygotowane konta i grupy dla usługi Office 365 lub Azure Active Directory:<br /><br />– Utworzono grupę z włączoną obsługą poczty o nazwie **Kierownicy** i dodano do niej wszystkich przedstawicieli kadry kierowniczej.<br /><br />– Utworzono grupę z włączoną obsługą poczty o nazwie **Administratorzy usługi RMS** i dodano do niej wszystkich administratorów, którzy będą konfigurować usługę Azure RMS.|[Przygotowanie do wdrożenia usługi Azure Rights Management](https://technet.microsoft.com/library/jj585029.aspx)|
|Klucz dzierżawy usługi Azure Rights Management jest zarządzany przez firmę Microsoft. Nie jest używana funkcja BYOK.|[Planowanie i wdrażanie klucza dzierżawy usługi Azure Rights Management](https://technet.microsoft.com/library/dn440580.aspx)|
|Usługa Azure Rights Management została aktywowana.|[Aktywacja usługi Azure Rights Management](https://technet.microsoft.com/library/jj658941.aspx)|
|Występuje jedna z poniższych konfiguracji:<br /><br />– Włączono obsługę usługi Azure Rights Management w usłudze Exchange Online.<br /><br />– Łącznik usługi RMS został zainstalowany i skonfigurowany do współdziałania z lokalną instalacją programu Exchange.|W przypadku usługi Exchange Online: zobacz sekcję **Exchange Online: konfiguracja usługi IRM** w temacie [Konfigurowanie aplikacji dla usługi Azure Rights Management](https://technet.microsoft.com/library/jj585031.aspx).<br /><br />W przypadku lokalnej instalacji programu Exchange: [Wdrażanie łącznika usługi Azure Rights Management](https://technet.microsoft.com/library/dn375964.aspx).|
|Skonfigurowano szablon niestandardowy zgodnie z poniższym opisem.|[Konfigurowanie szablonów niestandardowych usługi Azure Rights Management](https://technet.microsoft.com/library/dn642472.aspx)|
|Skonfigurowano regułę ochrony transportu dla usługi IRM zgodnie z opisem w dalszej części tego artykułu.|W przypadku usługi Exchange Online: [Create a Transport Protection Rule (Tworzenie reguły ochrony transportu)](https://technet.microsoft.com/library/dd302432.aspx)<br /><br />W przypadku programu Exchange 2013: [Create a Transport Protection Rule (Tworzenie reguły ochrony transportu)](https://technet.microsoft.com/library/dd302432%28v=exchg.150%29.asp)<br /><br />W przypadku programu Exchange 2010: [Create a Transport Protection Rule (Tworzenie reguły ochrony transportu)](https://technet.microsoft.com/en-us/library/dd302432%28v=exchg.141%29.aspx)|

### Aby skonfigurować szablon niestandardowy dla przedstawicieli kadry kierowniczej

1.  W klasycznym portalu Azure: utwórz nowy szablon niestandardowy usługi Azure Rights Management, który zawiera następujące wartości i ustawienia:

    -   Nazwa: **Kierownicy**.

    -   Uprawnienia: przyznaj grupie **Kierownicy** z włączoną obsługą poczty uprawnienia **Współwłaściciel**.

    -   Zakres: wybierz grupę **Kierownicy** z włączoną obsługą poczty oraz grupę **Administratorzy usługi RMS** z włączoną obsługą poczty.

2.  Opublikuj nowy szablon.

3.  Tylko w przypadku usługi Exchange Online: odśwież szablony przy użyciu polecenia programu Windows PowerShell dla usługi Exchange Online:

    ```
    Import-RMSTrustedPublishingDomain -Name "RMS Online -1" -RefreshTemplates -RMSOnline
    ```

### Aby skonfigurować regułę transportu dla usługi IRM

-   Skorzystaj z wymienionej w tabeli dokumentacji programu Exchange, aby uzyskać informacje o procedurach umożliwiających tworzenie reguł transportu z następującymi ustawieniami:

    -   Nazwa: **Stosowanie szablonów dla kierowników do wiadomości e-mail wysyłanych przez kadrę kierowniczą**

    -   Określ grupę **Kierownicy** jako nadawcę i odbiorcę w ramach reguły i zdefiniuj dodatkowy warunek.

    -   W obszarze akcji wybierz pozycję **Zastosuj mechanizm zarządzania prawami do wiadomości z**, a następnie wybierz skonfigurowany szablon **Kierownicy**.

    -   Dodaj wyjątek **NCHR** (skrót od „Niechroniona”) lub wpisz własny tekst określający wyjątek, aby uwzględnić go w temacie.

    -   Upewnij się, że dla reguły skonfigurowano opcję **Wymuś**.

## Instrukcje w dokumentacji użytkownika
Jeśli nie zamierzasz przekazywać instrukcji związanych z określaniem **wyjątku NCHR** lub własnego tekstu określającego wyjątek w temacie wiadomości e-mail, to ten scenariusz nie obejmuje udostępniania użytkownikom żadnych procedur, ponieważ ochrona wiadomości e-mail wysyłanych między członkami kadry kierowniczej nie wymaga od nich podejmowania dodatkowych czynności. Wiadomości e-mail i załączniki są automatycznie chronione, tak że tylko członkowie grupy Kierownicy mają do nich dostęp.

Warto jednak poinformować kadrę kierowniczą i dział pomocy technicznej o automatycznej ochronie tych wiadomości oraz o ewentualnych ograniczeniach dotyczących korzystania z nich. Na przykład jeśli te wiadomości e-mail lub załączniki zostaną później przesłane do innych osób, nie zostaną przez nie odczytane. W przypadku skonfigurowania wyjątku NCHR (lub równoważnego wyjątku dotyczącego braku ochrony) upewnij się, że dział pomocy technicznej wie o tej konfiguracji, tak aby członkowie kadry kierowniczej mogli sami wyłączać regułę ochrony bez podejmowania czynności przez administratora programu Exchange.

Skorzystaj z poniższego szablonu i skopiuj to zawiadomienie do wiadomości dla użytkowników końcowych, wprowadzając następujące zmiany, aby odzwierciedlić charakter lokalnego środowiska:

1.  Zastąp wystąpienia parametru *&lt;nazwa organizacji&gt;* nazwą swojej organizacji.

2.  W przypadku podania własnego tekstu określającego wyjątek wprowadź odpowiednie zmiany wartości tekstowej oraz zmodyfikuj zawartość obszaru wyjaśnienia.

3.  Zastąp parametr *&lt;domena_poczty_e-mail&gt;* nazwą domeny poczty e-mail w swojej organizacji.

4.  Zastąp parametr *&lt;dane kontaktowe&gt;* instrukcjami dla użytkowników dotyczącymi kontaktowania się z działem pomocy technicznej, na przykład podaj link do witryny internetowej lub adres e-mail albo numer telefonu.

5.  Wprowadź dodatkowe zmiany, które chcesz uwzględnić w tym powiadomieniu, a następnie wyślij je do odpowiednich użytkowników.

W przykładowej dokumentacji przedstawiono, jak może wyglądać odpowiednio dostosowane zawiadomienie, które zobaczą użytkownicy.

![Szablon dokumentacji użytkownika na potrzeby szybkiego wdrażania usługi Azure RMS](../media/AzRMS_UsersBanner.png)

### Zawiadomienie działu IT: wiadomości e-mail wysyłane przez członków kadry kierowniczej w firmie &lt;nazwa organizacji&gt; są teraz automatycznie chronione.
Od tej pory wszystkie wiadomości e-mail oraz załączniki wysyłane do innych członków kadry kierowniczej w firmie &lt;nazwa organizacji&gt; będą automatycznie chronione. Tylko inni członkowie kierownictwa firmy będą mogli je odczytywać, drukować, kopiować itd. To ograniczenie obowiązuje również w przypadku zapisania załączników lub przesłania wiadomości e-mail do innych użytkowników. Wprowadzona ochrona ma zapobiegać utracie poufnych i wrażliwych informacji.

Warto pamiętać o tym, że w przypadku konieczności odczytania i zmodyfikowania tych informacji przez osoby, które nie należą do kierownictwa firmy &lt;nazwa organizacji&gt;, należy je wysyłać w osobnych wiadomościach e-mail. Można również wyłączyć automatyczną ochronę, wpisując tekst **NCHR** (skrót od „Niechroniona”) w dowolnym miejscu tematu wiadomości e-mail.

Wysyłając wiadomość z poufnymi informacjami firmy do innego członka kadry kierowniczej w firmie &lt;nazwa organizacji&gt;, należy pamiętać o używaniu służbowych adresów e-mail (*imię_nazwisko*@&lt;domena_poczty_e-mail&gt;) zamiast adresów prywatnych.

**Potrzebujesz pomocy?**

-   Skontaktuj się z działem pomocy technicznej: &lt;dane kontaktowe&gt;

### Przykładowa dokumentacja użytkownika
![Przykładowa dokumentacja użytkownika na potrzeby szybkiego wdrażania usługi Azure RMS](../media/AzRMS_ExampleBanner.png)

#### Zawiadomienie działu IT: wiadomości e-mail wysyłane przez członków kadry kierowniczej w firmie VanArsdel są teraz automatycznie chronione
Od tej pory wszystkie wiadomości e-mail oraz załączniki wysyłane do innych członków kadry kierowniczej w firmie VanArsdel będą automatycznie chronione. Tylko inni członkowie kierownictwa firmy będą mogli je odczytywać, drukować, kopiować itd. To ograniczenie obowiązuje również w przypadku zapisania załączników lub przesłania wiadomości e-mail do innych użytkowników. Wprowadzona ochrona ma zapobiegać utracie poufnych i wrażliwych informacji.

Warto pamiętać o tym, że w przypadku konieczności odczytania i zmodyfikowania tych informacji przez osoby, które nie należą do kierownictwa firmy VanArsdel, należy je wysyłać w osobnych wiadomościach e-mail. Można również wyłączyć automatyczną ochronę, wpisując tekst **NCHR** (skrót od „Niechroniona”) w dowolnym miejscu tematu wiadomości e-mail.

Wysyłając wiadomość z poufnymi informacjami firmy do innego członka kadry kierowniczej w firmie VanArsdel, należy pamiętać o używaniu służbowych adresów e-mail (*imię_nazwisko*@vanarsdelltd.com) zamiast adresów prywatnych.

**Potrzebujesz pomocy?**

-   Skontaktuj się z działem pomocy technicznej: pomoc_techniczna@vanarsdelltd.com




<!--HONumber=Jul16_HO3-->


