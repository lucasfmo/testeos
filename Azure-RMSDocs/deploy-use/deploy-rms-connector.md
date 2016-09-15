---
title: "Wdrażanie łącznika usługi Azure Rights Management | Azure RMS"
description: 
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 05/20/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 90e7e33f-9ecc-497b-89c5-09205ffc5066
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: e31656e417a0861d33deb2436d2e4b596a7512a7
ms.openlocfilehash: 6b9b3b039ba2de0de174a134768afd763d26b5dd


---

# Wdrażanie łącznika usługi Azure Rights Management

*Dotyczy: Azure Rights Management, Windows Server 2012, Windows Server 2012 R2*

Te informacje można wykorzystać do lepszego poznania łącznika usługi Azure Rights Management (RMS) i sposobów używania go w celu zapewnienia ochrony informacji w istniejących wdrożeniach lokalnych korzystających z programu Microsoft Exchange Server, Microsoft SharePoint Server lub serwerów plików, na których uruchomiony jest system Windows Server i które używają funkcji infrastruktury klasyfikacji plików (FCI, File Classification Infrastructure) programu File Server Resource Manager.

> [!TIP]
> Przykładowy scenariusz wysokiego poziomu ze zrzutami ekranu można znaleźć w sekcji [Automatyczna ochrona plików na serwerach plików z systemem Windows Server i funkcją infrastruktury klasyfikacji plików](../understand-explore/what-admins-users-see.md#automatically-protecting-files-on-file-servers-running-windows-server-and-file-classification-infrastructure) w artykule [Usługa Azure RMS w działaniu](../understand-explore/what-admins-users-see.md).

## Łącznik usługi Microsoft Rights Management — omówienie
Łącznik usługi Microsoft Rights Management (RMS) pozwala szybko włączyć na istniejących serwerach lokalnych funkcjonalność zarządzania prawami do informacji (IRM, Information Rights Management) za pomocą opartej na chmurze usługi Microsoft Rights Management (usługa Azure RMS). Dzięki tej funkcji dział IT i użytkownicy mogą łatwo chronić dokumenty i obrazy zarówno wewnątrz organizacji, jak i poza nią, bez konieczności instalowania dodatkowej infrastruktury lub ustanawiania relacji zaufania z innymi organizacjami. Można użyć tego łącznika nawet w przypadku, gdy niektórzy użytkownicy są podłączeni do usług online w scenariuszu hybrydowym. Na przykład skrzynki pocztowe niektórych użytkowników korzystają z usługi Exchange Online, podczas gdy skrzynki pocztowe innych użytkowników korzystają z programu Exchange Server. Po zainstalowaniu łącznika usługi RMS wszyscy użytkownicy mogą chronić informacje oraz korzystać z wiadomości e-mail i załączników za pomocą usługi Azure RMS, podczas gdy ochrona informacji współpracuje płynnie z dwiema konfiguracjami wdrożenia.

Łącznik usług RMS jest niemal niepozostawiającą śladów usługą instalowaną lokalnie na serwerach z systemem Windows Server 2012 R2, Windows Server 2012 lub Windows Server 2008 R2. Poza uruchamianiem łącznika na komputerach fizycznych można go również uruchomić na maszynach wirtualnych, w tym na maszynach wirtualnych Azure IaaS Po zainstalowaniu i skonfigurowaniu łącznik działa jako interfejs komunikacji (przekaźnik) między serwerami lokalnymi i usługą w chmurze.

Jeśli zarządzasz kluczem dzierżawy dla usługi Azure RMS (scenariusz z użyciem własnego klucza — BYOK), łącznik usługi RMS i serwery lokalne, które go używają, nie uzyskują dostępu do modułu HSM, zawierającego klucz dzierżawy. Jest to spowodowane tym, że wszystkie operacje kryptograficzne, które używają klucza dzierżawy, są wykonywane w ramach usługi Azure RMS, a nie lokalnie.

![Architektura łącznika usługi RMS — omówienie](../media/RMS_connector.png)

Łącznik usługi RMS obsługuje następujące serwery lokalne: Exchange Server, SharePoint Server i serwery plików działające pod kontrolą systemu operacyjnego Windows Server i używające funkcji infrastruktury klasyfikacji plików do klasyfikowania oraz stosowania zasad do dokumentów pakietu Office w folderze. Aby chronić wszystkie typy plików za pomocą funkcji klasyfikacji plików, zamiast łącznika usługi RMS należy używać [poleceń ochrony cmdlet usługi RMS](https://msdn.microsoft.com/library/azure/mt433195.aspx).

> [!NOTE]
> Obsługiwane wersje tych serwerów lokalnych można znaleźć w sekcji [Serwery lokalne, które obsługują usługę Azure RMS](..\get-started\requirements-servers.md).

Skorzystaj z poniższych informacji, aby ułatwić planowanie, instalowanie i konfigurowanie łącznika usługi RMS. Następnie wykonaj pewne poinstalacyjne czynności konfiguracyjne, aby serwery mogły używać łącznika.

-   [Wymagania wstępne dotyczące łącznika usługi RMS](deploy-rms-connector.md#prerequisites-for-the-rms-connector)

-   **Krok 1.**  [Instalowanie łącznika usług RMS](install-configure-rms-connector.md#installing-the-rms-connector)

-   **Krok 2.**  [Wprowadzanie poświadczeń](install-configure-rms-connector.md#entering-credentials)

-   **Krok 3.**  [Autoryzowanie serwerów do korzystania z łącznika usługi RMS](install-configure-rms-connector.md#authorizing-servers-to-use-the-rms-connector)

-   **Krok 4.**  [Konfigurowanie funkcji równoważenia obciążenia i wysokiej dostępności](install-configure-rms-connector.md#configuring-load-balancing-and-high-availability)

-   Opcjonalnie: [Konfigurowanie łącznika usługi RMS do obsługi protokołu HTTPS](install-configure-rms-connector.md#configuring-the-rms-connector-to-use-https)

-   Opcjonalnie: [Konfigurowanie łącznika usługi RMS dla serwera proxy sieci web](install-configure-rms-connector.md#configuring-the-rms-connector-for-a-web-proxy-server)

-   Opcjonalnie: [Instalowanie narzędzia administracyjnego łącznika usługi RMS na komputerach administracyjnych](install-configure-rms-connector.md#installing-the-rms-connector-administration-tool-on-administrative-computers)

-   **Krok 5.**  [Konfigurowanie serwerów do korzystania z łącznika usługi RMS](configure-servers-rms-connector.md)

    -   [Konfigurowanie serwera programu Exchange do używania łącznika](configure-servers-rms-connector.md#configuring-an-exchange-server-to-use-the-connector)

    -   [Konfigurowanie serwera programu SharePoint do używania łącznika](configure-servers-rms-connector.md#configuring-a-sharepoint-server-to-use-the-connector)

    -   [Konfigurowanie serwera plików dla funkcji infrastruktury klasyfikacji plików do używania łącznika](configure-servers-rms-connector.md#configuring-a-file-server-for-file-classification-infrastructure-to-use-the-connector)


## Wymagania wstępne dotyczące łącznika usługi RMS
Przed zainstalowaniem łącznika usługi RMS upewnij się, że zostały spełnione następujące wymagania.

|Wymaganie|Więcej informacji|
|---------------|--------------------|
|Usługa Rights Management (RMS) została aktywowana|[Aktywacja usługi Azure Rights Management](activate-service.md)|
|Synchronizacja katalogu lokalnych lasów usługi Active Directory i usługi Azure Active Directory|Po uaktywnieniu usługi RMS usługa Azure Active Directory musi być skonfigurowana do pracy z użytkownikami i grupami w bazie danych usługi Active Directory użytkownika.<br /><br />**Ważne**: Ten krok synchronizacji katalogu należy wykonać dla zapewnienia działania łącznika usługi RMS, nawet w przypadku sieci testowej. Chociaż z usługi Office 365 i usługi Azure Active Directory można korzystać przy użyciu kont, które zostały ręcznie utworzone w usłudze Azure Active Directory, ten łącznik wymaga synchronizacji kont w usłudze Azure Active Directory z Usługami domenowymi Active Directory. Ręczna synchronizacja haseł nie jest wystarczająca.<br /><br />Więcej informacji można znaleźć w następujących zasobach:<br /><br />[Integrowanie tożsamości użytkownika lokalnego z usługą Azure Active Directory](/active-directory/active-directory-aadconnect)<br /><br />[Porównanie narzędzi integracji katalogu tożsamości hybrydowej](/active-directory/active-directory-hybrid-identity-design-considerations-tools-comparison)|
|Opcjonalne, ale zalecane:<br /><br />Włączenie federacji między lokalną usługą Active Directory i usługą Azure Active Directory|Można włączyć federację tożsamości między katalogiem lokalnym i usługą Azure Active Directory. Ta konfiguracja umożliwia zwiększenie wygody pracy użytkownika przez użycie funkcji logowania jednokrotnego do usługi RMS. Bez funkcji logowania jednokrotnego użytkownicy są monitowani o podanie poświadczeń, aby móc korzystać z zawartości chronionej prawami.<br /><br />Instrukcje konfigurowania federacji przy użyciu usług federacyjnych Active Directory (AD FS) między Usługami domenowymi Active Directory i usługą Azure Active Directory znajdują się w sekcji [Lista kontrolna: korzystanie z usług AD FS do wdrażania rejestracji jednokrotnej i zarządzania nią](http://technet.microsoft.com/library/jj205462.aspx) w bibliotece systemu Windows Server.|
|Co najmniej dwa komputery członkowskie, na których zostanie zainstalowany łącznik usług RMS:<br /><br />– 64-bitowy komputer fizyczny lub wirtualny działający pod kontrolą jednego z następujących systemów operacyjnych: Windows Server 2012 R2, Windows Server 2012 lub Windows Server 2008 R2.<br /><br />– Co najmniej 1 GB pamięci RAM.<br /><br />– Co najmniej 64 GB miejsca na dysku.<br /><br />– Co najmniej jeden interfejs sieciowy.<br /><br />– Dostęp do Internetu za pośrednictwem zapory (lub serwera proxy sieci Web), która nie wymaga uwierzytelniania.<br /><br />– Musi należeć do lasu lub domeny, które ufają innym lasom w organizacji, zawierającym instalacje serwerów programu Exchange lub SharePoint przeznaczone do użycia z łącznikiem usługi RMS.|W celu zachowania odporności na uszkodzenia i wysokiej dostępności łącznik usług RMS należy zainstalować na co najmniej dwóch komputerach.<br /><br />**Porada**: Jeśli używasz programu Outlook Web Access lub urządzeń przenośnych, które korzystają z programu Exchange ActiveSync IRM, a szczególnie ważne jest, by utrzymywać dostęp do wiadomości e-mail i załączników chronionych za pomocą usługi Azure RMS, zalecamy wdrożenie grupy serwerów łącznika z funkcją równoważenia obciążenia dla zapewnienia wysokiej dostępności.<br /><br />Do uruchomienia łącznika nie są potrzebne dedykowane serwery, ale musi on zostać zainstalowany na innym komputerze niż serwery używające łącznika.<br /><br />**Ważne**: Nie instaluj łącznika na komputerze z systemem Exchange Server, SharePoint Server ani na serwerze plików skonfigurowanym dla funkcji infrastruktury klasyfikacji plików, jeśli chcesz skorzystać z funkcjonalności tych usług za pomocą usługi Azure RMS. Ponadto nie należy instalować tego łącznika na kontrolerze domeny.|

## Następne kroki

Przejdź do sekcji [Instalowanie i konfigurowanie łącznika usługi Azure Rights Management](install-configure-rms-connector.md).


<!--HONumber=Jun16_HO4-->


