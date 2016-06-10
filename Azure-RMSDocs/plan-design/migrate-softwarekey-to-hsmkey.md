---
# required metadata

title: 2. lépés&colon; Szoftveres védelemmel ellátott kulcs áttelepítése HSM által védett kulccsá | Azure RMS
description:
keywords:
author: cabailey
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: c5f4c6ea-fd2a-423a-9fcb-07671b3c2f4f

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: esaggese
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# 2. lépés: Szoftveres védelemmel ellátott kulcs áttelepítése HSM által védett kulccsá

*A következőkre vonatkozik: Active Directory Rights Management Services, Azure Rights Management*


Ezek az utasítások az [AD RMS-ről az Azure Rights Managementre történő áttelepítés](migrate-from-ad-rms-to-azure-rms.md) részét képezik, és csak akkor alkalmazandók, ha az AD RMS-kulcs szoftveres védelemmel van ellátva, és HSM-védelemmel ellátott bérlőkulccsal rendelkező Azure Rights Management-környezetbe kívánt áttelepítést végezni. 

Amennyiben nem ez a választott konfigurációs forgatókönyv, térjen vissza a [2. lépéshez. Exportálja a konfigurációs adatokat az AD RMS-ből, majd importálja azokat az Azure RMS-be](migrate-from-ad-rms-to-azure-rms.md#step-2-export-configuration-data-from-ad-rms-and-import-it-to-azure-rms), és válasszon egy másik konfigurációt.

Ez egy háromlépéses eljárás, amellyel importálhatja az AD RMS konfigurációját az Azure RMS-be. Ennek eredményeképp jön létre az Ön által felügyelt (BYOK) Azure RMS-bérlőkulcs.

Először nyerje ki a kiszolgálólicenc-tanúsítványt (SLC kulcsot) a konfigurációs adatokból, és vigye át a kulcsot egy helyszíni Thales HSM-be, majd hozzon létre belőle egy csomagot, és vigye át a HSM-kulcsot az Azure RMS-re, végül importálja a konfigurációs adatokat.

## 1. lépés: Az SLC kinyerése a konfigurációs adatokból és a kulcs importálása a helyszíni HSM-be

1.  Kövesse a [Planning and Implementing Your Azure Rights Management Tenant Key (Az Azure Rights Management-bérlőkulcs tervezése és megvalósítása)](plan-implement-tenant-key.md) című témakör [Implementing bring your own key (BYOK) (A saját kulcs használatának (BYOK) megvalósítása)](plan-implement-tenant-key.md#BKMK_ImplementBYOK) szakaszának alábbi lépéseit:

    -   **Generate and transfer your tenant key – over the Internet (A bérlőkulcs létrehozása és átvitele – az interneten keresztül)**: **Prepare your Internet-connected workstation (Az internetre kapcsolódó munkaállomás előkészítése)**

    -   **Generate and transfer your tenant key – over the Internet (A bérlőkulcs létrehozása és átvitele – az interneten keresztül)**: **Prepare your Internet-connected workstation (A nem kapcsolódó munkaállomás előkészítése)**

    Ne kövesse a bérlőkulcs létrehozása vonatkozó utasításokat, mert ennek megfelelője már rendelkezésre áll az exportált konfigurációs adatok .xml fájljában. Ehelyett egy olyan parancsot fog futtatni, amely kinyeri ezt a kulcsot a fájlból és importálja a helyszíni HSM-be.

2.  A kapcsolat nélküli munkaállomáson futtassa az alábbi parancsot:

    ```
    KeyTransferRemote.exe -ImportRmsCentrallyManagedKey -TpdFilePath <TPD> -ProtectionPassword -KeyIdentifier <KeyID> -ExchangeKeyPackage <BYOK-KEK-pka-Region> -NewSecurityWorldPackage <BYOK-SecurityWorld-pkg-Region>
    ```
    Például Észak-Amerika esetében: **KeyTransferRemote.exe -ImportRmsCentrallyManagedKey -TpdFilePath E:\contosokey1.xml -ProtectionPassword -KeyIdentifier contosorms1key –- -ExchangeKeyPackage &lt;BYOK-KEK-pka-NA-1&gt; -NewSecurityWorldPackage &lt;BYOK-SecurityWorld-pkg-NA-1&gt;**

    További információ:

    -   Az ImportRmsCentrallyManagedKey paraméter azt jelzi, hogy ez a művelet az SLC-kulcs importálását célozza.

    -   Ha nem adja meg a jelszót a parancsban, a rendszer kérni fogja a megadását.

    -   A KeyIdentifier paraméter egy rövid kulcsnév, amely a kulcsfájl nevét hozza létre. Ehhez csak kisbetűs ASCII-karakterek használhatók.

    -   Az ExchangeKeyPackage paraméter egy régióspecifikus kulcscsere-kulcs- (KEK)-csomagot határoz meg, amelynek a neve BYOK-KEK-pkg-vel kezdődik.

    -   A NewSecurityWorldPackage egy régióspecifikus biztonságivilág-csomagot határoz meg, amelynek a neve BYOK-SecurityWorld-pkg-vel kezdődik.

    Ezen parancs eredménye a következő lesz:

    -   Egy HSM-kulcsfájl: %NFAST_KMDATA%\local\key_mscapi_&lt;kulcsazonosító&gt;

    -   RMS-konfigurációs adatfájl az SLC nélkül: %NFAST_KMDATA%\local\no_key_tpd_&lt;kulcsazonosító&gt;.xml

3.  Ha egynél több RMS-konfigurációs adatfájllal rendelkezik, végezze el újra a 2. lépést minden fennmaradó ilyen fájlhoz.

Miután az SLC-t kinyerte és egy HSM-alapú kulccsá alakította, készen áll a csomag létrehozására és az Azure RMS-be való importálásra.

## 2. lépés: Csomag létrehozása a HSM-kulcsból és átvitele az Azure RMS-re

1.  Kövesse a [Planning and Implementing Your Azure Rights Management Tenant Key (Az Azure Rights Management-bérlőkulcs tervezése és megvalósítása)](plan-implement-tenant-key.md) című témakör [Implementing bring your own key (BYOK) (A saját kulcs használatának (BYOK) megvalósítása)](plan-implement-tenant-key.md#BKMK_ImplementBYOK) szakaszának alábbi lépéseit:

    -   **Generate and transfer your tenant key – over the Internet (A bérlőkulcs létrehozása és átvitele – az interneten keresztül)**: **Prepare your tenant key for transfer (A bérlőkulcs előkészítése az átvitelre)**

    -   **Generate and transfer your tenant key – over the Internet (A bérlőkulcs létrehozása és átvitele – az interneten keresztül)**: **Transfer your tenant key to Azure RMS (A bérlőkulcs átvitele az Azure RMS szolgáltatásba)**

A HSM-kulcs Azure RMS szolgáltatásba történő átvitele után készen áll az AD RMS konfigurációs adatainak importálására, amelyek csak az újonnan átvitt bérlőkulcsra irányuló mutatót tartalmaznak.

## 3. rész: A konfigurációs adatok importálása az Azure RMS szolgáltatásba

1.  Az internethez csatlakoztatott munkaállomáson és a Windows PowerShell-munkamenetben másolja át az RMS konfigurációs fájljait az SLC nélkül (az internethez nem csatlakozó munkaállomásról: %NFAST_KMDATA%\local\no_key_tpd_&lt;kulcsazonosító&gt;.xml)

2.  Töltse fel az első fájlt. Ha több megbízható közzétételi tartománya volt, és ezért egynél több .xml fájllal rendelkezik, válassza ki azt a fájlt, amelyik tartalmazza az Azure RMS szolgáltatásban az áttelepítés utáni tartalomvédelemre használni kívánt HSM-kulcsnak megfelelő exportált megbízható közzétételi tartományt. Használja az alábbi parancsot:

    ```
    Import-AadrmTpd -TpdFile <PathToNoKeyTpdPackageFile> -ProtectionPassword -HsmKeyFile <PathToKeyTransferPackage> -Active $true -Verbose
    ```
    Például: **Import -TpdFile E:\no_key_tpd_contosorms1key.xml -ProtectionPassword -HsmKeyFile E:\KeyTransferPackage-contosorms1key.byok -Active $true -Verbose**

    Amikor a rendszer kéri, írja be a korábban megadott jelszót, és erősítse meg a művelet végrehajtására vonatkozó szándékát.

3.  A parancs befejezésekor ismételje meg a 2. lépést a többi olyan .xml fájl esetében, amelyet a megbízható közzétételi tartományok exportálásával hozott létre. Ezen fájlok esetében azonban az **-Active** esetében **false** értéket kell beállítani az Import parancs futtatásakor. Például: **Import -TpdFile E:\no_key_tpd_contosorms2key.xml -ProtectionPassword -HsmKeyFile E:\KeyTransferPackage-contosorms1key.byok -Active $false -Verbose**

4.  A [Disconnect-AadrmService](http://msdn.microsoft.com/library/windowsazure/dn629416.aspx) parancsmagot használva bontsa a kapcsolatot az Azure RMS szolgáltatással:

    ```
    Disconnect-AadrmService
    ```

Folytassa a következővel: [3. lépés: Az RMS-bérlő aktiválása](migrate-from-ad-rms-to-azure-rms.md#BKMK_Step3Migration).




<!--HONumber=Apr16_HO4-->


