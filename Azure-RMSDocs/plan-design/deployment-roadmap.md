---
# required metadata

title: Azure Rights Management üzembe helyezési menetrend | Azure RMS
description:
keywords:
author: cabailey
manager: mbaldwin
ms.date: 05/09/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 086600c2-c5d8-47ec-a4c0-c782e1797486

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: esaggese
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Azure Rights Management üzembe helyezési menetrend

*A következőkre vonatkozik: Azure Rights Management, Office 365*

A következő lépésekkel készítheti elő, valósíthatja meg és kezelheti az Azure Rights Management (Azure RMS) rendszert a szervezet számára.

Ha azonban az éles környezet helyett csak gyorsan ki szeretné próbálni az Azure RMS szolgáltatást, használja a [Azure Rights Management gyors üzembe helyezési oktatóanyag](../get-started/quick-start-tutorial.md) forrásanyagot.

Az adott forgatókönyveket és a társított konfigurációs lépéseket és a végfelhasználói dokumentációt a [Gyors üzembe helyezési útmutató az Azure Rights Management szolgáltatáshoz](../get-started/rapid-deployment-guide.md) szakaszban találja.

> [!IMPORTANT]
> A következő lépések elvégzése előtt tekintse át [Az Azure Rights Management követelményei](../get-started/requirements-azure-rms.md) című szakaszt.

## 1. lépés: Ellenőrizze, hogy az Azure Rights Management rendszert tartalmazó előfizetése van
Több előfizetés-típus is tartalmazza az [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] rendszert. Tekintse meg [Az Azure RMS-t támogató felhőalapú előfizetések](../get-started/requirements-subscriptions.md) című szakaszt, és ellenőrizze, hogy az előfizetése tartalmazza-e a szervezetben használni kívánt funkciót. Ehhez tekintse meg a [Comparison of Rights Management Services (RMS) Offerings](https://technet.microsoft.com/dn858608) (A Tartalomvédelmi szolgáltatásokra (RMS) vonatkozó ajánlatok összehasonlítása) című szakaszra. Ebből az előfizetésből olyan licencet kell rendelnie a szervezetben lévő összes felhasználóhoz, amely az Azure RMS használatával megvédi a fájlokat és e-maileket.

## 2. lépés: Készítse elő a bérlőfiókot a Rights Management használatára
A [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] használata előtt végezze el a következő előkészítést:

1.  Ellenőrizze, hogy az Azure vagy az Office 365 bérlő tartalmazza az Azure RMS által a szervezet felhasználóinak hitelesítéséhez használt felhasználói fiókokat és csoportokat. Szükség esetén hozza létre ezeket a fiókokat és csoportokat, vagy szinkronizálja azokat a helyszíni címtárból. További információkért lásd: [Az Azure Rights Management előkészítése](prepare.md).

2.  Döntse el, hogy a Microsoft felügyelje-e a bérlőkulcsot (az alapértelmezés), vagy hozzon létre és felügyelje a saját bérlőkulcsát (más néven saját kulcs használata vagy BYOK). Vegye figyelembe, hogy nem használhat saját kulcsot, ha az Exchange Online eszközt használja. További információ: [Planning and implementing your Azure Rights Management tenant key](plan-implement-tenant-key.md) (Az Azure Rights Management-bérlőkulcs tervezése és megvalósítása)..

3.  Telepítse a Windows PowerShell-modult a [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] szolgáltatáshoz legalább egy, internet-hozzáféréssel rendelkező számítógépen. Ezt a lépést most vagy később is elvégezheti. További információkért lásd: [Installing Windows PowerShell for Azure Rights Management](../deploy-use/install-powershell.md) (Az Azure Rights Managementhez készült Windows PowerShell telepítése)..

4.  Ha jelenleg helyszíni Rights Management szolgáltatásokat használ, végezzen áttelepítést, hogy a kulcsokat, a sablonokat és az URL-eket a felhőbe helyezze. További információ: [Áttelepítés AD RMS-ről Azure Rights Managementre](migrate-from-ad-rms-to-azure-rms.md)..

5.  Aktiválhatja a Rights Management eszközt, hogy elkezdhesse a szolgáltatás használatát. Ha szakaszos üzembe helyezésre van szükség, konfigurálja a felhasználók beléptető szabályait, hogy a használatot adott felhasználókra korlátozza. További információ: [Activating Azure Rights Management](../deploy-use/activate-service.md) (Az Azure Rights Management aktiválása)..

Opcionálisan a következőket konfigurálhatja:

-   Egyéni sablonok, ha az alapértelmezett jogosultságmegadási sablonok nem elegendőek a szervezete számára. Ezt a lépést most vagy később is elvégezheti. További információ: [Configuring custom templates for Azure Rights Management](../deploy-use/configure-custom-templates.md) (Egyéni sablonok konfigurálása az Azure Rights Management szolgáltatáshoz).

-   Használatnaplózás, hogy megfigyelhesse, hogy a szervezet hogyan használja a Rights Management eszközt. Ezt a lépést most vagy később is elvégezheti. További információ: [Az Azure Rights Management használatának naplózása és elemzése](../deploy-use/log-analyze-usage.md)..

## 3. lépés: Konfigurálja az alkalmazásokat és szolgáltatásokat a Rights Management eszközhöz
Az alkalmazások és szolgáltatások konfigurálásába tartozhat a Rights Management megosztóalkalmazás telepítése és a SharePoint Online vagy az Exchange Online tartalomvédelmi (IRM) támogatásának engedélyezése. További információ: [Configuring applications for Azure Rights Management](../deploy-use/configure-applications.md) (Alkalmazások konfigurálása az Azure Rights Managementhez).

Ha meglévő informatikai szolgáltatásai vannak, amelyeknek az Azure RMS által védett fájlokat kell megvizsgálniuk – például adatszivárgást megelőző (DLP) megoldások, tartalomtitkosító átjárók (CEG) és kártevőirtó termékek –, konfigurálja a szolgáltatásfiókokat, hogy az Azure RMS felügyelői legyenek. További információ: [Configuring super users for Azure Rights Management and discovery services or data recovery](../deploy-use/configure-super-users.md) (Felügyelők konfigurálása az Azure Rights Management és a felderítési szolgáltatások vagy adat-helyreállítás számára)..

Az összes fájltípus kötegelt védelme vagy a védelem kötegelt megszüntetése érdekében telepítse az RMS védőeszközt, amely az RMS Protection PowerShell-modult használja. További információ: [RMS Protection parancsmagok](https://msdn.microsoft.com/library/mt433195.aspx).

Ha az Azure Rights Management eszközzel használni kívánt helyszíni szolgáltatásokkal rendelkezik, telepítse és konfigurálja a Rights Management-összekötőt. További információk: [Deploying the Azure Rights Management connector](../deploy-use/deploy-rms-connector.md) (Az Azure Rights Management-összekötő telepítése).

## 4. lépés: Védelem alatt álló tartalmak közzététele és használata
Most készen áll a védett tartalmak közzétételére és használatára, valamint a Rights Management vállalat általi használati módjának naplózására. További információkért lásd: [Helping users to protect files by using Azure Rights Management](../deploy-use/help-users.md) (Útmutatás nyújtása a felhasználók számára a fájlok védelméhez az Azure Rights Management használatával) és [Logging and analyzing Azure Rights Management usage](../deploy-use/log-analyze-usage.md) (Az Azure Rights Management naplózása és elemzése).

Ha érdekli a fájlok Fájlbesorolási infrastruktúrával végzett automatikus védelme a Windows alapú fájlkiszolgálókon, lásd: [RMS protection with Windows Server File Classification Infrastructure (FCI)](../rms-client/configure-fci.md) (RMS-védelem és Windows Server fájlbesorolási infrastruktúra (FCI)).

## 5. lépés: Szükség szerint felügyelje a bérlőfiók Rights Management rendszerét
Amikor megkezdi a [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] használatát, hasznos lehet a Windows PowerShell [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] modulja a rendszergazdai módosítások parancsfájllá alakításában vagy automatizálásában. További információért lásd: [Administering Azure Rights Management by Using Windows PowerShell](../deploy-use/administer-powershell.md) (Az Azure Rights Management felügyelete a Windows PowerShell használatával).




<!--HONumber=May16_HO2-->


