---
title: "Ochrona za pomocą usług RMS z użyciem infrastruktury klasyfikacji plików (FCI, File Classification Infrastructure) w systemie Windows Server | Azure RMS"
description: 
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 06/14/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 9aa693db-9727-4284-9f64-867681e114c9
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 1fc1835b60c4c75b81f106011849940ba2e77164
ms.openlocfilehash: afb00e010df25dea5f3c3cad23824f773de59b18


---

# Ochrona za pomocą usług RMS z użyciem infrastruktury klasyfikacji plików (FCI, File Classification Infrastructure) w systemie Windows Server

*Dotyczy: Azure Rights Management, Windows Server 2012, Windows Server 2012 R2*

Ten artykuł zawiera skrypt umożliwiający użycie klienta Rights Management (RMS) z narzędziem RMS Protection Tool w celu skonfigurowania Menedżera zasobów serwera plików oraz infrastruktury klasyfikacji plików (FCI), a także odpowiednie instrukcje.

To rozwiązanie pozwala automatycznie chronić pliki w folderze na serwerze plików z systemem Windows Server lub pliki, które spełniają określone kryteria. Na przykład pliki, które zostały sklasyfikowane jako zawierające informacje poufne lub szczególnie chronione. To rozwiązanie wymaga usług Azure Rights Management (Azure RMS), aby chronić pliki, więc konieczne jest wdrożenie tej technologii w organizacji.

> [!NOTE]
> Mimo że usługi Azure RMS obejmują [łącznik](../deploy-use/deploy-rms-connector.md), który obsługuje infrastrukturę klasyfikacji plików, to rozwiązanie obsługuje wyłącznie ochronę natywną, np. plików pakietu Office.
> 
> Aby obsługiwać wszystkie typy plików za pomocą infrastruktury klasyfikacji plików, należy użyć modułu **ochrony usług RMS** programu Windows PowerShell, zgodnie z opisem w tym artykule. Polecenia cmdlet modułu ochrony usług RMS, takie jak aplikacja do udostępniania usług RMS, obsługują zarówno ochronę ogólną, jak i natywną, co oznacza, że wszystkie pliki mogą być chronione. Aby uzyskać więcej informacji na temat różnych poziomów ochrony, zobacz sekcję [Poziomy ochrony — natywny i ogólny](sharing-app-admin-guide-technical.md#levels-of-protection-native-and-generic) w [Przewodniku administratora aplikacji do udostępniania usługi Rights Management](sharing-app-admin-guide.md).

Poniższe instrukcje dotyczą systemu Windows Server 2012 R2 lub Windows Server 2012. W przypadku korzystania z innych obsługiwanych wersji systemu Windows może okazać się konieczne dostosowanie niektórych kroków z powodu różnic między używaną wersją systemu operacyjnego i wersją opisaną w tym artykule.

## Wymagania wstępne dotyczące ochrony za pomocą usług Azure RMS z użyciem infrastruktury FCI w systemie Windows Server
Wymagania wstępne dotyczące tych instrukcji:

-   Na każdym serwerze plików, na którym będzie uruchamiany Menedżer zasobów plików z infrastrukturą klasyfikacji plików:

    -   Zainstalowano Menedżer zasobów serwera plików jako jedną z usług ról dla roli Usługi plików.

    -   Zidentyfikowano lokalny folder zawierający pliki, które mają być chronione przez usługę Rights Management. Na przykład C:\FileShare.

    -   Zainstalowano narzędzie RMS Protection Tool i spełniono wymagania wstępne narzędzia (na przykład klienta RMS) i usług Azure RMS (takie jak konto główne usługi). Aby uzyskać więcej informacji, zobacz [Polecenia cmdlet narzędzia RMS Protection](https://msdn.microsoft.com/library/azure/mt433195.aspx).

    -   Aby zmienić poziom ochrony za pomocą usług RMS (natywny lub ogólny) dla określonych rozszerzeń nazw plików, należy edytować rejestr zgodnie z opisem na stronie [Konfiguracja interfejsu API plików](https://msdn.microsoft.com/library/dn197834%28v=vs.85%29.aspx).

    -   Masz połączenie z Internetem z ustawieniami komputera skonfigurowanymi w razie potrzeby dla serwera proxy. Na przykład: `netsh winhttp import proxy source=ie`

-   Skonfigurowano dodatkowe wymagania wstępne wdrożenia usługi Azure Rights Management, zgodnie z opisem w temacie [about_RMSProtection_AzureRMS](https://msdn.microsoft.com/library/mt433202.aspx). W szczególności do usługi Azure RMS należy dołączyć następujące wartości, korzystając z nazwy głównej usługi:

    -   Identyfikator BposTenantId

    -   Identyfikator AppPrincipalId

    -   Klucz symetryczny

-   Zsynchronizowano lokalne konta użytkowników usługi Active Directory, w tym ich adresy e-mail, z usługą Azure Active Directory lub Office 365. Jest to wymagane dla wszystkich użytkowników, którzy mogą wymagać dostępu do plików, które zostaną objęte ochroną przez infrastrukturę FCI i usługę Azure RMS. W przypadku pominięcia tego kroku (na przykład w środowisku testowym) dostęp użytkowników do tych plików może zostać zablokowany. Aby uzyskać więcej informacji na temat tej konfiguracji konta, zobacz [Preparing for Azure Rights Management](../plan-design/prepare.md) (Przygotowywanie do wdrożenia usługi Azure Rights Management).

-   Zidentyfikowano szablon usługi Rights Management, który ma zostać użyty i który będzie chronić pliki. Upewnij się, że znasz identyfikator tego szablonu, używając polecenia cmdlet [Get-RMSTemplate](https://msdn.microsoft.com/library/azure/mt433197.aspx).

## Instrukcje konfiguracji infrastruktury FCI Menedżera zasobów serwera plików na potrzeby ochrony za pomocą usług Azure RMS
Wykonaj te instrukcje, aby automatycznie chronić wszystkie pliki w folderze przy użyciu skryptu programu Windows PowerShell jako zadania niestandardowego. Wykonaj te procedury w następującej kolejności:

1.  Zapisz skrypt programu Windows PowerShell.

2.  Utwórz właściwość klasyfikacji dla usługi Rights Management (RMS).

3.  Utwórz regułę klasyfikacji (Klasyfikuj do ochrony za pomocą usługi RMS).

4.  Skonfiguruj harmonogram klasyfikacji.

5.  Utwórz niestandardowe zadanie zarządzania plikami (Chroń pliki za pomocą usługi RMS).

6.  Przetestuj konfigurację, ręcznie uruchamiając regułę i zadanie.

Po wykonaniu tych instrukcji wszystkie pliki w wybranym folderze zostaną sklasyfikowane z niestandardowymi właściwościami usługi RMS i będą chronione za pomocą usługi Rights Management. Na potrzeby bardziej złożonej konfiguracji selektywnej ochrony plików można utworzyć inną właściwość i regułę klasyfikacji zadania zarządzania plikami chroniącego tylko wybrane pliki, a następnie użyć jej.

### Zapisz skrypt programu Windows PowerShell.

1.  Skopiuj zawartość [skryptu programu Windows PowerShell](fci-script.md) na potrzeby ochrony za pomocą usług Azure RMS przy użyciu Menedżera zasobów serwera plików. Wklej zawartość skryptu i nazwij plik **Ochrona-RMS-FCI.ps1** na własnym komputerze.

2.  Przejrzyj skrypt i wprowadź następujące zmiany:

    -   Wyszukaj następujący ciąg i zastąp go własnym identyfikatorem AppPrincipalId, który jest używany z poleceniem cmdlet [Set-RMSServerAuthentication](https://msdn.microsoft.com/library/mt433199.aspx), aby nawiązać połączenie z usługami Azure RMS:

        ```
        <enter your AppPrincipalId here>
        ```
        Przykładowy skrypt może wyglądać następująco:

        `[Parameter(Mandatory = $false)]`

        `[Parameter(Mandatory = $false)]             [string]$AppPrincipalId = "b5e3f76a-b5c2-4c96-a594-a0807f65bba4",`

    -   Wyszukaj następujący ciąg i zastąp go własnym kluczem symetrycznym, który jest używany z poleceniem cmdlet [Set-RMSServerAuthentication](https://msdn.microsoft.com/library/mt433199.aspx), aby nawiązać połączenie z usługami Azure RMS:

        ```
        <enter your key here>
        ```
        Przykładowy skrypt może wyglądać następująco:

        `[Parameter(Mandatory = $false)]`

        `[string]$SymmetricKey = "zIeMu8zNJ6U377CLtppkhkbl4gjodmYSXUVwAO5ycgA="`

    -   Wyszukaj następujący ciąg i zastąp go własnym identyfikatorem BposTenantId (identyfikator dzierżawcy), który jest używany z poleceniem cmdlet [Set-RMSServerAuthentication](https://msdn.microsoft.com/library/mt433199.aspx), aby nawiązać połączenie z usługami Azure RMS:

        ```
        <enter your BposTenantId here>
        ```
        Przykładowy skrypt może wyglądać następująco:

        `[Parameter(Mandatory = $false)]`

        `[string]$BposTenantId = "23976bc6-dcd4-4173-9d96-dad1f48efd42",`

    -   Jeśli na serwerze jest zainstalowany system Windows Server 2012, trzeba będzie ręcznie załadować moduł RMSProtection na początku skryptu. Dodaj następujące polecenie (lub jego odpowiednik), jeśli folder Program Files znajduje się na dysku innym niż dysk C:

        ```
        Import-Module "C:\Program Files\WindowsPowerShell\Modules\RMSProtection\RMSProtection.dll"
        ```

3.  Podpisz skrypt. Jeśli nie podpiszesz skryptu (bezpieczniejsza opcja), należy skonfigurować program Windows PowerShell na serwerach, na których uruchomiono skrypt. Na przykład uruchom sesję programu Windows PowerShell, korzystając z opcji **Uruchom jako Administrator** i wpisz **Set-ExecutionPolicy RemoteSigned**. Jednak taka konfiguracja pozwala na uruchomienie wszystkich niepodpisanych skryptów przechowywanych na tym serwerze (mniej bezpieczna opcja).

    Aby uzyskać więcej informacji na temat podpisywania skryptów programu Windows PowerShell, zobacz artykuł [about_Signing](https://technet.microsoft.com/library/hh847874.aspx) w bibliotece dokumentacji programu PowerShell.

4.  Zapisz plik lokalnie na każdym serwerze plików, na którym będzie uruchamiany Menedżer zasobów plików z infrastrukturą klasyfikacji plików. Na przykład zapisz plik w katalogu **C:\RMS-Protection**. Zabezpiecz ten plik, używając uprawnień NTFS, aby nieautoryzowani użytkownicy nie mogli go zmodyfikować.

Teraz możesz rozpocząć konfigurowanie Menedżera zasobów serwera plików.

### Utwórz właściwość klasyfikacji dla usługi Rights Management (RMS).

-   W węźle Menedżer zasobów serwera plików w pozycji Zarządzanie klasyfikacją utwórz nową lokalną właściwość:

    -   **Nazwa**: Wpisz **RMS**.

    -   **Opis**: Wpisz **Ochrona za pomocą usługi Rights Management**.

    -   **Typ właściwości**: Wybierz **Tak/Nie**.

    -   **Wartość**: Wybierz **Tak**.

Teraz można utworzyć regułę klasyfikacji korzystającą z tej właściwości.

### Utwórz regułę klasyfikacji (Klasyfikuj do ochrony za pomocą usługi RMS).

-   Utwórz nową regułę klasyfikacji:

    -   Na karcie **Ogólne**:

        -   **Nazwa**: Wpisz **Klasyfikuj do ochrony za pomocą usługi RMS**.

        -   **Włączone**: Zachowaj ustawienie domyślne, czyli zaznaczenie tego pola wyboru.

        -   **Opis**: wpisz **Klasyfikuj wszystkie pliki w folderze &lt;nazwa folderu&gt; do ochrony za pomocą usługi Rights Management**.

            Zastąp *&lt;nazwę folderu&gt;* wybraną nazwą folderu. Na przykład **Klasyfikuj wszystkie pliki w folderze C:\FileShare do ochrony za pomocą usług Rights Management**.

        -   **Zakres**: Dodaj wybrany folder. Na przykład **C:\FileShare**.

            Nie zaznaczaj pól wyboru.

    -   Na karcie **Klasyfikacja**:

    -   **Metoda klasyfikacji**: Wybierz **Klasyfikator folderów**.

    -   Nazwa **Właściwości**: Wybierz **RMS**.

    -   **Wartość** właściwości: Wybierz **Tak**.

Chociaż zasady klasyfikacji można uruchomić ręcznie, dla trwających operacji ta reguła powinna być uruchamiana zgodnie z harmonogramem, dzięki czemu nowe pliki zostaną sklasyfikowane z właściwością usługi RMS.

### Skonfiguruj harmonogram klasyfikacji.

-   Na karcie **Automatyczna klasyfikacja**:

    -   **Włącz ustalony harmonogram**: Zaznacz to pole wyboru.

    -   Skonfiguruj harmonogram uruchamiania wszystkich reguł klasyfikacji, w tym naszej nowej reguły do klasyfikowania plików za pomocą właściwości usługi RMS.

    -   **Zezwalaj na ciągłą klasyfikację nowych plików**: Zaznacz to pole wyboru, aby nowe pliki zostały sklasyfikowane.

    -   Opcjonalnie: Wprowadź wszelkie potrzebne zmiany, takie jak konfigurowanie opcji raportów i powiadomień.

Po zakończeniu konfigurowania klasyfikacji można przejść do konfigurowania zadania zarządzania w celu zastosowania ochrony plików przy pomocy usługi RMS.

### Utwórz niestandardowe zadanie zarządzania plikami (Chroń pliki za pomocą usługi RMS).

-   W **Zadaniach zarządzania plikami** utwórz nowe zadanie zarządzania plikami:

    -   Na karcie **Ogólne**:

        -   **Nazwa zadania**: Wpisz **Chroń pliki za pomocą usługi RMS**

        -   Zachowaj zaznaczenie pola wyboru **Włącz**.

        -   **Opis**: Wpisz **Chroń pliki w folderze &lt;nazwa folderu&gt; za pomocą usługi Rights Management oraz szablon za pomocą skryptu Windows PowerShell.**

            Zastąp *&lt;nazwę folderu&gt;* wybraną nazwą folderu. Na przykład **Chroń pliki w folderze C:\FileShare za pomocą usługi Rights Management oraz szablon za pomocą skryptu Windows PowerShell.**

        -   **Zakres**: Zaznacz wybrany folder. Na przykład **C:\FileShare**.

            Nie zaznaczaj pól wyboru.

    -   Na karcie **Akcja**:

        -   **Typ**: Wybierz **Niestandardowe**

        -   **Plik wykonywalny**: Określ następujące ustawienia:

            ```
            C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe
            ```
            Jeśli system Windows nie znajduje się na dysku C:, należy zmodyfikować tę ścieżkę lub przejść do tego pliku.

        -   **Argument**: Określ następujące ustawienia, podając własne wartości &lt;ścieżki&gt; i &lt;identyfikatora szablonu&gt;:

            ```
            -Noprofile -Command "<path>\RMS-Protect-FCI.ps1 -File '[Source File Path]' -TemplateID <template GUID> -OwnerMail [Source File Owner Email]"
            ```
            Jeśli np. skrypt został skopiowany do katalogu C:\RMS-Protection, a identyfikator szablonu wskazanego na podstawie wymagań wstępnych to e6ee2481-26b9-45e5-b34a-f744eacd53b0, określ następujące ustawienia:

            `-Noprofile -Command "C:\RMS-Protection\RMS-Protect-FCI.ps1 -File '[Source File Path]' -TemplateID e6ee2481-26b9-45e5-b34a-f744eacd53b0 -OwnerMail [Source File Owner Email]"`

            W tym poleceniu zarówno **[Ścieżka pliku źródłowego]**, jak i **[E-mail właściciela pliku źródłowego]** są zmiennymi specyficznymi dla infrastruktury FCI i należy je wpisać dokładnie w takiej formie, w jakiej występują w powyższym poleceniu. Pierwsza z nich jest używana przez infrastrukturę FCI w celu automatycznego określenia wskazanego pliku w folderze, a druga jest przeznaczona dla infrastruktury FCI w celu automatycznego pobrania adresu e-mail nazwanego właściciela wskazanego pliku. To polecenie jest powtarzane dla każdego pliku w folderze, co w użytym przykładzie oznacza wszystkie pliki w folderze C:\FileShare, które dodatkowo jako właściwość klasyfikacji pliku mają usługę RMS.

            > [!NOTE]
            > Parametr i wartość **-OwnerMail [E-mail właściciela pliku źródłowego]** zapewniają, że po włączeniu ochrony pliku właściciel oryginalnego pliku otrzymuje uprawnienia właściciela zarządzania prawami pliku. Dzięki temu pierwotny właściciel pliku ma uprawnienia do zarządzania prawami dostępu do swoich plików. Kiedy pliki są tworzone przez użytkownika domeny, adres e-mail jest automatycznie pobierany z usługi Active Directory przy użyciu nazwy konta użytkownika w pliku właściwości właściciela. Aby to zrobić, serwer plików musi być w tej samej domenie lub zaufanej domenie co użytkownik.
            > 
            > W miarę możliwości należy przypisać pierwotnych właścicieli do chronionych dokumentów, aby zapewnić im dalszą pełną kontrolę nad utworzonymi przez nich plikami. Jeśli jednak użyjesz zmiennej [E-mail właściciela pliku źródłowego] zgodnie z powyższymi instrukcjami, a plik nie ma zdefiniowanego użytkownika domeny jako właściciela (na przykład do utworzenia pliku użyto konta lokalnego, więc jako właściciela wyświetlany jest SYSTEM), to skrypt zakończy się niepowodzeniem.
            > 
            > W przypadku plików, których właścicielem nie jest użytkownik domeny, możesz skopiować i zapisać pliki jako użytkownik domeny, stając się właścicielem tylko tych plików. Lub, jeśli masz uprawnienia, możesz ręcznie zmienić właściciela.  Możesz także podać konkretny adres e-mail (np. własny lub adres grupy działu informatycznego) zamiast zmiennej [E-mail właściciela pliku źródłowego], co oznacza, że wszystkie pliki, które chronisz za pomocą tego skryptu, będą używać tego adresu e-mail do definiowania nowego właściciela.

    -   **Uruchom polecenie jako**: Wybierz **System lokalny**

    -   Na karcie **Warunek**:

        -   **Właściwość**: Wybierz **RMS**

        -   W obszarze **Operator** wybierz pozycję **Równe**.

        -   **Wartość**: Wybierz **Tak**.

    -   Na karcie **Harmonogram**:

        -   **Uruchom o**: Skonfiguruj preferowany harmonogram.

            Wykonanie skryptu może zająć dużo czasu. Chociaż to rozwiązanie chroni wszystkie pliki w folderze, skrypt jest wykonywany jednokrotnie dla każdego pliku, przy każdym uruchomieniu. Chociaż trwa to dłużej niż obsługiwana przez narzędzie RMS Protection Tool ochrona wszystkich plików jednocześnie, to konfiguracja ochrony każdego pliku z osobna jest bardziej skuteczna. Na przykład chronione pliki mogą mieć różnych właścicieli (przy zachowaniu pierwotnego właściciela), gdy jest używana zmienna [E-mail właściciela pliku źródłowego]. Akcja ochrony każdego pliku osobno będzie wymagana, jeśli użytkownik zmieni konfigurację w celu ochrony tylko wybranych plików, a nie wszystkich plików w folderze.

        -   **Uruchamiaj stale w nowych plikach**: Zaznacz to pole wyboru.

### Przetestuj konfigurację, ręcznie uruchamiając regułę i zadanie.

1.  Uruchom regułę klasyfikacji:

    1.  Kliknij pozycję **Reguły klasyfikacji** &gt; **Uruchom teraz klasyfikację przy użyciu wszystkich reguł**

    2.  Kliknij pozycję **Zaczekaj na zakończenie operacji klasyfikacji**, a następnie kliknij przycisk **OK**.

2.  Poczekaj na zamknięcie okna dialogowego **Wykonywanie klasyfikacji**, a następnie przejrzyj wyniki w raporcie, który zostanie automatycznie wyświetlony. Dla pola **Właściwości** powinna zostać wyświetlona wartość **1**. Powinna również zostać wyświetlona liczba plików w folderze. Sprawdź właściwości plików w wybranym folderze za pomocą Eksploratora plików. Na karcie **Klasyfikacja** powinna zostać wyświetlona nazwa **RMS** jako nazwa właściwości i pozycja **Tak** dla jej **wartości**.

3.  Uruchom zadanie zarządzania plikami:

    1.  Kliknij węzeł **Zadania zarządzania plikami** &gt; **Chroń pliki za pomocą usługi RMS** &gt; **Uruchom teraz zadanie zarządzania plikami**

    2.  Kliknij pozycję **Zaczekaj na zakończenie zadania**, a następnie kliknij przycisk **OK**.

4.  Poczekaj na zamknięcie okna dialogowego **Uruchamianie zadania zarządzania plikami**, a następnie przejrzyj wyniki w raporcie, który zostanie automatycznie wyświetlony. Liczba plików w wybranym folderze programu powinna być widoczna w polu **Pliki**. Upewnij się, że pliki w wybranym folderze są teraz chronione przez usługi RMS. Na przykład, jeśli wybrany folder to C:\FileShare, wpisz następujące polecenie w sesji środowiska Windows PowerShell i upewnij się, że żaden plik nie ma statusu **Niechroniony**:

    ```
    foreach ($file in (Get-ChildItem -Path C:\FileShare -Force | where {!$_.PSIsContainer})) {Get-RMSFileStatus -f $file.PSPath}
    ```
    > [!TIP]
    > Wskazówki dotyczące rozwiązywania problemów:
    > 
    > -   Jeśli raport zawiera wartość **0** zamiast liczby plików w folderze, oznacza to, że skrypt nie został uruchomiony. Po pierwsze sprawdź sam skrypt przez załadowanie go w środowisku Windows PowerShell ISE, aby zweryfikować jego zawartość, a następnie spróbuj go uruchomić, aby zobaczyć, czy zostaną wyświetlone błędy. Jeśli nie zostaną określone argumenty, skrypt podejmie próbę nawiązania połączenia z usługami Azure RMS i wykonania uwierzytelnienia za ich pomocą.
    > 
    >     -   Jeśli skrypt zgłasza, że nie może nawiązać połączenia z usługami Azure RMS, sprawdź wartości wyświetlane dla konta głównego usługi określonego w skrypcie.  Aby uzyskać więcej informacji na temat tworzenia tego konta głównego usługi, zobacz drugie wymaganie wstępne w temacie [about_RMSProtection_AzureRMS](https://msdn.microsoft.com/library/mt433202.aspx)
    >     -   Jeśli skrypt zgłasza, że może nawiązać połączenie z usługami Azure RMS, sprawdź, czy może znaleźć wskazany szablon, uruchamiając polecenie [Get-RMSTemplate](https://msdn.microsoft.com/library/mt433197.aspx) bezpośrednio w programie Windows PowerShell na serwerze. Określony szablon powinien pojawić się w zwracanych w wynikach.
    > -   Jeśli skrypt samodzielnie uruchamia się w środowisku Windows PowerShell ISE bez błędów, spróbuj uruchomić go w następujący sposób z sesji programu PowerShell, określając nazwę pliku do ochrony i bez parametru -OwnerEmail:
    > 
    >     ```
    >     powershell.exe -Noprofile -Command "<path>\RMS-Protect-FCI.ps1 -File '<full path and name of a file>' -TemplateID <template GUID>"
    >     ```
    >     -   Jeśli skrypt zostanie uruchomiony pomyślnie w tej sesji środowiska Windows PowerShell, sprawdź wpisy dla pozycji **Główne** i **Argument** w akcji zadania zarządzania plikami.  Jeśli określono parametr **-OwnerEmail [E-mail właściciela pliku źródłowego]**, spróbuj go usunąć.
    > 
    >         Jeśli zadanie zarządzania plikami działa pomyślnie bez określenia parametru **-OwnerEmail [E-mail właściciela pliku źródłowego]**, upewnij się, że właścicielem niechronionych plików jest użytkownik domeny, a nie **SYSTEM**.  W tym celu użyj karty **Zabezpieczenia** we właściwościach pliku, a następnie kliknij pozycję **Zaawansowane**. Wartość **Właściciel** jest wyświetlana bezpośrednio po wartości **Nazwa** pliku. Sprawdź także, czy serwer plików jest w tej samej domenie lub w zaufanej domenie, aby wyszukać adres e-mail użytkownika z usług domenowych Active Directory.
    > -   Jeśli raport zawiera poprawną liczbę plików, ale pliki nie są chronione, spróbuj uruchomić ochronę ręcznie, za pomocą polecenia cmdlet [Protect-RMSFile](https://msdn.microsoft.com/library/azure/mt433201.aspx), aby sprawdzić, czy są wyświetlane błędy.

Po potwierdzeniu, że zadania zostały pomyślnie uruchomione, można zamknąć Menedżera zasobów plików. Nowe pliki będą chronione automatycznie, a wszystkie pliki zostaną objęte ochroną ponownie po uruchomieniu harmonogramów. Ponowna ochrona plików gwarantuje, że zmiany wprowadzone w szablonie są stosowane do plików.


## Modyfikowanie instrukcji na potrzeby selektywnej ochrony plików
Jeżeli poprzednie instrukcje działają, można je łatwo zmodyfikować na potrzeby bardziej zaawansowanej konfiguracji. Na przykład uruchom ochronę plików za pomocą tego samego skryptu, ale obejmij nią tylko pliki, które zawierają dane osobowe, wybierając szablon z bardziej restrykcyjnymi uprawnieniami.

Aby to zrobić, użyj jednej z wbudowanych właściwości klasyfikacji (na przykład **Dane osobowe**) lub utwórz własną właściwość. Następnie utwórz nową regułę, która używa tej właściwości. Na przykład możesz wybrać pozycję **Klasyfikator zawartości**, wybrać właściwość **Dane osobowe** o wartości **Wysokie** i skonfigurować ciąg lub wzorzec wyrażenia, który identyfikuje plik do skonfigurowania dla tej właściwości (np. **Data urodzenia**).

Teraz wystarczy tylko utworzyć nowe zadanie zarządzania plikami, które korzysta z tego samego skryptu, ale np. z innego szablonu, i skonfigurować warunek dla właśnie skonfigurowanej właściwości klasyfikacji. Na przykład zamiast warunku, który został wcześniej skonfigurowany (właściwość **RMS**, **Równe**, **Tak**), wybierz właściwość **Dane osobowe** z ustawieniem **Operator** o wartości **Równe** i ustawieniem **Wartość** o wartości **Wysokie**.




<!--HONumber=Jul16_HO3-->


