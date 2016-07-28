---
title: "Áttelepítés AD RMS-ről Azure Rights Managementre | Azure RMS"
description: 
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 07/13/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 828cf1f7-d0e7-4edf-8525-91896dbe3172
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 67129d6cdac124947fc07aa4d42523686227752e
ms.openlocfilehash: 8ef46d68594a6e559e050f846a844f566ff8770d


---

# Áttelepítés AD RMS-ről Azure Rights Managementre

*A következőkre vonatkozik: Active Directory Rights Management Services, Azure Rights Management*

A következő útmutatók használatával áttelepítheti Active Directory tartalomvédelmi szolgáltatásainak (AD RMS) telepítését az Azure Rights Management (Azure RMS) rendszerbe. Az áttelepítés után a felhasználók továbbra is hozzáférhetnek a dokumentumokhoz és e-mailekhez, amelyeket a szervezete az AD RMS használatával védett. Az újonnan védett tartalom az Azure RMS-t fogja használni.

Nem biztos benne, hogy az AD RMS áttelepítés megfelel-e az adott szervezetnek?

-   A [Mi az az Azure Rights Management?](../understand-explore/what-is-azure-rms.md) témakörben megismerkedhet az Azure RMS-sel: annak működésével, a segítségével megoldható vállalati problémákkal és azzal, hogy hogyan néz ki a rendszergazdáknak és a felhasználóknak.

-   Az Azure RMS és az AD RMS összehasonlítása: [Az Azure Rights Management és az AD RMS összehasonlítása](../understand-explore/compare-azure-rms-ad-rms.md).

## Előfeltételek az AD RMS Azure RMS-re való áttelepítéséhez
Mielőtt megkezdi az áttelepítést az Azure RMS-re, győződjön meg arról, hogy a következő feltételek biztosítottak, és megértette a fennálló korlátozásokat.


- **Egy támogatott RMS telepítés**

    Az Azure RMS-re való áttelepítést az AD RMS összes kiadása támogatja a Windows Server 2008-től a Windows Server 2012 R2-ig:

    - Windows Server 2008 (x86 vagy x64)

    - Windows Server 2008 R2 (x64)

    - Windows Server 2012 (x64)

    - Windows Server 2012 R2 (x64)

    Az összes érvényes AD RMS topológia támogatott:

    - Egyetlen erdő, egyetlen RMS-fürt

    - Egyetlen erdő, több csak licencelési RMS-fürt

    - Több erdő, több RMS-fürt

    **Megjegyzés**: Alapértelmezés szerint a több RMS-fürt egyetlen Azure RMS-bérlőhöz települ át. Ha más RMS-bérlőket szeretne, ezeket külön áttelepítésekként kell kezelnie. Az egyetlen RMS-fürtből származó kulcsok nem importálhatók egynél több Azure RMS-bérlőhöz.


- **Az Azure RMS futtatásához szükséges összes követelmény, köztük az Azure RMS-bérlő (nincs aktiválva)**

    Lásd: [Az Azure Rights Management követelményei](../get-started/requirements-azure-rms.md).

    Ugyan az AD RMS-ről való áttelepítéshez szükség van egy Azure RMS-bérlőre, javasoljuk, hogy az áttelepítés előtt ne aktiválja a tartalomvédelmi szolgáltatást. Az áttelepítési folyamatban ez a lépés az után következik, hogy exportálta a kulcsokat és a sablonokat az AD RMS-ből és importálta őket az Azure RMS-be. Az AD RMS-ből való áttelepítés azonban akkor is lehetséges, ha az Azure RMS már aktiválva van.


- **Előkészítés az Azure RMS-hez:**

    - Címtár-szinkronizálás a helyszíni címtár és az Azure Active Directory között

    - Levelezési csoportok az Azure Active Directoryban

    Lásd: [Az Azure Rights Management előkészítése](prepare.md).


- **IHa használta az Exchange Server vagy a SharePoint Server tartalomvédelmi szolgáltatásait** (IRM – például az átviteli szabályok és az Outlook Web Access) az AD RMS szolgáltatással:

    - A tervezéskor vegye figyelembe, hogy egy rövid időtartamra az IRM nem lesz elérhető a kiszolgálókon
 
    Az áttelepítés után folytathatja az IRM használatát ezeken a kiszolgálókon az Azure RMS-sel. Azonban az áttelepítés egyik lépése ideiglenesen letiltja az IRM szolgáltatást, telepíti és konfigurálja az összekötőt, újrakonfigurálja a kiszolgálókat, majd újból engedélyezi az IRM szolgáltatást.

    Ez az egyetlen időszak, amikor szolgáltatás nem érhető el az áttelepítés során.


Korlátozások:

-   Ugyan az áttelepítési folyamat támogatja a kiszolgálólicencelési tanúsítványkulcs (SLC-kulcs) áttelepítését egy hardveres biztonsági modulra (HMS) az Azure RMS-hez, az Exchange Online jelenleg nem támogatja ezt a konfigurációt. Ha az összes IRM-funkciót használni kívánja az Exchange Online-nal az Azure RMS-be való migrálás után, az Azure RMS-bérlőkulcsot [a Microsoftnak kell kezelnie](../plan-design/plan-implement-tenant-key.md#choose-your-tenant-key-topology-managed-by-microsoft-the-default-or-managed-by-you-byok). Alternatív megoldásként futtathatja az IRM-et az Exchange Online-ban korlátozott funkciókkal is, ha az Azure RMS-bérlőt Ön kezeli (BYOK). További információk az Exchange Online használatáról az Azure RMS-ben: [6. lépés. IRM-integráció konfigurálása Exchange Online-ban](migrate-from-ad-rms-phase3.md#step-6-configure-irm-integration-for-exchange-online) az itt látható áttelepítési útmutató alapján.

-   Ha az Azure RMS-ben nem támogatott szoftverrel és ügyfelekkel rendelkezik, ezek/ők nem védhetik le vagy fogyaszthatják az Azure RMS által védett tartalmakat. Ellenőrizze a támogatott alkalmazások és ügyfelek szakaszokat [Requirements for Azure Rights Management](../get-started/requirements-azure-rms.md) (Az Azure Rights Management követelményei) című cikkben.

-   Ha a helyszíni kulcsát archivált állapotban kívánja importálni az Azure RMS-be (a megbízható közzétételi tartományt nem állítja aktív állapotba az importálási folyamathoz), és a felhasználókat kötegekben, többlépcsősen telepíti át, az áttelepített felhasználók által újonnan levédett tartalmak nem lesznek elérhetőek az AD RMS-ben maradó felhasználók számára. Az ilyen forgatókönyvekben tartsa a lehető legrövidebben az áttelepítési időt, és a felhasználókat logikus kötegekben telepítse át – ha együttműködnek egymással, együtt történjen az áttelepítésük.

    Ez a korlátozás nem lép érvénybe, ha a megbízható közzétételi tartományt aktiválja az importálási folyamat idejére, mert így az összes felhasználó azonos kulcsot használva védi le a tartalmat. Ez az ajánlott konfiguráció, mert így függetlenül, a saját tempójában telepítheti át az összes felhasználót.

-   Ha külső partnerekkel működik együtt (például megbízható felhasználói tartományokat vagy összevonást használ), nekik is át kell térniük az Azure RMS-hez az Ön áttelepítésével egy időben, vagy nem sokkal utána. Ahhoz, hogy továbbra is hozzáférhessenek a korábban az AD RMS-sel levédett tartalomhoz, olyan ügyfél-konfigurációs változtatásokat kell alkalmazniuk, amelyek az Ön által beállítottakra hasonlítanak és szerepelnek ebben a dokumentumban.

    Mivel nagyon sokféle konfiguráció lehetséges a partnerek esetében, az újrakonfigurálás pontos lépései nem sorolhatók fel ebben a dokumentumban. Segítségért [forduljon a Microsoft támogatási szolgálatához](../get-started/information-support.md#support-options-and-community-resources).

## Az AD RMS Azure RMS-re való áttelepítésének lépéseinek áttekintése


A 9 áttelepítési lépés felosztható 4 fázisra. Ezeket elvégezhetik különböző rendszergazdák, különböző időpontokban.

[**1. FÁZIS: AZ AD RMS KISZOLGÁLÓOLDALI KONFIGURÁCIÓJA**](migrate-from-ad-rms-phase1.md)

- **1. lépés: Az Azure RMS kezelésfelügyeleti eszközének letöltése**

    Az áttelepítési folyamathoz futtatnia kell egy vagy több Windows PowerShell-parancsmagot az Azure RMS kezelésfelügyeleti eszközzel együtt telepített Azure RMS modulból.

- **2. lépés Konfigurációs adatok exportálása az AD RMS-ből és importálása az AD RMS-be**

    Exportálja a konfigurációs adatokat (kulcsok, sablonok, URL-címek) az AD RMS-ből egy XML-fájlba, majd töltse fel ezt a fájlt az Azure RMS-be az Import-AadrmTpd Windows PowerShell-parancsmag használatával. Az AD RMS-kulcs konfigurációjától függően további lépések lehetnek szükségesek:

    - **Szoftveres védelemmel ellátott kulcs áttelepítése szoftveres védelemmel rendelkező kulccsá**:

        Az AD RMS központilag felügyelt, jelszóalapú kulcsának áttelepítése a Microsoft által felügyelt Azure RMS-bérlői kulccsá. Ez a legegyszerűbb áttelepítési út. További lépéseket nem igényel.

    - **HSM által védett kulcs áttelepítése HSM által védett kulccsá**:

        Az AD RMS-hez HSM által tárolt kulcsokból ügyfél által felügyelt Azure RMS-bérlői kulccsá (a „saját kulcs használata” vagy BYOK forgatókönyv). Ez további lépéseket igényel, hogy a helyszíni Thales HSM-ből áttelepítse a kulcsot az Azure RMS HSM-be. A meglévő HSM által védett kulcsot modul által védetté kell tenni; az OCS által védett kulcsok nem támogatottak a BYOK eszközkészletben.

    - **Szoftveres védelemmel ellátott kulcs áttelepítése HSM által védett kulccsá**:

        Központilag felügyelt, jelszóalapú kulcsokból ügyfél által felügyelt Azure RMS bérlői kulccsá (a „saját kulcs használata” vagy BYOK forgatókönyv). Ez igényli a legtöbb konfigurációt, mert ekkor először ki kell nyerni a szoftverkulcsot és importálni egy helyszíni HSM-be, majd el kell végezni a további lépéseket a kulcs áttelepítéséhez a helyszíni Thales HSM-ből az Azure RMS HSM-be.

- **3. lépés. Az Azure RMS-bérlő aktiválása**

    Ha lehetséges, ezt a lépést az importálási folyamat után végezze el, ne előtte.

- **4. lépés. Importált sablonok konfigurálása**

    Amikor importálja a jogmegadási sablonokat, az állapotaikat archiválja a rendszer. Ha azt szeretné, hogy a felhasználók lássák és használhassák őket, állítsa közzétettre a sablonok állapotát a klasszikus Azure portálon.


[**2. FÁZIS: ÜGYFÉLOLDALI KONFIGURÁCIÓ**](migrate-from-ad-rms-phase2.md)


- **5. lépés: Ügyfelek újrakonfigurálása az Azure RMS használatára**

    A meglévő Windows rendszerű számítógépeket újra kell konfigurálni, hogy az Azure RMS szolgáltatást használják az AD RMS helyett. Ez a lépés a szervezete számítógépeire vonatkozik, valamint a partnerszervezetek számítógépeire, ha együttműködött velük az AD RMS futtatásakor.

    Emellett ha üzembe helyezte a [mobileszközhöz való kiegészítőt](http://technet.microsoft.com/library/dn673574.aspx) a mobileszközök támogatásához (például iOS-telefonok, iPadek, Android-telefonok és -táblagépek, Windows-telefonok, Mac-számítógépek), el kell távolítania azokat az SRV rekordokat a DNS-ből, amelyek átirányították ezeket az ügyfeleket az AD RMS-hez.


[**3. FÁZIS: TÁMOGATÁSI SZOLGÁLTATÁSOK KONFIGURÁCIÓJA**](migrate-from-ad-rms-phase3.md)


- **6. lépés: IRM-integráció konfigurálása Exchange Online-nal**

    Ez a lépés akkor szükséges, ha az Exchange Online-t szeretné használni az Azure RMS-sel.


- **7. lépés: Az RMS-összekötő üzembe helyezése**

    Ez a lépés akkor szükséges, ha a következő helyszíni szolgáltatások valamelyikét szeretné használni az Azure RMS-sel:

    - Exchange Server (például az átviteli szabályok és az Outlook Web Access)

    - SharePoint Server

    - Fájlbesorolási infrastruktúrát (FCI) futtató Windows Server


[**4. FÁZIS: ÁTTELEPÍTÉS UTÁNI FELADATOK**](migrate-from-ad-rms-phase4.md )

- **8. lépés: Az AD RMS leszerelése**

    Miután meggyőződött róla, hogy minden ügyfél az Azure RMS-t használja, és nem kapcsolódik az AD RMS kiszolgálóihoz, leszerelheti az AD RMS telepítését.


- **9. lépés: Kulcsismétlés végrehajtása az Azure RMS-bérlőkulcs esetében**

    Ez a lépés akkor szükséges, ha nem a 2. titkosítási módban futtatta a programot az áttelepítés előtt, valamint opcionális de ajánlott az összes áttelepítéshez az Azure RMS-bérlőkulcs biztonsága érdekében.


## További lépések
Az áttelepítés megkezdéséhez lépjen az [1. fázis – kiszolgálóoldali konfiguráció](migrate-from-ad-rms-phase1.md) szakaszhoz.




<!--HONumber=Jul16_HO3-->


