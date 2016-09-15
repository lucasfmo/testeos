---
title: "Aktywacja usługi Azure Rights Management | Azure RMS"
description: 
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 05/16/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: f8707e01-b239-4d1a-a1ea-0d1cf9a8d214
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: bf5e3561ef24d8f44e791ff7bdc8450a73f79705
ms.openlocfilehash: d66e4e6bca253bc2bf9d12ba22ed0202cba2edaf


---

# Aktywacja usługi Azure Rights Management

*Dotyczy usług: Azure Rights Management, Office 365*

Po aktywacji usługi [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] (Azure RMS) Twoja organizacja może rozpocząć chronienie ważnych danych za pomocą aplikacji i usług, które obsługują to rozwiązanie ochrony informacji. Administratorzy mogą również zarządzać chronionymi plikami i wiadomościami e-mail organizacji oraz monitorować je. Należy włączyć usługę [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] przed rozpoczęciem korzystania z funkcji zarządzania dostępem do informacji (IRM) w programach Office, SharePoint i Exchange i ochroną wszelkich poufnych plików.

Jeśli chcesz dowiedzieć się więcej na temat usługi Azure Rights Management przed jej aktywowaniem — na przykład o tym, jakie problemy biznesowe rozwiązuje, jak działa i jakie są jej przykładowe, typowe zastosowania — zobacz temat [Co to jest usługa Azure Rights Management?](../understand-explore/what-is-azure-rms.md)

> [!IMPORTANT]
> Przed aktywacją usługi [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] upewnij się, że Twoja organizacja ma plan subskrypcji obejmujący usługi [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)]. Jeśli nie ma, nie można aktywować usługi Azure RMS.
>
> Aby uzyskać więcej informacji, zobacz temat [Subskrypcje usług w chmurze, które obsługują usługi Azure RMS](../get-started/requirements-subscriptions.md).

Po uaktywnieniu usługi Azure RMS wszyscy użytkownicy w organizacji mogą stosować funkcje ochrony informacji wobec swoich plików oraz otwierać pliki (korzystać z nich) chronione przez usługę Azure RMS. Jeśli jednak wolisz ograniczyć możliwość stosowania funkcji ochrony informacji, możesz określić, kto będzie z niej korzystać, stosując kontrolki dołączania we wdrożeniu etapowym. Aby uzyskać więcej informacji, zobacz sekcję [Konfigurowanie kontrolek dołączania we wdrożeniu etapowym](#configuring-onboarding-controls-for-a-phased-deployment) w tym artykule.

Aby uzyskać instrukcje dotyczące aktywowania usługi Rights Management z poziomu portalu zarządzania, wybierz, czy będziesz używać centrum administracyjnego usługi Office 365 (wersja zapoznawcza lub classic) czy klasycznego portalu zarządzania platformy Azure:


- [Centrum administracyjne usługi Office 365 — wersja zapoznawcza](activate-office365-preview.md)
- [Centrum administracyjne usługi Office 365 — wersja classic](activate-office365-classic.md)
- [Klasyczny portal Azure](activate-azure-classic.md)

Alternatywnie możesz użyć programu Windows PowerShell do aktywacji usługi [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)]:

1. Zainstaluj narzędzie Azure Rights Management Administration Tool, które instaluje moduł administracyjny usługi Azure Rights Management. Instrukcje znajdują się w sekcji [Instalowanie programu Windows PowerShell dla usługi Azure Rights Management](../deploy-use/install-powershell.md).

2. W sesji programu Windows PowerShell uruchom polecenie [Connect-AadrmService](https://msdn.microsoft.com/library/windowsazure/dn629415.aspx), a po wyświetleniu odpowiedniego monitu podaj szczegóły konta administratora globalnego dla dzierżawcy usługi Azure RMS.

3. Uruchom polecenie [Enable-Aadrm](http://msdn.microsoft.com/library/windowsazure/dn629412.aspx), które aktywuje usługę Azure RMS.

## Konfigurowanie kontrolek dołączania we wdrożeniu etapowym
Jeśli nie chcesz, aby wszyscy użytkownicy mogli chronić pliki za pomocą usługi Azure RMS, możesz skonfigurować kontrolki dołączania, korzystając z polecenia [Set-AadrmOnboardingControlPolicy](http://msdn.microsoft.com/library/azure/dn857521.aspx) programu Windows PowerShell. To polecenie można uruchomić przed aktywacją lub po aktywacji usługi Azure RMS.

> [!IMPORTANT]
> Aby użyć tego polecenia, musisz mieć co najmniej wersję **2.1.0.0** [modułu programu Windows PowerShell usługi Azure RMS](http://go.microsoft.com/fwlink/?LinkId=257721).
>
> Aby sprawdzić zainstalowaną wersję, uruchom polecenie **(Get-Module aadrm –ListAvailable).Version**

Przykładowo jeśli chcesz, aby wstępnie tylko administratorzy w grupie „dział IT” (o identyfikatorze obiektu fbb99ded-32a0-45f1-b038-38b519009503) mogli chronić zawartość w celach testowych, użyj następującego polecenia:

```
Set-AadrmOnboardingControlPolicy – SecurityGroupObjectId fbb99ded-32a0-45f1-b038-38b519009503
```
Zauważ, że w tej opcji konfiguracji musisz określić grupę; nie można określać poszczególnych użytkowników.

Lub, jeśli chcesz upewnić się, że tylko użytkownicy prawidłowo licencjonowani do użycia usługi Azure RMS będą mogli chronić zawartość:

```
Set-AadrmOnboardingControlPolicy -UseRmsUserLicense $true
```
Jeśli skorzystasz z tych kontrolek dołączania, wszyscy użytkownicy w organizacji zawsze będą mogli skorzystać z chronionej zawartości, która została zabezpieczona przez wybrany podzbiór użytkowników, ale nie będą mogli stosować własnoręcznie funkcji ochrony informacji za pośrednictwem aplikacji klienckich. Przykładowo nie będą widzieć w swoich klientach pakietu Office domyślnych szablonów automatycznie publikowanych po aktywacji usługi Azure RMS lub skonfigurowanych szablonów niestandardowych.  Aplikacje serwerowe, np. program Exchange, mogą wdrażać własne kontrolki dołączania dla integracji z usługą RMS, aby osiągnąć ten sam rezultat.


## Następne kroki
Jako że usługa [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] jest już aktywowana dla Twojej organizacji, możesz użyć [planu wdrożenia usługi Azure Rights Management](../plan-design/deployment-roadmap.md), aby sprawdzić, czy istnieją czynności konfiguracyjne, które należy wykonać przed wdrożeniem usługi [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] dla użytkowników i administratorów. 

Przykładowo możesz użyć [szablonów niestandardowych](configure-custom-templates.md), aby ułatwić użytkownikom stosowanie ochrony informacji wobec plików, połączyć się z lokalnymi serwerami, aby użyć usługi [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] poprzez zainstalowanie [łącznika usługi RMS](deploy-rms-connector.md) i wdrożyć [aplikację Rights Management sharing](../rms-client/sharing-app-windows.md), która obsługuje ochronę wszystkich typów plików na wszystkich urządzeniach. 

Usługi pakietu Office, np. Exchange Online i SharePoint Online, wymagają przeprowadzenia dodatkowej konfiguracji przed użyciem narzędzia Zarządzanie prawami do informacji (IRM). Aby uzyskać informacje o współpracy aplikacji z usługą [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)], zobacz temat [Jak aplikacje obsługują usługę Azure Rights Management](../understand-explore/applications-support.md).




<!--HONumber=Jul16_HO3-->


