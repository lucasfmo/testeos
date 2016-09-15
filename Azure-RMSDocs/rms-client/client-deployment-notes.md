---
title: "Uwagi dotyczące wdrażania klienta usługi RMS | Azure RMS"
description: 
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 05/13/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 03cc8c6f-3b63-4794-8d92-a5df4cdf598f
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 2bd8aba91b9b65777c2319baea848e8313cbccda
ms.openlocfilehash: ffddda9a144b23b64b54df4fe4d25ec62600599d


---

# Uwagi dotyczące wdrażania klienta usługi RMS

*Dotyczy: usługi Active Directory Rights Management, Azure Rights Management, Windows 7 z dodatkiem SP1, Windows 8, Windows 8.1, Windows Server 2008, Windows Server 2008 R2, Windows Server 2012, Windows Server 2012 R2, Windows Vista*

Klient usługi Rights Management (klient usługi RMS) w wersji 2 jest także znany jako klient MSIPC. Jest to oprogramowanie przeznaczone dla komputerów z systemem Windows, które komunikuje się z usługą Microsoft Rights Management lokalnie lub w chmurze, aby ułatwić ochronę dostępu do informacji i ich użycia. Ochrona obejmuje przepływ informacji przez aplikacje i urządzenia w granicach organizacji lub poza zarządzanymi granicami. Klient usługi RMS jest dostarczany razem z [aplikacją do udostępniania usługi Rights Management dla systemu Windows](sharing-app-windows.md). Jest również dostępny [jako opcjonalny plik do pobrania](http://www.microsoft.com/download/details.aspx?id=38396), który można — po potwierdzeniu i zaakceptowaniu umowy licencyjnej — za darmo rozpowszechniać za pomocą oprogramowania innych firm. Dzięki temu klienci mogą chronić i wykorzystywać zawartość chronioną przy użyciu usług Rights Management.


## Dystrybucja klienta usługi RMS
Klient usługi RMS może być za darmo dystrybuowany i umieszczany w pakietach z innymi aplikacjami i rozwiązaniami IT. Jeśli jesteś deweloperem aplikacji lub dostawcą rozwiązań i chcesz dystrybuować klienta usługi RMS, masz dwie opcje:

-   Zalecana: osadź instalatora klienta usługi RMS w instalacji aplikacji i uruchom go w trybie dyskretnym (przełącznik **/quiet** szczegółowo opisany w następnej sekcji).

-   Ustaw klienta usługi RMS jako wymaganie wstępne aplikacji. W przypadku tej opcji może być konieczne udostępnienie użytkownikom dodatkowych instrukcji dotyczących uzyskiwania i instalowania klienta oraz aktualizowania komputerów przy jego użyciu przed rozpoczęciem korzystania z aplikacji.

## Instalowanie klienta usługi RMS
Klient RMS jest dostępny w pliku wykonywalnym instalatora o nazwie **setup_msipc_***<arch>***.exe**, gdzie *<arch>* to **x86** (dla 32-bitowych komputerów klienckich) lub **x64** (dla 64-bitowych komputerów klienckich). Pakiet instalatora wersji 64-bitowej (x64) instaluje zarówno plik wykonywalny 32-bitowego środowiska uruchomieniowego na potrzeby zachowania zgodności z 32-bitowymi aplikacjami działającymi w 64-bitowym systemie operacyjnym, jak i plik wykonywalny 64-bitowego środowiska uruchomieniowego do obsługi natywnych aplikacji 64-bitowych. Instalatora w wersji 32-bitowej (x86) nie można uruchomić w 64-bitowej instalacji systemu Windows.

> [!NOTE]
> Do zainstalowania klienta usługi RMS wymagane są podniesione uprawnienia, np. członka grupy Administratorzy na komputerze lokalnym.

Klienta usługi RMS można zainstalować przy użyciu jednej z następujących metod instalacji:

-   **Tryb dyskretny.** Używając przełącznika **/quiet** w opcjach wiersza polecenia, można zainstalować klienta usługi RMS na komputerach w trybie dyskretnym. W poniższym przykładzie przedstawiono instalację klienta usługi RMS w trybie dyskretnym na 64-bitowym komputerze klienckim:

    ```
    setup_msipc_x64.exe /quiet
    ```

-   **Tryb interaktywny.** Klienta usługi RMS można również zainstalować przy użyciu opartego na graficznym interfejsie użytkownika instalatora dostarczonego z Kreatorem instalacji klienta usługi RMS. W tym celu kliknij dwukrotnie pakiet instalatora klienta usługi RMS (**setup_msipc_***<arch>***.exe**) w folderze, do którego on został skopiowany lub pobrany na komputerze lokalnym.

## Pytania i odpowiedzi dotyczące klienta usługi RMS
Poniższa sekcja zawiera często zadawane pytania na temat klienta usługi RMS oraz odpowiedzi na nie.

### Które systemy operacyjne są obsługiwane przez klienta usługi RMS?
Klient usługi RMS jest obsługiwany w następujących systemach operacyjnych:

|System operacyjny Windows Server|Kliencki system operacyjny Windows|
|-----------------------------------|-----------------------------------|
|Windows Server 2012 R2|Windows 8.1|
|Windows Server 2012|Windows 8|
|Windows Server 2008 R2|Windows 7 co najmniej z dodatkiem SP1|
|Windows Server 2008 (tylko usługi AD RMS)|Windows Vista co najmniej z dodatkiem SP2 (tylko usługi AD RMS)|

### Które procesory lub platformy obsługują klienta usługi RMS?
Klient usługi RMS jest obsługiwany na platformach obliczeniowych x86 i x64.

### Gdzie jest instalowany klient usługi RMS?
Klient usługi RMS jest domyślnie instalowany w katalogu %ProgramFiles%\Active Directory Rights Management Services Client 2.<minor version number>.

### Które pliki są skojarzone z oprogramowaniem klienta usługi RMS?
Następujące pliki są instalowane jako część oprogramowania klienckiego usługi RMS:

-   Msipc.dll

-   Ipcsecproc.dll

-   Ipcsecproc_ssp.dll

-   MSIPCEvents.man

Oprócz wymienionych plików klient usługi RMS instaluje również pliki obsługi wielojęzycznego interfejsu użytkownika (MUI) w 44 językach. Aby sprawdzić listę obsługiwanych języków, uruchom instalację klienta usługi RMS i po jej zakończeniu przejrzyj zawartość folderów obsługi wielu języków w domyślnej ścieżce.

### Czy klient usługi RMS jest domyślnie uwzględniany podczas instalacji obsługiwanego systemu operacyjnego?
Nie. Ta wersja klienta usługi RMS jest dostarczana jako opcjonalny plik do pobrania, który można osobno instalować na komputerach z obsługiwanymi wersjami systemu operacyjnego Microsoft Windows.

### Czy klient usługi RMS jest automatycznie aktualizowany przy użyciu usługi Microsoft Update?
Jeśli ten klient usługi RMS został zainstalowany w trybie dyskretnym, dziedziczy bieżące ustawienia usługi Microsoft Update. Jeśli klient usługi RMS został zainstalowany za pomocą instalatora opartego na graficznym interfejsie użytkownika, kreator instalacji klienta usługi RMS monituje użytkownika o włączenie usługi Microsoft Update.

## Ustawienia klienta usługi RMS
Poniższa sekcja zawiera informacje na temat ustawień klienta usługi RMS. Informacje te mogą być przydatne, jeśli masz problemy z aplikacjami lub usługami korzystającymi z klienta usługi RMS.

> [!NOTE]
> Niektóre ustawienia są zależne od tego, czy aplikacja obsługująca usługę RMS działa jako aplikacja w trybie klienta (np. programy Microsoft Word i Outlook lub aplikacja do udostępniania usługi RMS), czy aplikacja w trybie serwera (np. programy SharePoint i Exchange).  W poniższych tabelach te ustawienia są identyfikowane odpowiednio jako **Tryb klienta** i **Tryb serwera**.

### Gdzie klient usługi RMS przechowuje licencje na komputerach klienckich
Klient usługi RMS przechowuje licencje na dysku lokalnym oraz buforuje niektóre informacje w rejestrze systemu Windows.

|Opis|Ścieżki trybu klienta|Ścieżki trybu serwera|
|---------------|---------------------|---------------------|
|Lokalizacja magazynu licencji|%localappdata%\Microsoft\MSIPC|%allusersprofile%\Microsoft\MSIPC\Server\*<SID>*\|
|Lokalizacja magazynu szablonów|%localappdata%\Microsoft\MSIPC\Templates|%allusersprofile%\Microsoft\MSIPC\Server\Templates\*<SID>*\|
|Lokalizacja w rejestrze|HKEY_CURRENT_USER<br /> \Software<br /> \Classes<br /> \Local Settings<br /> \Software<br /> \Microsoft<br /> \MSIPC|HKEY_CURRENT_USER<br /> \Software<br /> \Microsoft<br /> \MSIPC<br /> \Server<br /> \*<SID>*|
> [!NOTE]
> *<SID>* to bezpieczny identyfikator konta, na którym działa aplikacja serwera. Jeśli na przykład aplikacja działa na koncie wbudowanej usługi sieciowej, należy zastąpić *<SID>* wartością znanego identyfikatora SID dla tego konta (S-1-5-20).

### Ustawienia rejestru systemu Windows klienta usługi RMS
Za pomocą kluczy rejestru systemu Windows można ustawić lub zmodyfikować niektóre konfiguracje klienta usługi RMS. Na przykład administrator aplikacji z obsługą usługi RMS, które komunikują się z serwerami AD RMS, może zaktualizować lokalizację usługi przedsiębiorstwa (zastąpić serwer usług AD RMS wybrany do użycia podczas publikowania) w zależności od aktualnej lokalizacji komputera klienckiego w topologii usługi Active Directory. Można też włączyć śledzenie usługi RMS na komputerze klienckim, aby ułatwić rozwiązywanie problemów dotyczących aplikacji obsługującej usługę RMS. Skorzystaj z poniższej tabeli, aby zidentyfikować ustawienia rejestru, które możesz zmieniać w przypadku klienta usługi RMS.

|Zadanie|Ustawienia|
|--------|------------|
|Tylko usługi AD RMS: aby zaktualizować lokalizację usługi przedsiębiorstwa dla komputera klienckiego|Zaktualizuj następujące klucze rejestru:<br /><br />HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\ServiceLocation\EnterpriseCertification<br />REG_SZ: domyślna<br /><br />**Wartość:**<http or https>:// *Nazwa_klastra_usługi*/_wmcs/Certification<br /><br />HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\ServiceLocation\EnterprisePublishing<br />REG_SZ: domyślna<br /><br />**Wartość:** <http or https>:// *Nazwa_klastra_usługi_RMS*/_wmcs/Licensing|
|Aby włączyć lub wyłączyć śledzenie|Zaktualizuj następujący klucz rejestru:<br /><br />HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC<br />REG_DWORD: Trace<br /><br />**Wartość:** 1 — włączenie śledzenia, 0 — wyłączenie śledzenia (wartość domyślna)|
|Aby zmienić częstotliwość odświeżania szablonów w dniach|Poniższe wartości rejestru służą do określania, jak często szablony będą odświeżane na komputerze użytkownika, jeśli nie ustawiono wartości TemplateUpdateFrequencyInSeconds.  Jeśli żadna z tych wartości nie zostanie ustawiona, domyślnym interwałem odświeżania aplikacji za pomocą klienta usługi RMS (wersja 1.0.1784.0) w celu pobrania szablonów będzie 1 dzień. W starszych wersjach wartość domyślna to 7 dni.<br /><br />**Tryb klienta:**<br /><br />HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC<br />REG_DWORD: TemplateUpdateFrequency<br /><br />**Wartość:** wartość całkowita określająca liczbę dni (minimum 1) między pobraniami.<br /><br />**Tryb serwera:**<br /><br />HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\Server\\*\<SID\>\*<br />REG_DWORD: TemplateUpdateFrequency<br /><br />**Wartość:** wartość całkowita określająca liczbę dni (minimum 1) między pobraniami.|
|Aby zmienić częstotliwość odświeżania szablonów w sekundach<br /><br />Ważne: w przypadku określenia tej wartości częstotliwość odświeżania szablonów w dniach zostanie zignorowana. Określ jedną z tych wartości, nie obydwie.|Poniższe wartości rejestru wskazują, jak często szablony będą aktualizowane na komputerze użytkownika. Jeśli nie ustawiono tej wartości ani wartości zmiany częstotliwości w dniach (TemplateUpdateFrequency), domyślnym interwałem odświeżania aplikacji za pomocą klienta usługi RMS (wersja 1.0.1784.0) w celu pobrania szablonów będzie 1 dzień. W starszych wersjach wartość domyślna to 7 dni.<br /><br />**Tryb klienta:**<br /><br />HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC<br />REG_DWORD: TemplateUpdateFrequencyInSeconds<br /><br />**Wartość:** wartość całkowita określająca liczbę sekund (minimum 1) między pobraniami.<br /><br />**Tryb serwera:**<br /><br />HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\Server\\*\<SID\>\*<br />REG_DWORD: TemplateUpdateFrequencyInSeconds<br /><br />**Wartość:** wartość całkowita określająca liczbę sekund (minimum 1) między pobraniami.|
|Tylko usługi AD RMS: aby pobierać szablony natychmiast po następnym żądaniu publikowania|Na potrzeby operacji testowania i oceniania możesz wybrać opcję pobierania szablonów przy użyciu klienta usługi RMS tak szybko, jak to możliwe. W tym celu usuń poniższy klucz rejestru. Spowoduje to, że klient usługi RMS będzie pobierać szablony natychmiast po następnym żądaniu publikowania (nie będzie czekać przez czas określony w ustawieniu rejestru TemplateUpdateFrequency):<br /><br />HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC\<Server Name>\Template<br /><br />**Uwaga**: <Server Name> może wskazywać zewnętrzny (corprights.contoso.com) i wewnętrzny (corprights) adres URL, więc wpisy mogą być dwa.|
|Tylko usługi AD RMS: aby włączyć obsługę uwierzytelniania federacyjnego|Jeśli komputer kliencki usługi RMS łączy się z klastrem usług AD RMS za pomocą zaufania federacyjnego, należy skonfigurować obszar macierzysty federacji.<br /><br />HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\Federation<br />REG_SZ: FederationHomeRealm<br /><br />**Wartość:** wartość tego wpisu rejestru to identyfikator URI usługi federacyjnej (na przykład: „http://TreyADFS.trey.net/adfs/services/trust”).<br /><br /> **Uwaga**: Ważne jest, aby dla tej wartości podać protokół http, a nie https. Ponadto w przypadku 32-bitowej aplikacji MSIPC działającej w 64-bitowej wersji systemu Windows lokalizacja będzie następująca: HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\MSIPC\Federation. Konfigurację przykładową przedstawiono w temacie [Wdrażanie Usług Active Directory Rights Management z Usługami federacyjnymi Active Directory](https://technet.microsoft.com/library/dn758110.aspx).|
|Tylko usługi AD RMS: aby obsługiwać serwery federacyjne partnera wymagające uwierzytelniania opartego na formularzu do wprowadzenia danych przez użytkowników|Domyślnie klient usługi RMS działa w trybie dyskretnym i użytkownik nie musi wprowadzać żadnych danych. Serwery federacyjne partnerów mogą być jednak skonfigurowane tak, aby wymagać wprowadzenia danych przez użytkownika, na przykład w ramach uwierzytelniania opartego na formularzu. W takim przypadku należy skonfigurować klienta usługi RMS, aby ignorował tryb dyskretny w celu umożliwienia wyświetlenia formularza uwierzytelniania federacyjnego w oknie przeglądarki na potrzeby uwierzytelniania użytkowników.<br /><br />HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\Federation<br />REG_DWORD: EnableBrowser<br /><br />**Uwaga**: jeśli serwer federacyjny został skonfigurowany do użycia uwierzytelniania opartego na formularzu, ten klucz jest wymagany. Jeśli serwer federacyjny jest skonfigurowany do użycia zintegrowanego uwierzytelniania systemu Windows, ten klucz nie jest wymagany.|
|Tylko usługi AD RMS: aby zablokować użycie usługi ILS|Domyślnie klient usługi RMS obsługuje korzystanie z zawartości chronionej przez usługę ILS, można go jednak skonfigurować tak, aby blokował tę usługę, używając poniższego klucza rejestru. Jeśli ten klucz rejestru został ustawiony na blokowanie usługi ILS, wszelkie próby otwarcia lub uzyskania dostępu do zawartości chronionej przez usługę ILS spowodują zwrócenie następującego błędu:<br />HRESULT_FROM_WIN32(ERROR_ACCESS_DISABLED_BY_POLICY)<br /><br />HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC<br />REG_DWORD: **DisablePassportCertification**<br /><br />**Wartość:** 1 — blokowanie użycia usługi ILS, 0 — zezwolenie na użycie usługi ILS (wartość domyślna)|

### Zarządzanie dystrybucją szablonów dla klienta usługi RMS
Szablony ułatwiają użytkownikom i administratorom szybkie stosowanie ochrony przy użyciu usługi Rights Management. Klient usługi RMS automatycznie pobiera szablony z serwerów usługi lub usług RMS. Jeśli szablony zostaną umieszczone w poniższej lokalizacji folderu, klient usługi RMS nie będzie pobierać szablonów z lokalizacji domyślnej, a w zamian pobierze szablony znajdujące się w tym folderze. Klient usługi RMS może kontynuować pobieranie z innych dostępnych serwerów usługi RMS.

**Tryb klienta:** %localappdata%\Microsoft\MSIPC\UnmanagedTemplates

**Tryb serwera:** %allusersprofile%\Microsoft\MSIPC\Server\UnmanagedTemplates\\*\<SID\>\*

Jeśli korzystasz z tego folderu, nie trzeba używać specjalnej konwencji nazewnictwa. Szablony muszą jednak zostać wydane przez usługę lub serwer RMS, a wymagane rozszerzenie nazwy pliku to XML. Prawidłowe nazwy to na przykład Contoso-Confidential.xml lub Contoso-ReadOnly.xml.

## Tylko usługi AD RMS: ograniczanie klienta usługi RMS do użycia zaufanych serwerów usług AD RMS
Klienta usługi RMS można ograniczyć tak, aby używał tylko określonych zaufanych serwerów usług AD RMS, wprowadzając poniższe zmiany do rejestru systemu Windows na komputerach lokalnych.

**Aby włączyć ograniczanie klienta usługi RMS tak, aby używał tylko zaufanych serwerów AD RMS**

-   HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\TrustedServers\
    REG_DWORD: AllowTrustedServersOnly

    **Wartość:** jeśli zostanie określona wartość różna od zera, klient usługi RMS będzie ufać tylko określonym serwerom skonfigurowanym na liście TrustedServers i usłudze Azure Rights Management.

**Aby dodać elementy członkowskie do listy zaufanych serwerów usług AD RMS**

-   HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\TrustedServers\
    REG_SZ: *<Adres_URL_lub_nazwa_hosta>*

    **Wartość:** ciągi dodane w tej lokalizacji klucza rejestru mogą być podane w formacie nazwy domeny systemu DNS (np. **adrms.contoso.com**) lub w postaci pełnych adresów URL zaufanych serwerów usług AD RMS (np. **https://adrms.contoso.com**). Jeśli wybrany adres URL rozpoczyna się ciągiem **https://**, klient usługi RMS użyje protokołu SSL lub zabezpieczeń TLS do kontaktowania się z określonym serwerem usług AD RMS.

## Odnajdowanie usługi RMS
Odnajdowanie usługi RMS umożliwia klientowi usługi RMS sprawdzanie usługi lub serwera RMS, z którym będzie nawiązywana komunikacja, przed rozpoczęciem ochrony zawartości. Odnajdowanie usługi również może się nastąpić, gdy klient usługi RMS korzysta z zawartości chronionej, ale jest mniej prawdopodobne, ponieważ zasady dołączone do zawartości zawierają preferowaną usługę lub serwer RMS. Klient uruchomi odnajdowanie usługi, tylko jeśli wystąpi błąd tej czynności.

Podczas odnajdowania usługi najpierw wyszukiwana jest lokalna wersja usługi Rights Management (AD RMS). Jeśli to się nie powiedzie, funkcja odnajdowania usługi automatycznie wyszuka wersję usługi Rights Management (Azure RMS) w chmurze.

Podczas odnajdowania usługi w przypadku wdrożenia lokalnego klient usługi RMS sprawdza następujące elementy:

1.  Rejestr systemu Windows na komputerze lokalnym: jeśli w rejestrze skonfigurowano ustawienia odnajdowania usług, zostaną one wypróbowane jako pierwsze.  Domyślnie te ustawienia nie są konfigurowane w rejestrze.

2.  Usługi domenowe Active Directory: komputer dołączony do domeny wysyła do usługi Active Directory zapytanie o punkt połączenia usługi (SCP). Jeśli punkt połączenia usługi został zarejestrowany, do klienta usługi RMS zwracany jest adres URL serwera RMS do użycia.

### Tylko usługi AD RMS: włączanie odnajdowania po stronie serwera za pomocą usługi Active Directory
Jeśli konto ma wystarczające uprawnienia (administratorzy przedsiębiorstwa i administrator lokalny serwera usług AD RMS), można automatycznie zarejestrować punkt połączenia usługi (SCP) podczas instalowania serwera głównego klastra usług AD RMS. Jeśli punkt połączenia usługi już istnieje w lesie, należy najpierw usunąć istniejący punkt połączenia usługi przed zarejestrowaniem nowego.

Aby zarejestrować i usunąć punkt połączenia usługi po zainstalowaniu usług AD RMS, można wykonać kroki poniższej procedury. Przed rozpoczęciem upewnij się, że konto ma wymagane uprawnienia (administratorzy przedsiębiorstwa i administrator lokalny serwera usług AD RMS).

#### Aby włączyć odnajdywanie usług AD RMS przez zarejestrowanie punktu połączenia w usłudze Active Directory

1.  Otwórz konsolę usług Active Directory Management na serwerze usług AD RMS:

    -   W systemie Windows Server 2008 R2 lub Windows Server 2008 kliknij przycisk **Start**, kliknij pozycję **Narzędzia administracyjne**, a następnie kliknij pozycję **Usługi Active Directory Rights Management**.

    -   W systemie Windows Server 2012 R2 lub Windows Server 2012 w Menedżerze serwera kliknij pozycję **Narzędzia**, a następnie kliknij pozycję **Usługi Active Directory Rights Management**.

2.  W konsoli usług AD RMS kliknij prawym przyciskiem myszy klaster usług AD RMS, a następnie kliknij pozycję **Właściwości**.

3.  Kliknij kartę **Punkt połączenia usługi**.

4.  Zaznacz pole wyboru **Zmień punkt połączenia usługi**.

5.  Wybierz opcję **Ustaw punkt połączenia usługi na bieżący klaster certyfikacji**, a następnie kliknij przycisk **OK**.

### Włączanie odnajdowania usługi po stronie klienta za pomocą rejestru systemu Windows
Jeśli nie chcesz używać punktu połączenia usługi lub jeśli punkt połączenia usługi nie istnieje, możesz skonfigurować rejestr na komputerze klienckim, aby klient usługi RMS mógł znaleźć odpowiedni serwer usług AD RMS.

#### Aby włączyć odnajdowanie usługi AD RMS po stronie klienta za pomocą rejestru systemu Windows

1.  Otwórz edytor rejestru systemu Windows — Regedit.exe:

    -   Na komputerze klienckim w oknie uruchamiania wpisz ciąg **regedit**, a następnie naciśnij klawisz Enter, aby otworzyć Edytor rejestru.

2.  W Edytorze rejestru przejdź do klucza **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC**.

    > [!IMPORTANT]
    > W przypadku używania 32-bitowej aplikacji na 64-bitowym komputerze ścieżka będzie następująca: **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\MSIPC**

3.  Aby utworzyć podklucz ServiceLocation, kliknij prawym przyciskiem myszy pozycję **MSIPC**, wskaż pozycję **Nowy**, kliknij pozycję **Klucz**, a następnie wpisz ciąg **ServiceLocation**.

4.  Aby utworzyć podklucz EnterpriseCertification, kliknij prawym przyciskiem myszy pozycję **ServiceLocation**, wskaż pozycję **Nowy**, kliknij pozycję **Klucz**, a następnie wpisz ciąg **EnterpriseCertification**.

5.  Aby ustawić adres URL certyfikacji przedsiębiorstwa, kliknij dwukrotnie wartość **(Domyślna)** w podkluczu **EnterpriseCertification**. W wyświetlonym oknie dialogowym **Edytowanie ciągu** w polu **Dane wartości** wpisz <http or https>://*AD RMS_cluster_name*/_wmcs/Certification, a następnie kliknij przycisk **OK**.

6.  Aby utworzyć podklucz EnterprisePublishing, kliknij prawym przyciskiem myszy pozycję **ServiceLocation**, wskaż pozycję **Nowy**, kliknij pozycję **Klucz**, a następnie wpisz ciąg EnterprisePublishing.

7.  Aby ustawić adres URL publikowania przedsiębiorstwa, kliknij dwukrotnie wartość **(Domyślna)** w podkluczu **EnterprisePublishing**. W wyświetlonym oknie dialogowym **Edytowanie ciągu** w polu **Dane wartości** wpisz <http or https>://*AD RMS_cluster_name*/_wmcs/Licensing, a następnie kliknij przycisk **OK**.

8.  Zamknij Edytor rejestru.

Jeśli klient usługi RMS nie może znaleźć punktu połączenia usługi przy użyciu zapytania wysyłanego do usługi Active Directory i nie określono tego punktu w rejestrze, wywołania funkcji odnajdowania usługi dla usług AD RMS zakończą się niepowodzeniem.

### Przekierowywanie ruchu serwera licencyjnego
W pewnych przypadkach może wystąpić potrzeba przekierowania ruchu w czasie odnajdowania usługi, na przykład gdy są łączone ze sobą dwie organizacje i stary serwer licencyjny w jednej z organizacji jest wycofywany, a klienci muszą zostać przekierowani do nowego serwera. Dotyczy to także migracji z usług AD RMS do usługi Azure RMS. Użyj następującej procedury, aby włączyć przekierowywanie licencjonowania.

#### Aby włączyć przekierowywanie serwera licencyjnego usługi RMS za pomocą rejestru systemu Windows

1.  Otwórz edytor rejestru systemu Windows — Regedit.exe:

    -   Na komputerze klienckim w oknie uruchamiania wpisz ciąg **regedit**, a następnie naciśnij klawisz Enter, aby otworzyć Edytor rejestru.

2.  W Edytorze rejestru przejdź do jednej z gałęzi:

    -   W przypadku 64-bitowej wersji pakietu Office na platformie x64: HKLM\SOFTWARE\Microsoft\MSIPC\Servicelocation

    -   W przypadku 32-bitowej wersji pakietu Office na platformie x64: HKLM\SOFTWARE\Wow6432Node\Microsoft\MSIPC\Servicelocation

3.  Utwórz podklucz LicensingRedirection: kliknij prawym przyciskiem myszy pozycję **Servicelocation**, wskaż pozycję **Nowy**, kliknij pozycję **Klucz**, a następnie wpisz **LicensingRedirection**.

4.  Aby ustawić przekierowywanie licencjonowania, kliknij prawym przyciskiem myszy podklucz **LicensingRedirection**, wybierz pozycję **Nowy**, a następnie wybierz pozycję **Wartość ciągu**.  W polu **Nazwa** podaj adres URL starego serwera licencyjnego, a w polu **Wartość** podaj adres URL nowego serwera licencyjnego.

    Na przykład aby przekierować licencjonowanie z serwera Contoso.com do serwera Fabrikam.com, możesz wprowadzić następujące wartości:

    **Nazwa:** https://contoso.com/_wmcs/licensing

    **Wartość:** https://fabrikam.com/_wmcs/licensing

    > [!NOTE]
    > Jeśli stary serwer licencyjny ma określony intranetowy i ekstranetowy adres URL, nowe mapowanie nazwy i wartości musi zostać ustawione dla obu tych adresów URL w kluczu LicensingRedirection.

5.  Powtórz poprzedni krok w przypadku wszystkich serwerów, które muszą zostać przekierowane.

6.  Zamknij Edytor rejestru.




<!--HONumber=Jul16_HO3-->


