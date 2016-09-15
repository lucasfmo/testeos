---
title: Krok 2&colon; Migracja klucza chronionego przez oprogramowanie do klucza chronionego przez oprogramowanie | Azure RMS
description: 
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 08/17/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 81a5cf4f-c1f3-44a9-ad42-66e95f33ed27
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 437afd88efebd9719a3db98f8ab0ae07403053f7
ms.openlocfilehash: 9cd66efad548a4ddef4e6032b0ce7fc817a95c31


---


# Krok 2. Migracja klucza chronionego przez oprogramowanie do klucza chronionego przez oprogramowanie

*Dotyczy usług: Active Directory Rights Management Services, Azure Rights Management*


Te instrukcje są częścią [ścieżki migracji z usług AD RMS do usługi Azure Rights Management](migrate-from-ad-rms-to-azure-rms.md) oraz są stosowane tylko wtedy, gdy klucz usług AD RMS jest chroniony przez oprogramowanie, a użytkownik chce migrować klucz do usługi Azure Rights Management z wykorzystaniem klucza dzierżawy chronionego przez oprogramowanie. 

Jeśli nie jest to wybrany scenariusz konfiguracji, wróć do [Kroku 2. Eksportowanie danych konfiguracji z usług AD RMS i importowanie ich do usługi Azure RMS](migrate-from-ad-rms-phase1.md#step-2-export-configuration-data-from-ad-rms-and-import-it-to-azure-rms) i wybierz inną konfigurację.

Poniższa procedura umożliwia zaimportowanie konfiguracji usług AD RMS do usługi Azure RMS i zastosowanie w ten sposób klucza dzierżawy usługi Azure RMS zarządzanego przez firmę Microsoft.

## Aby importować dane konfiguracji do usługi Azure RMS

1.  Na połączonej z Internetem stacji roboczej pobierz i zainstaluj moduł Windows PowerShell dla usługi Azure RMS (wersja minimalna: 2.5.0.0), który zawiera polecenie cmdlet [Import-AadrmTpd](http://msdn.microsoft.com/library/azure/dn857523.aspx).

    > [!TIP]
    > Jeśli moduł został wcześniej pobrany i zainstalowany, sprawdź numer wersji, uruchamiając polecenie: `(Get-Module aadrm -ListAvailable).Version`

    Instrukcje instalacji znajdują się w sekcji [Instalowanie programu Windows PowerShell dla usługi Azure Rights Management](../deploy-use/install-powershell.md).

2.  Uruchom program Windows PowerShell przy użyciu opcji **Uruchom jako administrator**, a następnie uruchom polecenie cmdlet [Connect-AadrmService](http://msdn.microsoft.com/library/azure/dn629415.aspx), aby nawiązać połączenie z usługą Azure RMS:

    ```
    Connect-AadrmService
    ```
    Po wyświetleniu monitu wprowadź poświadczenia administratora dzierżawy usługi [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] (zazwyczaj jest używane konto administratora globalnego usługi Azure Active Directory lub Office 365).

3.  Użyj polecenia cmdlet [Import-AadrmTpd](http://msdn.microsoft.com/library/azure/dn857523.aspx), aby przekazać pierwszy wyeksportowany plik (XML) zaufanej domeny publikacji. Jeśli masz więcej niż jeden plik XML z powodu użycia wielu zaufanych domen publikacji, wybierz plik zawierający wyeksportowaną zaufaną domenę publikacji, którą chcesz zastosować w usłudze Azure RMS do ochrony zawartości po migracji. Użyj następującego polecenia:

    ```
    Import-AadrmTpd -TpdFile <PathToTpdPackageFile> -ProtectionPassword -Active $True -Verbose
    ```
    Na przykład: **Import-AadrmTpd -TpdFile E:\contosokey1.xml -ProtectionPassword -Active $true -Verbose**

    Po wyświetleniu monitu wprowadź określone wcześniej hasło i potwierdź, że chcesz wykonać tę akcję.

4.  Po zakończeniu wykonywania polecenia powtórz krok 3 dla każdego z pozostałych plików XML, które zostały utworzone przez wyeksportowanie zaufanej domeny publikacji. Dla tych plików ustaw opcję **-Active** na wartość **false** podczas uruchamiania polecenia Import. Na przykład: **Import-AadrmTpd -TpdFile E:\contosokey2.xml -ProtectionPassword -Active $false -Verbose**

5.  Użyj polecenia cmdlet [Disconnect-AadrmService](http://msdn.microsoft.com/library/azure/dn629416.aspx), aby zakończyć połączenie z usługą Azure RMS:

    ```
    Disconnect-AadrmService
    ```


Teraz możesz wykonać [Krok 3. Aktywowanie dzierżawy usługi RMS](migrate-from-ad-rms-phase1.md#step-3-activate-your-rms-tenant).





<!--HONumber=Aug16_HO3-->


