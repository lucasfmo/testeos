---
title: Tworzenie, konfigurowanie i publikowanie szablonu niestandardowego | Azure RMS
description: 
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 07/15/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: d6e9aa0c-1694-4a53-8898-4939f31cc13f
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 5737594c679be0702761014425e104e5eade59f3
ms.openlocfilehash: c240502f2e88ec61bcbee6be778e77a0d5aee66b


---


# Tworzenie, konfigurowanie i publikowanie szablonu niestandardowego

*Dotyczy usług: Azure Rights Management, Office 365*


Istnieje możliwość tworzenia szablonów niestandardowych i zarządzania nimi w klasycznym portalu Azure. Można to zrobić bezpośrednio z poziomu klasycznego portalu Azure lub zarejestrować się w Centrum administracyjnym usługi Office 365 i wybrać polecenie **Zaawansowane funkcje** odnoszące się do usługi Rights Management, co spowoduje przejście do klasycznego portalu Azure.

Musisz być administratorem globalnym, aby tworzyć szablony i zarządzać nimi w klasycznym portalu Azure. Jeśli innym użytkownikom również przypisano rolę administratora globalnego usług Azure RMS, także oni mogą tworzyć szablony i zarządzać nimi, ale muszą używać programu [PowerShell](configure-templates-with-powershell.md). Więcej informacji można znaleźć w odpowiedzi na pytanie [Czy trzeba być administratorem globalnym, aby skonfigurować usługę Azure RMS, czy można to oddelegować do innych administratorów?](../get-started/faqs.md#do-you-need-to-be-a-global-admin-to-configure-azure-rms-or-can-i-delegate-to-other-administrators) 

Wykonując poniższe procedury, można tworzyć, konfigurować i publikować szablony niestandardowe dla usługi Rights Management.

## Tworzenie szablonu niestandardowego

1.  W zależności od tego, czy logowanie ma miejsce w Centrum administracyjnym usługi Office 365, czy też w klasycznym portalu Azure, wykonaj jedną z następujących czynności:

    -   Przejdź do [Centrum administracyjnego usługi Office 365](https://portal.office.com/):

        1.  W lewym okienku kliknij opcję **Ustawienia usługi**.

        2.  W sekcji **Ustawienia usługi** kliknij opcję **Rights Management**.

        3.  W sekcji **Ochrona informacji użytkownika** kliknij przycisk **Zarządzaj**.

        4.  W sekcji **Rights Management** kliknij opcję **Zaawansowane funkcje**.

            > [!NOTE]
            > Jeśli usługa Rights Management nie została jeszcze aktywowana, najpierw kliknij pozycję **Aktywuj** i potwierdź wybór. Aby uzyskać więcej informacji o aktywacji, zobacz [Aktywacja usługi Azure Rights Management](activate-service.md).
            > 
            > Jeśli opcja **Zaawansowane funkcje** nie została wcześniej kliknięta, po aktywowaniu usługi Rights Management postępuj zgodnie z wyświetlanymi na ekranie instrukcjami w celu uzyskania bezpłatnej subskrypcji Azure, która jest wymagana do uzyskania dostępu do klasycznego portalu Azure.

            Kliknięcie opcji **Zaawansowane funkcje** spowoduje załadowanie klasycznego portalu Azure, w którym można zarządzać usługą **RIGHTS MANAGEMENT** wykorzystywaną przez organizację w ramach usługi Azure Active Directory.

    -   W [klasycznym portalu Azure ](http://go.microsoft.com/fwlink/p/?LinkID=275081):

        1.  W okienku po lewej stronie kliknij opcję **ACTIVE DIRECTORY**.

        2.  Na stronie **Active Directory** kliknij opcję **RIGHTS MANAGEMENT**.

        3.  Wybierz katalog, aby zarządzać usługą Rights Management.

        4.  Jeśli usługa Rights Management nie została jeszcze aktywowana, należy kliknąć opcję **AKTYWUJ** i potwierdzić wybór.

            > [!NOTE]
            > Aby uzyskać więcej informacji o aktywacji, zobacz [Aktywacja usługi Azure Rights Management](activate-service.md).

2.  Tworzenie szablonu:

    -   Na stronie szybkiego startu **Rozpoczynanie pracy z usługą Azure Rights Management** w klasycznym portalu Azure kliknij opcję **Utwórz nowy szablon zasad praw**.

        Jeśli ta strona nie zostanie wyświetlona natychmiast po wykonaniu instrukcji dotyczących usługi Office 365, należy skorzystać z opisanych powyżej instrukcji dotyczących nawigacji dla klasycznego portalu Azure.

3.  Na stronie **Dodaj nowy szablon zasad praw** wybierz język, w jakim zostaną wprowadzone nazwa i opis szablonu, które będą widoczne dla użytkowników (w późniejszym czasie można dodać więcej języków). Następnie wprowadź unikatową nazwę, opis i kliknij przycisk Zakończ.

Na stronie szybkiego startu **Rozpoczynanie pracy z usługą Azure Rights Management** kliknij opcję **Zarządzaj szablonami zasad praw**. Nowo dodany szablon zostanie wyświetlony na liście szablonów ze statusem **Zarchiwizowany**. Na tym etapie szablon jest utworzony, ale nie jest skonfigurowany. Nie jest także widoczny dla użytkowników.

## Konfiguracja i publikacja szablonu niestandardowego

1.  Wybierz nowo utworzony szablon na stronie **SZABLONY** w klasycznym portalu Azure.

2.  Na stronie szybkiego startu **Szablon został dodany** kliknij w kroku 1 opcję **Rozpocznij**, opcję **Skonfiguruj uprawnienia dla użytkowników i grup** i opcję **ROZPOCZNIJ TERAZ** lub **DODAJ**, a następnie wybierz odpowiednich użytkowników i grupy, aby nadać im prawo do korzystania z zawartości chronionej przez nowy szablon.

    > [!NOTE]
    > Wybrani użytkownicy lub grupy muszą mieć adres e-mail. W środowisku produkcyjnym adres jest dostępny prawie zawsze, ale w prostym środowisku testowym może być konieczne dodanie adresów e-mail do kont użytkowników lub grup.

    Dobrą praktyką jest wykorzystywanie grup zamiast użytkowników — taka strategia upraszcza zarządzanie szablonami. W przypadku dostępności lokalnej usługi Active Directory, jeśli planowana jest synchronizacja do usługi Azure AD, można użyć grup zabezpieczeń lub grup dystrybucyjnych z obsługą wiadomości e-mail. Chcąc nadać prawa wszystkim użytkownikom w obrębie organizacji, łatwiej będzie skopiować jeden z szablonów domyślnych niż określać wiele grup. Aby uzyskać więcej informacji, zobacz [Kopiowanie szablonu](copy-template.md).

    > [!TIP]
    > Aby dodać użytkowników spoza organizacji („użytkowników zewnętrznych”) do szablonu, wybierz grupę z włączoną obsługą poczty, która zawiera kontakty z usługi Office 365 lub Exchange Online. Pozwoli to przypisać prawa do tych użytkowników w ten sam sposób, w jaki można przypisać prawa do użytkowników w danej organizacji. Na przykład można zapobiec edytowaniu cennika wysłanego do klientów przez tych klientów. Nie należy używać tej konfiguracji szablonu do ochrony wiadomości e-mail, jeśli użytkownicy spoza danej organizacji będą czytać chronione wiadomości e-mail za pomocą aplikacji Outlook Web App.
    > 
    > Ponadto w późniejszym czasie można dodać do szablonu użytkowników spoza organizacji, korzystając z [modułu Windows PowerShell dla usługi Azure Rights Management](install-powershell.md) oraz jednej z następujących metod:
    > 
    > -  **Można użyć obiektu definicji praw w celu aktualizacji szablonu**: w tym celu należy określić w obiekcie definicji praw zewnętrzne adresy e-mail i ich prawa, które zostaną następnie użyte w celu aktualizacji szablonu. Obiekt definicji praw określa się, używając polecenia cmdlet [New-AadrmRightsDefinition](https://msdn.microsoft.com/library/azure/dn727080.aspx) do utworzenia zmiennej. Zmienna zostaje następnie dostarczona do parametru -RightsDefinition za pomocą polecenia cmdlet [Set-AadrmTemplateProperty](https://msdn.microsoft.com/library/azure/dn727076.aspx) (w przypadku modyfikacji istniejącego szablonu). W przypadku dodawania użytkowników do istniejącego szablonu trzeba jednak także zdefiniować obiekty definicji praw dla grup istniejących w szablonie, a nie tylko dla nowych użytkowników zewnętrznych.
    > -  **Można wyeksportować szablon, dokonać jego edycji, a następnie zaimportować zaktualizowany szablon**: użyj polecenia cmdlet [Export-AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727078.aspx), aby wyeksportować szablon do pliku, który można edytować w celu dodania zewnętrznych adresów e-mail użytkowników i ich praw w odniesieniu do istniejących grup i praw. Następnie należy użyć polecenia cmdlet [Import-AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727077.aspx) w celu zaimportowania zmienionego szablonu z powrotem do usługi Azure RMS.

3.  Następnie należy kliknąć przycisk Dalej i przypisać jedno z wymienionych praw do wybranych użytkowników i grup.

    Więcej informacji na temat każdego z praw (także niestandardowych) można znaleźć w wyświetlanych opisach. Bardziej szczegółowe informacje są także dostępne w sekcji [Konfigurowanie praw użytkowania usługi Azure Rights Management](configure-usage-rights.md). Aplikacje obsługujące usługę RMS mogą jednak różnić się w zakresie sposobu wdrażania tych praw. Należy zapoznać się z ich dokumentacją i samodzielnie przeprowadzić testy z użyciem aplikacji wykorzystywanych przez użytkowników, aby sprawdzić zachowanie szablonów przed ich wdrożeniem dla użytkowników. Aby wyświetlić ten szablon na potrzeby testów tylko dla administratorów, należy ustawić go jako szablon dla działu (krok 6).

4.  W przypadku wybrania opcji **Niestandardowy** należy kliknąć przycisk Dalej, a następnie wybrać prawa niestandardowe.

    Choć można użyć dowolnej kombinacji dostępnych praw, w wybranych aplikacjach niektóre prawa mogą być zależne od innych. W takim przypadku system automatycznie zaznacza za użytkownika wszelkie prawa zależne.

    > [!TIP]
    > Należy rozważyć dodanie praw **Kopiuj i Wyodrębnij zawartość** i ich nadanie wybranym administratorom lub pełniącym inne role pracownikom, których obowiązki służbowe mogą wymagać od nich odzyskiwania informacji. Nadanie tych praw umożliwi wspomnianym użytkownikom wyłączenie w razie potrzeby ochrony dla plików i wiadomości e-mail, które będą chronione za pomocą tego szablonu. Możliwość wyłączania ochrony z poziomu szablonu zapewnia bardziej szczegółową kontrolę niż ta, na jaką pozwala funkcja użytkownika nadrzędnego.

5.  Kliknij przycisk Zakończ.

6.  Jeśli chcesz, aby szablon był widoczny tylko dla określonej grupy użytkowników przeglądających listę szablonów w aplikacjach, kliknij opcję **ZAKRES**, aby skonfigurować szablon jako szablon dla działu, a następnie kliknij opcję **ROZPOCZNIJ TERAZ**. W przeciwnym razie przejdź do kroku 9.

    Więcej informacji o szablonach dla działu: Domyślnie wszyscy użytkownicy katalogu Azure widzą wszystkie opublikowane szablony i mogą wybierać je z poziomu aplikacji, chcąc zabezpieczyć zawartość. Aby wybrane pozycje spośród opublikowanych szablonów były widoczne tylko dla określonych użytkowników, należy określić zakres szablonów dla tych użytkowników. Po wykonaniu tej czynności tylko wskazani użytkownicy będą mieć możliwość wyboru tych szablonów. Inni użytkownicy, którzy nie zostaną wskazani, nie zobaczą szablonów i, co za tym idzie, nie będą mogli ich wybrać. Ta technika pozwala ułatwić użytkownikom wybór prawidłowego szablonu, zwłaszcza w przypadku, gdy tworzone są szablony przeznaczone dla określonych grup lub działów. Użytkownicy widzą w takim przypadku tylko te szablony, które są przeznaczone dla nich.

    Można na przykład utworzyć przeznaczony dla działu kadr szablon, który nadaje uprawnienia Tylko do odczytu członkom działu finansowego. Dzięki temu omawiany szablon mogą zastosować tylko członkowie działu kadr, korzystając w tym celu z aplikacji do udostępniania usługi Rights Management. Zakres szablonu określa się poprzez powiązanie szablonu z grupą o wskazanym adresie e-mail, której nazwa brzmi HumanResources. Po wykonaniu tych czynności omawiany szablon mogą zobaczyć i zastosować wyłącznie członkowie tej grupy.

7.  Na stronie **WIDOCZNOŚĆ SZABLONU** należy wybrać użytkowników i grupy, w przypadku których możliwe będzie wyświetlenie i wybór szablonu z poziomu aplikacji z obsługą usług RMS. Jak przedtem, także i w tym przypadku dobrą praktyką jest użycie grupy zamiast użytkowników, przy czym zarówno dla użytkowników, jak i dla grup dostępne muszą być adresy e-mail.

8.  Kliknij przycisk Dalej i określ, czy niezbędna jest konfiguracja zgodności aplikacji dla szablonu dla działu. Jeśli tak, kliknij opcję **ZGODNOŚĆ APLIKACJI**, zaznacz pole wyboru i kliknij opcję **Zakończ**.

    Dlaczego może być konieczne skonfigurowanie zgodności aplikacji? Nie wszystkie aplikacje obsługują szablony dla działów. Aby możliwa była ich obsługa, przed pobraniem szablonów niezbędne jest uwierzytelnienie aplikacji w usłudze RMS. Zgodnie z domyślnym ustawieniem, w przypadku, gdy proces uwierzytelniania nie zostanie przeprowadzony, nie zostaną pobrane żadne szablony dla działów. Takie działanie można ominąć, wskazując wszystkie szablony dla działów jako te, które mają zostać pobrane; w tym celu należy skonfigurować zgodność aplikacji i zaznaczyć pole wyboru **Pokaż ten szablon wszystkim użytkownikom, gdy aplikacje nie obsługują tożsamości użytkownika**.

    Jeśli na przykład zgodność aplikacji nie zostanie skonfigurowana dla szablonu dla działu kadr omawianego w przytoczonym przykładzie, tylko użytkownicy z działu kadr zobaczą szablon podczas korzystania z aplikacji RMS sharing; szablonu dla działu nie zobaczy jednak żaden użytkownik korzystający z usługi Outlook Web Access (OWA) w systemie Exchange Server 2013, ponieważ usługa OWA systemu Exchange oraz protokół Exchange ActiveSync nie obsługują aktualnie szablonów dla działów. Jeśli to domyślne działanie zostanie wyłączone poprzez skonfigurowanie zgodności aplikacji, to choć tylko użytkownicy z działu kadr zobaczą szablon dla działu podczas korzystania z aplikacji RMS sharing, szablon dla działu będzie widoczny dla wszystkich użytkowników korzystających z usługi Outlook Web Access (OWA). Jeśli użytkownicy korzystają w ramach usługi Exchange Online z usługi OWA lub protokołu Exchange ActiveSync, są dwie możliwości: szablony dla działów będą widoczne dla wszystkich użytkowników lub nie będą widoczne dla żadnego z nich, zależnie od statusu szablonu (archiwalny lub opublikowany) w usłudze Exchange Online.

    Pakiet Office 2016 zapewnia natywną obsługę szablonów dla działów, podobnie jak pakiet Office 2013, począwszy od wersji 15.0.4727.1000, wydanej w czerwcu 2015 roku jako część pakietu [KB 3054853](https://support.microsoft.com/kb/3054853).

    > [!NOTE]
    > W przypadku aplikacji, które nie obsługują natywnie szablonów dla działów, można użyć skryptu pobierania szablonu niestandardowego usługi RMS lub innych narzędzi do wdrażania tych szablonów w ramach lokalnego folderu klienta usług RMS. Po wykonaniu tych czynności aplikacje będą poprawnie wyświetlać szablony dla działów, ale tylko w przypadku użytkowników i grup, które uwzględniono w zakresie szablonu:
    > 
    > -   W przypadku pakietu Office 2010 folderem klienta jest: **%localappdata%\Microsoft\DRM\Templates**.
    > -   Z komputera klienckiego, z użyciem którego pobrano wszystkie szablony, można skopiować pliki szablonów, a następnie wkleić je do innych komputerów.
    > 
    > Można [pobrać skrypt szablonu niestandardowego usługi RMS z witryny Microsoft Connect](http://go.microsoft.com/fwlink/?LinkId=524506). Jeśli po kliknięciu tego linku zostaje wyświetlony błąd, oznacza to, że użytkownik prawdopodobnie nie został zarejestrowany w witrynie Microsoft Connect. W celu przeprowadzenia rejestracji:
    > 
    > 1.  Przejdź do [witryny Microsoft Connect](http://www.connect.microsoft.com) i zaloguj się przy użyciu danych konta Microsoft.
    > 2.  Kliknij przycisk **Katalog**, a następnie wybierz kategorię **Wyświetl produkty Connect, które obecnie nie akceptują informacji zwrotnych**.
    > 3.  Wyszukaj **Usługi Rights Management** i kliknij dla programu **Funkcje produktu Microsoft RMS Enterprise** przycisk **Dołącz**.

9. Kliknij opcję **KONFIGURUJ** i dodaj dodatkowe języki używane przez użytkowników, a także nazwę i opis tego szablonu w danym języku. Jeśli z infrastruktury korzystają użytkownicy posługujący się wieloma językami, ważne jest, aby dodać wszystkie wykorzystywane przez użytkowników języki, a następnie wprowadzić nazwę i opis szablonu w każdym z języków. Użytkownicy widzą nazwę i opis szablonu w tym samym języku, jaki jest ustawiony w ich systemie operacyjnym klienta, co stanowi gwarancję, że będą oni w stanie zrozumieć zasady mające zastosowanie do dokumentów lub wiadomości e-mail. W przypadku braku dopasowania do języka używanego w systemie operacyjnym klienta nazwa i opis będą widoczne w języku zdefiniowanym przez użytkownika podczas pierwszego utworzenia szablonu.

    Następnie należy sprawdzić, czy nie jest konieczne wprowadzenie zmian w następujących ustawieniach:

    |Ustawienie|Więcej informacji|
    |-----------|--------------------|
    |**wygaśnięcie zawartości**|Należy określić dla danego szablonu datę lub liczbę dni, po upływie których nie będzie możliwe otwarcie plików chronionych za pomocą szablonu. Można określić datę lub wskazać liczbę dni, jakie muszą minąć począwszy od momentu objęcia pliku ochroną.<br /><br />W przypadku określenia daty ustawienie wchodzi w życie o północy czasu mającego zastosowanie w bieżącej strefie czasowej.|
    |**dostęp w trybie offline**|Użycie tego ustawienia umożliwia zrównoważenie wszelkich wymagań dotyczących zabezpieczeń z wymaganiem, aby użytkownicy byli w stanie otworzyć chronione pliki w sytuacji, gdy nie mają oni połączenia z Internetem.<br /><br />Jeśli wybrane zostanie ustawienie uniemożliwiające uzyskanie dostępu do zawartości w przypadku braku połączenia z Internetem lub ustawienie umożliwiające uzyskanie dostępu do zawartości jedynie w ciągu określonej liczby dni, po osiągnięciu progu użytkownicy muszą zostać ponownie uwierzytelnieni, a ich dostęp musi zostać zarejestrowany. Kiedy tak się stanie, w przypadku, gdy poświadczenia nie są buforowane, użytkownicy otrzymują przed otwarciem pliku monit o zalogowanie się.<br /><br />Poza ponownym uwierzytelnieniem następuje także ponowna ocena zasad i członkostwa w grupie użytkowników. Oznacza to, że użytkownicy mogą mieć różny poziom dostępu do tego samego pliku po wprowadzeniu zmian w zasadach lub w członkostwie grupy mającym miejsce po ich ostatnim uzyskaniu dostępu do pliku.|

10. Po upewnieniu się, że szablon jest prawidłowo skonfigurowany pod kątem użytkowników, kliknij przycisk **OPUBLIKUJ**, aby ustawić szablon jako widoczny dla użytkowników, a następnie kliknij przycisk **ZAPISZ**.

11. Kliknij przycisk Wstecz w klasycznym portalu, aby powrócić do strony **SZABLONY**, na której szablon powinien teraz figurować ze statusem **Opublikowany**.

Aby wprowadzić zmiany w szablonie, zaznacz go i ponownie wykonaj kroki ze strony szybkiego startu. Możesz także wybrać jedną z następujących opcji:

-   Aby dodać większą liczbę użytkowników i grup oraz zdefiniować uprawnienia dla tych użytkowników i grup: kliknij opcję **PRAWA**, a następnie kliknij opcję **DODAJ**.

-   Aby usunąć użytkowników lub grupy, które wcześniej wybrano: kliknij **PRAWA**, wybierz z listy użytkownika lub grupę, a następnie kliknij przycisk **USUŃ**.

-   Aby zmienić ustawienie widoczności szablonów, spośród których użytkownicy mogą wybierać z poziomu aplikacji: kliknij **ZAKRES**, następnie kliknij przycisk **DODAJ** lub **USUŃ** albo **ZGODNOŚĆ APLIKACJI**.

-   Aby wybrać ustawienie szablonu powodujące, że nie będzie on już widoczny dla wszystkich użytkowników: kliknij kolejno opcje **KONFIGURUJ** i **ARCHIWUM**, a następnie opcję **ZAPISZ**.

-   Aby wprowadzić inne zmiany w konfiguracji: kliknij opcję **KONFIGURUJ**, wprowadź zmiany, a następnie kliknij przycisk **ZAPISZ**.

> [!WARNING]
> Po wprowadzeniu zmian do szablonu, który został wcześniej zapisany, w przypadku klientów zmiany te nie będą widoczne w szablonie do czasu, gdy szablony zostaną odświeżone na komputerach klienckich. Aby uzyskać więcej informacji, zobacz [Odświeżanie szablonów dla użytkowników](refresh-templates.md).

## Zobacz też
[Konfigurowanie szablonów niestandardowych usługi Azure Rights Management](configure-custom-templates.md)


<!--HONumber=Jul16_HO3-->


