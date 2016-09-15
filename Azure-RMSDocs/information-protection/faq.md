---
title: "Często zadawane pytania dotyczące usługi Azure Information Protection (wersja zapoznawcza) | Azure Information Protection"
description: 
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 08/10/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 4b595b6a-7eb0-4438-b49a-686431f95ddd
ms.reviewer: adhall
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: d17bacf8e148622db0e2393f40d3fd37c8f086eb
ms.openlocfilehash: c61e299cac50069afc119d37fd461cda88a2afd3


---

# Często zadawane pytania dotyczące usługi Azure Information Protection (wersja zapoznawcza)

>*Dotyczy: Azure Information Protection (wersja zapoznawcza)*

**[Niniejsze informacje mają charakter wstępny i mogą ulec zmianom. ]**

Masz pytanie dotyczące wersji zapoznawczej usługi Azure Information Protection?  Zobacz, czy nie znajdziesz tutaj odpowiedzi. 

Możesz się spodziewać, że ta lista będzie często aktualizowana, gdyż niektóre informacje są przenoszone do głównej dokumentacji, a poza tym są dołączane nowe pytania otrzymane od klientów. 

## Co mogę zrobić przy użyciu wersji zapoznawczej usługi Azure Information Protection i jakie są aktualne ograniczenia?

Ta wersja zapoznawcza dodaje do aplikacji pakietu Microsoft Office pasek Information Protection, który umożliwia wyświetlanie i modyfikowanie przypisanych etykiet klasyfikacji danych. Klasyfikacja może być wykonywana ręcznie, zalecana użytkownikom lub stosowana automatycznie. W przypadku klasyfikacji podanej przez Ciebie dane mogą być chronione przy użyciu szablonu Azure Rights Management.  

Etykiety i zachowanie klasyfikacji są skonfigurowane w portalu Azure. Wbudowane zasady mogą służyć do szybkiej oceny usługi Azure Information Protection lub do pełnego dostosowania własnych zasad. Można zmienić kolory, nazwy i kolejność etykiet klasyfikacji widocznych dla użytkowników. Można również skonfigurować etykietki narzędzi i wizualne oznaczenia klasyfikacji, takie jak nagłówek, stopka lub znak wodny.

Kilka minut wystarczy do zapoznania się z naszym samouczkiem Szybki start: [Samouczek Szybki start dla usługi Azure Information Protection](infoprotect-quick-start-tutorial.md).

Należy pamiętać, że wersja zapoznawcza umożliwia testowanie nowego **planu usług Premium P2** i że niektóre zaawansowane funkcje, takie jak automatyczne i zalecane etykietowanie, mogą nie być ogólnie dostępne w Twoim bieżącym planie. Informacje o różnych planach usług (Azure Information Protection Premium P1 i Azure Information Protection Premium P2) znajdują się w następującym wpisie w blogu: [Introducing Enterprise Mobility + Security](https://blogs.technet.microsoft.com/enterprisemobility/2016/07/07/introducing-enterprise-mobility-security/) (Wprowadzenie do pakietu Enterprise Mobility + Security).

Ta wersja zapoznawcza ma następujące ograniczenia: W blogu [dotyczącym pakietu Enterprise Mobility i zabezpieczeń](https://blogs.technet.microsoft.com/enterprisemobility/?product=azure-information-protection) i witrynie [Yammer](https://www.yammer.com/askipteam/#/threads/inGroup?type=in_group&feedId=8652489&view=all) będą się pojawiać ogłoszenia o dostępności dodatkowych funkcji i możliwości:

- Brak centralnego rejestrowania dla funkcji klasyfikacji i etykietowania.

- Nazwy etykiet i etykietki narzędzi są obsługiwane tylko w jednym języku.

- Warunkami klasyfikacji automatycznej muszą być frazy lub wzorce.

- Pliki nie mogą być klasyfikowane w Eksploratorze plików systemu Windows.

- Aplikacje pakietu Office dla komputerów Mac i urządzeń przenośnych (iOS i Android) ani aplikacje sieci Web pakietu Office (Office Online) nie są jeszcze obsługiwane.

- Brak integracji z programem Exchange Online i usługą SharePoint Online.

- Zestaw SDK dla deweloperów i partnerów nie jest dostępny.

## Jaka subskrypcja jest potrzebna, aby zapoznać się z usługą Azure Information Protection?

W wersji zapoznawczej można użyć dowolnej subskrypcji, która obejmuje usługę Azure Rights Management. Usługa Azure Information Protection jest dostępna we wszystkich regionach. Aby uzyskać więcej informacji o dostępnych subskrypcjach oraz linki do bezpłatnych wersji próbnych, zobacz artykuł [Wymagania dotyczące usługi Azure RMS: subskrypcje usług w chmurze, które obsługują usługę Azure RMS](../get-started/requirements-subscriptions.md).

Aby skonfigurować zasady usługi Azure Information Protection w portalu Azure, trzeba posiadać subskrypcję platformy Azure. Jeśli organizacja nie ma jeszcze subskrypcji platformy Azure, możesz ją uzyskać, tworząc konto do użycia na potrzeby bezpłatnej wersji próbnej: przejdź na stronę [wprowadzenia do platformy Azure](https://account.windowsazure.com/organization) i postępuj zgodnie z instrukcjami.

Wszelkie zmiany wymagań dotyczących subskrypcji będą ogłaszane w blogu [dotyczącym pakietu Enterprise Mobility i zabezpieczeń](https://blogs.technet.microsoft.com/enterprisemobility/?product=azure-information-protection).

## Czy muszę być administratorem globalnym, aby wypróbować wersję zapoznawczą usługi Azure Information Protection?

Tylko w przypadku wersji zapoznawczej dowolny użytkownik uwierzytelniony przez usługę Azure może zobaczyć i skonfigurować w portalu Azure zasady usługi Azure Information Protection dotyczące klasyfikacji i etykietowania dla swojej dzierżawy. Jednak aby skonfigurować etykietę w celu zastosowania szablonu usługi Rights Management, należy zalogować się jako administrator globalny dla usługi Azure Active Directory.

Jeśli w trakcie instalacji [klienta usługi Azure Information Protection](https://www.microsoft.com/en-us/download/details.aspx?id=53018) wybrano opcję zainstalowania zasady demonstracyjnej, nie jest nawet konieczne logowanie w portalu w celu wypróbowania wersji zapoznawczej. Zasada demonstracyjna instaluje lokalnie zasadę domyślną usługi Azure Information Protection, co umożliwia próby etykietowania dokumentów i wiadomości e-mail, ale nie pozwala na zmianę ani dodanie nowej etykiety bez rejestrowania się w portalu Azure. 

Jeśli chcesz chronić dokumenty i wiadomości e-mail sklasyfikowanie i zaetykietowane przez siebie, lecz jeszcze nie aktywowano usługi Azure Rights Management, proces aktywacji wymaga specjalnych uprawnień administratora. Więcej informacji można znaleźć w odpowiedzi na pytanie [Czy trzeba być administratorem globalnym, aby skonfigurować usługę Azure RMS, czy można to oddelegować do innych administratorów?](../get-started/faqs.md#do-you-need-to-be-a-global-admin-to-configure-azure-rms-or-can-i-delegate-to-other-administrators)


## Czy usługa Azure Information Protection obsługuje scenariusze lokalne i hybrydowe?

Usługa Azure Information Protection to rozwiązanie oparte na chmurze. Jeśli interesuje Cię wdrożenie usługi Azure Information Protection dla scenariusza hybrydowego, skontaktuj się z zespołem usługi Information Protection, wysyłając wiadomość e-mail na adres askipteam@microsoft.com.

## Jakie platformy klienckie i aplikacje są obsługiwane przez usługę Azure Information Protection?

Ten temat został udokumentowany i będzie aktualizowany w artykule [Wymagania dotyczące usługi Azure Information Protection](requirements-azure-infoprotect.md).


## Jak komputery uzyskują informacje o zasadach od usługi Azure Information Protection i jak często są one odświeżane?

Przy każdym otwarciu aplikacji pakietu Office klient usługi Azure Information Protection sprawdza, czy jest dostępna nowsza wersja zasad usługi. Jeśli istnieje nowsza wersja, klient pobiera ją za pomocą łącza HTTPS w celu zabezpieczenia danych. 

Jeśli podczas publikowania nowych zasad usługi Azure Information Protection załadowanych jest wiele wystąpień aplikacji pakietu Office, musisz zamknąć wszystkie instancje, aby pobrać najnowszą wersję zasad. Przykładowo, jeśli masz otwarte dwa dokumenty programu Word i chcesz przetestować zaktualizowane zasady usługi Azure Information Protection tylko w jednym dokumencie: zamknij oba dokumenty programu Word i otwórz ponownie dokument, którego chcesz użyć wraz z najnowszymi zasadami.

## Gdzie mogą być przechowywane pliki korzystające z usługi Azure Information Protection? 

Ponieważ usługa Azure Information Protection nadaje trwałe etykiety i chroni pliki oraz wiadomości e-mail, nie ma znaczenia, gdzie są przechowywane pliki.

## Czy mogę klasyfikować tylko nowe dane, czy też również dane istniejące?

Akcje zasady usługi Azure Information Protection stają się aktywne przy zapisywaniu dokumentów i wysyłaniu wiadomości e-mail, zarówno w przypadku nowej zawartości, jak i zmian w zawartości istniejącej. 

Jeśli pliki, które chcesz sklasyfikować, zostały już zapisane, wystarczy je otworzyć i zapisać w aplikacji pakietu Office. 

Obecnie nie można skanować i klasyfikować dokumentów zbiorczo, gdyż każdy dokument musi zostać otwarty i zapisany w aplikacji pakietu Office. 

## Czy usługi Azure Information Protection można używać wyłącznie do klasyfikowania, bez wymuszania szyfrowania i ograniczania prawa użytkowania?

Tak. Można tak skonfigurować zasadę usługi Azure Information Protection, aby wyłącznie nadawała etykiety. W zasadzie można oczekiwać, że będzie się tak dziać w większości już wdrożonych sieci, w których należy chronić tylko podzbiór dokumentów lub wiadomości e-mail wymagających specjalnego zarządzania danymi.

## Jak działa automatyczna klasyfikacja?

W portalu Azure można użyć wstępnie zdefiniowanych wzorców, takich jak numer karty kredytowej lub numer ubezpieczenia społecznego w USA. Możesz zdefiniować niestandardowy ciąg lub szablon będący warunkiem automatycznej klasyfikacji.

Podobny przykład pojawia się w [samouczku Szybki start dla usługi Azure Information Protection](infoprotect-quick-start-tutorial.md). 

Dokładność klasyfikacji zależy od sposobu skonfigurowania reguły klasyfikacji, która opiera się na warunkach. Obecnie warunki obsługują wzorce tekstu i wyrażenia regularne. Aby uzyskać informacje o wszystkich opcjach dostępnych podczas używania wersji zapoznawczej wraz z sugerowanymi przykładami do testowania, zobacz [Konfigurowanie warunków klasyfikacji automatycznej i zalecanej dla usługi Azure Information Protection](configure-policy-classification.md). Wykrywanie jest uruchamiane przy zapisywaniu dokumentu lub wysyłaniu wiadomości e-mail.

Aby zapewnić najlepszą jakość obsługi i ciągłość prowadzenia działalności biznesowej, warto rozpocząć od wydawania zaleceń użytkownikom, a nie od wprowadzania czynności w pełni zautomatyzowanych. Dzięki temu użytkownicy mają wybór pomiędzy akceptacją etykietowania lub akcji ochronnych a odrzuceniem takiego zalecenia.   

## Czy usługa Azure Information Protection monituje użytkowników o samodzielne klasyfikowanie plików zamiast używania automatycznej klasyfikacji? 

Tak. Użyj portalu Azure, aby skonfigurować, czy używać automatycznej klasyfikacji, czy wydawać zalecenie użytkownikom, nadając opcji **Wybierz sposób stosowania etykiet: automatycznie lub zalecając użytkownikowi ** wartość **Zalecenie**.

Podobny przykład pojawia się w [samouczku Szybki start dla usługi Azure Information Protection](infoprotect-quick-start-tutorial.md).  

## Czy można wymusić klasyfikowania wszystkich dokumentów?

Tak. Jeśli wymagasz, aby użytkownicy klasyfikowali wszystkie zapisywane pliki, w portalu Azure należy opcji **Wszystkie dokumenty i wiadomości e-mail muszą mieć etykietę** nadać wartość **Wł.**. 

## Czy można usunąć klasyfikację z pliku?

Tak. Aby usunąć klasyfikację z pliku, otwórz plik w aplikacji pakietu Office, kliknij ikonę **Edytuj etykietę** na pasku Information Protection, kliknij ikonę **Usuń etykietę**, a następnie kliknij przycisk **OK**, aby potwierdzić operację. 


## Czy można monitować użytkowników o uzasadnienie, dlaczego zmieniają poziom klasyfikacji?

Tak. Aby się upewnić, że użytkownicy uzasadniają swoje zmiany klasyfikacji, w portalu Azure należy opcji **Użytkownik musi podać uzasadnienie obniżenia poziomu ważności** nadać wartość **Wł.**. W takim przypadku wykonywana czynność oraz stosowne uzasadnienie zostaną zapisane w ich lokalnym dzienniku zdarzeń systemu Windows: **Application**  >  **Microsoft Azure Information Protection**.

## Jak automatycznie chronić zawartość po jej zakwalifikowaniu?

W portalu Azure można wybrać szablon Azure Rights Management, aby automatycznie chronić zawartość odpowiednio do podanego poziomu klasyfikacji.

Podobny przykład pojawia się w [samouczku Szybki start dla usługi Azure Information Protection](infoprotect-quick-start-tutorial.md). Aby uzyskać więcej informacji, zobacz [Konfigurowanie etykiety w celu zastosowania ochrony usługi Rights Management](configure-policy-protection.md).

## Czy plik może mieć dwie różne klasyfikacje?

W razie potrzeby można utworzyć etykiety podrzędne, aby lepiej opisać podkategorie konkretnej etykiety ważności. Na przykład etykieta główna **Tajne** może zawierać takie etykiety podrzędne jak **Tajne — prawne** i **Tajne — finanse**. Różnym etykietom podrzędnym można przypisać różne wizualne oznaczenia klasyfikacji i różne szablony usługi Rights Management.

Chociaż obecnie można ustawić oznaczenia wizualne, ochronę i warunki na obu poziomach, przy korzystaniu z poziomów podrzędnych te ustawienia należy konfigurować tylko dla poziomów podrzędnych. W przypadku skonfigurowania tych samych ustawień na etykiecie nadrzędnej i jej etykiecie podrzędnej ustawienia na poziomie podrzędnym mają pierwszeństwo.

## Jak rozwiązania DLP i inne aplikacje integrują się z usługą Azure Information Protection?

Ponieważ usługa Azure Information Protection używa do klasyfikacji trwałych metadanych, w tym etykiety w postaci zwykłego tekstu, te informacje są odczytywane przez rozwiązania DLP i inne aplikacje. W plikach metadane te są przechowywane we właściwościach niestandardowych; w wiadomościach e-mail znajdują się one w nagłówkach.

## Jak działa śledzenie i odwoływanie dokumentów w usłudze Azure Information Protection?

Śledzenie dokumentów w przypadku plików sklasyfikowanych i chronionych za pomocą usługi Azure Information Protection działa tak samo, jak obecnie w przypadku usługi Azure Rights Management i aplikacji RMS sharing. Możesz także uzyskać dostęp do witryny śledzenia dokumentów, używając klienta usługi Azure Information Protection (w wersji 1.0.233 lub nowszej): 

- W aplikacji pakietu Office na karcie **Narzędzia główne** w grupie **Ochrona** kliknij kolejno pozycje **Chroń** > **Śledź użycie**. 

Aby uzyskać więcej informacji, zobacz artykuł [Śledzenie i odwoływanie dokumentów podczas używania aplikacji RMS sharing](../rms-client/sharing-app-track-revoke.md).

## W jaki sposób usługa Azure Information Protection wymusza skonfigurowane przeze mnie zasady?

Jeśli dokument jest chroniony za pomocą szablonu Azure Rights Management, użytkownik jest najpierw uwierzytelniany w celu zapewnienia, że ma uprawnienia do dokumentu, a następnie aplikacja wymusza zasadę praw użytkowania. 

## Jak usługa Azure Information Protection korzysta z usługi Azure Active Directory?

Usługa Azure Information Protection używa usługi Azure Active Directory do uwierzytelniania użytkowników.

## Czy można kontrolować, którzy użytkownicy mogą używać usługi Azure Information Protection do klasyfikowania i ochrony zawartości?

Można ograniczyć grono użytkowników, którzy mogą klasyfikować i chronić dane, kontrolując dystrybucję klienta usługi Azure Information Protection. 

Pliki i wiadomości e-mail sklasyfikowane przez usługę Azure Information Protection mogą być używane lub edytowane przez dowolnego użytkownika, z użyciem lub bez zainstalowanego klienta usługi Azure Information Protection. 

## Jak zgłosić problem lub wysłać opinię dotyczącą tej wersji zapoznawczej?

Jeśli napotkasz problem podczas pracy z tą wersją zapoznawczą, w aplikacji pakietu Office na karcie **Główna** w grupie **Ochrona** kliknij przycisk **Chroń**, a następnie kliknij przycisk **Pomoc i opinie**. W oknie dialogowym **Microsoft Azure Information Protection** kliknij przycisk **Wyślij opinię**. Spowoduje to wysłanie wiadomości e-mail do zespołu Information Protection i automatyczne dołączenie plików dziennika z Twojego komputera służących do zdiagnozowania problemu. 

Jeśli masz pytania lub opinie, użyj witryny usługi Yammer [Azure Information Protection](https://www.yammer.com/askipteam/#/threads/inGroup?type=in_group&feedId=8652489&view=all). 

## Co należy zrobić, jeśli mojego pytania nie ma na tej liście?

Najpierw upewnij się, że pytanie nie jest zawarte w [ogłoszeniu o wersji zapoznawczej usługi Azure Information Protection](https://blogs.technet.microsoft.com/enterprisemobility/2016/07/12/azure-information-protection-public-preview-available-now/) na blogu Enterprise Mobility and Security.

Następnie odwiedź naszą witrynę [Yammer](https://www.yammer.com/askipteam/#/threads/inGroup?type=in_group&feedId=8652489&view=all) aby zobaczyć, czy inny użytkownik nie zapytał o to samo. Jeśli nie, zgłoś zapytanie tutaj.







<!--HONumber=Aug16_HO2-->


