---
# kötelező metaadatok

cím: Azure RMS gyors üzembe helyezési útmutató – 4. lépés | Azure RMS leírás: A negyedik lépése annak az oktatóanyagnak, amellyel gyorsan kipróbálhatja a szervezeténél a Microsoft Azure Rights Managementet csupán öt, 15 percnél gyorsabban végrehajtható lépéssel.
keywords: author: cabailey manager: mbaldwin ms.date: 04/28/2016 ms.topic: get-started-article ms.prod: azure ms.service: rights-management ms.technology: techgroup-identity ms.assetid: f8340056-87a1-4daa-8b63-3d95fc381b9c

# opcionális metaadatok

ROBOTS: audience: ms.devlang: ms.reviewer: esaggese ms.suite: ems ms.tgt_pltfrm: ms.technology: ms.custom:

---


# Gyors üzembe helyezési oktatóanyag az Azure RMS használatához – 4. lépés: A címzettek felkérése az e-mailben elküldött dokumentum megnyitására

*A következőkre vonatkozik: Azure Rights Management, Office 365*


Ugrás ide: 
> [!div class="op_single_selector"]
- [Bevezetés](quick-start-tutorial.md)
- [1. lépés: Az Azure RMS aktiválása](tutorial-step1.md)
- [2. lépés: Az RMS megosztóalkalmazás telepítése](tutorial-step2.md)
- [3. lépés: A bizalmas dokumentum elküldése e-mailben](tutorial-step3.md)
- [4. lépés: A címzett elolvassa a dokumentumot](tutorial-step4.md)
- [5. lépés: A dokumentum nyomon követése](tutorial-step5.md)


![Azure RMS gyors üzembe helyezési útmutató 4. lépés](../media/AzRMS_QuickStartSteps4.PNG)

A címzettek számos eszközön olvashatják el az e-mail-mellékletként elküldött védett dokumentumot. Ilyen eszközök például az iPad, iPhone készülékek, az Android rendszerű táblagépek és telefonok, Mac számítógépek és Windows rendszerű számítógépek.

Kérje meg a címzetteket az elküldött e-mail-üzenet elolvasására. Az e-mail-üzenet megtekintése előtt az alábbi szöveget látják majd:

**A mellékleteket a feladó Microsoft RMS-védelemmel látta el. A megnyitásukhoz ** [be kell jelentkeznie](http://aka.ms/rms)
      **.**

Amikor a címzettek a hivatkozásra kattintanak, utasítások jelennek meg, amelyek az RMS megosztóalkalmazás telepítésére, és ha szükséges, egy ingyenes fiók regisztrálására kérik fel őket. Az ingyenes fiók előfizetést biztosít az RMS egyéni felhasználók számára szolgáltatáshoz, ami lehetővé teszi, hogy a jogosult felhasználók mindig elolvashassák a védett dokumentumokat, még akkor is, ha a szervezetük nem rendelkezik Azure RMS-el. A címzettek ezután készen állnak a védett fájl elolvasására az alábbi utasításokat követve.

![Útmutató 4. lépésének képernyőképei](../media/AzRMS_Tutorial_4_Screenshots.png)

### A csatolt védett dokumentum megtekintése

1.  Mivel az Azure Rights Management védi a Word-dokumentumot, két melléklet tartozik az e-mail-üzenethez. A mellékletek valójában ugyanazon fájl két verziója eltérő kiterjesztéssel. Nyissa meg a **.ppdf** kiterjesztéssel rendelkező verziót (**Bizalmas.ppdf**).

    Amennyiben az [Office olyan verziója fut az eszközön, amely támogatja a Rights Managementet](https://technet.microsoft.com/library/dn655136.aspx), megnyithatja a fájl másik verzióját (**Bizalmas.docx**), amely így a Wordben nyílik meg.

2.  Ha a rendszer a felhasználónevet és jelszót kéri, felhasználónévként azt az e-mail-címet adja meg, amelyre az e-mail és a melléklet el lett küldve. Például: **janetm@contoso.com** vagy **p.dover@fabrikam.com**. Jelszóként azt a jelszót írja be, amelyet az RMS egyéni felhasználók számára szolgáltatásra való regisztráláskor adott meg. Ha a szervezet rendelkezik az Azure RMS-sel, adja meg a szokásos munkahelyi jelszót.

A dokumentum megnyílik, és elolvashatja a tartalmát. A dokumentum szövege például a következő lehet: **Ha az e-mail-melléklet tartalmát el tudja olvasni, a küldő sikeresen osztotta meg az Azure RMS-védelemmel ellátott fájlt.** Mivel a fájl írásvédett, a tartalma nem módosítható.

További lépésként megkérheti a címzettet, hogy továbbítsa az e-mailt más olyan személyek számára, akiknek nem küldte el az eredeti e-mailt. Ezen személyek akkor sem nyithatják meg a mellékletet, ha olyan szervezetnél dolgoznak, amely rendelkezik az Azure Rights Managementtel, vagy saját előfizetést igényelnek az RMS egyéni felhasználók számára szolgáltatáshoz. Amikor meg kell adniuk a felhasználónevüket, a dokumentumhoz való hozzáférésüket a rendszer megtagadja.

Most, hogy a címzett megnyitotta a mellékletet, és esetleg továbbította azt valaki más számára, e-mail-értesítést fog kapni erről a tevékenységről. Az e-mail-üzenetek idővel hajlamosak elkallódni, így annak követésére, hogy ki fért hozzá a dokumentumhoz, célszerűbb a dokumentumkövetési webhelyet használni, amit az utolsó lépésben tárgyalunk.

|Ha további információra van szüksége|További információ|
|--------------------------------|--------------------------|
|Átfogó utasítások az Azure Rights Management által védett fájlok megtekintéséhez|[A Rights Management szolgáltatásban védetté tett fájlok megtekintése és használata](../rms-client/sharing-app-view-use-files.md)|
|Információk az RMS egyéni felhasználók számára szolgáltatásra szóló ingyenes előfizetéséről|[RMS for Individuals and Azure Rights Management (RMS egyéni felhasználók számára és Azure Rights Management)](../understand-explore/rms-for-individuals.md)|
|Információk az e-mail-üzenethez csatolt fájl két verziójáról|[Mi az az automatikusan létrehozott .ppdf-fájl?](../rms-client/sharing-app-dialog-box.md#what-s-the-ppdf-file-that-s-automatically-created-)|


>[!div class="step-by-step"] [« 3. lépés](tutorial-step3.md)
[5. lépés »](tutorial-step5.md)

<!--HONumber=May16_HO2-->


