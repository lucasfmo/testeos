---
title: "Scenariusz — konfigurowanie folderów roboczych do stałej ochrony | Azure RMS"
description: 
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 05/20/2016
ms.topic: get-started-article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 1f189345-a69e-4bf5-8a45-eb0fe5bb542b
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 332e102cb27854314b93a71bfeae82a95c9a7812
ms.openlocfilehash: 35ad445e229eac3feeca5522a41b9e3b25fd1180


---

# Scenariusz — konfigurowanie folderów roboczych do stałej ochrony

*Dotyczy usług: Azure Rights Management, Office 365*

W tym scenariuszu i dodatkowej dokumentacji użytkownika usługa Azure Rights Management jest stosowana w celu zapewnienia stałej ochrony dokumentów pakietu Office w [folderach roboczych](https://technet.microsoft.com/library/dn265974.aspx). Foldery robocze korzystają z usługi roli dla serwerów plików z systemem Windows Server, co zapewnia spójny sposób dostępu użytkowników do plików roboczych z komputerów i urządzeń. Chociaż foldery robocze mają własne szyfrowanie w celu ochrony plików, tracimy tę ochronę, jeśli pliki są przenoszone poza środowisko folderów roboczych. Na przykład użytkownicy kopiują zsynchronizowane pliki i zapisują je do magazynu, który nie jest pod kontrolą działu IT, lub przesyłają pliki pocztą e-mail do innych osób.

Dodatkowa ochrona zapewniana przez usługę Azure Rights Management pomaga uniknąć przypadkowej utraty danych, zapobiegając wyświetlaniu plików przez osoby spoza organizacji. W tym celu można użyć jednego z wbudowanych domyślnych szablonów zasad praw dostępu. Jednak przed wdrożeniem tego scenariusza należy wziąć pod uwagę, czy użytkownicy mogą potrzebować legalnego udostępniania niektórych plików osobom spoza organizacji. Na przykład po zakończeniu pracy nad wstępnym cennikiem użytkownik może wysłać wiadomość e-mail z ostateczną wersją do klienta w innej organizacji. W przypadku użycia szablonu domyślnego usługi Rights Management dla folderów roboczych ten klient w innej organizacji nie mógłby przeczytać przesłanego dokumentu. Chcąc spełnić to wymaganie, można utworzyć szablon niestandardowy, który pozwala użytkownikom na zastosowanie nowych zasad praw dostępu do pliku, zastępując oryginalne ograniczenie, które pozwala wysyłać e-mail tylko do wszystkich pracowników.

> [!NOTE]
> W przypadku użycia szablonu niestandardowego, który opisano w tym scenariuszu, użytkownicy mogą co prawda celowo udostępniać pliki osobom, które nie zostały zdefiniowane w szablonie, jednak dodatkowa ochrona zastosowana przy użyciu usługi Azure Rights Management niesie wiele korzyści. Ta dodatkowa ochrona zapobiega przypadkowej utracie danych, jeśli zawartość zostanie przeniesiona poza granice folderów roboczych, ponieważ zawartość pozostaje chroniona przed nieautoryzowanymi użytkownikami zarówno w trakcie przechowywania, jak i przesyłania. Na przykład gdy użytkownik utraci urządzenie, na którym używa folderów roboczych, lub urządzenie to zostanie skradzione, lub synchronizowana zawartość jest przesyłana do urządzenia i z urządzenia przez niezabezpieczoną infrastrukturę.
> 
> Jeśli użytkownik udostępnia zawartość komuś w innej organizacji za pomocą funkcjonalności Udostępnianie chronionej zawartości z aplikacji do tworzenia i przetwarzania dokumentów chronionych usługami Rights Management, ten użytkownik zastępuje oryginalną ochronę własnymi zasadami ochrony. W rezultacie zawartość nadal jest chroniona przed nieautoryzowanym dostępem i tylko określone przez użytkownika osoby mogą uzyskać do niej dostęp.

Tę stałą ochronę można zastosować do wszystkich dokumentów pakietu Office w folderach roboczych użytkowników lub tylko do plików, które zawierają dane poufne lub mające duże znaczenie dla działalności firmy.

Podane tu instrukcje mają zastosowanie w następujących okolicznościach:

-   Pliki folderu roboczego, które chcesz chronić za pomocą stałej ochrony, są plikami pakietu Office. Te pliki mogą być chronione natywnie przez usługę Azure Right Management i nie trzeba zmieniać ich rozszerzenia nazwy pliku ani wymagać innego przepływu pracy przy ich otwieraniu.

-   Chcesz zastosować stałą ochronę do wszystkich plików pakietu Office w folderach roboczych użytkowników lub do wybranych plików, które zostały zidentyfikowane przy użyciu Infrastruktury klasyfikacji plików z Menedżera zasobów serwera plików w systemie Windows Server.

-   W przypadku plików, które muszą być udostępniane osobom nieokreślonym w szablonie zasad praw dostępu (na przykład użytkownikom z innej organizacji), użytkownicy muszą zastosować nowe zasady praw dostępu, aby zastąpić ochronę za pomocą oryginalnych zasad.

## Instrukcje dotyczące wdrażania
![Instrukcje dla administratora dotyczące szybkiego wdrażania usługi Azure RMS](../media/AzRMS_AdminBanner.png)

Przed przejściem do części dotyczącej dokumentacji użytkownika należy upewnić się, że zostały spełnione poniższe wymagania, i wykonać instrukcje zawarte w procedurach pomocniczych.

## Wymagania dotyczące tego scenariusza
Aby wykonać instrukcje dotyczące tego scenariusza, należy spełnić następujące wymagania:

|Wymaganie|Jeśli potrzebujesz dodatkowych informacji|
|---------------|--------------------------------|
|Usługa Azure Rights Management została aktywowana.|[Aktywacja usługi Azure Rights Management](https://technet.microsoft.com/library/jj658941.aspx)|
|Lokalne konta użytkowników usługi Active Directory, w tym ich adresy e-mail, zsynchronizowano z usługą Azure Active Directory lub Office 365. Jest to wymagane dla wszystkich użytkowników korzystających z folderów roboczych.|[Przygotowanie do wdrożenia usługi Azure Rights Management](https://technet.microsoft.com/library/jj585029.aspx)|
|Jeden z poniższych programów:<br /><br />– Aby użyć szablonu domyślnego dla wszystkich użytkowników, który nie zezwala użytkownikom na stosowanie nowych zasad praw dostępu: nie zarchiwizowano szablonu domyślnego **&lt;nazwa organizacji&gt; — poufne**.<br /><br />– Aby użyć szablonu niestandardowego, który jest odpowiedni dla użytkowników, kiedy chcą zastosować nowe zasady praw dostępu: postępuj zgodnie z instrukcjami, aby utworzyć szablon niestandardowy.|[Konfigurowanie szablonów niestandardowych usługi Azure Rights Management](https://technet.microsoft.com/library/dn642472.aspx)|
|Łącznik usługi Rights Management jest zainstalowany, autoryzowany dla komputera z systemem Windows Server i skonfigurowany dla roli **serwera infrastruktury FCI**.|[Wdrażanie łącznika usługi Azure Rights Management](https://technet.microsoft.com/library/dn375964.aspx)|
|Aplikacja do tworzenia i przetwarzania dokumentów chronionych usługami Rights Management została wdrożona na komputerach użytkowników z systemem Windows.|[Automatyczne wdrażanie aplikacji do udostępniania usługi Microsoft Rights Management](https://technet.microsoft.com/library/dn339003%28v=ws.10%29.aspx)|

### Konfigurowanie niestandardowego szablonu zasad praw dostępu, aby użytkownicy mogli udostępniać pliki folderów roboczych poza organizacją

1.  Zaloguj się do klasycznego portalu Azure i przejdź do szablonów usługi Azure Rights Management.

2.  Skopiuj szablon **&lt;nazwa organizacji&gt; — poufne** i podaj nazwę i opis dla tego scenariusza dotyczącego folderów roboczych. Sugerujemy następujące wartości:

    -   Nazwa: **Zawartość chroniona przez foldery robocze**

    -   Opis: **Ta zawartość jest chroniona przez foldery robocze, a dostęp do niej jest ograniczony tylko do pracowników firmy. Aby udostępnić tę zawartość osobom spoza organizacji, dołącz dokument do wiadomości e-mail i użyj funkcji Udostępnianie chronionej zawartości.**

3.  Na stronie **PRAWA**:

    -   Zmień istniejące prawa z **Niestandardowe** na **Współwłaściciel**.

4.  Na stronie **KONFIGUROWANIE**:

    -   Upewnij się opcja **STAN** ma wartość **PUBLIKUJ**

    -   W polach **nazwy i opisu** usuń wpisy dla języków, których nie używasz. Dla używanych języków zaktualizuj pola **NAZWA** i **OPIS**, aby odpowiadały nazwie i opisowi nadanym dla tego szablonu w danym języku.

5.  Zapisz szablon.

### Konfigurowanie folderów roboczych do stosowania stałej ochrony do plików pakietu Office

1.  Zaimplementuj foldery robocze dla użytkowników, aby lokalnie zapisane pliki były synchronizowane z folderem na serwerze plików, nazywanym *udziałem synchronizacji*. Udział synchronizacji na serwerze plików musi znajdować się na serwerze innym niż ten, na którym działa łącznik usługi Rights Management.

    To rozwiązanie wymaga usługi roli folderów roboczych w Menedżerze serwera dla roli Usługi plików i magazynowania. Serwer plików musi mieć system operacyjny Windows Server 2012 R2 lub nowszy i może działać lokalnie lub na maszynie wirtualnej w usłudze Azure. Aby uzyskać więcej informacji o folderach roboczych, zobacz temat [Foldery robocze — omówienie](https://technet.microsoft.com/library/dn265974.aspx).

    Instrukcje wdrożenia można znaleźć w temacie [Wdrażanie folderów roboczych](https://technet.microsoft.com/library/dn528861.aspx). Upewnij się, że wybrano wbudowane szyfrowanie (opcja **Szyfruj foldery robocze**), które zostanie zastosowane oprócz szyfrowania w usłudze Azure Rights Management. Ponadto:

    -   Po powiązaniu certyfikatu SSL na serwerze synchronizacji (krok 4): użyj polecenia netsh (zamiast konsoli zarządzania usługami IIS), aby powiązać certyfikat z interfejsem interfejs HTTPS domyślnej witryny sieci Web.

    -   Aby zapobiec otrzymywaniu przez użytkowników błędu konfiguracji folderów roboczych **Wystąpił problem podczas stosowania zasad zabezpieczeń** oraz uniknąć wymagania, że użytkownicy muszą mieć prawa administratora lokalnego na komputerach przyłączonych do domeny: użyj polecenia cmdlet [Set-SyncShare](https://technet.microsoft.com/library/dn296649%28v=wps.630%29.aspx) z parametrem PasswordAutolockExcludeDomain i określ nazwy domen, w których znajdują się te komputery (na przykład contoso.com).

2.  Aby ukończyć konfigurację łącznika usługi Rights Management:

    1.  Za pomocą Menedżera zasobów serwera plików utwórz zadanie zarządzania plikami identyfikujące folder udziału synchronizacji jako zakres.

    2.  Jako akcję wybierz **Szyfrowanie RMS**, a następnie wybierz szablon:

        -   Jeśli nie utworzono szablonu niestandardowego, ponieważ nie chcesz, aby użytkownicy mogli udostępniać pliki innym osobom spoza organizacji, wybierz nazwę szablonu **&lt;nazwa organizacji&gt; — poufne**, np. **VanArsdel, Ltd — poufne**.

        -   Jeśli przy użyciu poprzednich instrukcji został utworzony szablon niestandardowy, wybierz go. Na przykład **Zawartość chroniona przez foldery robocze**

    3.  Określ harmonogram, który zapewnia dużo czasu na zaszyfrowanie wszystkich plików pakietu Office przez usługę Azure Rights Management, i określ opcję **Uruchamiaj zadanie w sposób ciągły dla nowych plików**.

3.  Aby ręcznie przetestować tę konfigurację, upewnij się, że folder zawiera kilka plików pakietu Office, a następnie użyj opcji **Uruchom teraz zadanie zarządzania plikami**, a następnie wybierz opcję **Zaczekaj na zakończenie zadania**.

    Poczekaj na zamknięcie okna dialogowego **Uruchamianie zadania zarządzania plikami**, a następnie przejrzyj wyniki w raporcie, który zostanie automatycznie wyświetlony. Liczba plików w wybranym folderze powinna być widoczna w polu **Pliki**. Upewnij się, że pliki w wybranym folderze są teraz chronione przez usługę Azure Rights Management. Na przykład otwórz plik i upewnij się, że w górnej części dokumentu widzisz baner informacyjny z nazwą i opisem szablonu usługi Rights Management.

4.  Jeśli chcesz selektywnie chronić pliki za pomocą Infrastruktury klasyfikacji plików, skonfiguruj regułę klasyfikacji i harmonogram, a następnie zmodyfikuj zadanie zarządzania plikami, aby dołączyć tę właściwość klasyfikacji jako warunek.

## Instrukcje w dokumentacji użytkownika
Jeśli pliki, które są chronione za pomocą usługi Azure Rights Management, nie muszą być udostępniane osobom spoza organizacji, raczej nie trzeba udostępniać użytkownikom żadnych dodatkowych instrukcji oprócz tych dotyczących używania folderów roboczych. Pliki chronione za pomocą usługi Azure Rights Management i szablonu domyślnego mogą być zwyczajnie otwieranie przez użytkowników w pakiecie Office, a jedyną różnicą jest ewentualny monit o uwierzytelnienie oraz pasek informacyjny w górnej części dokumentu, z napisem, że w zawartości znajdują się zastrzeżone informacje przeznaczone tylko dla użytkowników wewnętrznych.

W przypadku skonfigurowania szablonu niestandardowego zgodnie opisem w tym scenariuszu użytkownicy będą widzieć na pasku informacji następujący opis szablonu: **Ta zawartość jest chroniona przez foldery robocze, a dostęp do niej jest ograniczony tylko do pracowników firmy. Aby udostępnić tę zawartość osobom spoza organizacji, dołącz dokument do wiadomości e-mail i użyj funkcji Udostępnianie chronionej zawartości**. Chociaż ten opis zawiera podsumowanie sposobu udostępniania plików poza organizacją, użytkownicy będą prawdopodobnie potrzebować szczegółowych instrukcji, szczególnie na początku. Aby kontynuować realizację tego scenariusza, skorzystaj z instrukcji dla administratorów i użytkowników końcowych z tematu [Scenariusz — udostępnianie plików pakietu Office użytkownikom z innej organizacji](scenario-share-office-file-externally.md).

> [!TIP]
> Jeśli zdecydujesz, aby nie używać szablonu niestandardowego opisanego w tych instrukcjach, ponieważ nie chcesz, aby użytkownicy mogli udostępniać te pliki poza organizację bez nadzoru działu IT, poinformuj dział pomocy technicznej, aby w przypadku uprawnionego wymagania udostępnienia, mogli je spełnić przy użyciu dowolnego mechanizmu najbardziej odpowiedniego dla firmy. Na przykład osoba, która jest [administratorem](https://technet.microsoft.com/library/mt147272.aspx) może zastosować do zawartości nowy szablon, który przyzna żądającemu użytkownikowi uprawnienia Pełna kontrola, aby ten użytkownik mógł następnie użyć funkcji Udostępnianie chronionej zawartości.
> 
> Jeśli po upływie pewnego czasu stwierdzisz, że istnieje wiele takich żądań, możesz zdecydować się na zdefiniowanie własnego niestandardowego szablonu w tym scenariuszu, który przyzna prawo Współwłaściciel tylko określonym użytkownikom (np. menedżerom lub pomocy technicznej), natomiast standardowi użytkownicy będą mieli przyznane prawa Współautor lub jakiekolwiek [prawa dostępu](https://technet.microsoft.com/library/mt169423.aspx) uznane przez Ciebie za odpowiednie.




<!--HONumber=Jul16_HO3-->


