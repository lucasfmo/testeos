---
title: "Konfigurowanie praw użytkowania dla usługi Azure Rights Management | Azure RMS"
description: 
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 08/09/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 97ddde38-b91b-42a5-8eb4-3ce6ce15393d
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 60f25cdcdabbfbb61072a95e39f84fed79cad871
ms.openlocfilehash: e656729fa9ea926681e560f40c4f43ce320a0d5e


---

# Konfigurowanie praw użytkowania dla usługi Azure Rights Management

*Dotyczy usług: Azure Rights Management, Office 365*

Jeśli ustawiasz ochronę plików lub wiadomości e-mail za pomocą usługi Azure Rights Management (Azure RMS) bez użycia szablonu, musisz własnoręcznie skonfigurować prawa użytkowania. Ponadto konfigurując szablony niestandardowe dla usługi Azure RMS, wybierasz prawa użytkowania, które zostaną automatycznie zastosowane po wybraniu szablonu przez użytkowników, administratorów lub skonfigurowane usługi. Na przykład w klasycznym portalu platformy Azure możesz wybrać role, które powodują ustawienie logicznego grupowania praw użytkowania, albo skonfigurować poszczególne prawa.

Niniejszy artykuł pomoże Ci skonfigurować prawa użytkowania dla używanej aplikacji oraz zrozumieć, jak te prawa będą interpretowane przez aplikacje.

## Prawa użytkowania wraz z opisami
Poniższa tabela zawiera listę i opisy praw użytkowania obsługiwanych przez usługę Rights Management oraz sposób ich wykorzystania i interpretowania. Są one wyświetlane według **nazwy pospolitej**, która jest często spotykanym sposobem na wyświetlenie prawa użytkowania lub odniesienie się do niego. Jest to przyjaźniejsza wersja jednowyrazowej wartości używanej w kodzie (wartość **Kodowanie w zasadach**). **Stała lub wartość API** jest nazwą zestawu SDK wywołania MSIPC API używanego podczas pisania aplikacji obsługujących usługę RMS. Wywołanie sprawdza prawa użytkowania lub dodaje prawo użytkowania do zasad.


|Prawe|Opis|Implementacja|
|-------------------------------|---------------------------|-----------------|
|Nazwa pospolita: **Edytuj zawartość, Edytuj** <br /><br />Kodowanie w zasadach: **DOCEDIT**|Zezwala użytkownikowi na modyfikowanie, rozmieszczanie, formatowanie lub filtrowanie zawartości wewnątrz aplikacji. Nie nadaje prawa do zapisywania edytowanej kopii.|W prawach niestandardowych pakietu Office: jako część opcji **Zmiana** i **Pełna kontrola**. <br /><br />Nazwa w klasycznym portalu Azure: **Edytuj zawartość**<br /><br />Nazwa w szablonach usługi AD RMS: **Edytuj** <br /><br />Stała lub wartość interfejsu API: nie dotyczy.|
|Nazwa pospolita: **Zapisz** <br /><br />Kodowanie w zasadach: **EDIT**|Umożliwia użytkownikowi zapisanie dokumentu w jego bieżącej lokalizacji.<br /><br />W aplikacjach pakietu Office to prawo umożliwia użytkownikowi modyfikowanie dokumentu.|W prawach niestandardowych pakietu Office: jako część opcji **Zmiana** i **Pełna kontrola**. <br /><br />Nazwa w klasycznym portalu Azure: **Zapisz plik**<br /><br />Nazwa w szablonach usługi AD RMS: **Zapisz** <br /><br />Stała API lub wartość API: `IPC_GENERIC_WRITE L"EDIT"`|
|Nazwa pospolita: **Komentarz** <br /><br />Kodowanie w zasadach: **COMMENT**|Pozwala dodawać adnotacje i komentarze do zawartości.<br /><br />To prawo jest dostępne w zestawie SDK oraz jest dostępne w formie zasad ad hoc w module RMS Protection w środowisku Windows PowerShell. Zostało zaimplementowane w niektórych aplikacjach dostawców oprogramowania. Nie jest jednak powszechnie używane i obecnie nie jest obsługiwane przez aplikacje pakietu Office.|W prawach niestandardowych pakietu Office: nie zaimplementowane. <br /><br />Nazwa w klasycznym portalu Azure: nie zaimplementowane.<br /><br />Nazwa w szablonach usługi AD RMS: nie zaimplementowane. <br /><br />Stała API lub wartość API: `IPC_GENERIC_COMMENT L"COMMENT`|
|Nazwa pospolita: **Zapisz jako, Eksportuj** <br /><br />Kodowanie w zasadach: **EXPORT**|Włącza opcję zapisu zawartości w pliku o innej nazwie (Zapisz jako). W przypadku dokumentów pakietu Office plik może zostać zapisany bez ochrony.<br /><br />To uprawnienie umożliwia też użytkownikowi korzystanie z innych opcji eksportu w aplikacjach, np. opcji **Wyślij do programu OneNote**.|W prawach niestandardowych pakietu Office: jako część opcji **Zmiana** i **Pełna kontrola**. <br /><br />Nazwa w klasycznym portalu Azure: **Eksportuj zawartość (Zapisz jako)**<br /><br />Nazwa w szablonach usługi AD RMS: **Eksportuj (Zapisz jako)** <br /><br />Stała API lub wartość API: `IPC_GENERIC_EXPORT L"EXPORT"`|
|Nazwa pospolita: **Prześlij dalej** <br /><br />Kodowanie w zasadach: **FORWARD**|Włącza opcję przesyłania dalej wiadomości e-mail oraz dodawania adresatów w wierszach **Do** i **DW**. To prawo dotyczy tylko wiadomości e-mail, a nie dokumentów.<br /><br />Nie zezwala osobie przekazującej wiadomość dalej na przyznanie praw innym użytkownikom jako części akcji przekazywania.|W prawach niestandardowych pakietu Office: odmowa przy użyciu standardowych zasad **Nie przekazuj**.<br /><br />Nazwa w klasycznym portalu Azure: **Prześlij dalej**<br /><br />Nazwa w szablonach usługi AD RMS: **Prześlij dalej** <br /><br />Stała API lub wartość API: `IPC_EMAIL_FORWARD L"FORWARD"`|
|Nazwa pospolita: **Pełna kontrola** <br /><br />Kodowanie w zasadach: **OWNER**|Przyznaje wszystkie prawa do dokumentu. Można wykonywać wszystkie dostępne akcje.<br /><br />Obejmuje możliwość usunięcia ochrony i ponownego włączenia ochrony dokumentu.|W prawach niestandardowych pakietu Office: jako opcja niestandardowa **Pełna kontrola**.<br /><br />Nazwa w klasycznym portalu Azure: **Pełna kontrola**<br /><br />Nazwa w szablonach usługi AD RMS: **Pełna kontrola** <br /><br />Stała API lub wartość API: `IPC_GENERIC_ALL L"OWNER"`|
|Nazwa pospolita: **Drukuj** <br /><br />Kodowanie w zasadach: **PRINT**|Włącza opcje związane z drukowaniem zawartości.|W prawach niestandardowych pakietu Office: jako opcja **Drukuj zawartość** w uprawnieniach niestandardowych. Nie jest to ustawienie określane dla poszczególnych odbiorców.<br /><br />Nazwa w klasycznym portalu Azure: **Drukuj**<br /><br />Nazwa w szablonach usługi AD RMS: **Drukuj** <br /><br />Stała API lub wartość API: `IPC_GENERIC_PRINT L"PRINT"`|
|Nazwa pospolita: **Odpowiedz** <br /><br />Kodowanie w zasadach: **PRINT**|Włącza opcję **Odpowiedz** w kliencie poczty e-mail bez możliwości zmiany w wierszach **Do** lub **DW**.|W prawach niestandardowych pakietu Office: nie dotyczy.<br /><br />Nazwa w klasycznym portalu Azure: **Odpowiedz**<br /><br />Nazwa w szablonach usługi AD RMS: **Odpowiedz** <br /><br />Stała API lub wartość API: `IPC_EMAIL_REPLY`|
|Nazwa pospolita: **Odpowiedz wszystkim** <br /><br />Kodowanie w zasadach: **REPLYALL**|Włącza opcję **Odpowiedz wszystkim** w kliencie poczty e-mail, ale nie zezwala użytkownikowi na dodawanie odbiorców w wierszach **Do** lub **DW**.|W prawach niestandardowych pakietu Office: nie dotyczy.<br /><br />Nazwa w klasycznym portalu Azure: **Odpowiedz wszystkim**<br /><br />Nazwa w szablonach usługi AD RMS: **Odpowiedz wszystkim** <br /><br />Stała API lub wartość API: `IPC_EMAIL_REPLYALL L"REPLYALL"`|
|Nazwa pospolita: **Wyświetl, Otwórz, Odczytaj** <br /><br />Kodowanie w zasadach: **VIEW**|Umożliwia użytkownikom otworzenie dokumentu i wyświetlenie zawartości.|W prawach niestandardowych pakietu Office: jako zasady niestandardowe **Odczytaj**, opcja **Wyświetl**.<br /><br />Nazwa w klasycznym portalu Azure: **Wyświetl**<br /><br />Nazwa w szablonach usługi AD RMS: **Odpowiedz wszystkim** <br /><br />Stała API lub wartość API: `IPC_GENERIC_READ L"VIEW"`|
|Nazwa pospolita: **Kopiuj** <br /><br />Kodowanie w zasadach: **EXTRACT**|Włącza opcje kopiowania danych (w tym przechwytywania ekranu) z dokumentu do tego samego lub innego dokumentu.<br /><br />W niektórych aplikacjach pozwala także na zapisanie całego dokumentu w postaci niechronionej.|W prawach niestandardowych pakietu Office: jako opcja zasady niestandardowej **Zezwalaj użytkownikom z dostępem do odczytu na kopiowanie zawartości**.<br /><br />Nazwa w klasycznym portalu Azure: **Kopiuj i Wyodrębnij zawartość**<br /><br />Nazwa w szablonach usługi AD RMS: **Wyodrębnij** <br /><br />Stała API lub wartość API: `IPC_GENERIC_EXTRACT L"EXTRACT"`|
|Nazwa pospolita: **Włącz makra** <br /><br />Kodowanie w zasadach: **OBJMODEL**|Włącza opcję uruchamiania makr lub innych rozwiązań programistycznych albo zezwala na zdalny dostęp do zawartości w dokumencie.|W prawach niestandardowych pakietu Office: jako opcja zasad niestandardowych **Zezwalaj na dostęp programistyczny**. Nie jest to ustawienie określane dla poszczególnych odbiorców.<br /><br />Nazwa w klasycznym portalu Azure: **Zezwalaj na makra**<br /><br />Nazwa w szablonach usługi AD RMS: **Zezwalaj na makra** <br /><br />Stała lub wartość interfejsu API: nie zaimplementowane.|



## Prawa zawarte w poziomach uprawnień

Niektóre aplikacje grupują prawa użytkowania w poziomach uprawnień. Dzięki temu można łatwiej wybrać prawa użytkowania, które zazwyczaj stosuje się wspólnie. Te poziomy uprawnień upraszczają skomplikowane działania po stronie użytkowników, którzy mogą wybrać opcje oparte na rolach.  Na przykład **Osoba dokonująca przeglądu** i **Współautor**. Chociaż opcje te często są dostępne z podsumowaniem praw, to mogą one nie obejmować wszystkich praw wymienionych w poprzedniej tabeli.

W tabeli poniżej znajduje się lista poziomów uprawnień i pełna lista praw w nich zawartych.

|Poziom uprawnień|Aplikacje|Zawarte prawa (nazwa pospolita)|
|---------------------|----------------|---------------------------------|
|Przeglądanie|Klasyczny portal Azure<br /><br />Aplikacja do udostępniania usługi Rights Management dla systemu Windows|Wyświetl, Otwórz, Odczytaj; Odpowiedz; Odpowiedz wszystkim|
|Osoba dokonująca przeglądu|Klasyczny portal Azure<br /><br />Aplikacja do udostępniania usługi Rights Management dla systemu Windows|Wyświetl, Otwórz, Odczytaj; Zapisz; Edytuj zawartość; Odpowiedz [[1]](#footnote-1); Odpowiedz wszystkim [[1]](#footnote-1); Prześlij dalej [[1]](#footnote-1)|
|Współautor|Klasyczny portal Azure<br /><br />Aplikacja do udostępniania usługi Rights Management dla systemu Windows|Wyświetl, Otwórz, Odczytaj; Zapisz; Edytuj zawartość, Edytuj; Kopiuj; Wyświetl prawa; Zezwalaj na makra; Zapisz jako; Eksportuj; Drukuj; Odpowiedz [[1]](#footnote-1); Odpowiedz wszystkim [[1]](#footnote-1); Prześlij dalej [[1]](#footnote-1)|
|Współwłaściciel|Klasyczny portal Azure<br /><br />Aplikacja do udostępniania usługi Rights Management dla systemu Windows|Wyświetl, Otwórz, Odczytaj; Zapisz; Edytuj zawartość, Edytuj; Kopiuj; Wyświetl prawa; Zezwalaj na makra; Zapisz jako; Eksportuj; Drukuj; Odpowiedz [[1]](#footnote-1); Odpowiedz wszystkim [[1]](#footnote-1); Prześlij dalej [[1]](#footnote-1); Pełna kontrola|

----

###### Przypis 1
Nie dotyczy aplikacji do udostępniania usługi Microsoft Rights Management dla systemu Windows.

## Prawa zawarte w domyślnych szablonach
W szablonach domyślnych zawarte są następujące prawa:

|Nazwa wyświetlana|Zawarte prawa (nazwa pospolita)|
|----------------|---------------------------------|
|&lt;*nazwa organizacji*&gt; *— tylko wgląd poufny*|Wyświetl, Otwórz, Odczytaj|
|&lt;*nazwa organizacji*&gt; *— poufne*|Wyświetl, Otwórz, Odczytaj; Zapisz; Edytuj zawartość; Edytuj; Wyświetl prawa; Zezwalaj na makra; Prześlij dalej; Odpowiedz; Odpowiedz wszystkim|

## Opcja Nie przekazuj dotycząca wiadomości e-mail

Klienci i usługi programu Exchange (na przykład klient programu Outlook, aplikacja Outlook Web Access i reguły transportu programu Exchange) mają jedną dodatkową opcję ochrony praw do informacji na potrzeby wiadomości e-mail: **Nie przekazuj**. 

Mimo że ta opcja jest dostępna dla użytkowników (i administratorów programu Exchange) w sposób sugerujący, że jest to domyślny szablon usługi Rights Management, który można wybrać, opcja **Nie przekazuj** nie jest szablonem. Tłumaczy to, dlaczego ta opcja nie jest widoczna w klasycznym portalu Azure podczas wyświetlania szablonów usług Azure RMS i zarządzania nimi. Zamiast tego opcje **Nie przekazuj** stanowią zestaw uprawnień dynamicznie stosowany przez użytkowników względem ich adresatów wiadomości e-mail.

Gdy opcja **Nie przekazuj** jest stosowana do wiadomości e-mail, adresaci nie mogą przekazać takiej wiadomości e-mail, wydrukować jej, skopiować z niej informacji, zapisać załączników ani zapisać załączników pod inną nazwą. Na przykład w kliencie programu Outlook przycisk Prześlij dalej jest niedostępny, opcje menu **Zapisz jako**, **Zapisz załącznik** i **Drukuj** nie są dostępne oraz nie można dodawać ani zmieniać adresatów w polach **Do**, **DW** i **UDW**.

Jest to ważna różnica między stosowaniem opcji **Nie przekazuj** i stosowaniem szablonu, za pomocą którego nie są przyznawane uprawnienia do przekazywania wiadomości e-mail: opcja **Nie przekazuj** używa dynamicznej listy autoryzowanych użytkowników opartej na wybranych przez użytkownika adresatach pierwotnej wiadomości e-mail. Prawa w szablonie zawierają natomiast statyczną listę autoryzowanych użytkowników określonych wcześniej przez administratora. Na czym polega różnica? Zostanie to wytłumaczone na przykładzie: 

Użytkownik chce wysłać pewne informacje w wiadomości e-mail do określonych osób w dziale marketingu, które nie powinny być udostępniane nikomu innemu. Czy w takiej sytuacji użytkownik powinien chronić wiadomość e-mail za pomocą szablonu ograniczającego prawa (do wyświetlania, odpowiedzi i zapisywania) tylko do działu marketingu?  Czy może powinna zostać użyta opcja **Nie przekazuj**? Obie te opcje spowodują, że adresaci nie będą mogli przekazywać wiadomości e-mail. 

- W przypadku zastosowania szablonu adresaci będą jednak mogli nadal udostępniać informacje innym użytkownikom w dziale marketingu. Na przykład adresat będzie mógł użyć Eksploratora Windows do przeciągnięcia i upuszczenia wiadomości e-mail do współdzielonej lokalizacji lub dysku USB. W takiej sytuacji każdy użytkownik z działu marketingu (oraz właściciel wiadomości e-mail), który ma dostęp do tej lokalizacji, będzie mógł wyświetlać informacje zawarte w wiadomości e-mail.
 
- Jeśli natomiast użytkownik zastosuje opcję **Nie przekazuj**, adresaci nie będą mogli udostępniać informacji nikomu innemu w dziale marketingu za pomocą przenoszenia wiadomości e-mail do innej lokalizacji. W takim scenariuszu tylko pierwotni adresaci (oraz właściciel wiadomości e-mail) będą mogli wyświetlać informacje zawarte w wiadomości e-mail.

> [!NOTE] 
> Użyj opcji **Nie przekazuj**, jeśli ważne jest, aby tylko wybrani przez nadawcę adresaci mogli wyświetlać informacje zawarte w wiadomości e-mail. Użyj szablonu na potrzeby wiadomości e-mail do ograniczenia praw do grupy osób określonych wcześniej przez administratora, niezależnie od adresatów wybranych przez nadawcę.




## Zobacz też
[Konfigurowanie szablonów niestandardowych usługi Azure Rights Management](configure-custom-templates.md)




<!--HONumber=Aug16_HO2-->


