---
title: "Scenariusz — zabezpieczanie najbardziej wartościowych (kilku) plików | Azure RMS"
description: 
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 05/20/2016
ms.topic: get-started-article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 95f1844a-612c-4e67-bbe6-4b6b92295221
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 332e102cb27854314b93a71bfeae82a95c9a7812
ms.openlocfilehash: d4325fb8a0b27d0a8d4fd7451b9d11d10153ed8d


---

# Scenariusz — zabezpieczanie najbardziej wartościowych (kilku) plików

*Dotyczy usług: Azure Rights Management, Office 365*

W tym scenariuszu i dodatkowej dokumentacji użytkownika usługa Azure Rights Management jest używana w celu zastosowania ręcznej i niestandardowej ochrony grupy plików zidentyfikowanych jako najbardziej wartościowe, aby zagwarantować im najwyższy poziom ochrony przed nieupoważnionym dostępem. Są to zazwyczaj pliki, do których dostęp powinno mieć tylko kilka osób. Mogą one zawierać na przykład przepisy kulinarne na potrawy będące specjalnością firmy lub plany przejęcia, których nie można opublikować przed upływem określonego terminu.

Podane tu instrukcje mają zastosowanie w następujących okolicznościach:

-   Zidentyfikowano niewielki zestaw plików do objęcia ochroną.

-   Pliki mają jeden z formatów pakietu Office obsługujących usługę Rights Management. Jeśli pliki mają inne formaty (np. CAD), należy upewnić się, że te formaty obsługują usługę Azure RMS oraz że wdrożenie dotyczy aplikacji, które natywnie obsługują usługę Azure RMS. Aby uzyskać więcej informacji, zobacz [Jak aplikacje obsługują usługę Azure Rights Management](https://technet.microsoft.com/library/jj585004.aspx).

-   Pliki zawierają ściśle poufne informacje, do których dostęp powinno mieć tylko kilka osób.

-   Wymaganie połączenia internetowego do autoryzowania każdej indywidualnej operacji dostępu do pliku to dopuszczalne rozwiązanie dla tych osób, ponieważ zapewnia ono wyższy poziom zabezpieczeń.

-   Osoby te nie mają potrzeby udostępniania informacji kolejnym użytkownikom, ale mogą je modyfikować i zapisywać wprowadzone zmiany.

-   Administrator musi mieć możliwość śledzenia, kto uzyskuje dostęp do plików, oraz w razie potrzeby odwoływania praw dostępu.

## Instrukcje dotyczące wdrażania
![Instrukcje dla administratora dotyczące szybkiego wdrażania usługi Azure RMS](../media/AzRMS_AdminBanner.png)

Przed przejściem do części dotyczącej dokumentacji użytkownika należy upewnić się, że zostały spełnione poniższe wymagania, i wykonać instrukcje zawarte w procedurach pomocniczych.

## Wymagania dotyczące tego scenariusza
W przypadku tego scenariusza należy spełnić następujące wymagania:

|Wymaganie|Jeśli potrzebujesz dodatkowych informacji|
|---------------|--------------------------------|
|Zostały przygotowane konta i grupy dla usługi Office 365 lub Azure Active Directory:<br /><br />– Utworzono grupę z włączoną obsługą poczty o nazwie **Dostęp uprzywilejowany**, zawierającą kilka osób, które powinny mieć dostęp do ściśle poufnych dokumentów.<br /><br />– Utworzono grupę z włączoną obsługą poczty o nazwie **Menedżerowie ds. zgodności IT**, zawierającą osoby, których zadania obejmują zbieranie elektronicznych materiałów dowodowych, monitorowanie i przeprowadzanie inspekcji.<br /><br />– Utworzono grupę z włączoną obsługą poczty o nazwie **Administratorzy usługi RMS** i dodano do niej wszystkich administratorów, którzy będą konfigurować usługę Azure RMS.|[Przygotowanie do wdrożenia usługi Azure Rights Management](https://technet.microsoft.com/library/jj585029.aspx)|
|Usługa Azure Rights Management została aktywowana.|[Aktywacja usługi Azure Rights Management](https://technet.microsoft.com/library/jj658941.aspx)|
|Skonfigurowano szablon niestandardowy zgodnie z poniższym opisem.|[Konfigurowanie szablonów niestandardowych usługi Azure Rights Management](https://technet.microsoft.com/library/dn642472.aspx)|
|Aplikacja do tworzenia i przetwarzania dokumentów chronionych usługami Microsoft Rights Management została wdrożona na komputerze z systemem Windows, dlatego można objąć te pliki ochroną miejscową zgodnie z opisem w następnej sekcji.|[Pobieranie i instalowanie aplikacji do udostępniania usługi Microsoft Rights Management](https://technet.microsoft.com/library/dn574734%28v=ws.10%29.aspx)|
|Upoważnieni użytkownicy mają pakiet Office w wersji 2013 lub nowszy.|Użytkownicy, którzy mają pakiet Office 2010, muszą również zainstalować aplikację do tworzenia i przetwarzania dokumentów chronionych usługami Rights Management.|
|Twoja subskrypcja usługi Azure RMS obejmuje śledzenie dokumentów.|Jeśli subskrypcja usługi Azure RMS nie obejmuje śledzenia dokumentów i odwoływania praw dostępu, nie będzie można korzystać z witryny śledzenia dokumentów w celu sprawdzenia, kto uzyskuje dostęp do tych dokumentów, ani w razie potrzeby odwołać praw dostępu. W takim przypadku należy kupić subskrypcję, która obsługuje śledzenie dokumentów, lub zaakceptować to ograniczenie. Można także rozważyć skorzystanie z możliwości [rejestrowania użycia](https://technet.microsoft.com/library/dn529121.aspx) w usłudze Azure RMS. Dzięki tej funkcji można sprawdzić, kto i kiedy uzyskiwał dostęp do poszczególnych plików, co ułatwia wykrywanie potencjalnie podejrzanego zachowania.<br /><br />Aby sprawdzić swoją subskrypcję, zobacz temat [Comparison of Rights Management Services (RMS) Offerings](https://technet.microsoft.com/dn858608) (Porównanie ofert usługi Rights Management (RMS)).|

### Aby skonfigurować szablon niestandardowy

1.  W klasycznym portalu Azure: utwórz nowy szablon niestandardowy usługi Azure Rights Management, który zawiera następujące wartości i ustawienia:

    -   Nazwa: **Dostęp uprzywilejowany**.

    -   Prawa: udziel grupie **Dostęp uprzywilejowany** z włączoną obsługą poczty praw **Współautor**.

    -   Zakres: wybierz grupę **Dostęp uprzywilejowany** z włączoną obsługą poczty, grupę **Menedżerowie zgodności IT** z włączoną obsługą poczty oraz grupę **Administratorzy usługi RMS** z włączoną obsługą poczty.

    -   Dostęp w trybie offline: **Zawartość jest dostępna tylko w przypadku połączenia internetowego**.

2.  Opublikuj nowy szablon.

### Aby objąć pliki ochroną miejscową

1.  W Eksploratorze plików przejdź do pierwszego folderu zawierającego pliki do objęcia ochroną:

    -   Jeśli chcesz objąć ochroną wszystkie pliki w folderze, wybierz ten folder.

    -   Jeśli chcesz objąć ochroną tylko niektóre pliki w folderze, wybierz jednocześnie te pliki.

2.  Kliknij prawym przyciskiem myszy, wybierz pozycję **Chroń za pomocą usługi RMS**, a następnie wybierz pozycję **Włącz ochronę miejscową**.

3.  Wybierz pozycję **Dostęp uprzywilejowany**

4.  Może zostać wyświetlony monit o podanie poświadczeń. Poczekaj na włączenie ochrony plików, a następnie kliknij pozycję **Zamknij** po wyświetleniu strony **chronionych plików**.

5.  Jeśli chcesz objąć ochroną więcej plików w innych folderach, powtórz kroki od 1 do 4 dla każdego folderu.

Aby uzyskać więcej informacji na temat ochrony miejscowej plików, zobacz [Protect a file on a device (protect in-place) by using the Rights Management sharing application](https://technet.microsoft.com/library/dn574733%28v=ws.10%29.aspx) (Ochrona pliku na urządzeniu (ochrona miejscowa) za pomocą aplikacji do tworzenia i przetwarzania dokumentów chronionych usługami Rights Management).

> [!TIP]
> Jeśli liczba plików do objęcia ochroną jest zbyt duża, aby można było wykonać ten ręczny proces, należy rozważyć użycie [narzędzia ochrony usług RMS](https://www.microsoft.com/en-us/download/details.aspx?id=47256) w celu zbiorczego objęcia plików ochroną plików przy użyciu szablonu.

### Aby monitorować i w razie potrzeby odwołać prawa dostępu do plików

1.  W Eksploratorze plików kliknij chroniony plik prawym przyciskiem myszy, wybierz pozycję **Chroń za pomocą usługi RMS**, a następnie wybierz pozycję **Śledź użycie**.

2.  Po wyświetleniu monitu zaloguj się, aby uzyskać dostęp do witryny śledzenia dokumentów.

3.  Sprawdź, kto uzyskiwał dostęp do pliku i innych chronionych plików, ze szczególnym uwzględnieniem nieudanych prób wskazujących na podejrzane zachowanie. Jeśli uważasz to za właściwe, możesz odwołać prawa dostępu do poszczególnych plików.

## Instrukcje w dokumentacji użytkownika
W tym scenariuszu nie ma żadnych instrukcji przeznaczonych dla użytkowników, ponieważ te pliki nie wymagają specjalnych działań ze strony użytkowników. Pliki są chronione przez Ciebie i Ty będziesz je monitorować. Być może trzeba będzie jednak poinformować użytkowników i inne kanały pomocy technicznej o tym, które pliki są chronione i jak może to ograniczyć użycie tych dokumentów. Jeśli na przykład upoważniony użytkownik nie ma połączenia internetowego, nie będzie mógł otworzyć pliku.

Przy użyciu następującego szablonu skopiuj i wklej zawiadomienie do wiadomości dla użytkowników końcowych i wprowadź poniższe zmiany:

1.  Podaj rzeczywiste nazwy plików lub użyj czytelnego odwołania, które będzie zrozumiałe dla upoważnionych użytkowników.

2.  Zastąp wartość *&lt;dane kontaktowe&gt;* instrukcjami dla użytkowników dotyczącymi sposobu kontaktowania się z pomocą techniczną lub działem IT za pośrednictwem eskalowanego kanału pomocy technicznej, który odpowiada ważności tych dokumentów. Na przykład można podać całodobowy numer telefonu pomocy technicznej, pod którym przyjmowane są zgłoszenia o dużej ważności.

3.  Wprowadź inne potrzebne zmiany w tym zawiadomieniu, a następnie wyślij je do odpowiednich użytkowników.

W przykładowej dokumentacji przedstawiono, jak może wyglądać odpowiednio dostosowane zawiadomienie, które zobaczą użytkownicy.

![Szablon dokumentacji użytkownika na potrzeby szybkiego wdrażania usługi Azure RMS](../media/AzRMS_UsersBanner.png)

### Zawiadomienie działu IT: ochrona ściśle poufnych dokumentów organizacji &lt;nazwa organizacji&gt;.
Poniższe pliki zostały teraz objęte ochroną na bardzo wysokim poziomie, dzięki czemu tylko &lt;wybrani użytkownicy&gt; mogą korzystać z tych plików i je modyfikować. Aby lepiej chronić pliki przed nieautoryzowanym dostępem, aplikacja będzie automatycznie żądać autoryzacji zawsze przy ich otwieraniu, dlatego w przypadku pracy z poniższymi plikami niezbędne jest połączenie internetowe i może zostać wyświetlony monit o podanie poświadczeń:

-   &lt;ściśle tajny dokument, typ lub lokalizacja 1&gt;

-   &lt;ściśle tajny dokument, typ lub lokalizacja 2&gt;

-   &lt;ściśle tajny dokument, typ lub lokalizacja 3&gt;

**Potrzebujesz pomocy?**

-   Jeśli nie masz dostępu do tych plików lub w przypadku zauważenia podejrzanych zmian w plikach, &lt;czynność oraz szczegóły kontaktu&gt;.

#### Przykładowa niestandardowa dokumentacja użytkownika
![Przykładowa dokumentacja użytkownika na potrzeby szybkiego wdrażania usługi Azure RMS](../media/AzRMS_ExampleBanner.png)

##### Zawiadomienie działu IT: ochrona ściśle poufnych dokumentów organizacji VanArsdel
Poniższe pliki zostały teraz objęte ochroną na bardzo wysokim poziomie, dzięki czemu tylko osoby wymienione w wierszu Do tej wiadomości e-mail mogą korzystać z tych plików i je modyfikować. Aby lepiej chronić pliki przed nieautoryzowanym dostępem, aplikacja będzie automatycznie żądać autoryzacji zawsze przy ich otwieraniu, dlatego w przypadku pracy z poniższymi plikami niezbędne jest połączenie internetowe i może zostać wyświetlony monit o podanie poświadczeń:

-   Specyfikacje projektu o nazwie kodowej „Merkury”

-   Specyfikacje projektu o nazwie kodowej „Jupiter”

-   Specyfikacje projektu o nazwie kodowej „Saturn”

-   Specyfikacje projektu o nazwie kodowej „Neptun”

**Potrzebujesz pomocy?**

-   Jeśli nie masz dostępu do tych plików lub jeśli zauważysz w nich podejrzane zmiany, zadzwoń do całodobowej linii eskalacji problemów pomocy technicznej. Jej numer znajduje się w chronionej wiadomości e-mail wysłanej przez dział IT.




<!--HONumber=Jul16_HO3-->


