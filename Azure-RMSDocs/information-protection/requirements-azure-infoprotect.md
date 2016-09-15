---
title: "Wymagania dotyczące usługi Azure Information Protection| Azure RMS"
description: 
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 08/10/2016
ms.topic: get-started-article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: aa4353e5-c5b0-47f6-a6f9-87d13e8f075f
ms.reviewer: eymanor
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: c0652e05576ab28d7b77380ab1b8aa0ca2d3e479
ms.openlocfilehash: e3eb845af4e2cfec43c63c9625163f62c83cf954


---

# Wymagania dotyczące usługi Azure Information Protection

>*Dotyczy: Azure Information Protection (wersja zapoznawcza)*

**[Niniejsze informacje mają charakter wstępny i mogą ulec zmianom. ]**

Aby ocenić wersję zapoznawczą usługi Azure Information Protection, upewnij się, że są spełnione następujące wymagania wstępne. 

|Wymaganie|Więcej informacji|
|---------------|--------------------|
|Subskrypcja usług w chmurze obejmująca usługę Azure RMS|Organizacja musi mieć subskrypcję usług w chmurze, która obsługuje usługę Rights Management.<br /><br />Więcej informacji oraz linki do bezpłatnych wersji próbnych można znaleźć w temacie [Subskrypcje usług w chmurze, które obsługują usługę Azure RMS](../get-started/requirements-subscriptions.md).|
|Katalog usługi Azure AD|Aby obsługiwać uwierzytelnianie użytkowników na potrzeby usługi RMS i Azure Information Protection, organizacja musi mieć katalog usługi Azure AD. Ponadto jeśli chcesz użyć kont użytkowników z katalogu lokalnego (AD DS), musisz również skonfigurować integrację katalogów.<br /><br />Usługa Multi-Factor Authentication (MFA) jest obsługiwana za pomocą usługi Azure RMS, jeśli masz wymagane oprogramowanie klienckie i prawidłowo skonfigurowaną infrastrukturę obsługującą usługę MFA.<br /><br />Aby uzyskać więcej informacji, zobacz [Katalog usługi Azure AD](../get-started/requirements-azure-ad.md), gdyż informacje dotyczące usługi Azure RMS mają zastosowanie również do usługi Azure Information Protection.|
|Urządzenia klienckie|W tej wersji zapoznawczej obsługiwane są urządzenia klienta z następującymi systemami operacyjnymi:<br /><br />— Windows 10 (x86, x64)<br /><br />— Windows 8.1 (x86, x64)<br /><br />— Windows 8 (x86, x64)<br /><br />— Windows 7 z dodatkiem Service Pack 1 (x86, x64)<br /><br />Chronione dane mogą być używane na urządzeniach ze wszystkimi systemami (Windows, Mac, iOS, Android), obsługujących usługę Azure Rights Management. Aby uzyskać szczegółowe informacje o urządzeniach i obsługiwanych wersjach, zobacz [Wymagania dotyczące usługi Azure RMS: urządzenia klienckie, które obsługują usługę Azure RMS](../get-started/requirements-client-devices.md).|
|Aplikacje|W wersji zapoznawczej i w wersji ogólnodostępnej (GA) usługa Azure Information Protection obsługuje etykietowanie i ochronę plików oraz wiadomości e-mail utworzonych przez aplikacje **Word**, **Excel**, **PowerPoint** i **Outlook** pochodzące z następujących pakietów Office:<br /><br />— Office Professional Plus 2016<br /><br />— Office Professional Plus 2013 z dodatkiem Service Pack 1<br /><br />— Office Professional Plus 2010<br /><br />Po udostępnieniu wersji ogólnodostępnej należy oczekiwać na ogłoszenie na blogu [Enterprise Mobility and Security](https://blogs.technet.microsoft.com/enterprisemobility/?product=azure-rights-management-services) daty rozpoczęcia przez usługę Azure Information Protection obsługi dodatkowych typów plików, takich jak PDF, audio, wideo i pliki obrazów.|
|Infrastruktura obsługująca łączność z Internetem i zależnymi usługami w chmurze|Jeśli jest używana zapora lub podobne aktywne urządzenie sieciowe wymagające skonfigurowania określonych połączeń sieciowych, zapoznaj się z informacjami o usłudze **Azure Rights Management (RMS)** w sekcji [Portal usługi Office 365 i udostępnianie](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2#BKMK_Portal-identity) w następującym artykule o pakiecie Office: [Adresy URL i zakresy adresów IP usługi Office 365](https://support.office.com/en-US/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2)<br /><br />Ponadto:<br /><br />— Zezwalaj na ruch HTTPS na porcie TCP 443 do witryny **informationprotection.azure.com**.<br /><br />— Nie kończ połączenia TLS między klientem i usługą (np. w celu przeprowadzenia inspekcji na poziomie pakietu). <br /><br />— Jeśli używasz serwera proxy sieci Web, który wymaga uwierzytelniania, musisz skonfigurować go do korzystania ze zintegrowanego uwierzytelniania systemu Windows przy użyciu poświadczeń logowania usługi Active Directory użytkownika.|

## Następne kroki

Jeśli te wymagania zostały spełnione, zapoznaj się z programem demonstracyjnym i samodzielnie wypróbuj usługę Azure Information Protection: [Samouczek Szybki start dla usługi Azure Information Protection](infoprotect-quick-start-tutorial.md).




<!--HONumber=Aug16_HO2-->


