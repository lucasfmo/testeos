---
title: "Kifejezések | Azure RMS"
description: "A Rights Management Services szolgáltatásokra jellemző terminológiai definíciók gyűjteménye."
keywords: 
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: adb1f868-0da7-431b-83d1-86f41c2da4ae
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.sourcegitcommit: f7dd88d90357c99c69fe4fdde67c1544595e02f8
ms.openlocfilehash: 5779cc10503ad7afe997e031a467021b513fc510


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

 

 






<!--HONumber=Jun16_HO4-->


