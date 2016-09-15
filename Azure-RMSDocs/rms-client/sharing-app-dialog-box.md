---
title: "Opcje w oknach dialogowych aplikacji do tworzenia i przetwarzania dokumentów chronionych usługami Rights Management | Azure RMS"
description: 
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 07/13/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 7b91ab30-6363-4929-bcbd-4dfbd05f644a
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 67129d6cdac124947fc07aa4d42523686227752e
ms.openlocfilehash: ed2ab42174ce5d83fd60ace1c394515db1450e3d


---

# Opcje w oknach dialogowych aplikacji do tworzenia i przetwarzania dokumentów chronionych usługami Rights Management

*Dotyczy: Active Directory Rights Management, Azure Rights Management, Windows 10, Windows 7 z dodatkiem SP1, Windows 8, Windows 8.1*

Te informacje ułatwiają określanie opcji w oknie dialogowym **dodawania ochrony** lub **udostępniania chronionej zawartości** w aplikacji RMS sharing. To okno dialogowe jest wyświetlane w przypadku [ochrony udostępnianego pliku](sharing-app-protect-by-email.md) lub [włączania ochrony miejscowej pliku](sharing-app-protect-in-place.md) i wybrania uprawnień niestandardowych.

> [!IMPORTANT]
> Jeśli opcje widoczne w Twojej aplikacji różnią się od opisanych tutaj, prawdopodobnie nie masz najnowszej wersji aplikacji do udostępniania. Najnowszą wersję można pobrać ze strony usługi [Microsoft Rights Management](http://go.microsoft.com/fwlink/?LinkId=303970).
> 
> Jak sprawdzić, czy jest zainstalowana najnowsza wersja? Na liście w aplecie Programy i funkcje wyszukaj pozycję **Aplikacja do tworzenia i przetwarzania dokumentów chronionych usługami Microsoft Rights Management**, a następnie sprawdź jej numer wersji. Opcje wymienione w tabeli są dostępne w wersji **1.0.1770.0** lub nowszych. Numer najnowszej wersji można znaleźć na stronie pobierania.

Oprócz opcji do wyboru mogą Cię również zainteresować następujące zagadnienia:

-   [Co to za plik ppdf, który jest automatycznie tworzony?](#what-s-the-ppdf-file-that-s-automatically-created)

-   [Jaka jest różnica między ochroną ogólną i ochroną wbudowaną (natywną)?](#what-s-the-difference-between-generic-protection-and-built-in-native-protection)

|Opcja|Opis|
|----------|---------------|
|**UŻYTKOWNICY**|Jeśli adres e-mail programu Outlook nie został jeszcze określony, wpisz adresy e-mail osób, którym chcesz umożliwić otwieranie pliku.<br /><br />Pamiętaj, że aplikacja RMS sharing nie obsługuje wszystkich adresów e-mail.<br /><br />Jeśli Twoja organizacja korzysta z lokalnej wersji usług Rights Management (AD RMS), możesz określić tylko adresy e-mail osób z tej organizacji. Jeśli to ograniczenie ma zastosowanie i spróbujesz określić zewnętrzne adresy e-mail, pojawi się komunikat z informacją, że konfiguracja firmy pozwala na udostępnianie chronionej zawartości tylko w ramach firmy. <br /><br /> Jeśli Twoja organizacja korzysta z usługi Azure RMS, możesz wybrać adresy e-mail osób z tej organizacji lub osób z innej organizacji.<br /><br />Na przykład: **joannam@contoso.com; p.michalski@fabrikam.com**.<br /><br />Aplikacja RMS sharing nie obsługuje obecnie osobistych adresów e-mail.|
|**Ochrona ogólna**|Jeśli ta opcja została wybrana, nie można natywnie chronić wybranego pliku. Więcej informacji można znaleźć w temacie [Jaka jest różnica między ochroną ogólną a wbudowaną (natywną)?](#what-s-the-difference-between-generic-protection-and-built-in-native-protection) na tej stronie.|
|**Przeglądający — tylko wyświetlanie**<br /><br />**Recenzent — wyświetlanie i edytowanie**<br /><br />**Współautor — wyświetlanie, edytowanie, kopiowanie i drukowanie**<br /><br />**Współwłaściciel — wszystkie uprawnienia**<br /><br />Uwaga: przed nazwami tych opcji jest wyświetlana okrągła ikona kuli ziemskiej. Ta ikona jest stosowana, ponieważ przeważnie jedna z tych opcji jest wybierana w przypadku wysyłania załącznika do osoby w innej organizacji.|Wybierz jedną z tych opcji, jeśli chcesz zdefiniować prawa dotyczące chronionego dokumentu. Kliknij każdą opcję, aby wyświetlić jej opis.<br /><br />Po wybraniu jednej z tych opcji tylko osoby określone w obszarze **UŻYTKOWNICY** będą mieć wskazane prawa do otwierania i używania dokumentu. Jeśli na przykład dokument zostanie przesłany do osoby spoza tej listy, jego otwarcie nie będzie możliwe.|
|Szablony zasad, które konfiguruje administrator.<br /><br />Na przykład, jeśli nazwa firmy to Contoso, Ltd: **Contoso, Ltd — tylko wyświetlanie poufne**.<br /><br />Uwaga: przed nazwami tych opcji jest wyświetlana kwadratowa ikona budynku biura. Ta ikona jest stosowana, ponieważ przeważnie jedna z tych opcji jest wybierana w przypadku wysyłania załącznika do osoby w tej samej organizacji.|Kiedy udostępnisz dokument osobom pracującym w swojej organizacji, zobaczysz dostępne szablony zasad skonfigurowane przez administratora. Wybierz jedną z tych opcji, jeśli dokument nie powinien być udostępniany poza firmą.<br /><br />W przypadku wybrania jednej z tych opcji administrator definiuje uprawnienia do dokumentu oraz wskazuje, kto może go otwierać.|
|**Dokumenty wygasają**|Tę opcję należy wybrać tylko w przypadku plików ważnych przez określony okres. Po upłynięciu wyznaczonej daty wybrani użytkownicy nie będą już mogli otworzyć tego pliku. Nadal będziesz mieć możliwość otwarcia oryginalnego pliku, ale po północy (bieżącej strefy czasowej) w wybranym dniu inne osoby nie będą mogły otwierać pliku.<br /><br />Ta opcja jest niedostępna w przypadku wybrania szablonu zasad skonfigurowanego przez administratora.|
|**Wyślij do mnie wiadomość e-mail, gdy ktoś spróbuje otworzyć te dokumenty**|Uwaga: ta opcja jest obecnie dostępna w wersji zapoznawczej.<br /><br />Wybierz tę opcję, jeśli chcesz otrzymywać powiadomienia pocztą e-mail, jeśli ktoś spróbuje otworzyć dokument, który jest chronisz. Z wiadomości tej dowiesz się, kto to był, kiedy to zrobił i czy mu się to udało.<br /><br />Ta opcja jest dostępna tylko w przypadku organizacji korzystających z usługi Azure RMS. Jeśli Twoja organizacja korzysta z lokalnej wersji usług Rights Management (AD RMS), ta opcja nie będzie widoczna.|
|**Zezwalaj mi na natychmiastowe odwołanie dostępu do tych dokumentów**|Wybierz tę opcję, jeśli w przyszłości może wystąpić konieczność odwołania dostępu do dokumentów za pomocą witryny śledzenia dokumentów, a odwołanie będzie konieczne w trybie natychmiastowym. Wybranie tej opcji wymaga jednak (o ile dokument nie został odwołany) dostępu do Internetu za każdym razem, kiedy użytkownik chce go otworzyć. Mogą wystąpić sytuacje, w których użytkownicy nie mogą nawiązać połączenia z Internetem, przez co nie mogą otworzyć przeznaczonego dla nich dokumentu.<br /><br />Nawet jeśli nie wybierzesz tej opcji, możesz odwołać później dokument, korzystając z witryny śledzenia dokumentów. Do otwierania dokumentów nie zawsze jest konieczne połączenie internetowe, dlatego użytkownicy nie będą od razu wiedzieć, że dokument został odwołany. Mogą go nadal czytać, a o odwołaniu dokumentu dowiedzą się po kolejnym uwierzytelnieniu się w usługach Azure RMS. Domyślnie maksymalna liczba dni, w ciągu których inna osoba może odczytywać odwołany chroniony dokument, to 30, ale administrator może zmienić tę wartość na mniejszą lub większą niż 30 dni.<br /><br />Ta opcja jest dostępna tylko w przypadku organizacji korzystających z usługi Azure RMS. Jeśli Twoja organizacja korzysta z lokalnej wersji usług Rights Management (AD RMS), ta opcja nie będzie widoczna.|

## Jaka jest różnica między ochroną ogólną i ochroną wbudowaną (natywną)?

-   Jeśli **plik jest objęty ochroną ogólną**, nieupoważnione osoby nie mogą go otworzyć. Upoważniona osoba może jednak po otwarciu pliku przesłać go bez ochrony do innych osób albo zapisać w miejscu dostępnym dla innych. Wyświetlany jest komunikat informujący o posiadanych przez nią uprawnieniach oraz prośba o ich respektowanie, ale ochrona nie jest wymuszana. Ponadto w przypadku ochrony ogólnej pliku nie można wyznaczyć uprawnień bardziej ograniczonych niż autoryzacja. Nie można na przykład ograniczyć uprawień do zawartości do uprawnień typu „tylko do odczytu” lub „nie do drukowania”:

    > [!NOTE]
    > Plik objęty ochroną ogólną ma zawsze rozszerzenie **pfile**.

-   Natomiast **ochrona wbudowana (natywna)** dostępna w ramach usługi Rights Management dla obsługujących ją aplikacji (np. plików pakietu Office) obowiązuje, nawet jeśli chroniony plik zostanie przesłany do innej osoby lub zapisany w innym miejscu. Ochrona takich plików umożliwia stosowanie restrykcyjnych uprawnień (np. tylko odczyt) lub uprawnień do edycji (ale nie do drukowania lub kopiowania). Można na przykład wybrać opcję **Przeglądający — tylko wyświetlanie**, aby nie można było edytować, drukować ani kopiować zawartości.

Aby uzyskać dodatkowe informacje, zobacz sekcję [Poziomy ochrony — natywny i ogólny](sharing-app-admin-guide-technical.md#levels-of-protection-native-and-generic) w [Przewodniku administratora aplikacji udostępniania usługi Rights Management](sharing-app-admin-guide.md).

## Co to za plik ppdf, który jest automatycznie tworzony?

-   W przypadku udostępniania pocztą e-mail pliku chronionego (udostępniania chronionej zawartości) aplikacja RMS sharing automatycznie tworzy wersję tego pliku w formacie **ppdf** (dla plików programu Word, Excel, PowerPoint lub plików PDF). Jest to chroniona wersja pliku przeznaczona tylko do odczytu, którą mogą otwierać tylko upoważnione osoby. Załącznik można otworzyć nawet na urządzeniu przenośnym, na którym nie ma aplikacji z natywną obsługą usługi Rights Management. Jeśli te osoby mają zainstalowaną aplikacje do udostępniania usług RMS, będą mogły otworzyć załącznik.

    W tym scenariuszu, w przeciwieństwie do plików objętych ochroną ogólną, ograniczenie użycia zostaje wymuszone. Odbiorca nie może zapisać tej wersji pliku, a jeśli prześle ją innej osobie, nadal będą obowiązywać pierwotne ograniczenia nałożone na dokument. Dokument chroniony mogą otworzyć tylko osoby, które zostały do tego upoważnione.

    > [!NOTE]
    > Plik ppdf jest tworzony automatycznie, kiedy udostępniasz zawartość chronioną (pocztą e-mail), ale nie jest tworzony w przypadku ochrony miejscowej.

## Przykłady i inne instrukcje
Aby uzyskać instrukcje i przykłady dotyczące korzystania z aplikacji do udostępniania usługi Rights Management, zapoznaj się z następującymi sekcjami podręcznika użytkownika aplikacji do udostępniania usługi Rights Management:

-   [Przykłady korzystania z aplikacji RMS sharing](sharing-app-user-guide.md#examples-for-using-the-rms-sharing-application)

-   [Co chcesz zrobić?](sharing-app-user-guide.md#what-do-you-want-to-do)

## Zobacz też
[Podręcznik użytkownika aplikacji do udostępniania usługi Rights Management](sharing-app-user-guide.md)




<!--HONumber=Jul16_HO3-->


