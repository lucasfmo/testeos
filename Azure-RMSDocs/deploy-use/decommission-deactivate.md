---
title: "Likwidowanie i dezaktywowanie usługi Azure Rights Management | Azure RMS"
description: 
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 0b1c2064-0d01-45ae-a541-cebd7fd762ad
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 0f355da35dff62ecee111737eb1793ae286dc93e
ms.openlocfilehash: 8c114336551417fdbf1503ffc8350e3fc28e9c95


---

# Likwidowanie i dezaktywowanie usługi Azure Rights Management

*Dotyczy usług: Azure Rights Management, Office 365*

To Ty masz zawsze kontrolę nad tym, czy organizacja chroni zawartość za pomocą usługi [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] (Azure RMS). Jeśli nie chcesz już korzystać z tego rozwiązania do ochrony informacji, możesz mieć pewność, że poprzednio chroniona zawartość nie zostanie zablokowana. Jeśli nie musisz mieć ciągłego dostępu do wcześniej chronionej zawartości, możesz po prostu dezaktywować usługę i zaczekać, aż subskrypcja usługi Azure Rights Management wygaśnie. Takie rozwiązanie byłoby na przykład odpowiednie w sytuacji, gdy testowanie usługi [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] zakończyło się przed wdrożeniem jej w środowisku produkcyjnym.

Jeśli jednak usługa [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] została wdrożona do produkcji, przed dezaktywowaniem usługi upewnij się, że masz kopię klucza dzierżawy usługi Azure Rights Management, i zrób to przed wygaśnięciem subskrypcji. Dzięki temu zachowasz dostęp do zawartości, która była chroniona przez usługę Azure Rights Management po dezaktywowaniu tej usługi. W przypadku użycia rozwiązania BYOK („użyj własnego klucza”) umożliwiającego generowanie własnego klucza i zarządzanie nim w module HSM będziesz już mieć klucz dzierżawy usługi Azure Rights Management. Jeśli jednak był to klucz zarządzany przez firmę Microsoft (opcja domyślna), zapoznaj się z instrukcjami dotyczącymi eksportowania klucza dzierżawy w artykule [Operacje dotyczące klucza dzierżawy usługi Azure Rights Management](operations-tenant-key.md).

> [!TIP]
> Nawet po wygaśnięciu subskrypcji dzierżawa usługi Azure Rights Management pozostaje dostępna, co umożliwia korzystanie z zawartości przez dłuższy czas. Nie można już jednak eksportować klucza dzierżawy.

Jeśli masz klucz dzierżawy usługi Azure Rights Management, możesz wdrożyć usługę Rights Management (AD RMS) lokalnie i zaimportować klucz dzierżawy jako zaufaną domenę publikacji (TPD). Następnie możesz wybrać następujące opcje likwidowania wdrożenia usługi Azure Rights Management:

|Jeśli dotyczy to Ciebie...|… Czynności|
|----------------------------|--------------|
|Chcesz, aby wszyscy użytkownicy nadal używali usługi Rights Management, ale za pomocą rozwiązania lokalnego, a nie usługi Azure RMS    →|Użyj polecenia cmdlet [Set-AadrmMigrationUrl](https://msdn.microsoft.com/library/azure/dn629429.aspx), aby przekierować istniejących użytkowników do wdrożenia lokalnego, jeśli używają oni zawartości chronionej po tej zmianie. Użytkownicy będą automatycznie używać instalacji usług AD RMS w przypadku korzystania z chronionej zawartości.<br /><br />Aby użytkownicy mogli korzystać z zawartości, która była chroniona przed wprowadzeniem tej zmiany, musisz przekierować klientów do wdrożenia lokalnego przy użyciu klucza rejestru **LicensingRedirection** dla pakietu Office 2016 lub Office 2013, zgodnie z opisem w [sekcji dotyczącej odnajdowania usługi](../rms-client/client-deployment-notes.md) w uwagach do wdrażania klienta usług RMS, lub klucza rejestru **LicenseServerRedirection** dla pakietu Office 2010, zgodnie z opisem w temacie [Office Registry Settings](https://technet.microsoft.com/library/dd772637%28v=ws.10%29.aspx) (Ustawienia rejestru pakietu Office).|
|Chcesz całkowicie zrezygnować z technologii Rights Management    →|Przyznaj wyznaczonemu użytkownikowi [prawa administratora](../deploy-use/configure-super-users.md) i udostępnij mu [narzędzie RMS Protection Tool](http://www.microsoft.com/en-us/download/details.aspx?id=47256).<br /><br />Administrator ten może następnie używać narzędzia do zbiorczego odszyfrowywania plików w folderach, które były chronione przez usługę Azure Rights Management. Pozwala to na anulowanie ochrony plików i odczytywanie ich bez użycia technologii Rights Management, takiej jak usługa Azure RMS lub AD RMS. To narzędzie może współpracować z usługami Azure RMS i AD RMS, dlatego możesz odszyfrować pliki przed lub po dezaktywowaniu usługi Azure RMS lub w kombinacji tych sytuacji.|
|Nie możesz zidentyfikować wszystkich plików, które były chronione przez usługę RMS, lub chcesz, aby wszyscy użytkownicy mogli automatycznie odczytywać wszystkie pominięte chronione pliki    →|Wdróż ustawienie rejestru na wszystkich komputerach klienckich przy użyciu klucza rejestru **LicensingRedirection** dla pakietu Office 2016 lub Office 2013, zgodnie z opisem w [sekcji dotyczącej odnajdowania usługi](../rms-client/client-deployment-notes.md) w uwagach do wdrażania klienta usług RMS, lub klucza rejestru **LicenseServerRedirection** dla pakietu Office 2010, zgodnie z opisem w temacie [Office Registry Settings](https://technet.microsoft.com/library/dd772637%28v=ws.10%29.aspx) (Ustawienia rejestru pakietu Office).<br /><br />Wdróż również inne ustawienie rejestru, aby uniemożliwić użytkownikom ochronę nowych plików, ustawiając opcję **DisableCreation** na **1**, zgodnie z opisem w temacie [Office Registry Settings](https://technet.microsoft.com/library/dd772637%28v=ws.10%29.aspx) (Ustawienia rejestru pakietu Office).|
|Potrzebujesz kontrolowanej usługi z możliwością odzyskiwania ręcznego w przypadku wszystkich pominiętych plików    →|Przyznaj wyznaczonym użytkownikom w grupie odzyskiwania danych [prawa administratora](../deploy-use/configure-super-users.md) i udostępnij im [Narzędzie ochrony usługi RMS](http://www.microsoft.com/en-us/download/details.aspx?id=47256), aby mogli anulować ochronę plików zleconą przez użytkowników standardowych.<br /><br />Na wszystkich komputerach wdróż ustawienie rejestru, aby uniemożliwić użytkownikom ochronę nowych plików, ustawiając opcję **DisableCreation** na wartość **1**, zgodnie z opisem w temacie [Office Registry Settings](https://technet.microsoft.com/library/dd772637%28v=ws.10%29.aspx) (Ustawienia rejestru pakietu Office).|
Więcej informacji na temat procedur opisanych w tej tabeli można znaleźć w następujących zasobach:

-   Informacje na temat dokumentacji usługi AD RMS i wdrożeń można znaleźć w temacie [Omówienie usług Active Directory Rights Management](https://technet.microsoft.com/library/hh831364.aspx).

-   Aby uzyskać instrukcje dotyczące importowania klucza dzierżawy usługi Azure RMS jako pliku TPD, zobacz [Dodawanie zaufanej domeny publikacji](https://technet.microsoft.com/library/cc771460.aspx).

-   Aby zainstalować moduł programu Windows PowerShell dla usługi Azure RMS w celu ustawienia adresu URL migracji, zobacz [Instalowanie programu Windows PowerShell dla usługi Azure Rights Management](install-powershell.md).

Gdy wszystko będzie gotowe do zdezaktywowania usługi Azure RMS w organizacji, postępuj zgodnie z poniższymi instrukcjami.

## Dezaktywowanie usługi Rights Management
Wykonaj kroki jednej z poniższych procedur, aby zdezaktywować usługę [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)].

> [!TIP]
> Możesz również użyć polecenia cmdlet programu Windows PowerShell, [Disable-Aadrm](http://msdn.microsoft.com/library/windowsazure/dn629422.aspx), aby zdezaktywować usługę [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)].

#### Aby zdezaktywować usługę Rights Management w centrum administracyjnym usługi Office 365

1.  [Zaloguj się do usługi Office 365 za pomocą konta służbowego](https://portal.office.com/) administratora wdrożenia usługi Office 365.

2.  Jeśli centrum administracyjne usługi Office 365 nie zostanie wyświetlone automatycznie, wybierz ikonę uruchamiania aplikacji w lewym górnym rogu i wybierz pozycję **Administrator**. Kafelek **Administrator** jest widoczny tylko dla administratorów usługi Office 365.

    > [!TIP]
    > Aby uzyskać pomoc dotyczącą centrum administracyjnego, zobacz [Centrum administracyjne usługi Office 365 — pomoc administratora](https://support.office.com/article/About-the-Office-365-admin-center-Admin-Help-58537702-d421-4d02-8141-e128e3703547).

3.  W okienku po lewej stronie rozwiń węzeł **USTAWIENIA USŁUGI**.

4.  Kliknij pozycję **Rights Management**.

5.  Na stronie **RIGHTS MANAGEMENT** kliknij pozycję **Zarządzaj**.

6.  Na stronie **Rights Management** kliknij pozycję **Dezaktywuj**.

7.  Po wyświetleniu monitu **Czy chcesz dezaktywować usługę Rights Management?** kliknij pozycję **Dezaktywuj**.

Teraz powinien pojawić się komunikat **Usługa Rights Management nie została aktywowana** oraz opcja jej aktywowania.

#### Aby zdezaktywować usługę Rights Management w klasycznym portalu Azure

1.  Zaloguj się do [klasycznego portalu Azure](http://go.microsoft.com/fwlink/p/?LinkID=275081).

2.  W okienku po lewej stronie kliknij opcję **ACTIVE DIRECTORY**.

3.  Na stronie **Active Directory** kliknij opcję **RIGHTS MANAGEMENT**.

4.  Wybierz katalog do zarządzania dla [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)], kliknij pozycję **DEZAKTYWUJ**, a następnie potwierdź akcję.

**STAN USŁUGI RIGHTS MANAGEMENT** powinien być teraz ustawiony na wartość **Nieaktywna**, a opcja **DEZAKTYWUJ** zostaje zastąpiona opcją **AKTYWUJ**.






<!--HONumber=Jun16_HO4-->


