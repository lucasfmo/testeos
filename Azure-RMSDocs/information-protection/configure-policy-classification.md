---
title: "Az Azure Information Protection automatikus és javasolt besorolási feltételeinek konfigurálása | Azure Rights Management"
description: "A címkék feltételeinek konfigurálásakor automatikusan elláthat egy dokumentumot vagy e-mailt egy címkével,  vagy megkérheti a felhasználókat, hogy az Ön által javasolt címkét használják."
manager: mbaldwin
ms.date: 08/29/2016
ms.topic: article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: e915f959-eafb-4375-8d2c-2f312edf2d29
translationtype: Human Translation
ms.sourcegitcommit: 87069b73e5f8959955b9967070bd3bcb5e7dc196
ms.openlocfilehash: 357b012bd8679d7e24bfe3ae40c3160e4b69c01f


---

# Az Azure Information Protection automatikus és javasolt besorolási feltételeinek konfigurálása

>*A következőkre vonatkozik: az Azure Information Protection előzetes verziója*

**[ Előzetes információ, a tartalma változhat. ]**

A címkék feltételeinek konfigurálásakor automatikusan elláthat egy dokumentumot vagy e-mailt egy címkével,  vagy megkérheti a felhasználókat, hogy az Ön által javasolt címkét használják: 

- Az automatikus besorolás az elmentett Word-, Excel- és PowerPoint-fájlokra, valamint az Outlookból elküldött e-mailekre vonatkozik. Az automatikus besorolás nem alkalmazható a korábban manuálisan megcímkézett fájlokra.
 
- A javasolt besorolás az elmentett Word-, Excel- és PowerPoint-fájlokra vonatkozik.

A feltételek konfigurálásakor előre meghatározott mintákat használhat, ilyen például a „Credit card numbers” (Bankkártyaszámok) vagy az „USA Social Security Number” (USA-beli társadalombiztosítási szám). Egyéni karakterláncot vagy mintát is megadhat az automatikus besorolás feltételeként. Ezek a feltételek a dokumentumok és e-mailek szövegtörzsére, fejlécére és láblécére vonatkoznak. A feltételekről további információt az [Tájékoztatás a beépített feltételekről](#information-about-the-built-in-conditions) szakaszban találhat.

A több címkére vonatkozó feltételek értékelésének módja:

1. A címkék a szabályzatban megszabott helyzetük alapján kerülnek értékelésre: az első helyen álló címke a legkevésbé bizalmas, az utolsó helyen álló címke pedig a leginkább bizalmas.

2. A program a leginkább bizalmas címkét alkalmazza.
 
3. A program az utolsó alcímkét alkalmazza.

> [!TIP]
>A legjobb felhasználói élmény és az üzletmenet folytonosságának biztosítása érdekében javasoljuk, hogy ne az automatikus besorolással kezdjen, hanem a felhasználók által javasolt besorolással. Ezzel a konfigurációval a felhasználók elfogadhatják a címkézési vagy védelmi műveletet, vagy felülírhatják a dokumentumhoz vagy e-mailhez nem megfelelő javaslatokat.

Íme egy egyéni házirendtippes példaüzenet, amely azt az esetet szemlélteti, amikor javasolt műveletként alkalmazandó címkével konfigurál egy feltételt:

![Azure Information Protection észlelés és javaslat](../media/info-protect-recommend-callouts.png)

Ebben a példában a felhasználó a **Change now** (Módosítás) gombra kattintva alkalmazhatja a javasolt címkét, vagy felülírhatja a javaslatot a menüsáv bezárásával.

## Címkék javasolt és automatikus besorolásainak konfigurálása

1. Ha még nem tette meg, jelentkezzen be az [Azure Portalra](https://portal.azure.com), majd lépjen az **Azure Information Protection** panelre. 
    
    A Központ menüben kattintson a **Tallózás** gombra, és kezdje el begépelni az **Information** szót a Szűrő mezőbe. Válassza az **Azure Information Protection** lehetőséget.

2. Az **Azure Information Protection** panelen jelölje ki a javasolt vagy automatikus besorolásra konfigurálni kívánt címkét.

3. A **Label** (Címke) panel **Configure conditions for automatically applying this label** (A címke automatikus alkalmazásához kapcsolódó feltételek konfigurálása) részén kattintson az **Add a new condition** (Új feltétel hozzáadása) elemre.

4. A **Condition** (Feltétel) panelen válassza a **Built-in** (Beépített) lehetőséget, ha egy előre meghatározott feltételt szeretne alkalmazni, vagy a **Custom** (Egyéni) lehetőséget, ha saját feltételt szeretne megszabni, majd kattintson a **Save** (Mentés) gombra:

    - A **Built-in** (Beépített) lehetőség esetében: Válasszon az elérhető feltételek közül, és adja meg az előfordulások minimális számát, valamint azt, hogy az egyedi értékekkel ellátott előfordulások is beleszámítsanak-e a számolásba.
        
        A feltételek észlelési szabályaival kapcsolatban további információt és példákat a [Tájékoztatás a beépített feltételekről](#information-about-the-built-in-conditions) című szakaszban találhat.

    - A **Custom** (Egyéni) lehetőség esetében: Adjon meg egy keresendő nevet és kifejezést, amely nem tartalmazhat idézőjelet vagy speciális karaktereket. Ezután adja meg, hogy a program reguláris kifejezésekre keressen-e, figyelembe vegye-e a kis- és nagybetűket és adja meg az előfordulások minimális számát, valamint azt, hogy az egyedi értékekkel ellátott előfordulások is beleszámítsanak-e a számolásba.
        
    **Példa az előfordulási beállításokra**: Tegyük fel, hogy Ön a beépített, TAJ szám beállítást választja, az előfordulások minimális számának 2-t ad meg, és az egyik dokumentumban kétszer szerepel ugyanaz a TAJ szám: Ha a **Count occurrences with unique values only** (Csak az egyéni értékkel ellátott előfordulások száma) beállítást **bekapcsolja**, a feltétel nem teljesül; azonban ha ezt a beállítást **kikapcsolja**, a feltétel teljesül.

5. A **Label** (Címke) panelen konfigurálja a következő beállításokat, és kattintson **Save** (Mentés) gombra:

    - Az automatikus vagy javasolt besorolás kiválasztása: A **Select how this label is applied: automatically or recommended to user** (Válassza ki a címke alkalmazási módját: automatikus vagy a felhasználónak javasolt) résznél válassza az **Automatic** (Automatikus) vagy a **Recommended** (Javasolt) lehetőséget.

    - A felhasználónak megjelenített üzenet vagy házirendtipp szövegének megadása: Tartsa meg az alapértelmezett szöveget, vagy írjon be egy újat.

6. A módosításokat az **Azure Information Protection** panel **Publish** (Közzététel) lehetőségével teheti elérhetővé a felhasználóknak.

## Tájékoztatás a beépített feltételekről

A próbaidőszak alatt az alábbi feltételekből választhat:

- [SWIFT-kód](#swift-code )

- [Bankkártyaszám](#credit-card-number )

- [ABA átutalási kód](#aba-routing-number )

- [USA-beli társadalombiztosítási szám (SSN)](#usa-social-security-number-ssn)

- [Nemzetközi bankszámlaszám (IBAN)](#international-banking-account-number-iban)


### SWIFT-kód

Ezt az adattípust az alábbi tartalmak esetén használja:  

1. Az alábbi kifejezések egyike: **swift**, **swiftnumber**, **swiftroutingnumber** 

2. A Swift-kód formátuma:  

    a. 4 betű (bankkód)  

    b. 2 betű (országkód)  

    c. 2 betű vagy szám (helykód)  

    d. 3 betű vagy szám (fiókkód) – nem kötelező  


Tesztelési példák:

- **NEDSZAJJXXX Swiftroutingnumber**

- **NEDSZAJJ100 Swiftnumber** 

----


### Bankkártyaszám

Ezt az adattípust az alábbi tartalmak esetén használja:  

- Érvényes, formázott vagy formázatlan bankkártyaszám, amely megfelel a [Luhn-algoritmusnak](https://wikipedia.org/wiki/Luhn_algorithm). Ez az adattípus az összes világszerte használt bankkártyát felismeri, beleértve a Visa, MasterCard, Discover Card, American Express és Diners kártyákat is.

    - **Formázott**:
    
        - 16 számjegy: (dddd-dddd-dddd-dddd)  
        
    - **Formázatlan**:
    
        - (dddddddddddddddd)  


Tesztelési példák:

- **4242-4242-4242-4242**

- **4242424242424242** 

----

### ABA átutalási kód

Ezt az adattípust az alábbi tartalmak esetén használja:  

1. Az alábbi kifejezések közül legalább egy: **aba**, **rtn**, **routing number** 

2. Egy 9 számjegyű, formázott vagy formázatlan ABA átutalási kód: 

    - **Formázott**: 
        
        a. Négy számjegy, amely az alábbi számok egyikével kezdődik: 0, 1, 2, 3, 6, 7 vagy 8 
        
        b. Kötőjel 
        
        c. Négy számjegy 
        
        d. Kötőjel 
        
        e. Egy számjegy 
        
        Például: 3456-9876-1 ABA 
        
    - **Formázatlan**: 
        
        Kilenc számjegy, amely az alábbi számok egyikével kezdődik: 0, 1, 2, 3, 6, 7 vagy 8 
        
        Például: 345698761 RTN 
 

Tesztelési példák:

- **3456-9876-1 ABA**

- **345698761 RTN** 

----

### USA-beli társadalombiztosítási szám (SSN)

Ezt az adattípust az alábbi tartalmak esetén használja:  

1. Az alábbi kifejezések közül legalább egy: **ssn**, **social security**, **ssid**, **ss#** 

2. A társadalombiztosítási szám 9 formázott vagy formázatlan számjegyből áll:

    - **Formázott**: 
    
        - Kilenc számjegy az alábbi formátumban: ddd-dd-dddd VAGY ddd dd dddd 
        
    - **Formázatlan**: 
    
        - Kilenc számjegy az alábbi formátumban: ddddddddd 


Tesztelési példák:

- **SSN 123-45-6789**

- **SS# 123456789** 


----

### Nemzetközi bankszámlaszám (IBAN)

Ezt az adattípust az alábbi tartalmak esetén használja:  

1. A következő kifejezés: **IBAN** 

2. Az IBAN szám egy országkóddal kezdődik (két betű), amit két ellenőrző szám számjegy követ, végül pedig a bban-szám következik (amely legfeljebb 30 számjegyből állhat).


Tesztelési példák:

- **GB29 NWBK 6016 1331 9268 19 IBAN**


## További lépések

További információt az Azure Information Protection-házirend konfigurálásáról a [Szervezet házirendjeinek konfigurálása](configure-policy.md#configuring-your-organization-s-policy) szakasz hivatkozásai között találhat.  






<!--HONumber=Aug16_HO5-->


