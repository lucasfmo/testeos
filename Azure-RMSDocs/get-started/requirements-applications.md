---
title: "Wymagania dotyczące usługi Azure RMS: aplikacje | Azure RMS"
description: 
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 08/15/2016
ms.topic: get-started-article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 7b33bcb8-63da-46be-ad56-b06de97822fa
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b02be530af8ee1bc1e5d5f16275d2fb28e2134b7
ms.openlocfilehash: a885ab6deaf874a8c66623c34eddc2b2778e0005


---


# Wymagania dotyczące usługi Azure RMS: aplikacje

*Dotyczy usług: Azure Rights Management, Office 365*


Skorzystaj z poniższej tabeli, aby zidentyfikować aplikacje, które w sposób natywny obsługują usługę Azure RMS, co oznacza, że usługa RMS została ściśle zintegrowana z tymi aplikacjami za pomocą interfejsów API usługi RMS i obsługuje ograniczenia użycia. Te aplikacje są również znane jako aplikacje obsługujące usługę RMS.

O ile nie wskazano inaczej, obsługiwane możliwości dotyczą zarówno usługi Azure RMS, jak i AD RMS. Ponadto obsługa usług AD RMS w systemach iOS, Android, OS X i Windows Phone 8.1 wymaga [rozszerzenia usług Active Directory Rights Management Services dla urządzeń przenośnych](https://technet.microsoft.com/library/dn673574.aspx).

Informacje dotyczące kolumn tabeli:

-   **Chroniony plik PDF:** pliki, które mają rozszerzenie nazwy PPDF i są tworzone automatycznie podczas używania aplikacji RMS sharing do udostępniania plików pakietu Office i plików PDF pocztą e-mail. Aplikacja RMS sharing zawiera czytnik chronionych plików PDF. Jeśli wcześniej utworzono pliki PDF chronione za pomocą usługi Azure RMS lub AD RMS, można nadal odczytywać je na urządzeniach z systemem Windows, iOS lub Android przy użyciu programów Foxit Reader i Nitro Pro.

-   **Poczta e-mail:** klienci poczty e-mail z listy mogą chronić wiadomości e-mail, które będą automatycznie chronić wszystkie dołączone pliki. W tym scenariuszu funkcja podglądu klienta umożliwia wyświetlanie chronionej zawartości (wiadomości i załączników) autoryzowanym odbiorcom. Jednak jeśli sama wiadomość e-mail nie jest chroniona, ale załącznik jest, funkcja podglądu klienta nie ma możliwości wyświetlania chronionego załącznika autoryzowanym odbiorcom.

-   **Inne typy plików:** pliki tekstowe i pliki obrazów mają następujące rozszerzenia nazw: TXT, XML, JPG i JPEG. Rozszerzenia nazw tych plików zmieniają się po objęciu plików natywną ochroną zapewnianą przez usługę RMS, a pliki stają się plikami tylko do odczytu. Pliki, które nie mogą być chronione w sposób natywny, mają rozszerzenie nazwy pliku PFILE, oznaczające, że zostały objęte ogólną ochroną przez usługę RMS. Aby uzyskać więcej informacji, zobacz [Przewodnik administratora aplikacji do udostępniania usługi Rights Management](../rms-client/sharing-app-admin-guide.md).


|**System operacyjny urządzenia**|Word, Excel, PowerPoint|Chroniony plik PDF|Poczta e-mail|Inne typy plików|
|-------------------------------|---------------------------|-----------------|---------|--------------------|
|**Windows**|Pakiet Office 2010<br /><br />Office 2013<br /><br />Office 2016 <br /><br />Aplikacje mobilne pakietu Office (tylko usługa Azure RMS) [[1]](#footnote-1)<br /><br />Office Online [[2]](#footnote-2)|Gaaiho Doc<br /><br />GigaTrust Desktop PDF Client for Adobe<br /><br />Foxit Reader<br /><br />Nitro PDF Reader<br /><br />Aplikacja do udostępniania usługi RMS|Outlook 2010<br /><br />Outlook 2013<br /><br />Office 2016 <br /><br />Outlook Web App (OWA) [[3]](#footnote-3)<br /><br />Poczta systemu Windows [[4]](#footnote-4)|Aplikacja RMS sharing dla systemu Windows: tekst, obrazy, plik PFILE<br /><br />Siemens JT2Go: pliki JT (tylko Windows 10)|
|**iOS**|Pakiet Office dla urządzeń iPad i iPhone [[5]](#footnote-5)<br /><br />Office Online [[2]](#footnote-2)<br /><br />TITUS Docs|Foxit Reader<br /><br />Aplikacja RMS sharing [[1]](#footnote-1)<br /><br />TITUS Docs|Citrix WorxMail [[6]](#footnote-6)<br /><br />NitroDesk [[4]](#footnote-4)<br /><br />Program Outlook dla urządzeń iPad i iPhone [[4]](#footnote-4)<br /><br />OWA dla systemu iOS [[3]](#footnote-3)<br /><br />TITUS Mail|Aplikacja RMS sharing [[1]](#footnote-1): tekst, obrazy, plik PFILE<br /><br />TITUS Docs: plik PFILE|
|**Android**|Aplikacja GigaTrust dla systemu Android<br /><br />Office Online (tylko Azure RMS) [[2]](#footnote-2)<br /><br />Office Mobile [[1]](#footnote-1)|Aplikacja GigaTrust dla systemu Android<br /><br />Foxit Reader<br /><br />Aplikacja RMS sharing [[1]](#footnote-1)|9Folders [[4]](#footnote-4)<br /><br />Aplikacja GigaTrust dla systemu Android [[4]](#footnote-4)<br /><br />Citrix WorxMail [[6]](#footnote-6)<br /><br />NitroDesk [[4]](#footnote-4)<br /><br />Aplikacja Outlook dla systemu Android [[4]](#footnote-4)<br /><br />OWA dla systemu Android [[3]](#footnote-3) i [[7]](#footnote-7)<br /><br />Poczta e-mail Samsung (urządzenia S3 i nowsze) [[7]](#footnote-7)<br /><br />TITUS Classification for Mobile|Aplikacja RMS sharing [[1]](#footnote-1): tekst, obrazy, plik PFILE|
|**OS X**|Office 2011 (tylko usługi AD RMS)<br /><br />Office 2016 dla komputerów Mac<br /><br />Office Online [[2]](#footnote-2)|Foxit Reader<br /><br />Aplikacja RMS sharing [[1]](#footnote-1)|Outlook 2011 (tylko usługi AD RMS)<br /><br />Outlook 2016 dla komputerów Mac<br /><br />Outlook dla komputerów Mac|Aplikacja RMS sharing [[1]](#footnote-1): tekst, obrazy, plik PFILE|
|**Windows 10 Mobile**|Aplikacje mobilne pakietu Office (tylko usługa Azure RMS) [[1]](#footnote-1)|Nieobsługiwane|Citrix WorxMail [[6]](#footnote-6)<br /><br />Poczta programu Outlook|Nieobsługiwane|
|**Windows RT**|Office 2013 RT<br /><br />Office Online [[2]](#footnote-2)|Nieobsługiwane|Outlook 2013 RT<br /><br />Aplikacja poczty dla systemu Windows<br /><br />Poczta systemu Windows [[4]](#footnote-4)|Siemens JT2Go: pliki JT|
|**Windows Phone 8,1**|Office Mobile (tylko usługi AD RMS)|Aplikacja RMS sharing [[1]](#footnote-1)|Outlook Mobile [[4]](#footnote-4)|Aplikacja RMS sharing [[1]](#footnote-1): tekst, obrazy, plik PFILE|
|**Blackberry 10**|Nieobsługiwane|Nieobsługiwane|Poczta e-mail Blackberry [[4]](#footnote-4)|Nieobsługiwane|


###### Przypis 1
Obsługuje wyświetlanie zawartości chronionej.

###### Przypis 2 
Obsługuje wyświetlanie zawartości chronionej w usłudze SharePoint Online, usłudze OneDrive dla Firm i programie Outlook Web Access.

###### Przypis 3
Jeśli adresat ma skrzynkę pocztową w lokalnym programie Exchange i otrzyma chronioną wiadomość e-mail, jej zawartość będzie można otworzyć tylko w zaawansowanym kliencie poczty e-mail, takim jak program Outlook.  Nie będzie można użyć do tego programu Outlook Web Access.

###### Przypis 4
Używa funkcji Exchange ActiveSync IRM, którą musi włączyć administrator programu Exchange. Użytkownicy mogą przeglądać chronione wiadomości e-mail, odpowiadać nadawcy i opowiadać wszystkim nadawcom, ale nie mogą chronić nowych wiadomości e-mail.

Jeśli adresat ma skrzynkę pocztową w lokalnym programie Exchange i otrzyma chronioną wiadomość e-mail z innej organizacji, która korzysta z programu Exchange, jej zawartość będzie można otworzyć tylko w zaawansowanym kliencie poczty e-mail, takim jak program Outlook.  Nie można jej otworzyć w urządzeniu, na którym jest używana funkcja Exchange Active Sync IRM.

###### Przypis 5
Obsługuje wyświetlanie i edytowanie chronionych dokumentów. Aby uzyskać więcej informacji, zobacz następujący wpis w blogu pakietu Office: [Azure Rights Management support comes to Office for iPad and iPhone](https://blogs.office.com/2015/07/22/azure-rights-management-support-comes-to-office-for-ipad-and-iphone-2/) (Obsługa usługi Azure Rights Management dołączana do pakietu Office dla urządzeń iPad i iPhone).

###### Przypis 6
Aby uzyskać więcej informacji, zobacz [dokumentację produktu WorxMail](http://docs.citrix.com/en-us/worx-mobile-apps/10/xmob-worx-mail.html) firmy Citrix.

###### Przypis 7
Aby uzyskać więcej informacji, zobacz następujący wpis na blogu pakietu Office: [OWA for Android now available on select devices](http://blogs.office.com/2014/06/11/owa-for-android-now-available-on-select-devices/) (Program OWA dla systemu Android teraz dostępny na wybranych urządzeniach).

## Więcej informacji na temat obsługi usługi Azure RMS dla pakietu Office

Usługa Azure RMS jest ściśle zintegrowana z aplikacjami Word, Excel, PowerPoint i Outlook, w których ta funkcja jest często określana jako Zarządzanie prawami do informacji (IRM, Information Rights Management). Następujące wersje klienta pakietu Office obsługują ochronę plików i wiadomości e-mail przy użyciu usługi Azure RMS:

- Office Professional Plus 2016

- Office Professional Plus 2013

- Office Professional Plus 2010

Wszystkie wersje pakietu Office (z wyjątkiem pakietu Office 2007) obsługują chronioną zawartość.

Usługa Azure RMS z pakietem Office Professional Plus 2010 lub Office Professional 2010:

- Wymaga aplikacji do udostępniania usługi Rights Management dla systemu Windows

- Nieobsługiwana w systemie Windows 10


## Więcej informacji na temat aplikacji do udostępniania usługi Rights Management

Aby uzyskać więcej informacji o aplikacji do udostępniania usługi Rights Management, zobacz następujące zasoby:

-   [Przewodnik administratora aplikacji do udostępniania usługi Rights Management](../rms-client/sharing-app-admin-guide.md)

-   [Podręcznik użytkownika aplikacji do udostępniania usługi Rights Management](../rms-client/sharing-app-user-guide.md)

Aby uzyskać więcej informacji o aplikacji do udostępniania usługi Rights Management dla platform urządzeń przenośnych, zobacz następujące zasoby:

-   Pobierz odpowiednią aplikację za pomocą linków na [stronie usługi Microsoft Rights Management](http://go.microsoft.com/fwlink/?LinkId=303970)

-   Jeśli masz usługę Microsoft Intune, możesz wdrożyć aplikację i zarządzać nią przy użyciu aplikacji zarządzanej przez zasady: 

    -   W przypadku urządzeń z systemem iOS lub Android zarejestrowanych przez usługę Intune: [Konfigurowanie i wdrażanie zasad zarządzania aplikacjami mobilnymi w konsoli usługi Microsoft Intune](/intune/deploy-use/configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console)

    -   W przypadku urządzeń z systemem Android, które nie są zarejestrowane przez usługę Intune: [Tworzenie i wdrażanie zasad zarządzania aplikacjami mobilnymi przy użyciu usługi Microsoft Intune](/intune/deploy-use/create-and-deploy-mobile-app-management-policies-with-microsoft-intune)

-   [Często zadawane pytania dotyczące aplikacji do udostępniania usługi Microsoft Rights Management dla platform urządzeń przenośnych](https://technet.microsoft.com/dn451248)



## Więcej informacji o innych aplikacjach, które obsługują usługę Azure RMS

Oprócz aplikacji wyszczególnionych w tabeli, z usługą Azure RMS można integrować każdą aplikację obsługującą interfejsy API usługi RMS, w tym:

- Aplikacje biznesowe, które są zapisywane we własnym zakresie za pomocą zestawu RMS SDK

- Aplikacje od dostawców oprogramowania, które zostały napisane przy użyciu zestawu RMS SDK

Aby uzyskać więcej informacji o zestawie SDK, zobacz artykuł [Zestaw Microsoft Rights Management SDK](../develop/developers-guide.md).

## Aplikacje, które nie są obsługiwane przez usługi Azure RMS

Następujące aplikacje nie są obecnie obsługiwane przez usługę Azure RMS:

-   Microsoft Office 2011 dla komputerów Mac

-   Microsoft OneDrive dla Firm dla programu SharePoint Server 2013

-   Przeglądarka plików XPS
 
Ponadto aplikacja RMS sharing ma następujące ograniczenia:

-   W przypadku komputerów z systemem Windows: wymaga co najmniej systemu Windows 7 z dodatkiem Service Pack 1



## Następne kroki
Aby sprawdzić pozostałe wymagania, zobacz [Wymagania dotyczące usługi Azure Rights Management](requirements-azure-rms.md).

Aby uzyskać informacje o współpracy najczęściej używanych aplikacji z usługą Azure RMS, zobacz artykuł [Jak aplikacje obsługują usługę Azure Rights Management](../understand-explore/applications-support.md).

Informacje o sposobach konfigurowania najczęściej używanych aplikacji dla usługi Azure RMS opisano w temacie [Konfigurowanie aplikacji dla usługi Azure Rights Management](../deploy-use/configure-applications.md).


<!--HONumber=Aug16_HO3-->


