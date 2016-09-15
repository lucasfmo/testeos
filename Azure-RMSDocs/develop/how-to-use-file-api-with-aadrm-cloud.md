---
title: "Jak umożliwiać współpracę aplikacji usługi z usługą RMS opartą na chmurze | Azure RMS"
description: "W tym temacie opisano kroki konfigurowania aplikacji usługi do korzystania z usługi Azure Rights Management."
keywords: 
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: EA1457D1-282F-4CF3-A23C-46793D2C2F32
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 79397c82d9478cbd55630a376fe2d12f3873ebc4
ms.openlocfilehash: fce408a8c7a1114375745c3783443b87cd80ba78


---

# Instrukcje: umożliwianie współdziałania aplikacji usługi z usługą RMS opartą na chmurze

W tym temacie opisano kroki konfigurowania aplikacji usługi do korzystania z usługi Azure Rights Management. Aby uzyskać więcej informacji, zobacz [Rozpoczynanie pracy z usługą Azure Rights Management](https://technet.microsoft.com/library/jj585016.aspx).

**Ważne**  
Aby móc użyć aplikacji usługi zestawu Rights Management Services SDK 2.1 z usługą Azure RMS, musisz utworzyć własne dzierżawy. Aby uzyskać więcej informacji, zobacz [Wymagania dotyczące usługi Azure RMS: subskrypcje usług w chmurze, które obsługują usługę Azure RMS](../get-started/requirements-subscriptions.md)

## Wymagania wstępne

-   Należy zainstalować i skonfigurować zestaw SDK usług RMS 2.1. Aby uzyskać więcej informacji, zobacz [Rozpoczynanie pracy z zestawem SDK usług RMS 2.1](getting-started-with-ad-rms-2-0.md).
-   Musisz [utworzyć tożsamość usługi przez ACS](https://msdn.microsoft.com/en-us/library/gg185924.aspx) przy użyciu opcji klucza symetrycznego lub innej metody oraz zarejestrować dane klucza z tego procesu.

## Łączenie z usługą Azure Rights Management

-   Wywołaj metodę [**IpcInitialize**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcinitialize).
-   Ustaw właściwość [**IpcSetGlobalProperty**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcsetglobalproperty).

        C++
        int mode = IPC_API_MODE_SERVER;
        IpcSetGlobalProperty(IPC_EI_API_MODE, &(mode));


  **Uwaga** Aby uzyskać więcej informacji, zobacz [Ustawianie trybu zabezpieczeń interfejsu API](setting-the-api-security-mode-api-mode.md)

     
-   Poniższe kroki to etapy konfiguracji tworzenia wystąpienia struktury [**IPC\_PROMPT\_CTX**](/rights-management/sdk/2.1/api/win/ipc_prompt_ctx#msipc_ipc_prompt_ctx) z elementem **pcCredential** ([**IPC\_CREDENTIAL**](/rights-management/sdk/2.1/api/win/ipc_credential#msipc_ipc_credential)) wypełnionym informacjami na temat połączenia z usługą Azure Rights Management.
-   Użyj informacji z procedury tworzenia tożsamości usługi klucza symetrycznego (zobacz wymagania wstępne wymienione we wcześniejszej części tego tematu), aby ustawić parametry **wszServicePrincipal**, **wszBposTenantId** i **cbKey** podczas tworzenia wystąpienia struktury [**IPC\_CREDENTIAL\_SYMMETRIC\_KEY**](/rights-management/sdk/2.1/api/win/ipc_credential_symmetric_key#msipc_ipc_credential_symmetric_key).

**Uwaga** Ze względu na stan naszej usługi odnajdywania, jeśli nie znajdujesz się w Ameryce Północnej, nie są akceptowane poświadczenia kluczy symetrycznych z innych regionów, w związku z czym należy bezpośrednio określić adresy URL dzierżawy. Można to zrobić przy użyciu parametru [**IPC\_CONNECTION\_INFO**](/rights-management/sdk/2.1/api/win/ipc_connection_info#msipc_ipc_connection_info) elementu [**IpcGetTemplateList**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcgettemplatelist) lub [**IpcGetTemplateIssuerList**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcgettemplateissuerlist).

## Generowanie klucza symetrycznego i zbieranie potrzebnych informacji

### Instrukcje generowania klucza symetrycznego

-   Zainstaluj [Asystenta logowania w witrynie Microsoft Online Services](http://go.microsoft.com/fwlink/p/?LinkID=286152)
-   Zainstaluj [moduł PowerShell usługi Azure AD](https://bposast.vo.msecnd.net/MSOPMW/8073.4/amd64/AdministrationConfig-en.msi).

**Uwaga** Tylko administrator dzierżawy może korzystać z poleceń cmdlet modułu Powershell.

-   Uruchom program Powershell i uruchom następujące polecenia, aby wygenerować klucz         `Import-Module MSOnline`
            `Connect-MsolService` (wpisz swoje poświadczenia administratora)         `New-MsolServicePrincipal` (wpisz nazwę wyświetlaną).
-   Po wygenerowaniu klucza symetrycznego wyświetlane są informacje na temat klucza, w tym sam klucz i element **AppPrincipalId**.


    Następujący klucz symetryczny został utworzony, ponieważ odpowiedni klucz nie został podany, ZYbF/lTtwE28qplQofCpi2syWd11D83+A3DRlb2Jnv8=

    DisplayName : RMSTestApp ServicePrincipalNames : {7d9c1f38-600c-4b4d-8249-22427f016963} ObjectId : 0ee53770-ec86-409e-8939-6d8239880518 AppPrincipalId : 7d9c1f38-600c-4b4d-8249-22427f016963


### Instrukcje określania wartości **TenantBposId** i **Urls**

-   Zainstaluj [moduł PowerShell usługi Azure RMS](https://technet.microsoft.com/en-us/library/jj585012.aspx).
-   Uruchom program Powershell i uruchom następujące polecenia, aby uzyskać konfigurację usługi RMS dzierżawy.

    `Import-Module aadrm`

    `Connect-AadrmService` (wpisz swoje poświadczenia administratora)

    `Get-AadrmConfiguration`


-   Utwórz wystąpienie struktury [**IPC\_CREDENTIAL\_SYMMETRIC\_KEY**](/rights-management/sdk/2.1/api/win/ipc_credential_symmetric_key#msipc_ipc_credential_symmetric_key) i ustaw kilku członków.

    // Utwórz strukturę klucza.
    IPC_CREDENTIAL_SYMMETRIC_KEY symKey = {0};

    // Skonfiguruj każdy element członkowski przy użyciu informacji z tworzenia usługi.
    symKey.wszBase64Key = "klucz główny usługi"; symKey.wszAppPrincipalId = "identyfikator główny aplikacji"; symKey.wszBposTenantId = "identyfikator dzierżawy";


Aby uzyskać więcej informacji, zobacz [**IPC\_CREDENTIAL\_SYMMETRIC\_KEY**](/rights-management/sdk/2.1/api/win/ipc_credential_symmetric_key#msipc_ipc_credential_symmetric_key).

-   Utwórz wystąpienie struktury [**IPC\_CREDENTIAL**](/rights-management/sdk/2.1/api/win/ipc_credential#msipc_ipc_credential) zawierające wystąpienie [**IPC\_CREDENTIAL\_SYMMETRIC\_KEY**](/rights-management/sdk/2.1/api/win/ipc_credential_symmetric_key#msipc_ipc_credential_symmetric_key).

**Uwaga** Elementy członkowskie *connectionInfo* są konfigurowane przy użyciu adresów URL z poprzedniego wywołania elementu `Get-AadrmConfiguration` i oznaczane w tym miejscu przy użyciu tych nazw pól.

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

### Zidentyfikuj szablon i zaszyfruj go

-   Wybierz szablon do użycia dla szyfrowania.
    Wywołaj element [**IpcGetTemplateList**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcgettemplatelist), przekazując to samo wystąpienie elementu [**IPC\_PROMPT\_CTX**](/rights-management/sdk/2.1/api/win/ipc_prompt_ctx#msipc_ipc_prompt_ctx).


    PCIPC_TIL pTemplates = NULL; IPC_TEMPLATE_ISSUER templateIssuer = (pTemplateIssuerList->aTi)[0];

    hr = IpcGetTemplateList(&(templateIssuer.connectionInfo),        IPC_GTL_FLAG_FORCE_DOWNLOAD,        0,        &promptCtx,        NULL,        &pTemplates);


-   Przy użyciu szablonu z wcześniejszej części tego tematu wywołaj element [**IpcfEncrcyptFile**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcfencryptfile), przekazując to samo wystąpienie elementu [**IPC\_PROMPT\_CTX**](/rights-management/sdk/2.1/api/win/ipc_prompt_ctx#msipc_ipc_prompt_ctx).

Przykładowe zastosowanie wywołania elementu [**IpcfEncrcyptFile**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcfencryptfile):

    LPCWSTR wszContentTemplateId = pTemplates->aTi[0].wszID;
    hr = IpcfEncryptFile(wszInputFilePath,
           wszContentTemplateId,
           IPCF_EF_TEMPLATE_ID,
           IPC_EF_FLAG_KEY_NO_PERSIST,
           &promptCtx,
           NULL,
           &wszOutputFilePath);

Przykładowe zastosowanie wywołania elementu [**IpcfDecryptFile**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcfdecryptfile):

    hr = IpcfDecryptFile(wszInputFilePath,
           IPCF_DF_FLAG_DEFAULT,
           &promptCtx,
           NULL,
           &wszOutputFilePath);

Ukończono kroki niezbędne do włączenia obsługi usługi Azure Rights Management przez aplikację.

## Tematy pokrewne

* [Rozpoczynanie pracy z usługą Azure Rights Management](https://technet.microsoft.com/en-us/library/jj585016.aspx)
* [Rozpoczynanie pracy z zestawem SDK 2.1 usługi RMS](getting-started-with-ad-rms-2-0.md)
* [Tworzenie tożsamości usługi za pośrednictwem usługi ACS](https://msdn.microsoft.com/en-us/library/gg185924.aspx)
* [**IpcSetGlobalProperty**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcsetglobalproperty)
* [**IpcInitialize**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcinitialize)
* [**IPC\_PROMPT\_CTX**](/rights-management/sdk/2.1/api/win/ipc_prompt_ctx#msipc_ipc_prompt_ctx)
* [**IPC\_CREDENTIAL**](/rights-management/sdk/2.1/api/win/ipc_credential#msipc_ipc_credential)
* [**IPC\_CREDENTIAL\_SYMMETRIC\_KEY**](/rights-management/sdk/2.1/api/win/ipc_credential_symmetric_key#msipc_ipc_credential_symmetric_key)
* [**IpcGetTemplateIssuerList**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcgettemplateissuerlist)
* [**IpcGetTemplateList**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcgettemplatelist)
* [**IpcfDecryptFile**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcfdecryptfile)
* [**IpcfEncrcyptFile**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcfencryptfile)
* [**IpcCreateLicenseFromScratch**](/rights-management/sdk/2.1/api/win/functions#msipc_ipccreatelicensefromscratch)
* [**IpcCreateLicenseFromTemplateID**](/rights-management/sdk/2.1/api/win/functions#msipc_ipccreatelicensefromtemplateid)
 

 



<!--HONumber=Jul16_HO4-->


