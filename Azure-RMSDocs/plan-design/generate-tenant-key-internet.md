---
title: "Generowanie i przekazywanie klucza dzierżawy — przez Internet | Azure RMS"
description: 
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 1bff9b06-8c5a-4b1d-9962-6668219210e6
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 67129d6cdac124947fc07aa4d42523686227752e
ms.openlocfilehash: 7ec87b63b31d0b41c93dab7998df63e208308811


---


# Generowanie i przekazywanie klucza dzierżawy — przez Internet

*Dotyczy usług: Azure Rights Management, Office 365*

Jeśli zdecydujesz się na [zarządzanie własnym kluczem dzierżawy](plan-implement-tenant-key.md#choose-your-tenant-key-topology-managed-by-microsoft-the-default-or-managed-by-you-byok) i chcesz przesłać go przez Internet zamiast przyjeżdżać do biura firmy Microsoft w celu osobistego przekazania go, wykonaj następujące czynności:


## Przygotowanie stacji roboczej podłączonej do Internetu
Aby przygotować stację roboczą podłączoną do Internetu, wykonaj poniższe trzy kroki:

-   [Krok 1. Zainstalowanie programu Windows PowerShell dla usługi Azure Rights Management](#step-1-install-windows-powershell-for-azure-rights-management)

-   [Krok 2. Uzyskanie identyfikatora dzierżawy usługi Azure Active Directory](#step-2-get-your-azure-active-directory-tenant-id)

-   [Krok 3. Pobranie zestawu narzędzi BYOK](#step-3-download-the-byok-toolset)

### Krok 1. Zainstalowanie programu Windows PowerShell dla usługi Azure Rights Management
Z poziomu stacji roboczej podłączonej do Internetu pobierz i zainstaluj moduł Windows PowerShell dla usługi Azure Rights Management.

> [!NOTE]
> Jeśli wcześniej pobrano ten moduł programu Windows PowerShell, uruchom następujące polecenie, aby sprawdzić, czy dostępna jest wersja 2.1.0.0 lub nowsza: `(Get-Module aadrm -ListAvailable).Version`

Aby uzyskać instrukcje instalacji, zobacz [Instalowanie programu Windows PowerShell dla usługi Azure Rights Management](../deploy-use/install-powershell.md).

### Krok 2: Uzyskanie identyfikatora dzierżawy usługi Azure Active Directory
Uruchom program Windows PowerShell za pomocą polecenia **Uruchom jako administrator**, a następnie uruchom poniższe polecenia:

-   Użyj polecenia cmdlet [Connect-AadrmService](http://msdn.microsoft.com/library/windowsazure/dn629415.aspx), aby połączyć się z usługą Azure RMS:

    ```
    Connect-AadrmService
    ```
    Po wyświetleniu monitu wprowadź poświadczenia administratora dzierżawy usługi [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] (zazwyczaj jest używane konto administratora globalnego usługi Azure Active Directory lub Office 365).

-   Użyj polecenia cmdlet [Get-AadrmConfiguration](http://msdn.microsoft.com/library/windowsazure/dn629410.aspx), aby wyświetlić konfigurację dzierżawy:

    ```
    Get-AadrmConfiguration
    ```
    Zapisz identyfikator GUID z pierwszego wiersza (BPOSId) danych wyjściowych. Jest to identyfikator dzierżawy usługi Azure Active Directory, który później będzie trzeba podać podczas przygotowywania klucza dzierżawy do przesłania.

-   Użyj polecenia cmdlet [Disconnect-AadrmService](http://msdn.microsoft.com/library/windowsazure/dn629416.aspx), aby zakończyć połączenie z usługą Azure RMS do czasu zakończenia przygotowań do przesłania klucza:

    ```
    Disconnect-AadrmService
    ```

Nie zamykaj okna programu Windows PowerShell.

### Krok 3. Pobranie zestawu narzędzi BYOK
Przejdź do Centrum pobierania Microsoft i [pobierz zestaw narzędzi BYOK](http://go.microsoft.com/fwlink/?LinkId=335781) dla odpowiedniego regionu:

|Region|Nazwa pakietu|
|----------|----------------|
|Ameryka Północna|AzureRMS-BYOK-tools-UnitedStates.zip|
|Europa|AzureRMS-BYOK-tools-Europe.zip|
|Azja|AzureRMS-BYOK-tools-AsiaPacific.zip|
Zestaw narzędzi zawiera następujące pozycje:

-   Pakiet klucza wymiany klucza (KEK), którego nazwa zaczyna się od **BYOK-KEK-pkg-**.

-   Pakiet środowiska zabezpieczeń Security World, którego nazwa zaczyna się od **BYOK-SecurityWorld-pkg-**.

-   Skrypt w języku python o nazwie **verifykeypackage.py**.

-   Plik wykonywalny wiersza polecenia o nazwie **KeyTransferRemote.exe**, plik metadanych o nazwie **KeyTransferRemote.exe.config** oraz powiązane biblioteki dll.

-   Pakiet redystrybucyjny Visual C++ o nazwie **vcredist_x64.exe**.

Skopiuj pakiet na dysk USB lub do innego przenośnego urządzenia pamięci masowej.

## Przygotowanie odłączonej stacji roboczej
Aby przygotować stację roboczą, która nie jest podłączona do sieci (Internetu lub sieci wewnętrznej), należy wykonać poniższe dwa kroki:

-   [Krok 1. Przygotowanie odłączonej stacji roboczej z użyciem modułu HSM firmy Thales](#step-1-prepare-the-disconnected-workstation-with-thales-hsm)

-   [Krok 2. Instalacja zestawu narzędzi BYOK na odłączonej stacji roboczej](#step-2-install-the-byok-toolset-on-the-disconnected-workstation)

### Krok 1. Przygotowanie odłączonej stacji roboczej z użyciem modułu HSM firmy Thales
Na odłączonej stacji roboczej będącej komputerem z systemem Windows zainstaluj oprogramowanie wspomagające nCipher firmy Thales, a następnie podłącz do tego komputera sprzętowy moduł zabezpieczeń (HSM, hardware security module) firmy Thales.

Upewnij się, że narzędzia firmy Thales znajdują się w ścieżce **%nfast_home%\bin** i **%nfast_home%\python\bin**. W wierszu polecenia można wprowadź na przykład następujący tekst:

```
set PATH=%PATH%;”%nfast_home%\bin”;”%nfast_home%\python\bin”
```
Więcej informacji znajduje się w podręczniku użytkownika dołączonym do sprzętowego modułu zabezpieczeń firmy Thales oraz w witrynie sieci Web firmy Thales poświęconej usłudze Azure RMS, dostępnej pod adresem [http://www.thales-esecurity.com/msrms/cloud](http://www.thales-esecurity.com/msrms/cloud).

### Krok 2: Instalacja zestawu narzędzi BYOK na odłączonej stacji roboczej
Skopiuj pakiet zestawu narzędzi BYOK z dysku USB lub innego przenośnego urządzenia pamięci masowej, a następnie wykonaj następujące czynności:

1.  Wyodrębnij pliki z pobranego pakietu do dowolnego folderu.

2.  Z poziomu tego folderu uruchom plik vcredist_x64.exe.

3.  Postępuj zgodnie z instrukcjami instalacji składników środowiska uruchomieniowego Visual C++ dla programu Visual Studio 2012.

## Generowanie klucza dzierżawy
Na odłączonej stacji roboczej wykonaj następujące trzy kroki, aby wygenerować własny klucz dzierżawy:

-   [Krok 1. Utworzenie środowiska zabezpieczeń Security World](#step-1-create-a-security-world)

-   [Krok 2. Weryfikacja pobranego pakietu](#step-2-validate-the-downloaded-package)

-   [Krok 3. Utworzenie nowego klucza](#step-3-create-a-new-key)

### Krok 1. Utworzenie środowiska zabezpieczeń Security World
Uruchom wiersz polecenia, a następnie uruchom program firmy Thales umożliwiający utworzenie nowego środowiska (new-world).

```
new-world.exe --initialize --cipher-suite=DLf1024s160mRijndael --module=1 --acs-quorum=2/3
```
Uruchomienie programu powoduje utworzenie pliku **Security World** w lokalizacji %NFAST_KMDATA%\local\world, co odpowiada lokalizacji folderu C:\ProgramData\nCipher\Key Management Data\local. Można użyć różnych wartości dla kworum. W naszym przykładzie zostanie jednak wyświetlony monit o użycie trzech pustych kart oraz kodów PIN dla każdej z nich. Następnie dowolne dwie spośród kart będą wymagane w celu zapewnienia dostępu administracyjnego do środowiska zabezpieczeń Security World (określone kworum).  Karty te tworzą od tej chwili **zestaw kart administratora** nowego środowiska zabezpieczeń Security World. Na tym etapie można określić hasła lub kody PIN dla każdej karty z zestawu kart administratora. Hasło lub kod PIN można dodać także później, korzystając z polecenia.

> [!TIP]
> Bieżący stan konfiguracji modułu HSM można sprawdzić za pomocą polecenia `nkminfo`.

Następnie wykonaj następujące czynności:

1.  Zainstaluj dostawcę kluczy CNG firmy Thales, postępując zgodnie z instrukcjami zawartymi w dokumentacji dostarczonej przez firmę Thales, a następnie skonfiguruj go pod kątem użycia nowego środowiska zabezpieczeń Security World.

2.  Utwórz kopię zapasową pliku środowiska w lokalizacji **%nfast_kmdata%\local**. Zabezpiecz i chroń plik środowiska zabezpieczeń, karty administratora oraz ich kody PIN, a także upewnij się, że nikt nie ma dostępu do więcej niż jednej karty.

### Krok 2. Weryfikacja pobranego pakietu
Ta czynność jest opcjonalna, ale zaleca się jej wykonanie w celu upewnienia się, że:

-   Klucz wymiany klucza uwzględniony w zestawie narzędzi został wygenerowany w oryginalnym module HSM firmy Thales.

-   Skrót środowiska zabezpieczeń Security World usługi Azure RMS uwzględniony w zestawie narzędzi został wygenerowany w oryginalnym module HSM firmy Thales.

-   Klucz wymiany klucza nie może zostać wyeksportowany.

> [!NOTE]
> Aby można było zweryfikować pobrany pakiet, moduł HSM musi być podłączony i włączony oraz musi być w nim dostępne środowisko zabezpieczeń Security World (np. to, które zostało wcześniej utworzone).

#### Aby zweryfikować pobrany pakiet

1.  Uruchom skrypt verifykeypackage.py, wpisując jedno z poniższych poleceń, w zależności od regionu:

    -   Dla Ameryki Północnej:

        ```
        python verifykeypackage.py -k BYOK-KEK-pkg-NA-1 -w BYOK-SecurityWorld-pkg-NA-1
        ```

    -   Dla Europy:

        ```
        python verifykeypackage.py -k BYOK-KEK-pkg-EU-1 -w BYOK-SecurityWorld-pkg-EU-1
        ```

    -   Dla Azji:

        ```
        python verifykeypackage.py -k BYOK-KEK-pkg-AP-1 -w BYOK-SecurityWorld-pkg-AP-1
        ```

    > [!TIP]
    > Oprogramowanie firmy Thales obejmuje interpreter języka Python dostępny w lokalizacji %NFAST_HOME%\python\bin.

2.  Upewnij się, że widoczny jest następujący komunikat, który potwierdza pomyślny wynik weryfikacji: **Result: SUCCESS** (Wynik: POWODZENIE).

Ten skrypt sprawdza łańcuch osoby podpisującej aż do klucza głównego firmy Thales. Skrót klucza głównego jest osadzony w skrypcie; jego wartość powinna wynosić **59178a47 de508c3f 291277ee 184f46c4 f1d9c639**. Można również potwierdzić samą tę wartość, odwiedzając [witrynę sieci Web firmy Thales](http://www.thalesesec.com/).

Możesz teraz utworzyć nowy klucz, który będzie pełnił rolę klucza dzierżawy usługi RMS.

### Krok 3. Utworzenie nowego klucza
Wygeneruj klucz CNG, korzystając z programów **generatekey** i **cngimport** firmy Thales.

Uruchom następujące polecenie, aby wygenerować klucz:

```
generatekey --generate simple type=RSA size=2048 protect=module ident=contosokey plainname=contosokey nvram=no pubexp=
```
Podczas uruchamiania tego polecenia należy zastosować się do następujących instrukcji:

-   Parametr **protect** musi mieć ustawioną wartość **module**, jak przedstawiono. Spowoduje to utworzenie klucza chronionego przez moduł. Zestaw narzędzi BYOK nie obsługuje kluczy chronionych z użyciem protokołu OCS.

-   Zalecamy zastosowanie klucza 2048-bitowego. Obsługiwane są jednak także 1024-bitowe klucze RSA istniejących klientów usługi AD RMS, którzy korzystają z takich kluczy i mają zamiar dokonać migracji do usługi Azure RMS.

-   Zamień wartość *contosokey* dla pozycji **ident** i **plainname** na dowolną wartość ciągu. Aby zminimalizować ogólne koszty administracyjne i zmniejszyć ryzyko błędów, zaleca się użycie dla obu pozycji tej samej wartości, zapisanej wyłącznie małymi literami.

-   W tym przykładzie parametr pubexp został pozostawiony pusty (wartość domyślna), można jednak określić konkretne jego wartości. Więcej informacji znajduje się w dokumentacji firmy Thales.

Następnie uruchom poniższe polecenie, aby zaimportować klucz do funkcji CNG:

```
cngimport --import -M --key=contosokey --appname=simple contosokey
```
Podczas uruchamiania tego polecenia należy zastosować się do następujących instrukcji:

-   Wartość *contosokey* zastąp taką samą wartością, jak ta podana w czynności [Krok 1. Utworzenie środowiska zabezpieczeń Security World](#step-1-create-a-security-world) w sekcji *Generowanie klucza dzierżawy*.

-   Użyj opcji **-M**, aby przystosować klucz do użycia w tym scenariuszu. W przeciwnym razie uzyskany klucz będzie kluczem utworzonym dla konkretnego (bieżącego) użytkownika.

-   Wartość opcji **appname** odpowiada nazwie aplikacji znajdującej się w pliku klucza. W instrukcjach mających na celu utworzenie nowego klucza użyto wartości „simple”, jak zostało to pokazane w poleceniu. Podczas migracji istniejącego klucza chronionego przez moduł HSM w celu przeprowadzenia migracji z usługi AD RMS do usługi Azure RMS należy określić istniejącą nazwę w treści tego polecenia oraz kolejnych poleceń korzystających z opcji appname.

To polecenie tworzy plik stokenizowanego klucza w folderze %NFAST_KMDATA%\local. Nazwa pliku zaczyna się od ciągu znaków **key_caping`_`**, po którym następuje identyfikator SID. Na przykład: **key_caping_machine--801c1a878c925fd9df4d62ba001b94701c039e2fb**. Ten plik zawiera zaszyfrowany klucz.

> [!TIP]
> Bieżący stan konfiguracji kluczy można sprawdzić za pomocą polecenia `nkminfo –k`.

Utwórz w bezpiecznej lokalizacji kopię zapasową tego pliku stokenizowanego klucza.

> [!IMPORTANT]
> Po późniejszym przekazaniu klucza do usługi Azure RMS firma Microsoft nie może wyeksportować tego klucza z powrotem, w związku z czym tak ważne jest wykonanie i bezpieczne przechowywanie kopii zapasowej klucza oraz środowiska zabezpieczeń Security World. Skontaktuj się z firmą Thales w celu uzyskania wskazówek i najlepszych rozwiązań dotyczących tworzenia kopii zapasowej klucza.

Teraz można przystąpić do przekazania klucza dzierżawy do usługi Azure RMS.

## Przygotowanie klucza dzierżawy do przekazania
Na odłączonej stacji roboczej wykonaj następujące 4 kroki, aby przygotować klucz dzierżawy:

-   [Krok 1. Utworzenie kopii klucza z ograniczonymi uprawnieniami](#step-1-create-a-copy-of-your-key-with-reduced-permissions)

-   [Krok 2. Sprawdzenie nowej kopii klucza](#step-2-inspect-the-new-copy-of-the-key)

-   [Krok 3. Zaszyfrowanie klucza przy użyciu klucza wymiany kluczy firmy Microsoft](#step-3-encrypt-your-key-by-using-microsoft-s-key-exchange-key)

-   [Krok 4. Skopiowanie pakietu przekazywania klucza na podłączoną do Internetu stację roboczą](#step-4-copy-your-key-transfer-package-to-the-internet-connected-workstation)

### Krok 1. Utworzenie kopii klucza z ograniczonymi uprawnieniami
Aby ograniczyć uprawnienia mające zastosowanie w przypadku danego klucza dzierżawy, wykonaj następujące czynności:

-   W wierszu polecenia uruchom jedno z następujących poleceń, w zależności od regionu:

    -   Dla Ameryki Północnej:

        ```
        KeyTransferRemote.exe -ModifyAcls -KeyAppName simple -KeyIdentifier contosokey -ExchangeKeyPackage BYOK-KEK-pkg-NA-1 -NewSecurityWorldPackage BYOK-SecurityWorld-pkg-NA-1
        ```

    -   Dla Europy:

        ```
        KeyTransferRemote.exe -ModifyAcls -KeyAppName simple -KeyIdentifier contosokey -ExchangeKeyPackage BYOK-KEK-pkg-EU-1 -NewSecurityWorldPackage BYOK-SecurityWorld-pkg-EU-1
        ```

    -   Dla Azji:

        ```
        KeyTransferRemote.exe -ModifyAcls -KeyAppName simple -KeyIdentifier contosokey -ExchangeKeyPackage BYOK-KEK-pkg-AP-1 -NewSecurityWorldPackage BYOK-SecurityWorld-pkg-AP-1
        ```

Podczas uruchamiania tego polecenia zastąp wartość *contosokey* taką samą wartością jak ta podana w czynności [Krok 1. Utworzenie środowiska zabezpieczeń Security World](#step-1-create-a-security-world) w sekcji *Generowanie klucza dzierżawy*.

Zostanie wyświetlona prośba o podłączenie kart z zestawu kart administratora środowiska zabezpieczeń oraz wpisanie ich haseł lub numerów PIN, jeśli je określono.

Po zakończeniu wykonywania polecenia zostanie wyświetlony komunikat **Result: SUCCESS** (Wynik: POWODZENIE), a kopia klucza dzierżawy z ograniczonymi uprawnieniami zostanie umieszczona w pliku o nazwie key_xferacId_*&lt;contosokey&gt;*.

### Krok 2. Sprawdzenie nowej kopii klucza
Opcjonalnie możesz uruchomić narzędzia firmy Thales, aby potwierdzić minimalne uprawnienia odnoszące się do nowego klucza dzierżawy:

-   aclprint.py:

    ```
    "%nfast_home%\bin\preload.exe" -m 1 -A xferacld -K contosokey "%nfast_home%\python\bin\python" "%nfast_home%\python\examples\aclprint.py"
    ```

-   kmfile-dump.exe:

    ```
    "%nfast_home%\bin\kmfile-dump.exe" "%NFAST_KMDATA%\local\key_xferacld_contosokey"
    ```

Podczas uruchamiania tego polecenia zastąp wartość *contosokey* taką samą wartością jak ta podana w czynności [Krok 1. Utworzenie środowiska zabezpieczeń Security World](#step-1-create-a-security-world) w sekcji *Generowanie klucza dzierżawy*.

### Krok 3. Zaszyfrowanie klucza przy użyciu klucza wymiany kluczy firmy Microsoft
Uruchom jedno z następujących poleceń, w zależności od regionu:

-   Dla Ameryki Północnej:

    ```
    KeyTransferRemote.exe -Package -KeyIdentifier contosokey -ExchangeKeyPackage BYOK-KEK-pkg-NA-1 -NewSecurityWorldPackage BYOK-SecurityWorld-pkg-NA-1 -TenantBposId GUID -KeyFriendlyName ContosoFirstkey
    ```

-   Dla Europy:

    ```
    KeyTransferRemote.exe -Package -KeyIdentifier contosokey -ExchangeKeyPackage BYOK-KEK-pkg-EU-1 -NewSecurityWorldPackage BYOK-SecurityWorld-pkg-EU-1 -TenantBposId GUID -KeyFriendlyName ContosoFirstkey
    ```

-   Dla Azji:

    ```
    KeyTransferRemote.exe -Package -KeyIdentifier contosokey -ExchangeKeyPackage BYOK-KEK-pkg-AP-1 -NewSecurityWorldPackage BYOK-SecurityWorld-pkg-AP-1 -TenantBposId GUID -KeyFriendlyName ContosoFirstkey
    ```

Podczas uruchamiania tego polecenia należy zastosować się do następujących instrukcji:

-   Zastąp wartość *contosokey* identyfikatorem użytym do wygenerowania klucza w ramach czynności [Krok 1. Utworzenie środowiska zabezpieczeń Security World](#step-1-create-a-security-world) w sekcji *Generowanie klucza dzierżawy*.

-   Zastąp identyfikator *GUID* identyfikatorem dzierżawy usługi Azure Active Directory, który uzyskano, wykonując czynność [Krok 2. Uzyskanie identyfikatora dzierżawy usługi Azure Active Directory](#step-2-get-your-azure-active-directory-tenant-id) w sekcji *Przygotowanie stacji roboczej podłączonej do Internetu*.

-   Zastąp wartość *ContosoFirstKey* etykietą, która będzie używana jako nazwa pliku wyjściowego.

Po pomyślnym zakończeniu zostanie wyświetlony komunikat **Result: SUCCESS** (Wynik: POWODZENIE), a w bieżącym folderze znajdzie się nowy plik o nazwie TransferPackage-*ContosoFirstkey*.byok.

### Krok 4. Skopiowanie pakietu przekazywania klucza na podłączoną do Internetu stację roboczą
Za pomocą dysku USB lub innego przenośnego urządzenia pamięci masowej skopiuj plik wyjściowy z poprzedniego kroku (KeyTransferPackage-*ContosoFirstkey*.byok) na stację roboczą podłączoną do Internetu.

> [!NOTE]
> Ten plik zawiera Twój klucz prywatny, w związku z czym należy chronić go, stosując zasady zapewniania bezpieczeństwa.

## Przekazywanie klucza dzierżawy do usługi Azure RMS
Wykonaj poniższe trzy kroki z poziomu stacji roboczej podłączonej do Internetu, aby przekazać nowy klucz dzierżawy do usługi Azure RMS:

-   [Krok 1. Nawiązanie połączenia z usługą Azure RMS](#step-1-connect-to-azure-rms)

-   [Krok 2. Przesłanie pakietu klucza](#step-2-upload-the-key-package)

-   [Krok 3. Wyliczenie kluczy dzierżawy — w razie potrzeby](#step-3-enumerate-your-tenant-keys-as-needed)

### Krok 1. Nawiązanie połączenia z usługą Azure RMS
Powróć do okna programu Windows PowerShell i wpisz następujące polecenie:

1.  Ponownie nawiąż połączenie z usługą [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)]:

    ```
    Connect-AadrmService
    ```

2.  Użyj polecenia cmdlet [Get-AadrmKeys](http://msdn.microsoft.com/library/windowsazure/dn629420.aspx), aby wyświetlić bieżącą konfigurację klucza dzierżawy:

    ```
    Get-AadrmKeys
    ```

### Krok 2. Przesłanie pakietu klucza
Użyj polecenia cmdlet [Add-AadrmKey](http://msdn.microsoft.com/library/windowsazure/dn629418.aspx), aby przesłać pakiet przekazywania klucza skopiowany z odłączonej stacji roboczej:

```
Add-AadrmKey –KeyFile <PathToPackageFile> -Verbose
```
> [!WARNING]
> Zostanie wyświetlony monit o potwierdzenie tej akcji. Należy pamiętać, że tej akcji nie można cofnąć. Przesłany klucz dzierżawy automatycznie staje się podstawowym kluczem dzierżawy organizacji, który będzie używany przez użytkowników zabezpieczających dokumenty i pliki.

Jeśli przesyłanie zakończy się pomyślnie, zostanie wyświetlony następujący komunikat: **The Rights management service successfully added the key** (Klucz został pomyślnie dodany w usłudze Rights Management Service).

Można spodziewać się pewnych opóźnień wynikających z konieczności przeprowadzenia replikacji, w wyniku której zmiana obejmie wszystkie centra danych [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)].

### Krok 3. Wyliczenie kluczy dzierżawy — w razie potrzeby
Ponownie użyj polecenia cmdlet Get-AadrmKeys, aby zobaczyć zmianę klucza dzierżawy. Polecenie pozwala także w dowolnym momencie wyświetlić listę kluczy dzierżawy. Wyświetlone z jego użyciem klucze dzierżawy obejmują początkowy klucz dzierżawy wygenerowany przez firmę Microsoft oraz klucze dzierżawy dodane przez użytkownika:

```
Get-AadrmKeys
```
Klucz dzierżawy z oznaczeniem **Active** (Aktywny) to klucz aktualnie używany przez organizację do ochrony dokumentów i plików.

Wykonanie tych czynności kończy procedurę przekazywania własnego klucza przez Internet, po przeprowadzeniu której użytkownik może przejść do następnych kroków planowania i implementowania klucza dzierżawy.


> [!div class="button"]
[Następne kroki >>](plan-implement-tenant-key.md#next-steps)





<!--HONumber=Jul16_HO3-->


