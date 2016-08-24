---
title: "Áttelepítés AD RMS-ről Azure Rights Managementre – 3. fázis | Azure RMS"
description: 
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 08/17/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 8b039ad5-95a6-4c73-9c22-78c7b0e12cb7
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 437afd88efebd9719a3db98f8ab0ae07403053f7
ms.openlocfilehash: 6d3cb53fb199bb880a0e61d2b964f297e547a027


---

# 3. áttelepítési fázis – támogatási szolgáltatások konfigurációja

*A következőkre vonatkozik: Active Directory Rights Management Services, Azure Rights Management*


Az alábbi, 3. fázisra vonatkozó információk segítséget nyújtanak az AD RMS-ről az Azure Rights Managementre (Azure RMS) való áttelepítésben. Ezek az eljárások megfelelnek az [Áttelepítés AD RMS-ről Azure Rights Managementre](migrate-from-ad-rms-to-azure-rms.md) című cikk 6–7. lépésének.


## 6. lépés IRM-integráció konfigurálása Exchange Online-ban

Ha a TDP-t korábban az AD RMS szolgáltatásból importálta az Exchange Online-ba, az Azure RMS-be történő áttelepítés utáni sablon- és házirendütközés elkerülése érdekében először el kell távolítania a TDP-t. Ehhez a [Remove-RMSTrustedPublishingDomain](https://technet.microsoft.com/library/jj200720%28v=exchg.150%29.aspx) parancsmagot használhatja az Exchange Online-ból.

Ha a **Microsoft által felügyelt** Azure RMS bérlőkulcs-topológiát választotta:

-   Tekintse meg az [Office 365: Konfigurálás ügyfelek és online szolgáltatások számára](../deploy-use/configure-office365.md) című cikk [Exchange Online: az IRM konfigurálása](../deploy-use/configure-office365.md#exchange-online-irm-configuration) szakaszát. Ez a szakasz olyan tipikus parancsokat tartalmaz, amelyek futtatásával csatlakozhat az Exchange Online szolgáltatáshoz, importálhatja a bérlőkulcsot az Azure RMS-ből, valamint elérheti az IRM-funkciókat az Exchange Online-ban. A lépések végrehajtása után az összes RMS-funkció elérhetővé válik az Exchange Online-nal.

Ha az **ügyfél által felügyelt (BYOK)** Azure RMS bérlőkulcs-topológiát választotta:

-   Az RMS-funkciók az Exchange Online szolgáltatásban korlátozottan érhetők el, a [BYOK pricing and restrictions](byok-price-restrictions.md) (A BYOK díjszabása és korlátozásai) cikkben leírtaknak megfelelően.

## 7. lépés Az RMS-összekötő üzembe helyezése
Ha használta az Exchange-kiszolgáló vagy a SharePoint-kiszolgáló tartalomvédelmi szolgáltatásait (IRM) az AD RMS szolgáltatással, először tiltsa le az IRM-et ezeken a kiszolgálókon, és távolítsa el az AD RMS-konfigurációt. Ezután helyezze üzembe a tartalomvédelmi (RMS) összekötőt, ami kommunikációs interfészként (továbbítóként) működik a helyszíni kiszolgálók és az Azure RMS között.

Ha több, az e-mail-üzenetek védelmére szolgáló AD RMS-adatkonfigurációs .xml-fájlt importált az Azure RMS szolgáltatásba, a lépés végén végezze el a beállításjegyzék manuális szerkesztését az Exchange-kiszolgáló számítógépeken az összes megbízható közzétételi tartomány URL-címének az RMS-összekötőre történő átirányításához.

> [!NOTE]
> Mielőtt elkezdi a műveletet, ellenőrizze az Azure RMS által támogatott helyszíni kiszolgálók verzióit [Az Azure RMS-t támogató helyszíni kiszolgálók](../get-started/requirements-servers.md) című cikk útmutatása alapján.

### Az IRM letiltása az Exchange-kiszolgálókon és az AD RMS-konfiguráció eltávolítása

1.  Keresse meg a következő mappát az egyes Exchange-kiszolgálókon, és törölje belőle azt összes bejegyzést: \ProgramData\Microsoft\DRM\Server\S-1-5-18

2.  Az egyik Exchange-kiszolgálón az Exchange [Set_IRMConfiguration](http://technet.microsoft.com/library/dd979792.aspx) parancsmaggal először tiltsa le a belső címzetteknek küldött üzenetek IRM-funkcióit:

    ```
    Set-IRMConfiguration -InternalLicensingEnabled $false
    ```

3.  Ezután ugyanezt a parancsmagot használva tiltsa le a külső címzetteknek küldött üzenetek IRM-funkcióit:

    ```
    Set-IRMConfiguration -ExternalLicensingEnabled $false
    ```

4.  Következő lépésként ugyanezzel a parancsmaggal tiltsa le az IRM-et a Microsoft Office Outlook Web Appben és a Microsoft Exchange ActiveSyncben:

    ```
    Set-IRMConfiguration -ClientAccessServerEnabled $false
    ```

5.  Végül ugyanezt a parancsmagot használva törölje a gyorsítótárazott tanúsítványokat:

    ```
    Set-IRMConfiguration -RefreshServerCertificates
    ```

6.  Állítsa alaphelyzetbe az IIS-t az egyes Exchange-kiszolgálókon a parancssor rendszergazdaként történő futtatásával és az **iisreset** karakterlánc begépelésével.

### Az IRM letiltása az SharePoint-kiszolgálókon és az AD RMS-konfiguráció eltávolítása

1.  Győződjön meg róla, hogy az RMS által védett könyvtárakból nincsenek-e kivéve dokumentumok. Ha vannak, ezek az eljárás végére nem lesznek elérhetők.

2.  A SharePoint központi felügyeleti webhely **Gyorsindítás** szakaszában kattintson a **Biztonság** elemre.

3.  A **Biztonság** lap **Tájékoztatási házirend** szakaszában kattintson a **Tartalomvédelmi szolgáltatás beállítása** elemre.

4.  A **Tartalomvédelmi szolgáltatás** lap **Tartalomvédelmi szolgáltatás** szakaszában válassza az **Ezen a kiszolgálón ne fusson tartalomvédelmi szolgáltatás** lehetőséget, majd kattintson az **OK** gombra.

5.  Törölje a következő mappa tartalmát a SharePoint Servert futtató számítógépeken: \ProgramData\Microsoft\MSIPC\Server\*&lt;a SharePoint Servert futtató fiók SID azonosítója&gt;*.

#### Az RMS-összekötő telepítése és beállítása

-   Kövesse a [Deploying the Azure Rights Management Connector (Az Azure Rights Management-összekötő üzembe helyezése)](../deploy-use/deploy-rms-connector.md) című cikkben leírt utasításokat.

#### Csak Exchange és több TPD esetén: A beállításjegyzék szerkesztése

-   Az egyes Exchange-kiszolgálókon adja hozzá manuálisan a további importált konfigurációs .xml-adatfájlokhoz tartozó következő beállításkulcsokat a megbízható közzétételi tartomány URL-címeinek az RMS-összekötőre történő átirányításához. Ezek a beállításjegyzékbeli bejegyzések az áttelepítésre vonatkoznak, és a kiszolgálókonfigurációs eszköz nem végzi el a Microsoft RMS-összekötőre vonatkozó hozzáadásukat.

    A beállításjegyzék szerkesztésekor kövesse az alábbi utasításokat:

    -   Az *összekötőFQDN* karaktersort cserélje le arra a névre, amelyet a DNS-ben megadott az összekötőnek. Például: **rmsconnector.contoso.com**.

    -   Az összekötő URL-címéhez HTTP vagy HTTPS protokollt használjon attól függően, hogy az összekötő és a helyszíni kiszolgálók közti kommunikációhoz HTTP vagy HTTPS protokollt konfigurált.

Exchange 2013 – 1. beállításjegyzék-bejegyzés esetén:


**Beállításjegyzékbeli elérési út:**

HKLM\SOFTWARE\Microsoft\ExchangeServer\v15\IRM\LicenseServerRedirection

**Írja be:**

REG_SZ

**Érték:**

https://<AD RMS Intranet Licensing URL>/_wmcs/licensing

**Adat:**

A következők egyike, attól függően, hogy az Exchange-kiszolgáló és az RMS-összekötő között HTTP vagy HTTPS protokollt használ:

- http://<connectorFQDN>/_wmcs/licensing

- https://<connectorName>/_wmcs/licensing


---

Exchange 2013 – 2. beállításjegyzék-bejegyzés esetén:

**Beállításjegyzékbeli elérési út:**

HKLM\SOFTWARE\Microsoft\ExchangeServer\v15\IRM\LicenseServerRedirection 


**Írja be:**

REG_SZ

**Érték:**

https://<AD RMS Extranet Licensing URL>/_wmcs/licensing


**Adat:**

A következők egyike, attól függően, hogy az Exchange-kiszolgáló és az RMS-összekötő között HTTP vagy HTTPS protokollt használ:

- http://<connectorFQDN>/_wmcs/licensing

- https://<connectorFQDN>/_wmcs/licensing

---

Exchange 2010 – 1. beállításjegyzék-bejegyzés esetén:



**Beállításjegyzékbeli elérési út:**

HKLM\SOFTWARE\Microsoft\ExchangeServer\v14\IRM\LicenseServerRedirection

**Írja be:**

REG_SZ

**Érték:**

https://<AD RMS Intranet Licensing URL>/_wmcs/licensing

**Adat:**

A következők egyike, attól függően, hogy az Exchange-kiszolgáló és az RMS-összekötő között HTTP vagy HTTPS protokollt használ:

- http://<connectorFQDN>/_wmcs/licensing

- https://<connectorName>/_wmcs/licensing


---

Exchange 2010 – 2. beállításjegyzék-bejegyzés esetén:


**Beállításjegyzékbeli elérési út:**

HKLM\SOFTWARE\Microsoft\ExchangeServer\v14\IRM\LicenseServerRedirection
 

**Írja be:**

REG_SZ

**Érték:**

https://<AD RMS Extranet Licensing URL>/_wmcs/licensing


**Adat:**

A következők egyike, attól függően, hogy az Exchange-kiszolgáló és az RMS-összekötő között HTTP vagy HTTPS protokollt használ:

- http://<connectorFQDN>/_wmcs/licensing

- https://<connectorFQDN>/_wmcs/licensing

---

A fenti eljárások végrehajtását követően készen áll arra, hogy elolvassa a [Deploying the Azure Rights Management connector](../deploy-use/deploy-rms-connector.md) (Az Azure Rights Management-összekötő üzembe helyezése) című cikk **További lépések** szakaszát.

## További lépések
Az áttelepítés folytatásához ugorjon a [4. fázis – áttelepítés utáni feladatok](migrate-from-ad-rms-phase4.md) című szakaszra.


<!--HONumber=Aug16_HO3-->


