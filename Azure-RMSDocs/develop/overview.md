---
title: "Przegląd — zestaw RMS SDK 4.2 | Azure RMS"
description: "AD RMS i Azure RMS to technologia ochrony informacji, która pomaga w zabezpieczaniu informacji cyfrowych przed nieautoryzowanym użyciem."
keywords: 
author: bruceperlerms
manager: mbaldwin
ms.date: 07/11/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 8A13494E-C1D7-407D-BCD1-A406915EA578
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 5afdf526fe9f8486c6a778eebf10899e0bd9f839
ms.openlocfilehash: d55a16d7ff6f11db3c02d3494dcdd088bffc8500


---

# Przegląd

Zestaw SDK 4.2 usługi Microsoft Rights Management to technologia ochrony informacji dostępna dla różnych platform.  Jest to zestaw dewelopera oprogramowania (SDK) lub architektura, której celem jest pomoc komputerom i urządzeniom klienckim w ochronie dostępu do informacji przepływających przez aplikacje obsługujące prawa i w korzystaniu z tych informacji. Zestawy SDK dla tych platform zapewniają prosty interfejs API dla deweloperów aplikacji, który umożliwia ochronę i korzystanie z zawartości cyfrowej, pobieranie szablonów i uzyskiwanie zasad z serwera oraz powiązanych zadań zarządzania prawami.

Dodatkowe informacje na temat obsługiwanych obecnie aplikacji są dostępne w portalu dokumentacji dla deweloperów dla [zestawu SDK usługi Microsoft Rights Management](active-directory-rights-management-services-multi-platform-thin-client-sdk-portal.md).

Poniżej zamieszczono kilka możliwych scenariuszy:

-   Kancelaria prawna chce zapobiec drukowaniu i przekazywaniu dalej poufnych wiadomości e-mail na urządzeniach przenośnych.
-   Deweloperzy oprogramowania CAD i oprogramowania produkcyjnego chcą ograniczyć dostęp do rysunków do niewielkiej grupy użytkowników z działu badawczego bez konieczności korzystania z haseł.
-   Właściciele graficznej aplikacji mobilnej chcą korzystać z pojedynczej licencji, która umożliwia swobodne wyświetlanie kopii obrazów w niskiej rozdzielczości, ale wymaga opłaty w celu uzyskania dostępu do wersji o wysokiej rozdzielczości.
-   Właściciele biblioteki dokumentów online chcą włączyć prawa do wyświetlania, drukowania i edycji dokumentów na podstawie tożsamości użytkownika przy pobieraniu dokumentów na urządzenie przenośne.
-   Firma chce publikować poufne informacje o pracownikach w wewnętrznej witrynie sieci Web, która ogranicza uprawnienia do wyświetlania i edycji do określonych użytkowników.

Zestaw SDK 4.2 usługi MS RMS może być pobierany (po potwierdzeniu i zaakceptowaniu umowy licencyjnej) i dystrybuowany za darmo razem z aplikacjami innych firm, aby umożliwić klientom dostęp do zawartości, do której prawa dostępu są chronione przez użycie i wdrożenie serwerów usługi AD RMS w danym środowisku lub usług Azure RMS. Aby uzyskać więcej informacji, zobacz [Rozpoczynanie pracy](get-started.md).

## Najważniejsze funkcje zestawu SDK


Zestaw SDK 4.2 usługi MS RMS oferuje nowe, atrakcyjne funkcje, w tym:

-   **Zmieniony interfejs API** — interfejs API zestawu SDK 4.2 usługi MS RMS został przeprojektowany pod kątem maksymalnej prostoty, dzięki czemu deweloperzy mogą korzystać z prostego i przejrzystego interfejsu API szyfrowania i odszyfrowywania, który zapewnia spójne działanie usługi RMS przy minimalnym wysiłku.
-   **Hybrydowa obsługa usług AD RMS i Azure RMS** — jedna aplikacja z włączoną obsługą usługi RMS może wykorzystywać i chronić zawartość z serwera usługi AD RMS (przy użyciu rozszerzenia usługi AD RMS dla urządzeń przenośnych) i usługi Azure RMS. Zestaw SDK 4.2 usługi MS RMS w przejrzysty sposób odnajduje odpowiednie punkty końcowe, które mogą być konfigurowane przez administratorów IT.
-   **Korzystanie z własnej biblioteki uwierzytelniania** — deweloper aplikacji może wybrać bibliotekę uwierzytelniania używaną z zestawem SDK 4.2 usługi MS RMS. Niezależnie od tego, czy jest to biblioteka [Azure AD Authentication Library](https://msdn.microsoft.com/library/jj573266.aspx), czy też niestandardowa biblioteka organizacji, zestaw SDK 4.2 usług MS RMS rozdziela stos autoryzacji, co umożliwia wybór biblioteki najlepiej odpowiadającej potrzebom użytkownika.
-   **Korzystanie z własnego interfejsu użytkownika** — zestaw SDK 4.2 usługi MS RMS umożliwia teraz wdrażanie własnego, niestandardowego interfejsu użytkownika. Od ochrony zawartości i wyboru szablonów po wyświetlanie i zmianę uprawnień podczas korzystania z zawartości chronionej, zestaw SDK 4.2 usługi MS RMS nie wymusza korzystania z żadnego wbudowanego interfejsu użytkownika w aplikacjach. Możesz też skorzystać z bibliotek interfejsów użytkownika usługi Microsoft RMS dla wszystkich platform. Biblioteki te są dostępne przez nasze [konto GitHub](https://github.com/AzureAD/).
-   **Dostęp do zawartości chronionej online** — zestaw SDK 4.2 usługi MS RMS umożliwia użytkownikom aplikacji dostęp do zawartości chronionej nawet bez łączności z Internetem. Zestaw SDK 4.2 usługi MS RMS bezpiecznie zapisuje zasady użytkowania zawartości chronionej w pamięci podręcznej, co zapewnia użytkownikom dostęp do danych chronionych usługi RMS w trybie offline.

Skorzystaj z przewodnika [Rozpoczynanie pracy](get-started.md), aby rozpocząć pracę nad projektem aplikacji dla urządzenia z informacjami chronionymi.

## Tematy pokrewne

* [Zestaw SDK usługi Microsoft Rights Management](active-directory-rights-management-services-multi-platform-thin-client-sdk-portal.md)
* [Wprowadzenie](get-started.md)
* [Biblioteka Azure AD Authentication Library](https://msdn.microsoft.com/en-us/library/jj573266.aspx)
* [Konto GitHub](https://github.com/AzureAD/)
 

 






<!--HONumber=Jul16_HO3-->


