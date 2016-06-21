---
# required metadata

title: A fájl API konfigurálása | Azure RMS
description: A fájl API működése konfigurálható a beállításjegyzék beállításaival.
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 930878C2-D2B4-45F1-885F-64927CEBAC1D
# optional metadata

#ROBOTS:
audience: developer
#ms.devlang:
ms.reviewer: shubhamp
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# File API configuration (A File API konfigurálása)


A fájl API működése konfigurálható a beállításjegyzék beállításain keresztül.

A fájl API kétféle védelmet biztosít: natív védelmet és PFile-védelmet.

-   **Natív védelem** – a fájl a MIME-típusán (fájlnévkiterjesztésén) alapuló AD RMS fájlformátumra van titkosítva.
-   **PFile-védelem** – a fájlok az AD RMS PFile formátumával vannak titkosítva.

További információt a támogatott fájlformátumokról ezen témakör **Fájl API – a fájltámogatás részletei** című szakaszában találhat.

## Kulcs/kulcsérték típusai és leírásai

A következő szakaszok a titkosítást szabályozó kulcsokat és kulcsértékeket írják le.

### HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\FileProtection

**Típus**: Kulcs

**Leírás**: A fájl API általános konfigurációját tartalmazza.

### HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\FileProtection\&lt;EXT&gt;

**Típus**: Kulcs

**Leírás**: Egy adott fájlkiterjesztés (például TXT, JPG stb.) konfigurációs adatait adja meg.

- A „*” helyettesítő karakter engedélyezett, de az adott fájlkiterjesztéshez tartozó beállítás elsőbbséget élvez a helyettesítő karakterrel szemben. A helyettesítő karakter nem érinti a Microsoft Office-fájlok beállításait; ezeket explicit módon kell letiltani fájltípusonként.
- A kiterjesztéssel nem rendelkező fájlok megadásához használja a „.” karaktert.
- Ha egy adott fájlkiterjesztéshez ad meg kulcsot, ne használjon „.” karaktert. A .txt fájlok beállításainak megadásához használja például a következőt: `HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\FileProtection\TXT`. (Ne használja ezt: `HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\FileProtection\.TXT`).

A védelem működésének beállításához adja meg az **Encryption** értéket a kulcsban. Ha az **Encryption** érték nincs megadva, a fájl az alapértelmezett működést követi.


### HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\FileProtection\&lt;EXT&gt;\Encryption*

**Típus:** REG_SZ

**Leírás**: a következő három érték egyikét tartalmazza:

- **Off**: A védelem le van tiltva.

> [!Note] A beállítás nincs hatással a visszafejtésre. Egy titkosított fájl – akár natív, akár Pfile-védelemmel lett titkosítva – visszafejthető, ha a felhasználó rendelkezik **EXTRACT** jogosultsággal.

- **Native**:  A rendszer natív titkosítást használ. Office-fájlok esetében a titkosított fájl kiterjesztése megegyezik az eredeti fájléval. Egy .docx kiterjesztésű fájl például .docx kiterjesztésű fájlba lesz titkosítva. Más natív védelemmel ellátott fájlok esetében a fájl p*zzz* kiterjesztési formátumú fájlba lesz titkosítva, ahol a *zzz* a fájl eredeti kiterjesztése. A .txt kiterjesztésű fájlok például .ptxt kiterjesztésű fájlba lesznek titkosítva. Az alábbiakban látható azon fájlkiterjesztések listája, amelyekre natív védelem alkalmazható.

- **Pfile**: A rendszer PFile-titkosítást használ. A fájl eredeti kiterjesztéséhez a titkosításkor a rendszer hozzáfűz egy .pfile kiterjesztést. Titkosítás után egy .txt fájl kiterjesztése például .txt.pfile lesz.


> [!Note] A beállítás nincs hatással az Office-fájlformátumokra. Ha `HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\FileProtection\DOCX\Encryption` például &quot;Pfile” értékre van állítva, a .docx fájlokat a rendszer továbbra is natív védelemmel titkosítja, és a titkosított fájl kiterjesztése továbbra is .docx lesz.

Bármely más érték megadása, vagy ha nincs érték megadva, alapértelmezett viselkedést eredményez.

## Az alapértelmezett viselkedés különböző fájlformátumok esetében

-   **Office-fájlok**: A natív titkosítás engedélyezve van.
-   **txt-, xml-, jpg-, jpeg-, pdf-, png-, tiff-, bmp-, gif-, giff-, jpe-, jfif-, jif-fájlok** A natív titkosítás engedélyezve van (xxx helyett pxxx lesz)
-   **Minden más fájl** A titkosítás pfile-kompatibilis (xxx helyett xxx.pfile lesz)

Ha egy blokkolt fájltípust próbál titkosítani, [**IPCERROR\_FILE\_ENCRYPT\_BLOCKED**](/rights-management/sdk/2.1/api/win/error%20codes) hiba jelentkezik.

### Fájl API – a fájltámogatás részletei

Natív támogatás adható hozzá bármilyen fájltípus (kiterjesztés) számára. Például: Az &lt;ext&gt; (nem Office-) kiterjesztés esetén a \*.p&lt;ext&gt; kiterjesztést használja a rendszer, ha a rendszergazdai konfiguráció „NATIVE” (Natív) értékű a kiterjesztésre vonatkozóan.

**Office-fájlok**

-   Fájlkiterjesztések: doc, dot, xla, xls, xlt, pps, ppt, docm, docx, dotm, dotx, xlam, xlsb, xlsm, xlsx, xltm, xltx, xps, potm, potx, ppsx, ppsm, pptm, pptx, thmx.
-   Védelem típusa = Natív (alapértelmezett): a sample.docx titkosítva sample.docx lesz
-   Védelem típusa = PFile: Office-fájlok esetében ugyanaz az eredmény, mint natív titkosításnál.
-   Off: Letiltja a titkosítást.

**PDF-fájlok**

-   Védelem típusa = Natív: a sample.pdf titkosítva sample.ppdf lesz
-   Védelem típusa = PFile: a sample.pdf titkosítva sample.pdf.pfile lesz.
-   Off: Letiltja a titkosítást.

**Minden más fájlformátum**

-   Védelem típusa = PFile: a sample.*zzz* titkosítva sample.*zzz*.pfile; ahol a *zzz* az eredeti fájlkiterjesztés.
-   Off: Letiltja a titkosítást.

### Példák

A következő beállítások engedélyezik a PFile-titkosítást a txt-fájlok esetében. Az Office-fájloknál alkalmazva lesz a natív védelem (alapértelmezés szerint), a txt-fájloknál alkalmazva lesz a PFile-védelem, és minden más fájlnál le lesz tiltva a védelem (alapértelmezés szerint).

```
HKEY_LOCAL_MACHINE
   Software
      Microsoft
         MSIPC
            FileProtection
               txt
                  Encryption = Pfile
```

Az alábbi beállítások engedélyezik a PFile-titkosítást az összes nem Office fájlhoz a txt-fájlok kivételével. Az Office-fájloknál alkalmazva lesz a natív védelem (alapértelmezés szerint), a txt-fájloknál le lesz tiltva a védelem, és minden más fájlnál alkalmazva lesz a PFile-védelem.

```
HKEY_LOCAL_MACHINE
   Software
      Microsoft
         MSIPC
            FileProtection
               *
                  Encryption = Pfile
               txt
                  Encryption = Off
```

A következő beállítások letiltják a docx-fájlok natív titkosítását. Az Office-fájloknál a docx-fájlok kivételével alkalmazva lesz a natív védelem (alapértelmezés szerint), és minden más fájlnál le lesz tiltva a védelem (alapértelmezés szerint).

```
HKEY_LOCAL_MACHINE
   Software
      Microsoft
         MSIPC
            FileProtection
               docx
                  Encryption = Off
```

## Kapcsolódó témakörök

* [Megjegyzések fejlesztők számára](developer-notes.md)
* [**IPCERROR\_FILE\_ENCRYPT\_BLOCKED**](/rights-management/sdk/2.1/api/win/error%20codes)
 

 


<!--HONumber=Jun16_HO2-->


