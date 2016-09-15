---
title: "Rejestrowanie i analizowanie danych użycia usługi Azure Rights Management | Azure RMS"
description: 
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 08/17/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: a735f3f7-6eb2-4901-9084-8c3cd3a9087e
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 437afd88efebd9719a3db98f8ab0ae07403053f7
ms.openlocfilehash: 28fed61b674112d2ebeb30a15a6f6217647e0b5f


---

# Rejestrowanie i analizowanie danych użycia usługi Azure Rights Management

*Dotyczy usług: Azure Rights Management, Office 365*

Informacje zawarte w tym temacie pozwalają zrozumieć sposób korzystania z funkcji rejestrowania użycia usługi Azure Rights Management (Azure RMS). Usługa Azure Rights Management może rejestrować wszystkie żądania obsługiwane dla danej organizacji, w tym żądania od użytkowników, akcje wykonywane przez administratorów usługi Rights Management w organizacji oraz akcje wykonywane przez operatorów firmy Microsoft w celu obsługi wdrożenia usługi Azure Rights Management.

Dzienniki usługi Azure Rights Management można wykorzystać na potrzeby następujących scenariuszy biznesowych:

-   **Analiza danych biznesowych**

    Dzienniki generowane przez usługę Azure Rights Management można zaimportować do wybranego przez użytkownika repozytorium (na przykład bazy danych, systemu przetwarzania analitycznego online (OLAP) lub systemu MapReduce) w celu analizowania danych i tworzenia raportów. Na przykład można zidentyfikować osoby, które uzyskują dostęp do danych chronionych przez usługę RMS. Można określić, do jakich chronionych danych, z jakich urządzeń i z jakich lokalizacji użytkownicy uzyskują dostęp. Można ustalić, czy użytkownicy są w stanie pomyślnie odczytywać zawartość chronioną. Można również zidentyfikować osoby, które odczytały ważny dokument objęty ochroną.

-   **Monitorowanie nadużyć**

    Dane rejestrowania usługi Azure Rights Management są dostępne w czasie niemal rzeczywistym, co pozwala na stałe monitorowanie użycia usługi Rights Management w firmie. 99,9% dzienników jest dostępnych w ciągu 15 minut od akcji zainicjowanej przez usługę RMS.

    Na przykład można otrzymywać alerty w przypadku nagłego wzrostu liczby osób odczytujących dane chronione przez usługę RMS poza standardowymi godzinami pracy, co mogłoby wskazywać, że złośliwy użytkownik gromadzi informacje, aby je sprzedać konkurencji. Można też wykryć sytuację, w której ten sam użytkownik w krótkim czasie uzyskuje dostęp do danych z dwóch różnych adresów IP, co mogłoby oznaczać naruszenie zabezpieczeń konta użytkownika.

-   **Wykonywanie analizy śledczej**

    W przypadku wycieku informacji prawdopodobnie pojawi się pytanie, kto ostatnio uzyskiwał dostęp do określonych dokumentów i z jakich informacji korzystała ostatnio podejrzana osoba. Korzystanie z usługi Azure Rights Management i funkcji rejestrowania pozwala odpowiedzieć na tego rodzaju pytania, ponieważ osoby korzystające z zawartości chronionej muszą zawsze uzyskać licencję usługi Rights Management, aby otworzyć dokumenty i obrazy chronione przez usługę Azure Rights Management, nawet jeśli te pliki są przesyłane pocztą e-mail lub kopiowane na dyski USB lub inne urządzenia pamięci masowej. Oznacza to, że dzienniki usługi Azure Rights Management mogą służyć jako ostateczne źródło informacji dla analizy śledczej w przypadku, gdy dane są chronione przy użyciu usługi Azure Rights Management.

> [!NOTE]
> Jeśli interesuje Cię tylko rejestrowanie zadań administracyjnych dotyczących usługi Azure Rights Management i nie chcesz śledzić korzystania z usługi Rights Management przez użytkowników, możesz użyć polecenia cmdlet [Get-AadrmAdminLog](https://msdn.microsoft.com/library/azure/dn629430.aspx) programu Windows PowerShell dla usługi Azure Rights Management.
> 
> Możesz także skorzystać z klasycznego portalu Azure w celu uzyskania podstawowych raportów użycia, które obejmują takie informacje, jak **podsumowanie usługi RMS**, **aktywni użytkownicy usługi RMS**, **platforma urządzeń usługi RMS** i **użycie aplikacji usługi RMS**. Aby uzyskać dostęp do tych raportów z klasycznego portalu Azure, kliknij opcję **Active Directory**, wybierz i otwórz katalog, a następnie kliknij opcję **RAPORTY**,

Więcej informacji na temat rejestrowania użycia usługi Azure Rights Management można znaleźć w sekcjach poniżej.

## Włączanie rejestrowania użycia usługi Azure Rights Management
Od lutego 2016 r. rejestrowanie użycia usługi Azure Rights Management jest domyślnie włączone dla wszystkich klientów. Dotyczy to klientów, którzy aktywowali usługę Azure RMS przed lutym 2016 r., oraz klientów, którzy aktywowali usługę po lutym 2016 r. 

> [!NOTE]
> Przechowywanie dziennika lub korzystanie z funkcji rejestrowania nie wiąże się z żadnymi dodatkowymi kosztami.
> 
> Do korzystania z funkcji rejestrowania użycia usługi Azure RMS przed lutym 2016 r. potrzebna była subskrypcja usługi Azure oraz wystarczająca ilość miejsca w magazynie Azure, które nie są już wymagane.



## Uzyskiwanie dostępu i korzystanie z dzienników użycia usługi Azure Rights Management
Usługa Azure Rights Management zapisuje dzienniki na koncie magazynu Azure w postaci serii obiektów blob. Każdy obiekt blob zawiera jeden lub większą liczbę rekordów w rozszerzonym formacie W3C dziennika. Nazwy obiektów blob są liczbami odpowiadającymi kolejności ich utworzenia. Sekcja [Interpretowanie dzienników użycia usługi Azure Rights Management](#how-to-interpret-your-azure-rights-management-usage-logs) w dalszej części tego dokumentu zawiera więcej informacji na temat zawartości dzienników i ich tworzenia.

Może upłynąć trochę czasu zanim dzienniki będą widoczne na koncie magazynu po akcji usługi Azure Rights Management. Większość dzienników pojawia się w ciągu 15 minut. Zalecamy pobranie dzienników do lokalnego magazynu, na przykład folderu lokalnego, bazy danych lub repozytorium MapReduce.

Aby pobrać dzienniki użycia, należy skorzystać z modułu administracyjnego usługi Azure RMS dla programu Windows PowerShell. Instrukcje instalacji znajdują się w sekcji [Instalowanie programu Windows PowerShell dla usługi Azure Rights Management](install-powershell.md). Jeśli ten moduł programu Windows PowerShell został już wcześniej pobrany, wykonaj następujące polecenie, aby sprawdzić, czy numer wersji nie jest niższy niż **2.4.0.0**: `(Get-Module aadrm -ListAvailable).Version` 

### Pobieranie dzienników użycia za pomocą programu PowerShell

1.  Uruchom program Windows PowerShell z opcją **Uruchom jako administrator** i wykonaj polecenie cmdlet [Connect AadrmService](https://msdn.microsoft.com/library/azure/dn629415.aspx), aby nawiązać połączenie z usługą Azure Rights Management:

    ```
    Connect-AadrmService
    ```
    
2.  Wykonaj następujące polecenie, aby pobrać dzienniki dotyczące określonej daty: 

    ```
    Get-AadrmUserLog -Path <location> -fordate <date>
    ```

    Na przykład po utworzeniu folderu o nazwie Dzienniki na dysku E:
    
    * Aby pobrać dzienniki dotyczące określonej daty (na przykład 1.02.2016), wykonaj następujące polecenia: `Get-AadrmUserLog -Path E:\Logs -fordate 2/1/2016`
    
    * Aby pobrać dzienniki dotyczące zakresu dat (np. od 1.02.2016 do 14.02.2016), wykonaj następujące polecenie: `Get-AadrmUserLog -Path E:\Logs -fromdate 2/1/2016 –todate 2/14/2016` 

Po określeniu tylko dnia, jak w naszych przykładach, przyjmuje się godzinę 00:00:00 w formacie czasu lokalnego, która jest następnie konwertowana na czas UTC. Po określeniu godziny przy użyciu parametrów -fromdate lub -todate (na przykład -fromdate „2/1/2016 15:00:00”), podane data i godzina są konwertowane na czas UTC. Polecenie Get-AadrmUserLog pobiera następnie dzienniki dla tego przedziału czasu UTC.

Nie można określić okresu krótszego niż cały dzień do pobrania.

Domyślnie to polecenie cmdlet używa trzech wątków do pobierania dzienników. Jeśli przepustowość sieci jest wystarczająca i chcesz skrócić czas wymagany do pobrania dzienników, użyj parametru -NumberOfThreads, który może przybierać wartość z zakresu od 1 do 32. Na przykład uruchomienie następującego polecenia cmdlet spowoduje utworzenie 10 wątków do pobierania dzienników: `Get-AadrmUserLog -Path E:\Logs -fromdate 2/1/2016 –todate 2/14/2016 -numberofthreads 10`


> [!TIP]
> Wszystkie pobrane pliki dziennika można zagregować do formatu CSV przy użyciu narzędzia [Log Parser firmy Microsoft](https://www.microsoft.com/download/details.aspx?id=24659), które umożliwia konwersję pomiędzy różnymi znanymi formatami dziennika. Można również skorzystać z narzędzia do konwersji danych do formatu SYSLOG lub importować dzienniki do bazy danych. Po zainstalowaniu narzędzia uruchom polecenie `LogParser.exe /?` w celu uzyskania pomocy i informacji na temat sposobu jego używania. 
>
> Można na przykład wykonać następujące polecenie, aby zaimportować wszystkie informacje do formatu pliku LOG: `logparser –i:w3c –o:csv "SELECT * INTO AllLogs.csv FROM *.log"`

#### Jeśli rejestrowanie użycia usługi Azure RMS zostało włączone ręcznie przed zmianą funkcji rejestrowania w dniu 22 lutego 2016 r.


Jeśli rejestrowanie użycia było wykorzystywane przed zmianą rejestrowania, dzienniki użycia będą znajdowały się na Twoim skonfigurowanym koncie magazynu Azure. Firma Microsoft nie skopiuje tych dzienników z Twojego konta magazynu do nowego zarządzanego konta magazynu usługi Azure RMS w ramach zmiany funkcji rejestrowania. Za zarządzanie cyklem życia wcześniej wygenerowanych dzienników odpowiedzialni są użytkownicy. Można wykonać polecenie cmdlet [Get-AadrmUsageLog](https://msdn.microsoft.com/library/dn629401.aspx) polecenia cmdlet, aby pobrać stare dzienniki. Na przykład:

- Aby pobrać wszystkie dzienniki dostępne w folderze E:\logs: `Get-AadrmUsageLog -Path "E:\Logs"`
    
- Aby pobrać określony zakres obiektów blob: `Get-AadrmUsageLog –Path "E:\Logs" –FromCounter 1024 –ToCounter 2047`

Należy zauważyć, że nie trzeba pobierać dzienników przy użyciu polecenia cmdlet Get-AadrmUsageLog, jeśli została wykonana jedna z następujących czynności:

-  Usługa Azure Rights Management została aktywowana w dniu 22 lutego 2016 r. lub wcześniej, ale nie została włączona funkcja rejestrowania użycia.

- Usługa Azure Rights Management została aktywowana po 22 lutego 2016 r.

## Interpretowanie dzienników użycia usługi Azure Rights Management
Poniższe informacji mogą ułatwić interpretowanie dzienników użycia usługi Azure Rights Management.

### Sekwencja dzienników
Usługa Azure Rights Management zapisuje dzienniki w postaci serii obiektów blob. 

Każdy wpis w dzienniku ma sygnaturę czasową UTC. Ponieważ usługa Azure Rights Management działa na wielu serwerach w wielu centrach danych, czasami dzienniki mogą wydawać się ułożone nie po kolei, nawet jeśli są posortowane według sygnatur czasowych. Jednak różnica jest mała i zazwyczaj mieści się zakresie jednej minuty. W większości przypadków nie jest to kwestia, która mogłaby stanowić problem podczas analizy dziennika.

### Format obiektów blob
Każdy obiekt blob jest w rozszerzonym formacie W3C dziennika. Rozpoczyna się od następujących dwóch wierszy:

**#Software: RMS**

**#Version: 1.1**

Pierwszy wiersz określa, że są to dzienniki usługi Azure Rights Management. Drugi wiersz wskazuje, że pozostała część obiektu blob odpowiada specyfikacji wersji 1.1. Zaleca się, aby wszystkie aplikacje, które analizują te dzienniki, sprawdziły te dwa wiersze przed kontynuowaniem analizowania pozostałej części obiektu blob.

Trzeci wiersz wylicza listę nazw pól rozdzielonych znakami tabulatora:

**#Pola: date            time            row-id        request-type           user-id       result          correlation-id          content-id                owner-email           issuer                     template-id             file-name                  date-published      c-info         c-ip            admin-action            acting-as-user**

Każdy z kolejnych wierszy jest rekordem dziennika. Wartości pól są zapisane w takiej samej kolejności, jak poprzedni wiersz, i są rozdzielone znakami tabulatora. Podczas interpretowania pól skorzystaj z poniższej tabeli.

|Nazwa pola|Typ danych W3C|Opis|Przykładowa wartość|
|--------------|-----------------|---------------|-----------------|
|date|Data|Data obsługi żądania w formacie UTC.<br /><br />Źródłem jest zegar lokalny na serwerze, który obsłużył żądanie.|2013-06-25|
|time|Godzina|Czas obsługi żądania w 24-godzinnym formacie UTC.<br /><br />Źródłem jest zegar lokalny na serwerze, który obsłużył żądanie.|21:59:28|
|row-id|Tekst|Unikatowy identyfikator GUID dla tego rekordu dziennika. Jeśli ta wartość nie została podana, użyj wartości correlation-id do zidentyfikowania wpisu.<br /><br />Ta wartość jest przydatna przy agregowaniu dzienników lub kopiowaniu dzienników do innego formatu.|1c3fe7a9-d9e0-4654-97b7-14fafa72ea63|
|request-type|Nazwa|Nazwa żądanego interfejsu API usługi RMS.|AcquireLicense|
|user-id|String|Użytkownik, który wysłał żądanie.<br /><br />Wartość jest ujęta w cudzysłów pojedynczy. Wywołania z klucza dzierżawy, który jest zarządzany przez użytkownika (BYOK), mają wartość **"**, która ma zastosowanie również w przypadku anonimowych typów żądań.|‘joe@contoso.com’|
|result|String|‘Success’, jeśli żądanie zostało obsłużone pomyślnie.<br /><br />Typ błędu w cudzysłowie pojedynczym, jeśli żądanie zakończyło się niepowodzeniem.|'Success'|
|correlation-id|Tekst|Identyfikator GUID, który jest wspólny dla dziennika klienta usługi RMS i dziennika serwera dotyczącego danego żądania.<br /><br />Ta wartość może być przydatna do rozwiązywania problemów klienta.|cab52088-8925-4371-be34-4b71a3112356|
|content-id|Tekst|Identyfikator GUID ujęty w nawiasy klamrowe, który identyfikuje chronioną zawartość (na przykład dokument).<br /><br />To pole ma wartość tylko w przypadku typu żądania AcquireLicense w polu request-type. Dla wszystkich innych typów żądań to pole jest puste.|{bb4af47b-cfed-4719-831d-71b98191a4f2}|
|owner-email|String|Adres e-mail właściciela dokumentu.|alice@contoso.com|
|issuer|String|Adres e-mail wystawcy dokumentu.|alice@contoso.com (lub) FederatedEmail.4c1f4d-93bf-00a95fa1e042@contoso.onmicrosoft.com'|
|template-id|String|Identyfikator szablonu użytego do ochrony dokumentu.|{6d9371a6-4e2d-4e97-9a38-202233fed26e}|
|file-name|String|Nazwa pliku dokumentu objętego ochroną. <br /><br />Obecnie dla niektórych plików (takich jak dokumenty pakietu Office) są wyświetlane identyfikatory GUID, a nie rzeczywiste nazwy plików.|TopSecretDocument.docx|
|date-published|Data|Data, w której włączono ochronę dokumentu.|2015-10-15T21:37:00|
|c-info|String|Informacje o platformie klienta, z której wysłano żądanie.<br /><br />Określony ciąg znaków różni się w zależności od aplikacji (na przykład systemu operacyjnego lub przeglądarki).|'MSIPC;version=1.0.623.47;AppName=WINWORD.EXE;AppVersion=15.0.4753.1000;AppArch=x86;OSName=Windows;OSVersion=6.1.7601;OSArch=amd64'|
|c-ip|Adres|Adres IP klienta, który wysłał żądanie.|64.51.202.144|


#### Wyjątki w polu user-id
Chociaż pole user-id zwykle wskazuje użytkownika, który wysłał żądanie, istnieją dwa wyjątki, kiedy wartość w polu nie odwzorowuje rzeczywistego użytkownika:

-   Wartość **'microsoftrmsonline@&lt;ID_dzierżawy&gt;.rms.&lt;region&gt;.aadrm.com'**.

    Ta wartość oznacza, że żądanie zostało wysłane przez usługę Office 365, taką jak Exchange Online lub SharePoint Online. W podanym ciągu znaków *&lt;ID_dzierżawy&gt;* oznacza identyfikator GUID dzierżawy, a *&lt;region&gt;* oznacza region rejestracji dzierżawy. Na przykład ciąg **na** reprezentuje Amerykę Północną, **eu** określa Europę, a **ap** — Azję.

-   Jeśli używasz łącznika usługi RMS.

    Żądania z tego łącznika są rejestrowane przy użyciu nazwy głównej usługi **Aadrm_S-1-7-0**, która jest generowana automatycznie po zainstalowaniu łącznika usług RMS.

#### Popularne typy żądań
Istnieje wiele typów żądań usługi Azure Rights Management. W poniższej tabeli przedstawiono niektóre spośród najbardziej popularnych typów żądań.

|Typ żądania|Opis|
|----------------|---------------|
|AcquireLicense|Klient z komputera z systemem Windows żąda licencji dla zawartości chronionej przez usługę RMS.|
|AcquirePreLicense|Klient w imieniu użytkownika żąda licencji dla zawartości chronionej przez usługę RMS.|
|AcquireTemplates|Wykonano wywołanie pobrania szablonów na podstawie identyfikatorów szablonów.|
|AcquireTemplateInformation|Wykonano wywołanie pobrania identyfikatorów szablonu z usługi.|
|AddTemplate|Wykonano wywołanie z klasycznego portalu Azure dotyczące dodania szablonu.|
|AllDocsCsv|Wykonano wywołanie z witryny śledzenia dokumentów dotyczące pobrania pliku CSV ze strony **Wszystkie dokumenty**.|
|BECreateEndUserLicenseV1|Wykonano wywołanie z urządzenia przenośnego dotyczące utworzenia licencji użytkowania.|
|BEGetAllTemplatesV1|Wykonano wywołanie z urządzenia przenośnego (zaplecze) dotyczące pobrania wszystkich szablonów.|
|Certify|Klient certyfikuje zawartość objętą ochroną.|
|DeleteTemplateById|Wykonano wywołanie z klasycznego portalu Azure dotyczące usunięcia szablonu na podstawie identyfikatora szablonu.|
|DocumentEventsCsv|Wykonano wywołanie z witryny śledzenia dokumentów dotyczące pobrania pliku CSV dla pojedynczego dokumentu.|
|ExportTemplateById|Wykonano wywołanie z klasycznego portalu Azure dotyczące eksportowania szablonu na podstawie identyfikatora szablonu.|
|FECreateEndUserLicenseV1|Działanie podobne do typu żądania AcquireLicense, ale dotyczy urządzeń przenośnych.|
|FECreatePublishingLicenseV1|Działanie takie samo, jak połączonych typów żądań Certify i GetClientLicensorCert, ale dotyczy klientów mobilnych.|
|FEGetAllTemplates|Wykonano wywołanie z urządzenia przenośnego (fronton) dotyczące pobrania szablonów.|
|FindServiceLocationsForUser|Wykonano wywołanie kwerendy zwracającej adresy URL, które są używane do wywoływania żądań Certify lub AcquireLicense.|
|GetAllDocs|Wykonano wywołanie z witryny śledzenia dokumentów dotyczące załadowania strony **wszystkie dokumenty** dla użytkownika lub wyszukania wszystkich dokumentów dla dzierżawy. Użyj tej wartości z polami admin-action i acting-as-admin:<br /><br />— pole admin-action jest puste: użytkownik wyświetla stronę **wszystkie dokumenty** dla swoich własnych dokumentów.<br /><br />— pole admin-action ma wartość true, pole acting-as-user jest puste: administrator wyświetla wszystkie dokumenty dla swojej dzierżawy.<br /><br />— pole admin-action ma wartość true, pole acting-as-user nie jest puste: administrator wyświetla stronę **wszystkie dokumenty** dla użytkownika.|
|GetAllTemplates|Wykonano wywołanie z klasycznego portalu Azure dotyczące pobrania wszystkich szablonów.|
|GetClientLicensorCert|Klient żąda certyfikatu publikowania (który jest później używany do ochrony zawartości) z komputera z systemem Windows.|
|GetConfiguration|Wykonano wywołanie polecenia cmdlet programu Azure PowerShell w celu pobrania konfiguracji dzierżawy usługi Azure RMS.|
|GetConnectorAuthorizations|Wykonano wywołanie z łączników usługi RMS dotyczące pobrania ich konfiguracji z chmury.|
|GetRecipients|Wykonano wywołanie z witryny śledzenia dokumentów dotyczące przejścia do widoku listy dla pojedynczego dokumentu.|
|GetSingle|Wykonano wywołanie z witryny śledzenia dokumentów dotyczące przejścia do strony **pojedynczego dokumentu**.|
|GetTenantFunctionalState|Klasyczny portal Azure sprawdza, czy usługa Azure RMS jest aktywowana.|
|GetTemplateById|Wykonano wywołanie z klasycznego portalu Azure dotyczące pobrania szablonu przez określenie identyfikatora szablonu.|
|KeyVaultDecryptRequest|Klient próbuje odszyfrować zawartość chronioną przez usługę RMS. Dotyczy tylko klucza dzierżawy zarządzanego przez klienta (BYOK) w usłudze Azure Key Vault.|
|KeyVaultGetKeyInfoRequest|Wykonywane jest wywołanie, aby sprawdzić, czy klucz podany do wykorzystania w usłudze Azure Key Vault dla klucza dzierżawy usługi Azure RMS jest dostępny i czy nie jest już używany.|
|KeyVaultSignDigest|Wykonywane jest wywołanie, gdy klucz zarządzany przez klienta (BYOK) w usłudze Azure Key Vault jest używany w celu złożenia podpisu. Jest to zazwyczaj jedno wywołanie dla typów żądań AcquireLicence (lub FECreateEndUserLicenseV1), Certify i GetClientLicensorCert (lub FECreatePublishingLicenseV1).|
|KMSPDecrypt|Klient próbuje odszyfrować zawartość chronioną przez usługę RMS. Dotyczy tylko starszego klucza dzierżawy zarządzanego przez klienta (BYOK).|
|KMSPSignDigest|Wykonywane jest wywołanie, gdy starszy klucz zarządzany przez klienta (BYOK) jest używany w celu złożenia podpisu. Jest to zazwyczaj jedno wywołanie dla typów żądań AcquireLicence (lub FECreateEndUserLicenseV1), Certify i GetClientLicensorCert (lub FECreatePublishingLicenseV1).|
|LoadEventsForMap|Wykonano wywołanie z witryny śledzenia dokumentów dotyczące przejścia do widoku mapy dla pojedynczego dokumentu.|
|LoadEventsForSummary|Wykonano wywołanie z witryny śledzenia dokumentów dotyczące przejścia do widoku osi czasu dla pojedynczego dokumentu.|
|LoadEventsForTimeline|Wykonano wywołanie z witryny śledzenia dokumentów dotyczące przejścia do widoku mapy dla pojedynczego dokumentu.|
|ImportTemplate|Wykonano wywołanie z klasycznego portalu Azure dotyczące importowania szablonu.|
|RevokeAccess|Wykonano wywołanie z witryny śledzenia dokumentów dotyczące odwołania dokumentu.|
|SearchUsers |Wykonano wywołanie z witryny śledzenia dokumentów dotyczące wyszukania wszystkich użytkowników w dzierżawie.|
|ServerCertify|Wykonano wywołanie z klienta z obsługą usługi RMS (na przykład programu SharePoint) dotyczące certyfikacji serwera.|
|SetUsageLogFeatureState|Wykonano wywołanie dotyczące włączenia rejestrowania użycia.|
|SetUsageLogStorageAccount|Wykonano wywołanie dotyczące określenia lokalizacji dzienników usługi Azure RMS.|
|UpdateNotificationSettings|Wykonano wywołanie z witryny śledzenia dokumentów dotyczące zmiany ustawień powiadomień dla pojedynczego dokumentu.|
|UpdateTemplate|Wykonano wywołanie z klasycznego portalu Azure dotyczące aktualizacji istniejącego szablonu.|


## Uwagi dotyczące programu Windows PowerShell
Od lutego 2016 r. jedynym poleceniem cmdlet programu Windows PowerShell potrzebnym do rejestrowania użycia usługi Azure RMS jest [Get AadrmUserLog](https://msdn.microsoft.com/library/azure/mt653941.aspx). 

Przed wprowadzeniem tej zmiany do obsługi dzienników użycia usługi Azure RMS potrzebne były następujące polecenia cmdlet, które obecnie są przestarzałe:  

-   [Disable-AadrmUsageLogFeature](https://msdn.microsoft.com/library/azure/dn629404.aspx)

-   [Enable-AadrmUsageLogFeature](https://msdn.microsoft.com/library/azure/dn629421.aspx)

-   [Get-AadrmUsageLog](https://msdn.microsoft.com/library/azure/dn629401.aspx)

-   [Get-AadrmUsageLogFeature](https://msdn.microsoft.com/library/azure/dn629425.aspx)

-   [Get-AadrmUsageLogLastCounterValue](https://msdn.microsoft.com/library/azure/dn629423.aspx)

-   [Get-AadrmUsageLogStorageAccount](https://msdn.microsoft.com/library/azure/dn629419.aspx)

-   [Set-AadrmUsageLogStorageAccount](https://msdn.microsoft.com/library/azure/dn629426.aspx)

Jeśli masz w magazynie Azure dzienniki sprzed zmiany funkcji rejestrowania usługi Azure RMS, możesz je pobrać w taki sam sposób, jak wcześniej, korzystając z tych starszych poleceń cmdlet: Get-AadrmUsageLog i Get-AadrmUsageLogLastCounterValue. Jednak wszystkie nowe dzienniki użycia będą zapisywane w nowym magazynie usługi Azure RMS i muszą zostać pobrane za pomocą polecenia Get-AadrmUserLog.

Aby uzyskać więcej informacji na temat korzystania ze środowiska Windows PowerShell z usługą Azure Rights Management, zobacz temat [Administrowanie usługą Azure Rights Management przy użyciu programu Windows PowerShell](administer-powershell.md).






<!--HONumber=Aug16_HO3-->


