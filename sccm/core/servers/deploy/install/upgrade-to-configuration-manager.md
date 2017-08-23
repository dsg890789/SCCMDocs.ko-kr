---
title: Uaktualnianie do programu System Center Configuration Manager | Dokumentacja firmy Microsoft
description: "Dowiedz się więcej czynności umożliwiające uruchamianie pomyślne uaktualnienie w miejscu lokacji i hierarchii programu System Center 2012 Configuration Manager."
ms.custom: na
ms.date: 6/6/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: c64e7483-b4bb-4738-95f4-ecdaeb6a2ba6
caps.latest.revision: "21"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 1166b739e1e8d667172d97883f484fdbc3a142c1
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="upgrade-to-system-center-configuration-manager"></a>Uaktualnianie do programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Można uruchomić uaktualnienia i uaktualnienia w miejscu do programu System Center Configuration Manager z lokacji i hierarchii programu System Center 2012 Configuration Manager.  

 Przed rozpoczęciem uaktualniania programu System Center 2012 Configuration Manager, należy przygotować Lokacje wymagające usunięcia konkretnych konfiguracji, które mogą uniemożliwiać pomyślne uaktualnienie, a następnie wykonaj sekwencji uaktualniania, gdy jest używany więcej niż jednej lokacji.  

 > [!TIP]
 > Podczas zarządzania w lokacji programu System Center Configuration Manager i infrastruktury hierarchii, warunki *uaktualnienia*, *aktualizacji*, i *zainstalować* służą do opisywania trzy oddzielne pojęcia. Aby dowiedzieć się, jak każdego terminu jest używany, zobacz [o uaktualnienie, aktualizacji i instalacji](/sccm/core/understand/upgrade-update-install).

##  <a name="bkmk_path"></a> Ścieżki uaktualnienia w miejscu  

**Uaktualnienie do wersji 1702**   
Jeśli masz nośnika linii bazowej 1702 wersji możesz uaktualnić następujące do pełni licencjonowanej wersji programu System Center Configuration Manager wersji 1702:   
-     Instalacja ewaluacyjna programu System Center Configuration Manager wersji 1702
-     System Center 2012 Configuration Manager z dodatkiem Service Pack 1
-     System Center 2012 Configuration Manager z dodatkiem Service Pack 2
-     System Center 2012 R2 Configuration Manager
-     System Center 2012 R2 Configuration Manager z dodatkiem Service Pack 1

**Uaktualnienie do wersji 1606**  
Na 15 grudnia 2016 wydano nośnika linii bazowej dla wersji 1606, aby dodać obsługę dodatkowych scenariuszy uaktualniania. Nowe wydanie obsługuje uaktualnienie następujące polecenie, aby w pełni licencjonowanej wersji programu System Center Configuration Manager wersji 1606:  
-   Instalacja ewaluacyjna programu System Center Configuration Manager wersji 1606
-   Instalacja wersji release candidate programu System Center Configuration Manager  
-   System Center 2012 Configuration Manager z dodatkiem Service Pack 1  
-   System Center 2012 Configuration Manager z dodatkiem Service Pack 2  
-   System Center 2012 R2 Configuration Manager  
-   System Center 2012 R2 Configuration Manager z dodatkiem Service Pack 1  

Jeśli używasz wersji linii bazowej 1606 nośnika pobrane przed 15 grudnia 2016 do pełni licencjonowanej wersji programu System Center Configuration Manager wersji 1606 można uaktualnić tylko następujące:
-   Instalacja ewaluacyjna programu System Center Configuration Manager wersji 1606
-   System Center 2012 Configuration Manager z dodatkiem Service Pack 2
-   System Center 2012 R2 Configuration Manager z dodatkiem Service Pack 1

<!-- Version 1511 has now dropped out of support
**Upgrade to version 1511**  
When you have version 1511 baseline media, you can upgrade the following to a fully licensed  version of System Center Configuration Manager version 1511:  
-   An evaluation install of System Center Configuration Manager version 1511
-   A release candidate install of System Center Configuration Manager  
-   System Center 2012 Configuration Manager with Service Pack 1  
-   System Center 2012 Configuration Manager with Service Pack 2  
-   System Center 2012 R2 Configuration Manager  
-   System Center 2012 R2 Configuration Manager with Service Pack 1  
-->


> [!TIP]  
>  Po uaktualnieniu z wersji System Center 2012 Configuration Manager do bieżącej gałęzi może być usprawnić proces uaktualniania. Aby uzyskać więcej informacji, zobacz następujące tematy:  
>   
>  -   Sekcja [Wersje linii bazowej i aktualizacji](../../../../core/servers/manage/updates.md#bkmk_Baselines) w temacie [Aktualizacje programu System Center Configuration Manager](../../../../core/servers/manage/updates.md)  
>  -   [Dysk CD. Najnowszy folder programu System Center Configuration Manager](../../../../core/servers/manage/the-cd.latest-folder.md)  

 **Nie są obsługiwane następujące scenariusze:**  
-   Uaktualnienie programu System Center Configuration Manager Technical Preview do w pełni licencjonowanej instalacji nie jest obsługiwane.  Wersja Technical Preview może zostać uaktualniona tylko do nowszej wersji Technical Preview.  

-   Migracja z wersji Technical Preview do w pełni licencjonowanej wersji nie jest obsługiwana.  

##  <a name="bkmk_checklist"></a> Listy kontrolne uaktualniania  
 Na poniższych listach wyboru ułatwiają zaplanowanie pomyślnego uaktualnienia do programu System Center Configuration Manager.  

### <a name="before-you-upgrade"></a>Przed uaktualnieniem  

**Przegląd środowiska System Center 2012 Configuration Manager** i rozwiązywanie problemów dotyczących zgodnie z opisem w KB4018655: [Klientów programu Configuration Manager z powodu cyklicznego zadania spróbuj ponownie zainstalować ponownie co pięć godzin i może spowodować uaktualnienie klienta przypadkowej](https://support.microsoft.com/help/4018655).

**Upewnij się, że środowisko przetwarzania danych spełnia wymagania dotyczące obsługiwanych konfiguracji** są niezbędne do uaktualnienia do programu System Center Configuration Manager:  

Sprawdź systemy operacyjne serwerów używane do hostowania ról systemu lokacji:  

-   Niektóre starsze systemy operacyjne obsługiwane przez System Center 2012 Configuration Manager nie są obsługiwane przez program System Center Configuration Manager, a role systemu lokacji w tych systemach operacyjnych należy przenieść lub usunąć przed przeprowadzeniem uaktualnienia. Przegląd [systemy operacyjne obsługiwane przez serwery systemu lokacji](../../../../core/plan-design/configs/supported-operating-systems-for-site-system-servers.md) dokumentacji.   
-   Narzędzie sprawdzania wymagań wstępnych dla programu Configuration Manager nie weryfikuje wymagań wstępnych dotyczących ról systemu lokacji na serwerze lokacji lub na zdalnych systemów lokacji  

Sprawdź wymagania wstępne dla wszystkich komputerów hostujących role systemu lokacji:  

-   Na przykład aby wdrożyć system operacyjny, System Center Configuration Manager korzysta z systemu Windows 10 Assessment and Deployment Kit (Windows ADK). Przed uruchomieniem Instalatora należy pobrać zestaw Windows 10 ADK i zainstalować go na serwerze lokacji i na każdym komputerze, na którym jest uruchamiane wystąpienie dostawcy programu SMS.  

Ogólne informacje o obsługiwanych platformach i konfiguracjach wymagań wstępnych znajdują się w temacie [Obsługiwane konfiguracje programu System Center Configuration Manager](../../../../core/plan-design/configs/supported-configurations.md).  

Aby dowiedzieć się, jak za pomocą zestawu Windows ADK z programem Configuration Manager, zobacz [wymagania dotyczące infrastruktury dla wdrożenia systemu operacyjnego w programie System Center Configuration Manager](../../../../osd/plan-design/infrastructure-requirements-for-operating-system-deployment.md).  

**Sprawdź stan lokacji i hierarchii, a następnie sprawdź, czy nie występują żadne nierozwiązane problemy:**  
Przed uaktualnieniem lokacji należy rozwiązać wszystkie problemy z działaniem serwera lokacji, serwera bazy danych lokacji i ról systemu lokacji zainstalowanych na komputerach zdalnych. Problemy z działaniem mogą spowodować niepowodzenie uaktualniania lokacji.  

**Zainstaluj wszystkie odpowiednie aktualizacje krytyczne dla systemów operacyjnych na komputerach hostujących lokację, serwer bazy danych lokacji i role zdalnego systemu lokacji:**  
Przed uaktualnieniem lokacji zainstaluj wszystkie aktualizacje krytyczne przeznaczone do odpowiednich systemów lokacji. Instalowana aktualizacja może wymagać ponownego uruchomienia odpowiednich komputerów przed rozpoczęciem aktualizacji dodatku Service Pack.  

Aby uzyskać więcej informacji, zobacz [usługi Windows Update](http://go.microsoft.com/fwlink/p/?LinkId=105851).  

**Odinstaluj role systemu lokacji, które są nieobsługiwane przez program System Center Configuration Manager:**  
Następujące role systemu lokacji nie są już używane w programie System Center Configuration Manager i musi zostać odinstalowane przed uaktualnieniem programu System Center 2012 Configuration Manager:  

-   Punkt zarządzania poza pasmem  
-   Punkt modułu sprawdzania kondycji systemu  

**Wyłącz repliki bazy danych dla punktów zarządzania w lokacjach głównych:**  
Menedżer konfiguracji nie może pomyślnie uaktualnić lokacji głównej, z repliki bazy danych dla punktów zarządzania włączone. Wyłącz replikację bazy danych przed:  

-   Utworzeniem kopii zapasowej bazy danych lokacji w celu przetestowania uaktualnienia bazy danych  
-   Uaktualnieniem lokacji produkcyjnej do programu System Center Configuration Manager  

Aby uzyskać więcej informacji, zobacz następujące tematy:  
-   System Center 2012 Configuration Manager:  [Konfigurowanie replik bazy danych dla punktów zarządzania](https://technet.microsoft.com/library/hh846234.aspx)  
-   System Center Configuration Manager: [Repliki bazy danych dla punktów zarządzania programu System Center Configuration Manager](../../../../core/servers/deploy/configure/database-replicas-for-management-points.md)  

**Skonfiguruj ponownie punkty aktualizacji oprogramowania, które używają usługi równoważenia obciążenia sieciowego:**  
Menedżer konfiguracji nie może uaktualnić lokacji hostującej punkty aktualizacji oprogramowania klastra równoważenia obciążenia sieciowego (NLB).  

W przypadku używania klastrów równoważenia obciążenia sieciowego w punktach aktualizacji oprogramowania należy usunąć te klastry za pomocą programu PowerShell. (Nie począwszy od programu System Center 2012 Configuration Manager SP1 było możliwości skonfigurowania klastra równoważenia obciążenia Sieciowego w konsoli programu Configuration Manager)  

**Wyłącz wszystkie zadania konserwacji w poszczególnych lokacjach na czas trwania uaktualniania lokacji:**  
Przed uaktualnieniem do programu System Center Configuration Manager, należy wyłączyć wszystkie zadania konserwacji lokacji, które mogą zostać uruchomione w czasie, gdy proces uaktualniania jest aktywny. Dotyczy to m.in. następujących zadań:  

-   Wykonaj kopię zapasową serwera lokacji  
-   Usuń przedawnione operacje klienta  
-   Usuń przedawnione dane odnajdywania  

Proces uaktualniania lokacji może zakończyć się niepowodzeniem, jeżeli w czasie jego trwania zostanie uruchomione zadanie obsługi bazy danych lokacji.  

Przed wyłączeniem zadania zarejestruj jego harmonogram, aby przywrócić jego konfigurację po ukończeniu uaktualniania lokacji.  

Więcej informacji o zadaniach obsługi lokacji znajduje się w temacie:  

-   System Center 2012 Configuration Manager:  [Planowanie zadań konserwacji programu Configuration Manager](https://technet.microsoft.com/library/gg712686.aspx)  
-   System Center Configuration Manager:  [Informacje o zadaniach konserwacji programu System Center Configuration Manager](../../../../core/servers/manage/reference-for-maintenance-tasks.md)  

**Uruchom Narzędzie sprawdzania wymagań wstępnych Instalatora**:  
Aby sprawdzić, czy lokacja spełnia wymagania wstępne, przed uaktualnieniem lokacji można uruchomić **Narzędzie sprawdzania wymagań wstępnych** niezależnie od Instalatora. Później podczas uaktualniania lokacji narzędzie sprawdzania wymagań wstępnych zostanie ponownie uruchomione.  

Jeśli używasz nośnika linii bazowej dla wersji 1606 z wersji z października 2016 niezależne sprawdzenie wymagań wstępnych oblicza lokacji do uaktualnienia do bieżącej gałęzi i długoterminowe Servicing Branch (LTSB) z zarządzania programu System Center Configuration. Niektóre funkcje nie są obsługiwane przez LTSB, mogą pojawić wpisy w *ConfigMgrPrereq.log* będących podobnie do następującej:
 - INFORMACJE: Witryna jest LTSB edition.
 - Nieobsługiwana Rola systemu lokacji "Punkt synchronizacji analizy zasobów" dla wersji LTSB;    Błąd;    Configuration Manager wykrył, że zainstalowano punkt synchronizacji analizy zasobów. Analiza zasobów nie jest obsługiwana w wersji LTSB. Przed kontynuowaniem należy odinstalować rolę systemu lokacji punktu synchronizacji analizy zasobów.

Jeśli planujesz uaktualnić do wersji bieżącej gałęzi, błędów dla wersji LTSB można bezpiecznie zignorować. Mają one zastosowanie tylko wtedy, jeśli planowane jest uaktualnienie do LTSB.

Później po uruchomieniu Instalatora programu Configuration Manager w celu uaktualnienia Sprawdzanie wymagań wstępnych Uruchom ponownie i ocenić witryny utworzonej w gałęzi programu System Center Configuration Manager zostanie zainstalowana (Current Branch lub LTSB). Jeśli chcesz uaktualnić do wersji bieżącej gałęzi wyboru funkcji, które nie są obsługiwane przez LTSB nie są uruchamiane.

Aby uzyskać więcej informacji, zobacz [narzędzie sprawdzania wymagań wstępnych](/sccm/core/servers/deploy/install/prerequisite-checker) i [listy z wymagań wstępnych sprawdza programu System Center Configuration Manager](/sccm/core/servers/deploy/install/list-of-prerequisite-checks).  

**Pobierz pliki wymagań wstępnych oraz pliki redystrybucyjne programu System Center Configuration Manager:**    
Użyj **Narzędzie pobierania Instalatora** pobierania wstępnie wymagane liki redystrybucyjne, pakiety językowe i najnowsze aktualizacje produktu System Center Configuration Manager.  

Aby uzyskać informacje, zobacz [Narzędzie pobierania Instalatora](/sccm/core/servers/deploy/install/setup-downloader).  

**Zaplanuj zarządzanie językami klienta i serwera**:  
W przypadku uaktualnienia lokacji uaktualnienie powoduje tylko zainstalowanie wersji pakietów językowych wybranych podczas uaktualniania.  

-   Instalator sprawdza bieżącą konfigurację języka w lokacji, a następnie identyfikuje pakiety językowe dostępne w folderze z zapisanymi wcześniej pobranymi plikami wymagań wstępnych.  
-   Następnie można potwierdzić wybór bieżących pakietów językowych klienta i serwera lub zmienić wybrane opcje w celu dodania albo usunięcia obsługi danych języków.  
-   Można wybrać tylko te pakiety językowe, które są dostępne po uruchomieniu Instalatora (uzyskane razem z pobranymi plikami wymaganymi).  

> [!NOTE]  
>  Pakiety językowe programu System Center 2012 Configuration Manager nie można użyć w celu włączenia obsługi języków w witrynie System Center Configuration Manager.  

Aby uzyskać więcej informacji o pakietach językowych, zobacz [pakiety językowe w programie System Center Configuration Manager](../../../../core/servers/deploy/install/language-packs.md).  

**Zapoznaj się z uwagami dotyczącymi uaktualniania lokacji**:  
Podczas uaktualniania lokacji programu w niektórych funkcjach i konfiguracjach jest przywracana konfiguracja domyślna. Aby ułatwić przygotowanie tych i powiązanych zmian, zapoznaj się z informacjami w temacie  [Zagadnienia dotyczące uaktualniania](#bkmk_considerations).  

**Utwórz kopię zapasową bazy danych lokacji w centralnej lokacji administracyjnej i lokacjach głównych:**  
Przed uaktualnieniem lokacji utwórz kopię zapasową bazy danych lokacji, której będzie można użyć do odzyskiwania awaryjnego.  

Zobacz [kopii zapasowych i odzyskiwania dla programu System Center Configuration Manager](../../../../protect/understand/backup-and-recovery.md).  

**Wykonaj kopię zapasową dostosowanego pliku Configuration.mof**:  
Jeśli dostosowany plik Configuration.mof jest używany do definiowania klas danych używanych w spisie sprzętu, utwórz kopię zapasową tego pliku przed uaktualnieniem lokacji. Następnie po uaktualnieniu odtwórz ten plik w lokacji. Aby uzyskać więcej informacji na temat korzystania z tego pliku zobacz [jak rozszerzyć spis sprzętu w programie System Center Configuration Manager](../../../../core/clients/manage/inventory/extend-hardware-inventory.md).  

**Przetestuj proces uaktualnienia bazy danych na kopii najnowszej kopii zapasowej bazy danych lokacji:**  
Przetestuj proces uaktualnienia bazy danych za pomocą najnowszej kopii zapasowej bazy danych lokacji przed uaktualnieniem centralnej lokacji administracyjnej programu lub lokacji głównej programu Configuration Manager.  

-   Należy przetestować proces uaktualniania bazy danych lokacji, ponieważ uaktualnienie lokacji może spowodować modyfikację bazy danych  
-   Test uaktualnienia bazy danych nie jest wymagany, ale pozwala wykryć problemy z uaktualnieniem przed wdrożeniem w produkcyjnej bazie danych  
-   Nieudane uaktualnienie bazy danych lokacji może uniemożliwić korzystanie z bazy danych lokacji i może wymagać przeprowadzenia odzyskiwania lokacji w celu przywrócenia jej funkcjonalności  
-   Choć baza danych lokacji jest udostępniana między lokacjami hierarchii, warto zaplanować testowanie bazy danych oddzielnie w każdej uaktualnianej lokacji  
-   W przypadku używania replik bazy danych dla punktów zarządzania w lokacji głównej przed utworzeniem kopii zapasowej bazy danych lokacji należy wyłączyć replikację  

Menedżer konfiguracji nie obsługuje kopii zapasowych lokacji dodatkowych ani testowego uaktualniania bazy danych lokacji dodatkowej.  

Wykonanie testowego uaktualnienia bazy danych na produkcyjnych bazach danych lokacji nie jest obsługiwane. Wykonanie tej czynności powoduje uaktualnienie bazy danych lokacji, przez co lokacja może przestać działać.  

Aby uzyskać więcej informacji, zobacz [Test uaktualnienia bazy danych lokacji](#bkmk_test).  

**Uruchom ponownie serwer lokacji i każdy komputer hostujący rolę systemu lokacji**:  
Można to zrobić, aby upewnić się, że żadnych oczekujących akcji z ostatnio instalowane aktualizacje lub realizowane wymagania wstępne i jest proces wewnętrzny specyficzny dla firmy.  

**Uaktualnianie lokacji**:  
Począwszy od lokacji najwyższego poziomu w hierarchii, uruchom Setup.exe z nośnika źródłowego programu System Center Configuration Manager.  

Po ukończeniu uaktualniania lokacji najwyższego poziomu możesz przystąpić do uaktualniania poszczególnych lokacji podrzędnych. Uaktualnienia poszczególnych lokacji należy wykonywać po kolei i nie realizować ich równolegle  

Dopóki wszystkie lokacje w hierarchii uaktualnienia do programu System Center Configuration Manager, hierarchia działa w trybie mieszanej wersji.  

Informacje dotyczące sposobu uruchamiania uaktualniania, zobacz [uaktualnienia lokacji](#bkmk_upgrade).  

### <a name="after-you-upgrade"></a>Po uaktualnieniu  
**Uaktualnić autonomiczne konsole programu Configuration Manager**:  
Domyślnie po uaktualnieniu centralnej lokacji administracyjnej lub lokacji głównej program instalacyjny uaktualnia także konsolę programu Configuration Manager, który jest zainstalowany na serwerze lokacji. Jednak każdą konsolę zainstalowaną na komputerze innym niż serwer lokacji należy uaktualnić ręcznie.  

> [!TIP]  
>  Przed rozpoczęciem uaktualniania zamknij otwarte konsole.  

Aby uzyskać więcej informacji, zobacz [Instalowanie konsol programu System Center Configuration Manager](../../../../core/servers/deploy/install/install-consoles.md).  

**Skonfiguruj ponownie repliki bazy danych dla punktów zarządzania w lokacjach głównych:**  
W przypadku używania replik bazy danych dla punktów zarządzania w lokacjach głównych należy odinstalować te repliki przed uaktualnieniem lokacji. Po uaktualnieniu lokacji głównej skonfiguruj ponownie repliki bazy danych dla punktów zarządzania.   
Aby uzyskać więcej informacji, zobacz [Repliki bazy danych dla punktów zarządzania programu System Center Configuration Manager](../../../../core/servers/deploy/configure/database-replicas-for-management-points.md).  

**Skonfiguruj ponownie wszystkie wyłączone przed uaktualnieniem zadania konserwacji bazy danych:**  
Jeśli przed uaktualnieniem w lokacji wyłączono zadania obsługi bazy danych ([Informacje o zadaniach konserwacji programu System Center Configuration Manager](../../../../core/servers/manage/reference-for-maintenance-tasks.md)), skonfiguruj je ponownie w lokacji przy użyciu ustawień stosowanych wcześniej przed uaktualnieniem.  

**Uaktualnij klientów**:  
Po uaktualnieniu wszystkich lokacji do programu System Center Configuration Manager, Zaplanuj uaktualnienie klientów.  

Podczas uaktualniania bieżące oprogramowanie klienta zostaje odinstalowane i zastąpione nową wersją oprogramowania. Aby uaktualnić klientów, można zastosować dowolną metodę obsługiwaną przez program Configuration Manager.  

> [!TIP]  
>  W przypadku uaktualniania lokacji najwyższego poziomu w hierarchii zostaje również zaktualizowany pakiet instalacyjny klienta w każdym punkcie dystrybucji w hierarchii. W ramach uaktualniania lokacji głównej zostaje zaktualizowany pakiet uaktualniający klienta dostępny w tej lokacji głównej.  

Aby uzyskać więcej informacji o sposobie uaktualniania istniejących klientów i instalowaniu nowych klientów, zobacz [Uaktualnianie klientów komputerów z systemem Windows w programie System Center Configuration Manager](../../../../core/clients/manage/upgrade/upgrade-clients-for-windows-computers.md).  

##  <a name="bkmk_considerations"></a> Zagadnienia dotyczące uaktualniania  
**Akcje automatyczne**:  
Po uaktualnieniu do programu System Center Configuration Manager automatycznie wykonywane następujące akcje:  

-   Lokacja samodzielnie się resetuje, jednocześnie instalując ponownie wszystkie role systemu lokacji.  
-   Lokacja najwyższego poziomu w hierarchii aktualizuje pakiet instalacyjny klienta w każdym punkcie dystrybucji w hierarchii. Lokacja aktualizuje także domyślne obrazy rozruchowe tak, aby była w nich używana nowa wersja systemu Windows PE dołączona do Zestawu do oceny i wdrażania systemu Windows 10. Jednak proces uaktualniania nie uaktualnia istniejących nośników służących do wdrażania obrazów.  
-   Lokacja główna aktualizuje pakiet uaktualniający klienta dla tej lokacji.  

**Ręczne akcje wykonywane przez użytkownika administracyjnego po uaktualnieniu**   
Po uaktualnieniu lokacji upewnij się, że są wykonywane następujące czynności:  

-   Sprawdź, czy w przypadku klientów przypisanych do poszczególnych lokacji głównych zostało wykonane uaktualnienie i zainstaluj oprogramowanie klienta z nową wersją  
-   Uaktualnienia poszczególnych konsoli programu Configuration Manager, która połączy się z lokacją i uruchomione na komputerze sterowanym zdalnie z serwera lokacji  
-   W lokacjach głównych, w których są używane repliki bazy danych dla punktów zarządzania, skonfiguruj ponownie repliki bazy danych  
-   Po uaktualnieniu lokacji należy ręcznie uaktualnić nośniki fizyczne, takie jak pliki ISO dysków CD lub DVD, dyski flash USB lub wcześniej przygotowane nośniki używane do wdrożeń funkcji Windows To Go lub udostępniane dostawcom sprzętu. Chociaż proces uaktualniania lokacji aktualizuje domyślne obrazy rozruchowe nie może uaktualnić plików nośników lub urządzeń używanych zewnętrznie w stosunku do programu Configuration Manager  
-   Aktualizowanie obrazów rozruchowych innych niż domyślne należy zaplanować, gdy oryginalne (starsze) wersje systemu Windows PE nie są potrzebne.  

**Akcje, które wpływają na konfiguracje i ustawienia**   
Podczas uaktualniania lokacji do programu System Center Configuration Manager, niektóre konfiguracje i ustawienia nie zostaną utrwalone po uaktualnieniu lub ustawiono Nowa domyślna konfiguracja. Poniższa tabela zawiera ustawienia, które nie są trwałe i mogą ulec zmianie, a także szczegółowe informacje ułatwiające zaplanowanie ich podczas uaktualniania lokacji:  

-   **Software Center:**  
    Następujące elementy programu Software Center są resetowane do wartości domyślnych:  
    -   Wardości w pozycji**Informacje o pracy** zostają zresedowane do godzin pracy od **5:00** do **22:00** Monday do Friday.  
    -   W pozycji **Konserwacja komputera** zostaje ustawiona wartość **Wstrzymaj działania programu Software Center, jeżeli mój komputer jest w trybie prezentacji**.  
    -   W pozycji **Zdalne sterowanie** zostaje ustawiona wartość ustawień klienta przypisanych do komputera.  
-   **Harmonogramy podsumowania aktualizacji oprogramowania:**  
     Niestandardowe harmonogramy podsumowania aktualizacji oprogramowania lub grup aktualizacji oprogramowania zostają zresetowane do wartości domyślnej równej 1 godz. Po zakończeniu uaktualniania należy zresetować niestandardowe wartości podsumowania do wymaganej częstotliwości.  

##  <a name="bkmk_test"></a> Testowanie uaktualnienia bazy danych lokacji  
Poniższe informacje dotyczą tylko wtedy, gdy są uaktualnianie poprzednich wersji, takich jak System Center 2012 Configuration Manager do programu System Center Configuration Manager.

Przed uaktualnieniem lokacji należy przetestować kopię bazy danych tej lokacji do uaktualnienia.  

Aby przetestować bazę danych do uaktualnienia, należy najpierw przywrócić kopię bazy danych lokacji do wystąpienia programu SQL Server, który nie jest hostem lokacji programu Configuration Manager. Wersja programu SQL Server używanego do hostowania kopii bazy danych musi być wersją programu SQL Server, czy wersja programu Configuration Manager obsługuje oznacza to kopia bazy danych.  

Następnie po przywróceniu bazy danych lokacji na komputerze programu SQL Server, uruchom Instalatora programu Configuration Manager z folderu nośnika źródłowego programu System Center Configuration Manager z **polecenia/testdbupgrade** opcji wiersza polecenia.  

-   Informacje o sposobie tworzenia i przywracania kopii zapasowej bazy danych lokacji znajdują się w temacie [Opcje wiersza polecenia dla Instalatora](../../../../core/servers/deploy/install/command-line-options-for-setup.md).  
-   Informacje o używaniu opcji wiersza polecenia **/TESTDBUPGRADE** znajdują się w tabeli w temacie [Opcje wiersza polecenia dla Instalatora](../../../../core/servers/deploy/install/command-line-options-for-setup.md).  
-   Informacje o obsługiwanych wersjach programu SQL Server można znaleźć w temacie [Obsługiwane konfiguracje programu SQL Server dla programu System Center Configuration Manager](../../../../core/plan-design/configs/support-for-sql-server-versions.md).  

> [!TIP]  
>  Po zintegrowaniu programu Microsoft Intune z programem Configuration Manager:  
>   
>  Po uruchomieniu testu uaktualnienia bazy danych na kopii bazy danych lokacji utworzonej 5 dni temu lub wcześniej może zostać wyświetlony jeden z następujących komunikatów:  
>   
>  -   OSTRZEŻENIE: Uaktualnienie wymusza pełną synchronizację z chmurą.  
>  -   BŁĄD: Uaktualnienie bazy danych wymusza pełną synchronizację z chmurą.  
>   
> Jednocześnie można bezpiecznie zignorować podczas testowania uaktualnienia bazy danych, ponieważ nie wskazują błędu lub problemu z uaktualnieniem testowym. Zamiast tego wskazują, że podczas rzeczywistego uaktualnienia dane z **chmury** grupy replikacji bazy danych mogą zostać zsynchronizowane w usłudze Microsoft Intune.  

W każdej centralnej lokacji administracyjnej i lokacji głównej, która ma zostać uaktualniona, wykonaj następującą procedurę.  

#### <a name="to-test-a-site-database-for-upgrade"></a>Aby przetestować bazę danych lokacji dla uaktualnienia  

1.  Wykonaj kopię bazy danych lokacji, a następnie przywróć ją do wystąpienia programu SQL Server, który używa tej samej wersji co baza danych lokacji i nie jest hostem lokacji programu Configuration Manager. Przykładowo kopia bazy danych lokacji uruchomionej w wystąpieniu programu SQL Server w wersji Enterprise musi być przywrócona w innym wystąpieniu programu SQL Server w wersji Enterprise.  

2.  Po przywróceniu kopii bazy danych, uruchom Instalatora z nośnika źródłowego programu System Center Configuration Manager. Podczas uruchamiania Instalatora użyj opcji wiersza polecenia **/TESTDBUPGRADE** . Jeśli wystąpienie programu SQL Server, które hostuje kopię bazy danych, nie jest wystąpieniem domyślnym, musisz także podać argumenty wiersza polecenia identyfikujące wystąpienie hostujące kopię bazy danych lokacji.  

     Przykładowo chcesz przeprowadzić uaktualnienie bazy danych lokacji z nazwą bazy danych SMS_ABC. Wykonano przywrócenie kopii bazy danych lokacji na obsługiwane wystąpienie serwera SQL Server o nazwie DBTest. Aby przetestować uaktualnienie kopii bazy danych lokacji, należy użyć następującego polecenia: **Setup.exe polecenia/testdbupgrade DBtest\CM_ABC**  

     Setup.exe można znaleźć w następującej lokalizacji na nośniku źródłowym programu System Center Configuration Manager: **SMSSETUP\BIN\X64**.  

3.  Na komputerze z wystąpieniem programu SQL Server realizującym test uaktualnienia bazy danych otwórz zapisany w głównym folderze dysku plik ConfigMgrSetup.log i sprawdź zapisywane w nim informacje:  

    -   Jeśli testowe uaktualnienie nie powiedzie się, usuń problemy związane z awarią uaktualnienia bazy danych lokacji, utwórz nową kopię zapasową bazy danych lokacji i przetestuj uaktualnienie nowej kopii bazy danych lokacji.  
    -   Gdy proces powiedzie się, możesz usunąć kopię bazy danych lokacji.  

        > [!NOTE]  
        >  Przywracanie kopii bazy danych lokacji użytej do testu uaktualnienia jako bazy danych dowolnej lokacji nie jest obsługiwane.  

Po pomyślnym uaktualnieniu kopii bazy danych lokacji, należy kontynuować proces uaktualniania lokacji programu Configuration Manager i jego bazy danych lokacji.  

##  <a name="bkmk_upgrade"></a> Uaktualnianie lokacji  
Po zakończeniu poprzedzających uaktualnienie czynności konfiguracyjnych lokacji należy sprawdzić uaktualnienie bazy danych lokacji na kopii bazy danych i pobrać wymagane pliki oraz pakiety językowe dla wersji dodatku service pack, które zamierzasz zainstalować można przystąpić do uaktualnienia tej lokacji programu Configuration Manager.  

Uaktualniając lokację umieszczoną w hierarchii, należy najpierw uaktualnić lokację najwyższego poziomu. Lokacja najwyższego to centralna lokacja administracyjna lub autonomiczna lokacja główna. Po zakończeniu uaktualniania centralnej lokacji administracyjnej można uaktualnić w dowolnej kolejności podrzędne lokacje główne. Po uaktualnieniu lokacji głównej można uaktualnić tej lokacji podrzędnych lokacji dodatkowych lub uaktualnić dodatkowe Lokacje główne, przed uaktualnieniem wszystkich lokacji dodatkowych.  

Aby uaktualnić centralną lokację administracyjną lub lokację główną, należy uruchomić instalację z nośnika źródłowego programu System Center Configuration Manager. Nie należy tego robić w celu uaktualnienia lokacji dodatkowych. Zamiast tego użyj konsoli programu Configuration Manager do uaktualnienia lokacji dodatkowej po zakończeniu uaktualnienia nadrzędnej lokacji głównej.  

Przed uaktualnieniem lokacji zamknij konsolę programu Configuration Manager, który jest zainstalowany na serwerze lokacji, aż do zakończenia uaktualnienia lokacji. Należy także zamknąć każdą konsolę programu Configuration Manager działa na komputerach innych niż serwer lokacji. Ponowne nawiązanie połączenia z konsolą będzie możliwe po zakończeniu uaktualnienia lokacji. Jednakże do momentu uaktualnienia konsoli programu Configuration Manager do nowej wersji programu Configuration Manager, nie będzie możliwe wyświetlenie niektórych obiektów i informacji dostępnych w nowej wersji programu Configuration Manager.  

Użyj poniższych procedur do uaktualnienia lokacji programu Configuration Manager:  

#### <a name="to-upgrade-a-central-administration-site-or-primary-site"></a>Aby uaktualnić centralną lokację administracyjną lub lokację główną  

1.  Sprawdź, czy użytkownik, który uruchamia instalatora, ma następujące prawa zabezpieczeń:  

    -   Uprawnienia administratora lokalnego na komputerze serwera lokacji.  
    -   Uprawnienia administratora lokalnego na zdalnym serwerze bazy danych lokacji (jeśli jest zdalna).    </br></br>

2.  Na komputerze serwera lokacji Otwórz Eksploratora Windows i przejdź do  **&lt;Nośnik_źródłowy_programu_configmgr\>\SMSSETUP\BIN\X64**.  

3.  Kliknij dwukrotnie plik **Setup.exe**. Otworzy się Kreator instalacji programu Configuration Manager.  

4.  Na stronie **Zanim rozpoczniesz** kliknij przycisk **Dalej**.  

5.  Na stronie **Wprowadzenie** wybierz polecenie **Uaktualnij tę lokację programu Configuration Manager**i kliknij przycisk **Dalej**.  

6.  Na stronie **Klucz produktu** kliknij przycisk **Dalej**.  

     Jeśli wcześniej została zainstalowana wersja ewaluacyjna Configuration Manager, możesz wybrać **Instaluj licencjonowaną wersję tego produktu**, a następnie wprowadź klucz produktu w celu uruchomienia pełnej instalacji programu Configuration Manager skonwertuje wówczas lokację do wersji pełnej.  

     Począwszy od wersji października 2016 nośnika linii bazowej 1606 wersji programu System Center Configuration Manager, można określić datę wygaśnięcia umowy Software Assurance. Masz również opcję, aby określić **Data wygaśnięcia Software Assurance** umowy licencyjnej jako wygodny monitu dla użytkownika z tą datą. Jeśli nie podasz to podczas instalacji, możesz podać go później z w konsoli programu Configuration Manager.

     >  [!NOTE]   
     >  Microsoft Data wygaśnięcia wprowadzone i nie będzie używać tej daty sprawdzanie oryginalności licencji nie można zweryfikować.  Należy zamiast tego należy używać go jako przypomnienie daty wygaśnięcia. Jest to przydatne, ponieważ stan licencji gwarancji oprogramowania należy bieżącego na kwalifikować się do korzystania z tych dodatkowych aktualizacji i programu Configuration Manager okresowo sprawdza, czy nowe aktualizacje oprogramowania oferowanych online.    

     Aby uzyskać więcej informacji, zobacz [licencjonowania i gałęzi programu System Center Configuration Manager](/sccm/core/understand/learn-more-editions).

7.  Na stronie **Postanowienia licencyjne dotyczące oprogramowania firmy Microsoft** przeczytaj i zaakceptuj postanowienia licencyjne, a następnie kliknij przycisk **Dalej**.  

8.  Na stronie **Licencje wymagań wstępnych** przeczytaj i zaakceptuj postanowienia licencyjne wstępnie wymaganego oprogramowania, a następnie kliknij przycisk **Dalej**. Instalator pobiera i automatycznie instaluje oprogramowanie w systemach lokacji lub na klientach, gdy jest to wymagane. Przed kontynuowaniem do następnej strony należy zaznaczyć wszystkie pola wyboru.  

9. Na stronie **Pobieranie plików wymaganych wstępnie** określ, czy instalator ma pobrać najnowsze wymagane wstępnie pliki, pakiety językowe i aktualizacje produktów z Internetu, czy mają być użyte poprzednio pobrane pliki, i kliknij przycisk **Dalej**. Jeżeli pliki zostały wcześniej pobrane przy użyciu Narzędzia pobierania Instalatora, wybierz opcję **Użyj wcześniej pobranych plików** i określ folder pobierania. Aby uzyskać więcej informacji, zobacz [Narzędzie pobierania Instalatora](/sccm/core/servers/deploy/install/setup-downloader).

    > [!NOTE]  
    >  W przypadku używania wcześniej pobranych plików sprawdź, czy ścieżka do folderu pobierania zawiera najnowszą wersję plików.  

10. Na stronie **Wybór języka serwera** wyświetl listę języków zainstalowanych obecnie w tej lokacji. Wybierz dodatkowe języki, które są dostępne w tej lokacji dla konsoli programu Configuration Manager i raporty, oraz usuń języki, które mają już w tej lokacji, a następnie kliknij przycisk **dalej**. Język angielski jest wybrany domyślnie i nie można go usunąć.  

    > [!IMPORTANT]  
    >  Każda wersja programu Configuration Manager nie może używać pakietów językowych z poprzednich wersji programu Configuration Manager. Aby włączyć obsługę języka w lokacji programu Configuration Manager, która uaktualnieniu, należy użyć wersji pakietu językowego dla nowej wersji. Na przykład podczas uaktualniania programu System Center 2012 Configuration Manager do System Center Configuration Manager, jeśli wersja pakietu językowego programu System Center Configuration Manager nie jest dostępna z plikami wymagań wstępnych, które można pobrać obsługę danego języka nie zostanie zainstalowane.  

11. Na stronie **Wybór języka klienta** wyświetl listę języków zainstalowanych obecnie w tej lokacji. Wybierz dodatkowe języki, które mają być dostępne w tej lokacji dla klientów, oraz usuń języki, które nie są już potrzebne w tej lokacji. Określ, czy w klientach urządzeń przenośnych mają zostać włączone wszystkie języki klienckie, i kliknij przycisk **Dalej**. Język angielski jest wybrany domyślnie i nie można go usunąć.  

    > [!IMPORTANT]  
    >  Każda wersja programu Configuration Manager nie może używać pakietów językowych z poprzednich wersji programu Configuration Manager. Aby włączyć obsługę języka w lokacji programu Configuration Manager, która uaktualnieniu, należy użyć wersji pakietu językowego dla nowej wersji. Na przykład podczas uaktualniania programu System Center 2012 Configuration Manager do System Center Configuration Manager, jeśli wersja pakietu językowego programu System Center Configuration Manager nie jest dostępna z plikami wymagań wstępnych, które można pobrać obsługę danego języka nie zostanie zainstalowane.  

12. Na stronie **Podsumowanie ustawień** kliknij przycisk **Dalej** . Zostanie uruchomione Narzędzie sprawdzania wymagań wstępnych, które potwierdzi gotowość serwera do uaktualnienia danej lokacji.  

13. Jeśli na stronie **Sprawdzenie instalacji wymagań wstępnych** nie zostały podane żadne problemy, kliknij przycisk **Dalej** , aby uaktualnić lokację i role systemu lokacji. Gdy Narzędzie sprawdzania wymagań wstępnych wykryje problem, kliknij element na liście w celu uzyskania szczegółów dotyczących sposobu rozwiązania problemu. Przed kontynuowaniem instalacji usuń przyczyny wszystkich pozycji o statusie **Błąd** . Po rozwiązaniu problemu kliknij przycisk **Uruchom sprawdzenie** , aby ponownie uruchomić sprawdzenie wymagań wstępnych. Aby przejrzeć wyniki zwrócone przez Narzędzie sprawdzania wymagań wstępnych, możesz również otworzyć plik ConfigMgrPrereq.log w katalogu głównym dysku systemowego. Plik dziennika może zawierać dodatkowe informacje, które nie są wyświetlane w interfejsie użytkownika. Aby uzyskać listę reguły wymagań wstępnych instalacji i opisy, zobacz [narzędzie sprawdzania wymagań wstępnych](/sccm/core/servers/deploy/install/list-of-prerequisite-checks).  

Na stronie **Uaktualnienie** instalator wyświetli ogólny postęp całej procedury. Gdy Instalator ukończy instalację podstawowego serwera lokacji i systemu lokacji, możesz zamknąć kreatora. Konfiguracja lokacji odbywa się w tle.  

#### <a name="to-upgrade-a-secondary-site"></a>Aby uaktualnić lokację dodatkową  

1.  Sprawdź, czy użytkownik administracyjny uruchamiający Instalatora ma następujące prawa zabezpieczeń:  

    -   Uprawnienia administratora lokalnego na komputerze serwera lokacji dodatkowej  
    -   Administrator infrastruktury lub administrator o pełnych uprawnieniach w głównym elemencie nadrzędnym  
    -   Uprawnienia administratora systemu w bazie danych lokacji dodatkowej  
    </br>
2.  W konsoli programu Configuration Manager kliknij przycisk **Administracja**.  

3.  W obszarze roboczym **Administracja** rozwiń węzeł **Konfiguracja lokacji**, a następnie kliknij przycisk **Lokacje**.  

4.  Wybierz lokację dodatkową do uaktualnienia, a następnie na karcie **Narzędzia główne** w grupie **Lokacja** kliknij przycisk **Uaktualnij**.  

5.  Potwierdź decyzję, klikając przycisk **Tak** , i rozpocznij uaktualnienie lokacji dodatkowej.  

Uaktualnienie lokacji dodatkowej będzie realizowane w tle. Po zakończeniu uaktualnienia można potwierdzenie stanu konsoli programu Configuration Manager. Aby potwierdzić stan konsoli, wybierz serwer lokacji dodatkowej, a następnie na karcie **Narzędzia główne** w grupie **Lokacja** kliknij przycisk **Pokaż stan instalacji**.  

##  <a name="BKMK_PostUpgrade"></a> Wykonywanie zadań po uaktualnieniu  
Po uaktualnieniu lokacji do nowego dodatku Service Pack może być konieczne wykonanie dodatkowych zadań konfiguracyjnych wymaganych do skończenia uaktualnienia lub zmiany konfiguracji lokacji. Może to obejmować uaktualnienie klientów programu Configuration Manager lub konsoli programu Configuration Manager, ponowne włączenie replik bazy danych dla punktów zarządzania i przywrócenie ustawień dla funkcji programu Configuration Manager, należy używać i które nie zostaną utrwalone po uaktualnienia z dodatkiem service pack.  

**Znane problemy dotyczące Lokacje dodatkowe:**  
- **Po uaktualnieniu do wersji 1511:** Aby zapewnić klientom w lokacjach dodatkowych można znaleźć punktu zarządzania z lokacji dodatkowej (punkt zarządzania proxy), ręcznie dodać punkt zarządzania do grup granic obejmujących punkty dystrybucji w lokacji dodatkowej.  

- **Po uaktualnieniu do wersji 1606 lub nowszy:** Punkty zarządzania serwera proxy są automatycznie dodawane do grupy granic, które zawierają punkty dystrybucji w lokacji dodatkowej.
