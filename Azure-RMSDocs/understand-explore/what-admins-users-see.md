---
title: "Co widzą administratorzy i użytkownicy? | Azure RMS"
description: 
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 06/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 013e0eb4-49a7-4e81-9e4d-f56c0ceb017f
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 7a9c8b531ec342e7d5daf0cbcacd6597a79e6a55
ms.openlocfilehash: 213d077a65abd5115b7e0491dfc9cd8145752b23


---


# Azure RMS w działaniu: co widzą administratorzy i użytkownicy

*Dotyczy usług: Azure Rights Management, Office 365*

W tym artykule przedstawiono kilka typowych przykładów opisujących, co administratorzy i użytkownicy mogą zobaczyć w usłudze Azure Rights Management (Azure RMS) i jak mogą chronić informacje poufne przy jej użyciu.

> [!NOTE]
> We wszystkich tych przykładach — jeśli usługa Azure RMS chroni dane — właściciel zawartości zachowuje pełen dostęp do danych (plików lub poczty e-mail), nawet jeśli zastosowana ochrona powoduje przyznanie uprawnień grupie, do której właściciel nie należy, lub nawet jeśli zastosowana ochrona ma datę wygaśnięcia.
>
> Podobnie dział IT ma zawsze dostęp bez ograniczeń do chronionych danych dzięki funkcji administratora usługi Rights Management, która umożliwia przyznawanie delegowanego dostępu wybranym autoryzowanym użytkowników lub usługom. Dodatkowo dział IT może śledzić i monitorować użycie danych objętych ochroną — na przykład, kto uzyskuje do nich dostęp i kiedy.

Inne zrzuty ekranu i filmy wideo przedstawiające działanie usług RMS można znaleźć w [blogu dotyczącym pakietu Enterprise Mobility i zabezpieczeń](https://blogs.technet.microsoft.com/enterprisemobility/?product=azure-rights-management-services).

## Aktywowanie i konfigurowanie usługi Rights Management
Mimo że usługę Azure RMS można aktywować i skonfigurować przy użyciu programu Windows PowerShell, najłatwiej wykonać te czynności w portalu zarządzania. Zaraz po aktywowaniu usługi dostępne są dwa szablony, które administratorzy i użytkownicy mogą wybrać, aby szybko i łatwo objąć pliki ochroną informacji. Można również tworzyć szablony niestandardowe z dodatkowymi opcjami i ustawieniami.

![CO WIDZĄ ADMINISTRATORZY W KROKU 1](../media/AzRMS_StoryboardActivate_small1.png)


**CO WIDZĄ ADMINISTRATORZY W KROKU 1:** do aktywowania usługi RMS można użyć centrum administracyjnego usługi Office 365 (pierwszy rysunek) lub klasycznego portalu Azure (drugi rysunek).<br /><br />Wystarczy jedno kliknięcie, aby aktywować usługę, i drugie, aby potwierdzić tę czynność, a ochrona informacji zostanie włączona dla administratorów i użytkowników w organizacji.

---

![CO WIDZĄ ADMINISTRATORZY W KROKU 2](../media/AzRMS_TemplatesPortal_small.png)

**CO WIDZĄ ADMINISTRATORZY W KROKU 2:** po aktywacji w organizacji zostają automatycznie udostępnione dwa szablony zasad praw. Jeden szablon jest tylko do odczytu — jego nazwa zawiera informację **Confidential View Only** (Poufne, tylko wyświetlanie). Drugi szablon jest do odczytu i modyfikowania — jego nazwa zawiera informację **Confidential** (Poufne).

Te szablony są stosowane do plików lub wiadomości e-mail i ograniczają dostęp do nich tylko do użytkowników w organizacji. Jest to bardzo szybki i łatwy sposób zapobiegania wyciekowi danych firmowych do osób spoza organizacji.

> [!TIP]
> Możesz łatwo rozpoznać te szablony domyślne, ponieważ są one automatycznie poprzedzone nazwą organizacji. W naszym przykładzie: **VanArsdel, Ltd**.

Jeśli nie chcesz, aby użytkownicy widzieli te szablony, lub jeśli chcesz tworzyć własne szablony, możesz wykonać te czynności w klasycznym portalu Azure. Jak pokazano na rysunku, kreator przeprowadza użytkownika przez proces tworzenia szablonu niestandardowego.

---

![CO WIDZĄ ADMINISTRATORZY W KROKU 3](../media/AzRMS_TemplatesSettings3.png)

**CO WIDZĄ ADMINISTRATORZY W KROKU 3:** dostęp w trybie offline, ustawienia wygaśnięcia i opcja natychmiastowego publikowania szablonu (tak, aby był widoczny w aplikacjach, które obsługują usługę Rights Management) to niektóre ustawienia konfiguracji dostępne w przypadku tworzenia własnych szablonów.

---

![CO WIDZĄ ADMINISTRATORZY W KROKU 4](../media/AzRMS_TemplatesPortal_ExplorerWord3.png)

**CO WIDZĄ ADMINISTRATORZY W KROKU 4:** w wyniku opublikowania tych szablonów użytkownicy mogą je teraz wybierać w aplikacjach, takich jak Eksplorator plików i Microsoft Word:

- Użytkownik może wybrać szablon domyślny **VanArsdel, Ltd — Confidential** (Poufny). Wówczas tylko pracownicy z organizacji VanArsdel będą mogli otwierać ten dokument i korzystać z niego, nawet jeśli później zostanie on wysłany pocztą e-mail do osób spoza organizacji lub zapisany w lokalizacji publicznej.

- Użytkownik może wybrać niestandardowy szablon utworzony przez administratora **Sales and Marketing – Read and Print Only** (Sprzedaż i marketing — tylko do odczytu i drukowania). Wówczas plik będzie chroniony nie tylko przed osobami spoza organizacji, ale dostęp zostanie również ograniczony do pracowników z działu sprzedaży i marketingu. Ponadto pracownicy ci nie mają pełnych praw do dokumentu — mogą go tylko odczytywać i drukować. Nie mogą na przykład modyfikować ani kopiować jego zawartości.

---

**Dodatkowe informacje dotyczące tego scenariusza:**

- Aby uzyskać instrukcje krok po kroku, zobacz [Aktywacja usługi Azure Rights Management](../deploy-use/activate-service.md) i [Konfigurowanie szablonów niestandardowych usługi Azure Rights Management](../deploy-use/configure-custom-templates.md).

- Aby ułatwić użytkownikom ochronę ważnych plików firmowych, zobacz [Ułatwienia dla użytkowników dotyczące ochrony plików za pomocą usługi Azure Rights Management](../deploy-use/help-users.md).

Następnie możesz zapoznać się z kilkoma przykładami opisującymi, jak administratorzy mogą stosować szablony do automatycznego konfigurowania ochrony informacji do plików i wiadomości e-mail.

## Automatyczna ochrona plików na serwerach plików z systemem Windows Server i infrastrukturą klasyfikacji plików

W tym przykładzie pokazano, jak za pomocą usługi Azure RMS można automatycznie chronić pliki na serwerach plików z co najmniej systemem Windows Server 2012, które skonfigurowano do używania infrastruktury struktury plików.

Istnieje wiele sposobów stosowania wartości klasyfikacji do plików. Można na przykład przeprowadzić inspekcję zawartości plików i odpowiednio zastosować wbudowane klasyfikacje, takie jak poufność i dane osobowe. W tym przykładzie administrator tworzy jednak niestandardową klasyfikację **Marketing**, która jest automatycznie stosowana do wszystkich dokumentów użytkownika zapisanych w folderze **Marketing Promotions** (Promocje marketingowe). Mimo że ten folder jest chroniony za pomocą uprawnień NTFS, które ograniczają dostęp do członków grupy Marketing, administrator wie, że te uprawnienia mogą zostać utracone, jeśli ktoś z tej grupy przeniesie pliki lub wyśle je pocztą e-mail. Następnie informacje w plikach mogą być używane przez nieautoryzowanych użytkowników.

![CO WIDZĄ ADMINISTRATORZY W KROKU 1](../media/AzRMS_FCI_ConnectorSmall.png)

**CO WIDZĄ ADMINISTRATORZY W KROKU 1:** administratorzy instalują i konfigurują łącznik usługi Rights Management (RMS), który działa jako przekaźnik między serwerami lokalnymi i usługą Azure RMS.

---

![CO WIDZĄ ADMINISTRATORZY W KROKU 2](../media/AzRMS_ExampleFCI_ConfigurationSmall.png)

**CO WIDZĄ ADMINISTRATORZY W KROKU 2:** na serwerze plików administrator konfiguruje zadania i reguły klasyfikacji, aby wszystkie pliki użytkownika w folderze **Marketing Promotions** były automatycznie klasyfikowane jako **Marketing** i chronione przy użyciu szyfrowania usługi RMS.

Administrator konfiguruje niestandardowy szablon usługi RMS, który został utworzony w naszym pierwszym przykładzie. Ten szablon ogranicza dostęp do członków działów sprzedaży i marketingu: **Sales and Marketing – Read and Print Only** (Sprzedaż i marketing — tylko do odczytu i drukowania).

W efekcie wszystkie dokumenty w tym folderze są automatycznie konfigurowane z klasyfikacją Marketing i chronione przy użyciu szablonu usługi RMS dotyczącego sprzedaży i marketingu.

---

![CO WIDZĄ ADMINISTRATORZY W KROKU 3](../media/AzRMS_FCI_EmailSmall.png)

**CO WIDZĄ ADMINISTRATORZY W KROKU 3:** w jaki sposób usługa RMS pomaga zapobiegać wyciekowi danych do osób, które nie powinny mieć dostępu do informacji ważnych ani poufnych:

- Janet z działu marketingu wysyła wiadomość e-mail z poufnym raportem z folderu promocji marketingowych. Ten raport zawiera opis nowych funkcji produktu oraz planów reklamowych i jest wysyłany na prośbę współpracownika przebywającego obecnie w podróży służbowej. Jednak Janet przez pomyłkę wysłała wiadomość e-mail do niewłaściwej osoby — nie zauważyła, że przypadkowo wybrała odbiorcę o podobnej nazwie w innej firmie.<br><br>
Odbiorca nie może odczytać poufnego raportu, ponieważ nie jest członkiem grupy Sprzedaż i marketing.

---

**Dodatkowe informacje dotyczące tego scenariusza:**

- Instrukcje krok po kroku można znaleźć w temacie [Wdrażanie łącznika usługi Azure Rights Management](../deploy-use/deploy-rms-connector.md).

## Automatyczna ochrona wiadomości e-mail przy użyciu usługi Exchange Online i zasad zapobiegania utracie danych

W poprzednim przykładzie pokazano, jak można automatycznie chronić pliki zawierające poufne informacje, ale co można zrobić, jeśli informacje znajdują się nie w pliku, ale w wiadomości e-mail? W takiej sytuacji stosowane są zasady ochrony przed utratą danych (DLP) usługi Exchange Online. Ich działanie polega na monitowaniu użytkowników o zastosowanie ochrony informacji (przy użyciu porad dotyczących zasad) albo jej automatycznym stosowaniu (przy użyciu reguł transportu).

W tym przykładzie administrator konfiguruje zasady, aby zapewnić zgodność organizacji z obowiązującymi w USA przepisami dotyczącymi ochrony danych osobowych. Może on również skonfigurować reguły dla innych regulacji dotyczących zgodności albo można zastosować niestandardowe reguły zdefiniowane przez użytkownika.

![CO WIDZĄ ADMINISTRATORZY W KROKU 1](../media/AzRMS_DLPExample1.png)

**CO WIDZĄ ADMINISTRATORZY W KROKU 1:** w centrum administracyjnym programu Exchange szablon programu Exchange o nazwie **Stany Zjednoczone — dane osobowe** jest używany przez administratora do tworzenia i konfigurowania nowej zasady DLP. Ten szablon wyszukuje w wiadomościach e-mail takie informacje jak numery ubezpieczenia społecznego i prawa jazdy.

Zasady są skonfigurowane tak, aby wiadomości e-mail, które zawierają te informacje i są wysyłane poza organizację, były automatycznie obejmowane ochroną praw przy użyciu szablonu usługi RMS, który ogranicza dostęp do tylko pracowników firmy.

W tym miejscu zasada jest skonfigurowana do korzystania z jednego z szablonów domyślnych **VanArsdel, Ltd — Confidential** z pierwszego przykładu. Można również zobaczyć, jak szablony do wyboru uwzględniają wszystkie utworzone przez użytkownika szablony niestandardowe, i zapoznać się z opcją **Nie przesyłaj dalej** specyficzną dla programu Exchange.

> [!NOTE]
> Jeśli wyświetlane opcje konfiguracji są nieco inne niż na ilustracji, może być konieczne wcześniejsze wybranie pozycji **Więcej opcji** podczas konfigurowania reguły. Następnie wybierz pozycję **Zmodyfikuj zabezpieczenia wiadomości**  >  **Zastosuj ochronę praw** i wybierz szablon usługi RMS.

---

![CO WIDZĄ ADMINISTRATORZY W KROKU 2](../media/AzRMS_DLPUnprotectedEmail_small.png)

**CO WIDZĄ UŻYTKOWNICY W KROKU 2:** kierownik ds. rekrutacji pisze wiadomość e-mail zawierającą numer ubezpieczenia społecznego ostatnio zatrudnionego pracownika. Następnie wysyła tę wiadomość e-mail do Sherrie w dziale kadr.

---

![CO WIDZĄ ADMINISTRATORZY W KROKU 3](../media/AzRMS_DLPProtectedEmail_small.png)

**CO WIDZĄ UŻYTKOWNICY W KROKU 3:** jeśli ta wiadomość e-mail jest wysyłana lub przesyłana dalej do osób spoza organizacji, zostanie zastosowana reguła DLP automatycznie chroniąca prawa.

Wiadomość e-mail jest szyfrowana w momencie opuszczenia infrastruktury organizacji tak, aby nie można było odczytać numeru ubezpieczenia społecznego podczas jej przesyłania ani w skrzynce odbiorczej odbiorcy. Odbiorca nie będzie mógł odczytać wiadomości, chyba że jest pracownikiem firmy VanArsdel.

---

**Dodatkowe informacje dotyczące tego scenariusza:**

-   Aby uzyskać więcej informacji na temat współdziałania usługi Azure RMS z usługą Exchange Online, zobacz sekcję [Exchange Online i Exchange Server](office-apps-services-support.md#exchange-online-and-exchange-server) w temacie [Jak aplikacje obsługują usługę Azure Rights Management](applications-support.md).

-   Instrukcje krok po kroku dotyczące konfigurowania usługi Exchange Online dla usługi Azure RMS można znaleźć w sekcji [Exchange Online: konfiguracja usługi IRM](../deploy-use/configure-office365.md#exchange-online-irm-configuration) w temacie [Konfigurowanie aplikacji usługi Azure Rights Management](../deploy-use/configure-applications.md).

## Automatyczna ochrona plików przy użyciu usługi SharePoint Online i bibliotek chronionych

W tej sekcji pokazano, jak łatwo chronić dokumenty przy użyciu usługi SharePoint Online i bibliotek chronionych.

W tym przykładzie administrator programu SharePoint w firmie Contoso utworzył dla każdego działu bibliotekę, która może być używana do centralnego przechowywania i wyewidencjonowywania dokumentów do edycji i kontroli wersji. Na przykład istnieje biblioteka działu sprzedaży, biblioteka działu marketing, biblioteka działu kadr itd. Nowy dokument przekazywany lub tworzony w jednej z tych chronionych bibliotek dziedziczy ochronę biblioteki (nie trzeba wybierać szablonu zasad praw). Dokument jest chroniony automatycznie i pozostaje chroniony nawet po przeniesieniu poza bibliotekę programu SharePoint.

![CO WIDZĄ ADMINISTRATORZY W KROKU 1](../media/AzRMS_StoryboardSPO_small1.png)

**CO WIDZĄ ADMINISTRATORZY W KROKU 1:** administrator włącza usługę Zarządzanie prawami do informacji dla witryny programu SharePoint.

---

![CO WIDZĄ ADMINISTRATORZY W KROKU 2](../media/AzRMS_StoryboardSPO_small2.png)

**CO WIDZĄ ADMINISTRATORZY W KROKU 2:** następnie administrator włącza usługę Rights Management w bibliotece. Mimo że dostępne są dodatkowe opcje, to proste ustawienie jest najczęściej wystarczające.

Dokumenty teraz pobierane z tej biblioteki są automatycznie chronione przez usługę Rights Management, ponieważ dziedziczą ochronę skonfigurowaną dla biblioteki.

---

![CO WIDZĄ ADMINISTRATORZY W KROKU 3](../media/AzRMS_StoryboardSPO_small3.png)

**CO WIDZĄ UŻYTKOWNICY W KROKU 3:** gdy pracownik działu sprzedaży wyewidencjonuje ten raport sprzedaży z biblioteki, na transparencie informacyjnym w górnej części wyraźnie widzi, że jest to chroniony dokument z ograniczonym dostępem.

Dokument pozostanie chroniony, nawet jeśli użytkownik zmieni jego nazwę, zapisze go w innej lokalizacji lub udostępni za pośrednictwem poczty e-mail. Niezależnie od tego, jaka jest nazwa pliku, gdzie jest przechowywany lub czy jest udostępniany za pośrednictwem poczty e-mail, tylko pracownicy działu sprzedaży mogą go odczytywać.

---

**Dodatkowe informacje dotyczące tego scenariusza:**

-   Aby uzyskać więcej informacji na temat współdziałania usługi Azure RMS z programem SharePoint, zobacz sekcję [SharePoint Online i SharePoint Server](office-apps-services-support.md#sharepoint-online-and-sharepoint-server) w temacie [Jak aplikacje obsługują usługę Azure Rights Management](applications-support.md).

-   Instrukcje krok po kroku dotyczące konfigurowania programu SharePoint na potrzeby usługi Azure RMS można znaleźć w sekcji [SharePoint Online i OneDrive dla Firm: konfiguracja usługi IRM](../deploy-use/configure-office365.md#sharepoint-online-and-onedrive-for-business-irm-configuration) w temacie [Konfigurowanie aplikacji usługi Azure Rights Management](../deploy-use/configure-applications.md).

## Użytkownicy bezpiecznie udostępniają załączniki użytkownikom mobilnym

W poprzednich przykładach pokazano, jak administratorzy mogą automatycznie stosować ochronę informacji w przypadku danych poufnych. Jednak w niektórych sytuacjach użytkownicy będą musieli samodzielnie zastosować tę ochronę. Na przykład jeśli użytkownicy współpracują z partnerami w innej organizacji, potrzebują niestandardowych uprawnień lub ustawień, które nie zostały zdefiniowane w szablonach, do zastosowania w doraźnych przypadkach, których nie opisano w poprzednich przykładach. W takich sytuacjach użytkownicy mogą zastosować szablony usługi RMS lub skonfigurować uprawnienia niestandardowe.

W tym przykładzie pokazano, jak użytkownicy mogą łatwo udostępnić dokument pracownikowi innej firmy, zachowując ochronę dokumentu i mając pewność, że odbiorca może go odczytać nawet na popularnym urządzeniu przenośnym. W tym scenariuszu jest używana aplikacja do udostępniania usługi Rights Management, którą można automatycznie wdrażać na komputerach z systemem Windows w organizacji. Użytkownicy mogą ją również instalować samodzielnie.

W tym przykładzie Alice z firmy Contoso wysyła pocztą e-mail poufny dokument programu Word do Boba w firmie Fabrikam. Bob odczytuje dokument na urządzeniu iPad, ale może równie łatwo odczytać go na urządzeniu iPhone, tablecie lub telefonie z systemem Android, komputerze Mac lub telefonie bądź komputerze z systemem Windows.

![CO UŻYTKOWNICY WIDZĄ W KROKU 1](../media/AzRMS_StoryboardEmail_small1.png)

**CO UŻYTKOWNICY WIDZĄ W KROKU 1:** na własnym komputerze z systemem Windows Alice tworzy standardową wiadomość e-mail i dołącza do niej dokument.

Na wstążce klika przycisk **Udostępnij chronione**, aby załadować okno dialogowe **udostępniania chronionej zawartości** z aplikacji do udostępniania usługi RMS.

Alice chce ograniczyć prawa do Boba do wyświetlania i edytowania dokumentu i nie chce, aby go kopiował lub drukował, więc wybiera opcję **RECENZENT — wyświetlanie i edytowanie**. Chce ona również otrzymywać wiadomość e-mail, gdy ktoś spróbuje otworzyć dokument, i mieć możliwość odwołania dokumentu później, wiedząc, że odwołanie zacznie obowiązywać natychmiast.

---

![CO UŻYTKOWNICY WIDZĄ W KROKU 2](../media/AzRMS_StoryboardEmail_small2.png)

**CO UŻYTKOWNICY WIDZĄ W KROKU 2:** Bob widzi wiadomość e-mail na urządzeniu iPad.

Oprócz wiadomości i załącznika od Alice Bob otrzymuje instrukcje, które wykonuje, aby utworzyć konto i zainstalować aplikację do udostępniania usługi RMS na urządzeniu iPad.

---

![CO UŻYTKOWNICY WIDZĄ W KROKU 3](../media/AzRMS_StoryboardEmail_small3.png)

**CO UŻYTKOWNICY WIDZĄ W KROKU 3:** Bob może teraz otworzyć załącznik. Jest najpierw proszony o zalogowanie się w celu potwierdzenia, że to on jest zamierzonym odbiorcą.

Gdy Bob wyświetla dokument, widzi również informacje o ograniczonym dostępie, które wskazują, że będzie mógł wyświetlać i edytować dokument, ale nie będzie mógł go skopiować ani wydrukować.

---

![CO UŻYTKOWNICY WIDZĄ W KROKU 4](../media/AzRMS_StoryboardEmail_small4.png)

**CO UŻYTKOWNICY WIDZĄ W KROKU 4:** Alice otrzymuje wiadomość e-mail informującą o tym, że Bob pomyślnie otworzył wysłany przez nią dokument oraz kiedy uzyskiwał dostęp do dokumentu.

Jeśli Bob prześle wiadomość e-mail z załącznikiem, zapisze ją w lokalizacji, do której mogą mieć dostęp inne osoby, lub jeśli wiadomość zostanie przechwycona w sieci, inne osoby nie będą mogły odczytać dokumentu.

---

**Dodatkowe informacje dotyczące tego scenariusza:**

- Instrukcje krok po kroku można znaleźć w sekcjach [Ochrona pliku udostępnionego pocztą e-mail](../rms-client/sharing-app-protect-by-email.md) oraz [Wyświetlanie i używanie chronionych plików](../rms-client/sharing-app-view-use-files.md) w dokumencie [Podręcznik użytkownika aplikacji do udostępniania usługi Rights Management](../rms-client/sharing-app-user-guide.md).

- Instrukcje krok po kroku dotyczące tego scenariusza można znaleźć w dokumencie [Samouczek szybkiego startu dla usługi Azure Rights Management](../get-started/quick-start-tutorial.md).

## Następne kroki

Skoro już znasz przykłady możliwości usługi Azure RMS, być może zechcesz się dowiedzieć, jak te czynności są wykonywane. Aby uzyskać informacje techniczne na temat działania usługi Azure RMS, zobacz artykuł [Jak działa usługa Azure RMS](how-does-it-work.md).



<!--HONumber=Jun16_HO4-->


