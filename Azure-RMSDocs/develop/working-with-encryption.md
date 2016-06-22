---
# required metadata

title:
How-to: work with encryption settings | Azure RMS
description: This article orients you to our encryption packages
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: B1D2C227-F43D-4B18-9956-767B35145792
# optional metadata

#ROBOTS:
audience: developer
#ms.devlang:
ms.reviewer: shubhamp
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Útmutató: A titkosítási beállítások kezelése

Ez a témakör tájékoztatást nyújt a titkosítási csomagok használatáról, és közöl néhány a használatukat bemutató kódrészletet.

## Az új alapértelmezett titkosítás, az AES 256 támogatása

Az *AES 256*-alapú titkosítás használatához nincs szükség további kódra (mostantól ez az alapértelmezett titkosítás), feltéve, hogy az RMS SDK 2.1 2015. márciusi vagy újabb frissítését használja. Javasoljuk, hogy végezze el alkalmazásainak e kiadással történő frissítését az *AES 256* által biztosított további biztonsági előnyök kihasználásához.

> [!IMPORTANT]
> Az *AES 256*-védelemmel ellátott fájlok használata a [2014 októberi kiadás](release-notes-rtm.md) megjelenése óta támogatott. Ha 2014 októberénél korábbi SDK-verzióval készült alkalmazásokat futtat, e frissítés telepítését követően azok nem fognak működni. Győződjön meg arról, hogy az Ön által létrehozott alkalmazások ügyfelei vagy a frissített SDK-t használják, vagy készek azonnal az alkalmazás legfrissebb verziójára frissíteni.

 
## API-titkosítás támogatása

A [2015. márciusi frissítés](release-notes-rtm.md) kiadása óta az alábbi három jelölőt és az azokhoz kapcsolódó titkosítási csomagokat építettük be az API-ba:

-   IPC\_ENCRYPTION\_PACKAGE\_AES256\_CBC4K
-   IPC\_ENCRYPTION\_PACKAGE \_AES128\_CBC4K
-   IPC\_ENCRYPTION\_PACKAGE \_AES128\_ECB (más néven: elavult algoritmusok)

A titkosítási csomag jelölői (lásd: [**Preferred encryption**](/rights-management/sdk/2.1/api/win/constants#msipc_preferred_encryption) (Előnyben részesített titkosítás)) az új, **IPC\_LI\_PREFERRED\_ENCRYPTION\_PACKAGE** licenctulajdonság-jelölővel együtt használhatók.

Az alábbiakban az új licenctulajdonság használatát bemutató néhány egyszerű kódrészlet látható.

## Elavult algoritmusok

Az **IPC\_LI\_DEPRECATED\_ENCRYPTION\_ALGORITHMS** jelzőt a már nem tesszük közzé az API felületen. Ez azt jelenti, hogy a jövőben az erre a jelölőre hivatkozó alkalmazások lefordítása nem fog megtörténni. Az azt használó, már létrehozott alkalmazások azonban továbbra is működnek majd, mivel a jelölőt rejtve megőrizzük az API-kódban.

A régi, elavult titkosítási algoritmus jelzőjének előnyei továbbra is kihasználhatóak egy jelző egyszerű módosításával. Tekintse meg példaként az alábbi kódrészleteket.

## Fájlok AES 256 CBC4K-védelemmel történő ellátása

Nincs szükség a kód módosítására, mivel az *AES 256* CBC4K az alapértelmezett titkosítás.

    C++

    hr = IpcCreateLicenseFromTemplateID(pcTil-&gt;aTi[0].wszID,
                                    0,
                                    NULL,
                                    &amp;pLicenseHandle);


## Fájlok AES-128 CBC4K-védelemmel történő ellátása

    C++

    hr = IpcCreateLicenseFromTemplateID(pcTil-&gt;aTi[0].wszID,
                                    0,
                                    NULL,
                                    &amp;pLicenseHandle);

    DWORD dwEncryptionMode = IPC_ENCRYPTION_PACKAGE_AES128_CBC4K;

    hr = IpcSetLicenseProperty(pLicenseHandle,
                           false,
                           IPC_LI_PREFERRED_ENCRYPTION_PACKAGE,
                           &amp;dwEncryptionMode);


## Fájlok AES-128 ECB-védelemmel történő ellátása (elavult algoritmusok)

Ez a példa az *elavult algoritmusok* támogatásának új módját is bemutatja.

    C++
    
    hr = IpcCreateLicenseFromTemplateID(pcTil-&gt;aTi[0].wszID,
                                    0,
                                    NULL,
                                    &amp;pLicenseHandle);

    DWORD dwEncryptionMode = IPC_ENCRYPTION_PACKAGE_AES128_ECB;

    hr = IpcSetLicenseProperty(pLicenseHandle,
                           false,
                           IPC_LI_PREFERRED_ENCRYPTION_PACKAGE,
                           &amp;dwEncryptionMode);

 

 


<!--HONumber=Jun16_HO2-->


