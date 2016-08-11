---
title: "Címkék konfigurálása a Rights Management-védelem aktiválásához | Azure Rights Management"
description: 
author: cabailey
manager: mbaldwin
ms.date: 07/29/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: df26430b-315a-4012-93b5-8f5f42e049cc
translationtype: Human Translation
ms.sourcegitcommit: 00b4cd2b1e7b1196cedd39d7052db534e781bb13
ms.openlocfilehash: 7a20b59c404959c4ec209e8c29ac61ab71233e87


---

# Címkék konfigurálása a Rights Management-védelem aktiválásához

>*A következőkre vonatkozik: az Azure Information Protection előzetes verziója*

**[ Előzetes információ, a tartalma változhat. ]**

A legbizalmasabb dokumentumait és e-mailjeit megvédheti az Azure Rights Management titkosítási, engedélyezési és identitási szabályzataival, így megelőzheti az adatok elvesztését. A védelem akkor lép életbe, amikor egy címkét a Rights Management-sablonnal használ. 

Ez a sablon lehet az egyik, az Azure Rights Management aktiválásakor automatikusan létrehozott alapértelmezett sablon, de lehet egyéni is. A program a részlegszintű sablonokat is támogatja, de az általuk nyújtott védelem csak akkor érvényes, ha a dokumentum vagy e-mail szerzője a sablon konfigurált hatókörén belül van. Ha a felhasználó nincs a hatókörön belül, egy üzenet értesíti arról, hogy az Azure Information Protection nem tudja alkalmazni a címkét.

## A védelem működése

Az Azure Rights Management által védett dokumentumok és e-mailek aktívan nem használt állapotban és átvitel közben titkosítva vannak, amelyet csak az illetékes felhasználók oldhatnak fel. A titkosítás a dokumentumok és e-mailek átnevezése után is érvényben marad. Emellett a használati engedélyeket és korlátozásokat is konfigurálhatja az alábbi példák szerint:

- Csak a szervezeten belüli felhasználók nyithatják meg a dokumentumot vagy e-mailt.

- Csak a marketingrészleg felhasználói szerkeszthetik és nyomtathatják ki a dokumentumot vagy e-mailt, a többi felhasználó csak megnyithatja azt.

- A felhasználók nem továbbíthatnak egy e-mailt.

- Az üzleti partnereknek küldött dokumentumok és e-mailek nem nyithatók meg egy megadott dátum után.

További információt a sablonokról, valamint a használati engedélyekről és korlátozásokról [Az Azure Rights Management egyéni sablonjainak konfigurálása](../deploy-use/configure-custom-templates.md) című témakörben találhat.

További információt az Azure Rights Managementről és annak működéséről a [Mi az az Azure Rights Management?](../understand-explore/what-is-azure-rms.md) című témakörben találhat

> [!IMPORTANT]
> A címkék az Azure Rights Management-szolgáltatás szervezeti szintű aktiválása nélkül nem nyújtanak Rights Management-védelmet. Ha ezt a lépést még nem tette meg, tekintse meg [Az Azure Rights Management aktiválása](../deploy-use/activate-service.md) című témakört.


## Címkék konfigurálása a Rights Management-védelem aktiválásához

1. Jelentkezzen be az [Azure portálra](https://portal.azure.com).
 
2. A menüben kattintson a **Tallózás** gombra, és kezdje el begépelni az **Information** szót a Szűrő mezőbe. Válassza az **Azure Information Protection** lehetőséget.

3. Az **Azure Information Protection** panelen jelölje ki a Rights Management-védelem aktiválásához konfigurálni kívánt címkét.

4. A **Label** (Címke) panel **Set RMS template for protecting documents and emails containing this label** (RMS-sablon beállítása az ezt a címkét tartalmazó dokumentumok és e-mailek védelméhez) szakaszán konfigurálja az alábbi beállításokat:

    - Ha megjelenik a **Select RMS template from** (RMS-sablon kiválasztása innen) lehetőség, válassza ki az **Azure RMS** lehetőséget. 
    
        A Microsoft szakértői segítsége nélkül ne válassza az **AD RMS** lehetőséget és az ahhoz kapcsolódó konfigurációs beállításokat. Ha szívesen tesztelné az Azure Information Protection-t az Active Directory Rights Management Services szolgáltatással, küldjön egy e-mailt az askipteam@microsoft.com címre. 
    
    - Az **Select RMS template** (RMS-sablon kiválasztása) területen kattintson a legördülő listára, és válassza ki a dokumentumok és e-mailek védelméhez használni kívánt sablont.

        > [!NOTE] Ha a **Label** (Címke) panel megnyitása után új sablont hoz létre, zárja be a panelt és térjen vissza a 3. lépésre, így az újonnan létrehozott sablon is megjelenik a választható lehetőségek között.

5. Kattintson a **Mentés**gombra.

6. A módosításokat az **Azure Information Protection** panel **Publish** (Közzététel) lehetőségével teheti elérhetővé a felhasználóknak.

## További lépések

További információt az Azure Information Protection-házirend konfigurálásáról a [Szervezet házirendjeinek konfigurálása](configure-policy.md#configuring-your-organization-s-policy) szakasz hivatkozásai között találhat.  



<!--HONumber=Jul16_HO5-->


