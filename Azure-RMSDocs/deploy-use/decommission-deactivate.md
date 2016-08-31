---
title: "Az Azure Rights Management leszerelése és inaktiválása | Azure RMS"
description: "Mindig ellenőrizni tudja, hogy a szervezete az (Azure RMS) használatával védi-e a tartalmakat, és ha nem kívánja tovább használni ezt az adatvédelmi megoldást, akkor biztos lehet benne, hogy továbbra is hozzáférhet a korábban védett tartalmakhoz. Ha nincs szüksége folyamatos hozzáférésre a korábban védett tartalomhoz, egyszerűen inaktiválja a szolgáltatást, és hagyja lejárni az Azure Rights Management-előfizetést. Ez például akkor lehet megfelelő, ha még az éles környezetben történő üzembe helyezés előtt elvégzi a tesztelést."
author: cabailey
manager: mbaldwin
ms.date: 08/24/2016
ms.topic: article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 0b1c2064-0d01-45ae-a541-cebd7fd762ad
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 024a29d7c7db2e4c0578a95c93e22f8e7a5b173e
ms.openlocfilehash: 40e4997f67a078ec781f1e7800599554858777a8


---

# Az Azure Rights Management leszerelése és deaktiválása

>*A következőkre vonatkozik: Azure Rights Management, Office 365*

Mindig ellenőrizni tudja, hogy a szervezete az [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] (Azure RMS) használatával védi-e a tartalmakat, és ha nem kívánja tovább használni ezt az adatvédelmi megoldást, akkor biztos lehet benne, hogy továbbra is hozzáférhet a korábban védett tartalmakhoz. Ha nincs szüksége folyamatos hozzáférésre a korábban védett tartalomhoz, egyszerűen inaktiválja a szolgáltatást, és hagyja lejárni az Azure Rights Management-előfizetést. Ez például akkor lehet megfelelő, ha még az éles környezetben történő üzembe helyezés előtt elvégzi az [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] tesztelését.

Ha azonban éles környezetben telepítette az [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] szolgáltatást, győződjön meg róla, hogy rendelkezik az Azure Rights Management-bérlőkulcs másolatával, mielőtt inaktiválja az alkalmazást. Ezt még az előfizetés lejárta előtt tegye meg, mivel ezzel biztosíthatja, hogy a szolgáltatás inaktiválása után is hozzáférjen az Azure Rights Management által védett tartalomhoz. Ha a saját kulcs használata (BYOK) megoldást használta, amely esetén Ön hozza létre és kezeli a saját kulcsát egy hardveres biztonsági modulban, akkor már rendelkezik Azure Rights Management-bérlőkulccsal. Ha azonban a Microsoft kezelte a kulcsot (ez az alapértelmezés), tekintse meg a bérlőkulcs exportálására vonatkozó útmutatást az [Operations for your Azure Rights Management tenant key](operations-tenant-key.md) (Az Azure Rights Management bérlőkulcsával kapcsolatos műveletek) című cikkben.

> [!TIP]
> Az Azure Rights Management-bérlő még az előfizetés lejárta után is hosszabb ideig elérhető marad a tartalom felhasználásához. A bérlőkulcsot azonban már nem exportálhatja.

Ha megvan az Azure Rights Management-bérlőkulcsa, elvégezheti a Rights Management központi telepítését a helyszínen (AD RMS), és importálhatja a bérlőkulcsát megbízható közzétételi tartományként (TPD). Ezután az alábbi lehetőségei vannak az üzembe helyezett Azure Rights Management leszerelésére:

|Ha ez érvényes Önre…|… tegye a következőket:|
|----------------------------|--------------|
|Ha azt szeretné, hogy a felhasználók továbbra is használják a Rights Managementet, de helyszíni megoldást használ az Azure RMS helyett    →|Használja a [Set-AadrmMigrationUrl](https://msdn.microsoft.com/library/azure/dn629429.aspx) parancsmagot, hogy a meglévő felhasználókat a helyszíni telepítéshez irányítsa, amikor a módosítás után védett tartalmakat használnak. A felhasználók a védett tartalom felhasználásához automatikusan használni fogják az AD RMS-telepítést.<br /><br />Ahhoz, hogy a felhasználók fel tudják használni a módosítás előtt védett tartalmakat, irányítsa át az ügyfeleket a helyszíni telepítéshez az Office 2016 és Office 2013 **LicensingRedirection** beállításkulcsának az RMS-ügyfél üzembe helyezésével kapcsolatos megjegyzések [szolgáltatásészleléssel kapcsolatos szakaszában](../rms-client/client-deployment-notes.md) leírtak szerinti használatával. Office 2010 esetén a **LicenseServerRedirection** beállításkulcsot használhatja, az [Office beállításjegyzék-beállítások](https://technet.microsoft.com/library/dd772637%28v=ws.10%29.aspx) témakörben leírtak szerint.|
|Ha egyáltalán nem kívánja a továbbiakban használni a Rights Management technológiákat    →|Adjon egy kijelölt rendszergazdának [felügyelői jogosultságokat](../deploy-use/configure-super-users.md), és tegye elérhetővé számára az [RMS Protection eszközt](http://www.microsoft.com/en-us/download/details.aspx?id=47256).<br /><br />A rendszergazda ezután használhatja az eszközt a fájlok tömeges visszafejtésére olyan mappákban, az Azure Rights Management által védett mappákban, hogy a fájlok visszaálljanak a védelem nélküli állapotra, és így a Rights Management technológia, például az Azure RMS vagy az AD RMS nélkül is olvashatók legyenek. Az eszközt az Azure RMS és az AD RMS szolgáltatással is lehet használni, így választhat, hogy a fájlokat az Azure RMS inaktiválása előtt vagy után fejti vissza, vagy kombinálja a kettőt.|
|Ha nem lehet azonosítani az Azure RMS által védett fájlok mindegyikét, vagy azt szeretné, hogy a felhasználók automatikusan tudják olvasni a kihagyott védett fájlokat    →|Telepítsen egy beállításjegyzék-beállítást minden ügyfélszámítógépre az Office 2016 és Office 2013 **LicensingRedirection** beállításkulcsának az RMS-ügyfél üzembe helyezésével kapcsolatos megjegyzések [szolgáltatásészleléssel kapcsolatos szakaszában](../rms-client/client-deployment-notes.md) leírtak szerinti használatával. Office 2010 esetén a **LicenseServerRedirection** beállításkulcsot használhatja, az [Office beállításjegyzék-beállítások](https://technet.microsoft.com/library/dd772637%28v=ws.10%29.aspx) témakörben leírtak szerint.<br /><br />Emellett telepítsen egy másik beállításjegyzék-beállítást is annak érdekében, hogy a felhasználók ne védjék meg az új fájlokat. Ezt a **DisableCreation** **1** értékre állításával érheti el, az [Office beállításjegyzék-beállításai](https://technet.microsoft.com/library/dd772637%28v=ws.10%29.aspx) szakaszban leírtak szerint.|
|Ha irányított, manuálisan működő helyreállítási szolgáltatást szeretne a kihagyott fájlokhoz    →|Egy adat-helyreállítási csoporton belül adjon a kijelölt felhasználóknak [felügyelői jogosultságokat](../deploy-use/configure-super-users.md), és tegye elérhetővé számukra az [RMS Protection eszközt](http://www.microsoft.com/en-us/download/details.aspx?id=47256), hogy meg tudják szüntetni az általános jogú felhasználók által kért fájlok védettségét.<br /><br />Telepítse a beállításjegyzék-beállítást minden számítógépen annak érdekében, hogy a felhasználók ne védjék meg az új fájlokat. Ezt a **DisableCreation** **1** értékre állításával érheti el, az [Office beállításjegyzék-beállításai](https://technet.microsoft.com/library/dd772637%28v=ws.10%29.aspx) szakaszban leírtak szerint.|
A táblázatban szereplő eljárásokkal kapcsolatos további információkért tekintse meg a következő forrásanyagokat:

-   Az AD RMS-sel és a telepítési referenciákkal kapcsolatos információk: [Active Directory Rights Management Services áttekintése](https://technet.microsoft.com/library/hh831364.aspx).

-   Az Azure RMS-bérlőkulcs TPD-fájlként való importálásával kapcsolatos útmutatásért lásd: [Megbízható közzétételi tartomány hozzáadása](https://technet.microsoft.com/library/cc771460.aspx).

-   Az Azure RMS-hez készült Windows PowerShell-modul telepítéséhez és az áttelepítés URL-címének beállításához tekintse meg [Az Azure Rights Managementhez készült Windows PowerShell telepítése](install-powershell.md) című témakört.

Amikor készen áll az Azure RMS szolgáltatás inaktiválására a szervezete számára, kövesse az alábbi utasításokat.

## A Rights Management inaktiválása
Használja a következő eljárások egyikét az [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] inaktiválásához.

> [!TIP]
> A [Disable-Aadrm](http://msdn.microsoft.com/library/windowsazure/dn629422.aspx) Windows PowerShell-parancsmagot is használhatja az [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] inaktiválásához.

#### A Rights Management inaktiválása az Office 365 Felügyeleti központban

1.  [Jelentkezzen be az Office 365-be a munkahelyi vagy iskolai fiókkal](https://portal.office.com/), amely a telepített Office 365 rendszergazdai fiókja.

2.  Ha az Office 365 Felügyeleti központ nem jelenik meg automatikusan, kattintson az alkalmazás indítóikonjára a bal felső sarokban, és válassza a **Rendszergazda** elemet. A **Rendszergazda** csempe csak az Office 365-rendszergazdák számára jelenik meg.

    > [!TIP]
    > A Felügyeleti központtal kapcsolatos segítségért tekintse meg [Az Office 365 Felügyeleti központ bemutatása – rendszergazdai súgó](https://support.office.com/article/About-the-Office-365-admin-center-Admin-Help-58537702-d421-4d02-8141-e128e3703547) című témakört.

3.  A bal oldali panelen bontsa ki a **SZOLGÁLTATÁS BEÁLLÍTÁSAI** elemet.

4.  Kattintson a **Rights Management** elemre.

5.  A **RIGHTS MANAGEMENT** lapon kattintson a **Kezelés** parancsra.

6.  A **rights management** lapon kattintson az **inaktiválás** elemre.

7.  Amikor megjelenik a **Szeretné inaktiválni a Rights Management szolgáltatást?** kérdés, kattintson az **inaktiválás** elemre.

Ekkor megjelenik **A Rights Management nincs aktiválva** üzenet és az aktiválásra szolgáló lehetőség.

#### A Rights Management inaktiválása a klasszikus Azure portálon

1.  Jelentkezzen be a [Klasszikus Azure-portálra](http://go.microsoft.com/fwlink/p/?LinkID=275081).

2.  A bal oldali panelen kattintson az **ACTIVE DIRECTORY** elemre.

3.  Az **Active Directory** lapon kattintson a **RIGHTS MANAGEMENT** gombra.

4.  Válassza ki a [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] felügyelni kívánt könyvtárát, kattintson a **DEACTIVATE** (INAKTIVÁLÁS) gombra, majd erősítse meg a műveletet.

A **RIGHTS MANAGEMENT STATUS** (RIGHTS MANAGEMENT-ÁLLAPOT) értékének **Inactive** (Inaktív) értékűnek kell lennie, és a **DEACTIVATE** (INAKTIVÁLÁS) lehetőséget az **ACTIVATE** (AKTIVÁLÁS) lehetőség váltja fel.






<!--HONumber=Aug16_HO4-->


