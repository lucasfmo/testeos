---
title: "Konfigurowanie etykiety w celu zastosowania ochrony usługi Rights Management | Azure Rights Management"
description: 
author: cabailey
manager: mbaldwin
ms.date: 08/15/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: df26430b-315a-4012-93b5-8f5f42e049cc
translationtype: Human Translation
ms.sourcegitcommit: e11a5a836d6a410ba49ac17cfe95d8530ecb785f
ms.openlocfilehash: 60738c310a3e7c734bfe3e48e16535ed3be05bb4


---

# Konfigurowanie etykiety w celu zastosowania ochrony usługi Rights Management

>*Dotyczy: Azure Information Protection (wersja zapoznawcza)*

**[Niniejsze informacje mają charakter wstępny i mogą ulec zmianom. ]**

Najbardziej poufne dokumenty i wiadomości e-mail możesz chronić przy użyciu usługi Rights Management, która korzysta z zasad szyfrowania, tożsamości oraz autoryzacji w celu zapobieżenia utracie danych. Ta ochrona jest stosowana, gdy skonfigurujesz etykietę do używania szablonu usługi Rights Management. 

Ten szablon może być jednym z szablonów domyślnych, które są automatycznie tworzone podczas aktywacji usługi Azure Rights Management, lub szablonem niestandardowym. Szablony działów usługi Azure Rights Management są obsługiwane, ale stosują ochronę tylko wtedy, gdy autor dokumentu lub wiadomości e-mail znajduje się w skonfigurowanym zakresie szablonu. Jeśli użytkownik znajduje się poza zakresem, zobaczy komunikat informujący o tym, że usługa Azure Information Protection nie może zastosować etykiety.

## Jak działa ochrona

Gdy dokument lub wiadomość e-mail są chronione przez usługę Rights Management, będą szyfrowane podczas przechowywania i podczas przesyłania, a odszyfrować je mogą tylko autoryzowani użytkownicy. Szyfrowanie zostaje utrzymane w dokumencie lub wiadomości e-mail, nawet w przypadku zmiany nazwy dokumentu lub wiadomości. Ponadto możesz skonfigurować prawa i ograniczenia użytkowania, np.:

- Tylko użytkownicy w organizacji mogą otworzyć poufny firmowy dokument lub wiadomość e-mail.

- Tylko użytkownicy w dziale marketingu mogą edytować i drukować dokument lub wiadomość e-mail z ogłoszeniem o promocji, podczas gdy wszyscy inni użytkownicy w organizacji mogą jedynie wyświetlać do odczytu ten dokument lub wiadomość e-mail.

- Użytkownicy nie mogą przesyłać dalej wiadomości e-mail, która zawiera informacje o wewnętrznej reorganizacji.

- Bieżącego cennika przesyłanego do partnerów biznesowych nie można otworzyć po określonej dacie.

Aby uzyskać więcej informacji o szablonach usługi Azure Rights Management i sposobie konfigurowania tych praw i ograniczeń użytkowania, zobacz [Konfigurowanie szablonów niestandardowych usługi Azure Rights Management](../deploy-use/configure-custom-templates.md).

Aby uzyskać więcej informacji na temat usługi Azure Rights Management i jej działania, zobacz [Co to jest usługa Azure Rights Management?](../understand-explore/what-is-azure-rms.md)

> [!IMPORTANT]
> Aby skonfigurować etykietę do stosowania ochrony usługi Rights Management, usługa Azure Rights Management musi być aktywowana dla Twojej organizacji. Jeśli jeszcze nie zostało to zrobione, zobacz [Aktywacja usługi Azure Rights Management](../deploy-use/activate-service.md).


## Aby skonfigurować etykietę w celu zastosowania ochrony usługi Rights Management

1. Jeśli jeszcze tego nie zrobiono, zaloguj się do [portalu Azure](https://portal.azure.com) jako administrator globalny, dzięki czemu będzie można pobrać szablony usługi Azure Rights Management. Następnie przejdź do bloku **Azure Information Protection**. 

    Na przykład w menu centralnym kliknij przycisk **Przeglądaj** i w polu filtru zacznij wpisywać ciąg **Information**. Wybierz pozycję **Azure Information Protection**.

2. W bloku **Azure Information Protection** wybierz etykietę, którą chcesz skonfigurować w celu stosowania ochrony usługi Rights Management.

3. W bloku **Etykieta** w sekcji **Ustaw szablon usług RMS w celu ochrony dokumentów i wiadomości e-mail zawierających tę etykietę** dla pola **Wybierz szablon usług RMS z** wybierz ustawienie **Azure RMS** lub **AD RMS (WERSJA ZAPOZNAWCZA)**.
    
    W większości przypadków wybierzesz usługę **Azure RMS**. Nie należy wybierać usługi AD RMS, chyba że użytkownik przeczytał i zrozumiał warunki wstępne i ograniczenia towarzyszące tej konfiguracji, która czasami nazywana jest scenariuszem *zachowaj własny klucz* (HYOK, hold your own key). Aby uzyskać więcej informacji, zobacz [Wymagania i ograniczenia dotyczące rozwiązania „hold your own key” (HYOK) dla ochrony za pomocą usług AD RMS](configure-adrms-restrictions.md).
    
4. W przypadku wybrania usługi Azure RMS: dla opcji **Wybierz szablon usług RMS** kliknij pole listy rozwijanej i wybierz szablon, którego chcesz użyć do ochrony dokumentów i wiadomości e-mail przy użyciu tej etykiety.

    > [!NOTE] 
    > Jeśli utworzysz nowy szablon po otworzeniu bloku **Etykieta**, zamknij ten blok i wróć do kroku 2, aby nowo utworzony szablon został pobrany z platformy Azure i był dostępny do wyboru.
    
    Należy pamiętać, że w przypadku wybrania szablonu dla działu lub skonfigurowania [kontrolek dołączania](../deploy-use/activate-service.md#configuring-onboarding-controls-for-a-phased-deployment):
    
    - Użytkownicy, którzy są poza skonfigurowanym zasięgiem szablonu lub są wyłączeni ze stosowania ochrony usługi Azure Rights Management, będą również widzieć etykietę, ale nie będą mogli jej zastosować. Jeśli wybiorą etykietę, zobaczą następujący komunikat: **Usługa Azure Information Protection nie może zastosować tej etykiety. Jeśli problem będzie nadal występować, skontaktuj się z administratorem.**
    
5. W przypadku wybrania usługi AD RMS: podaj identyfikator GUID szablonu i adres URL licencjonowania klastra usługi AD RMS. [Więcej informacji](configure-adrms-restrictions.md#locating-the-information-to-specify-ad-rms-protection-with-an-azure-information-protection-label)

6. Kliknij polecenie **Zapisz**.

7. Aby udostępnić użytkownikom zmiany, w bloku **Azure Information Protection** kliknij przycisk **Opublikuj**.

## Następne kroki

Aby uzyskać więcej informacji o konfigurowaniu zasad usługi Azure Information Protection, użyj linków w sekcji [Konfigurowanie zasad organizacji](configure-policy.md#configuring-your-organization-s-policy).  



<!--HONumber=Aug16_HO3-->


