---
title: "Áttekintés – RMS SDK 4.2 | Azure RMS"
description: "Az AD RMS és az Azure RMS egy információvédelmi technológia, amely segítségével megakadályozhatja a digitális adatok jogosulatlan használatát."
keywords: 
author: bruceperlerms
manager: mbaldwin
ms.date: 07/11/2016
ms.topic: article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 8A13494E-C1D7-407D-BCD1-A406915EA578
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 5d2339ece646fc51410186d43facdea28ac8fdfe
ms.openlocfilehash: da491f008043b11a04cbfe48acb952e67ad86dda


---

# Áttekintés

A Microsoft Rights Management SDK 4.2 egy adatvédelmi technológia, amely több platformon is elérhető.  Olyan szoftverfejlesztői készletet (SDK) vagy keretrendszert biztosít, amely az ügyfélszámítógépeken és eszközökön segít megvédeni a tartalomvédelemmel kompatibilis alkalmazásokon keresztüláramló információk elérését és felhasználását. Az ezen platformokhoz készült SDK-k egyszerű API-t biztosítanak az alkalmazásfejlesztőknek a digitális tartalom védelméhez vagy használatához, a sablonok lekéréséhez, a házirendek kiszolgálóról való beszerzéséhez, valamint más, kapcsolódó tartalomvédelmi feladatokhoz.

További információért a jelenleg támogatott platformokkal kapcsolatban lásd a [Microsoft Rights Management SDK](active-directory-rights-management-services-multi-platform-thin-client-sdk-portal.md) fejlesztői dokumentációs portált.

Néhány elképzelhető forgatókönyv:

-   Egy jogi vállalat szeretné megakadályozni a bizalmas e-mail-üzenetek kinyomtatását vagy továbbítását mobileszközökön.
-   Egy CAD- és gyártószoftver fejlesztői szeretnék korlátozni a rajzok hozzáférését a kutatási részlegen belül egy kis csoport számára, de nem szeretnének jelszavakat használni.
-   Egy grafikus tervező mobilalkalmazás tulajdonosai egyetlen licencet szeretnének használni, amely lehetővé teszi a képek ingyenes megtekintését alacsony felbontásban, de díjkötelessé tenné a nagy felbontású verziókhoz való hozzáférést.
-   Egy online dokumentumkönyvtár tulajdonosai a felhasználó személyazonossága alapján szeretnék engedélyezni a dokumentumok megtekintését, nyomtatását és szerkesztését, ha a dokumentumokat letöltik egy mobileszközre.
-   Egy vállalat szeretne bizalmas alkalmazotti információkat közzétenni egy belső webhelyen, amely bizonyos felhasználókra korlátozza a megtekintési és szerkesztési jogosultságot.

Az MS RMS SD 4.2 letölthető, majd a licenc-megállapodás tudomásul vétele és elfogadása után ingyenesen terjeszthető a harmadik fél szoftverével, hogy az ügyfelek hozzáférhessenek a környezetében AD RMS kiszolgálók üzembe helyezésével és használatával, illetve az Azure RMS szolgáltatással védett tartalmakhoz. További információ: [Get started](get-started.md) (Első lépések).

## Az SDK fontos jellemzői


Az MS RMS SDK 4.2 az alábbi nagyszerű új szolgáltatásokat nyújtja:

-   **Újratervezett API** – Az MS RMS SDK 4.2 API a maximális egyszerűség érdekében újra lett tervezve. A fejlesztők egy egyszerű és átlátható titkosítási és visszafejtési API-felületet használhatnak, amely egységes RMS-működést biztosít kevesebb ráfordítás mellett.
-   **Hibrid AD RMS és Azure RMS támogatása** – Egyetlen tartalomvédelemmel kompatibilis alkalmazás képes az AD RMS kiszolgálóról (az AD RMS mobileszköz-bővítményével) és az Azure RMS szolgáltatásból származó tartalom használatára és védelmére. Az MS RMS SDK 4.2 átláthatóan azonosítja az informatikai rendszergazdák által konfigurálható végpontot.
-   **Saját hitelesítési tár használata** – Alkalmazásfejlesztőként eldöntheti, milyen hitelesítési tárat szeretne használni az MS RMS SDK 4.2-es verziójához. Akár az [Azure AD hitelesítési tárát](https://msdn.microsoft.com/library/jj573266.aspx), akár a szervezete egyéni tárát használja, az MS RMS SDK 4.2 elkülöníti a hitelesítési készletet, hogy Ön kiválaszthassa az igényeinek megfelelő tárat.
-   **Saját felhasználói felület használata** – Az MS RMS SDK 4.2 mostantól lehetővé teszi a saját testre szabott felhasználói felület implementálását. Legyen szó a tartalomvédelemről, a sablonok kiválasztásáról, vagy az engedélyek megjelenítéséről és módosításáról a védett tartalom felhasználása közben, az MS RMS SDK 4.2 nem kényszerít semmilyen beépített felhasználói felületet az alkalmazásaira. Ha viszont szeretné, használhatja a Microsoft RMS felhasználói felület könyvtárait az összes platformra a [GitHub-fiókunkban](https://github.com/AzureAD/).
-   **Hozzáférés offline a védett tartalmakhoz** – Az MS RMS SDK 4.2 lehetővé teszi a felhasználók számára a védett tartalomhoz még akkor is, amikor nincs internetkapcsolat. Az MS RMS SDK 4.2 biztonságosan gyorsítótárazza a védett tartalomra vonatkozó felhasználási házirendeket, hogy a felhasználók offline is hozzáférjenek az RMS által védett adatokhoz.

Az [Első lépések](get-started.md) útmutató segítségével belekezdhet védett információs eszközalkalmazás-projektjébe.

## Kapcsolódó témakörök

* [Microsoft Rights Management SDK](active-directory-rights-management-services-multi-platform-thin-client-sdk-portal.md)
* [Első lépések](get-started.md)
* [Azure AD Authentication Library](https://msdn.microsoft.com/en-us/library/jj573266.aspx)
* [GitHub-fiók](https://github.com/AzureAD/)
 

 






<!--HONumber=Aug16_HO4-->


