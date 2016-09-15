---
title: "Címkék konfigurálása a Rights Management-védelem aktiválásához | Azure Rights Management"
description: "Bizalmas dokumentumai és e-mailjei védelmét tartalomvédelmi szolgáltatás segítségével biztosíthatja, amely titkosítási, identitás-kezelési és engedélyezési szabályzatokat alkalmaz az adatvesztés megakadályozása érdekében. A védelem akkor lép életbe, amikor egy címkét a Rights Management-sablonnal használ."
manager: mbaldwin
ms.date: 08/15/2016
ms.topic: article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: df26430b-315a-4012-93b5-8f5f42e049cc
translationtype: Human Translation
ms.sourcegitcommit: c9f9211e7c1dcf293caf81475515114b5433d6a7
ms.openlocfilehash: 23e62c82a38e696b0708f3b599d24f3a0f337fd8


---

# Címkék konfigurálása a Rights Management-védelem aktiválásához

>*A következőkre vonatkozik: az Azure Information Protection előzetes verziója*

**[ Előzetes információ, a tartalma változhat. ]**

Bizalmas dokumentumai és e-mailjei védelmét tartalomvédelmi szolgáltatás segítségével biztosíthatja, amely titkosítási, identitás-kezelési és engedélyezési szabályzatokat alkalmaz az adatvesztés megakadályozása érdekében. A védelem akkor lép életbe, amikor egy címkét a Rights Management-sablonnal használ. 

Ez a sablon lehet az egyik, az Azure Rights Management aktiválásakor automatikusan létrehozott alapértelmezett sablon, de lehet egyéni is. Az Azure Rights Management a részlegszintű sablonokat is támogatja, de az ezek által nyújtott védelmet csak akkor alkalmazza, ha a dokumentum vagy e-mail szerzője a sablon konfigurált hatókörén belül van. Ha a felhasználó nincs a hatókörön belül, egy üzenet értesíti arról, hogy az Azure Information Protection nem tudja alkalmazni a címkét.

## A védelem működése

Ha egy dokumentum vagy e-mail tartalomvédett, akkor mind inaktív állapotban, mind az átvitel során titkosítva van, és a titkosítást csak az arra jogosult felhasználók oldhatják fel. A titkosítás a dokumentumok és e-mailek átnevezése után is érvényben marad. Emellett a használati engedélyeket és korlátozásokat is konfigurálhatja az alábbi példák szerint:

- Csak a szervezeten belüli felhasználók nyithatják meg a bizalmas vállalati dokumentumokat vagy e-maileket.

- Csak a marketingrészleg felhasználói szerkeszthetik és nyomtathatják ki az akciókat bejelentő dokumentumokat vagy e-maileket, a szervezet többi felhasználója csak megtekintheti ezeket.

- A felhasználók nem továbbíthatnak belső átszervezésről szóló híreket tartalmazó e-maileket.

- Az üzleti partnereknek küldött aktuális árlista egy meghatározott időpont után már nem nyitható meg.

További információ az Azure Rights Management sablonokról és a felhasználási engedélyek és korlátozások beállításáról: [Az Azure Rights Management egyéni sablonok konfigurálása](../deploy-use/configure-custom-templates.md).

További információt az Azure Rights Managementről és annak működéséről a [Mi az az Azure Rights Management?](../understand-explore/what-is-azure-rms.md) című témakörben találhat

> [!IMPORTANT]
> A címkék csak abban az esetben nyújtanak Azure Rights Management-védelmet, ha az Azure Rights Management szolgáltatás aktiválva van a szervezet számára. Ha ezt a lépést még nem tette meg, tekintse meg [Az Azure Rights Management aktiválása](../deploy-use/activate-service.md) című témakört.


## Címkék konfigurálása a Rights Management-védelem aktiválásához

1. Ha még nem tette meg, jelentkezzen be globális rendszergazdaként az [Azure Portalon](https://portal.azure.com), hogy lekérhesse az Azure Rights Management-sablonokat. Navigáljon az **Azure Information Protection**-panelre. 

    A Központ menüben kattintson a **Tallózás** gombra, és kezdje el begépelni az **Information** szót a Szűrő mezőbe. Válassza az **Azure Information Protection** lehetőséget.

2. Az **Azure Information Protection** panelen jelölje ki a Rights Management-védelem aktiválásához konfigurálni kívánt címkét.

3. A **Label** (Címke) panelen a **Set RMS template for protecting documents and emails containing this label** (RMS-sablon beállítása az e címkét tartalmazó dokumentumok és e-mailek védelmére) szakaszban a **Select RMS template from** (RMS-sablon kiválasztása innen:) lehetőségnél válassza az **Azure RMS** vagy az **AD RMS (PREVIEW)** (előzetes verzió) opciót.
    
    A legtöbb esetben az **Azure RMS** lehetőséget kell választania. Csak abban az esetben válassza az AD RMS-t, ha elolvasta és megértette az ehhez az esetenként *HYOK-nak* is nevezett konfigurációhoz tartozó előfeltételeket és korlátozásokat. További információ: [Hold your own key (HYOK) requirements and restrictions for AD RMS protection](configure-adrms-restrictions.md) (A „Hold your own key - HYOK” megoldás követelményei és korlátozásai”).
    
4. Ha az Azure RMS-t választotta: A **Select RMS template** (RMS-sablon kiválasztása) területen kattintson a legördülő listára, és válassza ki a dokumentumok és e-mailek védelméhez használni kívánt sablont.

    > [!NOTE] 
    > Ha a **Label** (Címke) panel megnyitása után új sablont hoz létre, zárja be a panelt és térjen vissza a 2. lépéshez, így az újonnan létrehozott sablon is megjelenik a választható lehetőségek között.
    
    Ha részlegszintű sablont választ vagy [regisztrációs vezérlőket](../deploy-use/activate-service.md#configuring-onboarding-controls-for-a-phased-deployment) konfigurált, a következőket kell figyelembe vennie:
    
    - A sablon konfigurált hatókörén kívül lévő vagy az Azure Rights Management-védelemből kizárt felhasználók továbbra is látni fogják a címkét, azonban nem alkalmazhatják azt. Ha mégis rákattintanak a címkére, egy üzenet értesíti őket arról, hogy **az Azure Information Protection nem tudja alkalmazni a címkét, és ha a probléma nem oldódik meg, forduljanak a rendszergazdához.**
    
5. Ha az AD RMS-t választotta: adja meg a sablon GUID-azonosítóját és az Ön AD RMS-fürtjének licencelési URL-címét. [További információ](configure-adrms-restrictions.md#locating-the-information-to-specify-ad-rms-protection-with-an-azure-information-protection-label)

6. Kattintson a **Mentés**gombra.

7. A módosításokat az **Azure Information Protection** panel **Publish** (Közzététel) lehetőségével teheti elérhetővé a felhasználóknak.

## További lépések

További információt az Azure Information Protection-házirend konfigurálásáról a [Szervezet házirendjeinek konfigurálása](configure-policy.md#configuring-your-organization-s-policy) szakasz hivatkozásai között találhat.  



<!--HONumber=Aug16_HO4-->


