---
title: "Administrowanie usługą Azure Rights Management przy użyciu programu Windows PowerShell | Azure RMS"
description: 
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 08/18/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: a890e04a-4b70-41b5-8d5f-3c210a669faa
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: a80866576dc7d6400bcebc2fc1c37bc0367bcdf3
ms.openlocfilehash: d2aec9c4a0c462e9abfa145ee14df0144c60e584


---

# Administrowanie usługą Azure Rights Management przy użyciu programu Windows PowerShell

*Dotyczy usług: Azure Rights Management, Office 365*

Mimo że usługę Microsoft [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] (Azure RMS) można aktywować za pomocą centrum administracyjnego usługi [!INCLUDE[o365_2](../includes/o365_2_md.md)] lub klasycznego portalu Azure, można także użyć w tym celu modułu programu Windows PowerShell dla usługi [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] (AADRM).

Po aktywowaniu usługi [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] dalsze czynności administracyjne dla tej usługi mogą nie być wymagane. Jednak niektóre scenariusze konfiguracji zaawansowanej mogą wymagać użycia modułu programu Windows PowerShell dla usługi [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)]. Poniższa tabela zawiera niektóre scenariusze konfiguracji zaawansowanej, które korzystają z programu Windows PowerShell. Aby uzyskać pełną listę dostępnych poleceń cmdlet i więcej informacji o każdym z nich, zobacz [Azure Rights Management Cmdlets](http://msdn.microsoft.com/library/azure/dn629398.aspx) (Polecenia cmdlet usługi Azure Rights Management).

> [!NOTE]
> Jeśli musisz zainstalować moduł Windows PowerShell dla usługi [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)], zobacz [Instalowanie programu Windows PowerShell dla usługi Azure Rights Management](install-powershell.md).

Jest również uzupełniający moduł programu Windows PowerShell, **RMSProtection**, który obsługuje zarówno usługę Azure RMS, jak i AD RMS. Ten moduł obsługuje ochronę i usuwanie ochrony wielu plików, aby na przykład chronić zbiorczo wszystkie pliki w folderze. Aby uzyskać więcej informacji, zobacz sekcję [Opcje obsługi skryptów dla superużytkowników](configure-super-users.md#scripting-options-for-super-users) w artykule [Konfigurowanie superużytkowników usługi Azure Rights Management i usług odnajdywania lub odzyskiwania danych](configure-super-users.md).

|Jeśli chcesz...|...użyj następujących poleceń cmdlet|
|-------------------|------------------------------|
|Wykonać migrację z lokalnej usługi Rights Management (AD RMS lub Windows RMS) do usługi [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)].|[Import-AadrmTpd](http://msdn.microsoft.com/library/azure/dn857523.aspx)|
|Połączyć lub rozłączyć się z usługą [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] dla Twojej organizacji.|[Connect-AadrmService](http://msdn.microsoft.com/library/azure/dn629415.aspx)<br /><br />[Disconnect-AadrmService](http://msdn.microsoft.com/library/azure/dn629416.aspx)|
|Wygenerować własny klucz dzierżawy i zarządzać nim — scenariusz dostarczania własnego klucza (BYOK).|[Use-AadrmKeyVaultKey](https://msdn.microsoft.com/library/azure/mt759829.aspx)<br /><br />[Get-AadrmKeys](http://msdn.microsoft.com/library/azure/dn629420.aspx)|
|Aktywować lub dezaktywować usługę [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] dla Twojej organizacji.|[Enable-Aadrm](http://msdn.microsoft.com/library/azure/dn629412.aspx)<br /><br />[Disable-Aadrm](http://msdn.microsoft.com/library/azure/dn629422.aspx)|
|Wyłączyć lub włączyć lokację śledzenia dokumentów dla usługi Azure Rights Management.|[Disable-AadrmDocumentTrackingFeature](https://msdn.microsoft.com/library/azure/mt548471.aspx)<br /><br />[Enable-AadrmDocumentTrackingFeature](https://msdn.microsoft.com/library/azure/mt548469.aspx)<br /><br />[Get-AadrmDocumentTrackingFeature](https://msdn.microsoft.com/library/azure/mt548470.aspx)|
|Skonfigurować kontrolki dołączania we wdrożeniu etapowym usługi Azure Rights Management.|[Get-AadrmOnboardingControlPolicy](http://msdn.microsoft.com/library/azure/dn857522.aspx)<br /><br />[Set-AadrmOnboardingControlPolicy](http://msdn.microsoft.com/library/azure/dn857521.aspx)|
|Utworzyć szablony zasad praw dla Twojej organizacji i zarządzać nimi.|[Add-AadrmTemplate](http://msdn.microsoft.com/library/azure/dn727075.aspx)<br /><br />[Export-AadrmTemplate](http://msdn.microsoft.com/library/azure/dn727078.aspx)<br /><br />[Get-AadrmTemplate](http://msdn.microsoft.com/library/azure/dn727079.aspx)<br /><br />[Get-AadrmTemplateProperty](http://msdn.microsoft.com/library/azure/dn727081.aspx)<br /><br />[Import-AadrmTemplate](http://msdn.microsoft.com/library/azure/dn727077.aspx)<br /><br />[New-AadrmRightsDefinition](http://msdn.microsoft.com/library/azure/dn727080.aspx)<br /><br />[Remove-AadrmTemplate](http://msdn.microsoft.com/library/azure/dn727082.aspx)<br /><br />[Set-AadrmTemplateProperty](http://msdn.microsoft.com/library/azure/dn727076.aspx)|
|Skonfigurować maksymalną liczbę dni, przez jaką zawartość chroniona przez organizację może być dostępna bez połączenia internetowego (okres ważności licencji użytkowania).|[Get-AadrmMaxUseLicenseValidityTime](https://msdn.microsoft.com/library/azure/dn932062.aspx)<br /><br />[Set-AadrmMaxUseLicenseValidityTime](https://msdn.microsoft.com/library/azure/dn932063.aspx)|
|Zarządzać funkcją superużytkowników usługi [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] dla Twojej organizacji.|[Enable-AadrmSuperUserFeature](https://msdn.microsoft.com/library/azure/dn629400.aspx)<br /><br />[Disable-AadrmSuperUserFeature](https://msdn.microsoft.com/library/azure/dn629428.aspx)<br /><br />[Add-AadrmSuperUser](http://msdn.microsoft.com/library/azure/dn629411.aspx)<br /><br />[Get-AadrmSuperUser](https://msdn.microsoft.com/library/azure/dn629408.aspx)<br /><br />[Remove-AadrmSuperUser](https://msdn.microsoft.com/library/azure/dn629405.aspx)<br /><br />[Set-AadrmSuperUserGroup](https://msdn.microsoft.com/library/azure/mt653943.aspx)<br /><br />[Get-AadrmSuperUserGroup](https://msdn.microsoft.com/library/azure/mt653942.aspx)<br /><br />[Clear-AadrmSuperUserGroup](https://msdn.microsoft.com/library/azure/mt653944.aspx)|
|Zarządzać użytkownikami i grupami, które mają uprawnienia do administrowania usługą [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] dla Twojej organizacji.|[Add-AadrmRoleBasedAdministrator](http://msdn.microsoft.com/library/azure/dn629417.aspx)<br /><br />[Get-AadrmRoleBasedAdministrator](https://msdn.microsoft.com/library/azure/dn629407.aspx)<br /><br />[Remove-AadrmRoleBasedAdministrator](https://msdn.microsoft.com/library/azure/dn629424.aspx)|
|Pobrać dziennik zadań administracyjnych usługi [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] dla Twojej organizacji.|[Get-AadrmAdminLog](https://msdn.microsoft.com/library/azure/dn629430.aspx)|
|Rejestrować i analizować dzienniki użycia dla usługi [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)].|[Get-AadrmUserLog](https://msdn.microsoft.com/library/azure/mt653941.aspx)|
|Wyświetlić bieżącą konfigurację usługi [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] dla Twojej organizacji.|[Get-AadrmConfiguration](http://msdn.microsoft.com/library/azure/dn629410.aspx)|
|Przeprowadzić migrację organizacji z usługi [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] do lokalnego wdrożenia usług AD RMS.|[Set-AadrmMigrationUrl](https://msdn.microsoft.com/library/azure/dn629429.aspx)<br /><br />[Get-AadrmMigrationUrl](http://msdn.microsoft.com/library/azure/dn629403.aspx)|






<!--HONumber=Aug16_HO3-->


