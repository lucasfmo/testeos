---
title: "Office 365&colon; Konfigurálás ügyfelek és online szolgáltatások számára | Azure RMS"
description: 
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 0a6ce612-1b6b-4e21-b7fd-bcf79e492c3b
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 0f355da35dff62ecee111737eb1793ae286dc93e
ms.openlocfilehash: 7a2436a6ebb17e4336f1321b8f3742e34ea59689


---

# Office 365: Konfigurálás ügyfelek és online szolgáltatások számára

*A következőkre vonatkozik: Azure Rights Management, Office 365*

Mivel az Office 365 natívan támogatja az Azure RMS-t, az olyan alkalmazásokhoz, mint a Word, az Excel, a PowerPoint, az Outlook és az Outlook Web App, nincs szükség az ügyfélszámítógép konfigurálására a tartalomvédelmi szolgáltatások (IRM) funkcióinak támogatásához. A felhasználóknak egyszerűen be kell jelentkezniük az Office-alkalmazásaikba [!INCLUDE[o365_1](../includes/o365_1_md.md)] hitelesítő adataikkal, és máris levédhetik a fájljaikat, valamint használhatják a mások által levédett fájlokat és e-maileket.

Emellett azért javasoljuk, hogy egészítse ki ezeket az alkalmazásokat a Rights Management megosztóalkalmazással, hogy a felhasználók kihasználhassák az Office-bővítmény előnyeit. További információk: [Rights Management megosztóalkalmazás: telepítés és konfigurálás ügyfelek esetén](configure-sharing-app.md).

## Exchange Online: az IRM konfigurálása
Ahhoz, hogy az Exchange Online támogassa az Azure RMS-t, konfigurálnia kell a tartalomvédelmi szolgáltatásokat (IRM) az Exchange Online-hoz. Ehhez futtassa a Windows PowerShellben (nincs szükség külön modul telepítésére) [az Exchange Online PowerShell-parancsait](https://technet.microsoft.com/library/jj200677.aspx).

> [!NOTE]
> Ha ügyfél által felügyelt bérlőkulcsot (BYOK) használ az Azure RMS-hez egy Microsoft által felügyelt bérlőkulcs alapértelmezett konfigurációja helyett, jelenleg nem konfigurálhatja az Exchange Online-t az Azure RMS támogatására. További információ: [A BYOK díjszabása és korlátozásai](../plan-design/byok-price-restrictions.md).
>
> Ha BYOK használata mellett próbálja konfigurálni az Exchange Online-t, a kulcs importálására szolgáló parancs (a következő eljárás 5. lépése) meghiúsul a következő hibaüzenettel: **[FailureCategory=Cmdlet-FailedToGetTrustedPublishingDomainFromRmsOnlineException]**.

Az alábbi lépések egy jellemző parancskészletet mutatnak be, amely futtatásával engedélyezhető az Exchange Online számára az Azure RMS használata:

1.  Ha most először használja a számítógépén a Windows PowerShellt az Exchange Online-nal, konfigurálnia kell a Windows PowerShellt aláírt parancsfájlok futtatására. Indítson el egy Windows PowerShell-munkamenetet a **Futtatás rendszergazdaként** beállítással, majd írja be a következőt:

    ```
    Set-ExecutionPolicy RemoteSigned
    ```

2.  A Windows PowerShell-munkamenetben jelentkezzen be az Exchange Online-ba egy távoli rendszerhéj-hozzáféréshez engedélyezett fiókkal. Alapértelmezés szerint minden Exchange Online-ban létrehozott fióknál engedélyezett a távoli rendszerhéj-hozzáférés, de ez letiltható (illetve engedélyezhető) a [Set-User &lt;UserIdentity&gt; -RemotePowerShellEnabled](https://technet.microsoft.com/library/jj984292%28v=exchg.160%29.aspx) paranccsal.

    Bejelentkezéshez írja be a következőt:

    ```
    $Cred = Get-Credential
    ```
    A **Windows PowerShell – hitelesítő adatok kérése** párbeszédpanelen adja meg az Office 365-felhasználónevét és -jelszavát.

3.  Az Exchange Online szolgáltatáshoz az alábbi két parancs futtatásával csatlakozhat:

    ```
    $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.outlook.com/powershell/ -Credential $Cred -Authentication Basic –AllowRedirection
    ```

    ```
    Import-PSSession $Session
    ```

4.  Adja meg az Azure RMS-bérlőkulcs helyét a szervezet bérlőjének létrehozási helye szerint:

    Észak-Amerika (és kormányzati előfizetések) esetén:

    ```
    Set-IRMConfiguration -RMSOnlineKeySharingLocation "https://sp-rms.na.aadrm.com/TenantManagement/ServicePartner.svc"
    ```
    Európa esetében:

    ```
    Set-IRMConfiguration -RMSOnlineKeySharingLocation "https://sp-rms.eu.aadrm.com/TenantManagement/ServicePartner.svc"
    ```
    Ázsia esetében:

    ```
    Set-IRMConfiguration -RMSOnlineKeySharingLocation "https://sp-rms.ap.aadrm.com/TenantManagement/ServicePartner.svc"
    ```
    Dél-Amerika esetén:

    ```
    Set-IRMConfiguration -RMSOnlineKeySharingLocation "https://sp-rms.sa.aadrm.com/TenantManagement/ServicePartner.svc"
    ```

5.  Importálja az Azure RMS konfigurációs adatait az Exchange Online-ba megbízható közzétételi tartomány (TPD) formájában. Ez tartalmazza az Azure RMS-bérlőkulcsot és az Azure RMS-sablonokat:

    ```
    Import-RMSTrustedPublishingDomain -RMSOnline -name "RMS Online"
    ```
    Ebben a parancsban az **RMS Online** nevet használtuk az Azure RMS-hez tartozó TPD alapneveként az Exchange Online-ban. A TPD az importálása után az Exchange Online-ban az **RMS Online - 1** nevet kapja.

6.  Engedélyezze az Azure RMS funkcióit, hogy az Exchange Online elérhesse az IRM szolgáltatásait:

    ```
    Set-IRMConfiguration -InternalLicensingEnabled $true
    ```
    A parancs futtatása után a Rights Management automatikusan engedélyezve lesz az Outlook ügyfélprogramhoz, az Outlook Web Apphez és az Exchange Active Synchez.

7.  Az alábbi paranccsal lehetősége van ellenőrizni, hogy a konfigurálás sikeres volt-e:

    ```
    Test-IRMConfiguration -Sender <user email address>
    ```
    Például: **Test-IRMConfiguration -Sender  adams@contoso.com**

    Ez a parancs több ellenőrzést futtat, többek között ellenőrzi a szolgáltatáshoz való csatlakozás sikerességét, lekéri a konfigurációt, lekéri az URI-kat, a licenceket és a sablonokat (ha vannak). A Windows PowerShell-munkamenetben mindegyik eredményét megtekintheti, és legalul a következő jelenik meg, ha minden ellenőrzés rendben lezárult: **ÖSSZESÍTETT EREDMÉNY: SIKERES**

8.  Szakítsa meg a távoli PowerShell-munkamenetet:

    ```
    Remove-PSSession $Session
    ```

A felhasználók mostantól az Azure RMS használatával védhetik az e-mail-üzeneteiket. Az Outlook Web App alkalmazásban például válassza a bővített menü (**...**) **Engedélyek beállítása** elemét, majd válassza a **Nem továbbítandó** lehetőséget, vagy az egyik elérhető sablont az adatvédelem e-mail-üzenetekre és az esetleges mellékletekre való alkalmazásához. Viszont, mivel az Outlook Web App egy napig tartja a gyorsítótárban a felhasználói felületet, a konfigurációs parancsok futtatása után várja meg ezen időszak leteltét, mielőtt adatvédelmet próbál alkalmazni az e-mail-üzenetekre. Mielőtt a felhasználói felület frissülne, és tükrözné az új konfigurációt, az **Engedélyek beállítása** menüből nem érhetők el a lehetőségek.

> [!IMPORTANT]
> Ha új [egyéni sablonokat hoz létre](configure-custom-templates.md) az Azure RMS-hez, vagy frissíti a sablonokat, a módosítások Exchange Online-nal való szinkronizálásához minden alkalommal futtatnia kell a következő Exchange Online PowerShell-parancsot (ha szükséges, előbb futtassa a 2. és 3. lápést): `Import-RMSTrustedPublishingDomain -Name "RMS Online - 1" -RefreshTemplates –RMSOnline`

Exchange-rendszergazdaként konfigurálhat olyan szolgáltatásokat, amelyek automatikusan alkalmaznak adatvédelmet. Ilyenek az [átviteli szabályok](https://technet.microsoft.com/library/dd302432.aspx), az [adatveszteség-megelőzési házirendek (DLP)](https://technet.microsoft.com/library/jj150527%28v=exchg.150%29.aspx) és a [védett hangposta](https://technet.microsoft.com/library/dn198211%28v=exchg.150%29.aspx) (egyesített üzenetküldési szolgáltatások).

Az Exchange Online IRM-funkciókat engedélyező konfigurálásáról az Exchange-könyvtár dokumentációjában talál részletes útmutatást. Példa:

-   [Csatlakozás az Exchange Online-hoz távoli PowerShell használatával](https://technet.microsoft.com/library/jj984289%28v=exchg.160%29.aspx)

-   [Az IRM konfigurálása az Azure Rights Management használatára](https://technet.microsoft.com/library/dn151475%28v=exchg.150%29.aspx)

### Office 365-üzenetek titkosítása
Futtassa az előző szakaszban leírt lépéseket, de ha nem szeretné, hogy megjelenjenek sablonok, a 6. lépés előtt futtassa a következő parancsot, hogy az IRM-sablonok ne legyenek elérhetők az Outlook Web App alkalmazásban és az Outlook ügyfélprogramban: `Set-IRMConfiguration -ClientAccessServerEnabled $false`

Ekkor készen áll az [átviteli szabályok](https://technet.microsoft.com/library/dd302432.aspx) konfigurálására, hogy azok automatikusan módosítsák az üzenetbiztonságot, ha szervezeten kívüli a címzett, majd válassza az **Titkosítás az Office 365 üzenettitkosításával** lehetőséget.

Az üzenettitkosításról további információkat az Exchange-könyvtár [Encryption in Office 365](https://technet.microsoft.com/library/dn569286.aspx) (Titkosítás az Office 365-ben) című részében találhat.

## SharePoint Online és OneDrive Vállalati verzió: az IRM konfigurálása
Ahhoz, hogy a SharePoint Online és a OneDrive Vállalati verzió támogassa az Azure RMS-t, először engedélyeznie kell a tartalomvédelmi szolgáltatásokat (IRM) a SharePoint Online-hoz a SharePoint felügyeleti központon keresztül. Ekkor a webhely tulajdonosai elláthatják IRM-védelemmel a SharePoint-listáikat és -dokumentumtáraikat, a felhasználók pedig a OneDrive Vállalati verzió könyvtárát, így az oda mentett, és másokkal megosztott dokumentumok automatikusan Azure RMS-védelmet kapnak.

A tartalomvédelmi szolgáltatások (IRM) a SharePoint Online-hoz történő engedélyezéséhez tekintse meg az Office-webhely alábbi útmutatásait:

-   [A tartalomvédelmi szolgáltatás (IRM) beállítása a SharePoint Felügyeleti központban](http://office.microsoft.com/office365-sharepoint-online-enterprise-help/set-up-information-rights-management-irm-insharepoint-online-HA102895193.aspx)

Ezt a konfigurálást az Office 365-rendszergazda végzi el.

### Az IRM konfigurálása könyvtárakhoz és listákhoz
Ha engedélyezte az IRM szolgáltatást a SharePointhoz, a webhely tulajdonosai IRM-védelmet biztosíthatnak a SharePoint-dokumentumtáraikhoz és -listáikhoz. Útmutatást az Office-webhely alábbi részén találhat:

-   [Tartalomvédelmi szolgáltatás alkalmazása listában vagy tárban](http://office.microsoft.com/sharepoint-help/apply-information-rights-management-to-a-list-or-library-HA102891460.aspx)

Ezt a konfigurálást a SharePoint-webhely rendszergazdája végzi el.

### Az IRM konfigurálása a OneDrive Vállalati verzióhoz
Miután engedélyezte a tartalomvédelmi szolgáltatásokat a SharePoint Online-hoz, a felhasználók OneDrive Vállalati verzióban található dokumentumtárára is konfigurálható a Rights Management-védelem.  A felhasználók ezt maguknak konfigurálhatják a OneDrive **Beállítások** ikonjának használatával. Noha rendszergazdák nem konfigurálhatják a Rights Managementet a felhasználói OneDrive Vállalati verzióhoz a SharePoint felügyeleti központtal, a Windows PowerShell használatával elvégezhető ez a lépés.

> [!NOTE]
> A OneDrive Vállalati verzió konfigurálásával kapcsolatos további információért tekintse meg az Office-dokumentáció [a OneDrive Vállalati verzió az Office 365-ben történő beállítását](https://support.office.com/article/Set-up-OneDrive-for-Business-in-Office-365-3e21f8f0-e0a1-43be-aa3e-8c0236bf11bb) ismertető szakaszát.

#### Felhasználói konfigurálás
Juttassa el a felhasználókhoz ezt az útmutatást, hogy konfigurálhassák a OneDrive Vállalati verziót, és IRM-védelmet biztosíthassanak az üzleti fájljaikhoz.

1.  A OneDrive-ban kattintson a **Beállítások** ikonra a Beállítások menü megnyitásához, majd kattintson a **Webhely tartalma** elemre.

2.  Vigye a mutatót a **Dokumentumok** csempére, válassza a három pontot (**...**), majd kattintson a **BEÁLLÍTÁSOK** elemre.

3.  A **Beállítások** lap **Engedélyek és kezelés** szakaszában kattintson a **Tartalomvédelmi szolgáltatások** elemre.

4.  A **Tartalomvédelmi szolgáltatás beállításai** lapon jelölje be a **Letöltési jogosultságok korlátozása a tárban** jelölőnégyzetet, adja meg a választott engedélyek nevét és leírását, és amennyiben szeretne, kattintson a **BEÁLLÍTÁSOK MEGJELENÍTÉSE** elemre a választható konfigurációk beállításához, majd kattintson az **OK** gombra.

    A konfigurációs lehetőségekkel kapcsolatos további információért tekintse meg az Office-dokumentáció [Tartalomvédelmi szolgáltatás alkalmazása listában vagy tárban](https://support.office.com/article/Apply-Information-Rights-Management-to-a-list-or-library-3bdb5c4e-94fc-4741-b02f-4e7cc3c54aa1) című szakaszában található útmutatást.

Mivel ez a konfiguráció a rendszergazdák helyett a felhasználókra hárítja a OneDrive Vállalati verzió könyvtárának IRM-védelmével kapcsolatos feladatokat, ismertesse a felhasználóival a fájlok védelmének előnyeit és az aktiválás módját. Elmagyarázhatja például, hogy ha megosztanak egy dokumentumot a OneDrive Vállalati verzióról, csak azok férhetnek hozzá az általuk megadott korlátozások nélkül, akiket erre felhatalmaznak, még ha a fájlnak valaki új nevet is adna, vagy máshová másolná.

#### Rendszergazdai konfigurálás
Noha nem konfigurálhatja az IRM-et a felhasználók OneDrive Vállalati verziójához a SharePoint felügyeleti központtal, a Windows PowerShell használatával elvégezhető ez a lépés. Ha engedélyezni szeretné az IRM-et ezekhez a könyvtárakhoz, hajtsa végre az alábbi lépéseket:

1.  Töltse le és telepítse a [SharePoint Online ügyféloldali összetevők SDK-ját](http://www.microsoft.com/en-us/download/details.aspx?id=42038).

2.  Töltse le és telepítse a [SharePoint Online felügyeleti rendszerhéjat](http://www.microsoft.com/en-us/download/details.aspx?id=35588).

3.  Másolja át a következő parancsfájl tartalmát, és adja a Set-IRMOnOneDriveForBusiness.ps1 nevet a fájlnak a számítógépén.

    *&#42;&#42;Jogi nyilatkozat&#42;&#42;:* Ez a parancsfájlpélda semmilyen standard támogatási program vagy szolgáltatás esetében nem támogatott a Microsoft által. A parancsfájlpéldát „JELEN ÁLLAPOTÁBAN”, bármiféle jótállás vállalása nélkül biztosítjuk.

    ```
    # Requires Windows PowerShell version 3

    <#
      Description:

        Configures IRM policy settings for OneDrive for Business and can also be used for SharePoint Online libraries and lists

     Script Installation Requirements:

       SharePoint Online Client Components SDK
       http://www.microsoft.com/en-us/download/details.aspx?id=42038

       SharePoint Online Management Shell
       http://www.microsoft.com/en-us/download/details.aspx?id=35588

    ======
    #>

    # URL will be in the format https://<tenant-name>-admin.sharepoint.com
    $sharepointAdminCenterUrl = "https://contoso-admin.sharepoint.com"

    $tenantAdmin = "admin@contoso.com"

    $webUrls = @("https://contoso-my.sharepoint.com/personal/user1_contoso_com",
                 "https://contoso-my.sharepoint.com/personal/user2_contoso_com",
                 "https://contoso-my.sharepoint.com/personal/user3_contoso_com")

    <# As an alternative to specifying the URLs as an array, you can import them from a CSV file (no header, single value per row).
       Then, use: $webUrls = Get-Content -Path "File_path_and_name.csv"

    #>

    $listTitle = "Documents"

    function Load-SharePointOnlineClientComponentAssemblies
    {
        [cmdletbinding()]
        param()

        process
        {
            # assembly location: C:\Program Files\Common Files\microsoft shared\Web Server Extensions\16\ISAPI
            try
            {
                Write-Verbose "Loading Assembly: Microsoft.Office.Client.Policy, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
                [System.Reflection.Assembly]::Load("Microsoft.Office.Client.Policy, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

                Write-Verbose "Loading Assembly: Microsoft.Office.Client.TranslationServices, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
                [System.Reflection.Assembly]::Load("Microsoft.Office.Client.TranslationServices, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

                Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
                [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

                Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.DocumentManagement, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
                [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.DocumentManagement, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

                Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Publishing, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
                [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Publishing, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

                Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Runtime, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
                [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Runtime, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

                Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Search.Applications, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
                [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Search.Applications, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

                Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Search, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
                [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Search, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

                Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Taxonomy, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
                [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Taxonomy, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

                Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.UserProfiles, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
                [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.UserProfiles, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

                return $true
            }
            catch
            {
                if($_.Exception.Message -match "Could not load file or assembly")
                {
                    Write-Error -Message "Unable to load the SharePoint Server 2013 Client Components.`nDownload Location: http://www.microsoft.com/en-us/download/details.aspx?id=42038"
                }
                else
                {
                    Write-Error -Exception $_.Exception
                }
                return $false
            }
        }
    }

    function Load-SharePointOnlineModule
    {
        [cmdletbinding()]
        param()

        process
        {
            do
            {
                # Installation location: C:\Program Files\SharePoint Online Management Shell\Microsoft.Online.SharePoint.PowerShell
                $spoModule = Get-Module -Name Microsoft.Online.SharePoint.PowerShell -ErrorAction SilentlyContinue

                if(-not $spoModule)
                {
                    try
                    {
                        Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
                        return $true
                    }
                    catch
                    {
                        if($_.Exception.Message -match "Could not load file or assembly")
                        {
                            Write-Error -Message "Unable to load the SharePoint Online Management Shell.`nDownload Location: http://www.microsoft.com/en-us/download/details.aspx?id=35588"
                        }
                        else
                        {
                            Write-Error -Exception $_.Exception
                        }
                        return $false
                    }
                }
                else
                {
                    return $true
                }
            }
            while(-not $spoModule)
        }
    }

    function Set-IrmConfiguration
    {
        [cmdletbinding()]
        param(
            [parameter(Mandatory=$true)][Microsoft.SharePoint.Client.List]$List,
            [parameter(Mandatory=$true)][string]$PolicyTitle,
            [parameter(Mandatory=$true)][string]$PolicyDescription,
            [parameter(Mandatory=$false)][switch]$IrmReject,
            [parameter(Mandatory=$false)][DateTime]$ProtectionExpirationDate,
            [parameter(Mandatory=$false)][switch]$DisableDocumentBrowserView,
            [parameter(Mandatory=$false)][switch]$AllowPrint,
            [parameter(Mandatory=$false)][switch]$AllowScript,
            [parameter(Mandatory=$false)][switch]$AllowWriteCopy,
            [parameter(Mandatory=$false)][int]$DocumentAccessExpireDays,
            [parameter(Mandatory=$false)][int]$LicenseCacheExpireDays,
            [parameter(Mandatory=$false)][string]$GroupName
        )

        process
        {
            Write-Verbose "Applying IRM Configuration on '$($List.Title)'"

            # reset the value to the default settings
            $list.InformationRightsManagementSettings.Reset()

            $list.IrmEnabled = $true

            # IRM Policy title and description

                $list.InformationRightsManagementSettings.PolicyTitle       = $PolicyTitle
                $list.InformationRightsManagementSettings.PolicyDescription = $PolicyDescription

            # Set additional IRM library settings

                # Do not allow users to upload documents that do not support IRM
                $list.IrmReject = $IrmReject.IsPresent

                $parsedDate = Get-Date
                if([DateTime]::TryParse($ProtectionExpirationDate, [ref]$parsedDate))
                {
                    # Stop restricting access to the library at <date>
                    $list.IrmExpire = $true
                    $list.InformationRightsManagementSettings.DocumentLibraryProtectionExpireDate = $ProtectionExpirationDate
                }

                # Prevent opening documents in the browser for this Document Library
                $list.InformationRightsManagementSettings.DisableDocumentBrowserView = $DisableDocumentBrowserView.IsPresent

            # Configure document access rights

                # Allow viewers to print
                $list.InformationRightsManagementSettings.AllowPrint = $AllowPrint.IsPresent

                # Allow viewers to run script and screen reader to function on downloaded documents
                $list.InformationRightsManagementSettings.AllowScript = $AllowScript.IsPresent

                # Allow viewers to write on a copy of the downloaded document
                $list.InformationRightsManagementSettings.AllowWriteCopy = $AllowWriteCopy.IsPresent

                if($DocumentAccessExpireDays)
                {
                    # After download, document access rights will expire after these number of days (1-365)
                    $list.InformationRightsManagementSettings.EnableDocumentAccessExpire = $true
                    $list.InformationRightsManagementSettings.DocumentAccessExpireDays   = $DocumentAccessExpireDays
                }

            # Set group protection and credentials interval

                if($LicenseCacheExpireDays)
                {
                    # Users must verify their credentials using this interval (days)
                    $list.InformationRightsManagementSettings.EnableLicenseCacheExpire = $true
                    $list.InformationRightsManagementSettings.LicenseCacheExpireDays   = $LicenseCacheExpireDays
                }

                if($GroupName)
                {
                    # Allow group protection. Default group:
                    $list.InformationRightsManagementSettings.EnableGroupProtection = $true
                    $list.InformationRightsManagementSettings.GroupName             = $GroupName
                }
        }
        end
        {
            if($list)
            {
                Write-Verbose "Committing IRM configuration settings on '$($list.Title)'"
                $list.InformationRightsManagementSettings.Update()
                $list.Update()
                $script:clientContext.Load($list)
                $script:clientContext.ExecuteQuery()
            }
        }
    }

    function Get-CredentialFromCredentialCache
    {
        [cmdletbinding()]
        param([string]$CredentialName)

        #if( Test-Path variable:\global:CredentialCache )
        if( Get-Variable O365TenantAdminCredentialCache -Scope Global -ErrorAction SilentlyContinue )
        {
            if($global:O365TenantAdminCredentialCache.ContainsKey($CredentialName))
            {
                Write-Verbose "Credential Cache Hit: $CredentialName"
                return $global:O365TenantAdminCredentialCache[$CredentialName]
            }
        }
        Write-Verbose "Credential Cache Miss: $CredentialName"
        return $null
    }

    function Add-CredentialToCredentialCache
    {
        [cmdletbinding()]
        param([System.Management.Automation.PSCredential]$Credential)

        if(-not (Get-Variable CredentialCache -Scope Global -ErrorAction SilentlyContinue))
        {
            Write-Verbose "Initializing the Credential Cache"
            $global:O365TenantAdminCredentialCache = @{}
        }

        Write-Verbose "Adding Credential to the Credential Cache"
        $global:O365TenantAdminCredentialCache[$Credential.UserName] = $Credential
    }

    # load the required assemblies and Windows PowerShell modules

        if(-not ((Load-SharePointOnlineClientComponentAssemblies) -and (Load-SharePointOnlineModule)) ) { return }

    # Add the credentials to the client context and SharePoint Online service connection

        # check for cached credentials to use
        $o365TenantAdminCredential = Get-CredentialFromCredentialCache -CredentialName $tenantAdmin

        if(-not $o365TenantAdminCredential)
        {
            # when credentials are not cached, prompt for the tenant admin credentials
            $o365TenantAdminCredential = Get-Credential -UserName $tenantAdmin -Message "Enter the password for the Office 365 admin"

            if(-not $o365TenantAdminCredential -or -not $o365TenantAdminCredential.UserName -or $o365TenantAdminCredential.Password.Length -eq 0 )
            {
                Write-Error -Message "Could not validate the supplied tenant admin credentials"
                return
            }

            # add the credentials to the cache
            Add-CredentialToCredentialCache -Credential $o365TenantAdminCredential
        }

    # connect to Office365 first, required for SharePoint Online cmdlets to run

        Connect-SPOService -Url $sharepointAdminCenterUrl -Credential $o365TenantAdminCredential

    # enumerate each of the specified site URLs

        foreach($webUrl in $webUrls)
        {
            $grantedSiteCollectionAdmin = $false

            try
            {
                # establish the client context and set the credentials to connect to the site
                $script:clientContext = New-Object Microsoft.SharePoint.Client.ClientContext($webUrl)
                $script:clientContext.Credentials = New-Object Microsoft.SharePoint.Client.SharePointOnlineCredentials($o365TenantAdminCredential.UserName, $o365TenantAdminCredential.Password)

                # initialize the site and web context
                $script:clientContext.Load($script:clientContext.Site)
                $script:clientContext.Load($script:clientContext.Web)
                $script:clientContext.ExecuteQuery()

                # load and ensure the tenant admin user account if present on the target SharePoint site
                $tenantAdminUser = $script:clientContext.Web.EnsureUser($o365TenantAdminCredential.UserName)
                $script:clientContext.Load($tenantAdminUser)
                $script:clientContext.ExecuteQuery()

                # check if the tenant admin is a site admin
                if( -not $tenantAdminUser.IsSiteAdmin )
                {
                    try
                    {
                        # grant the tenant admin temporary admin rights to the site collection
                        Set-SPOUser -Site $script:clientContext.Site.Url -LoginName $o365TenantAdminCredential.UserName -IsSiteCollectionAdmin $true | Out-Null
                        $grantedSiteCollectionAdmin = $true
                    }
                    catch
                    {
                        Write-Error $_.Exception
                        return
                    }
                }

                try
                {
                    # load the list orlibrary using CSOM

                    $list = $null
                    $list = $script:clientContext.Web.Lists.GetByTitle($listTitle)
                    $script:clientContext.Load($list)
                    $script:clientContext.ExecuteQuery()

                    # **************  ADMIN INSTRUCTIONS  **************
                    # If necessary, modify the following Set-IrmConfiguration parameters to match your required values
                    # The supplied options and values are for example only
                    # Example that shows the Set-IrmConfiguration command with all parameters: Set-IrmConfiguration -List $list -PolicyTitle "Protected Files" -PolicyDescription "This policy restricts access to authorized users" -IrmReject -ProtectionExpirationDate $(Get-Date).AddDays(180) -DisableDocumentBrowserView -AllowPrint -AllowScript -AllowWriteCopy -LicenseCacheExpireDays 25 -DocumentAccessExpireDays 90

                    Set-IrmConfiguration -List $list -PolicyTitle "Protected Files" -PolicyDescription "This policy restricts access to authorized users"  
                }
                catch
                {
                    Write-Error -Message "Error setting IRM configuration on site: $webUrl.`nError Details: $($_.Exception.ToString())"
                }
           }
           finally
           {
                if($grantedSiteCollectionAdmin)
                {
                    # remove the temporary admin rights to the site collection
                    Set-SPOUser -Site $script:clientContext.Site.Url -LoginName $o365TenantAdminCredential.UserName -IsSiteCollectionAdmin $false | Out-Null
                }
           }
        }

    Disconnect-SPOService -ErrorAction SilentlyContinue
    ```

4.  Nézze át a parancsfájlt, és hajtsa végre a következő módosításokat:

    1.  Kerese meg a következőt: `$sharepointAdminCenterUrl`, és cserélje le a példában szereplő értéket a saját SharePoint felügyeleti központja URL-címére.

        Ez az érték szerepel kiindulási URL-címként, amikor belép a SharePoint felügyeleti központba, és a formátuma a következő: https://*&lt;bérlő_neve&gt;*-admin.sharepoint.com

        Ha a bérlő neve például „contoso”, akkor a következőt kellene megadnia: **https://contoso-admin.sharepoint.com**

    2.  Kerese meg a következőt: `$tenantAdmin`, és cserélje le a saját teljes globális Office 365-rendszergazdai fiókjára.

        Ez az érték megegyezik azzal, amit az Office 365-portálra való belépéshez használ globális rendszergazdaként, és a formátuma a következő: felhasználónév@*&lt;bérlői tartomány neve&gt;*.com

        Ha például az Office 365 globális rendszergazdájaként a felhasználóneve az „admin” a „contoso.com” bérlői tartományhoz, a következőt kellene megadnia: **admin@contoso.com**

    3.  Keresse meg a következőt: `$webUrls`, és cserélje le a példában szereplő értékeket a felhasználók OneDrive Vállalati verziójához tartozó webes URL-címre. Annyi bejegyzést adhat hozzá vagy törölhet, amennyit csak szeretne.

        Másik megoldásként nézze meg a parancsfájlhoz tartozó megjegyzéseknél, hogy miként cserélheti le ezt a tömböt egy, az összes konfigurálni kívánt URL-címet tartalmazó .CSV fájlt importálva.  Biztosítottunk egy másik parancsfájlpéldát is, amellyel automatikusan megkeresheti és kinyerheti az URL-címeket a .CSV fájl adatokkal való feltöltéséhez. Ha készen áll erre, nyissa meg a közvetlenül ezeket a lépéseket alatti, [Kiegészítő parancsfájl az összes OneDrive Vállalati verzió URL-címének .CSV fájlba való küldéséhez](#BKMK_Script_OD4B_URLS) című szakaszt.

        A felhasználó OneDrive Vállalati verziójához tartozó URL-cím formátuma a következő: https://*&lt;bérlő neve&gt;*-my.sharepoint.com/personal/*&lt;felhasználónév&gt;*_*&lt;bérlő neve&gt;*_com

        Ha például a contoso bérlő rendelkezik egy „rsimone” nevű felhasználóval, akkor a következőt kellene megadnia: **https://contoso-my.sharepoint.com/personal/rsimone_contoso_com**

    4.  Mivel a parancsfájlt a OneDrive Vállalati verzió konfigurálásához használjuk, ne módosítsa a `$listTitle` változónál a **Documents** (Dokumentumok) értékét.

    5.  Keresés a következőre: `ADMIN INSTRUCTIONS` Ha nem módosítja ezt a szakaszt, a felhasználó OneDrive Vállalati verziója a „Protected Files” (Védett fájlok) házirendnevű és „This policy restricts access to authorized users” (Ez a házirend korlátozza a jogosult felhasználók elérését) leírású IRM-mel lesz konfigurálva.  Más IRM-beállítás nem lesz megadva. Ez a legtöbb környezet esetében megfelelő. Természetesen a javasolt házirendnevet és a leírást módosíthatja, és megadhat még számos, az Ön környezetéhez megfelelő IRM-beállítást is. Ha saját paraméterkészletet szeretne létrehozni a Set-IrmConfiguration parancshoz, tekintse meg a megjegyzésekkel ellátott példát a parancsfájlban.

5.  Mentse a parancsfájlt, majd írja alá. Ha nem írja alá a parancsfájlt (biztonságosabb), a Windows PowerShellt konfigurálni kell a számítógépén a nem aláírt parancsfájlok futtatásához. Ehhez futtasson egy Windows PowerShell-munkamenetet a **Futtatás rendszergazdaként** beállítással, és írja be a következőt: **Set-ExecutionPolicy Unrestricted**. Ez a konfiguráció viszont engedi minden nem aláírt parancsfájl futását (kevésbé biztonságos).

    További információkat a Windows PowerShell-parancsfájlokról a PowerShell dokumentációs könyvtárban talál: [about_Signing](https://technet.microsoft.com/library/hh847874.aspx).

6.  Futtassa a parancsfájlt, és ha a rendszer kéri, adja meg az Office 365-rendszergazdai fiók jelszavát. Ha módosítja a parancsfájlt, és futtatja ugyanabban a Windows PowerShell-munkamenetben, a rendszer nem kér hitelesítő adatokat.

> [!TIP]
> Ezt a parancsfájlt használhatja a SharePoint Online-könyvtárhoz tartozó IRM konfigurálásához is. Ennél a konfigurációnál érdemes engedélyezni **A tartalomvédelmi szolgáltatást nem támogató dokumentumok feltöltésének tiltása** kiegészítő beállítást. Ezzel biztosítható, hogy a könyvtár csak védett dokumentumokat tartalmazzon.    Ehhez adja hozzá az `-IrmReject` paramétert a Set-IrmConfiguration parancshoz a parancsfájlban.
>
> Módosítania kell a `$webUrls` változót (például: **https://contoso.sharepoint.com**) és a `$listTitle` változót (például: **$Reports**) is.

Ha le kell tiltania az IRM-et a felhasználói OneDrive Vállalati verzió könyvtáraihoz, tekintse meg [Az IRM-et letiltó parancsfájl a OneDrive Vállalati verzióhoz](#script-to-disable-irm-for-onedrive-for-business) című szakaszt.

##### Kiegészítő parancsfájl az összes OneDrive Vállalati verzió URL-címének .CSV fájlba való küldéséhez
A fenti 4c lépésnél a következő Windows PowerShell-parancsfájl segítségével nyerheti ki az összes felhasználó OneDrive Vállalati verziójának könyvtárához tartozó URL-címeket. Ezeket aztán ellenőrizheti, szükség esetén szerkesztheti, majd importálhatja a fő parancsfájlba.

Ehhez a parancsfájlhoz szükséges a [SharePoint Online ügyféloldali összetevők SDK-ja](http://www.microsoft.com/en-us/download/details.aspx?id=42038) és a [SharePoint Online felügyeleti rendszerhéj](http://www.microsoft.com/en-us/download/details.aspx?id=35588) is. Ugyanezeket az utasításokat követve másolja, majd illessze be, végül mentse helyben a fájlt (például: „Report-OneDriveForBusinessSiteInfo.ps1”), módosítsa a `$sharepointAdminCenterUrl` és a `$tenantAdmin` értéket a korábbihoz hasonlóan, majd futtassa a parancsfájlt.

*&#42;&#42;Jogi nyilatkozat&#42;&#42;:* Ez a parancsfájlpélda semmilyen standard támogatási program vagy szolgáltatás esetében nem támogatott a Microsoft által. A parancsfájlpéldát „JELEN ÁLLAPOTÁBAN”, bármiféle jótállás vállalása nélkül biztosítjuk.

```
# Requires Windows PowerShell version 3

<#
  Description:

    Queries the search service of an Office 365 tenant to retrieve all OneDrive for Business sites.  
    Details of the discovered sites are written to a .CSV file (by default,"OneDriveForBusinessSiteInfo_<date>.csv").

 Script Installation Requirements:

   SharePoint Online Client Components SDK
   http://www.microsoft.com/en-us/download/details.aspx?id=42038

   SharePoint Online Management Shell
   http://www.microsoft.com/en-us/download/details.aspx?id=35588

======
#>

# URL will be in the format https://<tenant-name>-admin.sharepoint.com
$sharepointAdminCenterUrl = "https://contoso-admin.sharepoint.com"

$tenantAdmin = "admin@contoso.onmicrosoft.com"                           

$reportName = "OneDriveForBusinessSiteInfo_$((Get-Date).ToString("yyyy-MM-dd_hh.mm.ss")).csv"

$oneDriveForBusinessSiteUrls= @()
$resultsProcessed = 0

function Load-SharePointOnlineClientComponentAssemblies
{
    [cmdletbinding()]
    param()

    process
    {
        # assembly location: C:\Program Files\Common Files\microsoft shared\Web Server Extensions\16\ISAPI
        try
        {
            Write-Verbose "Loading Assembly: Microsoft.Office.Client.Policy, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.Office.Client.Policy, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            Write-Verbose "Loading Assembly: Microsoft.Office.Client.TranslationServices, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.Office.Client.TranslationServices, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.DocumentManagement, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.DocumentManagement, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Publishing, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Publishing, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Runtime, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Runtime, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Search.Applications, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Search.Applications, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Search, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Search, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Taxonomy, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Taxonomy, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.UserProfiles, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.UserProfiles, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            return $true
        }
        catch
        {
            if($_.Exception.Message -match "Could not load file or assembly")
            {
                Write-Error -Message "Unable to load the SharePoint Server 2013 Client Components.`nDownload Location: http://www.microsoft.com/en-us/download/details.aspx?id=42038"
            }
            else
            {
                Write-Error -Exception $_.Exception
            }
            return $false
        }
    }
}

function Load-SharePointOnlineModule
{
    [cmdletbinding()]
    param()

    process
    {
        do
        {
            # Installation location: C:\Program Files\SharePoint Online Management Shell\Microsoft.Online.SharePoint.PowerShell
            $spoModule = Get-Module -Name Microsoft.Online.SharePoint.PowerShell -ErrorAction SilentlyContinue

            if(-not $spoModule)
            {
                try
                {
                    Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
                    return $true
                }
                catch
                {
                    if($_.Exception.Message -match "Could not load file or assembly")
                    {
                        Write-Error -Message "Unable to load the SharePoint Online Management Shell.`nDownload Location: http://www.microsoft.com/en-us/download/details.aspx?id=35588"
                    }
                    else
                    {
                        Write-Error -Exception $_.Exception
                    }
                    return $false
                }
            }
            else
            {
                return $true
            }
        }
        while(-not $spoModule)
    }
}

function Get-CredentialFromCredentialCache
{
    [cmdletbinding()]
    param([string]$CredentialName)

    #if( Test-Path variable:\global:CredentialCache )
    if( Get-Variable O365TenantAdminCredentialCache -Scope Global -ErrorAction SilentlyContinue )
    {
        if($global:O365TenantAdminCredentialCache.ContainsKey($CredentialName))
        {
            Write-Verbose "Credential Cache Hit: $CredentialName"
            return $global:O365TenantAdminCredentialCache[$CredentialName]
        }
    }
    Write-Verbose "Credential Cache Miss: $CredentialName"
    return $null
}

function Add-CredentialToCredentialCache
{
    [cmdletbinding()]
    param([System.Management.Automation.PSCredential]$Credential)

    if(-not (Get-Variable CredentialCache -Scope Global -ErrorAction SilentlyContinue))
    {
        Write-Verbose "Initializing the Credential Cache"
        $global:O365TenantAdminCredentialCache = @{}
    }

    Write-Verbose "Adding Credential to the Credential Cache"
    $global:O365TenantAdminCredentialCache[$Credential.UserName] = $Credential
}

# load the required assemblies and Windows PowerShell modules

    if(-not ((Load-SharePointOnlineClientComponentAssemblies) -and (Load-SharePointOnlineModule)) ) { return }

# Add the credentials to the client context and SharePoint Online service connection

    # check for cached credentials to use
    $o365TenantAdminCredential = Get-CredentialFromCredentialCache -CredentialName $tenantAdmin

    if(-not $o365TenantAdminCredential)
    {
        # when credentials are not cached, prompt for the tenant admin credentials
        $o365TenantAdminCredential = Get-Credential -UserName $tenantAdmin -Message "Enter the password for the Office 365 admin"

        if(-not $o365TenantAdminCredential -or -not $o365TenantAdminCredential.UserName -or $o365TenantAdminCredential.Password.Length -eq 0 )
        {
            Write-Error -Message "Could not validate the supplied tenant admin credentials"
            return
        }

        # add the credentials to the cache
        Add-CredentialToCredentialCache -Credential $o365TenantAdminCredential
    }

# establish the client context and set the credentials to connect to the site

    $clientContext = New-Object Microsoft.SharePoint.Client.ClientContext($sharepointAdminCenterUrl)
    $clientContext.Credentials = New-Object Microsoft.SharePoint.Client.SharePointOnlineCredentials($o365TenantAdminCredential.UserName, $o365TenantAdminCredential.Password)

# run a query against the Office 365 tenant search service to retrieve all OneDrive for Business URLs

    do
    {
        # build the query object
        $query = New-Object Microsoft.SharePoint.Client.Search.Query.KeywordQuery($clientContext)
        $query.TrimDuplicates        = $false
        $query.RowLimit              = 500
        $query.QueryText             = "SPSiteUrl:'/personal/' AND contentclass:STS_Site"
        $query.StartRow              = $resultsProcessed
        $query.TotalRowsExactMinimum = 500000

        # run the query
        $searchExecutor = New-Object Microsoft.SharePoint.Client.Search.Query.SearchExecutor($clientContext)
        $queryResults = $searchExecutor.ExecuteQuery($query)
        $clientContext.ExecuteQuery()

        # enumerate the search results and store the site URLs
        $queryResults.Value[0].ResultRows | % {
            $oneDriveForBusinessSiteUrls += $_.Path
            $resultsProcessed++
        }
    }
    while($resultsProcessed -lt $queryResults.Value.TotalRows)

$oneDriveForBusinessSiteUrls | Out-File -FilePath $reportName
```

##### Az IRM-et letiltó parancsfájl a OneDrive Vállalati verzióhoz
Az alábbi parancsfájlmintával szükség esetén letilthatja az IRM-et a felhasználók OneDrive Vállalati verzióján.

Ehhez a parancsfájlhoz szükséges a [SharePoint Online ügyféloldali összetevők SDK-ja](http://www.microsoft.com/en-us/download/details.aspx?id=42038) és a [SharePoint Online felügyeleti rendszerhéj](http://www.microsoft.com/en-us/download/details.aspx?id=35588) is. Másolja ki és illessze be a tartalmakat, mentse a fájlt helyben (például: „Disable-IRMOnOneDriveForBusiness.ps1”), és módosítsa a `$sharepointAdminCenterUrl` és a `$tenantAdmin` értéket. Adja meg manuálisan a OneDrive Vállalati verzió URL-címeit, vagy használja az előző szakaszban bemutatott parancsfájlt az importálásukhoz, majd futtassa a parancsfájlt.

*&#42;&#42;Jogi nyilatkozat&#42;&#42;:* Ez a parancsfájlpélda semmilyen standard támogatási program vagy szolgáltatás esetében nem támogatott a Microsoft által. A parancsfájlpéldát „JELEN ÁLLAPOTÁBAN”, bármiféle jótállás vállalása nélkül biztosítjuk.

```
# Requires Windows PowerShell version 3

<#
  Description:

    Disables IRM for OneDrive for Business and can also be used for SharePoint Online libraries and lists

 Script Installation Requirements:

   SharePoint Online Client Components SDK
   http://www.microsoft.com/en-us/download/details.aspx?id=42038

   SharePoint Online Management Shell
   http://www.microsoft.com/en-us/download/details.aspx?id=35588

======
#>

$sharepointAdminCenterUrl = "https://contoso-admin.sharepoint.com"

$tenantAdmin = "admin@contoso.com"

$webUrls = @("https://contoso-my.sharepoint.com/personal/user1_contoso_com",
             "https://contoso-my.sharepoint.com/personal/user2_contoso_com",
             "https://contoso-my.sharepoint.com/personal/person3_contoso_com")

<# As an alternative to specifying the URLs as an array, you can import them from a CSV file (no header, single value per row).
   Then, use: $webUrls = Get-Content -Path "File_path_and_name.csv"

#>

$listTitle = "Documents"

function Load-SharePointOnlineClientComponentAssemblies
{
    [cmdletbinding()]
    param()

    process
    {
        # assembly location: C:\Program Files\Common Files\microsoft shared\Web Server Extensions\16\ISAPI
        try
        {
            Write-Verbose "Loading Assembly: Microsoft.Office.Client.Policy, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.Office.Client.Policy, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            Write-Verbose "Loading Assembly: Microsoft.Office.Client.TranslationServices, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.Office.Client.TranslationServices, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.DocumentManagement, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.DocumentManagement, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Publishing, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Publishing, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Runtime, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Runtime, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Search.Applications, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Search.Applications, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Search, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Search, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Taxonomy, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Taxonomy, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.UserProfiles, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.UserProfiles, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            return $true
        }
        catch
        {
            if($_.Exception.Message -match "Could not load file or assembly")
            {
                Write-Error -Message "Unable to load the SharePoint Server 2013 Client Components.`nDownload Location: http://www.microsoft.com/en-us/download/details.aspx?id=42038"
            }
            else
            {
                Write-Error -Exception $_.Exception
            }
            return $false
        }
    }
}

function Load-SharePointOnlineModule
{
    [cmdletbinding()]
    param()

    process
    {
        do
        {
            # Installation location: C:\Program Files\SharePoint Online Management Shell\Microsoft.Online.SharePoint.PowerShell
            $spoModule = Get-Module -Name Microsoft.Online.SharePoint.PowerShell -ErrorAction SilentlyContinue

            if(-not $spoModule)
            {
                try
                {
                    Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
                    return $true
                }
                catch
                {
                    if($_.Exception.Message -match "Could not load file or assembly")
                    {
                        Write-Error -Message "Unable to load the SharePoint Online Management Shell.`nDownload Location: http://www.microsoft.com/en-us/download/details.aspx?id=35588"
                    }
                    else
                    {
                        Write-Error -Exception $_.Exception
                    }
                    return $false
                }
            }
            else
            {
                return $true
            }
        }
        while(-not $spoModule)
    }
}

function Remove-IrmConfiguration
{
    [cmdletbinding()]
    param(
        [parameter(Mandatory=$true)][Microsoft.SharePoint.Client.List]$List
    )

    process
    {
        Write-Verbose "Disabling IRM Configuration on '$($List.Title)'"

        $List.IrmEnabled = $false
        $List.IrmExpire  = $false
        $List.IrmReject  = $false
        $List.InformationRightsManagementSettings.Reset()
    }
    end
    {
        if($List)
        {
            Write-Verbose "Committing IRM configuration settings on '$($list.Title)'"
            $list.InformationRightsManagementSettings.Update()
            $list.Update()
            $script:clientContext.Load($list)
            $script:clientContext.ExecuteQuery()
        }
    }
}

function Get-CredentialFromCredentialCache
{
    [cmdletbinding()]
    param([string]$CredentialName)

    #if( Test-Path variable:\global:CredentialCache )
    if( Get-Variable O365TenantAdminCredentialCache -Scope Global -ErrorAction SilentlyContinue )
    {
        if($global:O365TenantAdminCredentialCache.ContainsKey($CredentialName))
        {
            Write-Verbose "Credential Cache Hit: $CredentialName"
            return $global:O365TenantAdminCredentialCache[$CredentialName]
        }
    }
    Write-Verbose "Credential Cache Miss: $CredentialName"
    return $null
}

function Add-CredentialToCredentialCache
{
    [cmdletbinding()]
    param([System.Management.Automation.PSCredential]$Credential)

    if(-not (Get-Variable CredentialCache -Scope Global -ErrorAction SilentlyContinue))
    {
        Write-Verbose "Initializing the Credential Cache"
        $global:O365TenantAdminCredentialCache = @{}
    }

    Write-Verbose "Adding Credential to the Credential Cache"
    $global:O365TenantAdminCredentialCache[$Credential.UserName] = $Credential
}

# load the required assemblies and Windows PowerShell modules

    if(-not ((Load-SharePointOnlineClientComponentAssemblies) -and (Load-SharePointOnlineModule)) ) { return }

# Add the credentials to the client context and SharePoint Online service connection

    # check for cached credentials to use
    $o365TenantAdminCredential = Get-CredentialFromCredentialCache -CredentialName $tenantAdmin

    if(-not $o365TenantAdminCredential)
    {
        # when credentials are not cached, prompt for the tenant admin credentials
        $o365TenantAdminCredential = Get-Credential -UserName $tenantAdmin -Message "Enter the password for the Office 365 admin"

        if(-not $o365TenantAdminCredential -or -not $o365TenantAdminCredential.UserName -or $o365TenantAdminCredential.Password.Length -eq 0 )
        {
            Write-Error -Message "Could not validate the supplied tenant admin credentials"
            return
        }

        # add the credentials to the cache
        Add-CredentialToCredentialCache -Credential $o365TenantAdminCredential
    }

# connect to Office365 first, required for SharePoint Online cmdlets to run

    Connect-SPOService -Url $sharepointAdminCenterUrl -Credential $o365TenantAdminCredential

# enumerate each of the specified site URLs

    foreach($webUrl in $webUrls)
    {
        $grantedSiteCollectionAdmin = $false

        try
        {
            # establish the client context and set the credentials to connect to the site
            $script:clientContext = New-Object Microsoft.SharePoint.Client.ClientContext($webUrl)
            $script:clientContext.Credentials = New-Object Microsoft.SharePoint.Client.SharePointOnlineCredentials($o365TenantAdminCredential.UserName, $o365TenantAdminCredential.Password)

            # initialize the site and web context
            $script:clientContext.Load($script:clientContext.Site)
            $script:clientContext.Load($script:clientContext.Web)
            $script:clientContext.ExecuteQuery()

            # load and ensure the tenant admin user account if present on the target SharePoint site
            $tenantAdminUser = $script:clientContext.Web.EnsureUser($o365TenantAdminCredential.UserName)
            $script:clientContext.Load($tenantAdminUser)
            $script:clientContext.ExecuteQuery()

            # check if the tenant admin is a site admin
            if( -not $tenantAdminUser.IsSiteAdmin )
            {
                try
                {
                    # grant the tenant admin temporary admin rights to the site collection
                    Set-SPOUser -Site $script:clientContext.Site.Url -LoginName $o365TenantAdminCredential.UserName -IsSiteCollectionAdmin $true | Out-Null
                    $grantedSiteCollectionAdmin = $true
                }
                catch
                {
                    Write-Error $_.Exception
                    return
                }
            }

            try
            {
                # load the list orlibrary using CSOM

                $list = $null
                $list = $script:clientContext.Web.Lists.GetByTitle($listTitle)
                $script:clientContext.Load($list)
                $script:clientContext.ExecuteQuery()

               Remove-IrmConfiguration -List $list                 
            }
            catch
            {
                Write-Error -Message "Error setting IRM configuration on site: $webUrl.`nError Details: $($_.Exception.ToString())"
            }
       }
       finally
       {
            if($grantedSiteCollectionAdmin)
            {
                # remove the temporary admin rights to the site collection
                Set-SPOUser -Site $script:clientContext.Site.Url -LoginName $o365TenantAdminCredential.UserName -IsSiteCollectionAdmin $false | Out-Null
            }
       }
    }

Disconnect-SPOService -ErrorAction SilentlyContinue
```




<!--HONumber=Jun16_HO4-->


