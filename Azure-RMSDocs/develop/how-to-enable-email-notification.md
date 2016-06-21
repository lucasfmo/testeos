---
# required metadata

title: E-mail-értesítések engedélyezése | Azure RMS
description: Az e-mail-értesítések lehetővé teszik, hogy a védett tartalom tulajdonosa értesítést kapjon, ha hozzáfértek tartalmához.
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 5FB975EE-E4E5-4089-B8E1-CAFD5B9B34EC
# optional metadata

#ROBOTS:
audience: developer
#ms.devlang:
ms.reviewer: shubhamp
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Útmutató: Az e-mailes értesítés engedélyezése

Az e-mail-értesítések lehetővé teszik, hogy a védett tartalom tulajdonosa értesítést kapjon, ha hozzáfértek tartalmához.

Az adott licenchez tartozó e-mail-értesítések beállításához használja az [**IpcSetLicenseProperty**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcsetlicenseproperty) parancsmagot úgy, hogy a *dwPropID* tulajdonságtípus-paraméter formátuma [**IPC\_LI\_APP\_SPECIFIC\_DATA**](/rights-management/sdk/2.1/api/win/License%20property%20types#msipc_license_property_types_IPC_LI_APP_SPECIFIC_DATA), az alkalmazás adatmezőinek formátuma pedig [**IPC\_NAME\_VALUE\_LIST**](/rights-management/sdk/2.1/api/win/structures#msipc_ipc_name_value_list) legyen.

    C++

    int numDataPairs = 3;

    IPC_NAME_VALUE propertyValuePairs [numDataPairs];

    // lcid field set to 0 causes the default lcid to be used

    propertyValuePairs[0] = {&quot;MS.Conetent.Name&quot;, 0, &quot;FinancialReport.docx&quot;};
    propertyValuePairs[1] = {&quot;MS.Notify.Enabled&quot;,0 , &quot;true&quot;};
    propertyValuePairs[2] = {&quot;MS.Notify.Culture&quot;,0 , “en-US”};

    IPC_NAME_VALUE_LIST emailNotificationAppData = {numDataPairs, propertyValuePairs};

    result = IpcSetLicenseProperty( licenseHandle, FALSE, IPC_LI_APP_SPECIFIC_DATA, emailNotificationAppData);
        

Az RMS e-mail-értesítéshez tartozó alkalmazásadat-mezőket, tulajdonságnév- és értékpárokat az alábbi táblázat tartalmazza.


|Tulajdonság neve | Adattípus | Példaérték | Megjegyzések |
|--------------|-----------|---------------|-------|
|MS.Content.Name|karakterlánc|„FinancialReport.docx”|Ez a védett tartalomhoz társított azonosító.<br><br> A védett fájlok esetében ennek az értéknek a fájl nevének kell lennie, útvonaladatok nélkül.<br><br> Egyéb típusú tartalmak (például e-mail-üzenetek) esetében ez lehet az e-mail tárgya, vagy üresen is maradhat.|
|MS.Notify.Enabled|karakterlánc|„igaz” és „hamis”|Ha az érték „igaz”, a közzétételi licenc tulajdonosa minden alkalommal e-mail-értesítést kap, ha valaki egy végfelhasználói licenc beszerzéséhez megkísérli használni azt.|
|MS.Notify.Culture|karakterlánc|„hu-HU”| **Forrás:** System.Globalization.CultureInfo.CurrentUICulture.Name <br><br>Ez az érték az értesítő e-mail honosított nyelvét, valamint az e-mail-üzenetben használatos dátum-/időbeállítást és számformázást határozza meg.<br><br>Az értéket annak a gépnek a felhasználói beállításai alapján kell megadni, amelyen a közzétételi licencet létrehozták, vagy a közzétételi licenc tulajdonosának előnyben részesített kulturális környezete alapján.|
|MS.Notify.TZID|karakterlánc|„Csendes-óceáni téli idő”|**Forrás:** TimeZoneInfo.Local.Id – Windows-időzóna azonosítója.<br><br>Ez az érték a Microsoft Windows operációs rendszer időzóna-azonosítója, amely az adott időzóna és annak jellemzői leírására használatos.|
|MS.Notify.TZO|karakterlánc|“-480”|Ez a közzétételi licenc tulajdonosának időzóna-eltolódása az UTC szerinti időhöz képest, percben kifejezve.<br><br>Érvényes TZID-érték megadásakor a rendszer az általa megadott időzóna-eltolódást használja, ez az érték pedig figyelmen kívül lesz hagyva.<br><br>Több mint valószínű, hogy azok a nem Windows-alapú közzétételi platformok, amelyek nem rendelkeznek hozzáféréssel a Windows operációs rendszer időzóna-azonosítóinak értékeit tartalmazó listához, ezt az értéket használják.<br><br>Ha nem áll rendelkezésre TZID-érték, a rendszer ezt az értéket használja az értesítési üzenetekben alkalmazott időeltolódás kiszámításához, a TZSN-értéket pedig az időzóna nevének megjelenítéséhez használja (az időzóna értékétől függetlenül). Ezzel az időzóna értéke rögzített lesz, és azokban az esetekben, ahol alkalmazható, a nyári időszámítás szerint nem frissül.<br><br>Példa:<br><br>Ha a TXID értéke nincs megadva, a TZ0 értéke „-420”, a TZSN értéke pedig „Csendes-óceáni nyári idő”, az értesítési e-mailben megjelenített összes érték a „Csendes-óceáni nyári idő” szerint lesz beállítva és megjelenítve, még abban az esetben is, ha a nyári időszámítás aktuálisan már nincs használatban.<br><br>Ha azonban a TZSN és a TZDN mellett a TZID értéke is meg van adva, az értesítési e-mailben megadott időpontok annak megfelelően lesznek beállítva és megjelenítve, hogy a dátumnak és az időnek Nyári időszámítás szerinti vagy Téli időszámítás szerinti üzemmódban kell-e megjelennie.|
|MS.Notify.TZSN|karakterlánc|„Csendes-óceáni téli idő”|**Forrás:** TimeZoneInfo.Local.StandardName – Téli időzóna neve.<br><br>Ez az érték az adott időzóna szabványos időzónanevének honosított neve.|
|MS.Notify.TZDN|karakterlánc|„Csendes-óceáni nyári idő”|**Forrás:** TimeZoneInfo.Local.DaylightName – Nyári időzóna neve.<br><br>Ez az érték az adott időzóna nyári időszámítás szerinti nevének honosított neve. Ha az adott időzóna nem támogatja a nyári időszámítást, ez megegyezhet a normál névvel.|

## Kapcsolódó témakörök

* [**IpcSetLicenseProperty**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcsetlicenseproperty)
* [**IPC\_LI\_APP\_SPECIFIC\_DATA**](/rights-management/sdk/2.1/api/win/License%20property%20types#msipc_license_property_types_IPC_LI_APP_SPECIFIC_DATA)
* [**IPC\_NAME\_VALUE\_LIST**](/rights-management/sdk/2.1/api/win/structures#msipc_ipc_name_value_list)
 

 


<!--HONumber=Jun16_HO2-->


