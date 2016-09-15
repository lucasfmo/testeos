---
title: "Jak pracować z ustawieniami szyfrowania | Azure RMS"
description: "Ten artykuł kieruje użytkowników do pakietów szyfrowania firmy Microsoft"
keywords: 
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: B1D2C227-F43D-4B18-9956-767B35145792
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 29e856e3e9990f81a791c533ddad5a332093d5d3
ms.openlocfilehash: 82903eff43ee2dee7ef64e618171225a06013d99


---

# Instrukcje: korzystanie z ustawień szyfrowania

Ten temat kieruje użytkowników do pakietów szyfrowania firmy Microsoft i zawiera przykłady fragmentów kodu, w których zastosowano te pakiety.

## Obsługa nowego domyślnego algorytmu szyfrowania AES 256

Żaden dodatkowy kod nie jest wymagany do korzystania z szyfrowania opartego na nowym domyślnym algorytmie *AES 256* przy założeniu, że do opracowywania aplikacji jest używana aktualizacja zestawu RMS SDK 2.1 z marca 2015 lub nowsza. Zachęcamy do rozważenia możliwości zaktualizowania aplikacji przy użyciu tej wersji w celu skorzystania z dodatkowych zalet zabezpieczeń algorytmu *AES 256*.

> [!IMPORTANT]
> Obsługa plików chronionych przy użyciu algorytmu *AES 256* była dostępna już w [wersji z października 2014 roku](release-notes-rtm.md). Jeśli używasz aplikacji utworzonych za pomocą wersji zestawu SDK sprzed października 2014 r., ta aktualizacja spowoduje awarię aplikacji. Upewnij się, że klienci aplikacji, które tworzysz, używają zaktualizowanego zestawu SDK lub są gotowi do natychmiastowego przeprowadzenia aktualizacji do najnowszej wersji aplikacji.

 
## Obsługa szyfrowania w interfejsie API

Począwszy od [aktualizacji z marca 2015 roku](release-notes-rtm.md), uwzględniliśmy następujące trzy flagi w naszym interfejsie API i skojarzonych pakietach szyfrowania:

-   IPC\_ENCRYPTION\_PACKAGE\_AES256\_CBC4K
-   IPC\_ENCRYPTION\_PACKAGE \_AES128\_CBC4K
-   IPC\_ENCRYPTION\_PACKAGE \_AES128\_ECB (nazywane również przestarzałymi algorytmami)

Flag pakietów szyfrowania (zobacz [**Preferowane szyfrowanie**](/rights-management/sdk/2.1/api/win/constants#msipc_preferred_encryption)) można używać razem z nową flagą właściwości licencji **IPC\_LI\_PREFERRED\_ENCRYPTION\_PACKAGE**.

Poniższe przykłady fragmentu kodu przedstawiają sposób użycia nowej właściwości licencji.

## Przestarzałe algorytmy

Flaga **IPC\_LI\_DEPRECATED\_ENCRYPTION\_ALGORITHMS** nie jest już widoczna w interfejsie API. Oznacza to, że kompilacje aplikacji odwołujących się do tej flagi nie będą możliwe w przyszłości, ale aplikacje, które zostały już utworzone przy użyciu tej flagi, będą nadal działać, ponieważ flaga będzie prywatnie uznawana w kodzie interfejsu API.

Nadal będzie można uzyskiwać korzyści zapewniane przez przestarzałą flagę algorytmów szyfrowania, zmieniając po prostu jedną flagę. Jako przykład mogą posłużyć poniższe fragmenty kodu.

## Ochrona plików przy użyciu algorytmu AES 256 CBC4K

Zmiana kodu nie jest potrzebna, ponieważ *AES 256* CBC4K jest ustawieniem domyślnym.

    C++

    hr = IpcCreateLicenseFromTemplateID(pcTil-&gt;aTi[0].wszID,
                                    0,
                                    NULL,
                                    &amp;pLicenseHandle);


## Ochrona plików przy użyciu algorytmu AES-128 CBC4K

    C++

    hr = IpcCreateLicenseFromTemplateID(pcTil-&gt;aTi[0].wszID,
                                    0,
                                    NULL,
                                    &amp;pLicenseHandle);

    DWORD dwEncryptionMode = IPC_ENCRYPTION_PACKAGE_AES128_CBC4K;

    hr = IpcSetLicenseProperty(pLicenseHandle,
                           false,
                           IPC_LI_PREFERRED_ENCRYPTION_PACKAGE,
                           &amp;dwEncryptionMode);


## Ochrona plików przy użyciu algorytmu AES-128 ECB (przestarzałe algorytmy)

W tym przykładzie przedstawiono również nową metodą obsługi *przestarzałych algorytmów*.

    C++
    
    hr = IpcCreateLicenseFromTemplateID(pcTil-&gt;aTi[0].wszID,
                                    0,
                                    NULL,
                                    &amp;pLicenseHandle);

    DWORD dwEncryptionMode = IPC_ENCRYPTION_PACKAGE_AES128_ECB;

    hr = IpcSetLicenseProperty(pLicenseHandle,
                           false,
                           IPC_LI_PREFERRED_ENCRYPTION_PACKAGE,
                           &amp;dwEncryptionMode);

 

 



<!--HONumber=Jun16_HO4-->


