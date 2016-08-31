---
title: "Azure Rights Management üzembe helyezési menetrend | Azure RMS"
description: "A következő lépésekkel készítheti elő, valósíthatja meg és kezelheti az Azure Rights Management (Azure RMS) rendszert a szervezet számára."
author: cabailey
manager: mbaldwin
ms.date: 08/24/2016
ms.topic: article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 086600c2-c5d8-47ec-a4c0-c782e1797486
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 024a29d7c7db2e4c0578a95c93e22f8e7a5b173e
ms.openlocfilehash: 13ec3a88eb1c072bf94b6c54e3e4d97e45cc8eb2


---

# Azure Rights Management üzembe helyezési menetrend

>*A következőkre vonatkozik: Azure Rights Management, Office 365*

A következő lépésekkel készítheti elő, valósíthatja meg és kezelheti az Azure Rights Management (Azure RMS) rendszert a szervezet számára.

Ha azonban az éles környezet helyett csak gyorsan ki szeretné próbálni az Azure RMS szolgáltatást, használja a [Azure Rights Management gyors üzembe helyezési oktatóanyagát](../get-started/quick-start-tutorial.md).

A forgatókönyvek és a társított konfigurációs lépések listáját, valamint a végfelhasználói dokumentációt az [Azure Rights Management gyors üzembe helyezési útmutatójában](../get-started/rapid-deployment-guide.md) találja.

> [!IMPORTANT]
> A következő lépések elvégzése előtt tekintse át az [Azure Rights Management követelményeit](../get-started/requirements-azure-rms.md).

## 1. lépés: Ellenőrizze, hogy az Azure Rights Management rendszert tartalmazó előfizetése van
Több előfizetés-típus is tartalmazza az [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] rendszert. Tekintse meg [Az Azure RMS-t támogató felhőalapú előfizetések](../get-started/requirements-subscriptions.md) című szakaszt, és ellenőrizze, hogy az előfizetése tartalmazza-e a szervezetben használni kívánt funkciót. Ehhez tekintse meg a [Comparison of Rights Management Services (RMS) Offerings](https://technet.microsoft.com/dn858608) (A Tartalomvédelmi szolgáltatásokra (RMS) vonatkozó ajánlatok összehasonlítása) című szakaszra. Ebből az előfizetésből olyan licencet kell rendelnie a szervezetben lévő összes felhasználóhoz, amely az Azure RMS használatával megvédi a fájlokat és e-maileket.

## 2. lépés: Készítse elő a bérlőfiókot a Rights Management használatára
A [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] használata előtt végezze el a következő előkészítést:

1.  Ellenőrizze, hogy az Azure vagy az Office 365 bérlő tartalmazza az Azure RMS által a szervezet felhasználóinak hitelesítéséhez használt felhasználói fiókokat és csoportokat. Szükség esetén hozza létre ezeket a fiókokat és csoportokat, vagy szinkronizálja azokat a helyszíni címtárból. További információ: [Az Azure Rights Management előkészítése](prepare.md).

2.  Döntse el, hogy a Microsoft felügyelje-e a bérlőkulcsot (az alapértelmezés), vagy hozzon létre és felügyelje a saját bérlőkulcsát (más néven saját kulcs használata vagy BYOK). Vegye figyelembe, hogy nem használhat saját kulcsot, ha az Exchange Online eszközt használja. További információ: [Az Azure Rights Management-bérlőkulcs tervezése és megvalósítása](plan-implement-tenant-key.md).

3.  Telepítse a Windows PowerShell-modult a [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] szolgáltatáshoz legalább egy, internet-hozzáféréssel rendelkező számítógépen. Ezt a lépést most vagy később is elvégezheti. További információ: [Az Azure Rights Managementhez készült Windows PowerShell telepítése](../deploy-use/install-powershell.md).

4.  Ha jelenleg helyszíni Rights Management szolgáltatásokat használ, végezzen áttelepítést, hogy a kulcsokat, a sablonokat és az URL-eket a felhőbe helyezze. További információ: [Áttelepítés AD RMS-ről Azure Rights Managementre](migrate-from-ad-rms-to-azure-rms.md).

5.  Aktiválhatja a Rights Management eszközt, hogy elkezdhesse a szolgáltatás használatát. Ha szakaszos üzembe helyezésre van szükség, konfigurálja a felhasználók beléptető szabályait, hogy a használatot adott felhasználókra korlátozza. További információ: [Az Azure Rights Management aktiválása](../deploy-use/activate-service.md).

Opcionálisan a következőket konfigurálhatja:

-   Egyéni sablonok, ha az alapértelmezett jogosultságmegadási sablonok nem elegendőek a szervezete számára. Ezt a lépést most vagy később is elvégezheti. További információ: [Configuring custom templates for Azure Rights Management](../deploy-use/configure-custom-templates.md) (Egyéni sablonok konfigurálása az Azure Rights Management szolgáltatáshoz).

-   Használatnaplózás, hogy megfigyelhesse, hogy a szervezet hogyan használja a Rights Management eszközt. Ezt a lépést most vagy később is elvégezheti. További információ: [Az Azure Rights Management használatának naplózása és elemzése](../deploy-use/log-analyze-usage.md).

## 3. lépés: Konfigurálja az alkalmazásokat és szolgáltatásokat a Rights Management eszközhöz
Az alkalmazások és szolgáltatások konfigurálásába tartozhat a Rights Management megosztóalkalmazás telepítése és a SharePoint Online vagy az Exchange Online tartalomvédelmi (IRM) támogatásának engedélyezése. További információ: [Alkalmazások konfigurálása az Azure Rights Managementhez](../deploy-use/configure-applications.md).

Ha meglévő informatikai szolgáltatásai vannak, amelyeknek az Azure RMS által védett fájlokat kell megvizsgálniuk – például adatszivárgást megelőző (DLP) megoldások, tartalomtitkosító átjárók (CEG) és kártevőirtó termékek –, konfigurálja a szolgáltatásfiókokat, hogy az Azure RMS felügyelői legyenek. További információ: [Configuring super users for Azure Rights Management and discovery services or data recovery](../deploy-use/configure-super-users.md) (Felügyelők konfigurálása az Azure Rights Management és a felderítési szolgáltatások vagy adat-helyreállítás számára).

Az összes fájltípus kötegelt védelme vagy a védelem kötegelt megszüntetése érdekében telepítse az RMS védőeszközt, amely az RMS Protection PowerShell-modult használja. További információ: [RMS Protection parancsmagok](https://msdn.microsoft.com/library/mt433195.aspx).

Ha az Azure Rights Management eszközzel használni kívánt helyszíni szolgáltatásokkal rendelkezik, telepítse és konfigurálja a Rights Management-összekötőt. További információk: [Az Azure Rights Management-összekötő telepítése](../deploy-use/deploy-rms-connector.md).

## 4. lépés: Védelem alatt álló tartalmak közzététele és használata
Most készen áll a védett tartalmak közzétételére és használatára, valamint a Rights Management vállalat általi használati módjának naplózására. További információ: [Útmutatás a felhasználók számára a fájlok védelméhez az Azure Rights Management használatával](../deploy-use/help-users.md) és [Az Azure Rights Management használatának naplózása és elemzése](../deploy-use/log-analyze-usage.md).

Ha érdekli a fájlok Fájlbesorolási infrastruktúrával történő automatikus védelme a Windows alapú fájlkiszolgálókon, olvassa el az [RMS-védelem és Windows Server fájlbesorolási infrastruktúra (FCI)](../rms-client/configure-fci.md) című cikket.

## 5. lépés: Szükség szerint felügyelje a bérlőfiók Rights Management rendszerét
Amikor megkezdi a [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] használatát, hasznos lehet a Windows PowerShell [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] modulja a rendszergazdai módosítások parancsfájllá alakításában vagy automatizálásában. További információ: [Az Azure Rights Management felügyelete a Windows PowerShell használatával](../deploy-use/administer-powershell.md).





<!--HONumber=Aug16_HO4-->


