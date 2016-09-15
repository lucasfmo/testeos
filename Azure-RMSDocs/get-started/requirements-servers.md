---
title: "Wymagania dotyczące usługi Azure RMS: serwery lokalne obsługujące usługę Azure Rights Management | Azure RMS"
description: 
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: e7d91f2d-d6a7-4c7e-821f-c94e4be9967d
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ed50d87138c428fadfd22cd5b3ef3c7f7e421848
ms.openlocfilehash: 7e718d8178dd7c4b18ea7a19eb3165ee06dc4b36


---


# Wymagania dotyczące usługi Azure RMS: serwery lokalne, które obsługują usługę Azure RMS

*Dotyczy usług: Azure Rights Management, Office 365*

Następujące lokalne produkty serwerowe są obsługiwane za pomocą usługi Azure RMS w przypadku korzystania z łącznika usługi Azure RMS działającego jako interfejs komunikacji (przekaźnik) między serwerami lokalnymi i usługą Azure RMS. Ponadto w ramach tej konfiguracji należy skonfigurować synchronizację katalogów między lasami usługi Active Directory i usługą Azure Active Directory.

-   **Exchange Server**:

    -   Exchange Server 2016

    -   Exchange Server 2013

    -   Exchange Server 2010

-   **Office SharePoint Server**:

    -   Office SharePoint Server 2016

    -   Office SharePoint Server 2013

    -   Office SharePoint Server 2010

-   **Serwery plików z systemem Windows Server, które obsługują infrastrukturę klasyfikacji plików**:

    -   Windows Server 2012 R2

    -   Windows Server 2012

    > [!NOTE]
    > Ponieważ serwery plików z systemem Windows Server 2008 R2 nie mają wbudowanej akcji zadania zarządzania plikami, która pozwala na zastosowanie ochrony przy użyciu usługi RMS, w tym scenariuszu nie można używać łącznika usługi RMS. Można jednak użyć pliku klasyfikacji infrastruktury i usługi Azure RMS w tych systemach operacyjnych w przypadku konfigurowania niestandardowego zadania zarządzania plikami, aby uruchomić plik wykonywalny lub skrypt służący do ochrony plików przy użyciu usługi Azure RMS. Na przykład skrypt programu Windows PowerShell, który używa [poleceń cmdlet ochrony usługi RMS](https://msdn.microsoft.com/library/azure/mt433195.aspx).
    > 
    > Można również używać tych poleceń cmdlet na serwerach z nowszymi wersjami systemu Windows Server, ponieważ umożliwiają one ochronę wszystkich typów plików. Łącznik usługi RMS chroni tylko pliki pakietu Office. Dokładne instrukcje można znaleźć w temacie [Ochrona za pomocą usługi RMS z użyciem infrastruktury klasyfikacji plików (FCI)](../rms-client/configure-fci.md).

Łącznik usługi RMS jest obsługiwany w systemie Windows Server 2012 R2, Windows Server 2012 i Windows Server 2008 R2.

Aby uzyskać więcej informacji o sposobie konfigurowania łącznika usługi RMS na tych serwerach lokalnych, zobacz [Wdrażanie łącznika usługi Azure Rights Management](../deploy-use/deploy-rms-connector.md).

## Następne kroki
Aby sprawdzić pozostałe wymagania, zobacz [Wymagania dotyczące usługi Azure Rights Management](requirements-azure-rms.md).



<!--HONumber=Jul16_HO3-->


