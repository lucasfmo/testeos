---
title: "Migrowanie z usług AD RMS do usługi Azure Rights Management — faza 4 | Azure RMS"
description: 
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 08/17/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: d51e7bdd-2e5c-4304-98cc-cf2e7858557d
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 437afd88efebd9719a3db98f8ab0ae07403053f7
ms.openlocfilehash: 21fac7d684f2d544ab97f5ca6eb7faaaca3e9d26


---

# Faza 4 migracji — zadania po migracji

*Dotyczy usług: Active Directory Rights Management Services, Azure Rights Management*


Skorzystaj z poniższych informacji dotyczących fazy 4 migrowania usług AD RMS do usługi Azure Rights Management (Azure RMS). Te procedury obejmują kroki od 8 do 9 z sekcji [Migrowanie z usług AD RMS do usługi Azure Rights Management](migrate-from-ad-rms-to-azure-rms.md).


## Krok 8. Likwidowanie wdrożenia usług AD RMS

Opcjonalnie: należy usunąć punkt połączenia usługi (SCP) z usługi Active Directory, aby uniemożliwić komputerom odnajdywanie infrastruktury lokalnej usługi Rights Management. Ten krok jest opcjonalny z powodu przekierowania skonfigurowanego w rejestrze (np. przez uruchomienie skryptu migracji). Aby usunąć punkt połączenia usługi, należy użyć narzędzia rejestrowania punktu połączenia usługi AD będącego częścią [zestawu narzędzi administracyjnych usług Rights Management](http://www.microsoft.com/download/details.aspx?id=1479).

Aby monitorować działanie serwerów usług AD RMS, można na przykład sprawdzać [żądania w raporcie kondycji systemu](https://technet.microsoft.com/library/ee221012%28v=ws.10%29.aspx), [tabelę żądań obsługi](http://technet.microsoft.com/library/dd772686%28v=ws.10%29.aspx) lub [przeprowadzać inspekcję dostępu użytkowników do chronionej zawartości](http://social.technet.microsoft.com/wiki/contents/articles/3440.ad-rms-frequently-asked-questions-faq.aspx). Po potwierdzeniu, że klienci usług RMS nie komunikują się już z serwerami i pomyślnie używają usługi Azure RMS, można usunąć rolę serwera usług AD RMS z tych serwerów. W przypadku korzystania z serwerów dedykowanych można najpierw wykonać krok zapobiegawczy polegający na zamknięciu serwerów na pewien okres, aby upewnić się, że nie zostaną zgłoszone problemy, które wymagają ponownego uruchomienia tych serwerów w celu zapewnienia ciągłości usługi podczas badania, dlaczego klienci nie korzystają z usługi Azure RMS.

Po zlikwidowaniu serwerów usług AD RMS można skorzystać z możliwości przejrzenia szablonów w klasycznym portalu Azure. Umożliwi to ich skonsolidowanie, dzięki czemu użytkownicy będą mieć mniej szablonów do wyboru, a także ponowne ich skonfigurowanie, a nawet dodanie nowych. Będzie to również odpowiedni moment, aby opublikować szablony domyślne. Aby uzyskać więcej informacji, zobacz [Konfigurowanie szablonów niestandardowych usługi Azure Rights Management](../deploy-use/configure-custom-templates.md).

## Krok 9. Ponowne tworzenie klucza dzierżawy usługi Azure RMS
Ten krok jest stosowany tylko wtedy, gdy wybrana topologia klucza dzierżawy jest zarządzana przez firmę Microsoft, a nie przez klienta (rozwiązanie BYOK z usługą Azure Key Vault).

Ten krok jest opcjonalny, ale zalecany, jeśli klucz dzierżawy usługi Azure RMS jest zarządzany przez firmę Microsoft i został migrowany z usługi AD RMS. Ponowne utworzenie klucza w tym scenariuszu zabezpiecza klucz dzierżawy usługi Azure RMS przed potencjalnymi naruszeniami zabezpieczeń klucza usługi AD RMS.

W przypadku ponownego tworzenia klucza dzierżawy usługi Azure RMS (proces znany również jako „uaktualnianie klucza”) tworzony jest nowy klucz, a klucz oryginalny zostaje zarchiwizowany. Jednak ze względu na to, że przechodzenie z jednego klucza do innego nie jest realizowane natychmiast, ale trwa kilka tygodni, nie należy czekać do momentu naruszenia bezpieczeństwa oryginalnego klucza, ale ponownie utworzyć klucz dzierżawy usługi Azure RMS zaraz po zakończeniu migracji.

Aby ponownie utworzyć klucz dzierżawy usługi Azure RMS zarządzany przez firmę Microsoft, [skontaktuj się z pomocą techniczną firmy Microsoft](../get-started/information-support.md#to-contact-microsoft-support) i otwórz **sprawę pomocy technicznej usługi Azure RMS z żądaniem ponownego utworzenia klucza usługi Azure RMS po migracji z usługi AD RMS**. Musisz udowodnić, że jesteś administratorem dzierżawy usługi Azure RMS, i wiedzieć, że potwierdzenie tego procesu może potrwać kilka dni. Naliczane są standardowe opłaty za pomoc techniczną. Ponowne tworzenie klucza dzierżawy nie jest bezpłatną usługą pomocy technicznej.


## Następne kroki

Aby uzyskać więcej informacji na temat zarządzania kluczem dzierżawy usług RMS, zobacz [Operacje związane z kluczem dzierżawy usługi Azure Rights Management](../deploy-use/operations-tenant-key.md).

Teraz po zakończeniu migracji sprawdź [plan wdrożenia](deployment-roadmap.md), aby zidentyfikować wszelkie inne zadania wdrożenia, których wykonanie może być konieczne.




<!--HONumber=Aug16_HO3-->


