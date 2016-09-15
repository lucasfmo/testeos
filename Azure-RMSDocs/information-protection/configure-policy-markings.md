---
title: "A címkék vizuális megjelöléseinek konfigurálása az Azure Information Protection szolgáltatásban | Azure Rights Management"
description: "A dokumentumokhoz és e-mailekhez hozzárendelt címkék esetében több, a besorolások külső megkülönböztetését segítő beállítás közül választhat. Ezek a vizuális megjelölések a fejléc, az élőláb és a vízjel."
manager: mbaldwin
ms.date: 08/17/2016
ms.topic: article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: df2676eeb062-f25a-4cf8-a782-e59664427d54
translationtype: Human Translation
ms.sourcegitcommit: c9f9211e7c1dcf293caf81475515114b5433d6a7
ms.openlocfilehash: c73b6e3fe114625c16a7c2e799162902ba26e4cf


---

# A címkék vizuális megjelöléseinek konfigurálása az Azure Information Protection szolgáltatásban

>*A következőkre vonatkozik: az Azure Information Protection előzetes verziója*

**[ Előzetes információ, a tartalma változhat. ]**

A dokumentumokhoz és e-mailekhez hozzárendelt címkék esetében több, a besorolások külső megkülönböztetését segítő beállítás közül választhat. Ezek a vizuális megjelölések a fejléc, az élőláb és a vízjel:

A vizuális megjelölések a Word-, Excel- és PowerPoint-dokumentumokban alkalmazott címkéken, valamint a dokumentumok mentésekor jelennek meg. Az e-mailek esetében a vizuális megjelölések az üzenet elküldésekor jelennek meg.

További információ a vizuális megjelölésekről:

- A fejlécek és élőlábak a Word, az Excel, a PowerPoint és az Outlook programokban alkalmazhatók.

- A vízjelek a Word, az Excel és a PowerPoint programokban alkalmazhatók:

    - Excel: a vízjelek csak Oldalkép és Nyomtatási kép nézetben, illetve kinyomtatva láthatók.

    - PowerPoint: a vízjel a diamintán jelenik meg háttérképként.

- Megadhat pusztán egy karakterláncot, de használhat [változókat](#using-variables-in-the-text-string) is a karakterlánc dinamikus létrehozásához az élőfej, élőláb vagy vízjel alkalmazásakor. 

A címkék vizuális jeleinek konfigurálásához kövesse az alábbi utasításokat.

1. Ha még nem tette meg, jelentkezzen be az [Azure Portalra](https://portal.azure.com), majd lépjen az **Azure Information Protection** panelre. 
    
    A Központ menüben kattintson a **Tallózás** gombra, és kezdje el begépelni az **Information** szót a Szűrő mezőbe. Válassza az **Azure Information Protection** lehetőséget.

2. Az **Azure Information Protection** panelen jelölje ki a vizuális megjelölésekkel konfigurálni kívánt címkét.

3. A**Label** (Címke) panel **Set visual marking (such as header or footer)** (Vizuális megjelölés (például fejléc vagy élőláb) beállítása) területén konfigurálja a vizuális megjelölések beállításait, majd kattintson a **Save** (Mentés) gombra:

    - Fejléc konfigurálása: A **Documents with this label have a header** (Az ezzel a címkével ellátott dokumentumok fejléccel jelenjenek meg) beállítást kapcsolja **Be**, ha szeretne fejlécet, és kapcsolja **Ki**, ha nem. Ha a beállítást **bekapcsolta**, adja meg a fejléc szövegét, színét és állítsa be az igazítását.
    
    - Élőláb konfigurálása: A **Documents with this label have a footer** (Az ezzel a címkével ellátott dokumentumok előlábbal jelenjenek meg) beállítást kapcsolja **Be**, ha szeretne előlábat, és kapcsolja **Ki**, ha nem. Ha a beállítást **bekapcsolta**, adja meg az előláb szövegét, színét és állítsa be az igazítását.
    
    - Vízjel konfigurálása: A **Documents with this label have a watermark** (Az ezzel a címkével ellátott dokumentumok vízjellel jelenjenek meg) beállítást kapcsolja **Be**, ha szeretne vízjelet, és kapcsolja **Ki**, ha nem. Ha a beállítást **bekapcsolta**, adja meg a vízjel szövegét, színét és állítsa be az igazítását. 

4. A módosításokat az **Azure Information Protection** panel **Publish** (Közzététel) lehetőségével teheti elérhetővé a felhasználóknak.

## Változók használata a karakterláncban

Az élőfej, élőláb vagy vízjel létrehozását szolgáló karakterláncban a következő változókat használhatja:

- `${Item.Label}` a kiválasztott címkéhez. Például: Belső

- `${Item.Name}` a fájlnévhez vagy az e-mail tárgyához. Például: ErtekesitesJulius.docx

- `${Item.Location}` a dokumentumok elérési útjához vagy nevéhez, illetve az e-mailek tárgyához. Például: \\\Ertekesites\2016\Q3\JuliusiJelentes.docx

- `${User.Name}` a dokumentum vagy e-mail tulajdonosához, a Windowsba történő bejelentkezéshez használt felhasználónév alapján. Például: rsimon

- `${User.PrincipalName}` a dokumentum vagy e-mail tulajdonosához, az Azure Information Protection-ügyfélbe történő bejelentkezéshez használt e-mail-cím (UPN) alapján. Például: rsimone@vanarsdelltd.com

- `${Event.DateTime}` a kiválasztott címke beállításának dátumához és időpontjához. Például: 2016.08.16., 13:30
    
Példa: ha a `Document: ${item.name}  Classification: ${item.label}` karakterláncot adja meg titkos címke élőlábként, akkor a project.docx nevű dokumentum élőlába a következő lesz: **Dokumentum: project.docx Classification: Secret**.

## További lépések

További információt az Azure Information Protection-házirend konfigurálásáról a [Szervezet házirendjeinek konfigurálása](configure-policy.md#configuring-your-organization-s-policy) szakasz hivatkozásai között találhat.  





<!--HONumber=Aug16_HO4-->


