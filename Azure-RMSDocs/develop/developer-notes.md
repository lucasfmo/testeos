---
title: "Wskazówki i informacje dla deweloperów | Azure RMS"
description: "W tym temacie podano dokładne wskazówki dotyczące kilku ważnych scenariuszy programowania."
keywords: 
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 5A9F04FD-0FCD-482F-8671-36FE93B783B0
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 91d16ec6e9f9bb359a76562dee7fcb81aac2b44d
ms.openlocfilehash: 2f2323f32327324611df2b2e8a8824e6896546aa


---

# Wskazówki i informacje dla deweloperów

W tej sekcji podano dokładne wskazówki dotyczące kilku ważnych scenariuszy programowania, jak również ogólne informacje dotyczące programowania za pomocą tego zestawu SDK. Scenariusze zawarte w tej sekcji dotyczą tej wersji zestawu Rights Management Services SDK 2.1 i mogą zostać zmienione w kolejnych wersjach.
- [Porada: korzystanie z uwierzytelniania ADAL](how-to-use-adal-authentication.md) — uwierzytelnianie w usługach Azure RMS dla aplikacji z użyciem biblioteki Azure Active Directory Authentication Library (ADAL).
- [Porada: dodawanie jawnych praw właściciela](add-explicit-owner-rights.md) — w przypadku tworzenia licencji od podstaw (przy użyciu funkcji [IpcCreateLicenseFromScratch](/rights-management/sdk/2.1/api/win/functions#msipc_ipccreatelicensefromscratch)) w aplikacji należy jawnie dodać prawa &quot;właściciela&quot;.
- [Porada: debugowanie aplikacji obsługującej prawa](debugging-applications-that-use-ad-rms.md) — w tym temacie opisano metody debugowania aplikacji i korzystania z dziennika zdarzeń systemu Windows.
- [Porada: włączanie śledzenia dokumentów i odwołania](tracking-content.md) — w tym temacie podano podstawowe wskazówki dotyczące implementowania śledzenia dokumentu z zawartością i zawarto przykładowy kod służący do aktualizacji metadanych i tworzenia przycisku **Śledź użycie** na potrzeby aplikacji.
- [Porada: włączanie powiadomień e-mail](how-to-enable-email-notification.md) — powiadomienia e-mail umożliwiają informowanie właściciela chronionej zawartości o dostępie do jego zawartości.
- [Porada: umożliwianie współpracy aplikacji usługi z usługami RMS opartymi na chmurze](how-to-use-file-api-with-aadrm-cloud.md) — w tym temacie opisano kroki konfigurowania aplikacji usługi do korzystania z usługi Azure Rights Management.
- [Porada: instalowanie i konfigurowanie serwera usług RMS](how-to-install-and-configure-an-rms-server.md) — ten temat zawiera opis kroków związanych z nawiązywaniem połączenia z serwerem usług RMS lub usługami Azure RMS na potrzeby testowania aplikacji obsługującej prawa.
- [Porada: ustawianie trybu zabezpieczeń interfejsu API](setting-the-api-security-mode-api-mode.md) — za pomocą funkcji [IpcSetGlobalProperty](/rights-management/sdk/2.1/api/win/functions#msipc_ipcsetglobalproperty) można wybrać tryb zabezpieczeń, w którym uruchamiana jest aplikacja interfejsu API plików.
- [Porada: praca z ustawieniami szyfrowania](working-with-encryption.md) — ten temat umożliwia zapoznanie się z pakietami szyfrowania firmy Microsoft i zawiera przykładowe fragmenty kodu, w których zastosowano te pakiety.
- [Typy aplikacji](application-types.md) — w tym temacie omówiono typy aplikacji, które można wybrać do utworzenia jako aplikacje obsługujące prawa.
- [Konfiguracja interfejsu API plików](file-api-configuration.md) — działanie interfejsu API plików można skonfigurować za pomocą ustawień rejestru.
- [Obsługiwane typy plików](supported-file-formats.md) — interfejs API plików obsługuje formaty natywne i Pfile
- [Obsługiwane platformy](supported-platforms.md) — ten temat zawiera informacje o platformach klientów i serwerów obsługiwanych przez zestaw RMS SDK 2.1.
- [Opis ograniczeń użycia](understanding-usage-restrictions.md) — wszystkie aplikacje z obsługą usług RMS muszą wymuszać ograniczenia użycia.
- [Informacje o ograniczeniach użycia](usage-restriction-reference.md) — ograniczenia użycia są definiowane przez stałe wymienione w tym temacie.

 
## Tematy pokrewne ##
* [Przegląd](ad-rms-overview.md)
 

 



<!--HONumber=Jun16_HO4-->


