---
title: "Samouczek Szybki start dla usługi Azure Information Protection, krok 1 | Azure Rights Management"
description: "Krok 1 samouczka wprowadzającego, dzięki któremu możesz szybko wypróbować usługę Microsoft Azure Information Protection w swojej organizacji. Wystarczą 4 proste kroki, które powinny zająć mniej niż 10 minut."
author: cabailey
manager: mbaldwin
ms.date: 07/291/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: f6dbb143-96f7-4a9c-8208-be9280d69de9
translationtype: Human Translation
ms.sourcegitcommit: 93444affe94b280db2c9e4e2960c6902e491dec6
ms.openlocfilehash: 128952778ec317584e558e409961e2921c4ecd07


---

# Krok 1. Aktywowanie usługi Rights Management
 
>*Dotyczy: Azure Information Protection (wersja zapoznawcza)*

**[Niniejsze informacje mają charakter wstępny i mogą ulec zmianom. ]**

> [!NOTE]
>Jeśli chcesz wyłącznie klasyfikować dane bez włączania ochrony usługi Azure Rights Management lub jeśli już aktywowano usługę Azure Rights Management dla dzierżawcy — przejdź wprost do [następnego kroku](infoprotect-tutorial-step2.md). 

Po aktywowaniu usługi Azure Rights Management możesz chronić swoje najbardziej poufne dokumenty i pliki po ich sklasyfikowaniu. Usługę Azure Rights Management możesz aktywować przy użyciu centrum administracyjnego usługi Office 365 lub klasycznego portalu Azure:

-   Jeśli masz subskrypcję usługi Office 365 obejmującą usługę Azure Rights Management albo subskrypcję usługi Office 365 bez usługi Azure Rights Management, ale z usługą Azure RMS Premium: **użyj centrum administracyjnego usługi Office 365**.

-   Jeśli nie masz subskrypcji usługi Office 365: **użyj klasycznego portalu Azure**.

### Aby aktywować usługę Rights Management w klasycznym centrum administracyjnym usługi Office 365

> [!NOTE]
> Jeśli używasz **centrum administracyjnego usługi Office 365 w wersji zapoznawczej** zamiast centrum administracyjnego usługi Office 365 w wersji klasycznej, możesz użyć instrukcji z tematu [Jak aktywować usługę Azure Rights Management w centrum administracyjnym usługi Office 365 w wersji zapoznawczej](../deploy-use/activate-office365-preview.md) lub przełączyć się do klasycznej wersji w celu użycia poniższych instrukcji. Aby przełączyć się, po zalogowaniu kliknij pozycję **Przejdź do starego centrum administracyjnego** na stronie **Strona główna**.

1.  Przejdź do [portalu usługi Office 365](https://portal.office.com/) i zaloguj się przy użyciu konta administratora globalnego usługi Office 365.

2.  Jeśli centrum administracyjne usługi Office 365 nie zostanie wyświetlone automatycznie, wybierz ikonę uruchamiania aplikacji w lewym górnym rogu i wybierz pozycję **Administrator**. Kafelek **Administrator** jest widoczny tylko dla administratorów usługi Office 365.

  > [!TIP]
  > Aby uzyskać pomoc dotyczącą centrum administracyjnego, zobacz [Centrum administracyjne usługi Office 365 — pomoc administratora](https://support.office.com/article/About-the-Office-365-admin-center-Admin-Help-58537702-d421-4d02-8141-e128e3703547).

3.  W okienku po lewej stronie rozwiń węzeł **USTAWIENIA USŁUGI**.

4.  Kliknij pozycję **Rights Management**.

5.  Na stronie **RIGHTS MANAGEMENT** kliknij pozycję **Zarządzaj**.

6.  Na stronie **Rights Management** kliknij pozycję **Aktywuj**.

7.  Po wyświetleniu monitu **Czy chcesz aktywować usługę Rights Management?** kliknij pozycję **Aktywuj**.

Zostanie wyświetlony komunikat **Usługa Rights Management została aktywowana** wraz z opcją dezaktywowania tej usługi (może być konieczne ręczne odświeżenie strony).

Tym razem nie klikaj pozycji **Funkcje zaawansowane**. Kliknięcie tej pozycji spowoduje wyświetlenie klasycznego portalu Azure, umożliwiającego konfigurowanie szablonów niestandardowych, które nie są potrzebne w tym samouczku. Zamiast tego możesz zamknąć centrum administracyjne usługi Office 365.

### Aby aktywować usługę Rights Management w klasycznym portalu Azure

1.  Przejdź do [klasycznego portalu Azure](http://go.microsoft.com/fwlink/p/?LinkID=275081) i zaloguj się przy użyciu konta administratora globalnego usługi Azure Active Directory.

2.  W okienku po lewej stronie kliknij opcję **ACTIVE DIRECTORY**.

3.  Na stronie **Active Directory** kliknij pozycję **RIGHTS MANAGEMENT**.

4.  Wybierz katalog do zarządzania dla usługi [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)], kliknij pozycję **AKTYWUJ**, a następnie potwierdź akcję.

**STAN USŁUGI RIGHTS MANAGEMENT** powinien być teraz ustawiony na **Aktywna**, a opcja **AKTYWUJ** zostaje zastąpiona opcją **DEZAKTYWUJ**.

W portalu można skonfigurować inne opcje usługi Rights Management, ale nie są one potrzebne w tym samouczku, dlatego możesz zamknąć klasyczny portal Azure.

To wszystko, co musisz zrobić w pierwszym kroku. Usługa Azure Rights Management jest aktywna, więc w dalszej części samouczka możesz wybrać jeden z jej domyślnych szablonów do ochrony dokumentów i wiadomości e-mail sklasyfikowanych jako poufne.

W przypadku wdrożenia produkcyjnego prawdopodobnie zechcesz skonfigurować niestandardowe szablony zastępujące lub uzupełniające dwa domyślne szablony usługi Azure Rights Management. Jednak w naszym samouczku szablony niestandardowe nie są potrzebne, dlatego możesz teraz przejść do kroku 2.

|Jeśli potrzebujesz dodatkowych informacji|Dodatkowe informacje|
|--------------------------------|--------------------------|
|Informacje o aktywacji usługi Azure Rights Management|[Aktywacja usługi Azure Rights Management](../deploy-use/activate-service.md)|
|Informacje na temat szablonów domyślnych i sposobu tworzenia nowych szablonów niestandardowych|[Konfigurowanie szablonów niestandardowych usługi Azure Management Rights](../deploy-use/configure-custom-templates.md)|

>[!div class="step-by-step"]
[&#171; Wprowadzenie](infoprotect-quick-start-tutorial.md)
[Krok 2 &#187;](infoprotect-tutorial-step2.md)



<!--HONumber=Jul16_HO5-->


