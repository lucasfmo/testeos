---
title: "Használati jogosultságok konfigurálása az Azure Rights Managementhez | Azure RMS"
description: "Ismerje meg és határozza meg azokat a különleges jogokat, amikkel az Azure Rights Management (Azure RMS) használatakor védjük dokumentumait és e-mailjeit."
author: cabailey
manager: mbaldwin
ms.date: 08/25/2016
ms.topic: article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 97ddde38-b91b-42a5-8eb4-3ce6ce15393d
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ad32910b482ca9d92b4ac8f3f123eda195db29cd
ms.openlocfilehash: ab1b2f652d34183e1d95fd0a387abb10c3aff9b1


---

# Használati jogosultságok konfigurálása az Azure Rights Managementhez

>*A következőkre vonatkozik: Azure Rights Management, Office 365*

Amikor az Azure Rights Management (Azure RMS) segítségével lát el védelemmel fájlokat vagy e-maileket, és nem használ sablont, saját magának kell konfigurálnia a használati jogosultságokat. Továbbá, amikor egyéni sablonokat konfigurál az Azure RMS számára, ki kell választania a használati jogosultságokat, amelyeket a rendszer automatikusan alkalmazni fog, amikor a felhasználók, a rendszergazdák vagy a konfigurált szolgáltatások kiválasztják a sablont. A klasszikus Azure-portálon kiválaszthat például olyan szerepköröket, amelyek a használati jogosultságok logikus csoportját konfigurálják, illetve konfigurálhatja külön az egyes jogosultságokat.

Ez a cikk segítséget nyújt a használt alkalmazáshoz kapcsolódó kívánt használati jogosultságok konfigurálására, és segít megérteni, hogy az alkalmazások hogyan értelmezik ezeket a jogosultságokat.

## Használati jogosultságok és leírások
Az alábbi táblázat felsorolja és ismerteti a Rights Management által támogatott használati jogosultságokat, valamint ezek használatát és jelentését. **Köznapi név** alapján vannak listázva, ez azt a nevet jelenti, ahogy a használati jogosultság vagy az arra való hivatkozás általában megjelenik, a kódban használt egyszavas értéknek (a **Kódolás a házirendben** értéke) a felhasználók számára könnyebben értelmezhető verziójaként. Az **API-állandó vagy -érték** az MSIPC API-hívások SDK-neve, amely a használati jogosultságokat ellenőrző vagy a használati jogosultságot egy házirendhez hozzáadó RMS-kompatibilis alkalmazás írásakor használatos.


|Jobb oldali|Leírás|Megvalósítás|
|-------------------------------|---------------------------|-----------------|
|Köznapi név: **Tartalom szerkesztése, Szerkesztés** <br /><br />Kódolás a házirendben: **DOCEDIT**|Lehetővé teszi a felhasználó számára az alkalmazáson belüli tartalom módosítását, átrendezését, formázását vagy szűrését. A módosított tartalom mentéséhez szükséges jogosultságot nem biztosítja.|Egyéni Office-jogosultságok: a **Módosítás** és a **Teljes hozzáférés** beállítások részeként. <br /><br />Neve a klasszikus Azure portálon: **Tartalom szerkesztése**<br /><br />Neve az AD RMS-sablonokban: **Szerkesztés** <br /><br />API-állandó vagy érték: Nem alkalmazható.|
|Köznapi név: **Mentés** <br /><br />Kódolás a házirendben:** EDIT**|Lehetővé teszi a felhasználó számára a dokumentum mentését az aktuális helyén.<br /><br />Az Office-alkalmazásokban ez a jogosultság a dokumentum módosítását is lehetővé teszi.|Egyéni Office-jogosultságok: a **Módosítás** és a **Teljes hozzáférés** beállítások részeként. <br /><br />Neve a klasszikus Azure portálon: **Fájl mentése**<br /><br />Neve az AD RMS-sablonokban: **Mentés** <br /><br />API-állandó vagy -érték: `IPC_GENERIC_WRITE L"EDIT"`|
|Köznapi név: **Megjegyzés** <br /><br />Kódolás a házirendben: **COMMENT**|Engedélyezi jegyzetek és megjegyzések hozzáadását a tartalomhoz.<br /><br />Ez a jogosultság elérhető az SDK-ban, valamint alkalmi házirendként Windows PowerShell RMS Protection moduljában, és egyes szoftverszállítói alkalmazásokban is implementálva lett. Ennek ellenére a használata nem elterjedt, és az Office-alkalmazások jelenleg nem támogatják.|Egyéni Office-jogosultságok: Nincs implementálva. <br /><br />Neve a klasszikus Azure portálon: Nincs implementálva.<br /><br />Neve az AD RMS-sablonokban: Nincs implementálva. <br /><br />API-állandó vagy -érték: `IPC_GENERIC_COMMENT L"COMMENT`|
|Köznapi név: **Mentés másként, Exportálás** <br /><br />Kódolás a házirendben: **EXPORT**|Lehetővé teszi a tartalom mentését másik fájlnévvel (Save As (Mentés másként)). Office-dokumentumok esetében a fájl védelem nélkül is menthető.<br /><br />Ez a jogosultság lehetővé teszi a felhasználónak az alkalmazásokon belüli egyéb exportálási lehetőségek használatát (például **Küldés a OneNote-ba**).|Egyéni Office-jogosultságok: a **Módosítás** és a **Teljes hozzáférés** beállítások részeként. <br /><br />Neve a klasszikus Azure portálon: **Tartalom exportálása (Mentés másként)**<br /><br />Neve az AD RMS-sablonokban: **Exportálás (Mentés másként)** <br /><br />API-állandó vagy -érték: `IPC_GENERIC_EXPORT L"EXPORT"`|
|Köznapi név: **Továbbítás** <br /><br />Kódolás a házirendben: **FORWARD**|Lehetővé teszi az e-mail üzenetek továbbítását és a címzettek hozzáadását a **Címzett** és a **Másolatot kap** sorban. Ez a jogosultság nem érvényes a dokumentumokra, kizárólag az e-mailekre.<br /><br />Nem engedélyezi a továbbító számára, hogy jogosultságokat adjon más felhasználóknak a továbbítási művelet részeként.|Egyéni Office-jogosultságok: A rendszer megtagadja a **Nem továbbítandó** normál házirend használata esetén.<br /><br />Neve a klasszikus Azure portálon: **Továbbítás**<br /><br />Neve az AD RMS-sablonokban: **Továbbítás** <br /><br />API-állandó vagy -érték: `IPC_EMAIL_FORWARD L"FORWARD"`|
|Köznapi név: **Teljes hozzáférés** <br /><br />Kódolás a házirendben: **OWNER**|Megadja az összes jogosultságot a dokumentumhoz, így minden elérhető művelet elvégezhető.<br /><br />Lehetővé teszi a védelem eltávolítását és a dokumentum védelmének újbóli beállítását.|Egyéni Office-jogosultságok: A **Teljes hozzáférés** egyéni beállításként.<br /><br />Neve a klasszikus Azure portálon: **Teljes hozzáférés**<br /><br />Neve az AD RMS-sablonokban: **Teljes hozzáférés** <br /><br />API-állandó vagy -érték: `IPC_GENERIC_ALL L"OWNER"`|
|Köznapi név: **Nyomtatás** <br /><br />Kódolás a házirendben: **PRINT**|Lehetővé teszi a tartalom nyomtatását.|Egyéni Office-jogosultságok: A **Tartalom nyomtatása** beállításként az egyéni engedélyek között. Nem címzettenkénti beállítás.<br /><br />Neve a klasszikus Azure portálon: **Nyomtatás**<br /><br />Neve az AD RMS-sablonokban: **Nyomtatás** <br /><br />API-állandó vagy -érték: `IPC_GENERIC_PRINT L"PRINT"`|
|Köznapi név: **Válasz** <br /><br />Kódolás a házirendben: **REPLY**|Engedélyezi a **Válasz** lehetőséget az e-mail ügyfélprogramokban, de nem engedélyezi a **Címzett** és a **Másolatot** kap sor módosítását.|Egyéni Office-jogosultságok: Nincs alkalmazható.<br /><br />Neve a klasszikus Azure portálon: **Válasz**<br /><br />Neve az AD RMS-sablonokban: **Válasz** <br /><br />API-állandó vagy -érték: `IPC_EMAIL_REPLY`|
|Köznapi név: **Válasz mindenkinek** <br /><br />Kódolás a házirendben: **REPLYALL**|Engedélyezi a **Válasz mindenkinek** lehetőséget az e-mail ügyfélprogramokban, de nem engedélyezi a címzettek hozzáadását a **Címzett** és a **Másolatot kap** sorokban.|Egyéni Office-jogosultságok: Nincs alkalmazható.<br /><br />Neve a klasszikus Azure portálon: **Válasz mindenkinek**<br /><br />Neve az AD RMS-sablonokban: **Válasz mindenkinek** <br /><br />API-állandó vagy -érték: `IPC_EMAIL_REPLYALL L"REPLYALL"`|
|Köznapi név: **Megtekintés, Megnyitás, Olvasás** <br /><br />Kódolás a házirendben: **VIEW**|Lehetővé teszi a felhasználó számára a dokumentum megnyitását és a tartalom megtekintését.|Egyéni Office-jogosultságok: Az **Olvasás** egyéni házirend **Megtekintés** beállításaként.<br /><br />Neve a klasszikus Azure portálon: **Megtekintés**<br /><br />Neve az AD RMS-sablonokban: **Válasz mindenkinek** <br /><br />API-állandó vagy -érték: `IPC_GENERIC_READ L"VIEW"`|
|Köznapi név: **Másolás** <br /><br />Kódolás a házirendben: **EXTRACT**|Lehetővé teszi az adatok (ideértve a képernyőfelvételek) másolását a dokumentumból ugyanazon a dokumentumon belülre, vagy egy másik dokumentumba.<br /><br />Egyes alkalmazásokban a teljes dokumentum mentését is lehetővé teszi nem védett állapotban.|Egyéni Office-jogosultságok: Az **olvasási joggal rendelkező felhasználók másolhatják a tartalmat** egyéni házirend-beállításként.<br /><br />Neve a klasszikus Azure portálon: **Tartalom másolása és kinyerése**<br /><br />Neve az AD RMS-sablonokban: **Kinyerés** <br /><br />API-állandó vagy -érték: `IPC_GENERIC_EXTRACT L"EXTRACT"`|
|Köznapi név: **Makrók engedélyezése** <br /><br />Kódolás a házirendben: **OBJMODEL**|Engedélyezi a makrók futtatását, valamint az egyéb programozott vagy távelérési műveletek végzését a dokumentumok tartalmán.|Egyéni Office-jogosultságok: A **Programozott hozzáférés engedélyezése** egyéni házirend-beállításként. Nem címzettenkénti beállítás.<br /><br />Neve a klasszikus Azure portálon: **Makrók engedélyezése**<br /><br />Neve az AD RMS-sablonokban: **Makrók engedélyezése** <br /><br />API-állandó vagy érték: Nem implementált.|



## Jogosultságok az engedélyszintekben

Egyes alkalmazások a használati jogosultságokat engedélyszintekbe csoportosítják, hogy egyszerűbb legyen olyan használati jogosultságokat választani, amelyeket általában együtt használnak. Ezek az engedélyszintek kevésbé összetett, absztrakt módon teszik lehetővé a felhasználók számára, hogy szerepkör szerint választhassanak beállításokat.  Például: **Véleményező** és **Társszerző**. Bár ezek a beállítások általában megjelenítik a jogosultságok összegzését, előfordulhat, hogy nem tartalmaznak minden jogosultságot, amely az előző táblázatban szerepel.

A következő táblázatban láthatja az engedélyszinteket és az ezek által tartalmazott jogosultságok teljes listáját.

|Jogosultsági szint|Alkalmazások|Jogosultságok (köznapi név)|
|---------------------|----------------|---------------------------------|
|Megtekintő|Klasszikus Azure-portál<br /><br />A Windows Microsoft Rights Management megosztóalkalmazás|Megtekintés, Megnyitás, Olvasás; Válasz; Válasz mindenkinek|
|Felülvizsgáló|Klasszikus Azure-portál<br /><br />A Windows Microsoft Rights Management megosztóalkalmazás|Megtekintés, Megnyitás, Olvasás; Mentés; Tartalom szerkesztése, Szerkesztés; Válasz [[1]](#footnote-1); Válasz mindenkinek [[1]](#footnote-1); Továbbítás [[1]](#footnote-1)|
|Társszerző|Klasszikus Azure-portál<br /><br />A Windows Microsoft Rights Management megosztóalkalmazás|Megtekintés, Megnyitás, Olvasás; Mentés; Tartalom szerkesztése, Szerkesztés; Másolás; Jogosultságok megtekintése; Makrók engedélyezése; Mentés másként, Exportálás; Nyomtatás; Válasz [[1]](#footnote-1); Válasz mindenkinek [[1]](#footnote-1); Továbbítás [[1]](#footnote-1)|
|Társtulajdonos|Klasszikus Azure-portál<br /><br />A Windows Microsoft Rights Management megosztóalkalmazás|Megtekintés, Megnyitás, Olvasás; Mentés; Tartalom szerkesztése, Szerkesztés; Másolás; Jogosultságok megtekintése; Makrók engedélyezése; Mentés másként, Exportálás; Nyomtatás; Válasz [[1]](#footnote-1); Válasz mindenkinek [[1]](#footnote-1); Továbbítás [[1]](#footnote-1); Teljes hozzáférés|

----

###### 1. lábjegyzet
Nem alkalmazható a Windows Microsoft Rights Management megosztóalkalmazás esetén.

## Jogosultságok az alapértelmezett sablonokban
Az alapértelmezett sablonok részét képező jogosultságok a következők:

|Megjelenített név|Jogosultságok (köznapi név)|
|----------------|---------------------------------|
|&lt;*szervezet neve*&gt; *– Csak bizalmas megtekintésre*|Megtekintés, Megnyitás, Olvasás|
|&lt;*szervezet neve*&gt; *– Bizalmas*|Megtekintés, Megnyitás, Olvasás; Mentés; Tartalom szerkesztése, Szerkesztés; Jogosultságok megtekintése; Makrók engedélyezése; Továbbítás; Válasz; Válasz mindenkinek|

## A Nem továbbítható beállítás az e-maileknél

Az Exchange-ügyfeleknek és -szolgáltatásoknak (például az Outlook ügyfélnek, az Outlook Web Access alkalmazásnak és az Exchange átviteli szabályoknak) még egy tartalomvédelmi beállításuk van az e-mailekhez, ez a **Nem továbbítható**. 

Bár ez a beállítás úgy jelenik meg a felhasználók (és az Exchange-rendszergazdák) számára, mintha egy választható alapértelmezett tartalomvédelmi sablon volna, a **Nem továbbítható** valójában nem sablon. Ez indokolja, hogy nem látható a klasszikus Azure-portálon az Azure RMS sablonjainak megtekintésekor és kezelésekor. A **Nem továbbítás** igazából a jogok egy halmaza, amelyet dinamikusan alkalmaznak a felhasználók az e-mailjeik címzettjeire.

Ha a **Nem továbbítható** beállítást alkalmazzák egy e-mailre, akkor a címzettek nem továbbíthatják és nem nyomtathatják ki az e-mailt, nem másolhatnak belőle, nem menthetik a mellékleteit, és más néven sem menthetik. Az Outlook ügyfélben például nem érhető el a Továbbítás gomb, valamint a **Mentés másként**, a **Melléklet mentése** és a **Nyomtatás** menüpont, továbbá nem lehet címzetteket felvenni a **Címzett**, a **Másolatot kap** és a **Titkos másolatot** kap mezőbe, és nem is módosítható a címzettek köre.

Fontos különbség van a **Nem továbbítható** beállítás, illetve egy olyan sablon alkalmazása között, amely nem adja meg a Továbbítás jogot egy e-mailhez: A **Nem továbbítható** beállítás a felhasználó által az eredeti e-mailben kiválasztott címzettekből álló jogosult felhasználók dinamikus listáját használja, míg a sablonokban szereplő jogok a rendszergazda által korábban meghatározott jogosult felhasználók statikus listáján alapul. Mi a különbség? Vegyünk egy példát: 

Egy felhasználó e-mailben el szeretne küldeni bizonyos, másokra nem tartozó információkat a marketingosztály meghatározott dolgozóinak. Hogyan védje az e-mailt? A jogokat (a megtekintést, a megválaszolást és a mentést) a marketingosztályra korlátozó sablonnal?  Vagy a **Nem továbbítható** beállítást kell választania? Mindkét döntés azt eredményezné, hogy a címzettek nem tudnák továbbítani az e-mailt. 

- Ha a sablont alkalmazza, a címzettek a marketingosztály többi dolgozójával meg tudják osztani az információkat. Az egyik címzett megteheti például, hogy a Fájlkezelőben egy megosztott mappába vagy USB-meghajtóra húzza az e-mailt. Ekkortól az e-mail tulajdonosán kívül a marketingosztály minden olyan dolgozója, aki hozzáfér ehhez a helyhez, láthatja az e-mailben szereplő információkat.
 
- Ha a **Nem továbbítható** beállítást alkalmazza, a címzettek a marketingosztályon belül sem tudják mással megosztani az információkat azzal, hogy máshová helyezik az e-mailt. Ebben az esetben az e-mail tulajdonosán kívül csak az eredeti címzettek tudják megtekinteni az e-mailben szereplő információkat.

> [!NOTE] 
> A **Nem továbbítható** beállítást kell használni, ha fontos, hogy csak a feladó által kiválasztott címzettek láthassák az e-mailben foglaltakat. A sablonok használatával a személyeknek a rendszergazda által előre megadott csoportjára lehet korlátozni az e-mailre vonatkozó jogokat, függetlenül a feladó által kiválasztott címzettektől.




## Lásd még:
[Az Azure Rights Management egyéni sablonok konfigurálása](configure-custom-templates.md)




<!--HONumber=Aug16_HO4-->


