---
title: "Az Azure Information Protection-ügyfél telepítése | Azure Rights Management"
description: "A dokumentumok és e-mailek az Azure Information Protection-nel való besorolásához először telepítenie kell az Azure Information Protection-ügyfelet. A telepítés után az Office-alkalmazások felületén (Word, Excel, PowerPoint, Outlook) megjelenik az Information Protection-sáv , amely megjeleníti a szervezet besorolási címkéit, valamint az új Protection (Védelem) csoportot és a Protect (Védelem) gombot a Kezdőlapon (Word, Excel, PowerPoint)."
manager: mbaldwin
ms.date: 07/29/2016
ms.topic: article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 4445adff-4c5a-450f-aff8-88bf5bd4ca78
translationtype: Human Translation
ms.sourcegitcommit: c9f9211e7c1dcf293caf81475515114b5433d6a7
ms.openlocfilehash: ab8388e03803d32a6891785f905a1ddef796bc25


---

# Az Azure Information Protection-ügyfél telepítése

>*A következőkre vonatkozik: az Azure Information Protection előzetes verziója*

**[ Előzetes információ, a tartalma változhat. ]**

A dokumentumok és e-mailek az Azure Information Protection-nel való besorolásához először telepítenie kell az Azure Information Protection-ügyfelet. A telepítés után az Office-alkalmazások felületén (Word, Excel, PowerPoint, Outlook) megjelenik az Information Protection-sáv , amely megjeleníti a szervezet besorolási címkéit, valamint az új **Protection** (Védelem) csoportot és a **Protect** (Védelem) gombot a **Kezdőlapon** (Word, Excel, PowerPoint):

Az alábbi képen látható az Information Protection-sáv és az [alapértelmezett házirend](configure-policy-default.md) címkéi:

![Az Azure Information Protection-sáv és az alapértelmezett házirend](../media/info-protect-bar-default.png)

Töltse le az Azure Information Protection-ügyfelet a [Microsoft letöltőközpontból](https://www.microsoft.com/en-us/download/details.aspx?id=53018).

Az ügyfél telepítése előtt ellenőrizze, hogy megfelel-e az operációs rendszerrel és az alkalmazásokkal kapcsolatos előírásoknak: [Az Azure Information Protection használati követelményei](requirements-azure-infoprotect.md).


## Az Azure Information Protection-ügyfél manuális telepítése

1. Az [ügyfél letöltése után](https://www.microsoft.com/en-us/download/details.aspx?id=53018) futtassa az **AZInfoProtection.exe** fájlt, és kövesse az ügyfél telepítéséhez szükséges lépéseket. A telepítéshez helyi rendszergazdai engedély szükséges.

    Ha nem tud csatlakozni az Office 365 vagy az Azure Active Directory szolgáltatásaihoz, de egy helyi, bemutató jellegű házirenddel szeretné megismerni az Azure Information Protection ügyféloldalát, válassza a bemutató házirend telepítését. Amikor az ügyfél egy Azure Information Protection-szolgáltatáshoz csatlakozik, a bemutató házirendet helyére a szervezeti Azure Information Protection-házirend kerül. 

2. Az Azure Information Protection-ügyfél használata: Ha a számítógépén az Office 2010 van telepítve, indítsa újra a gépet. Az Office egyéb verziói esetén indítsa újra az Office-alkalmazásokat.

## Az Azure Information Protection-ügyfél telepítése felhasználók számára

- Az Azure Information Protection-ügyfél telepítését parancsfájlokkal automatizálhatja az AZInfoProtection.exe becsomagolásával és a szabványos [Windows Installer (msiexec.exe) parancssori beállításokkal](https://technet.microsoft.com/library/cc759262(v=ws.10).aspx).

    Ha például a létrehozott becsomagolt verzió neve InfoProtect.msi, és csendes telepítést szeretne: `msiexec /qn InfoProtection.msi`


## Az Azure Information Protection-ügyfél eltávolítása

- Program eltávolítása a Vezérlőpult segítségével: kattintson a **Microsoft Azure Information Protection** > **Eltávolítás** lehetőségre

## A telepítés és a kapcsolat állapotának ellenőrzése, problémák bejelentése

1. Nyisson meg egy Office-alkalmazást, és a **Kezdőlap** **Protection** (Védelem) csoportjában kattintson a **Protect** (Védelem) elemre, majd a **Help and feedback** (Súgó és visszajelzés) lehetőségre.

2. A **Microsoft Azure Information Protection** párbeszédpanelen tekintse át következőket:

    - A **Last connection** (Legutóbbi kapcsolat) értéke, amely azonosítja az ügyél legutóbbi csatlakozását a szervezeti Azure Information Protection-szolgáltatáshoz. Amikor az ügyfél csatlakozik a szolgáltatáshoz, automatikusan letölti a legújabb házirendet, amennyiben az nem egyezik a jelenlegivel. Ha a megjelenített időn túllépve módosította a házirendet, zárja be majd nyissa meg újra az Office-alkalmazást.

    - A megjelenített felhasználónév, amely azonosítja az Azure Information Protection-fiókot. A felhasználónévnek meg kell egyeznie az Office 365 vagy az Azure Active Directory szolgáltatáshoz használt fiók nevével.

    - Az Azure Information Protection-ügyfél verziója.

    - A **Send feedback** (Visszajelzés küldése) hivatkozás, amellyel automatikusan csatolhat ügyfélnaplókat az Information Protection csapatának vizsgálat céljából elküldött e-mailekhez.

    - A **Run diagnostics** (Diagnosztika futtatása) hivatkozás: Ez a funkció jelenleg nincs implementálva.

## Fájlhelyek

Ügyfélfájlok:   

- 64 bites operációs rendszerek esetén: **\ProgramFiles (x86)\Microsoft Azure Information Protection**

- 32 bites operációs rendszerek esetén: **\Program Files\Microsoft Azure Information Protection**

Ügyfélnaplók és az aktuális házirendfájl:

- 64 bites és 32 bites operációs rendszerek esetén: **%localappdata%\Microsoft\MSIP**


## További lépések

Az Information Protection-sáv címkéinek módosításához konfigurálnia kell az Azure Information Protection-házirendet. További információt [Az Azure Information Protection-házirend konfigurálása](configure-policy.md) című témakörben találhat.

Az alapértelmezett házirend testreszabásáról és az Office-alkalmazásokban való viselkedésről az [Azure Information Protection – gyors üzembe helyezési útmutató](infoprotect-quick-start-tutorial.md) tartalmaz példát. 



<!--HONumber=Aug16_HO4-->


