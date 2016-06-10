---
# required metadata

title: Áttekintés | Azure RMS
description: A Rights Management Services (RMS) egy információvédelmi technológia, amely segítségével megakadályozhatja a digitális adatok jogosulatlan használatát.
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: B546B6C1-ADC1-4EBD-95E2-B4A74E4E980B
# optional metadata

#ROBOTS:
audience: developer
#ms.devlang:
ms.reviewer: shubhamp
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---
** Ez az SDK-tartalom nem naprakész. Ideiglenesen arra kérjük, keresse fel az MSDN webhelyén található dokumentáció [aktuális verzióját](https://msdn.microsoft.com/library/windows/desktop/hh535290(v=vs.85).aspx). **
# Áttekintés

A Rights Management Services (RMS) egy információvédelmi technológia, amely segítségével megakadályozhatja a digitális adatok jogosulatlan használatát. A tartalomvédelemmel kompatibilis alkalmazása segítségével a tartalmak tulajdonosai meghatározhatják, ki nyithatja meg, szerkesztheti, nyomtathatja ki, továbbíthatja a tartalmaikat, vagy végezhet velük bármilyen más műveletet.

## Áttekintés

Az AD RMS [kiszolgáló-](ad-rms-server.md) és [ügyféloldali](ad-rms-client.md) összetevőkből áll. A kiszolgálóoldali összetevők olyan webes szolgáltatásokat foglalnak magukban, amelyek egy Windows Serveren, például a Windows Server 2008 R2-n, vagy a felhőben, az Azure RMS webes szolgáltatásain futnak. Az ügyféloldali összetevők mind az ügyfél, mind a kiszolgáló operációs rendszerén futtathatók, és olyan funkciókat tartalmaznak, amelyek lehetővé teszik az alkalmazások számára a tartalmak titkosítását és visszafejtését, sablonok és a visszavont tanúsítványok listáinak lekérését, licencek és tanúsítványok beszerzését a kiszolgálóról, valamint az egyéb kapcsolódó tartalomvédelmi feladatok elvégzését.

További információ: [Application types](application-types.md) (Alkalmazástípusok).

Az alábbiakban néhány olyan forgatókönyv látható, amelyben a Rights Management Services SDK 2.1-re épülő alkalmazások alkalmazhatók.

-   Egy jogi vállalat szeretné megakadályozni a bizalmas e-mail-üzenetek kinyomtatását vagy továbbítását.
-   Egy CAD- és gyártószoftver fejlesztői szeretnék korlátozni a rajzok hozzáférését a kutatási részlegen belül egy kis csoport számára, de nem szeretnének jelszavakat használni.
-   Egy grafikus tervező webhely tulajdonosai egyetlen licencet szeretnének használni, amely lehetővé teszi a képek ingyenes megtekintését alacsony felbontásban, de díjkötelessé tenné a nagy felbontású verziókhoz való hozzáférést.
-   Egy online dokumentumkönyvtár tulajdonosai a felhasználó személyazonossága alapján szeretnék engedélyezni a dokumentumok megtekintését, nyomtatását és szerkesztését.
-   Egy vállalat szeretne bizalmas alkalmazotti információkat közzétenni egy belső webhelyen, amely bizonyos felhasználókra korlátozza a megtekintési és szerkesztési jogosultságot.

Az AD RMS-kiszolgálóval, az AD RMS-ügyféllel és azok funkcióival kapcsolatos további információért lásd [az AD RMS informatikai szakembereknek szóló dokumentációját](https://TechNet.Microsoft.Com/en-us/library/cc771234.aspx) a TechNeten.

Az első lépésekért lásd: [Getting started](getting-started-with-ad-rms-2-0.md) (Első lépések).

## Kapcsolódó témakörök

* [Az AD RMS-sel kapcsolatos fogalmak](application-types.md)
* [Az AD RMS és az AD RMS 2.1 közötti különbségek](differences-between-ad-rms-and-ad-rms-2-0.md)
* [Első lépések](getting-started-with-ad-rms-2-0.md)
* [Az AD RMS informatikai szakembereknek szóló dokumentációja](https://TechNet.Microsoft.Com/en-us/library/cc771234.aspx)
* [kiszolgáló](ad-rms-server.md)
* [ügyfél](ad-rms-client.md)
 

 





<!--HONumber=Jun16_HO1-->


