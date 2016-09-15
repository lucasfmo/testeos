---
title: "Generowanie i przekazywanie klucza dzierżawy — osobiście | Azure RMS"
description: 
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 3281e45e-cf69-4dc5-946b-3029851d3152
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 67129d6cdac124947fc07aa4d42523686227752e
ms.openlocfilehash: 8e77298121a84f6feb16a992da81bd9c3bb7b20b


---

# Generowanie i przekazywanie klucza dzierżawy — osobiście

*Dotyczy usług: Azure Rights Management, Office 365*


Jeśli zdecydujesz się na [zarządzanie własnym kluczem dzierżawy](plan-implement-tenant-key.md#choose-your-tenant-key-topology-managed-by-microsoft-the-default-or-managed-by-you-byok) i wolisz osobiście przekazać klucz zamiast przesyłać go przez Internet, wykonaj czynności opisane poniżej.

## Generowanie klucza dzierżawy
Aby wygenerować klucz dzierżawy, należy wykonać poniższe trzy kroki:

-   [Krok 1. Przygotowanie stacji roboczej z modułem HSM firmy Thales](#step-1-prepare-a-workstation-with-thales-hsm)

-   [Krok 2. Utworzenie środowiska zabezpieczeń Security World](#step-2-create-a-security-world)

-   [Krok 3. Utworzenie nowego klucza](#step-3-create-a-new-key)

### Krok 1. Przygotowanie stacji roboczej z modułem HSM firmy Thales
Zainstaluj oprogramowanie wspomagające nCipher firmy Thales na komputerze z systemem Windows. Podłącz sprzętowy moduł zabezpieczeń (HSM, hardware security module) firmy Thales do komputera. Upewnij się, że narzędzia firmy Thales są dostępne w znanej ścieżce. Więcej informacji znajduje się w podręczniku użytkownika dołączonym do sprzętowego modułu zabezpieczeń firmy Thales oraz w witrynie sieci Web firmy Thales poświęconej usłudze Azure RMS, dostępnej pod adresem [http://www.thales-esecurity.com/msrms/cloud](http://www.thales-esecurity.com/msrms/cloud).

### Krok 2: Utworzenie środowiska zabezpieczeń Security World
Uruchom wiersz polecenia, a następnie uruchom program firmy Thales umożliwiający utworzenie nowego środowiska (new-world).

```
new-world.exe --initialize --cipher-suite=DLf1024s160mRijndael --module=1 --acs-quorum=2/3
```
Uruchomienie programu powoduje utworzenie pliku **Security World** w lokalizacji %NFAST_KMDATA%\local\world, co odpowiada lokalizacji folderu C:\ProgramData\nCipher\Key Management Data\local. Można użyć różnych wartości dla kworum. W naszym przykładzie zostanie jednak wyświetlony monit o użycie trzech pustych kart oraz kodów PIN dla każdej z nich. Następnie dowolne dwie karty zapewnią pełny dostęp do środowiska zabezpieczeń.  Karty te tworzą od tej chwili **zestaw kart administratora** nowego środowiska zabezpieczeń Security World.

Następnie wykonaj następujące czynności:

1.  Zainstaluj dostawcę kluczy CNG firmy Thales, postępując zgodnie z instrukcjami zawartymi w dokumentacji dostarczonej przez firmę Thales, a następnie skonfiguruj go pod kątem użycia nowego środowiska zabezpieczeń Security World.

2.  Utwórz kopię zapasową pliku środowiska zabezpieczeń. Zabezpiecz i chroń plik środowiska zabezpieczeń, karty administratora oraz ich kody PIN, a także upewnij się, że nikt nie ma dostępu do więcej niż jednej karty.

Teraz możesz utworzyć nowy klucz, który będzie pełnił rolę klucza dzierżawy usługi RMS.

### Krok 3. Utworzenie nowego klucza
Wygeneruj klucz CNG, korzystając z programów **generatekey** i **cngimport** firmy Thales.

Uruchom następujące polecenie, aby wygenerować klucz:

```
generatekey --generate simple type=RSA size=2048 protect=module ident=contosokey plainname=contosokey nvram=no pubexp=
```
Podczas uruchamiania tego polecenia należy zastosować się do następujących instrukcji:

-   Parametr **protect** musi mieć ustawioną wartość **module**, jak przedstawiono. Spowoduje to utworzenie klucza chronionego przez moduł. Zestaw narzędzi BYOK nie obsługuje kluczy chronionych z użyciem protokołu OCS.

-   Zalecamy zastosowanie klucza 2048-bitowego. Obsługiwane są jednak także 1024-bitowe klucze RSA istniejących klientów usługi AD RMS, którzy korzystają z takich kluczy i mają zamiar dokonać migracji do usługi Azure RMS.

-   Zamień wartość *contosokey* dla pozycji **ident** i **plainname** na dowolną wartość ciągu. Aby zminimalizować ogólne koszty administracyjne i zmniejszyć ryzyko błędów, zaleca się użycie dla obu pozycji tej samej wartości, zapisanej wyłącznie małymi literami.

-   W tym przykładzie parametr pubexp został pozostawiony pusty (wartość domyślna), można jednak określić konkretne jego wartości. Więcej informacji znajduje się w dokumentacji firmy Thales.

Następnie uruchom poniższe polecenie, aby zaimportować klucz do funkcji CNG:

```
cngimport --import –M --key=contosokey --appname=simple contosokey
```
Podczas uruchamiania tego polecenia należy zastosować się do następujących instrukcji:

-   Zastąp wartość *contosokey* wartością, która została określona w kroku 1.

-   Użyj opcji **-M**, aby przystosować klucz do użycia w tym scenariuszu. W przeciwnym razie uzyskany klucz będzie kluczem utworzonym dla konkretnego (bieżącego) użytkownika.

To polecenie tworzy plik stokenizowanego klucza w folderze %NFAST_KMDATA%\local. Nazwa pliku zaczyna się od ciągu znaków **key_caping`_`**, po którym następuje identyfikator SID. Na przykład: **key_caping_machine--801c1a878c925fd9df4d62ba001b94701c039e2fb**. Ten plik zawiera zaszyfrowany klucz.

Utwórz w bezpiecznej lokalizacji kopię zapasową tego pliku stokenizowanego klucza.

> [!IMPORTANT]
> Po późniejszym przesłaniu klucza do usługi Azure RMS firma Microsoft będzie dysponować kopią klucza, której odzyskanie nie będzie możliwe. Oznacza to, że nikt z firmy Microsoft nie może pobrać klucza z modułów HSM. Dzięki temu zachowujesz wyłączną kontrolę nad kluczem dzierżawy. W związku z tym tak ważne jest utworzenie i bezpieczne przechowywanie kopii zapasowej klucza oraz środowiska zabezpieczeń. Skontaktuj się z firmą Thales w celu uzyskania wskazówek i najlepszych rozwiązań dotyczących tworzenia kopii zapasowej klucza.

Teraz można przystąpić do przekazania klucza dzierżawy do usługi Azure RMS.

## Przekazywanie klucza dzierżawy do usługi Azure RMS
Wygenerowany przez siebie klucz należy przekazać do usługi Azure RMS przed jego użyciem. Aby zagwarantować najwyższy poziom zabezpieczeń, ten proces jest wykonywany ręcznie. W celu jego przeprowadzenia należy udać się do biura firmy Microsoft w Redmond w stanie Waszyngton (USA). Aby ukończyć ten proces, należy wykonać poniższe trzy kroki:

-   [Krok 1. Dostarczenie klucza do firmy Microsoft](#step-1-bring-your-key-to-microsoft)

-   [Krok 2. Przekazanie klucza do środowiska zabezpieczeń usługi Azure RMS](#step-2-transfer-your-key-to-the-azure-rms-security-world)

-   [Krok 3. Procedury końcowe](#step-3-closing-procedures)

### Krok 1. Dostarczenie klucza do firmy Microsoft

-   Skontaktuj się z działem pomocy technicznej firmy Microsoft w celu zaplanowania spotkania, podczas którego nastąpi przekazanie klucza dla usługi Azure RMS. Biuro firmy Microsoft w Redmond będzie wymagało:

    -   Dostarczenia kworum kart administracyjnych. W przypadku wykonaniu czynności opisanych w części [Krok 2. Utworzenie środowiska zabezpieczeń Security World](#step-2-create-a-security-world) są to dowolne dwie z trzech kart.

    -   Obecności osób uprawnionych do przenoszenia kart administracyjnych i kodów PIN, zwykle dwóch (po jednej dla każdej karty).

    -   Dostarczenia pliku środowiska zabezpieczeń Security World (%NFAST_KMDATA%\local\world) na dysku USB.

    -   Dostarczenia pliku stokenizowanego klucza na dysku USB.

### Krok 2. Przekazanie klucza do środowiska zabezpieczeń usługi Azure RMS

1.  Po przyjeździe do biura firmy Microsoft w celu przekazania klucza:

    -   Firma Microsoft dostarcza działającą w trybie offline stację roboczą z podłączonym modułem HSM firmy Thales, zainstalowanym oprogramowaniem firmy Thales i plikiem środowiska zabezpieczeń Security World dla usługi Azure RMS wstępnie załadowanym do folderu C:\Temp\Destination.

    -   Na tej stacji roboczej należy załadować plik środowiska zabezpieczeń Security World oraz plik stokenizowanego klucza z dysku USB, które należy umieścić w folderze C:\Temp\Source.

    -   Operatorzy usługi Azure RMS przenoszą klucz w bezpieczny sposób do środowiska zabezpieczeń usługi Azure RMS, korzystając z narzędzi firmy Thales.

    Ten proces przebiega podobnie do poniższego, przy czym ostatni parametr polecenia key-xfer-im w tym przykładzie zostaje zastąpiony nazwą pliku stokenizowanego klucza:

    **C:\&gt; mk-reprogram.exe --owner c:\Temp\Destination add c:\Temp\Source**

    **C:\&gt; key-xfer-im.exe c:\Temp\Source c:\Temp\Destination --module c:\Temp\Source\key_caping_machine--801c1a878c925fd9df4d62ba001b94701c039e2fb**

2.  Program mk-reprogram wyświetli skierowany do Ciebie oraz operatorów usługi Azure RMS monit o podłączenie odpowiednich kart administratora i użycie właściwych kodów PIN. Te polecenia powodują wygenerowanie pliku stokenizowanego klucza w lokalizacji C:\Temp\Destination, zawierającej klucz chroniony przez środowisko zabezpieczeń usługi Azure RMS.

### Krok 3. Procedury końcowe

-   W Twojej obecności operatorzy usługi Azure RMS wykonują następujące czynności:

    -   Uruchomienie narzędzia opracowanego przez firmę Microsoft we współpracy z firmą Thales, które usuwa dwa uprawnienia: uprawnienie do odzyskania klucza i uprawnienie do zmiany uprawnień. Po tej operacji kopia klucza zostaje zablokowana w środowisku zabezpieczeń usługi Azure RMS. Moduły HSM firmy Thales nie zezwolą operatorom usługi Azure RMS na odzyskanie kopii klucza w postaci zwykłego tekstu przy użyciu ich kart administratora.

    -   Uzyskany plik klucza zostaje skopiowany na dysk USB w celu jego przesłania do usługi Azure RMS.

    -   Następnie ma miejsce przywrócenie ustawień fabrycznych modułu HSM i wyczyszczenie stacji roboczej.

Stanowi to zakończenie instrukcji wymaganych do osobistego przekazania klucza dzierżawy, po przeprowadzeniu których możesz wrócić do swojej organizacji w celu wykonania następnych kroków związanych z planowaniem i wdrażaniem klucza dzierżawy.

> [!div class="button"]
[Następne kroki >>](plan-implement-tenant-key.md#next-steps)






<!--HONumber=Jul16_HO3-->


