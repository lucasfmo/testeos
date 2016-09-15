![Szybki start z usługą Azure RMS — krok 4](../media/AzRMS_QuickStartSteps4.PNG)

Odbiorcy mogą użyć różnych urządzeń do odczytania chronionego dokumentu wysłanego w załączniku do wiadomości e-mail. Mogą to zrobić na urządzeniach iPad, iPhone, tabletach i telefonach z systemem Android, komputerach Mac i komputerach z systemem Windows.

Poproś odbiorców o odczytanie wysłanej wiadomości e-mail. Odbiorcy zobaczą wiadomość e-mail, a wcześniej następujący tekst:

**Nadawca zabezpieczył załączniki przy użyciu usługi Microsoft RMS. Musisz** [zalogować się](http://aka.ms/rms)
      **, aby je otworzyć.**

Jeśli odbiorca kliknie link, zostanie przeniesiony do instrukcji związanych z instalacją aplikacji RMS sharing. W razie potrzeby będzie mógł zarejestrować się i uzyskać bezpłatne konto. Bezpłatne konto obejmuje subskrypcję usługi RMS dla użytkowników indywidualnych, która umożliwia autoryzowanym użytkownikom odczytywanie chronionych dokumentów, nawet jeśli ich organizacja nie ma usługi Azure RMS. Następnie odbiorcy mogą odczytać chroniony załącznik zgodnie z poniższymi instrukcjami.

![Zrzuty ekranu przedstawiające samouczek dotyczący usługi RM](../media/AzRMS_Tutorial_4_Screenshots.png)

#### Aby wyświetlić załącznik z chronionym dokumentem

1.  Jako że usługa Azure Rights Management chroni dokument programu Word, w wiadomości e-mail dostępne są dwa załączniki. Są to dwie wersje tego samego pliku o różnych rozszerzeniach nazwy pliku. Otwórz wersję z rozszerzeniem **ppdf** (**Confidential.ppdf**).

    Jeśli na urządzeniu masz pakiet [Office w wersji z obsługą usługi Rights Management](https://technet.microsoft.com/library/dn655136.aspx), możesz otworzyć drugą wersję pliku (**Confidential.docx**), aby zobaczyć plik w programie Word.

2.  Jeśli zobaczysz monit o podanie nazwy użytkownika i hasła, podaj nazwę użytkownika w takim samym formacie jak format adresu e-mail użytego do wysłania tej wiadomości e-mail i załącznika. Na przykład **joannam@contoso.com** lub **pmichalski@fabrikam.com**. Wpisz hasło podane podczas rejestracji w usłudze RMS dla użytkowników indywidualnych. Lub, jeśli Twoja organizacja ma usługę Azure RMS, podaj zwykłe hasło do konta firmowego.

Dokument zostanie otwarty i będzie można przeczytać jego zawartość. Przykładowo treść dokumentu może brzmieć: **Jeśli możesz przeczytać ten tekst z załącznika wiadomości e-mail, nadawca pomyślnie udostępnił plik chroniony za pomocą usługi Azure RMS.** Jako że dokument jest plikiem tylko do odczytu, nie możesz zmieniać jego zawartości.

Opcjonalnie możesz poprosić odbiorcę o przesłanie wiadomości e-mail dalej do innych osób, które nie zostały uwzględnione w oryginalnej wiadomości e-mail. Nawet jeśli te inne osoby pracują w organizacji, która ma usługę Azure Rights Management, lub zarejestrują własną subskrypcję usługi RMS dla użytkowników indywidualnych, nie będą mogły otworzyć załącznika. Gdy otrzymają monit o nazwę użytkownika, nastąpi odmowa dostępu do dokumentu.

Teraz po otwarciu załącznika przez odbiorcę (opcjonalnie po jego przesłaniu do innej osoby) możesz oczekiwać na powiadomienie e-mail z raportem o tym działaniu. Jednak wiadomości e-mail mogą się z czasem zagubić, dlatego lepszym sposobem na śledzenie dostępu do dokumentu jest użycie witryny śledzenia dokumentu. Metoda ta jest omówiona w ostatnim kroku samouczka.

|Jeśli potrzebujesz dodatkowych informacji|Dodatkowe informacje|
|--------------------------------|--------------------------|
|Pełne instrukcje dotyczące wyświetlania plików chronionych przez usługę Azure Rights Management →|[Wyświetlanie i używanie plików chronionych przez usługę Rights Management](../rms-client/sharing-app-view-use-files.md)|
|Informacje dotyczące bezpłatnej subskrypcji usługi RMS dla użytkowników indywidualnych →|[Usługa RMS dla użytkowników indywidualnych i usługa Azure Rights Management](../understand-explore/rms-for-individuals.md)|
|Informacje dotyczące dwóch wersji pliku, które widać w załączniku do wiadomości e-mail →|[Co to za plik ppdf, który jest automatycznie tworzony?](../rms-client/sharing-app-dialog-box.md)|



<!--HONumber=Jul16_HO3-->


