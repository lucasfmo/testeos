---
title: "HYOK-korlátozások | Azure Rights Management"
description: 
author: cabailey
manager: mbaldwin
ms.date: 08/18/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 7667b5b0-c2e9-4fcf-970f-05577ba51126
translationtype: Human Translation
ms.sourcegitcommit: a80866576dc7d6400bcebc2fc1c37bc0367bcdf3
ms.openlocfilehash: 1cbf6bd6c209a8aafd1db61422ce03b628aaec07


---

# A „hold your own key - HYOK” (saját tulajdonú kulcs) és az AD RMS védelmi szolgáltatások korlátozásai

>*A következőkre vonatkozik: az Azure Information Protection előzetes verziója*

**[ Előzetes információ, a tartalma változhat. ]**

Amikor a legbizalmasabb dokumentumok és e-mailek védelméről van szó, rendszerint az Azure Rights Management alkalmazása szükséges, hogy az alábbiakban felsorolt szolgáltatások elérhetőek legyenek:

- Nincs szükség kiszolgáló infrastruktúrára, így gyorsabb, költséghatékonyabb a telepítés és a karbantartás, mint a helyszíni megoldásokkal.

- A felhőalapú hitelesítés segítségével könnyebben megoszthat tartalmat más szervezeteket képviselő partnerekkel és felhasználókkal.

- Szoros integráció az Office 365 szolgáltatásaival, például a kereséssel, a webes megjelenítővel, az elforgatott nézetekkel, a kártevőirtó programokkal, az eDiscoveryvel és a Delve-vel.

- Dokumentumkövetés, -visszavonás, valamint a megosztott bizalmas dokumentumokról e-mailes értesítések.

Az Azure RMS titkos kulcs segítségével védi vállalata dokumentumait és elektronikus leveleit, amit a Microsoft felügyel (alapbeállítás), de akár ön is védheti azokat (a „saját tulajdonú kulccsal”, a BYOK-forgatókönyvvel). Az Azure RMS-védelemről szóló információ soha nem kerül a felhőbe; a védett dokumentumokat és e-maileket nem Azure-ban tároljuk, csak ha ezt kifejezetten így szeretné, vagy ha más felhőszolgáltatást vesz igénybe, ami Azure-ban tárolja azokat. További információ a bérlőkulcsról: [Planning and implementing your Azure Rights Management tenant key](../plan-design/plan-implement-tenant-key.md) (Az Azure Rights Management-bérlőkulcs tervezése és megvalósítása). 

Néhány ügyfélnek bizonyos dokumentumok és e-mailek védelméhez azonban helyszínen szolgáltatott kulcs szükséges. Ez például előírásokból és megfelelőségi okokból kifolyólag kerülhet sor. 

A konfiguráció neve „hold your own key - HYOK” (saját tulajdonú kulcs) , amit az Azure Information Protection is támogat, ha az Active Directory Rights Management Services (AD RMS) a következő részben foglalt előírások szerint érvényes üzemelő példányával rendelkezik. 

Ebben a HYOK-forgatókönyvben a jogmegadások és a vállalat ezeket védő privát kulcsa helyszínen felügyelt és tárolt, míg az Azure Information Protection címkézési és besorolási házirendje továbbra is az Azure-ban felügyelt és tárolt. Az Azure RMS-védelemhez hasonlóan a Active Directory tartalomvédelmi szolgáltatásokkal védett információt sem küldjük el a felhőbe.

> [!NOTE]
> Csak szükség esetén és azokra a dokumentumokra és e-mailekre használja ezt a konfigurációt, amelyek ilyen titkosítást igényelnek. Azure RMS használata esetén az Active Directory tartalomvédelmi szolgáltatások nem tartalmazzák a felsorolt szolgáltatásokat, és mindössze egyetlen célra szorítkoznak: „adatátlátszatlanság bármi áron”.

A felhasználók semmit sem éreznek abból, ha valamelyik címke Azure RMS helyett Active Directory tartalomvédelmi szolgáltatásokat használ. Az Active Directory tartalomvédelmi szolgáltatásokkal járó védelem miatt győződjön meg róla, világos útmutatóval szolgál, mikor kell a felhasználóknak az Active Directory tartalomvédelmi szolgáltatásokat alkalmazó címkéket választani.

## A HYOK követelményei

Ellenőrizze, hogy az AD RMS üzemelő példánya megfelel-e az alábbi követelményeknek, hogy a az Azure Information Protection számára AD RMS tartalomvédelmi szolgáltatást vegyen igénybe.

- Az Active Directory tartalomvédelmi szolgáltatások konfigurációi:
    
    - A Windows Server 2012 R2 minimális verziója: Az éles környezetekhez szükséges, azonban tesztelési és értékelési célokra az 1. szervizcsomaggal frissített Windows Server 2008 R2 is használható.
    
    - Egyetlen Active Directory tartalomvédelmi szolgáltatások-gyökérfürt.
    
    - [2. titkosítási mód](https://technet.microsoft.com/library/hh867439.aspx): Az AD RMS-fürt titkosítási módjának verzióját és általános állapotát az [RMS Analyzer eszközzel](https://www.microsoft.com/en-us/download/details.aspx?id=46437) ellenőrizheti.   
    
    - Az AD RMS-kiszolgálók a csatlakozó ügyfelek által biztonságosnak ítélt, érvényes x.509 tanúsítvánnyal rendelkező SSL/TLS használatára vannak konfigurálva: Ez az éles környezetekben szükséges, teszteléskor és értékeléskor azonban elhagyható.
    
    - Konfigurált tartalomvédelmi sablonok.

- Címtár-szinkronizálás a helyszíni Active Directory és az Azure Active Directory között. így az AD RMS tartalomvédelmi szolgáltatást felhasználók egyszeri bejelentkezésre vannak beállítva.

- Ha az Active Directory tartalomvédelmi szolgáltatással védett dokumentumokat vagy e-maileket osztana meg: az Active Directory tartalomvédelmi szolgáltatás meghatározott megbízható kapcsolattal, közvetlen,pont-pont kapcsolatban konfigurált a többi vállalattal, a megbízható felhasználói tartományok (TUDs) vagy az Active Directory összevonási szolgáltatások (AD FS) használatával létrehozott összevonási megbízhatósági kapcsolatok segítségével.

- A felhasználáshoz Windows 7 Service Pack 1 vagy későbbi verzión futó Office 2013 Pro Plus Service 1 vagy Office 2016 Pro Plus szükséges. Vegye figyelembe, hogy az Office 2010 és az Office 2007 nem támogatott ebben a forgatókönyvben.

- Az [Azure Information Protection-ügyfél](info-protect-client.md) **1.0.233.0** vagy későbbi verziója.

> [!IMPORTANT]
> Az itt elérhető magas szintű megbízhatóság igénybevételéhez azt javasoljuk, az AD RMS-kiszolgálók ne a DMZ zónában legyenek és csak jól felügyelt számítógépek használják (ne például mobileszközöket vagy munkacsoporthoz tartozó számítógépet). 
> 
> Javasoljuk továbbá, hogy az AD RMS-fürt esetében használjon hardveres biztonsági modult (HSM-et), így az AD RMS üzemelő példányába való esetleges behatolás vagy a biztonságának sérülése esetén elkerülhető, hogy a Kiszolgálólicenc-tanúsítvány (SLC) titkos kulcsa nyilvánosságra vagy azt ellopják. 

Az Active Directory tartalomvédelmi szolgáltatások telepítési információi és útmutatója [Active Directory Rights Management Services](https://technet.microsoft.com/library/hh831364.aspx) menüpont alatt található a Windows Server könyvtárában. 


## Az információ behatárolása az AD RMS tartalomvédelem megadásához egy Azure Information Protection-címkével

Ha AD RMS tartalomvédelemmel konfigurál egy címkét, meg kell adnia a sablon GUID-azonosítóját és az AD RMS-fürt licencelési URL-címét. Az Active Directory Rights Management Services konzolján keresse meg a következő két értéket:

- A sablon GUID-azonosító kereséshez: Bontsa ki a fürtöt és kattintson a **Jogmegadási sablonok** lehetőségre. A **Terjesztett jogmegadási sablonok** információból kiválaszthatja felhasználni kívánt sablon GUID-azonosítóját. Példa: 82bf3474-6efe-4fa1-8827-d1bd93339119

- A licencelési URL-cím kereséséhez kattintson rá a fürt nevére. A **Fürt részletes adatai**információból másolja ki a **Licencelés** értékét, kivéve a **/_wmcs/licensing** karakterláncot. Példa: https://rmscluster.contoso.com 
    
    Ha extranetes és intranetes licencelési értékkel egyaránt rendelkezik és azok különböznek: csak abban az esetben adja meg az extranetes értéket, amikor közvetlen, pont-pont megbízhatósági kapcsolathoz rendelt partnerrel oszt meg védett dokumentumokat vagy e-maileket. Ellenkező esetben használja az intranetes értéket és győződjön meg róla, hogy az összes AD RMS tartalomvédelmet használó ügyfélszámítógép intranetes kapcsolattal csatlakozik (a távoli számítógépek például VPN-kapcsolatot használnak).

## További lépések

Az előzetes funkcióval kapcsolatos további információ a következő blogbejegyzésben található: [Azure Information Protection with HYOK (Hold Your Own Key)](https://blogs.technet.microsoft.com/enterprisemobility/2016/08/10/azure-information-protection-with-hyok-hold-your-own-key/).

Az AD RMS tartalomvédelem konfigurálásáról lásd: [How to configure a label to apply Rights Management protection](configure-policy-protection.md) (Címkék konfigurálása a Rights Management-védelem aktiválásához). 



<!--HONumber=Aug16_HO3-->


