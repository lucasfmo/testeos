---
title: "Konfigurowanie aplikacji do współdziałania z usługą Azure Rights Management | Azure RMS"
description: 
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: ea09cbc5-b98b-444e-8b60-5bc3cb199c36
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 0f355da35dff62ecee111737eb1793ae286dc93e
ms.openlocfilehash: 8fe934c51e852791d19fbb336deaf9cd7be9817b


---

# Konfigurowanie aplikacji do współdziałania z usługą Azure Rights Management

*Dotyczy usług: Azure Rights Management, Office 365*

> [!NOTE]
> Te informacje są przeznaczone dla administratorów i doradców IT, którzy wdrożyli usługę Azure Rights Management. Jeśli szukasz pomocy dla użytkowników i informacji na temat sposobu używania usługi Rights Management dla określonej aplikacji lub sposobu otwierania pliku z ochroną praw, skorzystaj z pomocy i wskazówek dołączonych do aplikacji.
>
> Na przykład w przypadku aplikacji pakietu Office kliknij ikonę Pomoc i wprowadź terminy wyszukiwania, takie jak **Rights Management** lub **IRM**. W przypadku aplikacji do udostępniania usługi RMS dla systemu Windows skorzystaj z [Podręcznika użytkownika aplikacji do udostępniania usługi Rights Management](../rms-client/sharing-app-user-guide.md).

Po wdrożeniu usługi Azure Rights Management (Azure RMS) dla organizacji skonfiguruj aplikacje i usługi do obsługi usługi Azure RMS, korzystając z poniższych informacji. Dotyczy to aplikacji pakietu Office, takich jak Word 2013 i Word 2010 oraz usług, takich jak Exchange Online (zasady transportu, zapobieganie utracie danych, blokowanie przesyłania dalej i szyfrowanie wiadomości) i SharePoint Online (biblioteki chronione). Aby dowiedzieć się, jak te aplikacje i usługi obsługują usługę Rights Management, zobacz [Jak aplikacje obsługują usługę Azure Rights Management](../understand-explore/applications-support.md).

> [!IMPORTANT]
> Aby uzyskać informacje na temat obsługiwanych wersji i innych wymagań, zobacz [Wymagania dotyczące usługi Azure Rights Management](../get-started/requirements-azure-rms.md).

-   [Usługa Office 365: konfiguracja dla klientów i usług online](configure-office365.md)

    -   [Usługa Exchange Online: konfiguracja usługi IRM](configure-office365.md#exchange-online-irm-configuration)

    -   [Usługi SharePoint Online i OneDrive dla Firm: konfiguracja usługi IRM](configure-office365.md#sharepoint-online-and-onedrive-for-business-irm-configuration)

- [Aplikacje pakietu Office: konfiguracja dla klientów](configure-office-apps.md)

    -   [Pakiety Office 2016 i Office 2013](configure-office-apps.md#office-2016-and-office-2013)

    -   [Pakiet Office 2010](configure-office-apps.md#office-2010)

-   [Aplikacja do udostępniania usługi Rights Management: instalacja i konfiguracja dla klientów](configure-sharing-app.md)

    -   [Aplikacja RMS sharing dla systemu Windows: instalacja i konfiguracja](configure-sharing-app.md#the-rms-sharing-application-for-windows-installation-and-configuration)

    -   [Aplikacja RMS sharing dla platform urządzeń przenośnych: instalacja i zarządzanie](configure-sharing-app.md#the-rms-sharing-application-for-mobile-platforms-installation-and-management)


Aby skonfigurować serwery lokalne, takie jak Exchange Server i SharePoint Server, zobacz [Wdrażanie łącznika usługi Azure Rights Management](deploy-rms-connector.md).

> [!TIP]
> Aby wyświetlić ogólne przykłady i zrzuty ekranu aplikacji skonfigurowanych do korzystania z usługi Azure RMS, zobacz [Azure RMS w działaniu: co widzą administratorzy i użytkownicy](../understand-explore/what-admins-users-see.md).


Oprócz tych aplikacji i usług istnieją inne aplikacje obsługujące interfejsy API usługi RMS. Do tej kategorii należą aplikacje biznesowe, które są tworzone we własnym zakresie za pomocą zestawu RMS SDK, i aplikacje od dostawców oprogramowania tworzone przy użyciu zestawu RMS SDK. W przypadku tych aplikacji postępuj zgodnie z instrukcjami dostarczonymi z aplikacją.

## Następne kroki
Po skonfigurowaniu aplikacji do obsługi usługi Azure Rights Management użyj [planu wdrożenia usługi Azure Rights Management](../plan-design/deployment-roadmap.md), aby sprawdzić, czy istnieją inne czynności konfiguracyjne, które należy wykonać przed wdrożeniem usługi [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] dla użytkowników i administratorów. Jeśli nie, przydatne mogą być następujące informacje operacyjne:

- [Weryfikowanie usługi Azure Rights Management](verify.md)

- [Ułatwienia dla użytkowników dotyczące ochrony plików za pomocą usługi Azure Rights Management](help-users.md)

- [Rejestrowanie i analizowanie usługi Azure Rights Management](log-analyze-usage.md)

- [Operacje związane z kluczem dzierżawy usługi Azure Rights Management](operations-tenant-key.md)





<!--HONumber=Jul16_HO3-->


