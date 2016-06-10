---
# required metadata

title: Rights Management megosztóalkalmazás&colon; Telepítés és konfigurálás ügyfelek esetén | Azure RMS
description:
keywords:
author: cabailey
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: b9af5dc3-73d4-4147-b7ef-f6803b0d5216

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: esaggese
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Rights Management megosztóalkalmazás: Telepítés és konfigurálás ügyfelek esetén

*A következőkre vonatkozik: Azure Rights Management, Office 365*

A Rights Management (RMS) megosztóalkalmazás az Office 2010-zel rendelkező Azure RMS-t használó ügyfélszámítógépek számára szükséges, és javasolt az összes olyan számítógépen és mobileszközözön, amely az Azure RMS szolgáltatást támogatja. Az RMS megosztóalkalmazás az Office alkalmazásokba integrálható egy Office bővítmény telepítésével, hogy a felhasználók könnyedén védhessék meg a fájlokat és e-maileket közvetlenül a szalagról. Általános védelmet nyújt olyan fájltípusokhoz is, amelyeket az Azure RMS nem támogat natív módon, valamint egy dokumentumkövető webhelyet biztosít a felhasználók számára, amelyen követhetik és visszavonhatják a védett fájlokat.

## A Windows RMS-megosztóalkalmazása: Telepítés és konfigurálás
Ha az RMS megosztóalkalmazást vállalati üzembe helyezéshez szeretné telepíteni és konfigurálni a Windows rendszeren, lásd: [Rendszergazdai útmutató a Rights Management megosztóalkalmazáshoz](../rms-client/sharing-app-admin-guide.md).

> [!TIP]
> Ha gyorsan szeretné telepíteni és tesztelni az RMS megosztóalkalmazást egyetlen számítógéphez, tekintse meg [A Rights Management megosztóalkalmazás letöltése és telepítése](../rms-client/install-sharing-app.md) témakört [A Rights Management megosztóalkalmazás felhasználói útmutatójában](../rms-client/sharing-app-user-guide.md).

## Az RMS megosztóalkalmazás mobil platformokhoz: Telepítés és felügyelet
Ha az RMS megosztóalkalmazást mobil platformokhoz szeretné telepíteni, töltse le a megfelelő alkalmazást a [Microsoft Rights Management oldalon](http://go.microsoft.com/fwlink/?LinkId=303970) található hivatkozások használatával. Nincs szükség konfigurálásra, ha az Azure RMS alkalmazást ezzel az alkalmazással szeretné használni.

**Ha rendelkezik a Microsoft Intune-nal**: Mivel az RMS megosztóalkalmazás tartalmazza a Microsoft Intune App szoftverfejlesztői készletet, a következő lehetőségei vannak:

-   Az Intune által regisztrált eszközök esetén üzembe helyezheti és felügyelheti az RMS megosztóalkalmazásokat az iOS és Android rendszereket futtató eszközökhöz. További információkért lásd: [Mobilalkalmazás-felügyeleti házirendek konfigurálása és telepítése a Microsoft Intune-konzolon](/intune/deploy-use/configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console) az Intune dokumentációban. A 2. lépéshez használja a házirend által kezelt alkalmazás közzétételének utasításait.

-   A nem az Intune által regisztrált eszközök esetén felügyelheti az RMS megosztóalkalmazásokat az Android rendszereket futtató eszközökhöz. További információkért lásd: [Mobilalkalmazás-felügyeleti szabályzatok létrehozása és telepítése Microsoft Intune-ban](/intune/deploy-use/create-and-deploy-mobile-app-management-policies-with-microsoft-intune).



<!--HONumber=Apr16_HO4-->


