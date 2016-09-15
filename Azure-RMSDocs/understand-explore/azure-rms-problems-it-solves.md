---
title: "Jaki problem rozwiązuje usługa Azure RMS | Azure RMS"
description: 
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 07/13/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: b551c62d-5ac6-4359-85b3-90693e77b37f
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 06f615c993d54ab1e8e4a94d7414302481d919b4
ms.openlocfilehash: 17756d4e641c10c0522f7a849634ae67630b363b


---


# Jaki problem rozwiązuje usługa Azure RMS?

*Dotyczy usług: Azure Rights Management, Office 365*

Użyj poniższej tabeli, aby zidentyfikować wymagania biznesowe lub problemy, które może mieć organizacja, a także poznać sposoby ich rozwiązywania przy użyciu usługi Azure RMS.

|Wymaganie lub problem|Rozwiązanie przy użyciu usługi Azure RMS|
|--------------------------|-----------------------|
|Ochrona wszystkich typów plików|√ W poprzedniej implementacji usługi Rights Management tylko pliki pakietu Office mogły być chronione za pomocą ochrony natywnej. Teraz [ochrona natywna](../rms-client/sharing-app-dialog-box.md#what-s-the-difference-between-generic-protection-and-built-in-native-protection) oznacza, że obsługiwane są pliki wszystkie typów.|
|Ochrona plików w każdym miejscu|√ Gdy plik jest zapisywany w lokalizacji ([ochrony miejscowej](../rms-client/sharing-app-protect-in-place.md)), ochrona pozostaje skojarzona z plikiem, nawet jeśli zostanie on skopiowany do magazynu poza kontrolą działu IT, takiego jak usługa magazynu w chmurze.|
|Bezpieczne udostępnianie plików za pośrednictwem poczty e-mail|√ Gdy plik jest udostępniany za pośrednictwem poczty e-mail ([udostępnianie chronionej zawartości](../rms-client/sharing-app-protect-by-email.md)), plik jest chroniony jako załącznik do wiadomości e-mail z instrukcją otwierania chronionego załącznika. Tekst wiadomości e-mail nie jest szyfrowany, więc adresat zawsze może przeczytać instrukcję. Jednak ponieważ dołączony dokument jest chroniony, tylko autoryzowani użytkownicy będą mogli go otworzyć, nawet jeśli wiadomość e-mail lub dokument zostaną przesłane dalej do innych osób.|
|Inspekcja i monitorowanie|√ Możesz [przeprowadzać inspekcję i monitorowanie użycia](../deploy-use/log-analyze-usage.md) plików chronionych, nawet po opuszczeniu przez nie granic organizacji.<br /><br />Załóżmy, że pracujesz dla firmy Contoso, Ltd. Pracujesz nad wspólnym projektem z 3 osobami z firmy Fabrikam, Inc. Wysyłasz do tych 3 osób dokument, który chronisz i ograniczasz, aby był tylko do odczytu. Inspekcja Azure RMS może podać następujące informacje:<br /><br />— czy i kiedy wybrane osoby z firmy Fabrikam otworzyły dokument;<br /><br />— czy inne osoby, których nie podano, próbowały (bez powodzenia) otworzyć dokument — prawdopodobnie ponieważ został przekazany albo zapisany w lokalizacji udostępnionej innym osobom;<br /><br />— czy dowolna osoba z wybranych próbowała (bez powodzenia) drukować lub zmieniać dokument.|
|Obsługa wszystkich najczęściej używanych urządzeń, a nie tylko komputerów z systemem Windows|√ [Obsługiwane urządzenia](../get-started/requirements-client-devices.md) obejmują:<br /><br />— komputery i telefony z systemem Windows<br /><br />— komputery Mac<br /><br />— tablety i telefony z systemem iOS<br /><br />— tablety i telefony z systemem Android|
|Obsługa współpracy między firmami (B2B)|√ Ponieważ Azure RMS to usługa w chmurze, nie istnieje potrzeba jawnego konfigurowania relacji zaufania z innymi organizacjami przed udostępnieniem im chronionej zawartości. Jeżeli korzystają już one z usługi Office 365 lub katalogu usługi Azure AD, współpraca między organizacjami jest obsługiwana automatycznie. W przeciwnym razie użytkownicy mogą rejestrować się w ramach darmowej subskrypcji [usługi RMS dla osób indywidualnych](rms-for-individuals.md).|
|Obsługa usług lokalnych, jak również usługi Office 365|√ Oprócz [bezproblemowej pracy z usługą Office 365](office-apps-services-support.md) po wdrożeniu [łącznika usługi RMS](../deploy-use/deploy-rms-connector.md) możesz także używać usługi Azure RMS z następującymi usługami lokalnymi:<br /><br />— Exchange Server<br /><br />— SharePoint Server<br /><br />— System Windows Server z uruchomioną infrastrukturą klasyfikacji plików|
|Łatwa aktywacja|√ [Aktywowanie usługi Rights Management](../deploy-use/activate-service.md) dla użytkowników wymaga zaledwie kilku kliknięć w klasycznym portalu Azure.|
|Dostosowana do potrzeb możliwość skalowania w organizacji|√ Ponieważ Azure RMS działa jako usługa w chmurze, której elastyczność skalowania w górę i w dół zapewnia platforma Azure, nie trzeba zapewniać ani wdrażać dodatkowych serwerów lokalnych.|
|Możliwość tworzenia prostych i elastycznych zasad|√ [Dostosowane szablony zasad praw](../deploy-use/configure-custom-templates.md) stanowią rozwiązanie szybkie i łatwe, dzięki któremu administratorzy mogą stosować zasady, a użytkownicy mogą stosować odpowiedni poziom ochrony do każdego dokumentu, a także ograniczać dostęp do osób wewnątrz organizacji.<br /><br />Na przykład dokument strategii dla całej firmy może być udostępniony wszystkim pracownikom z zastosowaniem zasady tylko do odczytu dla wszystkich pracowników wewnętrznych. Natomiast dostęp do bardziej poufnego dokumentu, takiego jak raport finansowy, może zostać ograniczony tylko do dyrektorów.|
|Szerokie wsparcie aplikacji|√ Usługa Azure RMS ściśle integruje się z aplikacjami i usługami Microsoft Office, a także oferuje rozszerzone wsparcie dla innych aplikacji za pomocą aplikacji RMS sharing.<br /><br />√ Zestaw [Microsoft Rights Management SDK](../develop/developers-guide.md#software-development-kits) dostarcza wewnętrznym deweloperom i dostawcom oprogramowania interfejsy API do programowania niestandardowych aplikacji do udostępniania usługi RMS.<br /><br />Aby uzyskać więcej informacji, zobacz [Inne aplikacje, które obsługują interfejsy API usług RMS](api-support.md).|
|Dział IT musi zachować kontrolę nad danymi|√ Organizacje mogą wybrać zarządzanie własnym kluczem dzierżawcy z zastosowaniem rozwiązania „[Bring Your Own Key](../plan-design/plan-implement-tenant-key.md)” (BYOK) i przechowywać klucz dzierżawcy w sprzętowych modułach zabezpieczeń (HSM).<br /><br />√ Obsługa inspekcji i [rejestrowanie użycia](../deploy-use/log-analyze-usage.md) pozwala analizować szczegółowe informacje biznesowe, monitorować nadużycia oraz (w przypadku przecieku informacji) dokonywać analizy śledczej.<br /><br />√ Delegowanie dostępu za pomocą [funkcji administratorów](../deploy-use/configure-super-users.md) pozwala zagwarantować, że dział IT zawsze ma dostęp do zawartości chronionej, nawet jeśli dokument był chroniony przez pracownika, który opuścił organizację. W odróżnieniu od tego podejścia rozwiązania szyfrowania równorzędnego niosą ryzyko utraty dostępu do danych firmowych.<br /><br />√ Synchronizacja [wyłącznie atrybutów katalogu wymaganych przez usługę Azure RMS](/active-directory/active-directory-aadconnectsync-attributes-synchronized#azure-rms) do obsługi tożsamości wspólnych dla lokalnych kont usługi Active Directory przy użyciu [narzędzia synchronizacji katalogów](/active-directory/active-directory-hybrid-identity-design-considerations-tools-comparison), np. Azure AD Connect.<br /><br />√ Włączanie logowania jednokrotnego bez replikacji haseł w chmurze za pomocą usług AD FS.<br /><br />√ Organizacje mogą w dowolnie wybranym momencie przestać korzystać z usługi Azure RMS bez utraty dostępu do zawartości, która była wcześniej chroniona przez usługę Azure RMS. Aby uzyskać więcej informacji na temat opcji likwidowania, zobacz artykuł [Likwidowanie i dezaktywowanie usługi Azure Rights Management](../deploy-use/decommission-deactivate.md) Ponadto organizacje, które wdrożyły usługę Active Directory Rights Management Services (AD RMS), mogą [migrować do usługi Azure RMS](../plan-design/migrate-from-ad-rms-to-azure-rms.md) bez utraty dostępu do danych, które wcześniej były chronione przez usługę AD RMS.|
> [!TIP]
> Jeśli znasz lokalną wersję usługi Rights Management, Active Directory Rights Management Services (AD RMS), może Cię zainteresować tabela porównawcza z artykułu [Porównanie usług Azure Rights Management i AD RMS](compare-azure-rms-ad-rms.md).

## Wymagania dotyczące zabezpieczeń, zgodności i przepisów prawnych
Azure RMS obsługuje następujące wymagania dotyczące zabezpieczeń, zgodności i przepisów prawnych:

√ Wykorzystanie branżowego standardu kryptografii i obsługa standardu FIPS 140-2. Aby uzyskać więcej informacji, zobacz temat [formanty kryptograficzne używane przez usługę Azure RMS: algorytmy i długości kluczy](how-does-it-work.md#cryptographic-controls-used-by-azure-rms-algorithms-and-key-lengths).

√ Obsługa sprzętowych modułów zabezpieczeń (HSM) firmy Thales do przechowywania klucza dzierżawcy w centrach danych Microsoft Azure. W usłudze Azure RMS są wykorzystywane oddzielne środowiska Security World dla centrów danych w Ameryce Północnej, regionie Europy, Bliskiego Wschodu i Afryki (EMEA) oraz Azji, dzięki czemu klucze mogą być używane tylko w danym regionie.

√ Przyznane certyfikaty:

-   ISO/IEC 27001:2013 (obejmuje [ISO/IEC 27018](http://azure.microsoft.com/blog/2015/02/16/azure-first-cloud-computing-platform-to-conform-to-isoiec-27018-only-international-set-of-privacy-controls-in-the-cloud/))

-   Poświadczenia SOC 2 SSAE 16/ISAE 3402

-   HIPAA BAA

-   Klauzula modelu UE

-   Prawo do działania FedRAMP obejmujące usługę Azure Active Directory w ramach certyfikacji usługi Office 365 wystawione przez urząd HHS

-   PCI DSS poziom 1

Aby uzyskać więcej informacji o tych certyfikatach zewnętrznych, zobacz [Centrum zaufania platformy Azure](http://azure.microsoft.com/support/trust-center/compliance/).

## Następne kroki

Aby poznać usługi Azure RMS dla administratorów i użytkowników, zobacz [Usługi Azure RMS w akcji](what-admins-users-see.md).

Aby uzyskać informacje techniczne na temat działania usługi Azure RMS, zobacz artykuł [Jak działa usługa Azure RMS?](how-does-it-work.md) 


<!--HONumber=Jul16_HO3-->


