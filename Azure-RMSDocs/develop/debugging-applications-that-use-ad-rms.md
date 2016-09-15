---
title: "Útmutató: Tartalomvédelemmel kompatibilis alkalmazások hibakeresése | Azure RMS"
description: "A következő témakör az alkalmazások hibakeresésének és a Windows Eseménynapló használatának módját ismerteti."
keywords: 
author: bruceperlerms
manager: mbaldwin
ms.date: 08/24/2016
ms.topic: article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 6F6C7651-6A6E-45DD-A0C5-F036F803249B
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 024a29d7c7db2e4c0578a95c93e22f8e7a5b173e
ms.openlocfilehash: 31b2fe22bbbb31b991bdf88e408c943e6d2ba685


---

# Útmutató: Tartalomvédelemmel kompatibilis alkalmazások hibakeresése

A következő témakör az alkalmazások hibakeresésének és a Windows Eseménynapló használatának módját ismerteti.

## Az alkalmazás hibakeresése

A Rights Management Services SDK 2.1-es verziójában a fejlesztői verzió hibakeresést kizáró, futásidejű ellenőrzései le vannak tiltva.

Az alábbi beállításkulcs használatával kapcsolhatja be a hibakeresési nyomkövetést. (A hibakeresési nyomkövetés kikapcsolásához állítsa ezt az értéket 0-ra.) A jelen kiadásban semmi másra nincs szükség a hibakereséshez.


```
HKEY_LOCAL_MACHINE
   SOFTWARE
      Microsoft
         MSIPC
            "Trace" = 00000001
            Data type
            dword
```

### Alkalmazásnaplózás a Windows-eseménynapló használatával

Az eseménynapló neve: „Microsoft-RMS-MSIPC/Debug”. A Windows eseménynaplójában tehát a napló a következőképpen jelenik meg: „Alkalmazás- és szolgáltatásnaplók\\Microsoft\\RMS\\MSIPC\\Debug”.

**Megjegyzés** A napló alapértelmezés szerint engedélyezett, és 3. részletességi szintre van állítva.

 

A naplózási funkció beállításainak módosításához a Windows Eseménynapló vagy a Wevtutil (a Windows beépített parancssori eszköze) felhasználói felülete egyaránt használható.

A Wevtutil felületén keresztül beállítható a napló részletességi szintje.

Jelenleg a naplózás következő 3 szintje támogatott:

-   2. szint – Hiba
-   3. szint – Figyelmeztetés
-   4. szint – Információ

Az alábbi paranccsal például engedélyezhető az MSIPC eseménynaplózás, illetve a részletességi szint információsra állítható be.

**wevtutil sl Microsoft-RMS-MSIPC/Debug /e:true /l:4**

**Megjegyzés** A Windows eseménynapló **Nézet** menüjében az **Elemzési és hibakeresési naplók megjelenítése** lehetőség kiválasztásával tehető láthatóvá az MSIPC hibakeresési napló.

 

## Kapcsolódó témakörök

 

 



<!--HONumber=Aug16_HO4-->

