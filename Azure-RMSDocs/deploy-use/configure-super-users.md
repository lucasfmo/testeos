---
title: "Felügyelők konfigurálása az Azure Rights Management és a felderítési szolgáltatások vagy adat-helyreállítás számára | Azure RMS"
description: "A Microsoft Azure RMS felügyelői funkciója biztosítja, hogy a jogosult személyek és szolgáltatások mindig hozzáférjenek és vizsgálhassák az Azure RMS-védelemmel ellátott szervezeti adatokat. Ezenkívül, szükség esetén eltávolítja a védelmet, vagy módosítja az előzőleg alkalmazott védelmet. A felügyelők teljes tulajdonosi jogokat kapnak minden, a szervezet RMS-bérlője által biztosított összes használati licenchez. Ez a képesség más néven az „adatok indoklása”, és lényeges elem a szervezet adatai feletti irányítás megőrzéséhez."
author: cabailey
manager: mbaldwin
ms.date: 08/24/2016
ms.topic: article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: acb4c00b-d3a9-4d74-94fe-91eeb481f7e3
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 024a29d7c7db2e4c0578a95c93e22f8e7a5b173e
ms.openlocfilehash: 32da3f280b7dc8fa0655ae65d904864d80b9a035


---

# Felügyelők konfigurálása az Azure Rights Management és a felderítési szolgáltatások vagy adat-helyreállítás számára

>*A következőkre vonatkozik: Azure Rights Management, Office 365*

A Microsoft [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] (Azure RMS) felügyelői funkciója biztosítja, hogy a jogosult személyek és szolgáltatások mindig hozzáférjenek és vizsgálhassák az Azure RMS-védelemmel ellátott szervezeti adatokat. Ezenkívül, szükség esetén eltávolítja a védelmet, vagy módosítja az előzőleg alkalmazott védelmet. A felügyelők teljes tulajdonosi jogokat kapnak minden, a szervezet RMS-bérlője által biztosított összes használati licenchez. Ez a képesség más néven az „adatok indoklása”, és lényeges elem a szervezet adatai feletti irányítás megőrzéséhez. Az alábbi példahelyzetekben használhatja ezt a funkciót:

-   Egy alkalmazott kilép a szervezetből, és az általa védelemmel ellátott fájlt szeretné olvasni.

-   Egy rendszergazdának el kell távolítania a fájlokra konfigurált, aktuális védelmi házirendet, és új védelmi házirendet kell alkalmaznia.

-   A keresési műveletekhez az Exchange Servernek indexelnie kell a postafiókokat.

-   Rendelkezik olyan adatveszteség-megelőzési (DLP) informatikai megoldásokkal, tartalomtitkosító átjárókkal (CEG), valamint kártevőirtó termékekkel, amelyeknek a korábban már védelemmel ellátott fájlokat kell megvizsgálniuk.

-   A fájlok titkosításának tömeges feloldása szükséges naplózási, jogi vagy egyéb megfelelőségi okokból.

Alapértelmezés szerint a felügyelői funkció nincs engedélyezve, és nincsenek felhasználók sem hozzárendelve ehhez a szerepkörhöz. A Rights Management-összekötő Exchange-re történő konfigurálása esetén automatikusan engedélyezve van, az Exchange Online-t, a SharePoint Online-t vagy a SharePoint Servert futtató, szabványos szolgáltatások esetében pedig nem szükséges.

Ha manuálisan kívánja engedélyezni a felügyelői funkciót, használja az [Enable-AadrmSuperUserFeature](https://msdn.microsoft.com/library/azure/dn629400.aspx) Windows PowerShell-parancsmagot, majd szükség szerint rendeljen hozzá felhasználókat (vagy szolgáltatásfiókokat) az [Add-AadrmSuperUser](https://msdn.microsoft.com/library/azure/dn629411.aspx) vagy a [Set-AadrmSuperUserGroup](https://msdn.microsoft.com/library/azure/mt653943.aspx) parancsmaggal, végül pedig igény szerint adjon hozzá felhasználókat (vagy további csoportokat) ehhez a csoporthoz. 

> [!NOTE]
> Ha még nem telepítette az [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)]-hez készült Windows PowerShell-modult, tekintse meg [Az Azure Rights Managementhez készült Windows PowerShell telepítése](install-powershell.md) című témakört.

Ajánlott biztonsági eljárások a felügyelői funkcióhoz:

-   Korlátozza és kövesse nyomon azon rendszergazdák tevékenységét, akik globális rendszergazdaként vannak hozzárendelve az Office 365- vagy Azure RMS-bérlőhöz, illetve a GlobalAdministrator-szerepkörhöz vannak hozzárendelve az [Add-AadrmRoleBasedAdministrator](https://msdn.microsoft.com/library/azure/dn629417.aspx) parancsmag használatával. E felhasználók engedélyezhetik a felügyelői funkciót, valamint felügyelőként vehetnek fel felhasználókat (és saját magukat), illetve lehetőségük van valamennyi védett szervezeti fájl titkosításának feloldására.

-   A felügyelőként felvett felhasználók és szolgáltatásfiókok megtekintéséhez használja a [Get-AadrmSuperUser parancsmagot](https://msdn.microsoft.com/library/azure/dn629408.aspx). A felügyelői csoportok konfigurált állapotának megtekintéséhez használja a [Get-AadrmSuperUser](https://msdn.microsoft.com/library/azure/mt653942.aspx) parancsmagot, a szabványos felhasználó-felügyeleti eszközökkel pedig ellenőrizhető, hogy mely felhasználók tagjai ennek a csoportnak. Az összes többi felügyeleti művelethez hasonlóan a felügyelői funkció engedélyezése vagy letiltása, illetve a felügyelők hozzáadása vagy eltávolítása a [Get-AadrmAdminLog](https://msdn.microsoft.com/library/azure/dn629430.aspx) parancs használatával naplózható. A felügyelők által végrehajtott fájltitkosítás-feloldások naplózása a [használatnaplózás](log-analyze-usage.md) segítségével történik.

-   Ha mindennapi használatra nincs szüksége a felügyelői funkcióra, csak szükség esetén engedélyezze, majd a [Disable-AadrmSuperUserFeature](https://msdn.microsoft.com/library/azure/dn629428.aspx) parancsmag segítségével újra tiltsa le azt.

Az alábbi naplókivonat a Get-AadrmAdminLog parancsmag használatára mutat példabejegyzéseket. E példában a Contoso Ltd rendszergazdája meggyőződik róla, hogy a felügyelői funkció le van tiltva, felveszi Richard Simone-t felügyelőként, majd ellenőrzi, hogy Richard az egyetlen felügyelő, aki az Azure RMS konfigurálása során meg lett adva, végül pedig engedélyezi a felügyelői funkciót, így Richard mostantól feloldhatja azon fájlok titkosítását, amelyeket egy, a vállalattól most távozott alkalmazott látott el védelemmel.

`2015-08-01T18:58:20    admin@contoso.com   GetSuperUserFeatureState    Passed  Disabled`

`2015-08-01T18:59:44    admin@contoso.com   AddSuperUser -id rsimone@contoso.com    Passed  True`

`2015-08-01T19:00:51    admin@contoso.com   GetSuperUser    Passed  rsimone@contoso.com`

`2015-08-01T19:01:45    admin@contoso.com   SetSuperUserFeatureState -state Enabled Passed  True`

## Felügyelői parancsprogram-beállítások
Gyakori eset, hogy az [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] platformhoz felügyelőként hozzárendelt felhasználónak több helyen, több fájlról kell eltávolítania a védelmet. Bár ez megoldható manuálisan is, hatékonyabb (és gyakran megbízhatóbb) módszer erre egy parancsprogram írása. Ehhez [töltse le az RMS Protection eszközt](http://www.microsoft.com/en-us/download/details.aspx?id=47256). Ezt követően szükség szerint használja az [Unprotect-RMSFile](https://msdn.microsoft.com/library/azure/mt433200.aspx) és a [Protect-RMSFile](https://msdn.microsoft.com/library/azure/mt433201.aspx) parancsmagot.

További információk ezekről a parancsmagokról: [RMS Protection parancsmagok](https://msdn.microsoft.com/library/azure/mt433195.aspx).

> [!NOTE]
> Az RMS Protection eszköz részét képező RMS Protection PowerShell-modul eltérő, illetve kiegészíti a [Azure Rights Managementhez készült fő Windows PowerShell-modult](administer-powershell.md). Az RMS Protection modul az Azure RMS-t és az AD RMS-t is támogatja.





<!--HONumber=Aug16_HO4-->


