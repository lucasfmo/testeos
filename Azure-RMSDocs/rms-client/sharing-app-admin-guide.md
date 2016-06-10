---
# required metadata

title: Rendszergazdai útmutató a Rights Management megosztóalkalmazáshoz | Azure RMS
description:
keywords:
author: cabailey
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: d9992e30-f3d1-48d5-aedc-4e721f7d7c25

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: esaggese
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---


# Rendszergazdai útmutató a Rights Management megosztóalkalmazáshoz

*A következőkre vonatkozik: Active Directory tartalomvédelmi szolgáltatások, Azure Rights Management, Windows 10, Windows 7 SP1, Windows 8, Windows 8.1*


Ha a Microsoft Rights Management megosztóalkalmazás vállalati hálózaton való telepítésért felelős, vagy ha több technikai információt szeretne elérni, mint amennyi a [Rights Management megosztóalkalmazás felhasználói útmutatója](sharing-app-user-guide.md) vagy [A Microsoft Rights Management megosztóalkalmazás Windowsra kiadott verziójával kapcsolatos gyakori kérdések](http://go.microsoft.com/fwlink/?LinkId=303971) szakaszban található, használja az alábbi információkat.

Az RMS megosztóalkalmazás legjobban az Azure RMS szolgáltatással működik, mert ez az üzembe helyezési konfiguráció támogatja a védett mellékletek küldését más szervezethez tartozó felhasználók számára, valamint egyéb lehetőségeket is, mint az e-mail értesítések, a dokumentumkövetés és a visszahívás.  Bizonyos korlátozások mellett azonban az alkalmazás működik a helyszíni verzióval, az AD RMS-sel is. Az Azure RMS és az AD RMS által támogatott szolgáltatások átfogó összehasonlításával kapcsolatban lásd: [Az Azure Rights Management és az AD RMS összehasonlítása](../understand-explore/compare-azure-rms-ad-rms.md). Ha az AD RMS-ről Azure RMS-re szeretne áttelepítést végezni, olvassa el a következőt: [Áttelepítés AD RMS-ről Azure Rights Managementre](../plan-design/migrate-from-ad-rms-to-azure-rms.md).

## A Microsoft Rights Management megosztóalkalmazás automatikus központi telepítése
Az RMS-megosztó alkalmazás Windows verziója támogatja a parancsfájlból történő telepítést, épp ezért kiválóan alkalmas a vállalati központi telepítéshez.

A telepítés egyetlen előfeltétele, hogy a számítógépen legalább a Windows 7 Service Pack 1 szervizcsomaggal frissített változata fusson, és telepítve legyen rá a Microsoft .NET keretrendszer legalább 4.0-s verziója. Ha telepítenie kell a Microsoft .NET keretrendszer 4.0-s verzióját, a [Microsoft letöltőközpontból letöltheti és telepítheti](http://www.microsoft.com/download/details.aspx?id=17718).

### Az RMS-megosztó alkalmazás letöltése automatikus központi telepítéshez

1.  Lépjen a Microsoft letöltőközpont [Microsoft Rights Management megosztóalkalmazás Windows rendszerhez](http://www.microsoft.com/download/details.aspx?id=40857) oldalára, és kattintson a **Letöltés** lehetőségre.

2.  Válassza ki és töltse le a szükséges fájlokat. Két ügyféltelepítő csomag létezik: egy a 64 bites Windowshoz (Microsoft Rights Management sharing application x64.zip), és egy másik a 32 bites Windowshoz (Microsoft Rights Management sharing application x86.zip).

3.  Bontsa ki a fájlokat a tömörített telepítőcsomagokból (ezt például a fájlokra duplán kattintva teheti meg). Ezután a kibontott fájlokat másolja fel egy olyan hálózati helyre, ami az ügyfélszámítógépek számára is hozzáférhető.

Az RMS-megosztó alkalmazás telepítőcsomagja különböző központi telepítési forgatókönyveket támogat, és a következőket tartalmazza:

|Leírás|Megvalósítási példa|
|---------------|-----------------------|
|Microsoft Online bejelentkezési segéd|Office 2010 és Azure RMS<br /><br />Office 2013 és Azure RMS, ha még nem telepítette az [Office 2013 2015. június 9-i frissítését](https://support.microsoft.com/kb/3054853) (KB3054853)|
|Office gyorsjavítás (KB 2596501)|Office 2010 és Azure RMS<br /><br />Office 2010 és Active Directory RMS|
|Az AD RMS Client 1.0 Azure RMS alkalmazással való használatát lehetővé tevő gyorsjavítás (KB 2843630)|Office 2010 és Azure RMS<br /><br />Office 2010 és Active Directory RMS|
|Az AD RMS-ügyfél és az RMS-megosztó alkalmazás|Office 2016 vagy Office 2013 és Azure RMS vagy Active Directory RMS<br /><br />Office 2010 és Azure RMS<br /><br />Office 2010 és Active Directory RMS<br /><br />Csak RMS megosztóalkalmazás és Office-bővítmény|
|Az Office menüszalagba beépülő modul|Office 2016 vagy Office 2013 és Azure RMS vagy Active Directory RMS<br /><br />Office 2010 és Azure RMS<br /><br />Office 2010 és Active Directory RMS<br /><br />Csak RMS megosztóalkalmazás és Office-bővítmény|
|Azure Active Directory Rights Management-előkészítő eszköz|Office 2010 és Azure RMS|
Az alábbi eljárásokkal a következő központi telepítési forgatókönyvek esetén beazonosíthatja az RMS-megosztó alkalmazás központi telepítéséhez szükséges parancsokat:

-   **Office 2016 vagy Office 2013 és Azure RMS vagy Active Directory RMS**

    A felhasználók gépein Office 2016 vagy Office 2013 fut, a vállalat az Azure RMS vagy az Active Directory RMS alkalmazást használja, és a felhasználók Azure RMS vagy Active Directory RMS alkalmazást használó más vállalatokkal működnek együtt.

-   **Office 2010 és Azure RMS**

    A felhasználók gépein Office 2010 fut, a vállalat az Azure RMS alkalmazást használja, és a felhasználók Azure RMS vagy Active Directory RMS alkalmazást használó más vállalatokkal működnek együtt.

-   **Office 2010 és Active Directory RMS**

    A felhasználók gépein Office 2010 fut, a vállalat az AD RMS alkalmazást használja, és a felhasználók Azure RMS alkalmazást használó más vállalatokkal működnek együtt.

-   **Csak RMS megosztóalkalmazás és Office-bővítmény**

    A felhasználók gépein Office 2016, Office 2013 vagy Office 2010 fut, a vállalat az AD RMS alkalmazást használja, és a felhasználóknak nem kell Azure RMS alkalmazást használó más vállalatokkal együttműködniük. Ennél a telepítési változatnál elég csak a megosztóalkalmazást és az Office-bővítményt telepíteni.

> [!NOTE]
> Ha vállalata az AD RMS alkalmazást használja e telepítési eljárások használata esetén, a felhasználók tudnak védett tartalmakat fogadni olyan vállalatoktól, amelyek az Azure RMS alkalmazást használják, de nem tudnak Azure RMS alkalmazást használó vállalatnál dolgozó felhasználónak védett tartalmat küldeni. Ha viszont vállalata az Azure RMS alkalmazást használja, a felhasználók küldeni is tudnak védett tartalmakat más vállalatoknak, és fogadni is tudnak ilyeneket azoktól.

Az egyes telepítési eljárások befejezéséhez újra kell indítania a számítógépet. A **shutdown /i** paranccsal például automatikus újraindítást kezdeményezhet..

### Az RMS megosztóalkalmazás üzembe helyezése Office 2016 vagy Office 2013 és Azure RMS vagy Active Directory RMS használata esetén

-   Minden olyan számítógépen, amelyre telepíteni szeretné az RMS megosztóalkalmazást és az ahhoz kapcsolódó összetevőket, futtassa megemelt jogosultságokkal a következő parancsot:

    ```
    setup.exe /s
    ```

A sikeresség ellenőrzéséhez tekintse meg jelen cikk [A telepítés sikerességének ellenőrzése](#verifying-installation-success) szakaszát.

### Az RMS megosztóalkalmazás telepítése Office 2010 és Azure RMS használata esetén

1.  Önnek az Office 365 globális rendszergazdájának vagy az Azure Active Directory-bérlőjének kell lennie, hogy megkaphassa a vállalat tanúsítványszolgáltatói URL-címét az Azure Active Directory Rights Management-előkészítő eszközt futtatva. Ezt az eszközt csak egyszer, egy számítógépen kell futtatnia. A tanúsítványszolgáltatói URL-címre akkor lesz majd szükség, amikor az egyes számítógépekre telepíti az RMS megosztóalkalmazást:

    1.  Jelentkezzen be valamelyik számítógépre helyi rendszergazdajelszóval.

    2.  Az adott számítógépen [töltse le és telepítse a Microsoft Online Services bejelentkezési segédet](http://www.microsoft.com/download/details.aspx?id=28177).

    3.  Futtassa az alábbi parancsot a tanúsítványszolgáltatói URL megjelenítéséhez a képernyőn, amelyet másolhat és menthet a következő lépéshez:

        -   64 bites Windows 8.1 és Windows 8 esetén:

            ```
            x64\aadrmprep.exe /findCertificationUrl /logfile "<log file path and name>"
            ```

        -   32 bites Windows 8.1 és Windows 8 esetén:

            ```
            X86\aadrmprep.exe /findCertificationUrl /logfile "<log file path and name>"
            ```

        -   64 bites Windows 7 esetén:

            ```
            x64\win7\aadrmprep.exe /findCertificationUrl /logfile "<log file path and name>"
            ```

        > [!NOTE]
        > Ez a parancs kérheti az Azure hitelesítő adatok megadását. Ha a számítógép nem kapcsolódik tartományhoz, akkor kérni fogja ezeket az adatokat. Ha a számítógép egy tartomány tagja, akkor lehetséges, hogy az eszköz fel tudja használni a gyorsítótárazott hitelesítő adatokat.

2.  Minden számítógépen, amelyre telepíti az RMS megosztóalkalmazást, futtassa a következő parancsot megemelt jogosultságokkal:

    ```
    setup.exe /s /configureO2010Admin /certificationUrl <certification_url>
    ```

3.  Minden számítógépen, amelyre telepíti az RMS megosztóalkalmazást, a felhasználóknak futtatniuk kell a következő parancsot (nem szükségesek hozzá megemelt jogosultságok). Ez többféleképpen is megvalósítható: meg lehet kérni a felhasználókat, hogy futtassák a parancsot (például egy e-mailbe ágyazott vagy az ügyfélszolgálati portálon közzétett hivatkozásra kattintva), vagy felveheti Ön is a parancsot a felhasználók bejelentkezési parancsfájljába:

    ```
    bin\RMSSetup.exe /configureO2010Only
    ```

A sikeresség ellenőrzéséhez tekintse meg jelen cikk [A telepítés sikerességének ellenőrzése](#verifying-installation-success) szakaszát.

### Az RMS megosztóalkalmazás telepítése Office 2010 és Active Directory RMS használata esetén

1.  Minden számítógépen, amelyre telepíti az RMS megosztóalkalmazást, futtassa a következő parancsot megemelt jogosultságokkal:

    ```
    setup.exe /s /configureO2010Admin
    ```

2.  Minden számítógépen, amelyre telepíti az RMS megosztóalkalmazást, a felhasználóknak futtatniuk kell a következő parancsot (nem szükségesek hozzá megemelt jogosultságok). Ez többféleképpen is megvalósítható: meg lehet kérni a felhasználókat, hogy futtassák a parancsot (például egy e-mailbe ágyazott vagy az ügyfélszolgálati portálon közzétett hivatkozásra kattintva), vagy felveheti Ön is a parancsot a felhasználók bejelentkezési parancsfájljába:

    -   64 bites Windows 10, Windows 8.1 és Windows 8 esetén:

        ```
        x64\aadrmprep.exe /configureO2010
        ```

    -   32 bites Windows 10, Windows 8.1 és Windows 8 esetén:

        ```
        X86\aadrmprep.exe /configureO2010
        ```

    -   64 bites Windows 7 esetén:

        ```
        x64\win7\aadrmpep.exe /configureO2010
        ```

A sikeresség ellenőrzéséhez tekintse meg jelen cikk [A telepítés sikerességének ellenőrzése](#verifying-installation-success) szakaszát.

### Csak az RMS megosztóalkalmazás és az Office-bővítmény telepítése

1.  A következő paranccsal telepítheti az AD RMS-ügyfelet és az RMS-megosztó alkalmazást:

    -   64 bites Windows esetén:

        ```
        x64\setup_ipviewer.exe /norestart /quiet /msicl "MSIRESTARTMANAGERCONTROL=Disable" /log "<log file path and name>"
        ```

    -   32 bites Windows esetén:

        ```
        X86\setup_ipviewer.exe /norestart /quiet /msicl "MSIRESTARTMANAGERCONTROL=Disable" /log "<log file path and name>"
        ```

    Példa: `\\server5\apps\rms\x64\setup_ipviewer.exe /norestart /quiet /msicl "MSIRESTARTMANAGERCONTROL=Disable" /log "C:\Log files\ipviewerinstall.log"`

2.  A következő parancsokkal telepítheti az Office beépülő modult:

    -   Az Office 64 bites verziója esetén:

        ```
        msiexec.exe /norestart /quiet MSIRESTARTMANAGERCONTROL=Disable /i "x64\Setup64.msi" /L*v "<log file path and name>"
        ```

    -   Az Office 32 bites verziója esetén:

        ```
        msiexec.exe /norestart /quiet MSIRESTARTMANAGERCONTROL=Disable /i "x86\Setup.msi" /L*v "<log file path and name>"
        ```

    Példa: `\\server5\apps\rms\msiexec.exe /norestart /quiet MSIRESTARTMANAGERCONTROL=Disable /i "x64\Setup64.msi" /L*v "C:\Log files\rmsofficeinstall.log"`

A sikeresség ellenőrzéséhez tekintse meg jelen cikk [A telepítés sikerességének ellenőrzése](#verifying-installation-success) szakaszát.

## A telepítés sikerességének ellenőrzése
A telepítési naplófájlokban ellenőrizheti egy telepítés sikerességét.

### A telepítés sikerességének ellenőrzése az RMS megosztóalkalmazás Office 2016 vagy Office 2013 és Azure RMS vagy Active Directory RMS használata esetén történő telepítésekor

-   A Setup.exe parancs sikerességének ellenőrzéséhez mindegyik számítógépen keresse meg az **RMInstaller.log** telepítési naplófájlt a *%temp%\RMS_installer_&lt;guid&gt;* mappában, majd keresse meg a kilépési kódot.

    A sikeres telepítés kilépőkódja 0, minden más szám telepítési hibát jelez.

    Példa a naplófájl nevére: **C:\temp\RMS_Installer_9352fc91-1982-43bf-958a-2ef1fe9c2ed0\RMInstaller.log**

### A telepítés sikerességének ellenőrzése az RMS megosztóalkalmazás Office 2010 és Azure RMS használata esetén történő telepítésekor

1.  A Setup.exe parancs sikerességének ellenőrzéséhez mindegyik számítógépen keresse meg az **RMInstaller.log** telepítési naplófájlt a *%temp%\RMS_installer_&lt;guid&gt;* mappában, majd keresse meg a kilépési kódot.

    A sikeres telepítés kilépőkódja 0, minden más szám telepítési hibát jelez.

    Példa a naplófájl nevére: **C:\temp\RMS_Installer_9352fc91-1982-43bf-958a-2ef1fe9c2ed0**

2.  Az RMSSetup.exe parancs sikerességének ellenőrzéséhez a felhasználónak az alábbi fájlok létrejöttét kell ellenőriznie a *%localappdata%\microsoft\drm* mappában:

    -   CERT-Machine-2048.drm

    -   CERT-Machine.drm

    -   CLC-&#42;.drm

    -   GIC-&#42;.drm

    Példa CLC-&#42;.drm fájlra:

    **CLC-alice@isvtenant999.onmicrosoft.com-{1b9cfccf;k5b11;k4a10;kac15;k29b2b6980f4c}.drm**

### A telepítés sikerességének ellenőrzése az RMS megosztóalkalmazás Office 2010 és Active Directory RMS használata esetén történő telepítésekor

1.  A Setup.exe parancs sikerességének ellenőrzéséhez mindegyik számítógépen keresse meg a telepítési naplófájlt a *%temp%\RMS_installer_&lt;guid&gt;* mappában, majd keresse meg a kilépési kódot.

    A sikeres telepítés kilépőkódja 0, minden más szám telepítési hibát jelez.

    Példa a naplófájl nevére: **C:\temp\RMS_Installer_9352fc91-1982-43bf-958a-2ef1fe9c2ed0**

2.  Az aadrmprep.exe parancs sikerességének ellenőrzéséhez mindegyik számítógépen keresse meg a következő szöveget a telepítési naplófájlban: **aadrmprep.exe exited with status SUCCESS**

    > [!NOTE]
    > Egyes esetekben a telepítés kétszer is lefuthat, ekkor az első alkalommal sikertelen, a második alkalommal pedig sikeres lesz.

    A következő parancsokkal ellenőrizheti manuálisan az eszköz által végrehajtott beállításjegyzék-módosításokat:

    -   [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSDRM\Federation]

        "FederationHomeRealm"="urn:HostedRmsOnlineService:Certification"

    -   [HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\MSDRM\Federation]

        "FederationHomeRealm"="urn:HostedRmsOnlineService:Certification"

    -   [HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\MSDRM\ServiceLocation\Activation]

        @="&lt;tanúsítvány url-címe&gt;"

    -   [HKEY_CURRENT_USER\SOFTWARE\Microsoft\Office\14.0\Common\DRM]

        DefaultUser="&lt;default_user&gt;"

### A telepítés sikerességének ellenőrzése csak az RMS megosztóalkalmazás és az Office-bővítmény telepítésekor

1.  A Setup_ipviewer.exe parancs sikerességének ellenőrzéséhez mindegyik számítógépen keresse meg a következő szöveget a telepítési naplófájlban: **Installation success or error status: 0**

    Egy sikeres telepítésből származó példasorok:

    **MSI (s) (F0:B8) [14:19:57:854]: Product: Active Directory Rights Management Services Client 2.1 -- Installation completed successfully.**

    **MSI (s) (F0:B8) [14:19:57:854]: Windows Installer installed the product. Product Name: Active Directory Rights Management Services Client 2.1. Product Version: 1.0.1179.1. Product Language: 1033. Manufacturer: Microsoft Corporation. Installation success or error status: 0.**

2.  Az Office beépülő modul sikerességének ellenőrzéséhez mindegyik számítógépen keresse meg a következő szöveget a telepítési naplófájlban: **Installation success or error status: 0**

    Egy sikeres telepítésből származó példasorok:

    **MSI (s) (9C:88) [18:49:04:007]: Product: Microsoft RMS Office Addins -- Installation completed successfully.**

    **MSI (s) (9C:88) [18:49:04:007]: Windows Installer installed the product. Product Name: Microsoft RMS Office Addins. Product Version: 1.0.7. Product Language: 1033. Manufacturer: Microsoft. Installation success or error status: 0.**

## Eltávolítási parancsok
Az üzembe helyezéshez szükséges telepítési parancsok közül nem mindegyik támogatja az eltávolítási parancsokat. Eltávolíthatja az AD RMS-ügyfelet és az RMS megosztóalkalmazást, és törölheti az Office beépülő modult. Ezen elemek telepítésének eltávolításához használja a következő parancsokat.

### Az AD RMS-ügyfél és az RMS megosztóalkalmazás eltávolítása

-   Az alábbi parancsokat használja:

    -   64 bites Windows esetén:

        ```
        x64\setup_ipviewer.exe /uninstall /quiet
        ```

    -   32 bites Windows esetén:

        ```
        x86\setup_ipviewer.exe /uninstall /quiet
        ```

### Az Office beépülő modul eltávolítása

-   Az alábbi parancsokat használja:

    -   Az Office 64 bites verziója esetén:

        ```
        msiexec /x \x64\Setup[64].msi /quiet
        ```

    -   Az Office 32 bites verziója esetén:

        ```
        msiexec /x \x86\Setup.msi /quiet
        ```

## Az automatikus frissítés kikapcsolása
Alapértelmezés szerint a felhasználók értesítést kapnak, ha az RMS megosztóalkalmazás újabb verziója érhető el, és az alkalmazás kéri annak letöltését. Ezt az értesítést az alábbi beállításkulcsot létrehozva tilthatja le:

1.  Keresse meg a **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC** kulcsot, és hozzon létre egy új, **RmsSharingApp** nevű kulcsot, ha még nincs ilyen.

2.  Jelölje ki az **RmsSharingApp** kulcsot, hozzon létre egy új **AllowUpdatePrompt** DWORD-értéket, és rendelje hozzá a **0** értéket.

Mivel az RMS megosztóalkalmazást a WSUS nem támogatja, az alábbi eljárással tesztelheti az RMS megosztóalkalmazás új verzióit, mielőtt telepítené őket az összes felhasználó gépére:

1.  Minden felhasználó számítógépén futtassa az automatikus frissítést kikapcsoló parancsfájlt. A rendszergazdák által az új verziók tesztelésére használt számítógépen ne futtassa ezt a parancsfájlt.

2.  Ha új verzió érhető el, a rendszergazdák letöltik és tesztelik azt.

3.  A tesztelés befejeztével, miután minden problémát elhárítottak, telepítse a legfrissebb verziót minden felhasználó számítógépére a jelen útmutatóban szereplő, az automatikus telepítésre vonatkozó utasításokat használva.

## Csak Azure RMS esetében: A dokumentumkövetés konfigurálása
Ha [dokumentumkövetést támogató előfizetéssel](https://technet.microsoft.com/en-us/dn858608) rendelkezik, a dokumentumkövetési webhely alapértelmezés szerint a szervezete összes felhasználója számára engedélyezve van.  A dokumentumkövetés olyan információkat mutat meg, mint a felhasználók által megosztott védett dokumentumokhoz hozzáférni próbálók e-mail-címe és helye. Ha adatvédelmi előírások miatt az ilyen információk megjelenítése a szervezeténél nem engedélyezett, a [Disable-AadrmDocumentTrackingFeature](http://go.microsoft.com/fwlink/?LinkId=623032) parancsmaggal letilthatja a dokumentumkövetés elérését. Az [Enable-AadrmDocumentTrackingFeature](http://go.microsoft.com/fwlink/?LinkId=623037) parancsmaggal bármikor engedélyezheti újra a webhelyhez való hozzáférést, a [Get-AadrmDocumentTrackingFeature](http://go.microsoft.com/fwlink/?LinkId=623037) segítségével pedig ellenőrizheti, hogy jelenleg engedélyezve van-e a hozzáférés.

Ezen parancsmagok futtatásához legalább **2.3.0.0** verziójú Azure RMS Windows PowerShell-modulra van szükség.  A telepítési utasításokért lásd: [Installing Windows PowerShell for Azure Rights Management](../deploy-use/install-powershell.md) (Az Azure Rights Managementhez készült Windows PowerShell telepítése)..

> [!TIP]
> Ha már korábban letöltötte és telepítette a modult, ellenőrizze a verziószámot a következő futtatásával: `(Get-Module aadrm –ListAvailable).Version`

Az alábbi URL-címek a dokumentumkövetés során használatosak, és engedélyezni kell őket (adja hozzá például a Megbízható helyek listájához, ha Internet Explorert használ fokozott biztonsági beállításokkal):

-   https://&#42;.azurerms.com

-   https://ecn.dev.virtualearth.net

    > [!NOTE]
    > Ez az URL-cím a Bing térképekhez tartozik.

-   https://&#42;.microsoftonline.com

-   https://&#42;.microsoftonline-p.com

## Csak AD RMS esetén: Több e-mail tartomány támogatása a szervezeten belül
Ha vállalata AD RMS alkalmazást használ, és a felhasználók több e-mail tartományban vannak, például egy összeolvadást vagy felvásárlást követően, végezze el a beállításjegyzékben a következő módosítást:

1.  Keresse meg a **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC** kulcsot, és hozzon létre egy új, **RmsSharingApp** nevű kulcsot, ha még nincs ilyen.

2.  Jelölje ki az **RmsSharingApp** kulcsot, hozzon létre egy új karakterláncsoros értéket **FederatedDomains** néven, majd adja hozzá a szervezet által használt tartományokat és altartományokat. Helyettesítő karakterek nem használhatók.

    Példa: A Coho Vineyard &amp; Winery vállalat normál e-mail tartománya **cohovineyardandwinery.com**, de a fúziók következtében használják a **cohowinery.com**, az **eastcoast.cohowinery.com** és a **cohovineyard** e-mail tartományokat is. A **FederatedDomains** érték adataihoz a rendszergazda a következőket írja be: **cohowinery.com; eastcoast.cohowinery.com; cohovineyard**

Ha nem végzi el a módosítást a beállításjegyzékben, lehet, hogy a felhasználók nem tudják megtekinteni a vállalatukon belüli más felhasználók által levédett tartalmakat. Erre a beállításjegyzék-bejegyzésre az Azure RMS használata esetén nincs szükség.


## További lépések
A védelmi szintek (natív és általános) közötti különbségeket, a támogatott fájltípusokat és fájlnévkiterjesztéseket, valamint az alapértelmezett védelmi szint módosításának módját is ismertető további technikai információk: [A Rights Management megosztóalkalmazás technikai áttekintése](sharing-app-admin-guide-technical.md).



<!--HONumber=Apr16_HO4-->


