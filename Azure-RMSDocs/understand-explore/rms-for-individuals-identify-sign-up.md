---
# required metadata

title: Annak ellenőrzése, hogy a felhasználók regisztráltak-e az RMS egyéni felhasználók számára szolgáltatásra | Azure RMS
description:
keywords:
author: cabailey
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: a36c3d99-a794-4f7a-aafb-64a950f1fcf9

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: esaggese
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---


# Annak ellenőrzése, hogy a felhasználók regisztráltak-e az RMS egyéni felhasználók számára szolgáltatásra

*A következőkre vonatkozik: Azure Rights Management*

Honnan tudhatja meg rendszergazdaként, hogy a felhasználók regisztráltak-e az RMS egyéni felhasználók számára szolgáltatásra? Az alábbi módszerek bármelyikét használhatja, vagy kombinálhatja is őket:

-   Kérdezze meg a felhasználókat, hogy milyen módszerrel védik a fokozottan bizalmas fájlokat, különösen akkor, ha szervezeten kívüli személyekkel dolgoznak együtt.

-   Ha a szervezete rendelkezik Azure-előfizetéssel, a [Get-MsolAccountSku](https://msdn.microsoft.com/library/azure/dn194118.aspx) parancsmag használatával ellenőrizheti, hogy a **RIGHTSMANAGEMENT_ADHOC** szerepel-e a visszaadott előfizetések között. Ha igen, akkor az az RMS egyéni felhasználók számára előfizetés, amelyet a szervezet kapott. Ez tartalmazza a felhasználók számára elérhető aktív egységek készletét, amelyet az önkiszolgáló bejelentkezési folyamathoz használhatnak.

-   A telepített és használatban lévő szoftverek leltározásához használjon egy rendszerkezelési megoldást, például a System Center Configuration Managert. A Rights Management megosztóalkalmazás az **ipviewer.exe** program használatával fut. Az alkalmazás egyéb jellemzőinek azonosítására ingyenesen [letöltheti és telepítheti](http://go.microsoft.com/fwlink/?LinkId=303970) az alkalmazást, amelyet ezután a szoftverek leltározásához használhat.

-   Keressen olyan fájlnévkiterjesztéseket, amelyeket a Rights Management megosztóalkalmazás hozott létre. A .pfile és a .ppdf fájlnévkiterjesztések a legnyilvánvalóbb példák, de vannak más fájlok is, amelyek megváltoztatják a fájlnévkiterjesztésüket, amikor a Rights Management natív védelemmel látja el őket. További információkat a [Rights Management megosztóalkalmazás rendszergazdai útmutatójának](http://technet.microsoft.com/library/dn339003.aspx) [Támogatott fájltípusok és fájlnévkiterjesztések](../rms-client/sharing-app-admin-guide-technical.md#supported-file-types-and-file-name-extensions) című szakaszában találhat.



<!--HONumber=Apr16_HO4-->


