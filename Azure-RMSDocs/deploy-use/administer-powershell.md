---
title: "Administering Azure Rights Management by Using Windows PowerShell (Az Azure Rights Management felügyelete a Windows PowerShell használatával) | Azure RMS"
description: 
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: a890e04a-4b70-41b5-8d5f-3c210a669faa
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 0f355da35dff62ecee111737eb1793ae286dc93e
ms.openlocfilehash: bf1f684bc394ec3a1025f8c9ed3e57d07c598125


---

# Administering Azure Rights Management by Using Windows PowerShell (Az Azure Rights Management felügyelete a Windows PowerShell használatával)

*A következőkre vonatkozik: Azure Rights Management, Office 365*

Bár aktiválhatja a Microsoft [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] (Azure RMS) szolgáltatást az [!INCLUDE[o365_2](../includes/o365_2_md.md)] felügyeleti központja vagy a klasszikus Azure-portál használatával, használhatja az [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] (AADRM) Windows PowerShell-modulját is erre a célra.

A [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] aktiválása után a szolgáltatás további felügyelete esetlegesen nem is szükséges. Néhány speciális konfigurációs forgatókönyv esetén azonban szükség lehet az [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] Windows PowerShell-moduljának használatára. Az alábbi táblázat azon speciális konfigurációs forgatókönyvek közül sorol fel néhányat, amelyek a Windows PowerShellt használják. Az elérhető parancsmagok teljes listája és azok bővebb ismertetése: [Azure Rights Management Cmdlets](http://msdn.microsoft.com/library/azure/dn629398.aspx) (Azure RMS-parancsmagok).

> [!NOTE]
> Ha telepíteni szeretné az [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)]-hez készült Windows PowerShell-modult, tekintse meg az [Installing Windows PowerShell for Azure Rights Management](install-powershell.md) (Az Azure Rights Managementhez készült Windows PowerShell telepítése) című témakört.

Létezik továbbá egy kiegészítő Windows PowerShell-modul is, az **RMSProtection**, amely az Azure RMS-t és az AD RMS-t is támogatja. Ez a modul támogatja a védelem alkalmazását és eltávolítását egyszerre több fájl esetén, így például tömeges védelmet valósíthat meg egy mappában található összes fájlra. További információ: [Scripting options for super users (Felügyelőkre vonatkozó parancsfájl-beállítások)](configure-super-users.md#scripting-options-for-super-users) szakasz, [Configuring super users for Azure Rights Management and discovery services or data recovery](configure-super-users.md) (Felügyelők konfigurálása az Azure Rights Management és a felderítési szolgáltatások vagy adat-helyreállítás számára).

|Ha szeretne/szeretné...|...használja az alábbi parancsmagokat|
|-------------------|------------------------------|
|Áttelepíteni a helyszíni Rights Management (AD RMS vagy Windows RMS) rendszerből az [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)]-be.|[Import-AadrmTpd](http://msdn.microsoft.com/library/azure/dn857523.aspx)|
|Csatlakozni vagy a kapcsolatot bontani a [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] szolgáltatással szervezete számára.|[Connect-AadrmService](http://msdn.microsoft.com/library/azure/dn629415.aspx)<br /><br />[Disconnect-AadrmService](http://msdn.microsoft.com/library/azure/dn629416.aspx)|
|Létrehozni és felügyelni saját bérlőkulcsát – azaz a BYOK forgatókönyv mellett döntött.|[Add-AadrmKey](http://msdn.microsoft.com/library/azure/dn629418.aspx)<br /><br />[Get-AadrmKeys](http://msdn.microsoft.com/library/azure/dn629420.aspx)|
|Aktiválni vagy inaktiválni a [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] szolgáltatást szervezete számára.|[Enable-Aadrm](http://msdn.microsoft.com/library/azure/dn629412.aspx)<br /><br />[Disable-Aadrm](http://msdn.microsoft.com/library/azure/dn629422.aspx)|
|Letiltani vagy engedélyezni a dokumentumkövető oldalt az Azure Rights Management számára.|[Disable-AadrmDocumentTrackingFeature](https://msdn.microsoft.com/library/azure/mt548471.aspx)<br /><br />[Enable-AadrmDocumentTrackingFeature](https://msdn.microsoft.com/library/azure/mt548469.aspx)<br /><br />[Get-AadrmDocumentTrackingFeature](https://msdn.microsoft.com/library/azure/mt548470.aspx)|
|Regisztrációs vezérlőket konfigurálni az Azure Rights Management szakaszos bevezetéshez.|[Get-AadrmOnboardingControlPolicy](http://msdn.microsoft.com/library/azure/dn857522.aspx)<br /><br />[Set-AadrmOnboardingControlPolicy](http://msdn.microsoft.com/library/azure/dn857521.aspx)|
|Jogmegadási sablonokat létrehozni és felügyelni szervezete számára.|[Add-AadrmTemplate](http://msdn.microsoft.com/library/azure/dn727075.aspx)<br /><br />[Export-AadrmTemplate](http://msdn.microsoft.com/library/azure/dn727078.aspx)<br /><br />[Get-AadrmTemplate](http://msdn.microsoft.com/library/azure/dn727079.aspx)<br /><br />[Get-AadrmTemplateProperty](http://msdn.microsoft.com/library/azure/dn727081.aspx)<br /><br />[Import-AadrmTemplate](http://msdn.microsoft.com/library/azure/dn727077.aspx)<br /><br />[New-AadrmRightsDefinition](http://msdn.microsoft.com/library/azure/dn727080.aspx)<br /><br />[Remove-AadrmTemplate](http://msdn.microsoft.com/library/azure/dn727082.aspx)<br /><br />[Set-AadrmTemplateProperty](http://msdn.microsoft.com/library/azure/dn727076.aspx)|
|Beállítani azon napok maximális számát, ameddig a szervezete által védett tartalmak hozzáférhetők internetkapcsolat nélkül (használati licenc érvényességi időtartama).|[Get-AadrmMaxUseLicenseValidityTime](https://msdn.microsoft.com/library/azure/dn932062.aspx)<br /><br />[Set-AadrmMaxUseLicenseValidityTime](https://msdn.microsoft.com/library/azure/dn932063.aspx)|
|Kezelni a [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] felügyelői funkcióját a szervezethez.|[Enable-AadrmSuperUserFeature](https://msdn.microsoft.com/library/azure/dn629400.aspx)<br /><br />[Disable-AadrmSuperUserFeature](https://msdn.microsoft.com/library/azure/dn629428.aspx)<br /><br />[Add-AadrmSuperUser](http://msdn.microsoft.com/library/azure/dn629411.aspx)<br /><br />[Get-AadrmSuperUser](https://msdn.microsoft.com/library/azure/dn629408.aspx)<br /><br />[Remove-AadrmSuperUser](https://msdn.microsoft.com/library/azure/dn629405.aspx)<br /><br />[Set-AadrmSuperUserGroup](https://msdn.microsoft.com/library/azure/mt653943.aspx)<br /><br />[Get-AadrmSuperUserGroup](https://msdn.microsoft.com/library/azure/mt653942.aspx)<br /><br />[Clear-AadrmSuperUserGroup](https://msdn.microsoft.com/library/azure/mt653944.aspx)|
|Felügyelni a szervezetéhez kapcsolódó [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] szolgáltatás felügyeletére jogosult felhasználókat és csoportokat.|[Add-AadrmRoleBasedAdministrator](http://msdn.microsoft.com/library/azure/dn629417.aspx)<br /><br />[Get-AadrmRoleBasedAdministrator](https://msdn.microsoft.com/library/azure/dn629407.aspx)<br /><br />[Remove-AadrmRoleBasedAdministrator](https://msdn.microsoft.com/library/azure/dn629424.aspx)|
|Hozzáférni a szervezetéhez kapcsolódó [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] szolgáltatás adminisztratív feladatainak naplójához.|[Get-AadrmAdminLog](https://msdn.microsoft.com/library/azure/dn629430.aspx)|
|Naplózni és elemezni az [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] használati naplózását.|[Get-AadrmUserLog](https://msdn.microsoft.com/library/azure/mt653941.aspx)|
|Megjeleníteni a szervezetéhez tartozó aktuális [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] szolgáltatás konfigurációját.|[Get-AadrmConfiguration](http://msdn.microsoft.com/library/azure/dn629410.aspx)|
|Áttelepíteni szervezetét a [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] szolgáltatásból egy helyszíni AD RMS telepítésbe.|[Set-AadrmMigrationUrl](https://msdn.microsoft.com/library/azure/dn629429.aspx)<br /><br />[Get-AadrmMigrationUrl](http://msdn.microsoft.com/library/azure/dn629403.aspx)|






<!--HONumber=Jun16_HO4-->


