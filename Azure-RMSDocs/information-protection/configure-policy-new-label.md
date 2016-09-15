---
title: "Tworzenie nowej etykiety dla usługi Azure Information Protection | Azure Rights Management"
description: 
author: cabailey
manager: mbaldwin
ms.date: 08/10/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 1b45faa5-0c9c-40d6-910a-f117e7b6e8a3
translationtype: Human Translation
ms.sourcegitcommit: b2263c212a1b869b778767493645f10ad821828f
ms.openlocfilehash: c2f8f3204e3d5947137e7e9111ba4eba2628293b


---

# Tworzenie nowej etykiety dla usługi Azure Information Protection

>*Dotyczy: Azure Information Protection (wersja zapoznawcza)*

**[Niniejsze informacje mają charakter wstępny i mogą ulec zmianom. ]**

Usługa Azure Information Protection zawiera domyślne etykiety z możliwością dostosowania, ale możesz też utworzyć własne etykiety, które użytkownicy zobaczą na pasku usługi Information Protection.

Jeśli potrzebujesz dodatkowego poziomu klasyfikacji, możesz dodać nową etykietę lub etykietę podrzędną do istniejącej etykiety. Na przykład etykieta **Tajne** znajdująca się w [zasadach domyślnych](configure-policy-default.md) zawiera etykiety podrzędne.

Użyj poniższych instrukcji, aby dodać nową etykietę do zasad usługi Azure Information Protection.

1. Jeśli jeszcze tego nie zrobiono, zaloguj się do [Portalu Azure](https://portal.azure.com), a następnie przejdź do bloku **Azure Information Protection**. 
    
    Na przykład w menu centralnym kliknij przycisk **Przeglądaj** i w polu filtru zacznij wpisywać ciąg **Information**. Wybierz pozycję **Azure Information Protection**.

2. W bloku **Azure Information Protection** wykonaj jedną z następujących czynności:

    - Aby utworzyć nową etykietę: kliknij przycisk **Dodaj nową etykietę**.

    - Aby utworzyć nową etykietę podrzędną: kliknij prawym przyciskiem myszy lub wybierz menu kontekstowe (**...**) etykiety, dla której chcesz utworzyć etykietę podrzędną, a następnie kliknij polecenie **Dodaj etykietę podrzędną**.

3. W bloku **Etykieta** lub **Etykieta podrzędna** wybierz opcje dla nowej etykiety, a następnie kliknij przycisk **Zapisz**.

    > [!NOTE]
    >Aby uzyskać informacje o konfigurowaniu ochrony, zobacz [Konfigurowanie etykiety w celu zastosowania ochrony](configure-policy-protection.md).

4. Aby udostępnić użytkownikom zmiany, w bloku **Azure Information Protection** kliknij przycisk **Opublikuj**.

## Następne kroki

Aby uzyskać więcej informacji o konfigurowaniu zasad usługi Azure Information Protection, użyj linków w sekcji [Konfigurowanie zasad organizacji](configure-policy.md#configuring-your-organization-s-policy).  





<!--HONumber=Aug16_HO2-->


