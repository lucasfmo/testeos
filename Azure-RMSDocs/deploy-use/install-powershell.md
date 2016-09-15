---
title: "Instalowanie programu Windows PowerShell dla usługi Azure Rights Management | Azure RMS"
description: 
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 08/17/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 0d665ed6-b1de-4d63-854a-bc57c1c49844
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 5f8672b1f4d8e1b5ed707e89e88c9ba50d24f486
ms.openlocfilehash: 4120aeeae7c2c48168e4f01de6558da5034bf019


---

# Instalowanie programu Windows PowerShell dla usługi Azure Rights Management

*Dotyczy usług: Azure Rights Management, Office 365*

Użyj poniższych informacji, aby zainstalować program Windows PowerShell dla usługi Microsoft [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] (Azure RMS).

Ten moduł programu PowerShell umożliwia administrowanie usługą [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] z wiersza polecenia przy użyciu dowolnego komputera z połączeniem internetowym, który spełnia wymagania wstępne określone w kolejnej sekcji. Program Windows PowerShell dla usługi [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] obsługuje wykonywanie skryptów automatyzacji oraz może być wymagany w scenariuszach konfiguracji zaawansowanej. Aby uzyskać więcej informacji na temat zadań administracyjnych i konfiguracji obsługiwanych przez moduł, zobacz [Administrowanie usługą Azure Rights Management przy użyciu programu Windows PowerShell](administer-powershell.md).

## Wymagania wstępne
Poniższa tabela zawiera wymagania wstępne dotyczące instalacji i używania programu Windows PowerShell dla usługi [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)].

|Wymaganie|Więcej informacji|
|---------------|--------------------|
|Wersja systemu Windows, która obsługuje moduł administracji usługi [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)]|Sprawdź listę obsługiwanych systemów operacyjnych w sekcji **Wymagania systemowe** [strony pobierania narzędzia Azure Rights Management Administration Tool](http://go.microsoft.com/fwlink/?LinkId=257721).|
|Minimalna wersja programu Windows PowerShell: 2.0|Obsługa modułu administracyjnego usługi [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] została wprowadzona w programie Windows PowerShell 2.0.<br /><br />Domyślnie większość systemów operacyjnych Windows jest instalowana z programem Windows PowerShell w wersji co najmniej 2.0. Jeśli konieczne jest zainstalowanie programu Windows PowerShell 2.0, zobacz [Install Windows PowerShell 2.0](http://msdn.microsoft.com/library/ff637750.aspx) (Instalowanie programu Windows PowerShell 2.0).<br /><br />Porada: używaną wersję programu Windows PowerShell możesz sprawdzić, wpisując polecenie `$PSVersionTable` w sesji programu PowerShell.|
|Minimalna wersja platformy Microsoft .NET Framework: 4.5<br /><br />Uwaga: ta wersja platformy Microsoft .NET Framework jest dołączona do nowszych systemów operacyjnych, w związku z czym jej ręczna instalacja powinna być konieczna tylko wtedy, gdy kliencki system operacyjny jest starszy niż Windows 8.0 lub serwerowy system operacyjny jest starszy niż Windows Server 2012.|Jeśli nie zainstalowano minimalnej wersji platformy Microsoft .NET Framework, można pobrać platformę [Microsoft .NET Framework 4.5](http://www.microsoft.com/download/details.aspx?id=30653).<br /><br />Ta minimalna wersja platformy Microsoft .NET Framework jest wymagana przez niektóre klasy używane przez moduł administracyjny usługi [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)].|

> [!NOTE]
> Począwszy od wersji 2.5.0.0 modułu administracyjnego usługi Rights Management, asystent logowania w witrynie Microsoft Online Services nie jest już wymagany.
> 
> Jeśli istniała już zainstalowana wcześniejsza wersja modułu administracyjnego usługi Rights Management, użyj opcji **Programy i funkcje**, aby odinstalować narzędzie **Windows Azure AD Rights Management Administration** przed zainstalowaniem najnowszej wersji.


## Instalacja modułu administracyjnego usługi Rights Management

1.  Przejdź do Centrum pobierania Microsoft i pobierz [narzędzie Azure Rights Management Administration Tool](https://go.microsoft.com/fwlink/?LinkId=257721), które zawiera moduł administracyjny usługi [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] dla programu Windows PowerShell.

2.  W folderze lokalnym, do którego pobrano i w którym zapisano plik instalatora usługi [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)], kliknij dwukrotnie plik wykonywalny pobrany dla używanej platformy (WindowsAzureADRightsManagementAdministration_x64 lub WindowsAzureADRightsManagementAdministration_x86.exe), aby uruchomić Kreatora instalacji modułu administracyjnego usługi Azure AD Rights Management.

3.  Ukończ pracę kreatora.

Zostanie zainstalowany program Windows PowerShell dla usługi [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)].

## Następne kroki
Aby wyświetlić dostępne polecenia cmdlet, uruchom program Windows PowerShell za pomocą opcji **Uruchom jako administrator** i wpisz następujące polecenie:

```
Get-Command -Module aadrm
```
Użyj polecenia `the Get-Help <cmdlet_name>`, aby wyświetlić pomoc dla konkretnego polecenia cmdlet.

Aby uzyskać dodatkowe informacje:

-   Pełna lista dostępnych poleceń cmdlet: [Polecenia cmdlet usługi Azure Rights Management](https://msdn.microsoft.com/library/windowsazure/dn629398.aspx)

-   Lista głównych scenariuszy konfiguracji obsługujących program Windows PowerShell: [Administrowanie usługą Azure Rights Management przy użyciu programu Windows PowerShell](administer-powershell.md)

Przed uruchomieniem dowolnych poleceń konfigurujących usługę [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] należy nawiązać połączenie z usługą przy użyciu polecenia cmdlet [Connect-AadrmService](https://msdn.microsoft.com/library/windowsazure/dn629415.aspx). Po zakończeniu uruchamiania odpowiednich poleceń konfiguracji rozłącz się z usługą przy użyciu polecenia cmdlet [Disconnect-AadrmService](https://msdn.microsoft.com/library/windowsazure/dn629416.aspx).

> [!NOTE]
> Jeśli nie aktywowano jeszcze usługi [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)], można to zrobić po nawiązaniu połączenia z usługą, używając polecenia cmdlet [Enable-Aadrm](https://msdn.microsoft.com/library/windowsazure/dn629412.aspx).

## Zobacz też
[Administrowanie usługą Azure Rights Management przy użyciu programu Windows PowerShell](administer-powershell.md)



<!--HONumber=Aug16_HO3-->


