![Samouczek Szybki start — krok 1](../media/AzRMS_QuickStartSteps1.PNG)

Twoja subskrypcja może obsługiwać usługę Azure Rights Management, jednak domyślnie jest ona wyłączona. Możesz ją aktywować przy użyciu centrum administracyjnego usługi Office 365 lub klasycznego portalu Azure:

-   Jeśli masz subskrypcję usługi Office 365 obejmującą usługę Azure Rights Management albo subskrypcję usługi Office 365 bez usługi Azure Rights Management, ale z usługą Azure RMS Premium: **użyj centrum administracyjnego usługi Office 365**.

-   Jeśli nie masz subskrypcji usługi Office 365: **użyj klasycznego portalu Azure**.

![Klasyczny portal Azure](../media/AzRMS_Tutorial_1_Screenshots.png)

#### Aby aktywować usługę Rights Management w centrum administracyjnym usługi Office 365

1.  Przejdź do [portalu usługi Office 365](https://portal.office.com/) i zaloguj się przy użyciu konta służbowego.

2.  Jeśli centrum administracyjne usługi Office 365 nie zostanie wyświetlone automatycznie, wybierz ikonę uruchamiania aplikacji w lewym górnym rogu i wybierz pozycję **Administrator**. Kafelek **Administrator** jest widoczny tylko dla administratorów usługi Office 365.

    > [!TIP]
    > Aby uzyskać pomoc dotyczącą centrum administracyjnego, zobacz [Centrum administracyjne usługi Office 365 — pomoc administratora](https://support.office.com/article/About-the-Office-365-admin-center-Admin-Help-58537702-d421-4d02-8141-e128e3703547).

3.  W okienku po lewej stronie rozwiń węzeł **USTAWIENIA USŁUGI**.

4.  Kliknij pozycję **Rights Management**.

5.  Na stronie **RIGHTS MANAGEMENT** kliknij pozycję **Zarządzaj**.

6.  Na stronie **Rights Management** kliknij pozycję **Aktywuj**.

7.  Po wyświetleniu monitu **Czy chcesz aktywować usługę Rights Management?** kliknij pozycję **Aktywuj**.

Zostanie wyświetlony komunikat **Usługa Rights Management została aktywowana** wraz z opcją dezaktywowania tej usługi (może być konieczne ręczne odświeżenie strony).

Tym razem nie klikaj pozycji **Funkcje zaawansowane**. Kliknięcie tej pozycji spowoduje wyświetlenie klasycznego portalu Azure umożliwiającego konfigurowanie szablonów, które nie są potrzebne w tym samouczku. Zamiast tego możesz zamknąć centrum administracyjne usługi Office 365.

#### Aby aktywować usługę Rights Management w portalu platformy Azure

1.  Przejdź do [klasycznego portalu Azure](http://go.microsoft.com/fwlink/p/?LinkID=275081) i zaloguj się.

2.  W okienku po lewej stronie kliknij pozycję **ACTIVE DIRECTORY**.

3.  Na stronie **Active Directory** kliknij pozycję **RIGHTS MANAGEMENT**.

4.  Wybierz katalog do zarządzania dla usługi [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)], kliknij pozycję **AKTYWUJ**, a następnie potwierdź akcję.

**STAN USŁUGI RIGHTS MANAGEMENT** powinien być teraz ustawiony na **Aktywna**, a opcja **AKTYWUJ** zostaje zastąpiona opcją **DEZAKTYWUJ**.

W portalu można skonfigurować inne opcje usługi Rights Management, ale nie są one potrzebne w tym samouczku, dlatego możesz zamknąć klasyczny portal Azure.

To wszystko, co musisz zrobić w pierwszym kroku. Usługa została aktywowana i wszyscy użytkownicy w organizacji mogą teraz chronić ważne i poufne dokumenty. W środowisku produkcyjnym warto ograniczyć, kto może początkowo korzystać z tej funkcji, aby przeprowadzić wdrażanie etapowe. Jednak nie jest to konieczne w przypadku tego samouczka.

W przypadku wdrożenia produkcyjnego prawdopodobnie konieczne będzie również skonfigurowanie szablonów niestandardowych, które nie zostały uwzględnione w tym samouczku. Szablony ułatwiają użytkownikom szybkie stosowanie odpowiednich ustawień, gdy konieczna jest ochrona plików. Podczas aktywowania usługi Rights Management użytkownik automatycznie otrzymuje 2 szablony domyślne, które zazwyczaj uzupełnia własnymi szablonami niestandardowymi w środowisku produkcyjnym. Szablony nie są jednak potrzebne w tym samouczku, dlatego możesz teraz przejść do następnego kroku.

|Jeśli potrzebujesz dodatkowych informacji|Dodatkowe informacje|
|--------------------------------|--------------------------|
|Informacje na temat aktywowania usługi Rights Management i określania, kto może chronić pliki i wysyłać wiadomość e-mail po aktywowaniu usługi →|[Aktywacja usługi Azure Rights Management](../deploy-use/activate-azure-classic.md)|
|Informacje na temat szablonów domyślnych i tworzenia nowych szablonów niestandardowych →|[Konfigurowanie szablonów niestandardowych usługi Azure Rights Management](../deploy-use/create-template.md)|


<!--HONumber=Jul16_HO3-->


