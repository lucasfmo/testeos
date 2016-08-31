---
title: "Támogatott fájlformátumok | Azure RMS"
description: "A fájl API jelenlegi verziója támogatja a MS Office- és PDF-fájlok natív védelmét, valamint minden más fájlformátum PFile-védelmét."
keywords: 
author: bruceperlerms
manager: mbaldwin
ms.date: 08/24/2016
ms.topic: article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: EC831494-7F2C-4C70-9063-B02CDDEA14EE
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 024a29d7c7db2e4c0578a95c93e22f8e7a5b173e
ms.openlocfilehash: e41d8d697d7c35beef84277bc5b9fd497d79cc10


---

# Támogatott fájlformátumok

A fájl API támogatja a natív és a PFile formátumokat.

## Támogatott fájlformátumok

A fájl API jelenlegi verziója támogatja a Microsoft Office- és PDF-fájlok natív védelmét, valamint minden más fájlformátum PFile-védelmét. A PDF-fájlok opcionálisan elláthatók PFile-védelemmel is.

-   **Natív védelem**. Natív védelem esetén a fájl a MIME-típusán (fájlnévkiterjesztésén) alapuló AD RMS fájlformátumra van titkosítva. A fájl API-val natívan védett fájlok megfelelnek a natív védelmet használó AD RMS-kompatibilis alkalmazások által várt formátumnak; például: Office 2013, Office 2010 és FoxIt PDF reader. A natív védelem kizárólag Office-fájlok, PDF-fájlok és egyes választott fájltípusok esetén támogatott. Azokkal a fájltípusokkal kapcsolatos további információkért, amelyek esetében a natív védelem támogatott, lásd: [A fájl API konfigurálása](file-api-configuration.md).
-   **PFile-védelem**. PFile-védelem esetén a fájlok az AD RMS PFile formátumával vannak titkosítva. A fájl egy .pfile kiterjesztésű fájlba van titkosítva. A PFile-védelem az Office-fájlokon kívül minden fájlformátum esetében támogatott.

A rendszergazdák beállításkulcsok beállításával konfigurálhatják, hogy a fájlok védve legyenek-e a fájlnévkiterjesztésük alapján, és ha igen, akkor hogyan. További információ a fájlvédelem konfigurálásáról a fájl API használata esetén: [A fájl API konfigurálása](file-api-configuration.md).

## Kapcsolódó témakörök

* [Megjegyzések fejlesztők számára](developer-notes.md)
* [File API configuration (A File API konfigurálása)](file-api-configuration.md)
 

 



<!--HONumber=Aug16_HO4-->


