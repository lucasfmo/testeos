---
# required metadata

title: "Útmutató: A dokumentumkövetés használata | Azure RMS"
description: A dokumentumok nyomon követését biztosító szolgáltatás használatához ismerni kell a szolgáltatáshoz kapcsolódó metaadatok és regisztráció kezelését.
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 70E10936-7953-49B0-B0DC-A5E7C4772E60
# optional metadata

#ROBOTS:
audience: developer
#ms.devlang:
ms.reviewer: shubhamp
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Útmutató: A dokumentumkövetés használata

A dokumentumok nyomon követését biztosító szolgáltatás használatához ismerni kell a szolgáltatáshoz kapcsolódó metaadatok és regisztráció kezelését.

## Dokumentumkövetési metaadatok kezelése

Mindegyik dokumentumkövetést támogató operációs rendszer hasonló megvalósításokkal rendelkezik. Ezek közé tartozik egy tulajdonságkészlet, amely a metaadatokat képviseli, egy új, a felhasználóiházirend-létrehozási metódusokhoz tartozó paraméter, valamint egy, a dokumentumkövetési szolgáltatással nyomon követhető metódus a házirend regisztrálásához.

Működés közben csak a **tartalom neve** és az **értesítés típusa** tulajdonság szükséges a dokumentumok nyomon követéséhez.

A dokumentumkövetés beállításának lépései egy adott tartalomhoz:

-   Hozzon létre egy **licencmetaadat**-objektumot.

    További információk: [**LicenseMetadata**](/rights-management/sdk/4.2/api/android/com.microsoft.rightsmanagement#msipcthin2_licensemetadata_interface_java) vagy [**MSLicenseMetadata**](/rights-management/sdk/4.2/api/iOS/mslicensemetadata#msipcthin2_mslicensemetadata_class_objc).

-   Adja meg a **tartalom neve** és az **értesítés típusa** tulajdonság értékét. Csak ezek a tulajdonságok kötelezőek.

    További információért tekintse meg a tulajdonság-hozzáférési metódusokat a platformhoz megfelelő licencmetaadat-osztályhoz: [**LicenseMetadata**](/rights-management/sdk/4.2/api/android/com.microsoft.rightsmanagement#msipcthin2_licensemetadata_interface_java) vagy [**MSLicenseMetadata**](/rights-management/sdk/4.2/api/iOS/mslicensemetadata#msipcthin2_mslicensemetadata_class_objc).

-   Házirendtípus szerint; sablon vagy alkalmi:

    -   Sablonalapú dokumentumkövetéshez hozzon létre egy **felhasználói házirend** objektumot a licencmetaadatok paraméterként való átadásával.

        További információk: [**UserPolicy.create**](/rights-management/sdk/4.2/api/android/userpolicy#msipcthin2_userpolicy_class_java) és [**MSUserPolicy.userPolicyWithTemplateDescriptor**](/rights-management/sdk/4.2/api/iOS/msuserpolicy#msipcthin2_msuserpolicy_templatedescriptor_property_objc).

    -   Alkalmi dokumentumkövetéshez adja meg a **licencmetaadat** tulajdonságot a **házirendleíró** objektumon.

        További információk: [**PolicyDescriptor.getLicenseMetadata**](/rights-management/sdk/4.2/api/android/policydescriptor#msipcthin2_policydescriptor_interface_java), [**PolicyDescriptor.setLicenseMetadata**](/rights-management/sdk/4.2/api/android/policydescriptor#msipcthin2_policydescriptor_setlicensemetadata_java) és [**MSPolicyDescriptor.licenseMetadata**](/rights-management/sdk/4.2/api/iOS/mspolicydescriptor#msipcthin2_mspolicydescriptor_licensemetadata_property_objc).

    **Megjegyzés**  A licencmetaadat-objektum csak közvetlenül érhető el a dokumentumkövetés beállítása során az adott felhasználói házirend számára. Ha létrejött a felhasználóiházirend-objektum, a társított licencmetaadatok nem érhetők el, azaz a licencmetaadatok értékeinek módosítása nem fejt ki hatást.

     

-   Hívja meg a platformregisztrációs metódust a dokumentumkövetéshez.

    Lásd: [**MSUserPolicy.registerForDocTracking**](/rights-management/sdk/4.2/api/iOS/msuserpolicy#msipcthin2_msuserpolicy_registerfordoctracking_userid_authenticationcallback_completionblock_method_objc) vagy [**UserPolicy.registerForDocTracking**](/rights-management/sdk/4.2/api/iOS/msuserpolicy#msipcthin2_msuserpolicy_registerfordoctracking_userid_authenticationcallback_completionblock_method_objc).

 

 


<!--HONumber=Jun16_HO2-->


