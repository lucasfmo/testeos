---
title: "Cennik i ograniczenia dotyczące funkcji BYOK | Azure RMS"
description: 
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 08/17/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: f5930ed3-a6cf-4eac-b2ec-fcf63aa4e809
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 437afd88efebd9719a3db98f8ab0ae07403053f7
ms.openlocfilehash: ece615912d69eda78107c60245620ed36c0affd2


---

# Cennik i ograniczenia dotyczące funkcji BYOK

*Dotyczy usług: Azure Rights Management, Office 365*


Organizacje, które mają subskrypcję obejmującą usługę Azure Rights Management, mogą używać kluczy zarządzanych przez klienta (BYOK) w usłudze Azure Key Vault i rejestrować ich użycie bez dodatkowych opłat. Niemniej, aby użyć usługi Azure Key Vault, musisz mieć subskrypcję platformy Azure obsługującą usługę Key Vault z kluczami chronionymi za pomocą modułu HSM. Użycie klucza w usłudze Azure Key Vault generuje opłatę miesięczną. Aby uzyskać więcej informacji, zobacz [stronę z cenami usługi Azure Key Vault](https://azure.microsoft.com/en-us/pricing/details/key-vault/).

Jeśli istnieją użytkownicy, którzy zarejestrowali się na bezpłatne konto przy użyciu usługi RMS dla użytkowników indywidualnych, nie możesz użyć rozwiązania BYOK i rejestrowania użycia, ponieważ ta konfiguracja nie ma administratora dzierżawy do skonfigurowania tych funkcji.


> [!NOTE]
> Więcej informacji o usługach RMS dla użytkowników indywidualnych zawiera temat [Usługa RMS dla użytkowników indywidualnych i usługa Azure Rights Management](../understand-explore/rms-for-individuals.md).

![Funkcja BYOK nie obsługuje usługi Exchange Online](../media/RMS_BYOK_noExchange.png)

Rozwiązanie BYOK i rejestrowanie użycia współpracują bezproblemowo z każdą aplikacją, która integruje się z usługą Azure RMS. Dotyczy to usług w chmurze, takich jak SharePoint Online, serwerów lokalnych z programem Exchange i SharePoint, które współpracują z usługą Azure RMS za pomocą łącznika usługi RMS, a także aplikacji klienckich, np. Office 2016 i Office 2013. Dzienniki użycia klucza uzyskasz niezależnie od tego, która aplikacja zgłasza żądania dotyczące usługi Azure RMS.

Istnieje jeden wyjątek: obecnie **usługa Azure RMS BYOK nie jest zgodna z usługą Exchange Online**. Użytkownikom usługi Exchange Online zaleca się wdrożenie usługi Azure RMS w domyślnym trybie zarządzania kluczami, w którym firma Microsoft generuje klucze i zarządza nimi. Istnieje możliwość skorzystania z funkcji BYOK w późniejszym czasie, na przykład wtedy, gdy dla usługi Exchange Online zostanie zapewniona obsługa trybu BYOK usługi Azure RMS. Jeśli nie możesz czekać, istnieje inne rozwiązanie. Możesz wdrożyć usługę Azure RMS z funkcją BYOK już teraz, ale będzie ona mieć ograniczoną funkcjonalność w przypadku usługi Exchange Online (niechronione wiadomości e-mail i załączniki pozostaną w pełni funkcjonalne):

-   Nie można wyświetlać chronionych wiadomości e-mail i załączników w usłudze Outlook Web Access.

-   Nie można wyświetlać chronionych wiadomości e-mail na urządzeniach przenośnych, które używają programu Exchange ActiveSync z funkcją IRM.

-   Odszyfrowywanie transportu (np. w celu przeprowadzenia skanowania w poszukiwaniu złośliwego oprogramowania) oraz dziennika nie jest możliwe, dlatego chronione wiadomości e-mail i załączniki będą pomijane.

-   Reguły ochrony transportu i zapobiegania utracie danych (DLP), które wymuszają zasady IRM, są niedostępne, dlatego nie można wdrożyć ochrony RMS za pomocą tych metod.

-   Podczas wyszukiwania chronionych wiadomości e-mail na serwerze zostaną one pominięte.

W przypadku korzystania z usługi Azure RMS BYOK z ograniczoną funkcjonalnością usługi RMS w usłudze Exchange Online usługa RMS będzie współpracować z klientami poczty e-mail w programie Outlook w systemach Windows i Mac. Nie będzie współpracować z żadnym innym klientem poczty e-mail, który nie używa programu Exchange ActiveSync z funkcją IRM.

Jeśli użytkownik migruje do usługi Azure RMS z usług AD RMS, możliwe że zaimportował klucz jako zaufaną domenę publikacji (TPD) do usługi Exchange Online (co jest nazywane rozwiązaniem BYOK w terminologii programu Exchange, jednak różni się od rozwiązania BYOK usługi Azure Key Vault). W tym scenariuszu należy usunąć zaufaną domenę publikacji z usługi Exchange Online, aby uniknąć konfliktów szablonów i zasad. Aby uzyskać więcej informacji, zobacz temat [Remove-RMSTrustedPublishingDomain](https://technet.microsoft.com/library/jj200720%28v=exchg.150%29.aspx) w bibliotece poleceń cmdlet usługi Exchange Online.

Czasami wyjątek usługi Azure RMS BYOK dla usługi Exchange Online nie stanowi problemu w praktyce. Przykładowo jest tak w przypadku organizacji potrzebujących funkcji BYOK i rejestrowania, które uruchamiają swoje aplikacje do obsługi danych (Exchange, SharePoint, Office) lokalnie i używają usługi Azure RMS w celu korzystania z funkcji, która nie jest łatwo dostępna z lokalną usługą AD RMS (np. w przypadku współpracy z innymi firmami i uzyskiwaniem dostępu z klientów mobilnych). Zarówno funkcja BYOK, jak i możliwość rejestrowania będą działać prawidłowo w tym scenariuszu, a organizacja zachowa pełną kontrolę nad swoją subskrypcją usługi Azure RMS.

## Następne kroki

Jeśli zdecydujesz się na zarządzanie własnym kluczem, przejdź do tematu [Wdrażanie klucza dzierżawy usługi Azure Rights Management](plan-implement-tenant-key.md#implementing-your-azure-rights-management-tenant-key).

Jeśli zdecydujesz się nadal używać domyślnej konfiguracji, w której firma Microsoft zarządza kluczem dzierżawy, zobacz sekcję [Następne kroki](plan-implement-tenant-key.md#next-steps) w artykule Planowanie i wdrażanie klucza dzierżawy usługi Azure Rights Management.




<!--HONumber=Aug16_HO3-->


