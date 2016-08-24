---
title: "Az Azure Rights Managementhez készült Windows PowerShell telepítése | Azure RMS"
description: 
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 08/17/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 0d665ed6-b1de-4d63-854a-bc57c1c49844
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 5f8672b1f4d8e1b5ed707e89e88c9ba50d24f486
ms.openlocfilehash: 4120aeeae7c2c48168e4f01de6558da5034bf019


---

# Az Azure Rights Managementhez készült Windows PowerShell telepítése

*A következőkre vonatkozik: Azure Rights Management, Office 365*

Az alábbi információk segítséget nyújtanak a Microsoft [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] (Azure RMS) szolgáltatáshoz készült Windows PowerShell telepítéséhez.

Ezzel a PowerShell-modullal felügyelheti az [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] szolgáltatást a parancssorból olyan internetkapcsolattal rendelkező számítógép használatával, amely megfelel az alábbi szakaszban felsorolt feltételeknek. Az [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] szolgáltatáshoz készült Windows PowerShell támogatja az automatizálási parancsfájlokat, illetve speciális konfigurációs forgatókönyvek esetén válhat szükségessé a használata. A modul által támogatott felügyeleti feladatokkal és konfigurációkkal kapcsolatos további információ: [Az Azure Rights Management felügyelete a Windows PowerShell használatával](administer-powershell.md).

## Előfeltételek
Ez a táblázat az [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)]-hez készült Windows PowerShell telepítéséhez és használatához szükséges előfeltételeket ismerteti.

|Követelmény|További információ|
|---------------|--------------------|
|A [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] felügyeleti modult támogató Windows-verzió.|A támogatott operációs rendszerek listáját az [Azure Rights Management Administration Tool letöltési oldalának](http://go.microsoft.com/fwlink/?LinkId=257721) **Rendszerkövetelmények** című szakaszában tekintheti meg.|
|A Windows PowerShell minimális verziója: 2.0|A [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] felügyeleti modul támogatása a Windows PowerShell 2.0-s verziójától érhető el.<br /><br />Alapértelmezés szerint a legtöbb Windows operációs rendszer a Windows PowerShell legalább 2.0-s verzióját telepíti. Ha telepítenie kell a Windows PowerShell 2.0-s verzióját, olvassa el [A Windows PowerShell 2.0 telepítése](http://msdn.microsoft.com/library/ff637750.aspx) című témakört.<br /><br />Tipp: A futtatott Windows PowerShell verziójának megtekintéséhez írja be a következő karakterláncot egy Windows PowerShell-munkamenetben: `$PSVersionTable`.|
|A Microsoft .NET-keretrendszer minimális verziója: 4.5<br /><br />Megjegyzés: A Microsoft .NET-keretrendszer ezen verzióját tartalmazzák az újabb operációs rendszerek, így manuálisan csak akkor kell telepíteni, ha az ügyfél operációs rendszer a Windows 8.0-nál korábbi, illetve ha a kiszolgálói operációs rendszere a Windows Server 2012 előtti.|Amennyiben a Microsoft .NET-keretrendszer minimális verziója még nem lett telepítve, letöltheti a [Microsoft .NET-keretrendszer 4.5-ös verzióját](http://www.microsoft.com/download/details.aspx?id=30653).<br /><br />A Microsoft .NET-keretrendszer ezen minimális verziója a [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] felügyeleti modul által használt bizonyos osztályokhoz szükséges.|

> [!NOTE]
> A Rights Management felügyeleti moduljának 2.5.0.0-s verziójától kezdve nincs szükség a Microsoft Online Services - Bejelentkezési segéd szolgáltatás használatára.
> 
> Ha a Rights Management felügyeleti moduljának egy korábbi verziója van telepítve, a legújabb verzió telepítése előtt távolítsa el a **Windows Azure AD Rights Management Administration** programot a **Programok és szolgáltatások** területen.


## A Rights Management felügyeleti modul telepítése

1.  Nyissa meg a Microsoft letöltőközpontot, és töltse le az [Azure Rights Management Administration Tool](https://go.microsoft.com/fwlink/?LinkId=257721) eszközt, amelynek része az [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] felügyeleti modul a Windows PowerShellhez.

2.  A [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)]-telepítőfájl letöltéséhez és mentéséhez használt helyi mappában kattintson duplán a platformhoz letöltött végrehajtható fájlra (WindowsAzureADRightsManagementAdministration_x64 vagy WindowsAzureADRightsManagementAdministration_x86.exe) az Azure AD Rights Management rendszergazdai telepítési varázsló elindításához.

3.  Fejezze be a varázslót.

Az [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] szolgáltatáshoz készült Windows PowerShell telepítése megtörtént.

## További lépések
A rendelkezésre álló parancsmagok megtekintéséhez indítsa el a Windows PowerShellt a **Futtatás rendszergazdaként** lehetőséggel, majd írja be az alábbi parancsot:

```
Get-Command -Module aadrm
```
Használja a `the Get-Help <cmdlet_name>` parancsot egy adott parancsmag súgójának a megtekintéséhez.

További információk:

-   A rendelkezésre álló parancsmagok teljes listája: [Azure Rights Management Cmdlets](https://msdn.microsoft.com/library/windowsazure/dn629398.aspx) (Azure Rights Management-parancsmagok).

-   A Windows PowerShellt támogató fő konfigurációs forgatókönyvek listája: [Administering Azure Rights Management by Using Windows PowerShell](administer-powershell.md) (Az Azure Rights Management felügyelete a Windows PowerShell használatával).

Az [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] szolgáltatást konfiguráló parancsok futtatása előtt a [Connect-AadrmService](https://msdn.microsoft.com/library/windowsazure/dn629415.aspx) parancsmag használatával csatlakoznia kell a szolgáltatáshoz. Ha befejezte a kívánt konfigurációs parancsok futtatását, a [Disconnect-AadrmService](https://msdn.microsoft.com/library/windowsazure/dn629416.aspx) parancsmag használatával megszüntetheti a szolgáltatással létesített kapcsolatot.

> [!NOTE]
> Ha a [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] még nem lett aktiválva, az aktiválást végrehajthatja a szolgáltatáshoz való kapcsolódás után is az [Enable-Aadrm](https://msdn.microsoft.com/library/windowsazure/dn629412.aspx) parancsmag használatával.

## Lásd még
[Administering Azure Rights Management by Using Windows PowerShell (Az Azure Rights Management felügyelete a Windows PowerShell használatával)](administer-powershell.md)



<!--HONumber=Aug16_HO3-->


