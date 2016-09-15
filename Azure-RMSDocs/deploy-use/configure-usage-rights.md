---
title: "Használati jogosultságok konfigurálása az Azure Rights Managementhez | Azure RMS"
description: 
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 06/16/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 97ddde38-b91b-42a5-8eb4-3ce6ce15393d
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 3883a46440f016138dd50d061a58089253721719
ms.openlocfilehash: 21b92fae5fd00d80f9afd2e80d21c08bfa47b7b2


---

# Használati jogosultságok konfigurálása az Azure Rights Managementhez

*A következőkre vonatkozik: Azure Rights Management, Office 365*

Amikor az Azure Rights Management (Azure RMS) segítségével lát el védelemmel fájlokat vagy e-maileket, és nem használ sablont, saját magának kell konfigurálnia a használati jogosultságokat. Továbbá, amikor egyéni sablonokat konfigurál az Azure RMS számára, ki kell választania a használati jogosultságokat, amelyeket a rendszer automatikusan alkalmazni fog, amikor a felhasználók, a rendszergazdák vagy a konfigurált szolgáltatások kiválasztják a sablont. A klasszikus Azure-portálon kiválaszthat például olyan szerepköröket, amelyek a használati jogosultságok logikus csoportját konfigurálják, illetve konfigurálhatja külön az egyes jogosultságokat.

Ez a cikk segítséget nyújt a használt alkalmazáshoz kapcsolódó kívánt használati jogosultságok konfigurálására, és segít megérteni, hogy az alkalmazások hogyan értelmezik ezeket a jogosultságokat.

## Használati jogosultságok és leírások
Az alábbi szakaszok felsorolják és leírják a Rights Management által támogatott használati jogosultságokat, valamint a használatuk és az értelmezésük módját. **Köznapi név** alapján vannak listázva, ez azt a nevet jelenti, ahogy a használati jogosultság vagy az arra való hivatkozás általában megjelenik, a kódban használt egyszavas értéknek (a **Kódolás a házirendben** értéke) a felhasználók számára könnyebben értelmezhető verziójaként. Az **API-állandó vagy -érték** az MSIPC API-hívások SDK-neve, amely a használati jogosultságokat ellenőrző vagy a használati jogosultságot egy házirendhez hozzáadó RMS-kompatibilis alkalmazás írásakor használatos.


### Tartalom szerkesztése, Szerkesztés

Lehetővé teszi a felhasználó számára az alkalmazáson belüli tartalom módosítását, átrendezését, formázását vagy szűrését. A módosított tartalom mentéséhez szükséges jogosultságot nem biztosítja.

**Kódolás a házirendben**: DOCEDIT

**Implementáció az Office egyéni jogosultságai között**: A *Módosítás* és a *Teljes hozzáférés* beállítások részeként.

**Neve a klasszikus Azure-portálon**: *Tartalom szerkesztése*

**Neve az Active Directory tartalomvédelmi szolgáltatásokban**: *Szerkesztés*

**API-állandó vagy érték**: *Nem alkalmazható*

---

### Mentés

Lehetővé teszi a felhasználó számára a dokumentum mentését az aktuális helyén.

**Kódolás a házirendben**: EDIT

**Implementáció az Office egyéni jogosultságai között**: A *Módosítás* és a *Teljes hozzáférés* beállítások részeként.

**Neve a klasszikus Azure-portálon**: *Fájl mentése*

**Neve az Active Directory tartalomvédelmi szolgáltatásokban**: *Mentés*

**API-állandó vagy érték**: IPC_GENERIC_WRITE L"EDIT"

Az Office-alkalmazásokban ez a jogosultság a dokumentum módosítását is lehetővé teszi.

---

### Megjegyzés

Engedélyezi jegyzetek és megjegyzések hozzáadását a tartalomhoz.

**Kódolás a házirendben**: COMMENT

**Implementáció az Office egyéni jogosultságai között**: Nincs implementálva.

**Neve a klasszikus Azure-portálon**: Nincs implementálva.

**Neve az Active Directory tartalomvédelmi szolgáltatásokban:** Nincs implementálva.

**API-állandó vagy érték**: IPC_GENERIC_COMMENT L"COMMENT

Ez a jogosultság elérhető az SDK-ban, valamint alkalmi házirendként Windows PowerShell RMS Protection moduljában, és egyes szoftverszállítói alkalmazásokban is implementálva lett. Ennek ellenére a használata nem elterjedt, és az Office-alkalmazások jelenleg nem támogatják.

---

### Mentés másként, Exportálás

Lehetővé teszi a tartalom mentését másik fájlnévvel (Save As (Mentés másként)). Office-dokumentumok esetében a fájl védelem nélkül is menthető.

**Kódolás a házirendben:** EXPORT

**Implementáció az Office egyéni jogosultságai között**: A *Módosítás* és a *Teljes hozzáférés* beállítások részeként.

**Neve a klasszikus Azure-portálon:** *Tartalom exportálása (Mentés másként)*

**Neve az Active Directory tartalomvédelmi szolgáltatásokban:** *Exportálás (Mentés másként)*

**API-állandó vagy érték:** IPC_GENERIC_EXPORT L"EXPORT"

Ez a jogosultság lehetővé teszi a felhasználónak az alkalmazásokon belüli egyéb exportálási lehetőségek használatát (például *Küldés a OneNote-ba*).

---

### Továbbítás

Lehetővé teszi az e-mail üzenetek továbbítását és a címzettek hozzáadását a *Címzett* és a *Másolatot kap* sorban. Ez a jogosultság nem érvényes a dokumentumokra, kizárólag az e-mailekre.

**Kódolás a házirendben:** FORWARD

**Implementáció az Office egyéni jogosultságai között:** A rendszer megtagadja a *Nem továbbítandó* normál házirend használata esetén.

**Neve a klasszikus Azure-portálon:** *Továbbítás*

**Neve az Active Directory tartalomvédelmi szolgáltatásokban:** *Továbbítás*

**API-állandó vagy érték:** IPC_EMAIL_FORWARD L"FORWARD"

Nem engedélyezi a továbbító számára, hogy jogosultságokat adjon más felhasználóknak a továbbítási művelet részeként.

---

### Teljes hozzáférés

Megadja az összes jogosultságot a dokumentumhoz, így minden elérhető művelet elvégezhető.

**Kódolás a házirendben:** OWNER

**Implementáció az Office egyéni jogosultságai között:** A *Teljes hozzáférés* egyéni beállításként.

**Neve a klasszikus Azure-portálon:** *Teljes hozzáférés*

**Neve az Active Directory tartalomvédelmi szolgáltatásokban:** *Teljes hozzáférés*

**API-állandó vagy érték:** IPC_GENERIC_ALL L"OWNER"

Lehetővé teszi a védelem eltávolítását.

---

### Nyomtatás

Lehetővé teszi a tartalom nyomtatását.

**Kódolás a házirendben:** PRINT

**Implementáció az Office egyéni jogosultságai között:** A *Tartalom nyomtatása* beállításként az egyéni engedélyek között. Nem címzettenkénti beállítás.

**Neve a klasszikus Azure-portálon:** *Nyomtatás*

**Neve az Active Directory tartalomvédelmi szolgáltatásokban:** *Nyomtatás*

**API-állandó vagy érték:** IPC_GENERIC_PRINT L"PRINT

---

### Válasz

Engedélyezi a Válasz lehetőséget az e-mail ügyfélprogramokban, de nem engedélyezi a *Címzett* és a *Másolatot kap* sor módosítását.

**Kódolás a házirendben:** REPLY

**Implementáció az Office egyéni jogosultságai között**: Nem alkalmazható

**Neve a klasszikus Azure-portálon:** *Válasz*

**Neve az Active Directory tartalomvédelmi szolgáltatásokban**: *Válasz*

**API-állandó vagy érték:** IPC_EMAIL_REPLY

---

### Válasz mindenkinek

Engedélyezi a *Válasz mindenkinek* lehetőséget az e-mail ügyfélprogramokban, de nem engedélyezi a címzettek hozzáadását a *Címzett* és a *Másolatot kap* sorokban.

**Kódolás a házirendben:** REPLYALL

**Implementáció az Office egyéni jogosultságai között**: Nem alkalmazható

**Neve a klasszikus Azure-portálon:** *Válasz mindenkinek*

**Neve az Active Directory tartalomvédelmi szolgáltatásokban:** *Válasz mindenkinek*

**API-állandó vagy érték:** IPC_EMAIL_REPLYALL L"REPLYALL"

---

### Megtekintés, Megnyitás, Olvasás

Lehetővé teszi a felhasználó számára a dokumentum megnyitását és a tartalom megtekintését.

**Kódolás a házirendben:** VIEW

**Implementáció az Office egyéni jogosultságai között:** Az *Olvasás* egyéni házirend *Megtekintés* beállításaként.

**Neve a klasszikus Azure-portálon:** *Tartalom megtekintése*

**Neve az Active Directory tartalomvédelmi szolgáltatásokban**: *Megtekintés*

**API-állandó vagy érték:** IPC_GENERIC_READ L"VIEW"

---

### Másolás

Lehetővé teszi az adatok (ideértve a képernyőfelvételek) másolását a dokumentumból ugyanazon a dokumentumon belülre, vagy egy másik dokumentumba.

**Kódolás a házirendben:** EXTRACT

**Implementáció az Office egyéni jogosultságai között:** *Az olvasási joggal rendelkező felhasználók másolhatják a tartalmat* egyéni házirend-beállításként.

**Neve a klasszikus Azure-portálon**: *Tartalom másolása és kinyerése*

**Neve az Active Directory tartalomvédelmi szolgáltatásokban**: *Kinyerés*

**API-állandó vagy érték:** IPC_GENERIC_EXTRACT L"EXTRACT"

Egyes alkalmazásokban a teljes dokumentum mentését is lehetővé teszi nem védett állapotban.

---


### Allow Macros (Makrók engedélyezése)

Engedélyezi a makrók futtatását, valamint az egyéb programozott vagy távelérési műveletek végzését a dokumentumok tartalmán.

**Kódolás a házirendben:** OBJMODEL

**Implementáció az Office egyéni jogosultságai között:** *Programozott hozzáférés engedélyezése* egyéni házirend-beállításként. Nem címzettenkénti beállítás.

**Neve a klasszikus Azure-portálon:** *Makrók engedélyezése*

**Neve az Active Directory tartalomvédelmi szolgáltatásokban:** *Makrók engedélyezése*

**API-állandó vagy érték:** Nem alkalmazható


## Jogosultságok az engedélyszintekben

Egyes alkalmazások a használati jogosultságokat engedélyszintekbe csoportosítják, hogy egyszerűbb legyen olyan használati jogosultságokat választani, amelyeket általában együtt használnak. Ezek az engedélyszintek kevésbé összetett, absztrakt módon teszik lehetővé a felhasználók számára, hogy szerepkör szerint választhassanak beállításokat.  Például: **Véleményező** és **Társszerző**. Bár ezek a beállítások általában megjelenítik a jogosultságok összegzését, előfordulhat, hogy nem tartalmaznak minden jogosultságot, amely az előző táblázatban szerepel.

A következő táblázatban láthatja az engedélyszinteket és az ezek által tartalmazott jogosultságok teljes listáját.

|Jogosultsági szint|Alkalmazások|Jogosultságok (köznapi név)|
|---------------------|----------------|---------------------------------|
|Megtekintő|Klasszikus Azure-portál<br /><br />A Windows Microsoft Rights Management megosztóalkalmazás|Megtekintés, Megnyitás, Olvasás; Válasz; Válasz mindenkinek|
|Felülvizsgáló|Klasszikus Azure-portál<br /><br />A Windows Microsoft Rights Management megosztóalkalmazás|Megtekintés, Megnyitás, Olvasás; Mentés; Tartalom szerkesztése, Szerkesztés; Válasz [[1]](#footnote-1); Válasz mindenkinek [[1]](#footnote-1); Továbbítás [[1]](#footnote-1)|
|Társszerző|Klasszikus Azure-portál<br /><br />A Windows Microsoft Rights Management megosztóalkalmazás|Megtekintés, Megnyitás, Olvasás; Mentés; Tartalom szerkesztése, Szerkesztés; Másolás; Jogosultságok megtekintése; Jogosultságok módosítása; Makrók engedélyezése; Mentés másként, Exportálás; Nyomtatás; Válasz [[1]](#footnote-1); Válasz mindenkinek [[1]](#footnote-1); Továbbítás [[1]](#footnote-1)|
|Társtulajdonos|Klasszikus Azure-portál<br /><br />A Windows Microsoft Rights Management megosztóalkalmazás|Megtekintés, Megnyitás, Olvasás; Mentés; Tartalom szerkesztése, Szerkesztés; Másolás; Jogosultságok megtekintése; Jogosultságok módosítása; Makrók engedélyezése; Mentés másként, Exportálás; Nyomtatás; Válasz [[1]](#footnote-1); Válasz mindenkinek [[1]](#footnote-1); Továbbítás [[1]](#footnote-1); Teljes hozzáférés|

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




<!--HONumber=Jul16_HO2-->


