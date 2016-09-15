---
title: "Nowości i informacje o wersji | Azure RMS"
description: "Spis ważnych zmian i funkcji w tej nowej wersji zestawu RMS SDK."
keywords: 
author: bruceperlerms
manager: mbaldwin
ms.date: 06/16/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 4fa1c686-b00b-4734-9abb-141ce582a6af
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 79397c82d9478cbd55630a376fe2d12f3873ebc4
ms.openlocfilehash: 8de1886adf322439721274e23452af75b4db2e00


---

# Nowości i informacje o wersji

## Co nowego
Zestaw Microsoft Rights Management SDK 4.2 umożliwia łatwiejsze i bardziej elastyczne włączanie aplikacji RMS. W tym temacie wymieniono ważne zmiany i funkcjonalności w tej nowej wersji zestawu RMS SDK.

-   [Nowości z czerwca 2016 r.](#new-for-June-2016)
-   [Aktualizacja z grudnia 2015 r.](#december-2015-update)
-   [Aktualizacja z lipca 2015 r. — dodaje obsługę systemu Linux / programowania w języku C++](#july-2015-update-adds-support-for-linux-c-developm)
-   [Aktualizacja z maja 2015 r. — dodaje sterowanie rejestrowaniem](#may-2015-update-adds-logging-control)
-   [Aktualizacja z lutego 2015 r. — dodaje obsługę aplikacji ze Sklepu Windows](#february-2015-update-adds-windows-store-application-support)
-   [Aktualizacja ze stycznia 2015 r. — dodaje obsługę platformy WinPhone](#january-2015-update-adds-winphone-platform-support)
-   [Aktualizacja z października 2014 r. — uaktualnienie do zestawu Microsoft RMS SDK 4.1](#october-2014-update-upgrade-to-microsoft-rms-sdk-4-1)
-   [Informacje o wersji](#release-notes)
-   [Często zadawane pytania](#frequently-asked-questions)

### Nowości z czerwca 2016 r.

- **Obsługa nowoczesnego uwierzytelniania** — umożliwi logowanie oparte na bibliotece uwierzytelniania usługi Active Directory (ADAL) do aplikacji z obsługą usługi RMS. Zostaną udostępnione opcje logowania, takie jak usługa Multi-Factor Authentication (MFA), oparci na języku SAML dostawcy tożsamości firm zewnętrznych z aplikacjami klienckimi usługi RMS oraz uwierzytelnianie oparte na kartach inteligentnych i certyfikatach. Równocześnie zostanie wyeliminowana potrzeba korzystania z protokołu uwierzytelniania podstawowego w aplikacjach z obsługą usługi RMS.
- **Obsługa śledzenia dokumentów** — deweloperzy mogą teraz włączać śledzenie dokumentów w przypadku objęcia ich ochroną w swoich aplikacjach. 
- Ulepszenia wydajności
- Poprawki


### Aktualizacja z grudnia 2015 r.

W tym wydaniu zestaw RMS SDK dla urządzeń ma wersję 4.2 i dodaje następujące funkcjonalności:

-   Śledzenie dokumentów, usługa RMS tylko w trybie online dla systemów operacyjnych iOS/OS X i Android.

    Aby uzyskać szczegółowe informacje i wskazówki dotyczące użycia w systemach iOS/OS X, zapoznaj się z klasą [**MSLicenseMetadata**](/rights-management/sdk/4.2/api/iOS/mslicensemetadata#msipcthin2_mslicensemetadata_class_objc), która dostarcza informacje dotyczące śledzenia, a także dodatkową metodą rejestrowania śledzenia dokumentów w zasadzie [**MSUserPolicy**](/rights-management/sdk/4.2/api/iOS/iOS#msipcthin2_msuserpolicy_interface_objc). Istnieją podobne dodatki dla systemu Android do klasy [**LicenseMetadata**](/rights-management/sdk/4.2/api/android/com.microsoft.rightsmanagement#msipcthin2_licensemetadata_interface_java) i zasady [**UserPolicy**](/rights-management/sdk/4.2/api/android/userpolicy).

    Aby uzyskać szczegółowy opis funkcjonalności śledzenia dokumentów, zobacz temat [**Porady: używanie śledzenia dokumentów**](how-to-use-document-tracking.md).

-   Zbiór metod synchronicznych, które w sposób równoległy realizują wersje asynchroniczne dla interfejsu API systemu Android:

    [**Metoda synchroniczna CustomProtectedInputStream.create**](/rights-management/sdk/4.2/api/android/customprotectedinputstream#msipcthin2_customprotectedinputstream_create_synchronous_method_java)

    [**Metoda synchroniczna CustomProtectedOutputStream.create**](/rights-management/sdk/4.2/api/android/customprotectedoutputstream#msipcthin2_customprotectedoutputstream_create_synchronous_method)

    [**Metoda synchroniczna ProtectedFileInputStream.create**](/rights-management/sdk/4.2/api/android/protectedfileinputstream#msipcthin2_protectedfileinputstream_create_synchronous_method)

    [**Metoda synchroniczna ProtectedFileOutputStream.create**](/rights-management/sdk/4.2/api/android/customprotectedoutputstream#msipcthin2_customprotectedoutputstream_create_synchronous_method)

    [**Metoda synchroniczna TemplateDescriptor.getTemplates**](/rights-management/sdk/4.2/api/android/templatedescriptor#msipcthin2_templatedescriptor_gettemplates_synchronous_method_java)

    [**Metoda synchroniczna UserPolicy.acquire**](/rights-management/sdk/4.2/api/android/userpolicy#msipcthin2_userpolicy_acquire_synchronous_method_java)

    [**Metoda synchroniczna UserPolicy.create (PolicyDescriptor...)**](/rights-management/sdk/4.2/api/android/userpolicy#msipcthin2_userpolicy_create_policydescriptor_______synchronous_method_java)

    [**Metoda synchroniczna UserPolicy.create (TemplateDescriptor...)**](/rights-management/sdk/4.2/api/android/userpolicy#msipcthin2_userpolicy_create_templatedescriptor_______synchronous_method_java)

-   Nowa klasa [**ProtectedBuffer**](/rights-management/sdk/4.2/api/android/com.microsoft.rightsmanagement#msipcthin2_protectedbuffer_class) została dodana do interfejsu API systemu Android.
-   Aktualizacje poprawiające komunikowanie błędów i rozwiązywanie problemów.
-   Znaczący wzrost wydajności operacji kryptograficznych.

### Aktualizacja z lipca 2015 r. — dodaje obsługę systemu Linux / programowania w języku C++

W tej wersji dodano następujące funkcjonalności:

-   Zestaw RMS SDK 4.1 dla platform Linux

    Aby uzyskać więcej informacji, zobacz temat [Rozpoczynanie pracy](get-started.md).

### Aktualizacja z maja 2015 r. — dodaje sterowanie rejestrowaniem

W tej wersji dodano obsługę następujących funkcjonalności:

-   iOS

    Szyfrowanie i deszyfrowanie aplikacji może działać niezależnie i równolegle.

    Aby uzyskać więcej informacji, zobacz klasę [**MSProtector**](/rights-management/sdk/4.2/api/iOS/iOS#msipcthin2_msprotector_class_objc).

    Włączono ustawienia kontroli poziomu dziennika.

    Aby uzyskać więcej informacji, zobacz temat [Porady: Włączanie rejestrowania błędów i wydajności](enabling-logging.md)

    Dodano obsługę czyszczenia pamięci podręcznej.

    Aby uzyskać więcej informacji, zobacz metodę [**MSProtection:resetStateWithCompletionBlock**](/rights-management/sdk/4.2/api/iOS/msprotection#msipcthin2_msprotection_resetstatewithcompletionblock_method_objc).

### Aktualizacja z lutego 2015 r. — dodaje obsługę aplikacji ze Sklepu Windows

W tym wydaniu dodano obsługę aplikacji ze Sklepu Windows, zapewniając funkcjonalność odpowiadającą wydaniom dla systemów Windows Phone, Android i iOS/OS zestawu RMS SDK 4.1.

### Aktualizacja ze stycznia 2015 r. — dodaje obsługę platformy WinPhone

W tym wydaniu dodano obsługę systemu Windows Phone, zapewniając funkcjonalność odpowiadającą wydaniom dla systemów Android i iOS/OS zestawu RMS SDK 4.1.

### Aktualizacja z października 2014 r. — uaktualnienie do zestawu Microsoft RMS SDK 4.1

W wydaniu wersji 4.1 zestawu RMS SDK dodano następujące nowe funkcjonalności do systemów Google Android i Apple iOS / OS X.

-   Rozszerzenia API zestawu SDK dla systemów Android i iOS/OS X dotyczące przetwarzania *zgody użytkownika*, umożliwiające potwierdzanie przez użytkownika działań zestawu SDK. Obecnie obsługiwanymi typami wyrażania zgody są śledzenie dokumentów i dostęp do nieznanych adresów URL usługi AD RMS.

    Aby uzyskać więcej informacji, zobacz jako przykład wersję [**interfejsu ConsentCallback**](/rights-management/sdk/4.2/api/android/com.microsoft.rightsmanagement#msipcthin2_consentcallback_interface_java) przeznaczoną dla interfejsu API systemu Android.

-   Systemy iOS 8 i OS X 10.10 (Yosemite) są teraz obsługiwane. Wprowadzono również kilka zmian nazw właściwości wymaganych przez Xcode 6.

    Na przykład nazwa właściwości MSUserPolicy.name została zmieniona na [**MSUserPolicy.policyName**](/rights-management/sdk/4.2/api/iOS/msuserpolicy#msipcthin2_msuserpolicy_name_property_objc).

## Informacje o wersji

W tej części przedstawiono istotne dla deweloperów informacje o bieżącym i poprzednich wydaniach interfejsów API zestawu Microsoft Rights Management SDK 4.x.

**Usługi AD RMS SDK 4.1 — wydanie z dostępnością globalną dla platform iOS / OS X i Android**

-   **Obsługa usług AD RMS** —administratorzy IT mogą używać aplikacji z włączoną usługą RMS na urządzeniach przenośnych z rozszerzeniami dla urządzeń przenośnych nowego serwera usług AD RMS.
-   **Użycie trybu offline** — użytkownicy końcowi mogą uzyskać dostęp do chronionych przez usługę RMS danych w trybie offline.
-   **Rozdzielone uwierzytelnianie** — deweloperzy mogą używać własnych bibliotek uwierzytelniania dla usług Azure RMS i AD RMS (lub używać zalecanej [biblioteki uwierzytelniania usługi Azure AD (ADAL)](https://MSDN.Microsoft.Com/library/jj573266.aspx)).
-   **Rozdzielony interfejs użytkownika** —deweloperzy mogą tworzyć interfejsy użytkownika, aby używać dokumentów chronionych przez usługę RMS i ochraniać je.
-   **Zmieniony interfejs API** — deweloperzy mogą korzystać z prostego i przejrzystego interfejsu API szyfrowania i odszyfrowywania, który zapewnia spójne działanie usługi RMS i interfejsu użytkownika przy minimalnym wysiłku.

**Wspólne dla wszystkich platform**

-   Interfejsy API zestawi RMS SDK 4.x nie są *bezpieczne wątkowo*.

**Android**

-   Korzystając z przykładowej aplikacji na urządzeniu z systemem Amazon® Kindle do wyświetlania załączników PTXT, należy najpierw pobrać plik zanim będzie się go wyświetlać.

    **Rozwiązanie** — jest to znany problem i zostanie rozwiązany później.

-   Aplikacja, która korzysta z zestawu SDK może ulec awarii w przypadku zezwolenia na działanie wielu wystąpień.

    **Rozwiązanie** — upewnij się, że aplikacja nie zezwala na wywołania interfejsu API systemu Android przez wiele wystąpień.

-   W razie użycia metody [**ProtectedFileOutputStream**](/rights-management/sdk/4.2/api/android/protectedfileoutputstream#msipcthin2_protectedfileoutputstream_class_java)**.write(byte\[\] array, int offset, int length)** z parametrem length różnym od wartości *array.length* późniejsze użycie zawartości za pomocą zestawu SDK jest niemożliwe.

    **Rozwiązanie** — jest to znany problem. Aby go unikać, albo zawsze przekazuj parametr **byte \[\]** array o długości odpowiadającej parametrowi length, albo używaj metody [**ProtectedFileOutputStream**](/rights-management/sdk/4.2/api/android/protectedfileoutputstream#msipcthin2_protectedfileoutputstream_class_java)**.write(byte\[\] array)**.

**iOS i OS X**

-   Istnieją dwa dialekty języka portugalskiego obsługiwane przez nasze zestawy SDK dla systemów operacyjnych iOS i OS X. Niestety z powodu usterki, obecnie nie obsługujemy całkowicie 1. lokalizacji. Z powodu tej usterki język portugalski nie jest w pełni obsługiwany. Przetłumaczono większość tekstu, ale nie interfejs użytkownika.

    1. portugalski

    2. Portugalski (Portugalia)

**Tylko system iOS**

-   Zestaw RMS SDK4.x nie pokazuje wskaźnika działania sieci.

    Jest to znane zachowanie opcjonalne systemu iOS zgodnie z dokumentem Apple Human Interface Guidelines.

**Tylko system OS X**

-   Zestaw RMS SDK4.x nie pokazuje wskaźnika działania sieci.

    Jest to znane zachowanie opcjonalne systemu OS X zgodnie z dokumentem Apple Human Interface Guidelines.

-   **Rozwiązanie** — aby utworzyć aplikację z interfejsem wielu dokumentów (MDI) za pomocą naszego zestawu OS X SDK, użyj poniższych wskazówek.

    Następujących metod nie wolno uruchamiać jednocześnie. Aby monitorować przebieg działania, użyj wspomnianego podejścia bloku ukończenia.

    - [**protectedDataWithProtectedFile**](/rights-management/sdk/4.2/api/iOS/msprotecteddata#msipcthin2_msprotecteddata_protecteddatawithprotectedfile_completionblock_method_objc)
    - [**customProtectedDataWithPolicy**](/rights-management/sdk/4.2/api/iOS/mscustomprotecteddata#msipcthin2_mscustomprotecteddata_customprotecteddatawithpolicy_protecteddata_contentstartposition_contentsize_completionblock_method_objc)



**Uwaga**  — aplikacje MDI nie są obsługiwane przez nasz interfejs API dla systemu iOS.

## Często zadawane pytania

**Wszystkie platformy**

**Pytanie**: nie widzę elementu wyboru **Uprawnienia niestandardowe** w interfejsie użytkownika w przepływie pracy ochrony. Dlaczego?

**Odpowiedź**: jest to znany problem i zostanie rozwiązany później.

**Pytanie**: jak uzyskać nowego organizacyjnego dzierżawcę, aby wypróbować zestaw SDK i przykładowe aplikacje?

**Odpowiedź**: wyślij wiadomość e-mail na adres <rmcstbeta@microsoft.com> z żądaniem poświadczeń dla organizacji testowych usługi Azure AD RMS.

**Pytanie**: w niniejszej dokumentacji nie widzę żadnych informacji o hierarchii testowej. Dlaczego?

**Odpowiedź**: w nowych zestawach AD RMS SDK nie obowiązuje koncepcja hierarchii testowej. Zawsze korzystasz z hierarchii produkcyjnej.

**Pytanie**: W wersji 2.1 zestawu RMS SDK dla każdej aplikacji implementującej ochronę informacji był potrzebny wygenerowany manifest. Czy obowiązuje to nadal wersji 4.0 i nowszych wersjach zestawu SDK?

**Odpowiedź**: nie, manifesty nie są już potrzebne w wersji 3.0 ani nowszych zestawu Rights Management SDK.

**Android**

**Pytanie**: w których środowiskach programistycznych został przetestowany zestaw SDK?

**Odpowiedź**: Eclipse Juno z interfejsem Google API 15 lub nowszym.

**Pytanie**: czy można wywołać metodę anulowani cancel() z wątku interfejsu użytkownika?
**Odpowiedź**: metodę cancel() należy wywoływać z wątku innego niż wątek interfejsu użytkownika, ponieważ może to przerwać połączenie sieciowe.

**iOS**

**Pytanie**: na których platformach sprawdzono programowanie z zestawem SDK?

**Odpowiedź**: Xcode 5.0 z systemem iOS 7 i nowszym.

**Pytanie**: po wywołaniu metody cancel() na operacji nadal otrzymuję powiadomienie, że operacja została ukończona. Dlaczego?

**Odpowiedź**: nie wszystkie operacje mogą zostać anulowane, więc operacja anulowania jest wykonywana w najlepszy możliwy sposób.

**OS X**

**Pytanie**: przykładowa platforma aplikacji została dostosowana do wersji Xcode 5. Czy mogę pracować z wersją Xcode 4.6?

**Odpowiedź**: OS X SDK współpracuje tylko z Xcode 4.6 i nowszymi wersjami, a także z systemem OS X 10.8 i nowszymi.

 

 



<!--HONumber=Jul16_HO4-->


