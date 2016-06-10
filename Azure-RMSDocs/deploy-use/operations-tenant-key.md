---
# required metadata

title: Operations for Your Azure Rights Management Tenant Key (Az Azure Rights Management bérlőkulcsával kapcsolatos műveletek) | Azure RMS
description:
keywords:
author: cabailey
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 1284d0ee-0a72-45ba-a64c-3dcb25846c3d

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: esaggese
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Operations for Your Azure Rights Management Tenant Key (Az Azure Rights Management bérlőkulcsával kapcsolatos műveletek)

*A következőkre vonatkozik: Azure Rights Management, Office 365*

A Microsoft Azure Rights Management (Azure RMS) bérlőkulcs megvalósítása után az irányítás és a felelősség szintje a bérlőkulcs topológiájától függően (Microsoft által felügyelt vagy felhasználó által felügyelt) eltérő lehet.

Ha saját maga felügyeli a bérlőkulcsát, azt a saját kulcs használatának (BYOK) nevezik. További információk erről a forgatókönyvről és arról, hogy melyik bérlőkulcs-topológiát válassza: [Planning and implementing your Azure Rights Management tenant key](../plan-design/plan-implement-tenant-key.md) (Az Azure Rights Management-bérlőkulcs tervezése és megvalósítása).

Az alábbi táblázat tartalmazza azokat a műveleteket, amelyeket végrehajthat, attól függően, hogy melyik topológiát választotta az Azure RMS-bérlőkulcshoz.

|Életciklushoz kapcsolódó művelet|Microsoft által felügyelt (alapértelmezett)|Felhasználó által felügyelt (BYOK)|
|-----------------------|-------------------------------|---------------------------|
|A bérlőkulcs visszavonása|Nem (automatikus)|Nem (automatikus)|
|A bérlőkulcs kulcsismétlése|Igen|Igen|
|A bérlőkulcs biztonsági mentése és helyreállítása|Nem|Igen|
|A bérlőkulcs exportálása|Igen|Nem|
|Válasz a biztonsági szabályok megsértésére|Igen|Igen|

Miután azonosította, hogy melyik topológiát valósította meg, válasszon egyet az alábbiak közül, ha további információkat szeretne ezekről az Azure RMS bérlőkulcshoz kapcsolódó műveletekről:


- [Microsoft által felügyelt bérlőkulcs](operations-microsoft-managed-tenant-key.md)
- [Felhasználó által felügyelt bérlőkulcs](operations-customer-managed-tenant-key.md)






<!--HONumber=Apr16_HO4-->


