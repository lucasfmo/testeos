---
title: "Instalowanie i konfigurowanie łącznika Azure Rights Management | Azure RMS"
description: 
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 06/27/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 4fed9d4f-e420-4a7f-9667-569690e0d733
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ea4b7539ab311d782c3987a8fd74940aad72e65b
ms.openlocfilehash: 165292482349e4a233ab4030f49a297f57b041ac


---

# Instalowanie i konfigurowanie łącznika Azure Rights Management

*Dotyczy usług: Azure Rights Management, Office 365*

Skorzystaj z poniższych informacji, aby zainstalować i skonfigurować łącznik Azure Rights Management (RMS). Te procedury obejmują kroki od 1 do 4 z sekcji [Wdrażanie łącznika usługi Azure Rights Management](deploy-rms-connector.md).

Przed rozpoczęciem upewnij się, czy zostały sprawdzone [wymagania wstępne](deploy-rms-connector.md#prerequisites-for-the-rms-connector) dla tego wdrożenia.


## Instalowanie łącznika usług RMS

1.  Zidentyfikuj komputery (co najmniej dwa), na których będzie uruchamiany łącznik usług RMS. Muszą one odpowiadać minimalnej specyfikacji wymienionej w wymaganiach wstępnych.

    > [!NOTE]
    > Zostanie zainstalowany pojedynczy łącznik RMS (składający się z wielu serwerów w celu zapewnienia wysokiej dostępności) na dzierżawę (dzierżawę usługi Office 365 lub dzierżawę usługi Azure AD). W przeciwieństwie do usługi Active Directory RMS nie musisz instalować łącznika usług RMS w każdym lesie.

2.  Pobierz pliki źródłowe dla łącznika usług RMS z [Centrum pobierania Microsoft](http://go.microsoft.com/fwlink/?LinkId=314106).

    Aby zainstalować łącznik usług RMS, pobierz plik RMSConnectorSetup.exe.

    Ponadto:

    -   Jeśli chcesz później skonfigurować łącznik z komputera 32-bitowego, pobierz również plik RMSConnectorAdminToolSetup_x86.exe.

    -   Jeśli chcesz użyć narzędzia konfiguracji serwera w odniesieniu do łącznika usług RMS, aby zautomatyzować konfigurację ustawień rejestru lokalnych serwerów, pobierz również plik GenConnectorConfig.ps1.

3.  Na komputerze, na którym chcesz zainstalować łącznik usług RMS, uruchom plik **RMSConnectorSetup.exe** z uprawnieniami administratora.

4.  Na stronie powitalnej strony Instalator łącznika usługi Microsoft Rights Management wybierz pozycję **Zainstaluj łącznik usługi Microsoft Rights Management na komputerze**, a następnie kliknij przycisk **Dalej**.

5.  Przeczytaj i zaakceptuj postanowienia licencyjne łącznika usług RMS, a następnie kliknij przycisk **Dalej**.

W celu kontynuacji wprowadź konto i hasło, aby skonfigurować łącznik usługi RMS.

## Wprowadzanie poświadczeń
Przed skonfigurowaniem łącznika usług RMS, musisz wprowadzić poświadczenia dla konta, które ma wystarczające uprawnienia do konfigurowania łącznika usług RMS. Na przykład można wpisać **admin@contoso.com**, a następnie podać hasło dla tego konta.

Istnieją pewne ograniczenia dotyczące znaków dla tego hasła. Nie można użyć hasła, które ma jakiekolwiek z następujących znaków: handlowe „i” (**&**) lewy nawias (**[**), prawy nawias (**]**), prosty cudzysłów (**"**) i apostrof (**'**). Jeśli hasło zawiera dowolny z tych znaków, uwierzytelnienie dla łącznika usług RMS zakończy się niepowodzeniem i pojawi się komunikat o błędzie, informujący, że kombinacja nazwy użytkownika i hasła nie jest poprawna, mimo że można pomyślnie zalogować się przy użyciu tego konta i hasła dla innych scenariuszy. Jeśli dotyczy to Twojego hasła, użyj innego konta z hasłem, które nie zawiera żadnego z tych znaków specjalnych, lub zresetuj hasło, dzięki czemu nie będzie ono zawierało żadnego z tych znaków specjalnych.

Ponadto, jeśli zostały zaimplementowane [kontrolki dołączania](activate-service.md#configuring-onboarding-controls-for-a-phased-deployment), upewnij się, że podane przez Ciebie konto użytkownika może chronić zawartość. Na przykład jeśli możliwość ochrony zawartości została ograniczona do grupy „Dział IT”, konto określone w tym miejscu musi być członkiem tej grupy. W przeciwnym razie zostanie wyświetlony komunikat o błędzie: **Próba odnalezienia lokalizacji usługi administracji i organizacji nie powiodła się. Upewnij się, że usługa Microsoft Rights Management jest włączona dla Twojej organizacji.**

Można użyć konta, które ma jedno z następujących uprawnień:

-   **Administrator globalny dla dzierżawy**: konto administratora globalnego dla dzierżawy usługi Office 365 lub dzierżawy usługi Azure AD.

-   **Administrator globalny usługi Azure Rights Management**: konto w usłudze Azure Active Directory, któremu przypisano rolę administratora globalnego usługi Azure RMS.

-   **Administrator łącznika usługi Azure Rights Management**: konto w usłudze Azure Active Directory, któremu przyznano prawa do instalowania łącznika usługi RMS dla Twojej organizacji i administrowania tym łącznikiem.

    > [!NOTE]
    > Rola administratora globalnego usługi Azure Rights Management i roli administratora łącznika usługi Azure Rights Management jest przypisana do kont za pomocą polecenia cmdlet [Add-AadrmRoleBasedAdministrator](https://msdn.microsoft.com/library/dn629417.aspx) usługi Azure RMS.
    > 
    > Aby uruchomić łącznik usługi RMS z najmniejszymi uprawnieniami, utwórz w tym celu dedykowane konto, dla którego zostanie następnie przypisana rola administratora łącznika usługi Azure RMS w następujący sposób:
    >
    > 1.  Jeśli jeszcze nie zostało to zrobione, pobierz i zainstaluj środowisko Windows PowerShell dla usług Rights Management. Aby uzyskać więcej informacji, zobacz [Instalowanie programu Windows PowerShell dla usługi Azure Rights Management](install-powershell.md).
    >
    >     Uruchom program Windows PowerShell za pomocą polecenia **Uruchom jako administrator** i połącz się z usługą Azure RMS za pomocą polecenia [Connect-AadrmService](https://msdn.microsoft.com/library/azure/dn629415.aspx):
    >
    >     ```
    >     Connect-AadrmService                   //provide Office 365 tenant administrator or Azure RMS global administrator credentials
    >     ```
    > 2.  Następnie uruchom polecenie [AadrmRoleBasedAdministrator](https://msdn.microsoft.com/library/azure/dn629417.aspx) przy użyciu tylko jednego z następujących parametrów:
    >
    >     ```
    >     Add-AadrmRoleBasedAdministrator -EmailAddress <email address> -Role "ConnectorAdministrator"
    >     ```
    >
    >     ```
    >     Add-AadrmRoleBasedAdministrator -ObjectId <object id> -Role "ConnectorAdministrator"
    >     ```
    >
    >     ```
    >     Add-AadrmRoleBasedAdministrator -SecurityGroupDisplayName <group Name> -Role "ConnectorAdministrator"
    >     ```
    >     Na przykład wpisz: **Add-AadrmRoleBasedAdministrator -EmailAddress melisa@contoso.com -Role "ConnectorAdministrator"**
    >
    >     Mimo że te polecenia przypisują rolę ConnectorAdministrator, można w tym miejscu użyć również roli GlobalAdministrator.

W procesie instalacji łącznika usług RMS weryfikowane i instalowane jest całe wstępnie wymagane oprogramowanie, instalowana jest usługa Internet Information Services (IIS), jeśli nie została zainstalowana wcześniej, oraz instalowane i konfigurowane jest oprogramowanie łącznika. Ponadto usługa Azure RMS zostaje przygotowana do konfiguracji poprzez utworzenie następujących obiektów:

-   Pusta tabela serwerów, które są autoryzowane do korzystania z łącznika w celu komunikowania się z usługami Azure RMS. Serwery zostaną dodane do tej tabeli później.

-   Zestaw tokenów zabezpieczających łącznik, które autoryzują operacje przeprowadzane za pomocą usług Azure RMS. Tokeny te są pobierane z usług Azure RMS i instalowane na komputerze lokalnym w rejestrze. Są chronione za pomocą danych interfejsu programowania aplikacji ochrony (DPAPI) oraz poświadczeń konta systemu lokalnego.

Na ostatniej stronie kreatora wykonaj następujące czynności, a następnie kliknij przycisk **Zakończ**:

-   Jeśli jest to pierwszy łącznik, który został zainstalowany, nie zaznaczaj w tej chwili opcji **Uruchom konsolę administratora łącznika do autoryzowania serwerów**. Zaznaczysz tę opcję po zainstalowaniu drugiego (lub końcowego) łącznika usług RMS. Zamiast tego uruchom ponownie kreatora na co najmniej jednym komputerze. Należy zainstalować co najmniej dwa łączniki.

-   Jeśli zainstalowano drugi (lub końcowy) łącznik, wybierz pozycję **Uruchom konsolę administratora łącznika do autoryzowania serwerów**.

> [!TIP]
> W tym momencie dostępny jest test weryfikujący, który można wykonać, aby sprawdzić, czy usługi sieci web dla łącznika usług RMS działają:
>
> -   Za pomocą przeglądarki sieci web połącz się z adresem **http://&lt;adres_łącznika&gt;/_wmcs/certification/servercertification.asmx**, zastępując *&lt;adres_łącznika&gt;* adresem serwera lub nazwą zainstalowanego łącznika usług RMS. Po udanym połączeniu wyświetlana jest strona **ServerCertificationWebService**.

Jeśli musisz odinstalować łącznik usług RMS, ponownie uruchom kreatora i wybierz opcję odinstalowania.

## Autoryzowanie serwerów do korzystania z łącznika usług RMS
Po zainstalowaniu łącznika usług RMS na co najmniej dwóch komputerach wszystko jest gotowe do autoryzowania serwerów i usług, które mają używać łącznika usług RMS. Na przykład: serwerów z systemem Exchange Server 2013 lub SharePoint Server 2013.

Aby zdefiniować te serwery, uruchom narzędzie administracyjne łącznika usług RMS i dodaj pozycje do listy dozwolonych serwerów. To narzędzie można uruchomić po zaznaczeniu opcji **Uruchom konsolę administracyjną łącznika do autoryzowania serwerów** pod koniec działania kreatora konfigurowania łącznika Microsoft Rights Management. Można też uruchomić je oddzielnie z poziomu kreatora.

Podczas autoryzowania serwerów należy pamiętać o następujących kwestiach:

-   Dodawanym serwerom zostaną przyznane specjalne uprawnienia. Wszystkim kontom określonym dla roli programu Exchange Server w konfiguracji łącznika zostanie przyznana [rola administratora](configure-super-users.md) w usługach Azure RMS, która umożliwi im dostęp do całej zawartości dla tej dzierżawy RMS. Funkcja administratora jest automatycznie włączana na tym etapie w razie potrzeby. Aby uniknąć zagrożenia zabezpieczeń podniesienia uprawnień, należy wskazać tylko konta używane przez serwery programu Exchange w danej organizacji. Wszystkim serwerom skonfigurowanym jako serwery programu SharePoint lub serwery plików, które używają infrastruktury FCI, zostaną przyznane uprawnienia zwykłych użytkowników.

-   Można dodać wiele serwerów jako pojedynczy wpis, określając zabezpieczenie usługi Active Directory lub grupy dystrybucyjnej, lub konto usługi, które jest używane przez więcej niż jeden serwer. Podczas używania tej konfiguracji grupa serwerów współużytkuje te same certyfikaty usług RMS i wszystkie uznaje się za właścicieli zawartości chronionej przez dowolny z nich. Aby zminimalizować ogólne koszty administracyjne, zalecane jest użycie tej konfiguracji pojedynczej grupy zamiast poszczególnych serwerów w celu autoryzowania serwerów programu Exchange w danej organizacji lub farmy serwerów programu SharePoint.

Na stronie **Serwery, które mogą wykorzystywać łącznik** kliknij przycisk **Dodaj**.

> [!NOTE]
> Autoryzowanie serwerów jest konfiguracją w usłudze Azure RMS równoważną konfiguracji usługi AD RMS ręcznego zastosowania uprawnień NTFS do pliku ServerCertification.asmx dla kont usługi lub serwera i ręcznego udzielania uprawnień administratora dla kont serwera Exchange. Stosowanie uprawnień NTFS do pliku ServerCertification.asmx nie jest wymagane dla łącznika.


### Dodawanie serwera do listy dozwolonych serwerów
Na stronie **Zezwalaj serwerowi na korzystanie z łącznika** wprowadź nazwę obiektu lub przewiń, aby zidentyfikować obiekt do autoryzacji.

Ważne jest, aby autoryzować odpowiedni obiekt. Aby serwera mógł korzystać z łącznika, do autoryzacji należy wybrać konto, na którym uruchomiona jest usługa lokalna (na przykład program Exchange lub SharePoint). Na przykład jeśli usługa jest uruchomiona jako skonfigurowane konto usługi, dodaj nazwę tego konta usługi do listy. Jeśli usługa jest uruchomiona jako System lokalny, dodaj nazwę obiektu komputera (na przykład SERVERNAME$). Najlepszym rozwiązaniem jest utworzenie grupy, która zawiera te konta i wskazanie jej zamiast nazw poszczególnych serwerów.

Więcej informacji na temat różnych ról serwerów:

-   W przypadku serwerów z systemem Exchange: należy określić grupę zabezpieczeń i użyć domyślnej grupy (**Serwery Exchange**), którą program Exchange tworzy automatycznie i przechowuje na wszystkich serwerach programu Exchange w lesie.

-   W przypadku serwerów z programem SharePoint:

    -   Jeśli serwer programu SharePoint 2010 jest skonfigurowany do uruchamiania jako System lokalny (nie używa konta usługi), ręcznie utwórz grupę zabezpieczeń w usługach domenowych w usłudze Active Directory, a następnie dodaj obiekt nazwy komputera dla serwera w tej konfiguracji do tej grupy.

    -   Jeśli serwer programu SharePoint jest skonfigurowany do używania konta usługi (zalecana praktyka dla programu SharePoint 2010 i jedyna możliwość dla programu SharePoint 2016 i SharePoint 2013), należy wykonać następujące czynności:

        1.  Dodaj konto usługi, na którym jest uruchomiona Usługa administracji centralnej programu SharePoint, aby umożliwić skonfigurowanie programu SharePoint za pomocą jego konsoli administratora.

        2.  Dodaj konto skonfigurowane dla puli aplikacji programu SharePoint.

        > [!TIP]
        > Jeśli te dwa konta są różne, należy rozważyć utworzenie pojedynczej grupy, który zawiera oba konta, aby zminimalizować ogólne koszty administracyjne.

-   W przypadku serwerów plików, które korzystają z infrastruktury klasyfikacji pliku, usługi skojarzone są uruchamiane za pomocą konta systemu lokalnego, dlatego jest wymagane autoryzowanie konta komputera dla serwerów plików (na przykład SERVERNAME$) lub grupy, która zawiera te konta komputera.

Po zakończeniu dodawania serwerów do listy kliknij przycisk **Zamknij**.

Jeśli jeszcze nie zostało to zrobione, należy teraz skonfigurować funkcję równoważenia obciążenia dla serwerów, które mają zainstalowany łącznik usług RMS, i rozważyć, czy dla połączeń między tymi serwerami i serwerami, które właśnie zostały autoryzowane, należy używać protokołu HTTPS.

## Konfigurowanie funkcji równoważenia obciążenia i wysokiej dostępności
Po zainstalowaniu drugiego lub końcowego wystąpienia łącznika usług RMS należy zdefiniować nazwę serwera w adresie URL łącznika i skonfigurować system z równoważeniem obciążenia.

Nazwa serwera w adresie URL łącznika może być dowolną nazwą w kontrolowanym obszarze nazw. Na przykład można utworzyć wpis w systemie DNS dla adresu **rmsconnector.contoso.com** i skonfigurować go do używania adresu IP w systemie równoważenia obciążenia. Nie ma żadnych specjalnych wymagań dla tej nazwy i nie musi być ona skonfigurowana na samych serwerach łącznika. Jeśli serwery programów Exchange i SharePoint nie będą komunikować się za pomocą łącznika przez Internet, ta nazwa nie musi być rozpoznawalna w sieci Internet.

> [!IMPORTANT]
> Zaleca się nie zmieniać tej nazwy po skonfigurowaniu serwerów programu Exchange i SharePoint do korzystania z łącznika, ponieważ należy następnie wyczyść wszystkie konfiguracje IRM tych serwerów i skonfigurować je ponownie.

Po utworzeniu nazwy w systemie DNS i skonfigurowaniu jej dla adresu IP należy skonfigurować dla tego adresu funkcję równoważenia obciążenia kierującą ruch do serwerów łącznika. Do tego celu można wykorzystać dowolną usługę równoważenia obciążenia opartą na protokole IP, która obejmuje funkcję równoważenia obciążenia sieciowego (NLB) w systemie Windows Server. Aby uzyskać więcej informacji, zobacz [Load Balancing Deployment Guide](http://technet.microsoft.com/library/cc754833%28v=WS.10%29.aspx) (Przewodnik wdrażania usługi równoważenia obciążenia).

Aby skonfigurować klaster równoważenia obciążenia sieciowego, użyj następujących ustawień:

-   Porty: 80 (dla protokołu HTTP) lub 443 (dla protokołu HTTPS)

    Aby uzyskać więcej informacji na temat użycia protokołu HTTP lub HTTPS, zobacz następną sekcję.

-   Koligacja: Brak

-   Metoda dystrybucji: równy

Nazwa zdefiniowana dla systemu z równoważeniem obciążenia (dla serwerów z uruchomioną usługą łącznika usług RMS) jest nazwą łącznika usług RMS w danej organizacji. Można jej użyć później, podczas konfigurowania serwerów lokalnych do korzystania z usługi Azure RMS.

## Konfigurowanie łącznika usług RMS do korzystania z protokołu HTTPS
> [!NOTE]
> Ten krok konfiguracji jest opcjonalny, ale zalecany w celu zapewnienia dodatkowej ochrony.

Mimo że korzystanie z protokołu TLS lub SSL jest opcjonalne dla łącznika usług RMS, jest zalecane dla dowolnej usługi opartej na protokole HTTP wymagającej zwiększonej ochrony. Ta konfiguracja uwierzytelnia serwery z łącznikiem na serwerach programu Exchange i SharePoint używających tego łącznika. Dodatkowo wszystkie dane, które są wysyłane z tych serwerów do łącznika są zaszyfrowane.

Aby umożliwić łącznikowi usług RMS wykorzystanie protokołu TLS, na każdym serwerze z uruchomionym łącznikiem usług RMS zainstaluj certyfikat uwierzytelniania serwera zawierający nazwę, która będzie używana dla łącznika. Na przykład jeśli nazwą Twojego łącznika usług RMS zdefiniowanego w systemie DNS jest **rmsconnector.contoso.com**, wdróż certyfikat uwierzytelniania serwera zawierający wpis **rmsconnector.contoso.com** w podmiocie certyfikatu jako nazwę pospolitą. Możesz także umieścić wpis **rmsconnector.contoso.com** w alternatywnej nazwie certyfikatu jako wartość DNS. Certyfikat nie musi obejmować nazwy serwera. Następnie w usługach IIS, powiąż ten certyfikat z domyślną witryny sieci Web.

Jeśli używasz opcji protokołu HTTPS, upewnij się, że wszystkie serwery z uruchomionym łącznikiem mają ważny certyfikat uwierzytelniania serwera, który tworzy łańcuch z zaufanym dla serwerów programu Exchange i SharePoint głównym urzędem certyfikacji. Ponadto jeśli urząd certyfikacji (CA), który wystawił certyfikaty dla serwerów łącznika publikuje listy odwołania certyfikatów (CRL), serwery programu Exchange i programu SharePoint muszą mieć możliwość pobrania tej listy CRL.

> [!TIP]
> Można użyć następujących informacji i zasobów w celu żądania i instalowania certyfikatu uwierzytelniania serwera i powiązania tego certyfikatu z domyślną witryną sieci Web w usługach IIS:
>
> -   Jeśli używasz usług certyfikatów w usłudze Active Directory (AD CS) i urzędu certyfikacji przedsiębiorstwa (CA) do wdrożenia tych certyfikatów uwierzytelniania serwera, możesz zduplikować, a następnie wykorzystać szablon certyfikatu serwera sieci Web. Ten szablon certyfikatu używa **podanej w żądaniu** nazwy podmiotu certyfikatu, co oznacza, że w przypadku żądania certyfikatu można podać nazwę FQDN łącznika usług RMS dla nazwy podmiotu certyfikatu lub alternatywnej nazwy podmiotu.
> -   Jeśli używasz autonomicznego urzędu certyfikacji lub nabywasz ten certyfikat od innej firmy, zobacz [Konfigurowanie certyfikatów serwera internetowego (usługi IIS 7)](http://technet.microsoft.com/library/cc731977%28v=ws.10%29.aspx) w bibliotece dokumentacji [serwera sieci Web (IIS)](http://technet.microsoft.com/library/cc753433%28v=ws.10%29.aspx) w witrynie TechNet.
> -   Aby skonfigurować usługi IIS do używania certyfikatu, zobacz [Dodawanie powiązań do witryny (usługi IIS 7)](http://technet.microsoft.com/library/cc731692.aspx) w bibliotece dokumentacji [serwera sieci Web (IIS)](http://technet.microsoft.com/library/cc753433%28v=ws.10%29.aspx) w witrynie TechNet.

## Konfigurowanie łącznika usług RMS dla serwera proxy sieci Web
Jeśli serwery łącznika są zainstalowane w sieci, która nie ma bezpośredniego połączenia z siecią Internet i wymaga ręcznej konfiguracji serwera proxy sieci Web dla zapewnienia ruchu wychodzącego do sieci Internet, należy na tych serwerach skonfigurować rejestr dla łącznika usług RMS.

#### Aby skonfigurować łącznik usług RMS w celu użycia serwera proxy sieci Web

1.  Na każdym serwerze z programem łącznika usług RMS otwórz edytor rejestru, np. Regedit.

2.  Przejdź do klucza **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\AADRM\Connector**

3.  Dodaj wartość ciągu **ProxyAddress**, a następnie ustaw dla tej wartości dane**http://&lt;Mój_adres_IP_lub_domena_serwera_proxy&gt;:&lt;Mój_port_serwera_proxy&gt;**.

    Na przykład: **http://serwerproxy.contoso.com:8080**

4.  Zamknij edytor rejestru, a następnie ponownie uruchom serwer lub wykonaj polecenie IISReset w celu ponownego uruchomienia usług IIS.

## Instalowanie narzędzia administracyjnego łącznika usług RMS na komputerach administracyjnych
Narzędzie administracyjne łącznika usług RMS można uruchomić z komputera, który nie ma zainstalowanego łącznika usług RMS, jeśli ten komputer spełnia następujące wymagania:

-   Komputer fizyczny lub wirtualny z systemem Windows Server 2012 lub Windows Server 2012 R2 (wszystkie wersje), Windows Server 2008 R2 lub Windows Server 2008 R2 z dodatkiem Service Pack 1 (wszystkie wersje), Windows 8.1, Windows 8 lub Windows 7.

-   Co najmniej 1 GB pamięci RAM.

-   Co najmniej 64 GB miejsca na dysku.

-   Co najmniej jeden interfejs sieciowy.

-   Dostęp do sieci Internet za pośrednictwem zapory (lub serwera proxy sieci Web).

Aby zainstalować narzędzie administracyjne łącznika usług RMS, uruchom następujące pliki:

-   Na komputerze 32-bitowym: RMSConnectorAdminToolSetup_x86.exe

-   Na komputerze 64-bitowym: RMSConnectorSetup.exe

Jeśli te pliki nie zostały już pobrane, możesz to zrobić w [Centrum pobierania Microsoft](http://go.microsoft.com/fwlink/?LinkId=314106).


## Następne kroki
Teraz, gdy łącznik RMS jest zainstalowany i skonfigurowany, można przystąpić do konfigurowania serwerów lokalnych, aby mogły z niego korzystać. Przejdź do sekcji [Konfigurowanie serwerów na potrzeby łącznika Azure Rights Management](configure-servers-rms-connector.md).


<!--HONumber=Jun16_HO4-->


