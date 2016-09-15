---
title: "Azure RMS — samouczek Szybki start — krok 3 | Azure RMS"
description: "Trzeci krok samouczka, dzięki któremu możesz szybko wypróbować usługę Microsoft Azure Rights Management dla swojej organizacji. Wystarczy 5 prostych kroków, które powinny zająć mniej niż 15 minut."
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: c604e749-8918-40e8-8148-6bd000cb2be2
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ed50d87138c428fadfd22cd5b3ef3c7f7e421848
ms.openlocfilehash: efe389db839f3f70e9cdb9138f6749e2bd2e029f


---


# Samouczek Szybki start usługi Azure RMS, krok 3: prześlij w wiadomości e-mail dokument, który chcesz chronić

*Dotyczy usług: Azure Rights Management, Office 365*


Przejdź do: 
> [!div class="op_single_selector"]
- [Wprowadzenie](quick-start-tutorial.md)
- [Krok 1. Aktywacja usługi Azure RMS](tutorial-step1.md)
- [Krok 2. Instalacja aplikacji RMS sharing](tutorial-step2.md)
- [Krok 3. Przesłanie poufnego dokumentu w wiadomości e-mail](tutorial-step3.md)
- [Krok 4. Odbiorca odczytuje dokument](tutorial-step4.md)
- [Krok 5. Śledzenie dokumentu](tutorial-step5.md)


W tym kroku najpierw musisz w programie Word utworzyć i zapisać dokument reprezentujący plik, który chcesz chronić. Nazwij go **Confidential.docx**. W ramach tego samouczka nie jest istotne, jaki tekst zawiera dokument. Niemniej dobrze będzie wpisać jakiś tekst, aby łatwiej potwierdzić, że autoryzowany odbiorca mógł go odczytać. Na przykład możesz wpisać: **Jeśli możesz przeczytać ten tekst z załącznika wiadomości e-mail, nadawca pomyślnie udostępnił plik chroniony za pomocą usługi Azure RMS.**

Następnie możesz bezpiecznie udostępnić ten dokument pocztą e-mail.

![Azure RMS — samouczek Szybki start — krok 3](../media/AzRMS_Tutorial_3_Screenshots.png)

### Bezpieczne udostępnianie dokumentu w wiadomościach e-mail

1.  Za pomocą programu Outlook utwórz nową wiadomość i dołącz do niej właśnie utworzony plik.

2.  W polu **Do** wpisz jeden lub kilka służbowych adresów e-mail. Upewnij się, że podajesz służbowe adresy e-mail, np. **joannam@contoso.com** lub **pmichalski@fabrikam.com**, ponieważ obecnie usługa Azure Rights Management nie obsługuje osobistych adresów e-mail, z których można korzystać w domu za pośrednictwem swojego usługodawcy internetowego. Nie musisz martwić się tym, czy odbiorca wiadomości również ma usługę Azure Rights Management.

3.  Wpisz temat, np. **Poufny dokument**, i wpisz krótką wiadomość w treści, np. **Przeczytaj ten poufny dokument i nie udostępniaj go nikomu.**

4.  Następnie na karcie **Wiadomość** w grupie **RMS** kliknij opcję **Udostępnij chronioną zawartość**, a następnie ponownie kliknij opcję **Udostępnij chronioną zawartość**:

5.  W oknie dialogowym **Udostępnianie chronionej zawartości**:

    1.  Wybierz opcję **Przeglądający — tylko wyświetlanie**.

        Oznacza to, że odbiorcy będą mogli wyświetlić dokument, ale nie będą mogli go edytować ani drukować.

    2.  Wybierz opcję **Wyślij mi wiadomość e-mail, gdy ktoś spróbuje otworzyć te dokumenty**.

        Otrzymasz wiadomość e-mail z powiadomieniem za każdym razem, gdy któryś z odbiorców spróbuje otworzyć załącznik, a także wtedy, gdy ktoś inny spróbuje go otworzyć, np. jeśli jeden z odbiorców prześle wiadomość e-mail dalej do współpracownika. W tym ostatnim przypadku zobaczysz, że nastąpiła odmowa dostępu oraz otrzymasz dane użytkownika. Możesz zdecydować, czy wysłać tej osobie kopię dokumentu, którą będzie mogła otworzyć.

    3.  Wybierz opcję **Zezwalaj mi na natychmiastowe odwołanie dostępu do tych dokumentów**.

        Ta opcja wymaga od odbiorców połączenia internetowego za każdym razem, gdy próbują otworzyć załącznik, ale niesie ze sobą dodatkową korzyść: jeśli w późniejszym czasie wycofasz dokument, odbiorcy nie będą mogli go otworzyć przy kolejnej próbie. Jeśli nie zaznaczysz tej opcji, odbiorcy będą mogli otwierać dokument nawet bez połączenia z Internetem. Niemniej w przypadku późniejszego wycofania dokumentu może nastąpić opóźnienie jego faktycznego wycofania.

    4.  Kliknij pozycję **Wyślij teraz**.

        Wiadomość e-mail z załącznikiem zostanie wysłana do określonych adresatów. Oprócz wiadomości e-mail odbiorcy zobaczą instrukcje dotyczące sposobu odczytywania dołączonego dokumentu, który jest chroniony przez usługę Azure Rights Management.

Chroniony dokument został wysłany, więc możesz teraz poprosić adresatów o jego odebranie i otworzenie. Nie zamykaj jednak programu Outlook, ponieważ będziemy z niego korzystać ponownie w ostatnim kroku związanym ze śledzeniem załącznika.

|Jeśli potrzebujesz dodatkowych informacji|Dodatkowe informacje|
|--------------------------------|--------------------------|
|Pełne instrukcje i alternatywne metody ochrony plików udostępnianych za pośrednictwem poczty e-mail|[Ochrona plików udostępnianych pocztą e-mail za pomocą aplikacji do udostępniania usługi Rights Management](../rms-client/sharing-app-protect-by-email.md)|
|Informacje o opcjach dostępnych w oknie dialogowym **Udostępnianie chronionej zawartości**|[Opcje okien dialogowych aplikacji do udostępniania usługi Rights Management](../rms-client/sharing-app-dialog-box.md)|


>[!div class="step-by-step"]
[« Krok 2](tutorial-step2.md)
[Krok 4 »](tutorial-step4.md)


<!--HONumber=Jun16_HO4-->


