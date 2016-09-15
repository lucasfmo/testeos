---
title: "Szybkie wdrażanie usługi Azure Rights Management | Azure RMS"
description: 
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: c994d616-cff6-4930-9228-a7f7d198a160
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ed50d87138c428fadfd22cd5b3ef3c7f7e421848
ms.openlocfilehash: 01c2436218e0d7fd80a31cdc037d9dc8933e42f2


---

# Szybkie wdrażanie usługi Azure Rights Management

*Dotyczy usług: Azure Rights Management, Office 365*

Ten przewodnik udostępnia listę określonych scenariuszy implementacji. Użyj tego przewodnika oraz informacji dotyczących konfiguracji zawartych w sekcji **Wdrażanie i używanie**, aby szybciej wdrożyć usługę Azure Rights Management (Azure RMS) i korzystać z niej.

Opisane scenariusze zawierają zarówno instrukcje dla administratora, jak i dokumentację użytkownika końcowego. Przed przekazaniem tej dokumentacji (w postaci instrukcji lub anonsów) użytkownikom końcowym należy dostosować ją do określonych wymagań biznesowych oraz istniejących przepływów pracy. W przykładowym zestawie instrukcji lub anonsie pokazano, jak może wyglądać końcowa wersja dokumentacji dla użytkowników końcowych.

Każdy scenariusz zawiera listę wymagań z linkami prowadzącymi do dodatkowych informacji, co pozwala niezależnie wdrożyć te rozwiązania w dowolnej kolejności.

W tym artykule zawarto przykładowe, najpopularniejsze scenariusze. Usługa Azure RMS może służyć do ochrony informacji w wielu scenariuszach zarówno wewnątrz jednej organizacji, jak i między różnymi organizacjami, dlatego można użyć tego samego modelu do zdefiniowania własnych scenariuszy i wdrożenia ich w środowisku oraz na komputerach użytkowników. Skupienie się na konkretnych scenariuszach pozwala na dokładniejsze dopasowanie wdrożenia usługi Azure RMS do celów biznesowych. Ponadto wiemy z doświadczenia, że użytkownicy często wykonują instrukcje specyficzne dla scenariusza bardziej ściśle i systematycznie niż w przypadku ogólnych wytycznych, na przykład „należy chronić poufne dokumenty”.

Przed wdrożeniem opisanych rozwiązań warto wysłać do użytkowników końcowych obszerne powiadomienie o planowanych modyfikacjach mających na celu ochronę danych firmy wraz z informacją o ewentualnej konieczności wprowadzenia zmian w sposobie pracy. Treść takiej przykładowej komunikacji zamieszczono pod poniższą tabelą.

> [!NOTE]
> Jeśli masz pytania lub uwagi dotyczące tego przewodnika, skorzystaj z elementów umożliwiających przekazanie opinii, dostępnych na tej stronie, lub wyślij wiadomość e-mail na adres [AskIPTeam@Microsoft.com](mailto:%20askipteam@microsoft.com?subject=Rapid%20Deployment%20Guide%20feedback).

## Scenariusze dotyczące usługi Azure RMS
Aby szybciej wdrożyć usługę Azure RMS w celu rozwiązania określonych problemów w firmie, należy wybrać scenariusze, które najlepiej pasują do celów biznesowych, i w razie potrzeby dostosować je.



**Bezpieczne wysyłanie plików pakietu Office pocztą e-mail do użytkowników z innej organizacji oraz możliwość śledzenia wynikowych operacji dostępu (współpraca między firmami)**

Przykłady:

- Wysyłanie cennika, przewodnika lub planów wprowadzenia produktu do klienta

- Wysyłanie zlecenia roboczego lub specyfikacji marketingowej do dostawcy

- Wysyłanie oferty przetargowej lub zapytania ofertowego do partnera

Patrz [Scenariusz — udostępnianie plików pakietu Office użytkownikom z innej organizacji](scenario-share-office-file-externally.md)

**Zachowywanie kontroli nad dokumentami przechowywanymi w bibliotece programu SharePoint**

Przykłady:

- Wydziałowe arkusze kalkulacyjne i raporty

- Współpraca między zespołami dotycząca dokumentów projektowych lub innych materiałów

Patrz [Scenariusz — zachowanie kontroli nad dokumentami przechowywanymi w programie SharePoint](scenario-sharepoint.md)

**Przedstawiciele kadry kierowniczej mogą bezpiecznie wymieniać zastrzeżone informacje za pośrednictwem poczty e-mail**

Przykłady:

- Udostępnianie planów przejęcia

- Omawianie zagadnień prawnych lub rozpowszechnianie informacji dotyczących kwestii prawnych

- Informacje dotyczące potencjalnej redukcji zatrudnienia lub innych poufnych tematów

Patrz [Scenariusz — bezpieczna wymiana zastrzeżonych informacji przez przedstawicieli kadry kierowniczej](scenario-executives-email.md)

**Automatyczna ochrona wszystkich plików na serwerze plików**

Przykłady:

- Dokumenty programów CAD, które muszą być przechowywane w zasobach firmowych ze względu na własność intelektualną

- Plany promocji marketingowych i daty, które muszą być trzymane w tajemnicy w celu zachowania przewagi konkurencyjnej

Patrz [Scenariusz — ochrona plików w udziale serwera plików](scenario-fci.md)

**Ścisła ochrona najbardziej poufnych dokumentów mających duże znaczenie biznesowe**

Przykłady:

- Informacje dotyczące unikatowych przepisów lub formuł, które są własnością firmy

- Ściśle tajne plany przejęcia lub fuzji

- Dane dotyczące poszukiwania zasobów naturalnych

Patrz [Scenariusz — zabezpieczanie &#40;kilku&#41; najcenniejszych plików](scenario-secure-most-valuable-files.md)

**Bezpieczne wysyłanie wiadomości e-mail i załączników zawierających poufne dane firmy**

Przykłady:

- Szczegóły dotyczące wizji firmy

- Schematy organizacyjne, wiadomości dotyczące reorganizacji lub powiadomienia o promocjach

- Informacje o zasadach firmy

Patrz [Scenariusz — wysyłanie wiadomości e-mail zawierających poufne dane firmy](scenario-company-confidential-email.md)

**Stosowanie stałej ochrony plików pakietu Office w folderach roboczych**

Przykłady:

- Lokalnie edytowane dokumenty programu Word dotyczące poufnego projektu firmowego

- Lokalnie tworzone arkusze kalkulacyjne zawierające poufne dane lub informacje o dużym znaczeniu biznesowym

- Lokalnie przechowywane robocze wersje prezentacji programu PowerPoint, które nie mogą zostać ujawnione lub przypadkowo udostępnione osobom spoza organizacji do momentu utworzenia końcowych wersji prezentacji

Patrz [Scenariusz — konfigurowanie folderów roboczych do stałej ochrony](scenario-work-folders.md)




## Powiadomienie dla użytkowników przed wdrożeniem
Można użyć następującego przykładowego komunikatu, aby dać znać użytkownikom, że wdrożenie usługi Azure RMS oznacza wprowadzenie pewnych zmian. Przedstawiciel kadry kierowniczej organizacji, najlepiej dyrektor generalny, powinien skopiować poniższy tekst i wysłać go pocztą e-mail do wszystkich użytkowników. W tekście można wprowadzać zmiany, tak aby lepiej dopasować go do potrzeb użytkowników i uwarunkowań występujących w organizacji.

![Transparent przykładowej dokumentacji użytkownika dotyczącej szybkiego wdrażania usługi Azure RMS](../media/AzRMS_ExampleBanner.png)

### Wprowadzamy zmiany, aby chronić nasze dane
Czy zdarzyło Ci się wysłać kontrahentowi dokument przez pomyłkę? Czy chcesz mieć możliwość zablokowania dostępu do takiego dokumentu? Czy zdarzyło Ci się zastanawiać, jak można ustalić, którzy klienci przeczytali najnowsze informacje o produkcie? Czy musisz udostępniać poufne informacje o produktach, ale nie chcesz się martwić tym, że mogą one trafić do osób, które nie powinny ich zobaczyć?

Już wkrótce będzie można korzystać z tych możliwości. W ramach rozwiązania ochrony danych w przedsiębiorstwie nasz dział IT wprowadza pewne zmiany związane z wdrożeniem usługi Microsoft Azure Rights Management (Azure RMS). Wiele nowych rozwiązań spowoduje automatyczne zastosowanie potrzebnych zabezpieczeń bez potrzeby wykonywania dodatkowych czynności z Twojej strony. Jednak niektóre zmiany wymagają, aby inaczej wykonywać pewne czynności. W takim przypadku otrzymasz odpowiednie informacje i instrukcje od działu IT. W razie pytań lub problemów możesz również uzyskać wsparcie w dziale pomocy technicznej.

Na przykład za pomocą witryny śledzenia dokumentów można śledzić udostępniane dokumenty (i w razie potrzeby odwoływać dostęp do nich):

![Zrzuty ekranu przedstawiające śledzenie dokumentów w usłudze Azure RMS](../media/AzRMS_Tutorial_5_Screenshots.png)

Aby zobaczyć, jak to działa, obejrzyj 2-minutowy film wideo: [Śledzenie dokumentów i odwoływanie dostępu do nich w usłudze Azure RMS](https://channel9.msdn.com/Series/Information-Protection/Azure-RMS-Document-Tracking-and-Revocation)

Jednym z najcenniejszych zasobów naszej organizacji są dane. Tworzymy je, przechowujemy i korzystamy z nich w codziennej pracy. Dostęp do danych zapewnia nam przewagę konkurencyjną i pozwala odnosić sukcesy. Dlatego tak ważne jest zachowanie kontroli nad danymi i poczucie pewności, że niepowołane osoby nie mają do nich dostępu.

Rozwiązania, które wdrażamy, pomogą nam chronić nasze cenne zasoby i pozwolą korzystać z narzędzi umożliwiających sprawowanie kontroli nad danymi. Dziękujemy za Twoją współpracę podczas wprowadzania opisanych zmian.




<!--HONumber=Jun16_HO4-->


