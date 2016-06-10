---
# required metadata

title: A tesztkörnyezet beállítása | Azure RMS
description: A tartalomvédelemmel kompatibilis alkalmazás különböző kiszolgálóbeállításokkal tesztelhető.
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: E480D8D6-F070-43D1-B2B0-6921459C3437
# optional metadata

#ROBOTS:
audience: developer
#ms.devlang:
ms.reviewer: shubhamp
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# A tesztkörnyezet beállítása

A tartalomvédelemmel kompatibilis alkalmazás különböző kiszolgálóbeállításokkal tesztelhető.

**Fontos** Először ajánlott a Rights Management Services SDK 2.1 alkalmazás az éles üzem előtti AD RMS környezetben egy AD RMS-kiszolgálóval tesztelni. Ha ezután azt szeretné, hogy az ügyfél használhassa az alkalmazást az Azure RMS szolgáltatással, folytassa a tesztelést ezzel a környezettel. További információ: [Enable your service application to work with cloud based RMS](how-to-use-file-api-with-aadrm-cloud.md) (A szolgáltatásalkalmazás alkalmassá tétele a felhőalapú RMS használatára).

 

### Előfeltételek

-   [Az SDK telepítése](create-your-first-rights-aware-application.md)

Utasítások

### 1. lépés: A tesztkörnyezet beállítása

A tartalomvédelemmel kompatibilis alkalmazást a tesztelés során az éles üzem előtti használathoz konfigurált RMS-kiszolgálóval kell futtatnia. Az éles üzem előtti RMS-kiszolgáló az éles üzem előtti/ISV tanúsítványhierarchiával titkosítja és fejti vissza a fájlokat.

Az AD RMS tanúsítványhierarchiáról további információért lásd: [Understanding certificate chains](understanding-certificate-chains.md) (A tanúsítványláncok megértése).

Két lehetőség érhető el az alkalmazás RMS-kiszolgálón való teszteléséhez:

-   **Az alkalmazást a 1-box AD RMS ISV környezeten futtathatja**. Ha a Windows Server 2012, Windows Server 2008 R2 vagy Windows Server 2008 rendszert futtatja és telepítve van a Hyper-V, üzembe helyezheti a 1-box AD RMS ISV környezetet, ha virtuális gépet épít az AD RMS 1-box VHD-vel. A 1-box AD RMS ISV környezet éles üzem előtti használathoz konfigurált RMS-kiszolgálót nyújt, és tartalmazza az Active Directory Rights Management Services Client 2.1 alkalmazást. Az RMS-kiszolgáló és ügyfél beállításjegyzékbeli beállításai már konfigurálva vannak. Az alkalmazás teszteléséhez futtassa azt azon virtuális gépen, amelyen a 1-box környezet üzembe van helyezve.
-   **Az alkalmazást az éles üzem előtti használathoz konfigurált és a hálózat üzembe helyezett RMS-kiszolgálóval futtathatja**. Ebben az esetben az AD RMS Client 2.1 verziót is telepítenie kell a számítógépre, ahol az alkalmazást futtatja. Információ ennek elvégzéséről: [Ügyfél konfigurálása](how-to-configure-the-ad-rms-client-2-0.md). Az RMS-kiszolgálók üzembe helyezéséről és az éles üzem előtti használathoz végzett konfigurálásáról további információkért lásd: [A kiszolgáló telepítése és konfigurálása](how-to-install-and-configure-an-rms-server.md).

## Kapcsolódó témakörök

* [Használati útmutató](how-to-use-msipc.md)
* [AD RMS SDK Webinar collateral letöltési oldal](https://connect.microsoft.com/site1170/Downloads/DownloadDetails.aspx?DownloadID=42440)
* [Ügyfél konfigurálása](how-to-configure-the-ad-rms-client-2-0.md)
* [Az SDK telepítése](create-your-first-rights-aware-application.md)
* [A kiszolgáló telepítése és konfigurálása](how-to-install-and-configure-an-rms-server.md)
* [A tanúsítványláncok megértése](understanding-certificate-chains.md)
 

 





<!--HONumber=Apr16_HO4-->


