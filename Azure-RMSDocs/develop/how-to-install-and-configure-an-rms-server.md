---
# required metadata

title: Install and configure the server (A kiszolgáló telepítése és konfigurálása) | Azure RMS
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

# A kiszolgáló telepítése és konfigurálása

Ez a témakör az RMS-kiszolgáló telepítésének és konfigurálásának lépéseit tartalmazza a tartalomvédelemmel kompatibilis alkalmazás teszteléséhez.

**Fontos**: Ha az alkalmazást az alkalmazás futtatásával teszteli az 1 keretes RMS ISV-környezetben, nem szükséges telepítenie az RMS-kiszolgálót, mert az már telepítve és konfigurálva van az 1 keretes környezetben.
További információt a 1 keretes AD RMS ISV-környezetről a [Set up the test environment](how-to-set-up-your-test-environment.md) (A tesztelési környezet létrehozása) című témakörben talál.

 

## Utasítások

### 1. lépés: Állítsa be az RMS-kiszolgálót

A következő lépések segítségével beállíthatja az RMS-kiszolgálót:

-   A beállításjegyzék konfigurálása
-   A kiszolgáló telepítése
-   A kiszolgáló beléptetése

1.  **A beállításjegyzék konfigurálása**

    Annak megadásához, hogy az éles üzem előtti tanúsítványhierarchiát használja, állítsa be a következő beállításazonosítókat.

    **Megjegyzés**: Ha Windows Server 2008 R2 vagy Windows Server 2008 operációs rendszert használ, állítsa be a beállításazonosítókat az AD RMS szolgáltatás telepítése előtt.

    Ha Windows Server 2008 R2 operációs rendszeren használja az AD RMS szolgáltatást, állítsa be az alábbi **REG\_DWORD** értéket. Az éles hierarchiára való váltáshoz állítsa ezt az értéket nullára (0).

    **Computer**\\**HKEY\_LOCAL\_MACHINE**\\**Software**\\**Microsoft**\\**DRMS**\\**Hierarchy** = 0x00000001

    Ha Windows Server 2008 R2 operációs rendszeren használja az AD RMS szolgáltatást, és egy másik AD RMS szolgáltatás már telepítve van az Active Directoryban éles üzem előtti szolgáltatásként, adja hozzá a következő üres karakterláncértéket a beállításjegyzékhez.

    **Computer**\\**HKEY\_LOCAL\_MACHINE**\\**Software**\\**Microsoft**\\**DRMS**\\**GICURL** = ""

    Ha Windows Server 2008 operációs rendszeren használja az AD RMS szolgáltatást, állítsa be az alábbi **REG\_DWORD** értéket. Az éles hierarchiára való váltáshoz állítsa ezt az értéket nullára (0).

    **Computer**\\**HKEY\_LOCAL\_MACHINE**\\**Software**\\**Microsoft**\\**DRMS**\\**2.0**\\**Hierarchy** = 0x00000001

    Ha Windows Server 2008 operációs rendszeren használja az AD RMS szolgáltatást, és egy másik AD RMS szolgáltatás már telepítve van az Active Directoryban éles üzem előtti szolgáltatásként, adja hozzá a következő üres karakterláncértéket a beállításjegyzékhez.

    **Computer**\\**HKEY\_LOCAL\_MACHINE**\\**Software**\\**Microsoft**\\**DRMS**\\**2.0**\\**GICURL** = ""

2.  **A kiszolgáló telepítése**

    Az Active Directory Rights Management Services (AD RMS) külön ügyfél- és kiszolgáló-összetevőkből áll. A kiszolgáló-összetevő megvalósítása webszolgáltatásként történik, amely az RMS-infrastruktúra felügyeletéhez, a fogyasztók és a közzétevők számára licencek, illetve a számítógépek és a felhasználók számára tanúsítványok kibocsátásához használható.

    A Windows Server 2008 óta az ügyfél- és a kiszolgáló-összetevők is az operációs rendszer részét képezik. A korábbi operációs rendszerekhez letöltheti a kiszolgáló-összetevőket a következő helyről.

    -   [RMS Server v1.0 SP2](http://go.microsoft.com/fwlink/p/?linkid=73722)

    A kiszolgáló-összetevő Windows Server 2008 operációs rendszeren való konfigurálásához telepítenie kell az AD RMS szerepkört. Előtte azonban konfigurálnia kell a beállításjegyzéket annak megadásához, hogy az éles üzem előtti tanúsítványhierarchiát fogja használni az éles hierarchia helyett. Ha azonban egy korábbi kiszolgáló operációs rendszeren fejleszt alkalmazásokat, konfigurálja a beállításjegyzéket az 1.0-s verziójú RMS-kiszolgáló SP2 telepítése után, de még az RMS-kiszolgáló üzembe helyezése előtt.

    További információkért tekintse meg az előző lépést (1. lépés: A beállításjegyzék konfigurálása).

3.  **A kiszolgáló beléptetése**

    A Rights Management Services (RMS) kiszolgálót az éles üzem előtti vagy éles hierarchiában való azonosításukhoz be kell léptetnie. A beléptetési folyamat egy kiszolgálólicenc-tanúsítványt helyez el a kiszolgáló számítógépen. Ez a tanúsítvány a Microsoft bizalomforrásához kötődik. A kiszolgáló beléptetésének módja az RMS használt verziójától függ.

    -   **Önbeléptetés**

        A Windows Server 2008 óta anélkül léptetheti be az RMS-kiszolgálót a megfelelő hierarchiába, hogy információkat küldene a Microsoftnak. Az RMS szerepkör telepítésekor a rendszer telepíti az önbeléptetési tanúsítványt és a titkos kulcsot is. Ezek segítéségével a kiszolgálólicenc-tanúsítvány automatikusan létrehozható. A rendszer nem küld információkat a Microsoftnak.

    -   **Online beléptetés**: Ha az 1.0-s verziójú AD RMS SP2-t használja, online is beléptetheti a kiszolgálót. A beléptetés a háttérben történik az üzembe helyezési folyamat során, azonban szükség van internetkapcsolatra, és meg kell adnia a megfelelő beállításazonosítót, hogy kiválaszthassa, melyik hierarchiába lépteti be a kiszolgálót. Az éles üzem előtti hierarchiába való beléptetéshez adja hozzá a következő **REG\_SZ** értéket, és helyezze üzembe a kiszolgálót. Az éles hierarchiába való beléptetéshez törölje ezt az értéket, és helyezze üzembe a kiszolgálót.

        További információkért tekintse meg az előző lépést (1. lépés: A beállításjegyzék konfigurálása).

        **HKEY\_LOCAL\_MACHINE**\\**Software**\\**Microsoft**\\**DRMS**\\**1.0**\\**UddiProvider** = 0e3d9bb8-b765-4a68-a329-51548685fed3

## Kapcsolódó témakörök

* [Használati útmutató](how-to-use-msipc.md)
 

 





<!--HONumber=Apr16_HO4-->


