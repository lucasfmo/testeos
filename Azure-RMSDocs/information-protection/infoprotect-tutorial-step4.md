---
title: "Samouczek Szybki start dla usługi Azure Information Protection, krok 4 | Azure Rights Management"
description: "Krok 4 samouczka wprowadzającego, dzięki któremu możesz szybko wypróbować usługę Microsoft Azure Information Protection dla swojej organizacji. Wystarczą 4 proste kroki, które powinny zająć mniej niż 15 minut."
author: cabailey
manager: mbaldwin
ms.date: 08/10/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 468748c1-49d6-4c3e-a612-9c584acdc782
translationtype: Human Translation
ms.sourcegitcommit: d17bacf8e148622db0e2393f40d3fd37c8f086eb
ms.openlocfilehash: a36433167462275e91059f9eb3a2141ffa2797d5


---

# Krok 4: Zobacz, jak działają funkcje klasyfikacji, etykietowania i ochrony 

>*Dotyczy: Azure Information Protection (wersja zapoznawcza)*

**[Niniejsze informacje mają charakter wstępny i mogą ulec zmianom. ]**

Po otwarciu dokumentu programu Word z zainstalowanym klientem usługi Azure Information Protection możesz sprawdzić, jak łatwo rozpocząć etykietowanie i chronienie dokumentu za pomocą skonfigurowanej zasady.

Klasyfikacja i ochrona zachodzą podczas zapisywania dokumentu, ale zanim do tego przejdziemy, użyjemy naszego niezapisanego dokumentu, aby zobaczyć, jak łatwo stosować i zmieniać etykiety.

### Aby ręcznie zmienić naszą domyślną etykietę:

- Na pasku Information Protection wybierz etykietę **Osobiste**. Zostanie wyświetlony monit o uzasadnienie obniżenia poziomu klasyfikacji. Wybierz opcję **Ten plik nie wymaga już klasyfikacji** i kliknij przycisk **Potwierdź**.  

    Wartość opcji **Ważność** zmieni się na **Osobiste**.

    ![Samouczek Szybki start dla usługi Azure Information Protection, krok 4 — monit o uzasadnienie potwierdzenia obniżenia](../media/confirm-lowering.png)

### Aby całkowicie usunąć klasyfikację:

- Na pasku Information Protection kliknij ikonę **Edytuj etykietę** obok opcji **Osobiste**. Zostaną wyświetlone dostępne etykiety. Zamiast wybierać którąś z etykiet, kliknij ikonę **Usuń etykietę**. Kliknij przycisk **OK**, aby potwierdzić, a następnie podaj uzasadnienie dla tej akcji.  

    Zobaczysz, że wartość opcji **Ważność** zmieni się na **Nieustawione**, która jest wartością wyświetlaną początkowo, przed ustawieniem etykiety domyślnej.

    ![Samouczek Szybki start dla usługi Azure Information Protection, krok 4 — usuwanie klasyfikacji](../media/sensitivity-not-set.png)


### Aby wyświetlić monit zalecający etykietowanie i automatyczne włączanie ochrony:

1. W dokumencie programu Word wpisz poprawny numer karty kredytowej, na przykład: **4242-4242-4242-4242**. 

2. Zapisz dokument (użyj dowolnej nazwy pliku i dowolnej lokalizacji). 

3. Pojawi się monit: **Zaleca się nadać temu plikowi etykietę Poufne**. Kliknij przycisk **Zmień teraz**.

    ![Samouczek Szybki start dla usługi Azure Information Protection, krok 4 — monit z zaleceniem klasyfikacji](../media/change-now.png)

    Na stronie natychmiast pojawi się znak wodny z nazwą organizacji, towarzyszący stopce **Ważność: poufne**. 

    Jeśli wybrano opcję stosowania szablonu RMS, dokument jest również chroniony za pomocą podanego szablonu Azure Rights Management, co można potwierdzić, klikając kartę **Plik** i wyświetlając informację **Ochrona dokumentu**. Jeśli używany jest domyślny szablon Poufne, zostaną wyświetlone informacje, że zasięg dokumentu jest ograniczony do użytkowników wewnętrznych (użytkownicy spoza organizacji nie będą mogli otworzyć dokumentu) i jego zawartość nie może być kopiowana ani drukowana. Jako właściciel dokumentu możesz skopiować i wydrukować dokument, ale jeśli wyślesz go pocztą e-mail do innego użytkownika w organizacji, nie będzie on mógł wykonać tych czynności.

> [!NOTE]
>Jeśli masz problemy z wykonaniem tych kroków, kliknij kartę **Główna** w grupie **Ochrona**, a następnie kliknij kolejno przyciski **Chroń** i **Pomoc i opinie**. 
>
>W oknie dialogowym **Microsoft Azure Information Protection** kliknij przycisk **Wyślij opinię**. Spowoduje to wysłanie wiadomości e-mail do zespołu Information Protection i automatyczne dołączenie plików dziennika z Twojego komputera służących do zdiagnozowania problemów.

##  Następne kroki

Po zapoznaniu się z domyślnymi zasadami usługi Azure Information Protection i sposobami ich dostosowywania oraz z działaniem etykietowania dla programu Word poeksperymentuj z innymi ustawieniami i zobacz, jak działają w innych aplikacjach pakietu Office obsługujących usługę Azure Information Protection: Excel, PowerPoint i Outlook. Jeśli te aplikacje były otwarte podczas instalowania klienta Azure Information Protection, zamknij je i otwórz przed podjęciem próby używania usługi Azure Information Protection.

Na przykład można zmienić tytuł domyślny **Ważność** na pasku Information Protection na dowolny inny. Użytkownik może zmienić etykietki narzędzi, kolory etykiet, ich kolejność oraz nazwy. Można tworzyć nowe etykiety i definiować własne automatyczne reguły. Można dostosowywać swoje znaki wodne, konfigurując rozmiar i kolor oraz zmieniając pozycję z przekątnej na poziomą.

Należy pamiętać, że jeśli korzystasz ze znaków wodnych w programie Excel, są one widoczne tylko w trybach Podgląd wydruku i Układ strony oraz po wydrukowaniu.

Przy każdej zmianie ustawień zasad usługi Information Protection w portalu Azure należy pamiętać o **zapisaniu** zasady i następnie **opublikowaniu** jej. Ponieważ zmiany mogą być wykonywane na wielu kartach, dobrym pomysłem jest sprawdzenie, czy dla karty nie są wyświetlane aktywne przyciski **Zapisz**, co oznacza, że zmiany nie zostały zapisane. Jeśli aplikacja pakietu Office była otwarta podczas publikowania nowych zmian, zamknij ją i otwórz ponownie, aby pobrać najnowsze zasady.

Po zakończeniu testowania warto zapoznać się z [często zadawanymi pytaniami dotyczącymi usługi Azure Information Protection](faq.md).




<!--HONumber=Aug16_HO2-->


