![](../media/AzRMS_QuickStartSteps3.PNG)

Ehhez a lépéshez először készítsen és mentsen el egy **Confidential.docx** elnevezésű dokumentumot a Word használatával. Ez fogja jelképezni a dokumentumot, amely számára védelmet kíván biztosítani. A jelen oktatóanyag esetében nem számít, hogy pontosan milyen szöveg kerül a fájlba, de mindenképpen érdemes valamilyen szöveget tartalmaznia, mert úgy könnyebben ellenőrizhető, hogy a hitelesített címzett el tudta-e olvasni. A dokumentum szövege például a következő lehet: **Ha az e-mail-melléklet tartalmát el tudja olvasni, a küldő sikeresen osztotta meg az Azure RMS-védelemmel ellátott fájlt.**

Ezek után készen áll a dokumentum biztonságos, e-mailen keresztül történő megosztására.

![Azure RMS-megosztás e-mailben küldött képernyőképekkel](../media/AzRMS_Tutorial_3_Screenshots.png)

#### A dokumentum biztonságos, e-mailen keresztül történő megosztása

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
|Teljes útmutatás és alternatív módszerek az e-mailben megosztani kívánt fájlok védelméhez   →|[E-mailben megosztott fájl védelme a Rights Management megosztóalkalmazással](../rms-client/sharing-app-protect-by-email.md)|
|A **védett megosztás** párbeszédpanelen megjelenő beállítások   →|[A Rights Management megosztóalkalmazás párbeszédpanel-beállításai](../rms-client/sharing-app-dialog-box.md)|


<!--HONumber=Jun16_HO4-->


