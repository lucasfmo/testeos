---
title: "A BYOK díjszabása és korlátozásai | Azure RMS"
description: 
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 08/17/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: f5930ed3-a6cf-4eac-b2ec-fcf63aa4e809
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 437afd88efebd9719a3db98f8ab0ae07403053f7
ms.openlocfilehash: ece615912d69eda78107c60245620ed36c0affd2


---

# A BYOK díjszabása és korlátozásai

*A következőkre vonatkozik: Azure Rights Management, Office 365*


Az Azure Rights Managementet tartalmazó előfizetéssel rendelkező szervezetek külön díjfizetés nélkül használhatnak ügyfél által felügyelt kulcsokat (BYOK) az Azure Key Vaultban, és naplózhatják annak használatát. Az Azure Key Vault használatához azonban a HSM által védett kulcsokkal rendelkező Key Vaultot támogató Azure-előfizetés szükséges. A kulcsok használata az Azure Key Vaultban havi díjfizetési kötelezettséggel jár. További információt az [Azure Key Vault díjszabását ismertető weblapon](https://azure.microsoft.com/en-us/pricing/details/key-vault/) talál.

Ha a szervezetben vannak az RMS egyéni felhasználók számára szolgáltatásban elérhető ingyenes fiókokra regisztrált felhasználók, a BYOK és a használati naplózás nem vehető igénybe, mivel az ingyenes fiókok nem rendelkeznek bérlői rendszergazdával, aki konfigurálhatná ezeket a funkciókat.


> [!NOTE]
> További információk az RMS-ről egyéni felhasználók számára: [RMS egyéni felhasználók számára és Azure Rights Management](../understand-explore/rms-for-individuals.md).

![A BYOK nem támogatja az Exchange Online-t](../media/RMS_BYOK_noExchange.png)

A BYOK és a használat naplózása minden olyan alkalmazással zökkenőmentesen működik, amely integrálható az Azure RMS-sel. Ezek közé tartoznak felhőszolgáltatások, mint a SharePoint Online; az Exchange-et és SharePointot futtató helyszíni kiszolgálók, amelyek az RMS-összekötőn keresztül működnek együtt az Azure RMS-sel, valamint az ügyfélalkalmazások, például az Office 2016 és az Office 2013. A kulcshasználati naplók elérhetők, bármelyik alkalmazás is küld kérelmeket az Azure RMS felé.

Ez alól egyetlen kivétel van: jelenleg **az Azure RMS BYOK nem kompatibilis az Exchange Online-nal**. Ha az Exchange Online-t szeretné használni, javasoljuk, hogy az Azure RMS-t az alapértelmezett kulcsfelügyeleti módban telepítse, amelyben a kulcsát a Microsoft hozza létre és felügyeli. Később is átválthat a BYOK módszerre, például amikor az Exchange Online már támogatja az Azure RMS BYOK módját. Ha azonban nem tud várni, egy másik lehetőség az Azure RMS telepítése BYOK módban, ami az Exchange Online korlátozott RMS-funkcionalitását eredményezi (a nem védett e-mailek és mellékletek továbbra is teljesen működőképesek maradnak):

-   A védett e-maileket és mellékleteket nem lehet megjeleníteni az Outlook Web Accessben.

-   A védett e-maileket nem lehet megjeleníteni az olyan mobileszközökön, amelyek az Exchange ActiveSync IRM-funkcióját használják.

-   Nem lehetséges az átviteli visszafejtés (például a kártevők keresése céljából) és a naplók visszafejtése, így a védett e-mailek és a védett mellékletek ki lesznek hagyva.

-   Az IRM-házirendeket kikényszerítő átvitelvédelmi szabályok és adatveszteség-megelőzési (DLP) funkció használata nem lehetséges, így az RMS nyújtotta védelem ezekkel a módszerekkel nem alkalmazható.

-   A védett e-mailek kiszolgálóalapú keresése korlátozva lesz, így a védett e-mailek ki lesznek hagyva.

Ha az Azure RMS BYOK módját az Exchange Online korlátozott RMS-funkcionalitása mellett használja, az RMS működni fog az Outlook levelezőügyfelekkel Windows- és Mac gépeken, valamint az egyéb olyan levelezőügyfelekkel, amelyek nem használják az Exchange ActiveSync IRM-funkcióját.

Ha az AD RMS-ről áll át az Azure RMS-re, lehetséges, hogy a kulcsa megbízható közzétételi tartományként (TPD) lett importálva az Exchange Online-ba (ezt az Exchange terminológiája szintén BYOK-nak hívja, azonban ez nem azonos az Azure Key Vault BYOK-val). Ebben az esetben el kell távolítania a TPD-t az Exchange Online-ból a sablonok és házirendek ütközéseinek elkerülése érdekében. További információk: [Remove-RMSTrustedPublishingDomain](https://technet.microsoft.com/library/jj200720%28v=exchg.150%29.aspx) parancsmag az Exchange Online parancsmagtárában.

Előfordulhat, hogy az Azure RMS BYOK módjának az Exchange Online-ra vonatkozó kivétele a gyakorlatban nem okoz problémát. Például azon szervezetek, amelyeknek szükségük van a BYOK-ra és a naplózásra, helyszíni környezetben futtatják az adatalkalmazásaikat (Exchange, SharePoint, Office), és olyan funkciókra használják az Azure RMS-t, amelyek a helyszíni AD RMS-sel nem lennének könnyen elérhetőek (ilyenek például a más vállalatokkal való együttműködés és a mobilügyfelek számára biztosított hozzáférés). Ebben az esetben a BYOK és a naplózás is jól működik, és lehetővé teszik, hogy a szervezet teljes felügyeletet gyakoroljon az Azure RMS-előfizetése felett.

## További lépések

Ha úgy döntött, hogy saját maga kívánja felügyelni a saját kulcsát, folytassa a következővel: [Az Azure Rights Management-bérlőkulcs megvalósítása](plan-implement-tenant-key.md#implementing-your-azure-rights-management-tenant-key).

Ha úgy döntött, hogy marad az alapértelmezett konfigurációnál, ahol a Microsoft felügyeli a bérlőkulcsot, tekintse meg a Planning and implementing your Azure Rights Management tenant key (Az Azure Rights Management-bérlőkulcs tervezése és megvalósítása) című cikk [Next steps](plan-implement-tenant-key.md#next-steps) (További lépések) című szakaszát.




<!--HONumber=Aug16_HO3-->


