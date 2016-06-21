---
# required metadata

title: A Visual Studio konfigurálása | Azure RMS
description: Visual Studio projekteknek az RMS SDK 2.1 használatára való konfigurálására vonatkozó utasítások.
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 396A2C19-3A00-4E9A-9088-198A48B15289
# optional metadata

#ROBOTS:
audience: developer
#ms.devlang:
ms.reviewer: shubhamp
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# A Visual Studio konfigurálása

Ez a témakör a Visual Studio-projekteknek a Rights Management Services SDK 2.1 használatára való konfigurálásával kapcsolatos utasításokat tartalmaz.

## Előfeltételek

-   [Az SDK telepítése](install-the-rms-sdk.md)

**Utasítások**

### 1. lépés: A Visual Studio-projekt konfigurálása az RMS SDK 2.1 használatára

Ezek az utasítások a Microsoft Visual Studio 2010-re vonatkoznak. Ha a Microsoft Visual Studio egy másik verzióját használja, akkor a beállítási párbeszédpanelek megjelenése eltérő lehet.

Ezek az utasítások natív 32 bites alkalmazások összeállítására vonatkoznak.

1.  Adja hozzá az RMS SDK 2.1-es verzióját is magában foglaló könyvtárat a Visual Studio 2010-projekthez.

    A **Configuration Properties** (Konfigurációs tulajdonságok) menüben válassza a **VC++ Directories** (VC++ könyvtárak) lehetőséget, és adja hozzá az RMS SDK 2.1-es verzióját tartalmazó **$(MSIPCSDKDIR)\\inc** könyvtárat az **Include Directories** (Belefoglalt könyvárak) mezőhöz.

    ![A Configuration Properties (Konfigurációs tulajdonságok) menü Include directories (Belefoglalt könyvárak) mezője](../media/include_directories.png)

2.  Adja az RMS SDK 2.1 könyvtárat a Visual Studio 2010-projekthez.

    A **Configuration Properties** (Konfigurációs tulajdonságok) menüben válassza a **VC++ Directories** (VC++ könyvtárak) lehetőséget, és adja hozzá az RMS SDK 2.1 könyvtárat a platformhoz tartozó **Library Directories** (Könyvtárak) mezőhöz.

    -   Win32 esetén használja a következőt: **$(MSIPCSDKDIR)\\lib**
    -   x64 esetén használja a következőt: **$(MSIPCSDKDIR)\\lib\\x64**

    ![A Configuration Properties (Konfigurációs tulajdonságok) menü Library directories (Könyvtárak) mezője](../media/library_directories.png)

3.  Adja hozzá az RMS SDK 2.1 könyvtárban lévő fájlokat Visual Studio 2010-függőségekként.

    A **Linker** (Kötéskészítő) mezőben válassza az **Input** (Bevitel) lehetőséget, és adja hozzá az RMS SDK 2.1 könyvtárban lévő fájlokat, valamint az **Msipc.lib** és az **Msipc\_s.lib** fájlt az **Additional Dependencies** (További függőségek) mezőhöz.

    ![A Linker (Kötéskészítő) könyvtár Dependencies (Függőségek) mezője](../media/additional_dependencies.png)

4.  Adja hozzá az RMS SDK 2.1 dinamikus csatolású kódtárat (DLL-t) késleltetett betöltésű DLL-ként.

    A **Linker** (Kötéskészítő) menőben válassza az **Input** (Bevitel) lehetőséget, és adja hozzá az **Msipc.dll** RMS SDK 2.1 DLL-fájlt a **Delay Loaded Dlls** (Késleltetett betöltésű DLL-fájlok) mezőhöz.

    ![A Linker (Kötéskészítő) könyvtár Delay Loaded Dlls (Késleltetett betöltésű DLL-fájlok) mezője](../media/delay_loaded.png)

5.  Hozzon létre verzióinformációkat az eredményül létrejött bináris fájl számára.

    A **Solution Explorer** (Megoldáskezelő) felületén válassza a **Resource Files** (Erőforrásfájlok) lehetőséget, és adja hozzá a bináris fájl nevét az **OriginalFileName** (Eredeti fájlnév) mezőhöz.

    ![A Solution Explorer (Megoldáskezelő) Resource Files (Erőforrásfájlok) mezője](../media/original_file_name.png)

## Kapcsolódó témakörök

* [Az SDK telepítése](install-the-rms-sdk.md)
 

 


<!--HONumber=Jun16_HO2-->


