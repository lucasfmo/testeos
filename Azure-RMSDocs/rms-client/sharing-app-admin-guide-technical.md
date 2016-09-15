---
title: "Przegląd techniczny aplikacji do udostępniania usługi Rights Management | Azure RMS"
description: 
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 07/15/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: f7b13fa4-4f8e-489a-ba46-713d7a79f901
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 09effc3dfb238370563981defdcf3c3b4cffcaae
ms.openlocfilehash: 2f249996b9b912f744754357423a0c4f134ec094


---


# Przegląd techniczny i szczegółowe informacje o ochronie aplikacji do udostępniania usługi Microsoft Rights Management

*Dotyczy: Active Directory Rights Management, Azure Rights Management, Windows 10, Windows 7 z dodatkiem SP1, Windows 8, Windows 8.1*


Aplikacja do udostępniania usługi Microsoft Rights Management to opcjonalna aplikacja do pobrania dla systemu Microsoft Windows i innych platform, która zapewnia następujące korzyści:

-   Ochrona pojedynczego pliku lub masowa ochrona wielu plików, a także wszystkich plików w wybranym folderze.

-   Pełna obsługa ochrony dowolnego typu pliku oraz wbudowana przeglądarka dla często używanych typów plików tekstowych i obrazów.

-   Ogólna ochrona plików, które nie obsługują ochrony usług RMS.

-   Pełne współdziałanie z plikami chronionymi za pomocą usługi Zarządzanie prawami do informacji pakietu Office.

-   Pełne współdziałanie z plikami PDF chronionymi przy użyciu infrastruktury klasyfikacji plików (FCI, File Classification Infrastructure) i obsługiwanymi narzędziami do tworzenia plików PDF.

Aplikacja do udostępniania usługi Microsoft Rights Management używa nowego [środowiska uruchomieniowego klienta AD RMS Client 2.1](http://www.microsoft.com/download/details.aspx?id=38396). Korzystając z funkcji usług AD RMS 2.1, aplikacja do udostępniania usługi Microsoft Rights Management oferuje użytkownikom końcowym proste środowisko ochrony i środowisko użytkowe.

Począwszy od wersji usług RMS z października 2013 r., możesz chronić dokumenty w sposób natywny za pomocą pakietu Office 2010 i wysyłać je do osób w innej firmie, które będą mogły ich używać za pomocą usług Azure RMS. Ponadto, jeśli używasz trybu kryptograficznego 2 usług AD RMS, możesz w tej wersji korzystać z usług RMS dla pojedynczych osób i używać zawartości od osób z innej firmy, w której są używane usługi Azure RMS. Aby uzyskać więcej informacji na temat trybu kryptograficznego 2, zobacz [Tryby kryptograficzne usług AD RMS](http://technet.microsoft.com/library/hh867439%28v=ws.10%29.aspx).

Aby uzyskać informacje na temat wdrożenia, zobacz [Automatyczne wdrażanie aplikacji do udostępniania usługi Microsoft Rights Management](sharing-app-admin-guide.md#automatic-deployment-for-the-microsoft-rights-management-sharing-application).

## Poziomy ochrony — natywny i ogólny
Aplikacja do udostępniania usługi Microsoft Rights Management obsługuje ochronę na dwóch różnych poziomach, co opisano w poniższej tabeli.

|Typ ochrony|Natywna|Ogólne|
|----------------------|----------|-----------|
|Opis|W przypadku plików tekstowych, obrazów, plików pakietu Microsoft Office (Word, Excel, PowerPoint), plików pdf oraz innych typów plików aplikacji obsługujących usługi AD RMS ochrona natywna zapewnia silny poziom ochrony obejmujący szyfrowanie i wymuszanie praw (uprawnień).|W przypadku pozostałych aplikacji i typów plików ochrona ogólna zapewnia poziom ochrony obejmujący hermetyzację plików z wykorzystaniem typu pliku pfile oraz uwierzytelnianie umożliwiające weryfikację, czy użytkownik jest autoryzowany do otwierania pliku.|
|Protection|Pliki są w pełni szyfrowane, a ochrona jest wymuszana w następujący sposób:<br /><br />— Przed wyświetleniem chronionej zawartości musi nastąpić pomyślne uwierzytelnienie użytkowników odbierających plik pocztą e-mail lub mających dostęp do niego za pośrednictwem uprawnień do pliku lub uprawnień udziału.<br /><br />— Ponadto, gdy pliki są chronione, wymuszane są prawa użytkowania i zasady ustawiane przez właściciela zawartości, gdy zawartość jest wyświetlana w aplikacji IP Viewer (dla chronionych plików tekstowych i plików obrazów) lub w skojarzonej aplikacji (dla wszystkich pozostałych obsługiwanych typów plików).|Ochrona plików jest wymuszana w następujący sposób:<br /><br />— Przed wyświetleniem chronionej zawartości musi nastąpić pomyślne uwierzytelnienie użytkowników autoryzowanych do otwierania pliku i mających do niego dostęp. W przypadku niepowodzenia autoryzacji plik nie jest otwierany.<br /><br />— Prawa do użytkowania i zasady ustawiane przez właściciela zawartości są wyświetlane, aby informować autoryzowanych użytkowników o zamierzonych zasadach użytkowania.<br /><br />— Rejestrowanie inspekcji autoryzowanych użytkowników otwierających pliki i uzyskujących do nich dostęp jest przeprowadzane, jednak żadne prawa użytkowania nie są wymuszane przez aplikacje, które tego nie obsługują.|
|Domyślny dla typów plików|Jest to domyślny poziom ochrony dla następujących typów plików:<br /><br />— Pliki tekstowe i pliki obrazów<br /><br />— Pliki pakietu Microsoft Office (programów Word, Excel i PowerPoint)<br /><br />— Pliki w formacie Portable Document Format (pdf)<br /><br />Więcej informacji można znaleźć w poniższej sekcji [Obsługiwane typy plików i rozszerzenia nazw plików](#supported-file-types-and-file-name-extensions).|Jest to domyślna ochrona dla wszystkich pozostałych typów plików (takich jak vsdx, rtf itd.), które nie są obsługiwane w ramach pełnej ochrony.|
Domyślny poziom ochrony stosowany przez aplikację RMS sharing można zmienić. Można zmienić poziom domyślny z natywnego na ogólny, z ogólnego na natywny, a nawet zupełnie uniemożliwić ochronę ze strony aplikacji RMS sharing. Aby uzyskać więcej informacji, zobacz sekcję [Zmiana domyślnego poziomu ochrony plików](#changing-the-default-protection-level-of-files) w tym artykule.

## Obsługiwane typy plików i rozszerzenia nazw plików:
Poniższa tabela zawiera listę typów plików, które są natywnie obsługiwane przez aplikację do udostępniania usługi Microsoft Rights Management. W przypadku tych typów plików oryginalne rozszerzenie nazwy pliku zostaje zmienione po zastosowaniu do nich ochrony natywnej i pliki zyskują status tylko do odczytu.

Ponadto w przypadku natywnej ochrony pliku programu Word, Excel lub PowerPoint w aplikacji RMS sharing (jeśli plik jest chroniony za pomocą udostępniania) ta akcja powoduje automatyczne utworzenie drugiego pliku stanowiącego kopię oryginału, który ma taką samą nazwę jak oryginał, ale rozszerzenie **ppdf**¹. Ta wersja pliku chronionego w sposób natywny może zostać otwarta przez adresatów, którzy zainstalowali aplikację RMS sharing.

W przypadku plików objętych ochroną ogólną oryginalne rozszerzenie nazwy pliku w każdej sytuacji zostaje zmienione na pfile.

> [!WARNING]
> Jeśli korzystasz z zapory, internetowego serwera proxy lub oprogramowania zabezpieczającego, które sprawdza pliki i podejmuje odpowiednie działania w zależności od rozszerzenia nazwy pliku, może zaistnieć konieczność zmiany konfiguracji tych zasobów w celu zapewnienia obsługi nowych rozszerzeń.

|Oryginalne rozszerzenie nazwy pliku|Rozszerzenie nazwy pliku chronionego przez usługi RMS|
|--------------------------------|-------------------------------------|
|txt|ptxt|
|xml|pxml|
|jpg|pjpg|
|jpeg|ppng|
|pdf|ppdf|
|PNG|ppng|
|tif|ptif|
|tiff|ptiff|
|bmp|pbmp|
|gif|pgif|
|giff|pgiff|
|jpe|pjpe|
|jfif|pjfif|
|jt|pjt|
¹ Renderowanie plików PDF obsługiwane przez technologię Foxit. Copyright © 2003–2014 Foxit Corporation.

Poniższa tabela zawiera typy plików obsługiwanych natywnie przez aplikację do udostępniania usługi Microsoft Rights Management w pakiecie Microsoft Office 2016, Office 2013 i Office 2010. Rozszerzenia nazw tych plików nie zmieniają się po objęciu plików ochroną przez usługi RMS.

|Typy plików obsługiwanych przez pakiet Office|Typy plików obsługiwanych przez pakiet Office|
|----------------------------------|----------------------------------|
|doc<br /><br />docm<br /><br />docx<br /><br />dot<br /><br />dotm<br /><br />dotx<br /><br />potm<br /><br />potx<br /><br />pps<br /><br />ppsm<br /><br />ppsx<br /><br />ppt<br /><br />pptm|pptx<br /><br />thmx<br /><br />xla<br /><br />xlam<br /><br />xls<br /><br />xlsb<br /><br />xlt<br /><br />xlsm<br /><br />xlsx<br /><br />xltm<br /><br />xltx<br /><br />xps|

### Zmiana domyślnego poziomu ochrony plików
Edytując rejestr, możesz zmienić sposób ochrony plików w aplikacji RMS sharing. Możesz na przykład wymusić, aby pliki obsługujące ochronę natywną były objęte ochroną ogólną aplikacji RMS sharing.

W jakich sytuacjach warto to zrobić:

-   Jeśli chcesz mieć pewność, że każdy użytkownik będzie mógł otworzyć plik na swoim urządzeniu przenośnym.

-   Jeśli chcesz mieć pewność, że każdy użytkownik będzie mógł otworzyć plik, nawet jeśli nie ma aplikacji obsługującej ochronę natywną.

-   Jeśli chcesz rozwiązać problem dotyczący systemów zabezpieczeń, które podejmują działania względem plików na podstawie ich rozszerzeń nazw i które można tak skonfigurować, aby uwzględniały rozszerzenie nazwy pliku pfile, ale nie wiele rozszerzeń nazw plików w ramach ochrony natywnej.

Analogicznie, można wymusić stosowanie przez aplikację RMS sharing ochrony natywnej względem plików, które domyślnie byłyby chronione w sposób ogólny. Może się to przydać, jeśli masz aplikację obsługującą interfejsy API usług RMS, taką jak aplikacja branżowa utworzona przez deweloperów w Twojej firmie lub aplikacja kupiona od niezależnego dostawcy oprogramowania.

Możesz też wymusić blokowanie ochrony plików przez aplikację RMS sharing. Wówczas nie jest stosowana ani ochrona natywna, ani ogólna. Ta opcja może się przydać, jeśli na przykład masz działającą automatycznie aplikację lub usługę, która musi otworzyć określony plik, aby przetworzyć jego zawartość. Jeśli zablokujesz ochronę określonego typu plików, użytkownicy nie mogą ochronić plików tego typu za pomocą aplikacji RMS sharing. Jeśli ktoś spróbuje to zrobić, zobaczy komunikat informujący o zablokowaniu przez administratora możliwości ochrony i będzie musiał zrezygnować z tego działania.

W celu skonfigurowania aplikacji RMS sharing, aby stosowała ochronę ogólną do wszystkich plików, które domyślnie byłyby chronione natywnie, wprowadź w rejestrze następujące zmiany:

1.  **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\RMSSharingApp\FileProtection**: Utwórz nowy klucz o nazwie *.

    To ustawienie oznacza pliki z dowolnym rozszerzeniem nazwy pliku.

2.  W nowo dodanym kluczu HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\RMSSharingApp\FileProtection\\\* utwórz nową wartość ciągu (REG_SZ) o nazwie **Encryption** z wartością danych **Pfile**.

    To ustawienie powoduje stosowanie ochrony ogólnej przez aplikację RMS sharing.

Te dwa ustawienia powodują, że aplikacja RMS sharing stosuje ochronę ogólną do wszystkich plików mających rozszerzenie nazwy pliku. Jeśli taki był Twój cel, nie trzeba już nic konfigurować. Możesz jednak zdefiniować wyjątki dla określonych typów plików, aby nadal były objęte ochroną natywną. W tym celu dla każdego typu plików trzeba wprowadzić trzy dodatkowe zmiany do rejestru:

1.  **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\RMSSharingApp\FileProtection**: Dodaj nowy klucz o nazwie takiej jak dane rozszerzenie nazwy pliku (bez kropki przed rozszerzeniem).

    Na przykład w przypadku plików z rozszerzeniem nazwy pliku docx utwórz klucz o nazwie **DOCX**.

2.  W nowo dodanym kluczu typu pliku (np. **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\RMSSharingApp\FileProtection\DOCX**) utwórz nową wartość DWORD o nazwie **AllowPFILEEncryption** z wartością **0**.

3.  W nowo dodanym kluczu typu pliku (np. **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\RMSSharingApp\FileProtection\DOCX**) utwórz nową wartość ciągu o nazwie **Encryption** z wartością **Native**.

W wyniku skonfigurowania tych ustawień wszystkie pliki będą chronione ogólnie z wyjątkiem plików mających rozszerzenie nazwy pliku docx, które będą chronione natywnie przez aplikację RMS sharing.

Powtórz te trzy kroki dla innych typów plików, które chcesz zdefiniować jako wyjątki, ponieważ obsługują ochronę natywną i nie chcesz, aby były objęte ochroną ogólną przez aplikację RMS sharing.

Podobne zmiany w rejestrze możesz wprowadzić w innych sytuacjach, zmieniając wartość ciągu **Encryption** obsługującego następujące wartości:

-   **Pfile**: ogólna ochrona

-   **Native**: ochrona natywna

-   **Off**: blokowanie ochrony

## Zobacz też
[Podręcznik użytkownika aplikacji do udostępniania usługi Rights Management](sharing-app-user-guide.md)




<!--HONumber=Jul16_HO3-->


