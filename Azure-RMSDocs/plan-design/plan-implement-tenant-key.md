---
title: "Az Azure Rights Management-bérlőkulcs tervezése és megvalósítása | Azure RMS"
description: 
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 08/17/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: f0d33c5f-a6a6-44a1-bdec-5be1bc8e1e14
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: a80866576dc7d6400bcebc2fc1c37bc0367bcdf3
ms.openlocfilehash: ee7b9b5f251856f102651f1e8f379f7bbacea77e


---

# Planning and implementing your Azure Rights Management tenant key (Az Azure Rights Management-bérlőkulcs tervezése és megvalósítása)

*A következőkre vonatkozik: Azure Rights Management, Office 365*

A jelen cikkben található információk segítségével megtervezheti és kezelheti a tartalomvédelmi szolgáltatásbeli (RMS-) bérlőkulcsát az Azure RMS szolgáltatáshoz. Például ahelyett, hogy a Microsoft felügyelné a bérlőkulcsát (alapértelmezett beállítás), Ön is felügyelheti a saját bérlőkulcsát, hogy az megfeleljen a szervezetére vonatkozó speciális szabályozásoknak.  A saját bérlőkulcs felügyelete más néven a saját kulcs használata (BYOK).

> [!NOTE]
> Az RMS-bérlőkulcsot más néven kiszolgálólicenc-tanúsítványnak (SLC-kulcsnak) is nevezzük. Az Azure RMS minden, az Azure RMS szolgáltatásra előfizető szervezet számára fenntart egy vagy több kulcsot. Ha a szervezetben valamilyen kulcsot használnak az RMS-hez (felhasználói kulcs, számítógépkulcs, dokumentumtitkosítási kulcs), az titkosítási lánccal kapcsolódik az RMS-bérlőkulcshoz.

**Áttekintés:** A következő táblázat segít kiválasztani az Ön számára ajánlott bérlőkulcs-topológiát. További információt a további dokumentációkban talál.

Ha az Azure RMS-t egy, a Microsoft által felügyelt bérlőkulccsal telepíti, később bármikor BYOK-ra válthat. Azonban jelenleg nem lehetséges a BYOK módszerről a Microsoft általi felügyeletre állítani az Azure RMS-bérlőkulcsokat.

|Üzleti követelmény|Ajánlott bérlőkulcs-topológia|
|------------------------|-----------------------------------|
|Az Azure RMS telepítése gyorsan, anélkül, hogy speciális hardverre lenne szükség|Microsoft által felügyelt|
|Teljes körű IRM-funkciókra van szükség az Exchange Online-ban az Azure RMS mellett|Microsoft által felügyelt|
|A kulcsok saját kezű létrehozása és védelmük biztosítása egy hardveres biztonsági modulban (HSM)|BYOK<br /><br />Ez a konfiguráció jelenleg korlátozott IRM-funkciókat eredményez az Exchange Online-ban. További információ: [A BYOK díjszabása és korlátozásai](byok-price-restrictions.md).|

## A bérlőkulcs-topológia kiválasztása: a Microsoft által felügyelt (alapértelmezés) vagy saját felügyeletű (BYOK)
Döntse el, melyik bérlőkulcs-topológia a legjobb az Ön szervezete számára. Alapértelmezés szerint az Azure RMS hozza létre a bérlőkulcsot és felügyeli a bérlőkulcs-életciklus legtöbb területét. Ez a legegyszerűbb lehetőség, amely a legkisebb adminisztratív teherrel jár. A legtöbb esetben Önnek nem is kell róla tudnia, hogy rendelkezik bérlőkulccsal. Egyszerűen csak regisztrál az Azure RMS-re, a kulcskezelési folyamat fennmaradó részét pedig a Microsoft elintézi.

Emellett az is előfordulhat, hogy az [Azure Key Vault](https://azure.microsoft.com/services/key-vault/) használatával teljes körű felügyeletet szeretne gyakorolni a bérlőkulcs felett. Ebben a forgatókönyvben létrehozza a bérlőkulcsot és a helyszínen tárolja a fő példányt. Ez a forgatókönyv más néven a saját kulcs használata (BYOK). Ha ezt választja, a következők történnek:

1.  Létrehozza a saját bérlőkulcsát a helyszínen, a saját informatikai és biztonsági szabályzatának megfelelően.

2.  Az Azure Key Vault segítségével biztonságos módon továbbítja a bérlőkulcsot a saját tulajdonában lévő hardveres biztonsági modulról (HSM) a Microsoft által birtokolt és felügyelt HSM-ekre. A folyamat során a bérlőkulcs soha nem kerül a hardveres védelem határain kívülre.

3.  Amikor elküldi a bérlőkulcsot a Microsoftnak, annak védelmét az Azure Key Vault biztosítja.

Választható lehetőségként az Azure RMS közel valós idejű használati naplóiban nyomon követheti a bérlőkulcsa használatának pontos módját és idejét.

> [!NOTE]
> További védelmi intézkedésként az Azure Key Vault különböző biztonsági tartományt használ többek között az Észak-Amerikában, az EMEA (Európa, a Közel-Kelet és Afrika) régióban, illetve az Ázsiában található adatközpontjaihoz, valamint az Azure különféle példányaihoz (például a Microsoft Azure Germany vagy az Azure Government). A saját felügyeletű bérlőkulcsok annak a régiónak vagy példánynak a biztonsági tartományához vannak kötve, amelyben az RMS-bérlő regisztrálva lett. Például egy európai ügyfél bérlőkulcsát nem lehet észak-amerikai vagy ázsiai adatközpontokban felhasználni.

## A bérlőkulcsok életciklusa
Ha úgy dönt, hogy a bérlőkulcsát a Microsoft felügyeli, a Microsoft a kulcs életciklusához kapcsolódó legtöbb műveletet elvégzi. Ha azonban Ön felügyeli a saját bérlőkulcsát, az Ön felelőssége lesz számos, a kulcs életciklusához kapcsolódó művelet, valamint az Azure Key Vault néhány további eljárásának elvégzése.

Az alábbi ábrák bemutatják és összehasonlítják a két lehetőséget. Az első ábra azt mutatja, milyen kicsi adminisztratív teher hárul Önre az alapértelmezett beállítás szerint, amikor a bérlőkulcsot a Microsoft felügyeli.

![Azure RMS-bérlőkulcs életciklusa – a Microsoft felügyeli, ez az alapértelmezett beállítás](../media/RMS_BYOK_cloud.png)

A második ábra azt mutatja, milyen további lépések szükségesek abban az esetben, ha a bérlőkulcsot Ön felügyeli.

![Azure RMS-bérlőkulcs életciklusa – a felhasználó felügyeli, saját kulcs használata](../media/RMS_BYOK_onprem4.png)

Ha úgy dönt, hogy a bérlőkulcsát a Microsoft felügyelje, a kulcs létrehozásához semmilyen további műveletet nem kell elvégeznie, és rögtön a [További lépések](plan-implement-tenant-key.md#next-steps) című szakasszal folytathatja.

Ha úgy dönt, hogy a bérlőkulcsot Ön felügyeli, további információkért olvassa el a következő szakaszokat.

## Az Azure Rights Management-bérlőkulcs megvalósítása

Az ebben a szakaszban található információkat és eljárásokat akkor használhatja, ha a bérlőkulcs saját kezű létrehozása és felügyelete, azaz a BYOK forgatókönyv mellett döntött:


> [!IMPORTANT]
> Ha már használatba vette az [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] szolgáltatást (tehát a szolgáltatás aktiválva van), és egyes felhasználók az Office 2010-et használják, a következő eljárások futtatása előtt [lépjen kapcsolatba a Microsoft támogatási szolgálatával](../get-started/information-support.md#to-contact-microsoft-support). A forgatókönyvtől és a követelményektől függően így is használhatja a BYOK-t, de csak bizonyos korlátozásokkal vagy további lépések végrehajtása után.
> 
> Akkor is [lépjen kapcsolatba a Microsoft támogatási szolgálatával](../get-started/information-support.md#to-contact-microsoft-support), ha a szervezete speciális kulcskezelési szabályzatokat használ.

### A BYOK előfeltételei
A következő táblázat felsorolja a saját kulcs használata (BYOK) előfeltételeit.

|Követelmény|További információ|
|---------------|--------------------|
|Az Azure RMS-t támogató előfizetés.|További információ az elérhető előfizetésekkel kapcsolatban: [Az Azure RMS-t támogató felhőalapú előfizetések](../get-started/requirements-subscriptions.md).|
|Ne használja az RMS-t egyéni felhasználók számára vagy az Exchange Online-hoz. Vagy ha mégis használja az Exchange Online-t, tudomásul veszi és elfogadja a BYOK ezzel a konfigurációval való használatával járó korlátozásokat.|További információ a BYOK-ra vonatkozó jelenlegi korlátozásokkal kapcsolatban: [A BYOK díjszabása és korlátozásai](byok-price-restrictions.md).<br /><br />**Fontos**: A BYOK jelenleg nem kompatibilis az Exchange Online-nal.|
|A Key Vault BYOK esetében felsorolt minden előfeltétel.|További információt az Azure Key Vault dokumentációjának [A BYOK előfeltételei](https://azure.microsoft.com/documentation/articles/key-vault-hsm-protected-keys/#prerequisites-for-byok) című szakaszában talál. <br /><br />**Megjegyzés**: Ha AD RMS-ről tér át Azure RMS-re a szoftverkulcs hardverkulcsra váltásával, akkor a Thales-vezérlőprogramok legalább 11.62-es verziójával kell rendelkeznie.|
|A Windows PowerShellhez készült Azure RMS felügyeleti modul.|A telepítési utasításokat [Az Azure Rights Managementhez készült Windows PowerShell telepítése](../deploy-use/install-powershell.md) című cikk tartalmazza. <br /><br />Ha a Windows PowerShell-modult már korábban telepítette, a következő parancs futtatásával ellenőrizze, hogy a verziószáma legalább **2.5.0.0**-e: `(Get-Module aadrm -ListAvailable).Version`|

A Thales HSM-ekről és azok az Azure Key Vaultban történő használatáról további információt a [Thales webhelyén](https://www.thales-esecurity.com/msrms/cloud) találhat.

Saját Azure Key Vault-beli bérlőkulcs létrehozásához és átviteléhez kövesse az Azure Key Vault dokumentációjának [How to generate and transfer HSM-protected keys for Azure Key Vault](https://azure.microsoft.com/documentation/articles/key-vault-hsm-protected-keys/) (HSM-védelemmel ellátott kulcsot létrehozása és átvitele az Azure Key Vaultba) című témakörét.

A kulcs átvitelét követően a Key Vault ellátja azt egy azonosítóval, amely nem más, mint a tároló nevét, a kulcstárolót, valamint a kulcs nevét és verzióját tartalmazó URL-cím. Példa: **https://contosorms-kv.vault.azure.net/keys/contosorms-byok/aaaabbbbcccc111122223333**. Az Azure RMS-t ezen URL-cím megadásával kell beállítani a kulcs használatára.

Mielőtt azonban az Azure RMS megkezdhetné a kulcs használatát, a szervezet kulcstartójában engedélyezni kell azt a számára. Ehhez az Azure Key Vault rendszergazdájának szüksége lesz a [Set-AzureRmKeyVaultAccessPolicy](https://msdn.microsoft.com/library/mt603625.aspx) Key Vault PowerShell-parancsmagra, majd meg kell adnia az engedélyt az Azure RMS egyszerű szolgáltatás (**Microsoft.Azure.RMS**) számára. Példa:

    Set-AzureRmKeyVaultAccessPolicy -VaultName 'ContosoRMS-kv' -ResourceGroupName 'ContosoRMS-byok-rg' -ServicePrincipalName Microsoft.Azure.RMS -PermissionsToKeys decrypt,encrypt,unwrapkey,wrapkey,verify,sign 

Most már készen áll annak beállítására, hogy az Azure RMS ezt a kulcsot használja a szervezet Azure RMS-bérlőkulcsaként. Az Azure RMS-parancsmagok használatához először kapcsolódjon az Azure RMS szolgáltatáshoz, majd jelentkezzen be:

    Connect-AadrmService

Ezt követően futtassa a kulcs URL-címének megadásához szükséges [Use-AadrmKeyVaultKey parancsmagot](https://msdn.microsoft.com/library/azure/mt759829.aspx). Példa:

    Use-AadrmKeyVaultKey -KeyVaultKeyUrl "https://contosorms-kv.vault.azure.net/keys/contosorms-byok/aaaabbbbcccc111122223333"

Ha meg szeretne győződni arról, hogy helyesen állította be az URL-címet az Azure RMS szolgáltatásban, a [Get-AzureKeyVaultKey](https://msdn.microsoft.com/library/dn868053.aspx) parancsmag futtatásával az Azure Key Vaultban megtekintheti a címet.


## További lépések

Miután megtervezte, és ha szükséges, létrehozta a bérlőkulcsot, tegye az alábbiakat:

1.  Kezdje meg a bérlőkulcs használatát:

    -   Ha még nem tette meg, most aktiválnia kell a Rights Management szolgáltatást, hogy a szervezete használatba vehesse az RMS-t. A felhasználók azonnal megkezdik az Ön bérlőkulcsának használatát (akár a Microsoft, akár Ön felügyeli azt az Azure Key Vaultban).

        További információ az aktiválásról: [Activating Azure Rights Management](../deploy-use/activate-service.md) (Az Azure Rights Management aktiválása).

    -   Ha már aktiválta a Rights Managementet, és később döntött a saját bérlőkulcsának felügyelete mellett, a felhasználók fokozatosan állnak át a régi bérlőkulcsról az újra, és ez a lépcsőzetes átállás eltarthat néhány hétig. A régi bérlőkulccsal védett dokumentumok és fájlok hozzáférhetők maradnak a jogosult felhasználók számára.

2.  Fontolja meg a használat naplózásának alkalmazását, amely az Azure Rights Management által végrehajtott minden egyes tranzakciót naplóz.

    Ha úgy döntött, hogy Ön felügyeli a bérlőkulcsot, a napló a bérlőkulcs használatára vonatkozó információkat is tartalmaz. A következő példában egy Excelben megjelenített naplófájlrészlet látható, amelyben a **KeyVaultDecryptRequest** és a **KeyVaultSignRequest** kérelemtípusok azt jelzik, hogy a bérlőkulcs használatban van.

    ![Naplófájl az Excelben bérlőkulcs használata mellett](../media/RMS_Logging.png)

    További információ a használati naplózásról: [Logging and analyzing Azure Rights Management usage](../deploy-use/log-analyze-usage.md) (Az Azure Rights Management használatának naplózása és elemzése).

3.  Tartsa karban a bérlőkulcsot.

    További információ: [Operations for Your Azure Rights Management Tenant Key](../deploy-use/operations-tenant-key.md) (Az Azure Rights Management bérlői kulcsával kapcsolatos műveletek).




<!--HONumber=Aug16_HO3-->


