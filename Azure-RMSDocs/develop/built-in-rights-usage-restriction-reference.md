---
title: "A beépített jogosultságok használata | Azure RMS"
description: "Bemutatja az RMS SDK 4.2 által biztosított beépített jogosultságokat és azokat a használati korlátozásokat, amelyeket az alkalmazásnak érvényesítenie kell a korlátozások betartása érdekében."
keywords: 
author: bruceperlerms
manager: mbaldwin
ms.date: 08/24/2016
ms.topic: article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 9142dd29-f1f4-4c2f-82ac-534f14b8bba1
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
experimental: true
experiment_id: priyamo-TableVsFlatList-20160805
translationtype: Human Translation
ms.sourcegitcommit: 024a29d7c7db2e4c0578a95c93e22f8e7a5b173e
ms.openlocfilehash: 4da2bebb10965e99c2e788f035ae8151777700b9


---

# Útmutató: A beépített jogosultságok használata

Ez a témakör bemutatja az Microsoft Rights Management SDK 4.2 által biztosított beépített jogosultságokat és azokat a használati korlátozásokat, amelyeket az alkalmazásnak érvényesítenie kell a korlátozások betartása érdekében. Az alábbiakban a beépített jogosultságok láthatók; a közös jogosultságok, a szerkeszthető dokumentumokkal kapcsolatos jogosultságok és az e-mailekkel kapcsolatos jogosultságok, a leírásukkal és az operációs rendszer által adott értékeikkel együtt.

**Megjegyzés** – A Linux SDK esetében a részletes információk a *rights.h* forrásfájlban találhatóak meg.

## Közös jogosultságok ##

**All (mind)** – Valamennyi közös jogosultságot tartalmazó gyűjtemény.
- Android: [CommonRights.All](/rights-management/sdk/4.2/api/android/commonrights#msipcthin2_commonrights_class_java_ALL)
- iOS és OS X: [MSCommonRights owner](/rights-management/sdk/4.2/api/iOS/mscommonrights#msipcthin2_mscommonrights_interface_objc___NSString__owner_)
- Windows Áruház és Windows Phone: [CommonRights.All</strong>](/rights-management/sdk/4.2/api/winrt/commonrights#msipcthin2_commonrights)
- Linux: [CommonRights::All](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1CommonRights.html)

** Owner (tulajdonos)** – A tulajdonosi jogosultságok teljes hozzáférést biztosítanak a védett tartalomhoz.
- Android: [<strong>CommonRights.Owner](/rights-management/sdk/4.2/api/android/commonrights#msipcthin2_commonrights_class_java_Owner)
- iOS és OS X: [MSCommonRights owner](/rights-management/sdk/4.2/api/iOS/mscommonrights#msipcthin2_mscommonrights_interface_objc___NSString__owner_)
- Windows Áruház és Windows Phone: [CommonRights.Owner](/rights-management/sdk/4.2/api/winrt/commonrights#msipcthin2_commonrights_owner)
- Linux: [CommonRights::Owner](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1CommonRights.html)

**View (megtekintés)** – A védett tartalmak megtekintésére vonatkozó jogosultság. A jogosultság megadását követően az alkalmazás lehetővé teszi a felhasználó számára a védett tartalom megnyitását és megtekintését; annak módosításához, kigyűjtéséhez, továbbításához és mentéséhez azonban további jogosultságokra van szükség.

- Android: [CommonRights.View](/rights-management/sdk/4.2/api/android/commonrights#msipcthin2_commonrights_class_java_View)
- iOS és OS X: [MSCommonRights view](/rights-management/sdk/4.2/api/iOS/mscommonrights#msipcthin2_mscommonrights_interface_objc___NSString__owner_)
- Windows Áruház és Windows Phone: [CommonRights.View](/rights-management/sdk/4.2/api/android/commonrights#msipcthin2_commonrights_class_java_View)
- Linux: [CommonRights::View](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1CommonRights.html)</li>

 

## Szerkeszthető dokumentumokkal kapcsolatos jogosultságok ##
**All (mind)** – A szerkeszthető dokumentumokkal kapcsolatos jogosultságok mindegyikét tartalmazó gyűjtemény.
- Android:[EditableDocumentRights.All](/rights-management/sdk/4.2/api/android/editabledocumentrights#msipcthin2_editabledocumentrights_class_java_ALL)
- iOS és OS X: [MSEditableDocumentRights all](/rights-management/sdk/4.2/api/iOS/mseditabledocumentrights#msipcthin2_mseditabledocumentrights_interface_objc)
- Windows Áruház és Windows Phone: [EditableDocumentRights.All](/rights-management/sdk/4.2/api/winrt/editabledocumentrights#msipcthin2_editabledocumentrights_all)
- Linux: [EditableDocumentRights::All](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EditableDocumentRights.html)

**Comment (megjegyzés)** – A dokumentum megjegyzésekkel való ellátásához kapcsolódó jogosultság.
- Android: [EditableDocumentRights.Comment](/rights-management/sdk/4.2/api/android/editabledocumentrights#msipcthin2_editabledocumentrights_class_java_Comment)
- iOS és OS X: [MSEditableDocumentRights comment](/rights-management/sdk/4.2/api/iOS/mseditabledocumentrights#msipcthin2_mseditabledocumentrights_interface_objc)
- Windows Áruház és Windows Phone: [EditableDocumentRights.Comment](/rights-management/sdk/4.2/api/winrt/editabledocumentrights#msipcthin2_editabledocumentrights__comment)
- Linux: [EditableDocumentRights::Comment](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EditableDocumentRights.html)

**Edit (szerkesztés)** – A védett tartalom szerkesztésére és annak ugyanazon védett formátumban történő mentésére vonatkozó jogosultság. A jogosultság megadását követően az alkalmazás lehetővé teszi a felhasználó számára a védett tartalom módosítását, majd annak ugyanazon fájlba történő mentését.
- Android: [EditableDocumentRights.Edit](/rights-management/sdk/4.2/api/android/editabledocumentrights#msipcthin2_editabledocumentrights_class_java_Edit)
- iOS és OS X: [MSEditableDocumentRights edit](/rights-management/sdk/4.2/api/iOS/mseditabledocumentrights#msipcthin2_mseditabledocumentrights_interface_objc)
- Windows Áruház és Windows Phone: [EditableDocumentRights.Edit](/rights-management/sdk/4.2/api/winrt/editabledocumentrights#msipcthin2_editabledocumentrights_edit)
- Linux: [EditableDocumentRights::Edit](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EditableDocumentRights.html)

**Export (exportálás)** – A tartalmak védett formátumból való kigyűjtésére, majd azok eltérő AD RMS-védelemmel ellátott formátumban történő elhelyezésére vonatkozó jogosultság. A jogosultság megadását követően az alkalmazás lehetővé teszi a felhasználó számára a védett tartalom eltérő AD RMS-védelemmel ellátott formátumban történő mentését; például ha az alkalmazás megvalósítja a *Mentés másként* funkciót.

- Android: [EditableDocumentRights.Export](/rights-management/sdk/4.2/api/android/editabledocumentrights#msipcthin2_editabledocumentrights_class_java_Export)
- iOS és OS X: [MSEditableDocumentRights exportable](/rights-management/sdk/4.2/api/iOS/mseditabledocumentrights#msipcthin2_mseditabledocumentrights_interface_objc)
- Windows Áruház és Windows Phone: [EditableDocumentRights.Export](/rights-management/sdk/4.2/api/winrt/editabledocumentrights#msipcthin2_editabledocumentrights_export)
- Linux: [EditableDocumentRights::Export](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EditableDocumentRights.html)

**Extract (kigyűjtés)** – A tartalmak védett formátumból való kigyűjtésére, majd azok nem védett formátumban történő elhelyezésére vonatkozó jogosultság. A jogosultság megadását követően az alkalmazás lehetővé teszi a felhasználó számára a védett tartalomból származó információk másolását és beillesztését. Ha az alkalmazás megvalósítja a <em>Mentés másként</em> funkciót, az alkalmazás lehetővé teheti a felhasználó számára a védett tartalom nem védett formátumban vagy eltérő, védett formátumban történő mentését is. E jogosultság értéke megegyezik a Kigyűjtés e-mailes jogosultság értékével.

- Android: [EditableDocumentRights.Extract](/rights-management/sdk/4.2/api/android/editabledocumentrights#msipcthin2_editabledocumentrights_class_java_Extract)
- iOS és OS X: [MSEditableDocumentRights extract](/rights-management/sdk/4.2/api/iOS/mseditabledocumentrights#msipcthin2_mseditabledocumentrights_interface_objc)
- Windows Áruház és Windows Phone: [EditableDocumentRights.Extract](/rights-management/sdk/4.2/api/winrt/editabledocumentrights#msipcthin2_editabledocumentrights_extract)
- Linux: [EditableDocumentRights::Extract](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EditableDocumentRights.html)

**Print (nyomtatás)** – A védett tartalmak kinyomtatására vonatkozó jogosultság. A jogosultság megadását követően az alkalmazás lehetővé teszi a felhasználó számára a védett tartalom nyomtatását. E jogosultság értéke megegyezik a Nyomtatás e-mailes jogosultság értékével.

- Android: [EditableDocumentRights.Print](/rights-management/sdk/4.2/api/android/editabledocumentrights#msipcthin2_editabledocumentrights_class_java_Print)
- iOS és OS X: [MSEditableDocumentRights print](/rights-management/sdk/4.2/api/iOS/mseditabledocumentrights#msipcthin2_mseditabledocumentrights_interface_objc)
- Windows Áruház és Windows Phone: [EditableDocumentRights.Print](/rights-management/sdk/4.2/api/winrt/editabledocumentrights#msipcthin2_editabledocumentrights_print)
- Linux: [EditableDocumentRights::Print](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EditableDocumentRights.html)

 

## E-mailekkel kapcsolatos jogosultságok ##

**All (mind)** – Az e-mailekkel kapcsolatos jogosultságok mindegyikét tartalmazó gyűjtemény.
- Android: [EmailRights.All](/rights-management/sdk/4.2/api/android/emailrights#msipcthin2_emailrights_class_java_ALL)
- iOS és OS X: [MSEmailRights all](/rights-management/sdk/4.2/api/iOS/msemailrights#msipcthin2_msemailrights_interface_objc)
- Windows Áruház és Windows Phone: [EmailRights.All](/rights-management/sdk/4.2/api/winrt/emailrights#msipcthin2_emailrights_all)
- Linux: [EmailRights::All](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EmailRights.html)

**Extract (kigyűjtés)** – A tartalmak védett formátumból való kigyűjtésére, majd azok nem védett formátumban történő elhelyezésére vonatkozó jogosultság. A jogosultság megadását követően az alkalmazás lehetővé teszi az e-mail címzettje számára a védett üzenetből származó információk másolását és beillesztését. Ha az alkalmazás megvalósítja a <em>Mentés másként</em> funkciót, az alkalmazás lehetővé teheti a címzett számára a védett tartalom nem védett formátumban vagy eltérő, védett formátumban történő mentését is. E jogosultság értéke megegyezik a Kigyűjtés szerkeszthető dokumentumokhoz kapcsolódó jogosultság értékével.

- Android: [EmailRights.Extract](/rights-management/sdk/4.2/api/android/emailrights#msipcthin2_emailrights_class_java_Extract)
- iOS és OS X: [MSEmailRights extract](/rights-management/sdk/4.2/api/iOS/msemailrights#msipcthin2_msemailrights_interface_objc)
- Windows Áruház és Windows Phone: [EmailRights.Extract</strong>](/rights-management/sdk/4.2/api/winrt/emailrights#msipcthin2_emailrights_extract)
- Linux: [EmailRights::Extract](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EmailRights.html)

**Forward (továbbítás)** – Védett üzenetek továbbítására vonatkozó jogosultság. A jogosultság megadását követően az alkalmazás lehetővé teszi az e-mail címzettje számára egy védett üzenet továbbítását.
- Android: [<strong>EmailRights.Forward</strong>](/rights-management/sdk/4.2/api/android/emailrights#msipcthin2_emailrights_class_java_Forward)
- iOS és OS X: [MSEmailRights forward](/rights-management/sdk/4.2/api/iOS/msemailrights#msipcthin2_msemailrights_interface_objc)
- Windows Áruház és Windows Phone: [EmailRights.Forward](/rights-management/sdk/4.2/api/winrt/emailrights#msipcthin2_emailrights_forward)
- Linux: [EmailRights::Forward](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EmailRights.html)

**Print (nyomtatás)** – A védett tartalmak kinyomtatására vonatkozó jogosultság. A jogosultság megadását követően az alkalmazás lehetővé teszi az e-mail címzettje számára egy védett üzenet nyomtatását. E jogosultság értéke megegyezik a Nyomtatás szerkeszthető dokumentumokhoz kapcsolódó jogosultság értékével.

- Android: [EmailRights.Print](/rights-management/sdk/4.2/api/android/emailrights#msipcthin2_emailrights_class_java_Print)
- iOS és OS X: [MSEmailRights print](/rights-management/sdk/4.2/api/iOS/msemailrights#msipcthin2_msemailrights_interface_objc)
- Windows Áruház és Windows Phone: [EmailRights.Print](/rights-management/sdk/4.2/api/winrt/emailrights#msipcthin2_emailrights_print)
- Linux: [EmailRights::Print](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EmailRights.html)

**Reply (válasz)** – A jogosultság megadását követően az alkalmazás lehetővé teszi az e-mail címzettje számára egy védett üzenet megválaszolását, és abban az eredeti üzenet másolatának elhelyezését.

- Android: [EmailRights.Reply](/rights-management/sdk/4.2/api/android/emailrights#msipcthin2_emailrights_class_java_Reply)
- iOS és OS X: [MSEmailRights reply](/rights-management/sdk/4.2/api/iOS/msemailrights#msipcthin2_msemailrights_interface_objc)
- Windows Áruház és Windows Phone: [EmailRights.Reply](/rights-management/sdk/4.2/api/winrt/emailrights#msipcthin2_emailrights_reply)
- Linux: [EmailRights::Reply](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EmailRights.html)

**ReplyAll (válasz mindenkinek)** – A jogosultság megadását követően az alkalmazás lehetővé teszi az e-mail címzettje számára egy védett üzenet megválaszolását annak összes címzettje számára, és abban az eredeti üzenet másolatának elhelyezését.

- Android: [EmailRights.ReplyAll</strong>](/rights-management/sdk/4.2/api/android/emailrights#msipcthin2_emailrights_class_java_ReplyAll)
- iOS és OS X: [MSEmailRights replyAll](/rights-management/sdk/4.2/api/iOS/msemailrights#msipcthin2_msemailrights_interface_objc)
- Windows Áruház és Windows Phone: [EmailRights.ReplyAll](/rights-management/sdk/4.2/api/winrt/emailrights#msipcthin2_emailrights_replyall)
- Linux: [EmailRights::ReplyAll](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1EmailRights.html)

 

 

 



<!--HONumber=Aug16_HO4-->


