---
title: "Konfigurowanie warunków klasyfikacji automatycznej i zalecanej dla usługi Azure Information Protection | Azure Rights Management"
description: 
author: cabailey
manager: mbaldwin
ms.date: 08/10/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: e915f959-eafb-4375-8d2c-2f312edf2d29
translationtype: Human Translation
ms.sourcegitcommit: b2263c212a1b869b778767493645f10ad821828f
ms.openlocfilehash: 80c201dcf316a5aa5e123645d47c6741f8b61f05


---

# Konfigurowanie warunków klasyfikacji automatycznej i zalecanej dla usługi Azure Information Protection

>*Dotyczy: Azure Information Protection (wersja zapoznawcza)*

**[Niniejsze informacje mają charakter wstępny i mogą ulec zmianom. ]**

W przypadku skonfigurowania warunków dla etykiety możesz automatycznie przypisywać etykietę do dokumentu lub wiadomości e-mail. Możesz też monitować użytkowników o wybranie zalecanej etykiety: 

- Automatyczna klasyfikacja ma zastosowanie do programów Word, Excel i PowerPoint, gdy zapisywane są pliki oraz programu Outlook, gdy wysyłane są wiadomości e-mail. Nie możesz użyć automatycznej klasyfikacji wobec plików, które wcześniej zostały oznaczone ręcznie.
 
- Zalecana klasyfikacja ma zastosowanie do programów Word, Excel i PowerPoint, gdy zapisywane są pliki.

Gdy konfigurujesz warunki, możesz użyć wstępnie zdefiniowanych wzorców, takich jak numer karty kredytowej lub numer ubezpieczenia społecznego w USA. Możesz zdefiniować niestandardowy ciąg lub szablon będący warunkiem automatycznej klasyfikacji. Aby uzyskać więcej informacji o warunkach, zobacz sekcję [Informacje o wbudowanych warunkach](#information-about-the-built-in-conditions).

W jaki sposób ocenia się wiele warunków, jeśli są zastosowane wobec więcej niż jednej etykiety:

1. Etykiety są uporządkowane do oceny zgodnie z ich pozycją określoną w zasadach: etykieta na pierwszej pozycji ma najniższą pozycję (najmniejszą ważność), a ostatnia najwyższą (największa ważność).

2. Zostaje zastosowana etykieta wskazująca najwyższą ważność.
 
3. Zostaje zastosowana ostatnia etykieta podrzędna.

> [!TIP]
>Aby zapewnić najlepszą jakość obsługi i ciągłość prowadzenia działalności biznesowej, warto rozpocząć od użycia zalecanej klasyfikacji dla użytkownika, a nie od klasyfikacji automatycznej. Ta konfiguracja daje użytkownikom możliwość zaakceptowania etykiet lub akcji ochronnej, a także zignorowania tych sugestii, jeśli nie są one odpowiednie dla danego dokumentu lub wiadomości e-mail.

Przykład monitu w przypadku konfigurowania warunki do zastosowania etykiety jako akcji zalecanej, ze wskazówką dotyczącą zasad niestandardowych:

![Wykrywanie i zalecenia usługi Azure Information Protection](../media/info-protect-recommend-callouts.png)

W tym przykładzie użytkownik może kliknąć opcję **Zmień teraz**, aby zastosować zalecaną etykietę, lub zignorować zalecenie przez zamknięcie paska.

## Aby skonfigurować zalecaną lub automatyczną klasyfikację dla etykiety

1. Jeśli jeszcze tego nie zrobiono, zaloguj się do [Portalu Azure](https://portal.azure.com), a następnie przejdź do bloku **Azure Information Protection**. 
    
    Na przykład w menu centralnym kliknij przycisk **Przeglądaj** i w polu filtru zacznij wpisywać ciąg **Information**. Wybierz pozycję **Azure Information Protection**.

2. W bloku **Azure Information Protection** wybierz etykietę, którą chcesz skonfigurować pod kątem automatycznej lub zalecanej klasyfikacji.

3. W bloku **Etykieta** w sekcji **Konfigurowanie warunków dla automatycznego stosowania tej etykiety** kliknij przycisk **Dodaj nowy warunek**.

4. W bloku **Warunek** wybierz opcję **Wbudowany**, jeśli chcesz użyć wstępnie zdefiniowanego warunku lub **Niestandardowy**, jeśli chcesz określić własny warunek, a następnie kliknij przycisk **Zapisz**:

    - W przypadku opcji **Wbudowany**: wybierz warunek z listy dostępnych warunków, a następnie wybierz minimalną liczbę wystąpień oraz określ, czy wystąpienie powinno mieć unikatową wartość, aby było uwzględnione w liczbie wystąpień.
        
        Aby uzyskać więcej informacji o regułach wykrywania dla tych warunków wraz z przykładami, zobacz sekcję [Informacje o wbudowanych warunkach](#information-about-the-built-in-conditions).

    - W przypadku opcji **Niestandardowy**: określ nazwę i frazę do dopasowania, bez znaków cudzysłowu i znaków specjalnych. Następnie określ, czy dopasowywać jako wyrażenie regularne lub uwzględniać wielkość liter, podaj minimalną liczbę wystąpień i wskaż, czy wystąpienie powinno mieć unikatową wartość, aby było uwzględnione w liczbie wystąpień.
        
    **Przykład opcji wystąpień**: wybierasz wbudowaną opcję numeru ubezpieczenia społecznego i ustawiasz minimalną liczbę wystąpień na 2. Dokument ma ten sam numer ubezpieczenia społecznego wymieniony dwukrotnie. Jeśli ustawisz opcję **Zliczaj tylko wystąpienia o unikatowych wartościach** na wartość **Wł.**, warunek nie zostanie spełniony. Jeśli ustawisz tę opcję na wartość **Wył.**, warunek zostanie spełniony.

5. W bloku **Etykieta** skonfiguruj następujące opcje i kliknij przycisk **Zapisz**:

    - Wybierz automatyczną lub zalecaną klasyfikację: dla opcji **Wybierz sposób stosowania etykiety: automatycznie lub jako zalecenie dla użytkownika** wybierz wartość **Automatycznie** lub **Zalecenie**.

    - Określ tekst monitu dla użytkownika lub wskazówki dotyczącej zasad: zachowaj tekst domyślny lub podaj własny ciąg.

6. Aby udostępnić użytkownikom zmiany, w bloku **Azure Information Protection** kliknij przycisk **Opublikuj**.

## Informacje o wbudowanych warunkach

W okresie używania wersji zapoznawczej możesz wybrać następujące warunki:

- [Kod SWIFT](#swift-code )

- [Numer karty kredytowej](#credit-card-number )

- [Numer rozliczeniowy ABA](#aba-routing-number )

- [Numer ubezpieczenia społecznego USA (SSN)](#usa-social-security-number-ssn)

- [Międzynarodowy numer konta bankowego (IBAN)](#international-banking-account-number-iban)


### Kod SWIFT

Dopasuj ten typ informacji, jeśli zawartość obejmuje następujące elementy:  

1. Jedna z następujących fraz: **swift**, **swiftnumber**, **swiftroutingnumber** 

2. Kod SWIFT w układzie sformatowanym:  

    a. 4 litery (kod banku)  

    b. 2 litery (kod kraju)  

    c. 2 litery lub cyfry (kod lokalizacji)  

    d. Opcjonalnie 3 litery lub cyfry (kod oddziału)  


Przykłady do testowania:

- **NEDSZAJJXXX Swiftroutingnumber**

- **NEDSZAJJ100 Swiftnumber** 

----


### Numer karty kredytowej

Dopasuj ten typ informacji, jeśli zawartość obejmuje następujące elementy:  

- Numer ważnej karty kredytowej, w układzie sformatowanym lub niesformatowanym, który przechodzi przez [kontrolę przy użyciu algorytmu Luhna](https://wikipedia.org/wiki/Luhn_algorithm). Ten typ informacji wykrywa karty wszystkich głównych marek na całym świecie, w tym karty Visa, MasterCard, Discover Card, American Express i Diners.

    - **Sformatowany**:
    
        - 16 cyfr: (dddd-dddd-dddd-dddd)  
        
    - **Niesformatowany**:
    
        - (dddddddddddddddd)  


Przykłady do testowania:

- **4242-4242-4242-4242**

- **4242424242424242** 

----

### Numer rozliczeniowy ABA

Dopasuj ten typ informacji, jeśli zawartość obejmuje następujące elementy:  

1. Co najmniej jedna z następujących fraz: **aba**, **rtn**, **routing number** 

2. Numer rozliczeniowy ABA, który zawiera 9 cyfr, może być sformatowany lub niesformatowany: 

    - **Sformatowany**: 
        
        a. Cztery cyfry, z których pierwsza to 0, 1, 2, 3, 6, 7 lub 8 
        
        b. Łącznik 
        
        c. Cztery cyfry 
        
        d. Łącznik 
        
        e. Cyfra 
        
        Przykład: 3456-9876-1 ABA 
        
    - **Niesformatowany**: 
        
        9 kolejnych cyfr, z których pierwsza to 0, 1, 2, 3, 6, 7 lub 8 
        
        Przykład: 345698761 RTN 
 

Przykłady do testowania:

- **3456-9876-1 ABA**

- **345698761 RTN** 

----

### Numer ubezpieczenia społecznego USA (SSN)

Dopasuj ten typ informacji, jeśli zawartość obejmuje następujące elementy:  

1. Co najmniej jedna z następujących fraz: **ssn**, **social security**, **ssid**, **ss#** 

2. Numer ubezpieczenia społecznego: 9 cyfr w układzie sformatowanym lub niesformatowanym:

    - **Sformatowany**: 
    
        - Dziewięć cyfr w następującym formacie: ddd-dd-dddd lub ddd dd dddd 
        
    - **Niesformatowany**: 
    
        - Dziewięć cyfr w następującym formacie: ddddddddd 


Przykłady do testowania:

- **SSN 123-45-6789**

- **SS# 123456789** 


----

### Międzynarodowy numer konta bankowego (IBAN)

Dopasuj ten typ informacji, jeśli zawartość obejmuje następujące elementy:  

1. Następująca fraza: **IBAN** 

2. Numer IBAN: rozpoczyna się od kodu kraju (dwie litery), następnie zawiera cyfry kontrolne (dwie cyfry) i numer bban (maksymalnie do 30 cyfr).


Przykłady do testowania:

- **GB29 NWBK 6016 1331 9268 19 IBAN**


## Następne kroki

Aby uzyskać więcej informacji o konfigurowaniu zasad usługi Azure Information Protection, użyj linków w sekcji [Konfigurowanie zasad organizacji](configure-policy.md#configuring-your-organization-s-policy).  






<!--HONumber=Aug16_HO2-->


