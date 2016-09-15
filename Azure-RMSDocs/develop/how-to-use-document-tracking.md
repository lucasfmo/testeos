---
title: "Jak korzystać ze śledzenia dokumentów | Azure RMS"
description: "Funkcja śledzenia dokumentów wymaga zrozumienia podstaw zarządzania skojarzonymi metadanymi i rejestracji w usłudze."
keywords: 
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 70E10936-7953-49B0-B0DC-A5E7C4772E60
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ca4982cc86d9c006486540055de7c165adca21da
ms.openlocfilehash: 9872317c2d5f5f56f28ed2683d7ebc9743041a37


---

# Instrukcje: korzystanie ze śledzenia dokumentów

Korzystanie z funkcji śledzenia dokumentów wymaga zrozumienia podstaw zarządzania skojarzonymi metadanymi i rejestracji w usłudze.

## Zarządzanie metadanymi śledzenia dokumentów

Każdy system operacyjny obsługujący śledzenie dokumentów charakteryzuje się podobnymi implementacjami. Obejmują one zestaw właściwości reprezentujących metadane, nowy parametr dodany do metod tworzenia zasad użytkowników oraz metodę rejestrowania zasad do śledzenia przy użyciu usługi śledzenia dokumentów.

Z perspektywy operacyjnej śledzenie dokumentów wymaga tylko właściwości **nazwy zawartości** i **typu powiadomienia**.

Sekwencja kroków używanych do konfigurowania śledzenia dokumentów dla danego elementu zawartości to:

-   Utwórz obiekt **metadanych licencji**.

    Więcej informacji zawierają opisy metod [**LicenseMetadata**](/rights-management/sdk/4.2/api/android/com.microsoft.rightsmanagement#msipcthin2_licensemetadata_interface_java) i [**MSLicenseMetadata**](/rights-management/sdk/4.2/api/iOS/mslicensemetadata#msipcthin2_mslicensemetadata_class_objc).

-   Ustaw właściwości **nazwy zawartości** i **typu powiadomienia**. Są to jedyne wymagane właściwości.

    Więcej informacji zawierają opisy metod dostępu do właściwości dla klasy metadanych licencji odpowiedniej dla platformy, [**LicenseMetadata**](/rights-management/sdk/4.2/api/android/com.microsoft.rightsmanagement#msipcthin2_licensemetadata_interface_java) lub [**MSLicenseMetadata**](/rights-management/sdk/4.2/api/iOS/mslicensemetadata#msipcthin2_mslicensemetadata_class_objc).

-   Według typu zasad: szablon lub ad hoc:

    -   W przypadku śledzenia dokumentów na podstawie szablonu utwórz obiekt **zasad użytkownika** przekazujący metadane licencji jako parametr.

        Więcej informacji zawierają opisy metod [**UserPolicy.create**](/rights-management/sdk/4.2/api/android/userpolicy#msipcthin2_userpolicy_class_java) i [**MSUserPolicy.userPolicyWithTemplateDescriptor**](/rights-management/sdk/4.2/api/iOS/msuserpolicy#msipcthin2_msuserpolicy_templatedescriptor_property_objc).

    -   W przypadku śledzenia dokumentów ad hoc ustaw właściwość **metadanych licencji** obiektu **deskryptora zasad**.

        Więcej informacji zawierają opisy metod [**PolicyDescriptor.getLicenseMetadata**](/rights-management/sdk/4.2/api/android/policydescriptor#msipcthin2_policydescriptor_interface_java), [**PolicyDescriptor.setLicenseMetadata**](/rights-management/sdk/4.2/api/android/policydescriptor#msipcthin2_policydescriptor_setlicensemetadata_java) i [**MSPolicyDescriptor.licenseMetadata**](/rights-management/sdk/4.2/api/iOS/mspolicydescriptor#msipcthin2_mspolicydescriptor_licensemetadata_property_objc).

    **Uwaga** Obiekt metadanych licencji jest dostępny bezpośrednio tylko podczas procesu konfigurowania śledzenia dokumentów dla danych zasad użytkownika. Po utworzeniu obiektu zasad użytkownika skojarzone metadane licencji nie są dostępne, np. zmiana wartości metadanych licencji nie ma żadnego wpływu.

     

-   Wywołaj metodę rejestracji platformy w celu śledzenia dokumentów.

    Zobacz opis metody [**MSUserPolicy.registerForDocTracking**](/rights-management/sdk/4.2/api/iOS/msuserpolicy#msipcthin2_msuserpolicy_registerfordoctracking_userid_authenticationcallback_completionblock_method_objc) lub [**UserPolicy.registerForDocTracking**](/rights-management/sdk/4.2/api/iOS/msuserpolicy#msipcthin2_msuserpolicy_registerfordoctracking_userid_authenticationcallback_completionblock_method_objc).

 

 



<!--HONumber=Jul16_HO3-->


