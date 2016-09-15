---
title: "Az alkalmazás tesztelése | Azure RMS"
description: "Útmutatás az alkalmazás tesztelésének előkészítéséhez."
keywords: 
author: bruceperlerms
manager: mbaldwin
ms.date: 08/24/2016
ms.topic: article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: E480D8D6-F070-43D1-B2B0-6921459C3437
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 024a29d7c7db2e4c0578a95c93e22f8e7a5b173e
ms.openlocfilehash: 9cc96c7f4d75969ec75b1372a4a49499709b0d32


---

# Az alkalmazás tesztelése

Ez a témakör az alkalmazás tesztelésének előkészítéséhez ad útmutatást.

## Utasítások

### 1. lépés: A tesztelés előkészítése

A tesztelést az Azure RMS szolgáltatással vagy egy Windows Serveren futó tartalomvédelmi kiszolgálóval is végezheti. Azt javasoljuk, hogy az Azure RMS szolgáltatással kezdje a tesztelést, majd (amennyiben az üzembe helyezés ezt megköveteli) ez után térjen át a tartalomvédelmi kiszolgálón való tesztelésre.

1. Az Azure RMS szolgáltatással való tesztelés leírását itt tekintheti meg: [Útmutató: az ADAL-hitelesítés használata](how-to-use-adal-authentication.md).
2. A tartalomvédelmi kiszolgálóval való tesztelés leírását itt tekintheti meg: [Útmutató: a tartalomvédelmi kiszolgáló telepítése és konfigurálása](how-to-install-and-configure-an-rms-server.md).
3. Az alábbiakban a fejlesztői futtatókörnyezet telepítésének leírását tekintheti meg.

   A tartalomvédelmi szolgáltatás ügyfélprogramja 2.1-es verziójának telepítve kell lennie azon a számítógépen, ahol tesztelni fogja az alkalmazását.
   - Ha az alkalmazást nem a fejlesztési számítógépen teszteli, az [RMS-ügyfélprogram letöltési oldaláról](http://www.microsoft.com/en-us/download/details.aspx?id=38396) telepítheti az adott számítógépen az ügyfélprogram 2.1-es verzióját.
   - Ha az alkalmazást a fejlesztési számítógépen teszteli, ahhoz telepítenie kell a Rights Management Services SDK 2.1-es verzióját. Az RMS-ügyfélprogram 2.1-es verziója ezzel beavatkozás nélkül települ.

    További információt az RMS SDK 2.1 telepítéséről [Az SDK telepítése](install-the-rms-sdk.md) című cikkben találhat.

## Megjegyzések

A témakörben található ismertetés nem teljes körű. Részletes információt az RMS-ügyfélprogram 2.1-es verziójának konfigurálásával kapcsolatban [Az RMS 2.1-s ügyfelének üzembe helyezésével kapcsolatos megjegyzések](https://technet.microsoft.com/en-us/library/jj159267(WS.10).aspx) című cikkben találhat.

### Kapcsolódó témakörök

* [Útmutató az RMS-kiszolgáló telepítéséhez és konfigurálásához](how-to-install-and-configure-an-rms-server.md)
* [Útmutató: az ADAL-hitelesítés használata](how-to-use-adal-authentication.md)
* [Az SDK telepítése](install-the-rms-sdk.md)
* [Az RMS-ügyfélprogram 2.1-es verziójának üzembe helyezésével kapcsolatos megjegyzések](https://technet.microsoft.com/en-us/library/jj159267(WS.10).aspx)
 

 



<!--HONumber=Aug16_HO4-->


