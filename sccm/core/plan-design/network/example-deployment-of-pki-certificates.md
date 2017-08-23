---
title: "Wdrożenie certyfikatów PKI | Dokumentacja firmy Microsoft"
description: "Wykonaj krok przykładowy sposób tworzenia i wdrażania certyfikatów infrastruktury kluczy publicznych, których używa System Center Configuration Manager."
ms.custom: na
ms.date: 02/14/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 3417ff88-7177-4a0d-8967-ab21fe7eba17
caps.latest.revision: "11"
author: arob98
ms.author: angrobe
manager: angrobe
ms.openlocfilehash: b15f85b4483bbae2444d4e73d2e2aa0b3979d9ab
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="step-by-step-example-deployment-of-the-pki-certificates-for-system-center-configuration-manager-windows-server-2008-certification-authority"></a>Krok po kroku Przykładowe wdrożenie certyfikatów PKI dla programu System Center Configuration Manager: Urząd certyfikacji systemu Windows Server 2008

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

To przykładowe krok wdrożenie, która używa urząd certyfikacji (CA) systemu Windows Server 2008, ma procedur pokazujących, sposobu tworzenia i wdrażania certyfikatów infrastruktury kluczy publicznych (PKI), których używa System Center Configuration Manager. W procedurach korzysta się z urzędu certyfikacji przedsiębiorstwa i z szablonów certyfikatów. Kroki procedur są właściwe tylko na użytek sieci testowej, jako weryfikacja koncepcji.  

 Ponieważ nie ma jednej właściwej metody wdrażania wymaganych certyfikatów, można znaleźć w dokumentacji konkretnego wdrożenia infrastruktury kluczy publicznych dla wymaganych procedur i najlepszych praktyk wdrażania wymaganych certyfikatów w środowisku produkcyjnym. Aby uzyskać więcej informacji na temat wymagań dotyczących certyfikatów, zobacz [wymagania dotyczące certyfikatu PKI dla programu System Center Configuration Manager](../../../core/plan-design/network/pki-certificate-requirements.md).  

> [!TIP]  
>  Istnieje możliwość dostosowania instrukcje w tym temacie dla systemów operacyjnych, które nie są udokumentowane w sekcji wymagania dotyczące sieci testowej. Niemniej jednak w przypadku uruchamiania urzędu certyfikacji wystawiającego certyfikat w systemie Windows Server 2012 nie jest wyświetlany monit o wersję szablonu certyfikatu. Zamiast tego należy określić to na **zgodności** właściwości szablonu:  
>   
>  -   **Urząd certyfikacji**: **Windows Server 2003**  
> -   **Odbiorca certyfikatu**: **Windows XP / Server 2003**  

## <a name="in-this-section"></a>W tej sekcji  
 W poniższych sekcjach zawarto przykładowe instrukcje krok po kroku dotyczące tworzenia i wdrażania następujących certyfikatów, które mogą być używane z System Center Configuration Manager:  

 [Wymagania dotyczące sieci testowej](#BKMK_testnetworkenvironment)  

 [Przegląd certyfikatów](#BKMK_overview2008)  

 [Wdrażanie certyfikatu serwera sieci web dla systemów lokacji z usługami IIS](#BKMK_webserver2008_cm2012)  

 [Wdrażanie certyfikatu usługi dla punktów dystrybucji w chmurze](#BKMK_clouddp2008_cm2012)  

 [Wdrażanie certyfikatu klienta dla komputerów z systemem Windows](#BKMK_client2008_cm2012)  

 [Wdrażanie certyfikatu klienta dla punktów dystrybucji](#BKMK_clientdistributionpoint2008_cm2012)  

 [Wdrażanie certyfikatu rejestracji dla urządzeń przenośnych](#BKMK_mobiledevices2008_cm2012)  

 [Wdrażanie certyfikatów dla AMT](#BKMK_AMT2008_cm2012)  

 [Wdrażanie certyfikatu klienta dla komputerów Mac](#BKMK_MacClient_SP1)  

##  <a name="BKMK_testnetworkenvironment"></a>Wymagania dotyczące sieci testowej  
 Z instrukcjami krok po kroku wiążą się następujące wymagania:  

-   W sieci testowej działają usługi domenowe Active Directory z systemem Windows Server 2008; instalacja to pojedyncza domena, pojedynczy las.  

-   Masz serwer członkowski z systemem Windows Server 2008 Enterprise Edition, który ma na nim zainstalowany roli usług certyfikatów Active Directory i jest on skonfigurowany jako główny urząd certyfikacji przedsiębiorstwa (CA).  

-   Istnieje jeden komputer z systemem Windows Server 2008 (Standard Edition lub Enterprise Edition, wersja R2 lub nowszy) na nim zainstalowany tego komputera jest wyznaczony jako serwer członkowski, a Internet Information Services (IIS) jest na nim zainstalowany. Ten komputer będzie serwer systemu lokacji programu System Center Configuration Manager, który skonfigurujesz z intranetu pełną nazwę domeny (FQDN) do obsługi połączeń klienckich w sieci intranet i internetowej nazwy FQDN, jeśli zachodzi potrzeba obsługi urządzeń przenośnych zarejestrowanych w programie System Center Configuration Manager i klienci w Internecie.  

-   Jeden klient systemu Windows Vista z najnowszego dodatku service pack zainstalowany, a ten komputer jest skonfigurowany przy użyciu nazwy komputera, by zawierała znaki ASCII, który jest przyłączony do domeny. Ten komputer będzie komputer kliencki System Center Configuration Manager.  

-   Możesz zalogować się przy użyciu konta administratora domeny głównej lub konta administratora domeny przedsiębiorstwa i wykorzystać to konto do wszystkich procedur tego przykładowego wdrożenia.  

##  <a name="BKMK_overview2008"></a>Przegląd certyfikatów  
 W poniższej tabeli wymieniono typy certyfikatów PKI, które mogą być wymagane dla programu System Center Configuration Manager i opisano sposób użycia.  

|Wymagany certyfikat|Opis certyfikatu|  
|-----------------------------|-----------------------------|  
|Certyfikat serwera sieci Web dla systemów lokacji z usługami IIS|Ten certyfikat służy do szyfrowania danych i uwierzytelniania serwera wobec klientów. Należy instalować go zewnętrznie z programu System Center Configuration Manager na serwerach systemów lokacji z systemem Internet Information Services (IIS), które są skonfigurowane w programie System Center Configuration Manager do używania protokołu HTTPS.<br /><br /> Aby uzyskać instrukcje dotyczące konfigurowania i instalowania tego certyfikatu, zobacz [wdrażania certyfikatu serwera sieci web dla systemów lokacji z usługami IIS](#BKMK_webserver2008_cm2012) w tym temacie.|  
|Certyfikat usługi dla klientów do łączenia się z chmurowymi punktami dystrybucji|Aby uzyskać instrukcje dotyczące konfigurowania i instalowania tego certyfikatu, zobacz [wdrożenia certyfikatu usługi dla punktów dystrybucji w chmurze](#BKMK_clouddp2008_cm2012) w tym temacie.<br /><br /> **Ważne:** Ten certyfikat jest używany w połączeniu z certyfikatem zarządzania platformy Microsoft Azure. Aby uzyskać więcej informacji o certyfikacie zarządzania, zobacz [jak utworzyć certyfikat zarządzania](http://go.microsoft.com/fwlink/p/?LinkId=220281) i [jak dodać certyfikat zarządzania do subskrypcji systemu Windows Azure](http://go.microsoft.com/fwlink/?LinkId=241722) w sekcji platformy Windows Azure w bibliotece MSDN.|  
|Certyfikat klienta dla komputerów z systemem Windows|Ten certyfikat służy do uwierzytelniania komputerów klienckich programu System Center Configuration Manager do systemów lokacji, które są skonfigurowane do używania protokołu HTTPS. Również umożliwia dla punktów zarządzania i punktów migracji stanu do monitorowania stanu operacyjnego, gdy są one skonfigurowane do używania protokołu HTTPS. Należy instalować go zewnętrznie z programu System Center Configuration Manager na komputerach.<br /><br /> Aby uzyskać instrukcje dotyczące konfigurowania i instalowania tego certyfikatu, zobacz [wdrażanie certyfikatu klienta dla komputerów z systemem Windows](#BKMK_client2008_cm2012) w tym temacie.|  
|Certyfikat klienta dla punktów dystrybucji|Ten certyfikat ma dwa cele:<br /><br /> Certyfikat służy do uwierzytelniania punktu dystrybucji wobec punktu zarządzania z włączonym protokołem HTTPS przed wysłaniem przez dany punkt dystrybucji komunikatów o stanie.<br /><br /> Po wybraniu w punkcie dystrybucji opcji **Włącz obsługę środowiska PXE dla klientów** certyfikat zostanie wysłany do komputerów przeprowadzających rozruch w środowisku PXE, aby umożliwić im połączenie z punktem zarządzania z włączoną obsługą HTTPS podczas wdrażania systemu operacyjnego.<br /><br /> Aby uzyskać instrukcje dotyczące konfigurowania i instalowania tego certyfikatu, zobacz [wdrażanie certyfikatu klienta dla punktów dystrybucji](#BKMK_clientdistributionpoint2008_cm2012) w tym temacie.|  
|Certyfikat rejestracji dla urządzeń przenośnych|Ten certyfikat służy do uwierzytelniania klientów urządzeń przenośnych programu System Center Configuration Manager do systemów lokacji, które są skonfigurowane do używania protokołu HTTPS. Musi być zainstalowany w ramach rejestracji urządzeń przenośnych w programie System Center Configuration Manager, a następnie wybierz skonfigurowany szablon certyfikatu jako ustawienie klienta urządzenia przenośnego.<br /><br /> Aby uzyskać instrukcje dotyczące konfigurowania tego certyfikatu, zobacz [wdrażanie certyfikatu rejestracji dla urządzeń przenośnych](#BKMK_mobiledevices2008_cm2012) w tym temacie.|  
|Certyfikaty dla komputerów Intel AMT|Trzy certyfikaty odnoszą się do zarządzania poza pasmem komputerami opartymi na technologii Intel AMT:<ul><li>Certyfikat udostępniania technologii zarządzania aktywnego (AMT)</li><li>Certyfikat serwera sieci web AMT</li><li>Opcjonalnie certyfikat uwierzytelniania klienta dla 802.1 X sieci przewodowej lub bezprzewodowej</li></ul>Certyfikat udostępniania AMT musi być zainstalowany zewnętrznie z programu System Center Configuration Manager na komputerze punktu Usługi poza pasmem, a następnie wybierz certyfikat zainstalowany we właściwościach punktu Usługi poza pasmem. Certyfikat serwera sieci web AMT i certyfikat uwierzytelniania klienta są instalowane podczas udostępniania AMT i zarządzania i wybierz szablony certyfikatów skonfigurowane we właściwościach składnika zarządzania poza pasmem.<br /><br /> Aby uzyskać instrukcje dotyczące konfigurowania tych certyfikatów, zobacz [wdrożyć certyfikaty dla AMT](#BKMK_AMT2008_cm2012) w tym temacie.|  
|Certyfikat klienta dla komputerów Mac|Można zażądać oraz instalacji tego certyfikatu z komputera Mac, użyj rejestracji za pomocą programu System Center Configuration Manager i wybrać jako ustawienie klienta urządzenia przenośnego skonfigurowany szablon certyfikatu.<br /><br /> Aby uzyskać instrukcje dotyczące konfigurowania tego certyfikatu, zobacz [wdrażanie certyfikatu klienta dla komputerów Mac](#BKMK_MacClient_SP1) w tym temacie.|  

##  <a name="BKMK_webserver2008_cm2012"></a>Wdrażanie certyfikatu serwera sieci web dla systemów lokacji z usługami IIS  
 Wdrożenie tego certyfikatu jest objęte następującymi procedurami:  

-   Utworzyć i wystawić szablon certyfikatu w urzędzie certyfikacji serwera sieci web  

-   Żądanie certyfikatu serwera sieci web  

-   Skonfiguruj usługi IIS do używania certyfikatu serwera sieci web  

###  <a name="BKMK_webserver22008"></a>Utworzyć i wystawić szablon certyfikatu w urzędzie certyfikacji serwera sieci web  
 Ta procedura powoduje utworzenie szablonu certyfikatu dla systemów lokacji programu System Center Configuration Manager i dodaje go do urzędu certyfikacji.  

##### <a name="to-create-and-issue-the-web-server-certificate-template-on-the-certification-authority"></a>Aby utworzyć i wystawić szablon certyfikatu serwera sieci Web w urzędzie certyfikacji  

1.  Utwórz grupę zabezpieczeń o nazwie **serwery IIS programu ConfigMgr** zawierającej serwery Członkowskie do zainstalowania systemów lokacji programu System Center Configuration Manager, z uruchomionymi usługami IIS.  

2.  Na serwerze członkowskim z usługami certyfikatów zainstalowane, w konsoli Urząd certyfikacji kliknij prawym przyciskiem myszy **szablonów certyfikatów** , a następnie wybierz **Zarządzaj** załadować **szablonów certyfikatów** konsoli.  

3.  W okienku wyników kliknij prawym przyciskiem myszy wpis **serwera sieci Web** w **Nazwa wyświetlana szablonu** kolumny, a następnie wybierz pozycję **Duplikuj szablon**.  

4.  W **Duplikuj szablon** okna dialogowego Sprawdź, czy **systemu Windows Server 2003, Enterprise Edition** jest zaznaczone, a następnie wybierz pozycję **OK**.  

    > [!IMPORTANT]  
    >  Nie wybieraj systemu **Windows 2008 Server, Enterprise Edition**.  

5.  W **właściwości nowego szablonu** na okna dialogowego **ogólne** wprowadź nazwę szablonu, takie jak **certyfikat serwera sieci Web programu ConfigMgr**, w celu wygenerowania certyfikatów sieci web, które będą używane w systemach lokacji programu Configuration Manager.  

6.  Wybierz **nazwa podmiotu** karcie i upewnij się, że **Dostarcz w żądaniu** jest zaznaczone.  

7.  Wybierz **zabezpieczeń** karcie, a następnie usuń **Zarejestruj** zgody **Administratorzy domeny** i **Administratorzy przedsiębiorstwa** grup zabezpieczeń.  

8.  Wybierz **Dodaj**, wprowadź **serwery IIS programu ConfigMgr** w tekście polu, a następnie wybierz pozycję **OK**.  

9. Wybierz **Zarejestruj** dla tej grupy uprawnienie i nie usuwaj **odczytu** uprawnienia.  

10. Wybierz **OK**, a następnie Zamknij **konsolę Szablony certyfikatów**.  

11. W konsoli Urząd certyfikacji kliknij prawym przyciskiem myszy **szablonów certyfikatów**, wybierz **nowy**, a następnie wybierz pozycję **szablon certyfikatu do wystawienia**.  

12. W **Włączanie szablonu certyfikatu** okno dialogowe Nowy szablon, który właśnie utworzony, wybierz pozycję **certyfikat serwera sieci Web programu ConfigMgr**, a następnie wybierz pozycję **OK**.  

13. Jeśli nie ma potrzeby tworzenia i wystawiania certyfikatów więcej, Zamknij **urzędu certyfikacji**.  

###  <a name="BKMK_webserver32008"></a>Żądanie certyfikatu serwera sieci web  
 Ta procedura pozwala określić wartości intranetowej i internetowej nazwy FQDN wartości, które będą skonfigurowane we właściwościach serwera systemu lokacji, a następnie instaluje certyfikat serwera sieci web na serwerze członkowskim z uruchomionymi usługami IIS.  

##### <a name="to-request-the-web-server-certificate"></a>Aby zażądać certyfikatu serwera sieci Web  

1.  Uruchom ponownie serwer członkowski z uruchomionymi usługami IIS, aby upewnić się, że komputer ma dostęp do szablonu certyfikatu, który został utworzony za pomocą **odczytu** i **Zarejestruj** skonfigurowanych uprawnień.  

2.  Wybierz **Start**, wybierz **Uruchom**, a następnie wpisz **mmc.exe.** W pustej konsoli wybierz **pliku**, a następnie wybierz pozycję **Dodaj/Usuń przystawkę**.  

3.  W **Dodawanie lub usuwanie przystawek** oknie dialogowym wybierz **certyfikaty** z listy **dostępne przystawki**, a następnie wybierz pozycję **Dodaj**.  

4.  W **certyfikatów przystawki** okno dialogowe Wybierz **konto komputera**, a następnie wybierz pozycję **dalej**.  

5.  W **Wybieranie komputera** okna dialogowego Sprawdź, czy **komputer lokalny: (komputer ten jest uruchomiona konsola)** jest zaznaczone, a następnie wybierz pozycję **Zakończ**.  

6.  W **Dodawanie lub usuwanie przystawek** oknie dialogowym wybierz **OK**.  

7.  W konsoli rozwiń węzeł **certyfikaty (komputer lokalny)**, a następnie wybierz pozycję **osobistych**.  

8.  Kliknij prawym przyciskiem myszy **certyfikaty**, wybierz **wszystkie zadania**, a następnie wybierz pozycję **Żądaj nowego certyfikatu**.  

9. Na **przed rozpoczęciem** wybierz pozycję **dalej**.  

10. Jeśli widzisz **wybierz zasady rejestracji certyfikatu** wybierz pozycję **dalej**.  

11. Na **żądania certyfikatów** Znajdź **certyfikat serwera sieci Web programu ConfigMgr** z listy dostępnych certyfikatów, a następnie wybierz pozycję **do zarejestrowania tego certyfikatu jest wymaganych więcej informacji. Kliknij tutaj, aby skonfigurować ustawienia**.  

12. W **właściwości certyfikatu** okna dialogowego, **podmiotu** karcie, nie należy wprowadzać żadnych zmian do **nazwa podmiotu**. Inaczej mówiąc, pole **Wartość** w sekcji **Nazwa podmiotu** pozostanie puste. Zamiast tego w **alternatywnej nazwy** wybierz **typu** listy rozwijanej liście, a następnie wybierz pozycję **DNS**.  

13. W **wartość** określ te wartości nazw FQDN, które będą określonym we właściwościach systemu lokacji programu System Center Configuration Manager, a następnie wybierz pozycję **OK** zamknąć **właściwości certyfikatu** okno dialogowe.  

     Przykłady:  

    -   Jeśli system lokacji przyjmuje tylko połączenia klienckie z intranetu, a intranetowa nazwa FQDN serwera systemu lokacji to **server1.internal.contoso.com**, wprowadź **server1.internal.contoso.com**, a następnie wybierz pozycję **Dodaj**.  

    -   Jeśli system lokacji przyjmuje połączenia klienckie i z intranetu, i z Internetu, przy czym intranetowa nazwa FQDN serwera systemu lokacji to **server1.internal.contoso.com** , a internetowa nazwa FQDN serwera systemu lokacji to **server.contoso.com**:  

        1.  Wprowadź **server1.internal.contoso.com**, a następnie wybierz pozycję **Dodaj**.  

        2.  Wprowadź **server.contoso.com**, a następnie wybierz pozycję **Dodaj**.  

        > [!NOTE]  
        >  Można określić nazwy FQDN dla programu System Center Configuration Manager w dowolnej kolejności. Należy jednak sprawdzić, czy wszystkie urządzenia, które będą używać certyfikatu, takie jak urządzenia przenośne i serwerów proxy sieci web, można użyć nazwy alternatywnej podmiotu (SAN) certyfikatu oraz wielu wartości w sieci SAN. Jeśli urządzenia obsługują ograniczoną liczbę wartości SAN w certyfikatach, może zajść potrzeba zmiany kolejności nazw FQDN lub użycia zamiast nich wartości Podmiot.  

14. Na **żądania certyfikatów** wybierz pozycję **certyfikat serwera sieci Web programu ConfigMgr** z listy dostępnych certyfikatów, a następnie wybierz pozycję **Zarejestruj**.  

15. Na **wyniki instalacji certyfikatów** strony, poczekaj, aż certyfikat został zainstalowany, a następnie wybierz **Zakończ**.  

16. Zamknij konsolę **Certyfikaty (komputer lokalny)**.  

###  <a name="BKMK_webserver42008"></a>Skonfiguruj usługi IIS do używania certyfikatu serwera sieci web  
 Ta procedura wiąże zainstalowany certyfikat z **Domyślną witryną sieci Web**usług IIS.  

##### <a name="to-set-up-iis-to-use-the-web-server-certificate"></a>Aby skonfigurować usługi IIS do używania certyfikatu serwera sieci web  

1.  Na serwerze członkowskim, na którym są zainstalowane usługi IIS, wybierz **Start**, wybierz **programy**, wybierz **narzędzia administracyjne**, a następnie wybierz pozycję **Internet Information Services (IIS) Manager**.  

2.  Rozwiń węzeł **witryny**, kliknij prawym przyciskiem myszy **domyślna witryna sieci Web**, a następnie wybierz pozycję **Edytuj powiązania**.  

3.  Wybierz **https** wpis, a następnie wybierz pozycję **Edytuj**.  

4.  W **edytowanie powiązań witryny** okno dialogowe, wybierz certyfikat, którego zażądano za pomocą szablonu certyfikat serwera sieci Web programu ConfigMgr, a następnie **OK**.  

    > [!NOTE]  
    >  Jeśli nie masz pewności, który certyfikat jest tym właściwym, wybierz jedną, a następnie wybierz **widoku**. Pozwala to porównać szczegóły wybranego certyfikatu do certyfikatów w przystawce Certyfikaty. Na przykład przystawki Certyfikaty zawiera szablon certyfikatu, który został użyty do żądania certyfikatu. Możesz następnie porównać odcisk palca certyfikatu, którego zażądano za pomocą szablonu certyfikat serwera sieci Web programu ConfigMgr do odcisk palca certyfikatu aktualnie wybranego w **edytowanie powiązań witryny** okno dialogowe.  

5.  Wybierz **OK** w **edytowanie powiązań witryny** okna dialogowego polu, a następnie wybierz pozycję **Zamknij**.  

6.  Zamknij **Menedżera internetowych usług informacyjnych (IIS)**.  

 Serwer członkowski jest skonfigurowane przy użyciu certyfikatu serwera sieci web programu System Center Configuration Manager.  

> [!IMPORTANT]  
>  Po zainstalowaniu serwera systemu lokacji programu System Center Configuration Manager na tym komputerze, upewnij się, określ tej samej nazwy FQDN we właściwościach systemu lokacji, jak określono podczas żądania certyfikatu.  

##  <a name="BKMK_clouddp2008_cm2012"></a>Wdrażanie certyfikatu usługi dla punktów dystrybucji w chmurze  

Wdrożenie tego certyfikatu jest objęte następującymi procedurami:  

-   [Utworzyć i wydać szablon certyfikatu w urzędzie certyfikacji serwera sieci web niestandardowego](#BKMK_clouddpcreating2008)  

-   [Żądanie certyfikatu serwera sieci web niestandardowego](#BKMK_clouddprequesting2008)  

-   [Eksportowanie certyfikatu serwera sieci web niestandardowego dla punktów dystrybucji w chmurze](#BKMK_clouddpexporting2008)  

###  <a name="BKMK_clouddpcreating2008"></a>Utworzyć i wydać szablon certyfikatu w urzędzie certyfikacji serwera sieci web niestandardowego  
 Ta procedura powoduje utworzenie niestandardowego szablonu certyfikatu opartego na szablonie certyfikatu serwera sieci web. Certyfikat jest przeznaczony dla punktów dystrybucji w chmurze programu System Center Configuration Manager i klucz prywatny musi być możliwy do eksportu. Po utworzeniu szablon certyfikatu jest dodawany do urzędu certyfikacji.  

> [!NOTE]  
>  Ta procedura wykorzystuje inny szablon certyfikatu z utworzonego szablonu certyfikatu serwera sieci web dla systemów lokacji z usługami IIS. Mimo że certyfikaty wymagają funkcji uwierzytelniania serwera, certyfikat dla punktów dystrybucji w chmurze wymaga wprowadzenia niestandardowej wartości w polu Nazwa podmiotu i można wyeksportować klucza prywatnego. Zabezpieczeń najlepszym rozwiązaniem, czy nie Konfigurowanie szablonów certyfikatów, dzięki czemu można można wyeksportować klucza prywatnego, chyba że taka konfiguracja jest wymagana. Punkt dystrybucji w chmurze wymaga tej konfiguracji, ponieważ należy zaimportować certyfikat jako plik, zamiast wybierz go z magazynu certyfikatów.  
>   
>  Podczas tworzenia nowego szablonu certyfikatu dla tego certyfikatu, można ograniczyć komputerów, które może zażądać certyfikatu, którego klucz prywatny można eksportować. W sieci produkcyjnej można także rozważyć wprowadzenie następujących zmian dla tego certyfikatu:  
>   
>  -   Wymaganie zatwierdzenia instalacji certyfikatu w celu zapewnienia dodatkowych zabezpieczeń.  
> -   Wydłużenie okresu ważności certyfikatu. Ponieważ należy wyeksportować i zaimportować certyfikat każdorazowo przed jego wygaśnięciem, zwiększenia okresu ważności zmniejsza częstotliwość należy powtórzyć całą procedurę. Jednak wzrost okresu ważności również zmniejszenie bezpieczeństwa certyfikatu, ponieważ zawiera więcej czasu osobie atakującej do odszyfrowania klucza prywatnego i kradzież certyfikatu.  
> -   Użycie niestandardowej wartości nazwa alternatywnej podmiotu (SAN) w celu łatwiejszego odróżnienia tego certyfikatu od standardowych certyfikatów serwera sieci Web używanego z programem IIS.  

##### <a name="to-create-and-issue-the-custom-web-server-certificate-template-on-the-certification-authority"></a>Aby utworzyć i wystawić szablon certyfikatu w urzędzie certyfikacji serwera sieci web niestandardowego  

1.  Utwórz grupę zabezpieczeń o nazwie **serwerów lokacji programu ConfigMgr** zawierającej serwery Członkowskie do zainstalowania serwerów lokacji podstawowej programu System Center Configuration Manager, które będą zarządzać punktami dystrybucji w chmurze.  

2.  Na serwerze członkowskim, na którym uruchomiona jest Konsola urzędu certyfikacji, kliknij prawym przyciskiem myszy **szablonów certyfikatów**, a następnie wybierz pozycję **Zarządzaj** aby załadować Konsolę zarządzania szablony certyfikatów.  

3.  W okienku wyników kliknij prawym przyciskiem myszy wpis **serwera sieci Web** w **Nazwa wyświetlana szablonu** kolumny, a następnie wybierz pozycję **Duplikuj szablon**.  

4.  W **Duplikuj szablon** okna dialogowego Sprawdź, czy **systemu Windows Server 2003, Enterprise Edition** jest zaznaczone, a następnie wybierz pozycję **OK**.  

    > [!IMPORTANT]  
    >  Nie wybieraj systemu **Windows 2008 Server, Enterprise Edition**.  

5.  W **właściwości nowego szablonu** na okna dialogowego **ogólne** wprowadź nazwę szablonu, takie jak **certyfikat punktu dystrybucji w chmurze programu ConfigMgr**, w celu wygenerowania certyfikatu serwera sieci web dla punktów dystrybucji w chmurze.  

6.  Wybierz **obsługiwanie żądań** karcie, a następnie wybierz pozycję **Zezwalaj na eksportowanie klucza prywatnego**.  

7.  Wybierz **zabezpieczeń** karcie, a następnie usuń **Zarejestruj** zgody **Administratorzy przedsiębiorstwa** grupy zabezpieczeń.  

8.  Wybierz **Dodaj**, wprowadź **serwerów lokacji programu ConfigMgr** w tekście polu, a następnie wybierz pozycję **OK**.  

9. Wybierz dla tej grupy uprawnienie **Rejestracja** i nie usuwaj zaznaczenia uprawnienia **Odczyt** .  

10. Wybierz **OK**, a następnie Zamknij **konsolę Szablony certyfikatów**.  

11. W konsoli Urząd certyfikacji kliknij prawym przyciskiem myszy **szablonów certyfikatów**, wybierz **nowy**, a następnie wybierz pozycję **szablon certyfikatu do wystawienia**.  

12. W **Włączanie szablonu certyfikatu** okno dialogowe Nowy szablon, który właśnie utworzony, wybierz pozycję **certyfikat punktu dystrybucji w chmurze programu ConfigMgr**, a następnie wybierz pozycję **OK**.  

13. Jeśli nie masz do tworzenia i wystawiania certyfikatów więcej, Zamknij **urzędu certyfikacji**.  

###  <a name="BKMK_clouddprequesting2008"></a>Żądanie certyfikatu serwera sieci web niestandardowego  
 Ta procedura żądań, a następnie instaluje certyfikat serwera sieci web niestandardowego na serwerze członkowskim, który będzie uruchamiany na serwerze lokacji.  

##### <a name="to-request-the-custom-web-server-certificate"></a>Aby zażądać niestandardowego certyfikatu serwera sieci Web  

1.  Uruchom ponownie serwer członkowski po utworzeniu i skonfigurowaniu **serwerów lokacji programu ConfigMgr** grupy zabezpieczeń, aby upewnić się, że komputer ma dostęp do szablonu certyfikatu, który został utworzony za pomocą **odczytu** i **Zarejestruj** skonfigurowanych uprawnień.  

2.  Wybierz **Start**, wybierz **Uruchom**, a następnie wprowadź **mmc.exe.** W pustej konsoli wybierz **pliku**, a następnie wybierz pozycję **Dodaj/Usuń przystawkę**.  

3.  W **Dodawanie lub usuwanie przystawek** oknie dialogowym wybierz **certyfikaty** z listy **dostępne przystawki**, a następnie wybierz pozycję **Dodaj**.  

4.  W **certyfikatów przystawki** okno dialogowe Wybierz **konto komputera**, a następnie wybierz pozycję **dalej**.  

5.  W **Wybieranie komputera** okna dialogowego Sprawdź, czy **komputer lokalny: (komputer ten jest uruchomiona konsola)** jest zaznaczone, a następnie wybierz pozycję **Zakończ**.  

6.  W **Dodawanie lub usuwanie przystawek** oknie dialogowym wybierz **OK**.  

7.  W konsoli rozwiń węzeł **certyfikaty (komputer lokalny)**, a następnie wybierz pozycję **osobistych**.  

8.  Kliknij prawym przyciskiem myszy **certyfikaty**, wybierz **wszystkie zadania**, a następnie wybierz pozycję **Żądaj nowego certyfikatu**.  

9. Na **przed rozpoczęciem** wybierz pozycję **dalej**.  

10. Jeśli widzisz **wybierz zasady rejestracji certyfikatu** wybierz pozycję **dalej**.  

11. Na **żądania certyfikatów** Znajdź **certyfikat punktu dystrybucji w chmurze programu ConfigMgr** z listy dostępnych certyfikatów, a następnie wybierz pozycję **więcej informacji jest wymagany do zarejestrowania dla tego certyfikatu. Wybierz tutaj Konfigurowanie ustawień**.  

12. W **właściwości certyfikatu** okna dialogowego, **podmiotu** karcie dla **nazwa podmiotu**, wybierz **nazwa pospolita** jako **typu**.  

13. W polu **Wartość** określ wybór nazwy usługi i nazwy domeny, używając formatu FQDN. Na przykład: **clouddp1.contoso.com**.  

    > [!NOTE]  
    >  Nazwa usługi należy unikatowa w danym obszarze nazw. Zostanie użyty system DNS w celu utworzenia aliasu (rekordu CNAME) i odwzorowania tej nazwy usługi na automatycznie generowany identyfikator (GUID) i adres IP z usługi Windows Azure.  

14. Wybierz **Dodaj**, a następnie wybierz pozycję **OK** zamknąć **właściwości certyfikatu** okno dialogowe.  

15. Na **żądania certyfikatów** wybierz pozycję **certyfikat punktu dystrybucji w chmurze programu ConfigMgr** z listy dostępnych certyfikatów, a następnie wybierz pozycję **Zarejestruj**.  

16. Na **wyniki instalacji certyfikatów** strony, poczekaj, aż certyfikat został zainstalowany, a następnie wybierz **Zakończ**.  

17. Zamknij konsolę **Certyfikaty (komputer lokalny)**.  

###  <a name="BKMK_clouddpexporting2008"></a>Eksportowanie certyfikatu serwera sieci web niestandardowego dla punktów dystrybucji w chmurze  
 Ta procedura umożliwia wyeksportowanie niestandardowego certyfikatu serwera sieci Web do pliku, aby można go było zaimportować po utworzeniu chmurowego punktu dystrybucji.  

##### <a name="to-export-the-custom-web-server-certificate-for-cloud-based-distribution-points"></a>Aby wyeksportować niestandardowy certyfikat serwera sieci Web dla chmurowych punktów dystrybucji  

1.  W **certyfikaty (komputer lokalny)** konsoli, kliknij prawym przyciskiem myszy certyfikat, który został właśnie zainstalowany, wybierz **wszystkie zadania**, a następnie wybierz pozycję **wyeksportować**.  

2.  W Kreatorze eksportu certyfikatów wybierz **dalej**.  

3.  Na **eksportowanie klucza prywatnego** wybierz pozycję **tak, Eksportuj klucz prywatny**, a następnie wybierz pozycję **dalej**.  

    > [!NOTE]  
    >  Jeżeli ta opcja nie jest dostępna, certyfikat został utworzony bez opcji eksportu klucza prywatnego. W tym scenariuszu nie można wyeksportować certyfikatu w wymaganym formacie. Należy skonfigurować szablon certyfikatu, aby klucz prywatny można wyeksportować, a następnie zażądać certyfikatu ponownie.  

4.  Na **Format pliku eksportu** strony, upewnij się, że **wymiana informacji osobistych — PKCS #12 (. PFX)** opcja jest zaznaczona.  

5.  Na **hasło** Określ silne hasło, aby zabezpieczyć wyeksportowany certyfikat kluczem prywatnym, a następnie wybierz pozycję **dalej**.  

6.  Na **Eksport pliku** strony, określ nazwę pliku, który chcesz wyeksportować, a następnie wybierz pozycję **dalej**.  

7.  Aby zamknąć kreatora, należy wybrać **Zakończ** w **Kreatora eksportu certyfikatów** strony, a następnie wybierz pozycję **OK** w oknie dialogowym potwierdzenia.  

8.  Zamknij konsolę **Certyfikaty (komputer lokalny)**.  

9. Zapisz plik w bezpiecznym miejscu i upewnij się, że można do niego dostęp z konsoli programu System Center Configuration Manager.  

 Certyfikat jest teraz gotowy do zaimportowania po utworzeniu chmurowego punktu dystrybucji.  

##  <a name="BKMK_client2008_cm2012"></a>Wdrażanie certyfikatu klienta dla komputerów z systemem Windows  
 Wdrożenie tego certyfikatu jest objęte następującymi procedurami:  

-   Utworzyć i wydać szablon certyfikatu uwierzytelniania stacji roboczej w urzędzie certyfikacji  

-   Konfigurowanie automatycznej rejestracji szablonu uwierzytelniania stacji roboczej za pomocą zasad grupy  

-   Automatyczne rejestrowanie certyfikatu uwierzytelniania stacji roboczej i zweryfikować jego instalację na komputerach  

###  <a name="BKMK_client02008"></a>Utworzyć i wydać szablon certyfikatu uwierzytelniania stacji roboczej w urzędzie certyfikacji  
 Ta procedura powoduje utworzenie szablonu certyfikatu dla klienta programu System Center Configuration Manager z komputerów i dodaje go do urzędu certyfikacji.  

##### <a name="to-create-and-issue-the-workstation-authentication-certificate-template-on-the-certification-authority"></a>Aby utworzyć i wydać szablon certyfikatu uwierzytelniania stacji roboczej w urzędzie certyfikacji  

1.  Na serwerze członkowskim, na którym uruchomiona jest Konsola urzędu certyfikacji, kliknij prawym przyciskiem myszy **szablonów certyfikatów**, a następnie wybierz pozycję **Zarządzaj** aby załadować Konsolę zarządzania szablony certyfikatów.  

2.  W okienku wyników kliknij prawym przyciskiem myszy wpis **Uwierzytelnianie stacji roboczej** w **Nazwa wyświetlana szablonu** kolumny, a następnie wybierz pozycję **Duplikuj szablon**.  

3.  W **Duplikuj szablon** okna dialogowego Sprawdź, czy **systemu Windows Server 2003, Enterprise Edition** jest zaznaczone, a następnie wybierz pozycję **OK**.  

    > [!IMPORTANT]  
    >  Nie wybieraj systemu **Windows 2008 Server, Enterprise Edition**.  

4.  W **właściwości nowego szablonu** na okna dialogowego **ogólne** wprowadź nazwę szablonu, takie jak **certyfikat klienta programu ConfigMgr**, w celu wygenerowania certyfikatów klienta, które zostaną użyte na komputerach klienckich programu Configuration Manager.  

5.  Wybierz **zabezpieczeń** wybierz opcję **komputery domeny** , a następnie wybierz dodatkowe uprawnienia **odczytu** i **Autorejestrowanie**. Nie usuwaj zaznaczenia opcji **Rejestracja**.  

6.  Wybierz **OK**, a następnie Zamknij **konsolę Szablony certyfikatów**.  

7.  W konsoli Urząd certyfikacji kliknij prawym przyciskiem myszy **szablonów certyfikatów**, wybierz **nowy**, a następnie wybierz pozycję **szablon certyfikatu do wystawienia**.  

8.  W **Włączanie szablonu certyfikatu** okno dialogowe Nowy szablon, który właśnie utworzony, wybierz pozycję **certyfikat klienta programu ConfigMgr**, a następnie wybierz pozycję **OK**.  

9. Jeśli nie ma potrzeby tworzenia i wystawiania certyfikatów więcej, Zamknij **urzędu certyfikacji**.  

###  <a name="BKMK_client12008"></a>Konfigurowanie automatycznej rejestracji szablonu uwierzytelniania stacji roboczej za pomocą zasad grupy  
 Ta procedura konfiguruje zasady grupy do autorejestrowania certyfikatu klienta na komputerach.  

##### <a name="to-set-up-autoenrollment-of-the-workstation-authentication-template-by-using-group-policy"></a>Aby skonfigurować autorejestrację szablonu uwierzytelniania stacji roboczej za pomocą zasad grupy  

1.  Na kontrolerze domeny, wybierz **Start**, wybierz **narzędzia administracyjne**, a następnie wybierz pozycję **Zarządzanie zasadami grupy**.  

2.  Przejdź do domeny, kliknij prawym przyciskiem myszy domenę, a następnie wybierz pozycję **Utwórz obiekt GPO w tej domenie i umieść tu łącze**.  

    > [!NOTE]  
    >  W tym kroku wykorzystano najlepsze rozwiązanie dotyczące tworzenia nowej zasady grupy dla ustawień niestandardowych zamiast edycji domyślnych zasad domeny instalowanych za pomocą usług domenowych w usłudze Active Directory. Po przypisaniu zasad grupy na poziomie domeny spowoduje zastosować je do wszystkich komputerów w domenie. W środowisku produkcyjnym można ograniczyć autorejestrację tak, aby dotyczyła ona tylko wybranych komputerów. Można przypisać zasady grupy na poziomie jednostki organizacyjnej lub zasad grupy z grupą zabezpieczeń domeny można filtrować, że jest ona stosowana tylko do komputerów w grupie. Jeśli przypadku ograniczenia autorejestracji należy pamiętać o uwzględnieniu serwera, który jest skonfigurowany jako punkt zarządzania.  

3.  W **nowy obiekt zasad grupy** okna dialogowego wprowadź nazwę, jak **autorejestrowanie certyfikatów**, nowe zasady grupy, a następnie wybierz pozycję **OK**.  

4.  W okienku wyników na **powiązane obiekty zasad grupy** karcie, kliknij prawym przyciskiem myszy nową zasadę grupy, a następnie wybierz **Edytuj**.  

5.  W **Edytor zarządzania zasadami grupy**, rozwiń węzeł **zasady** w obszarze **Konfiguracja komputera**, a następnie przejdź do **ustawienia systemu Windows** / **ustawienia zabezpieczeń** / **zasady kluczy publicznych**.  

6.  Kliknij prawym przyciskiem myszy typ obiektu o nazwie **klient usług certyfikatów — automatyczna rejestracja**, a następnie wybierz pozycję **właściwości**.  

7.  Z **Model konfiguracji** listy rozwijanej wybierz pozycję **włączone**, wybierz **Odnów wygasłe certyfikaty, aktualizuj oczekujące certyfikaty, usuń odwołane certyfikaty**, wybierz **Aktualizuj certyfikaty, które używają szablonów certyfikatów**, a następnie wybierz pozycję **OK**.  

8.  Zamknij okno **Zarządzanie zasadami grupy**.  

###  <a name="BKMK_client22008"></a>Automatyczne rejestrowanie certyfikatu uwierzytelniania stacji roboczej i zweryfikować jego instalację na komputerach  
 Ta procedura powoduje zainstalowanie certyfikatu klienta na komputerach i weryfikację instalacji.  

##### <a name="to-automatically-enroll-the-workstation-authentication-certificate-and-verify-its-installation-on-the-client-computer"></a>Aby automatycznie zarejestrować certyfikat uwierzytelniania stacji roboczej i zweryfikować jego instalację na komputerze klienckim  

1.  Uruchom ponownie stację roboczą i poczekaj kilka minut przed zalogowaniem.  

    > [!NOTE]  
    >  Ponowne uruchomienie komputera to najbardziej niezawodna metoda zapewnienia pomyślnej autorejestracji certyfikatu.  

2.  Zaloguj się przy użyciu konta z uprawnieniami administratora.  

3.  W polu wyszukiwania wprowadź **mmc.exe.**, a następnie naciśnij klawisz **Enter**.  

4.  W pustej konsoli zarządzania, wybierz **pliku**, a następnie wybierz pozycję **Dodaj/Usuń przystawkę**.  

5.  W **Dodawanie lub usuwanie przystawek** oknie dialogowym wybierz **certyfikaty** z listy **dostępne przystawki**, a następnie wybierz pozycję **Dodaj**.  

6.  W **certyfikatów przystawki** okno dialogowe Wybierz **konto komputera**, a następnie wybierz pozycję **dalej**.  

7.  W **Wybieranie komputera** okna dialogowego Sprawdź, czy **komputer lokalny: (komputer ten jest uruchomiona konsola)** jest zaznaczone, a następnie wybierz pozycję **Zakończ**.  

8.  W **Dodawanie lub usuwanie przystawek** oknie dialogowym wybierz **OK**.  

9. W konsoli rozwiń węzeł **certyfikaty (komputer lokalny)**, rozwiń węzeł **osobistych**, a następnie wybierz pozycję **certyfikaty**.  

10. W okienku wyników sprawdź, czy certyfikat ma **uwierzytelnianie klienta** w **zamierzony cel** kolumny, a **certyfikat klienta programu ConfigMgr** w **szablonu certyfikatu** kolumny.  

11. Zamknij konsolę **Certyfikaty (komputer lokalny)**.  

12. Powtórz kroki od 1 do 11 dla serwera członkowskiego, aby sprawdzić, czy serwer, który będzie można skonfigurować jako punkt zarządzania również jest certyfikat klienta.  

 Komputer jest skonfigurowany z certyfikatem klienta programu System Center Configuration Manager.  

##  <a name="BKMK_clientdistributionpoint2008_cm2012"></a>Wdrażanie certyfikatu klienta dla punktów dystrybucji  

> [!NOTE]  
>  Tego certyfikatu można także użyć dla obrazów nośników, które nie używają rozruchu PXE, ponieważ wymagania dotyczące certyfikatu są takie same.  

 Wdrożenie tego certyfikatu jest objęte następującymi procedurami:  

-   Utworzyć i wydać niestandardowy szablon certyfikatu uwierzytelniania stacji roboczej w urzędzie certyfikacji  

-   Żądanie niestandardowego certyfikatu uwierzytelniania stacji roboczej  

-   Wyeksportuj certyfikat klienta dla punktów dystrybucji  

###  <a name="BKMK_clientdistributionpoint02008"></a>Utworzyć i wydać niestandardowy szablon certyfikatu uwierzytelniania stacji roboczej w urzędzie certyfikacji  
 Ta procedura powoduje utworzenie niestandardowego szablonu certyfikatu dla punktów dystrybucji programu System Center Configuration Manager, aby klucz prywatny można eksportować i dodanie szablonu certyfikatu do urzędu certyfikacji.  

> [!NOTE]  
>  Ta procedura wykorzystuje inny szablon certyfikatu z utworzonego szablonu certyfikatu dla komputerów klienckich. Mimo że oba certyfikaty wymagają możliwości uwierzytelniania klienta, certyfikat dla punktów dystrybucji wymaga wyeksportowania klucza prywatnego. Zabezpieczeń najlepszym rozwiązaniem, czy nie Konfigurowanie szablonów certyfikatów, więc klucz prywatny można eksportować, chyba że taka konfiguracja jest wymagana. Punkt dystrybucji wymaga tej konfiguracji, ponieważ należy zaimportować certyfikat jako plik zamiast wybierz go z magazynu certyfikatów.  
>   
>  Podczas tworzenia nowego szablonu certyfikatu dla tego certyfikatu, można ograniczyć komputerów, które może zażądać certyfikatu, którego klucz prywatny można eksportować. W naszym przykładowym wdrożeniu będzie to grupy zabezpieczeń utworzonej wcześniej dla serwerów systemu lokacji programu System Center Configuration Manager z usługami IIS. W używanej sieci, która dystrybuuje role systemu lokacji usług IIS, należy rozważyć utworzenie nowej grupy zabezpieczeń dla serwerów, na których działają punkty dystrybucji, aby można było ograniczyć certyfikaty tylko do tych serwerów systemu lokacji. Można także rozważyć wprowadzenie następujących modyfikacji certyfikatu:  
>   
>  -   Wymaganie zatwierdzenia instalacji certyfikatu w celu zapewnienia dodatkowych zabezpieczeń.  
> -   Wydłużenie okresu ważności certyfikatu. Ponieważ należy wyeksportować i zaimportować certyfikat każdorazowo przed jego wygaśnięciem, zwiększenia okresu ważności zmniejsza częstotliwość należy powtórzyć całą procedurę. Jednak wzrost okresu ważności również zmniejszenie bezpieczeństwa certyfikatu, ponieważ zawiera więcej czasu osobie atakującej do odszyfrowania klucza prywatnego i kradzież certyfikatu.  
> -   Użycie niestandardowej wartości w polu Podmiot certyfikatu lub nazwy alternatywnej podmiotu (SAN), aby ułatwić odróżnienie tego certyfikatu od standardowych certyfikatów klientów. Może to być szczególnie przydatne, jeżeli ten sam certyfikat jest używany dla kilku punktów dystrybucji.  

##### <a name="to-create-and-issue-the-custom-workstation-authentication-certificate-template-on-the-certification-authority"></a>Aby utworzyć i wydać niestandardowy szablon certyfikatu uwierzytelniania stacji roboczej w urzędzie certyfikacji  

1.  Na serwerze członkowskim, na którym uruchomiona jest Konsola urzędu certyfikacji, kliknij prawym przyciskiem myszy **szablonów certyfikatów**, a następnie wybierz pozycję **Zarządzaj** aby załadować Konsolę zarządzania szablony certyfikatów.  

2.  W okienku wyników kliknij prawym przyciskiem myszy wpis **Uwierzytelnianie stacji roboczej** w **Nazwa wyświetlana szablonu** kolumny, a następnie wybierz pozycję **Duplikuj szablon**.  

3.  W **Duplikuj szablon** okna dialogowego Sprawdź, czy **systemu Windows Server 2003, Enterprise Edition** jest zaznaczone, a następnie wybierz pozycję **OK**.  

    > [!IMPORTANT]  
    >  Nie wybieraj systemu **Windows 2008 Server, Enterprise Edition**.  

4.  W **właściwości nowego szablonu** na okna dialogowego **ogólne** wprowadź nazwę szablonu, takie jak **certyfikat punktu dystrybucji klienta programu ConfigMgr**, aby wygenerować certyfikat uwierzytelniania klienta dla punktów dystrybucji.  

5.  Wybierz **obsługiwanie żądań** karcie, a następnie wybierz pozycję **Zezwalaj na eksportowanie klucza prywatnego**.  

6.  Wybierz **zabezpieczeń** karcie, a następnie usuń **Zarejestruj** zgody **Administratorzy przedsiębiorstwa** grupy zabezpieczeń.  

7.  Wybierz **Dodaj**, wprowadź **serwery IIS programu ConfigMgr** w tekście polu, a następnie wybierz pozycję **OK**.  

8.  Wybierz dla tej grupy uprawnienie **Rejestracja** i nie usuwaj zaznaczenia uprawnienia **Odczyt** .  

9. Wybierz **OK**, a następnie Zamknij **konsolę Szablony certyfikatów**.  

10. W konsoli Urząd certyfikacji kliknij prawym przyciskiem myszy **szablonów certyfikatów**, wybierz **nowy**, a następnie wybierz pozycję **szablon certyfikatu do wystawienia**.  

11. W **Włączanie szablonu certyfikatu** okno dialogowe Nowy szablon, który właśnie utworzony, wybierz pozycję **certyfikat punktu dystrybucji klienta programu ConfigMgr**, a następnie wybierz pozycję **OK**.  

12. Jeśli nie masz do tworzenia i wystawiania certyfikatów więcej, Zamknij **urzędu certyfikacji**.  

###  <a name="BKMK_clientdistributionpoint12008"></a>Żądanie niestandardowego certyfikatu uwierzytelniania stacji roboczej  
 Ta procedura żądań, a następnie instalację niestandardowego certyfikatu klienta na serwerze członkowskim, na którym działają usługi IIS i który zostanie skonfigurowany jako punkt dystrybucji.  

##### <a name="to-request-the-custom-workstation-authentication-certificate"></a>Aby zażądać niestandardowego certyfikatu uwierzytelniania stacji roboczej  

1.  Wybierz **Start**, wybierz **Uruchom**, a następnie wprowadź **mmc.exe.** W pustej konsoli wybierz **pliku**, a następnie wybierz pozycję **Dodaj/Usuń przystawkę**.  

2.  W **Dodawanie lub usuwanie przystawek** oknie dialogowym wybierz **certyfikaty** z listy **dostępne przystawki**, a następnie wybierz pozycję **Dodaj**.  

3.  W **certyfikatów przystawki** okno dialogowe Wybierz **konto komputera**, a następnie wybierz pozycję **dalej**.  

4.  W **Wybieranie komputera** okna dialogowego Sprawdź, czy **komputer lokalny: (komputer ten jest uruchomiona konsola)** jest zaznaczone, a następnie wybierz pozycję **Zakończ**.  

5.  W **Dodawanie lub usuwanie przystawek** oknie dialogowym wybierz **OK**.  

6.  W konsoli rozwiń węzeł **certyfikaty (komputer lokalny)**, a następnie wybierz pozycję **osobistych**.  

7.  Kliknij prawym przyciskiem myszy **certyfikaty**, wybierz **wszystkie zadania**, a następnie wybierz pozycję **Żądaj nowego certyfikatu**.  

8.  Na **przed rozpoczęciem** wybierz pozycję **dalej**.  

9. Jeśli widzisz **wybierz zasady rejestracji certyfikatu** wybierz pozycję **dalej**.  

10. Na **żądania certyfikatów** wybierz pozycję **certyfikat punktu dystrybucji klienta programu ConfigMgr** z listy dostępnych certyfikatów, a następnie wybierz pozycję **Zarejestruj**.  

11. Na **wyniki instalacji certyfikatów** strony, poczekaj, aż certyfikat został zainstalowany, a następnie wybierz **Zakończ**.  

12. W okienku wyników sprawdź, czy certyfikat ma **uwierzytelnianie klienta** w **zamierzony cel** kolumny i że **certyfikat punktu dystrybucji klienta programu ConfigMgr** w **szablonu certyfikatu** kolumny.  

13. Nie zamykaj konsoli **Certyfikaty (komputer lokalny)**.  

###  <a name="BKMK_exportclientdistributionpoint22008"></a>Wyeksportuj certyfikat klienta dla punktów dystrybucji  
 Ta procedura eksportuje niestandardowego certyfikatu uwierzytelniania stacji roboczej do pliku, aby można było importować we właściwościach punktu dystrybucji.  

##### <a name="to-export-the-client-certificate-for-distribution-points"></a>Aby wyeksportować certyfikat klienta dla punktów dystrybucji  

1.  W **certyfikaty (komputer lokalny)** konsoli, kliknij prawym przyciskiem myszy certyfikat, który został właśnie zainstalowany, wybierz **wszystkie zadania**, a następnie wybierz pozycję **wyeksportować**.  

2.  W Kreatorze eksportu certyfikatów wybierz **dalej**.  

3.  Na **eksportowanie klucza prywatnego** wybierz pozycję **tak, Eksportuj klucz prywatny**, a następnie wybierz pozycję **dalej**.  

    > [!NOTE]  
    >  Jeżeli ta opcja nie jest dostępna, certyfikat został utworzony bez opcji eksportu klucza prywatnego. W tym scenariuszu nie można wyeksportować certyfikatu w wymaganym formacie. Należy skonfigurować szablon certyfikatu, aby klucz prywatny można eksportować i zażądać certyfikatu ponownie.  

4.  Na **Format pliku eksportu** strony, upewnij się, że **wymiana informacji osobistych — PKCS #12 (. PFX)** opcja jest zaznaczona.  

5.  Na **hasło** Określ silne hasło, aby zabezpieczyć wyeksportowany certyfikat kluczem prywatnym, a następnie wybierz pozycję **dalej**.  

6.  Na **Eksport pliku** strony, określ nazwę pliku, który chcesz wyeksportować, a następnie wybierz pozycję **dalej**.  

7.  Aby zamknąć kreatora, należy wybrać **Zakończ** na **Kreatora eksportu certyfikatów** stronie, a następnie wybierz **OK** w oknie dialogowym potwierdzenia.  

8.  Zamknij konsolę **Certyfikaty (komputer lokalny)**.  

9. Zapisz plik w bezpiecznym miejscu i upewnij się, że można do niego dostęp z konsoli programu System Center Configuration Manager.  

 Certyfikat jest teraz gotowy do zaimportowania podczas konfigurowania punktu dystrybucji.  

> [!TIP]  
>  Można użyć tego samego pliku certyfikatu, konfigurując obrazy nośników do wdrożenia systemu operacyjnego, które nie są używane w środowisku PXE i sekwencji zadań umożliwia zainstalowanie obrazu musisz skontaktować się z punktem zarządzania, który wymaga połączeń klienckich HTTPS.  

##  <a name="BKMK_mobiledevices2008_cm2012"></a>Wdrażanie certyfikatu rejestracji dla urządzeń przenośnych  
 W tym wdrożeniu certyfikatu zarówno utworzenie, jak i wystawienie szablonu certyfikatu rejestracji w urzędzie certyfikacji jest objęte tą samą procedurą.  

### <a name="create-and-issue-the-enrollment-certificate-template-on-the-certification-authority"></a>Utworzyć i wydać szablon certyfikatu rejestracji w urzędzie certyfikacji  
 Ta procedura powoduje utworzenie szablonu certyfikatu rejestracji dla urządzeń przenośnych w programie System Center Configuration Manager i dodaje go do urzędu certyfikacji.  

##### <a name="to-create-and-issue-the-enrollment-certificate-template-on-the-certification-authority"></a>Aby utworzyć i wystawić szablon certyfikatu rejestracji w urzędzie certyfikacji  

1.  Utwórz grupę zabezpieczeń, która zawiera użytkowników, którzy będą rejestrować urządzenia przenośne w programie System Center Configuration Manager.  

2.  Na serwerze członkowskim z usługami certyfikatów zainstalowane, w konsoli Urząd certyfikacji kliknij prawym przyciskiem myszy **szablonów certyfikatów**, a następnie wybierz pozycję **Zarządzaj** aby załadować Konsolę zarządzania szablony certyfikatów.  

3.  W okienku wyników kliknij prawym przyciskiem myszy wpis **sesja uwierzytelniona** w **Nazwa wyświetlana szablonu** kolumny, a następnie wybierz pozycję **Duplikuj szablon**.  

4.  W **Duplikuj szablon** okna dialogowego Sprawdź, czy **systemu Windows Server 2003, Enterprise Edition** jest zaznaczone, a następnie wybierz pozycję **OK**.  

    > [!IMPORTANT]  
    >  Nie wybieraj systemu **Windows 2008 Server, Enterprise Edition**.  

5.  W **właściwości nowego szablonu** na okna dialogowego **ogólne** wprowadź nazwę szablonu, takie jak **certyfikat rejestracji urządzeń przenośnych programu ConfigMgr**, w celu wygenerowania certyfikatów rejestracji dla urządzeń przenośnych, które mają być zarządzane przez program System Center Configuration Manager.  

6.  Wybierz **nazwa podmiotu** karcie, upewnij się, że **Konstruuj z tej informacji usługi Active Directory** jest wybrany, wybierz pozycję **nazwa pospolita** dla **format nazwy podmiotu:**, a następnie wyczyść **główna nazwa użytkownika (UPN)** z **Dołącz tę informację do alternatywnej nazwy podmiotu**.  

7.  Wybierz **zabezpieczeń** karcie, wybierz grupę zabezpieczeń, która zawiera użytkowników z urządzeniami przenośnymi do zarejestrowania i wybierz uprawnienie dodatkowe **Zarejestruj**. Nie usuwaj zaznaczenia opcji **Odczyt**.  

8.  Wybierz **OK**, a następnie Zamknij **konsolę Szablony certyfikatów**.  

9. W konsoli Urząd certyfikacji kliknij prawym przyciskiem myszy **szablonów certyfikatów**, wybierz **nowy**, a następnie wybierz pozycję **szablon certyfikatu do wystawienia**.  

10. W **Włączanie szablonu certyfikatu** okno dialogowe Nowy szablon, który właśnie utworzony, wybierz pozycję **certyfikat rejestracji urządzeń przenośnych programu ConfigMgr**, a następnie wybierz pozycję **OK**.  

11. Jeśli nie ma potrzeby tworzenia i wystawiania certyfikatów więcej, zamknij konsolę Urząd certyfikacji.  

 Szablon certyfikatu rejestracji urządzeń przenośnych jest teraz gotowy do wybrania podczas konfigurowania profilu rejestracji urządzenia przenośnego w ustawieniach klienta.  

##  <a name="BKMK_AMT2008_cm2012"></a>Wdrażanie certyfikatów dla AMT  
 Wdrożenie tego certyfikatu jest objęte następującymi procedurami:  

-   Tworzenia, wystawiania i instalowanie certyfikatu udostępniania AMT  

-   Utworzyć i wystawić certyfikat serwera sieci web dla komputerów opartych na technologii AMT  

-   Utworzyć i wydać certyfikaty uwierzytelniania 802.1 X AMT, na komputerach klienta  

###  <a name="BKMK_AMTprovisioning2008"></a>Tworzenia, wystawiania i instalowanie certyfikatu udostępniania AMT  
 Z wewnętrznego urzędu certyfikacji należy utworzyć certyfikat udostępniania, gdy komputery oparte na technologii AMT są skonfigurowane z odcisk palca certyfikatu z wewnętrznego głównego urzędu certyfikacji. Jeśli nie jest to i musi użyć zewnętrznego urzędu certyfikacji, postępuj zgodnie z instrukcjami firmy, który wystawił certyfikat udostępniania AMT, który często pociąga za sobą żądanie certyfikatu za pośrednictwem publicznej witryny sieci web firmy. Można także znaleźć szczegółowe instrukcje dotyczące wybranego zewnętrznego urzędu certyfikacji na [Intel vPro Expert Center: Witrynie sieci web firmy Microsoft vPro możliwości zarządzania](http://go.microsoft.com/fwlink/?LinkId=132001).  

> [!IMPORTANT]  
>  Zewnętrzne urzędy certyfikacji mogą nie obsługiwać identyfikatora obiektu udostępniania Intel AMT. W takim przypadku należy podać **Intel(R) Client Setup Certificate** atrybut jednostki Organizacyjnej.  

 W przypadku żądania certyfikatu udostępniania AMT od zewnętrznego urzędu certyfikacji, należy zainstalować certyfikat w magazynie certyfikatów osobistych komputera na serwerze członkowskim, który będzie hostem punktu Usługi poza pasmem.  

##### <a name="to-request-and-issue-the-amt-provisioning-certificate"></a>Aby zażądać certyfikatu udostępniania AMT i go wystawić  

1.  Utwórz grupę zabezpieczeń, która ma kont komputerów serwerów systemu lokacji, które będą uruchamiane punktu Usługi poza pasmem.  

2.  Na serwerze członkowskim z usługami certyfikatów zainstalowane, w konsoli Urząd certyfikacji kliknij prawym przyciskiem myszy **szablonów certyfikatów**, a następnie wybierz pozycję **Zarządzaj** załadować **szablonów certyfikatów** konsoli.  

3.  W okienku wyników kliknij prawym przyciskiem myszy wpis **serwera sieci Web** w **Nazwa wyświetlana szablonu** kolumny, a następnie wybierz pozycję **Duplikuj szablon**.  

4.  W **Duplikuj szablon** okna dialogowego Sprawdź, czy **systemu Windows Server 2003, Enterprise Edition** jest zaznaczone, a następnie wybierz pozycję **OK**.  

    > [!IMPORTANT]  
    >  Nie wybieraj systemu **Windows 2008 Server, Enterprise Edition**.  

5.  W **właściwości nowego szablonu** na okna dialogowego **ogólne** wprowadź nazwę szablonu, takie jak **udostępniania AMT programu ConfigMgr**, dla szablonu certyfikatu udostępniania AMT.  

6.  Wybierz **nazwa podmiotu** , wybierz pozycję **Konstruuj z tej informacji usługi Active Directory**, a następnie wybierz pozycję **nazwa pospolita**.  

7.  Wybierz **rozszerzenia** karcie, upewnij się, że **zasady aplikacji** jest zaznaczone, a następnie wybierz pozycję **Edytuj**.  

8.  W **Edytowanie rozszerzenia zasad aplikacji** oknie dialogowym wybierz **Dodaj**.  

9. W **Dodawanie zasady aplikacji** oknie dialogowym wybierz **nowy**.  

10. W **Nowa zasada aplikacji** okna dialogowego wprowadź **udostępniania AMT** w **nazwa** , a następnie wprowadź następujący ciąg liczb w **identyfikator obiektu**: **2.16.840.1.113741.1.2.3**.  

11. Wybierz **OK**, a następnie wybierz pozycję **OK** w **Dodawanie zasady aplikacji** okno dialogowe.  

12. Wybierz **OK** w **Edytowanie rozszerzenia zasad aplikacji** okno dialogowe.  

13. W **właściwości nowego szablonu** następujące okno dialogowe, jest wymienione jako **zasady aplikacji** opis: **Uwierzytelnianie serwera** i **udostępniania AMT**.  

14. Wybierz **zabezpieczeń** karcie, a następnie usuń **Zarejestruj** zgody **Administratorzy domeny** i **Administratorzy przedsiębiorstwa** grup zabezpieczeń.  

15. Wybierz **Dodaj**, wprowadź nazwę grupy zabezpieczeń zawierającej konto komputera dla roli systemu lokacji punktu Usługi poza pasmem, a następnie wybierz pozycję **OK**.  

16. Wybierz **Zarejestruj** dla tej grupy uprawnienie i nie usuwaj **odczytu** uprawnienia...  

17. Wybierz **OK**, a następnie Zamknij **szablonów certyfikatów** konsoli.  

18. W **urzędu certyfikacji**, kliknij prawym przyciskiem myszy **szablonów certyfikatów**, wybierz **nowy**, a następnie wybierz pozycję **szablon certyfikatu do wystawienia**.  

19. W **Włączanie szablonu certyfikatu** okno dialogowe Nowy szablon, który właśnie utworzony, wybierz pozycję **udostępniania AMT programu ConfigMgr**, a następnie wybierz pozycję **OK**.  

    > [!NOTE]  
    >  Jeśli nie możesz ukończyć kroku 18 lub 19, sprawdź, czy na pewno korzystasz z systemu Windows Server 2008 w wersji Enterprise Edition. Mimo że można skonfigurować szablony z systemu Windows Server Standard Edition i usług certyfikatów, nie można wdrażać certyfikatów przy użyciu zmodyfikowanych szablonów certyfikatów, chyba że używasz Enterprise Edition systemu Windows Server 2008.  

20. Nie zamykaj konsoli **Urząd certyfikacji**.  

 Certyfikat udostępniania AMT z wewnętrznego urzędu certyfikacji jest teraz gotowe do zainstalowania na komputerze punktu Usługi poza pasmem.  

##### <a name="to-install-the-amt-provisioning-certificate"></a>Aby zainstalować certyfikat udostępniania AMT  

1.  Uruchom ponownie serwer członkowski z uruchomionymi usługami IIS, aby upewnić się, że można uzyskać dostęp do szablonu certyfikatu dzięki skonfigurowanemu uprawnieniu.  

2.  Wybierz **Start**, wybierz **Uruchom**, a następnie wprowadź **mmc.exe.** W pustej konsoli wybierz **pliku**, a następnie wybierz pozycję **Dodaj/Usuń przystawkę**.  

3.  W **Dodawanie lub usuwanie przystawek** oknie dialogowym wybierz **certyfikaty** z listy **dostępne przystawki**, a następnie wybierz pozycję **Dodaj**.  

4.  W **certyfikatów przystawki** okno dialogowe Wybierz **konto komputera**, a następnie wybierz pozycję **dalej**.  

5.  W **Wybieranie komputera** okna dialogowego Sprawdź, czy **komputer lokalny: (komputer ten jest uruchomiona konsola)** jest zaznaczone, a następnie wybierz pozycję **Zakończ**.  

6.  W **Dodawanie lub usuwanie przystawek** oknie dialogowym wybierz **OK**.  

7.  W konsoli rozwiń węzeł **certyfikaty (komputer lokalny)**, a następnie wybierz pozycję **osobistych**.  

8.  Kliknij prawym przyciskiem myszy **certyfikaty**, wybierz **wszystkie zadania**, a następnie wybierz pozycję **Żądaj nowego certyfikatu**.  

9. Na **przed rozpoczęciem** wybierz pozycję **dalej**.  

10. Jeśli widzisz **wybierz zasady rejestracji certyfikatu** wybierz pozycję **dalej**.  

11. Na **żądania certyfikatów** wybierz pozycję **udostępniania AMT** z listy dostępnych certyfikatów, a następnie wybierz pozycję **Zarejestruj**.  

12. Na **wyniki instalacji certyfikatów** strony, poczekaj, aż certyfikat został zainstalowany, a następnie wybierz **Zakończ**.  

13. Zamknij konsolę **Certyfikaty (komputer lokalny)**.  

 Certyfikat udostępniania AMT z wewnętrznego urzędu certyfikacji jest teraz zainstalowany i jest gotowy do wybrania we właściwościach punktu obsługi poza pasmem.  

### <a name="create-and-issue-the-web-server-certificate-for-amt-based-computers"></a>Utworzyć i wystawić certyfikat serwera sieci web dla komputerów opartych na technologii AMT  
 Użyj poniższej procedury, aby przygotować certyfikaty serwera sieci Web dla komputerów opartych na technologii AMT.  

##### <a name="to-create-and-issue-the-web-server-certificate-template"></a>Aby utworzyć i wystawić szablon certyfikatu serwera sieci web  

1.  Utwórz grupy zabezpieczeń pusta, która zawiera konta komputerów AMT tworzone podczas udostępniania AMT System Center Configuration Manager.  

2.  Na serwerze członkowskim z usługami certyfikatów zainstalowane, w konsoli Urząd certyfikacji kliknij prawym przyciskiem myszy **szablonów certyfikatów**, a następnie wybierz pozycję **Zarządzaj** załadować **szablonów certyfikatów** konsoli.  

3.  W okienku wyników kliknij prawym przyciskiem myszy wpis **serwera sieci Web** w **Nazwa wyświetlana szablonu** kolumny, a następnie wybierz pozycję **Duplikuj szablon**.  

4.  W **Duplikuj szablon** okna dialogowego Sprawdź, czy **systemu Windows Server 2003, Enterprise Edition** jest zaznaczone, a następnie wybierz pozycję **OK**.  

    > [!IMPORTANT]  
    >  Nie wybieraj systemu **Windows 2008 Server, Enterprise Edition.**  

5.  W **właściwości nowego szablonu** na okna dialogowego **ogólne** wprowadź nazwę szablonu, takie jak **certyfikat serwera sieci Web AMT programu ConfigMgr**, w celu wygenerowania certyfikatów sieci web, które będą używane do zarządzania poza pasmem na komputerach AMT.  

6.  Wybierz **nazwa podmiotu** , wybierz pozycję **Konstruuj z tej informacji usługi Active Directory**, wybierz **nazwa pospolita** dla **format nazwy podmiotu**, a następnie wyczyść **główna nazwa użytkownika (UPN)** dla ustawienia alternatywnej nazwy podmiotu.  

7.  Wybierz **zabezpieczeń** karcie, a następnie usuń **Zarejestruj** zgody **Administratorzy domeny** i **Administratorzy przedsiębiorstwa** grup zabezpieczeń.  

8.  Wybierz **Dodaj**i wprowadź nazwę grupy zabezpieczeń utworzonej dla udostępniania AMT, a następnie wybierz **OK**.  

9. Wybierz następujące **Zezwalaj** uprawnienia dla tej grupy zabezpieczeń: **Odczyt** i **zarejestrować**.  

10. Wybierz **OK**, a następnie Zamknij **szablonów certyfikatów** konsoli.  

11. W **urzędu certyfikacji** konsoli, kliknij prawym przyciskiem myszy **szablonów certyfikatów**, wybierz **nowy**, a następnie wybierz pozycję **szablon certyfikatu do wystawienia**.  

12. W **Włączanie szablonu certyfikatu** okno dialogowe Nowy szablon, który właśnie utworzony, wybierz pozycję **certyfikat serwera sieci Web AMT programu ConfigMgr**, a następnie wybierz pozycję **OK**.  

13. Jeśli nie masz do tworzenia i wystawiania certyfikatów więcej, Zamknij **urzędu certyfikacji**.  

 Szablon serwera sieci Web AMT jest teraz gotowy do konfigurowania komputerów opartych na technologii AMT certyfikatów serwera sieci web. Wybierz ten szablon certyfikatu we właściwościach składnika zarządzania poza pasmem.  

### <a name="create-and-issue-the-client-authentication-certificates-for-8021x-amt-based-computers"></a>Utworzyć i wydać certyfikaty uwierzytelniania 802.1 X AMT, na komputerach klienta  
 Użyj poniższej procedury, jeśli komputery oparte na technologii AMT będą używać certyfikatów klienta dla uwierzytelnianych sieci przewodowych i bezprzewodowych 802.1X.  

##### <a name="to-create-and-issue-the-client-authentication-certificate-template-on-the-ca"></a>Aby utworzyć i wydać szablon certyfikatu uwierzytelniania klienta w urzędzie certyfikacji  

1.  Na serwerze członkowskim z usługami certyfikatów zainstalowane, w konsoli Urząd certyfikacji kliknij prawym przyciskiem myszy **szablonów certyfikatów**, a następnie wybierz pozycję **Zarządzaj** załadować **szablonów certyfikatów** konsoli.  

2.  W okienku wyników kliknij prawym przyciskiem myszy wpis **Uwierzytelnianie stacji roboczej** w **Nazwa wyświetlana szablonu** kolumny, a następnie wybierz pozycję **Duplikuj szablon**.  

    > [!IMPORTANT]  
    >  Nie wybieraj systemu **Windows 2008 Server, Enterprise Edition.**  

3.  W **właściwości nowego szablonu** na okna dialogowego **ogólne** wprowadź nazwę szablonu, takie jak **certyfikat uwierzytelniania klienta programu ConfigMgr AMT 802.1 X**, w celu wygenerowania certyfikatów klienta, które będzie służyć do zarządzania poza pasmem na komputerach AMT.  

4.  Wybierz **nazwa podmiotu** , wybierz pozycję **Konstruuj z tej informacji usługi Active Directory**, a następnie wybierz pozycję **nazwa pospolita** dla **format nazwy podmiotu**. Wyczyść **nazwy DNS** dla alternatywnej podmiotu nazwy, a następnie wybierz pozycję **główna nazwa użytkownika (UPN)**.  

5.  Wybierz **zabezpieczeń** karcie, a następnie usuń **Zarejestruj** zgody **Administratorzy domeny** i **Administratorzy przedsiębiorstwa** grup zabezpieczeń.  

6.  Wybierz **Dodaj**, wprowadź nazwę grupy zabezpieczeń, który będzie określić we właściwościach składnika zarządzania poza pasmem, aby obejmować konta komputerów opartych na technologii AMT, a następnie wybierz **OK**.  

7.  Wykonaj następujące czynności **Zezwalaj** uprawnienia dla tej grupy zabezpieczeń: **Odczyt** i **zarejestrować**.  

8.  Wybierz **OK**, a następnie Zamknij **szablonów certyfikatów** konsoli zarządzania **certtmpl - [szablony certyfikatów]**.  

9. W **urzędu certyfikacji** konsoli zarządzania kliknij prawym przyciskiem myszy **szablonów certyfikatów**, wybierz **nowy**, a następnie wybierz pozycję **szablon certyfikatu do wystawienia**.  

10. W **Włączanie szablonu certyfikatu** okno dialogowe Nowy szablon, który właśnie utworzony, wybierz pozycję **certyfikat uwierzytelniania klienta programu ConfigMgr AMT 802.1 X**, a następnie wybierz pozycję **OK**.  

11. Jeśli nie ma potrzeby tworzenia i wystawiania certyfikatów więcej, Zamknij **urzędu certyfikacji**.  

 Szablon certyfikatu uwierzytelniania klienta jest teraz gotowy do wystawiania komputerom opartym na technologii AMT certyfikatów, których można będzie użyć do uwierzytelniania klientów 802.1X. Wybierz ten szablon certyfikatu we właściwościach składnika zarządzania poza pasmem.  

##  <a name="BKMK_MacClient_SP1"></a>Wdrażanie certyfikatu klienta dla komputerów Mac  

W tym wdrożeniu certyfikatu zarówno utworzenie, jak i wystawienie szablonu certyfikatu rejestracji w urzędzie certyfikacji jest objęte tą samą procedurą.  

###  <a name="BKMK_MacClient_CreatingIssuing"></a>Utworzyć i wydać szablon certyfikatu w urzędzie certyfikacji klienta na komputery Mac  
 Ta procedura powoduje utworzenie niestandardowego szablonu certyfikatu dla komputerów Mac programu System Center Configuration Manager i dodanie szablonu certyfikatu do urzędu certyfikacji.  

> [!NOTE]  
>  Ta procedura korzysta z innego szablonu certyfikatu niż szablony certyfikatów, które być może utworzono wcześniej dla klientów z systemem Windows lub dla punktów dystrybucji.  
>   
>  Podczas tworzenia nowego szablonu certyfikatu dla tego certyfikatu, można ograniczyć żądanie certyfikatu do autoryzowanych użytkowników.  

##### <a name="to-create-and-issue-the-mac-client-certificate-template-on-the-certification-authority"></a>Aby utworzyć i wydać szablon certyfikatu klienta Mac w urzędzie certyfikacji  

1.  Utwórz grupę zabezpieczeń, która zawiera konta użytkowników dla użytkowników administracyjnych, którzy będą rejestrowali ten certyfikat na komputerze Mac za pomocą programu System Center Configuration Manager.  

2.  Na serwerze członkowskim, na którym uruchomiona jest Konsola urzędu certyfikacji, kliknij prawym przyciskiem myszy **szablonów certyfikatów**, a następnie wybierz pozycję **Zarządzaj** aby załadować Konsolę zarządzania szablony certyfikatów.  

3.  W okienku wyników kliknij prawym przyciskiem myszy wpis opisany **sesja uwierzytelniona** w **Nazwa wyświetlana szablonu** kolumny, a następnie wybierz pozycję **Duplikuj szablon**.  

4.  W **Duplikuj szablon** okna dialogowego Sprawdź, czy **systemu Windows Server 2003, Enterprise Edition** jest zaznaczone, a następnie wybierz pozycję **OK**.  

    > [!IMPORTANT]  
    >  Nie wybieraj systemu **Windows 2008 Server, Enterprise Edition**.  

5.  W **właściwości nowego szablonu** na okna dialogowego **ogólne** wprowadź nazwę szablonu, takie jak **certyfikat klienta Mac ConfigMgr**, aby wygenerować certyfikat klienta Mac.  

6.  Wybierz **nazwa podmiotu** karcie, upewnij się, że **Konstruuj z tej informacji usługi Active Directory** jest wybrana, wybierz **nazwa pospolita** dla **format nazwy podmiotu:**, a następnie wyczyść **główna nazwa użytkownika (UPN)** z **Dołącz tę informację do alternatywnej nazwy podmiotu**.  

7.  Wybierz **zabezpieczeń** karcie, a następnie usuń **Zarejestruj** zgody **Administratorzy domeny** i **Administratorzy przedsiębiorstwa** grup zabezpieczeń.  

8.  Wybierz **Dodaj**, określ grupę zabezpieczeń utworzoną w pierwszym kroku, a następnie wybierz pozycję **OK**.  

9. Wybierz **Zarejestruj** dla tej grupy uprawnienie i nie usuwaj **odczytu** uprawnienia.  

10. Wybierz **OK**, a następnie Zamknij **konsolę Szablony certyfikatów**.  

11. W konsoli Urząd certyfikacji kliknij prawym przyciskiem myszy **szablonów certyfikatów**, wybierz **nowy**, a następnie wybierz pozycję **szablon certyfikatu do wystawienia**.  

12. W **Włączanie szablonu certyfikatu** okno dialogowe Nowy szablon, który właśnie utworzony, wybierz pozycję **certyfikat klienta Mac ConfigMgr**, a następnie wybierz pozycję **OK**.  

13. Jeśli nie masz do tworzenia i wystawiania certyfikatów więcej, Zamknij **urzędu certyfikacji**.  

 Szablon certyfikatu klienta Mac jest teraz gotowy do wybrania podczas konfigurowania ustawień klienta do rejestracji.
