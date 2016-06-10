---
# required metadata

title: Sablonok frissítése | Azure RMS
description:
keywords:
author: cabailey
manager: mbaldwin
ms.date: 05/06/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 8c2064f0-dd71-4ca5-9040-1740ab8876fb

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: esaggese
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---


# Sablonok frissítése a felhasználók számára

*A következőkre vonatkozik: Azure Rights Management, Office 365*

Az Azure RMS használata során a rendszer automatikusan letölti a sablonokat az ügyfélszámítógépekre, így a felhasználók kiválaszthatják azokat az alkalmazásaikból. Ha azonban módosítja a sablonokat, további lépések végrehajtására lehet szükség:

|Alkalmazás vagy szolgáltatás|A sablonok frissítésének módja a módosításokat követően|
|--------------------------|---------------------------------------------|
|Exchange Online|A sablonok frissítéséhez manuális konfigurálás szükséges.<br /><br />A konfigurálás lépéseinek végrehajtásához tekintse meg az alábbi, [Csak az Exchange Online esetén: az Exchange konfigurálása módosított egyéni sablonok letöltésére](#exchange-online-only-how-to-configure-exchange-to-download-changed-custom-templates) című részt..|
|Office 365|Automatikus frissítés – nem igényel további lépéseket.|
|Office 2016 és Office 2013<br /><br />A Windows RMS-megosztóalkalmazása|Automatikus frissítés – ütemezés szerint:<br /><br />Az Office ezen újabb verziói esetén: az alapértelmezett frissítési gyakoriság 7 nap.<br /><br />A Windows RMS-megosztóalkalmazása esetén: az 1.0.1784.0-s verziótól kezdődően az alapértelmezett frissítési gyakoriság 1 nap. A korábbi verziók esetében az alapértelmezett frissítési gyakoriság 7 nap.<br /><br />Ennél az ütemezésnél gyakoribb frissítés kényszerítéséhez tekintse meg az alábbi, [Az Office 2016, Office 2013 és a Windows RMS-megosztóalkalmazása esetén: módosított egyéni sablon frissítésének kényszerítése](#office-2016-office-2013-and-rms-sharing-application-for-windows-how-to-force-a-refresh-for-a-changed-custom-template) című részt..|
|Office 2010|A frissítés a felhasználók bejelentkezésekor történik.<br /><br />A frissítés kényszerítéséhez kérje meg vagy kényszerítse a felhasználókat a kijelentkezésre, majd újbóli bejelentkezésre. Vagy tekintse meg az alábbi, [Csak az Office 2010 esetén: módosított egyéni sablon frissítésének kényszerítése](#office-2010-only-how-to-force-a-refresh-for-a-changed-custom-template) című részt..|
Az RMS-megosztóalkalmazást használó mobileszközök esetén a sablonok letöltése (és szükség esetén frissítése) automatikusan megtörténik, és nem igényel további konfigurálást.

## Csak az Exchange Online esetén: az Exchange konfigurálása módosított egyéni sablonok letöltésére
Ha már konfigurálta a Tartalomvédelmi szolgáltatást (IRM) az Exchange Online esetén, az egyéni sablonok letöltése addig nem történik meg a felhasználók számára, amíg végre nem hajtja a következő módosításokat a Windows PowerShell használatával az Exchange Online szolgáltatásban.

> [!NOTE]
> A Windows PowerShellnek az Exchange Online szolgáltatásban történő használatával kapcsolatos további információk: [Using PowerShell with Exchange Online](https://technet.microsoft.com/library/jj200677%28v=exchg.160%29.aspx) (A PowerShell és az Exchange Online együttes használata)..

Ezt az eljárást minden alkalommal végre kell hajtania, amikor módosít egy sablont.

### Sablonok frissítése az Exchange Online esetén

1.  A Windows PowerShellt az Exchange Online szolgáltatásban használva kapcsolódjon a szolgáltatáshoz:

    1.  Adja meg az Office 365-felhasználónevét és -jelszavát:

        ```
        $Cred = Get-Credential
        ```

    2.  Az Exchange Online szolgáltatáshoz az alábbi két parancs futtatásával csatlakozhat:

        ```
        $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.outlook.com/powershell/ -Credential $Cred -Authentication Basic –AllowRedirection
        ```

        ```
        Import-PSSession $Session
        ```

2.  Az [Import-RMSTrustedPublishingDomain](http://technet.microsoft.com/library/jj200724%28v=exchg.160%29.aspx) parancsmaggal importálja újra a megbízható közzétételi tartományt (TPD) az Azure RMS-ből:

    ```
    Import-RMSTrustedPublishingDomain -Name "<TPD name>" -RefreshTemplates -RMSOnline
    ```
    Ha például a TPD neve **RMS Online - 1** (általánosan használt név számos vállalat esetében), írja be a következőt: **Import-RMSTrustedPublishingDomain -Name "RMS Online - 1" -RefreshTemplates -RMSOnline**

    > [!NOTE]
    > A TPD nevét a [Get-RMSTrustedPublishingDomain](http://technet.microsoft.com/library/jj200707%28v=exchg.160%29.aspx) parancsmaggal ellenőrizheti.

3.  Ha szeretne meggyőződni arról, hogy a sablonok importálása sikeresen megtörtént-e, várjon pár percet, majd futtassa a [Get-RMSTemplate](http://technet.microsoft.com/library/dd297960%28v=exchg.160%29.aspx) parancsmagot, és állítsa be a Type (Típus) paraméter értékét All (Mind) értékűre. Példa:

    ```
    Get-RMSTemplate -TrustedPublishingDomain "RMS Online - 1" -Type All
    ```
    > [!TIP]
    > Hasznos lehet megőrizni a kimenet egy másolatát, így könnyedén másolhatja a sablonok nevét vagy GUID azonosítóit, ha a későbbiekben archivál egy sablont.

4.  Az Outlook Web App alkalmazásban elérhetővé tenni kívánt sablonok mindegyike esetén a [Set-RMSTemplate](http://technet.microsoft.com/library/hh529923%28v=exchg.160%29.aspx) parancsmagot kell használnia, és a Type (Típus) paraméter értékét Distributed (Elosztott) értékűre kell beállítania:

    ```
    Set-RMSTemplate -Identity "<name  or GUID of the template>" -Type Distributed
    ```
    Mivel az Outlook Web Access 24 órára gyorsítótárazza a felhasználói felületet, előfordulhat, hogy a felhasználóknál csak egy nap elteltével jelenik meg az új sablon.

Továbbá, amikor archivál egy (egyéni vagy alapértelmezett) sablont, és az Exchange Online-t az Office 365 szolgáltatással használja, a felhasználók továbbra is látni fogják az archivált sablonokat, ha az Outlook Web App alkalmazást, illetve az Exchange ActiveSync protokollt használó mobileszközöket használnak.

Ahhoz, hogy a felhasználóknál ne jelenjenek meg a továbbiakban ezek a sablonok, csatlakozzon a szolgáltatáshoz a Windows PowerShell használatával az Exchange Online szolgáltatásban, majd használja a [Set-RMSTemplate](http://technet.microsoft.com/library/hh529923%28v=exchg.160%29.aspx) parancsmagot az alábbi parancs futtatásával:

```
Set-RMSTemplate -Identity "<name or GUID of the template>" -Type Archived
```

## Az Office 2016, Office 2013 és a Windows RMS-megosztóalkalmazása esetén: módosított egyéni sablon frissítésének kényszerítése
Az Office 2016-ot, Office 2013-at és Windows RMS-megosztóalkalmazását futtató számítógépek beállításjegyzékének módosításával módosíthatja az automatikus ütemezést, így a módosított sablonok frissítése az alapértelmezett értéknél gyakrabban fog bekövetkezni a számítógépeken. Egy beállításazonosító meglévő adatainak törlésével azonnali frissítést kényszeríthet.

> [!WARNING]
> A Beállításszerkesztő nem megfelelő használatával olyan súlyos problémákat okozhat, amelyek az operációs rendszer újratelepítését tehetik szükségessé. A Microsoft nem tudja garantálni, hogy a Beállításszerkesztő nem megfelelő használatából eredő problémákat meg tudja oldani. A Beállításszerkesztőt saját kockázatára használhatja.

### Az automatikus ütemezés módosítása

1.  Egy beállításszerkesztő segítségével hozza létre és adja meg az alábbi beállításazonosítók egyikét:

    - A frissítési gyakoriság megadása napokban (legalább 1 nap): Hozzon létre egy új beállításazonosítót a **TemplateUpdateFrequency** néven, majd az adatok számára adjon meg egy egész számot, amely napokban adja meg a letöltött sablonok módosításainak letöltési gyakoriságát. Az alábbi információkkal megkeresheti az új beállításazonosító létrehozásához szükséges beállításjegyzékbeli elérési utat.

        **Beállításjegyzékbeli elérési út:** HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC

        **Típus:** REG_DWORD

        **Érték:** TemplateUpdateFrequency

    - A frissítési gyakoriság megadása másodpercben (legalább 1 másodperc): Hozzon létre egy új beállításazonosítót a **TemplateUpdateFrequencyInSeconds** néven, majd az adatok számára adjon meg egy egész számot, amely másodpercben adja meg a letöltött sablonok módosításainak letöltési gyakoriságát. Az alábbi információkkal megkeresheti az új beállításazonosító létrehozásához szükséges beállításjegyzékbeli elérési utat.

        **Beállításjegyzékbeli elérési út:** HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC

        **Típus:** REG_DWORD

        **Érték:** TemplateUpdateFrequencyInSeconds

    A két beállításazonosító közül csak az egyiket hozza létre és adja meg, mindkettőt ne. Ha mindkettő jelen van, a rendszer a **TemplateUpdateFrequency** beállításazonosítót figyelmen kívül hagyja.

2.  Ha a sablonok azonnali frissítését szeretné kényszeríteni, ugorjon a következő eljárásra. Egyéb esetben indítsa újra most az Office-alkalmazásokat és a Fájlkezelő példányait.

### Azonnali frissítés kényszerítése

1.  Egy beállításszerkesztő használatával törölje a **LastUpdatedTime** beállításazonosító adatait. Ha például a megjelenő adat **2015-04-20T15:52**, akkor törölje a 2015-04-20T15:52 értéket, hogy ne jelenjen meg semmilyen adat. Az alábbi információkkal megkeresheti a beállításazonosító adatainak törléséhez szükséges beállításjegyzékbeli elérési utat.

    **Beállításjegyzékbeli elérési út:** HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC\<*MicrosoftRMS_FQDN*>\Template

    **Típus:**REG_SZ

    **Érték:** LastUpdatedTime

    > [!TIP]
        > A beállításjegyzékbeli elérési út <*MicrosoftRMS_FQDN*> része a Microsoft RMS szolgáltatás teljes tartományneve. Ha ellenőrizni szeretné ezt az értéket:

    > 1.  Futtassa az Azure RMS [Get-AadrmConfiguration](https://msdn.microsoft.com/library/windowsazure/dn629410.aspx) parancsmagját. Ha még nem telepítette az Azure RMS-hez készült Windows PowerShell-modult, tekintse meg az [Installing Windows PowerShell for Azure Rights Management](install-powershell.md) (Az Azure Rights Managementhez készült Windows PowerShell telepítése) című témakört..
    > 2.  A kimenetben azonosítsa a **LicensingIntranetDistributionPointUrl** értéket.
    > 
    >     Például: **LicensingIntranetDistributionPointUrl   : https://5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com/_wmcs/licensing**
    > 3.  Az értékben távolítsa el a **https://** and a **/_wmcs/licensing** részt a karakterláncból. A fennmaradó érték a Microsoft RMS szolgáltatás teljes tartományneve. A példánkban a Microsoft RMS szolgáltatás teljes tartományneve az alábbi érték lenne:
    > 
    >     **5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com**

2.  Törölje a következő mappát és annak összes fájlját: **%localappdata%\Microsoft\MSIPC\Templates**

3.  Indítsa újra most az Office-alkalmazásokat és a Fájlkezelő példányait.

## Csak az Office 2010 esetén: módosított egyéni sablon frissítésének kényszerítése
Az Office 2010-et futtató számítógépek beállításjegyzékének módosításával beállíthat egy értéket, hogy a módosított sablonok frissítése a számítógépeken a felhasználók kijelentkezésére és újbóli bejelentkezésére való várakozás nélkül történjen meg. Egy beállításazonosító meglévő adatainak törlésével azonnali frissítést kényszeríthet.

> [!WARNING]
> A Beállításszerkesztő nem megfelelő használatával olyan súlyos problémákat okozhat, amelyek az operációs rendszer újratelepítését tehetik szükségessé. A Microsoft nem tudja garantálni, hogy a Beállításszerkesztő nem megfelelő használatából eredő problémákat meg tudja oldani. A Beállításszerkesztőt saját kockázatára használhatja.

### A frissítési gyakoriság módosítása

1.  Egy beállításszerkesztő használatával hozzon létre egy új beállításazonosítót az **UpdateFrequency** néven, majd az adatok számára adjon meg egy egész számot, amely napokban adja meg a letöltött sablonok módosításainak letöltési gyakoriságát. Az alábbi táblázattal megkeresheti az új beállításazonosító létrehozásához szükséges beállításjegyzékbeli elérési utat.

    **Beállításjegyzékbeli elérési út:** HKEY_CURRENT_USER\Software\Microsoft\MSDRM\TemplateManagement

    **Típus:** REG_DWORD

    **Érték:** UpdateFrequency

2.  Ha a sablonok azonnali frissítését szeretné kényszeríteni, ugorjon a következő eljárásra. Egyéb esetben indítsa újra most az Office-alkalmazásokat.

### Azonnali frissítés kényszerítése

1.  Egy beállításszerkesztő használatával törölje a **LastUpdatedTime** beállításazonosító adatait. Ha például a megjelenő adat **2015-04-20T15:52**, akkor törölje a 2015-04-20T15:52 értéket, hogy ne jelenjen meg semmilyen adat. Az alábbi táblázattal megkeresheti a beállításazonosító adatainak törléséhez szükséges beállításjegyzékbeli elérési utat.

    **Beállításjegyzékbeli elérési út:** HKEY_CURRENT_USER\Software\Microsoft\MSDRM\TemplateManagement

    **Típus:**REG_SZ

    **Érték:** lastUpdatedTime


2.  Törölje a következő mappát és annak összes fájlját: **%localappdata%\Microsoft\MSIPC\Templates**

3.  Indítsa újra az Office-alkalmazásokat.

## Lásd még:
[Egyéni sablonok konfigurálása az Azure Rights Management szolgáltatáshoz](configure-custom-templates.md)

<!--HONumber=May16_HO1-->


