---
# kötelező metaadatok

cím: Azure RMS gyors üzembe helyezési útmutató – 5. lépés | Azure RMS leírás: Az utolsó lépése annak az oktatóanyagnak, amellyel gyorsan kipróbálhatja a szervezeténél a Microsoft Azure Rights Managementet csupán öt, 15 percnél gyorsabban végrehajtható lépéssel.
keywords: author: cabailey manager: mbaldwin ms.date: 05/09/2016 ms.topic: get-started-article ms.prod: azure ms.service: rights-management ms.technology: techgroup-identity ms.assetid: aa06826d-c227-449b-93ea-6ce394608997

# opcionális metaadatok

ROBOTS: audience: ms.devlang: ms.reviewer: esaggese ms.suite: ems ms.tgt_pltfrm: ms.technology: ms.custom:

---


# Azure RMS gyors üzembe helyezése 5. lépés: A védett dokumentum nyomon követése

*A következőkre vonatkozik: Azure Rights Management, Office 365*


Ugrás ide: 
> [!div class="op_single_selector"]
- [Bevezetés](quick-start-tutorial.md)
- [1. lépés: Az Azure RMS aktiválása](tutorial-step1.md)
- [2. lépés: Az RMS megosztóalkalmazás telepítése](tutorial-step2.md)
- [3. lépés: A bizalmas dokumentum elküldése e-mailben](tutorial-step3.md)
- [4. lépés: A címzett elolvassa a dokumentumot](tutorial-step4.md)
- [5. lépés: A dokumentum nyomon követése](tutorial-step5.md)

![Azure RMS gyors üzembe helyezési útmutató 5. lépés](../media/AzRMS_QuickStartSteps5.PNG)

> [!NOTE]
> Ehhez a lépéshez rendelkeznie kell egy dokumentumkövetést támogató előfizetéssel. Annak ellenőrzése, hogy az előfizetés tartalmazza-e a dokumentumkövetést: [Comparison of Rights Management Services (RMS) Offerings](https://technet.microsoft.com/dn858608.aspx) (A Tartalomvédelmi szolgáltatásokra (RMS) vonatkozó ajánlatok összehasonlítása).

Ez a lépés opcionális, de a legtöbben szeretik tudni, hogy az általuk elküldött mellékleteket megnyitották-e, és ha igen, mikor és honnan. Példa:

-   Adott időre választ vár valakitől és a dokumentumkövető webhelyről látja, hogy a címzett nem nyitotta meg a dokumentumot, bár közeleg a határidő. Másik e-mailt küld vagy felhívja, hogy időben emlékeztesse.

-   Miután látja, hogy valaki megnyitotta a dokumentumot, megkérdezi a címzettet, hogy van-e kérdése vagy további információra van-e szüksége.

![Útmutató 5. lépésének képernyőképei](../media/AzRMS_Tutorial_5_Screenshots.png)

### A védett dokumentum nyomon követése

1.  Az Outlookban a **Kezdőlapon** az **RMS** csoportban kattintson a **Használat követése** menüpontra.

2.  Ha megjelenik a **Védelem és megosztás saját igényei szerint** oldal, kattintson a **Bejelentkezés** lehetőségre, és adja meg ismét a felhasználónevét és a jelszavát.

3.  A **Megosztott dokumentumok** oldalon láthatja az e-mailhez csatolt **Confidential.docx** dokumentumot. Ekkor csak ez a fájl jelenik meg, de további bizalmas dokumentumok megosztásakor a lista nő.

    Ezen az oldalon láthatja, mikor osztotta meg a dokumentumot (mikor küldte el az e-mailt a védett melléklettel), a legutolsó tevékenység dátumát és az e-mail címzettjének nevét. További részletekért kattintson a dokumentum nevére.

4.  Az új oldalon, amelynek a neve azon fájl neve, amelyre kattintott, csak a dokumentum összegző részleteit láthatja, valamint a dokumentumhoz elérhető egyéb lehetőségek listáját (**Lista**, **Idővonal**, **Térkép**, **Beállítások**).

    Kattintson az egyes elemekre a védett dokumentum nyomon követése különböző módjainak felderítéséhez. Másik lehetőségként továbbra is az **Összegzés** lapon kattintson a **Megnyitás Excelben** gombra, hogy az információkat táblázatba exportálja, vagy kattintson a **Hozzáférés visszavonása** gombra a dokumentum megosztásának leállításához.

Visszatérhet erre a webhelyre a védett dokumentum további tevékenységeinek nyomon követéséhez vagy szükség esetén a hozzáférés visszavonásához. A mobileszközéről vagy táblagépéről is elérheti a webhelyet, ha egy böngészőben a következő hivatkozást használja: [dokumentumkövetés](http://go.microsoft.com/fwlink/?LinkId=529562)

|Ha további információra van szüksége|További információ|
|--------------------------------|--------------------------|
|Részletes utasítások a dokumentumkövetéshez|[Dokumentumok nyomon követése és visszavonása az RMS-megosztó alkalmazás használata során](../rms-client/sharing-app-track-revoke.md)|
|Egy kétperces videó ismerteti és bemutatja a dokumentumkövetést|[Azure RMS dokumentumkövetés és visszavonás](http://channel9.msdn.com/Series/Information-Protection/Azure-RMS-Document-Tracking-and-Revocation)|
|Hibaelhárításhoz és ügyfélkérdések esetén|[A dokumentumkövetéssel kapcsolatos gyakori kérdések](https://technet.microsoft.com/dn947488)|

### További lépések
Ez az oktatóanyag csak egy forgatókönyvön vezette át, amelynek során az Azure RMS az adatok védelmét segítette. A többi gyakori használati mód megtekintéséhez olvassa el [Az Azure RMS működés közben](../understand-explore/what-admins-users-see.md) című szakaszt a [Mi az az Azure Rights Management?](../understand-explore/what-is-azure-rms.md) fejezetben Ezen cikk más szakaszait is hasznosnak találhatja, például azzal kapcsolatban, hogyan működik az Azure RMS és milyen üzleti problémákat tud megoldani.

Ha készen áll az Azure RMS központi telepítésére, az [Azure Rights Management üzembe helyezési menetrend](../plan-design/deployment-roadmap.md) felkeresésével megismerheti a telepítés lépéseit, valamint ugyanitt megtalálja az útmutatókra mutató hivatkozásokat is.

Emellett az adott forgatókönyveket, a társított konfigurációs lépéseket és a végfelhasználói dokumentációt a [Gyors üzembe helyezési útmutató az Azure Rights Management szolgáltatáshoz](../get-started/rapid-deployment-guide.md) szakaszban találja.

>[!div class="step-by-step"] [Bevezetés](quick-start-tutorial.md)
[1. lépés](tutorial-step1.md)
[2. lépés](tutorial-step2.md)
[3. lépés](tutorial-step3.md)
[4. lépés](tutorial-step4.md)
*5. lépés*


<!--HONumber=May16_HO2-->


