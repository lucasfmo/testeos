---
title: "Zmiana uprawnień do plików chronionych przez usługę Rights Management | Azure RMS"
description: "Gdy plik jest chroniony przez usługę Rights Management, można zmienić uprawnienia do niego, ponownie włączając jego ochronę, a następnie określając wszystkich użytkowników, którzy muszą mieć dostęp do niego, oraz przysługujące im uprawnienia."
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 08/03/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 5ac121b3-d7a0-40e4-8fe7-90bf4cf796f1
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ba029e48b540fda8474eba83322c531ff3daa7b3
ms.openlocfilehash: a123338e34a8c4585a01782a473a400ecb58f166


---

# Zmiana uprawnień do plików chronionych przez usługę Rights Management

*Dotyczy: Active Directory Rights Management, Azure Rights Management, Windows 10, Windows 7 z dodatkiem SP1, Windows 8, Windows 8.1*

Gdy plik jest chroniony przez usługę Rights Management, można zmienić uprawnienia do niego, ponownie włączając jego ochronę, a następnie określając wszystkich użytkowników, którzy muszą mieć dostęp do niego, oraz przysługujące im uprawnienia.

> [!IMPORTANT]
> Nie jest to zmiana przyrostowa, ale całkowite zastąpienie. Oznacza to, że plik jest chroniony na nowo przy użyciu pełnego zestawu uprawnień wybranych przez użytkownika.
> 
>  Na przykład jeśli plik jest chroniony tak, aby mogli go otworzyć tylko pracownicy działu marketingu, ale chcemy nadać uprawnienia do otwarcia tego pliku również pracownikom działu sprzedaży, należy ponownie włączyć ochronę pliku, tak aby mogli go otworzyć pracownicy działu sprzedaży i działu marketingu.
>
> Podobnie jeśli chcesz nadać lub cofnąć uprawnienie, nie możesz po prostu określić, które uprawnienie ma zostać nadane lub cofnięte, lecz musisz podać wszystkie uprawnienia, które mają mieć określone osoby.

Jeśli jesteś właścicielem pliku, dla którego chcesz na nowo włączyć ochronę (na przykład plik był pierwotnie chroniony za pomocą aplikacji do udostępniania), będziesz automatycznie mieć uprawnienia do ponownego włączenia ochrony pliku. Jeśli nie jesteś właścicielem, możesz mieć uprawnienia do ponownego włączania ochrony pliku lub nie mieć ich, w zależności od uprawnień, które obecnie ma chroniony plik. W celu ponownego włączenia ochrony pliku konieczne jest [prawo użytkowania Pełna kontrola](../deploy-use/configure-usage-rights.md#usage-rights-and-descriptions).

Na przykład jeśli ktoś inny włączył ochronę pliku za pomocą aplikacji do udostępniania usługi Rights Management oraz podał grupę, do której należysz, oraz określił niestandardowe uprawnienie **Współwłaściciel**, masz uprawnienia do ponownego włączenia ochrony pliku. Jednakże jeśli ta osoba nie podała Ciebie ani grupy, do której należysz, lub wybrała opcję **Recenzent — wyświetlanie i edytowanie** albo szablon, który nie zezwala Ci na usuwanie uprawnień, nie masz uprawnienia do ponownego włączenia ochrony pliku. Najprostszym sposobem sprawdzenia tego jest próba ponownego włączenia ochrony pliku.

Jeśli chcesz całkowicie usunąć wszystkie uprawnienia, aby plik nie był już chroniony, zobacz [Usuwanie ochrony pliku](sharing-app-remove-protection.md).

## Aby ponownie włączyć ochronę pliku w miejscu

1.  W Eksploratorze plików wybierz plik, który ma być chroniony. Kliknij prawym przyciskiem myszy, wybierz pozycję **Chroń za pomocą usługi RMS**, a następnie wybierz pozycję **Włącz ochronę miejscową**. Na przykład:

    ![Opcja menu Ochrona miejscowa](../media/ADRMS_MSRMSApp_SP_CompanyDefined.png)

    > [!NOTE]
    > Jeśli opcja **Chroń za pomocą usługi RMS** nie jest wyświetlana, możliwe, że aplikacja RMS sharing nie jest zainstalowana na danym komputerze albo trzeba ponownie uruchomić komputer w celu ukończenia instalacji. Aby uzyskać więcej informacji o sposobie instalowania aplikacji do udostępniania usługi RMS, zobacz [Pobieranie i instalowanie aplikacji do udostępniania usługi Microsoft Rights Management](install-sharing-app.md).

2.  Wykonaj jedną z następujących czynności:

    -   Wybierz szablon zasad: są to wstępnie zdefiniowane uprawnienia, które zwykle ograniczają dostęp i użycie do osób w danej organizacji. Jeśli na przykład nazwa organizacji to „Contoso, Ltd”, może zostać wyświetlona pozycja **Contoso, Ltd — tylko wyświetlanie poufne**. Jeśli po raz pierwszy włączasz ochronę pliku na tym komputerze, najpierw musisz wybrać pozycję **Ochrona zdefiniowana przez firmę** w celu pobrania szablonów.

        Przy następnym kliknięciu opcji **Włącz ochronę miejscową**, zostanie wyświetlonych do 10 szablonów do wyboru. Jeśli dostępnych jest ponad 10 szablonów i odpowiedni szablon nie jest wyświetlany, kliknij pozycję **Ochrona zdefiniowana przez firmę** w celu pobrania i wyświetlenia wszystkich szablonów.

        Podczas wybierania szablonu zasad można zdecydować się na ochronę wielu plików i folderu. Wybranie folderu powoduje ochronę wszystkich plików znajdujących się w tym folderze, ale nowe pliki w nim tworzone nie będą już automatycznie chronione.

    -   Wybierz opcję **Uprawnienia niestandardowe**: wybierz tę opcję, jeśli szablony nie umożliwiają ustawienia odpowiedniego poziomu ochrony lub jeśli chcesz jawnie ustawić opcje ochrony. Określ odpowiednie opcje dla tego pliku w oknie dialogowym [Dodawanie ochrony](sharing-app-dialog-box.md), a następnie kliknij przycisk **Zastosuj**.

3. Jeśli nie masz uprawnień do ponownego włączenia ochrony pliku, zobaczysz komunikat **Nie można ochronić zawartości** zawierający adres e-mail osoby, z którą należy się skontaktować (właściciela dokumentu) w celu zmiany Twoich uprawnień.

    Jeśli masz uprawnienia do ponownego włączenia ochrony pliku, na chwilę może zostać wyświetlone okno dialogowe informujące, że plik jest chroniony, po czym nastąpi powrót do Eksploratora plików. Wybrane pliki są teraz chronione z uwzględnieniem zmienionych uprawnień. 

> [!NOTE]
> Zanim będzie można ponownie włączyć ochronę pliku, usługa RMS musi najpierw potwierdzić, że masz uprawnienia do tej czynności (sprawdzana jest nazwa użytkownika i hasło). W niektórych sytuacjach te dane są buforowane, w związku z czym monit o podanie poświadczeń nie zostanie wyświetlony. W pozostałych przypadkach jest wyświetlany monit o podanie poświadczeń.
>
> Jeśli Twoja organizacja nie korzysta z usługi Azure Rights Management (Azure RMS) ani usług AD RMS, możesz poprosić o utworzenie bezpłatnego konta z wykorzystaniem Twoich poświadczeń, co umożliwi Ci używanie plików chronionych za pomocą usług RMS:
>
> -   Aby poprosić o utworzenie konta, kliknij link [usług RMS dla użytkowników indywidualnych](http://go.microsoft.com/fwlink/?LinkId=309469).
>
>     Podczas tworzenia konta użyj swojego służbowego adresu e-mail, a nie adresu prywatnego. Jeśli tworzysz konto w związku z otrzymaniem chronionego załącznika pocztą e-mail, użyj tego samego adresu e-mail, który został użyty przez nadawcę do wysłania tej wiadomości e-mail do Ciebie.
> -   Aby uzyskać więcej informacji, zobacz [Usługa RMS dla użytkowników indywidualnych i usługa Azure Rights Management](../understand-explore/rms-for-individuals.md).

## Aby ponownie włączyć ochronę pliku wysłanego pocztą e-mail

Jeśli chcesz zmienić uprawnienia do pliku wysłanego pocztą e-mail:

- **Aby umożliwić większej liczbie użytkowników odczytanie pliku**: wyślij plik pocztą e-mail, zgodnie z instrukcjami zawartymi w temacie [Ochrona pliku udostępnionego pocztą e-mail](sharing-app-protect-by-email.md).

- **Aby zmienić uprawnienia do pliku**: wyślij ponownie plik pocztą e-mail, postępując zgodnie z instrukcjami w temacie [Ochrona pliku udostępnionego pocztą e-mail](sharing-app-protect-by-email.md), i wybierz dla niego nowe uprawnienia. 

    Ponieważ nie można usunąć poprzednich uprawnień do pliku uprzednio wysłanego pocztą e-mail, lecz jedynie zastąpić je w nowej wersji, rozważ odwołanie pliku wcześniej wysłanego pocztą e-mail w celu uniemożliwienia adresatom otwarcia wysłanej wersji dokumentu. Odwoływanie przydaje się, jeśli chcesz nadać bardziej restrykcyjne uprawnienia (na przykład usunąć osoby, które nie powinny mieć dostępu do pliku lub nie powinny już mieć możliwości jego edytowania).

    Aby odwołać plik wysłany pocztą e-mail, zobacz temat [Śledzenie i odwoływanie dokumentów](sharing-app-track-revoke.md).


## Przykłady i inne instrukcje
Aby uzyskać instrukcje i przykłady dotyczące korzystania z aplikacji do udostępniania usługi Rights Management, zapoznaj się z następującymi sekcjami podręcznika użytkownika aplikacji do udostępniania usługi Rights Management:

-   [Przykłady korzystania z aplikacji RMS sharing](sharing-app-user-guide.md#examples-for-using-the-rms-sharing-application)

-   [Co chcesz zrobić?](sharing-app-user-guide.md#what-do-you-want-to-do)

## Zobacz też
[Podręcznik użytkownika aplikacji do udostępniania usługi Rights Management](sharing-app-user-guide.md)



<!--HONumber=Aug16_HO1-->


