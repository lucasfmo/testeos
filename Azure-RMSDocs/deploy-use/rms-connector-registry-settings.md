---
title: "Az RMS-összekötő beállításjegyzékbeli beállításai | Azure RMS"
description: "Információ a RMS-összekötőt használó kiszolgálók beállításjegyzék-beállításairól. A beállítások konfigurálásának javasolt módja a Microsoft RMS-összekötő kiszolgálókonfiguráló eszközének használata."
author: cabailey
manager: mbaldwin
ms.date: 08/25/2016
ms.topic: article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: ed3e9a3d-0f7c-4abc-9d0b-aa3b18403d39
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ad32910b482ca9d92b4ac8f3f123eda195db29cd
ms.openlocfilehash: 5ff109543685049be5e89a12ea037de941736547


---


# A Rights Management-összekötő beállításjegyzékbeli beállításai

>*A következőkre vonatkozik: Azure Rights Management, Office 365*


Az alábbi szakaszokban található táblázatokat csak akkor használja, ha az Exchange-et, SharePointot vagy Windows Servert futtató kiszolgálókhoz manuálisan szeretne olyan beállításjegyzék-beállításokat hozzáadni, illetve ellenőrizni, amelyek az [RMS-összekötő](deploy-rms-connector.md) használatára konfigurálják a kiszolgálókat. A kiszolgálók konfigurálásának javasolt módja a Microsoft RMS-összekötő kiszolgálókonfiguráló eszközének használata.

Utasítások a beállítások használatához:

-   A *MicrosoftRMSURL* a szervezethez tartozó Microsoft RMS szolgáltatás URL-címe. Az érték kereséséhez tegye a következőket:

    1.  Futtassa az Azure RMS [Get-AadrmConfiguration](http://msdn.microsoft.com/library/windowsazure/dn629410.aspx) parancsmagját. Ha még nem telepítette az Azure RMS-hez készült Windows PowerShell-modult, tekintse meg az [Installing Windows PowerShell for Azure Rights Management](install-powershell.md) (Az Azure Rights Managementhez készült Windows PowerShell telepítése) című témakört.

    2.  A kimenetben azonosítsa a **LicensingIntranetDistributionPointUrl** értéket.

        Például: **LicensingIntranetDistributionPointUrl   : https://5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com/_wmcs/licensing**

    3.  Az értékben távolítsa el a **/_wmcs/licensing** részt a karakterláncból. A fennmaradó karakterlánc a Microsoft RMS URL-címe. A példánkban a Microsoft RMS URL-címe az alábbi érték lenne:

        **https://5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com**

-   Az *összekötőFQDN* karaktersor a terheléselosztó név, amelyet a DNS-ben megadott az összekötőnek. Például: **rmsconnector.contoso.com**.

-   Az összekötő URL-címéhez HTTPS protokollt használjon, ha az összekötő és a helyszíni kiszolgálók közti kommunikációhoz HTTPS protokollt konfigurált. További információkat a fő útmutató [Az RMS-összekötő konfigurálása HTTPS használatára](install-configure-rms-connector.md#configuring-the-rms-connector-to-use-https) című szakaszában találhat. A Microsoft RMS URL-címek mindig HTTPS protokollt használnak.


## Az Exchange 2016 vagy az Exchange 2013 beállításjegyzék-beállításai

**Beállításjegyzékbeli elérési út:** HKEY_LOCAL_MACHINE\Software\Microsoft\MSDRM\ServiceLocation\Activation

**Típus:** REG_SZ

**Érték:** Default

**Adatok:** https://*MicrosoftRMSURL*/_wmcs/certification

---

**Beállításjegyzékbeli elérési út:** HKEY_LOCAL_MACHINE\Software\Microsoft\MSDRM\ServiceLocation\EnterprisePublishing

**Típus:** REG_SZ

**Érték:** Default

**Adatok:** https://*MicrosoftRMSURL*/_wmcs/Licensing

---

**Beállításjegyzékbeli elérési út:** HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ExchangeServer\v15\IRM\CertificationServerRedirection

**Típus:** REG_SZ

**Érték:** https://*MicrosoftRMSURL*


**Adatok:**A következők egyike, attól függően, hogy az Exchange-kiszolgáló és az RMS-összekötő között HTTP vagy HTTPS protokollt használ:

- http://*összekötőFQDN*

- https://*összekötőFQDN*

---

**Beállításjegyzékbeli elérési út:** HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ExchangeServer\v15\IRM\LicenseServerRedirection

**Típus:** REG_SZ

**Érték:** https://*MicrosoftRMSURL*


**Adatok:**A következők egyike, attól függően, hogy az Exchange-kiszolgáló és az RMS-összekötő között HTTP vagy HTTPS protokollt használ:

- http://*összekötőFQDN*

- https://*összekötőFQDN*


## Az Exchange 2010 beállításjegyzék-beállításai

**Beállításjegyzékbeli elérési út:** HKEY_LOCAL_MACHINE\Software\Microsoft\MSDRM\ServiceLocation\Activation

**Típus:** REG_SZ

**Érték:** Default

**Adatok:** https://*MicrosoftRMSURL*/_wmcs/certification

---

**Beállításjegyzékbeli elérési út:** HKEY_LOCAL_MACHINE\Software\Microsoft\MSDRM\ServiceLocation\EnterprisePublishing

**Típus:** REG_SZ

**Érték:** Default

**Adatok:** https://*MicrosoftRMSURL*/_wmcs/Licensing

---

**Beállításjegyzékbeli elérési út:** HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ExchangeServer\v14\IRM\CertificationServerRedirection

**Típus:** REG_SZ

**Érték:** https://*MicrosoftRMSURL*

**Adatok:**A következők egyike, attól függően, hogy az Exchange-kiszolgáló és az RMS-összekötő között HTTP vagy HTTPS protokollt használ:

- http://*összekötőFQDN*

- https://*összekötőFQDN*

---

**Beállításjegyzékbeli elérési út:** HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ExchangeServer\v14\IRM\LicenseServerRedirection

**Típus:** REG_SZ

**Érték:** https://*MicrosoftRMSURL*

**Adatok:**A következők egyike, attól függően, hogy az Exchange-kiszolgáló és az RMS-összekötő között HTTP vagy HTTPS protokollt használ:

- http://*összekötőFQDN*

- https://*összekötőFQDN*


## A SharePoint 2016 vagy a SharePoint 2013 beállításjegyzék-beállításai

**Beállításjegyzékbeli elérési út:** HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\ServiceLocation\LicensingRedirection

**Típus:** REG_SZ

**Érték:** https://*MicrosoftRMSURL*/_wmcs/licensing


**Adatok:**A következők egyike, attól függően, hogy az SharePoint-kiszolgáló és az RMS-összekötő között HTTP vagy HTTPS protokollt használ:

- http://*összekötőFQDN*/_wmcs/licensing

- https://*összekötőFQDN*/_wmcs/licensing

---

**Beállításjegyzékbeli elérési út:** HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\ServiceLocation\EnterpriseCertification

**Típus:** REG_SZ

**Érték:** Default

**Adatok:**A következők egyike, attól függően, hogy az SharePoint-kiszolgáló és az RMS-összekötő között HTTP vagy HTTPS protokollt használ:

- http://*összekötőFQDN*/_wmcs/certification

- https://*összekötőFQDN*/_wmcs/certification

---

**Beállításjegyzékbeli elérési út:** HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\ServiceLocation\EnterprisePublishing

**Típus:** REG_SZ

**Érték:** Default


**Adatok:**A következők egyike, attól függően, hogy az SharePoint-kiszolgáló és az RMS-összekötő között HTTP vagy HTTPS protokollt használ:

- http://*összekötőFQDN*/_wmcs/licensing

- https://*összekötőFQDN*/_wmcs/licensing




## A fájlkiszolgáló és Fájlbesorolási infrastruktúra beállításjegyzék-beállításai

**Beállításjegyzékbeli elérési út:** HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSDRM\ServiceLocation\EnterprisePublishing

**Típus:** REG_SZ

**Érték:** Default

**Adatok:** https://*összekötőFQDN*/_wmcs/licensing

---

**Beállításjegyzékbeli elérési út:** HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSDRM\ServiceLocation\Activation

**Típus:** REG_SZ

**Érték:** Default

**Adatok:** https://*összekötőFQDN*/_wmcs/certification


Vissza a [Deploying the Azure Rights Management connector](deploy-rms-connector.md) (Az Azure Rights Management-összekötő üzembe helyezése) című témakörhöz


<!--HONumber=Aug16_HO4-->

