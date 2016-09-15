---
title: "Domyślne zasady usługi Azure Information Protection | Azure Rights Management"
description: 
author: cabailey
manager: mbaldwin
ms.date: 08/08/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 671281c8-f0d1-42b6-aae3-681d1821e2cf
translationtype: Human Translation
ms.sourcegitcommit: 0e02a3f78f1c5986d61f73e57265b944e9d03552
ms.openlocfilehash: 4abce96c4e1215f92211a231a187bd2de4ad3845


---

# Domyślne zasady usługi Azure Information Protection

>*Dotyczy: Azure Information Protection (wersja zapoznawcza)*

**[Niniejsze informacje mają charakter wstępny i mogą ulec zmianom. ]**

Skorzystaj z poniższych informacji, aby poznać, jak są skonfigurowane domyślne zasady usługi Azure Information Protection. Jeśli zmodyfikujesz zasady domyślne, możesz odnieść się do tych wartości, aby przywrócić wartości domyślne zasad.

## Pasek usługi Information Protection

|Ustawienie|Wartość|
|-------------------------------|---------------------------|
|Tytuł|Czułość|
|Etykietka narzędzia|Ważność informacji składa się z czterech różnych poziomów (Publiczne, Wewnętrzne, Poufne, Tajne), dzięki czemu użytkownik może zidentyfikować ryzyko ujawnienia informacji nieautoryzowanym użytkownikom wewnątrz firmy lub poza nią.|

## Etykiety

|Etykieta|Etykietka narzędzia|Ustawienia|
|-------------------------------|---------------------------|-----------------|
|Osobiste|Wyłącznie do użytku osobistego. Te dane nie będą monitorowane przez organizację. Informacje osobiste nie mogą zawierać żadnych danych związanych z firmą.|**Włączone**: Włączone <br /><br />**Kolor**: Jasnozielony<br /><br />**Oznaczenia wizualne**: Brak <br /><br />**Warunki**: Brak<br /><br />**Ochrona**: Nie|
|Publiczne|Te informacje są informacjami wewnętrznymi. Mogą ich używać osoby wewnątrz firmy i poza nią.|**Włączone**: Włączone <br /><br />**Kolor**: Zielony<br /><br />**Oznaczenia wizualne**: Brak<br /><br />**Warunki**: Brak<br /><br />**Ochrona**: Nie|
|Wewnętrzne|Te informacje zawierają szerokie spektrum wewnętrznych danych firmowych, których mogą używać wszyscy pracownicy. Dane można udostępniać autoryzowanym klientom i partnerom biznesowym. Przykładami informacji wewnętrznych są zasady firmowe i większość komunikacji wewnętrznej.|**Włączone**: Włączone <br /><br />**Kolor**: Niebieski <br /><br />**Oznaczenia wizualne**: Stopka (dokument i wiadomość e-mail)<br /><br />**Warunki**: Brak<br /><br />**Ochrona**: Nie|
|Poufne|Te dane zawierają poufne informacje biznesowe. Udostępnianie tych danych nieautoryzowanym użytkownikom może zaszkodzić organizacji. Przykładami informacji poufnych są informacje dotyczące pracowników, poszczególnych projektów lub umów z klientami oraz dane dotyczące konta sprzedaży.|**Włączone**: Włączone <br /><br />**Kolor**: Pomarańczowy<br /><br />**Oznaczenia wizualne**: Stopka (dokument i wiadomość e-mail)<br /><br />**Warunki**: Brak<br /><br />**Ochrona**: Nie|
|Tajne|Te dane uwzględniają wysoce poufne informacje, które należy chronić w firmie. Udostępnianie danych tajnych nieautoryzowanym użytkownikom może poważnie zaszkodzić organizacji. Przykładami informacji tajnych są informacje umożliwiające identyfikację poszczególnych osób, rekordy klientów, kod źródłowy i wstępnie ogłoszone raporty finansowe.|**Włączone**: Włączone <br /><br />**Kolor**: Czerwony<br /><br />**Oznaczenia wizualne**: Stopka (dokument i wiadomość e-mail)<br /><br />**Warunki**: Brak<br /><br />**Ochrona**: Nie|

## Etykiety podrzędne

|Etykieta|Etykietka narzędzia|Ustawienia|
|-------------------------------|---------------------------|-----------------|
|*Tajne* > Cała firma|Te dane obejmują poufne informacje biznesowe, do których mają dostęp wszyscy pracownicy firmy.|**Włączone**: Włączone <br /><br />**Oznaczenia wizualne**: Brak<br /><br />**Warunki**: Brak<br /><br />**Ochrona**: Nie|
|*Tajne* > Moja grupa|Te dane obejmują poufne informacje biznesowe, do których mają dostęp tylko grupy pracowników.|**Włączone**: Włączone <br /><br />**Oznaczenia wizualne**: Brak<br /><br />**Warunki**: Brak<br /><br />**Ochrona**: Nie|

## Ustawienia globalne

|Ustawienie|Wartość|
|-------------------------------|---------------------------|
|Wszystkie dokumenty i wiadomości e-mail muszą mieć etykietę (stosowaną automatycznie lub przez użytkowników)|Wyłączone|
|Wybierz etykietę domyślną|Brak|
|Użytkownicy muszą podać uzasadnienie w przypadku obniżenia charakterystyki (np. z Poufne na Publiczne)|Wyłączone|


## Następne kroki

Aby uzyskać więcej informacji o konfigurowaniu zasad usługi Azure Information Protection, użyj linków w sekcji [Konfigurowanie zasad organizacji](configure-policy.md#configuring-your-organization-s-policy). 



<!--HONumber=Aug16_HO2-->


