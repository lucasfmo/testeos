---
title: "Ograniczenia rozwiązania HYOK | Azure Rights Management"
description: 
author: cabailey
manager: mbaldwin
ms.date: 08/18/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 7667b5b0-c2e9-4fcf-970f-05577ba51126
translationtype: Human Translation
ms.sourcegitcommit: a80866576dc7d6400bcebc2fc1c37bc0367bcdf3
ms.openlocfilehash: 1cbf6bd6c209a8aafd1db61422ce03b628aaec07


---

# Wymagania i ograniczenia dotyczące rozwiązania „hold your own key” (HYOK) dla ochrony za pomocą usług AD RMS

>*Dotyczy: Azure Information Protection (wersja zapoznawcza)*

**[Niniejsze informacje mają charakter wstępny i mogą ulec zmianom. ]**

W przypadku ochrony najbardziej poufnych dokumentów i wiadomości e-mail zazwyczaj będziesz to robić przez zastosowanie ochrony usługi Azure Rights Management, która zapewnia następujące korzyści:

- Nie wymaga infrastruktury serwera, co sprawia, że wdrożenie, i obsługa rozwiązania są szybsze i tańsze niż w przypadku rozwiązania lokalnego.

- Łatwiejsze udostępnianie zawartości partnerom i użytkownikom z innych organizacji przy użyciu uwierzytelniania opartego na chmurze.

- Ścisła integracja z usługami Office 365, takimi jak wyszukiwanie, przeglądarki sieci Web, widoki przestawne, ochrona przed złośliwym oprogramowaniem, zbieranie elektronicznych materiałów dowodowych i aplikacja Delve.

- Śledzenie i odwoływanie dokumentów, powiadomienia e-mail dotyczące udostępnionych poufnych dokumentów.

Usługa Azure RMS chroni dokumenty i wiadomości e-mail organizacji przy użyciu klucza prywatnego dla organizacji, który jest zarządzany przez firmę Microsoft (ustawienie domyślne) lub przez użytkownika (scenariusz „bring your own key”, BYOK). Informacje chronione za pomocą usługi Azure RMS nigdy nie są wysyłane do chmury, a chronione dokumenty i wiadomości e-mail nie są przechowywane na platformie Azure, chyba że jawnie je tam przechowujesz lub korzystasz z innej usługi w chmurze, która przechowuje je na platformie Azure. Aby uzyskać więcej informacji na temat opcji klucza dzierżawy, zobacz [Planowanie i wdrażanie klucza dzierżawy usługi Azure Rights Management](../plan-design/plan-implement-tenant-key.md). 

Niektórzy klienci mogą jednak wymagać ochrony wybranych dokumentów i wiadomości e-mail przy użyciu klucza przechowywanego i obsługiwanego lokalnie. Przykładowo może to być wymagane ze względu na obowiązujące przepisy i zachowanie zgodności. 

Ta konfiguracja jest czasami określana jako „hold your own key” (HYOK) i jest obsługiwana przez usługę Azure Information Protection, gdy masz działające wdrożenie usług Active Directory Rights Management Services (AD RMS) spełniające wymagania opisane w następnej sekcji. 

W tym scenariuszu HYOK zasady praw i klucz prywatny organizacji, który chroni te zasady, są zarządzane i przechowywane lokalnie, podczas gdy zasady usługi Azure Information Protection dotyczące etykietowania i klasyfikacji pozostają zarządzane i przechowywane na platformie Azure. Podobnie jak w przypadku ochrony za pomocą usługi Azure RMS, informacje chronione za pomocą usług AD RMS nigdy nie są wysyłane do chmury.

> [!NOTE]
> Tej konfiguracji należy używać tylko w razie konieczności i tylko dla dokumentów i wiadomości e-mail, które tego wymagają. Ochrona za pomocą usług AD RMS nie zapewnia wymienionych korzyści, które daje ochrona za pomocą usługi Azure RMS, a jej celem jest "nieprzezroczystość danych za wszelką cenę".

Użytkownicy nie będą świadomi, że etykieta używa ochrony za pomocą usług AD RMS zamiast ochrony za pomocą usługi Azure RMS. Ze względu na ograniczenia wiążące się z ochroną w usługach AD RMS, musisz zapewnić jasne wskazówki dotyczące tego, kiedy użytkownicy powinni wybierać etykiety korzystające z ochrony usług AD RMS.

## Wymagania dotyczące rozwiązania HYOK

Sprawdź, czy wdrożenie usług AD RMS spełnia następujące wymagania, aby zapewniać ochronę za pomocą usług AD RMS dla usługi Azure Information Protection.

- Konfiguracja usług AD RMS:
    
    - Minimalna wersja systemu Windows Server 2012 R2: wymagana dla środowisk produkcyjnych; w celach związanych z testowaniem lub oceną można użyć minimalnej wersji systemu Windows Server 2008 R2 z dodatkiem Service Pack 1.
    
    - Jeden klaster główny usług AD RMS.
    
    - [Tryb kryptograficzny 2](https://technet.microsoft.com/library/hh867439.aspx): możesz sprawdzić wersję trybu kryptograficznego klastra AD RMS oraz jego ogólną kondycję przy użyciu [narzędzia RMS Analyzer](https://www.microsoft.com/en-us/download/details.aspx?id=46437).   
    
    - Serwery AD RMS są skonfigurowane do użycia protokołów SSL/TLS z ważnym certyfikatem x.509, który jest zaufany przez klientów nawiązujących połączenie: wymagane dla środowisk produkcyjnych, ale niewymagane w celach związanych z testowaniem lub oceną.
    
    - Skonfigurowane szablony praw.

- Skonfigurowano synchronizację katalogów między lokalną usługą Active Directory i usługą Azure Active Directory, a użytkownicy, którzy będą korzystać z ochrony usług AD RMS, są skonfigurowani w celu logowania jednokrotnego.

- Jeśli będziesz udostępniać dokumenty lub wiadomości e-mail chronione za pomocą usług AD RMS użytkownikom spoza organizacji: usługi AD RMS są skonfigurowane dla jawnie zdefiniowanych relacji zaufania w bezpośredniej relacji point-to-point z innymi organizacjami przy użyciu zaufanych domen użytkowników (TUD) lub federacyjnych relacji zaufania, które są tworzone za pomocą usługi Active Directory Federation Services (AD FS).

- Użytkownicy mają pakiet Office 2013 Pro Plus z dodatkiem Service Pack 1 lub Office 2016 Pro Plus, uruchomiony w systemie Windows 7 z dodatkiem SP1 lub nowszym. Należy zauważyć, że pakiety Office 2010 i Office 2007 nie są obsługiwane w przypadku tego scenariusza.

- [Klient usługi Azure Information Protection](info-protect-client.md) jest w wersji **1.0.233.0** lub nowszej.

> [!IMPORTANT]
> W celu zrealizowania wysokiego bezpieczeństwa, które oferuje ten scenariusz, zaleca się, aby serwery usług AD RMS znajdowały się poza Twoją strefą DMZ i były używane wyłącznie przez dobrze zarządzane komputery (a nie, na przykład, przez urządzenia mobilne lub komputery grupy roboczej). 
> 
> Ponadto zaleca się, aby klaster AD RMS używał sprzętowego modułu zabezpieczeń (HSM, Hardware Security Module), dzięki czemu klucz prywatny certyfikatu licencjodawcy serwera (SLC, Server Licensor Certificate) nie może być ujawniony lub skradziony, jeśli wdrożenie usług AD RMS zostanie kiedykolwiek naruszone lub gdy jego zabezpieczenia zostaną złamane. 

Aby uzyskać informacje na temat wdrażania oraz instrukcje dotyczące usług AD RMS, zobacz [Usługi Active Directory Rights Management Services](https://technet.microsoft.com/library/hh831364.aspx) w bibliotece systemu Windows Server. 


## Lokalizowanie informacji używanych do określania ochrony usług AD RMS za pomocą etykiety usługi Azure Information Protection

Po skonfigurowaniu etykiety dla ochrony za pomocą usług AD RMS należy określić identyfikator GUID szablonu i adres URL licencjonowania klastra usług AD RMS. Obie te wartości można znaleźć za pomocą konsoli usług Active Directory Rights Management Services:

- Aby zlokalizować identyfikator GUID szablonu: rozwiń klaster i kliknij pozycję **Szablony zasad praw**. Z informacji o **dystrybuowanych szablonach zasad praw**, możesz następnie skopiować identyfikator GUID szablonu, którego chcesz użyć. Na przykład: 82bf3474-6efe-4fa1-8827-d1bd93339119

- Aby znaleźć adres URL licencjonowania: kliknij nazwę klastra. Z informacji o **szczegółach klastra** skopiuj wartość **licencjonowania** minus ciąg **/_wmcs/licensing**. Na przykład: https://rmscluster.contoso.com 
    
    Jeżeli masz zarówno wartość licencjonowania ekstranetu, jak i wartość licencjonowania sieci intranet i są one różne: podaj tylko wartość ekstranetu, jeśli będziesz udostępniać chronione dokumenty lub wiadomości e-mail partnerom zdefiniowanym za pomocą jawnej relacji zaufania point-to-point. W przeciwnym razie użyj wartości intranetowej i upewnij się, że wszystkie komputery klienckie korzystające z ochrony za pomocą usług AD RMS nawiązują połączenie przy użyciu połączenia intranetowego(na przykład komputery zdalne używają połączenia sieci VPN).

## Następne kroki

Aby uzyskać więcej informacji na temat tej funkcji w wersji zapoznawczej, zobacz anons we wpisie w blogu [Usługa Azure Information Protection z rozwiązaniem HYOK (Hold Your Own Key)](https://blogs.technet.microsoft.com/enterprisemobility/2016/08/10/azure-information-protection-with-hyok-hold-your-own-key/).

Aby skonfigurować etykietę w celu zastosowania ochrony usług AD RMS, zobacz [Konfigurowanie etykiety w celu zastosowania ochrony usługi Rights Management](configure-policy-protection.md). 



<!--HONumber=Aug16_HO3-->


