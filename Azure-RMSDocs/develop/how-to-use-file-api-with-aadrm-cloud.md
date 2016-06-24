---
# required metadata

title: A szolgáltatásalkalmazás alkalmassá tétele a felhőalapú RMS használatára | Azure RMS
description: Ez a témakör a szolgáltatásalkalmazás Azure Rights Management használatához végzett beállításának lépéseit ismerteti.
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: EA1457D1-282F-4CF3-A23C-46793D2C2F32
# optional metadata

#ROBOTS:
audience: developer
#ms.devlang:
ms.reviewer: shubhamp
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Útmutató: A szolgáltatásalkalmazás alkalmassá tétele a felhőalapú RMS használatára

Ez a témakör a szolgáltatásalkalmazásnak az Azure Rights Management használatához végzett beállításának lépéseit ismerteti. További információ: [Ismerkedés az Azure Rights Management szolgáltatással](https://technet.microsoft.com/en-us/library/jj585016.aspx).

**Fontos**  
A Rights Management Services SDK 2.1 segítségével készített szolgáltatásalkalmazásának az Azure RMS-sel történő használatához saját bérlőt kell létrehoznia. További információért lásd: [Azure RMS-követelmények: Az Azure RMS-t támogató felhőalapú előfizetések](/rights-management/get-started/requirements-subscriptions.md).

## Előfeltételek

-   Telepíteni és konfigurálni kell az RMS SDK 2.1 eszközt. További információkért lásd: [Getting started with RMS SDK 2.1](getting-started-with-ad-rms-2-0.md) (Ismerkedés az RMS SDK 2.1 szolgáltatással).
-   [Létre kell hoznia egy szolgáltatásidentitást az ACS-en keresztül](https://msdn.microsoft.com/en-us/library/gg185924.aspx) a szimmetrikus kulcs lehetőséggel vagy más módszerrel, és rögzítenie kell ezen folyamat kulcsinformációit.

## Csatlakozás az Azure Rights Management szolgáltatáshoz

-   Hívja meg az [**IpcInitialize**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcinitialize) függvényt.
-   Állítsa be az [**IpcSetGlobalProperty**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcsetglobalproperty) függvényt.

        C++
        int mode = IPC_API_MODE_SERVER;
        IpcSetGlobalProperty(IPC_EI_API_MODE, &(mode));


  **Megjegyzés** További információkért lásd: [Setting the API security mode](setting-the-api-security-mode-api-mode.md) (Az API biztonsági módjának beállítása).

     
-   A következő lépésekkel beállíthatja az [**IPC\_PROMPT\_CTX**](/rights-management/sdk/2.1/api/win/ipc_prompt_ctx#msipc_ipc_prompt_ctx) struktúra példányát az Azure Rights Management Service csatlakozási adataival kitöltött **pcCredential** ([**IPC\_CREDENTIAL**](/rights-management/sdk/2.1/api/win/ipc_credential#msipc_ipc_credential)) tag használatával.
-   A szimmetrikus kulcs szolgáltatásidentitás létrehozásának információival (lásd a témakör korábbi szakaszában lévő előfeltételeket) állítsa be a **wszServicePrincipal**, **wszBposTenantId** és **cbKey** paramétereket az [**IPC\_CREDENTIAL\_SYMMETRIC\_KEY**](/rights-management/sdk/2.1/api/win/ipc_credential#msipc_ipc_credential_symmetric_key) struktúra példányának létrehozásakor.

**Megjegyzés:** Az észlelési szolgáltatás jelenlegi feltételei miatt Észak-Amerikán kívül a szimmetrikus kulcs hitelesítő adatai nem fogadhatók el más régiókból, így közvetlenül kell megadnia a bérlői URL-címeket. Ezt az [**IpcGetTemplateList**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcgettemplatelist) vagy az [**IpcGetTemplateIssuerList**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcgettemplateissuerlist) [**IPC\_CONNECTION\_INFO**](/rights-management/sdk/2.1/api/win/ipc_connection_info#msipc_ipc_connection_info) paraméterével teheti meg.

## Szimmetrikus kulcs létrehozása és a szükséges információk begyűjtése

### Szimmetrikus kulcs létrehozásának utasításai

-   Telepítse a [Microsoft Online Services bejelentkezési segédet](http://go.microsoft.com/fwlink/p/?LinkID=286152)
-   Telepítse az [Azure AD Powershell-modult](https://bposast.vo.msecnd.net/MSOPMW/8073.4/amd64/AdministrationConfig-en.msi).

**Megjegyzés** Bérlői rendszergazdának kell lennie a PowerShell-parancsmagok használatához.

-   Indítsa el a PowerShellt, és generáljon kulcsot a következő parancsok futtatásával:         `Import-Module MSOnline`
            `Connect-MsolService` (írja be a rendszergazdai hitelesítő adatait)         `New-MsolServicePrincipal` (írjon be egy megjelenített nevet)
-   Miután létrehoz egy szimmetrikus kulcsot, a parancsmag kiadja a kulccsal kapcsolatos információkat, beleértve magát a kulcsot és az **AppPrincipalId** azonosítót.


    Megadott kulcs hiányában az alábbi szimmetrikus kulcs lett létrehozva ZYbF/lTtwE28qplQofCpi2syWd11D83+A3DRlb2Jnv8=

    DisplayName : RMSTestApp ServicePrincipalNames : {7d9c1f38-600c-4b4d-8249-22427f016963} ObjectId : 0ee53770-ec86-409e-8939-6d8239880518 AppPrincipalId : 7d9c1f38-600c-4b4d-8249-22427f016963


### A **TenantBposId** és az **Urls** megtekintésének utasításai

-   Telepítse az [Azure RMS Powershell-modult](https://technet.microsoft.com/en-us/library/jj585012.aspx).
-   Indítsa el a Powershellt, és futtassa a következő parancsokat a bérlő RMS-konfigurációjának lekéréséhez.

    `Import-Module aadrm`

    `Connect-AadrmService` (írja be a rendszergazdai hitelesítő adatait)

    `Get-AadrmConfiguration`


-   Hozza létre az [**IPC\_CREDENTIAL\_SYMMETRIC\_KEY**](/rights-management/sdk/2.1/api/win/ipc_credential#msipc_ipc_credential_symmetric_key) példányát, és állítson be néhány tagot.

    // Hozzon létre egy kulcsstruktúrát.
    IPC_CREDENTIAL_SYMMETRIC_KEY symKey = {0};

    // Állítsa be mindegyik tagot a szolgáltatás létrehozásának információival.
    symKey.wszBase64Key = "a szolgáltatás egyszerű nevének kulcsa"; symKey.wszAppPrincipalId = "az alkalmazás egyszerű nevének azonosítója"; symKey.wszBposTenantId = "a bérlő azonosítója";


További információ: [**IPC\_CREDENTIAL\_SYMMETRIC\_KEY**](/rights-management/sdk/2.1/api/win/ipc_credential#msipc_ipc_credential_symmetric_key).

-   Hozza létre az [**IPC\_CREDENTIAL\_SYMMETRIC\_KEY**](/rights-management/sdk/2.1/api/win/ipc_credential#msipc_ipc_credential_symmetric_key) példányt tartalmazó [**IPC\_CREDENTIAL**](/rights-management/sdk/2.1/api/win/ipc_credential#msipc_ipc_credential) struktúra példányát.

**Megjegyzés:** A *connectionInfo* tagok a `Get-AadrmConfiguration` előző hívásából származó URL-ekkel vannak beállítva, és itt láthatók ezekkel a mezőnevekkel.

    // Create a credential structure.
    IPC_CREDENTIAL cred = {0};

    IPC_CONNECTION_INFO connectionInfo = {0};
    connectionInfo.wszIntranetUrl = LicensingIntranetDistributionPointUrl;
    connectionInfo.wszExtranetUrl = LicensingExtranetDistributionPointUrl;

    // Set each member.
    cred.dwType = IPC_CREDENTIAL_TYPE_SYMMETRIC_KEY;
    cred.pcCertContext = (PCCERT_CONTEXT)&symKey;

    // Create your prompt control.
    IPC_PROMPT_CTX promptCtx = {0};

    // Set each member.
    promptCtx.cbSize = sizeof(IPC_PROMPT_CTX);
    promptCtx.hwndParent = NULL;
    promptCtx.dwflags = IPC_PROMPT_FLAG_SILENT;
    promptCtx.hCancelEvent = NULL;
    promptCtx.pcCredential = &cred;

### Sablon azonosítása, majd titkosítása

-   Válassza ki a titkosításhoz használni kívánt sablont.
    Hívja meg az [**IpcGetTemplateList**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcgettemplatelist) függvényt az [**IPC\_PROMPT\_CTX**](/rights-management/sdk/2.1/api/win/ipc_prompt_ctx#msipc_ipc_prompt_ctx) ugyanezen példányában.


    PCIPC_TIL pTemplates = NULL; IPC_TEMPLATE_ISSUER templateIssuer = (pTemplateIssuerList->aTi)[0];

    hr = IpcGetTemplateList(&(templateIssuer.connectionInfo),        IPC_GTL_FLAG_FORCE_DOWNLOAD,        0,        &promptCtx,        NULL,        &pTemplates);


-   A témakörben korábban használt sablonnal hívja meg az [**IpcfEncrcyptFile**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcfencryptfile) függvényt az [**IPC\_PROMPT\_CTX**](/rights-management/sdk/2.1/api/win/ipc_prompt_ctx#msipc_ipc_prompt_ctx) ugyanezen példányában.

Példa az [**IpcfEncrcyptFile**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcfencryptfile) használatára:

    LPCWSTR wszContentTemplateId = pTemplates->aTi[0].wszID;
    hr = IpcfEncryptFile(wszInputFilePath,
           wszContentTemplateId,
           IPCF_EF_TEMPLATE_ID,
           IPC_EF_FLAG_KEY_NO_PERSIST,
           &promptCtx,
           NULL,
           &wszOutputFilePath);

Példa az [**IpcfDecryptFile**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcfdecryptfile) használatára:

    hr = IpcfDecryptFile(wszInputFilePath,
           IPCF_DF_FLAG_DEFAULT,
           &promptCtx,
           NULL,
           &wszOutputFilePath);

Most elvégezte azon lépéseket, amelyekkel az alkalmazás használhatja az Azure Rights Management eszközt.

## Kapcsolódó témakörök

* [Ismerkedés az Azure Rights Management szolgáltatással](https://technet.microsoft.com/en-us/library/jj585016.aspx)
* [Getting started with RMS SDK 2.1 (Ismerkedés az RMS SDK 2.1 szolgáltatással)](getting-started-with-ad-rms-2-0.md)
* [Szolgáltatásidentitás létrehozása ACS-n keresztül](https://msdn.microsoft.com/en-us/library/gg185924.aspx)
* [**IpcSetGlobalProperty**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcsetglobalproperty)
* [**IpcInitialize**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcinitialize)
* [**IPC\_PROMPT\_CTX**](/rights-management/sdk/2.1/api/win/ipc_prompt_ctx#msipc_ipc_prompt_ctx)
* [**IPC\_CREDENTIAL**](/rights-management/sdk/2.1/api/win/ipc_credential#msipc_ipc_credential)
* [**IPC\_CREDENTIAL\_SYMMETRIC\_KEY**](/rights-management/sdk/2.1/api/win/ipc_credential#msipc_ipc_credential_symmetric_key)
* [**IpcGetTemplateIssuerList**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcgettemplateissuerlist)
* [**IpcGetTemplateList**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcgettemplatelist)
* [**IpcfDecryptFile**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcfdecryptfile)
* [**IpcfEncrcyptFile**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcfencryptfile)
* [**IpcCreateLicenseFromScratch**](/rights-management/sdk/2.1/api/win/functions#msipc_ipccreatelicensefromscratch)
* [**IpcCreateLicenseFromTemplateID**](/rights-management/sdk/2.1/api/win/functions#msipc_ipccreatelicensefromtemplateid)
 

 


<!--HONumber=Jun16_HO2-->


