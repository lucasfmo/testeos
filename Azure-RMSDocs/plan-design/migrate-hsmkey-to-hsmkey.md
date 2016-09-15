---
title: "Krok 2&colon; Migracja klucza chronionego przez moduł HSM do klucza chronionego przez moduł HSM | Azure RMS"
description: 
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 08/17/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: c5bbf37e-f1bf-4010-a60f-37177c9e9b39
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 437afd88efebd9719a3db98f8ab0ae07403053f7
ms.openlocfilehash: 86f7bd025824b23c8eecdb05b62d83204ae1ccb4


---

# Krok 2. Migracja klucza chronionego przez moduł HSM do klucza chronionego przez moduł HSM

*Dotyczy usług: Active Directory Rights Management Services, Azure Rights Management*


Te instrukcje są częścią [ścieżki migracji z usług AD RMS do usługi Azure Rights Management](migrate-from-ad-rms-to-azure-rms.md) oraz są stosowane tylko wtedy, gdy klucz usług AD RMS jest chroniony przez moduł HSM, a użytkownik chce migrować klucz do usługi Azure Rights Management z wykorzystaniem klucza dzierżawy chronionego przez moduł HSM w usłudze Azure Key Vault. 

Jeśli nie jest to wybrany scenariusz konfiguracji, wróć do [Kroku 2. Eksportowanie danych konfiguracji z usług AD RMS i importowanie ich do usługi Azure RMS](migrate-from-ad-rms-phase1.md#step-2-export-configuration-data-from-ad-rms-and-import-it-to-azure-rms) i wybierz inną konfigurację.

> [!NOTE]
> W tych instrukcjach przyjęto założenie, że klucz usługi AD RMS jest chroniony przez moduł. Jest to najbardziej typowy przypadek. 

Jest to składająca się z dwóch części procedura, która umożliwia zaimportowanie klucza HSM i konfiguracji usług AD RMS do usługi Azure RMS i zastosowanie w ten sposób klucza dzierżawy usługi Azure RMS zarządzanego przez użytkownika (BYOK).

Ponieważ klucz dzierżawy usługi Azure RMS będzie przechowywany i zarządzany w ramach usługi Azure Key Vault, ta część migracji wymaga administracji w usłudze Azure Key Vault poza administracją w usłudze Azure RMS. Jeśli usługa Azure Key Vault jest zarządzana przez innego administratora w Twojej organizacji, musisz skoordynować pracę z tym administratorem, aby zakończyć procedurę.

Przed rozpoczęciem upewnij się, że Twoja organizacja ma magazyn kluczy utworzony w usłudze Azure Key Vault oraz że obsługuje klucze chronione przez moduł HSM. Chociaż nie jest to wymagane, zaleca się posiadanie dedykowanego magazynu kluczy dla usługi Azure RMS. Ten magazyn kluczy zostanie skonfigurowany tak, aby usługa Azure RMS mogła uzyskać do niego dostęp, dlatego klucze przechowywane w tym magazynie kluczy powinny być ograniczone wyłącznie do kluczy usługi Azure RMS.


> [!TIP]
> Jeśli chcesz przeprowadzić konfigurację usługi Azure Key Vault, a nie masz doświadczenia z tą usługą platformy Azure, przydatne może okazać się przeczytanie artykułu [Wprowadzenie do usługi Azure Key Vault](https://azure.microsoft.com/documentation/articles/key-vault-get-started/). 


## Część 1. Przesłanie klucza HSM do usługi Azure Key Vault

Te procedury są wykonywane tylko przez administratora usługi Azure Key Vault.

1.  Wykonaj instrukcje zawarte w dokumentacji usługi Azure Key Vault, korzystając z sekcji [Implementowanie funkcji BYOK dla usługi Azure Key Vault](https://azure.microsoft.com/documentation/articles/key-vault-hsm-protected-keys/#implementing-bring-your-own-key-byok-for-azure-key-vault) z następującym wyjątkiem:

    - Nie wykonuj kroków procedury **Generowanie klucza dzierżawy**, ponieważ istnieje już jego odpowiednik pochodzący z wdrożenia usług AD RMS. Zamiast tego zidentyfikuj klucz używany na serwerze usług AD RMS z instalacji firmy Thales i użyj go podczas migracji. Zaszyfrowane pliki klucza firmy Thales mają przeważnie nazwę **key<*nazwa_aplikacji_klucza*><*identyfikator_klucza*>** i są przechowywane lokalnie na serwerze.

    Gdy klucz zostanie przekazany do usługi Azure Key Vault, zostaną wyświetlone właściwości klucza zawierające identyfikator klucza. Identyfikator będzie wyglądać podobnie do następującego: https://contosorms-kv.vault.azure.net/keys/contosorms-byok/aaaabbbbcccc111122223333. Zanotuj ten adres URL, ponieważ administrator usługi Azure RMS będzie go potrzebować, aby skonfigurować usługę Azure RMS do użycia tego klucza jako klucza dzierżawy.

2. Na stacji roboczej podłączonej do Internetu, w sesji programu PowerShell, użyj polecenia cmdlet [Set-AzureRmKeyVaultAccessPolicy](https://msdn.microsoft.com/library/mt603625.aspx ), aby autoryzować nazwę główną usługi Azure RMS (Microsoft.Azure.RMS) do dostępu do magazynu kluczy, w którym przechowywany będzie klucz dzierżawy usługi Azure RMS. Wymagane uprawnienia to: decrypt, encrypt, unwrapkey, wrapkey, verify i sign.
    
    Przykładowo, jeśli magazyn kluczy utworzony dla usługi Azure RMS ma nazwę contoso-byok-ky, a grupa zasobów ma nazwę contoso-byok-rg, uruchom następujące polecenie:
    
        Set-AzureRmKeyVaultAccessPolicy -VaultName "contoso-byok-kv" -ResourceGroupName "contoso-byok-rg" -ServicePrincipalName Microsoft.Azure.RMS -PermissionsToKeys decrypt,encrypt,unwrapkey,wrapkey,verify,sign


Teraz klucz HSM w usłudze Azure Key Vault jest już gotowy do użycia w usłudze Azure RMS, a Ty możesz importować dane konfiguracji usług AD RMS.

## Część 2. Importowanie danych konfiguracji do usługi Azure RMS

Te procedury są wykonywane tylko przez administratora usługi Azure RMS.

1.  Na stacji roboczej podłączonej do Internetu i w sesji programu PowerShell połącz się z usługą Azure RMS, używając polecenia cmdlet [Connect-AadrmService](https://msdn.microsoft.com/library/dn629415.aspx ).
    
    Następnie przekaż pierwszy wyeksportowany plik (XML) zaufanej domeny publikacji, korzystając z polecenia cmdlet [Import-AadrmTpd](https://msdn.microsoft.com/library/dn857523.aspx). Jeśli masz więcej niż jeden plik XML z powodu użycia wielu zaufanych domen publikacji, wybierz plik zawierający wyeksportowaną zaufaną domenę publikacji odpowiadającą kluczowi HSM, który chcesz zastosować w usłudze Azure RMS do ochrony zawartości po migracji. 
    
    Aby uruchomić to polecenie cmdlet, wymagany jest adres URL dla klucza zidentyfikowany w poprzednim kroku.
    
    Przykładowo, używając naszej wartości adresu URL klucza z poprzedniego kroku i pliku TPD C:\contoso-tpd1.xml, należy uruchomić następujące polecenie:
    
    ```
    Import-AadrmTpd -TpdFile "C:\contoso-tpd1.xml" -ProtectionPassword –KeyVaultStringUrl https://contoso-byok-kv.vault.azure.net/keys/contosorms-byok/aaaabbbbcccc111122223333 -Active $True -Verbose
    ```
    
    Po wyświetleniu monitu wprowadź określone wcześniej hasło i potwierdź, że chcesz wykonać tę akcję.

2.  Po zakończeniu wykonywania polecenia powtórz krok 1 dla każdego z pozostałych plików XML, który został utworzony przez wyeksportowanie zaufanej domeny publikacji. Dla tych plików ustaw opcję **-Active** na wartość **false** podczas uruchamiania polecenia Import.  

3.  Użyj polecenia cmdlet [Disconnect-AadrmService](http://msdn.microsoft.com/library/windowsazure/dn629416.aspx), aby zakończyć połączenie z usługą Azure RMS:

    ```
    Disconnect-AadrmService
    ```

    > [!NOTE]
    > Jeśli chcesz później potwierdzić, którego klucza używa Twój klucz dzierżawy usługi Azure RMS w usłudze Azure Key Vault, użyj polecenia cmdlet usługi Azure RMS [Get-AadrmKeys](https://msdn.microsoft.com/library/dn629420.aspx).

Teraz możesz wykonać [Krok 3. Aktywowanie dzierżawy usługi RMS](migrate-from-ad-rms-phase1.md#step-3-activate-your-rms-tenant).




<!--HONumber=Aug16_HO3-->


