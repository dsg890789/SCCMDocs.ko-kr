---
title: Konfigurowanie odnajdywania | Dokumentacja firmy Microsoft
description: "Skonfiguruj metody odnajdywania w lokacji programu Configuration Manager w celu odnalezienia zasobów, którymi można zarządzać z infrastruktury sieci i usługi Active Directory."
ms.custom: na
ms.date: 7/31/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 49505eb1-d44d-4121-8712-e0f3d8b15bf5
caps.latest.revision: "5"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 34a539ceaea6b070f81a28d2c0a9ce388e26cfeb
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="configure-discovery-methods-for-system-center-configuration-manager"></a>Skonfiguruj metody odnajdywania dla programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*


Możesz skonfigurować metod odnajdywania do uruchamiania w witrynie System Center Configuration Manager, aby znaleźć zasoby, które można zarządzać za pomocą infrastruktury sieci i usługi Active Directory. Należy włączyć, a następnie skonfiguruj każdej metody, która ma być używany do wyszukiwania środowiska. (Można również wyłączyć metodę przy użyciu tej samej procedury, która umożliwia ją włączyć.)  Jedynym wyjątkiem od tej są odnajdywania pulsu i odnajdowanie serwera:  

-   Domyślnie odnajdywanie pulsu jest już włączona po zainstalowaniu lokacji głównej programu Configuration Manager i skonfigurowane do uruchamiania na podstawowe harmonogramu. Należy dobrze jest włączone, ponieważ zapewnia, że rekordy danych odnajdywania (DDR) dla urządzeń są aktualne odnajdywanie pulsu warto pozostawić. Aby uzyskać więcej informacji dotyczących odnajdywania pulsu, zobacz [o odnajdywaniu pulsu](../../../../core/servers/deploy/configure/about-discovery-methods.md#bkmk_aboutHeartbeat).  

-   Odnajdowanie serwera jest metodę automatycznego wykrywania, która umożliwia znalezienie komputerów, które używają jako systemy lokacji. Nie można skonfigurować lub go wyłączyć.  

**Aby włączyć metodę odnajdywania można skonfigurować:**  
 > [!NOTE]  
 > Następujące informacje nie dotyczą odnajdywania użytkownika usługi Azure Active Directory. Zamiast tego zobacz [odnajdywania Skonfiguruj użytkownika programu Azure AD](#azureaadisc) dalszej części tego tematu.

1.  W konsoli programu Configuration Manager wybierz **administracji** > **Konfiguracja hierarchii**, a następnie wybierz pozycję **metod odnajdywania**.  

2.  Wybierz metodę odnajdywania dla lokacji, w której chcesz włączyć odnajdywanie.  

3.  Na **Home** karcie **właściwości** grupy, wybierz **właściwości**, a następnie na **ogólne** karcie wyboru **włączyć&lt;metody odnajdywania\>**  pole.  

     Jeśli to pole jest już zaznaczone, można wyłączyć metodę odnajdywania, usuwając zaznaczenie pola wyboru pole.  

4.  Wybierz **OK** Aby zapisać konfigurację.  


##  <a name="BKMK_ConfigADForestDisc"></a>Konfigurowanie odnajdywania lasu usługi Active Directory  
Aby ukończyć konfigurację odnajdywania lasu usługi Active Directory, należy skonfigurować ustawienia w dwóch miejscach:  

-   W **metod odnajdywania** węzła, można wykonywać następujące czynności:

    - Włączenie tej metody odnajdywania.
    - Ustaw harmonogram sondowania.
    - Wybierz, czy odnajdywanie ma automatycznie tworzyć granice lokacji usługi Active Directory i podsieci, które wykryje.  

-   W **lasy usługi Active Directory** węzła, można wykonywać następujące czynności:

    - Dodać lasy, które chcesz odnajdywać.
    - Włącz odnajdywanie lokacji usługi Active Directory i podsieci, w tym lesie.
    - Skonfiguruj ustawienia, które umożliwiają Lokacje programu Configuration Manager do publikowania swoich informacji o lokacji w lesie.
    - Przypisywanie konta do użycia jako konto lasu usługi Active Directory dla każdego lasu.  

Użyj poniższych procedur, aby włączyć odnajdowanie lasu usługi Active Directory oraz do skonfigurowania poszczególnych lasów na użytek z odnajdywaniem lasu usługi Active Directory.  

#### <a name="to-enable-active-directory-forest-discovery"></a>Aby włączyć odnajdowanie lasu usługi Active Directory  

1.  W konsoli programu Configuration Manager wybierz **administracji** > **Konfiguracja hierarchii**, a następnie wybierz pozycję **metod odnajdywania**.  

2.  Wybierz metodę odnajdywania lasu usługi Active Directory dla lokacji, w której chcesz skonfigurować odnajdywanie.  

3.  Na **Home** karcie **właściwości** grupy, wybierz **właściwości**.  

4.  Na **ogólne** karcie, pole wyboru, aby włączyć odnajdywanie. Lub skonfigurować odnajdywanie teraz, a następnie włączyć je później.  

5.  Określ opcje dotyczące tworzenia granic lokacji dla odnajdywanych lokalizacji.  

6.  Określ harmonogram uruchamiania odnajdywania.  

7.  Po zakończeniu konfigurowania odnajdywania lasu usługi Active Directory dla tej lokacji, wybierz **OK** Aby zapisać konfigurację.  

#### <a name="to-configure-a-forest-for-active-directory-forest-discovery"></a>Aby skonfigurować las dla odnajdywania lasu usługi Active Directory  

1.  W **administracji** obszaru roboczego wybierz **lasy usługi Active Directory**. Jeśli odnajdywanie lasu za pomocą usługi Active Directory było wcześniej uruchamiane, wszystkie odnalezione lasy zostaną wyświetlone w okienku wyników. Uruchomienie odnajdywania lasu za pomocą usługi Active Directory powoduje odnalezienie lasu lokalnego oraz wszystkich lasów zaufanych. Ręcznie należy dodać tylko lasy niezaufane.  

    -   W celu skonfigurowania poprzednio odnalezionego lasu wybierz go w okienku wyników. Następnie na **Home** karcie **właściwości** grupy, wybierz **właściwości** aby otworzyć właściwości lasu. Przejdź do kroku 3.  

    -   Do skonfigurowania nowego lasu, który nie ma na liście, na **Home** karcie **Utwórz** grupy, wybierz **Dodaj las** otworzyć **Dodawanie lasów** okno dialogowe. Przejdź do kroku 3.  

2.  Na **ogólne** pozycję Zakończ konfigurację lasu, który chcesz odnaleźć i określ **konto lasu usługi Active Directory**.  

    > [!NOTE]  
    >  Aby odnajdywać lasy niezaufane i w nich publikować, odnajdywanie lasu usługi Active Directory wymaga konta globalnego. Jeśli nie używasz konta komputera serwera lokacji, można wybrać tylko konto globalne.  

3.  Jeśli zamierzasz umożliwić publikowanie danych lokacji w tym lesie na Lokacje **publikowania** pozycję Zakończ konfigurację publikowania w tym lesie.  

    > [!NOTE]  
    >  Jeśli umożliwisz lokacji publikowanie w lesie, należy rozszerzyć schemat usługi Active Directory tego lasu dla programu Configuration Manager. Konto lasu usługi Active Directory musi mieć uprawnienia pełnej kontroli do kontenera systemu w tym lesie.  

4.  Po zakończeniu konfiguracji tego lasu do stosowania z odnajdywaniem lasu usługi Active Directory, wybierz **OK** Aby zapisać konfigurację.  

##  <a name="BKMK_ConfigADDiscGeneral"></a>Konfigurowanie odnajdywania usługi Active Directory dla komputerów, użytkowników lub grup  
 Skorzystaj z informacji w poniższych sekcjach, aby skonfigurować odnajdywanie komputerów, użytkowników lub grup. Użyjesz tych metod odnajdywania:  

-   Odnajdywanie grupy usługi Active Directory  

-   Odnajdywanie systemu usługi Active Directory  

-   odnajdywanie użytkownika usługi Active Directory  

> [!NOTE]  
>  Informacje przedstawione w tej sekcji nie dotyczą odnajdywania lasu usługi Active Directory.  

 Mimo że każda z tych metod odnajdywania jest niezależna od innych, mają podobne opcje. Aby uzyskać więcej informacji o tych opcjach konfiguracji, zobacz [udostępniane opcje odnajdywania grupy, systemu i użytkownika](../../../../core/servers/deploy/configure/about-discovery-methods.md#bkmk_shared).  

> [!WARNING]  
>  Sondowanie usługi Active Directory każdą z tych metod odnajdywania może powodować znaczne obciążenie sieci. Warto pomyśleć o zaplanowaniu każdej metody odnajdywania w czasie, gdy ruch sieciowy nie wpływa na firm korzystanie z sieci.  

#### <a name="to-configure-active-directory-group-discovery"></a>Aby skonfigurować odnajdywanie grupy usługi Active Directory  

1.  W konsoli programu Configuration Manager wybierz **administracji** > **Konfiguracja hierarchii**, a następnie wybierz pozycję **metod odnajdywania**.  

2.  Wybierz **odnajdowanie grup usługi Active Directory** metodę dla lokacji, w której chcesz skonfigurować odnajdywanie.  

3.  Na **Home** karcie **właściwości** grupy, wybierz **właściwości**.  

4.  Na **ogólne** karcie, pole wyboru, aby włączyć odnajdywanie. Lub skonfigurować odnajdywanie teraz, a następnie włączyć je później.  

5.  Wybierz **Dodaj** do skonfigurowania zakresu odnajdywania, wybierz **grup** lub **lokalizacji**i Zakończ następujące konfiguracje w **Dodawanie grup** lub **Dodawanie lokalizacji usługi Active Directory** okno dialogowe:  

    1.  Określ **nazwa** dla tego zakresu odnajdywania.  

    2.  Określ **domeny usługi Active Directory** lub **lokalizacji** do wyszukania:  

        -   Jeśli została wybrana opcja **grup**, określ jedną lub więcej grup usługi Active Directory do odnalezienia.  

        -   Jeśli została wybrana opcja **lokalizacji**, określ kontener usługi Active Directory jako lokalizację do odnalezienia. Można również włączyć wyszukiwanie cykliczne we wszystkich kontenerach podrzędnych usługi Active Directory dla tej lokalizacji.  

    3.  Określ **konto odnajdywania grup usługi Active Directory** używane do przeszukiwania tego zakresu odnajdywania.  

    4.  Wybierz **OK** Aby zapisać konfigurację zakresu odnajdywania.  

6.  Powtórz krok 6 dla każdego dodatkowego zakresu odnajdywania, który chcesz zdefiniować.  

7.  Na **harmonogram sondowania** skonfiguruj zarówno sondowania pełnego odnajdywania, harmonogram i odnajdywanie zmian.  

8.  Opcjonalna metoda polega na **opcji** kartę, można skonfigurować opcje odfiltrowywania, czyli wykluczania starych rekordów z procesu odnajdywania i odnajdywania członkostwa w grupach dystrybucyjnych.  

    > [!NOTE]  
    >  Domyślnie odnajdywanie grupy usługi Active Directory odnajduje tylko członkostwo grup zabezpieczeń.  

9. Po zakończeniu konfigurowania odnajdywania grupy usługi Active Directory dla tej lokacji wybrać **OK** Aby zapisać konfigurację.  

#### <a name="to-configure-active-directory-system-discovery"></a>Aby skonfigurować odnajdywanie systemu usługi Active Directory  

1.  W konsoli programu Configuration Manager wybierz **administracji** > **Konfiguracja hierarchii**, a następnie wybierz pozycję **metod odnajdywania**.  

2.  Wybierz metodę dla lokacji, w której chcesz skonfigurować odnajdywanie.  

3.  Na **Home** karcie **właściwości** grupy, wybierz **właściwości**.  

4.  Na **ogólne** karcie, pole wyboru, aby włączyć odnajdywanie. Lub skonfigurować odnajdywanie teraz, a następnie włączyć je później.  

5.  Wybierz **nowy** ikona ![nową ikonę](media/Disc_new_Icon.gif) Aby określić nowy kontener usługi Active Directory. W **kontener usługi Active Directory** okna dialogowego pozycję Zakończ następujące konfiguracje:  

    1.  Określ co najmniej jedna lokalizacja do wyszukiwania.  

    2.  Dla każdej lokalizacji określ opcje, które należy zmienić to zachowanie wyszukiwania.  

    3.  Dla każdej lokalizacji określ konto do użycia jako **konto odnajdywania usługi Active Directory**.  

        > [!TIP]  
        >  Dla każdej lokalizacji można skonfigurować zestaw opcji odnajdywania i unikatowe konto odnajdywania Active Directory.  

    4.  Wybierz **OK** Aby zapisać konfigurację kontenera usługi Active Directory.  

6.  Na **harmonogram sondowania** skonfiguruj zarówno sondowania pełnego odnajdywania, harmonogram i odnajdywanie zmian.  

7.  Opcjonalna metoda polega na **atrybuty usługi Active Directory** kartę, można skonfigurować dodatkowe atrybuty usługi Active Directory dla komputerów, które chcesz odnajdywać. Są także wyświetlane domyślne atrybuty obiektów.  

8.  Opcjonalna metoda polega na **opcji** kartę, można skonfigurować opcje odfiltrowywania, czyli wykluczania starych rekordów z procesu odnajdywania.  

9. Po zakończeniu konfigurowania odnajdywania systemu usługi Active Directory dla tej lokacji wybrać **OK** Aby zapisać konfigurację.  

#### <a name="to-configure-active-directory-user-discovery"></a>Aby skonfigurować odnajdowanie użytkowników usługi Active Directory  

1.  W konsoli programu Configuration Manager wybierz **administracji** > **Konfiguracja hierarchii**, a następnie wybierz pozycję **metod odnajdywania**.  

2.  Wybierz **odnajdywania użytkownika usługi Active Directory** metodę dla lokacji, w której chcesz skonfigurować odnajdywanie.  

3.  Na **Home** karcie **właściwości** grupy, wybierz **właściwości**.  

4.  Na **ogólne** karcie, pole wyboru, aby włączyć odnajdywanie. Lub skonfigurować odnajdywanie teraz, a następnie włączyć je później.  

5.  Wybierz **nowy** ikona ![nową ikonę](media/Disc_new_Icon.gif) Aby określić nowy kontener usługi Active Directory. W **kontener usługi Active Directory** okna dialogowego pozycję Zakończ następujące konfiguracje:  

    1.  Określ co najmniej jedna lokalizacja do wyszukiwania.  

    2.  Dla każdej lokalizacji określ opcje, które należy zmienić to zachowanie wyszukiwania.  

    3.  Dla każdej lokalizacji określ konto do użycia jako **konto odnajdywania usługi Active Directory**.  

        > [!NOTE]  
        >  Dla każdej lokalizacji można skonfigurować unikatowy zestaw opcji odnajdywania i unikatowe konto odnajdywania Active Directory.  

    4.  Wybierz **OK** Aby zapisać konfigurację kontenera usługi Active Directory.  

6.  Na **harmonogram sondowania** skonfiguruj zarówno sondowania pełnego odnajdywania, harmonogram i odnajdywanie zmian.  

7.  Opcjonalna metoda polega na **atrybuty usługi Active Directory** kartę, można skonfigurować dodatkowe atrybuty usługi Active Directory dla komputerów, które chcesz odnajdywać. Są także wyświetlane domyślne atrybuty obiektów.  

8.  Po zakończeniu konfigurowania odnajdywania użytkownika usługi Active Directory dla tej lokacji wybrać **OK** Aby zapisać konfigurację.  

## <a name="azureaadisc"></a>Konfigurowanie odnajdywania użytkownika usługi Azure AD
Począwszy od wersji 1706, można skonfigurować odnajdowanie użytkowników usługi Active Directory Azure podczas łączenia programu Configuration Manager do Twojej [subskrypcji platformy Azure i usługi Azure Active Directory](/sccm/core/servers/deploy/configure/azure-services-wizard).

Odnajdowanie użytkowników usługi Azure AD jest skonfigurowany jako część *zarządzania chmurą*. Procedury w tym celu została szczegółowo opisana w [tworzenie aplikacji sieci web platformy Azure do użytku w programie Configuration Manager](/sccm/core/servers/deploy/configure/Azure-services-wizard#webapp) w temacie *usług Azure skonfigurować do użytku z programem Configuration Manager*.




##  <a name="BKMK_ConfigHBDisc"></a>Konfigurowanie odnajdywania pulsu  
 Domyślnie odnajdywanie pulsu jest włączane podczas instalowania lokacji głównej programu Configuration Manager. W związku z tym wystarczy tylko skonfigurować harmonogram jak często klienci wysyłania danych odnajdywania pulsu rekordów z punktem zarządzania, jeśli nie chcesz użyć wartości domyślnej co siedem dni.  

> [!NOTE]  
>  Jeśli zarówno wypychana instalacja klienta, jak i obsługi lokacji zadanie **Wyczyść flagę instalacji** są włączone w tej samej lokacji, ustawić harmonogram odnajdywania pulsu należy mniejszej niż **okres ponownego odnajdywania klienta** z **Wyczyść flagę instalacji** zadanie obsługi lokacji. Aby uzyskać więcej informacji na temat zadań konserwacji lokacji, zobacz [zadania konserwacji programu System Center Configuration Manager](../../../../core/servers/manage/maintenance-tasks.md).  

#### <a name="to-configure-the-heartbeat-discovery-schedule"></a>Aby skonfigurować harmonogram odnajdywania pulsu  

1.  W konsoli programu Configuration Manager wybierz **administracji** > **Konfiguracja hierarchii**, a następnie wybierz pozycję **metod odnajdywania**.  

2.  Wybierz **odnajdywania pulsu** dla witryny, w której chcesz skonfigurować odnajdywanie pulsu.  

3.  Na **Home** karcie **właściwości** grupy, wybierz **właściwości**.  

4.  Skonfiguruj częstotliwość, z jaką klienci przesłali rekordu danych odnajdywania pulsu, a następnie wybierz **OK** Aby zapisać konfigurację.  

##  <a name="BKMK_ConfigNetworkDisc"></a>Konfigurowanie odnajdywania sieci  
 Skorzystaj z informacji w poniższych sekcjach ułatwiają konfigurowanie odnajdywania sieci.  

###  <a name="BKMK_AboutConfigNetworkDisc"></a>Informacje o konfigurowaniu odnajdywania sieci  
 Przed rozpoczęciem konfigurowania odnajdywania sieci, należy zrozumieć następujące kwestie:  

-   Dostępne poziomy odnajdywania sieci  

-   Dostępne opcje odnajdywania sieci  

-   Ograniczanie odnajdywania sieci w sieci  

Aby uzyskać więcej informacji, zobacz [o odnajdywania sieci](../../../../core/servers/deploy/configure/about-discovery-methods.md#bkmk_aboutNetwork).  

 Poniższe sekcje zawierają informacje o popularnych konfiguracjach odnajdywania sieci. Można skonfigurować jeden lub więcej z tych konfiguracji do użycia podczas odnajdowania tego samego uruchomienia. Jeśli używasz wielu konfiguracji należy zaplanować interakcje, które mogą wpłynąć na wyniki odnajdywania.  

 Na przykład możesz chcieć odnaleźć wszystkie urządzenia zarządzania protokołu SNMP (Simple Network), używające określonej nazwy wspólnoty SNMP. Ponadto na tym samym uruchomieniu odnajdywania można wyłączyć odnajdywanie w określonej podsieci. Podczas odnajdywania odnajdywania sieci nie odnajdzie urządzeń SNMP o określonej nazwie Wspólnoty w podsieci, która została wyłączona.  

####  <a name="BKMK_DetermineNetTopology"></a>Ustalenie topologii sieci  
 Odnajdowanie tylko topologii służy do mapowania sieci. Ten rodzaj odnajdywania nie odnajduje potencjalnych klientów. Tylko topologii odnajdowania sieci korzysta z protokołu SNMP.  

 W przypadku mapowania topologii sieci, należy skonfigurować **maksymalna liczba przeskoków** na **SNMP** karcie **odnajdowanie sieci: właściwości** okno dialogowe. Wystarczy kilka przeskoków, aby pomóc kontroli przepustowości sieci, który jest używany podczas odnajdywania. W miarę odnajdywania dalszych obszarów sieci, można zwiększyć liczbę przeskoków w celu uzyskania lepszej orientacji w topologii sieci.  

 Po zidentyfikowaniu topologii sieci można skonfigurować dodatkowe właściwości odnajdywania sieci w celu odnalezienia potencjalnych klientów i ich systemy operacyjne, podczas używania dostępnych konfiguracji do ograniczania segmentów sieci, które odnajdywanie sieci może przeszukiwać.  

####  <a name="BKMK_LimitBySubnet"></a>Ograniczanie wyszukiwań za pomocą podsieci  
 Można skonfigurować odnajdywanie sieci w celu przeszukiwania określonych podsieci podczas odnajdywania. Domyślnie funkcja odnajdowania sieci przeszukuje podsieć serwera, na którym działa odnajdywanie. Dodatkowe podsieci, które można skonfigurować i włączyć mają zastosowanie tylko do protokołu SNMP protokołu dynamicznej konfiguracji hosta (DHCP) opcje wyszukiwania. Gdy funkcja odnajdowania sieci przeszukuje domeny, nie jest ograniczone konfiguracjami dotyczącymi podsieci.  

 W przypadku określenia co najmniej jednej podsieci **podsieci** karcie **odnajdowanie sieci: właściwości** okno dialogowe, tylko podsieci oznaczone jako **włączone** są przeszukiwane.  

 Po wyłączeniu podsieci jest ona wykluczana z odnajdywania i mają zastosowanie następujące warunki:  

-   W podsieci nie są uruchamiane zapytania oparte na protokole SNMP.  

-   Serwery DHCP nie odpowiadają wyświetleniem listy zasobów znajdujących się w podsieci.  

-   Zapytania oparte na domenie umożliwia odnalezienie zasobów, które znajdują się w podsieci.  

####  <a name="BKMK_SearchByDomain"></a>Przeszukiwanie określonej domeny  
 Można skonfigurować odnajdywanie sieci w celu przeszukania określonej domeny lub zestawu domen podczas pracy odnajdywania. Domyślnie funkcja odnajdowania sieci przeszukuje lokalną domenę serwera, na którym działa odnajdywanie.  

 Po określeniu jednej lub kilku domen na **domen** karcie **odnajdowanie sieci: właściwości** okno dialogowe, tylko domeny oznaczone jako **włączone** są przeszukiwane.  

 Po wyłączeniu domeny jest wykluczana z odnajdywania i mają zastosowanie następujące warunki:  

-   Odnajdywania sieci nie odpytuje kontrolerów domeny w tej domenie.  

-   Zapytania oparte na protokole SNMP mogą nadal działać w podsieci w domenę.  

-   Serwery DHCP nadal mogą odpowiedzieć listę zasobów znajdujących się w domenie.  

####  <a name="BKMK_LimitBySNMPname"></a>Ograniczanie wyszukiwań za pomocą nazw wspólnot SNMP  
 Możesz skonfigurować odnajdywanie sieci w celu przeszukania określonej Wspólnoty SNMP lub zestawów Wspólnot podczas pracy odnajdywania. Domyślnie nazwa Wspólnoty **publicznego** jest skonfigurowana do użycia.  

 Funkcja odnajdowania sieci korzysta z nazw Wspólnot w celu uzyskania dostępu do routerów, które są urządzeniami SNMP. Router może udostępnić funkcji odnajdowania sieci informacje o innych routerach i podsieciach połączonych z pierwszym routerem.  

> [!NOTE]  
>  Nazwy wspólnot SNMP przypominają hasła. Funkcja odnajdowania sieci informacji można uzyskać tylko z urządzenia SNMP, dla którego określono nazwę Wspólnoty. Każde urządzenie SNMP może mieć własną nazwę Wspólnoty, ale często jest udostępniany tej samej nazwy Wspólnoty korzysta kilka urządzeń. Ponadto większość urządzeń SNMP ma domyślną nazwę Wspólnoty **publicznego**. Niektóre organizacje usuwania **publicznego** nazwę Wspólnoty ze swoich urządzeń w celu zapewnienia bezpieczeństwa.  

 Jeśli kilka Wspólnot SNMP są pokazywane na **SNMP** karcie **odnajdowanie sieci: właściwości** okno dialogowe, funkcja odnajdowania sieci przeszukuje je w kolejności, w którym są wyświetlane. Aby zminimalizować ruch sieciowy, który jest generowany przez próby połączenia z urządzeniem przy użyciu różnych nazw, upewnij się, że najczęściej używane nazwy znajdowały się u góry listy.  

> [!NOTE]  
>  Oprócz przy użyciu nazwy wspólnoty SNMP, możesz określić adres IP lub rozpoznawalną nazwę urządzenia SNMP. Możesz to zrobić na **urządzeń SNMP** karcie **odnajdowanie sieci: właściwości** okno dialogowe.  

####  <a name="BKMK_SearchByDHCP"></a>Przeszukiwanie określonego serwera DHCP  
 Można skonfigurować odnajdywania sieci do używania określonego serwera DHCP lub wiele serwerów do odnajdywania klientów DHCP podczas pracy odnajdywania.  

 Funkcja odnajdowania sieci przeszukuje każdy serwer DHCP, który określisz na **DHCP** karcie **odnajdowanie sieci: właściwości** okno dialogowe. Jeśli serwer, na którym działa odnajdywanie wydzierżawi swój adres IP od serwera DHCP, można skonfigurować odnajdywanie do przeszukania tego serwera DHCP, zaznaczając **Dołącz serwer DHCP, który serwer lokacji jest skonfigurowany do użycia** pole.  

> [!NOTE]  
>  Aby pomyślnie skonfigurować serwer DHCP w ramach odnajdywania sieci, środowisko musi obsługiwać protokół IPv4. Nie można skonfigurować odnajdowania sieci w celu korzystania z serwera DHCP w macierzystym środowisku IPv6.  

###  <a name="BKMK_HowToConfigNetDisc"></a>Jak skonfigurować odnajdywanie sieci  
 Poniższe procedury umożliwiają najpierw wykrycie tylko topologii sieci, a następnie skonfigurowanie funkcji odnajdowania sieci w celu odnalezienia potencjalnych klientów przy użyciu co najmniej jeden z dostępnych opcji odnajdowania sieci.  

##### <a name="to-determine-your-network-topology"></a>Ustalenie topologii sieci  

1.  W konsoli programu Configuration Manager wybierz **administracji** > **Konfiguracja hierarchii**, a następnie wybierz pozycję **metod odnajdywania**.  

2.  Wybierz **odnajdywania sieci** dla lokacji, na którym chcesz uruchomić odnajdowanie sieci.  

3.  Na **Home** karcie **właściwości** grupy, wybierz **właściwości**.  

    -   Na **ogólne** karcie wyboru **Włącz odnajdowanie sieci** polu, a następnie wybierz pozycję **topologii** z **typ odnajdowania** opcje.  

    -   Na **podsieci** karcie wyboru **przeszukiwania podsieci lokalnej** pole.  

        > [!TIP]  
        >  Jeśli znasz określonych podsieci, które tworzą używaną sieć, można usunąć zaznaczenie **przeszukiwania podsieci lokalnej** polu i użyj **nowy** ikona ![nową ikonę](media/Disc_new_Icon.gif) można dodać podsieci do przeszukania. W przypadku dużych sieci warto często przeszukiwania tylko jednego lub dwóch podsieci naraz w celu zminimalizowania użycia przepustowości sieci.  

    -   Na **domen** karcie wyboru **Przeszukaj domenę lokalną** pole.  

    -   Na **SNMP** użyj **maksymalna liczba przeskoków** listy rozwijanej, aby określić liczbę przeskoków odnajdowania sieci może wykonać podczas mapowania topologii.  

        > [!TIP]  
        >  Przed pierwszym mapowaniem topologii sieci, należy skonfigurować tylko kilka przeskoków, aby zminimalizować wykorzystanie przepustowości sieci.  

4.  Na **harmonogram** , wybierz pozycję **nowy** ikona ![nową ikonę](media/Disc_new_Icon.gif) Aby ustawić harmonogram uruchamiania funkcji odnajdowania sieci.  

    > [!NOTE]  
    >  Nie można przypisać różnych konfiguracji odnajdywania do oddzielnych harmonogramów funkcji odnajdowania sieci. Każdym uruchomieniu funkcja odnajdowania sieci korzysta z bieżącej konfiguracji odnajdywania.  

5.  Wybierz **OK** aby zaakceptować konfiguracje. Funkcja odnajdywania sieci działa w zaplanowanym terminie.  

##### <a name="to-configure-network-discovery"></a>Aby skonfigurować odnajdywanie sieci  

1.  W konsoli programu Configuration Manager wybierz **administracji** > **Konfiguracja hierarchii**, a następnie wybierz pozycję **metod odnajdywania**.  

2.  Wybierz **odnajdywania sieci** dla lokacji, na którym chcesz uruchomić odnajdowanie sieci.  

3.  Na **Home** karcie **właściwości** grupy, wybierz **właściwości**.  

4.  Na **ogólne** karcie wyboru **Włącz odnajdowanie sieci** , a następnie wybierz typ odnajdywania, która ma zostać uruchomione z **typ odnajdowania** opcje.  

5.  Aby skonfigurować odnajdywanie w celu przeszukiwania podsieci, wybierz **podsieci** karcie, a następnie skonfiguruj jedną lub więcej z następujących opcji:  

    -   Aby uruchomić odnajdywanie w podsieciach lokalnych dla komputera, na którym działa odnajdywanie, zaznacz **przeszukiwania podsieci lokalnej** pole.  

    -   Aby przeszukać określoną podsieć, upewnij się, że podsieci jest wymieniony w **podsieci do przeszukania** i ma **wyszukiwania** wartość **włączone**:  

        1.  Jeżeli podsieć nie jest widoczna na liście, wybierz **nowy** ikona ![nową ikonę](media/Disc_new_Icon.gif). W **nowe przypisanie podsieci** okna dialogowego wprowadź **podsieci** i **maski** informacje, a następnie wybierz pozycję **OK**. Domyślnie nowa podsieć jest włączona do przeszukiwania.  

        2.  Aby zmienić **wyszukiwania** wartość dla podsieci widocznej na liście, wybierz podsieć, a następnie wybierz **Przełącz** ikonę, aby przełączyć między wartością **wyłączone** i **włączone**.  

6.  Aby skonfigurować odnajdywanie w celu przeszukiwania domen, należy wybrać **domen** karcie, a następnie skonfiguruj jedną lub więcej z następujących opcji:  

    -   Aby uruchomić odnajdywanie w domenie komputera, na którym działa odnajdowanie, zaznacz **Przeszukaj domenę lokalną** pole.  

    -   Aby przeszukać określoną domenę, upewnij się, że domeny jest wymieniony w **domen** i ma **wyszukiwania** wartość **włączone**:  

        1.  Jeśli domena nie jest widoczna na liście, wybierz **nowy** ikona ![nową ikonę](media/Disc_new_Icon.gif). W **właściwości domeny** okna dialogowego wprowadź **domeny** informacje, a następnie wybierz pozycję **OK**. Domyślnie nowa domena jest włączona do przeszukiwania.  

        2.  Aby zmienić **wyszukiwania** wartość dla domeny widocznej na liście, wybierz domenę, a następnie wybierz pozycję **Przełącz** ikonę, aby przełączyć między wartością **wyłączone** i **włączone**.  

7.  Aby skonfigurować odnajdywanie w celu przeszukiwania nazw wspólnot SNMP dla urządzeń SNMP, wybierz **SNMP** karcie, a następnie skonfiguruj jedną lub więcej z następujących opcji:  

    -   Aby dodać nazwę wspólnoty SNMP do listy **nazw wspólnot SNMP**, wybierz **nowy** ikona ![nową ikonę](media/Disc_new_Icon.gif). W **Nowa nazwa wspólnoty SNMP** oknie dialogowym Określ **nazwa** Wspólnoty SNMP, a następnie wybierz pozycję **OK**.  

    -   Aby usunąć nazwę wspólnoty SNMP, wybierz nazwę Wspólnoty, a następnie wybierz pozycję **usunąć** ikona ![ikonę Usuń](media/Disc_delete_Icon.gif).  

    -   Aby dostosować kolejność przeszukiwania nazw wspólnot SNMP, wybierz nazwę Wspólnoty, a następnie wybierz pozycję **Przenieś element w górę** ikona ![Przenieś ikonę](media/Disc_moveUp_Icon.gif) lub **Przenieś element w dół** ikona ![Przenieś ikonę](media/Disc_moveDown_Icon.gif). Po uruchomieniu odnajdywania nazwy Wspólnot są przeszukiwane w kolejności od góry do dołu. Następujące kwestie należy wziąć pod uwagę.

        > [!NOTE]  
        >  Funkcja odnajdowania sieci korzysta z nazw wspólnot SNMP do uzyskania dostępu do routerów, które są urządzeniami SNMP. Router może przekazać funkcji odnajdowania sieci o innych routerach i podsieciach połączonych z pierwszym routerem.  

        -   Nazwy wspólnot SNMP przypominają hasła.  

        -   Funkcja odnajdowania sieci informacji można uzyskać tylko z urządzenia SNMP, dla którego określono nazwę Wspólnoty.  

        -   Każde urządzenie SNMP może mieć własną nazwę Wspólnoty, ale często jest udostępniany tej samej nazwy Wspólnoty korzysta kilka urządzeń.  

        -   Większość urządzeń SNMP ma domyślną nazwę Wspólnoty **publicznego**. Można go używać, jeśli nie znasz inne nazwy Wspólnot. Jednak niektóre organizacje usunąć **publicznego** nazwę Wspólnoty ze swoich urządzeń w celu zapewnienia bezpieczeństwa.  

8.  Aby skonfigurować maksymalną liczbę przeskoków między routerami używany przez wyszukiwania SNMP, wybierz **SNMP** , a następnie wybierz liczbę przeskoków z **maksymalna liczba przeskoków** listy rozwijanej.  

9. Aby skonfigurować urządzenia SNMP, wybierz **urządzeń SNMP** kartę. Jeśli urządzenie nie znajduje się tam, wybierz **nowy** ikona ![nową ikonę](media/Disc_new_Icon.gif). W **nowe urządzenie SNMP** okno dialogowe, określ adres IP lub urządzenie nazwę urządzenia SNMP, a następnie wybierz **OK**.  

    > [!NOTE]  
    >  Określenia nazwy urządzenia, programu Configuration Manager musi być w stanie rozpoznać nazwę NetBIOS na adres IP.  

10. Aby skonfigurować odnajdywanie w celu odpytywania określonych serwerów DHCP dla klientów DHCP, wybierz **DHCP** karcie, a następnie skonfiguruj jedną lub więcej z następujących opcji:  

    -   Aby odpytać serwer DHCP na komputerze, na którym działa odnajdowanie, zaznacz **zawsze używaj serwer DHCP serwera lokacji** pole.  

        > [!NOTE]  
        >  Aby użyć tej opcji, serwer musi wydzierżawić swój adres IP od serwera DHCP i nie może używać statycznego adresu IP.  

    -   Aby odpytać określony serwer DHCP, należy wybrać **nowy** ikona ![nową ikonę](media/Disc_new_Icon.gif). W **nowy serwer DHCP** okno dialogowe, określ adres IP lub serwera nazwę serwera DHCP, a następnie wybierz **OK**.  

        > [!NOTE]  
        >  Jeśli określono nazwę serwera, programu Configuration Manager musi być w stanie rozpoznać nazwę NetBIOS na adres IP.  

11. Aby skonfigurować czas uruchamiania wyszukiwania, wybierz **harmonogram** karcie, a następnie wybierz pozycję **nowy** ikona ![nową ikonę](media/Disc_new_Icon.gif) Aby ustawić harmonogram uruchamiania funkcji odnajdowania sieci.  

     Można skonfigurować kilka harmonogramów cyklicznych i kilka harmonogramów bez cyklu.  

    > [!NOTE]  
    >  Jeśli wiele harmonogramów są pokazywane na **harmonogram** kartę w tym samym czasie wszystkich harmonogramów odnajdowania sieci działa dla zgodnie z konfiguracją o godzinie określonej w harmonogramie. Dotyczy to również harmonogramów cyklicznych.  

12. Wybierz **OK** Aby zapisać konfiguracje.  

###  <a name="BKMK_HowToVerifyNetDisc"></a>Jak sprawdzić, czy odnajdywanie sieci zostało zakończone  
 Czas odnajdowania sieci wymaga, aby zakończyć zależy od różnych czynników. Czynniki te mogą obejmować co najmniej jeden z następujących czynności:  

-   Rozmiar sieci  

-   Topologia sieci  

-   Maksymalna liczba przeskoków skonfigurowanych do znalezienia routerów w sieci  

-   Typ odnajdywania, które zostało uruchomione  

Ponieważ funkcja odnajdowania sieci nie tworzy komunikatów powiadamiających o zakończeniu odnajdowania, służy poniższej procedury można zweryfikować, czy odnajdowanie zostało zakończone.  

##### <a name="to-verify-that-network-discovery-has-finished"></a>Aby sprawdzić, czy odnajdywanie sieci zostało zakończone  

1.  W konsoli programu Configuration Manager wybierz **monitorowanie**.  

2.  W **monitorowanie** obszaru roboczego, rozwiń węzeł **stan systemu**, a następnie wybierz pozycję **kwerendy komunikatów o stanie**.  

3.  Wybierz **wszystkie komunikaty o stanie**.  

4.  Na **Home** karcie **kwerendy komunikatów o stanie** grupy, wybierz **Pokaż komunikaty**.  

5.  W **wybierz datę i godzinę** listy rozwijanej, wybierz wartość zawierającą czas przed rozpoczęto odnajdowanie, a następnie wybierz **OK** otworzyć **Podgląd komunikatów o stanie Menedżera konfiguracji**.  

    > [!TIP]  
    >  Można również użyć **Określ datę i godzinę** opcję, aby wybrać daną datę i godzinę uruchomienia odnajdowania. Ta opcja jest przydatne w przypadku uruchomienia odnajdowania sieci danego dnia i chcesz pobierać wiadomości z tylko tej daty.  

6.  Aby sprawdzić, czy odnajdywanie sieci zostało zakończone, wyszukaj komunikat o stanie zawierający następujące informacje:  

    -   Identyfikator komunikatu: **502**  

    -   Składnik: **SMS_NETWORK_DISCOVERY**  

    -   Opis: **Ten składnik został zatrzymany**  

    Jeśli ten komunikat o stanie nie jest obecny, funkcja odnajdywania sieci nie zostało ukończone.  

7.  Aby sprawdzić, gdy uruchomienie funkcji odnajdowania sieci, wyszukaj komunikat o stanie zawierający następujące informacje:  

    -   Identyfikator komunikatu: **500**  

    -   Składnik: **SMS_NETWORK_DISCOVERY**  

    -   Opis: **Ten składnik został rozpoczęty**  

    Te informacje oznaczają uruchomienie funkcji odnajdowania sieci. Jeśli te informacje nie jest obecny, harmonogram odnajdywania sieci.  
