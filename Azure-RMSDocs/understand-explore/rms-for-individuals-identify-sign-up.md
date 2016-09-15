---
title: "Annak ellenőrzése, hogy a felhasználók regisztráltak-e az RMS egyéni felhasználók számára szolgáltatásra | Azure RMS"
description: "Honnan tudhatja meg rendszergazdaként, hogy a felhasználók regisztráltak-e az RMS egyéni felhasználók számára szolgáltatásra? Az itt leírt módszereket egyesével vagy akár egymással kombinálva is felhasználhatja."
author: cabailey
manager: mbaldwin
ms.date: 08/25/2016
ms.topic: article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: a36c3d99-a794-4f7a-aafb-64a950f1fcf9
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 43429b44c019144744f39a1f92f144d315c2024c
ms.openlocfilehash: fb9331686f5b04ba7aea8653c412127fd6913033


---


# Annak ellenőrzése, hogy a felhasználók regisztráltak-e az RMS egyéni felhasználók számára szolgáltatásra

>*A következőkre vonatkozik: Azure Rights Management*

Honnan tudhatja meg rendszergazdaként, hogy a felhasználók regisztráltak-e az RMS egyéni felhasználók számára szolgáltatásra? Az alábbi módszerek bármelyikét használhatja, vagy kombinálhatja is őket:

-   Kérdezze meg a felhasználókat, hogy milyen módszerrel védik a fokozottan bizalmas fájlokat, különösen akkor, ha szervezeten kívüli személyekkel dolgoznak együtt.

-   Ha a szervezete rendelkezik Azure-előfizetéssel, a [Get-MsolAccountSku](https://msdn.microsoft.com/library/azure/dn194118.aspx) parancsmag használatával ellenőrizheti, hogy a **RIGHTSMANAGEMENT_ADHOC** szerepel-e a visszaadott előfizetések között. Ha igen, akkor az az RMS egyéni felhasználók számára előfizetés, amelyet a szervezet kapott. Ez tartalmazza a felhasználók számára elérhető aktív egységek készletét, amelyet az önkiszolgáló bejelentkezési folyamathoz használhatnak.

-   A telepített és használatban lévő szoftverek leltározásához használjon egy rendszerkezelési megoldást, például a System Center Configuration Managert. A Rights Management megosztóalkalmazás az **ipviewer.exe** program használatával fut. Az alkalmazás egyéb jellemzőinek azonosítására ingyenesen [letöltheti és telepítheti](http://go.microsoft.com/fwlink/?LinkId=303970) az alkalmazást, amelyet ezután a szoftverek leltározásához használhat.

-   Keressen olyan fájlnévkiterjesztéseket, amelyeket a Rights Management megosztóalkalmazás hozott létre. A .pfile és a .ppdf fájlnévkiterjesztések a legnyilvánvalóbb példák, de vannak más fájlok is, amelyek megváltoztatják a fájlnévkiterjesztésüket, amikor a Rights Management natív védelemmel látja el őket. További információkat a [Rights Management megosztóalkalmazás rendszergazdai útmutatójának](http://technet.microsoft.com/library/dn339003.aspx) [Támogatott fájltípusok és fájlnévkiterjesztések](../rms-client/sharing-app-admin-guide-technical.md#supported-file-types-and-file-name-extensions) című szakaszában találhat.




<!--HONumber=Aug16_HO4-->


