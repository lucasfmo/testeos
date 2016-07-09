---
title: "Áttelepítés AD RMS-ről Azure Rights Managementre – 2. fázis | Azure RMS"
description: 
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 06/23/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: e3fd9bd9-3638-444a-a773-e1d5101b1793
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: a9dc45fb5146b0a4d2f013bff9d090723ce95ee5
ms.openlocfilehash: 1016ecdd77e818840f2a2cfab8212e908291bb89


---
# 2. áttelepítési fázis: Ügyféloldali konfiguráció

*A következőkre vonatkozik: Active Directory Rights Management Services, Azure Rights Management*

Az alábbi, 2. fázisra vonatkozó információk segítséget nyújtanak az AD RMS-ről az Azure Rights Managementre (Azure RMS) való áttelepítésben. Ezek az eljárások megfelelnek az [Áttelepítés AD RMS-ről Azure Rights Managementre](migrate-from-ad-rms-to-azure-rms.md) 5. lépésének.


## 5. lépés. Ügyfelek újrakonfigurálása az Azure RMS használatára
Windows rendszerű ügyfelek:

1.  [Töltse le a következő áttelepítési parancsfájlokat](http://go.microsoft.com/fwlink/?LinkId=524619):

    -   CleanUpRMS_RUN_Elevated.cmd

    -   Redirect_OnPrem.cmd

    Ezek a parancsfájlok visszaállítják a Windows rendszerű számítógépek konfigurációját, így az AD RMS helyett az Azure RMS szolgáltatást fogják használni.

2.  Az átirányítási parancsfájl (Redirect_OnPrem.cmd) utasításait követve módosítsa a parancsfájlt úgy, hogy az új Azure RMS-bérlőjére mutasson.

    > [!IMPORTANT]
    > Az utasítások tartalmazzák az **adrms** és az **adrms.contoso.com** mintaként használt címeinek lecserélését a felhasználó saját AD RMS-kiszolgálóinak címeire. Ennek végrehajtása során ügyeljen arra, hogy ne legyenek további szóközök a címek előtt vagy után, mert az megszakítaná az áttelepítési parancsfájlt, és nagyon nehéz lenne azonosítani a probléma kiváltó okát. Egyes szerkesztőeszközök automatikusan szóközt helyeznek el a beillesztett szöveg után.

3. Ha a felhasználók Office 2016-tal rendelkeznek: a parancsfájlok még nincsenek frissítve, hogy alkalmasok legyenek az Office 2016 beállítására, így ha a felhasználók ezzel az Office-verzióval rendelkeznek, egyedileg kell frissítenie a parancsfájlokat:

    - A **CleanUpRMS.cmd** esetén: keresse meg a `reg delete HKCU\Software\Microsoft\Office\15.0\Common\DRM /f` sort, és közvetlenül alá adja hozzá a következő sort:

            reg delete HKCU\Software\Microsoft\Office\16.0\Common\DRM /f

    - A **Redirect_Onprem.cmd** esetén: keresse meg a `reg add "HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Common\DRM" /t REG_SZ /v "DefaultServer" /d "%CloudRMS%" /F1` sort, és közvetlenül alá adja hozzá a következő sort:

            reg add "HKEY_CURRENT_USER\Software\Microsoft\Office\16.0\Common\DRM" /t REG_SZ /v "DefaultServerUrl" /d "https://%CloudRMS%/_wmcs/licensing" /F 

            reg add "HKEY_CURRENT_USER\Software\Microsoft\Office\16.0\Common\DRM" /t REG_SZ /v "DefaultServer" /d "%CloudRMS%" /F

    Nem kötelező: A parancsfájlok nem hivatkoznak az Office 2016-ra a megjegyzésekben. Ha frissíteni szeretné a megjegyzéseket, hogy tükrözzék az Office 2016 ezen kiegészítéseit, végezze el a következő módosításokat a **Redirect_Onprem.cmd** fájlban:

    - Keressen meg az `::     or MSIPC (Office 2013) with on-premises AD RMS` sort, és cserélje le a következőre:
    
            ::     or MSIPC (Office 2013 and 2016) with on-premises AD RMS

    - Keressen meg az `echo Redirect SCP for Office 2013` sort, és cserélje le a következőre:
    
            echo Redirect SCP for Office versions based on MSIPC

    - Keressen meg az `echo Redirect MSIPC for Office 2013` sort, és cserélje le a következőre:
    
            echo Redirect MSIPC for Office versions based on MSIPC

4.  Windows rendszerű számítógépeken:

    - Futtassa a parancsfájlokat emelt szintű jogosultsággal a felhasználói környezetben.

    Mobileszközre telepített ügyfelek és Mac gépek:

    -  Távolítsa el az [AD RMS mobileszköz-bővítmény](http://technet.microsoft.com/library/dn673574.aspx) üzembe helyezésekor létrehozott SRV DNS-rekordokat.

#### Az áttelepítési parancsfájlok által végrehajtott módosítások
Ez a szakasz az áttelepítési parancsfájlok által végrehajtott módosításokat ismerteti. Ezeket az információkat csak tájékoztatási céllal, hibaelhárításhoz, illetve akkor használhatja, ha a módosításokat inkább saját kezűleg szeretné végrehajtani.

CleanUpRMS_RUN_Elevated.cmd:

-   Törölje a %userprofile%\AppData\Local\Microsoft\DRM és a %userprofile%\AppData\Local\Microsoft\MSIPC mappák tartalmát, beleértve az almappákat és a hosszú névvel rendelkező fájlokat is.

-   Törölje a következő beállításkulcsok tartalmát:

    -   HKEY_LOCAL_MACHINE\Software\Microsoft\Office\(11.0|12.0|14.0)\Common\DRM

    -   HKEY_CURRENT_USER\Software\Microsoft\Office\(11.0|12.0|14.0)\Common\DRM

    -   HKEY_LOCAL_MACHINE\Software\WoW6432Node\Microsoft\Office\(11.0|12.0|14.0)\Common\DRM

    -   HKEY_CURRENT_USER\Software\WoW6432Node\Microsoft\Office\(11.0|12.0|14.0)\Common\DRM

    -   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\ServiceLocation

    -   HKEY_LOCAL_MACHINE\SOFTWARE\WoW6432Node\Microsoft\MSIPC\ServiceLocation

    -   HKEY_LOCAL_MACHINE\Software\Microsoft\MSDRM\ServiceLocation

-   Adja hozzá a következő beállításazonosítókat:

    -   HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Common\DRM\DefaultServerURL

    -   HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Common\DRM\DefaultServer

Redirect_OnPrem.cmd:

-   Hozza létre a következő beállításkulcs-értékeket az egyes megadott URL-címekhez tartozó paraméterként a következő helyek mindegyikén:

    -   HKEY_CURRENT_USER\Software\Microsoft\Office\(11.0|12.0|14.0)\Common\DRM\LicenseServerRedirection

    -   HKEY_CURRENT_USER\Software\WoW6432Node\Microsoft\Office\(11.0|12.0|14.0)\Common\DRM\LicenseServerRedirection

    -   HKEY_LOCAL_MACHINE\Software\Microsoft\Office\(11.0|12.0|14.0)\Common\DRM\LicenseServerRedirection

    -   HKEY_LOCAL_MACHINE\Software\WoW6432Node\Microsoft\Office\(11.0|12.0|14.0)\Common\DRM\LicenseServerRedirection

    -   HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC\LicensingRedirection

    Mindegyik bejegyzés rendelkezik **https://RégiRMSkiszolgálóURL-címe/_wmcs/licensing** REG_SZ-értékkel, ami a következő formátumban tartalmazza az adatokat: **https://&lt;SajátBérlőURL-címe&gt;/_wmcs/licensing**.

    > [!NOTE]
    > A *&lt;SajátBérlőURL-címe&gt;* formátuma a következő: **{GUID}.rms.[régió].aadrm.com**.
    > 
    > Például: 5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com
    > 
    > Ezt az értéket a **RightsManagementServiceId** érték azonosításával keresheti meg, amikor az Azure RMS-hez futtatja a [Get-AadrmConfiguration](http://msdn.microsoft.com/library/windowsazure/dn629410.aspx) parancsmagot.


## További lépések
Az áttelepítés folytatásához ugorjon a [3. fázis: Támogatási szolgáltatások konfigurálása](migrate-from-ad-rms-phase3.md) című szakaszra.


<!--HONumber=Jul16_HO2-->


