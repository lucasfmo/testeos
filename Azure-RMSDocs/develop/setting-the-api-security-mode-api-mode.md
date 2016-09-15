---
title: "Útmutató: Az API biztonsági üzemmód beállítása | Azure RMS"
description: "Válassza ki, hogy melyik biztonsági módban fusson a File API alkalmazás."
keywords: 
author: bruceperlerms
manager: mbaldwin
ms.date: 08/24/2016
ms.topic: article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 3B088F14-81C5-4C78-8DED-F5F153353EE0
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 024a29d7c7db2e4c0578a95c93e22f8e7a5b173e
ms.openlocfilehash: 1cc034787f8bc47f874259edb143ba0b3f62e47a


---

# Útmutató: Az API biztonsági üzemmód beállítása

Az [**IpcSetGlobalProperty**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcsetglobalproperty) funkció használatával kiválaszthatja, hogy melyik biztonsági módban fusson a File API alkalmazás.

Az alkalmazás *kiszolgáló módban* való futtatásának inicializálásához hívja az [**IpcSetGlobalProperty**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcsetglobalproperty) funkciót, és állítsa a biztonsági módot az [**IPC\_API\_MODE\_SERVER**](/rights-management/sdk/2.1/api/win/api%20mode%20values#msipc_api_mode_values_IPC_API_MODE_SERVER) értékre. Alapértelmezés szerint az alkalmazás *ügyfélmódban* (**IPC\_API\_MODE\_CLIENT**) fog futni.

További információ a *kiszolgáló módról*: [Application types](application-types.md) (Alkalmazástípusok).

**Fontos**  A biztonsági módot azelőtt kell beállítani, mielőtt a Rights Management Services SDK 2.1 bármely más funkcióját hívná. A biztonsági módot a beállítása után már nem lehet módosítani az adott folyamat esetében.

## Kapcsolódó témakörök

* [Alkalmazástípusok](application-types.md)
* [**API módértékek**](/rights-management/sdk/2.1/api/win/api%20mode%20values#msipc_api_mode_values_IPC_API_MODE_SERVER)
* [**IpcSetGlobalProperty**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcsetglobalproperty)
 

 



<!--HONumber=Aug16_HO4-->


