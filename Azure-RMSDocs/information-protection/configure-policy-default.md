---
title: "Az alapértelmezett Azure Information Protection-házirend | Azure Rights Management"
description: "Ismerje meg az alapértelmezett Azure Information Protection-házirend konfigurálását. Ha módosítja az alapértelmezett házirendet, ezekkel az értékekkel visszaállíthatja a házirendet az alapértelmezett állapotra."
manager: mbaldwin
ms.date: 08/25/2016
ms.topic: article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 671281c8-f0d1-42b6-aae3-681d1821e2cf
translationtype: Human Translation
ms.sourcegitcommit: da0145444a7d0abb6407ed2ccbb581d4dcdd10d6
ms.openlocfilehash: 44dd47bd73eabe73241ab331c5dee7e06c6c0bef


---

# Az alapértelmezett Azure Information Protection-házirend

>*A következőkre vonatkozik: az Azure Information Protection előzetes verziója*

**[ Előzetes információ, a tartalma változhat. ]**

Az alábbi információk segítségével megismerkedhet az alapértelmezett Azure Information Protection-házirend konfigurálásának módjával. Ha módosítja az alapértelmezett házirendet, ezekkel az értékekkel visszaállíthatja a házirendet az alapértelmezett állapotra.

## Information Protection-menüsáv

|Beállítás|Érték|
|-------------------------------|---------------------------|
|Cím|Érzékenység|
|Elemleírás|Az adatok a bizalmasság szempontjából négy kategóriába sorolhatók (Nyilvános, Belső, Bizalmas, Titkos); a felhasználók ennek alapján felmérhetik az adatok illetéktelen belső vagy külső felhasználók számára történő átadásának kockázatait.|

## Címkék

|Címke|Elemleírás|Beállítások|
|-------------------------------|---------------------------|-----------------|
|Személyes eszközök|Csak személyes használatra. Ezeket az adatokat nem figyeli a szervezete. A személyes adatok között nem tárolhatók üzleti adatok.|**Engedélyezve**: Igen <br /><br />**Szín**: Világoszöld<br /><br />**Vizuális megjelölés**: Nincs <br /><br />**Feltétel**: Nincs<br /><br />**Védelem**: Nincs|
|Nyilvános|Belső információ, amely bárki által felhasználható a cégen belül vagy kívül.|**Engedélyezve**: Igen <br /><br />**Szín**: Zöld<br /><br />**Vizuális megjelölés**: Nincs<br /><br />**Feltétel**: Nincs<br /><br />**Védelem**: Nincs|
|Belső|Belső üzleti adatok tág köre, amelyet minden alkalmazott használhat, és amely megosztható a jogosult ügyfelekkel és üzleti partnerekkel. Belső adatnak minősülnek például a vállalati szabályzatok és a belső kommunikáció nagy része.|**Engedélyezve**: Igen <br /><br />**Szín**: Kék <br /><br />**Vizuális megjelölés**: élőláb (dokumentumokban és e-mailekben)<br /><br />**Feltétel**: Nincs<br /><br />**Védelem**: Nincs|
|Bizalmas|Ezek az adatok bizalmas üzleti információkat tartalmaznak. Az ilyen adatok illetéktelen felhasználókkal való megosztása kárt okozhat a szervezetnek. Bizalmas adatok többek között az alkalmazottakkal kapcsolatos információk, az egyedi ügyfélprojektek vagy -szerződések, valamint az értékesítési adatok.|**Engedélyezve**: Igen <br /><br />**Szín**: narancssárga<br /><br />**Vizuális megjelölés**: élőláb (dokumentumokban és e-mailekben)<br /><br />**Feltétel**: Nincs<br /><br />**Védelem**: Nincs|
|Titkos|Szigorúan bizalmas üzleti adatok, amelyek védelmet igényelnek. Az ilyen adatok illetéktelen felhasználókkal való megosztása komoly kárt okozhat a szervezetnek. Titkosak például a személyes azonosító adatok, az ügyfélrekordok, a forráskódok és a még nem nyilvánosságra hozott pénzügyi jelentések.|**Engedélyezve**: Igen <br /><br />**Szín**: piros<br /><br />**Vizuális megjelölés**: élőláb (dokumentumokban és e-mailekben)<br /><br />**Feltétel**: Nincs<br /><br />**Védelem**: Nincs|

## Alcímkék

|Címke|Elemleírás|Beállítások|
|-------------------------------|---------------------------|-----------------|
|*Titkos* > A teljes cég|Bizalmas üzleti adatok, amelyekhez minden céges alkalmazott hozzáférhet.|**Engedélyezve**: Igen <br /><br />**Vizuális megjelölés**: Nincs<br /><br />**Feltétel**: Nincs<br /><br />**Védelem**: Nincs|
|*Secret* > Saját csoport|Bizalmas üzleti adatok, amelyekhez csak az alkalmazotti csoportok férhetnek hozzá.|**Engedélyezve**: Igen <br /><br />**Vizuális megjelölés**: Nincs<br /><br />**Feltétel**: Nincs<br /><br />**Védelem**: Nincs|

## Globális beállítások

|Beállítás|Érték|
|-------------------------------|---------------------------|
|Minden dokumentumnak és e-mailnek rendelkeznie kell (automatikusan vagy a felhasználók által megadott) címkével|Ki|
|Alapértelmezett címke kiválasztása|Nincsenek|
|A felhasználóknak meg kell indokolniuk a bizalmassági szint csökkentését (például Bizalmasról Nyilvánosra)|Ki|


## További lépések

További információt az Azure Information Protection-házirend konfigurálásáról a [Szervezet házirendjeinek konfigurálása](configure-policy.md#configuring-your-organization-s-policy) szakasz hivatkozásai között találhat. 



<!--HONumber=Aug16_HO4-->


