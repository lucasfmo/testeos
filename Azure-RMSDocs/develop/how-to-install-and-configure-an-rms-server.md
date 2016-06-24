---
# required metadata

title: Útmutató: telepítés, konfigurálás és tesztelés az RMS-kiszolgálóval | Azure RMS
description: Telepítse és konfigurálja az RMS-kiszolgálót a tartalomvédelemmel kompatibilis alkalmazás teszteléséhez.
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 32C7F387-CF7E-4CE0-AFC9-4C63FE1E134A
# optional metadata

#ROBOTS:
audience: developer
#ms.devlang:
ms.reviewer: shubhamp
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Útmutató: telepítés, konfigurálás és tesztelés az RMS-kiszolgálóval

Ez a témakör az RMS-kiszolgálóhoz vagy az Azure RMS-hez való csatlakozás lépéseit tartalmazza a tartalomvédelemmel kompatibilis alkalmazás teszteléséhez.
 
## Utasítások

### 1. lépés: Állítsa be az RMS-kiszolgálót

A következő lépések segítségével beállíthatja az RMS-kiszolgálót:

-   A kiszolgáló telepítése
-   A kiszolgáló beléptetése

1.  **A kiszolgáló telepítése**

    Az Active Directory Rights Management Services (AD RMS) külön ügyfél- és kiszolgáló-összetevőkből áll. A kiszolgáló-összetevő megvalósítása webszolgáltatásként történik, amely az RMS-infrastruktúra felügyeletéhez, a fogyasztók és a közzétevők számára licencek, illetve a számítógépek és a felhasználók számára tanúsítványok kibocsátásához használható.

    A Windows Server 2008 óta az ügyfél- és a kiszolgáló-összetevők is az operációs rendszer részét képezik. A korábbi operációs rendszerekhez letöltheti a kiszolgáló-összetevőket a következő helyről.

    -   [RMS Server v1.0 SP2](http://go.microsoft.com/fwlink/p/?linkid=73722)

    A kiszolgáló-összetevő Windows Server 2008 operációs rendszeren való konfigurálásához telepítenie kell az AD RMS szerepkört. Ha egy korábbi kiszolgáló operációs rendszeren fejleszt alkalmazásokat, konfigurálja a beállításjegyzéket az 1.0-s verziójú RMS-kiszolgáló SP2 telepítése után, de még az RMS-kiszolgáló üzembe helyezése előtt.

2.  **A kiszolgáló beléptetése**

    A Rights Management Services (RMS) kiszolgálót az éles üzem előtti vagy éles hierarchiában való azonosításukhoz be kell léptetnie. A beléptetési folyamat egy kiszolgálólicenc-tanúsítványt helyez el a kiszolgáló számítógépen. Ez a tanúsítvány a Microsoft bizalomforrásához kötődik. A kiszolgáló beléptetésének módja az RMS használt verziójától függ.

    -   **Önbeléptetés**

        A Windows Server 2008 óta anélkül léptetheti be az RMS-kiszolgálót a megfelelő hierarchiába, hogy információkat küldene a Microsoftnak. Az RMS szerepkör telepítésekor a rendszer telepíti az önbeléptetési tanúsítványt és a titkos kulcsot is. Ezek segítéségével a kiszolgálólicenc-tanúsítvány automatikusan létrehozható. A rendszer nem küld információkat a Microsoftnak.

    -   **Online beléptetés**

        Ha az 1.0-s verziójú AD RMS SP2-t használja, online is beléptetheti a kiszolgálót. A beléptetés az üzembe helyezési folyamat alatt a háttérben történik, de kizárólag működő internetkapcsolat esetén.

        **HKEY\_LOCAL\_MACHINE**\\**Software**\\**Microsoft**\\**DRMS**\\**1.0**\\**UddiProvider** = 0e3d9bb8-b765-4a68-a329-51548685fed3

3. **Tesztelés az RMS-kiszolgálóval**

    Az RMS-kiszolgálóval való teszteléshez konfigurálja a kiszolgálóoldali vagy az ügyféloldali észlelést, hogy a Rights Management Service ügyfélprogram 2.1-es verziója felderítse és létrehozza a kommunikációt az RMS-kiszolgálóval.

    > [!Note] Az Azure RMS-szel való tesztelés nem igényel felderítési konfigurációt.

  - A kiszolgálóoldali felderítés során egy rendszergazda regisztrál egy szolgáltatáskapcsolati pontot (SCP) az Active Directoryban az RMS-gyökérfürthöz, az ügyfél pedig az Active Directoryt lekérdezve észlelheti az SCP-t és hozhat létre kapcsolatot a kiszolgálóval.
  - Ügyféloldali felderítés esetén annak a számítógépnek a beállításjegyzékben kell konfigurálni az RMS szolgáltatásészlelés beállításait, ahol az RMS-ügyfélprogram 2.1-es verziója fut. Ezek a beállítások adják meg az RMS-kiszolgáló számára, hogy az RMS-ügyfélprogram 2.1-es verzióját használja. Ha ezek meg vannak adva, a rendszer nem végez kiszolgálóoldali felderítést.

  Az ügyféloldali felderítés konfigurálásához beállíthatja a következő beállításkulcsokat, hogy azok az éles az RMS-kiszolgálóra mutassanak. A kiszolgálóoldali felderítés konfigurálásáról további információt [Az RMS 2.0-s ügyfelének üzembe helyezésével kapcsolatos megjegyzések](https://technet.microsoft.com/en-us/library/jj159267(WS.10).aspx) című témakörben találhat.

1. **EnterpriseCertification**
        HKEY_LOCAL_MACHINE        SOFTWARE          Microsoft            MSIPC              ServiceLocation                EnterpriseCertification

  **Érték**: (alapértelmezett): [**http|https**]://RMSClusterName/**_wmcs/Certification**

2. **EnterprisePublishing**
        HKEY_LOCAL_MACHINE        SOFTWARE          Microsoft            MSIPC              ServiceLocation                EnterprisePublishing **Érték**: (alapértelmezett): [**http|https**]://RMSClusterName/**_wmcs/Licensing**

>[!NOTE] Alapértelmezés szerint ezek a kulcsok nem szerepelnek a beállításjegyzékben, és létre kell őket hozni.

>[!IMPORTANT] Ha egy 32 bites alkalmazást futtat egy 64 bites Windows-verzión, meg kell adnia ezeket a kulcsokat a következő kulcshelyen:<p>
  ```    
  HKEY_LOCAL_MACHINE
    SOFTWARE
      Wow6432Node
        Microsoft
          MSIPC
            ```

 

 


<!--HONumber=Jun16_HO2-->


