---
title: "Mapa wdrożenia usługi Azure Rights Management | Azure RMS"
description: 
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 05/09/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 086600c2-c5d8-47ec-a4c0-c782e1797486
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 7f8a4d53665dd79a6d0e02d340b0e7a09d995e00
ms.openlocfilehash: 96ee0aa3151ede8b8a263f3ce6c3d2e5b8ec9c81


---

# Mapa wdrożenia usługi Azure Rights Management

*Dotyczy usług: Azure Rights Management, Office 365*

Wykonaj poniższe kroki, aby przygotować się do wdrożenia usługi Azure Rights Management (Azure RMS) dla organizacji, wdrożyć ją i zarządzać nią.

Jeśli jednak chcesz szybko wypróbować usługę Azure RMS we własnym zakresie zamiast wdrażać ją w środowisku produkcyjnym, zobacz [Samouczek Szybki start dotyczący usługi Azure Rights Management](../get-started/quick-start-tutorial.md).

Aby uzyskać listę konkretnych scenariuszy, powiązanych kroków dotyczących konfiguracji i dokumentację użytkownika końcowego, zobacz [Szybkie wdrażanie usługi Azure Rights Management](../get-started/rapid-deployment-guide.md).

> [!IMPORTANT]
> Przed wykonaniem poniższych kroków zapoznaj się z tematem [Wymagania dotyczące usługi Azure Rights Management](../get-started/requirements-azure-rms.md).

## Krok 1. Sprawdź, czy masz subskrypcję obejmującą usługę Azure Rights Management
Istnieje kilka typów subskrypcji obejmujących usługę [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)]. Zobacz temat [Subskrypcje usług w chmurze, które obejmują usługę Azure RMS](../get-started/requirements-subscriptions.md) i sprawdź, czy Twoja subskrypcja obejmuje funkcje, których chcesz używać w organizacji, odnosząc się do tabeli w temacie [Porównanie ofert Usług Rights Management (RMS)](https://technet.microsoft.com/dn858608). Należy przypisać licencję z tej subskrypcji do wszystkich użytkowników w organizacji, którzy będą chronić pliki i wiadomości e-mail przy użyciu usługi Azure RMS.

## Krok 2. Przygotuj swoje konto dzierżawy do używania usługi Rights Management
Przed rozpoczęciem korzystania z usługi [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] przeprowadź następujące przygotowania:

1.  Upewnij się, że dzierżawa usługi Azure lub Office 365 obejmuje konta użytkowników i grupy, które będą używane przez usługę Azure RMS do uwierzytelniania użytkowników z organizacji. W razie potrzeby utwórz to konto i grupy lub zsynchronizuj je z katalogu lokalnego. Aby uzyskać więcej informacji, zobacz [Przygotowanie do wdrożenia usługi Azure Rights Management](prepare.md).

2.  Określ, czy Twoim kluczem dzierżawy powinna zarządzać firma Microsoft (opcja domyślna), czy też chcesz wygenerować klucz dzierżawy i zarządzać nim samodzielnie (opcja nazywana „przynieś własny klucz”, BYOK). Pamiętaj, że obecnie nie możesz korzystać z opcji BYOK, jeśli używasz usługi Exchange Online. Aby uzyskać więcej informacji, zobacz [Planowanie i wdrażanie klucza dzierżawy usługi Azure Rights Management](plan-implement-tenant-key.md).

3.  Zainstaluj moduł Windows PowerShell dla usługi [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] na co najmniej jednym komputerze z dostępem do Internetu. Możesz wykonać ten krok teraz lub później. Aby uzyskać więcej informacji, zobacz [Instalowanie programu Windows PowerShell dla usługi Azure Rights Management](../deploy-use/install-powershell.md).

4.  Jeśli obecnie używasz lokalnych usług Rights Management: przeprowadź migrację, aby przenieść klucze, szablony i adresy URL do chmury. Aby uzyskać więcej informacji, zobacz [Migrowanie z usług AD RMS do usługi Azure Rights Management](migrate-from-ad-rms-to-azure-rms.md).

5.  Aktywuj usługę Rights Management, aby rozpocząć korzystanie z usługi. Jeśli wymagane jest wdrożenie etapowe, skonfiguruj kontrolki dołączania użytkowników, aby ograniczyć użytkowanie do określonych użytkowników. Aby uzyskać więcej informacji, zobacz [Aktywacja usługi Azure Rights Management](../deploy-use/activate-service.md).

Opcjonalnie rozważ skonfigurowanie następujących elementów:

-   Szablony niestandardowe, jeśli domyślne szablony zasad praw nie są wystarczające dla Twojej organizacji. Możesz wykonać ten krok teraz lub później. Aby uzyskać więcej informacji, zobacz [Konfigurowanie szablonów niestandardowych usługi Azure Rights Management](../deploy-use/configure-custom-templates.md).

-   Rejestrowanie użytkowania, umożliwiające monitorowanie wykorzystania usługi Rights Management przez organizację. Możesz wykonać ten krok teraz lub później. Aby uzyskać więcej informacji, zobacz [Rejestrowanie i analizowanie danych użycia usługi Azure Rights Management](../deploy-use/log-analyze-usage.md).

## Krok 3. Skonfiguruj aplikacje i usługi dla usługi Rights Management
Konfigurowanie aplikacji i usług może obejmować instalację aplikacji udostępniania usługi Rights Management oraz włączenie obsługi funkcji zarządzania prawami do informacji (IRM) w usłudze SharePoint Online lub Exchange Online. Aby uzyskać więcej informacji, zobacz [Konfigurowanie aplikacji do współdziałania z usługą Azure Rights Management](../deploy-use/configure-applications.md).

Jeśli masz istniejące usługi IT, które wymagają inspekcji plików chronionych przez usługę Azure RMS, takie jak rozwiązania zapobiegania wyciekom danych (DLP), bramy szyfrowania zawartości (CEG) i produkty chroniące przed złośliwym oprogramowaniem, skonfiguruj konta usług jako superużytkowników usługi Azure RMS. Aby uzyskać więcej informacji, zobacz [Konfigurowanie superużytkowników usługi Azure Rights Management i usług odnajdywania lub odzyskiwania danych](../deploy-use/configure-super-users.md).

Aby włączyć funkcje zbiorczej ochrony i wyłączania ochrony wszystkich typów plików, zainstaluj narzędzie RMS Protection Tool, które korzysta z modułu RMS Protection PowerShell. Aby uzyskać więcej informacji, zobacz [RMS Protection Cmdlets](https://msdn.microsoft.com/library/mt433195.aspx) (Polecenia cmdlet narzędzia RMS Protection).

Jeśli masz usługi lokalne, których chcesz używać z usługą Azure Rights Management, zainstaluj i skonfiguruj łącznik usługi Rights Management. Aby uzyskać więcej informacji, zobacz [Wdrażanie łącznika usługi Azure Rights Management](../deploy-use/deploy-rms-connector.md).

## Krok 4. Opublikuj zawartość chronioną prawami i korzystaj z niej
Masz teraz wszystko gotowe do publikowania zawartości chronionej i korzystania z niej oraz rejestrowania sposobu korzystania z usługi Rights Management przez firmę. Aby uzyskać więcej informacji, zobacz [Ułatwienia dla użytkowników dotyczące ochrony plików za pomocą usługi Azure Rights Management](../deploy-use/help-users.md) i [Rejestrowanie i analizowanie danych użycia usługi Azure Rights Management](../deploy-use/log-analyze-usage.md).

Jeśli interesuje Cię automatyczne chronienie plików przy użyciu infrastruktury klasyfikacji plików na serwerze plików opartym na systemie Windows, zobacz temat [Ochrona za pomocą usług RMS z użyciem infrastruktury klasyfikacji plików (FCI, File Classification Infrastructure) w systemie Windows Server](../rms-client/configure-fci.md).

## Krok 5. Zarządzaj usługą Rights Management dla swojego konta dzierżawy zgodnie z potrzebami
Po rozpoczęciu korzystania z usługi [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] moduł [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] dla programu Windows PowerShell może okazać się pomocny w tworzeniu skryptów i automatyzacji zmian administracyjnych. Aby uzyskać więcej informacji, zobacz [Administrowanie usługą Azure Rights Management przy użyciu programu Windows PowerShell](../deploy-use/administer-powershell.md).





<!--HONumber=Jun16_HO4-->


