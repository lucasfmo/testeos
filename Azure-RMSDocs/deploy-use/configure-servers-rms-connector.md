---
title: "Konfigurowanie serwerów na potrzeby łącznika Azure Rights Management | Azure RMS"
description: 
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 06/08/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 75846ee1-2370-4360-81ad-e2b6afe3ebc9
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 0b07ecc88b1d2d344f0984d4a805cc033996cc4d
ms.openlocfilehash: 79171b5931b69ca18d2a2cbe321d5d5887903da2


---

# Konfigurowanie serwerów na potrzeby łącznika Azure Rights Management

*Dotyczy: Azure Rights Management, Windows Server 2012, Windows Server 2012 R2*


Skorzystaj z poniższych informacji, aby łatwiej skonfigurować serwery lokalne, które będą używać łącznika Azure Rights Management (RMS). Te procedury obejmują krok 5 z instrukcji [Wdrażanie łącznika usługi Azure Rights Management](deploy-rms-connector.md).

Przed rozpoczęciem upewnij się, że łącznik usługi RMS jest zainstalowany i skonfigurowany, oraz sprawdź wszystkie [wymagania wstępne](deploy-rms-connector.md#prerequisites-for-the-rms-connector), które dotyczą serwerów używających łącznika.


## Konfigurowanie serwerów do korzystania z łącznika usługi RMS
Po zainstalowaniu i skonfigurowaniu łącznika usługi RMS można przystąpić do konfigurowania serwerów lokalnych, które będą korzystać z usługi Rights Management i łączyć się z usługą Azure RMS za pomocą łącznika. Oznacza to konfigurowanie następujących serwerów:

-   **Dla programów Exchange 2016 i Exchange 2013**: serwery dostępu klientów i serwery skrzynek pocztowych

-   **Dla programu Exchange 2010**: serwery dostępu klientów i serwery transportu centralnego

-   **Dla programu SharePoint**: serwery frontonu sieci Web programu SharePoint, łącznie z tymi hostującymi serwer administracji centralnej

-   **Dla infrastruktury klasyfikacji plików**: komputery z systemem Windows Server, na których zainstalowano program File Resource Manager

Ta konfiguracja wymaga zmiany ustawień rejestru. Dostępne są dwie opcje realizacji tego zadania: automatycznie przy użyciu narzędzia do konfiguracji serwera dla łącznika Microsoft RMS lub za pomocą ręcznej edycji rejestru.

---

**Automatycznie przy użyciu narzędzia do konfiguracji serwera dla łącznika Microsoft RMS:**

- Zalety:

    - Bez bezpośredniej edycji rejestru. Automatyzacja za pomocą skryptu.

    - Nie trzeba uruchamiać polecenia cmdlet Windows PowerShell, aby uzyskać adres URL usługi Microsoft RMS.

    - Wymagania wstępne są automatycznie sprawdzane (ale nie automatycznie korygowane) w przypadku uruchomienia lokalnego.

Wady:

- Przy uruchamianiu narzędzia należy ustanowić połączenie z serwerem, na którym działa już łącznik usługi RMS.

---

**Ręczna edycja rejestru:**

- Zalety:

    - Nie jest wymagana łączność z serwerem, na którym działa łącznik usługi RMS.

- Wady:

    - Większa podatność na błędy spowodowana większymi nakładami prac administracyjnych.

    - Należy uzyskać adres URL usługi Microsoft RMS, co wymaga uruchomienia polecenia Windows PowerShell.

    - Zawsze należy samodzielnie sprawdzić wszystkie wymagania wstępne.


---

> [!IMPORTANT]
> W obu przypadkach należy ręcznie zainstalować wszystkie wymagania wstępne oraz skonfigurować programy Exchange i SharePoint, a także infrastrukturę klasyfikacji plików, aby korzystać z usługi Rights Management.

W przypadku większości organizacji konfiguracja automatyczna za pomocą narzędzia do konfiguracji serwera dla łącznika usługi Microsoft RMS będzie lepszym rozwiązaniem, ponieważ zapewnia większą wydajność i niezawodność niż konfiguracja ręczna.

Po wprowadzeniu zmian konfiguracji na tych serwerach należy uruchomić je ponownie, jeśli działają na nich programy Exchange lub SharePoint, a wcześniejsza konfiguracja obejmowała korzystanie z usługi AD RMS. Nie ma potrzeby ponownego uruchomienia tych serwerów w przypadku konfigurowania ich do korzystania z usługi Rights Management po raz pierwszy. Po wprowadzeniu tych zmian konfiguracji zawsze należy ponownie uruchomić serwer plików skonfigurowany do używania infrastruktury klasyfikacji plików.

### Sposób użycia narzędzia do konfiguracji serwera dla łącznika usługi Microsoft RMS:

1.  Jeśli nie pobrano jeszcze skryptu narzędzia konfiguracji serwera dla łącznika usługi Microsoft RMS (GenConnectorConfig.ps1), pobierz go z [Centrum pobierania Microsoft](http://go.microsoft.com/fwlink/?LinkId=314106).

2.  Zapisz plik GenConnectorConfig.ps1 na komputerze, na którym zostanie uruchomione narzędzie. W przypadku lokalnego uruchamiania narzędzia musi to być serwer, który chcesz skonfigurować do komunikowania się z łącznikiem usługi RMS. W przeciwnym razie możesz zapisać plik na dowolnym komputerze.

3.  Zdecyduj, jak uruchomić narzędzie:

    -   **Lokalnie**: możesz uruchomić narzędzie w trybie interakcyjnym na serwerze, który ma być skonfigurowany do komunikowania się z łącznikiem usługi RMS. Jest to przydatne w przypadku jednorazowego przeprowadzania konfiguracji, np. w środowisku testowym.

    -   **Wdrożenie oprogramowania**: możesz uruchomić narzędzie w celu utworzenia plików rejestru do późniejszego wdrożenia na jednym serwerze lub większej liczbie odpowiednich serwerów za pomocą aplikacji do zarządzania systemami, która obsługuje wdrożenia oprogramowania, takiej jak System Center Configuration Manager.

    -   **Zasady grupy**: możesz uruchomić narzędzie w celu utworzenia skryptu do przekazania administratorowi, który może utworzyć obiekty zasad grupy służące do konfigurowania serwerów. Ten skrypt tworzy jeden obiekt zasad grupy dla każdego typu serwera, który ma być skonfigurowany. Następnie administrator może przypisać obiekty do odpowiednich serwerów.

    > [!NOTE]
    > To narzędzie służy do konfigurowania wymienionych na początku tego tematu serwerów, które będą komunikować się z łącznikiem usługi RMS. Nie uruchamiaj tego narzędzia na serwerach, na których działa łącznik usługi RMS.

4.  Uruchom program Windows PowerShell z opcją **Uruchom jako administrator** i użyj polecenia Get-help, aby przeczytać instrukcje obsługi narzędzia dotyczące wybranej metody konfiguracji:

    ```
    Get-help .\GenConnectorConfig.ps1 -detailed
    ```

Aby uruchomić skrypt, wprowadź adres URL łącznika usługi RMS danej organizacji. Wprowadź prefiks protokołu (HTTP:// lub HTTPS://) i nazwę łącznika, zdefiniowaną w systemie DNS dla adresu łącznika ze zrównoważonym obciążeniem. Na przykład https://connector.contoso.com. Narzędzie będzie używać tego adresu URL do kontaktowania się z serwerami, na których działa łącznik usługi RMS, i pozyskiwania innych parametrów potrzebnych do tworzenia wymaganych konfiguracji.

> [!IMPORTANT]
> Przy uruchamianiu tego narzędzia upewnij się, że podajesz nazwę łącznika usługi RMS ze zrównoważonym obciążeniem w danej organizacji, a nie nazwę pojedynczego serwera, na którym działa usługa łącznika usługi RMS.

Aby uzyskać szczegółowe informacje dla każdego typu usług, skorzystaj z następujących tematów:

-   [Konfigurowanie serwera programu Exchange do używania łącznika](#configuring-an-exchange-server-to-use-the-connector)

-   [Konfigurowanie serwera programu SharePoint do używania łącznika](#configuring-a-sharepoint-server-to-use-the-connector)

-   [Konfigurowanie serwera plików dla funkcji infrastruktury klasyfikacji plików do używania łącznika](#configuring-a-file-server-for-file-classification-infrastructure-to-use-the-connector)

> [!NOTE]
> Po skonfigurowaniu tych serwerów do korzystania z łącznika zainstalowane na nich lokalnie aplikacje klienckie mogą nie współpracować z usługą RMS. Przyczyną jest fakt, że aplikacje próbują używać łącznika zamiast korzystać bezpośrednio z usługi RMS, co nie jest obsługiwane.
>
> Ponadto w razie lokalnej instalacji pakietu Office 2010 na serwerze programu Exchange funkcje IRM aplikacji klienckiej mogą działać na tym komputerze po skonfigurowaniu serwera do używania łącznika, ale nie jest to obsługiwane.
>
> W obu przypadkach należy zainstalować aplikacje klienckie na oddzielnych komputerach, które nie są skonfigurowane do używania łącznika. Wtedy będą one poprawnie korzystać bezpośrednio z usługi RMS.

## Konfigurowanie serwera programu Exchange do używania łącznika
Następujące role Exchange komunikują się z łącznikiem usługi RMS:

-   Dla programów Exchange 2016 i Exchange 2013: serwery dostępu klientów i serwery skrzynek pocztowych

-   Dla programu Exchange 2010: serwery dostępu klientów i serwery transportu centralnego

W celu korzystania z łącznika usługi RMS te serwery programu Exchange muszą mieć uruchomioną jedną z następujących wersji oprogramowania:

-   Exchange Server 2016

-   Exchange Server 2013 z pakietem zbiorczym aktualizacji 3 dla programu Exchange 2013

-   Exchange Server 2010 z dodatkiem Service Pack 3 i pakietem zbiorczym aktualizacji 6 dla programu Exchange 2010

Należy również zainstalować na tych serwerach wersję klienta RMS z obsługą trybu kryptograficznego 2 usługi RMS. Minimalna wersja obsługiwana w systemie Windows Server 2008 jest dołączona do poprawki, którą można pobrać z artykułu informującego, że [długość klucza RSA zostaje zwiększona do 2048 bitów dla usługi AD RMS w systemie Windows Server 2008 R2 i Windows Server 2008](http://support.microsoft.com/kb/2627272). Minimalną wersję dla systemu Windows Server 2008 R2 można pobrać z artykułu informującego, że [długość klucza RSA zostaje zwiększona do 2048 bitów dla usługi AD RMS w systemie Windows 7 lub Windows Server 2008 R2](http://support.microsoft.com/kb/2627273). Systemy Windows Server 2012 i Windows Server 2012 R2 natywnie obsługują tryb kryptograficzny 2.

> [!IMPORTANT]
> Jeśli te wersje lub nowsze wersje programu Exchange i klienta usługi RMS nie są zainstalowane, nie można skonfigurować programu Exchange do korzystania z łącznika. Przed kontynuowaniem sprawdź, czy te wersje są zainstalowane.

### Konfigurowanie serwerów programu Exchange do używania łącznika

1. Upewnij się, że serwery Exchange są autoryzowane do używania łącznika usługi RMS za pomocą narzędzia administracyjnego łącznika usługi RMS i informacji z tematu [Autoryzowanie serwerów do korzystania z łącznika usługi RMS](install-configure-rms-connector.md#authorizing-servers-to-use-the-rms-connector). Ta konfiguracja jest wymagana, aby program Exchange mógł korzystać z łącznika usługi RMS.

2.  Na rolach serwera programu Exchange, które komunikują się z łącznikiem usług RMS wykonaj jedną z następujących czynności:

    -   Uruchom narzędzie do konfiguracji serwera dla łącznika usługi Microsoft RMS. Aby uzyskać więcej informacji, zobacz temat [Sposób użycia narzędzia do konfiguracji serwera dla łącznika usługi Microsoft RMS](#how-to-use-the-server-configuration-tool-for-microsoft-rms-connector) w tym artykule.

        Na przykład, aby uruchomić narzędzie lokalnie w celu skonfigurowania serwera z programem Exchange 2016 lub Exchange 2013:

        ```
        .\GenConnectorConfig.ps1 -ConnectorUri https://rmsconnector.contoso.com -SetExchange2013
        ```

    -   Dokonaj edycji rejestru ręcznie przy użyciu informacji w temacie [Ustawienia rejestru dla łącznika usługi RMS](rms-connector-registry-settings.md), aby ręcznie dodać ustawienia rejestru na serwerach. 

3.  Włącz funkcjonalność IRM w programie Exchange. Aby uzyskać więcej informacji, zobacz temat opisujący [procedury zarządzania prawami do informacji](https://technet.microsoft.com/library/dd351212%28v=exchg.150%29.aspx) w bibliotece programu Exchange.

    > [!NOTE]
    > Domyślnie po uruchomieniu polecenia **Set-IRMConfiguration-InternalLicensingEnabled $true** usługa IRM jest automatycznie włączona dla programu Outlook Web App i urządzeń przenośnych, a nie tylko dla skrzynek pocztowych. Jednak administratorzy mogą wyłączyć usługę IRM na różnych poziomach, na przykład dla roli Serwer dostępu klienta, katalogu wirtualnego programu Outlook Web App lub zasady skrzynek pocztowych programu Outlook Web App, a także zasady skrzynki pocztowej urządzenia przenośnego. Jeśli użytkownicy nie widzą żadnych szablonów usługi Azure RMS w programie Outlook Web App (po odczekaniu dnia) lub na urządzeniach przenośnych, a szablony są już widoczne w kliencie programu Outlook, sprawdź odpowiednie ustawienia, aby upewnić się, że usługa IRM nie została wyłączona. Aby uzyskać więcej informacji, zobacz temat opisujący [włączanie lub wyłączanie Zarządzania prawami do informacji na Serwerach dostępu klienta](https://technet.microsoft.com/library/dd876938(v=exchg.150).aspx) w dokumentacji programu Exchange. 


## Konfigurowanie serwera programu SharePoint do używania łącznika
Następujące role SharePoint komunikują się z łącznikiem usługi RMS:

-   Serwery frontonu sieci Web programu SharePoint, łącznie z tymi hostującymi serwer administracji centralnej

W celu korzystania z łącznika usługi RMS te serwery programu SharePoint muszą mieć uruchomioną jedną z następujących wersji oprogramowania:

-   SharePoint Server 2016

-   SharePoint Server 2013

-   SharePoint Server 2010

Serwer z działającym programem SharePoint 2016 lub SharePoint 2013 musi mieć również uruchomioną wersję klienta MSIPC 2.1, która jest zgodna z łącznikiem usługi RMS. Aby upewnić się, że masz obsługiwaną wersję, pobierz najnowszego klienta z [Centrum pobierania Microsoft](http://www.microsoft.com/download/details.aspx?id=38396).

> [!WARNING]
> Istnieje wiele wersji klienta MSIPC 2.1, dlatego upewnij się, że została zainstalowana wersja 1.0.2004.0 lub nowsza.
>
> Wersję klienta można sprawdzić, odczytując numer wersji pliku MSIPC.dll, który znajduje się w folderze **\Program Files\Active Directory Rights Management Services Client 2.1**. Okno dialogowe właściwości zawiera numer wersji klienta MSIPC 2.1.

Serwery z działającym programem SharePoint 2010 muszą mieć zainstalowaną wersję klienta MSDRM, która obsługuje tryb kryptograficzny 2 usługi RMS. Minimalna wersja obsługiwana w systemie Windows Server 2008 jest dołączona do poprawki, którą można pobrać z artykułu informującego, że [długość klucza RSA zostaje zwiększona do 2048 bitów dla usługi AD RMS w systemach Windows Server 2008 R2 i Windows Server 2008](http://support.microsoft.com/kb/2627272). Natomiast minimalną wersję dla systemu Windows Server 2008 R2 można pobrać z artykułu informującego, że [długość klucza RSA zostaje zwiększona do 2048 bitów dla usługi AD RMS w systemie Windows 7 lub Windows Server 2008 R2](http://support.microsoft.com/kb/2627273). Systemy Windows Server 2012 i Windows Server 2012 R2 natywnie obsługują tryb kryptograficzny 2.

### Konfigurowanie serwerów programu SharePoint do używania łącznika

1. Upewnij się, że serwery SharePoint są autoryzowane do używania łącznika usługi RMS za pomocą narzędzia administracyjnego łącznika usługi RMS i informacji z tematu [Autoryzowanie serwerów do korzystania z łącznika usługi RMS](install-configure-rms-connector.md#authorizing-servers-to-use-the-rms-connector). Ta konfiguracja jest wymagana, aby program Exchange mógł korzystać z łącznika usługi RMS.

2.  Na serwerach programu SharePoint, które komunikują się z łącznikiem usługi RMS wykonaj jedną z następujących czynności:

    -   Uruchom narzędzie do konfiguracji serwera dla łącznika usługi Microsoft RMS. Aby uzyskać więcej informacji, zobacz temat [Sposób użycia narzędzia do konfiguracji serwera dla łącznika usługi Microsoft RMS](#how-to-use-the-server-configuration-tool-for-microsoft-rms-connector) w tym artykule.

        Na przykład, aby uruchomić narzędzie lokalnie w celu skonfigurowania serwera z programem SharePoint 2016 lub SharePoint 2013:

        ```
        .\GenConnectorConfig.ps1 -ConnectorUri https://rmsconnector.contoso.com -SetSharePoint2013
        ```

    -   Jeśli używasz programu SharePoint 2016 lub SharePoint 2013, dokonaj edycji rejestru ręcznie, korzystając z informacji z tematu [Ustawienia rejestru dla łącznika usługi RMS](rms-connector-registry-settings.md), aby ręcznie dodać ustawienia rejestru na serwerach. 

3.  Włącz IRM w programie SharePoint. Aby uzyskać więcej informacji, zobacz temat opisujący [konfigurowanie zarządzania prawami do informacji (SharePoint Server 2010)](https://technet.microsoft.com/library/hh545607%28v=office.14%29.aspx) w bibliotece programu SharePoint.

    Podczas wykonywania tych instrukcji należy skonfigurować program SharePoint do korzystania z łącznika, określając opcję **Użyj tego serwera usług RMS**, a następnie wprowadzić skonfigurowany wcześniej adres URL łącznika ze zrównoważonym obciążeniem. Wprowadź prefiks protokołu (HTTP:// lub HTTPS://) i nazwę łącznika, zdefiniowaną w systemie DNS dla adresu łącznika ze zrównoważonym obciążeniem. Na przykład, jeśli nazwą łącznika jest https://connector.contoso.com, konfiguracja będzie wyglądać tak, jak na poniższej ilustracji:

    ![Konfigurowanie serwera programu SharePoint dla łącznika usługi RMS](../media/AzRMS_SharePointConnector.png)

    Po włączeniu usługi IRM w farmie programu SharePoint można włączyć usługę IRM na poszczególnych bibliotekach przy użyciu opcji **Zarządzanie prawami do informacji** na stronie **Ustawienia biblioteki** dla poszczególnych bibliotek.


## Konfigurowanie serwera plików dla funkcji infrastruktury klasyfikacji plików do używania łącznika
Aby można było użyć łącznika usług RMS i infrastruktury klasyfikacji plików do ochrony dokumentów pakietu Office, serwer plików mieć jeden z następujących systemów operacyjnych:

-   Windows Server 2012 R2

-   Windows Server 2012

### Konfigurowanie serwerów plików do używania łącznika

1.  Upewnij się, że serwery plików są autoryzowane do używania łącznika usługi RMS, za pomocą narzędzia administracyjnego łącznika usługi RMS i informacji z tematu [Autoryzowanie serwerów do korzystania z łącznika usługi RMS](install-configure-rms-connector.md#authorizing-servers-to-use-the-rms-connector). Ta konfiguracja jest wymagana, aby program Exchange mógł korzystać z łącznika usługi RMS.

2.  Na serwerach plików skonfigurowanych dla infrastruktury klasyfikacji plików, które będą komunikować się z łącznikiem usługi RMS, wykonaj jedną z następujących czynności:

    -   Uruchom narzędzie do konfiguracji serwera dla łącznika usługi Microsoft RMS. Aby uzyskać więcej informacji, zobacz temat [Sposób użycia narzędzia do konfiguracji serwera dla łącznika usługi Microsoft RMS](#how-to-use-the-server-configuration-tool-for-microsoft-rms-connector) w tym artykule.

        Na przykład, aby uruchomić narzędzie lokalnie w celu skonfigurowania serwera plików z działającą infrastrukturą klasyfikacji plików:

        ```
        .\GenConnectorConfig.ps1 -ConnectorUri https://rmsconnector.contoso.com -SetFCI2012
        ```

    - Dokonaj edycji rejestru ręcznie przy użyciu informacji w temacie [Ustawienia rejestru dla łącznika usługi RMS](rms-connector-registry-settings.md), aby ręcznie dodać ustawienia rejestru na serwerach. 

3.  Utwórz reguły klasyfikacji i zadania zarządzania plikami w celu ochrony dokumentów za pomocą szyfrowania RMS, a następnie określ szablon RMS, aby automatycznie zastosować zasady RMS. Aby uzyskać więcej informacji, zobacz temat [Menedżer zasobów serwera plików — omówienie](http://technet.microsoft.com/library/hh831701.aspx) w bibliotece dokumentacji systemu Windows Server.

## Następne kroki
Kiedy łącznik usługi RMS zostanie zainstalowany i skonfigurowany, a serwery zostaną skonfigurowane, aby z niego korzystać, administratorzy IT i użytkownicy będą mogli chronić oraz stosować wiadomości e-mail i dokumenty przy użyciu usługi Azure RMS. Aby użytkownikom było łatwiej, warto wdrożyć aplikację RMS sharing, która instaluje dodatek do pakietu Office i dodaje nowe opcje prawego przycisku myszy do Eksploratora plików. Aby uzyskać więcej informacji, zobacz [Przewodnik administratora aplikacji do udostępniania usługi Rights Management](../rms-client/sharing-app-admin-guide.md).

Możesz użyć [planu wdrożenia usługi Azure Rights Management](../plan-design/deployment-roadmap.md), aby sprawdzić, czy istnieją inne czynności konfiguracyjne, które warto wykonać przed udostępnieniem usługi [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] użytkownikom i administratorom.

Aby monitorować łącznik usługi RMS, zobacz [Monitorowanie łącznika usługi Azure Rights Management](monitor-rms-connector.md). 



<!--HONumber=Jul16_HO3-->


