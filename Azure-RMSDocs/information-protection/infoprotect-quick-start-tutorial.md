---
title: "Azure Information Protection – gyors üzembe helyezési útmutató | Azure Rights Management"
description: "Egy bevezető oktatóanyag, amellyel gyorsan kipróbálhatja a szervezetnél a Microsoft Azure Information Protection szolgáltatást csupán 4, 15 percnél gyorsabban végrehajtható lépésben."
author: cabailey
manager: mbaldwin
ms.date: 07/29/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 1260b9e5-dba1-41de-84fd-609076587842
translationtype: Human Translation
ms.sourcegitcommit: 93444affe94b280db2c9e4e2960c6902e491dec6
ms.openlocfilehash: 17670eadc7cbf6111ab7fd0a9322e51d401b86e1


---

# Azure Information Protection – gyors üzembe helyezési útmutató 

>*A következőkre vonatkozik: az Azure Information Protection előzetes verziója*

**[ Előzetes információ, a tartalma változhat. ]**

Az alábbi oktatóanyag segítségével gyorsan kipróbálhatja a szervezetnél az Azure Information Protection előzetes verzióját csupán 4, 15 percnél gyorsabban végrehajtható lépésben. Az útmutató során aktiválhatja az Azure Rights Management szolgáltatást, megtekintheti és módosíthatja az alapértelmezett Azure Information Protection-szabályzatot, telepítheti az Azure Information Protection-ügyfelet, valamint egy Word-dokumentumban kipróbálhatja a besorolási, címkézési és védelmi műveleteket.

Ez az oktatóanyag az informatikai rendszergazdáknak és tanácsadóknak szól, hogy könnyebben kiértékelhessék az Azure Information Protection szolgáltatást a szervezetek vállalati információvédelmi megoldásaként. A szolgáltatás aktiválását, az Information Protection-szabályzat konfigurálását és az ügyfél telepítését éles környezetben a rendszergazda végezné el a felhasználók számára. A dokumentum címkézése pedig a végfelhasználók feladata. Ebben az oktatóanyagban mindkét utasítássor szerepel, hogy bemutathassuk a szervezeti adatok besorolásának, címkézésének és védelmének teljes forgatókönyvét. 

Ha problémát tapasztal az oktatóanyag elvégzésekor vagy az Azure Information Protection használata közben, esetleg kíváncsi mások véleményére, látogasson el az [Azure Information Protection Yammer-webhelyére](https://www.yammer.com/askipteam/#/threads/inGroup?type=in_group&feedId=8652489&view=all).

## Előfeltételek 
Az oktatóanyag elvégzéséhez a következőkre lesz szüksége:

- Az Azure Rights Management szolgáltatást tartalmazó előfizetés. Erre azért van szükség, hogy hozzáférhessen az Azure Information Protection előzetes kiadásához. Az Azure Information Protection minden olyan régióban elérhető, ahol támogatott az Azure Rights Management használata. Az előfizetési lehetőségekkel kapcsolatos további információkat és az ingyenes próbaverzió hivatkozásait az [Azure RMS-követelmények: Az Azure RMS-t támogató felhőalapú előfizetések](../get-started/requirements-subscriptions.md) című cikkben találja.

- Azure-előfizetés ahhoz, hogy hozzáférhessen az Azure portálhoz és konfigurálhassa az Azure Information Protection-szabályzatot. Ha a szervezete még nem rendelkezik Azure-előfizetéssel, akkor igényelhet egy ingyenes próbaverziót: keresse fel az [Azure Get started](https://account.windowsazure.com/organization) (Ismerkedés az Azure-ral) oldalt, és kövesse az utasításokat.

  > [!TIP] 
  > Ha be kell szereznie a fenti előfizetések valamelyikét, érdemes előre megtennie ezt, mert ez a folyamat néha időigényes lehet.

- Egy globális rendszergazdai fiók az Office 365 felügyeleti központjába vagy a klasszikus Azure portálra történő belépéshez, hogy szükség esetén aktiválhassa a Rights Management szolgáltatást. Ennek a fióknak egy e-mail-címmel és egy működő levelezőszolgáltatással is rendelkeznie kell (például az Exchange Online vagy az Exchange Server használatával).

- Egy Windows (legalább Windows 7 SP1) rendszert futtató számítógép, amelyen telepítve van az Office Professional Plus 2016, az Office Professional Plus 2013 a Service Pack 1 csomaggal, vagy az Office Professional Plus 2010. 

- Ha a szervezetnél az Active Directory Rights Management Services (AD RMS) van telepítve, olyan munkacsoporthoz tartozó számítógépet kell használni, amelyen korábban még nem használták az AD RMS szolgáltatást. Erre a dokumentumok védelmekor van szükség, emellett biztosítja, hogy a számítógép csak Azure Rights Management-sablonokat töltsön le. A számítógép nem kapcsolódhat egyszerre az AD RMS és az Azure RMS szolgáltatáshoz. A migrálásról további információt az [Áttelepítés AD RMS-ről Azure Rights Managementre](../plan-design/migrate-from-ad-rms-to-azure-rms.md) című témakörben talál.   

Lássunk neki!

>[!div class="step-by-step"]
[&#187; 1. lépés](infoprotect-tutorial-step1.md)





<!--HONumber=Jul16_HO5-->


