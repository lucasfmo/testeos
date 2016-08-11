---
title: "A címkék vizuális megjelöléseinek konfigurálása az Azure Information Protection szolgáltatásban | Azure Rights Management"
description: 
author: cabailey
manager: mbaldwin
ms.date: 07/29/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: df2676eeb062-f25a-4cf8-a782-e59664427d54
translationtype: Human Translation
ms.sourcegitcommit: 93444affe94b280db2c9e4e2960c6902e491dec6
ms.openlocfilehash: 9f2d28e4f162891497a7b0518322338628118b9d


---

# A címkék vizuális megjelöléseinek konfigurálása az Azure Information Protection szolgáltatásban

>*A következőkre vonatkozik: az Azure Information Protection előzetes verziója*

**[ Előzetes információ, a tartalma változhat. ]**

A dokumentumokhoz és e-mailekhez hozzárendelt címkék esetében több, a besorolások külső megkülönböztetését segítő beállítás közül választhat. Ezek a vizuális megjelölések a fejléc, az élőláb és a vízjel:

A vizuális megjelölések a Word-, Excel- és PowerPoint-dokumentumokban alkalmazott címkéken, valamint a dokumentumok mentésekor jelennek meg. Az e-mailek esetében a vizuális megjelölések az üzenet elküldésekor jelennek meg.

További információ a vizuális megjelölésekről:

- A fejlécek és élőlábak a Word, az Excel, a PowerPoint és az Outlook programokban alkalmazhatók.

- A vízjelek a Word, az Excel és a PowerPoint programokban alkalmazhatók:

    - Excel: a vízjelek csak Oldalkép és Nyomtatási kép nézetben, illetve kinyomtatva láthatók.

    - PowerPoint: a vízjel a diamintán jelenik meg háttérképként.

A címkék vizuális jeleinek konfigurálásához kövesse az alábbi utasításokat.

1. Jelentkezzen be az [Azure portálra](https://portal.azure.com).
 
2. A menüben kattintson a **Tallózás** gombra, és kezdje el begépelni az **Information** szót a Szűrő mezőbe. Válassza az **Azure Information Protection** lehetőséget.

3. Az **Azure Information Protection** panelen jelölje ki a vizuális megjelölésekkel konfigurálni kívánt címkét.

4. A**Label** (Címke) panel **Set visual marking (such as header or footer)** (Vizuális megjelölés (például fejléc vagy élőláb) beállítása) területén konfigurálja a vizuális megjelölések beállításait, majd kattintson a **Save** (Mentés) gombra:

    - Fejléc konfigurálása: A **Documents with this label have a header** (Az ezzel a címkével ellátott dokumentumok fejléccel jelenjenek meg) beállítást kapcsolja **Be**, ha szeretne fejlécet, és kapcsolja **Ki**, ha nem. Ha a beállítást **bekapcsolta**, adja meg a fejléc szövegét, színét és állítsa be az igazítását.

    - Élőláb konfigurálása: A **Documents with this label have a footer** (Az ezzel a címkével ellátott dokumentumok előlábbal jelenjenek meg) beállítást kapcsolja **Be**, ha szeretne előlábat, és kapcsolja **Ki**, ha nem. Ha a beállítást **bekapcsolta**, adja meg az előláb szövegét, színét és állítsa be az igazítását.

    - Vízjel konfigurálása: A **Documents with this label have a watermark** (Az ezzel a címkével ellátott dokumentumok vízjellel jelenjenek meg) beállítást kapcsolja **Be**, ha szeretne vízjelet, és kapcsolja **Ki**, ha nem. Ha a beállítást **bekapcsolta**, adja meg a vízjel szövegét, színét és állítsa be az igazítását.

5. A módosításokat az **Azure Information Protection** panel **Publish** (Közzététel) lehetőségével teheti elérhetővé a felhasználóknak.

## További lépések

További információt az Azure Information Protection-házirend konfigurálásáról a [Szervezet házirendjeinek konfigurálása](configure-policy.md#configuring-your-organization-s-policy) szakasz hivatkozásai között találhat.  





<!--HONumber=Jul16_HO5-->


