![](../media/AzRMS_QuickStartSteps3.PNG)

W tym kroku najpierw musisz utworzyć i zapisać dokument w programie Word reprezentujący plik, który chcesz chronić. Nazwij go **Confidential.docx**. W ramach tego samouczka nie jest istotne, jaki tekst zawiera dokument. Niemniej dobrze będzie wpisać jakiś tekst, aby łatwiej potwierdzić, że autoryzowany odbiorca mógł go odczytać. Na przykład możesz wpisać: **Jeśli możesz przeczytać ten tekst z załącznika wiadomości e-mail, nadawca pomyślnie udostępnił plik chroniony za pomocą usługi Azure RMS.**

Następnie możesz bezpiecznie udostępnić ten dokument za pomocą poczty e-mail.

![Zrzuty ekranu przedstawiające udostępnianie dokumentów za pomocą poczty e-mail przy użyciu usługi Azure RMS](../media/AzRMS_Tutorial_3_Screenshots.png)

#### Aby bezpiecznie udostępnić dokument w wiadomości e-mail

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
|Pełne instrukcje i alternatywne metody ochrony plików udostępnianych za pośrednictwem poczty e-mail   ->|[Ochrona plików udostępnianych pocztą e-mail za pomocą aplikacji do udostępniania usługi Rights Management](../rms-client/sharing-app-protect-by-email.md)|
|Informacje o opcjach dostępnych w oknie dialogowym **Udostępnianie chronionej zawartości** ->|[Opcje okien dialogowych aplikacji do udostępniania usługi Rights Management](../rms-client/sharing-app-dialog-box.md)|


<!--HONumber=Jul16_HO3-->


