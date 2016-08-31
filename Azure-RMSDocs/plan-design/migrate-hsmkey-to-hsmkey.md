---
title: "2. lépés&colon; HSM által védett kulcs áttelepítése HSM által védett kulccsá | Azure RMS"
description: "Ezek az utasítások az AD RMS-ről az Azure Rights Managementre történő áttelepítés részét képezik, és csak akkor alkalmazandók, ha az AD RMS-kulcs HSM-védelemmel van ellátva, és HSM-védelemmel ellátott bérlőkulccsal rendelkező Azure Rights Management-környezetbe kíván áttelepítést végezni az Azure Key Vaultban."
author: cabailey
manager: mbaldwin
ms.date: 08/24/2016
ms.topic: article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: c5bbf37e-f1bf-4010-a60f-37177c9e9b39
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 024a29d7c7db2e4c0578a95c93e22f8e7a5b173e
ms.openlocfilehash: 690729d16358b7b997d9cd1fd8cabed22ce78df4


---

# 2. lépés: HSM által védett kulcs áttelepítése HSM által védett kulccsá

>*A következőkre vonatkozik: Active Directory Rights Management Services, Azure Rights Management*


Ezek az utasítások az [AD RMS-ről az Azure Rights Managementre történő áttelepítés](migrate-from-ad-rms-to-azure-rms.md) részét képezik, és csak akkor alkalmazandók, ha az AD RMS-kulcs HSM-védelemmel van ellátva, és HSM-védelemmel ellátott bérlőkulccsal rendelkező Azure Rights Management-környezetbe kívánt áttelepítést végezni az Azure Key Vaultban. 

Amennyiben nem ez a választott konfigurációs forgatókönyv, térjen vissza a [2. lépéshez. Exportálja a konfigurációs adatokat az AD RMS-ből, majd importálja az Azure RMS-be](migrate-from-ad-rms-phase1.md#step-2-export-configuration-data-from-ad-rms-and-import-it-to-azure-rms), és válasszon egy másik konfigurációt.

> [!NOTE]
> Ezek az utasítások feltételezik, hogy az AD RMS-kulcs modul általi védelemmel van ellátva. Ez a leggyakoribb eset. 

Ez egy kétlépéses eljárás, amellyel importálhatja az AD RMS konfigurációját az Azure RMS-be. Ennek eredményeképp jön létre az Ön által felügyelt (BYOK) Azure RMS-bérlőkulcs.

Mivel az Azure RMS-bérlőkulcs tárolását és felügyeletét az Azure Key Vault végzi, az áttelepítés ezen része az Azure Key RMS-en kívül Azure Key Vault-beli adminisztrációt is igényel. Ha az Azure Key Vaultot nem Ön, hanem a szervezet egy másik rendszergazdája felügyeli, vele együttműködve kell elvégeznie ezt az eljárást.

Mielőtt elkezdené, győződjön meg arról, hogy a szervezet rendelkezik egy Azure Key Vaultban létrehozott kulcstartóval, és támogatja a HMS-védelemmel ellátott kulcsok használatát. Bár az áttelepítés elvégzéséhez nem szükséges, Azure RMS-hez dedikált kulcstartó használata ajánlott. A kulcstartó annak engedélyezésére lesz konfigurálva, hogy az Azure RMS hozzáférjen, így a kulcstartó tárolóit csak Azure RMS-kulcsokra kell korlátozni.


> [!TIP]
> Ha Ön végzi el az Azure Key Vault konfigurálásához szükséges lépéseket, de nem ismeri az Azure ezen szolgáltatását, először tekintse át a [Bevezetés az Azure Key Vault használatába](https://azure.microsoft.com/documentation/articles/key-vault-get-started/) című témakörben leírtakat. 


## 1. rész: A HSM-kulcs átvitele az Azure Key Vaultba

Az alábbi műveleteket az Azure Key Vault rendszergazdájának kell elvégeznie.

1.  Kövesse az Azure Key Vault-dokumentáció [Implementing bring your own key (BYOK) for Azure Key Vault](https://azure.microsoft.com/documentation/articles/key-vault-hsm-protected-keys/#implementing-bring-your-own-key-byok-for-azure-key-vault) (A saját kulcs használatának (BYOK) megvalósítása) című szakaszának lépéseit, az alábbi kivétellel:

    - Ne végezze el a **Generate your tenant key** (A bérlőkulcs létrehozása) szakasz lépéseit, mert ennek megfelelője már rendelkezésre áll az AD RMS telepítéséből. Ehelyett azonosítsa az AD RMS kiszolgálója által használt kulcsot a Thales-telepítésben, és használja ezt az áttelepítéskor. A Thales titkosított kulcsfájljai általában **key<*keyAppName*><*keyIdentifier*>** néven találhatók meg a helyi kiszolgálón.

    Miután a kulcs feltöltődött az Azure Key Vaultba, megjelennek a kulcs tulajdonságai, köztük a kulcs azonosítója. Az azonosító az alábbihoz fog hasonlítani: https://contosorms-kv.vault.azure.net/keys/contosorms-byok/aaaabbbbcccc111122223333. Jegyezze fel ezt az URL-címet, mert az Azure RMS-rendszergazdának szüksége lesz rá az Azure RMS arra való beállításához, hogy ezt a kulcsot használja a bérlőkulcsához.

2. Az internetre kapcsolódó munkaállomásban indítson el egy PowerShell-munkamenetet, és a [Set-AzureRmKeyVaultAccessPolicy](https://msdn.microsoft.com/library/mt603625.aspx ) parancsmag segítségével engedélyezze az Azure RMS-bérlőkulcsot tároló kulcstartó elérését az Azure RMS egyszerű szolgáltatás (Microsoft.Azure.RMS) számára. A szükséges engedélyek a következők: visszafejtés, titkosítás, unwrapkey, wrapkey, ellenőrzés és aláírás.
    
    Ha például az Azure RMS-hez készített kulcstartónak a contoso-byok-kl nevet adta, az erőforráscsoport neve pedig contoso-byok-ecs, az alábbi parancsot kell futtatni:
    
        Set-AzureRmKeyVaultAccessPolicy -VaultName "contoso-byok-kv" -ResourceGroupName "contoso-byok-rg" -ServicePrincipalName Microsoft.Azure.RMS -PermissionsToKeys decrypt,encrypt,unwrapkey,wrapkey,verify,sign


Sikeresen előkészítette az Azure RMS szolgáltatáshoz tartozó HSM-kulcsot az Azure Key Vaultban. Készen áll az AD RMS konfigurációs adatainak importálására.

## 2. rész: A konfigurációs adatok importálása az Azure RMS szolgáltatásba

Az alábbi műveleteket az Azure RMS szolgáltatás rendszergazdájának kell elvégeznie.

1.  Az internetre kapcsolódó munkaállomáson és a PowerShell-munkamenetben csatlakoztassa az Azure RMS szolgáltatást a [Connnect-AadrmService](https://msdn.microsoft.com/library/dn629415.aspx ) parancsmag segítségével.
    
    Ezután az [Import-AadrmTpd](https://msdn.microsoft.com/library/dn857523.aspx) parancsmaggal töltse fel az első megbízható közzétételi tartomány .xml fájlját. Ha több megbízható közzétételi tartománya volt, és ezért egynél több .xml fájllal rendelkezik, válassza ki azt a fájlt, amelyik tartalmazza az Azure RMS szolgáltatásban az áttelepítés utáni tartalomvédelemre használni kívánt HSM-kulcsnak megfelelő exportált megbízható közzétételi tartományt. 
    
    A parancsmag futtatásához szüksége lesz a kulcs az előző lépésben meghatározott URL-címére.
    
    Az előző lépés során létrehozott URL-címet és a C:\contoso-tpd1.xml TPD-fájlt használva például a következőt futtatná:
    
    ```
    Import-AadrmTpd -TpdFile "C:\contoso-tpd1.xml" -ProtectionPassword –KeyVaultStringUrl https://contoso-byok-kv.vault.azure.net/keys/contosorms-byok/aaaabbbbcccc111122223333 -Active $True -Verbose
    ```
    
    Amikor a rendszer kéri, írja be a korábban megadott jelszót, és erősítse meg a művelet végrehajtására vonatkozó szándékát.

2.  A parancs befejeződésekor ismételje meg az 1. lépést a többi .xml fájl esetében, amelyeket a megbízható közzétételi tartományok exportálásával hozott létre. Ezen fájlok esetében azonban az **-Active** esetében **false** értéket kell beállítani az Import parancs futtatásakor.  

3.  A [Disconnect-AadrmService](http://msdn.microsoft.com/library/windowsazure/dn629416.aspx) parancsmagot használva bontsa a kapcsolatot az Azure RMS szolgáltatással:

    ```
    Disconnect-AadrmService
    ```

    > [!NOTE]
    > Ha később meg kell erősítenie az Azure RMS-bérlőkulcs által az Azure Key Vaultban használt kulcsot, ezt a [Get-AadrmKeys](https://msdn.microsoft.com/library/dn629420.aspx) Azure RMS-parancsmaggal teheti meg.

Folytassa a következővel: [3. lépés: Az RMS-bérlő aktiválása](migrate-from-ad-rms-phase1.md#step-3-activate-your-rms-tenant).




<!--HONumber=Aug16_HO4-->


