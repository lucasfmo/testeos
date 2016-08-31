---
title: "Egyéni sablonok konfigurálása az Azure Rights Management szolgáltatáshoz | Azure RMS"
description: "Miután aktiválta az Azure Rights Management (Azure RMS) szolgáltatást, a felhasználók automatikusan két alapértelmezett sablont használhatnak, amelyek megkönnyítik számukra, hogy olyan házirendeket alkalmazzanak az érzékeny fájlokra, amelyek a fájlokhoz való hozzáférést a szervezeten belüli jogosult felhasználókra korlátozzák. Ez a két sablon a következő jogmegadási korlátozást biztosítja."
author: cabailey
manager: mbaldwin
ms.date: 06/03/2016
ms.topic: article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 1775d8d0-9a59-42c8-914f-ce285b71ac1c
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 26b043f1f9e7a1e0cd00c2f31c28f7d6685f0232
ms.openlocfilehash: 83db5e11a4603523d7c4a86921fbdafb5f6fbfb5


---

# Az Azure Rights Management egyéni sablonok konfigurálása

>*A következőkre vonatkozik: Azure Rights Management, Office 365*

Miután [aktiválta az Azure Rights Management](activate-service.md) (Azure RMS) szolgáltatást, a felhasználók automatikusan két alapértelmezett sablont használhatnak, amelyek megkönnyítik számukra, hogy olyan házirendeket alkalmazzanak az érzékeny fájlokra, amelyek a fájlokhoz való hozzáférést a szervezeten belüli jogosult felhasználókra korlátozzák. Ez a két sablon a következő jogmegadási korlátozást biztosítja:

-   A védett tartalmak csak olvasásra történő megnyitása

    -   Megjelenített név: **&lt;szervezet neve&gt; – Csak bizalmas megtekintésre**

    -   Konkrét engedély: Tartalom megtekintése

-   A védett tartalmak olvasására vagy módosítására vonatkozó engedélyek

    -   Megjelenített név: **&lt;szervezet neve&gt; – Bizalmas**

    -   Konkrét engedélyek: Tartalom megtekintése, fájl mentése, tartalom szerkesztése, hozzárendelt jogosultságok megtekintése, makrók engedélyezése, továbbítás, válasz, válasz mindenkinek

Emellett az [RMS megosztóalkalmazás](../rms-client/sharing-app-windows.md) lehetővé teszi a felhasználók számára, hogy meghatározzák a saját engedélykészletüket. Továbbá az Outlook-ügyfélprogramban és az Outlook Web Accessben a felhasználók kiválaszthatják a [Nem továbbítandó](../deploy-use/configure-usage-rights.md#do-not-forward-option-for-emails) lehetőséget.

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

-   [Sablonok kezelése a PowerShellel](configure-templates-with-powershell.md)





<!--HONumber=Aug16_HO4-->


