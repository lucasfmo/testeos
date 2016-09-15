---
title: "Kifejezések | Azure RMS"
description: "A Rights Management Services szolgáltatásokra jellemző terminológiai definíciók gyűjteménye."
keywords: 
author: bruceperlerms
manager: mbaldwin
ms.date: 08/24/2016
ms.topic: article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: adb1f868-0da7-431b-83d1-86f41c2da4ae
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 024a29d7c7db2e4c0578a95c93e22f8e7a5b173e
ms.openlocfilehash: 5340673beb2a6f2dd4acd96fd599c0b90b9991dd


---

# Kifejezések

A Rights Management Services szolgáltatásokra jellemző terminológiai definíciók gyűjteménye.

**Elavult algoritmus**  
Egy régi tartalomvédelmi sémát implementáló modális beállítás, amely kifejezetten hivatkozik az elektronikus kódkönyv (ECB) módú titkosításra. A jelen SDK-ban a beállítás lehetővé teszi az [AAD Rights Management Services SDK](https://msdn.microsoft.com/library/windows/desktop/cc530379.aspx) által használt MSDRM könyvtárral kompatibilis licencek létrehozását.

Elképzelhető, hogy ezen beállítás miatt az alkalmazás olyan tartalomvédelmi módszert használ, amely nem felel meg az ügyfelei tartalomvédelmi szabványainak.

Ez a beállítás megakadályozza, hogy az alkalmazás kihasználja a Microsoft Right Management SDK 3.0-s és újabb verzióiban elérhető titkosítási fejlesztések által nyújtott előnyöket.

**A Microsoft védett fájlformátuma**

Más néven PFile formátum, az AD RMS alapértelmezett fájlformátuma, amely szabványként funkcionál az RMS-kompatibilis alkalmazásokban.

A PFile formátum átlátható az alkalmazás fejlesztője számára, mivel az a Microsoft Rights Management SDK 4.2 felépítésének megfelelően van beágyazva.

 

 






<!--HONumber=Aug16_HO4-->


