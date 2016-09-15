---
title: "Przewodnik dewelopera usług RMS | Azure RMS"
description: "Obecnie dostępne są trzy generacje zestawu Rights Management SDK."
keywords: 
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 0510ead4-2fe7-4269-885b-fe16bcc69888
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: f7dd88d90357c99c69fe4fdde67c1544595e02f8
ms.openlocfilehash: 6f8a475907347e545eb3ea46fecc04013fa74c5e


---

# Przewodnik dewelopera usług RMS

## Przegląd ##
Obecnie dostępne są trzy generacje zestawu Rights Management SDK: **zestaw Microsoft Rights Management SDK 4.2** dla systemu Android, iOS/OS X, urządzeń z systemem Windows i systemu Linux, **zestaw Microsoft Rights Management SDK 2.1** dla komputerów klienckich z systemem Windows oraz zastąpiony **zestaw AD RMS SDK**.

## Zestawy Software Development Kit ##
| SDK | Opis |
|------|---------|
| [RMS SDK 4.2](active-directory-rights-management-services-multi-platform-thin-client-sdk-portal.md) | Uproszczony zestaw narzędzi nowej generacji, zapewniający lekkie środowisko programistyczne dostarczające aplikacjom dla urządzeń z systemami Android, iOS, Mac OS X, Windows Phone/RT i Linux/C++ zabezpieczenia informacji za pośrednictwem usług Microsoft Rights Management |
| [RMS SDK 2.1](microsoft-information-protection-and-control-client-portal.md) | Zaawansowany zestaw SDK dla twórców aplikacji komputerowych dla systemu Windows i rozwiązań serwerowych, umożliwiający wprowadzenie w produktach zarządzania prawami|
|[Zestaw AD RMS SDK]()|** UWAGA ** — zestaw AD RMS SDK wykorzystujący funkcje udostępniane przez klienta w bibliotece Msdrm.dll jest dostępny do użytku w systemach Windows Server 2012, Windows 8, Windows Server 2008 R2, Windows 7, Windows Server 2008 i Windows Vista. Może on zostać zmieniony lub przestać być dostępny w kolejnych wersjach. Zamiast tego należy używać zestawu Microsoft Rights Management Services SDK 2.1 korzystającego z funkcji udostępnianych przez klienta w bibliotece Msipc.dll.|
|[Interfejs API obsługi skryptów usług AD RMS]()| Służy do tworzenia skryptów administrujących instalacją usług AD RMS|

## Przykłady kodu i narzędzia ##
Ta kolekcja przykładów kodu usług RMS i narzędzi wspierających twórców dostarczonych przez firmę Microsoft obejmuje wszystkie obsługiwane systemy operacyjne: Android, iOS/OS X, Windows Phone i Windows Desktop. Jest okresowo aktualizowana w celu zapewnienia zgodności z obsługiwanym zestawem SDK.

| Element | System operacyjny | Wersja pomocniczego zestawu SDK | Opis |
|------|------------------|------------------------|-------------|
| [Odczyt dokumentu PDF zabezpieczonego plikiem PFILE](https://blogs.msdn.microsoft.com/rms/2015/11/09/reading-a-pfile-protected-pdf/) | System Windows Desktop| [Zestaw RMS SDK 2.1](microsoft-information-protection-and-control-client-portal.md) i nowsze wersje zestawu SDK 2.x | **Odczyt dokumentu PDF zabezpieczonego plikiem PFILE** to prosty przykład kodu zamieszczony w naszym blogu RMS Developer's Corner, wykorzystujący interfejs API plików MSIPC do odszyfrowania i otwarcia dokumentu PDF zabezpieczonego plikiem PFILE.|
| [IpcManagedAPI](https://github.com/Azure-Samples/active-directory-dotnet-rms) | System Windows Desktop | [Zestaw RMS SDK 2.1](microsoft-information-protection-and-control-client-portal.md) i nowsze wersje zestawu SDK 2.x | **IpcManagedAPI** to reprezentacja .NET (C#) zestawu RMS SDK 2.1, ułatwiająca włączenie obsługi usługi RMS w aplikacji zarządzanej.|
| [IPCNotepad](https://code.msdn.microsoft.com/ipcnotepad-sample-f67dae80) | System Windows Desktop | [Zestaw RMS SDK 2.1](microsoft-information-protection-and-control-client-portal.md) i nowsze wersje zestawu SDK 2.x| **IPCNotepad** to przykładowa aplikacja obsługująca usługi RMS, prezentująca podstawowe kroki, które każda aplikacja obsługująca usługi RMS powinna wykonywać podczas chronienia i wykorzystywania zawartości ograniczonej.|
| [IpcDlp](https://github.com/Azure-Samples/active-directory-dotnet-rms)|System Windows Desktop|[Zestaw RMS SDK 2.1](microsoft-information-protection-and-control-client-portal.md) i nowsze wersje zestawu SDK 2.x|**IpcDlp** to przykładowa aplikacja Data Leak Protection (DLP) obsługująca usługi RMS, prezentująca podstawowe kroki, które każda aplikacja DLP obsługująca usługi RMS powinna wykonywać podczas wykorzystywania interfejsu API plików do ochrony i wykorzystywania zawartości ograniczonej.|
| [IpcAzureApp](https://github.com/Azure-Samples/active-directory-dotnet-rms) | System Windows Desktop|[Zestaw RMS SDK 2.1](microsoft-information-protection-and-control-client-portal.md) i nowsze wersje zestawu SDK 2.x|**IpcAzureApp** to przykład przedstawiający zastosowanie zestawu RMS SDK w aplikacji Azure do ochrony danych w usłudze Magazyn obiektów Blob Azure.|
| [RmsDocumentInspector](https://github.com/Azure-Samples/active-directory-dotnet-rms) | System Windows Desktop|[Zestaw RMS SDK 2.1](microsoft-information-protection-and-control-client-portal.md) i nowsze wersje zestawu SDK 2.x|**RmsDocumentInspector** to narzędzie dostarczające informacji takich jak identyfikator zawartości i uprawnienia użytkownika na temat dowolnego pliku chronionego przez usługę RMS.|
| [RmsFileWatcher](https://github.com/Azure-Samples/active-directory-dotnet-rms) | System Windows Desktop|[Zestaw RMS SDK 2.1](microsoft-information-protection-and-control-client-portal.md) i nowsze wersje zestawu SDK 2.x|**RmsFileWatcher** to przykład, który demonstruje sposób tworzenia aplikacji systemu Windows, która prowadzi obserwację katalogów w systemie plików i stosuje zasady ochrony usług RMS dla każdej zmiany, na przykład dodania lub modyfikacji pliku.|
| [Scenariusze użycia w systemie iOS/OS X](https://msdn.microsoft.com/library/dn758307(v=vs.85).aspx) |iOS / OS X|[Zestaw RMS SDK 4.2](active-directory-rights-management-services-multi-platform-thin-client-sdk-portal.md) i nowsze wersje zestawu SDK 4.x|Przykłady kodu w języku **Objective C** przedstawiające ważne scenariusze programowania, umożliwiające zapoznanie się z zestawem RMS SDK. Przykłady obejmują korzystanie z formatu Microsoft Protected File, niestandardowe formaty plików chronionych oraz niestandardowe kontrolki interfejsu użytkownika.|
| [Biblioteka interfejsów użytkownika i przykładowa aplikacja](https://github.com/AzureAD/rms-sdk-ui-for-ios) |iOS|[Zestaw RMS SDK 4.2](active-directory-rights-management-services-multi-platform-thin-client-sdk-portal.md) i nowsze wersje zestawu SDK 4.x|**Biblioteki interfejsów użytkownika i przykładowa aplikacja dla systemu iOS** w witrynie GitHub, umożliwiające szybkie rozpoczęcie pracy i wielokrotne korzystanie z naszego standardowego interfejsu użytkownika w aplikacjach.|
| [Biblioteka interfejsów użytkownika i przykładowa aplikacja](https://github.com/AzureAD/rms-sdk-ui-for-android) |Android|[Zestaw RMS SDK 4.2](active-directory-rights-management-services-multi-platform-thin-client-sdk-portal.md) i nowsze wersje zestawu SDK 4.x|**Biblioteki interfejsów użytkownika i przykładowa aplikacja dla systemu Android** w witrynie GitHub, umożliwiające szybkie rozpoczęcie pracy i wielokrotne korzystanie z naszego standardowego interfejsu użytkownika w aplikacjach.|
| [Scenariusze użycia w systemie Android](https://msdn.microsoft.com/en-us/library/dn758246(v=vs.85).aspx) |Android|[Zestaw RMS SDK 4.2](active-directory-rights-management-services-multi-platform-thin-client-sdk-portal.md) i nowsze wersje zestawu SDK 4.x|**Przykłady kodu w języku Java** przedstawiające ważne scenariusze programowania, umożliwiające zapoznanie się z zestawem RMS SDK. Przykłady obejmują korzystanie z formatu Microsoft Protected File, niestandardowe formaty plików chronionych oraz niestandardowe kontrolki interfejsu użytkownika.|



<!--HONumber=Jul16_HO1-->


