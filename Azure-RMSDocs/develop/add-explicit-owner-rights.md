---
# required metadata

title: Explicit tulajdonosi jogosultságok hozzáadása | Azure RMS
description: Az alkalmazásnak kifejezetten hozzá kellene adnia a „Tulajdonos” jogosultságokat egy teljesen új licenc létrehozásakor.
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: EF43FAC4-ABB4-459D-B173-972B5716F816
# optional metadata

#ROBOTS:
audience: developer
#ms.devlang:
ms.reviewer: shubhamp
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Add explicit owner rights (Explicit tulajdonosi jogosultságok hozzáadása)

Az alkalmazásnak kifejezetten hozzá kellene adnia a „Tulajdonos” jogosultságokat egy teljesen új licenc létrehozásakor ([**IpcCreateLicenseFromScratch**](/rights-management/sdk/2.1/api/win/functions#msipc_ipccreatelicensefromscratch)).

## Előfeltételek

Ha az alkalmazás az [**IpcCreateLicenseFromScratch**](/rights-management/sdk/2.1/api/win/functions#msipc_ipccreatelicensefromscratch) segítségével hoz létre egy licencleírót, teljes körű engedélyeket is kifejezetten biztosítania kell a tulajdonosnak.

**Megjegyzés**  Egy felhasználó „tulajdonosként” való beállítása az [**IpcSetLicenseProperty**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcsetlicenseproperty) segítségével az **IPC\_LI\_OWNER** tulajdonsággal nem biztosít a tulajdonos számára teljes körű engedélyeket.

 
## Forgatókönyv – jogosultságok hozzárendelése egy licenchez

Ebben a C++ példában a szükséges jogosultságokat a rendszer hozzáadja az [**IpcCreateLicenseFromScratch**](/rights-management/sdk/2.1/api/win/functions#msipc_ipccreatelicensefromscratch) paranccsal létrehozott licenchez. A példa egy jogosultságlistán keresztül mutatja be a jogosultságok létrehozását és egy licenchez való hozzárendelését.

Ezekhez a felhasználókhoz a következő két jogosultság lesz hozzárendelve:

-   *Olvasási* engedélyek hozzárendelve a joe@contoso.com-hoz
-   *Teljes körű* engedélyek hozzárendelve a mary\_kay@contoso.com-hoz

**MEGJEGYZÉS** – Ez a kódpélda csak adott jogosultságok létrehozása és egy adott licenchez való hozzáadása során szükséges lépéseket mutatja be.

    // Create User Rights structure
    IPC_USER_RIGHTS ownerRightForOwner = {0};

    // Create rights
    LPCWSTR rgwszOwnerRights[1] = {IPC_GENERIC_ALL};

    // Assign values to members of Rights structure
    ownerRightForOwner.User.dwType = IPC_USER_TYPE_IPC;
    ownerRightForOwner.User.wszID = IPC_USER_ID_OWNER;
    ownerRightForOwner.rgwszRights = rgwszOwnerRights;
    ownerRightForOwner.cRights = 1;

    // Create User Rights structure for Joe with Read permissions
    IPC_USER_RIGHTS joeReadRight = {0};
    LPCWSTR rgwszReadRights[1] = {IPC_GENERIC_READ};

    // Assign values to members of Rights structure for Joe
    joeReadRight.User.dwType = IPC_USER_TYPE_EMAIL;
    joeReadRight.User.wszID = "joe@contoso.com";
    joeReadRight.rgwszRights = rgwszReadRights;
    joeReadRight.cRights = 1;

    // Create User Rights structure for Mary Kay with Full permissions
    IPC_USER_RIGHTS mary_kayFullRight = {0};
    LPCWSTR rgwszFullRights[1] = {IPC_GENERIC_ALL};

    // Assign values to members of Rights structure for Mary Kay
    mary_kayFullRight.User.dwType = IPC_USER_TYPE_EMAIL;
    mary_kayFullRight.User.wszID = L"mary_kay@contoso.com";
    mary_kayFullRight.rgwszRights = rgwszFullRights;
    mary_kayFullRight.cRights = 1;

    // Create User Rights List and assign the above rights
    size_t uNoOfUserRights = 3;
    PIPC_USER_RIGHTS_LIST pUserRightsList = NULL;
    pUserRightsList = reinterpret_cast<PIPC_USER_RIGHTS_LIST>
    (new BYTE[ sizeof(IPC_USER_RIGHTS_LIST) + uNoOfUserRights * sizeof(IPC_USER_RIGHTS)]);

    if(pUserRightsList == NULL)
    {
      // Handle error
    }

    // Assign values to members of Rights List structure for Joe and Mary Kay
    (*pUserRightsList).cbSize = sizeof(IPC_USER_RIGHTS_LIST);
    (*pUserRightsList).cUserRights = uNoOfUserRights;
    (*pUserRightsList).rgUserRights[0] = ownerRightForOwner;
    (*pUserRightsList).rgUserRights[1] = joeReadRight;
    (*pUserRightsList).rgUserRights[2] = mary_kayFullRight;

    // Set the Rights List property on the license via its handle
    // hLicense is a license handle created with IpcCreateLicenseFromScratch
    hr = IpcSetLicenseProperty(hLicense, FALSE, IPC_LI_USER_RIGHTS_LIST, pUserRightsList);

    if(FAILED(hr))
    {
      // Handle the error
    }



## Kapcsolódó témakörök

* [Megjegyzések fejlesztők számára](developer-notes.md)
* [**IpcCreateLicenseFromScratch**](/rights-management/sdk/2.1/api/win/functions#msipc_ipccreatelicensefromscratch)
* [**IpcSetLicenseProperty**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcsetlicenseproperty)
 

 


<!--HONumber=Apr16_HO4-->


