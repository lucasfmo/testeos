---
title: "Planowanie i wdrażanie klucza dzierżawy usługi Azure Rights Management | Azure RMS"
description: 
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 08/17/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: f0d33c5f-a6a6-44a1-bdec-5be1bc8e1e14
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: a80866576dc7d6400bcebc2fc1c37bc0367bcdf3
ms.openlocfilehash: ee7b9b5f251856f102651f1e8f379f7bbacea77e


---

# Planowanie i wdrażanie klucza dzierżawy usługi Azure Rights Management

*Dotyczy usług: Azure Rights Management, Office 365*

Informacje zawarte w tym artykule umożliwiają zaplanowanie użycia klucza dzierżawy usługi Rights Management (RMS) dla usługi Azure RMS oraz zarządzanie nim. Domyślne ustawienie zakłada, że to firma Microsoft zarządza kluczem dzierżawy. Ustawienie to można zmienić, aby zarządzać własnym kluczem dzierżawy w celu zachowania zgodności z konkretnymi przepisami mającymi zastosowanie w danej organizacji.  Samodzielne zarządzanie kluczem dzierżawy określa się także mianem strategii BYOK (Bring Your Own Key), czyli „Przynieś własny klucz”.

> [!NOTE]
> Klucz dzierżawy usługi RMS jest również nazywany kluczem certyfikatu licencjodawcy serwera (SLC). Usługa Azure RMS obsługuje co najmniej jeden klucz dla każdej organizacji, która ją subskrybuje. Za każdym razem, gdy na potrzeby usługi RMS używanej w obrębie organizacji jest wykorzystywany klucz (np. klucz użytkownika, klucz komputera, klucz szyfrowania dokumentu), ma miejsce szyfrowane połączenie użytego klucza z kluczem dzierżawy RMS.

**Krótki przegląd:** poniższa tabela pełni rolę przewodnika po zalecanych topologiach klucza dzierżawy. Więcej informacji można znaleźć w dodatkowej dokumentacji.

W przypadku wdrożenia usługi Azure RMS z użyciem klucza dzierżawy zarządzanego przez firmę Microsoft istnieje możliwość przejścia w późniejszym czasie na klucz zarządzany przez użytkownika (BYOK). Obecnie nie ma jednak możliwości zmiany klucza dzierżawy usługi Azure RMS z BYOK na zarządzany przez firmę Microsoft.

|Wymaganie biznesowe|Zalecana topologia klucza dzierżawy|
|------------------------|-----------------------------------|
|Skorzystaj z możliwości szybkiego wdrożenia usługi Azure RMS — proces nie wymaga użycia żadnego specjalnego sprzętu|Klucz zarządzany przez firmę Microsoft|
|Wymagana pełna funkcjonalność IRM w usłudze Exchange Online z usługą Azure RMS|Klucz zarządzany przez firmę Microsoft|
|Klucze są tworzone przez użytkownika i bezpiecznie przechowywane w sprzętowym module zabezpieczeń (HSM)|BYOK<br /><br />Obecnie wybór tej konfiguracji powoduje ograniczenie funkcjonalności IRM w usłudze Exchange Online. Aby uzyskać więcej informacji, zobacz [Cennik i ograniczenia dotyczące funkcji BYOK](byok-price-restrictions.md).|

## Wybierz topologię klucza dzierżawy: klucz zarządzany przez firmę Microsoft (ustawienie domyślne) lub klucz zarządzany przez użytkownika (BYOK)
Zdecyduj, która topologia klucza dzierżawy jest najodpowiedniejsza dla Twojej organizacji. Domyślnie usługa Azure RMS generuje klucz dzierżawy i zarządza większością aspektów cyklu jego życia. Jest to najprostsza opcja, która wiąże się z najmniejszą liczbą obowiązków administracyjnych użytkownika. W większości przypadków użytkownik nie musi nawet wiedzieć, że ma klucz dzierżawy. Wystarczy, że zarejestruje się w usłudze Azure RMS — resztą procesu zarządzania kluczem zajmie się firma Microsoft.

Możesz też skorzystać z pełnej kontroli nad swoim kluczem dzierżawy, używając usługi [Azure Key Vault](https://azure.microsoft.com/services/key-vault/). Ten scenariusz obejmuje utworzenie klucza dzierżawy i lokalne przechowywanie kopii głównej. Ten model jest często określany mianem BYOK (ang. Bring Your Own Key), czyli „Przynieś własny klucz”. Po wybraniu tej opcji:

1.  Klucz dzierżawy jest generowany lokalnie przez użytkownika w sposób zgodny z zasadami dotyczącymi infrastruktury IT i zasadami dotyczącymi zabezpieczeń obowiązującymi w organizacji.

2.  Przechowywany lokalnie klucz jest bezpiecznie przesyłany z lokalnego sprzętowego modułu zabezpieczeń (HSM, Hardware Security Module) do należących do firmy Microsoft i zarządzanych przez nią modułów HSM, przy użyciu usługi Azure Key Vault. W toku całego tego procesu klucz dzierżawy nigdy nie przekracza granic zabezpieczeń sprzętowych.

3.  W przypadku przeniesienia klucza dzierżawy do firmy Microsoft pozostaje on objęty ochroną usługi Azure Key Vault.

Choć generowane niemalże w czasie rzeczywistym dzienniki z usługi Azure RMS są opcjonalne, warto z nich skorzystać, aby przekonać się, kiedy i w jaki sposób jest używany klucz dzierżawy.

> [!NOTE]
> Dodatkowym środkiem ochrony dostępnym w usłudze Azure Key Vault są wykorzystywane w jej ramach oddzielne domeny zabezpieczeń dla centrów danych w regionach, takich jak Ameryka Północna; Europa, Bliski Wschód i Afryka (EMEA) oraz Azja. Ponadto dotyczy to różnych wystąpień platformy Azure, np. Microsoft Azure Germany i Azure Government. Klucz dzierżawy, którym zarządza użytkownik, jest powiązany z domeną zabezpieczeń odpowiadającą regionowi lub wystąpieniu, w którym jest zarejestrowana dzierżawa usługi RMS. Na przykład klucz dzierżawy europejskiego klienta nie może zostać użyty w centrach danych w Ameryce Północnej ani Azji.

## Cykl życia klucza dzierżawy
Jeśli użytkownik zdecyduje, że to firma Microsoft ma zarządzać kluczem dzierżawy, będzie ona obsługiwać większość operacji związanych z cyklem życia klucza. Jeśli jednak użytkownik chce zarządzać kluczem dzierżawy, będzie odpowiadać za wiele operacji związanych z cyklem życia klucza oraz za niektóre dodatkowe procedury w usłudze Azure Key Vault.

Na poniższych diagramach omówiono te dwie opcje i przedstawiono ich porównanie. Na pierwszym diagramie pokazano, jak niskie są koszty administracyjne ponoszone przez użytkownika w przypadku konfiguracji domyślnej, gdy to firma Microsoft zarządza kluczem dzierżawy.

![Cykl życia klucza dzierżawy usługi Azure RMS w przypadku zarządzania kluczem przez firmę Microsoft (konfiguracja domyślna)](../media/RMS_BYOK_cloud.png)

Drugi diagram przedstawia dodatkowe kroki wymagane w przypadku, gdy za zarządzanie kluczem dzierżawy odpowiada użytkownik.

![Cykl życia klucza dzierżawy usługi Azure RMS w przypadku zarządzania kluczem przez użytkownika (konfiguracja BYOK)](../media/RMS_BYOK_onprem4.png)

Jeśli zdecydujesz się powierzyć firmie Microsoft zarządzanie kluczem dzierżawy, w celu wygenerowania klucza nie są wymagane żadne dalsze działania — można przejść bezpośrednio do sekcji [Następne kroki](plan-implement-tenant-key.md#next-steps).

Jeśli użytkownik zdecyduje się samodzielnie zarządzać kluczem dzierżawy, powinien przeczytać poniższe sekcje, aby uzyskać więcej informacji.

## Wdrażanie klucza dzierżawy usługi Azure Rights Management

Użyj zawartych w tej sekcji informacji oraz procedur, aby wygenerować klucz dzierżawy i samodzielnie nim zarządzać; scenariusz BYOK:


> [!IMPORTANT]
> Jeśli używasz już usługi [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] (usługa została aktywowana) i masz użytkowników, którzy korzystają z pakietu Office 2010, przed rozpoczęciem realizacji tych procedur [skontaktuj się z pomocą techniczną firmy Microsoft](../get-started/information-support.md#to-contact-microsoft-support). W zależności od scenariusza i wymagań może być możliwe dalsze używanie funkcji BYOK, mogą jednak mieć zastosowanie wybrane ograniczenia lub może zajść potrzeba wykonania dodatkowych kroków.
> 
> [Skontaktuj się z pomocą techniczną firmy Microsoft](../get-started/information-support.md#to-contact-microsoft-support) także wtedy, gdy w Twojej organizacji obowiązują konkretne zasady dotyczące postępowania z kluczami.

### Wymagania wstępne dotyczące funkcji BYOK
Poniższa tabela zawiera listę wymagań wstępnych, które należy spełnić, aby móc korzystać z funkcji BYOK.

|Wymaganie|Więcej informacji|
|---------------|--------------------|
|Subskrypcja obejmująca usługę Azure RMS.|Aby uzyskać więcej informacji o dostępnych subskrypcjach, zobacz [Subskrypcje usług w chmurze, które obsługują usługę Azure RMS](../get-started/requirements-subscriptions.md).|
|Nie należy używać usługi RMS dla użytkowników indywidualnych ani usługi Exchange Online. Użytkownicy, którzy zdecydują się korzystać z usługi Exchange Online, muszą zrozumieć i zaakceptować ograniczenia związane z korzystaniem z funkcji BYOK w tej konfiguracji.|Aby uzyskać więcej informacji na temat ogólnych i bieżących ograniczeń dotyczących korzystania z funkcji BYOK, zobacz [Cennik i ograniczenia dotyczące funkcji BYOK](byok-price-restrictions.md).<br /><br />**Ważne**: funkcja BYOK nie jest obecnie zgodna z usługą Exchange Online.|
|Wszystkie wymagania wstępne wymienione dla rozwiązania BYOK usługi Key Vault.|Zobacz [Wymagania wstępne dla funkcji BYOK](https://azure.microsoft.com/documentation/articles/key-vault-hsm-protected-keys/#prerequisites-for-byok) w dokumentacji usługi Azure Key Vault. <br /><br />**Uwaga**: do przeprowadzenia migracji z usługi AD RMS do usługi Azure RMS przy użyciu klucza oprogramowania i klucza sprzętowego wymagane jest oprogramowanie układowe firmy Thales w wersji 11.62 lub nowszej.|
|Moduł administracyjny usługi Azure RMS dla programu Windows PowerShell.|Instrukcje instalacji znajdują się w sekcji [Instalowanie programu Windows PowerShell dla usługi Azure Rights Management](../deploy-use/install-powershell.md). <br /><br />Jeśli ten moduł programu Windows PowerShell został już wcześniej zainstalowany, wykonaj następujące polecenie, aby sprawdzić, czy numer wersji nie jest niższy niż **2.5.0.0**: `(Get-Module aadrm -ListAvailable).Version`|

Aby uzyskać więcej informacji o modułach HSM firmy Thales i sposobie ich wykorzystania w usłudze Azure Key Vault, zobacz [witrynę sieci Web firmy Thales](https://www.thales-esecurity.com/msrms/cloud).

Aby wygenerować i przenieść własny klucz dzierżawy do usługi Azure Key Vault, wykonaj procedury opisane w temacie [Jak wygenerować i przenieść klucze chronione przy użyciu modułu HSM do usługi Azure Key Vault](https://azure.microsoft.com/documentation/articles/key-vault-hsm-protected-keys/) w dokumentacji usługi Azure Key Vault.

Gdy klucz jest przesyłany do usługi Key Vault, otrzymuje identyfikator klucza w usłudze Key Vault, który jest adresem URL zawierającym nazwę magazynu, kontener kluczy, nazwę klucza i wersję klucza. Na przykład: **https://contosorms-kv.vault.azure.net/keys/contosorms-byok/aaaabbbbcccc111122223333**. Należy polecić usłudze Azure RMS użycie tego klucza poprzez określenie tego adresu URL.

Zanim usługa Azure RMS będzie mogła użyć tego klucza, należy autoryzować usługę Azure RMS do używania kluczy znajdujących się w magazynie kluczy organizacji. Aby to zrobić, administrator usługi Azure Key Vault używa polecenia cmdlet programu PowerShell dla usługi Key Vault, [Set-AzureRmKeyVaultAccessPolicy](https://msdn.microsoft.com/library/mt603625.aspx), i przydziela uprawnienia głównej nazwie usługi Azure RMS, **Microsoft.Azure.RMS**. Na przykład:

    Set-AzureRmKeyVaultAccessPolicy -VaultName 'ContosoRMS-kv' -ResourceGroupName 'ContosoRMS-byok-rg' -ServicePrincipalName Microsoft.Azure.RMS -PermissionsToKeys decrypt,encrypt,unwrapkey,wrapkey,verify,sign 

Teraz możesz przystąpić do konfigurowania usługi Azure RMS do użycia tego klucza jako klucza dzierżawy usługi Azure RMS w organizacji. Korzystając z poleceń cmdlet usługi Azure RMS, nawiąż połączenie z usługą Azure RMS i zaloguj się:

    Connect-AadrmService

Następnie uruchom polecenie [cmdlet Use-AadrmKeyVaultKey](https://msdn.microsoft.com/library/azure/mt759829.aspx), określając adres URL klucza. Na przykład:

    Use-AadrmKeyVaultKey -KeyVaultKeyUrl "https://contosorms-kv.vault.azure.net/keys/contosorms-byok/aaaabbbbcccc111122223333"

Jeśli chcesz potwierdzić, że adres URL klucza jest skonfigurowany prawidłowo w usłudze Azure RMS, w usłudze Azure Key Vault możesz uruchomić polecenie cmdlet [Get-AzureKeyVaultKey](https://msdn.microsoft.com/library/dn868053.aspx), aby zobaczyć adres URL klucza.


## Następne kroki

Gdy udało się już zaplanować używanie klucza dzierżawy i w razie potrzeby wygenerować go, wykonaj następujące czynności:

1.  Rozpocznij korzystanie z klucza dzierżawy:

    -   Jeśli jeszcze nie zostało to zrobione, należy teraz aktywować usługę Rights Management, aby organizacja mogła zacząć korzystać z usługi RMS. Użytkownicy natychmiast otrzymują możliwość korzystania ze swojego klucza dzierżawy (zarządzanego przez firmę Microsoft lub przez użytkownika w usłudze Azure Key Vault).

        Aby uzyskać więcej informacji o aktywacji, zobacz [Aktywacja usługi Azure Rights Management](../deploy-use/activate-service.md).

    -   Jeśli usługa Rights Management została już aktywowana, a następnie podjęto decyzję o samodzielnym zarządzaniu kluczem dzierżawy, użytkownicy stopniowo przechodzą ze starego klucza dzierżawy na nowy. Okres przejściowy może trwać do kilku tygodni. Dokumenty i pliki, które były chronione przy użyciu starego klucza dzierżawy, pozostają dostępne dla użytkowników upoważnionych do dostępu do nich.

2.  Rozważ włączenie funkcji rejestrowania użycia, która tworzy dzienniki uwzględniające każdą czynność wykonywaną w ramach usługi Azure Rights Management.

    Użytkownik samodzielnie zarządzający kluczem dzierżawy może uzyskać dostęp do rejestrów uwzględniających informacje o użyciu jego własnego klucza dzierżawy. Poniżej znajduje się fragment kodu z pliku dziennika wyświetlany w programie Excel. Typy żądań **KeyVaultDecryptRequest** i **KeyVaultSignRequest** pokazują, że klucz dzierżawy jest w użyciu.

    ![Plik dziennika wyświetlony w programie Excel, pokazujący, że klucz dzierżawy jest w użyciu](../media/RMS_Logging.png)

    Aby uzyskać więcej informacji na temat rejestrowania użycia, zobacz [Rejestrowanie i analizowanie danych użycia usługi Azure Rights Management](../deploy-use/log-analyze-usage.md).

3.  Wykonuj czynności związane z obsługą klucza dzierżawy.

    Aby uzyskać więcej informacji, zobacz [Operacje związane z kluczem dzierżawy usługi Azure Rights Management](../deploy-use/operations-tenant-key.md).




<!--HONumber=Aug16_HO3-->


