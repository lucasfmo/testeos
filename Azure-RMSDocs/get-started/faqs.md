---
title: "Często zadawane pytania dotyczące usługi Azure Rights Management | Azure RMS"
description: 
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 07/13/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 71ce491f-41c1-4d15-9646-455a6eaa157d
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: e89c59716eef7fbdea415b41b1adfa54b0c16689
ms.openlocfilehash: bd53b73452f444ac8529a8b8b613e76d8cc234a1


---

# Często zadawane pytania dotyczące usługi Azure Rights Management

*Dotyczy usług: Azure Rights Management, Office 365*

Niektóre często zadawane pytania dotyczące usługi Microsoft [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)], znanej również jako Azure RMS:

## Co jest potrzebne do wdrożenia usługi Azure RMS i jak zacząć?
Najpierw należy sprawdzić [wymagania dotyczące usługi Azure Rights Management](requirements-azure-rms.md), które zawierają informacje o opcjach subskrypcji chmury, korzystaniu z serwerów lokalnych z usługą Azure RMS, aktualnie obsługiwanych scenariuszach wdrażania, urządzeniach i aplikacjach obsługujących usługę Azure RMS, a także link na wypadek potrzeby skorzystania z listy adresów IP i nazw domen dla zapór lub serwerów proxy. 

Można także zapoznać się z innymi artykułami w sekcji **Wprowadzenie**, a także w sekcji **Poznawanie i eksplorowanie**. Pozwoli to uzyskać podstawowe informacje o możliwościach usługi [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] w zakresie ochrony danych organizacji, współpracy z aplikacjami oraz porównaniu z wersjami lokalnymi usługi Active Directory Rights Management. Umożliwi także zapoznanie się z terminologią i skrótami właściwymi dla usługi [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)].

Następnie, aby rozpocząć pracę, użyj [mapy wdrożenia usługi Azure Rights Management](../plan-design/deployment-roadmap.md).

## Czy pliki muszą znajdować się w chmurze, aby mogły być chronione przez usługę Azure RMS?
Nie, to powszechne nieporozumienie. Usługa Azure Rights Management (ani firma Microsoft) nie widzi ani nie przechowuje danych użytkownika w ramach procesu ochrony informacji. Chronione informacje nie są wysyłane na platformę Azure ani na niej przechowywane, chyba że użytkownik jawnie zapisze je na platformie Azure lub w innej usłudze chmurowej, która magazynuje dane na tej platformie. 

Aby uzyskać więcej informacji, zobacz temat [How does Azure RMS work? Under the hood](../understand-explore/how-does-it-work.md) (Jak działa usługa RMS? Kulisy), aby dowiedzieć się, jak tajna receptura coli, utworzona i przechowywana lokalnie, jest chroniona przez usługę Azure RMS, ale pozostaje zapisana lokalnie.

## Czy można zintegrować usługę Azure RMS z serwerami lokalnymi?
Tak. Usługę Azure RMS można zintegrować z serwerami lokalnymi, takimi jak Exchange Server, SharePoint i serwery plików systemu Windows. W tym celu należy użyć [łącznika usługi Rights Management](../deploy-use/deploy-rms-connector.md). Osoby zainteresowane używaniem infrastruktury klasyfikacji plików (FCI, File Classification Infrastructure) z systemem Windows Server mogą skorzystać z [poleceń cmdlet narzędzia RMS Protection](https://technet.microsoft.com/library/mt601315%28v=ws.10%29.aspx). Można także przeprowadzić synchronizację i federację kontrolerów domeny usługi Active Directory z usługą Azure AD, aby usprawnić środowisko uwierzytelniania dla użytkowników, na przykład za pomocą programu [Azure AD Connect](http://azure.microsoft.com/documentation/articles/active-directory-aadconnect/).

Usługa Azure RMS automatycznie generuje certyfikaty XrML i zarządza nimi zgodnie z wymaganiami, dlatego nie korzysta z lokalnej infrastruktury kluczy publicznych. Aby uzyskać więcej informacji o używaniu certyfikatów przez usługę Azure RMS, zobacz sekcję [Wskazówki dotyczące działania usługi Azure RMS: pierwsze użycie, ochrona zawartości, zużycie zawartości](../understand-explore/how-does-it-work.md#walkthrough-of-how-azure-rms-works-first-use-content-protection-content-consumption) w artykule [Jak działa usługa Azure RMS?](../understand-explore/how-does-it-work.md).

## Gdzie można znaleźć informacje o rozwiązaniach innych firm, które integrują się z usługą Azure RMS?

Wielu dostawców oprogramowania ma już rozwiązania, które integrują się z usługą Azure RMS, lub jest w trakcie ich implementowania. Liczba takich rozwiązań rośnie bardzo szybko. Dla użytkowników może być bardzo przydatne zapoznanie się z [blogiem dotyczącym pakietu Enterprise Mobility i zabezpieczeń](https://blogs.technet.microsoft.com/enterprisemobility/?product=azure-rights-management-services) i śledzenie najnowszych aktualizacji kanału [@TheRMSGuy Dana Plastina](https://twitter.com/TheRMSGuy) w serwisie Twitter. Jeśli jednak masz konkretne pytanie, wyślij wiadomość e-mail do zespołu ochrony informacji na adres askipteam@microsoft.com.

## Czy istnieje pakiet zarządzania lub podobny mechanizm monitorowania dla łącznika usługi RMS?

Mimo że łącznik usługi Rights Management rejestruje informacje, ostrzeżenia i komunikaty o błędach w dzienniku zdarzeń, nie istnieje pakiet administracyjny, który obejmuje monitorowanie tych zdarzeń. Jednak lista zdarzeń i ich opisów wraz dodatkowymi informacjami ułatwiającymi podejmowanie działań naprawczych jest opisana w sekcji [Monitorowanie łącznika usługi Azure Rights Management](../deploy-use/monitor-rms-connector.md).

## Czy trzeba być administratorem globalnym, aby skonfigurować usługę Azure RMS, czy można to oddelegować do innych administratorów?

Administratorzy globalni dla dzierżawy usługi Office 365 lub dzierżawy usługi Azure AD mogą oczywiście uruchamiać wszystkie zadania administracyjne dla usługi Azure RMS. Jednak jeśli chcesz przypisać uprawnienia administracyjne do innych użytkowników, możesz to zrobić przy użyciu polecenia cmdlet programu PowerShell usługi Azure RMS [Add-AadrmRoleBasedAdministrator](https://msdn.microsoft.com/library/dn629417.aspx). Tę rolę administracyjną można przypisać według konta użytkownika lub grupy. Dostępne są dwie role: **Administrator globalny** i **Administrator łącznika**. 

Tak jak te nazwy sugerują, pierwsza rola przyznaje uprawnienia do uruchamiania wszystkich zadań administracyjnych dla usługi Azure Rights Management (bez nadawania użytkownikom roli administratora globalnego dla innych usług w chmurze), a druga rola przyznaje uprawnienia do uruchamiania tylko łącznika usługi Rights Management (RMS).

Dodatkowe kwestie, na które należy zwrócić uwagę:

- Tylko administratorzy globalni usługi Office 365 i administratorzy globalni usługi Azure AD mogą używać portali zarządzania (centrum administracyjne usługi Office 365 lub klasyczny portal Azure) do konfigurowania usługi Azure RMS. Użytkownicy, którym przypisywana jest rola administratora globalnego usługi Azure RMS, muszą używać poleceń cmdlet programu PowerShell usługi Azure RMS do konfigurowania usługi Azure RMS. W celu łatwiejszego znalezienia odpowiednich poleceń cmdlet służących do wykonywania określonych zadań, zobacz [Administrowanie usługą Azure Rights Management przy użyciu programu Windows PowerShell](../deploy-use/administer-powershell.md).

- Jeśli skonfigurowano [kontrolki dołączania](../deploy-use/activate-service.md#configuring-onboarding-controls-for-a-phased-deployment), nie ma to wpływu na możliwość administrowania usługą Azure RMS, z wyjątkiem łącznika usługi RMS. Na przykład jeśli kontrolki dołączania zostały skonfigurowane w taki sposób, że możliwość ochrony zawartości jest ograniczona do grupy Dział IT, konto używane do instalowania i konfigurowania łącznika usługi RMS musi należeć do tej grupy. 

- Żaden administrator usługi Azure RMS (administrator globalny dzierżawy lub administrator globalny usługi Azure RMS) nie może automatycznie usunąć ochrony dokumentów lub wiadomości e-mail, które były chronione przez usługę Azure RMS. Tylko użytkownicy przypisani do funkcji administratorów usługi Azure RMS mogą to zrobić i może to mieć miejsce tylko po włączeniu funkcji administratorów. Jednak administrator globalny dzierżawy i dowolny administrator globalny usługi Azure RMS może przypisywać użytkowników jako administratorów (dotyczy to również ich własnego konta). Mogą oni również włączyć funkcję administratorów. Te akcje są rejestrowane w dzienniku administratora usługi Azure RMS. Aby uzyskać więcej informacji, zobacz sekcję najlepszych praktyk dotyczących zabezpieczeń w temacie [Konfigurowanie superużytkowników usług Azure Rights Management i usług odnajdywania lub odzyskiwania danych](../deploy-use/configure-super-users.md). 


## Mam hybrydowe wdrożenie programu Exchange — niektórzy użytkownicy korzystają z usługi Exchange Online, inni z programu Exchange Server. Czy usługa Azure RMS obsługuje taką sytuację?
Oczywiście, a dodatkową korzyścią jest to, że użytkownicy będą mogli w łatwy sposób chronić wiadomości e-mail i załączniki, a także korzystać z nich w obu wdrożeniach programu Exchange. W przypadku takiej konfiguracji należy najpierw [aktywować usługę Azure RMS](../deploy-use/activate-service.md) i [włączyć usługę IRM dla usługi Exchange Online](https://technet.microsoft.com/library/dn151475%28v=exchg.150%29.aspx), a następnie [wdrożyć i skonfigurować łącznik usługi RMS](../deploy-use/deploy-rms-connector.md) dla programu Exchange Server.

## Czy istnieją szczegółowe instrukcje konfigurowania usługi Exchange Online do używania usługi Azure RMS?

Tak. Zobacz [Usługa Exchange Online: konfiguracja usługi IRM](../deploy-use/configure-office365.md#exchange-online-irm-configuration), aby zapoznać się z typowym zestawem poleceń umożliwiających usłudze Exchange Online korzystanie z usługi Azure RMS, dowiedzieć się, dlaczego aplikacja Outlook Web App nie wyświetla natychmiast opcji menu **Ustawianie uprawnień**, oraz poznać polecenie, które należy wykonać w przypadku zmiany lub aktualizacji szablonów usługi Azure RMS. 

## Czy wdrożenie usługi Azure RMS w środowisku produkcyjnym zmusza przedsiębiorstwo do korzystania z tego rozwiązania lub powoduje ryzyko utraty dostępu do zawartości chronionej za pomocą usługi Azure RMS?
Nie, użytkownik zawsze zachowuje kontrolę nad swoimi danymi i może z nich korzystać, nawet jeśli zrezygnuje z używania usługi Azure RMS. Aby uzyskać więcej informacji, zobacz artykuł [Likwidowanie i dezaktywowanie usługi Azure Rights Management](../deploy-use/decommission-deactivate.md).

Jednak zanim zlikwidujesz wdrożenie usługi Azure RMS, chcielibyśmy poznać powód podjęcia takiej decyzji. Jeśli usługa Azure RMS nie spełnia wymagań przedsiębiorstwa, należy skontaktować się z nami i sprawdzić, czy w najbliższej przyszłości planowane jest wprowadzenie nowych funkcji lub czy są dostępne opcje alternatywne. Wyślij wiadomość e-mail na adres [AskIPTeam@Microsoft.com](mailto:askipteam@microsoft.com?subject=Planning%20to%20decommission%20Azure%20RMS), a chętnie omówimy Twoje wymagania techniczne i biznesowe.

## Czy można kontrolować, którzy użytkownicy w przedsiębiorstwie mogą korzystać z usługi Azure RMS do ochrony zawartości?
Tak, usługa Azure RMS jest wyposażona w funkcje kontroli dołączania użytkowników na potrzeby takiego scenariusza. Aby uzyskać więcej informacji, zobacz sekcję dotyczącą [konfigurowania funkcji kontroli dołączania użytkowników we wdrożeniu etapowym](../deploy-use/activate-service.md#configuring-onboarding-controls-for-a-phased-deployment) w artykule [Activating Azure Rights Management](../deploy-use/activate-service.md) (Aktywowanie usługi Azure Rights Management).

## Czy można uniemożliwić udostępnianie przez użytkowników dokumentów chronionych określonym organizacjom?
Jedną z największych zalet usługi Azure RMS jest obsługiwanie współpracy między firmami bez konieczności jawnego konfigurowania zaufania dla każdej organizacji partnerskiej, ponieważ usługa Azure AD sama obsługuje uwierzytelnianie.

Nie ma administracyjnej możliwości uniemożliwiania bezpiecznego udostępniania dokumentów przez użytkowników określonym organizacjom. Na przykład chcesz zablokować organizację, której nie ufasz lub która prowadzi konkurencyjną działalność. Uniemożliwienie usłudze Azure RMS wysyłania chronionych dokumentów do użytkowników w takich organizacjach nie miałoby sensu, ponieważ użytkownicy mogliby wówczas udostępniać dokumenty bez ochrony, co byłoby zdecydowanie niepożądane. W takiej sytuacji wskazanie osoby udostępniającej poufne dokumenty firmy i ich odbiorców w takich organizacjach byłoby niemożliwe. Można to zrobić, jeśli dokument (lub wiadomość e-mail) podlega ochronie za pomocą usługi Azure RMS.

## W jaki sposób może zostać uwierzytelniony użytkownik spoza mojej firmy, któremu udostępniam chroniony dokument?
Do uwierzytelnienia użytkownika usługa Azure RMS zawsze używa konta usługi Azure Active Directory i powiązanego adresu e-mail, dlatego współpraca między firmami przebiega bez sprawiania problemów administratorom. Jeśli inna organizacja używa usług Azure, użytkownicy mają już konta w usłudze Azure Active Directory, nawet jeśli te konta są tworzone i zarządzane lokalnie, a następnie synchronizowane z platformą Azure. Jeśli organizacja korzysta z usługi Office 365, to ta usługa również używa usługi Azure Active Directory do obsługi kont użytkowników. Jeśli organizacja użytkownika nie posiada kont zarządzanych na platformie Azure, użytkownicy mogą rejestrować się w celu uzyskania [usług RMS dla osób indywidualnych](../understand-explore/rms-for-individuals.md), co powoduje utworzenie niezarządzanej dzierżawy platformy Azure i katalogu dla organizacji z kontem użytkownika, tak aby ten użytkownik (i kolejni) mógł zostać uwierzytelniony do korzystania z usługi Azure RMS.

Metody uwierzytelniania w przypadku tych kont mogą się różnić w zależności od tego, jak administrator drugiej organizacji skonfigurował konta w usłudze Azure Active Directory. Można na przykład korzystać z haseł utworzonych dla tych kont, uwierzytelniania wieloskładnikowego (MFA), federacji lub haseł utworzonych w usługach domenowych Active Directory i następnie zsynchronizowanych z usługą Azure Active Directory.

## Czy mogę dodać użytkowników spoza firmy do szablonów niestandardowych?
Tak. Tworzenie szablonów niestandardowych, które użytkownicy końcowi (i administratorzy) mogą wybierać z poziomu aplikacji, ułatwia i przyspiesza stosowanie ochrony informacji za pomocą określonych wstępnie zdefiniowanych zasad. Jedno z ustawień w szablonie dotyczy użytkownika, który może uzyskiwać dostęp do zawartości. Można wskazać użytkowników i grupy w obrębie własnej organizacji i użytkowników spoza niej.

Aby określić użytkowników spoza organizacji, dodaj ich jako kontakty do grupy wybranej w klasycznym portalu Azure podczas konfigurowania szablonów. Możesz też użyć [modułu programu Windows PowerShell dla usługi Azure Rights Management](../deploy-use/install-powershell.md):

-   **Użyj obiektu definicji praw, aby utworzyć lub zaktualizować szablon**.    Określ zewnętrzne adresy e-mail i ich prawa w obiekcie definicji praw, który następnie zostanie użyty do utworzenia lub zaktualizowania szablonu. Aby określić obiekt definicji praw, utwórz zmienną za pomocą polecenia cmdlet [New-AadrmRightsDefinition](https://msdn.microsoft.com/library/azure/dn727080.aspx). Następnie wykonaj polecenie cmdlet [Add-AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727075.aspx) (w przypadku nowego szablonu) lub polecenie cmdlet [Set-AadrmTemplateProperty](https://msdn.microsoft.com/library/azure/dn727076.aspx) (w przypadku modyfikacji istniejącego szablonu), aby dostarczyć tę zmienną do parametru -RightsDefinition. Jeśli jednak użytkownicy są dodawani do istniejącego szablonu, należy zdefiniować obiekty definicji praw dla istniejących grup w szablonach, a nie tylko dla użytkowników zewnętrznych.

Więcej informacji na temat szablonów niestandardowych można znaleźć w temacie [Konfigurowanie szablonów niestandardowych usługi Azure Rights Management](../deploy-use/configure-custom-templates.md).

## Czy usługa Azure RMS współpracuje z grupami dynamicznymi w usłudze Azure AD?
Funkcja Azure AD Premium pozwala skonfigurować członkostwo dynamiczne w grupach, określając [reguły oparte na atrybucie](https://azure.microsoft.com/documentation/articles/active-directory-accessmanagement-groups-with-advanced-rules/). Typ grupy zabezpieczeń utworzonej w usłudze Azure AD obsługuje członkostwo dynamiczne, ale nie obsługuje adresu e-mail i dlatego nie może być używany z usługami Azure RMS. Teraz można jednak utworzyć w usłudze Azure AD nowy typ grupy, który obsługuje członkostwo dynamiczne, a jednocześnie ma włączoną obsługę poczty. Podczas dodawania nowej grupy w klasycznym portalu Azure można wybrać **TYP GRUPY** **usługi Office 365 Preview**. Ponieważ jest to grupa z włączoną obsługą poczty e-mail, można używać jej wraz z usługą Azure RMS.

Jak jasno wskazuje nazwa opcji, nowy typ grupy jest dostępny w wersji zapoznawczej. Oczekuje się, że zostaną udostępnione dodatkowe funkcje oraz nowa dokumentacja w tym zakresie. Obecnie możemy potwierdzić, że ten nowy typ grupy może być używany z usługą Azure RMS.


## Jakie urządzenia i typy plików są obsługiwane przez usługę Azure RMS?
Aby uzyskać listę obsługiwanych urządzeń, zobacz [Wymagania dotyczące usługi Azure RMS: urządzenia klienckie, które obsługują usługę Azure RMS](../get-started/requirements-client-devices.md). Ponieważ nie wszystkie obsługiwane urządzenia obecnie obsługują wszystkie funkcje usług RMS, należy również zapoznać się z tabelą w sekcji [Wymagania dotyczące usługi Azure RMS: aplikacje](../get-started/requirements-applications.md).

Usługa Azure RMS obsługuje wszystkie typy plików. W przypadku plików tekstowych, obrazów, plików pakietu Microsoft Office (Word, Excel, PowerPoint), plików pdf oraz niektórych typów plików innych aplikacji usługa Azure RMS zapewnia natywną ochronę obejmującą zarówno szyfrowanie, jak i wymuszanie praw (uprawnień). W przypadku pozostałych aplikacji i typów plików ochrona ogólna zapewnia hermetyzację plików oraz uwierzytelnianie umożliwiające weryfikację, czy użytkownik jest uprawniony do otwarcia pliku.

Lista rozszerzeń typów plików obsługiwanych przez usługę Azure RMS znajduje się w sekcji dotyczącej [obsługiwanych typów plików i rozszerzeń nazw plików](../rms-client/sharing-app-admin-guide-technical.md#supported-file-types-and-file-name-extensions) w [Przewodniku administratora aplikacji do udostępniania usługi Rights Management](../rms-client/sharing-app-admin-guide.md). Rozszerzenia nazw plików, które nie są wymienione na liście, są obsługiwane za pomocą aplikacji do udostępniania usługi RMS, która automatycznie stosuje ochronę ogólną do tych plików.

## Czy po otwarciu dokumentu pakietu Office chronionego przez usługę RMS skojarzony plik tymczasowy jest również chroniony przez usługę RMS?

Nie. W tym scenariuszu skojarzony plik tymczasowy nie zawiera danych z oryginalnego dokumentu, tylko dane wprowadzone przez użytkownika w czasie, w którym ten oryginalny plik był otwarty. W przeciwieństwie do oryginalnego pliku plik tymczasowy oczywiście nie jest przeznaczony do udostępniania i pozostanie na urządzeniu, chroniony przez lokalne zabezpieczenia, takie jak funkcja BitLocker i system szyfrowania plików.

## Kiedy będzie obsługiwana migracja z usługi AD RMS?
Początkowo usługa Azure RMS nie obsługiwała migracji z lokalnego wdrożenia usługi Rights Management, takiego jak usługa AD RMS. Jednak obecnie jest ona obsługiwana.

Aby uzyskać więcej informacji, zobacz [Migrowanie z usługi AD RMS do usługi Azure Rights Management](../plan-design/migrate-from-ad-rms-to-azure-rms.md).

## Chcemy używać funkcji BYOK z usługą Azure RMS, ale dowiedzieliśmy się, że nie jest zgodna z usługą Exchange Online. Jaki jest zalecany sposób postępowania?
To aktualne ograniczenie nie powinno opóźniać wdrożenia usługi Azure RMS. Użytkownikom usługi Exchange Online chcącym korzystać z funkcji generowania własnych kluczy (BYOK) zaleca się wdrożenie usługi Azure RMS w domyślnym trybie zarządzania kluczami, w którym firma Microsoft generuje klucze i nimi zarządza. Dzięki temu można od razu korzystać z ochrony ważnych plików i wiadomości e-mail z opcją późniejszego wprowadzenia funkcji BYOK (na przykład kiedy usługa Exchange Online będzie już obsługiwać funkcję BYOK).

Jeśli jednak zasady firmy wymagają używania sprzętowego modułu zabezpieczeń (HSM) i w innym przypadku wdrożenie usługi Azure RMS będzie blokowane, jest możliwe wdrożenie usługi Azure RMS z funkcją BYOK już teraz, przy ograniczonej funkcjonalności usługi RMS w odniesieniu do programu Exchange. Więcej informacji zawiera temat [Cennik i ograniczenia dotyczące funkcji BYOK](../plan-design/byok-price-restrictions.md) w części [Planowanie i wdrażanie klucza dzierżawy usługi Azure Rights Management](../plan-design/plan-implement-tenant-key.md).

## Wygląda na to, że funkcja, której potrzebuję, nie współpracuje z chronionymi bibliotekami programu SharePoint. Czy obsługa tej funkcji jest planowana?
Obecnie program SharePoint obsługuje dokumenty chronione za pomocą usługi RMS, korzystając w tym celu z bibliotek chronionych za pomocą usługi IRM, które nie obsługują niestandardowych szablonów, śledzenia dokumentów i innych funkcji. Więcej informacji można znaleźć w sekcji dotyczącej [usługi SharePoint Online i programu SharePoint Server](../understand-explore/office-apps-services-support.md#sharepoint-online-and-sharepoint-server) w artykule [Office applications and services](../understand-explore/office-apps-services-support.md) (Aplikacje i usługi biurowe).

Użytkownicy zainteresowani konkretną funkcją, która nie jest jeszcze obsługiwana, powinni śledzić ogłoszenia na [blogu dotyczącym pakietu Enterprise Mobility i zabezpieczeń](https://blogs.technet.microsoft.com/enterprisemobility/?product=azure-rights-management-services).

## Jak skonfigurować usługę OneDrive dla Firm w usłudze SharePoint Online, tak aby użytkownicy mogli bezpiecznie udostępniać pliki wewnątrz i na zewnątrz firmy?
Domyślnie tej usługi nie konfiguruje administrator usługi Office 365, lecz robią to użytkownicy.

Podobnie jak administrator witryny programu SharePoint włącza i konfiguruje usługę IRM dla biblioteki programu SharePoint, której jest właścicielem, usługa OneDrive dla Firm jest zaprojektowana tak, aby użytkownicy włączali i konfigurowali usługę IRM dla własnej biblioteki usługi OneDrive dla Firm.  Można jednak zrobić to dla nich, korzystając ze środowiska PowerShell. Instrukcje można znaleźć w sekcji [SharePoint Online and OneDrive for Business: IRM Configuration](../deploy-use/configure-office365.md#sharepoint-online-and-onedrive-for-business-irm-configuration) (Usługi SharePoint Online i OneDrive dla Firm: konfiguracja usługi IRM) artykułu [Office 365: Configuration for clients and online services](../deploy-use/configure-office365.md) (Usługa Office 365: konfiguracja dla klientów i usług online).

## Czy istnieją jakieś wskazówki ułatwiające pomyślne wdrożenie usług RMS?
Po nadzorowaniu wielu wdrożeń i wysłuchaniu opinii naszych klientów, partnerów, konsultantów i inżynierów pomocy technicznej możemy udzielić jednej podstawowej wskazówki opartej na naszym doświadczeniu: **projektuj i wdrażaj proste zasady praw**.

Ponieważ usługa Azure RMS umożliwia bezpieczne udostępnianie dowolnym osobom, można pozwolić sobie na ambitne podejście do zasięgu ochrony informacji. Jednak zasady dotyczące praw należy określać w sposób konserwatywny. W przypadku wielu organizacji najsilniejszy wpływ na prowadzoną działalność ma zapobieganie wyciekowi danych przez stosowanie domyślnego szablonu zasad praw umożliwiającego dostęp wyłącznie osobom z danej organizacji. Oczywiście w razie potrzeby można wprowadzić bardziej szczegółowe ograniczenia — uniemożliwiać drukowanie, edycję itd. Jednak takie szczegółowe ograniczenia należy stosować wyjątkowo, w przypadku dokumentów wymagających naprawdę specjalnej ochrony, i nie implementować ich od razu, ale zaplanować podejście etapowe.

## Jakie funkcje mogą lub nie mogą być używane w przypadku różnych subskrypcji obsługujących usługę Azure RMS?
W przypadku płatnych subskrypcji obsługujących usługę Azure RMS (Office 365, Azure RMS Premium i Enterprise Mobility Suite) istnieją pewne różnice w obsługiwanych funkcjach usługi RMS. Z listą tych różnic można zapoznać się w artykule [Porównanie ofert usług Rights Management (RMS)](http://technet.microsoft.com/dn858608).

Bezpłatna subskrypcja obsługująca usługę Azure RMS (usługę RMS dla użytkowników indywidualnych) obsługuje korzystanie z zawartości chronionej za pomocą usługi Azure RMS. Aby uzyskać więcej informacji, zobacz [Usługa RMS dla użytkowników indywidualnych i usługa Azure Rights Management](../understand-explore/rms-for-individuals.md).

## Gdzie można uzyskać informacje techniczne na temat bezpłatnej subskrypcji usługi Azure RMS (usługi RMS dla użytkowników indywidualnych) dotyczących na przykład sposobu działania, metody kontrolowania kont oraz domen, których nie można używać?
Odpowiedzi na te pytania można znaleźć w artykule [Usługa RMS dla użytkowników indywidualnych i usługa Azure Rights Management](../understand-explore/rms-for-individuals.md) i innych pokrewnych artykułach.

## Jak odzyskać dostęp do plików, które były chronione przez pracownika, który opuścił organizację?
Należy użyć funkcji administratora usługi Azure RMS pozwalającej uprawionym użytkownikom korzystać z pełnych praw właściciela dotyczących wszystkich licencji na użytkowanie przydzielonych przez dzierżawcę usługi RMS w danej organizacji. Ta sama funkcja w razie potrzeby umożliwia autoryzowanym usługom indeksowanie i przeprowadzanie inspekcji plików.

Aby uzyskać więcej informacji, zobacz [Konfigurowanie superużytkowników usługi Azure Rights Management i usług odnajdywania lub odzyskiwania danych](../deploy-use/configure-super-users.md).

## Czy usługa Rights Management może uniemożliwiać przechwytywanie ekranu?
Przez nieprzyznanie [prawa użytkowania](../deploy-use/configure-usage-rights.md) **Kopiowanie** usługa Rights Management może zapobiegać przechwytywaniu ekranu za pomocą wielu typowych narzędzi na różnych platformach Windows (Windows 7, Windows 8.1, Windows 10, Windows Phone) i Android. Jednak urządzenia z systemem iOS i komputery Mac nie zezwalają żadnej aplikacji na zapobieganie przechwytywaniu ekranu. Podobna sytuacja ma miejsce w przypadku przeglądarek (na przykład używanych łącznie z aplikacjami Outlook Web App i Office Online), które również nie mogą uniemożliwiać przechwytywania ekranu.

Uniemożliwianie przechwytywania ekranu może pomóc uniknąć przypadkowego lub wynikającego z niedbałości ujawnienia poufnych lub wrażliwych informacji. Użytkownik może jednak udostępniać dane wyświetlane na ekranie różnymi sposobami, a wykonanie zrzutu ekranu jest tylko jedną z nich. Użytkownik chcący udostępnić wyświetlane informacje może na przykład zrobić zdjęcie ekranu aparatem w telefonie, przepisać dane lub po prostu słownie przekazać je innej osobie.

Jak dowodzą te przykłady, nawet jeśli wszystkie platformy i całe oprogramowanie obsługuje interfejsy API usługi Rights Management pod kątem blokowania przechwytywania ekranu, sama technologia nie może zapobiec udostępnieniu przez użytkowników poufnych danych. Usługa Rights Management może pomóc chronić ważne dane za pomocą zasad autoryzacji i użycia, ale to rozwiązanie do zarządzania prawami w przedsiębiorstwie powinno być stosowane razem z innymi środkami kontroli. Przekłady obejmują wdrożenie zabezpieczeń fizycznych, dokładne monitorowanie osób mających uprawnienia dostępu do danych organizacji oraz inwestowanie w edukację użytkowników, tak aby wiedzieli, których danych nie należy udostępniać.

## Jaka jest różnica między ochroną wiadomości e-mail za pomocą ustawienia Nie przesyłaj dalej i szablonem bez prawa do przesyłania dalej?

Niezależnie od nazwy i wyglądu ustawienie **Nie przesyłaj dalej** nie jest przeciwieństwem prawa do przesyłania dalej ani szablonem. Jest to zestaw praw obejmujących ograniczenia przesyłania dalej wiadomości e-mail, kopiowania, drukowania i zapisywania załączników. Prawa są dynamicznie stosowane do użytkowników za pośrednictwem wybranych adresatów, a nie statycznie przypisane przez administratora. Więcej informacji można znaleźć w sekcji [Opcja Nie przekazuj dotycząca wiadomości e-mail](../deploy-use/configure-usage-rights.md#do-not-forward-option-for-emails) w artykule [Konfigurowanie praw użytkowania dla usługi Azure Rights Management](../deploy-use/configure-usage-rights.md).

## Gdzie można znaleźć dodatkowe informacje na temat usługi Azure RMS, dotyczące na przykład kwestii prawnych, zgodności i umów SLA?
Usługa Azure RMS obsługuje inne usługi i korzysta z nich. Jeśli szukasz informacji związanych z usługą Azure RMS, ale niedotyczących sposobu korzystania z usługi Azure RMS, sprawdź następujące zasoby:

**Informacje prawne i ochrona prywatności:**

-   Informacje o umowie dotyczącej usług Microsoft Azure: [Umowa dotycząca usług Microsoft Azure](http://azure.microsoft.com/support/legal/subscription-agreement/)

-   Informacje o ochronie prywatności w usługach Microsoft Azure: [Zasady zachowania poufności informacji usług Microsoft Azure](http://azure.microsoft.com/support/legal/privacy-statement/)

**Zabezpieczenia, zgodność i inspekcja:**

Zobacz sekcję [Wymagania dotyczące zabezpieczeń, zgodności i przepisów prawnych](../understand-explore/azure-rms-problems-it-solves.md#security-compliance-and-regulatory-requirements) w artykule [Jakie problemy rozwiązuje usługa Azure RMS?](../understand-explore/azure-rms-problems-it-solves.md). Ponadto:

-   Zewnętrzne certyfikaty usługi Azure RMS: [Centrum zaufania systemu Microsoft Azure](http://azure.microsoft.com/support/trust-center/)

-   Informacje dotyczące standardu FIPS 140: [FIPS 140 Validation](https://technet.microsoft.com/library/security/cc750357.aspx)

**Umowy dotyczące poziomu usług:**

-   Umowa dotycząca poziomu usług dla usługi Azure RMS, według wybranego regionu: [pobierz ze strony wyszukiwania licencjonowania produktów](http://microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&amp;DocumentTypeId=37)

    - Na przykład kliknij pozycję **OnlineSvcsConsolidatedSLA(WW)(English)(March2016)**, aby pobrać umowę dotyczącą poziomu usług dla Ameryki Północnej z marca 2016 r.

-   Umowa dotycząca poziomu usług dla usługi Azure Active Directory: [Umowy dotyczące poziomu usług](http://azure.microsoft.com/support/legal/sla/)

**Dokumentacja:**

-   Witryna dokumentacji usługi Azure Active Directory: [Azure Active Directory](http://azure.microsoft.com/documentation/services/active-directory/)

-   Biblioteka usługi Azure Active Directory: [Azure Active Directory](https://msdn.microsoft.com/library/azure/mt168838.aspx)

-   Biblioteka usługi Office 365: [Office 365](http://technet.microsoft.com/library/dn127064%28v=office.14%29.aspx)

## Jakie są najnowsze informacje na temat nowych funkcji klasyfikacji i etykietowania?

Ta funkcja jest obecnie dostępna w publicznej wersji zapoznawczej usługi Azure Information Protection. Wypróbuj ją teraz. Listę dostępnych zasobów można znaleźć w artykule [What is Azure Information Protection preview?](../information-protection/what-is-information-protection.md) (Co to jest wersja zapoznawcza usługi Azure Information Protection?).


## Podobno nowa wersja ma być wkrótce dostępna dla usługi Azure RMS — kiedy zostanie ona wydana?

Dokumentacja techniczna nie zawiera informacji o kolejnych wersjach. W przypadku tego typu informacji i zapowiedzi dotyczących wersji zapoznaj się z [blogiem dotyczącym pakietu Enterprise Mobility i zabezpieczeń](https://blogs.technet.microsoft.com/enterprisemobility/?product=azure-rights-management-services) i pobierz najnowsze aktualizacje kanału [@TheRMSGuy Dana Plastina](https://twitter.com/TheRMSGuy) w serwisie Twitter. Jeśli interesuje Cię wersja pakietu Office, sprawdź również [blog dotyczący pakietu Office](https://blogs.office.com/).

## Co należy zrobić, jeśli mojego pytania nie ma na tej liście?
Skorzystaj z linków i zasobów wymienionych w artykule [Informacje i pomoc techniczna dla usługi Azure Rights Management](information-support.md).

Istnieją także często zadawane pytania sformułowane pod kątem użytkowników końcowych:

-   [Często zadawane pytania dotyczące aplikacji do udostępniania usługi Rights Management dla systemu Windows](https://technet.microsoft.com/dn467883)

-   [Często zadawane pytania dotyczące aplikacji do udostępniania usługi Rights Management dla platform mobilnych i Mac](https://technet.microsoft.com/dn451248)

-   [Często zadawane pytania dotyczące śledzenia dokumentów](http://go.microsoft.com/fwlink/?LinkId=523977)

Ta strona zawierająca często zadawane pytania będzie regularnie aktualizowana, a nowe informacje będą publikowane w comiesięcznych ogłoszeniach o aktualizacji dokumentacji na [blogu dotyczącym pakietu Enterprise Mobility i zabezpieczeń](https://blogs.technet.microsoft.com/enterprisemobility/?product=azure-rights-management-services).





<!--HONumber=Jul16_HO3-->


