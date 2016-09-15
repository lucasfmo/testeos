---
title: "A fejlesztési környezet fájljai | Azure RMS"
description: "Ez a témakör a fejlesztési környezet fájljait és azok relatív telepítési útvonalait ismerteti a számítógépen."
keywords: 
author: bruceperlerms
manager: mbaldwin
ms.date: 08/24/2016
ms.topic: article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: B57AC6F3-733C-42A8-AF83-0E15FBF27C99
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 024a29d7c7db2e4c0578a95c93e22f8e7a5b173e
ms.openlocfilehash: a3f1e913c92dbee3b889a3d3c0bd6c97317112c9


---

# A fejlesztési környezet fájljai

Ez a témakör a fejlesztési környezet fájljait és azok relatív telepítési útvonalait ismerteti a számítógépen.

A Rights Management Services SDK 2.1 a következő fájlokat tartalmazza, amelyek az alapértelmezett helyen vagy a megadott helyen vannak telepítve a számítógépen: %MsipcSDKDir%.

|Fájl|Elérési út|Leírás|
|----|----|-----------|
|ReadMe.htm| \ | Az RMS súgójának és a [Kibocsátási megjegyzések](release-notes-rtm.md) hivatkozását tartalmazza.|
|Isvtier5appsigningprivkey.dat|\bin|Az RMS-kompatibilis alkalmazások fejlesztése során használatos jegyzékfájl létrehozásához használt titkos kulcsot tartalmazza.|
|Isvtier5appsigningpubkey.dat|\bin|Az RMS-kompatibilis alkalmazások fejlesztése során használatos jegyzékfájl létrehozásához használt nyilvános kulcsot tartalmazza.|
|Isvtier5appsignsdk_client.xml|\bin|Az RMS-kompatibilis alkalmazások fejlesztése során a jegyzékfájl létrehozására szolgál.|
|YourAppName.isv.mcf|\bin|Egy bolierplate jegyzékkonfigurációs fájl, amellyel egy jegyzékfájl hozható létre az RMS-kompatibilis alkalmazások fejlesztése során.|
|Ipcsecproc_isv.dll|\bin\x86|Belsőleg, az Active Directory Rights Management Services ügyfelének 2.1-es verziója által az ISV hierarchiában használt DLL az x86-alkalmazásokhoz.|
|Ipcsecproc_ssp_isv.dll|\bin\x86|Belsőleg, az AD RMS 2.1-es verziója által az ISV hierarchiában használt DLL az x86-alkalmazásokhoz.|
|Ipcsecproc_isv.dll|\bin\x64|Belsőleg, az AD RMS ügyfél 2.1-es verziója által az ISV hierarchiában használt DLL az x64-alkalmazásokhoz.|
|Ipcsecproc_ssp_isv.dll|\bin\x64|Belsőleg, az AD RMS ügyfél 2.1-es verziója által az ISV hierarchiában használt DLL az x64-alkalmazásokhoz.|
|Msipc.h|\inc|Az RMS SDK 2.1 fő beágyazott fájlja.|
|Ipcprot.h|\inc|Az RMS SDK 2.1 által exportált nyilvános illesztőfelületet tartalmazza.|
|Ipcbase.h|\inc|Az RMS SDK 2.1 által exportált alaptípusokat és súgófunkciókat tartalmazza.|
|Ipcerror.h|\inc|Az RMS SDK 2.1 által exportált nyilvános hibakódokat tartalmazza.|
|Ipcfile.h|\inc|Az RMS SDK 2.1 által exportált fájl API-felületeket tartalmazza.|
|Msipc.lib|\lib|A hivatkozott könyvtár, amikor az RMS SDK 2.1 használatával állítanak össze x86-alkalmazásokat.|
|Msipc_s.lib|\lib|Egy belépési pontot nyújt az [<strong>IpcInitialize</strong>](/rights-management/sdk/2.1/api/win/functions#msipc_ipcinitialize) használatához az x86-alkalmazások esetén.|
|Msipc.lib|\lib\x64|A hivatkozott könyvtár, amikor az RMS SDK 2.1 használatával állítanak össze x64-alkalmazásokat.|
|Msipc_s.lib|\lib\x64|Egy belépési pontot nyújt az [<strong>IpcInitialize</strong>](/rights-management/sdk/2.1/api/win/functions#msipc_ipcinitialize) használatához az x64-alkalmazások esetén.|
|Genmanifest.exe|\tools|Az RMS-kompatibilis alkalmazások fejlesztése során a jegyzékfájl létrehozására szolgál.|
 

 

 



<!--HONumber=Aug16_HO4-->


