---
# required metadata

title: RMS fejlesztői útmutató | Azure RMS
description: Jelenleg a Rights Management SDK három generációja érhető el.
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 0510ead4-2fe7-4269-885b-fe16bcc69888
# optional metadata

#ROBOTS:
audience: developer
#ms.devlang:
ms.reviewer: shubhamp
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# RMS fejlesztői útmutató

## Áttekintés ##
Jelenleg a Rights Management SDK három generációja érhető el: az Android és iOS/OS X operációs rendszerhez, Windows rendszerű eszközökhöz és a Linux operációs rendszerhez készült **Microsoft Rights Management SDK 4.2**, a Windows asztali ügyfélalkalmazáshoz készült **Microsoft Rights Management SDK 2.1**, valamint az újabb verziók által felváltott **AD RMS SDK**.

## Szoftverfejlesztői készletek ##
| SDK | Leírás |
|------|---------|
| [RMS SDK 4.2](active-directory-rights-management-services-multi-platform-thin-client-sdk-portal.md) | Egyszerűsített, új generációs eszközkészlet, amellyel könnyedén építhet be adatvédelmet Android-, iOS-, Mac OS X-, Windows Phone-/RT- és Linux-/C++-eszközalkalmazásaiba a Microsoft Rights Management szolgáltatások segítségével. |
| [RMS SDK 2.1](microsoft-information-protection-and-control-client-portal.md) | Hatékony SDK, amelynek köszönhetően a Windows asztali alkalmazások fejlesztői és a kiszolgálóalapú megoldások szolgáltatói tartalomvédelemmel láthatják el a termékeiket.|
|[AD RMS SDK]()|** MEGJEGYZÉS ** – Az AD RMS SDK az ügyfélprogram által az Msdrm.dll fájlban biztosított, és Windows Server 2012, Windows 8, Windows Server 2008 R2, Windows 7, Windows Server 2008 és Windows Vista rendszerben használható funkciók előnyeit használja ki. A későbbi verziókban előfordulhat, hogy ezek a funkciók módosított formában vagy egyáltalán nem lesznek elérhetők. Ezért használja inkább a Microsoft Rights Management Services SDK 2.1-es verzióját, amely az ügyfélprogram által az Msipc.dll fájlban közzétett funkciók használatán alapul.|
|[AD RMS parancsfájlkezelési API]()| Az AD RMS-telepítések felügyeletére szolgáló parancsfájlok létrehozására használható.|

## Kódminták és eszközök ##
A Microsoft által biztosított alábbi RMS-kódminták és fejlesztői támogatási eszközök az összes támogatott operációs rendszert, így az Android, iOS/OS X, Windows Phone és az asztali számítógépekhez készült Windows rendszert is lefedik, és rendszeresen frissülnek a támogatott SDK-kal való kompatibilitás megőrzése érdekében.

| Elem | Operációs rendszer | Támogatást biztosító SDK-verzió | Leírás |
|------|------------------|------------------------|-------------|
| [PFILE-védett PDF elolvasása](https://blogs.msdn.microsoft.com/rms/2015/11/09/reading-a-pfile-protected-pdf/) | Windows asztali rendszer| [RMS SDK 2.1](microsoft-information-protection-and-control-client-portal.md) és a 2.x-es SDK későbbi verziói | A **PFILE-védett PDF elolvasása** az RMS Developer's Corner blogban elérhető egyszerű kódminta, amely az MSIPC File API használatával fejti vissza és nyitja meg a PFILE által védett PDF-dokumentumokat.|
| [IpcManagedAPI](https://github.com/Azure-Samples/active-directory-dotnet-rms) | Windows asztali rendszer | [RMS SDK 2.1](microsoft-information-protection-and-control-client-portal.md) és a 2.x-es SDK későbbi verziói | Az **IpcManagedAPI** az RMS SDK 2.1-es verziójának a .NET (C#) keretrendszerben használható formája, amely egyszerűbbé teszi a felügyelt alkalmazás RMS-kompatibilissá tételét.|
| [IPCNotepad](https://code.msdn.microsoft.com/ipcnotepad-sample-f67dae80) | Windows asztali rendszer | [RMS SDK 2.1](microsoft-information-protection-and-control-client-portal.md) és a 2.x-es SDK későbbi verziói| Az **IPCNotepad** egy RMS-kompatibilis mintaalkalmazás, amely végigvezeti azokon a lépéseken, amelyeket az egyes RMS-kompatibilis alkalmazásoknak végre kell hajtania, amikor korlátozott tartalmakat használnak vagy a védelmükről gondoskodnak.|
| [IpcDlp](https://github.com/Azure-Samples/active-directory-dotnet-rms)|Windows asztali rendszer|[RMS SDK 2.1](microsoft-information-protection-and-control-client-portal.md) és a 2.x-es SDK későbbi verziói|Az **IpcDlp** egy RMS-kompatibilis adatszivárgás-megelőzési (DLP) mintaalkalmazás, amely végigvezeti azokon a lépéseken, amelyeket az RMS-kompatibilis DLP-alkalmazásoknak végre kell hajtania a File API használatával, amikor korlátozott tartalmakat használnak vagy a védelmükről gondoskodnak.|
| [IpcAzureApp](https://github.com/Azure-Samples/active-directory-dotnet-rms) | Windows asztali rendszer|[RMS SDK 2.1](microsoft-information-protection-and-control-client-portal.md) és a 2.x-es SDK későbbi verziói|Az **IpcAzureApp** minta azt mutatja be, hogyan használható az RMS SDK az Azure-alkalmazásokban az Azure Blob Storage-ban található adatok védelmének biztosítására.|
| [RmsDocumentInspector](https://github.com/Azure-Samples/active-directory-dotnet-rms) | Windows asztali rendszer|[RMS SDK 2.1](microsoft-information-protection-and-control-client-portal.md) és a 2.x-es SDK későbbi verziói|Az **RmsDocumentInspector** eszköz az RMS-sel védett fájlokra vonatkozó különböző adatokat, például tartalomazonosítót vagy felhasználói jogosultságokat adhat meg.|
| [RmsFileWatcher](https://github.com/Azure-Samples/active-directory-dotnet-rms) | Windows asztali rendszer|[RMS SDK 2.1](microsoft-information-protection-and-control-client-portal.md) és a 2.x-es SDK későbbi verziói|Az **RmsFileWatcher** minta bemutatja, hogyan hozható létre olyan Windows-alkalmazás, amely a fájlrendszer könyvtárait figyeli, és az RMS-védelem házirendjeit alkalmazza minden változás, például fájlok hozzáadása vagy módosítása esetén.|
| [iOS/OS X használati forgatókönyvek](https://msdn.microsoft.com/en-us/library/dn758307(v=vs.85).aspx) |iOS/OS X|[RMS SDK 4.2](active-directory-rights-management-services-multi-platform-thin-client-sdk-portal.md) és a 4.x-es SDK későbbi verziói|Az **Objective C**-kódminták fontos fejlesztési forgatókönyvek bemutatásával nyújtanak segítséget az RMS SDK használatának a megismeréséhez. A minták kitérnek a Microsoft védett fájlformátumának, az egyéni védett fájlformátumok és az egyéni felhasználói felületi vezérlők használatára.|
| [Felhasználói felületi kódtár és mintaalkalmazás](https://github.com/AzureAD/rms-sdk-ui-for-ios) |iOS|[RMS SDK 4.2](active-directory-rights-management-services-multi-platform-thin-client-sdk-portal.md) és a 4.x-es SDK későbbi verziói|**Az iOS rendszer számára készült felhasználói felületi kódtárak és mintaalkalmazás** a GitHub webhelyen, amelynek a segítségével gyorsan végrehajthatja az első lépéseket, és újra felhasználhatja szabványos felhasználói felületünket az alkalmazásokban.|
| [Felhasználói felületi kódtár és mintaalkalmazás](https://github.com/AzureAD/rms-sdk-ui-for-android) |Android|[RMS SDK 4.2](active-directory-rights-management-services-multi-platform-thin-client-sdk-portal.md) és a 4.x-es SDK későbbi verziói|**Az Android rendszer számára készült felhasználói felületi kódtárak és mintaalkalmazás** a GitHub webhelyen, amelynek a segítségével gyorsan végrehajthatja az első lépéseket, és újra felhasználhatja szabványos felhasználói felületünket az alkalmazásokban.|
| [Android használati forgatókönyvek](https://msdn.microsoft.com/en-us/library/dn758246(v=vs.85).aspx) |Android|[RMS SDK 4.2](active-directory-rights-management-services-multi-platform-thin-client-sdk-portal.md) és a 4.x-es SDK későbbi verziói|A **Java-kódminták** fontos fejlesztési forgatókönyvek bemutatásával nyújtanak segítséget az RMS SDK használatának a megismeréséhez. A minták kitérnek a Microsoft védett fájlformátumának, az egyéni védett fájlformátumok és az egyéni felhasználói felületi vezérlők használatára.|


<!--HONumber=Apr16_HO4-->


