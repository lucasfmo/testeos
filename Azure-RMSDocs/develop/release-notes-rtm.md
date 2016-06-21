---
# required metadata

title: Kibocsátási megjegyzések | Azure RMS
description:
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 05/03/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: CE379738-4E1D-42AD-83F4-F89B70456EBB
# optional metadata

#ROBOTS:
audience: developer
#ms.devlang:
ms.reviewer: shubhamp
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Kibocsátási megjegyzések

Ez a témakör fontos információkat tartalmaz az RMS SDK 2.1 jelenlegi és korábbi kiadásaival kapcsolatban.

## 2016. februári újdonság – SDK-dokumentáció frissítése

>[!Note]  A szolgáltatásdokumentációnak a jelen szakaszban található frissítései a 2015. december 11-i SDK-letöltésre vonatkoznak.

- **Továbbfejlesztett hitelesítési folyamat** – az OAuth2 tokenalapú hitelesítés használata az [Azure Active Directory Authentication Library (ADAL)](https://azure.microsoft.com/en-us/documentation/articles/active-directory-authentication-libraries/) hitelesítési táron keresztül. További információ a folyamattal és annak API-bővítményeivel kapcsolatban: [ADAL-hitelesítés RMS-kompatibilis alkalmazásokhoz](how-to-use-adal-authentication.md).

- **Frissítés az ADAL-ra** – Az alkalmazásnak a Microsoft Online bejelentkezési segéd helyett az ADAL-hitelesítés használatára való frissítésével Ön és ügyfelei az alábbiakra lesznek képesek:

 - Többtényezős hitelesítés használata.
 - Az RMS 2.1 ügyfél telepítése rendszergazdai jogosultságok nélkül a számítógépen.
 - Az alkalmazás tanúsítása a Windows 10-re.

- **Az RMS SDK a továbbiakban nem támogatja a Microsoft Online bejelentkezési segédet (SIA).** Az SIA számára 6 hónapig nyújtunk támogatást, utána azonban nem részesül támogatásban.


## 2015. decemberi frissítés

- Teljesítménnyel kapcsolatos fejlesztések történtek számos területen, például:
    - Közzététel az elsődleges licenckiszolgálóról csak licenccel használható kiszolgálók esetén.
    - Az RMS SDK 2.1 gyorsabban jelez hibát, ha nincs hálózati kapcsolat.

- Számos, a hibaüzenetekkel és a hibaelhárítással kapcsolatos élményt javító frissítés.
- Vegye figyelembe, hogy a [Supported platforms](supported-platforms.md) (Támogatott platformok) című témakörben ismertetett platformlista is frissítve lett.
- Az RMS SDK 2.1 már nem követeli meg üzem előtti környezet, illetve alkalmazásjegyzékek használatát. A fejlesztői dokumentációból töröltük ezeket a szakaszokat, és a teljes dokumentációt leegyszerűsítettük és átszerveztük.

## 2015. májusi frissítés

-   **Szolgáltatásalkalmazások és felhőalapú RMS** - [Az **IPC\_CREDENTIAL\_SYMMETRIC\_KEY**](/rights-management/sdk/2.1/api/win/ipc_credential#msipc_ipc_credential_symmetric_key) három információt igényel: szimmetrikus kulcs, **AppPrincipalId** és a **TenantBposId**. Az erre vonatkozó témakör frissítve lett, hogy útmutatást biztosítson a szükséges információ beszerzésének feldolgozásáról. A frissítéssel kapcsolatban tekintse meg az [Enable your service application to work with cloud based RMS](how-to-use-file-api-with-aadrm-cloud.md) (A szolgáltatásalkalmazás alkalmassá tétele a felhőalapú RMS használatára) című témakör frissített verzióját.

## 2015. áprilisi frissítés

-   A **dokumentumok nyomon követését** új API felületek biztosítják. További információ: [Tracking Content](tracking-content.md) (Tartalom nyomon követése).
-   **Titkosítási típus** – Mostantól támogatjuk a titkosítási csomag kiválasztásának API-szintű vezérlését. További információ: [Working with encryption](working-with-encryption.md) (A titkosítás használata).

    **Megjegyzés:** Az **IPC\_LI\_DEPRECATED\_ENCRYPTION\_ALGORITHMS** jelzőt a továbbiakban nem tesszük közzé az API felületen. Ez azt jelenti, hogy a jövőben az erre a jelzőre hivatkozó alkalmazások lefordítása nem fog megtörténni. A már létrehozott alkalmazások azonban továbbra is működnek majd, mivel a jelzőt rejtve megőrizzük az API-kódban. A régi, elavult titkosítási algoritmus jelzőjének előnyei továbbra is kihasználhatóak egy jelző egyszerű módosításával. További információ: [Working with encryption](working-with-encryption.md) (A titkosítás használata).

-   Azon **kiszolgáló módhoz készült alkalmazások**, amelyek az **IPC\_API\_MODE\_SERVER** [**API-mód értékét**](/rights-management/sdk/2.1/api/win/api%20mode%20values#msipc_api_mode_values_IPC_API_MODE_SERVER) használják, a továbbiakban nem igényelnek alkalmazásjegyzéket. Az alkalmazást tesztelheti éles RMS-kiszolgálón, és nem kell éles licencet beszereznie éles környezetbe történő váltáskor. További információ a kiszolgáló módhoz készült alkalmazásokkal kapcsolatban: [Application types](application-types.md) (Alkalmazástípusok).
-   A **naplózás** mostantól a Windows-metódusok fájl- és az eseménykövetése esetén is használható.
-   Ha **Windows 7 SP1 vagy Windows Server 2008 R2 rendszerű számítógépet** használ, olvassa el az alábbi, „Fontos megjegyzések fejlesztők számára” című szakaszban található megjegyzést.

## 2015. januári frissítés

-   **Nagyobb méretű védett fájlok (pfile) támogatása** – Mostantól az egy gigabájtnál (1 GB) nagyobb méretű védett fájlok is támogatást élveznek. További információ a védett fájlokkal kapcsolatban: [Támogatott fájlformátumok](supported-file-formats.md).
-   **Továbbfejlesztett naplózás a jobb diagnosztika érdekében** – A naplózási szintek **ERROR** (Hiba) vagy **WARNING** (Figyelmeztetés) jelzést fognak megjeleníteni az áttekintést igénylő üzenetek esetén. A többi üzenet, a továbbra is megjelenő kivételeket is beleértve, **INFO** (Tájékoztatás) jelzéssel lesz naplózva.

    Ezt a megközelítést az adatvesztés elkerülése érdekében választottuk. Mostantól csak a fontos üzenetek jelennek meg a WARNING (Figyelmeztetés) szinttel.

-   **Vállalati sablonok beszerzése** – jelentős javítások történtek a sablonbeszerzési kódban az ügyfelek jelentései és visszajelzései alapján.
-   Nagyobb következetesség a honosításban.

## 2014. októberi frissítés

-   Frissítve lett az SDK File API összetevőjének alapértelmezett működése. További információ: [File API configuration](file-api-configuration.md) (A File API konfigurálása).
-   Az új szolgáltatásként váltak elérhetővé az e-mail-értesítések, amelynek leírása a fejlesztőknek szóló [Enabling email notification](how-to-enable-email-notification.md) (E-mail-értesítések engedélyezése) című témakörben található.

## 2014. júliusi frissítés

Bővítve lettek az SDK File API összetevői, és az alábbi szolgáltatásokat kínálják:

-   A használandó védőelem azonosítása.
-   RMS-védelem biztosítása fájlszinten.

    A jelen kiadásban megjelent függvények:

    **Megjegyzés** A File API-bővítmények további, itt nem látható támogatási adattípusokkal és -struktúrákkal bővültek. A jelen kiadásra vonatkozóan frissített témakörök mindegyike az **előzetes változat, a későbbiekben változhat** jelzéssel lett ellátva.

    -   [**IpcfOpenFileOnHandle**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcfopenfileonhandle)
    -   [**IpcfOpenFileOnILockBytes**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcfopenfileonilockbytes)
    -   [**IpcfGetFileProperty**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcfgetfileproperty)
    -   [**IpcfLogicalFileRangeToRawFileRange**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcflogicalfilerangetorawfilerange)
    -   [**IpcfReadFile**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcfreadfile)
    -   [**IpcfSetEndOfFile**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcfsetendoffile)
    -   [**IpcfWriteFile**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcfwritefile)

## 2014. áprilisi frissítés

-   A **File API memóriahasználata**, különösen nagyméretű védett fájlok esetén jelentős mértékben javult.
-   A **tartalomazonosító** írhatóvá vált az **IPC\_LI\_CONTENT\_ID** tulajdonságon keresztül. További információ: [**License property types**](/rights-management/sdk/2.1/api/win/License%20property%20types#msipc_license_property_types_IPC_LI_APP_SPECIFIC_DATA) (Licenctulajdonság-típusok).
-   **Éles jegyzék követelményei** – Amikor az RMS-kompatibilis alkalmazás/szolgáltatás kiszolgáló módban fut, a továbbiakban nem lesz szükség jegyzékre. További információ: [Application types](application-types.md) (Alkalmazástípusok).
-   **Dokumentációfrissítések**

    **Ajánlott tesztelési eljárás** – útmutató a helyi kiszolgáló használatával kapcsolatban az Azure RMS használatával történő tesztelés előtt. További információ: [Enable your service application to work with cloud based RMS](how-to-use-file-api-with-aadrm-cloud.md) (A szolgáltatásalkalmazás alkalmassá tétele a felhőalapú RMS használatára).

## Fontos megjegyzések fejlesztők számára

-   **Natív támogatás minden fájltípus számára**

    A Rights Management Services SDK 2.1 jelen kiadásával natív támogatás adható hozzá bármilyen fájltípus (kiterjesztés) számára. Például: Az &lt;ext&gt; (nem Office és pdf) kiterjesztés esetén a \*.p&lt;ext&gt; kiterjesztést használja a rendszer, ha a rendszergazdai konfiguráció „NATIVE” (Natív) értékű a kiterjesztésre vonatkozóan.

    További információ a támogatott fájltípusokkal kapcsolatban: [File API configuration](file-api-configuration.md) (A File API konfigurálása).

-   A [KB2533623](https://support.microsoft.com/en-us/kb/2533623) frissítéssel nem rendelkező **Windows 7 SP1 és Windows Server 2008 R2 SP1 rendszerű számítógépek** az alábbi hibát jeleníthetik meg az Office-fájlok védelemmel való ellátása közben: „A paraméter nem megfelelő. Hibakód: 0x80070057”. Ha ezt látja, telepítse újra a frissítést, majd próbálkozzon újra. Ha továbbra is problémákba ütközik, vegye fel a kapcsolatot az RMS SDK Beta Feedback csapatával az <rmcstbeta@microsoft.com> címen.

    **Megjegyzés** A 2015. áprilisi kiadás során egy ellenőrzés lett hozzáadva ezen KB telepítési folyamatához.

     

-   **A File API integrációja**

    Az Active Directory Rights Management Services File API a File API felülettel való bővítést követően az alábbi előnyöket és képességeket biztosítja.

      - Automatikusan láthat el védelemmel bizalmas adatokat a különböző fájlformátumok által használt Tartalomvédelmi szolgáltatás (IRM) megvalósításának részleteire vonatkozó ismeretek nélkül.

      - A Microsoft Office-fájlok, a PDF-fájlok, illetve bizonyos más fájltípusok natív módon láthatók el védelemmel. A natív védelemmel ellátható fájltípusok teljes listája: [File API configuration](file-api-configuration.md) (A File API konfigurálása).

      - A rendszer- és Office-fájlok kivételével minden fájl ellátható védelemmel az RMS Protected File formátum (PFile) használatával.

    A fájl API implementálása a következő négy új függvénnyel történik: [IpcfDecryptFile](/rights-management/sdk/2.1/api/win/functions#msipc_ipcfdecryptfile), [IpcfEncryptFile](/rights-management/sdk/2.1/api/win/functions#msipc_ipcfencryptfile), [IpcfGetSerializedLicenseFromFile](/rights-management/sdk/2.1/api/win/functions#msipc_ipcfgetserializedlicensefromfile) és [IpcfIsFileEncrypted](/rights-management/sdk/2.1/api/win/functions#msipc_ipcfisfileencrypted).

    A fájl API megköveteli, hogy a Rights Management Services-ügyfél 2.1-es verziója telepítve legyen az ügyfélszámítógépre, és hogy a számítógép kapcsolatot tudjon létesíteni egy RMS-kiszolgálóval. Az RMS-kiszolgálóval, az RMS-ügyféllel és funkcióikkal kapcsolatos további információkért lásd [az AD RMS informatikusoknak szóló dokumentációját](https://technet.microsoft.com/en-us/library/cc771234(v=ws.10).aspx) a TechNeten.

-   **Probléma**: Teljesen új licenc létrehozásakor a tulajdonosi jogosultságokat explicit módon kell megadni.

    **Megoldás**: Az alkalmazásnak explicit módon kell hozzáadnia a **Tulajdonos** jogosultságokat a licenctulajdonos számára, ha teljesen új licencet hoz létre az [**IpcCreateLicenseFromScratch**](/rights-management/sdk/2.1/api/win/functions#msipc_ipccreatelicensefromscratch) használatával. További információ: [Add explicit owner rights](add-explicit-owner-rights.md) (Explicit tulajdonosi jogosultságok hozzáadása).

-   **Probléma:** Ha egy alkalmazás kétszer hívja meg az [**IpcProtectWindow**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcprotectwindow) vagy az [**IpcUnprotectWindow**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcunprotectwindow) függvényt ugyanazon ablakra vonatkozóan annak leíróját használva, az RMS SDK 2.1 hibát jelez a **HRESULT** értékben.

    **Megoldás:** A problémával kapcsolatban az [**IpcProtectWindow**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcprotectwindow) és az [**IpcUnprotectWindow**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcunprotectwindow) függvényt ismertető témakör megjegyzéseket tartalmazó szakaszában talál útmutatást.

-   **Probléma**: Több architektúrára való fejlesztéskor ezt az útmutatást kell használnia.

    **Megoldás:** Ha az Ipcsecproc\*isv.dll fájlokat más architektúrához szeretné használni (ha például az SDK 64 bites változatát telepítette egy 64 bites számítógépre, most azonban egy 32 bites számítógépen szeretné üzembe helyezni, amelynek szüksége van az Ipcsecproc\*isv.dll fájlokra), telepítenie kell az SDK 32 bites változatát egy másik számítógépre, és át kell másolnia arra az Ipcsecproc\*isv.dll fájlokat a „%PROGRAMFILES%\\Microsoft Information Protection And Control” mappából (az alapértelmezett vagy az SDK telepítésekor választott helyen található).

## Gyakori kérdések

**K**: Hogyan működik az alapértelmezett nyelv az LCID paramétert használó függvények esetén?

**V**: Használja a 0 értéket az alapértelmezett területi beállításhoz. Ebben az esetben az AD RMS Client 2.1 az alábbi sorrendben keresi a neveket és leírásokat, és az első elérhetőt adja vissza:

    1 - User preferred LCID.
    2 - System locale LCID.
    3 - The first available language specified in the Rights Management Server (RMS) template.

Ha nem kérhető le név és leírás, a rendszer hibát jelez. Egy adott LCID azonosítóhoz csak egy név és leírás tartozhat.

## Kapcsolódó témakörök

* [Áttekintés](ad-rms-overview.md)
* [Add explicit owner rights (Explicit tulajdonosi jogosultságok hozzáadása)](add-explicit-owner-rights.md)
* [File API configuration (A File API konfigurálása)](file-api-configuration.md)
* [**IpcfGetSerializedLicenseFromFile**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcfgetserializedlicensefromfile)
* [**IpcfEncryptFile**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcfencryptfile)
* [**IpcfDecryptFile**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcfdecryptfile)
* [**IpcfIsFileEncrypted**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcfisfileencrypted)
* [**IpcCreateLicenseFromScratch**](/rights-management/sdk/2.1/api/win/functions#msipc_ipccreatelicensefromscratch)
* [**IpcProtectWindow**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcprotectwindow)
* [**IpcUnprotectWindow**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcunprotectwindow)
 

 


<!--HONumber=Jun16_HO2-->


