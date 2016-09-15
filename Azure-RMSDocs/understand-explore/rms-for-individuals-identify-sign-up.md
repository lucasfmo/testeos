---
title: "Jak sprawdzić, czy użytkownicy utworzyli konto usługi RMS dla użytkowników indywidualnych | Azure RMS"
description: 
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: a36c3d99-a794-4f7a-aafb-64a950f1fcf9
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 0f355da35dff62ecee111737eb1793ae286dc93e
ms.openlocfilehash: e577366be26f7296079751e72fb6531b9e28c504


---


# Jak sprawdzić, czy użytkownicy utworzyli konto usługi RMS dla użytkowników indywidualnych

*Dotyczy usługi Azure Rights Management*

Być może zastanawiasz się, w jaki sposób administrator może sprawdzić, czy użytkownicy utworzyli konta usługi RMS dla użytkowników indywidualnych. W tym celu można użyć jednej z poniższych metod lub ich dowolnej kombinacji:

-   Zapytaj użytkowników, jak chronią poufne pliki, zwłaszcza gdy współpracują z osobami spoza organizacji.

-   Jeśli Twoja organizacja ma subskrypcję platformy Azure, użyj polecenia cmdlet [Get-MsolAccountSku](https://msdn.microsoft.com/library/azure/dn194118.aspx) i sprawdź, czy zostanie zwrócona wartość **RIGHTSMANAGEMENT_ADHOC** odpowiadająca jednej z subskrypcji. Jeśli tak się stanie, oznacza to, że organizacji przyznano subskrypcję usługi RMS dla użytkowników indywidualnych wraz z pulą aktywnych jednostek, z których mogą korzystać użytkownicy w celu samodzielnego utworzenia konta.

-   Sporządź spis zainstalowanego i używanego oprogramowania za pomocą rozwiązania do zarządzania systemem, takiego jak program System Center Configuration Manager. Aplikacja do udostępniania usługi Rights Management korzysta z programu **ipviewer.exe**. Możesz bezpłatnie [pobrać i zainstalować tę aplikację](http://go.microsoft.com/fwlink/?LinkId=303970), aby poznać inne jej charakterystyki, których następnie możesz użyć do sporządzenia spisu oprogramowania.

-   Poszukaj rozszerzeń nazw plików utworzonych przez aplikację do udostępniania usługi Rights Management. Najbardziej typowe przykłady rozszerzeń nazw plików to pfile i ppdf, ale w przypadku innych plików ich rozszerzenia również są zmieniane, gdy pliki te są natywnie chronione przez usługę Rights Management. Aby uzyskać więcej informacji, zobacz sekcję [Obsługiwane typy plików i rozszerzenia nazw plików](../rms-client/sharing-app-admin-guide-technical.md#supported-file-types-and-file-name-extensions) w [Przewodniku administratora po aplikacji do udostępniania usługi Rights Management](http://technet.microsoft.com/library/dn339003.aspx).




<!--HONumber=Jul16_HO3-->


