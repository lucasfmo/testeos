---
title: "Instalowanie klienta usługi Azure Information Protection | Azure Rights Management"
description: 
author: cabailey
manager: mbaldwin
ms.date: 07/29/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 4445adff-4c5a-450f-aff8-88bf5bd4ca78
translationtype: Human Translation
ms.sourcegitcommit: 93444affe94b280db2c9e4e2960c6902e491dec6
ms.openlocfilehash: c8a7c7d7182df7b525b3425ab378126feb389d9f


---

# Instalowanie klienta usługi Azure Information Protection

>*Dotyczy: Azure Information Protection (wersja zapoznawcza)*

**[Niniejsze informacje mają charakter wstępny i mogą ulec zmianom. ]**

Aby klasyfikować dokumenty i wiadomości e-mail przy użyciu usługi Azure Information Protection, musisz najpierw zainstalować klienta usługi Azure Information Protection. Ta instalacja dodaje pasek usługi Information Protection do aplikacji pakietu Office (Word, Excel, PowerPoint, Outlook), który wyświetla etykiety klasyfikacji dla Twojej organizacji, a także nową grupę **Ochrona** na karcie **Narzędzia główne** (Word, Excel, PowerPoint), która zawiera przycisk o nazwie **Chroń**:

Na poniższej ilustracji przedstawiono ten pasek usługi Information Protection oraz etykiety z [zasad domyślnych](configure-policy-default.md):

![Pasek usługi Azure Information Protection z zasadami domyślnymi](../media/info-protect-bar-default.png)

Pobierz klienta usługi Azure Information Protection z [Centrum pobierania Microsoft](https://www.microsoft.com/en-us/download/details.aspx?id=53018).

Przed zainstalowaniem klienta sprawdź, czy masz wymagane wersje systemu operacyjnego i aplikacji: [Wymagania dla usługi Azure Information Protection](requirements-azure-infoprotect.md).


## Aby zainstalować klienta usługi Azure Information Protection ręcznie

1. Po [pobraniu klienta](https://www.microsoft.com/en-us/download/details.aspx?id=53018) uruchom program **AZInfoProtection.exe** i postępuj zgodnie z monitami, aby zainstalować klienta. Ta instalacja wymaga lokalnych uprawnień administracyjnych.

    Wybierz opcję zainstalowania zasad demonstracyjnych, jeśli nie możesz nawiązać połączenia z usługą Office 365 lub Azure Active Directory, ale chcesz zobaczyć i wypróbować klienta usługi Azure Information Protection przy użyciu zasad lokalnych w celach demonstracyjnych. Gdy klient nawiąże połączenie z usługą Azure Information Protection, te zasady demonstracyjne zostaną zastąpione zasadami usługi Azure Information Protection obowiązującymi w organizacji. 

2. Aby rozpocząć użytkowanie klienta usługi Azure Information Protection: jeśli Twój komputer ma uruchomiony pakiet Office 2010, uruchom ponownie komputer. W przypadku innych wersji pakietu Office uruchom ponownie wszystkie aplikacje pakietu Office.

## Aby zainstalować klienta usługi Azure Information Protection dla użytkowników

- Możesz użyć skryptu i zautomatyzować instalację klienta Azure Information Protection, pakując program AZInfoProtection.exe i korzystając ze standardowych [opcji wiersza polecenia Instalatora Windows (msiexec)](https://technet.microsoft.com/library/cc759262(v=ws.10).aspx).

    Przykładowo, jeśli spakowana utworzona wersja ma nazwę InfoProtect.msi i chcesz zainstalować klienta w trybie dyskretnym: `msiexec /qn InfoProtection.msi`


## Aby odinstalować klienta usługi Azure Information Protection

- Odinstaluj program za pomocą Panelu sterowania: kliknij kolejno pozycje **Microsoft Azure Information Protection** > **Odinstaluj**

## Aby zweryfikować instalację lub stan połączenia albo zgłosić problem

1. Otwórz aplikację pakietu Office i na karcie **Narzędzia główne** w grupie **Ochrona** kliknij kolejno przyciski **Chroń** oraz **Pomoc i opinie**.

2. W oknie dialogowym **Microsoft Azure Information Protection** zwróć uwagę na następujące elementy:

    - Wartość **Ostatnie połączenie** umożliwia określenie ostatniego momentu połączenia klienta z usługą Azure Information Protection w organizacji. Gdy klient łączy się z usługą, automatycznie pobiera najnowsze zasady, jeśli wykryje zmiany w porównaniu z obecnymi zasadami. Jeśli wprowadzono zmiany zasad po wyświetlonym czasie, zamknij i ponownie otwórz aplikację pakietu Office.

    - Wyświetlona nazwa użytkownika identyfikuje konto używane do uwierzytelniania w usłudze Azure Information Protection. Ta nazwa użytkownika musi pasować do konta używanego w usłudze Office 365 lub Azure Active Directory.

    - Wersja klienta usługi Azure Information Protection.

    - Link **Wyślij opinię** umożliwia automatyczne dołączanie dzienników klienta do wiadomości e-mail, którą można wysłać do zespołu usługi Information Protection w celu zbadania.

    - Link **Uruchom diagnostykę**: ta funkcja nie jest obecnie zaimplementowana.

## Lokalizacje plików

Pliki klienta:   

- Dla 64-bitowych systemów operacyjnych: **\ProgramFiles (x86)\Microsoft Azure Information Protection**

- Dla 32-bitowych systemów operacyjnych: **\Program Files\Microsoft Azure Information Protection**

Pliki dziennika klienta i plik obecnie zainstalowanych zasad:

- Dla 64- i 32-bitowych systemów operacyjnych: **%localappdata%\Microsoft\MSIP**


## Następne kroki

Aby zmienić etykiety na pasku usługi Information Protection, musisz skonfigurować zasady usługi Azure Information Protection. Aby uzyskać więcej informacji, zobacz [Konfigurowanie zasad usługi Azure Information Protection](configure-policy.md).

Aby uzyskać przykład konfigurowania zasad domyślnych i zobaczyć efekty w aplikacji pakietu Office, wypróbuj [Samouczek Szybki start dla usługi Azure Information Protection](infoprotect-quick-start-tutorial.md). 



<!--HONumber=Jul16_HO5-->


