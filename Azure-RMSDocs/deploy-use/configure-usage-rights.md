---
# required metadata

title: Használati jogosultságok konfigurálása az Azure Rights Managementhez | Azure RMS
description:
keywords:
author: cabailey
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 97ddde38-b91b-42a5-8eb4-3ce6ce15393d

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: esaggese
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

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

**Implementáció az Office egyéni jogosultságai között**: A *Módosítás* és a *Teljes hozzáférés* beállítás részeként.**

**Neve a klasszikus Azure-portálon**: *Tartalom szerkesztése*

**Neve az Active Directory tartalomvédelmi szolgáltatásokban**: *Szerkesztés*

**API-állandó vagy érték**: *Nem alkalmazható*

Az Office-alkalmazásokban ez a jogosultság a dokumentum mentését is lehetővé teszi.

---

### Mentés

Lehetővé teszi a felhasználó számára a dokumentum mentését az aktuális helyén.

**Kódolás a házirendben**: EDIT

**Implementáció az Office egyéni jogosultságai között**: A *Módosítás* és a *Teljes hozzáférés* beállítások részeként.

**Neve a klasszikus Azure-portálon**: *Fájl mentése*

**Neve az Active Directory tartalomvédelmi szolgáltatásokban**: *Mentés*

**API-állandó vagy érték**: IPC_GENERIC_WRITEL"EDIT"

Az Office-alkalmazásokban ez a jogosultság a dokumentum módosítását is lehetővé teszi.

---

### Megjegyzés

Engedélyezi jegyzetek és megjegyzések hozzáadását a tartalomhoz.

**Kódolás a házirendben**: COMMENT

**Implementáció az Office egyéni jogosultságai között**: Nincs implementálva.

**Neve a klasszikus Azure-portálon**: Nincs implementálva.

**Neve az Active Directory tartalomvédelmi szolgáltatásokban:** Nincs implementálva.

**API-állandó vagy érték:** IPC_GENERIC_COMMENTL"COMMENT

Ez a jogosultság elérhető az SDK-ban, valamint alkalmi házirendként Windows PowerShell RMS Protection moduljában, és egyes szoftverszállítói alkalmazásokban is implementálva lett. Ennek ellenére a használata nem elterjedt, és az Office-alkalmazások jelenleg nem támogatják.

---

### Mentés másként, Exportálás

Lehetővé teszi a tartalom mentését másik fájlnévvel (Save As (Mentés másként)). Az alkalmazástól függően előfordulhat, hogy a rendszer védelem nélkül menti a fájlt.

**Kódolás a házirendben:** EXPORT

**Implementáció az Office egyéni jogosultságai között**: A *Módosítás* és a *Teljes hozzáférés* beállítások részeként.

**Neve a klasszikus Azure-portálon:** *Tartalom exportálása (Mentés másként)*

**Neve az Active Directory tartalomvédelmi szolgáltatásokban:** *Exportálás (Mentés másként)*

**API-állandó vagy érték:** IPC_GENERIC_EXPORTL"EXPORT"

Ez a jogosultság lehetővé teszi a felhasználónak az alkalmazásokon belüli egyéb exportálási lehetőségek használatát (például *Küldés a OneNote-ba*)..

---

### Továbbítás

Lehetővé teszi az e-mail üzenetek továbbítását és a címzettek hozzáadását a *Címzett* és a *Másolatot kap* sorban.

**Kódolás a házirendben:** FORWARD

**Implementáció az Office egyéni jogosultságai között:** A rendszer megtagadja a *Nem továbbítandó* normál házirend használata esetén.

**Neve a klasszikus Azure-portálon:** *Továbbítás*

**Neve az Active Directory tartalomvédelmi szolgáltatásokban:** *Továbbítás*

**API-állandó vagy érték:** IPC_EMAIL_FORWARDL"FORWARD"

Nem engedélyezi a továbbító számára, hogy jogosultságokat adjon más felhasználóknak a továbbítási művelet részeként.

---

### Teljes hozzáférés

Megadja az összes jogosultságot a dokumentumhoz, így minden elérhető művelet elvégezhető.

**Kódolás a házirendben:** OWNER

**Implementáció az Office egyéni jogosultságai között:** A *Teljes hozzáférés* egyéni beállításként.

**Neve a klasszikus Azure-portálon:** *Teljes hozzáférés*

**Neve az Active Directory tartalomvédelmi szolgáltatásokban:** *Teljes hozzáférés*

**API-állandó vagy érték:** IPC_GENERIC_ALLL"OWNER"

Lehetővé teszi a védelem eltávolítását.

---

### Nyomtatás

Lehetővé teszi a tartalom nyomtatását.

**Kódolás a házirendben:** PRINT

**Implementáció az Office egyéni jogosultságai között:** A *Tartalom nyomtatása* beállításként az egyéni engedélyek között. Nem címzettenkénti beállítás.

**Neve a klasszikus Azure-portálon:** *Nyomtatás*

**Neve az Active Directory tartalomvédelmi szolgáltatásokban:** *Nyomtatás*

**API-állandó vagy érték:** IPC_GENERIC_PRINTL"PRINT

---

### Válasz

Engedélyezi a Válasz lehetőséget az e-mail ügyfélprogramokban, de nem engedélyezi a *Címzett* és a *Másolatot kap* sor módosítását.

**Kódolás a házirendben:** REPLY

**Implementáció az Office egyéni jogosultságai között**: Nem alkalmazható

**Neve a klasszikus Azure-portálon:** *Válasz*

**Neve az Active Directory tartalomvédelmi szolgáltatásokban:** *Válasz*

**API-állandó vagy érték:** IPC_EMAIL_REPLY

---

### Válasz mindenkinek

Engedélyezi a *Válasz mindenkinek* lehetőséget az e-mail ügyfélprogramokban, de nem engedélyezi a címzettek hozzáadását a *Címzett* és a *Másolatot kap* sorokban.

**Kódolás a házirendben:** REPLYALL

**Implementáció az Office egyéni jogosultságai között**: Nem alkalmazható

**Neve a klasszikus Azure-portálon:** *Válasz mindenkinek*

**Neve az Active Directory tartalomvédelmi szolgáltatásokban:** *Válasz mindenkinek*

**API-állandó vagy érték:** IPC_EMAIL_REPLYALLL"REPLYALL"

---

### Megtekintés, Megnyitás, Olvasás

Lehetővé teszi a felhasználó számára a dokumentum megnyitását és a tartalom megtekintését.

**Kódolás a házirendben:** VIEW

**Implementáció az Office egyéni jogosultságai között:** Az *Olvasás* egyéni házirend *Megtekintés* beállításaként.

**Neve a klasszikus Azure-portálon:** *Tartalom megtekintése*

**Neve az Active Directory tartalomvédelmi szolgáltatásokban:** *Megtekintés*

**API-állandó vagy érték:** IPC_GENERIC_READL"VIEW"

---

### View Rights (Jogosultságok megtekintése)

Lehetővé teszi a felhasználó számára a dokumentumra alkalmazott házirend megtekintését.

**Kódolás a házirendben:** VIEWRIGHTSDATA

**Implementáció az Office egyéni jogosultságai között:** Nincs implementálva.

**Neve a klasszikus Azure-portálon:** *Hozzárendelt jogosultságok megtekintése*

**Neve az Active Directory tartalomvédelmi szolgáltatásokban:** *Jogosultságok megtekintése*

**API-állandó vagy érték:** IPC_READ_RIGHTSL"VIEWRIGHTSDATA"

---

### Köznapi név: View Rights (Jogosultságok megtekintése)

Lehetővé teszi a felhasználó számára a dokumentumra alkalmazott házirend megtekintését.

**Kódolás a házirendben:** VIEWRIGHTSDATA

**Implementáció az Office egyéni jogosultságai között:** Nincs implementálva.

**Neve a klasszikus Azure-portálon:** *Hozzárendelt jogosultságok megtekintése*

**Neve az Active Directory tartalomvédelmi szolgáltatásokban:** *Jogosultságok megtekintése*

**API-állandó vagy érték:** IPC_READ_RIGHTSL"VIEWRIGHTSDATA"

Egyes alkalmazások figyelmen kívül hagyják.

---

### Change Rights (Jogosultságok módosítása)

Lehetővé teszi a felhasználó számára a dokumentumra alkalmazott házirend módosítását. Magában foglalja a védelem eltávolítását.

**Kódolás a házirendben:** EDITRIGHTSDATA

**Implementáció az Office egyéni jogosultságai között:** Nincs implementálva.

**Neve a klasszikus Azure-portálon:** *Jogosultságok módosítása*

**Neve az Active Directory tartalomvédelmi szolgáltatásokban:** *Jogosultságok szerkesztése*

**API-állandó vagy érték:** IPC_WRITE_RIGHTSL"EDITRIGHTSDATA"

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
|&lt;*szervezet neve*&gt; * – Csak bizalmas megtekintésre*|Megtekintés, Megnyitás, Olvasás|
|&lt;*szervezet neve*&gt; * – Bizalmas*|Megtekintés, Megnyitás, Olvasás; Mentés; Tartalom szerkesztése, Szerkesztés; Jogosultságok megtekintése; Makrók engedélyezése; Továbbítás; Válasz; Válasz mindenkinek|

## Lásd még:
[Az Azure Rights Management egyéni sablonok konfigurálása](configure-custom-templates.md)



<!--HONumber=Apr16_HO4-->


