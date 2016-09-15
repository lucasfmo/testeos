---
title: "Scenariusz — zachowanie kontroli nad dokumentami przechowywanymi w programie SharePoint | Azure RMS"
description: 
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 1b6244c7-5ab9-4881-bc8f-6fa960390d89
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ed50d87138c428fadfd22cd5b3ef3c7f7e421848
ms.openlocfilehash: cb028afcbfd9b59f134539c434f4f49efc5e9092


---

# Scenariusz — zachowanie kontroli nad dokumentami przechowywanymi w programie SharePoint

*Dotyczy usług: Azure Rights Management, Office 365*

W tym scenariuszu i dodatkowej dokumentacji użytkownika usługa Azure Rights Management jest używana w celu zapewnienia kontroli nad dokumentami pakietu Office przechowywanymi w programie SharePoint za pomocą bibliotek chronionych. Na przykład dokumenty są automatycznie chronione przed przypadkowym lub zamierzonym wyciekiem spowodowanym przez użytkowników, przy czym dostęp do zawartości można zablokować nawet po jej pobraniu lub zsynchronizowaniu. Pliki, którym chcesz zapewnić ochronę, mogą być używane podczas wewnętrznej współpracy nad dokumentami lub planami projektowymi bądź innymi materiałami. Po skonfigurowaniu bibliotek chronionych dla programu SharePoint przechowywane w nich pliki pakietu Office będą chronione za pomocą usługi Azure Rights Management.

Podane tu instrukcje mają zastosowanie w następujących okolicznościach:

-   Pracownicy udostępniają dokumenty pakietu Office, które znajdują się w bibliotece programu SharePoint, i wspólnie nad nimi pracują.

-   Pracownicy nie potrzebują ustawiać ani zmieniać uprawnień, które administrator konfiguruje na poziomie biblioteki.

-   Pracownicy nie muszą udostępniać tych dokumentów osobom spoza organizacji.

## Instrukcje dotyczące wdrażania
![Instrukcje dla administratora dotyczące szybkiego wdrażania usługi Azure RMS](../media/AzRMS_AdminBanner.png)

Zanim przejdziesz do dokumentacji użytkownika, upewnij się, że zostały spełnione następujące wymagania i wykonano procedury pomocnicze.

## Wymagania dotyczące tego scenariusza
Aby zrealizować ten scenariusz, należy spełnić następujące wymagania:

|Wymaganie|Jeśli potrzebujesz dodatkowych informacji|
|---------------|--------------------------------|
|Zostały przygotowane konta i grupy dla usługi Office 365 lub Azure Active Directory.|[Przygotowanie do wdrożenia usługi Azure Rights Management](https://technet.microsoft.com/library/jj585029.aspx)|
|Usługa Azure Rights Management została aktywowana.|[Aktywacja usługi Azure Rights Management](https://technet.microsoft.com/library/jj658941.aspx)|
|W przypadku używania programu SharePoint Server: należy wdrożyć łącznik usługi RMS i skonfigurować go na potrzeby programu SharePoint.|[Wdrażanie łącznika usługi Azure Rights Management](https://technet.microsoft.com/library/dn375964.aspx)|
|Należy skonfigurować uprawnienia do chronionej witryny programu SharePoint.|[Zarządzanie uprawnieniami dotyczącymi listy, biblioteki, folderu, dokumentu lub elementu listy](https://support.office.com/en-ca/article/Manage-permissions-for-a-list-library-folder-document-or-list-item-9d13e7df-a770-4646-91ab-e3c117fcef45)<br /><br />[Stosowanie usługi Zarządzanie prawami do informacji w odniesieniu do listy lub biblioteki](http://office.microsoft.com/sharepoint-help/apply-information-rights-management-to-a-list-or-library-HA102891460.aspx)|
|Należy skonfigurować program SharePoint na potrzeby usługi IRM i bibliotek chronionych.|[Konfigurowanie usługi Zarządzanie prawami do informacji w centrum administracyjnym programu SharePoint](https://support.office.com/en-us/article/Set-up-Information-Rights-Management-IRM-in-SharePoint-admin-center-239ce6eb-4e81-42db-bf86-a01362fed65c)<br /><br />[Stosowanie usługi Zarządzanie prawami do informacji w odniesieniu do listy lub biblioteki](http://office.microsoft.com/sharepoint-help/apply-information-rights-management-to-a-list-or-library-HA102891460.aspx)|

### Aby skonfigurować ustawienia biblioteki programu SharePoint dla usługi IRM

1.  Po skonfigurowaniu programu SharePoint do korzystania z usługi IRM przejdź do biblioteki programu SharePoint, która ma być chroniona za pomocą usługi Azure RMS. Na stronie witryny **Ustawienia** &gt; **Zarządzanie prawami do informacji (IRM)** wybierz opcję **Ogranicz uprawnienia do tej biblioteki podczas pobierania**, określ tytuł zasad dla administratorów i opisy zasad dla użytkowników, a następnie kliknij przycisk **POKAŻ OPCJE**.

2.  Wybierz następujące opcje:

    -   **Nie zezwalaj użytkownikom na przekazywanie dokumentów nieobsługujących usługi IRM**

    -   Opcjonalnie: **Zezwalaj na ochronę grupy. Grupa domyślna** — podaj nazwę dodatkowej grupy, która może współpracować nad dokumentami przechowywanymi w tej bibliotece, ale poza programem SharePoint. Na przykład zespół sprzedaży ma uprawnienia do edycji w witrynie i członek tego zespołu pobiera dokument, zapisuje go na dysku i wysyła pocztą e-mail do współpracownika, który nie należy do zespołu sprzedaży. Jeśli współpracownik należy do grupy określonej w tym miejscu, automatycznie odziedziczy te same uprawnienia, które zostały skonfigurowane dla witryny, i będzie mógł edytować dokument.

        Bez tej opcji tylko użytkownicy, którzy mają dostęp do biblioteki programu SharePoint, będą mogli współpracować nad tymi dokumentami i to wyłącznie przez pobranie ich bezpośrednio z programu SharePoint. W wielu przypadkach to ograniczenie jest słuszne.

## Instrukcje w dokumentacji użytkownika
W tym scenariuszu nie ma żadnych przeznaczonych dla użytkowników instrukcji związanych z procedurami, ponieważ biblioteki chronione nie wymagają żadnych specjalnych działań ze strony użytkowników. Dokumenty są chronione automatycznie podczas pobierania zgodnie z uprawnieniami, które administrator programu SharePoint ustawi dla witryny. Należy jednak poinformować użytkowników o tej zmianie, aby wiedzieli, czego mogą się spodziewać. Natomiast dział pomocy technicznej powinien otrzymać informacje o tym, które biblioteki są chronione i jakim ograniczeniom podlega korzystanie z dokumentów. Na przykład ze względu na bieżące ograniczenia dokumenty mogą być wyświetlane, ale nie edytowane na urządzeniach przenośnych. Jeśli została skonfigurowana ochrona grupy, powiadom użytkowników, które grupy mają dostęp do dokumentów i mogą je edytować poza programem SharePoint.

Przy użyciu następującego szablonu skopiuj i wklej powiadomienie do wiadomości dla użytkowników końcowych i wprowadź poniższe zmiany, aby odzwierciedlić charakter lokalnego środowiska:

1.  Zastąp każde wystąpienie zmiennej *&lt;nazwa biblioteki programu SharePoint&gt;* nazwą i linkiem do biblioteki programu SharePoint skonfigurowanej dla usługi Azure Rights Management. Jeśli wiadomość ma dotyczyć kilku bibliotek chronionych, zmień odpowiednio instrukcje.

2.  Jeśli została skonfigurowana opcja **Zezwalaj na ochronę grupy. Grupa domyślna**, zastąp zmienną *&lt;nazwa grupy&gt;* nazwą skonfigurowanej grupy i podaj przyczynę &lt;przyczyna przyznania tej grupie uprawnień dostępu w celu współpracy nad plikami, ale nie przy użyciu biblioteki programu SharePoint&gt;. Jeśli ta opcja nie została skonfigurowana, usuń to zdanie.

3.  Zastąp *&lt;dane kontaktowe&gt;* instrukcjami dla użytkowników dotyczącymi sposobu kontaktowania się z działem pomocy technicznej, na przykład podaj link do witryny sieci Web, adres e-mail lub numer telefonu.

4.  Wprowadź dodatkowe zmiany, które chcesz uwzględnić w tym powiadomieniu, a następnie wyślij je do odpowiednich użytkowników.

W przykładowej dokumentacji przedstawiono, jak może wyglądać odpowiednio dostosowane zawiadomienie, które zobaczą użytkownicy.

![Dokumentacja użytkownika dotycząca szablonów na potrzeby szybkiego wdrażania usługi Azure RMS](../media/AzRMS_UsersBanner.png)

### Powiadomienie działu IT: zmiany w witrynie &lt;nazwa biblioteki programu SharePoint&gt;
Witryna programu SharePoint **&lt;nazwa biblioteki programu SharePoint&gt;** została skonfigurowana pod kątem bezpiecznej współpracy. Obecnie tylko członkowie grupy &lt;nazwa grupy&gt; mogą otwierać dokumenty z tej witryny, nawet jeśli zostaną one zapisane lokalnie lub przesłane pocztą e-mail do innej osoby. Wyjątek stanowi możliwość udostępniania tych dokumentów po ich pobraniu członkom grupy &lt;nazwa grupy&gt;, aby &lt;przyczyna przyznania tej grupie uprawnień dostępu w celu współpracy nad plikami, ale nie przy użyciu biblioteki programu SharePoint&gt;. Podczas edycji plików u góry dokumentu widoczny jest żółty baner informujący o tym, że dokument podlega ochronie, i określający osoby, które mają do niego dostęp.

Ta zmiana pomaga w zabezpieczeniu poufnych danych firmy przed dostępem osób niepowołanych. W przypadku uzyskiwania dostępu do dokumentów chronionych na urządzeniu przenośnym możesz je przeglądać, ale edycja jest możliwa wyłącznie na komputerze stacjonarnym.

Nie można przekazywać do witryny &lt;nazwa witryny programu SharePoint&gt; dokumentów, które nie obsługują bezpiecznej współpracy.

**Potrzebujesz pomocy?**

-   Skontaktuj się z działem pomocy technicznej: &lt;dane kontaktowe&gt;

### Przykładowa dokumentacja użytkownika
![Przykładowa dokumentacja użytkownika dotycząca szybkiego wdrażania usługi Azure RMS](../media/AzRMS_ExampleBanner.png)

#### Powiadomienie działu IT: zmiany w witrynie Prognozy i raporty dotyczące sprzedaży
Witryna programu SharePoint **Prognozy i raporty dotyczące sprzedaży** została skonfigurowana pod kątem bezpiecznej współpracy. Obecnie tylko członkowie naszego zespołu Sprzedaż i marketing mogą otwierać dokumenty z tej witryny, nawet jeśli zostaną one zapisane lokalnie lub przesłane pocztą e-mail do innej osoby. Wyjątek stanowi możliwość udostępniania tych dokumentów po ich pobraniu członkom zespołu Finanse, aby mogli wyodrębnić prognozowane wartości miesięczne. Podczas edycji plików u góry dokumentu widoczny jest żółty baner informujący o tym, że dokument podlega ochronie, i określający osoby, które mają do niego dostęp.

Ta zmiana pomaga w zabezpieczeniu poufnych danych firmy przed dostępem osób niepowołanych. W przypadku uzyskiwania dostępu do dokumentów chronionych na urządzeniu przenośnym możesz je przeglądać, ale edycja jest możliwa wyłącznie na komputerze stacjonarnym.

Nie można przekazywać do witryny Prognozy i raporty dotyczące sprzedaży dokumentów, które nie obsługują bezpiecznej współpracy.

**Potrzebujesz pomocy?**

-   Skontaktuj się z działem pomocy technicznej: pomoc_techniczna@vanarsdelltd.com




<!--HONumber=Jul16_HO3-->


