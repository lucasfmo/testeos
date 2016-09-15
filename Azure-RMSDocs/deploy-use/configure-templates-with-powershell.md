---
title: "Informacje dotyczące obsługi szablonów niestandardowych w programie PowerShell | Azure RMS"
description: 
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 05/20/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 30ee2f77-ce16-4113-bcda-6089131849ec
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 332e102cb27854314b93a71bfeae82a95c9a7812
ms.openlocfilehash: 645f9ed4080e3b38fcda9afe148923c021046724


---



# Informacje dotyczące obsługi szablonów niestandardowych w programie PowerShell

*Dotyczy usług: Azure Rights Management, Office 365*

Wszystkie czynności, które można wykonać w klasycznym portalu Azure w celu tworzenia szablonów i zarządzania nimi, można wykonać z poziomu wiersza polecenia, korzystając z programu PowerShell. Ponadto istnieje możliwość eksportowania i importowania szablonów, dzięki czemu można kopiować szablony między dzierżawami i dokonywać edycji zbiorczej złożonych właściwości w szablonach, takich jak wielojęzyczne nazwy i opisy.

Można również używać funkcji eksportowania i importowania w celu tworzenia kopii zapasowych szablonów niestandardowych i ich przywracania. Najlepszym rozwiązaniem jest regularne tworzenie kopii zapasowych szablonów niestandardowych, dzięki któremu po ewentualnym przypadkowym wprowadzeniu zmiany można łatwo przywrócić poprzednią wersję szablonów.

> [!IMPORTANT]
> Aby użyć środowiska Windows PowerShell do tworzenia szablonów zasad praw usługi Azure RMS i zarządzania nimi, użytkownik musi dysponować co najmniej wersją 2.0.0.0 [modułu Windows PowerShell dla usługi Azure RMS](http://go.microsoft.com/fwlink/?LinkId=257721).
> 
> Jeśli wcześniej zainstalowano ten moduł programu PowerShell, należy uruchomić następujące polecenie w oknie PowerShell, aby sprawdzić numer wersji: `(Get-Module aadrm -ListAvailable).Version`

Instrukcje instalacji znajdują się w sekcji [Instalowanie programu Windows PowerShell dla usługi Azure Rights Management](install-powershell.md).

Polecenia cmdlet używane do tworzenia szablonów i zarządzania nimi:

-   [Add-AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727075.aspx)

-   [Export-AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727078.aspx)

-   [Get-AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727079.aspx)

-   [Get-AadrmTemplateProperty](https://msdn.microsoft.com/library/azure/dn727081.aspx)

-   [Import-AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727077.aspx)

-   [New-AadrmRightsDefinition](https://msdn.microsoft.com/library/azure/dn727080.aspx)

-   [Remove-AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727082.aspx)

-   [Set-AadrmTemplateProperty](https://msdn.microsoft.com/library/azure/dn727076.aspx)



## Zobacz też
[Konfigurowanie szablonów niestandardowych usługi Azure Rights Management](configure-custom-templates.md)


<!--HONumber=Jun16_HO4-->


