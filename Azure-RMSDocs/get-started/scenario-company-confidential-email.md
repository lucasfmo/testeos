---
# required metadata

title: Forgatókönyv – Bizalmas vállalati e-mail küldése | Azure RMS
description:
keywords:
author: cabailey
manager: mbaldwin
ms.date: 05/20/2016
ms.topic: get-started-article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 950799e9-2289-48c7-b95a-f54a8ead520a

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: esaggese
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Forgatókönyv – Bizalmas vállalati e-mail küldése

*A következőkre vonatkozik: Azure Rights Management, Office 365*

Ez a forgatókönyv és a kiegészítő felhasználói dokumentáció az Azure Rights Managementet használja arra hogy a szervezet bármely felhasználója biztonságosan küldhessen a szervezeten kívül nem olvasható e-mail üzeneteket. Például akkor, ha valaki egy másik szervezethez tartozó személy számára vagy egy személyes e-mail fiókra továbbít egy üzenetet. Az e-mailt és a mellékleteit az Azure Rights Management és a felhasználó által az e-mail ügyfélprogramból kiválasztott sablon látja el védelemmel.

A forgatókönyv engedélyezésének egyik legegyszerűbb módja az egyik beépített, alapértelmezett sablon használata, amely automatikusan a szervezet összes felhasználójára korlátozza a hozzáférést. Szükség szerint viszont ennél is szigorúbb korlátozásokat vezethet be egyéni sablonok létrehozásával, amelyek a felhasználók csak egy kis csoportjára korlátozzák a hozzáférést, vagy egyéb korlátozásokkal (például csak olvasható vagy lejárati dátum) rendelkeznek, illetve letiltják a Továbbítás gombot az e-mail ügyfélprogramban.

> [!IMPORTANT]
> Bár ebben a forgatókönyvben eltávolíthatja a **Továbbítás** jogot az Ön által konfigurált egyéni sablonból (és ezzel le is tiltja a Továbbítás gombot az e-mail ügyfélprogramban), a konfiguráció nem gátolja meg, hogy a felhasználók megosszák az e-mailt egy másik jogosult felhasználóval. A címzett mentheti az e-mailt (és a mellékleteit), majd egyéb megosztási mechanizmusok használatával megoszthatja az információt.
> 
> Például Bálint küld egy e-mailt Ágnes részére egy olyan egyéni sablon használatával, amely a Fájl mentése és a Tartalom szerkesztése jogokat alkalmazza a Marketing csoportra, de nem tartalmazza a Továbbítás jogot. Bár Ágnes nem tudja másoknak továbbítani az e-mailt, USB-meghajtóra vagy fájlkiszolgáló-megosztásra mentheti az üzenetet és a mellékleteket, amelyeket aztán a Marketing csoport összes tagja elolvashat és szerkeszthet, ha hozzáfér a fájlokhoz. Az olyan felhasználók, akik nem tagjai a Marketing csoportnak, nem tudják megnyitni a tartalmat.

Az utasítások a következő körülmények között alkalmazhatók:

-   A szervezet minden felhasználója szeretne információkat megosztani a szervezet más tagjaival, viszont ezeknek az információknak nem szabad kikerülniük a szervezeten kívülre.

-   A megosztani kívánt információt tartalmazhatja az e-mail üzenet, vagy a melléklet.

-   A felhasználóknak manuálisan kell kiválasztaniuk a sablont az e-mail ügyfélprogramból.

## Üzembe helyezési utasítások
![Rendszergazdai utasítások az Azure RMS gyors üzembe helyezéséhez](../media/AzRMS_AdminBanner.png)

Ellenőrizze, hogy a következő feltételek teljesülnek-e, mielőtt továbblépne a felhasználói dokumentációra.

## A forgatókönyv követelményei
Ahhoz, hogy a forgatókönyv utasításai működjenek, az alábbiaknak kell teljesülniük:

|Követelmény|Ha további információra van szüksége|
|---------------|--------------------------------|
|Előkészítette a fiókokat és a csoportokat az Office 365 vagy az Azure Active Directory számára|[Az Azure Rights Management előkészítése](https://technet.microsoft.com/library/jj585029.aspx)|
|Az Azure Rights Management-bérlőkulcsát a Microsoft felügyeli; nem a BYOK módot használja|[Planning and implementing your Azure Rights Management tenant key (Az Azure Rights Management-bérlőkulcs tervezése és megvalósítása)](https://technet.microsoft.com/library/dn440580.aspx)|
|Az Azure Rights Management aktiválása megtörtént|[Az Azure Rights Management aktiválása](https://technet.microsoft.com/library/jj658941.aspx)|
|A következők egyike:<br /><br />– Az Exchange Online engedélyezve van az Azure Rights Managementhez<br /><br />– Az RMS-összekötő telepítve és konfigurálva van a helyszíni Exchange-hez|Az Exchange Online esetében lásd a [Configuring Applications for Azure Rights Management (Alkalmazások konfigurálása az Azure Rights Managementhez)](https://technet.microsoft.com/library/jj585031.aspx) című témakör **Exchange Online: IRM Configuration (Exchange Online: IRM konfiguráció)** szakaszát.<br /><br />Helyszíni Exchange esetében: [Deploying the Azure Rights Management connector (Az Azure Rights Management-összekötő üzembe helyezése)](https://technet.microsoft.com/library/dn375964.aspx)|
|Nem archiválta a **&lt;szervezet&gt; - Bizalmas** alapértelmezett Azure Rights Management sablont. Másik megoldás, hogy erre a célra konfigurált egy egyéni sablont, mert szigorúbb beállításokra volt szüksége, illetve a szervezet felhasználóinak csak egy kis csoportja olvashatja a védett e-maileket.|[Az Azure Rights Management egyéni sablonok konfigurálása](https://technet.microsoft.com/library/dn642472.aspx)<br /><br />Tipp: Ha szigorúbb használati házirendre vonatkozó beállításokra van szüksége, amely a szervezet minden felhasználójára vonatkozik, egy teljesen új sablon létrehozása helyett másolja, majd szerkessze az alapértelmezett sablonokat.<br /><br />Ebben a forgatókönyvben a frissített sablonok nem frissülnek azonnal az e-mail ügyfélprogramokban. További információkat a sablonok konfigurálását ismertető cikk [Sablonok frissítése a felhasználók számára](https://technet.microsoft.com/library/dn642472.aspx) című szakaszában találhat.|
|A védett e-maileket küldő felhasználók a következők egyikével rendelkeznek: Outlook 2013, Outlook 2016 vagy Outlook Web Access.<br /><br />Az e-mail címzettjei az Azure Rights Managementet támogató e-mail ügyfélprogrammal rendelkeznek.|Használhatja az Outlook 2010 programot is, de [telepítenie kell a Windows Rights Management megosztóalkalmazását](https://technet.microsoft.com/library/dn339003.aspx), és ennek megfelelően kell módosítania a felhasználói utasításokat.<br /><br />Az Azure Rights Managementet támogató e-mail ügyfélprogramok listájáért tekintse meg az [Azure Rights Management követelményei](https://technet.microsoft.com/library/dn655136.aspx) szakasz [Ügyféleszközök képességei](https://technet.microsoft.com/library/dn655136.aspx) táblázatának **E-mail** oszlopát.|

## A felhasználói dokumentáció utasításai
Az alábbi sablon használatával másolja és illessze be a felhasználói utasításokat egy végfelhasználóknak szóló üzenetbe, és végezze el a módosításokat a környezetének megfelelő adatok érdekében:

1.  Cserélje le a *&lt;szervezet neve&gt;* szöveg összes példányát a saját szervezetének nevére.

2.  Cserélje le a *&lt;szervezet neve – Bizalmas&gt;* összes példányát a saját alapértelmezett vagy egyéni sablonjának nevére.

3.  Cserélje le a képernyőfelvételeket, hogy a szervezet sablonjainak nevét mutassák.

4.  Cserélje le a *&lt;kapcsolattartás adatok&gt;* szöveget azokra az utasításokra, amelyeket követve a felhasználók elérhetik az ügyfélszolgálatot (pl. webhelyhivatkozások, e-mail címek vagy telefonszámok).

5.  **További megfontolandó módosítások:**

    -   Ha érdemes csak egy e-mail ügyfélprogramra korlátozni az utasításokat, akkor az egyszerűség érdekében fontolja meg a többi utasításkészlet törlését.

    -   Ha a javasolt alapértelmezett sablon helyett egyéni sablont használ, ennek megfelelően módosítsa a megfogalmazást:

        -   Pontosítsa a címet.

        -   Adja meg a kiválasztandó felhasználókat vagy csoportokat az 1. lépésben.

        -   Adja meg az egyéni sablon nevét a 2. lépésben.

        -   Módosítsa az utolsó bekezdést a címzettekre vonatkozó korlátozások ismertetéséhez.

6.  Végezzen el bármilyen egyéb tetszés szerinti módosítást az utasításkészletre vonatkozóan, majd küldje el az érintett felhasználóknak.

7.  Mivel nem minden ügyfél támogatja a Rights Managementet, előfordulhat, hogy útmutatást és javaslatokat is biztosítania kell a védett e-mail üzenetek címzettjeinek. Ezeket az információkat a szervezetén belül használtban lévő eszközök és e-mail alkalmazások, valamint az egyéb beállítások határozzák meg. Javasolja például, hogy az iOS felhasználói az iPad és iPhone Outlook használatával olvassák el a védett e-maileket, és ne az iOS beépített e-mail-ügyfélprogramjával.

    Az e-mail-ügyfélprogramokkal kapcsolatos további információkért tekintse meg az [Azure Rights Management követelményei](https://technet.microsoft.com/library/dn655136.aspx) szakasz [Ügyféleszközök képességei](https://technet.microsoft.com/library/dn655136.aspx) táblázatának **E-mail** oszlopát.

A példadokumentációban látható, hogyan jelennek meg ezek az utasítások a felhasználók számára a testre szabást követően.

![Felhasználói dokumentációs sablon az Azure RMS gyors üzembe helyezéséhez](../media/AzRMS_UsersBanner.png)

### Bizalmas vállalati információkat tartalmazó e-mailek küldése az Outlook használatával

1.  Hozzon létre az Outlookban egy új e-mail üzenetet, adjon hozzá bármilyen tetszés szerinti mellékletet, majd válasszon *&lt;szervezet neve&gt;*-felhasználókat és csoportokat.

2.  Kattintson a **BEÁLLÍTÁSOK** lapon az **Engedély** lehetőségre, és válassza a **&lt;szervezet neve – Bizalmas&gt;** lehetőséget:

    ![Képernyőfelvétel: Bizalmas vállalati információkat tartalmazó e-mailek küldése az Outlook használatával](../media/AzRMS_OutlookTemplate.PNG)

3.  Küldje el az üzenetet.

### Bizalmas vállalati információkat tartalmazó e-mailek küldése az Outlook Web App használatával

1.  Hozzon létre az Outlook Web App alkalmazásban egy új e-mail üzenetet, adjon hozzá bármilyen tetszés szerinti mellékletet, majd válasszon *&lt;szervezet neve&gt;*-felhasználókat és -csoportokat a címjegyzékből.

2.  Kattintson a **…**, majd az **Engedélyek beállítása** lehetőségre, és válassza a **&lt;szervezet neve – Bizalmas&gt;** lehetőséget:

    ![Képernyőfelvétel: Bizalmas vállalati információkat tartalmazó e-mailek küldése az Outlook Web App használatával](../media/AzRMS_OWATemplate.png)

3.  Küldje el az üzenetet.

Ha a **Címzett**, **Másolatot kap** vagy **Titkos másolat** sorban szereplő személy megkapja az e-mailt, az üzent elolvasása előtt a rendszer hitelesítő adatokat kérhet tőle, hogy ellenőrizze, valóban a(z) *&lt;szervezet neve&gt;* felhasználója-e. Más alkalmakkor a rendszer nem kéri a felhasználókat a hitelesítő adataik megadására, mivel a hitelesítés már megtörtént.

Az e-mail címzettjei továbbküldhetik az üzenetet másoknak, de csak a *&lt;szervezet neve&gt;* felhasználói tudják elolvasni. Ha Office dokumentumot csatol, akkor még akkor is ugyanazzal a védelemmel fog rendelkezni, ha a dokumentumot más néven, vagy más helyre mentik. A sikeresen hitelesített felhasználók viszont másolhatják, beilleszthetik és kinyomtathatják az e-mailt vagy a melléklet részeit. Ha ennél szigorúbb korlátozást jelentő védelemre van szüksége, amely képes meggátolni a fenti műveletek végrehajtását, lépjen kapcsolatba az ügyfélszolgálattal.

**Segítségre van szüksége?**

-   Lépjen kapcsolatba az ügyfélszolgálattal:

    -   *&lt;kapcsolattartási adatok&gt;*

### Példa testre szabott felhasználói dokumentációra
![Példa felhasználói dokumentációra az Azure RMS gyors üzembe helyezéséhez](../media/AzRMS_ExampleBanner.png)

#### Bizalmas vállalati információkat tartalmazó e-mailek küldése az Outlook használatával

1.  Hozzon létre az Outlookban egy új e-mail üzenetet, adjon hozzá bármilyen tetszés szerinti mellékletet, majd válasszon VanArsdel felhasználókat és csoportokat a címjegyzékből.

2.  Kattintson a **BEÁLLÍTÁSOK** lapon az **Engedély** lehetőségre, és válassza a **VanArsdel, Ltd – Bizalmas** lehetőséget:

    ![Képernyőfelvétel: Bizalmas vállalati információkat tartalmazó e-mailek küldése az Outlook használatával](../media/AzRMS_OutlookTemplate.PNG)

3.  Küldje el az üzenetet.

#### Bizalmas vállalati információkat tartalmazó e-mailek küldése az Outlook Web App használatával

1.  Hozzon létre az Outlook Web App alkalmazásban egy új e-mail üzenetet, adjon hozzá bármilyen tetszés szerinti mellékletet, majd válasszon VanArsdel-felhasználókat és -csoportokat a címjegyzékből.

2.  Kattintson a **…**, majd az **Engedélyek beállítása** lehetőségre, és válassza a **VanArsdel, Ltd – Bizalmas** lehetőséget:

    ![Képernyőfelvétel: Bizalmas vállalati információkat tartalmazó e-mailek küldése az Outlook Web App használatával](../media/AzRMS_OWATemplate.png)

3.  Küldje el az üzenetet.

Ha a **Címzett**, **Másolatot kap** vagy **Titkos másolat** sorban szereplő személy megkapja az e-mailt, az üzent elolvasása előtt a rendszer hitelesítő adatokat kérhet tőle, hogy ellenőrizze, valóban a VanArsdel, Ltd felhasználója-e. Más alkalmakkor a rendszer nem kéri a felhasználókat a hitelesítő adataik megadására, mivel a hitelesítés már megtörtént.

Az e-mail címzettjei továbbküldhetik az üzenetet másoknak, de csak a VanArsdel felhasználói tudják elolvasni. Ha Office dokumentumot csatol, akkor még akkor is ugyanazzal a védelemmel fog rendelkezni, ha a dokumentumot más néven, vagy más helyre mentik. A sikeresen hitelesített felhasználók viszont másolhatják, beilleszthetik és kinyomtathatják az e-mailt vagy a melléklet részeit. Ha ennél szigorúbb korlátozást jelentő védelemre van szüksége, amely képes meggátolni a fenti műveletek végrehajtását, lépjen kapcsolatba az ügyfélszolgálattal.

**Segítségre van szüksége?**

-   Lépjen kapcsolatba az ügyfélszolgálattal:

    -   E-mail: helpdesk@vanarsdelltd.com



<!--HONumber=May16_HO3-->


