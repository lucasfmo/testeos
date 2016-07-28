---
title: "Egyéni sablonok létrehozása, konfigurálása és közzététele | Azure RMS"
description: 
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 07/15/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: d6e9aa0c-1694-4a53-8898-4939f31cc13f
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 5737594c679be0702761014425e104e5eade59f3
ms.openlocfilehash: c240502f2e88ec61bcbee6be778e77a0d5aee66b


---


# Egyéni sablonok létrehozása, konfigurálása és közzététele

*A következőkre vonatkozik: Azure Rights Management, Office 365*


Az egyéni sablonok létrehozása és kezelése a klasszikus Azure-portálon történik. Ezt megteheti közvetlenül a klasszikus Azure-portálról, vagy beléphet az Office 365 felügyeleti központjába, és kiválaszthatja a Rights Managementre vonatkozó **Speciális szolgáltatások** lehetőséget, amely azután átirányítja Önt a klasszikus Azure-portálra.

A klasszikus Azure portálon található sablonok létrehozásához és kezeléséhez globális rendszergazdának kell lennie. Ha az Azure RMS globális rendszergazdájának szerepkörét más felhasználókhoz rendelte, ők is létrehozhatják és kezelhetik a sablonokat, azonban erre a célra a [PowerShellt](configure-templates-with-powershell.md) kell használniuk. További információt a [Globális rendszergazdának kell lenni az Azure RMS konfigurálásához, vagy átadható a feladat más rendszergazdáknak?](../get-started/faqs.md#do-you-need-to-be-a-global-admin-to-configure-azure-rms-or-can-i-delegate-to-other-administrators) című kérdésben talál. 

Az alábbi eljárásokkal hozhat létre, konfigurálhat és tehet közzé egyéni sablonokat a Rights Management szolgáltatáshoz.

## Egyéni sablon létrehozása

1.  Attól függően, hogy az Office 365 felügyeleti központjába vagy a klasszikus Azure-portálra lépett be, a következők egyikét teheti:

    -   Az [Office 365 felügyeleti központjából](https://portal.office.com/):

        1.  A bal oldali panelen kattintson a **Szolgáltatás beállításai** elemre.

        2.  A **Szolgáltatás beállításai** lapon kattintson a **jogosultságkezelés** gombra.

        3.  Az **Információvédelem** szakaszban kattintson a **Kezelés** elemre.

        4.  A **jogosultságkezelés** szakaszban kattintson a **speciális szolgáltatások** elemre.

            > [!NOTE]
            > Ha még nem aktiválta a Rights Managementet, először kattintson az **aktiválás** elemre, és erősítse meg a műveletet. További információ: [Activating Azure Rights Management](activate-service.md) (Az Azure Rights Management aktiválása).
            > 
            > Ha korábban még nem kattintott a **speciális szolgáltatások** elemre, akkor a Rights Management aktiválása után kövesse a képernyőn megjelenő utasításokat, amelyekkel hozzájuthat egy, a klasszikus Azure-portál eléréséhez szükséges ingyenes Azure-előfizetéshez.

            A **speciális szolgáltatások** lehetőségre kattintva betöltődik a klasszikus Azure-portál, ahonnan felügyelheti a szervezete Azure Active Directoryjára vonatkozó **RIGHTS MANAGEMENT** szolgáltatásokat.

    -   A [Klasszikus Azure-portálon](http://go.microsoft.com/fwlink/p/?LinkID=275081):

        1.  A bal oldali panelen kattintson az **ACTIVE DIRECTORY** elemre.

        2.  Az **Active Directory** lapon kattintson a **RIGHTS MANAGEMENT** gombra.

        3.  Válassza ki a Rights Management által felügyelni kívánt mappát.

        4.  Ha még nem aktiválta a Rights Managementet, kattintson az **ACTIVATE** (AKTIVÁLÁS) elemre, és erősítse meg a műveletet.

            > [!NOTE]
            > További információ: [Activating Azure Rights Management](activate-service.md) (Az Azure Rights Management aktiválása).

2.  Új sablon létrehozása:

    -   A klasszikus Azure-portál **Get started with Rights Management** (A Rights Management használatának megkezdése) első lépéseket ismertető lapján kattintson a **Create a new rights policy template** (Új jogmegadási sablon létrehozása) parancsra.

        Ha az Office 365-re vonatkozó utasítások végrehajtása után nem jelenik meg rögtön ez az oldal, használja a klasszikus Azure-portállal kapcsolatban megadott fenti navigációs utasításokat.

3.  Az **Add a new rights policy template** (Új jogmegadási sablon hozzáadása) lapon válassza ki a nyelvet, amelyen be fogja írni a felhasználók számára megjelenő sablonnevet és leírást (később további nyelveket is hozzáadhat). Ezután írjon be egy egyéni nevet és leírást, majd kattintson a Complete (Befejezés) gombra.

A **Get started with Rights Management** (A Rights Management használatának megkezdése) első lépéseket ismertető lapon kattintson a **Manage your rights policy templates** (Jogmegadási sablonok kezelése) elemre. Látni fogja, hogy az újonnan létrehozott sablon **Archived** (Archív) állapotúként jelenik meg a sablonok listáján. Ezen a ponton a sablon létrehozása már megtörtént, azonban még nem lett konfigurálva és nem látható a felhasználók számára.

## Egyéni sablon konfigurálása és közzététele

1.  Válassza ki az újonnan létrehozott sablont a klasszikus Azure-portál **TEMPLATES** (SABLONOK) lapján.

2.  A **Your template has been added** (A sablon hozzáadása megtörtént) első lépéseket ismertető lapon kattintson az 1. lépés, **Configure rights for users and groups** (Felhasználók és csoportok jogosultságainak konfigurálása) **Get started** (Első lépések) lehetőségére, majd kattintson a **GET STARTED NOW** (ELSŐ LÉPÉSEK) vagy az **ADD** (HOZZÁADÁS) parancsra, és válassza ki azokat a felhasználókat és csoportokat, akik jogosultságokkal fognak rendelkezni az új sablon által védett tartalom használatához.

    > [!NOTE]
    > A kiválasztott felhasználóknak vagy csoportoknak rendelkezniük kell e-mail címmel. Éles környezetben ez szinte mindig így lesz, azonban egy egyszerű tesztelési környezetben előfordulhat, hogy hozzá kell majd adnia az e-mail címeket a felhasználói fiókokhoz vagy csoportokhoz.

    Ajánlott eljárásként csoportok használata javasolt felhasználók helyett, mert ez leegyszerűsíti a sablonok kezelését. Ha helyszíni Active Directoryval rendelkezik, és az Azure AD szolgáltatással szinkronizál, használhat levelezési csoportokat, amelyek lehetnek biztonsági csoportok vagy terjesztési csoportok. Ha azonban a szervezet minden felhasználója számára szeretne jogosultságokat biztosítani, hatékonyabb, ha több csoport megadása helyett csak lemásolja az egyik alapértelmezett sablont. További információ: [Sablon másolása](copy-template.md).

    > [!TIP]
    > A sablonhoz a szervezetén kívülről is hozzáadhat felhasználókat („külső felhasználók”) egy Office 365- vagy Exchange Online-névjegyeket tartalmazó levelezési csoport kiválasztásával. Ez lehetővé teszi, hogy ezekhez a felhasználókhoz ugyanúgy rendeljen jogokat, mint saját szervezete felhasználóihoz. Például letilthatja egy ügyfeleknek kiküldött árlista szerkesztését. Ne használja ezt a sablonkonfigurációt e-mailek védelmére, ha a szervezetén kívüli felhasználók az Outlook Web App alkalmazással olvassák a védett leveleket.
    > 
    > Ezen felül a későbbiekben a szervezeten kívülről is hozzáadhat felhasználókat a sablonhoz [az Azure Rights Managementhez készült Windows PowerShell-modul](install-powershell.md) és az alábbi módszerek egyikének használatával:
    > 
    > -  **Sablon frissítése jogosultság-definíciós objektummal**: A külső e-mail-címeket és azok jogosultságait egy jogosultság-definíciós objektumban adhatja meg, amelyet a későbbiekben a sablon frissítésére használhat. A jogosultság-definíciós objektumot úgy adhatja meg, ha a [New-AadrmRightsDefinition](https://msdn.microsoft.com/library/azure/dn727080.aspx) parancsmaggal létrehoz egy változót, majd megadja ezt a változót a [Set-AadrmTemplateProperty](https://msdn.microsoft.com/library/azure/dn727076.aspx) parancsmag -RightsDefinition paramétere számára egy meglévő sablon módosításához. Ha azonban egy meglévő sablonhoz adja hozzá ezeket a felhasználókat, a sablonok meglévő csoportjai számára is meg kell határoznia jogosultság-definíciós objektumokat, nem csak az új, külső felhasználók számára.
    > -  **A frissített sablon exportálása, szerkesztése és importálása**:  Az [Export-AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727078.aspx) parancsmaggal exportálhatja a sablont egy fájlba, amelyet szerkesztve hozzáadhatja ezen felhasználók külső e-mail-címeit és jogosultságait a meglévő csoportokhoz és jogosultságokhoz. Ezután az [Import-AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727077.aspx) parancsmaggal importálhatja vissza a módosítást az Azure RMS szolgáltatásba.

3.  Kattintson a Next (Tovább) gombra, majd rendelje a felsorolt jogosultságok egyikét a kiválasztott felhasználókhoz és csoportokhoz.

    Használja a megjelenő leírást, ha további információra van szüksége az egyes jogosultságokkal (és egyéni jogosultságokkal) kapcsolatban. További részletes információt a [Configuring Usage Rights for Azure Rights Management](configure-usage-rights.md) (Használati jogosultságok konfigurálása az Azure Rights Managementhez) című témakörben is találhat. Eltérő lehet azonban, hogy az RMS szolgáltatást támogató alkalmazások hogyan valósítják meg ezeket a jogosultságokat. Tekintse meg az alkalmazások dokumentációját, és mielőtt üzembe helyezi a sablont a felhasználók számára, végezzen saját teszteket azon alkalmazásokkal, amelyekkel a felhasználók a működést ellenőrzik. Ha a sablont csak a rendszergazdák számára szeretné láthatóvá tenni a tesztelés céljából, állítsa be a sablont részlegsablonná (6. lépés).

4.  Ha a **Custom** (Egyéni) beállítást választotta, kattintson a Next (Tovább) gombra, majd válassza ki az egyéni jogosultságokat.

    Jóllehet az egyes elérhető jogosultságokat bármilyen kombinációban használhatja, bizonyos alkalmazásokban néhány jogosultság más jogosultságtól függhet. Ebben az esetben a függő jogosultságokat a rendszer automatikusan kiválasztja.

    > [!TIP]
    > Érdemes lehet hozzáadni a **Copy and Extract Content** (Tartalom másolása és kinyerése) jogosultságot, és megadni néhány olyan rendszergazdának vagy más szerepkört betöltő személynek, akiknek felelősségi körébe tartozik az adatok visszaállítása. A jogosultság megadása lehetővé teszi, hogy szükség esetén eltávolítsák a védelmet azokról a fájlokról és e-mail üzenetekről, amelyek a jelen sablon használatával védettek lesznek. A védelem sablonszintű eltávolítása részletesebb vezérlést tesz lehetővé, mint a felügyelői funkció használata.

5.  Kattintson a Complete (Befejezés) gombra.

6.  Ha azt szeretné, hogy a sablont csak a felhasználók egy része lássa, amikor megtekintik a sablonok listáját az alkalmazásokban: kattintson a **SCOPE** (HATÓKÖR) elemre, és konfigurálja a sablont részlegsablonként, majd kattintson a **GET STARTED NOW** (ELSŐ LÉPÉSEK) lehetőségre. Egyéb esetben folytassa a 9. lépéssel.

    További információ a részlegsablonokkal kapcsolatban: Alapértelmezés szerint az Azure-címtár mindegyik felhasználója láthatja az összes közzétett sablont, és kiválaszthatja azokat az alkalmazásokból, amikor szeretne megvédeni valamilyen tartalmat. Ha azt szeretné, hogy csak bizonyos felhasználók láthassanak egyes közzétett sablonokat, a sablonokat ezekre a felhasználókra kell korlátoznia. Ezt követően csak ezek a felhasználók választhatják ki ezeket a sablonokat. Nem láthatják, így ki sem választhatják a sablonokat azok a felhasználók, akiket nem adott meg. Ez a technika megkönnyíti a felhasználók számára a megfelelő sablon kiválasztását, különösen amikor adott csoportok vagy részlegek számára kialakított sablonokat hoz létre. A felhasználók csak a számukra kialakított sablonokat látják.

    Tegyük fel, hogy létrehozott egy sablont az emberi erőforrások részleg számára, és a sablon csak olvasási jogosultságot biztosít a pénzügyi részleg tagjainak. Ha azt szeretné, hogy csak az emberi erőforrások részleg alkalmazhassa ezt a sablont a Rights Management megosztóalkalmazás használata során, a sablont az EmberiErőforrások levelezési csoportra kell korlátoznia. A sablont ezt követően csak a csoport tagjai láthatják és alkalmazhatják.

7.  A **TEMPLATE VISIBILITY** (SABLON LÁTHATÓSÁGA) lapon válassza ki azokat a felhasználókat és csoportokat, akik az RMS-kompatibilis alkalmazásokban láthatják és kiválaszthatják majd a sablont. Ahogy korábban is, ajánlott eljárásként csoportok használata javasolt a felhasználók helyett, és a kiválasztott csoportoknak vagy felhasználóknak e-mail címmel kell rendelkezniük.

8.  Kattintson a Next (Tovább) gombra és döntse el, hogy konfigurálnia kell-e az alkalmazáskompatibilitást a részlegsablon számára. Ha igen, kattintson az **APPLICATION COMPATIBILITY** (ALKALMAZÁSKOMPATIBILITÁS) elemre, jelölje be a jelölőnégyzetet, majd kattintson a **Complete** (Befejezés) gombra.

    Miért lehet szükség az alkalmazáskompatibilitás konfigurálására? Nem minden alkalmazás képes támogatni a részlegsablonokat. Ehhez az alkalmazásnak először hitelesítenie kell magát az RMS szolgáltatással a sablonok keltöltése előtt. Ha a hitelesítési folyamat nem megy végbe, alapértelmezés szerint egyetlen részlegsablon letöltése sem történik meg. Ezt a működést felülírhatja, ha megadja, hogy a rendszer minden részlegsablont letöltsön. Ezt az alkalmazáskompatibilitás konfigurálásával és a **Show this template to all users when the applications do not support user identity** (Sablon megjelenítése minden felhasználónak, ha az alkalmazások nem támogatják a felhasználói identitást) jelölőnégyzet bejelölésével érheti el.

    Ha például a részlegsablon számára nem konfigurálja az alkalmazáskompatibilitást az emberi erőforrások részleggel kapcsolatos példában, akkor az RMS megosztóalkalmazás használata során csak az emberi erőforrások részleg felhasználói láthatják majd a részlegsablont, azonban az Outlook Web Access (OWA) Exchange Server 2013 kiszolgálóról történő használata során egyetlen felhasználó sem láthatja a részlegsablont, mert az Exchange OWA és az Exchange ActiveSync jelenleg nem támogatja a részlegsablonokat. Ha az alkalmazáskompatibilitás konfigurálásával felülírja ezt az alapértelmezett működést, akkor az RMS megosztóalkalmazás használata során csak az emberi erőforrások részleg felhasználói láthatják majd a részlegsablont, az Outlook Web Access (OWA) használata során azonban az összes felhasználó számára látható lesz. Ha a felhasználók az Exchange Online szolgáltatásból használják az OWA vagy az Exchange ActiveSync szolgáltatást, a sablonnak az Exchange Online szolgáltatásbeli állapotától (archív vagy közzétett) függően vagy az összes felhasználó látja majd a részlegsablonokat vagy egyik felhasználó sem láthatja azokat.

    Az Office 2016 natív módon támogatja a részlegsablonokat, ahogyan az Office 2013 is a 15.0.4727.1000-es verziótól kezdve, amely 2015 júniusában lett kibocsátva a [KB 3054853](https://support.microsoft.com/kb/3054853) részeként.

    > [!NOTE]
    > Ha olyan alkalmazásokkal rendelkezik, amelyek még nem támogatják natív módon a részlegsablonokat, egy egyéni RMS-sablonletöltési parancsfájllal vagy más eszközökkel üzembe helyezheti ezeket a sablonokat a helyi RMS-ügyfélmappában. Ezután ezek az alkalmazások helyesen, csak a sablon hatóköréhez kiválasztott felhasználók és csoportok számára jelenítik majd meg a részlegsablonokat:
    > 
    > -   Office 2010 esetén az ügyfélmappa a **%localappdata%\Microsoft\DRM\Templates**.
    > -   Ha egy ügyfélszámítógép már letöltötte az összes sablont, az ügyfélszámítógépen másolhatja, majd beillesztheti a sablonfájlokat más számítógépekre.
    > 
    > [Az egyéni RMS-sablonparancsfájlt a Microsoft Connect webhelyről töltheti le](http://go.microsoft.com/fwlink/?LinkId=524506). Ha a hivatkozásra kattintva hiba jelenik meg, valószínűleg még nem regisztrált a Microsoft Connect webhelyen. Regisztráció:
    > 
    > 1.  Nyissa meg a [Microsoft Connect webhelyet](http://www.connect.microsoft.com), és jelentkezzen be Microsoft-fiókjával.
    > 2.  Kattintson a **Jegyzék** elemre, és válassza az **Azoknak a Connect-termékeknek a megjelenítése, amelyekhez most nem küldhető be visszajelzés** kategóriát.
    > 3.  Keresse meg a **Rights Management Services** terméket, és a **Microsoft RMS Enterprise Features** program mellett kattintson a **Csatlakozás** lehetőségre.

9. Kattintson a **KONFIGURÁLÁS** lehetőségre, és adjon hozzá további, a felhasználók által használt nyelveket a sablon nevével és leírásával az adott nyelven. Különböző nyelveken beszélő felhasználók esetén fontos, hogy a felhasználók által használt nyelvek mindegyikét hozzáadja, és megadjon egy nevet és egy leírást az adott nyelveken. A felhasználók ekkor ugyanazon a nyelven láthatják a sablon nevét és leírását, mint amelyet az ügyfélszámítógép operációs rendszere használ, így biztosan megértik majd a dokumentumokra vagy e-mail üzenetekre alkalmazott házirendet. Ha nem érhető el az ügyfélszámítógép operációs rendszerével azonos nyelv, a megjelenő név és leírás visszavált arra a nyelvre és leírásra, amelyet a sablon kezdeti létrehozásakor megadott.

    Ezután ellenőrizze, hogy szeretné-e módosítani az alábbi beállításokat:

    |Beállítás|További információ|
    |-----------|--------------------|
    |**tartalom lejárata**|Adja meg azon dátumot vagy napok számát a sablon számára, amikor a sablon által védett fájlok nem nyithatók meg. Meghatározhatja a pontos dátumot, vagy a fájlra alkalmazott védelem időpontjától számított napok számát.<br /><br />Dátum megadása esetén az érvényesség az aktuális időzónában, éjfélkor lép életbe.|
    |**offline elérés**|Ezzel a beállítással kiegyensúlyozhat bármilyen olyan biztonsági követelményt, amelyet azzal a követelménnyel szemben támasztott, hogy a felhasználók meg tudjanak nyitni védett fájlokat, amikor nincs internetkapcsolatuk.<br /><br />Ha megadja, hogy a tartalom ne legyen elérhető internetkapcsolat nélkül, illetve hogy a tartalom csak adott számú napig legyen elérhető, akkor a küszöbérték elérése esetén a felhasználókat újra hitelesíteni kell, és hozzáférésüket a rendszer naplózza. Ebben az esetben, ha a felhasználók hitelesítő adatai nem lettek gyorsítótárazva, a felhasználókat a rendszer arra kéri, hogy a fájl megnyitásához jelentkezzenek be.<br /><br />Az ismételt hitelesítés mellett a házirend és a felhasználói csoporttagság újraértékelése is megtörténik. Ez azt jelenti, hogy a felhasználók különböző eredménnyel érhetik el ugyanazt a fájlt, ha a házirend vagy a csoporttagság megváltozott azóta, hogy utoljára hozzáfértek a fájlhoz.|

10. Amikor biztos abban, hogy a sablont megfelelően konfigurálta a felhasználók számára, kattintson a **PUBLISH** (KÖZZÉTÉTEL) elemre, hogy a sablon láthatóvá váljon a felhasználók számára, majd kattintson a **SAVE** (MENTÉS) parancsra.

11. A klasszikus portál Back (Vissza) gombjára kattintva visszatérhet a **TEMPLATES** (SABLONOK) lapra, ahol a sablonnál most már a frissített **Published** (Közzétett) állapot jelenik meg.

A sablon módosításához válassza ki a sablont, és hajtsa végre újra az első lépések lépéseit. Vagy válasszon az alábbi lehetőségek közül:

-   További felhasználók és csoportok hozzáadása, illetve ezen felhasználók és csoportok jogosultságainak megadása: Kattintson a **RIGHTS** (JOGOSULTSÁGOK), majd az **ADD** (HOZZÁADÁS) elemre.

-   Korábban kiválasztott felhasználók vagy csoportok eltávolítása: Kattintson a **RIGHTS** (JOGOSULTSÁGOK) lehetőségre, válassza ki a listában az adott felhasználót vagy csoportot, majd kattintson a **DELETE** (TÖRLÉS) parancsra.

-   Annak a módosítása, hogy mely felhasználók láthatják és választhatják ki a sablonokat az alkalmazásokból: Kattintson a **SCOPE** (HATÓKÖR), majd az **ADD** (HOZZÁADÁS) vagy a **DELETE** (TÖRLÉS) vagy az **APPLICATION COMPATIBILITY** (ALKALMAZÁSKOMPATIBILITÁS) lehetőségre.

-   A sablon elrejtése az összes felhasználó elől: Kattintson a **CONFIGURE** (KONFIGURÁLÁS), az **ARCHIVE** (ARCHIVÁLÁS), majd a **SAVE** (MENTÉS) parancsra.

-   Egyéb konfigurációs módosítások végrehajtása: Kattintson a **CONFIGURE** (KONFIGURÁLÁS) elemre, hajtsa végre a módosításokat, és kattintson a **SAVE** (MENTÉS) parancsra.

> [!WARNING]
> Ha egy korábban mentett sablont módosít, az ügyfeleknél csak akkor jelennek meg ezek a módosítások, ha a sablonok frissítése megtörtént a számítógépeken. További információk: [Sablonok frissítése a felhasználók számára](refresh-templates.md).

## Lásd még:
[Egyéni sablonok konfigurálása az Azure Rights Management szolgáltatáshoz](configure-custom-templates.md)


<!--HONumber=Jul16_HO3-->


