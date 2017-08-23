---
title: Ustawienia klienta | Dokumentacja firmy Microsoft
description: "Wybierz ustawienia klienta przy użyciu konsoli administracyjnej programu System Center Configuration Manager."
ms.custom: na
ms.date: 08/01/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f7560876-8084-4570-aeab-7fd44f4ba737
caps.latest.revision: "15"
caps.handback.revision: "0"
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.openlocfilehash: a8233c361e1a78b14a02f328da445814624e38d8
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="about-client-settings-in-system-center-configuration-manager"></a>Informacje o ustawieniach klienta w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (wersji current branch)*

Wszystkimi ustawieniami klienta w programie System Center Configuration Manager są zarządzane w konsoli programu Configuration Manager z **ustawień klienta** w węźle **administracji** obszaru roboczego. Menedżer konfiguracji jest dostarczany z zestawem ustawień domyślnych. Zmiana domyślnych ustawień klienta, te ustawienia są stosowane do wszystkich klientów w hierarchii. Można również konfigurować niestandardowe ustawienia klienta, które zastąpią domyślne ustawienia klienta po ich przypisaniu do kolekcji. Aby uzyskać informacje na temat konfigurowania ustawień klienta, zobacz [Jak skonfigurować ustawienia klienta w programie System Center Configuration Manager](../../../core/clients/deploy/configure-client-settings.md).  

Wiele ustawień klienta nie wymaga wyjaśnień. Inne są opisane w tym miejscu.  

## <a name="background-intelligent-transfer-service"></a>Usługa inteligentnego transferu w tle  

-   **Ogranicz maksymalną przepustowość sieci dla transferów w tle wykonywanych przez usługę BITS**  

   Gdy ta opcja jest **True** lub **tak**, klienci będą korzystać z funkcji ograniczania przepustowości usługi BITS.  

-   **Godzina rozpoczęcia okna ograniczenia przepustowości**  

   Określ czas rozpoczęcia lokalnego oknie ograniczenia przepustowości usługi BITS.  

-   **Godzina zakończenia okna ograniczenia przepustowości**  

   Określ czas zakończenia lokalnego oknie ograniczenia przepustowości usługi BITS. Jeśli równa **godzina rozpoczęcia okna ograniczenia przepustowości**, ograniczenia przepustowości usługi BITS jest zawsze włączona.  

-   **Maksymalna szybkość transferu w oknie ograniczenia przepustowości (Kb/s)**  

   Określ maksymalną szybkość transmisji używanego przez klientów podczas okna.  

-   **Zezwalaj na pobieranie usługi BITS poza oknem ograniczenia przepustowości**  

   Wybierz tę opcję, aby umożliwić klientom programu Configuration Manager używać oddzielnych ustawień usługi BITS poza określonym oknem.  

-   **Maksymalna szybkość transferu poza oknem ograniczenia przepustowości (Kb/s)**  

   Określ maksymalną szybkość transmisji używanego przez klientów poza przepustowości okna, gdy wybrano ograniczenia przepustowości poza oknem usługi BITS usługi BITS.  

## <a name="client-cache-settings"></a>Ustawienia pamięci podręcznej klienta

- **Konfiguruj usługę BranchCache**

  Począwszy od wersji 1606, użyj tego ustawienia, aby skonfigurować komputer kliencki [usługi BranchCache](/sccm/core/plan-design/configs/support-for-windows-features-and-networks#branchcache). Aby zezwolić na buforowanie usługi BranchCache na kliencie, **Włącz usługę BranchCache** do **tak**.

- **Włącz usługę BranchCache**

Włącza funkcję BranchCache na komputerach klienckich.

- **Maksymalny rozmiar pamięci podręcznej usługi BranchCache (część procentowa dysku)**.

- **Skonfiguruj rozmiar pamięci podręcznej klienta**

  Pamięci podręcznej klienta na komputerach z systemem Windows są przechowywane tymczasowe pliki służące do instalacji aplikacji i programów. Wybierz **tak** następnie określ:
    - **Maksymalny rozmiar pamięci podręcznej** (MB). 
    - **Maksymalny rozmiar pamięci podręcznej** (procent dysku).
Rozmiar pamięci podręcznej klienta można rozszerzyć do maksymalnego rozmiaru w Megabajtach lub wartość procentowa dysku, **ta wartość jest mniejsza**. Jeśli ta opcja jest **nr**, domyślny rozmiar to 5,120 MB.

- **Włącz klienta programu Configuration Manager w pełnej wersji systemu operacyjnego, aby udostępnić zawartość**

Umożliwia elementu równorzędnego pamięci podręcznej klientów programu Configuration Manager. Następnie należy określić informacje o portach za pomocą której klient komunikuje się z komputerem równorzędnym. Menedżer konfiguracji automatycznie skonfiguruje reguł zapory systemu Windows, aby zezwolić na ten ruch. Jeśli używasz innej zapory, należy ręcznie skonfigurować reguły zezwalające na ten ruch.




## <a name="client-policy"></a>Zasady klienta  

-   **Interwał sondowania zasad klienta (minuty)**  

   Określ częstotliwość pobierania zasad klienta przez następujących klientów programu Configuration Manager:  

  -   Komputery z systemem Windows (na przykład komputery stacjonarne, serwery, komputery przenośne)  

  -   Urządzenia przenośne, które rejestruje programu Configuration Manager  

  -   Komputery Mac  

  -   Komputery z systemem Linux lub UNIX  

-   **Włącz sondowanie zasad użytkownika na klientach**  

   Po ustawieniu tej opcji **True** lub **tak**, a Configuration Manager ma [odnalezione użytkownika](../../../core/servers/deploy/configure/about-discovery-methods.md#bkmk_aboutUser), klientów na komputerach będą otrzymywać aplikacje i programy przeznaczone dla zalogowanego użytkownika.  

   Ponieważ katalog aplikacji otrzymuje listę oprogramowania dostępnego dla użytkowników z serwera lokacji, to ustawienie nie ma być **True** lub **tak** dla użytkowników wyświetlić aplikacje i zażądać ich z katalogu aplikacji. Jeśli to ustawienie jest jednak **False** lub **nr**, następujące nie będzie działać, jeśli użytkownicy korzystają z katalogu aplikacji:  

  -   Użytkownicy nie mogą instalować aplikacji widocznych w wykazie aplikacji.  

  -   Użytkownicy nie będą widzieć powiadomień dotyczących ich żądań zatwierdzenia aplikacji. Zamiast tego muszą odświeżyć katalog aplikacji i sprawdzić stan zatwierdzenia.  

  -   Użytkownicy nie będą otrzymywać poprawek i aktualizacji aplikacji, które są opublikowane w katalogu aplikacji. Jednak zobaczą zmiany informacji o aplikacjach w katalogu aplikacji.  

  -   Jeśli użytkownik usunie wdrożenie aplikacji po zainstalowaniu przez klienta aplikacji z katalogu aplikacji, klienci będą sprawdzać przez maksymalnie dwa dni, czy aplikacja jest zainstalowana.  

   Ponadto, gdy to ustawienie jest **False** lub **nr**, użytkownicy nie będą otrzymywali wymaganych aplikacji wdrażanych dla użytkowników lub inne zadania zarządzania w zasadach użytkownika.  

   To ustawienie dotyczy użytkowników, gdy komputer będzie połączony z siecią intranet lub Internetem. Musi to być **True** lub **tak** Jeśli chcesz również włączyć zasady użytkownika w Internecie.  

-   **Włącz żądania dotyczące zasad użytkownika od klientów internetowych**  

   Jeśli klienta i lokację skonfigurowano do internetowego zarządzania i zostanie wybrana opcja jako **True** lub **tak** , a oba poniższe warunki są spełnione, użytkownicy będą otrzymywali zasady użytkownika, gdy komputer jest połączony z Internetem:  

  -   **Włącz sondowanie zasad użytkownika na klientach** jest ustawienie klienta **True**, lub **Włącz zasady użytkownika na klientach** jest **tak**.  

  -   Internetowy punkt zarządzania pomyślnie uwierzytelnił użytkownika za pomocą uwierzytelniania systemu Windows (Kerberos lub NTLM).  

   Jeśli opuścisz tę opcję **False** lub **nr**, lub jeden z warunków nie powiedzie się, komputer na Internet będzie otrzymywał wyłącznie zasady komputera. Przy takim scenariuszu użytkownicy mogą nadal oglądać i instalować aplikacje oraz zażądać ich z internetowego katalogu aplikacji. Jeśli to ustawienie jest **False** lub **nr** , ale **Włącz sondowanie zasad użytkownika na klientach** jest **True** lub **Włącz zasady użytkownika na klientach** jest **tak**, użytkownicy nie będą otrzymywali zasady użytkownika, dopóki komputer jest połączony z intranetem.  

   Aby uzyskać więcej informacji na temat zarządzania klientami przez Internet, zobacz [uwagi dotyczące komunikacji klientów z Internetu lub niezaufanego lasu](../../../core/plan-design/hierarchy/communications-between-endpoints.md#BKMK_clientspan) w [komunikacja między punktami końcowymi w programie System Center Configuration Manager](../../../core/plan-design/hierarchy/communications-between-endpoints.md).  

  > [!NOTE]  
  >  Żądania zatwierdzenia aplikacji od użytkowników nie wymagają zasad użytkownika ani uwierzytelnienia użytkownika.  

##  <a name="compliance-settings"></a>Ustawienia zgodności  

-   **Zaplanuj ocenę zgodności**  

     Wybierz **harmonogram** Aby utworzyć domyślny harmonogram, który jest pokazywane użytkownikom po wdrożeniu przez nich podstawy konfiguracji. Tę wartość można skonfigurować dla każdej podstawy w oknie dialogowym **Wdrażanie podstawy konfiguracji** .  

-   **Włącz dane użytkownika i profile**  

     Wybierz **tak** Jeśli chcesz wdrożyć [dane użytkownika i profile](../../../compliance/deploy-use/create-user-data-and-profiles-configuration-items.md) elementy konfiguracji na komputerach z systemem Windows 8 w hierarchii.  

## <a name="computer-agent"></a>Agent komputera  

-   **Domyślny punkt witryny sieci Web katalogu aplikacji**  

     Configuration Manager używa tego ustawienia, aby łączyć użytkowników z katalogiem aplikacji w Centrum oprogramowania. Użytkownik może określić serwer hostujący punkt witryny sieci Web katalogu aplikacji przy użyciu nazwy NetBIOS lub FQDN, automatyczne wykrywanie lub adres URL wdrożeń dostosowanych. W większości przypadków najlepszym wyborem będzie automatyczne wykrywanie, które ma następujące zalety:  

    -   Klienci automatycznie otrzymują punkt witryny sieci Web katalogu aplikacji z ich lokacji, jeśli ich lokacja ma punkt witryny sieci Web katalogu aplikacji.  

    -   Aplikacja katalogu punktami witryny sieci Web w sieci intranet skonfigurowane dla protokołu HTTPS są preferowane względem tych, które nie są skonfigurowane dla protokołu HTTPS. Pozwala to chronić przed serwerami nieautoryzowanymi.

    -   Gdy klienci zostali skonfigurowani do klienta intranetowego i internetowego zarządzania, otrzymają oni punkt witryny sieci Web katalogu aplikacji internetowych połączonymi z Internetem oraz intranetowy punkt witryny sieci Web katalogu aplikacji, gdy znajdują się w intranecie.  

     Automatyczne wykrywanie nie gwarantuje, że klienci otrzymają najbliższy punkt witryny sieci Web katalogu aplikacji. Użytkownik może zrezygnować z funkcji **Wykryj automatycznie** z następujących przyczyn:  

     -   Użytkownik chce ręcznie skonfigurować najbliższy serwer dla klientów lub uniemożliwić klientom łączenie się z serwerem przez wolne połączenie sieciowe.  

     -   Użytkownik chce kontrolować, którzy klienci łączą się z którym serwerem. Ta konfiguracja może być do testowania wydajności lub z przyczyn biznesowych.  

     -   Użytkownik nie chce czekać do 25 godzin na zmianę sieci, aby klienci zostali skonfigurowani przy użyciu innego punktu witryny sieci Web katalogu aplikacji.  

     Jeśli punkt witryny sieci Web katalogu aplikacji należy określić zamiast używać automatycznego wykrywania, określ nazwę NetBIOS zamiast intranetową nazwę FQDN. Pozwala to zmniejszyć prawdopodobieństwo czy użytkownicy będą monitowani o poświadczenia podczas łączenia się z katalogiem aplikacji w sieci intranet. Aby korzystać z nazwy NetBIOS, muszą być spełnione następujące warunki:  

     -   Nazwa NetBIOS została określona we właściwościach punktu witryny sieci Web katalogu aplikacji.  

     -   Korzystanie z usługi WINS lub wszyscy klienci znajdują się w tej samej domenie co punkt witryny sieci Web katalogu aplikacji.  

     -   Punkt witryny sieci Web katalogu aplikacji jest skonfigurowany dla połączeń klienckich HTTP, lub jest ono skonfigurowane dla połączeń klienckich HTTPS i certyfikatu serwera sieci web ma nazwę NetBIOS.  

     Zwykle użytkownicy są monitowani o podanie poświadczeń, gdy adres URL ma nazwę FQDN, ale nie w przypadku, gdy adres URL jest nazwą NetBIOS. Monit będzie wyświetlany zawsze wtedy, gdy użytkownicy będą się łączyć z Internetu, ponieważ to połączenie musi korzystać z internetowej nazwy FQDN. Jeśli jest wyświetlany monit o podanie poświadczeń gdy użytkownicy są połączeni z Internetem, należy sprawdzić, czy serwer, na którym jest uruchomiony punkt witryny sieci Web katalogu aplikacji, może się połączyć z kontrolerem domeny konta użytkownika, co umożliwi uwierzytelnienie użytkownika przy użyciu protokołu Kerberos.  

    > [!NOTE]  
    >  Opis działania automatycznego wykrywania:  
    >   
    >  Klient wysyła żądanie lokalizacji usługi do punktu zarządzania. Jeśli w tej samej lokacji, w której znajduje się klient, istnieje punkt witryny sieci Web katalogu aplikacji, serwer zostanie przekazany klientowi jako serwer, który ma być wykorzystywany jako serwer katalogu aplikacji. Gdy więcej niż jeden punkt witryny sieci Web katalogu aplikacji jest dostępna w lokacji, z włączonym protokołem HTTPS serwera mają pierwszeństwo przed serwerem, który nie jest włączony dla protokołu HTTPS. Po powyższym filtrowaniu wszyscy klienci otrzymają jeden z serwerów, które ma być używana jako katalog aplikacji; Menedżer konfiguracji nie równoważy obciążenia między wieloma serwerami. Gdy lokacja klienta nie ma punkt witryny sieci Web katalogu aplikacji, punkt zarządzania zwróci w sposób niedeterministyczny punkt witryny sieci Web katalogu aplikacji z hierarchii.  
    >   
    >  Jeśli klient znajduje się w intranecie, jeśli wybrany punkt witryny sieci Web katalogu aplikacji jest skonfigurowana przy użyciu nazwy NetBIOS dla adresu URL katalogu aplikacji, klienci otrzymają tę nazwę NetBIOS zamiast intranetową nazwę FQDN. Po stwierdzeniu, że klient znajduje się w Internecie, klient otrzyma wyłącznie internetową nazwę FQDN.  
    >   
    >  Klient wysyła to żądanie lokalizacji usługi co 25 godzin lub po wykryciu zmiany sieci. Na przykład, jeśli klient zostanie przeniesiony z sieci intranet do Internetu i zlokalizuje internetowy punkt zarządzania, internetowy punkt zarządzania udostępni klientom internetowe serwery punktów witryny sieci Web katalogu aplikacji.  

-   **Dodaj domyślną witrynę sieci Web katalogu aplikacji do strefy Zaufane witryny programu Internet Explorer**  

     Jeśli ta opcja jest **True** lub **tak**, bieżący domyślny katalog aplikacji witryny sieci Web adres URL jest automatycznie dodawany do strefy Zaufane witryny w programie Internet Explorer na komputerach klienckich.  

     To ustawienie zapewnia, że tryb chroniony programu Internet Explorer jest wyłączony. Jeśli tryb chroniony jest włączony, klient programu Configuration Manager nie może być mógł instalować aplikacji z katalogu aplikacji. Domyślnie strefa Zaufane witryny obsługuje również logowanie użytkownika do katalogu aplikacji, co wymaga uwierzytelnienia systemu Windows.  

     Jeśli opuścisz tę opcję **False**, klientów programu Configuration Manager nie można instalować aplikacji z katalogu aplikacji, chyba że te ustawienia programu Internet Explorer zostały skonfigurowane w innej strefie dla adresu URL katalogu aplikacji używanego przez klientów.  

    > [!NOTE]  
    >  Zawsze, gdy programu Configuration Manager dodaje domyślny katalog aplikacji do strefy Zaufane witryny, programu Configuration Manager usuwa wcześniejszy domyślny adres URL katalogu aplikacji programowi Configuration Manager dodany przed dodaniem nowego wpisu.  
    >   
    >  Menedżer konfiguracji nie może dodać adresu URL, jeśli został on już określony w jednej ze stref zabezpieczeń. W tym scenariuszu należy usunąć adres URL z innej strefy lub ręcznie skonfigurować wymagane ustawienia programu Internet Explorer.  

-   **Pozwól na uruchamianie aplikacji Silverlight w trybie podwyższonego zaufania**  

     To ustawienie musi być **tak** Jeśli użytkownicy uruchamiają klienta programu Configuration Manager i korzystają z katalogu aplikacji.  

     Zmiana tego ustawienia będzie wprowadzona po kolejnym załadowaniu przeglądarki lub odświeżeniu obecnie otwartego okna przeglądarki przez użytkowników.  

     Aby uzyskać więcej informacji o tym ustawieniu, zobacz [certyfikatów dla programu Microsoft Silverlight 5 i tryb podwyższonego zaufania wymagany przez katalog aplikacji](../../../apps/plan-design/security-and-privacy-for-application-management.md#BKMK_CertificatesSilverlight5) w [bezpieczeństwo i prywatność zarządzania aplikacjami w programie System Center Configuration Manager](../../../apps/plan-design/security-and-privacy-for-application-management.md).  

-   **Nazwa organizacji wyświetlana w Centrum oprogramowania**  

     Wpisz nazwę wyświetlaną użytkownikom w Centrum oprogramowania. Te informacje o znakowaniu ułatwiają użytkownikom zidentyfikowanie tej aplikacji jako pochodzącej z zaufanego źródła.  

-   **Użyj nowego Centrum oprogramowania**  

     Jeśli opcja jest włączona, wszystkie komputery klienckie z celem tych ustawień klienta zostanie Użyj nowego centrum oprogramowania. Program Software Center zawiera aplikacje dostępne dla użytkowników, które były wcześniej dostępne tylko w wykazie aplikacji zależnych od programu Silverlight.  

     Punkt witryny sieci Web katalogu aplikacji i usług sieci web katalogu aplikacji punktu systemu lokacji, które role są nadal wymagane dla aplikacje dostępne dla użytkowników, które mają być widoczne w Centrum oprogramowania.  

     Aby uzyskać więcej informacji, zobacz [Planowanie konfiguracji zarządzania aplikacjami w programie System Center Configuration Manager i przeprowadzanie konfiguracji](../../../apps/plan-design/plan-for-and-configure-application-management.md).  

-   **Uprawnienia do instalacji**  

    > [!WARNING]  
    >  To ustawienie dotyczy katalogu aplikacji i Centrum oprogramowania. To ustawienie nie obowiązuje, gdy użytkownicy korzystają z portalu firmy.  

     Konfigurowanie sposobu inicjowania instalacji oprogramowania, aktualizacji oprogramowania oraz sekwencji zadań przez użytkowników:  

    -   **Wszyscy użytkownicy**: Użytkownicy zalogowani do komputera klienckiego z dowolnym uprawnieniami oprócz uprawnień gościa mogą inicjować instalację oprogramowania, aktualizacji oprogramowania i sekwencji zadań.  

    -   **Tylko Administratorzy**: Użytkownicy zalogowani na komputerze klienckim musi być członkiem lokalnej grupy administratorów, aby inicjować instalację oprogramowania, aktualizacji oprogramowania i sekwencji zadań.  

    -   **Tylko administratorzy i użytkownicy podstawowi**: Użytkownicy zalogowani na komputerze klienckim musi być członkiem lokalnej grupy administratorów lub użytkownikiem podstawowym komputera, aby móc inicjować instalację oprogramowania, aktualizacji oprogramowania i sekwencji zadań.  

    -   **Użytkownicy nie**: Użytkownicy zalogowani na komputerze klienckim nie mogą inicjować instalację oprogramowania, aktualizacji oprogramowania i sekwencji zadań. Wdrożenia wymagane dla komputera są zawsze instalowane po upływie terminu wdrożenia. Użytkownicy nie mogą inicjować instalację oprogramowania z katalogu aplikacji lub Centrum oprogramowania.  

-   **Zawieś wprowadzanie numeru PIN funkcji BitLocker przy ponownym uruchomieniu**  

     Jeśli na komputerach skonfigurowano wprowadzanie numeru PIN funkcji BitLocker, za pomocą tej opcji można pominąć wymaganie wprowadzania numeru PIN przy ponownym uruchomieniu komputera po zainstalowaniu oprogramowania.  

    -   **Zawsze**: Configuration Manager tymczasowo zawiesi funkcji BitLocker po zainstalowaniu oprogramowania wymagającego ponownego uruchomienia i zainicjował ponowne uruchomienie komputera. To ustawienie ma zastosowanie tylko do ponownego uruchomienia komputera, który jest inicjowane przez program Configuration Manager i nie wstrzymuje wymagania podania numeru PIN funkcji BitLocker po ponownym uruchomieniu komputera przez użytkownika. Wymaganie wprowadzania numeru PIN funkcji BitLocker zostanie wznowione po uruchomieniu systemu Windows.

    -   **Nigdy nie**: Menedżer konfiguracji nie zawiesił funkcji BitLocker przy następnym uruchomieniu komputera po zainstalowaniu oprogramowania wymagającego ponownego uruchomienia. Przy takim scenariuszu instalowanie oprogramowania nie zostanie zakończone przed wprowadzeniem numeru PIN przez użytkownika w celu ukończenia standardowego procesu uruchamiania i załadowania systemu Windows.

-   **Wdrażanie aplikacji oraz aktualizowanie oprogramowania jest zarządzane przez dodatkowe oprogramowanie**  

     Tę opcję należy włączyć tylko po spełnieniu jednego z następujących warunków:  

    -   Użytkownik korzysta z rozwiązania dostawcy wymagającego, aby to ustawienie było włączone.  

    -   Korzystając z programu Configuration Manager zestaw software development kit (SDK) w celu zarządzania powiadomieniami agentem klienta i instalacji aplikacji i aktualizacji oprogramowania.  

    > [!WARNING]  
    >  Jeśli wybierzesz tę opcję, gdy żadna z tych warunków nie ma zastosowania, aktualizacji oprogramowania i wymaganych aplikacji nie są zainstalowane na komputerach klienckich. To ustawienie nie uniemożliwia użytkownikom instalowanie aplikacji z katalogu aplikacji lub uniemożliwić pakietów, programów i sekwencji zadań jest instalowany na komputerach klienckich.  

-   **Zasady wykonywania programu PowerShell**  

     Skonfiguruj sposób klientów programu Configuration Manager może uruchamiać skrypty programu Windows PowerShell. Skrypty te są często używane do wykrywania w elementach konfiguracji ustawień zgodności. Mogą być również wysyłane w ramach wdrożenia jako skrypty standardowe.  

    -   **Obejście**: Klient programu Configuration Manager pomija konfigurację programu Windows PowerShell na komputerze klienckim, co umożliwia uruchamianie niepodpisanych skryptów.  

    -   **Ograniczone**: Klient programu Configuration Manager korzysta z bieżącej konfiguracji środowiska Windows PowerShell na komputerze klienckim. Ta konfiguracja Określa, czy można uruchamiać niepodpisane skrypty.  

    -   **Wszystko podpisane**: Klient programu Configuration Manager uruchamia skrypty tylko wtedy, gdy podpisała ich zaufanego wydawcę. To ograniczenie obowiązuje niezależnie od bieżącej konfiguracji programu Windows PowerShell na komputerze klienckim.  

     Ta opcja wymaga co najmniej programu Windows PowerShell w wersji 2.0. Wartość domyślna to **wszystko podpisane**.  

    > [!TIP]  
    >  Jeśli nie ze względu na to ustawienie klienta uruchomienie niepodpisanych skryptów, program Configuration Manager zaraportuje ten błąd w następujący sposób:  
    >   
    > -   Identyfikator błędu **0X87D00327** i opis **skrypt nie jest podpisany** jako błąd stanu wdrożenia w **monitorowanie** obszaru roboczego w konsoli programu Configuration Manager.  
    > -   Kody błędów i opisy **0X87D00327** i **skrypt nie jest podpisany** lub **0X87D00320** i **host skryptów nie został jeszcze zainstalowany** z typem błędu **błąd odnajdywania** w raportach. Na przykład **szczegóły błędów elementów konfiguracji w linii bazowej konfiguracji dla zasobu**.  
    > -   Komunikat **skrypt nie jest podpisany (błąd: 87D 00327; Źródło: CCM)** w **DcmWmiProvider.log** pliku.  

-   **Pokaż powiadomienia o nowych wdrożeniach**  

     Wybierz **tak** jeśli mają być wyświetlane powiadomienia w przypadku wdrożeń, które były dostępne mniej niż tydzień.  Zawsze, gdy agent klienta uruchamia zostanie wyświetlony ten komunikat.

-   **Wyłącz losowe generowanie terminu ostatecznego**  

     To ustawienie określa, czy klient stosuje maksymalnie 2 godziny opóźnienie aktywacji w celu zainstalowania wymaganych aktualizacji oprogramowania po osiągnięciu terminu ostatecznego. Opóźnienie aktywacji jest domyślnie wyłączone.  

     W scenariuszach infrastruktury pulpitu wirtualnego (VDI) to opóźnienie może pomóc w rozłożeniu przetwarzania procesora CPU i transferu danych na komputerze, który ma wiele maszyn wirtualnych z klientem programu Configuration Manager. Nawet jeśli nie używasz infrastruktury pulpitów wirtualnych, jeśli wielu klientów instaluje jednocześnie te same aktualizacje, to to zwiększyć użycie procesora CPU na serwerze lokacji. Można również spowolnić punkty dystrybucji i znacznie zmniejszyć dostępną przepustowość sieci.  

     Jeśli wymagane aktualizacje oprogramowania musi być zainstalowane niezwłocznie po osiągnięciu terminu ostatecznego, wybierz **tak** dla tego ustawienia.  

-   **Okres prolongaty wymuszania po wdrożenia terminu wdrożenia (godziny)**

     W niektórych przypadkach można umożliwić użytkownikom więcej czasu do instalacji wymagane wdrożenia aplikacji lub aktualizacji oprogramowania poza wszystkie terminy, które zostały skonfigurowane. To może być zwykle być wymagane, jeśli komputer został wyłączony przez dłuższy czas i musi zainstalować dużą liczbę wdrożeń aplikacji lub aktualizacji. Na przykład jeśli użytkownik ma tylko zwrócone z urlopu, ich może być konieczne Zaczekaj, aż do postaci długiej jako zaległe aplikacji są zainstalowane wdrożeń. Aby rozwiązać ten problem, można zdefiniować okres prolongaty wymuszania przez wdrożenie ustawienia klienta programu Configuration Manager do kolekcji.

     Można ustawić okresu prolongaty, 1 – 120 godzin. To ustawienie jest używane w połączeniu z właściwością wdrożenia **Opóźnij wymuszenie dotyczące tego wdrożenia zgodnie z preferencjami użytkownika**. Aby uzyskać więcej informacji, zobacz [wdrażania aplikacji](/sccm/apps/deploy-use/deploy-applications).

##  <a name="computer-restart"></a>Ponowne uruchomienie komputera  
 Po określeniu tych ustawień dotyczących ponownego uruchomienia komputera należy sprawdzić, czy wartość interwału tymczasowego powiadamiania o ponownym uruchomieniu i wartość interwału odliczania końcowego są krótsze od najkrótszego okna obsługi ustawionego dla komputera.  

 Aby uzyskać więcej informacji o korzystaniu z okien obsługi, zobacz [Używanie okien obsługi w programie System Center Configuration Manager](../../../core/clients/manage/collections/use-maintenance-windows.md).  

##  <a name="endpoint-protection"></a>Program Endpoint Protection  

-   **Zarządzanie klientem programu Endpoint Protection na komputerach klienckich**  

     Wybierz **True** lub **tak** Jeśli chcesz zarządzać istniejącymi klientami programu Endpoint Protection na komputerach w hierarchii.  

     Wybierz tę opcję, jeśli użytkownik zainstalował już klienta programu Endpoint Protection i chce możesz nim zarządzać za pomocą programu Configuration Manager.  

     Ponadto należy wybrać tę opcję, jeśli chcesz utworzyć skrypt w celu odinstalowania istniejącego rozwiązania chroniącego przed złośliwym kodem, zainstalowania klienta programu Endpoint Protection i wdrożyć ten skrypt za pomocą aplikacji programu Configuration Manager lub pakietów i programów.  

-   **Zainstaluj klienta programu Endpoint Protection na komputerach klienckich**  

     Wybierz **True** lub **tak** Aby zainstalować i włączyć klienta programu Endpoint Protection na komputerach klienckich, na którym nie jest już zainstalowany.  

    > [!NOTE]  
    >  Jeśli jest już zainstalowany klient programu Endpoint Protection, wybierając **False** lub **nr** nie spowoduje odinstalowania klienta programu Endpoint Protection. Aby odinstalować klienta programu Endpoint Protection, **klienta zarządzania Endpoint Protection na komputerach klienckich** ustawienia klienta dotyczącego **False** lub **nr**. Następnie należy wdrożyć pakiet i program, aby odinstalować klienta programu Endpoint Protection.  

-   **W przypadku urządzeń Windows Embedded z filtrami zapisu należy zatwierdzić instalację klienta programu Endpoint Protection (wymaga to ponownego uruchomienia komputera).**  

     Wybierz **tak** wyłączyć filtr zapisu na urządzeniu Windows Embedded, a następnie ponownie uruchomić urządzenie. co spowoduje zatwierdzenie instalacji na urządzeniu.  

     Po określeniu dla opcji wartości **Nie** klient zostanie zainstalowany na tymczasowej nakładce, która zostanie wyczyszczona po ponownym uruchomieniu urządzenia. Przy takim scenariuszu klient programu Endpoint Protection nie zostanie zatwierdzony przed zatwierdzeniem zmian na urządzeniu przez inną instalację. To jest ustawienie domyślne.  

-   **Pomiń wszystkie wymagane ponowne uruchomienie komputera po zainstalowaniu klienta programu Endpoint Protection**  

     Wybierz **True** lub **tak** pominąć ponowne uruchomienie komputera, jeśli jest ono wymagane po zainstalowaniu klienta programu Endpoint Protection.  

    > [!IMPORTANT]  
    >  Jeśli klient programu Endpoint Protection wymaga ponownego uruchomienia komputera, a to ustawienie jest **False**, ponowne uruchomienie nastąpi niezależnie od oknami obsługi, które zostały skonfigurowane.  

-   **Dozwolony okres czasu, użytkownicy mogą odłożyć ponowne uruchomienie w celu ukończenia instalacji programu Endpoint Protection (godziny)**  

     Określ liczbę godzin, który użytkownicy mogą odłożyć ponowne uruchomienie komputera, jeśli jest to wymagane po zainstalowaniu klienta programu Endpoint Protection. Tę opcję można skonfigurować tylko wtedy, gdy **Pomiń wszystkie wymagane ponowne uruchomienie komputera po zainstalowaniu klienta programu Endpoint Protection** jest opcja **False**.  

-   **Wyłącz źródła alternatywne (takie jak Windows Update, Microsoft Windows Server Update Services lub udziały UNC) dla wstępnej aktualizacji definicji na komputerach klienckich**  

     Wybierz **True** lub **tak** Jeśli program Configuration Manager do zainstalowania wyłącznie wstępną aktualizację definicji na komputerach klienckich. To ustawienie pomaga uniknąć niepotrzebnych połączeń sieciowych i ograniczyć przepustowość podczas wstępnej instalacji aktualizacji definicji.  

##  <a name="hardware-inventory"></a>Spis sprzętu  

-   **Maksymalny rozmiar niestandardowego pliku MIF (KB)**  

     Określ maksymalny rozmiar w kilobajtach dozwoloną dla każdego niestandardowy plik Management Information Format (MIF), które zostaną zebrane od klientów w cyklu wykonywania spisu sprzętu. Pliki MIF o większym rozmiarze, spisu sprzętu programu Configuration Manager nie będzie przetwarzał je. Można określić rozmiar od 1 do 5000 KB. Wartością domyślną jest 250 KB. To ustawienie nie wpływa na rozmiar standardowego pliku danych zapasów sprzętu.  

    > [!NOTE]  
    >  To ustawienie jest dostępne tylko w domyślnych ustawieniach klienta.  

-   **Klasy zapasów sprzętu**  

     W programie Configuration Manager można rozszerzyć informacje o sprzęcie zbierane od klientów bez konieczności ręcznego modyfikowania pliku sms_def.mof. Wybierz **Ustaw klasy** Aby rozszerzyć spis sprzętu programu Configuration Manager. Aby uzyskać więcej informacji, zobacz [jak skonfigurować spis sprzętu w programie System Center Configuration Manager](../../../core/clients/manage/inventory/configure-hardware-inventory.md).  

-   **Zbierz pliki MIF**  

     To ustawienie umożliwia określenie, czy do zbierania plików MIF z klientów programu Configuration Manager podczas tworzenia spisu sprzętu.  

     Aby plik MIF mają zostać zebrane przez spis sprzętu musi w poprawnej lokalizacji na komputerze klienckim. Domyślnie pliki znajdują się w następujący sposób:  

    -   Pliki IDMIF powinny znajdować się w folderze Windows\System32\CCM\Inventory\Idmif.  

    -   Pliki NOIDMIF powinny znajdować się w folderze Windows\System32\CCM\Inventory\Noidmif.  

    > [!NOTE]  
    >  To ustawienie jest dostępne tylko w domyślnych ustawieniach klienta.

-   **Maksymalne opóźnienie losowe**

    Zbieranie informacji sprzętu jest wybierane przez maksymalnie cztery godziny tak, że operacja nie została wykonana jednocześnie na wszystkich klientach. Można ustawić wartości maksymalnego opóźnienia, aby ograniczyć czas, w którym odbywa się działanie.      

##  <a name="metered-internet-connections"></a>Mierzonych połączeń internetowych  
 Można zarządzać, jak komputery klienckie systemu Windows 8 będą komunikować się z lokacji programu Configuration Manager po korzystają z mierzonych połączeń internetowych. Dostawcy Internetu czasami naliczają opłaty według ilości wysyłanych i odbieranych danych podczas taryfowego połączenia z Internetem.  

> [!NOTE]  
>  Skonfigurowane ustawienie klienta nie zostanie zastosowane na komputerach klienckich z systemem Windows 8 w następujących scenariuszach:  
>   
> -   Komputer jest zasilany z połączenia danych w roamingu: Klient programu Configuration Manager wykonuje wszystkie zadania, które wymagają danych do przeniesienia do lokacji programu Configuration Manager.  
> -   Właściwości połączenia sieciowego systemu Windows są skonfigurowane jako inną niż taryfową: Klienta programu Configuration Manager działa tak, jakby to nietaryfowe połączenie internetowe i przesyła dane do lokacji programu Configuration Manager.  

-   **Komunikacja z klientem w przypadku mierzonych połączeń internetowych**  

     Dla komputerów klienckich z systemem Windows 8 należy wybrać z listy rozwijanej jedną z następujących opcji:  

    -   **Zezwalaj na**: Cała komunikacja z klientem są dozwolone przez taryfowe połączenie internetowe, chyba że urządzenie klienckie korzysta z połączenia danych w roamingu.  

    -   **Limit**: Wyłącznie następująca komunikacja z klientem są dozwolone przez taryfowe połączenie internetowe:  

        -   Pobieranie zasad klienta  

        -   Komunikaty o stanie klienta, które będą wysłane do lokacji  

        -   Żądania instalacji oprogramowania wynikające z korzystania z katalogu aplikacji  

        -   Wymagane wdrożenia (po osiągnięciu ostatecznego terminu instalacji)  

        > [!IMPORTANT]  
        >  Po zainicjowaniu przez użytkownika instalacji oprogramowania z poziomu Centrum oprogramowania lub katalogu aplikacji instalacje te będą zawsze dozwolone, niezależnie od ustawień mierzonego połączenia internetowego.  

         Po osiągnięciu limitu transferu danych mierzonego połączenia internetowego, klient nie próbuje nawiązać połączenia z lokacji programu Configuration Manager.  

    -   **Blok**: Klient programu Configuration Manager nie będzie próbował komunikować się z lokacji programu Configuration Manager, gdy znajduje się w mierzonego połączenia internetowego. Jest to wartość domyślna.  

##  <a name="power-management"></a>Zarządzanie energią  

-   **Zezwalaj użytkownikom na wykluczanie swoich urządzeń z zarządzania zasilaniem**  

     Z listy rozwijanej wybierz **True** lub **tak** aby umożliwić użytkownikom w programie Software Center wykluczenie ich komputera ze skonfigurowanych ustawień zarządzania energią.  

-   **Włącz serwer proxy wznawiania**  

     Wybierz opcję **Tak** , aby uzupełnić ustawienie funkcji Wake On LAN lokacji, jeżeli została skonfigurowana dla pakietów emisji pojedynczej.  

     Aby uzyskać więcej informacji o serwerze proxy wznawiania, zobacz [planowanie sposobu wznawiania działania klientów w programie System Center Configuration Manager](../../../core/clients/deploy/plan/plan-wake-up-clients.md).  

    > [!WARNING]  
    >  Nie należy włączać serwera proxy wznawiania w sieci produkcyjnej bez wcześniejszego zrozumienia sposobu jego działania i oceny w środowisku testowym.  

-   **Numer portu serwera proxy wznawiania (UDP)**  

     Należy zachować wartość domyślną numeru portu, które są używane przez komputery do wysyłania pakietów wznawiania do uśpionych komputerów zarządzanych. Lub zmienić numer na wybraną wartość.  

     Określony tutaj numer portu jest automatycznie konfigurowany dla klientów, na których działa Zapora systemu Windows, korzystając z **wyjątek zapory systemu Windows dla serwera proxy wznawiania** opcji. Jeżeli na klientach działa inna zapora, należy skonfigurować ją ręcznie w celu zezwolenia na użycie numeru portu UDP określonego dla tego ustawienia.  

-   **Numer portu funkcji Wake On LAN (UDP)**  

     Należy zachować wartość domyślną 9, chyba że zmieniono numer portu Wake On LAN (UDP) na **porty** kartę witryny **właściwości**.  

    > [!IMPORTANT]  
    >  Ten numer musi być zgodny z wartością w oknie **Właściwości**lokacji. W przypadku zmiany tego numeru w jednym miejscu, nie jest aktualizowana w innym miejscu.  

##  <a name="remote-tools"></a>Zdalne narzędzia  

-   **Włącz zdalne sterowanie na klientach** z opisem **Profile wyjątków zapory**  

     Wybierz, czy zdalne sterowanie programu Configuration Manager jest włączone dla wszystkich komputerów klienckich, które odbierają te ustawienia klienta. Wybierz **Konfiguruj** Aby włączyć zdalne sterowanie. Opcjonalnie skonfigurować ustawienia zapory, aby umożliwić zdalne sterowanie do pracy na komputerach klienckich.  

     Zdalne sterowanie jest domyślnie wyłączone.  

    > [!IMPORTANT]  
    >  Jeżeli ustawienia zapory nie zostaną skonfigurowane, zdalne sterowanie może nie działać prawidłowo.  

-   **Użytkownicy mogą zmieniać zasady lub ustawienia powiadomień w programie Software Center**  

     Wybierz, czy użytkownicy mogą zmieniać opcje zdalnego sterowania z programu Software Center.  

-   **Zezwalaj na zdalne sterowanie komputerem nienadzorowanym**  

     Wybierz, czy administrator może użyć sterowania zdalnego dostępu do komputera klienta, który jest wylogowanego lub zablokowanego. Tylko zalogowanymi i odblokowanymi komputer można sterować zdalnie, gdy to ustawienie jest wyłączone.  

-   **Monituj użytkownika o zezwolenie na zdalne sterowanie**  

     Wybierz, czy komputer kliencki wyświetli komunikat z pytaniem o zezwolenie użytkownika przed zezwoleniem na sesję zdalnego sterowania.  

-   **Przyznaj uprawnienie do zdalnego sterowania lokalnej grupie administratorów**  

     Wybierz, czy Administratorzy lokalni na serwerze inicjującym połączenie zdalnego sterowania mogą nawiązywać sesje zdalnego sterowania na komputerach klienckich.  

-   **Dozwolony poziom dostępu**  

     Należy określić dozwolony poziom dostępu za pomocą zdalnego sterowania. Można wybrać jedną z następujących opcji:  

    -   Pełna kontrola  

    -   Wyświetl tylko  

    -   Brak  

-   **Dopuszczone podglądy**  

     Wybierz **Ustaw podglądy** otworzyć **Konfiguruj ustawienie klienta** okna dialogowego i określić nazwy użytkowników systemu Windows, którzy mogą nawiązywać sesje zdalnego sterowania na komputerach klienckich.  

-   **Pokaż ikonę powiadomienia sesji na pasku zadań**  

     Wybierz tę opcję, aby wyświetlić ikony na pasku zadań klienta komputerów, aby wskazać, że sesja zdalnego sterowania jest aktywna.  

-   **Pokaż pasek połączenia sesji**  

     Wybierz tę opcję, aby wyświetlić pasek połączenia sesji wysokiej widoczności na kliencie komputerów, aby wskazać, że sesja zdalnego sterowania jest aktywna.  

-   **Odtwórz dźwięk na kliencie**  

     Wybierz tę opcję, aby użyć dźwięku sygnalizującego, kiedy sesja zdalnego sterowania jest aktywna na komputerze klienckim. Dźwięk można odtworzyć po połączeniu lub rozłączeniu sesji albo odtwarzać go wielokrotnie podczas sesji.  

-   **Zarządzaj ustawieniami nieżądanej pomocy zdalnej**  

     Wybierz tę opcję, aby umożliwić programowi Configuration Manager Zarządzanie sesjami nieżądanej pomocy zdalnej.  

     W sesji nieżądanej pomocy zdalnej użytkownika na komputerze klienckim nie żądanie pomocy w zainicjowaniu sesji.  

-   **Zarządzaj ustawieniami pomocy zdalnej na żądanie**  

     Wybierz tę opcję, aby umożliwić programowi Configuration Manager Zarządzanie sesjami pomocy zdalnej na żądanie.  

     W sesji Pomocy zdalnej na żądanie użytkownika na komputer kliencki wysłał żądanie do administratora o pomoc zdalną.  

-   **Poziom dostępu dla pomocy zdalnej**  

     Wybierz poziom dostępu przypisany do sesji Pomocy zdalnej, inicjowanych w konsoli programu Configuration Manager.  

    > [!NOTE]  
    >  Użytkownik przy komputerze klienckim musi zawsze udzielić zezwolenia, aby można było rozpocząć sesję pomocy zdalnej.  

-   **Zarządzaj ustawieniami pulpitu zdalnego**  

     Wybierz tę opcję, aby umożliwić programowi Configuration Manager Zarządzanie sesjami pulpitu zdalnego dla komputerów.  

-   **Zezwalaj dopuszczonym podglądom na połączenie za pomocą programu Podłączanie pulpitu zdalnego**  

     Wybierz tę opcję, aby umożliwić użytkownikom określonych na liście dopuszczonych podglądów mają zostać dodane do grupy użytkowników lokalnych usług pulpitu zdalnego na komputerach klienckich.  

-   **Wymagaj uwierzytelniania na poziomie sieci na komputerach z systemem operacyjnym Windows Vista i nowszymi wersjami**  

     Wybierz tę bezpieczniejszą opcję, jeśli chcesz użyć uwierzytelniania na poziomie sieci w celu nawiązania połączeń pulpitu zdalnego komputerom klienckim z systemem Windows Vista lub nowszym. Uwierzytelnianie na poziomie sieci wymaga początkowo mniej zasobów na komputerze zdalnym, ponieważ uwierzytelnianie użytkownika zostanie zamknięty przed nawiązaniem połączenia pulpitu zdalnego. Ta metoda jest bezpieczniejsza, ponieważ może ułatwić ochronę komputera przed złośliwymi użytkownikami lub oprogramowaniem i zmniejsza ryzyko ataków typu „odmowa usługi”.  

## <a name="software-deployment"></a>Wdrażanie oprogramowania  

-   **Zaplanuj ponowną ocenę dla wdrożeń**  

     Należy skonfigurować harmonogram, gdy program Configuration Manager ponownie ocenia reguły wymagań dla wszystkich wdrożeń. Domyślna wartość to co 7 dni.  

    > [!IMPORTANT]  
    >  Zaleca się, że nie zmienisz tę wartość na mniejszą wartość niż domyślne. Czynności, które mogą negatywnie wpłynąć na wydajność sieci i klienta komputerów.  

     Można także zainicjować tę akcję z komputera klienckiego programu Configuration Manager, wybierając akcję **cykl oceny wdrażania aplikacji** z **akcje** karcie **programu Configuration Manager** w Panelu sterowania.  

##  <a name="software-inventory"></a>Zapasy oprogramowania  

-   **Szczegóły raportowania spisu**  

     Należy określić poziom informacji o plikach umieszczanych w spisie. W celu sporządzenia spisu szczegółowe informacje o pliku, szczegóły dotyczące produktu skojarzonego z plikiem lub wszystkie informacje o pliku.  

-   **Następujące typy plików do spisu**  

     Jeśli chcesz określić typy plików do spisu, wybierz **Ustaw typy** , a następnie skonfiguruj następujące opcje w **Konfiguruj ustawienie klienta** okno dialogowe:  

    > [!NOTE]  
    >  W przypadku wielu niestandardowych ustawień klienta są stosowane do komputera, magazynu, która zwraca każdego ustawienia zostaną scalone.  

    -   Wybierz **nowy** ikonę, aby dodać do spisu nowy typ pliku. Następnie określ następujące informacje w **właściwości zinwentaryzowanych plików** okno dialogowe:  

        -   **Nazwa**: Podaj nazwę pliku, który chcesz dodać do spisu. Można użyć * *\**  znak oznaczającego dowolny ciąg tekstu i **?** oznaczającego pojedynczy znak. Na przykład, jeśli chcesz dodać do spisu wszystkie pliki z rozszerzeniem doc, określ nazwę pliku  **\*doc**.  

        -   **Lokalizacja**: Wybierz **ustawić** otworzyć **właściwości ścieżki** okno dialogowe. Można skonfigurować spis oprogramowania w celu wyszukania na dyskach twardych wszystkich klientów określonego pliku, określonej ścieżki (na przykład **C:\Folder**), lub Wyszukaj określonej zmiennej (na przykład *% windir %*). Można także przeszukać wszystkie podfoldery w określonej ścieżce.  

        -   **Wyklucz pliki zaszyfrowane i skompresowane**: Po wybraniu tej opcji pliki skompresowane lub zaszyfrowane nie podlega ewidencjonowaniu.  

        -   **Wyklucz pliki zawarte w folderze systemu Windows**: Po wybraniu tej opcji pliki w folderze systemu Windows i jego podfolderach nie podlega ewidencjonowaniu.  

    -   Wybierz **OK** zamknąć **właściwości zinwentaryzowanych plików** okno dialogowe.  

    -   Dodaj wszystkie pliki, które mają być spisu, a następnie wybierz pozycję **OK** zamknąć **Konfiguruj ustawienie klienta** okno dialogowe.  

-   **Zbierz pliki**  

     Aby zebrać pliki z komputerów klienckich, należy wybrać **Ustaw pliki** , a następnie skonfiguruj następujące opcje:  

    > [!NOTE]  
    >  W przypadku wielu niestandardowych ustawień klienta są stosowane do komputera, magazynu, która zwraca każdego ustawienia zostaną scalone.  

    -   W **Konfiguruj ustawienie klienta** oknie dialogowym wybierz **nowy** ikonę, aby dodać plik do zebrania.  

    -   W oknie dialogowym **Właściwości zebranych plików** wprowadź następujące informacje:  

        -   **Nazwa**: Podaj nazwę pliku, który chcesz zebrać. Można użyć * *\**  znak oznaczającego dowolny ciąg tekstu i **?** oznaczającego pojedynczy znak.  

        -   **Lokalizacja**: Wybierz **ustawić** otworzyć **właściwości ścieżki** okno dialogowe. Można skonfigurować spis oprogramowania, aby wyszukać dyskach twardych wszystkich klientów pliku do zebrania, określonej ścieżki (na przykład **C:\Folder**), lub Wyszukaj określonej zmiennej (na przykład *% windir %*). Można także przeszukać wszystkie podfoldery w określonej ścieżce.  

        -   **Wyklucz pliki zaszyfrowane i skompresowane**: Po wybraniu tej opcji pliki skompresowane lub zaszyfrowane nie zostaną zebrane.  

        -   **Zatrzymaj zbieranie plików, gdy łączny rozmiar plików przekracza (KB)**: Określ rozmiar pliku (w kilobajtach), po przekroczeniu którego kolejne pliki określone w obszarze **nazwa** zostaną zebrane.  

          > [!NOTE]  
          >  Serwer lokacji zbiera pięć ostatnio zmienionych wersji zebranych plików i zapisuje je w  *&lt;katalog instalacyjny programu ConfigMgr\>*\Inboxes\Sinv.box\Filecol katalogu. Jeżeli plik nie został zmieniony od momentu ostatniego zebrania spisu oprogramowania, plik nie zostanie zebrany ponownie.  
          >   
          >  Spis oprogramowania nie zbiera pliki większe niż 20 MB.  
          >   
          >  Wartość **maksymalny rozmiar wszystkich zebranych plików (KB)** w **Konfiguruj ustawienie klienta** wyświetlane okno dialogowe maksymalny rozmiar wszystkich zebranych plików. Po osiągnięciu tego rozmiaru zbieranie zostanie zatrzymane. Wszystkie już zebrane pliki są zachowywane i wysłane do serwera lokacji.  

          > [!IMPORTANT]
          >  Jeśli skonfigurowano zapasy oprogramowania w celu zebrania wielu dużych plików, może to negatywnie wpłynąć na wydajność sieci i serwera lokacji.  

        Aby uzyskać informacje o sposobie wyświetlania zebranych plików, zobacz [jak używać Eksploratora zasobów do wyświetlania spisu oprogramowania w programie System Center Configuration Manager](../../../core/clients/manage/inventory/use-resource-explorer-to-view-software-inventory.md).  

    -   Wybierz **OK** zamknąć **właściwości zebranych plików** okno dialogowe.  

    -   Dodaj wszystkie pliki, które chcesz zebrać, a następnie wybierz **OK** zamknąć **Konfiguruj ustawienie klienta** okno dialogowe.  

-   **Ustaw nazwy**  

     Podczas tworzenia spisu oprogramowania nazwy producentów i produktów są pobierane z informacji w nagłówku plików zainstalowanych na klientach w lokacji. Ponieważ te nazwy w informacjach w nagłówkach plików nie zawsze są standardowe, podczas wyświetlania informacji o spisie oprogramowania w programie Eksplorator zasobów lub wykonywania kwerend mogą zostać wyświetlone różne wersje tego samego producenta lub nazwy produktu. Jeśli chcesz ustandaryzować te wyświetlane nazwy, wybierz **Ustaw nazwy** , a następnie skonfiguruj następujące opcje w **Konfiguruj ustawienie klienta** okno dialogowe:  

    -   **Nazwa typu**: Spis oprogramowania zbiera informacje o producentach i produktach. Z listy rozwijanej wybierz, czy chcesz skonfigurować nazwy wyświetlane dla **producenta** lub **produktu**.  

    -   **Nazwa wyświetlana**: Określ nazwę wyświetlaną, która ma być używany zamiast nazw na **zinwentaryzowane nazwy** listy. Możesz wybrać **nowy** ikonę, aby określić nową nazwę wyświetlaną.  

    -   **Zinwentaryzowane nazwy**: Wybierz **nowy** ikonę, aby dodać nową zinwentaryzowaną nazwę, która zostanie zastąpiona w spisie oprogramowania przez nazwę wybraną w **Nazwa wyświetlana** listy. Można dodać kilka nazw, które zostaną zastąpione.  

##  <a name="software-updates"></a>Aktualizacje oprogramowania  

-   **Włącz aktualizacje oprogramowania na klientach**  

     To ustawienie umożliwia włączenie aktualizacji oprogramowania na klientach programu Configuration Manager. Gdy to ustawienie zostanie wyłączone, programu Configuration Manager usunie istniejące zasady wdrażania z klienta. Po ponownym włączeniu tego ustawienia klient pobierze bieżące zasady wdrażania.  

    > [!IMPORTANT]  
    >  Gdy to ustawienie zasad ustawienia ochrony dostępu do sieci i zgodności, które opierają się na ustawienie urządzenia dla aktualizacji oprogramowania nie będzie już działać.  

-   **Harmonogram skanowania w poszukiwaniu aktualizacji oprogramowania**  

     To ustawienie umożliwia określenie częstotliwości inicjowania przez klienta skanowania w celu oceny zgodności aktualizacji oprogramowania. Skanowanie w celu oceny zgodności określa stan aktualizacji oprogramowania na kliencie (na przykład wymagane lub zainstalowane). Aby uzyskać więcej informacji na temat oceny zgodności, zobacz [oceny zgodności aktualizacji oprogramowania](../../../sum/understand/software-updates-introduction.md#BKMK_SUMCompliance).  

     Domyślnie używany jest prosty harmonogram i zainicjowaniu skanowania zgodności co 7 dni. Można wybrać utworzenie harmonogramu niestandardowego w celu dokładnego określenia dnia i godziny rozpoczęcia, wybrać, czy ma być używany czas UTC czy lokalny i skonfigurować interwał powtarzania dla określonego dnia tygodnia.  

    > [!NOTE]  
    >  W przypadku określenia interwału krótszego niż 1 dzień, programu Configuration Manager automatycznie domyślnie 1 dzień.  

    > [!WARNING]  
    >  Rzeczywista godzina uruchomienia na komputerach klienckich to godzina uruchomienia plus przypadkowy czas wynoszący maksymalnie 2 godziny. Zapobiega to inicjowaniu przez komputery klienckie jednoczesnego skanowania i łączenia się z usługami Windows Server Update Services (WSUS) na serwerze punktu aktualizacji oprogramowania aktywnego.  

-   **Zaplanuj ponowną ocenę wdrożenia**  

     To ustawienie umożliwia skonfigurowanie, jak często Agent klienta aktualizacji oprogramowania ponownie ocenia aktualizacje oprogramowania dla stanu instalacji na komputerach klienckich programu Configuration Manager. Gdy aktualizacje oprogramowania, które poprzednio były zainstalowane znajduje się już na komputerach klienckich i są nadal wymagane, ich ponownie są zainstalowane.

     Harmonogram ponownej oceny wdrożenia należy dostosować zgodnie z zasadą firmową dotyczącą zgodności aktualizacji oprogramowania, czy użytkownicy mają możliwość odinstalowania aktualizacji oprogramowania i tak dalej. Należy pamiętać, że każdy cykl ponownej oceny wdrożenia powoduje niektóre działania Procesora komputera klienta i sieci. Domyślnie używany jest prosty harmonogram i skanowania ponownej oceny wdrożenia jest inicjowane co 7 dni.  

    > [!NOTE]  
    >  W przypadku określenia interwału krótszego niż 1 dzień, programu Configuration Manager automatycznie domyślnie 1 dzień.  

-   **Po osiągnięciu ostatecznego terminu dowolnej aktualizacji oprogramowania zainstaluj wszystkie pozostałe wdrożenia aktualizacji oprogramowania z terminem wypadającym w danym czasie**  

     To ustawienie umożliwia zainstalowanie wszystkich aktualizacji oprogramowania w wymaganych wdrożeniach, których terminy wypadają w danym czasie. Po osiągnięciu ostatecznego terminu wdrożenia aktualizacji do wymaganego oprogramowania, instalacja jest inicjowana na klientów pod kątem aktualizacji oprogramowania we wdrożeniu. To ustawienie określa, czy ma być dodatkowo inicjowana instalacja aktualizacji oprogramowania w innych wymaganych wdrożeniach, których termin wypada w określonym czasie.  

     To ustawienie umożliwia przyspieszenie instalacji wymaganych aktualizacji oprogramowania, potencjalne zwiększenie bezpieczeństwa, potencjalne zmniejszenie liczby wyświetlanych powiadomień oraz potencjalne zmniejszenie liczby ponownych uruchomień systemów na komputerach klienckich. Domyślnie to urządzenie nie jest włączone.  

-   **Okres czasu, w którym wszystkie oczekujące wdrożenia z terminem wypadającym w tym okresie także zostaną zainstalowane**  

     To ustawienie umożliwia określenie przedziału czasu dla poprzedniego ustawienia. Można wprowadzić wartość od 1 do 23 godzin oraz 1 do 365 dni. Domyślne ustawienie to 7 dni.  

-   **Włącz instalację plików instalacji ekspresowej na klientach**

-   **Port używany do pobierania zawartości plików instalacji ekspresowej**

-   **Włącz zarządzanie Office 365 klienta ponownie** to ustawienie umożliwia włączanie zarządzania agenta klienta Office 365. Jeśli ustawisz wartość **tak**, pozwala na konfigurowanie ustawień instalacji usługi Office 365, pobierania plików z pakietu Office sieci dostarczania zawartości (CDN) i wdrożenia plików jako aplikacji w programie Configuration Manager.

##  <a name="user-and-device-affinity"></a>Koligacja użytkowników i urządzeń  

-   **Próg użycia dla koligacji użytkownika i urządzenia (minuty)**  

     Określ liczbę minut, zanim programu Configuration Manager tworzy mapowanie koligacji urządzenia użytkownika.  

-   **Próg użycia dla koligacji użytkownika i urządzenia (dni)**  

     Określ liczbę dni, przez jaką jest mierzony próg koligacji na podstawie użycia.  

    > [!NOTE]  
    >  Na przykład jeśli **próg użycia koligacji urządzenia użytkownika (w minutach)** jest określony jako **60** minut i **próg użycia koligacji użytkownika i urządzenia (dni)** jest określony jako **5** dni, użytkownik musi używać urządzenia przez 60 minut w okresie 5 dni w celu automatycznego utworzenia koligacji urządzenia użytkownika.  

-   **Automatycznie konfiguruj koligację użytkownika i urządzenia na podstawie danych użycia**  

     Wybierz **True** lub **tak** aby umożliwić automatyczne tworzenie koligacji użytkownika i urządzenia na podstawie zebranych informacji użycia programu Configuration Manager.  

##  <a name="mobile-devices"></a>Urządzenia przenośne  

-   **Profil rejestracji urządzenia przenośnego**  

     Przed skonfigurowaniem tego ustawienia musisz wybrać opcję **Prawda** ustawienia **Zezwalaj użytkownikom na rejestrację urządzeń przenośnych**użytkownika urządzenia przenośnego. Następnie możesz wybrać **Ustaw profil** Aby określić profil rejestracji, który zawiera informacje o szablonie certyfikatu do użycia podczas procesu rejestracji, lokację zawierającą punkt rejestracyjny i punkt proxy rejestracji oraz lokację, która ma zarządzać urządzeniem po wdrożeniu.  

    > [!IMPORTANT]  
    >  Upewnij się, że przed skonfigurowaniem tej opcji został skonfigurowany szablon certyfikatu, który ma być używany z rejestracją urządzenia przenośnego.  

##  <a name="enrollment"></a>Rejestrowanie  

-   **Profil rejestracji urządzenia przenośnego**  

     Przed skonfigurowaniem tego ustawienia musisz wybrać opcję **Tak** ustawienia **Zezwalaj użytkownikom na rejestrację urządzeń przenośnych i komputerów Mac**użytkownika rejestracji. Następnie możesz wybrać **Ustaw profil** Aby określić profil rejestracji, który zawiera informacje o szablonie certyfikatu do użycia podczas procesu rejestracji, lokację zawierającą punkt rejestracyjny i punkt proxy rejestracji oraz lokację, która ma zarządzać urządzeniem po wdrożeniu.  

    > [!IMPORTANT]  
    >  Upewnij się, że przed skonfigurowaniem tej opcji został skonfigurowany szablon certyfikatu, który ma być używany z rejestracją urządzenia przenośnego lub rejestracją certyfikatu klienta na komputery Mac.  

## <a name="user-and-device-affinity"></a>Koligacja użytkowników i urządzeń  

-   **Zezwalaj użytkownikowi na definiowanie urządzeń podstawowych**  

     Określ, czy użytkownicy mogą identyfikować własne urządzenia podstawowe na **Moje urządzenia** kartę katalogu aplikacji.  
