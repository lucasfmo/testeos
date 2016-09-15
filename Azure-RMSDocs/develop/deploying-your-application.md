---
title: "Wdrażanie aplikacji | Azure RMS"
description: "Ten temat przedstawia opcje wdrażania aplikacji z obsługą praw i przeprowadza Cię przez ten proces"
keywords: 
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 4B785564-6839-49ED-A243-E2A6DFF88B2E
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 04454886841fe7b3482d10e1e32422f28d1c434f
ms.openlocfilehash: 40eb6628f5204d422bf304f44d64cdf0dcd8537d


---

# Wdrażanie w środowisku produkcyjnym


Ten temat przedstawia opcje wdrażania aplikacji z obsługą praw i przeprowadza Cię przez ten proces.

## Żądanie produkcyjnej umowy licencyjnej

 Aby można było wydać aplikację utworzoną za pomocą zestawu Rights Management Services SDK 2.1, należy najpierw złożyć wniosek o zawarcie produkcyjnej umowy licencyjnej w celu uzyskania certyfikatu produkcyjnego.

Certyfikat można uzyskać, wnioskując o produkcyjną umowę licencyjną.

Wyślij wiadomość e-mail na adres [RMLA@microsoft.com](mailto:rmla@microsoft.com) i podaj następujące informacje:

- Pełna nazwa firmy
- Fizyczny adres firmy (w tym miejscowość, stan, kraj lub region, kod pocztowy)
- Firmowy adres korespondencyjny (w tym miejscowość, stan, kraj lub region, kod pocztowy)
- Numer telefonu i faksu firmy
- Adres URL firmy
- Kraj lub region włączenia
- Nazwa aplikacji lub produktu
- Imię i nazwisko osoby żądającej
- Tytuł lub stanowisko osoby żądającej
- Adres e-mail osoby żądającej

Chociaż konto e-mail nie jest ścisłym wymogiem, proces aplikacji zazwyczaj polega na komunikacji za pośrednictwem poczty e-mail. Możesz uzyskać bezpłatne konto e-mail na stronie Outlook.com firmy Microsoft. Jeśli nie masz konta i nie chcesz go zakładać, możesz wysłać drukowane zgłoszenie na następujący adres:

      Active Directory Rights Management License Agreements (ADRMLA)

      Microsoft Corporation

      One Microsoft Way

      Redmond, WA 98052-6399

Podczas wnioskowania o umowę wykonaj następujące czynności:
- Prześlij informacje w języku angielskim w takiej formie, w jakiej powinny pojawić się na umowie.
- Prześlij wszystkie wymagane informacje. Brakujące lub niekompletne informacje mogą opóźnić proces przetwarzania żądania.

Zespół Active Directory Rights Management Licensing Agreement (ADRMLA) będzie odpowiadać na żądania przesłane pocztą e-mail w ciągu trzech dni roboczych. Proces będzie dłuższy w przypadku żądań wysłanych tradycyjną pocztą. W odpowiedzi zawarty będzie formularz umowy licencyjnej oraz dalsze instrukcje. Przeczytaj, podpisz i odeślij wszystkie strony umowy do zespołu ADRMLA. Nie zmieniaj czcionek ani formatowania akapitów umowy licencyjnej.

Postępuj zgodnie z instrukcjami otrzymanymi od zespołu ADRMLA. Instrukcje zawierają listę elementów informacji cyfrowych wymaganych do spełnienia żądania certyfikatu. Postępując zgodnie z przekazanymi instrukcjami krok po kroku, zredukujesz opóźnienia.

Zespół ADRMLA prześle Ci certyfikat produkcyjny po jego utworzeniu. Należy pamiętać, że przesłanie certyfikatu w wiadomości e-mail może zająć zespołowi ADRMLA do 15 dni roboczych. Proces będzie dłuższy w przypadku komunikacji za pośrednictwem tradycyjnej poczty.


## Opcje instalacji i wymagania klienta Rights Management Services Client 2.1

Jeśli był używany zestaw SDK 2.1 usługi RMS, na komputerze użytkownika końcowego będzie trzeba wdrożyć program Active Directory Rights Management Services Client 2.1.

### Klient RMS Client 2.1

Klient RMS Client 2.1 to oprogramowanie przeznaczone dla komputerów klienckich pomagające chronić użycie informacji przepływających przez aplikacje korzystające z usług RMS i dostęp do tych informacji — w przypadku instalacji lokalnej lub instalacji w centrum danych firmy Microsoft.

Klient RMS Client 2.1 nie jest składnikiem systemu operacyjnego Windows. Klient RMS Client 2.1 jest dostarczany w formie pliku do opcjonalnego pobrania i może być (po potwierdzeniu i zaakceptowaniu umowy licencyjnej) dystrybuowany za darmo razem z aplikacjami innych firm, aby umożliwić klientom dostęp do zawartości, do której prawa dostępu są chronione przez użycie i wdrożenie serwerów usług RMS w danym środowisku.


> [!IMPORTANT]
> Klient AD RMS Client 2.1 jest powiązany z architekturą i musi odpowiadać architekturze docelowego systemu operacyjnego.


## Opcje instalacji klienta RMS Client 2.1

-   **Ponowna dystrybucja klienta RMS Client 2.1**

    Zalecanym podejściem jest dołączenie pakietu instalatora klienta RMS Client do aplikacji lub rozwiązania z wykorzystaniem preferowanej technologii instalacji. Klient RMS Client może być za darmo dystrybuowany i umieszczany w pakietach z innymi aplikacjami i rozwiązaniami IT.

    Istnieje możliwość interaktywnego instalowania klienta RMS Client 2.1 poprzez uruchomienie instalatora klienta RMS Client 2.1 lub jego zainstalowanie w trybie dyskretnym. Kroki integracji:

    -   Pobierz instalator klienta RMS Client 2.1
    -   Zintegruj uruchomienie instalatora klienta RMS Client 2.1 z instalatorem aplikacji

    Dwa dobre przykłady integracji klienta RMS Client 2.1 z aplikacją to pakiet instalatora zestawu RMS SDK 2.1 oraz pakiet Right Protected Folder Explorer. Spróbuj je zainstalować, aby zrozumieć zastosowane podejście.

-   **Ustawianie klienta RMS Client 2.1 jako warunek wstępny dla instalacji aplikacji**

    W takim przypadku utworzysz warunek wstępny, który spowoduje, że instalacja aplikacji zakończy się niepowodzeniem, jeśli klient RMS Client 2.1 nie będzie znajdował się na komputerze użytkownika końcowego.

    W przypadku braku klienta podaj komunikat o błędzie, z którego użytkownik dowie się, skąd pobrać kopię klienta RMS Client 2.1

    W przypadku obecności klienta przejdź do instalacji aplikacji.

## Włączanie Usług Azure Rights Management z aplikacją

> [!NOTE]
> W przypadku migracji do nowego modelu ADAL w celu uwierzytelniania nie trzeba instalować usługi SIA. Aby uzyskać więcej informacji, zobacz [Uwierzytelnianie ADAL dla aplikacji z obsługą usług RMS](adal-auth.md).
> Możliwe jest również **certyfikowanie aplikacji dla systemu Windows 10** — aktualizacja aplikacji umożliwiająca użycie uwierzytelniania ADAL zamiast asystenta logowania usługi online firmy Microsoft oferuje następujące możliwości: korzystanie z uwierzytelniania wieloskładnikowego i instalowanie klienta RMS Client 2.1 bez wymogu posiadania uprawnień administracyjnych na komputerze


Aby użytkownik końcowy mógł korzystać z usług Azure Rights Management Services, należy wdrożyć *Asystenta logowania w witrynie Online Services*. Jako deweloper aplikacji nie wiesz, czy użytkownik końcowy skorzysta z usługi RMS (lokalnie), czy usług Azure Rights Management (usługa w chmurze).


> [!IMPORTANT]
> Jeśli aplikacja kliencka będzie uruchamiana za pomocą usług RMS na platformie Azure, konieczne będzie utworzenie własnych dzierżaw. Aby uzyskać więcej informacji, zobacz [Wymagania dotyczące usług Azure RMS: subskrypcje usług w chmurze, które obsługują usługi Azure RMS](../get-started/requirements-subscriptions.md).
> Aby uzyskać więcej informacji o współpracy z usługami Azure RMS, zobacz [Umożliwianie współpracy aplikacji usługi z usługami RMS opartymi na chmurze](how-to-use-file-api-with-aadrm-cloud.md).

-   Pobierz [Asystenta logowania w witrynie Microsoft Online Services](http://www.microsoft.com/en-us/download/details.aspx?id=28177) z Centrum pobierania Microsoft.
-   Upewnij się, że wdrożenie aplikacji z obsługą praw zawiera kontrolę warunków wstępnych dla tego wyboru usługi.
-   Aby uzyskać informacje o własnym testowaniu i wykorzystaniu usługi online przez użytkownika końcowego, zobacz temat TechNet [Konfiguracja usługi Rights Management](https://TechNet.Microsoft.Com/en-us/library/jj585002.aspx).

Aby uzyskać więcej informacji na temat umożliwiania aplikacji korzystania z usługi RMS na potrzeby usług Azure Rights Management, zobacz temat [Umożliwianie współpracy aplikacji z usługą RMS opartą na chmurze](how-to-use-file-api-with-aadrm-cloud.md).

## Tematy pokrewne

* [Asystent logowania w witrynie Microsoft Online Services](http://www.microsoft.com/en-us/download/details.aspx?id=28177)
* [Konfiguracja usługi Rights Management](https://TechNet.Microsoft.Com/en-us/library/jj585002.aspx)
* [Umożliwianie współpracy aplikacji z usługą RMS opartą na chmurze](how-to-use-file-api-with-aadrm-cloud.md)
 

 



<!--HONumber=Jul16_HO3-->


