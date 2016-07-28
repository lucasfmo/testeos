---
title: "Áttekintés – RMS SDK 2.1 | Azure RMS"
description: "A Rights Management Services (RMS) egy információvédelmi technológia, amely segítségével megakadályozhatja a digitális adatok jogosulatlan használatát."
keywords: 
author: bruceperlerms
manager: mbaldwin
ms.date: 07/11/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: B546B6C1-ADC1-4EBD-95E2-B4A74E4E980B
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 5afdf526fe9f8486c6a778eebf10899e0bd9f839
ms.openlocfilehash: 53571aff357bbc0cdcb44ce9b403c68719abbaff


---

# Áttekintés

A Rights Management Services SDK 2.1 egy információvédelmi technológia, amelynek segítségével megakadályozható a digitális adatok jogosulatlan használata. A tartalomvédelemmel kompatibilis alkalmazás segítségével a tartalmak tulajdonosai meghatározhatják, ki nyithatja meg, szerkesztheti, nyomtathatja ki, továbbíthatja a tartalmaikat, vagy végezhet velük bármilyen más műveletet.

Az AD RMS [kiszolgáló-](ad-rms-server.md) és [ügyféloldali](ad-rms-client.md) összetevőkből áll. A kiszolgáló Azure vagy Windows Servert futtat, és több webszolgáltatásból áll.

Az [ügyféloldali](ad-rms-client.md) összetevők mind az ügyfél, mind a kiszolgáló operációs rendszerén futtathatók, és olyan funkciókat tartalmaznak, amelyek lehetővé teszik az alkalmazások számára a tartalmak titkosítását és visszafejtését, sablonok és a visszavont tanúsítványok listáinak lekérését, licencek és tanúsítványok beszerzését a kiszolgálóról, valamint az egyéb kapcsolódó tartalomvédelmi feladatok elvégzését.

További információ: [Application types](application-types.md) (Alkalmazástípusok).

Az alábbiakban néhány olyan forgatókönyv látható, amelyben a Rights Management Services SDK 2.1-re épülő alkalmazások alkalmazhatók.

-   Egy jogi vállalat szeretné megakadályozni a bizalmas e-mail-üzenetek kinyomtatását vagy továbbítását.
-   Egy CAD- és gyártószoftver fejlesztői szeretnék korlátozni a rajzok hozzáférését a kutatási részlegen belül egy kis csoport számára, de nem szeretnének jelszavakat használni.
-   Egy grafikus tervező webhely tulajdonosai egyetlen licencet szeretnének használni, amely lehetővé teszi a képek ingyenes megtekintését alacsony felbontásban, de díjkötelessé tenné a nagy felbontású verziókhoz való hozzáférést.
-   Egy online dokumentumkönyvtár tulajdonosai a felhasználó személyazonossága alapján szeretnék engedélyezni a dokumentumok megtekintését, nyomtatását és szerkesztését.
-   Egy vállalat szeretne bizalmas alkalmazotti információkat közzétenni egy belső webhelyen, amely bizonyos felhasználókra korlátozza a megtekintési és szerkesztési jogosultságot.

Az AD RMS-kiszolgálóról, az AD RMS-ügyfélről és azok funkcióiról további információt a TechNet [az AD RMS informatikai szakembereknek szóló dokumentációjában](https://TechNet.Microsoft.Com/library/cc771234.aspx) találhat.

A szakasz többi témaköre az RMS-architektúrával és annak üzembe helyezésével foglalkozik.

## A szakasz tartalma

| Témakör | Leírás |
|-------|-------------|
|[Ügyfél](ad-rms-client.md) |Ez a témakör a Rights Management Services-ügyfél 2.1-es verziójának célját és funkcióját ismerteti |
|[Kiszolgáló](ad-rms-server.md) | Ez a témakör az RMS-kiszolgáló célját és funkcióit ismerteti az Azure-ra és a Windows Serverre vonatkozóan.|


## Kapcsolódó témakörök

* [Az RMS-sel kapcsolatos fogalmak](application-types.md)
* [Első lépések](getting-started-with-ad-rms-2-0.md)
* [Az AD RMS informatikai szakembereknek szóló dokumentációja](https://TechNet.Microsoft.Com/en-us/library/cc771234.aspx)
 

 



<!--HONumber=Jul16_HO3-->


