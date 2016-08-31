---
title: "Azure RMS gyors üzembe helyezési útmutató – 3. lépés | Azure RMS"
description: "A harmadik lépése annak az oktatóanyagnak, amellyel gyorsan kipróbálhatja a szervezeténél a Microsoft Azure Rights Managementet csupán 5, 15 percnél gyorsabban végrehajtható lépéssel."
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 08/24/2016
ms.topic: get-started-article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: c604e749-8918-40e8-8148-6bd000cb2be2
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 024a29d7c7db2e4c0578a95c93e22f8e7a5b173e
ms.openlocfilehash: 62b2303074ccf2b23e29a5770f51b003c8f97780


---


# Azure RMS gyors üzembe helyezés – 3. lépés: Küldje el e-mailben a dokumentumot, amelyet védelemmel szeretne ellátni

>*A következőkre vonatkozik: Azure Rights Management, Office 365*


Ugrás ide: 
> [!div class="op_single_selector"]
- [Bevezetés](quick-start-tutorial.md)
- [1. lépés: Az Azure RMS aktiválása](tutorial-step1.md)
- [2. lépés: Az RMS megosztóalkalmazás telepítése](tutorial-step2.md)
- [3. lépés: A bizalmas dokumentum elküldése e-mailben](tutorial-step3.md)
- [4. lépés: A címzett elolvassa a dokumentumot](tutorial-step4.md)
- [5. lépés: A dokumentum nyomon követése](tutorial-step5.md)


Ehhez a lépéshez először készítsen és mentsen el egy **Confidential.docx** elnevezésű dokumentumot a Word használatával. Ez fogja jelképezni a dokumentumot, amely számára védelmet kíván biztosítani. A jelen oktatóanyag esetében nem számít, hogy pontosan milyen szöveg kerül a fájlba, de mindenképpen érdemes valamilyen szöveget tartalmaznia, mert úgy könnyebben ellenőrizhető, hogy a hitelesített címzett el tudta-e olvasni. A dokumentum szövege például a következő lehet: **Ha az e-mail-melléklet tartalmát el tudja olvasni, a küldő sikeresen osztotta meg az Azure RMS-védelemmel ellátott fájlt.**

Ezek után készen áll a dokumentum biztonságos, e-mailen keresztül történő megosztására.

![Azure RMS gyors üzembe helyezési útmutató 3. lépés](../media/AzRMS_Tutorial_3_Screenshots.png)

### A dokumentum biztonságos, e-mailen keresztül történő megosztása

1.  Outlook használata esetén hozzon létre egy új üzenetet, és csatolja az imént készített fájlt.

2.  A **Címzett** mezőbe írjon be egy vagy több üzleti e-mail-címet. Győződjön meg róla, hogy üzleti e-mail-címet adott meg (például **janetm@contoso.com** vagy **p.dover@fabrikam.com**), mert az Azure Rights Management jelenleg nem támogatja a személyes e-mail-címeket, amelyek otthonról, egy internetszolgáltatón keresztül használhatóak. Nem fontos, hogy a címzett is rendelkezik-e Azure Rights Managementtel vagy sem.

3.  Írja be a tárgyat, például **Bizalmas dokumentum**, majd írjon egy rövid üzenetet az e-mail törzsébe, például **Kérem, olvassa el ezt a bizalmas dokumentumot, és ne ossza meg másokkal.**

4.  Ezt követően kattintson az **Üzenet** lap **RMS** csoportjának **Védett megosztás** elemére, majd kattintson újra a **Védett megosztás** elemre:

5.  A **Védett megosztás** párbeszédpanelen:

    1.  Válassza a **Megtekintő – Csak megtekintés** beállítást.

        Ez azt jelenti, hogy a címzettek megtekinthetik a dokumentumot, de nem szerkeszthetik vagy nyomtathatják ki.

    2.  Jelölje be az **E-mailt kérek a dokumentumok megnyitási kísérleteiről** jelölőnégyzetet.

        Minden alkalommal e-mail értesítést kap, ha a címzettek megpróbálják megnyitni a mellékletet, valamint akkor is, ha valaki más próbálja megnyitni azt, például ha az egyik címzett továbbította az e-mailt egy munkatársának. Ez utóbbi esetben látni fogja, hogy a hozzáférés meg lett tagadva, és a felhasználói adatokból eldöntheti, hogy szeretne-e egy megnyitható másolatot küldeni a dokumentumról ennek a személynek.

    3.  Jelölje be az **Azonnal vissza lehessen vonni a dokumentumokhoz való hozzáférést** jelölőnégyzetet.

        Ehhez a beállításhoz az szükséges, hogy a címzettek minden egyes alkalommal rendelkezzenek internetkapcsolattal, amikor megnyitják a mellékletet, viszont azzal az előnnyel jár, hogy ha a későbbiekben visszavonja a dokumentumot, akkor a legközelebb alkalommal már nem fogják tudni megnyitni azt. Ha nem választja ki ezt a beállítást, akkor a címzettek akár internetkapcsolat nélkül is megnyithatják a mellékletet, ennek a hátránya azonban az, hogy ha a dokumentumot a későbbiekben visszavonja, akkor lehetséges, hogy az csak késéssel lép érvénybe.

    4.  Kattintson az **Azonnali küldés** parancsra.

        A rendszer elküldi a melléklettel ellátott e-mailt a megadott e-mail-címekre. Az e-mail-üzeneten kívül utasításokat is látni fognak majd arra vonatkozóan, hogy hogyan olvashatják el az Azure Rights Management által védett csatolt dokumentumot.

Miután elküldte a védett dokumentumot, megkérheti a címzetteket, hogy várják meg, amíg megérkezik, és nyissák meg. Az Outlookot azonban ne zárja be, mert az utolsó lépésben ismét igénybe vesszük a melléklet nyomon követéséhez.

|Ha további információra van szüksége|További információ|
|--------------------------------|--------------------------|
|Teljes útmutatás és alternatív módszerek az e-mailben megosztani kívánt fájlok védelméhez|[E-mailben megosztott fájl védelme a Rights Management megosztóalkalmazással](../rms-client/sharing-app-protect-by-email.md)|
|A **védett megosztás** párbeszédpanelen megjelenő beállítások|[A Rights Management megosztóalkalmazás párbeszédpanel-beállításai](../rms-client/sharing-app-dialog-box.md)|


>[!div class="step-by-step"]
[« 2. lépés](tutorial-step2.md)
[4. lépés »](tutorial-step4.md)


<!--HONumber=Aug16_HO4-->


