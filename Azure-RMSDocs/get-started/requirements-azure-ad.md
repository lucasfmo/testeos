---
title: "Azure RMS-követelmények&#58; Azure AD-címtár | Azure RMS"
description: 
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: get-started-article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: ed25aa83-e272-437b-b445-3f01e985860c
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ed50d87138c428fadfd22cd5b3ef3c7f7e421848
ms.openlocfilehash: 75b2414cc360704deb6107d6c0038f5b0bf7fa70


---

# Azure RMS-követelmények: Azure AD-címtár

*A következőkre vonatkozik: Azure Rights Management, Office 365*


Az Azure Rights Management (Azure RMS) használatához Azure AD-címtárral kell rendelkeznie. A címtárhoz tartozó szervezeti fiók segítségével léphet be a klasszikus Azure portálra, ahol többek között konfigurálhatja és kezelheti a tartalomvédelmi sablonokat.

Ha a szervezete még nem rendelkezik Azure-előfizetéssel, akkor igényelhet egy ingyenes próbaverziót: Keresse fel az [Ismerkedés az Azure szolgáltatással](https://account.windowsazure.com/organization) oldalt, és kövesse az utasításokat.

További információkért lásd az Azure Active Directory dokumentációjának következő forrásanyagait:

-   [Mi az az Azure AD-címtár?](/active-directory/active-directory-whatis)

-   [How Azure subscriptions are associated with Active Directory? (Hogyan kapcsolódnak az Azure-előfizetések az Azure Active Directory-hoz?)](/active-directory/active-directory-how-subscriptions-associated-directory)

Ha szeretné integrálni Azure AD-címtárát a helyszíni AD-erdőkkel, tekintse meg az [Integrating your on-premises identities with Azure Active Directory](/active-directory/active-directory-aadconnect) (Helyszíni identitások integrálása az Azure Active Directoryval) című szakaszt.

> [!NOTE]
> Ha olyan mobileszközökkel vagy Mac számítógépekkel rendelkezik, amelyek az AD FS vagy egy annak megfelelő hitelesítési szolgáltató használatával végeznek helyszíni hitelesítést:
> 
> -   Az AD FS-t legalább a **Windows Server 2012 R2** kiszolgálóverzióval vagy az OAuth 2.0 protokollt támogató egyéb hitelesítési szolgáltatóval kell használnia.

## Többtényezős hitelesítés (MFA) és az Azure RMS
A többtényezős hitelesítés (MFA) Azure RMS szolgáltatással való használatához az alábbiak legalább egyike szükséges:

-   Office 2013 (minimális verzió):

    -   Ha az Office 2013 szoftverrel rendelkezik, telepítenie kell az [Office 2013 2015. június 9-i frissítését (KB3054853)](https://support.microsoft.com/kb/3054853) is. További információkat arról, hogy miként biztosítható a modern hitelesítéssel az Active Directory Authentication Library-(ADAL-) alapú bejelentkezés az Office 2013-ba, az Office blog [Office 2013 modern authentication public preview announced](https://blogs.office.com/2015/03/23/office-2013-modern-authentication-public-preview-announced/) (Az Office 2013 modern hitelesítés nyilvános előzetes verziójának bejelentése) című bejegyzésben talál.

-   A Windows Microsoft Rights Management megosztóalkalmazás:

    -   Legalább az 1.0.1908.0 verziónak kell telepítve lennie, amit a Vezérlőpult Programok és szolgáltatások menüjében ellenőrizhet. További információk a megosztóalkalmazásról: [Windows Rights Management megosztóalkalmazás](../rms-client/sharing-app-windows.md).

-   Rights Management megosztóalkalmazás mobileszközökre és Mac számítógépekre:

    -   Győződjön meg arról, hogy a legfrissebb verzió van telepítve. Az RMS-megosztóalkalmazás 2015. szeptemberi kiadása MFA-támogatással bővült.

Ezt követően konfigurálja MFA-megoldását:

-   Microsoft által felügyelt bérlők esetén (Azure Active Directory vagy Office 365 szolgáltatással rendelkezik):

    -   Konfigurálja az Azure MFA-t a többtényezős hitelesítés kényszerítéséhez a felhasználók számára. Útmutatásért tekintse meg a többtényezős hitelesítésről szóló dokumentáció [Getting started with Azure Multi-Factor Authentication in the cloud](/multi-factor-authentication/multi-factor-authentication-get-started-cloud) (Azure többtényezős hitelestés a felhőben) című részét.

        További információ az Azure többtényezős hitelesítésről: [What is Azure Multi-Factor Authentication?](/multi-factor-authentication/multi-factor-authentication) (Mi az az Azure többtényezős hitelesítés?)

-   Összevont bérlők esetén (helyszíni összevonási kiszolgálókat üzemeltet):

    -   Konfigurálja az összevonási kiszolgálóit az Azure Active Directory vagy az Office 365 szolgáltatáshoz. Ha például AD FS-t használ, tekintse meg a [További hitelesítési módszerek konfigurálása az AD FS szolgáltatásokhoz](https://technet.microsoft.com/library/dn758113.aspx) című anyagot a TechNet webhelyén.

        További információkért erről a forgatókönyvről lásd: az Office blog [The Works with Office 365 – Identity program now streamlined](https://blogs.office.com/2014/01/30/the-works-with-office-365-identity-program-now-streamlined/) (Mindent a Office 365-ről – Az identitás program mostantól egyszerűbb) című bejegyzése.

## További lépések
Az egyéb követelményeket [Az Azure Rights Management követelményei](requirements-azure-rms.md) című témakörben tekintheti meg.




<!--HONumber=Jun16_HO4-->


