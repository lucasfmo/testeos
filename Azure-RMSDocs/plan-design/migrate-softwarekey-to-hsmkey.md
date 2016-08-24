---
title: "2. lépés&colon; Szoftveres védelemmel ellátott kulcs áttelepítése HSM által védett kulccsá | Azure RMS"
description: 
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 08/17/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: c5f4c6ea-fd2a-423a-9fcb-07671b3c2f4f
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 437afd88efebd9719a3db98f8ab0ae07403053f7
ms.openlocfilehash: bd93e781da7dc34c18e236a90a03dbc8fb012a1c


---

# 2. lépés: Szoftveres védelemmel ellátott kulcs áttelepítése HSM által védett kulccsá

*A következőkre vonatkozik: Active Directory Rights Management Services, Azure Rights Management*


Ezek az utasítások az [AD RMS-ről az Azure Rights Managementre történő áttelepítés](migrate-from-ad-rms-to-azure-rms.md) részét képezik, és csak akkor alkalmazandók, ha az AD RMS-kulcs szoftveres védelemmel van ellátva, és HSM-védelemmel ellátott bérlőkulccsal rendelkező Azure Rights Management-környezetbe kíván áttelepítést végezni az Azure Key Vaultban. 

Amennyiben nem ez a választott konfigurációs forgatókönyv, térjen vissza a [2. lépéshez. Exportálja a konfigurációs adatokat az AD RMS-ből, majd importálja az Azure RMS-be](migrate-from-ad-rms-phase1.md#step-2-export-configuration-data-from-ad-rms-and-import-it-to-azure-rms), és válasszon egy másik konfigurációt.

Ez egy négylépéses eljárás, amellyel importálhatja az AD RMS konfigurációját az Azure RMS-be. Ennek eredményeképp jön létre az Ön által az Azure Key Vault szolgáltatásban felügyelt (BYOK) Azure RMS-bérlőkulcs.

Először nyerje ki a kiszolgálólicenc-tanúsítványt (SLC-kulcsot) az AD RMS konfigurációs adataiból, és vigye át a kulcsot egy helyszíni Thales HMS-be. Ezután hozzon létre belőle egy csomagot és vigye át a HSM-kulcsot az Azure Key Vaultba, majd engedélyezze a kulcstartó elérését az Azure RMS számára, végül importálja a konfigurációs adatokat.

Mivel az Azure RMS-bérlőkulcs tárolását és felügyeletét az Azure Key Vault végzi, az áttelepítés ezen része az Azure Key RMS-en kívül Azure Key Vault-beli adminisztrációt is igényel. Ha az Azure Key Vaultot nem Ön, hanem a szervezet egy másik rendszergazdája felügyeli, vele együttműködve kell elvégeznie ezt az eljárást.

Mielőtt elkezdené, győződjön meg arról, hogy a szervezet rendelkezik egy Azure Key Vaultban létrehozott kulcstartóval, és támogatja a HMS-védelemmel ellátott kulcsok használatát. Bár az áttelepítés elvégzéséhez nem szükséges, Azure RMS-hez dedikált kulcstartó használata ajánlott. A kulcstartó annak engedélyezésére lesz konfigurálva, hogy az Azure RMS hozzáférjen, így a kulcstartó tárolóit csak Azure RMS-kulcsokra kell korlátozni.


> [!TIP]
> Ha Ön végzi el az Azure Key Vault konfigurálásához szükséges lépéseket, de nem ismeri az Azure ezen szolgáltatását, először tekintse át a [Bevezetés az Azure Key Vault használatába](https://azure.microsoft.com/documentation/articles/key-vault-get-started/) című témakörben leírtakat. 


## 1. rész: Az SLC-kulcs kinyerése a konfigurációs adatokból és a kulcs importálása a helyszíni HSM-be

1.  Azure Key Vault-rendszergazda számára: Kövesse az Azure Key Vault-dokumentáció [Implementing bring your own key (BYOK) for Azure Key Vault](https://azure.microsoft.com/documentation/articles/key-vault-hsm-protected-keys/#implementing-bring-your-own-key-byok-for-azure-key-vault) (A saját kulcs használatának (BYOK) megvalósítása) című szakaszának alábbi lépéseit:

    -   **Generate and transfer your key to Azure Key Vault HSM (A kulcs létrehozása és átvitele az Azure Key Vault HSM-be)**: [Step 1: Prepare your Internet-connected workstation (1. lépés: Az internetre kapcsolódó munkaállomás előkészítése)](https://azure.microsoft.com/documentation/articles/key-vault-hsm-protected-keys/#step-1-prepare-your-internet-connected-workstation)

    -   **Generate and transfer your tenant key – over the Internet (A bérlőkulcs létrehozása és átvitele – az interneten keresztül)**: [Step 2: Prepare your disconnected workstation (2. lépés: A nem kapcsolódó munkaállomás előkészítése)](https://azure.microsoft.com/documentation/articles/key-vault-hsm-protected-keys/#step-2-prepare-your-disconnected-workstation)

    Ne kövesse a bérlőkulcs létrehozása vonatkozó utasításokat, mert ennek megfelelője már rendelkezésre áll az exportált konfigurációs adatok .xml fájljában. Ehelyett egy olyan eszközt fog futtatni, amely kinyeri ezt a kulcsot a fájlból és importálja azt a helyszíni HSM-be. Futtatáskor az eszköz két fájlt hoz létre:

    - Egy kulcs nélküli új konfigurációs adatfájlt, melyet később az Azure RMS-bérlőbe importálhat.

    - Egy, a kulcsot tartalmazó PEM-fájlt (kulcstárolót), melyet a helyszíni HSM-be importálhat.

2. Azure RMS- vagy Azure Key Vault-rendszergazda számára: Futtassa az [Azure RMS áttelepítési eszközkészlet](https://go.microsoft.com/fwlink/?LinkId=524619) TpdUtil eszközét a kapcsolat nélküli munkaállomáson. Ha az eszközt például az E meghajtóra telepítette, és erre a meghajtóra másolja a ContosoTPD.xml nevű konfigurációs adatfájlt:

    ```
        E:\TpdUtil.exe /tpd:ContosoTPD.xml /otpd:ContosoTPD.xml /opem:ContosoTPD.pem
    ```

    Ha egynél több RMS-konfigurációs adatfájllal rendelkezik, futtassa ezt az eszközt minden fennmaradó fájlhoz.

    A TpdUtil.exe paraméterek nélküli futtatásával megnyithatja az eszköz Súgóját, mely az eszköz leírását, használati útmutatóját és hozzá kapcsolódó példákat tartalmaz

    További információ a parancsról:

    - **/tpd**: megadja az exportált AD RMS-konfigurációs adatfájl teljes elérési útvonalát és nevét. A paraméter teljes neve: **TpdFilePath**.

    - **/otpd**: meghatározza a konfigurációs adatfájl azon kimeneti fájljának nevét, amely nem tartalmazza a kulcsot. A paraméter teljes neve: **OutPfxFile**. Ha nem adja meg ezt a paramétert, a kimeneti fájl felveszi az eredeti fájlnevet a **_keyless** végződéssel, és az aktuális mappában lesz tárolva.

    - **/opem**: megadja a kinyert kulcsot tartalmazó PEM-fájl kimeneti fájljának nevét. A paraméter teljes neve: **OutPemFile**. Ha nem adja meg ezt a paramétert, a kimeneti fájl felveszi az eredeti fájlnevet a **_key** végződéssel, és az aktuális mappában lesz tárolva.

    - Ha a parancs futtatásakor nem állít be jelszót (a **TpdPassword** teljes paraméternév vagy a **pwd** rövidített paraméternév használatával), a rendszer bekéri azt.

3. A Thales-dokumentációnak megfelelően csatolja és konfigurálja a Thales HSM-et az eddig használt kapcsolat nélküli munkaállomáson. Az alábbi paranccsal importálhatja a kulcsot a csatolt Thales HSM-be, és adhatja meg a ContosoTPD.pem fájl nevét:

        generatekey --import simple pemreadfile=e:\ContosoTPD.pem plainname=ContosoBYOK protect=module ident=contosobyok type=RSA

    > [!NOTE]
    >Ha több mint egy fájllal rendelkezik, a tartalom áttelepítést követő védelme érdekében válassza ki az Azure RMS-ben használni kívánt HSM-kulcsnak megfelelő fájlt.

    Ekkor egy ehhez hasonló kimeneti képernyő lesz látható:

    **kulcslétrehozási paraméterek:**

    **operation &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Elvégzendő művelet &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; import**

    **application &nbsp;&nbsp;&nbsp;&nbsp;Alkalmazás&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; simple**

    **verify &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; A konfigurációs kulcs biztonságának ellenőrzése&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; yes**

    **type &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Kulcs típusa &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; RSA**

    **pemreadfile &nbsp;&nbsp; Az RSA-kulcsot tartalmazó PEM-fájl &nbsp;&nbsp; e:\ContosoTPD.pem**

    **ident &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Kulcs azonosítója &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; contosobyok**

    **plainname &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Kulcs neve &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ContosoBYOK**

    **A kulcs importálása sikeresen befejeződött.**

    **A kulcs elérési útvonala: C:\ProgramData\nCipher\Key Management Data\local\key_simple_contosobyok**

Ez a kimenet megerősíti, hogy a titkos kulcs, valamint egy titkosított másolat (példánkban a „key_simple_contosobyok”) át lett telepítve a helyi Thales HSM-eszközre. 

Most, hogy sikeresen kinyerte az SLC-kulcsot és a helyi HSM-re importálta, a HSM-védelemmel ellátott kulcsból csomagot kell létrehoznia és át kell vinnie az Azure Key Vaultba.

> [!IMPORTANT]
> A lépés elvégzését követően törölje biztonságosan ezeket a PEM-fájlokat a kapcsolat nélküli munkaállomásról, hogy jogosulatlan személyek ne férhessenek hozzájuk. Az E meghajtón lévő fájlok biztonságos törléséhez például futtassa a cipher /w:E parancsot.

## 2. rész: Csomag létrehozása a HSM-kulcsból és annak átvitele az Azure Key Vaultba

1.  Azure Key Vault-rendszergazda számára: Kövesse az Azure Key Vault-dokumentáció [Implementing bring your own key (BYOK) for Azure Key Vault](https://azure.microsoft.com/documentation/articles/key-vault-hsm-protected-keys/#implementing-bring-your-own-key-byok-for-azure-key-vault) (A saját kulcs használatának (BYOK) megvalósítása) című szakaszának alábbi lépéseit:

    -   [4. lépés: A kulcs előkészítése az átvitelre](https://azure.microsoft.com/documentation/articles/key-vault-hsm-protected-keys/#step-4-prepare-your-key-for-transfer)

    -   [5. lépés: A kulcs átvitele az Azure Key Vaultba](https://azure.microsoft.com/documentation/articles/key-vault-hsm-protected-keys/#step-5-transfer-your-key-to-azure-key-vault)

    Ne kövesse a kulcspár létrehozására vonatkozó lépéseket, mert már rendelkezik a kulccsal. Ehelyett egy parancs futtatásával fogja átvinni a kulcsot (példánkban a KeyIdentifier paraméter a „contosobyok” értéket használja) a helyi HSM-ből.

    Mielőtt átvinné a kulcsot az Azure Key Vaultba, győződjön meg arról, hogy a KeyTransferRemote.exe segédprogram a **Result: SUCCESS** eredményt adja, amikor korlátozott engedélyekkel másolatot készít a kulcsról (4.1. lépés) és amikor titkosítja a kulcsot (4.3. lépés).

    Miután a kulcs feltöltődött az Azure Key Vaultba, megjelennek a kulcs tulajdonságai, köztük a kulcs azonosítója. Az azonosító az alábbihoz fog hasonlítani: **https://contosorms-kv.vault.azure.net/keys/contosorms-byok/aaaabbbbcccc111122223333**. Jegyezze fel ezt az URL-címet, mert az Azure RMS-rendszergazdának szüksége lesz rá az Azure RMS arra való beállításához, hogy ezt a kulcsot használja a bérlőkulcsához.

    A HMS-kulcs Azure Key Vaultba történő átvitelét követően készen áll az AD RMS konfigurációs adatainak importálására.

## 3. rész: A konfigurációs adatok importálása az Azure RMS szolgáltatásba

1.  Azure RMS-rendszergazdák számára: Az internetre kapcsolódó munkaállomáson, a PowerShell-munkamenetben másolja át azokat az új konfigurációs adatfájlokat (.xml) amelyekből az TpdUtil eszköz futtatása után eltávolította az SLC-kulcsot.

2. Töltse fel az első .xml-fájlt az [Import-AadrmTpd](https://msdn.microsoft.com/library/dn857523.aspx) parancsmag segítségével. Ha több megbízható közzétételi tartománya volt, ezért egynél több ilyen fájllal rendelkezik, a tartalom áttelepítést követő védelme érdekében válassza ki az Azure RMS-ben használni kívánt HSM-kulcsnak megfelelő fájlt.

    A parancsmag futtatásához szüksége lesz a kulcs az előző lépésben meghatározott URL-címére.

    Az előző lépésben létrehozott URL-címet és a C:\contoso_keyless.xml konfigurációs adatfájlt használva például a következőt futtatná:

    ```
    Import-AadrmTpd -TpdFile "C:\contoso_keyless.xml" -ProtectionPassword –KeyVaultStringUrl https://contoso-byok-kv.vault.azure.net/keys/contosorms-byok/aaaabbbbcccc111122223333 -Active $True -Verbose
    ```

    Amikor a rendszer kéri, írja be a konfigurációs adatfájlhoz korábban megadott jelszót, és erősítse meg a művelet végrehajtására vonatkozó szándékát.

    Ha egynél több konfigurációs adatfájllal rendelkezik, ismételje meg a parancsot minden fennmaradó ilyen fájlhoz. Ezen fájlok esetében azonban az **-Active** esetében **false** értéket kell beállítani az Import parancs futtatásakor.



3.  A [Disconnect-AadrmService](http://msdn.microsoft.com/library/windowsazure/dn629416.aspx) parancsmagot használva bontsa a kapcsolatot az Azure RMS szolgáltatással:

    ```
    Disconnect-AadrmService
    ```

    > [!NOTE]
    > Ha később meg kell erősítenie az Azure RMS-bérlőkulcs által az Azure Key Vaultban használt kulcsot, ezt a [Get-AadrmKeys](https://msdn.microsoft.com/library/dn629420.aspx) Azure RMS-parancsmaggal teheti meg.


Folytassa a következővel: [3. lépés: Az RMS-bérlő aktiválása](migrate-from-ad-rms-phase1.md#step-3-activate-your-rms-tenant).






<!--HONumber=Aug16_HO3-->


