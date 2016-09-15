---
title: "A Rights Management megosztóalkalmazás&colon; Verziókiadások | Azure RMS"
description: "Tekintse meg, mi az újdonság vagy mi változott a Windows Rights Management megosztóalkalmazás kiadásában."
author: cabailey
manager: mbaldwin
ms.date: 08/25/2016
ms.topic: article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 6751bd90-959f-4eba-91ed-6588ac983762
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 035c9eb6cb630cafd5bd7fc7e2371340043ddc5e
ms.openlocfilehash: 361fde97756c24fa46df6eda16d7506b4b8aaa3a


---

# A Rights Management megosztóalkalmazás: Verziókiadások

>*A következőkre vonatkozik: Active Directory tartalomvédelmi szolgáltatások, Azure Rights Management, Windows 10, Windows 7 SP1, Windows 8, Windows 8.1*

A Rights Management csapata a javítások és új funkciók bevezetéséhez rendszeresen frissíti a Rights Management megosztóalkalmazást. Az alábbi információkból megismerheti a kiadás újdonságait és módosításait. A legújabb kiadás a lista tetején található.

A 2015. január 1. előtt kiadott verziók nem szerepelnek a listán.

> [!NOTE]
> Ha kérdése van, vagy visszajelzést szeretne küldeni az RMS-megosztó alkalmazásról, küldjön e-mailt az [AskIPTeam](mailto:AskIPTeam@microsoft.com?subject=RMS%20sharing%20app:%20Feedback%20or%20question) címre.

## 1.0.2217.0-s verzió

**Kiadás dátuma**: 2016.07.13.

**Javítások**:

- Már nem jelenik meg a 0x800704DC hibakód, amikor az összevonást és többtényezős hitelesítést használó vállalati ügyfelek védetté szeretnének tenni bizonyos tartalmakat.



## Verzió: 1.0.2191.0.
**Kiadás dátuma**: 2016. 06. 16.

**Javítások**:

- A dokumentumkövetési webhelyen már helyesen jelenik meg a követett dokumentumok megtekintéseinek száma.

- A sablonok már minden nyelv esetében a felhasználók által elérhetőként jelennek meg.

- Ha védett megosztást használt egy PowerPoint-fájlhoz, a rendszer a fájl helyi változatának módosításait már megfelelően menti.

- Javítottunk néhány apróbb hibát és hibaüzenetet.


## Verzió: 1.0.2004.0
**Kiadás dátuma**:2015.12.11.

**Javítások**:

-   Csak a fájl tulajdonosa és a **Társtulajdonos** engedélyszinttel rendelkező személyek szüntethetik meg a fájlok védelmét. Korábban a fájl tulajdonosa, illetve a **Társszerző** és **Társtulajdonos** engedélyszinttel rendelkező személyek szüntethették meg a fájlok védelmét.

-   Natív védelem **.tif** fájlok számára (a .tiff fájlok mellett) RMS-védelemmel rendelkező, írásvédett **.ptif** fájl létrehozásához.

-   Hibaüzenetek fejlesztései (pontosság és egyértelműség).

-   Teljesítménybeli fejlesztések a tartalmak titkosításához és visszafejtéséhez.

**Új funkciók**:

-   Nem rendszergazda általi telepítés támogatása, így az általános jogú felhasználók is telepíthetik az RMS megosztóalkalmazást.

    Az Office 2010-et futtató általános jogú felhasználókra bizonyos korlátozások vonatkoznak. További információkért tekintse meg a [Download and install the Rights Management sharing application](install-sharing-app.md) (A Rights Management megosztóalkalmazás letöltése és telepítése) felhasználói útmutató [If you are not a local administrator and use Office 2010](install-sharing-app.md#if-you-are-not-a-local-administrator-and-use-office-2010) (Ha Ön nem helyi rendszergazda, és Office 2010-et használ) című szakaszát.

## 1.0.1908.0 verzió
**Kiadás dátuma**:2015.09.16.

**Javítások**:

-   A többtényezős hitelesítés (MFA) támogatása az Azure RMS-ben, ami egyúttal megszünteti a Microsoft bejelentkezési segédtől való függést a modern hitelesítést használó alkalmazások esetén.

    További információt [Az Azure Rights Management követelményei](../get-started/requirements-azure-rms.md) című témakör [Többtényezős hitelesítés (MFA) és az Azure RMS](../get-started/requirements-azure-ad.md#multi-factor-authentication-mfa-and-azure-rms) című szakaszában talál.

## 1.0.1784.0 verzió
**Kiadás dátuma**:2015.07.30.

**Javítások**:

-   A jogmegadási sablonok alapértelmezett frissítési időköze 7 napról 1 napra csökkent.

-   Kevesebb regresszió és kisebb hibák elhárítása.

## 1.0.1770.0 verzió
**Kiadás dátuma**:2015.04.25.

**Javítások**:

-   Ezen verziótól csak a tulajdonos és a társtulajdonosok távolíthatják el a védelmet. A társszerzők nem távolíthatják el a védelmet.

-   A verzió már a hálózati megosztáson tárolt fájlok védelemmel való ellátását is lehetővé teszi.

**Új funkciók**:

-   Dokumentumkövetés és visszavonás támogatása. További információ: [Dokumentumok nyomon követése és visszavonása az RMS-megosztó alkalmazás használatakor](sharing-app-track-revoke.md).

-   Sablontámogatás a **Védett megosztás** lehetőség választásakor:

    -   Mostantól kiválaszthat sablonokat.

    -   A csúszka a sablonokat és az egyéni engedélyeket tartalmazó listát fogja látni.

    -   A továbbiakban nem látható a **Felhasználás engedélyezése minden eszközön** és a **Használati korlátozások kényszerítése** lehetőség. Helyette a rendszer automatikusan az **Általános védelem** beállítást választja a fájl típusától függően.

    További információ: [A Rights Management megosztóalkalmazás párbeszédpanel-beállításai](sharing-app-dialog-box.md).

## 1.0.1667.0-s verzió
**Kiadás dátuma**:2015.01.19.

**Javítások**:

-   Kínai nyelvi betűtípusok támogatása az RMS-megosztó alkalmazás PPDF-megjelenítőjében.

-   Továbbfejlesztett hiba- és üzenetkezelés.

-   Az automatikus frissítési értesítéssel azonnal kijavíthatja a hibákat, amint letölthető az alkalmazás legújabb verziója.

**Új funkciók**:

-   **Több e-mail-tartomány támogatása a szervezeten belül**: Ha az AD RMS-t használja, és a szervezet felhasználói több e-mail-tartománnyal rendelkeznek, ez a frissítés lehetővé teszi a felhasználók számára olyan tartalmak felhasználását, amelyet a szervezet más tartományait használó felhasználók láttak el védelemmel. További információt a [Rendszergazdai útmutató a Rights Management megosztóalkalmazáshoz](sharing-app-admin-guide.md) témakör [Csak AD RMS esetén: Több e-mail-tartomány támogatása a szervezeten belül](sharing-app-admin-guide.md#ad-rms-only-support-for-multiple-email-domains-within-your-organization) című szakaszában talál.




<!--HONumber=Aug16_HO4-->


