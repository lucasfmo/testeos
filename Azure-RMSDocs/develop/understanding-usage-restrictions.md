---
title: "A használattal kapcsolatos korlátozások megértése | Azure RMS"
description: "Minden RMS-kompatibilis alkalmazásnak ki kell kényszerítenie a használattal kapcsolatos korlátozásokat."
keywords: 
author: bruceperlerms
manager: mbaldwin
ms.date: 08/24/2016
ms.topic: article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: E388B16C-ECDA-4696-A040-D457D3C96766
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 024a29d7c7db2e4c0578a95c93e22f8e7a5b173e
ms.openlocfilehash: df210bd7aff33fda41a278e6aed1108574fe68eb


---

# A használattal kapcsolatos korlátozások megértése

Minden RMS-kompatibilis alkalmazásnak ki kell kényszerítenie a használattal kapcsolatos korlátozásokat. A használattal kapcsolatos korlátozás egy olyan feltétel, amely akkor ad eredményt, ha az ügyfél megpróbál elvégezni egy műveletet (például egy dokumentum nyomtatása), de az RMS-házirend nem ad neki az adott művelet elvégzésére engedélyt vagy jogosultságot (például a PRINT jogosultságot).

Egy felhasználó adott dokumentumra vonatkozó engedélyei lekérhetők az [**IpcAccessCheck**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcaccesscheck) függvénnyel.

## A használattal kapcsolatos korlátozások megértése

-   A szabványos RMS-jogosultságok megismerése

    Az alkalmazás által kikényszeríthető összes RMS-jogosultsággal kapcsolatban lásd: [Használattal kapcsolatos korlátozások – referencia](usage-restriction-reference.md).

    Vegye figyelembe, hogy létrehozhatók az adott helyzetre jellemző, alkalmazás által meghatározott jogosultságok, vagy olyanok, amelyek részletesebbek a szabványos RMS-jogosultságoknál.

-   A használattal kapcsolatos korlátozások kényszerítési pontjainak azonosítása

    A *használattal kapcsolatos korlátozások kényszerítési pontja* egy olyan hely az alkalmazás vezérlési folyamatában, ahol ki kell kényszerítenie egy használattal kapcsolatos korlátozást. A [Használattal kapcsolatos korlátozások – referencia](usage-restriction-reference.md) című témakör számos példát biztosít a tipikus kényszerítési pontokra.

    Értékelje az alkalmazását, hogy meghatározhassa, melyik használattal kapcsolatos korlátozási kényszerítési pontot kell alkalmaznia.

    Előfordulhat, hogy az alkalmazásában nem lesz szükség az összes, a [Használattal kapcsolatos korlátozások – referencia](usage-restriction-reference.md) szakaszban leírt kényszerítési pontra. Ha például az alkalmazása nem engedélyezi a felhasználók számára tartalom nyomtatását, nem kell ellenőriznie az **IPC\_GENERIC\_PRINT** jogosultságot.

-   A kód frissítése, hogy minden kényszerítési pontnál végrehajtson egy hozzáférés-ellenőrzést

    Útmutatás az adott jogosultságok kényszerítésével kapcsolatban: [Használattal kapcsolatos korlátozások – referencia](usage-restriction-reference.md).

## Kapcsolódó témakörök

* [**IpcAccessCheck**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcaccesscheck)
* [Használattal kapcsolatos korlátozások – referencia](usage-restriction-reference.md)
 

 



<!--HONumber=Aug16_HO4-->


