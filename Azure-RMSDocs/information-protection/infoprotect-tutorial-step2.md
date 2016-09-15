---
title: "Samouczek Szybki start dla usługi Azure Information Protection, krok 2 | Azure Rights Management"
description: "Krok 2 samouczka wprowadzającego, dzięki któremu możesz szybko wypróbować usługę Microsoft Azure Information Protection dla swojej organizacji. Wystarczą 4 proste kroki, które powinny zająć mniej niż 15 minut."
author: cabailey
manager: mbaldwin
ms.date: 08/08/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 3bc193c2-0be0-4c8e-8910-5d2cee5b14f7
translationtype: Human Translation
ms.sourcegitcommit: 09cb56aaa0d7d97073623c518aa331d591a376e3
ms.openlocfilehash: 65d758635b77ee7d6c423a1400a7621e8e05b14d


---

# Krok 2: Skonfiguruj i opublikuj zasadę usługi Azure Information Protection

>*Dotyczy: Azure Information Protection (wersja zapoznawcza)*

**[Niniejsze informacje mają charakter wstępny i mogą ulec zmianom. ]**

Usługa Azure Information Protection zawiera domyślną zasadę, której można użyć bez konfiguracji, ale chcemy się jej przyjrzeć i wprowadzić kilka zmian.

1. Zaloguj się do [portalu Azure](https://portal.azure.com). Jeśli chcesz przetestować ochronę, a także klasyfikację i etykietowanie, zaloguj się jako administrator globalny, co umożliwi pobranie szablonów usługi Azure Rights Management.
 
2. W menu centralnym: kliknij pozycję **Nowy** > **Zabezpieczenia i tożsamość** > **Azure Information Protection (wersja zapoznawcza)** > **Utwórz**.

    Spowoduje to utworzenie bloku **Azure Information Protection**, dzięki czemu przy następnym logowaniu do portalu będzie można wybrać usługę z listy centralnej **Przeglądaj**. 

    > [!TIP] 
    > Wybierz opcję **Przypnij do pulpitu nawigacyjnego**, aby utworzyć kafelek usługi **Azure Information Protection** na pulpicie nawigacyjnym, dzięki czemu można będzie pominąć krok przeglądania przy następnym zalogowaniu do portalu.

3.  Eksploruj główny blok **Azure Information Protection** przedstawiający domyślne zasady usługi Information Protection, które są tworzone automatycznie:
    
    - Etykiety klasyfikacji: **Osobiste**, **Publiczne**, **Wewnętrzne**, **Poufne** i **Tajne**. Przeczytaj etykietkę narzędzia każdej z nich, aby zrozumieć sposób korzystania z etykiet. Należy pamiętać, że etykieta **Tajne** zawiera dwie etykiety podrzędne: **Wszyscy pracownicy** i **Moja grupa**, które stanowią przykład klasyfikacji z podkategoriami.

    - Z ustawieniami domyślnymi etykiety **Wewnętrzne**, **Poufne** i **Tajne** mają skonfigurowane oznaczenia wizualne (takie jak stopka, nagłówek i znak wodny), lecz żadna z tych etykiet nie ma ustawionej ochrony. Ponadto te trzy ustawienia globalne nie są ustawione, tak więc nie jest wymagane, aby dokumenty i wiadomości e-mail miały etykietę, brak jest etykiety domyślnej, a użytkownicy nie muszą uzasadniać obniżenia poziomu ważności.

    ![Samouczek Szybki start dla usługi Azure Information Protection, krok 3 — zasada domyślna](../media/info-protect-policy.png)

W naszym samouczku zmienimy kilka ustawień globalnych, aby zobaczyć, jak działają:

-  **Wybierz etykietę domyślną**: ustaw tę wartość na **Wewnętrzne**.

- **Użytkownik musi podać uzasadnienie obniżenia poziomu ważności**: ustaw tę wartość na **Wł.**.

Zmienimy teraz ustawienia jednej z etykiet, **Poufne**:

1. Kliknij etykietę **Poufne**.

2. W bloku **Etykieta: Poufne** ukażą się ustawienia dostępne dla każdej etykiety. Wprowadź następujące zmiany:

    a. Jeśli aktywowano usługę Azure Rights Managment: jeśli w sekcji **Ustaw szablon usług RMS w celu ochrony dokumentów i wiadomości e-mail zawierających tę etykietę** jest widoczne pole **Wybierz szablon usług RMS z**, zachowaj ustawienie domyślne **Azure RMS**. Następnie dla opcji **Wybierz szablon usług RMS** kliknij menu rozwijane i wybierz szablon domyślny **\<nazwa organizacji > Poufne**. Na przykład jeśli nazwą firmy jest VanArsdel, Ltd, zobaczysz opcję **VanArsdel, Ltd — Poufne**, którą wybierzesz. Jeśli ten szablon domyślny usługi Azure Rights Management został wyłączony, wybierz szablon alternatywny. Jednak w przypadku wybrania szablonu działu upewnij się, czy Twoje konto znajduje się w jego zakresie.
    
    Jeśli usługa Azure Rights Management nie została aktywowana, nie można użyć tej opcji.
    
    b. **Dokumenty z etykietą mają znak wodny**: kliknij **Wł.** i w polu **Tekst** wpisz nazwę organizacji. W naszym przykładzie: **VanArsdel, Ltd**. 
    
    c. Kliknij przycisk **Dodaj nowy warunek** i następnie w bloku **Warunek** wykonaj następujące czynności:
    
    - **Wybierz typ warunku**: **Wbudowany**
    
    - **Wybierz wbudowany**: **Numer karty kredytowej**
    
    - **Minimalna liczba wystąpień**: **1**
    
    - **Zliczaj tylko wystąpienia o unikatowych wartościach**: **Wł.**
    
    - Kliknij przycisk **Zapisz**, aby powrócić do bloku **Etykieta: Poufne**.

3. W bloku **Etykieta: Poufne** zobaczysz, że jako **NAZWA WARUNKU** jest wyświetlany **Numer karty kredytowej** z opcją **WYSTĄPIENIA** równą **1**.

4. Pozostaw opcję **Wybierz sposób zastosowania tej etykiety**: **Zalecane**

5. W polu **Wprowadź informacje dla celów wewnętrznych** wpisz **Tylko do testów**.

6. Kliknij przycisk **Zapisz** w bloku **Etykieta: Poufne** i w głównym bloku **Azure Information Protection** kliknij ponownie przycisk **Zapisz**.

7. Po wprowadzeniu i zapisaniu zmian chcemy udostępnić je użytkownikom, więc klikamy **Opublikuj**, a następnie klikamy przycisk **Tak**, aby potwierdzić.

![Samouczek Szybki start dla usługi Azure Information Protection, krok 3 — skonfigurowana zasada domyślna](../media/info-protect-policy-configured.png)

Po zakończeniu tego samouczka możesz zamknąć portal Azure lub zostawić otwarty w celu wypróbowania innych opcji konfiguracji.

Skoro przyjrzeliśmy się już domyślnej zasadzie i wprowadziliśmy w niej kilka zmian, następnym krokiem jest zainstalowanie klienta usługi Azure Information Protection.

|Jeśli potrzebujesz dodatkowych informacji|Dodatkowe informacje|
|--------------------------------|--------------------------|
|Informacje o opcjach konfiguracji zasad|[Konfigurowanie zasad usługi Azure Information Protection](configure-policy.md)|


>[!div class="step-by-step"]
[&#171; Krok 1](infoprotect-tutorial-step1.md)
[Krok 3 &#187;](infoprotect-tutorial-step3.md)


<!--HONumber=Aug16_HO2-->


