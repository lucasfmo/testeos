---
title: "2. lépés&colon; HSM által védett kulcs áttelepítése HSM által védett kulccsá | Azure RMS"
description: 
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: c5bbf37e-f1bf-4010-a60f-37177c9e9b39
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 7a9c8b531ec342e7d5daf0cbcacd6597a79e6a55
ms.openlocfilehash: 7b531ebba1923653cb37c70a02fa888a40e96528


---

# 2. lépés: HSM által védett kulcs áttelepítése HSM által védett kulccsá

*A következőkre vonatkozik: Active Directory Rights Management Services, Azure Rights Management*


Ezek az utasítások az [AD RMS-ről az Azure Rights Managementre történő áttelepítés](migrate-from-ad-rms-to-azure-rms.md) részét képezik, és csak akkor alkalmazandók, ha az AD RMS-kulcs HSM-védelemmel van ellátva, és HSM-védelemmel ellátott bérlőkulccsal rendelkező Azure Rights Management-környezetbe kívánt áttelepítést végezni. 

Amennyiben nem ez a választott konfigurációs forgatókönyv, térjen vissza a [2. lépéshez. Exportálja a konfigurációs adatokat az AD RMS-ből, majd importálja az Azure RMS-be](migrate-from-ad-rms-phase1.md#step-2-export-configuration-data-from-ad-rms-and-import-it-to-azure-rms), és válasszon egy másik konfigurációt.

> [!NOTE]
> Ezek az utasítások feltételezik, hogy az AD RMS-kulcs modul általi védelemmel van ellátva. Ez az általános eset. Ha az AD RMS-kulcs OCS általi védelemmel van ellátva, lépjen kapcsolatba velünk az [AskIPTeam@microsoft.com](mailto: askipteam@microsoft.com?subject=AD%20RMS%20migration%20with%20OCS-protected%20key) címen az utasítások elvégzése előtt.

Ez egy kétlépéses eljárás, amellyel importálhatja az AD RMS konfigurációját az Azure RMS-be. Ennek eredményeképp jön létre az Ön által felügyelt (BYOK) Azure RMS-bérlőkulcs.

Először hozzon létre csomagot a HSM-kulccsal, hogy készen álljon az Azure RMS-be való átvitelre, majd importálja azt a konfigurációs adatokkal.

## 1. lépés: Csomag létrehozása a HSM-kulccsal, hogy készen álljon az Azure RMS-be való átvitelre

1.  Kövesse [Az Azure Rights Management-bérlőkulcs és megvalósítása](plan-implement-tenant-key.md) című témakör [A saját kulcs használatának (BYOK) megvalósítása](plan-implement-tenant-key.md#implementing-your-azure-rights-management-tenant-key) című szakaszának a **bérlőkulcs interneten keresztül történő létrehozását és továbbítását** ismertető eljárását, a következő kivételekkel:

    -   Ne kövesse a **Generate your tenant key (A bérlőkulcs létrehozása)** lépéseit, mert ennek megfelelője már rendelkezésre áll az AD RMS telepítéséből. Azonosítsa az AD RMS kiszolgálója által használt kulcsot a Thales-telepítésben, és használja ezt az áttelepítéskor. A Thales titkosított kulcsfájljai általában **key_(keyAppName)_(keyIdentifier)** néven találhatók meg a helyi kiszolgálón.

    -   Ne kövesse a **Transfer your tenant key to Azure RMS (A bérlőkulcs átvitele az Azure RMS-be)** lépéseit, amely az Add-AadrmKey parancsot használja.  Ehelyett az előkészített HSM-kulcsot akkor fogja átvinni, amikor az exportált megbízható közzétételi tartományt feltölti az Import-AadrmTpd paranccsal.

2.  Az internetkapcsolattal rendelkező munkaállomáson, a Windows PowerShell-munkamenetben kapcsolódjon újra az Azure RMS szolgáltatáshoz.

A HSM-kulcs Azure RMS szolgáltatáshoz történő előkészítése után készen áll a HSM kulcsfájl és az AD RMS konfigurációs adatainak importálására.

## 2. lépés: A konfigurációs adatok importálása az Azure RMS szolgáltatásba

1.  Az internetkapcsolattal rendelkező munkaállomáson, a Windows PowerShell-munkamenetben maradva töltse fel az első megbízható közzétételi tartomány .xml fájlját. Ha több megbízható közzétételi tartománya volt, és ezért egynél több .xml fájllal rendelkezik, válassza ki azt a fájlt, amelyik tartalmazza az Azure RMS szolgáltatásban az áttelepítés utáni tartalomvédelemre használni kívánt HSM-kulcsnak megfelelő exportált megbízható közzétételi tartományt. Használja az alábbi parancsot:

    ```
    Import-AadrmTpd -TpdFile <PathToTpdPackageFile> -ProtectionPassword -HsmKeyFile <PathToBYOKPackage> -Active $True -Verbose
    ```
    Például: **Import -TpdFile E:\no_key_tpd_contosokey1.xml  -HsmKeyFile E:\KeyTransferPackage-contosokey.byok -ProtectionPassword -Active $true -Verbose**

    Amikor a rendszer kéri, írja be a korábban megadott jelszót, és erősítse meg a művelet végrehajtására vonatkozó szándékát.

2.  A parancs befejeződésekor ismételje meg az 1. lépést a többi .xml fájl esetében, amelyeket a megbízható közzétételi tartományok exportálásával hozott létre. Ezen fájlok esetében azonban az **-Active** esetében **false** értéket kell beállítani az Import parancs futtatásakor.  Például: **Import -TpdFile E:\contosokey2.xml -HsmKeyFile E:\KeyTransferPackage-contosokey.byok -ProtectionPassword -Active $false -Verbose**

3.  A [Disconnect-AadrmService](http://msdn.microsoft.com/library/windowsazure/dn629416.aspx) parancsmagot használva bontsa a kapcsolatot az Azure RMS szolgáltatással:

    ```
    Disconnect-AadrmService
    ```

Folytassa a következővel: [3. lépés: Az RMS-bérlő aktiválása](migrate-from-ad-rms-phase1.md#step-3-activate-your-rms-tenant).




<!--HONumber=Jun16_HO4-->


