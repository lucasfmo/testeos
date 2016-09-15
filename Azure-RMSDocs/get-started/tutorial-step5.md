---
title: "Azure RMS — samouczek Szybki start — krok 5 | Azure RMS"
description: "Ostatni krok samouczka umożliwiającego szybkie wypróbowanie usługi Microsoft Azure Rights Management w swojej organizacji. Wystarczy wykonać 5 prostych kroków, co powinno zająć mniej niż 15 minut."
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 05/09/2016
ms.topic: get-started-article
ms.prod: azure
ms.service: rights-management
ms.technology: 
ms.assetid: aa06826d-c227-449b-93ea-6ce394608997
ROBOTS: 
audience: 
ms.devlang: 
ms.reviewer: esaggese
ms.suite: ems
ms.tgt_pltfrm: 
ms.custom: 
translationtype: Human Translation
ms.sourcegitcommit: ed50d87138c428fadfd22cd5b3ef3c7f7e421848
ms.openlocfilehash: 9c335e054d4aed1a8cca654420a580d02a4c849f


---


# Samouczek Szybki start usługi Azure RMS, krok 5: śledzenie chronionego dokumentu

*Dotyczy usług: Azure Rights Management, Office 365*


Przejdź do: 
> [!div class="op_single_selector"]
- [Wprowadzenie](quick-start-tutorial.md)
- [Krok 1. Aktywacja usługi Azure RMS](tutorial-step1.md)
- [Krok 2. Instalacja aplikacji RMS sharing](tutorial-step2.md)
- [Krok 3. Przesłanie poufnego dokumentu w wiadomości e-mail](tutorial-step3.md)
- [Krok 4. Odbiorca odczytuje dokument](tutorial-step4.md)
- [Krok 5. Śledzenie dokumentu](tutorial-step5.md)

![Azure RMS — samouczek Szybki start — krok 5](../media/AzRMS_QuickStartSteps5.PNG)

> [!NOTE]
> W tym kroku musisz mieć subskrypcję, która obsługuje śledzenie dokumentu. Aby sprawdzić, czy Twoja subskrypcja obsługuje śledzenie dokumentu, zobacz temat [Porównanie ofert usług Rights Management (RMS)](https://technet.microsoft.com/dn858608.aspx).

Ten krok jest opcjonalny, ale większość osób chce wiedzieć, czy załącznik wysłany do odbiorców został otwarty, kiedy go otwarto, a nawet z jakiego miejsca. Na przykład:

-   Spodziewasz się odpowiedzi od danej osoby o konkretnej porze, a w witrynie śledzenia dokumentu widzisz, że ta osoba nie otworzyła dokumentu, chociaż zbliża się termin realizacji zadania. W takim przypadku możesz wysłać kolejną wiadomość e-mail lub zadzwonić do tej osoby i przypomnieć o działaniu z odpowiednim wyprzedzeniem.

-   Jeśli zobaczysz, że dana osoba otworzyła dokument, możesz zapytać, czy ma jakieś pytania lub potrzebuje dodatkowych informacji.

![Zrzuty ekranu do kroku 5 samouczka](../media/AzRMS_Tutorial_5_Screenshots.png)

### Aby śledzić chroniony dokument

1.  Korzystając z programu Outlook, na karcie **Narzędzia główne** w grupie **RMS** kliknij pozycję **Śledź użycie**.

2.  Jeśli zobaczysz stronę **Chroń i udostępniaj na własnych warunkach**, kliknij opcję **Zaloguj się** i podaj ponownie nazwę użytkownika i hasło.

3.  Na stronie **Dokumenty udostępnione** zobaczysz dokument, który został załączony do wiadomości e-mail, **Confidential.docx**. W tym momencie jest to jedyny wyświetlany plik, ale liczba pozycji na liście będzie rosnąć wraz z udostępnianiem kolejnych dokumentów chronionych.

    Na tej stronie możesz zobaczyć czas udostępnienia dokumentu (kiedy wysłano wiadomość e-mail z chronionym dokumentem), datę ostatniej aktywności oraz nazwę odbiorcy, do którego wysłano wiadomość e-mail. Kliknij nazwę dokumentu, aby uzyskać dodatkowe informacje.

4.  Na nowej stronie, która zawiera nazwę klikniętego pliku, zobaczysz szczegółowe informacje dotyczące wyłącznie tego dokumentu oraz listę opcji dostępnych dla tego dokumentu (**Lista**, **Oś czasu**, **Mapa**, **Ustawienia**).

    Klikaj poszczególne opcje, aby poznać różne sposoby śledzenia chronionego dokumentu. Lub (nadal na stronie **Podsumowanie**) kliknij opcję **Otwórz w programie Excel**, aby wyeksportować informacje do arkusza kalkulacyjnego, albo kliknij opcję **Odwołaj dostęp**, aby zatrzymać udostępnianie dokumentu.

Możesz powrócić do tej witryny, aby śledzić dalszą aktywność dotyczącą chronionego dokumentu lub w razie potrzeby wycofać dostęp. Możesz również uzyskać dostęp do witryny z urządzenia przenośnego lub tabletu, korzystając z przeglądarki i następującego linku: [śledzenie dokumentu](http://go.microsoft.com/fwlink/?LinkId=529562)

|Jeśli potrzebujesz dodatkowych informacji|Dodatkowe informacje|
|--------------------------------|--------------------------|
|Pełne instrukcje dotyczące śledzenia dokumentów|[Śledzenie i odwoływanie dokumentów podczas używania aplikacji do udostępniania usługi RMS](../rms-client/sharing-app-track-revoke.md)|
|Dwuminutowe wideo, które objaśnia i przedstawia funkcję śledzenia dokumentu|[Śledzenie dokumentów i odwoływanie dostępu w usłudze Azure RMS](http://channel9.msdn.com/Series/Information-Protection/Azure-RMS-Document-Tracking-and-Revocation)|
|Rozwiązywanie problemów i pytania klienta|[Często zadawane pytania dotyczące śledzenia dokumentów](https://technet.microsoft.com/dn947488)|

### Następne kroki
Ten samouczek przeprowadził Cię przez tylko jeden scenariusz związany z ochroną danych za pomocą usługi Azure RMS. Aby poznać inne częste zastosowania usługi, zobacz temat [Usługa Azure RMS w akcji](../understand-explore/what-admins-users-see.md) w artykule [Co to jest usługa Azure Rights Management?](../understand-explore/what-is-azure-rms.md) W tym artykule istnieją też inne sekcje, które również mogą być przydatne, np. sekcje związane ze sposobem działania usługi Azure RMS oraz problemami biznesowymi, które może ona rozwiązać.

Jeśli masz wszystko gotowe i możesz rozpocząć wdrażanie usługi Azure RMS, użyj [planu wdrożenia usługi Azure Rights Management](../plan-design/deployment-roadmap.md), który zawiera kroki związane z wdrażaniem i linki prowadzące do instrukcji dotyczących danych zadań.

Możesz też zobaczyć [Szybkie wdrażanie usługi Azure Rights Management](../get-started/rapid-deployment-guide.md), aby uzyskać listę konkretnych scenariuszy, powiązanych kroków dotyczących konfiguracji i dokumentację użytkownika końcowego.

>[!div class="step-by-step"]
[Wprowadzenie](quick-start-tutorial.md)
[Krok 1](tutorial-step1.md)
[Krok 2](tutorial-step2.md)
[Krok 3](tutorial-step3.md)
[Krok 4](tutorial-step4.md)
*krok 5*



<!--HONumber=Jul16_HO3-->


