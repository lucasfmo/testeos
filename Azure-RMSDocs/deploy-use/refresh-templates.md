---
title: "Odświeżanie szablonów | Azure RMS"
description: 
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 05/06/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 8c2064f0-dd71-4ca5-9040-1740ab8876fb
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 771f4139b09cccc05f2d1ee52c76b99467c70446
ms.openlocfilehash: 13c2b79558202d59ec49da3a189a58356518718d


---


# Odświeżanie szablonów dla użytkowników

*Dotyczy usług: Azure Rights Management, Office 365*

W przypadku korzystania z usług Azure RMS szablony są automatycznie pobierane na komputery klienckie, dzięki czemu użytkownicy mogą wybrać je z poziomu ich aplikacji. W przypadku wprowadzenia zmian do szablonów może być jednak konieczne wykonanie dodatkowych czynności:

|Aplikacja lub usługa|Odświeżanie szablonów po wprowadzeniu zmian|
|--------------------------|---------------------------------------------|
|Exchange Online|W celu odświeżenia szablonów wymagana jest konfiguracja ręczna.<br /><br />Aby uzyskać informacje na temat kroków konfiguracyjnych, zobacz następującą sekcję [Tylko usługa Exchange Online: Konfiguracja programu Exchange pod kątem pobierania zmienionych szablonów niestandardowych](#exchange-online-only-how-to-configure-exchange-to-download-changed-custom-templates).|
|Office 365|Automatyczne odświeżanie — nie wymaga dodatkowych kroków.|
|Pakiety Office 2016 i Office 2013<br /><br />Aplikacja RMS sharing dla systemu operacyjnego Windows|Automatycznie odświeżane — według harmonogramu:<br /><br />W przypadku nowszych wersji pakietu Office: odświeżanie odbywa się domyślnie co 7 dni.<br /><br />W przypadku aplikacji RMS sharing dla systemu Windows: począwszy od wersji 1.0.1784.0, domyślne ustawienie uwzględnia codzienne odświeżanie. W przypadku wcześniejszych wersji odświeżanie odbywa się domyślnie co 7 dni.<br /><br />Aby wymusić odświeżenie w terminie wcześniejszym niż ujęty w harmonogramie, zobacz następującą sekcję: [Pakiety Office 2016 i Office 2013 oraz aplikacja RMS sharing dla systemu Windows: Wymuszenie odświeżenia zmienionego szablonu niestandardowego](#office-2016-office-2013-and-rms-sharing-application-for-windows-how-to-force-a-refresh-for-a-changed-custom-template).|
|Office 2010|Odświeżanie może odbywać się podczas logowania się użytkowników.<br /><br />Aby wymusić odświeżenie, poproś użytkowników o wylogowanie się i ponowne zalogowanie lub wymuś je. Możesz także zapoznać się z sekcją [Tylko pakiet Office 2010: Wymuszenie odświeżenia zmienionego szablonu niestandardowego](#office-2010-only-how-to-force-a-refresh-for-a-changed-custom-template).|
W przypadku urządzeń przenośnych, w których jest wykorzystywana aplikacja udostępniania usługi RMS, szablony są automatycznie pobierane (w razie potrzeby także odświeżane) bez konieczności dodatkowej konfiguracji.

## Tylko usługa Exchange Online: Konfiguracja programu Exchange pod kątem pobierania zmienionych szablonów niestandardowych
Jeśli została już skonfigurowana usługa Information Rights Management (IRM) dla usługi Exchange Online, szablony niestandardowe nie będą pobierane dla użytkowników, dopóki nie zostaną wprowadzone następujące zmiany w środowisku Windows PowerShell usługi Exchange Online.

> [!NOTE]
> Aby uzyskać więcej informacji na temat korzystania ze środowiska Windows PowerShell usługi Exchange Online, zobacz [Korzystanie ze środowiska PowerShell usługi Exchange Online](https://technet.microsoft.com/library/jj200677%28v=exchg.160%29.aspx).

Tę procedurę należy wykonać po każdej zmianie szablonu.

### Aktualizacja szablonów dla usługi Exchange Online

1.  Za pomocą środowiska Windows PowerShell w usłudze Exchange Online połącz się z usługą:

    1.  Podaj nazwę i hasło użytkownika usługi Office 365:

        ```
        $Cred = Get-Credential
        ```

    2.  Połącz się z usługą Exchange Online, uruchamiając następujące dwa polecenia:

        ```
        $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.outlook.com/powershell/ -Credential $Cred -Authentication Basic –AllowRedirection
        ```

        ```
        Import-PSSession $Session
        ```

2.  Użyj polecenia cmdlet [Import-RMSTrustedPublishingDomain](http://technet.microsoft.com/library/jj200724%28v=exchg.160%29.aspx), aby ponownie zaimportować zaufaną domenę publikacji (TDP) z usługi Azure RMS:

    ```
    Import-RMSTrustedPublishingDomain -Name "<TPD name>" -RefreshTemplates -RMSOnline
    ```
    Na przykład jeśli nazwą zaufanej domeny publikacji jest **RMS Online — 1** (typowa nazwa stosowana w wielu organizacjach), należy użyć polecenia: **Import-RMSTrustedPublishingDomain -Name "RMS Online — 1" -RefreshTemplates -RMSOnline**

    > [!NOTE]
    > Aby sprawdzić nazwę zaufanej domeny publikacji, można użyć polecenia cmdlet [Get-RMSTrustedPublishingDomain](http://technet.microsoft.com/library/jj200707%28v=exchg.160%29.aspx).

3.  Aby upewnić się, że szablony zostały pomyślnie zaimportowane, zaczekaj kilka minut, a następnie uruchom polecenie cmdlet [Get-RMSTemplate](http://technet.microsoft.com/library/dd297960%28v=exchg.160%29.aspx) i ustaw typ All (Wszystkie). Na przykład:

    ```
    Get-RMSTemplate -TrustedPublishingDomain "RMS Online - 1" -Type All
    ```
    > [!TIP]
    > Warto przechowywać kopię danych wyjściowych, aby móc łatwo skopiować nazwy szablonów lub ich identyfikatory GUID, jeśli w późniejszym czasie zostanie przeprowadzona archiwizacja szablonu.

4.  W odniesieniu do każdego zaimportowanego szablonu, który ma być dostępny w programie Outlook Web App, należy użyć polecenia cmdlet [Set-RMSTemplate](http://technet.microsoft.com/library/hh529923%28v=exchg.160%29.aspx) i ustawić typ Distributed (Rozproszone):

    ```
    Set-RMSTemplate -Identity "<name  or GUID of the template>" -Type Distributed
    ```
    Jako że program Outlook Web Access buforuje interfejs użytkownika na 24 godziny, użytkownicy mogą nie widzieć nowego szablonu aż do następnego dnia.

Ponadto, jeśli używana jest usługa Exchange Online z usługą Office 365, w przypadku archiwizacji szablonu (niestandardowego lub domyślnego) użytkownicy korzystający z programu Outlook Web App lub urządzeń przenośnych, w których wykorzystywany jest protokół Exchange ActiveSync, będą w dalszym ciągu widzieć zarchiwizowane szablony.

Aby użytkownicy nie widzieli już tych szablonów, należy połączyć się z usługą za pomocą środowiska Windows PowerShell w usłudze Exchange Online, a następnie użyć polecenia cmdlet [Set-RMSTemplate](http://technet.microsoft.com/library/hh529923%28v=exchg.160%29.aspx), uruchamiając następujące polecenie:

```
Set-RMSTemplate -Identity "<name or GUID of the template>" -Type Archived
```

## Pakiety Office 2016 i Office 2013 oraz aplikacja RMS sharing dla systemu Windows: Wymuszenie odświeżenia zmienionego szablonu niestandardowego
Edytując rejestr na komputerach z pakietem Office 2016 lub Office 2013 albo z aplikacją do udostępniania usługi Rights Management (RMS) dla systemu operacyjnego Windows, można zmienić automatyczny harmonogram w taki sposób, aby zmienione szablony były odświeżane częściej niż częstotliwość domyślna. Można też wymusić natychmiastowe odświeżanie przez usunięcie istniejących danych z wartości rejestru.

> [!WARNING]
> Używanie Edytora rejestru w niewłaściwy sposób może spowodować poważne problemy, w wyniku których może być konieczna ponowna instalacja systemu operacyjnego. Firma Microsoft nie może zagwarantować użytkownikowi, że uda się rozwiązać problemy wynikające z niewłaściwego używania Edytora rejestru. Używasz Edytora rejestru na własne ryzyko.

### Zmiana automatycznego harmonogramu

1.  Za pomocą edytora rejestru należy utworzyć i ustawić jedną z następujących wartości rejestru:

    - Aby ustawić częstotliwość aktualizacji w dniach (co najmniej 1 dzień): Utwórz nową wartość rejestru o nazwie **TemplateUpdateFrequency** i zdefiniuj dla danych wartość całkowitą, która będzie określać wyrażaną w dniach częstotliwość pobierania wszelkich zmian do pobranego szablonu. Skorzystaj z poniższych informacji, aby zlokalizować ścieżkę rejestru w celu utworzenia wspomnianej nowej wartości rejestru.

        **Ścieżka rejestru:** HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC

        **Typ:** REG_DWORD

        **Wartość:** TemplateUpdateFrequency

    - Aby ustawić częstotliwość aktualizacji w sekundach (co najmniej 1 sekunda): Utwórz nową wartość rejestru o nazwie **TemplateUpdateFrequencyInSeconds** i zdefiniuj dla danych wartość całkowitą, która będzie określać wyrażaną w sekundach częstotliwość pobierania wszelkich zmian do pobranego szablonu. Skorzystaj z poniższych informacji, aby zlokalizować ścieżkę rejestru w celu utworzenia wspomnianej nowej wartości rejestru.

        **Ścieżka rejestru:** HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC

        **Typ:** REG_DWORD

        **Wartość:** TemplateUpdateFrequencyInSeconds

    Upewnij się, że utworzona i ustawiona została jedna z tych wartości rejestru, a nie obie. Jeśli dostępne są obie wartości, wartość **TemplateUpdateFrequency** jest ignorowana.

2.  Aby wymusić natychmiastowe odświeżenie szablonów, przejdź do następnej procedury. Jeśli nie jest konieczne natychmiastowe odświeżenie, należy ponownie uruchomić aplikacje pakietu Office i wystąpienia Eksploratora plików.

### Wymuszenie natychmiastowego odświeżenia

1.  Korzystając z edytora rejestru, usuń dane dla wartości **LastUpdatedTime**. Przykładowa wartość to **2015-04-20T15:52** — w tym przypadku należy usunąć ciąg 2015-04-20T15:52, aby nie były wyświetlane żadne dane. Skorzystaj z poniższych informacji, aby zlokalizować ścieżkę rejestru w celu usunięcia danych dla tej wartości rejestru.

    **Ścieżka rejestru:** HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC\<*MicrosoftRMS_FQDN*>\Template

    **Typ:** REG_SZ

    **Wartość:** LastUpdatedTime

    > [!TIP]
        > W ścieżce rejestru ciąg <*MicrosoftRMS_FQDN*> odnosi się do nazwy FQDN usługi RMS firmy Microsoft. Aby sprawdzić tę wartość:

    > 1.  Uruchom polecenie cmdlet [Get-AadrmConfiguration](https://msdn.microsoft.com/library/windowsazure/dn629410.aspx) dla usługi Azure RMS. Jeśli jeszcze nie zainstalowano modułu Windows PowerShell dla usługi Azure RMS, zobacz [Instalowanie programu Windows PowerShell dla usługi Azure Rights Management](install-powershell.md).
    > 2.  W danych wyjściowych zidentyfikuj wartość **LicensingIntranetDistributionPointUrl**.
    > 
    >     Na przykład: **LicensingIntranetDistributionPointUrl   : https://5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com/_wmcs/licensing**
    > 3.  Wykasuj z wartości ciąg **https://** oraz **/_wmcs/licensing**. Pozostała wartość stanowi nazwę FQDN usługi Microsoft RMS. W naszym przykładzie nazwa FQDN usługi Microsoft RMS ma następującą wartość:
    > 
    >     **5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com**

2.  Usuń następujący folder i wszystkie zawarte w nim pliki: **%localappdata%\Microsoft\MSIPC\Templates**

3.  Ponownie uruchom aplikacje pakietu Office i wystąpienia Eksploratora plików.

## Tylko pakiet Office 2010: Wymuszenie odświeżenia zmienionego szablonu niestandardowego
Edytując rejestr na komputerach z pakietem Office 2010, można ustawić wartość w taki sposób, że zmienione szablony zostaną odświeżone na komputerach bez konieczności wylogowania się i ponownego zalogowania się przez użytkowników. Można też wymusić natychmiastowe odświeżanie przez usunięcie istniejących danych z wartości rejestru.

> [!WARNING]
> Używanie Edytora rejestru w niewłaściwy sposób może spowodować poważne problemy, w wyniku których może być konieczna ponowna instalacja systemu operacyjnego. Firma Microsoft nie może zagwarantować użytkownikowi, że uda się rozwiązać problemy wynikające z niewłaściwego używania Edytora rejestru. Używasz Edytora rejestru na własne ryzyko.

### Zmiana częstotliwości aktualizacji

1.  Korzystając z edytora rejestru, utwórz nową wartość o nazwie **UpdateFrequency** i zdefiniuj dla danych wartość całkowitą, która będzie określać wyrażaną w dniach częstotliwość pobierania wszelkich zmian do pobranego szablonu. Skorzystaj z poniższej tabeli, aby zlokalizować ścieżkę rejestru w celu utworzenia wspomnianej nowej wartości rejestru.

    **Ścieżka rejestru:** HKEY_CURRENT_USER\Software\Microsoft\MSDRM\TemplateManagement

    **Typ:** REG_DWORD

    **Wartość:** UpdateFrequency

2.  Aby wymusić natychmiastowe odświeżenie szablonów, przejdź do następnej procedury. Jeśli nie jest to konieczne, uruchom ponownie aplikacje pakietu Office.

### Wymuszenie natychmiastowego odświeżenia

1.  Korzystając z edytora rejestru, usuń dane dla wartości **LastUpdatedTime**. Przykładowa wartość to **2015-04-20T15:52** — w tym przypadku należy usunąć ciąg 2015-04-20T15:52, aby nie były wyświetlane żadne dane. Skorzystaj z poniższej tabeli, aby zlokalizować ścieżkę rejestru w celu usunięcia danych dla tej wartości rejestru.

    **Ścieżka rejestru:** HKEY_CURRENT_USER\Software\Microsoft\MSDRM\TemplateManagement

    **Typ:** REG_SZ

    **Wartość:** lastUpdatedTime


2.  Usuń następujący folder i wszystkie zawarte w nim pliki: **%localappdata%\Microsoft\MSIPC\Templates**

3.  Uruchom ponowne aplikacje pakietu Office.

## Zobacz też
[Konfigurowanie szablonów niestandardowych usługi Azure Rights Management](configure-custom-templates.md)


<!--HONumber=Jul16_HO3-->


