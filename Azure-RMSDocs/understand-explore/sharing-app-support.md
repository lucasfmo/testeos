---
title: "RMS megosztóalkalmazás Windows rendszerhez és mobil platformokhoz | Azure RMS"
description: "Az RMS megosztóalkalmazás egy ingyenes, letölthető alkalmazás, amely az Office 2010 támogatásához szükséges, de a használata ajánlott Windows rendszerű számítógépek, Mac számítógépek és mobileszközök esetén is. Az egyik előnye, hogy általános védelemmel láthat el olyan alkalmazásokat és fájlokat, amelyek nem támogatják natív módon a Rights Management szolgáltatást, ami azt jelenti, hogy minden fájl ellátható védelemmel."
author: cabailey
manager: mbaldwin
ms.date: 08/24/2016
ms.topic: article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 1da6e372-2b3f-4af7-80f7-6b9073dff7f5
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 024a29d7c7db2e4c0578a95c93e22f8e7a5b173e
ms.openlocfilehash: 6304c5c29e2dab176fb9d5a617e1467af00ab504


---


# RMS-megosztóalkalmazás Windows és mobil platformokra

>*A következőkre vonatkozik: Azure Rights Management, Office 365*

Az RMS megosztóalkalmazás egy ingyenes, letölthető alkalmazás, amely az Office 2010 támogatásához szükséges, de a használata ajánlott Windows rendszerű számítógépek, Mac számítógépek és mobileszközök esetén is. Az egyik előnye, hogy általános védelemmel láthat el olyan alkalmazásokat és fájlokat, amelyek nem támogatják natív módon a [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] szolgáltatást, ami azt jelenti, hogy minden fájl ellátható védelemmel. A különböző védelmi szintekről a [Rights Management megosztóalkalmazás rendszergazdai kézikönyvének](../rms-client/sharing-app-admin-guide.md) [Védelmi szintek – natív és általános](../rms-client/sharing-app-admin-guide-technical.md#levels-of-protection-native-and-generic) című szakaszában talál további információt.

Ha a felhasználók az RMS megosztóalkalmazás használatával látják el védelemmel a fájlokat, nyomon követhetik a védett fájlokat, és ha szükséges, visszavonhatják a fájlokhoz való hozzáférést. Ezt a [dokumentumkövetési webhely](http://go.microsoft.com/fwlink/?LinkId=529562) segítségével tehetik meg.

Windows rendszerű számítógépek esetén az RMS megosztóalkalmazás a háttérben integrálja magát a felhasználók által már használt alkalmazásokba, és javítja azok működését:

-   Egy Office-bővítmény a Word, Excel, PowerPoint és Outlook számára. A bővítmény a **Védett megosztás** gombot helyezi el a menüszalagra, amellyel egy egyszerűen használható párbeszédpanel nyitható meg az e-mailben elküldeni kívánt fájlok védelemmel való ellátásához a leggyakrabban használt beállítások használatával. A gomb a dokumentumkövetési webhely gyors elérését is lehetővé teszi.

-   Új elem a Fájlkezelő helyi menüjében. A menüelem a **Helyi védelem** lehetőség, amellyel egy egyszerűen használható párbeszédpanel nyitható meg a lemezen tárolni kívánt fájlok védelemmel való ellátásához a leggyakrabban használt beállítások használatával.

-   Egy megjelenítő azon fájlok megnyitásához, amelyek a [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] használatával lettek ellátva védelemmel. Ez a megjelenítő automatikusan megnyílik, ha nem lett más olyan alkalmazás telepítve, amely meg tudná nyitni a védett fájlt.

-   Háttérkonfiguráció Office 2010-hez, amely lehetővé teszi a csomagban található Word, Excel, PowerPoint és Outlook számára, hogy zökkenőmentesen működjön együtt az [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] szolgáltatással.

Jóllehet a Windows rendszerhez készült RMS megosztóalkalmazás egyetlen számítógép számára tölthető le és telepíthető a [Microsoft Rights Management lap](http://go.microsoft.com/fwlink/?LinkId=303970) segítségével, az alkalmazás támogatja a csendes telepítést és egyéni konfigurálást vállalati üzembe helyezés esetén is. További információkért lásd a következőket:

-   [Rendszergazdai útmutató a Rights Management megosztóalkalmazáshoz](../rms-client/sharing-app-admin-guide.md)

-   [A Rights Management megosztóalkalmazás felhasználói útmutatója](../rms-client/sharing-app-user-guide.md)

A mobileszközökhöz készült RMS megosztóalkalmazás a leggyakrabban használt mobileszközöket támogatja, ilyenek például az iPad és iPhone készülékek, valamint az Android, Windows Phone és Windows RT rendszerű készülékek. A felhasználók a megfelelő áruházból tölthetik le az alkalmazást, illetve a [Microsoft Rights Management lap](http://go.microsoft.com/fwlink/?LinkId=303970) is biztosít a kapcsolódó alkalmazásra mutató hivatkozást.

**Ha rendelkezik a Microsoft Intune-nal**: Mivel az RMS megosztóalkalmazás tartalmazza a Microsoft Intune App Software Development Kitet, az alábbi lehetőségek állnak a rendelkezésére:

-   Az Intune által regisztrált iOS- és Android-eszközökhöz készült alkalmazás üzembe helyezése és kezelése.

-   Az Intune által nem regisztrált Android-eszközökhöz készült alkalmazás kezelése.


## További lépések
Információk az egyéb alkalmazások és szolgáltatások Azure Rights Management-támogatásáról: [Hogyan támogatják a különböző alkalmazások az Azure Rights Managementet?](applications-support.md)




<!--HONumber=Aug16_HO4-->


