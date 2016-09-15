---
title: Typy aplikacji | Azure RMS
description: "W tym temacie omówiono typy aplikacji, które można wybrać do utworzenia jako aplikacje obsługujące prawa."
keywords: 
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 97169FC3-1395-4433-A632-7B0F020FABFE
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 872bb0c20db2ef8d661d321598a2b1fe61d69316
ms.openlocfilehash: a27d1921336a795df5a3c91b36b97846e74cca34


---

# Typy aplikacji


W tym temacie omówiono typy aplikacji, które można wybrać do utworzenia jako aplikacje obsługujące prawa.

Następujące typy aplikacji są obecnie obsługiwane przez zestaw Rights Management Services SDK 2.1.

## Proste aplikacje

Prosta aplikacja może być narzędziem wiersza polecenia wbudowanym w celu zaszyfrowania podanego pliku. Aby zapoznać się z przykładem prostej aplikacji obsługującej prawa, zobacz temat [IPCHelloWorld — przykładowa aplikacja](how-to-build-your-first-application.md).

### Aplikacje w trybie serwera

*Tryb serwera* jest przeznaczony dla nieinterakcyjnych aplikacji, które wykorzystują, chronią lub przetwarzają zawartość chronioną przez usługę RMS. Przykładem może być aplikacja do *ochrony przed utratą danych*, która działa jako usługa na serwerze plików i automatycznie chroni poufne dokumenty. Zobacz przykład tego typu aplikacji w temacie [IpcDlp — przykład](https://Code.MSDN.Microsoft.Com/IpcDlp-Sample-Application-d30bb99d).

Jeśli aplikacja używa *trybu serwera*, powinna uwierzytelniać się na serwerze usługi RMS w trybie dyskretnym. W przeciwieństwie do *trybu klienta* zestaw RMS SDK 2.1 nie otworzy monitu poświadczeń w razie niepowodzenia uwierzytelniania w trybie dyskretnym. Ponadto podczas uruchamiania w *trybie serwera* nie jest wymagany manifest aplikacji.

Aby uzyskać więcej informacji na temat ustawiania trybu zabezpieczeń interfejsu API, zobacz [Ustawianie trybu zabezpieczeń interfejsu API](setting-the-api-security-mode-api-mode.md).

### Rozbudowane aplikacje klienckie

Rozbudowane aplikacje klienckie pozwalają użytkownikom na wyświetlanie i manipulowanie danymi przy użyciu graficznego interfejsu użytkownika (GUI). Często dane prezentowane w tym graficznym interfejsie są cenne i wrażliwe na kradzież lub przypadkowe ujawnienie. Obsługa ochrony informacji zazwyczaj rozszerza istniejący scenariusz, ale nie jest główną motywacją do tworzenia aplikacji.

Użycie zestawu RMS SDK 2.1 w przypadku zaawansowanych aplikacji klienckich ułatwia:

-   Zagwarantowanie, że te dane są zawsze szyfrowane.

-   Uniemożliwienie użytkownikom wyodrębniania danych do formatu niechronionego (na przykład uniemożliwienie im korzystanie ze Schowka do kopiowania i wklejania).

Microsoft Notepad jest prostą rozbudowaną aplikacją kliencką. Microsoft Office jest bardziej złożoną rozbudowaną aplikacją kliencką.

Aby uzyskać więcej informacji o ochronie aplikacji, zobacz [Zrozumienie ograniczeń użycia](understanding-usage-restrictions.md).

## Tematy pokrewne

* [IpcDlp — przykład](https://Code.MSDN.Microsoft.Com/IpcDlp-Sample-Application-d30bb99d)
* [IPCHelloWorld — przykładowa aplikacja](how-to-build-your-first-application.md)
* [Ustawianie trybu zabezpieczeń interfejsu API](setting-the-api-security-mode-api-mode.md)
* [Opis ograniczeń użycia](understanding-usage-restrictions.md)



<!--HONumber=Jul16_HO3-->


