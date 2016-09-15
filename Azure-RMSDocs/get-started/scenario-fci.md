---
title: "Scenariusz — ochrona plików w udziale serwera plików | Azure RMS"
description: 
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 05/20/2016
ms.topic: get-started-article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 283c7db3-5730-439e-a215-40a1088ed506
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 332e102cb27854314b93a71bfeae82a95c9a7812
ms.openlocfilehash: c16098a2d0fe41748280704716a2eeef8921a6fa


---

# Scenariusz — ochrona plików w udziale serwera plików

*Dotyczy usług: Azure Rights Management, Office 365*

W tym scenariuszu i dodatkowej dokumentacji użytkownika usługa Azure Rights Management jest używana w celu zastosowania zbiorczej ochrony wszystkich plików wybranych na serwerze plików. Dzięki temu tylko pracownicy danej organizacji będą mogli uzyskiwać do nich dostęp, nawet jeśli pliki zostaną skopiowane i zapisane w magazynie niekontrolowanym przez dział IT albo wysłane do innych osób pocztą e-mail.

W tych instrukcjach jest stosowany jeden z domyślnych szablonów, który ogranicza dostęp do wszystkich pracowników z dowolnymi prawami do użytkowania. W razie potrzeby można jednak bardziej ograniczyć prawa dostępu i użytkowania, konfigurując szablon niestandardowy, zamiast używać szablonu domyślnego.

Podane tu instrukcje mają zastosowanie w następujących okolicznościach:

-   Chcesz objąć ochroną wszystkie typy plików, nie tylko pliki pakietu Office. Pliki, które nie mogą być chronione w sposób natywny przez usługę Azure RMS, zostaną objęte ochroną ogólną.

-   Ochrona zostanie włączona dla wszystkich plików (w tym podfolderów) w określonej ścieżce.

-   Ochrona wszystkich plików jest ponownie stosowana zgodnie z harmonogramem. Dzięki temu można mieć pewność, że zmiany szablonów zasad praw dostępu będą stosowane do chronionych plików.

## Instrukcje dotyczące wdrażania
![Instrukcje dla administratora dotyczące szybkiego wdrażania usługi Azure RMS](../media/AzRMS_AdminBanner.png)

Przed przejściem do części dotyczącej dokumentacji użytkownika należy upewnić się, że zostały spełnione poniższe wymagania, i wykonać instrukcje zawarte w procedurach pomocniczych.

## Wymagania dotyczące tego scenariusza
Aby wykonać instrukcje dotyczące tego scenariusza, należy spełnić następujące wymagania:

|Wymaganie|Jeśli potrzebujesz dodatkowych informacji|
|---------------|--------------------------------|
|Usługa Azure Rights Management została aktywowana.|[Aktywacja usługi Azure Rights Management](https://technet.microsoft.com/library/jj658941.aspx)|
|Lokalne konta użytkowników usługi Active Directory, w tym ich adresy e-mail, zsynchronizowano z usługą Azure Active Directory lub Office 365. Jest to wymagane dla wszystkich użytkowników, którzy mogą wymagać dostępu do plików po objęciu ich ochroną przez infrastrukturę FCI i usługę Azure Rights Management.|[Przygotowanie do wdrożenia usługi Azure Rights Management](https://technet.microsoft.com/library/jj585029.aspx)|
|Jeden z poniższych programów:<br /><br />– Aby użyć szablonu domyślnego dla wszystkich użytkowników: nie zarchiwizowano szablonu domyślnego &lt;nazwa organizacji&gt; — poufne.<br /><br />– Aby użyć szablonu niestandardowego dla wybranych użytkowników: utworzono i opublikowano ten szablon niestandardowy.|[Konfigurowanie szablonów niestandardowych usługi Azure Rights Management](https://technet.microsoft.com/library/dn642472.aspx)|
|Aplikacja do tworzenia i przetwarzania dokumentów chronionych usługami Rights Management została wdrożona na komputerach użytkowników z systemem Windows.|[Automatyczne wdrażanie aplikacji do udostępniania usługi Microsoft Rights Management](https://technet.microsoft.com/library/dn339003%28v=ws.10%29.aspx)|
|Pobrano narzędzie ochrony usługi RMS i skonfigurowano wymagania wstępne dotyczące usługi Azure RMS.|Instrukcje dotyczące pobierania narzędzia i wymagań wstępnych: [RMS Protection Cmdlets](https://msdn.microsoft.com/library/mt433195.aspx) (Polecenia cmdlet dotyczące ochrony RMS)<br /><br />Aby skonfigurować dodatkowe wymagania wstępne dotyczące usługi Azure RMS, takie jak konto główne usługi: [about_RMSProtection_AzureRMS](https://msdn.microsoft.com/library/mt433202.aspx)|

### Konfigurowanie serwera plików w celu objęcia ochroną wszystkich plików za pomocą usługi Azure RMS i Menedżera zasobów serwera plików przy użyciu infrastruktury klasyfikacji plików

1.  Uruchom sesję programu Windows PowerShell. Nie musisz uruchamiać tej sesji jako administrator.

2.  Uwierzytelnij się w usłudze Azure RMS:

    ```
    Set-RMSServerAuthentication
    ```
    Po wyświetleniu monitu podaj wartości konta głównego usługi utworzonego jako warunek wstępny na potrzeby poleceń cmdlet ochrony przy użyciu usługi RMS.

3.  Uruchom następujące polecenie, aby określić identyfikator szablonu, który będzie używany do ochrony plików:

    ```
    Get-RMSTemplate
    ```
    Aby użyć domyślnego szablonu, który ogranicza dostęp do wszystkich pracowników z dowolnymi prawami użytkowania, wyszukaj nazwę szablonu **&lt;nazwa organizacji&gt; — poufne**, np. **VanArsdel, Ltd — poufne**.

4.  Dokładne instrukcje można znaleźć w temacie [RMS Protection with Windows Server File Classification Infrastructure (FCI)](https://technet.microsoft.com/library/mt601315%28v=ws.10%29.aspx) (Ochrona za pomocą usługi RMS przy użyciu infrastruktury klasyfikacji plików (FCI)).

    Instrukcje te obejmują skrypt programu Windows PowerShell wybierany do uruchamiania jako niestandardowy plik wykonywalny w Menedżerze zasobów serwera plików. Instrukcje umożliwiają także sprawdzanie, czy pliki są chronione przez usługę Azure Rights Management.

## Instrukcje w dokumentacji użytkownika
Jeśli ochrona została włączona tylko dla plików pakietu Office, być może nie trzeba udostępniać użytkownikom żadnych instrukcji dotyczących chronionych plików. Otwieranie tych dokumentów przez upoważnionych użytkowników w pakiecie Office będzie odbywać się w zwykły sposób, z tą jedyną różnicą, że użytkownicy mogą zostać poproszeni o uwierzytelnienie oraz że prawdopodobnie w górnej części dokumentu zostanie wyświetlony pasek informujący o objęciu tego dokumentu ochroną.

Jeśli chronione pliki mają rozszerzenie nazwy **.ppdf** lub zawierają chroniony tekst bądź obraz (np. nazwa pliku ma rozszerzenie **.ptxt** lub **.pjpg**), są dostępne tylko do odczytu i nie można ich edytować. Użytkownicy mogą je wyświetlać w przeglądarce aplikacji RMS sharing, która w przypadku tych typów plików jest ładowana automatycznie. Te pliki są chronione natywnie przez usługę Azure RMS, co oznacza, że są stosowane wszystkie ustawienia zasad z wybranego szablonu z wyjątkiem praw użytkowania, ponieważ sam plik jest tylko do odczytu. Jeśli nie masz pewności, że będziesz chronić te typy plików, jest mało prawdopodobne, że w przypadku tego scenariusza będą potrzebne instrukcje dla użytkownika. Warto jednak uprzedzić dział pomocy technicznej, że może zaistnieć potrzeba wyjaśnienia użytkownikom, dlaczego nie można edytować tych plików.

Jeśli chronione pliki mają rozszerzenie nazwy **.pfile**, użytkownicy mogą je wyświetlać, ale jeśli chcą je edytować i zapisywać swoje zmiany, muszą podczas zapisywania użyć oryginalnej nazwy pliku (usuwając rozszerzenie nazwy pliku .pfile). Pliki te są objęte ochroną ogólną przez usługę Azure RMS i nie można wymuszać praw użytkowania z zastosowanego szablonu. Oznacza to, że zapisanie pliku z nową nazwą spowoduje wyłączenie jego ochrony. W tym scenariuszu należy udostępnić użytkownikom instrukcje.

Korzystając z poniższego szablonu, skopiuj i wklej instrukcje dla użytkowników końcowych, aby wiedzieli, jak edytować pliki objęte ochroną ogólną. Wprowadź poniższe zmiany, używając informacji z własnego środowiska pracy:

-   Zastąp wartości *&lt;typ pliku&gt;* i *&lt;udział serwera plików&gt;* typem pliku, który zostanie objęty ochroną ogólną, i nazwą udziału serwera plików.

-   Zastąp wartość *&lt;nazwa organizacji&gt;* nazwą swojej organizacji w postaci, w której jest wyświetlana w domyślnych szablonach usługi Azure Rights Management.

-   Zastąp wartość *&lt;nazwa organizacji&gt;* nazwą swojej firmy.

-   Zastąp wartość *&lt;Instrukcje dotyczące zapisywania pliku i usuwania rozszerzenia nazwy pliku .pfile&gt;* instrukcjami powiązanymi z określoną aplikacją, dotyczącymi danego typu pliku.

-   Zastąp dane kontaktowe instrukcjami dla użytkowników dotyczącymi sposobu kontaktowania się z działem pomocy technicznej, na przykład podaj link do witryny sieci Web, adres e-mail lub numer telefonu.

-   Wprowadź wszelkie dodatkowe zmiany, które chcesz uwzględnić w tym zestawie instrukcji, a następnie wyślij go do wybranych użytkowników.

W przykładowej dokumentacji przedstawiono potencjalny wygląd odpowiednio dostosowanych instrukcji, które zobaczą użytkownicy.

![Szablon dokumentacji użytkownika na potrzeby szybkiego wdrażania usługi Azure RMS](../media/AzRMS_UsersBanner.png)

### Jak edytować pliki typu &lt;typ pliku&gt; z poziomu udziału &lt;udział serwera plików&gt;

1.  Kliknij dwukrotnie plik, aby go otworzyć. Może zostać wyświetlony monit o podanie poświadczeń.

2.  Zostanie wyświetlone okno dialogowe **pliku chronionego** aplikacji do tworzenia i przetwarzania dokumentów chronionych usługami Microsoft Rights Management. Wskazuje ono, że należy przestrzegać uprawnień szablonu **&lt;nazwa organizacji&gt; — poufne**. Oznacza to, że nie należy udostępniać tego dokumentu innym osobom, jeśli nie pracują w firmie &lt;nazwa organizacji&gt;.

3.  Kliknij pozycję **Otwórz**.

4.  Aby edytować plik, najpierw go zapisz i usuń rozszerzenie nazwy .pfile:

    -   &lt;Instrukcje dotyczące zapisywania pliku i usuwania rozszerzenia nazwy pliku .pfile&gt;

5.  Teraz możesz edytować i zapisać plik w zwykły sposób.

Okresowo ochrona pliku będzie ponownie stosowana, co spowoduje dodanie rozszerzenia .pfile do jego nazwy. W takiej sytuacji należy powtórzyć te kroki.

**Potrzebujesz pomocy?**

-   Dodatkowe informacje:

    -   [Wyświetlanie i używanie chronionych plików](https://technet.microsoft.com/library/dn574741%28v=ws.10%29)

-   Skontaktuj się z działem pomocy technicznej:

    -   *&lt;dane kontaktowe&gt;*

### Przykładowa niestandardowa dokumentacja użytkownika
![Przykładowa dokumentacja użytkownika na potrzeby szybkiego wdrażania usługi Azure RMS](../media/AzRMS_ExampleBanner.png)

#### Jak edytować rysunki CAD z poziomu udziału ProjectNextGen

1.  Kliknij dwukrotnie plik, aby go otworzyć. Może zostać wyświetlony monit o podanie poświadczeń.

2.  Zostanie wyświetlone okno dialogowe **pliku chronionego** aplikacji do tworzenia i przetwarzania dokumentów chronionych usługami Microsoft Rights Management Wskazuje ono, że należy przestrzegać uprawnień szablonu **VanArsdel, Ltd — poufne**. Oznacza to, że nie należy udostępniać tego dokumentu innym osobom, jeśli nie pracują w firmie VanArsdel, Ltd.

3.  Kliknij pozycję **Otwórz**.

4.  Aby edytować plik, najpierw go zapisz i usuń rozszerzenie nazwy .pfile:

    -   **Plik** &gt; **Zapisz jako**

    -   Usuń rozszerzenie **.pfile** znajdujące się na końcu nazwy pliku, a następnie kliknij przycisk **OK**.

5.  Teraz możesz edytować i zapisać plik w zwykły sposób.

Okresowo ochrona pliku będzie ponownie stosowana, co spowoduje dodanie rozszerzenia .pfile do jego nazwy. W takiej sytuacji należy powtórzyć te kroki.

**Potrzebujesz pomocy?**

-   Dodatkowe informacje:

    -   [Wyświetlanie i używanie chronionych plików](https://technet.microsoft.com/library/dn574741%28v=ws.10%29)

-   Skontaktuj się z działem pomocy technicznej: pomoc_techniczna@vanarsdelltd.com




<!--HONumber=Jul16_HO3-->


