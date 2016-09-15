---
title: "Podręcznik użytkownika aplikacji do udostępniania usługi Rights Management | Azure RMS"
description: 
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: eaf6d02c-aa36-4915-856e-49bb71ab1484
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 384a58f32aae8c7d908392e7fd9a1629bc05cdff
ms.openlocfilehash: d3727eb963532e03137aea2140293fa9c5821db2


---

# Podręcznik użytkownika aplikacji do udostępniania usługi Rights Management

*Dotyczy: Active Directory Rights Management, Azure Rights Management, Windows 10, Windows 7 z dodatkiem SP1, Windows 8, Windows 8.1*

Aplikacja do udostępniania usługi Microsoft Rights Management (RMS) dla systemu Windows pomaga zabezpieczyć ważne dokumenty i obrazy przed niepowołanymi osobami nawet po przesłaniu tych plików pocztą e-mail lub zapisaniu na innym urządzeniu. Za pomocą tej aplikacji można też otwierać pliki chronione przez innych za pomocą tej samej technologii (Rights Management).

Wystarczy mieć komputer z systemem Windows 7 z dodatkiem Service Pack 1 lub nowszym. Następnie [pobierz i zainstaluj](http://go.microsoft.com/fwlink/?LinkId=303970) tę bezpłatną aplikację firmy Microsoft.

Jeśli masz pytania, na które nie udało Ci się znaleźć odpowiedzi w tym podręczniku, zobacz [Często zadawane pytania dotyczące aplikacji do udostępniania usługi Microsoft Rights Management dla systemu Windows](http://go.microsoft.com/fwlink/?LinkId=303971). Na tej stronie są również dostępne pewne informacje dotyczące rozwiązywania problemów, które mogą wystąpić.

## Przykłady korzystania z aplikacji RMS sharing
Poniżej przedstawiono kilka sposobów ochrony plików za pomocą aplikacji RMS sharing.

|Cel|Metoda|
|----------------|------------------|
|**… Bezpieczne udostępnienie informacji finansowych zaufanej osobie, która pracuje dla innej organizacji**<br /><br />Chcesz przesłać pocztą e-mail firmie, z którą współpracujesz, arkusz kalkulacyjny programu Excel zawierający prognozy finansowe. Chcesz, aby mogli oni wyświetlić dane bez możliwości ich edycji.|Użyj przycisku **Udostępnij chronione** na wstążce w programie Excel, wpisz adresy e-mail dwóch adresatów z partnerskiej firmy, wybierz pozycję **Przeglądający — tylko wyświetlanie**, a następnie kliknij pozycję **Wyślij**.<br /><br />Kiedy wiadomość e-mail dotrze do partnerskiej firmy, załączony arkusz będą mogli otworzyć tylko adresaci wiadomości (bez możliwości zapisywania, edytowania, drukowania ani przekazywania dalej).<br /><br />Krok po kroku: [Ochrona plików udostępnianych pocztą e-mail za pomocą aplikacji do udostępniania usługi Rights Management](sharing-app-protect-by-email.md).|
|**… Bezpieczne wysłanie dokumentu pocztą e-mail do osoby korzystającej z urządzenia z systemem iOS**<br /><br />Chcesz wysłać pocztą e-mail poufny dokument programu Word do współpracownika, który często sprawdza pocztę na swoim urządzeniu z systemem iOS.|W Eksploratorze plików kliknij plik prawym przyciskiem myszy, a następnie wybierz polecenie **Udostępnij chronione**. Wyślij współpracownikowi plik jako załącznik.<br /><br />Adresat odbierze wiadomość e-mail na swoim urządzeniu z systemem iOS. Ponieważ adresat nie ma pakietu Office dla urządzeń iPad i iPhone, klika link w wiadomości e-mail do informacji o pobieraniu aplikacji do udostępniania, instaluje wersję aplikacji przeznaczoną na urządzenia z systemem iOS, po czym wyświetla dokument¹.<br /><br />Krok po kroku: [Ochrona plików udostępnianych pocztą e-mail za pomocą aplikacji do udostępniania usługi Rights Management](sharing-app-protect-by-email.md).|
|**… Sprawdzenie, kto i kiedy otwierał chronione dokumenty, oraz odwołanie dostępu w razie konieczności**<br /><br />Poufny dokument projektowy został bezpiecznie udostępniony potencjalnym dostawcom, a teraz chcesz sprawdzić, kto uzyskał do niego dostęp, kiedy i z jakiej lokalizacji. Następnie, gdy jeden z dostawców otrzymał zlecenie, chcesz odwołać dostęp do oryginalnego dokumentu, tak aby osoby, którym go udostępniono, nie mogły już go odczytać.|Po udostępnieniu dokumentu pocztą e-mail możesz przejść do [witryny śledzenia dokumentów](http://go.microsoft.com/fwlink/?LinkId=529562), aby sprawdzić, kto i kiedy miał dostęp do tego dokumentu. Aby zatrzymać udostępnianie dokumentu, wybierz opcję odwołania dostępu.<br /><br />Krok po kroku: [Śledzenie i odwoływanie dokumentów podczas używania aplikacji RMS sharing](sharing-app-track-revoke.md).|
|**… Otwarcie chronionego załącznika otrzymanego w wiadomości e-mail w firmie, która nie korzysta z usługi Rights Management**<br /><br />Nadawcą wiadomości e-mail jest zaufana osoba (kiedyś współpracowaliście). Podejrzewasz, że mogła Ci wysłać informacje dotyczące nowych możliwości biznesowych.|Postępujesz zgodnie z instrukcjami w wiadomości e-mail i klikasz link, aby założyć konto w usłudze Microsoft Rights Management. Firma Microsoft potwierdza, że Twoja organizacja nie ma subskrypcji obejmującej usługę Azure Rights Management, wysyła Ci wiadomość e-mail umożliwiającą ukończenie procesu zakładania bezpłatnego konta, po czym możesz się już do niego zalogować. Klikasz drugi link znajdujący się w wiadomości e-mail, który umożliwia zainstalowanie aplikacji do udostępniania usługi Rights Management. Po ukończeniu instalacji możesz już otworzyć załącznik i przeczytać o nowych możliwościach biznesowych.<br /><br />Krok po kroku: [Wyświetlanie i używanie plików chronionych przez usługę Rights Management](sharing-app-view-use-files.md).|
|**… Ochrona poufnych danych firmy na laptopie przed osobami spoza firmy**<br /><br />Często podróżujesz, co wymaga używania laptopa do obsługi plików w folderze, który musi być zabezpieczony przed nieautoryzowanymi osobami.|Na laptopie masz zainstalowaną aplikację RMS sharing. Korzystając z Eksploratora plików, chronisz pliki za pomocą szablonu służącego do szybkiego zabezpieczania plików. W przypadku kradzieży laptopa nikt spoza firmy nie będzie mógł uzyskać dostępu do tych dokumentów.<br /><br />Krok po kroku: [Ochrona pliku na urządzeniu &#40;ochrona miejscowa&#41; za pomocą aplikacji do udostępniania usługi Rights Management](sharing-app-protect-in-place.md).|
¹ Renderowanie plików PDF obsługiwane przez technologię Foxit. Copyright © 2003–2014 Foxit Corporation.

## Co chcesz zrobić?
> [!NOTE]
> Aby uzyskać więcej informacji technicznych dotyczących między innymi [obsługiwanych typów plików](sharing-app-admin-guide-technical.md#supported-file-types-and-file-name-extensions) i [sposobu instalacji tej aplikacji w sieci przedsiębiorstwa](sharing-app-admin-guide.md#automatic-deployment-for-the-microsoft-rights-management-sharing-application), zobacz [Przewodnik administratora aplikacji do udostępniania usługi Rights Management](sharing-app-admin-guide.md).

- [Pobieranie i instalowanie aplikacji do udostępniania](install-sharing-app.md)

- [Ochrona pliku na urządzeniu (ochrona miejscowa)](sharing-app-protect-in-place.md)

- [Ochrona pliku udostępnionego pocztą e-mail](sharing-app-protect-by-email.md)

- [Zmienianie uprawnień do chronionych plików](sharing-app-reprotect-files.md)

- [Śledzenie i odwoływanie dokumentów](sharing-app-track-revoke.md)

- [Wyświetlanie i używanie chronionych plików](sharing-app-view-use-files.md)

- [Usuwanie ochrony z pliku](sharing-app-remove-protection.md)

- [Używanie skrótów klawiaturowych](sharing-app-keyboard-shortcuts.md)

- [Określanie ustawień w oknie dialogowym](sharing-app-dialog-box.md)






<!--HONumber=Jul16_HO3-->


