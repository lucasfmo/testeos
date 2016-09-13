---
title: "Operations for Your Azure Rights Management Tenant Key (Az Azure Rights Management bérlőkulcsával kapcsolatos műveletek) | Azure RMS"
description: "Határozza meg az Azure Rights Management (Azure RMS) bérlőkulccsal kapcsolatos vezérlés és felelősség különböző szintjeit."
author: cabailey
manager: mbaldwin
ms.date: 08/25/2016
ms.topic: article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 1284d0ee-0a72-45ba-a64c-3dcb25846c3d
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ad32910b482ca9d92b4ac8f3f123eda195db29cd
ms.openlocfilehash: d496a99c4b05e0cf0ba5929f44cdbd1906d31341


---

# Operations for Your Azure Rights Management Tenant Key (Az Azure Rights Management bérlőkulcsával kapcsolatos műveletek)

>*A következőkre vonatkozik: Azure Rights Management, Office 365*

A Microsoft Azure Rights Management (Azure RMS) bérlőkulcs megvalósítása után az irányítás és a felelősség szintje a bérlőkulcs topológiájától függően (Microsoft által felügyelt vagy felhasználó által felügyelt) eltérő lehet.

Ha saját maga felügyeli a bérlőkulcsát az Azure Key Vaultban, azt általában a saját kulcs használatának (BYOK) nevezik. További információk erről a forgatókönyvről és arról, hogy melyik bérlőkulcs-topológiát válassza: [Az Azure Rights Management-bérlőkulcs tervezése és megvalósítása](../plan-design/plan-implement-tenant-key.md).

Az alábbi táblázat tartalmazza azokat a műveleteket, amelyeket végrehajthat, attól függően, hogy melyik topológiát választotta az Azure RMS-bérlőkulcshoz.

|Életciklushoz kapcsolódó művelet|Microsoft által felügyelt (alapértelmezett)|Felhasználó által felügyelt (BYOK)|
|-----------------------|-------------------------------|---------------------------|
|A bérlőkulcs visszavonása|Nem (automatikus)|Igen|
|A bérlőkulcs kulcsismétlése|Igen|Igen|
|A bérlőkulcs biztonsági mentése és helyreállítása|Nem|Igen|
|A bérlőkulcs exportálása|Igen|Nem|
|Válasz a biztonsági szabályok megsértésére|Igen|Igen|

Miután azonosította, hogy melyik topológiát valósította meg, válasszon egyet az alábbiak közül, ha további információkat szeretne ezekről az Azure RMS bérlőkulcshoz kapcsolódó műveletekről:


- [Microsoft által felügyelt bérlőkulcs](operations-microsoft-managed-tenant-key.md)
- [Felhasználó által felügyelt bérlőkulcs](operations-customer-managed-tenant-key.md)







<!--HONumber=Aug16_HO4-->


