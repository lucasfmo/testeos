---
title: "Jak tworzyć konta usługi RMS dla użytkowników indywidualnych | Azure RMS"
description: 
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: a60731bd-f78d-4f00-bb3e-354637b312ab
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 0f355da35dff62ecee111737eb1793ae286dc93e
ms.openlocfilehash: 19252180802c69d6e5d6bf22c71ff3bcba96fb36


---

# Jak tworzyć konta usługi RMS dla użytkowników indywidualnych

*Dotyczy: Azure Rights Management*

Aby utworzyć bezpłatne konto, użytkownicy wysyłają żądanie, przechodząc do [strony usługi Microsoft Rights Management](https://portal.aadrm.com/) i podając służbowy adres e-mail. 

Najczęściej spotykaną metodą przekierowywania użytkowników na stronę tworzenia konta jest wysłanie do nich wiadomości e-mail z chronionym załącznikiem, który zawiera instrukcje dotyczące sposobu tworzenia konta. W odpowiedzi użytkownicy otrzymują wiadomość e-mail od firmy Microsoft i mogą zakończyć proces tworzenia konta, wprowadzając wymagane szczegóły. Następnie otrzymują oni ostatnią wiadomość e-mail z potwierdzeniem od firmy Microsoft. Wiadomość ta odsyła ich do strony, z której można pobrać aplikację do udostępniania dla różnych urządzeń i która zawiera link do podręcznika użytkownika.

## Aby utworzyć konto usługi RMS dla użytkowników indywidualnych

1.  Na komputerze z systemem Windows lub Mac przejdź do [strony usługi Microsoft Rights Management](https://portal.aadrm.com).

2.  Wpisz adres e-mail używany dla organizacji, taki jak **joannam@contoso.com** lub **p.michalski@fabrikam.com**.

    > [!IMPORTANT]
    > Osobiste konta e-mail nie są obsługiwane, dlatego nie należy wprowadzać konta Microsoft (wcześniej znanego jako konto usługi Microsoft Live ID) ani innego konta osobistego od usługodawcy internetowego, z którego można korzystać w domu.

3.  Kliknij pozycję **Rozpocznij**.

    Firma Microsoft użyje Twojego adresu e-mail w celu sprawdzenia, czy Twoja organizacja ma już [płatną subskrypcję obejmującą usługę Azure RMS](../get-started/requirements-subscriptions.md). Jeśli tak, nie potrzebujesz konta usługi RMS dla użytkowników indywidualnych. Nastąpi natychmiastowe zalogowanie, a proces samoobsługowego tworzenia konta usługi RMS dla użytkowników indywidualnych zostanie anulowany. Jeśli płatna subskrypcja usługi Azure RMS nie zostanie znaleziona, nastąpi przejście do następnego kroku.

4.  Poczekaj na wiadomość e-mail z potwierdzeniem, która zostanie wysłana na podany adres e-mail. Będzie to wiadomość od firmy Microsoft (DoNotReply@microsoft.com) zatytułowana **Microsoft RMS**.

5.  Po otrzymaniu wiadomości e-mail kliknij link w obrębie instrukcji, aby ukończyć proces tworzenia konta.

6.  Link prowadzi do nowej strony **Microsoft Rights Management**, na której należy podać szczegóły swojego konta. Wpisz swoje imię i nazwisko, wprowadź i potwierdź wybrane hasło, wybierz swój kraj z listy rozwijanej (lub najbliższy, jeśli na liście nie ma Twojego kraju), a następnie kliknij pozycję **Utwórz**.

7.  Poczekaj na kolejną wiadomość e-mail od firmy Microsoft, która potwierdzi, że Twoje konto jest gotowe do użycia.

8.  Po otrzymaniu wiadomości e-mail kliknij link umożliwiający zalogowanie i zapoznaj się z instrukcjami dotyczącymi pobierania i instalowania aplikacji do udostępniania. Możesz również kliknąć link Pomoc, aby zapoznać się z podręcznikiem użytkownika aplikacji do udostępniania.

Teraz konto zostało utworzone i możesz już chronić pliki oraz odczytywać pliki chronione przez innych. Po wyświetleniu monitu o zalogowanie się w celu włączenia ochrony plików lub odczytania chronionych plików wprowadź swój adres e-mail i hasło użyte podczas tworzenia konta usługi RMS dla użytkowników indywidualnych.

## Omówienie techniczne procesu tworzenia konta
Usługa RMS dla użytkowników indywidualnych korzysta z samoobsługowego procesu tworzenia konta, który jest również stosowany przez inne usługi używające technologii firmy Microsoft opartych na chmurze do uwierzytelniania użytkowników.

Oto co dzieje się w tle, gdy użytkownik tworzy konto usługi RMS dla użytkowników indywidualnych, a jego organizacja nie ma subskrypcji usługi Office 365 ani platformy Azure, a w związku z tym nie ma na platformie Azure katalogu służącego do uwierzytelniania użytkowników:

1.  Gdy pierwszy użytkownik z organizacji wysyła żądanie dotyczące subskrypcji usługi RMS dla użytkowników indywidualnych, nazwa domeny podana w jego adresie e-mail jest sprawdzana pod kątem już istniejącego skojarzenia z dzierżawą platformy Azure. Jeśli dzierżawa nie istnieje, następuje automatyczne utworzenie nowej dzierżawy i katalogu platformy Azure dla organizacji z kontem pierwszego użytkownika. W odróżnieniu od płatnej subskrypcji platformy Azure pierwsze konto nie odpowiada administratorowi globalnemu, ale użytkownikowi standardowemu. Nowe konto używa adresu e-mail i hasła podanego przez użytkownika.

    > [!NOTE]
    > Niektórych nazw domen nie można używać do tworzenia katalogu, a co za tym idzie — na potrzeby usługi RMS dla użytkowników indywidualnych. Listę zablokowanych domen można wyświetlić z pliku notacji obiektu JavaScript: [http://portal.aadrm.com/content/blocked_domains.json](http://portal.aadrm.com/content/blocked_domains.json).

    W przypadku znalezienia istniejącej dzierżawy nastąpi sprawdzenie, czy ma ona już subskrypcję usługi Azure RMS. Jeśli subskrypcja nie zostanie znaleziona, można dodać bezpłatną subskrypcję usługi RMS dla użytkowników indywidualnych.

2.  Organizacja otrzymuje subskrypcję usługi RMS dla użytkowników indywidualnych. Teraz dany użytkownik może zostać uwierzytelniony przez platformę Azure, a następnie chronić pliki i odczytywać pliki chronione przez inne osoby za pomocą usługi Azure Rights Management. Aby chronić pliki i odczytywać pliki chronione, użytkownik musi mieć aplikację obsługującą usługi RMS, taką jak bezpłatna [aplikacja do udostępniania usługi Rights Management](../rms-client/sharing-app-windows.md).

3.  Gdy drugi użytkownik z tej samej organizacji wyśle żądanie dotyczące subskrypcji usługi RMS dla użytkowników indywidualnych, nowe konto użytkownika zostanie dodane do utworzonego wcześniej katalogu platformy Azure za pomocą należącej do organizacji subskrypcji usługi RMS dla użytkowników indywidualnych. Drugi użytkownik może robić wszystko to, co pierwszy (chronić pliki i odczytywać pliki chronione). Dodatkowo ci dwaj użytkownicy mogą teraz łatwiej współpracować w bezpieczny sposób dzięki możliwości szybkiego stosowania do plików domyślnych szablonów, które ograniczają dostęp do kont w organizacyjnym katalogu platformy Azure.

4.  Kolejni użytkownicy z tej samej organizacji wykonują te same czynności, aby dodać swoje konta (w przypadku tworzenia kont nowych użytkowników) do katalogu platformy Azure w organizacji. Im więcej kont zostanie dodanych do katalogu, tym większa grupa użytkowników będzie mogła bezpiecznie współpracować z innymi pracownikami i partnerami. Łatwiejsze stanie się również uniemożliwianie nieupoważnionym osobom odczytywania plików, do których nie powinny mieć dostępu.

W trakcie tego procesu organizacja nie jest obciążana żadnymi opłatami, a dział IT nie musi wykonywać żadnych czynności. Pracownicy tego działu mogą jednak zdecydować się na wykonanie jednej z poniższych czynności:

-   **Zarządzanie kontami i procesem tworzenia kont**: administratorzy IT mogą przejąć prawo własności katalogu i kont tworzonych automatycznie na platformie Azure. Mogą oni następnie zarządzać kontami, wdrażając rozwiązania do integracji katalogu, takie jak synchronizacja haseł i logowanie jednokrotne. Mogą również uniemożliwiać użytkownikom tworzenie kont lub rejestrowanie się w usłudze RMS dla użytkowników indywidualnych.

    Aby uzyskać więcej informacji, zobacz [Metody kontrolowania przez administratorów kont utworzonych dla usług RMS dla użytkowników indywidualnych](rms-for-individuals-take-control.md).

-   **Zarządzanie usługami Rights Management**: administratorzy IT mogą przekonwertować subskrypcję usługi RMS dla użytkowników indywidualnych dla organizacji na płatną subskrypcję obejmującą usługę Azure Rights Management. W takiej sytuacji istniejące konta i katalog platformy Azure zostaną zachowane w celu łatwego przeniesienia danych istniejących użytkowników, którzy korzystali z usługi RMS dla użytkowników indywidualnych. Wszystkie pliki, które użytkownicy chronili wcześniej, będą nadal chronione za pomocą tych samych zasad, a osoby, którym udzielono uprawnień do użycia plików, będą nadal mogły korzystać z plików w ten sam sposób.

    Wybór takiej metody postępowania sprawi, że organizacja osiągnie korzyści polegające na możliwości integracji usługi Rights Management ze swoimi przepływami pracy, usługami i magazynami danych. Ponadto można teraz zarządzać usługą Rights Management, ponieważ użytkownik kontroluje powiązany z organizacją klucz dzierżawy usługi Azure Rights Management. Można teraz wykonać następujące czynności:

    -   Konfigurowanie programów Exchange i SharePoint do obsługi usługi Azure Rights Management, nawet jeśli są one uruchamiane lokalnie. Programy Exchange i SharePoint są obsługiwane w sposób natywny w usługach online przez łącznik przeznaczony dla serwerów lokalnych. Aby uzyskać więcej informacji, zobacz następujące tematy:

        -   Sekcje dotyczące usług Exchange Online i SharePoint Online w temacie [Usługa Office 365: konfiguracja dla klientów i usług online](../deploy-use/configure-office365.md)

        -   [Wdrażanie łącznika usługi Azure Rights Management](../deploy-use/deploy-rms-connector.md)

    -   Zbieranie elektronicznych materiałów dowodowych związanych z danymi firmowymi. Dzięki temu można w razie potrzeby odszyfrowywać pliki chronione za pomocą usługi Rights Management. Aby uzyskać więcej informacji, zobacz [Konfigurowanie administratorów usługi Azure Rights Management i usług odnajdywania lub odzyskiwania danych](../deploy-use/configure-super-users.md).

    -   Rejestrowanie wszystkich działań na potrzeby usługi Rights Management przy użyciu metody stosowanej w organizacji. Jest to bardzo pomocna funkcja, ponieważ umożliwia nie tylko sprawdzanie, które pliki są obejmowane ochroną i kto pomyślnie uzyskuje do nich dostęp, ale także identyfikowanie podejrzanego zachowania nieupoważnionych osób, które próbują uzyskać dostęp do chronionych plików. Aby uzyskać więcej informacji, zobacz [Rejestrowanie i analizowanie danych użycia usługi Azure Rights Management](../deploy-use/log-analyze-usage.md).

    -   Udostępnianie użytkownikom możliwości śledzenia i odwoływania chronionych dokumentów, jeśli te funkcje są obsługiwane przez [subskrypcję usługi Azure RMS](https://technet.microsoft.com/dn858608). Aby uzyskać więcej informacji, zobacz [Śledzenie i odwoływanie plików](../rms-client/sharing-app-track-revoke.md) w [Podręczniku użytkownika aplikacji do udostępniania usług RMS](../rms-client/sharing-app-user-guide.md).

    -   Implementowanie rozwiązania „użyj własnego klucza” (BYOK, bring your own key), aby klucz dzierżawy usługi Azure Rights Management był generowany lokalnie zgodnie z zasadami dotyczącymi infrastruktury IT i bezpiecznie przesyłany do firmy Microsoft za pomocą sprzętowego modułu zabezpieczeń (HSM). Aby uzyskać więcej informacji, zobacz [Planowanie i wdrażanie klucza dzierżawy usługi Azure Rights Management](../plan-design/plan-implement-tenant-key.md).


## Następne kroki
Zobacz [Metody kontrolowania przez administratorów kont utworzonych dla usług RMS dla użytkowników indywidualnych](rms-for-individuals-take-control.md).





<!--HONumber=Jun16_HO4-->


