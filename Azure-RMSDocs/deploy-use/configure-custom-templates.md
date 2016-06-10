---
# required metadata

title: Egyéni sablonok konfigurálása az Azure Rights Management szolgáltatáshoz | Azure RMS
description:
keywords:
author: cabailey
manager: mbaldwin
ms.date: 05/23/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 1775d8d0-9a59-42c8-914f-ce285b71ac1c

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: esaggese
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Az Azure Rights Management egyéni sablonok konfigurálása

*A következőkre vonatkozik: Azure Rights Management, Office 365*

Miután [aktiválta az Azure Rights Management](activate-service.md) (Azure RMS) szolgáltatást, a felhasználók automatikusan két alapértelmezett sablont használhatnak, amelyek megkönnyítik számukra, hogy olyan házirendeket alkalmazzanak az érzékeny fájlokra, amelyek a fájlokhoz való hozzáférést a szervezeten belüli jogosult felhasználókra korlátozzák. Ez a két sablon a következő jogmegadási korlátozást biztosítja:

-   A védett tartalmak csak olvasásra történő megnyitása

    -   Megjelenített név: **&lt;szervezet neve&gt; – Csak bizalmas megtekintésre**

    -   Konkrét engedély: Tartalom megtekintése

-   A védett tartalmak olvasására vagy módosítására vonatkozó engedélyek

    -   Megjelenített név: **&lt;szervezet neve&gt; – Bizalmas**

    -   Konkrét engedélyek: Tartalom megtekintése, fájl mentése, tartalom szerkesztése, hozzárendelt jogosultságok megtekintése, makrók engedélyezése, továbbítás, válasz, válasz mindenkinek

Emellett az [RMS megosztóalkalmazás](../rms-client/sharing-app-windows.md) lehetővé teszi a felhasználók számára, hogy meghatározzák a saját engedélykészletüket. Emellett az Outlook-ügyfélben és az Outlook Web Accessben a felhasználók az e-mailekhez kiválaszthatják a **Nem továbbítandó** lehetőséget.

A legtöbb szervezet számára az alapértelmezett sablonok valószínűleg elegendőek. Ha azonban szeretné létrehozni a saját egyéni jogmegadási sablonjait, azt is megteheti. Az egyéni sablonok létrehozásának több oka is lehet, például:

-   Egy olyan sablont szeretne használni, amely bizonyos jogokat a szervezet összes felhasználója helyett csak a felhasználók egy részének ad meg.

-   Azt szeretné, hogy a szervezet összes felhasználója helyett csak a felhasználók egy része számára legyen látható és kiválasztható egy bizonyos sablon (részlegszintű sablon) az alkalmazások közül.

-   Egyéni jogokat szeretne beállítani egy sablonhoz, például hogy az engedélyezze a megtekintést és a szerkesztést, de a másolást és a nyomtatást ne.

-   Olyan további beállításokat szeretne megadni egy sablonon, mint a lejárati dátum, vagy hogy a tartalom elérhető legyen-e internetkapcsolat nélkül.

Ahhoz, hogy az ilyen és ehhez hasonló beállításokkal rendelkező egyéni sablonok a felhasználók számára láthatóvá és kiválaszthatóvá váljanak, először létre kell hozni egy egyéni sablont, majd be kell állítani és közzé kell tenni azt. Bár a későbbiekben valószínűleg csak néhány sablonra lesz szüksége, az Azure-ban akár 500 egyéni sablont is menthet. 

A következő információk segítséget nyújtanak az egyéni sablonok konfigurálásában és használatában:

-   [Egyéni sablonok létrehozása, konfigurálása és közzététele](create-template.md)

-   [Sablon másolása](copy-template.md)

-   [Sablonok eltávolítása (archivált sablonokat is beleértve)](remove-template.md)

-   [Sablonok frissítése a felhasználók számára](refresh-templates.md)

-   [Sablonok kezelése a PowerShell-lel](configure-templates-with-powershell.md)




<!--HONumber=May16_HO5-->


