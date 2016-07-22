---
title: "Az Azure Rights Management aktiválása a klasszikus Azure-portálról | Azure RMS"
description: 
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 06/27/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 9b0a0227-88ce-44b8-ba3f-31eeaab27ff7
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b214d7951820c8cb98c5d6f81af3325597ea72ec
ms.openlocfilehash: 9cde79791e8c2b04d1d7622f5aa69d654a70646e


---

# Az Azure Rights Management aktiválása a klasszikus Azure-portálról

*A következőkre vonatkozik: Azure Rights Management*


Akkor használja ezeket az utasításokat, ha hozzáfér az Azure-portálhoz. Például Nagyvállalati mobilitási csomaggal vagy prémium szintű Azure Rights Management-előfizetéssel rendelkezik.

> [!TIP]
> Tekintsen meg egy 2 perces videót: [How to activate Azure RMS](https://channel9.msdn.com/series/pit-stop-enterprise-mobility-suite/activate-azure-rms) (Az Azure RMS aktiválása)

1.  Miután regisztrálta Azure-fiókját, [jelentkezzen be a klasszikus Azure-portálra](http://go.microsoft.com/fwlink/p/?LinkID=275081). Használjon globális rendszergazdai fiókot, amilyen például az Azure Rights Managementet tartalmazó előfizetés beszerzéséhez használt fiók.

2.  A bal oldali panelen kattintson az **ACTIVE DIRECTORY** elemre.

3.  Az **Active Directory** lapon kattintson a **RIGHTS MANAGEMENT** gombra.

4.  Jelölje ki a [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] kezelni kívánt könyvtárát, kattintson az **ACTIVATE** (AKTIVÁLÁS) gombra, majd erősítse meg a műveletet.

    > [!NOTE]
    >Aktiválási hiba történhet, ha a szolgáltatáscsomag vagy a termékverzió nem tartalmazza az [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)]et.
    >
    >A [Cloud subscriptions that support Azure RMS](../get-started/requirements-subscriptions.md) (Az Azure RMS-t támogató felhőalapú előfizetések) című témakörben található információk segítséget nyújtanak az RMS-támogatás megerősítésében. Ha segítséget szeretne kérni a probléma megoldásához, küldjön e-mailt az [askipteamnek](mailto:askipteam?subject=I%20cannot%20activate%20RMS).


A **RIGHTS MANAGEMENT STATUS** (RIGHTS MANAGEMENT ÁLLAPOT) értékének **Active** (Aktív) értékűnek kell lennie, és az **ACTIVATE** (AKTIVÁLÁS) lehetőséget a **DEACTIVATE** (INAKTIVÁLÁS) lehetőség váltja fel.

## A Rights Management állapotértékei és azok leírása a klasszikus Azure-portálon
Az **Active** (Aktív) állapot mellett, amely jelzi, hogy a Rights Management szolgáltatás engedélyezett és készen áll a használatra, az **Inactive** (Inaktív), **Unavailable** (Nem érhető el) vagy **Unauthorized** (Jogosulatlan) állapotot is láthatja.

|Állapotérték|Leírás|
|----------------|---------------|
|**Aktív**|[!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] engedélyezett és készen áll a használatra.|
|**Inaktív**|[!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] letiltott és aktiválni kell, mielőtt a szervezet fájlokat védhetne meg.|
|**Nem érhető el**|A [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] szolgáltatás le van állítva. Próbálkozzon újra később.|
|**Jogosulatlan**|Nem rendelkezik engedélyekkel a [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] szolgáltatás állapotának megtekintésére. A fiókja például zárolva van, vagy nem Ön a kiválasztott bérlő globális rendszergazdája.|

## További lépések
Vissza [Az Azure Rights Management aktiválása](activate-service.md) című témakörhöz.


<!--HONumber=Jul16_HO3-->


