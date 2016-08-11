---
title: "Az alapértelmezett Azure Information Protection-házirend | Azure Rights Management"
description: 
author: cabailey
manager: mbaldwin
ms.date: 07/21/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 671281c8-f0d1-42b6-aae3-681d1821e2cf
translationtype: Human Translation
ms.sourcegitcommit: 93444affe94b280db2c9e4e2960c6902e491dec6
ms.openlocfilehash: 977cbf2f45cab75aaca9c2a16dd1564c2af2fe4a


---

# Az alapértelmezett Azure Information Protection-házirend

>*A következőkre vonatkozik: az Azure Information Protection előzetes verziója*

**[ Előzetes információ, a tartalma változhat. ]**

Az alábbi információk segítségével megismerkedhet az alapértelmezett Azure Information Protection-házirend konfigurálásának módjával. Ha módosítja az alapértelmezett házirendet, ezekkel az értékekkel visszaállíthatja a házirendet az alapértelmezett állapotra.

## Information Protection-menüsáv

Cím: **Bizalmasság**

Elemleírás: **Az adatok bizalmassága négy szintre osztható (Nyilvános, Belső, Bizalmas, Titkos), a felhasználók így felmérhetik az adatok illetéktelen belső vagy külső felhasználók számára történő nyilvánosságra hozásának kockázatait.**


## Címkék

Öt alapértelmezett címke közül választhat, amelyek az alábbi beállításokkal rendelkeznek:

### **Személyes eszközök**

Elemleírás: **Csak személyes használatra. Ezeket az adatokat nem figyeli a szervezete. A személyes adatok között nem tárolhatók üzleti adatok.**

Szín: világoszöld

Vizuális megjelölés: nincs

Feltétel: nincs

Védelem: nincs

----


### **Nyilvános**

Elemleírás: **Belső adatok, amelyek a cégen belüli és kívüli felhasználók által is használhatók.**

Szín: zöld

Vizuális megjelölés: nincs

Feltétel: nincs

Védelem: nincs

----

### **Belső**

Elemleírás: ** Belső üzleti adatok széles skálája, amely minden alkalmazott, valamint jogosult ügyfél és üzlettárs által használható. Belső adat például a vállalati szabályzatok és a belső kommunikáció nagy része.**

Szín: kék

Vizuális megjelölés: élőláb (dokumentumokban és e-mailekben)

Feltétel: nincs

Védelem: nincs

----

### **Bizalmas**

Elemleírás: **Bizalmas üzleti adatok. Az ilyen adatok illetéktelen felhasználókkal való megosztása kárt okozhat a szervezetnek. Bizalmas adatok többek között az alkalmazottakkal kapcsolatos információk, az egyéni ügyfélprojektek vagy -szerződések, valamint az értékesítési fiók adatai.**

Szín: narancssárga

Vizuális megjelölés: élőláb (dokumentumokban és e-mailekben)

Feltétel: nincs

Védelem: nincs

----

### **Titkos**

Elemleírás: **Szigorúan bizalmas üzleti adatok, amelyeket védelem alá kell helyezni. Az ilyen adatok illetéktelen felhasználókkal való megosztása komoly kárt okozhat a szervezetnek. Titkos adatok, például a személyes azonosító adatok, az ügyfélrekordok, a forráskódok és az előre bejelentett pénzügyi jelentések.**

Szín: piros

Vizuális megjelölés: élőláb (dokumentumokban és e-mailekben)

Feltétel: nincs

Védelem: nincs

----


## Alcímkék

Két alapértelmezett alcímke közül választhat, amelyek az alábbi beállításokkal rendelkeznek:

### Titkos > **A teljes cég**

Elemleírás: **Bizalmas üzleti adatok, amelyekhez minden céges alkalmazott hozzáférhet.**

Vizuális megjelölés: nincs

Feltétel: nincs

Védelem: nincs

----

### Titkos > **Saját csoport**

Elemleírás: **Bizalmas üzleti adatok, amelyekhez csak az alkalmazotti csoportok férhetnek hozzá.**

Vizuális megjelölés: nincs

Feltétel: nincs

Védelem: nincs

## Globális beállítások

**All documents and emails must have a label (applied automatically or by users)** (Minden dokumentumnak és e-mailnek rendelkeznie kell (automatikusan vagy a felhasználók által megadott) címkével): Kikapcsolva

**Select the default label** (Alapértelmezett címke kiválasztása): Nincs

**Users must provide justification when lowering the sensitivity level** (A felhasználóknak meg kell indokolniuk a bizalmassági szint csökkentését): Kikapcsolva

## További lépések

További információt az Azure Information Protection-házirend konfigurálásáról a [Szervezet házirendjeinek konfigurálása](configure-policy.md#configuring-your-organization-s-policy) szakasz hivatkozásai között találhat. 



<!--HONumber=Jul16_HO5-->


