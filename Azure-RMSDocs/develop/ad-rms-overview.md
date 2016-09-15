---
title: "Przegląd — zestaw RMS SDK 2.1 | Azure RMS"
description: "Usługi Rights Management (RMS) to technologia ochrony informacji, która pomaga w zabezpieczaniu informacji cyfrowych przed nieautoryzowanym użyciem."
keywords: 
author: bruceperlerms
manager: mbaldwin
ms.date: 07/11/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: B546B6C1-ADC1-4EBD-95E2-B4A74E4E980B
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 5afdf526fe9f8486c6a778eebf10899e0bd9f839
ms.openlocfilehash: 53571aff357bbc0cdcb44ce9b403c68719abbaff


---

# Przegląd

Zestaw Rights Management SDK 2.1 to technologia ochrony informacji, która pomaga w zabezpieczaniu informacji cyfrowych przed nieautoryzowanym użyciem. Przy użyciu aplikacji obsługujących prawa właściciele zawartości mogą zdefiniować użytkowników, którzy mogą otwierać, modyfikować, drukować i przekazywać zawartość oraz podejmować inne związane z nią działania.

W usługach AD RMS uwzględniono składniki [serwera](ad-rms-server.md) i [klienta](ad-rms-client.md). Składnik serwera działający na platformie Azure lub w systemie Windows Server zawiera wiele usług sieci Web.

Składnik [klienta](ad-rms-client.md) może działać w systemie operacyjnym klienta lub serwera i zawiera funkcje umożliwiające aplikacji szyfrowanie i odszyfrowywanie zawartości, pobieranie szablonów i list odwołania, uzyskiwanie licencji i certyfikatów z serwera oraz wykonywanie innych zadań związanych z zarządzaniem prawami.

Aby uzyskać więcej informacji, zobacz temat [Typy aplikacji](application-types.md).

Poniżej przedstawiono kilka scenariuszy, w których można stosować aplikacje utworzone przy użyciu zestawu Rights Management Services SDK 2.1.

-   Kancelaria prawna chce zapobiec drukowaniu i przekazywaniu dalej poufnych wiadomości e-mail.
-   Deweloperzy oprogramowania CAD i oprogramowania produkcyjnego chcą ograniczyć dostęp do rysunków do niewielkiej grupy użytkowników z działu badawczego bez konieczności korzystania z haseł.
-   Właściciele witryny internetowej dla projektów graficznych chcą korzystać z pojedynczej licencji, która umożliwia swobodne wyświetlanie kopii obrazów w niskiej rozdzielczości, ale wymaga opłaty w celu uzyskania dostępu do wersji o wysokiej rozdzielczości.
-   Właściciele biblioteki dokumentów online chcą włączyć prawa do wyświetlania, drukowania i edycji dokumentów na podstawie tożsamości użytkownika.
-   Firma chce publikować poufne informacje o pracownikach w wewnętrznej witrynie sieci Web, która ogranicza uprawnienia do wyświetlania i edycji do określonych użytkowników.

Aby uzyskać więcej informacji na temat serwera usług AD RMS, klienta usług AD RMS i ich funkcji, zobacz zawartość TechNet w [dokumentacji usług AD RMS dla specjalistów IT](https://TechNet.Microsoft.Com/library/cc771234.aspx).

Pozostałe tematy w tej sekcji dotyczą architektury usług RMS i ich implementacji.

## W tej sekcji

| Temat | Opis |
|-------|-------------|
|[Klient](ad-rms-client.md) |W tym temacie opisano przeznaczenie i funkcję klienta Rights Management Services Client 2.1 |
|[Serwer](ad-rms-server.md) | W tym temacie opisano przeznaczenie i funkcje serwera usług RMS na potrzeby platformy Azure i systemu Windows Server.|


## Tematy pokrewne

* [Koncepcje związane z usługami RMS](application-types.md)
* [Wprowadzenie](getting-started-with-ad-rms-2-0.md)
* [Dokumentacja usług AD RMS dla specjalistów IT](https://TechNet.Microsoft.Com/en-us/library/cc771234.aspx)
 

 



<!--HONumber=Jul16_HO3-->


