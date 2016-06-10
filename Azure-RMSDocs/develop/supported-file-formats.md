---
# required metadata

title: Támogatott fájlformátumok | Azure RMS
description: A fájl API jelenlegi verziója támogatja a MS Office- és PDF-fájlok natív védelmét, valamint minden más fájlformátum PFile-védelmét.
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: EC831494-7F2C-4C70-9063-B02CDDEA14EE
# optional metadata

#ROBOTS:
audience: developer
#ms.devlang:
ms.reviewer: shubhamp
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---
** Ez az SDK-tartalom nem naprakész. Ideiglenesen arra kérjük, keresse fel az MSDN webhelyén található dokumentáció [aktuális verzióját](https://msdn.microsoft.com/library/windows/desktop/hh535290(v=vs.85).aspx). **
# Támogatott fájlformátumok

A fájl API támogatja a natív és a PFile formátumokat.

## Támogatott fájlformátumok

A fájl API jelenlegi verziója támogatja a Microsoft Office- és PDF-fájlok natív védelmét, valamint minden más fájlformátum PFile-védelmét. A PDF-fájlok opcionálisan elláthatók PFile-védelemmel is.

-   **Natív védelem**. Natív védelem esetén a fájl a MIME-típusán (fájlnévkiterjesztésén) alapuló AD RMS fájlformátumra van titkosítva. A fájl API-val natívan védett fájlok megfelelnek a natív védelmet használó AD RMS-kompatibilis alkalmazások által várt formátumnak; például: Office 2013, Office 2010 és FoxIt PDF reader. A natív védelem kizárólag Office-fájlok, PDF-fájlok és egyes választott fájltípusok esetén támogatott. Azokkal a fájltípusokkal kapcsolatos további információkért, amelyek esetében a natív védelem támogatott lásd: [File API configuration](file-api-configuration.md) (A fájl API konfigurálása).
-   **PFile-védelem**. PFile-védelem esetén a fájlok az AD RMS PFile formátumával vannak titkosítva. A fájl egy .pfile kiterjesztésű fájlba van titkosítva. A PFile-védelem az Office-fájlokon kívül minden fájlformátum esetében támogatott.

A rendszergazdák beállításkulcsok beállításával konfigurálhatják, hogy a fájlok védve legyenek-e, és ha igen, akkor hogyan a fájlnévkiterjesztésük alapján. További információ a fájlvédelem konfigurálásáról a fájl API használata esetén: [File API configuration](file-api-configuration.md) (A fájl API konfigurálása).

## Kapcsolódó témakörök

* [Megjegyzések fejlesztők számára](developer-notes.md)
* [File API configuration (A File API konfigurálása)](file-api-configuration.md)
 

 





<!--HONumber=Jun16_HO1-->


