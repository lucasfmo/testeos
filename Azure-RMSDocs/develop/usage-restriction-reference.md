---
title: "Használattal kapcsolatos korlátozások – referencia | Azure RMS"
description: "A használattal kapcsolatos korlátozásokat az ebben a témakörben felsorolt állandók határozzák meg."
keywords: 
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 16E36039-0FD6-4A0A-82C8-2C9DB19D27DD
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 2acf8095764e2c222881240985df8bccf8a64173
ms.openlocfilehash: 9788b067f9395b9e078e76994a2a8a79e95baf06


---

# Használattal kapcsolatos korlátozások – referencia

A használattal kapcsolatos korlátozásokat az ebben a témakörben felsorolt állandók határozzák meg.

Minden, az AD RMS-jogosultság oszlopban felsorolt felhasználói jogosultsághoz tartozik egy leírás, egy kényszerítési pont és javasolt kikényszerítési módszerek.

| AD RMS jogosultság/leírás | A kényszerítés módja |
|--------------------------|----------------|
|**IPC_GENERIC_ALL** <br><br> Megadja az összes jogosultságot a felhasználó számára. <br><br> **Gyakori kényszerítési pontok**: Nincsenek |Ezt a jogosultságot a rendszer használja, és általában nincs szükség a közvetlen ellenőrzésére. <br><br> Az [**IpcAccessCheck**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcaccesscheck) ezen jogosultság segítségével határozza meg, hogy a felhasználó kapjon-e más jogosultságokat, ahogyan az ebben a példában is látszik.<br><br> `/* fAccessGranted is set to TRUE if either the IPC_GENERIC_WRITE or the IPC_GENERIC_ALL right is granted */` <br><br> `IpcAccessCheck(hKey, IPC_GENERIC_WRITE, &fAccessGranted);`|
|**IPC_GENERIC_READ** <br><br> A dokumentumok tartalmának olvasására vonatkozó jogosultság. <br><br> **Gyakori kényszerítési pontok**: Dokumentum betöltése|Ne töltődjön be vagy jelenjen meg a dokumentum tartalma|
|**IPC_GENERIC_WRITE** <br><br> A dokumentumok tartalmának szerkesztésére vonatkozó jogosultság <br><br> **Gyakori kényszerítési pontok**: Dokumentum módosítása|A dokumentum tartalmának módosítására használható felhasználói felületi vezérlők ne legyenek szerkeszthetőek. <br><br> Tiltsa le a dokumentummódosításokat aktiváló menüelemeket. Gyakori példák: **Szerkesztés** > **Kivágás**, **Szerkesztés** > **Beillesztés** és **Beszúrás**. <br><br>Tiltsa le a dokumentummódosításokat aktiváló helyimenü-elemeket.|
|Nincs AD RMS-jogosultság <br><br> Nincs leírás <br><br> **Gyakori kényszerítési pontok**: Mentés | Tiltsa le a **Fájl** > **Mentés** menüt. <br><br> **Megjegyzés** Ez a jogosultság nem szabályozza a **Fájl** > **Mentés másként** műveletet, mert az nem jelent változást az eredeti dokumentumra nézve.<br><br> Tiltsa le a mentés indításához használható billentyűparancsokat (például Ctrl+S).<br><br> **Tipp** Ajánlott eljárás frissíteni az alapvető **Fájl** > **Mentés** kódot, hogy meghiúsuljon, ha a felhasználó nem rendelkezik ezzel a jogosultsággal. Ez biztonsági hálóként funkcionál, ha kihagyná valamelyik, a mentést aktiváló UX-mechanizmust. |
|**IPC_GENERIC_EXTRACT** <br><br> A tartalmak védett formátumból való kigyűjtésére, majd azok nem védett formátumban történő elhelyezésére vonatkozó jogosultság. <br><br> **Gyakori kényszerítési pontok**: Másolás a vágólapra | Tiltsa le a **Szerkesztés** > **Másolás** menüt. Tiltsa le a **Szerkesztés** > **Kivágás** menüt. <br><br>Tiltsa le minden helyi menüben a **Másolás** és a **Kivágás** parancsot.<br><br>Tiltsa le a másolás indításához használható billentyűparancsokat (például Ctrl+C vagy Ctrl+X).<br><br>Frissítse a [**WM_CUT**](https://msdn.microsoft.com/library/windows/desktop/ms649023) üzenetkezelőjét, hogy visszautasítsa az adatok másolását, ha a felhasználó nem rendelkezik ezzel a jogosultsággal. Ha az ablak az alapértelmezett, Windows által biztosított üzenetkezelőt használja, helyezze alosztályba ezt az ablakot, és adja meg a saját kezelőit a következőkhöz: **WM_COPY** és **WM_CUT**. |
|Nincs AD RMS-jogosultság <br><br> Nincs leírás <br><br> **Gyakori kényszerítési pontok**: Mentés másként |A **Mentés másként** párbeszédablakban tiltsa le azokat a fájlformátumokat, amelyek azt eredményeznék, hogy a dokumentumot a rendszer RMS-védelem nélkül mentse.|
|Nincs AD RMS-jogosultság <br><br> Nincs leírás <br><br> **Gyakori kényszerítési pontok**: Alt+PrtScn|Hívja meg az [**IpcProtectWindow**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcprotectwindow) parancsot bármelyik, dokumentumtartalmakat megjelenítő ablakban.|
|**IPC_GENERIC_EXPORT** <br><br> A tartalmak védett formátumból való kigyűjtésére, majd azok eltérő AD RMS-védelemmel ellátott formátumban történő elhelyezésére vonatkozó jogosultság. <br><br> **Gyakori kényszerítési pontok**: Mentés másként|A **Mentés másként** párbeszédablakban tiltsa le a más fájlformátumban való mentés képességét.<br><br>**Tipp** Ajánlott eljárás frissíteni az alapvető **Fájl** > **Mentés másként** kódot, hogy meghiúsuljon, ha a felhasználó megkísérli más formátumba menteni ezt a fájlt, és nem rendelkezik ezzel a jogosultsággal. Ez biztonsági hálóként funkcionál, ha kihagyná valamelyik, a mentés másként funkciót aktiváló UX-mechanizmust.|
|**IPC_GENERIC_PRINT** <br><br> A dokumentumok tartalmának nyomtatására vonatkozó jogosultság. <br><br> **Gyakori kényszerítési pontok**: Nyomtatás|Tiltsa le a **Fájl** > **Nyomtatás** menüt.<br><br>Tiltsa le a nyomtatás indításához használható billentyűparancsokat (például Ctrl+P).<br><br>Tiltsa le a nyomtatás indításához használható helyimenü-elemeket.<br><br>**Tipp** Ajánlott eljárás frissíteni az alapvető **Fájl** > **Nyomtatás** kódot, hogy meghiúsuljon, ha a felhasználó nem rendelkezik ezzel a jogosultsággal. Ez biztonsági hálóként funkcionál, ha kihagyná valamelyik, a nyomtatást aktiváló UX-mechanizmust.|
|**IPC_GENERIC_COMMENT** <br><br> Néhány alkalmazás a fő dokumentumtartalom frissítése nélkül is támogatja a megjegyzések és feliratok a dokumentumhoz adását.<br><br>Ez a jogosultság biztosítja a felhasználó számára a képesség elérését. <br><br> **Gyakori kényszerítési pontok**: <br><br> Véleményezés > Megjegyzés beszúrása <br><br> Véleményezés > Megjegyzés törlése | Tiltsa le a dokumentumokhoz fűzött megjegyzések vagy feliratok módosításához használható menüelemeket. Példák: **Véleményezés** > **Megjegyzés beszúrása** és **Véleményezés** > **Megjegyzés törlése**. <br><br>Tiltsa le az összes billentyűparancsot, amellyel a dokumentum megjegyzéseinek módosítása aktiválható.<br><br>**Megjegyzés** Az alapértelmezett megvalósításhoz szükséges az **IPC_GENERIC_COMMENT** és az **IPC_GENERIC_WRITE** is, hogy tartósan új megjegyzéseket lehessen írni egy fájlba. Az alkalmazások támogathatják azt az esetet, ahol az **IPC_GENERIC_COMMENT** jogosultság meg van adva, az **IPC_GENERIC_WRITE** jogosultság azonban nincs. Ebben az esetben engedélyezve van a Mentés lehetővé tétele, ha a dokumentummódosítások csak a megjegyzésekre korlátozódnak.|
|**IPC_VIEW_RIGHTS** <br><br> Nincs leírás <br><br> **Gyakori kényszerítési pontok**: nem áll rendelkezésre|A rendszer kényszeríti ki. A rendszer nem engedi, hogy a fejlesztő lekérdezze a [**felhasználói jogosultságok listáját**](/rights-management/sdk/2.1/api/win/structures#msipc_ipc_user_rights_list) egy licencről, ha nem rendelkezik ezzel a jogosultsággal.
|**IPC_EDIT_RIGHTS** <br><br> Bizonyos alkalmazások lehetővé teszik a felhasználók számára a felhasználók és a jogosultságok módosítását az AD RMS-védelemmel ellátott tartalomra vonatkozóan.<br><br>Ez a jogosultság biztosítja a felhasználó számára a képesség elérését. <br><br> **Gyakori kényszerítési pontok**: Alkalmazásjogosultságok szerkesztési felhasználói felületének vezérlői|Tiltsa le minden olyan felhasználói felülethez a felhasználói hozzáférést, amellyel szerkeszthető egy dokumentum RMS-házirendje.|

 

 

 



<!--HONumber=Jul16_HO3-->


