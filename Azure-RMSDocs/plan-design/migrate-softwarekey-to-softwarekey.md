---
# required metadata

title: 2. lépés&colon; Szoftveres védelemmel ellátott kulcs áttelepítése szoftveres védelemmel rendelkező kulccsá | Azure RMS
description:
keywords:
author: cabailey
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 81a5cf4f-c1f3-44a9-ad42-66e95f33ed27

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: esaggese
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---


# 2. lépés: Szoftveres védelemmel ellátott kulcs áttelepítése szoftveres védelemmel rendelkező kulccsá

*A következőkre vonatkozik: Active Directory Rights Management Services, Azure Rights Management*


Ezek az utasítások az [AD RMS-ről az Azure Rights Managementre történő áttelepítés](migrate-from-ad-rms-to-azure-rms.md) részét képezik, és csak akkor alkalmazandók, ha az AD RMS-kulcs szoftveres védelemmel van ellátva, és szoftveres védelemmel ellátott bérlőkulccsal rendelkező Azure Rights Management-környezetbe kívánt áttelepülni. 

Amennyiben nem ez a választott konfigurációs forgatókönyv, térjen vissza a [2. lépéshez. Exportálja a konfigurációs adatokat az AD RMS-ből, majd importálja azokat az Azure RMS-be](migrate-from-ad-rms-to-azure-rms.md#step-2-export-configuration-data-from-ad-rms-and-import-it-to-azure-rms), és válasszon egy másik konfigurációt.

Az alábbi eljárással importálhatja az AD RMS konfigurációját az Azure RMS-be. Ennek eredményeképp jön létre a Microsoft által felügyelt Azure RMS-bérlőkulcs.

## Konfigurációs adatok importálása az Azure RMS szolgáltatásba

1.  Egy internethez csatlakoztatott munkaállomáson töltse le és telepítse a Windows PowerShell-modult az Azure RMS-hez (minimális verzió: 2.1.0.0), amelynek része az [Import-AadrmTpd](http://msdn.microsoft.com/library/azure/dn857523.aspx) parancsmag.

    > [!TIP]
    > Ha már korábban letöltötte és telepítette a modult, ellenőrizze a verziószámot a következő futtatásával: `(Get-Module aadrm -ListAvailable).Version`

    A telepítési utasításokért lásd: [Installing Windows PowerShell for Azure Rights Management](../deploy-use/install-powershell.md) (Az Azure Rights Managementhez készült Windows PowerShell telepítése)..

2.  **Futtatás rendszergazdaként** beállítással indítsa el a Windows PowerShellt, majd a [Connect-AadrmService](http://msdn.microsoft.com/library/azure/dn629415.aspx) parancsmagot használva csatlakozzon az Azure RMS-hez:

    ```
    Connect-AadrmService
    ```
    A kérésre adja meg a [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] bérlői rendszergazdai hitelesítő adatait (jellemzően egy olyan fiókot fog használni, amely globális rendszergazda az Azure Active Directoryben vagy az Office 365-ben).

3.  Az [Import-AadrmTpd](http://msdn.microsoft.com/library/azure/dn857523.aspx) parancsmaggal töltse fel az első megbízható közzétételi tartomány .xml fájlját. Ha több megbízható közzétételi tartománya volt és ezért egynél több .xml fájllal rendelkezik, válassza ki azt a fájlt, amely az Azure RMS szolgáltatásban az áttelepítés utáni tartalomvédelemre használni kívánt exportált megbízható közzétételi tartományt tartalmazza. Használja az alábbi parancsot:

    ```
    Import-AadrmTpd -TpdFile <PathToTpdPackageFile> -ProtectionPassword -Active $True -Verbose
    ```
    Például: **Import-AadrmTpd -TpdFile E:\contosokey1.xml -ProtectionPassword -Active $true -Verbose**

    Amikor a rendszer kéri, írja be a korábban megadott jelszót, és erősítse meg a művelet végrehajtására vonatkozó szándékát.

4.  A parancs befejeződésekor ismételje meg a 3. lépést a többi .xml fájl esetében, amelyeket a megbízható közzétételi tartományok exportálásával hozott létre. Ezen fájlok esetében azonban az **-Active** esetében **false** értéket kell beállítani az Import parancs futtatásakor. Például: **Import-AadrmTpd -TpdFile E:\contosokey2.xml -ProtectionPassword -Active $false -Verbose**

5.  A [Disconnect-AadrmService](http://msdn.microsoft.com/library/azure/dn629416.aspx) parancsmagot használva bontsa a kapcsolatot az Azure RMS szolgáltatással:

    ```
    Disconnect-AadrmService
    ```

Folytassa a következővel: [3. lépés: Az RMS-bérlő aktiválása](migrate-from-ad-rms-to-azure-rms.md#BKMK_Step3Migration).



<!--HONumber=Apr16_HO4-->


