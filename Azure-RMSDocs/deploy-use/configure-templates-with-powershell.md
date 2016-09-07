---
title: "PowerShell-referencia az egyéni sablonokhoz | Azure RMS"
description: "A klasszikus Azure-portál sablonok létrehozására vagy módosítására szolgáló műveleteinek mindegyikét a parancssorból is végrehajthatja a PowerShell segítségével. Továbbá exportálhat és importálhat sablonokat, így a bérlők között másolhatja a sablonokat, vagy tömegesen szerkesztheti a sablonok összetett tulajdonságait, mint például a többnyelvű neveket és leírásokat."
author: cabailey
manager: mbaldwin
ms.date: 08/25/2016
ms.topic: article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 30ee2f77-ce16-4113-bcda-6089131849ec
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ad32910b482ca9d92b4ac8f3f123eda195db29cd
ms.openlocfilehash: 5068021b504e9f943c0d4e57f13d58fc5cb5d391


---



# PowerShell-referencia az egyéni sablonokhoz

>*A következőkre vonatkozik: Azure Rights Management, Office 365*

A klasszikus Azure-portál sablonok létrehozására vagy módosítására szolgáló műveleteinek mindegyikét a parancssorból is végrehajthatja a PowerShell segítségével. Továbbá exportálhat és importálhat sablonokat, így a bérlők között másolhatja a sablonokat, vagy tömegesen szerkesztheti a sablonok összetett tulajdonságait, mint például a többnyelvű neveket és leírásokat.

Az exportálás és importálás segítségével biztonsági másolatot is készíthet az egyéni sablonokról és vissza is állíthatja azokat. Ajánlott eljárásként rendszeresen készítsen biztonsági másolatot az egyéni sablonokról, így ha egy nem megfelelő módosítást hajt végre, egyszerűen visszaállíthat egy korábbi verziót.

> [!IMPORTANT]
> Ha a Windows PowerShell segítségével szeretne Azure RMS jogmegadási sablonokat létrehozni, az [Azure RMS-hez készült Windows PowerShell-modul](http://go.microsoft.com/fwlink/?LinkId=257721) legalább 2.0.0.0-s verziójával kell rendelkeznie.
> 
> Ha a PowerShell-modult korábban már telepítette, futtassa a következő parancsot egy PowerShell-ablakban a verziószám ellenőrzéséhez: `(Get-Module aadrm -ListAvailable).Version`

A telepítési utasításokért lásd: [Installing Windows PowerShell for Azure Rights Management](install-powershell.md) (Az Azure Rights Managementhez készült Windows PowerShell telepítése).

A sablonok létrehozását és kezelését támogató parancsmagok:

-   [Add-AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727075.aspx)

-   [Export-AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727078.aspx)

-   [Get-AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727079.aspx)

-   [Get-AadrmTemplateProperty](https://msdn.microsoft.com/library/azure/dn727081.aspx)

-   [Import-AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727077.aspx)

-   [New-AadrmRightsDefinition](https://msdn.microsoft.com/library/azure/dn727080.aspx)

-   [Remove-AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727082.aspx)

-   [Set-AadrmTemplateProperty](https://msdn.microsoft.com/library/azure/dn727076.aspx)



## Lásd még
[Egyéni sablonok konfigurálása az Azure Rights Management szolgáltatáshoz](configure-custom-templates.md)


<!--HONumber=Aug16_HO4-->


