---
title: "Az Azure Rights Management aktiválása | Azure RMS"
description: "Az (Azure RMS) aktiválásakor a szervezete megkezdheti a fontos adatok védelmét az ezen adatvédelmi megoldást támogató alkalmazások és szolgáltatások használatával. A rendszergazdák ezenkívül kezelhetik és megfigyelhetik a szervezete tulajdonában lévő védett fájlokat és e-maileket. Az Office, a SharePoint és az Exchange szoftverekben lévő tartalomvédelmi szolgáltatások (IRM) használatának és az érzékeny vagy bizalmas fájlok védelmének megkezdéséhez engedélyezni kell a szolgáltatást."
author: cabailey
manager: mbaldwin
ms.date: 08/24/2016
ms.topic: article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: f8707e01-b239-4d1a-a1ea-0d1cf9a8d214
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 024a29d7c7db2e4c0578a95c93e22f8e7a5b173e
ms.openlocfilehash: d8ec823553934442ecb1e0a0b288eaa6d9c21ea6


---

# Az Azure Rights Management aktiválása

>*A következőkre vonatkozik: Azure Rights Management, Office 365*

Az [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] (Azure RMS) aktiválásakor a szervezete megkezdheti a fontos adatok védelmét az ezen adatvédelmi megoldást támogató alkalmazások és szolgáltatások használatával. A rendszergazdák ezenkívül kezelhetik és megfigyelhetik a szervezete tulajdonában lévő védett fájlokat és e-maileket. Az Office, a SharePoint és az Exchange szoftverekben lévő tartalomvédelmi szolgáltatások használatának és az érzékeny vagy bizalmas fájlok védelmének megkezdéséhez engedélyezni kell a [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] szolgáltatást.

Ha szeretne többet megtudni az Azure Rights Management szolgáltatásról annak aktiválása előtt, például, hogy milyen üzleti problémákat orvosol, melyek a tipikus használati esetek és hogyan működik, tekintse meg a [ Mi az az Azure Rights Management?](../understand-explore/what-is-azure-rms.md) című témakört.

> [!IMPORTANT]
> A [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] aktiválása előtt győződjön meg arról, hogy a szervezete olyan szolgáltatáscsomaggal rendelkezik, amely tartalmazza a [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] szolgáltatásokat. Ha nem rendelkezik, akkor nem tudja aktiválni az Azure RMS szolgáltatást.
>
> További információ: [Az Azure RMS-t támogató felhőalapú előfizetések](../get-started/requirements-subscriptions.md).

Az Azure RMS aktiválását követően a szervezetében lévő összes felhasználó tartalomvédelemmel láthatja el a fájljait, és az összes felhasználó megnyithatja (felhasználhatja) az Azure RMS által védett fájlokat. Azonban akár korlátozhatja is, ki alkalmazhat tartalomvédelmet azzal, hogy regisztrációs vezérlőket használ a szakaszos bevezetéshez. További információt a jelen cikk [Regisztrációs vezérlők konfigurálása szakaszos bevezetéshez](#configuring-onboarding-controls-for-a-phased-deployment) című szakaszában találhat.

A Rights Management felügyeleti portálból való aktiválásával kapcsolatos utasításokért válassza ki, hogy az Office 365 Felügyeleti központot (előnézet vagy klasszikus) vagy a klasszikus Azure felügyeleti portált kívánja használni:


- [Office 365 Felügyeleti központ – előnézet](activate-office365-preview.md)
- [Office 365 Felügyeleti központ – klasszikus](activate-office365-classic.md)
- [Klasszikus Azure-portál](activate-azure-classic.md)

Alternatív megoldásként a Windows PowerShellel is aktiválhatja a [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)]et:

1. Telepítse a Azure Rights Management felügyeleti eszközt, amely telepíti az Azure Rights Management felügyeleti modult. Az utasítások itt találhatók: [Az Azure Rights Managementhez készült Windows PowerShell telepítése](../deploy-use/install-powershell.md).

2. Futtassa egy Windows PowerShell-munkamenetből a [Connect-AadrmService](https://msdn.microsoft.com/library/windowsazure/dn629415.aspx) parancsot, és ha a rendszer kéri, adja meg a globális rendszergazdai fiók adatait az Azure RMS-bérlő számára.

3. Futtassa az [Enable-Aadrm](http://msdn.microsoft.com/library/windowsazure/dn629412.aspx) parancsot, amely aktiválja az Azure RMS-szolgáltatást.

## Regisztrációs vezérlők konfigurálása szakaszos bevezetéshez
Ha nem szeretné, hogy az összes felhasználó azonnal képes a fájlok számára védelmet biztosítani az Azure RMS használatával, felhasználóregisztrációs vezérlőket állíthat be a [Set-AadrmOnboardingControlPolicy](http://msdn.microsoft.com/library/azure/dn857521.aspx) Windows PowerShell-parancs segítségével. Ezt a parancsot az Azure RMS aktiválása előtt vagy után futtathatja.

> [!IMPORTANT]
> E parancs használatához legalább **2.1.0.0** verziójú [Azure RMS Windows PowerShell-modulra](http://go.microsoft.com/fwlink/?LinkId=257721) van szükség.
>
> A telepített verzió ellenőrzéséhez futtassa a **(Get-Module aadrm –ListAvailable).Version** parancsot

Ha például azt szeretné, hogy eleinte kizárólag az „Informatikai részleg” csoportban (objektumazonosító: fbb99ded-32a0-45f1-b038-38b519009503) lévő rendszergazdák tudjanak tesztelési célból tartalomvédelmet biztosítani, használja az alábbi parancsot:

```
Set-AadrmOnboardingControlPolicy – SecurityGroupObjectId fbb99ded-32a0-45f1-b038-38b519009503
```
Vegye figyelembe, hogy ezen konfigurációs beállítás esetén egy csoportot kell megadnia; nem határozhat meg egyéni felhasználókat.

Vagy ha azt szeretné, hogy csak a megfelelő Azure RMS-licenccel rendelkező felhasználók biztosíthassanak tartalomvédelmet:

```
Set-AadrmOnboardingControlPolicy -UseRmsUserLicense $true
```
Ezen regisztrációs vezérlők használatakor a szervezetben lévő összes felhasználó bármikor felhasználhatja a felhasználók egy része által védett tartalmakat, de nem biztosíthatnak tartalomvédelmet az ügyfélalkalmazásokból. Például az Office-ügyfélben nem látják az Azure RMS aktiválásakor automatikusan közzétett sablonokat vagy az Ön által esetlegesen konfigurált egyéni sablonokat.  A kiszolgálóoldali alkalmazások, például az Exchange, megvalósíthatják a saját, felhasználónkénti vezérlőiket az RMS-integrációhoz az azonos eredmények elérése érdekében.


## További lépések
Most, hogy aktiválta az [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] szolgáltatást a szervezete számára, az [Azure Rights Management deployment roadmap](../plan-design/deployment-roadmap.md) (Azure Rights Management üzembe helyezési menetrend) segítségével ellenőrizheti, hogy vannak-e további konfigurációs lépések, amelyeket érdemes lehet megtenni, mielőtt a felhasználók és rendszergazdák megkezdik az [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] használatát. 

Például lehet, hogy [egyéni sablonok](configure-custom-templates.md) segítségével meg szeretné könnyíteni a felhasználóknak, hogy információvédelmet alkalmazzanak a fájlokra, az [RMS-összekötő](deploy-rms-connector.md) telepítésével csatlakoztatni kívánja a helyi kiszolgálóit az [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] szolgáltatáshoz, és telepíteni kívánja a [Rights Management megosztóalkalmazást](../rms-client/sharing-app-windows.md), amely támogatja az összes fájltípus védelmét az összes eszközön. 

Az Office-szolgáltatások, például az Exchange Online és a SharePoint Online további konfigurációt igényelnek a tartalomvédelmi szolgáltatásaik (IRM) használatához. Információ arról, hogyan működnek együtt az alkalmazásai az [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] szolgáltatással: [Hogyan támogatják a különböző alkalmazások az Azure Rights Managementet?](../understand-explore/applications-support.md).




<!--HONumber=Aug16_HO4-->


