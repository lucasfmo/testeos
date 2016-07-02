---
title: "Kiszolgálók konfigurálása az Azure Rights Management-összekötő használatához | Azure RMS"
description: 
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 06/08/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 75846ee1-2370-4360-81ad-e2b6afe3ebc9
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 0b07ecc88b1d2d344f0984d4a805cc033996cc4d
ms.openlocfilehash: 79171b5931b69ca18d2a2cbe321d5d5887903da2


---

# Kiszolgálók konfigurálása az Azure Rights Management-összekötő használatához

*A következőkre vonatkozik: Azure Rights Management, Windows Server 2012, Windows Server 2012 R2*


Az alábbi információk segítségével konfigurálhatja a helyszíni kiszolgálókat az Azure Rights Management- (RMS-) összekötő használatához. Ezeket az eljárásokat a [Deploying the Azure Rights Management connector](deploy-rms-connector.md) (Az Azure Rights Management-összekötő üzembe helyezése) című témakör 5. lépése is ismerteti.

Mielőtt belekezdene, győződjön meg róla, hogy telepítette és konfigurálta az RMS-összekötőt, és ellenőrzött minden [előfeltételt](deploy-rms-connector.md#prerequisites-for-the-rms-connector), amelyek az összekötőt a későbbiekben használó kiszolgálókra vonatkoznak.


## A kiszolgálók konfigurálása az RMS-összekötő használatára
Miután telepítette és konfigurálta az RMS-összekötőt, készen áll azon helyszíni kiszolgálók konfigurálására, amelyek a Rights Managementet használni fogják, és az összekötő használatával csatlakoznak majd az Azure RMS-hez. Ez a következő kiszolgálók konfigurálását jelenti:

-   **Exchange 2016 and Exchange 2013 esetén:** Ügyfélelérési és postaláda-kiszolgálók

-   **Exchange 2010 esetén:** Ügyfélelérési és elosztó továbbítókiszolgálók

-   **SharePoint esetén:** Előtérbeli SharePoint-webkiszolgálók, köztük a központi felügyeleti kiszolgáló gazdái

-   **Fájlbesorolási infrastruktúra esetén:** Windows Server operációs rendszert futtató számítógépek, amelyeken telepítve van a File Resource Manager

A konfiguráláshoz a beállításjegyzék módosítására van szükség. Ezt kétféle módon teheti meg: automatikusan, a Microsoft RMS-összekötő kiszolgálókonfiguráló eszközével, vagy a beállításjegyzék manuális szerkesztésével.

---

**Automatikusan, a Microsoft RMS-összekötő kiszolgálókonfiguráló eszközével:**

- Előnyök:

    - Nem szükséges a beállításjegyzék közvetlen szerkesztése. A folyamat egy parancsfájl segítségével automatikusan végbemegy.

    - A Microsoft RMS URL-címének megszerzéséhez nincs szükség Windows PowerShell-parancsmag futtatására.

    - Helyi futtatás esetén a rendszer automatikusan ellenőrzi az előfeltételeket (de nem pótolja őket automatikusan).

Hátrányok:

- Az eszköz futtatásakor kapcsolatot kell létesítenie egy, az RMS-összekötőt már futtató kiszolgálóval.

---

**A beállításjegyzék manuális szerkesztésével:**

- Előnyök:

    - Nincs szükség az RMS-összekötőt futtató kiszolgálóhoz való csatlakozásra.

- Hátrányok:

    - Nagyobb adminisztrációs terhelés és több hibalehetőség.

    - Be kell szereznie a saját Microsoft RMS URL-címét, amelyhez futtatnia kell egy Windows PowerShell-parancsot.

    - Mindig saját kezűleg kell ellenőriznie az előfeltételeket.


---

> [!IMPORTANT]
> Mindkét esetben manuálisan kell telepítenie az előfeltételeket és konfigurálnia az Exchange-et, a SharePointot és a fájlbesorolási infrastruktúrát a Rights Management használatára.

A legtöbb szervezet esetében az automatikusan, a Microsoft RMS-összekötő kiszolgálókonfiguráló eszközével végzett konfiguráció a jobb megoldás, mert hatékonyabb és megbízhatóbb a manuális konfigurálásnál.

Miután végrehajtotta az érintett kiszolgálókon a konfigurációs változtatásokat, újra kell indítania őket, ha Exchange-et vagy SharePointot futtatnak, és korábban az AD RMS használatára voltak konfigurálva. Ha először konfigurálja a kiszolgálókat a Rights Management használatára, nem szükséges újraindítani őket. A konfigurációs módosítások elvégzése után a fájlbesorolási infrastruktúra használatára konfigurált fájlkiszolgálót mindig újra kell indítani.

### A Microsoft RMS-összekötő kiszolgálókonfiguráló eszközének használata

1.  Ha még nem töltötte le a Microsoft RMS-összekötő kiszolgálókonfiguráló eszközének parancsfájlját (GenConnectorConfig.ps1), töltse le a [Microsoft letöltőközpontból](http://go.microsoft.com/fwlink/?LinkId=314106).

2.  Mentse a GenConnectorConfig.ps1 fájlt arra a számítógépre, amelyen az eszközt futtatni fogja. Ha az eszközt helyileg fogja futtatni, ennek a számítógépnek az RMS-összekötővel folytatott kommunikációhoz konfigurálandó kiszolgálónak kell lennie. Egyéb esetben bármilyen számítógépre mentheti a fájlt.

3.  Döntse el, hogyan futtatja az eszközt:

    -   **Helyileg:** Az eszközt futtathatja interaktívan, az RMS-összekötővel folytatott kommunikációhoz konfigurálandó kiszolgálóról. Ez egyszeri konfigurálás esetében, például tesztkörnyezetekben lehet hasznos.

    -   **Szoftverek központi telepítése:** Az eszközzel létrehozhat beállításjegyzék-fájlokat, amelyeket aztán egy vagy több kiszolgálón is üzembe helyezhet egy, a szoftvertelepítést támogató rendszerkezelő alkalmazás, például a System Center Configuration Manager használatával.

    -   **Csoportházirend:** Az eszközzel létrehozhat egy parancsfájlt, amelyet átadhat egy rendszergazdának, aki csoportházirend-objektumokat hozhat létre a konfigurálandó kiszolgálókon való felhasználásra. A parancsfájl minden konfigurálandó kiszolgálótípushoz egy csoportházirend-objektumot hoz létre, amelyeket a rendszergazda hozzárendelhet a kívánt kiszolgálókhoz.

    > [!NOTE]
    > Ez az eszköz konfigurálja azokat a kiszolgálókat, amelyek kommunikálni fognak az RMS-összekötővel, és amelyek a jelen szakasz elején szerepelnek a listában. Ne futtassa ezt az eszközt azokon a kiszolgálókon, amelyek az RMS-összekötőt futtatják.

4.  A **Futtatás rendszergazdaként** beállítással indítsa el a Windows PowerShellt, majd a Get-help paranccsal jelenítse meg az eszköz választott konfigurációs módszer szerinti felhasználásával kapcsolatos utasításokat:

    ```
    Get-help .\GenConnectorConfig.ps1 -detailed
    ```

A parancsfájl futtatásához meg kell adnia a szervezete RMS-összekötőjének URL-címét. Adja meg a protokoll-előtagot (HTTP:// vagy HTTPS://) és az összekötő nevét, amelyet a DNS-ben az összekötője terheléselosztási címeként megadott. Például: https://connector.contoso.com. Az eszköz ezután a megadott URL-cím felhasználásával csatlakozik az RMS-összekötőt futtató kiszolgálókhoz, és beszerzi a szükséges konfigurációk létrehozásához használt további paramétereket.

> [!IMPORTANT]
> Az eszköz futtatásakor győződjön meg róla, hogy a szervezetére vonatkozó terheléselosztási RMS-összekötő nevét adja meg, és nem egy különálló kiszolgálóét, amelyen az RMS-összekötő szolgáltatás fut.

Az egyes szolgáltatástípusokról a következő szakaszokban talál pontosabb információt:

-   [Exchange-kiszolgáló konfigurálása az összekötő használatára](#configuring-an-exchange-server-to-use-the-connector)

-   [SharePoint-kiszolgáló konfigurálása az összekötő használatára](#configuring-a-sharepoint-server-to-use-the-connector)

-   [Fájlbesorolási infrastruktúrát használó fájlkiszolgáló konfigurálása az összekötő használatára](#configuring-a-file-server-for-file-classification-infrastructure-to-use-the-connector)

> [!NOTE]
> Miután ezek a kiszolgálók konfigurálva vannak az összekötő használatára, lehetséges, hogy a rajtuk helyileg telepített ügyfélalkalmazások nem fognak működni az RMS-sel. Ha ez történik, az azért van, mert az alkalmazások az összekötőt próbálják használni az RMS közvetlen használata helyett, ami nem támogatott.
>
> Emellett, ha az Office 2010 helyileg van telepítve egy Exchange-kiszolgálón, az ügyfélalkalmazás IRM-funkciói működhetnek arról a számítógépről, miután a kiszolgálót konfigurálták az összekötő használatára, de ez nem támogatott.
>
> Mindkét esetben olyan különálló számítógépekre kell telepítenie az ügyfélalkalmazásokat, amelyek nincsenek az összekötő használatára konfigurálva. Ekkor a helyes módon, közvetlenül az RMS-t használják majd.

## Exchange-kiszolgáló konfigurálása az összekötő használatára
Az alábbi Exchange-szerepkörök kommunikálnak az RMS-összekötővel:

-   Exchange 2016 and Exchange 2013 esetén: Ügyfélelérési és postaláda-kiszolgáló

-   Exchange 2010 esetén: Ügyfélelérési és elosztó továbbítókiszolgáló

Az RMS-összekötő használatához az Exchange-et futtató kiszolgálóknak az alábbi szoftververziók egyikét kell futtatniuk:

-   Exchange Server 2016

-   Exchange Server 2013 a 3. összegző Exchange 2013-frissítéssel

-   Exchange Server 2010 a 3. Exchange 2010-szervízcsomaggal és a 6. összesített frissítéssel

Emellett ezeken a kiszolgálókon telepítenie kell az RMS-ügyfél egy olyan verzióját, amely támogatja az RMS 2. titkosítási módját. A Windows Server 2008 által támogatott minimális verzió megtalálható abban a gyorsjavításban, amely a következő helyről tölthető le: [RSA key length is increased to 2048 bits for AD RMS in Windows Server 2008 R2 and in Windows Server 2008](http://support.microsoft.com/kb/2627272) (A Windows Server 2008 R2 és Windows Server 2008 rendszereken az AD RMS RSA-kulcshossza 2048 bitre emelkedik). A Windows Server 2008 R2 által támogatott minimális verzió a következő helyről tölthető le: [RSA key length is increased to 2048 bits for AD RMS in Windows 7 or in Windows Server 2008 R2](http://support.microsoft.com/kb/2627273) (A Windows 7 és Windows Server 2008 R2 rendszereken az AD RMS RSA-kulcshossza 2048 bitre emelkedik). A Windows Server 2012 és a Windows Server 2012 R2 natív módon támogatja a 2. titkosítási módot.

> [!IMPORTANT]
> Ha az Exchange ezen vagy későbbi verziói és az RMS-ügyfél nincs telepítve, az Exchange-et nem lehet az összekötő használatára konfigurálni. A folytatás előtt ellenőrizze, hogy a szükséges verziók telepítve vannak-e.

### Exchange-kiszolgálók konfigurálása az összekötő használatára

1. Az RMS-összekötőfelügyelő és az [Authorizing servers to use the RMS connector](install-configure-rms-connector.md#authorizing-servers-to-use-the-rms-connector) (Az RMS-összekötő használatának engedélyezése a kiszolgálók számára) című szakasz információi segítségével győződjön meg róla, hogy az Exchange-kiszolgálók jogosultak az RMS-összekötő használatára. Ez a konfiguráció szükséges ahhoz, hogy az Exchange használni tudja az RMS-összekötőt.

2.  Az RMS-összekötővel kommunikáló Exchange-szerepkörökkel kapcsolatban tegye a következők egyikét:

    -   Futtassa le a Microsoft RMS-összekötő kiszolgálókonfiguráló eszközét. További információért lásd a jelen cikk [A Microsoft RMS-összekötő kiszolgálókonfiguráló eszközének használata](#how-to-use-the-server-configuration-tool-for-microsoft-rms-connector) című szakaszát.

        Például az eszköz helyi futtatásához egy Exchange 2016-ot vagy Exchange 2013-at futtató kiszolgáló konfigurálásához:

        ```
        .\GenConnectorConfig.ps1 -ConnectorUri https://rmsconnector.contoso.com -SetExchange2013
        ```

    -   Szerkessze saját kezűleg a beállításjegyzéket a [Registry settings for the RMS connector](rms-connector-registry-settings.md) (Az RMS-összekötő beállításjegyzékbeli beállításai) című szakaszban olvasható információk alapján a kiszolgálók beállításainak kézi hozzáadásához. 

3.  Engedélyezze az IRM-funkciókat az Exchange-ben. További információkat az Exchange-könyvtár [Information Rights Management Procedures](https://technet.microsoft.com/library/dd351212%28v=exchg.150%29.aspx) (Tartalomvédelmi szolgáltatások eljárásai) című részében találhat.

    > [!NOTE]
    > Alapértelmezés szerint a **Set-IRMConfiguration -InternalLicensingEnabled $true** futtatása után a rendszer automatikusan engedélyezi az IRM-et a postaládák mellett az Outlook Web App és a mobileszközök esetében is. Azonban a rendszergazdák az IRM-et letilthatják a különböző szinteken, például egy ügyfélelérési kiszolgáló, az Outlook Web App virtuális könyvtára vagy az Outlook Web App postaláda-házirendje, illetve egy mobileszköz postafiók-házirendje révén. Ha a felhasználók egyetlen Azure RMS-sablont sem látnak az Outlook Web App alkalmazásban (még egy nap várakozás után sem) vagy mobileszközökön, miközben az Outlook ügyfélben látszanak a sablonok, ellenőrizze a vonatkozó beállítások között, hogy nincs-e letiltva az IRM. További információt az Exchange-dokumentáció [Enable or Disable Information Rights Management on Client Access Servers](https://technet.microsoft.com/library/dd876938(v=exchg.150).aspx) (A tartalomvédelmi szolgáltatások engedélyezése vagy letiltása az ügyfélelérési kiszolgálókon) című részében találhat. 


## SharePoint-kiszolgáló konfigurálása az összekötő használatára
Az alábbi SharePoint-szerepkörök kommunikálnak az RMS-összekötővel:

-   Előtérbeli SharePoint-webkiszolgálók, köztük a központi felügyeleti kiszolgáló gazdái

Az RMS-összekötő használatához a SharePointot futtató kiszolgálóknak az alábbi szoftververziók egyikét kell futtatniuk:

-   SharePoint Server 2016

-   SharePoint Server 2013

-   SharePoint Server 2010

Egy SharePoint 2016-ot vagy SharePoint 2013-at futtató kiszolgálónak az MSIPC ügyfél 2.1 egy olyan verzióját is futtatnia kell, amely támogatott az RMS-összekötő mellett. Hogy biztosan a támogatott verzióval rendelkezzen, töltse le a legfrissebb ügyfélprogramot a [Microsoft letöltőközpontból](http://www.microsoft.com/download/details.aspx?id=38396).

> [!WARNING]
> Az MSIPC 2.1 ügyfélnek több verziója is van, ezért győződjön meg róla, hogy 1.0.2004.0-s vagy annál újabb verzióval rendelkezik.
>
> Az ügyfél verzióját az MSIPC.dll fájl verziószámának ellenőrzésével tudja megerősíteni, amely a **\Program Files\Active Directory Rights Management Services Client 2.1**mappában található. Az MSIPC 2.1 ügyfél verziószáma a Tulajdonságok párbeszédablakban látható.

A SharePoint 2010-et futtató kiszolgálókon telepítve kell lennie az MSDRM-ügyfél egy olyan verziójának, amely támogatja az RMS 2. titkosítási módját. A Windows Server 2008 által támogatott minimális verzió megtalálható abban a gyorsjavításban, amely a következő helyről tölthető le: [RSA key length is increased to 2048 bits for AD RMS in Windows Server 2008 R2 and in Windows Server 2008](http://support.microsoft.com/kb/2627272) (A Windows Server 2008 R2 és Windows Server 2008 rendszereken az AD RMS RSA-kulcshossza 2048 bitre emelkedik), míg a Windows Server 2008 R2 által támogatott minimális verzió a következő helyről tölthető le: [RSA key length is increased to 2048 bits for AD RMS in Windows 7 or in Windows Server 2008 R2](http://support.microsoft.com/kb/2627273) (A Windows 7 és Windows Server 2008 R2 rendszereken az AD RMS RSA-kulcshossza 2048 bitre emelkedik). A Windows Server 2012 és a Windows Server 2012 R2 natív módon támogatja a 2. titkosítási módot.

### SharePoint-kiszolgálók konfigurálása az összekötő használatára

1. Az RMS-összekötőfelügyelő és az [Authorizing servers to use the RMS connector](install-configure-rms-connector.md#authorizing-servers-to-use-the-rms-connector) (Az RMS-összekötő használatának engedélyezése a kiszolgálók számára) című szakasz információi segítségével győződjön meg róla, hogy a SharePoint-kiszolgálók jogosultak az RMS-összekötő használatára. Ez a konfiguráció szükséges ahhoz, hogy az Exchange használni tudja az RMS-összekötőt.

2.  Az RMS-összekötővel kommunikáló SharePoint-kiszolgálókkal kapcsolatban tegye a következők egyikét:

    -   Futtassa le a Microsoft RMS-összekötő kiszolgálókonfiguráló eszközét. További információért lásd a jelen cikk [A Microsoft RMS-összekötő kiszolgálókonfiguráló eszközének használata](#how-to-use-the-server-configuration-tool-for-microsoft-rms-connector) című szakaszát.

        Például az eszköz helyi futtatásához egy SharePoint 2016-ot vagy SharePoint 2013-at futtató kiszolgáló konfigurálásához:

        ```
        .\GenConnectorConfig.ps1 -ConnectorUri https://rmsconnector.contoso.com -SetSharePoint2013
        ```

    -   Ha SharePoint 2016-ot vagy SharePoint 2013-at használ, szerkessze saját kezűleg a beállításjegyzéket a [Registry settings for the RMS connector](rms-connector-registry-settings.md) (Az RMS-összekötő beállításjegyzékbeli beállításai) című szakaszban olvasható információk alapján a kiszolgálók beállításainak kézi hozzáadásához. 

3.  Engedélyezze az IRM-et a SharePointban. További információkat a SharePoint-könyvtár [Configure Information Rights Management (SharePoint Server 2010)](https://technet.microsoft.com/library/hh545607%28v=office.14%29.aspx) (Tartalomvédelmi szolgáltatások beállítása (SharePoint Server 2010)) című részében találhat.

    Ha követi ezeket az utasításokat, a SharePointot az **Ezen Windows tartalomvédelmi kiszolgáló használata:** lehetőséggel kell az összekötő használatára konfigurálnia, majd meg kell adnia az összekötőhöz beállított terheléselosztási URL-címet is. Adja meg a protokoll-előtagot (HTTP:// vagy HTTPS://) és az összekötő nevét, amelyet a DNS-ben az összekötője terheléselosztási címeként megadott. Például, ha az összekötője neve https://connector.contoso.com, a konfiguráció a következőképpen fog kinézni:

    ![A SharePoint-kiszolgáló konfigurálása az RMS-összekötőhöz](../media/AzRMS_SharePointConnector.png)

    Miután egy SharePoint-farmon engedélyezte az IRM-et, az önálló könyvtárakra vonatkozóan is engedélyezheti azt, a **Tartalomvédelmi szolgáltatások** opcióval az egyes könyvtárak **Könyvtárbeállítások** oldalán.


## Fájlbesorolási infrastruktúrát használó fájlkiszolgáló konfigurálása az összekötő használatára
Ahhoz, hogy az RMS-összekötőt és a fájlbesorolási infrastruktúrát Office-dokumentumok védelmére lehessen használni, a fájlkiszolgálónak a következő operációs rendszerek egyikét kell futtatnia:

-   Windows Server 2012 R2

-   Windows Server 2012

### Fájlkiszolgálók konfigurálása az összekötő használatára

1.  Az RMS-összekötőfelügyelő és az [Authorizing servers to use the RMS connector](install-configure-rms-connector.md#authorizing-servers-to-use-the-rms-connector) (Az RMS-összekötő használatának engedélyezése a kiszolgálók számára) című szakasz információi segítségével győződjön meg róla, hogy a fájlkiszolgálók jogosultak az RMS-összekötő használatára. Ez a konfiguráció szükséges ahhoz, hogy az Exchange használni tudja az RMS-összekötőt.

2.  Az RMS-összekötővel kommunikáló és a fájlbesorolási infrastruktúrára konfigurált fájlkiszolgálókon tegye a következők egyikét:

    -   Futtassa le a Microsoft RMS-összekötő kiszolgálókonfiguráló eszközét. További információért lásd a jelen cikk [A Microsoft RMS-összekötő kiszolgálókonfiguráló eszközének használata](#how-to-use-the-server-configuration-tool-for-microsoft-rms-connector) című szakaszát.

        Például az eszköz helyi futtatásához konfiguráljon egy FCI-t futtató fájlkiszolgálót:

        ```
        .\GenConnectorConfig.ps1 -ConnectorUri https://rmsconnector.contoso.com -SetFCI2012
        ```

    - Szerkessze saját kezűleg a beállításjegyzéket a [Registry settings for the RMS connector](rms-connector-registry-settings.md) (Az RMS-összekötő beállításjegyzékbeli beállításai) című szakaszban olvasható információk alapján a kiszolgálók beállításainak kézi hozzáadásához. 

3.  Hozzon létre besorolási szabályokat és fájlkezelési feladatokat a dokumentumok RMS-titkosítással történő védelmére, majd határozzon meg egy RMS-sablont az RMS-házirendek automatikus alkalmazásához. További információkat a Windows Server dokumentációs könyvtárának [A fájlkiszolgálói erőforrás-kezelő áttekintése](http://technet.microsoft.com/library/hh831701.aspx) című részében talál.

## További lépések
Most, hogy az RMS-összekötőt telepítette és konfigurálta, valamint a kiszolgálókat is konfigurálta a használatára, az informatikai rendszergazdák és a felhasználók megvédhetik és felhasználhatják az e-mail-üzeneteket és a dokumentumokat az Azure RMS használatával. Hogy megkönnyítse a felhasználók dolgát, helyezze üzembe az RMS megosztóalkalmazását, amely telepít egy Office-bővítményt és új, a jobb kattintásra megjelenő opciókat tesz elérhetővé a Fájlkezelőben. További információk: [Rights Management sharing application administrator guide](../rms-client/sharing-app-admin-guide.md) (A Rights Management megosztóalkalmazás rendszergazdai kézikönyve).

Az [Azure Rights Management deployment roadmap](../plan-design/deployment-roadmap.md) (Azure Rights Management üzembe helyezési menetrend) segítségével ellenőrizheti, hogy vannak-e további konfigurációs lépések, amelyeket érdemes lehet megtenni, mielőtt a felhasználók és rendszergazdák megkezdik az [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] használatát.

Az RMS-összekötő megfigyelése: [Az Azure Rights Management-összekötő megfigyelése](monitor-rms-connector.md). 



<!--HONumber=Jun16_HO4-->


