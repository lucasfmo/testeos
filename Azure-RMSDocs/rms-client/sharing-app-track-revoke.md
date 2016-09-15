---
title: "Śledzenie i odwoływanie dokumentów podczas używania aplikacji RMS sharing | Azure RMS"
description: 
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 08/10/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 61f349ce-bdd2-45c1-acc5-bc83937fb187
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: e9ad2e518b4a7dac608572eb5eb2d99bbda4754e
ms.openlocfilehash: 4c757494a1fe948ed26b32f86844f7b5896c919b


---

# Śledzenie i odwoływanie dokumentów podczas używania aplikacji RMS sharing

*Dotyczy: Azure Rights Management, Windows 10, Windows 7 z dodatkiem SP1, Windows 8, Windows 8.1*

Po zapewnieniu ochrony dokumentów przy użyciu aplikacji RMS sharing, jeśli organizacja korzysta z usługi Azure Rights Management zamiast Usług Active Directory Rights Management, można sprawdzić, w jaki sposób użytkownicy korzystają z chronionych dokumentów. W razie konieczności można także cofnąć dostęp do tych dokumentów, aby zatrzymać ich udostępnianie. W tym celu należy użyć **witryny śledzenia dokumentów** dostępnej z komputerów z systemem Windows, komputerów Mac, a nawet tabletów i telefonów.

<div style="padding-top: 56.25%; position: relative; width: 100%;">
<iframe style="position: absolute;top: 0;left: 0;right: 0;bottom: 0;" width="100%" height="100%" src="https://channel9.msdn.com/Series/Information-Protection/Azure-RMS-Document-Tracking-and-Revocation/player" frameborder="0" allowfullscreen></iframe>
</div>

Po uzyskaniu dostępu do tej witryny zaloguj się, aby śledzić swoje dokumenty. Jeśli Twoja organizacja ma [subskrypcję obsługującą śledzenie i odwoływanie dokumentów](https://technet.microsoft.com/dn858608.aspx) oraz masz licencję na tę subskrypcję, możesz sprawdzić, kto próbował otworzyć zabezpieczone pliki i czy próba ta zakończyła się powodzeniem (nastąpiło pomyślne uwierzytelnienie). Rejestrowana jest także data i godzina próby otwarcia dokumentu oraz lokalizacja tego zdarzenia. Ponadto:

-   Jeśli chcesz zatrzymać udostępnianie dokumentu: kliknij pozycję **Odwołaj dostęp**, podaj okres, przez jaki dokument będzie jeszcze dostępny, i zdecyduj, czy chcesz powiadomić o odwołaniu dostępu osoby, którym dokument był wcześniej udostępniony. Jeśli się na to zdecydujesz, przygotuj niestandardową wiadomość dla nich. Odwołanie udostępnionego dokumentu nie powoduje jego usunięcia, ale blokuje możliwość otwierania go przez autoryzowanych użytkowników.

-   Jeśli chcesz wyeksportować plik do programu Excel: kliknij pozycję **Eksportuj do pliku CSV**, aby móc modyfikować dane i tworzyć własne widoki oraz wykresy.

-   Jeśli chcesz skonfigurować powiadomienia e-mail: kliknij pozycję **Ustawienia** i zdecyduj, czy chcesz otrzymywać pocztą e-mail powiadomienia o dostępie do dokumentu.

- Jeśli chcesz śledzić i odwoływać dokumenty udostępnione innym: administratorzy usługi Azure RMS mogą śledzić i odwoływać dokumenty dla innych użytkowników, klikając ikonę administratora. Ta ikona jest widoczna tylko dla administratorów.

-   Jeśli masz pytania lub chcesz wyrazić swoją opinię na temat witryny śledzenia dokumentów: kliknij ikonę Pomoc, aby uzyskać dostęp do artykułu [Często zadawane pytania dotyczące śledzenia dokumentów](http://go.microsoft.com/fwlink/?LinkId=523977).

## Dostęp do witryny śledzenia dokumentów za pomocą pakietu Office

-   W przypadku aplikacji pakietu Office (Word, Excel i PowerPoint): na karcie **Narzędzia główne** w grupie **RMS** kliknij pozycję **Udostępnij chronione**, a następnie kliknij pozycję **Śledź użycie**.

    ![Śledzenie użycia z poziomu aplikacji pakietu Office w przypadku korzystania z aplikacji RMS sharing ](../media/ADRMS_MSRMSApp_OfficeToolbarTrackUsage.png)

-   W programie Outlook: na karcie **Narzędzia główne** w grupie **RMS** kliknij pozycję **Śledź użycie**:

    ![Wybierz opcję Śledź użycie w programie Outlook w przypadku korzystania z aplikacji RMS sharing ](../media/ADRMS_MSRMSApp_OutlookTrackUsage.png)

Jeśli te opcje usług RMS nie są wyświetlone, możliwe, że aplikacja RMS sharing nie jest zainstalowana na danym komputerze, nie zainstalowano najnowszej wersji albo trzeba ponownie uruchomić komputer w celu ukończenia instalacji. Aby uzyskać więcej informacji na temat sposobu instalowania aplikacji do udostępniania, zobacz [Pobieranie i instalowanie aplikacji do udostępniania usługi Microsoft Rights Management](install-sharing-app.md).

> [!NOTE] 
> Jeśli zainstalowano wersję zapoznawczą [klienta usługi Azure Information Protection](../information-protection/info-protect-client.md) w wersji 1.0.233 lub nowszej, możesz także uzyskać dostęp do witryny śledzenia dokumentów przy użyciu przycisku **Chroń**: 
> 
> - W aplikacji pakietu Office na karcie **Narzędzia główne** w grupie **Ochrona** kliknij kolejno pozycje **Chroń** > **Śledź użycie**. 

### Inne metody śledzenia i odwoływania dokumentów
Oprócz śledzenia dokumentów na komputerach z systemem Windows przy użyciu aplikacji pakietu Office można użyć także następujących alternatyw:

-   **W przeglądarce sieci Web**: ta metoda działa w przypadku wszystkich obsługiwanych urządzeń.

-   **W Eksploratorze plików**: ta metoda działa na komputerach z systemem Windows.

-   **W wiadomości e-mail programu Outlook**: ta metoda działa na komputerach z systemem Windows.

#### Otwieranie witryny śledzenia dokumentów za pomocą przeglądarki sieci Web

-   Przy użyciu obsługiwanej przeglądarki przejdź do [witryny śledzenia dokumentów](http://go.microsoft.com/fwlink/?LinkId=529562).

    Obsługiwane przeglądarki: zaleca się korzystanie z przeglądarki Internet Explorer w wersji 10 lub nowszej, jednak dostęp do witryny śledzenia dokumentów można uzyskać przy użyciu dowolnej z poniższych przeglądarek:

    -   Internet Explorer: wersja 10 lub nowsza

    -   Internet Explorer 9 z poprawką MS12-037: zbiorcza aktualizacja zabezpieczeń programu Internet Explorer z 12 czerwca 2012 r.

    -   Mozilla Firefox: wersja 12 lub nowsza

    -   Apple Safari 5: wersja 5 lub nowsza

    -   Google Chrome: wersja 18 lub nowsza

#### Otwieranie witryny śledzenia dokumentów za pomocą Eksploratora plików

-   Kliknij plik prawym przyciskiem myszy, wybierz pozycję **Chroń za pomocą usługi RMS**, a następnie wybierz pozycję **Śledź użycie**:

    ![Wybierz opcję Śledź użycie w Eksploratorze w przypadku korzystania z aplikacji RMS sharing](../media/ADRMS_MSRMSApp_ExplorerTrackUsage.png)

#### Dostęp do witryny śledzenia dokumentów za pomocą wiadomości e-mail programu Outlook

-   W wiadomości e-mail na karcie **Wiadomość** w grupie **RMS** kliknij pozycję **Udostępnij chronioną zawartość**, a następnie kliknij pozycję **Śledź użycie**:

    ![Wybierz opcję Śledź użycie w programie Outlook w przypadku korzystania z aplikacji RMS sharing](../media/ADRMS_MSRMSApp_OutlookMessageTrackUsage.png)

## Przykłady i inne instrukcje
Aby uzyskać instrukcje i przykłady dotyczące korzystania z aplikacji do udostępniania usługi Rights Management, zapoznaj się z następującymi sekcjami podręcznika użytkownika aplikacji do udostępniania usługi Rights Management:

-   [Przykłady korzystania z aplikacji RMS sharing](sharing-app-user-guide.md#examples-for-using-the-rms-sharing-application)

-   [Co chcesz zrobić?](sharing-app-user-guide.md#what-do-you-want-to-do)

## Zobacz też
[Podręcznik użytkownika aplikacji do udostępniania usługi Rights Management](sharing-app-user-guide.md)



<!--HONumber=Aug16_HO2-->


