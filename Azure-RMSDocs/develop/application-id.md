---
# required metadata

title: "How to&#58; Get an Azure Application ID (Útmutató: Azure alkalmazásazonosító beszerzése) | Azure RMS"
description: Ahhoz, hogy RMS-kompatibilis alkalmazásokat hozhasson létre a Microsoft Rights Management SDK 4.2 segítségével, szerződést kell kötnie az RMS csapatával.
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 0fe9dc-bc91-4018-b28d-2db293a3eaa2
# optional metadata

#ROBOTS:
audience: developer
#ms.devlang:
ms.reviewer: shubhamp
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Útmutató: Azure alkalmazásazonosító beszerzése

Ahhoz, hogy RMS-kompatibilis alkalmazásokat hozhasson létre a Microsoft Rights Management SDK 4.2 segítségével, szerződést kell kötnie az RMS csapatával.

## Áttekintés

Ahhoz, hogy RMS-kompatibilis alkalmazásokat hozhasson létre és tehessen közzé az MS RMS SDK 4.2 segítségével, szolgáltatáshasználati szerződést is kell kötnie az RMS csapatával. Ez a szerződés – vagyis a Rights Management License Agreement (Rights Management Licencszerződés, RMLA) – útmutatóként szolgál a tartalomvédelmi szerződés betartásához, amelyet a felhasználó és/vagy a tartalom tulajdonosa nevében fog megvalósítani alkalmazása viselkedése (az üzleti szabályoknak való megfelelése) által. Egy RMS-kompatibilis alkalmazás létrehozójaként az RMS csapattal kötött szerződést az „Azure alkalmazásazonosító” léte érvényesíti, amely jelképezi ezt a szerződést, és lehetővé teszi az alkalmazás számára, hogy csatlakozzon az Azure AD hitelesítési rendszeréhez.

## Folyamat

Kövesse az alábbi lépéseket az alkalmazásazonosító létrehozásához és az RMS csapattal kötött használati szerződés aláírásához.

-   Kövesse a [How to create an App ID on Azure (Alkalmazásazonosító létrehozása az Azure rendszeren)](https://msdn.microsoft.com/en-us/library/azure/dn132599.aspx) témakörben található útmutatót az alkalmazásaazonosító létrehozásához.
-   Az RMLA folyamatának elindításához írjon üzenetet az RMS csapatának, és küldje el alkalmazásának azonosítóját („App ID”) az <askipteam@microsoft.com> e-mail-címre.
-   Írja alá az RMLA szerződést, és juttassa el az RMS csapat részére.
-   Most, hogy már rendelkezik aláírt RMLA szerződéssel, a hitelesítési könyvtár hívásakor adja át az alkalmazásazonosítót a *clientID* paraméterben.

    A következő egy példa hitelesítési hívás az [iOS/OS X-kódpéldák](ios-os-x-code-examples.md) témakörben.


    // Token lekérése az ADAL használatával
        [context acquireTokenWithResource:authenticationParameters.resource
                                 clientId:appClientId
                              redirectUri:redirectURI
                                   userId:authenticationParameters.userId
                          completionBlock:^(ADAuthenticationResult *result)



**Megjegyzés** Ha aláírt RMLA szerződése nem jut el az RMS csapathoz 60 napon belül, az Azure hitelesítési rendszerrel való hitelesítés használata blokkolva lesz alkalmazása számára.

 

 

 


<!--HONumber=Apr16_HO4-->


