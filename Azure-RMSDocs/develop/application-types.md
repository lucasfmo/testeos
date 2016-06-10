---
# required metadata

title: Alkalmazástípusok | Azure RMS
description: Ez a témakör azokat az alkalmazástípusokat ismerteti, amelyeket létre lehet hozni tartalomvédelemmel kompatibilisként.
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 97169FC3-1395-4433-A632-7B0F020FABFE
# optional metadata

#ROBOTS:
audience: developer
#ms.devlang:
ms.reviewer: shubhamp
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Alkalmazástípusok


Ez a témakör azokat az alkalmazástípusokat ismerteti, amelyeket létre lehet hozni tartalomvédelemmel kompatibilisként.

A Rights Management Services SDK 2.1 jelenleg az alábbi alkalmazástípusokat támogatja

## Egyszerű alkalmazások

Egyszerű alkalmazás lehet egy fájltitkosításra használt, parancssori eszköz is. Egy egyszerű, tartalomvédelemmel kompatibilis alkalmazásra mintát a következő témakörben tekinthet meg: [IPCHelloWorld – mintaalkalmazás](how-to-build-your-first-application.md).

### Kiszolgáló üzemmódhoz készült alkalmazások


A *kiszolgáló üzemmód* olyan nem interaktív alkalmazások számára lett kifejlesztve, amelyek RMS-védelemmel ellátott tartalmak kezelését, védelemmel történő ellátását és feldolgozását végzik. Jellemző példa erre egy *adatveszteség-megelőzési* alkalmazás, amely szolgáltatásként fut egy fájlkiszolgálón, és automatikusan védelemmel látja el az érzékeny dokumentumokat. Példa erre az alkalmazástípusra: [IpcDlp mintaalkalmazás](https://Code.MSDN.Microsoft.Com/IpcDlp-Sample-Application-d30bb99d).

Ha az alkalmazása *kiszolgáló üzemmódot* használ, annak RMS-kiszolgálón történő hitelesítése beavatkozás nélkül történik meg. Az *ügyfél üzemmódtól* eltérően a beavatkozás nélküli hitelesítés sikertelensége esetén az RMS SDK 2.1 nem nyit meg hitelesítőadat-kérést. A *kiszolgáló üzemmódban* történő futtatáskor nincs szükség alkalmazásjegyzékre.

További információk az API biztonsági mód beállításáról: [Setting the API security mode](setting-the-api-security-mode-api-mode.md) (Az API biztonsági módjának beállítása)

### Gazdagügyfél-alkalmazások

A gazdagügyfél-alkalmazások lehetővé teszik az ügyfelek számára az adatok grafikus felhasználói felületen (GUI-n) keresztül történő megtekintését és kezelését. A jelen GUI-n megjelenített adatok gyakran jelentős értékkel bírnak, valamint lopási és véletlen visszaéléssel kapcsolatos kockázat is fennáll. Bár az alkalmazás kifejlesztésének elsődleges célja nem ez volt, az adatvédelmi támogatás jellemzően elősegíti a meglévő forgatókönyvek végrehajtását.

Az RMS SDK 2.1 gazdagügyfél-alkalmazásokkal együtt való alkalmazása a következőkben nyújt segítséget:

-   Annak biztosítása, hogy az adatok mindig titkosítva legyenek.

-   Annak megelőzése, hogy a felhasználók nem védett formátumba gyűjtsenek ki adatokat (például a vágólapról történő másolás/beillesztés megelőzése).

A Microsoft Jegyzettömb egy egyszerű gazdagügyfél-alkalmazás. A Microsoft Office pedig egy összetettebb gazdagügyfél-alkalmazás.

További információ az alkalmazások védelemmel történő ellátásáról: [A használattal kapcsolatos korlátozások megértése](understanding-usage-restrictions.md).

## Kapcsolódó témakörök

* [Fejlesztői fogalmak](ad-rms-concepts-nav.md)
* [IpcDlp mintaalkalmazás](https://Code.MSDN.Microsoft.Com/IpcDlp-Sample-Application-d30bb99d)
* [IPCHelloWorld – mintaalkalmazás](how-to-build-your-first-application.md)
* [Az API biztonsági mód beállítása](setting-the-api-security-mode-api-mode.md)
* [A használattal kapcsolatos korlátozások megértése](understanding-usage-restrictions.md)
 

 





<!--HONumber=Apr16_HO4-->


