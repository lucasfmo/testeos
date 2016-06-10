---
# required metadata

title: Fejlesztői útmutató | Azure RMS
description: A fejlesztői eszközök használatának áttekintse; SDK-k, további könyvtárak és kódpéldák.
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: a22e6bd0-8ce8-45b4-9a32-273126ab831e
# optional metadata

#ROBOTS:
audience: developer
#ms.devlang:
ms.reviewer: shubhamp
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Fejlesztői útmutató

## Áttekintés ##
Ez az útmutató ismerteti Rights Management SDK-ink csomagját, illetve az eszközök és mintakódok folyton növekvő halmazát, amely minden támogatott platformra kiterjed. 

## Szoftverfejlesztői készletek ##
Jelenleg az RMS SDK három generációja érhető el, ezek megtekinthetők az alábbi táblázatban.

| SDK | Leírás |
|------|---------|
| [RMS SDK 4.2](active-directory-rights-management-services-multi-platform-thin-client-sdk-portal.md) | Egyszerűsített, új generációs eszközkészlet, amellyel könnyedén építhet be adatvédelmet Android-, iOS-, Mac OS X-, Windows Phone-/RT- és Linux-/C++-eszközalkalmazásaiba a Microsoft Rights Management szolgáltatások segítségével. |
| [RMS SDK 2.1](microsoft-information-protection-and-control-client-portal.md) | Hatékony SDK, amelynek köszönhetően a Windows asztali alkalmazások fejlesztői és a kiszolgálóalapú megoldások szolgáltatói tartalomvédelemmel láthatják el a termékeiket.|
|[AD RMS SDK](https://msdn.microsoft.com/en-us/library/cc530379(v=vs.85).aspx)|** MEGJEGYZÉS ** – Az AD RMS SDK az ügyfélprogram által az Msdrm.dll fájlban biztosított, és Windows Server 2012, Windows 8, Windows Server 2008 R2, Windows 7, Windows Server 2008 és Windows Vista rendszerben használható funkciók előnyeit használja ki. A későbbi verziókban előfordulhat, hogy ezek a funkciók módosított formában vagy egyáltalán nem lesznek elérhetők. Ezért használja inkább a Microsoft Rights Management Services SDK 2.1-es verzióját, amely az ügyfélprogram által az Msipc.dll fájlban közzétett funkciók használatán alapul.|
|[AD RMS parancsfájlkezelési API](https://msdn.microsoft.com/en-us/library/bb968797(v=vs.85).aspx)| Az AD RMS-telepítések felügyeletére szolgáló parancsfájlok létrehozására használható.|

## Kódminták és eszközök
A Microsoft által biztosított alábbi RMS-kódminták és fejlesztői támogatási eszközök az összes támogatott operációs rendszert, így az Android, iOS/OS X, Windows Phone és az asztali számítógépekhez készült Windows rendszert is lefedik, és rendszeresen frissülnek a támogatott SDK-kal való kompatibilitás megőrzése érdekében.

### Android

A következő az [RMS SDK 4.2](active-directory-rights-management-services-multi-platform-thin-client-sdk-portal.md) és a 4.x-es SDK későbbi verziói által támogatott Android rendszeren fut.

- [A felhasználói felületi kódtár és mintaalkalmazás](https://github.com/AzureAD/rms-sdk-ui-for-android) a GitHub webhelyen, amelyek segítségével gyorsan végrehajthatja az első lépéseket, és újra felhasználhatja szabványos felhasználói felületünket az alkalmazásokban.
- A Java nyelven készült [androidos használati forgatókönyvek](https://msdn.microsoft.com/en-us/library/dn758246(v=vs.85).aspx) fontos fejlesztési forgatókönyvek bemutatásával nyújtanak segítséget az RMS SDK használatának a megismeréséhez. A minták kitérnek a Microsoft védett fájlformátumának, az egyéni védett fájlformátumok és az egyéni felhasználói felületi vezérlők használatára.

### iOS/OS X

A következő az [RMS SDK 4.2](active-directory-rights-management-services-multi-platform-thin-client-sdk-portal.md) és a 4.x-es SDK későbbi verziói által támogatott iOS / OS X rendszereken fut.

- Az Objective C-ben készült [iOS/OS X használati forgatókönyvek](https://msdn.microsoft.com/en-us/library/dn758307(v=vs.85).aspx) fontos fejlesztési forgatókönyvek bemutatásával nyújtanak segítséget az RMS SDK használatának a megismeréséhez. A minták kitérnek a Microsoft védett fájlformátumának, az egyéni védett fájlformátumok és az egyéni felhasználói felületi vezérlők használatára.
- [A felhasználói felületi kódtár és mintaalkalmazás](https://github.com/AzureAD/rms-sdk-ui-for-ios) a GitHub webhelyen, amelyek segítségével gyorsan végrehajthatja az első lépéseket, és újra felhasználhatja szabványos felhasználói felületünket az alkalmazásokban. **Csak iOS** rendszeren támogatott.

### Windows asztali rendszer

A következő az [RMS SDK 2.1](microsoft-information-protection-and-control-client-portal.md) és a 2.x-es SDK későbbi verziói által támogatott Windows Desktop rendszeren fut.

- A [PFILE-védett PDF elolvasása](https://blogs.msdn.microsoft.com/rms/2015/11/09/reading-a-pfile-protected-pdf/) az RMS Developer's Corner blogban elérhető egyszerű kódminta, amely az MSIPC File API használatával fejti vissza és nyitja meg a PFILE által védett PDF-dokumentumokat.
- Az [IpcManagedAPI](https://github.com/Azure-Samples/active-directory-dotnet-rms) az RMS SDK 2.1-es verziójának a .NET (C#) keretrendszerben használható formája, amely egyszerűbbé teszi a felügyelt alkalmazás RMS-kompatibilissá tételét.
- Az [IPCNotepad](https://code.msdn.microsoft.com/ipcnotepad-sample-f67dae80) egy RMS-kompatibilis mintaalkalmazás, amely végigvezeti azokon a lépéseken, amelyeket az egyes RMS-kompatibilis alkalmazásoknak végre kell hajtania, amikor korlátozott tartalmakat használnak vagy a védelmükről gondoskodnak.
- Az [IpcDlp](https://github.com/Azure-Samples/active-directory-dotnet-rms) egy RMS-kompatibilis adatszivárgás-megelőzési (DLP) mintaalkalmazás, amely végigvezeti azokon a lépéseken, amelyeket az RMS-kompatibilis DLP-alkalmazásoknak végre kell hajtania a File API használatával, amikor korlátozott tartalmakat használnak vagy a védelmükről gondoskodnak.
- Az [IpcAzureApp](https://github.com/Azure-Samples/active-directory-dotnet-rms) minta azt mutatja be, hogyan használható az RMS SDK az Azure-alkalmazásokban az Azure Blob Storage-ban található adatok védelmének biztosítására.
- Az [RmsDocumentInspector](https://github.com/Azure-Samples/active-directory-dotnet-rms) eszköz az RMS-sel védett fájlokra vonatkozó különböző adatokat, például tartalomazonosítót vagy felhasználói jogosultságokat adhat meg.
- Az [RmsFileWatcher](https://github.com/Azure-Samples/active-directory-dotnet-rms) minta bemutatja, hogyan hozható létre olyan Windows-alkalmazás, amely a fájlrendszer könyvtárait figyeli, és az RMS-védelem házirendjeit alkalmazza minden változás, például fájlok hozzáadása vagy módosítása esetén.

### Windows Áruház és Phone

- [Felhasználói felületi kódtár Windows Áruházhoz](https://github.com/AzureAD/rms-sdk-ui-for-windowsstore) – Egy felhasználói felületi kódtár a Microsoft RMS SDK v4.1-es verziójához a Windows Áruházbeli alkalmazásokhoz. Ez egy választható kódtár, és a fejlesztők dönthetnek úgy, hogy saját felhasználói felületet hoznak létre a Microsoft RMS SDK v4.1 használatakor

- [Felhasználói felületi kódtár Windows Phone eszközökhöz](https://github.com/AzureAD/rms-sdk-ui-for-winphone) – Egy felhasználói felületi kódtár a Microsoft RMS SDK v4.1-es verziójához Windows Phone alkalmazásokhoz. Ez egy választható kódtár, és a fejlesztők dönthetnek úgy, hogy saját felhasználói felületet hoznak létre a Microsoft RMS SDK v4.1 használatakor

- [Mintaalkalmazás](https://github.com/Azure-Samples/active-directory-dotnet-rms-windowsstore) – A minta a Windows Áruházbeli alkalmazásokhoz kapcsolódó Microsoft RMS SDK v4.1-es verziójához mutat be alapszintű dokumentumfelhasználási példát a platformhoz.


<!--HONumber=Apr16_HO4-->


