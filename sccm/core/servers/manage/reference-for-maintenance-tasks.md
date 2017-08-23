---
title: Informacje o zadaniach konserwacji | Dokumentacja firmy Microsoft
description: "Przeczytaj szczegółowe informacje dla każdego zadania konserwacji programu System Center Configuration Manager lokacji i określa, czy zadania te są domyślnie włączone."
ms.custom: na
ms.date: 3/8/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 68dc6acd-5848-47a4-b4c1-ffa40e47890b
caps.latest.revision: "16"
caps.handback.revision: "0"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: a2d4420c2274a9b1ceb47ffd267849fdb5a55a61
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="reference-for-maintenance-tasks-for-system-center-configuration-manager"></a>Informacje o zadaniach konserwacji programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Ten temat zawiera szczegółowe informacje dotyczące każdego zadania konserwacji lokacji programu System Center Configuration Manager i określa typy lokacji, w którym zadanie będzie dostępne. Każdy wpis wskazuje także, gdy zadanie jest włączone lub nie jest domyślnie włączone. Aby uzyskać informacje dotyczące planowania i konfigurowania lokacji pod kątem uruchamiania zadań konserwacji, zobacz [zadania konserwacji programu System Center Configuration Manager](../../../core/servers/manage/maintenance-tasks.md).  

**Tworzenie kopii zapasowej serwera lokacji**: To zadanie służy do przygotowania odzyskiwania kluczowych danych. Można utworzyć kopii zapasowej kluczowych informacji w celu przywrócenia lokacji i bazy danych programu Configuration Manager. Aby uzyskać więcej informacji, zobacz [kopii zapasowych i odzyskiwania dla programu System Center Configuration Manager](../../../protect/understand/backup-and-recovery.md).  

-   **Centralna lokacja administracyjna**: Włączono    
-   **Lokacja główna**: Niewłączona    
-   Lokacja dodatkowa: Niedostępne  

**Sprawdź tytuł aplikacji z informacjami o spisie**: To zadanie służy do zapewniania spójności między tytułów oprogramowania, które są zgłaszane w spisie oprogramowania i tytułów oprogramowania w katalogu analizy zasobów. Aby uzyskać więcej informacji, zobacz [Wprowadzenie do analizy zasobów w programie System Center Configuration Manager](../../../core/clients/manage/asset-intelligence/introduction-to-asset-intelligence.md).  

-   **Centralna lokacja administracyjna**: Włączono    
-   **Lokacja główna**: Włączono    
-   Lokacja dodatkowa: Niedostępne  

**Wyczyść flagę instalacji**: To zadanie służy do usuwania flagi instalacji w odniesieniu do klientów, którzy nie przesłali rekordu wykrywania interwału czasowego w okresie **ponowne odnajdywanie klienta** okresu. Flaga instalacji uniemożliwia automatyczną instalację wypychaną klienta na komputerze, który może być aktywnego klienta programu Configuration Manager.  

-   Centralna lokacja administracyjna: Niedostępne    
-   **Lokacja główna**: Niewłączona    
-   Lokacja dodatkowa: Niedostępne  

**Usuń przestarzałe dane żądania aplikacji**: To zadanie służy do usuwania przestarzałych żądań aplikacji z bazy danych. Aby uzyskać więcej informacji dotyczących żądań aplikacji, zobacz [tworzenie i wdrażanie aplikacji w programie System Center Configuration Manager](/sccm/apps/get-started/create-and-deploy-an-application).  

-   Centralna lokacja administracyjna: Niedostępne
-   **Lokacja główna**: Włączono    
-   Lokacja dodatkowa: Niedostępne  

**Usuń przestarzałą historię pobierania klienta**: To zadanie służy do usuwania danych historycznych dotyczących źródła pobierania używany przez klientów. Pobierz informacje o źródle jest używany do wypełniania [źródła danych klienta pulpitu nawigacyjnego](/sccm/core/servers/deploy/configure/monitor-content-you-have-distributed#client-data-sources-dashboard).  
-  Centralna lokacja administracyjna — niedostępna
-    **Lokacja główna** — włączona
-  Lokacja dodatkowa — niedostępna

**Usuń przestarzałe operacje klienta**: To zadanie służy do usuwania wszystkich przestarzałych danych operacji klienta z bazy danych lokacji. Obejmują one na przykład dane dla przestarzałych lub wygasłych powiadomień klienta (takich jak żądania pobierania zasad komputera lub użytkownika) i dane programu Endpoint Protection (takie jak żądania użytkownika administracyjnego dla klientów w celu wykonania skanowania lub pobrania zaktualizowanych definicji).

-   **Centralna lokacja administracyjna**: Włączono    
-   **Lokacja główna**: Włączono    
-   Lokacja dodatkowa: Niedostępne  

**Usuń przestarzałą historię obecności klienta**: To zadanie służy do usuwania informacji o historii stanu online klientów (zarejestrowanych przez powiadomienia klienta), która jest starsza niż określony czas. Aby uzyskać więcej informacji na temat powiadomień klienta, zobacz [Jak monitorować klientów w programie System Center Configuration Manager](../../../core/clients/manage/monitor-clients.md).  

-   **Centralna lokacja administracyjna**: Włączono   
-   **Lokacja główna**: Włączono    
-   Lokacja dodatkowa: Niedostępne  

**Usuń przestarzałe chmury zarządzania bramy ruchu danych**: To zadanie służy do usuwania wszystkich przestarzałych danych dotyczących ruchu, który przechodzi przez [brama zarządzania chmury](/sccm/core/clients/manage/plan-cloud-management-gateway) z bazy danych lokacji. Na przykład w tym dane o liczbie żądań, całkowita liczba żądań w bajtach bajtów odpowiedzi, liczba nieudanych żądań i maksymalną liczbę równoczesnych żądań.  
- **Centralna lokacja administracyjna** — włączona
- **Lokacja główna** — włączona
- Lokacja dodatkowa — niedostępna


**Usuń przestarzałe zgromadzone pliki**: To zadanie służy do usuwania z bazy danych przestarzałych informacji na temat zbieranych plików. Umożliwia również usunięcie zebranych plików ze struktury folderów serwera lokacji w wybranej lokacji. Domyślnie pięć najnowsze kopii zebranych plików są przechowywane na serwerze lokacji w **Inboxes\sinv.box\FileCol** katalogu. Aby uzyskać więcej informacji, zobacz [wprowadzenie do spisu oprogramowania w programie System Center Configuration Manager](/sccm/core/clients/manage/inventory/introduction-to-software-inventory).  

-   Centralna lokacja administracyjna: Niedostępne    
-   **Lokacja główna**: Włączono    
-   Lokacja dodatkowa: Niedostępne  

**Usuń przestarzałe dane powiązania komputera**: To zadanie służy do usuwania przestarzałych danych powiązania komputera wdrożenia systemu operacyjnego z bazy danych. Te informacje są używane w ramach przywracania stanu użytkowników. Aby uzyskać więcej informacji o skojarzeniach komputera, zobacz [Zarządzanie stanem użytkownika w programie System Center Configuration Manager](../../../osd/get-started/manage-user-state.md).  

-   Centralna lokacja administracyjna: Niedostępne    
-   **Lokacja główna**: Włączono    
-   Lokacja dodatkowa: Niedostępne  

**Usuń przestarzałe dane wykrywania usunięcia**: To zadanie służy do usuwania przestarzałych danych z bazy danych, który został utworzony przy użyciu funkcji widoków wyodrębniania. Widoków wyodrębniania są domyślnie wyłączone. Można włączyć tylko je przy użyciu zestawu SDK programu Configuration Manager. Jeśli funkcja widoków wyodrębniania nie będzie włączona, nie będą istniały dane do usunięcia przez to zadanie.  

-   **Centralna lokacja administracyjna**: Włączono    
-   **Lokacja główna**: Włączono    
-   Lokacja dodatkowa: Niedostępne  

**Usuń przestarzałe przestarzały rekord wymazania urządzenia**: To zadanie służy do usuwania przestarzałych danych dotyczących akcji wymazania urządzenia przenośnego z bazy danych. Aby dowiedzieć się, jak czyszczenie urządzeń przenośnych, zobacz [ochrona danych za pomocą czyszczenia danych, blokowania lub resetowania przy użyciu programu System Center Configuration Manager kodu dostępu](/sccm/mdm/deploy-use/wipe-lock-reset-devices).  

-   Centralna lokacja administracyjna: Niedostępne    
-   **Lokacja główna**: Włączono    
-   Lokacja dodatkowa: Niedostępne  

**Usuń przestarzałe urządzenia zarządzane przez łącznik serwera Exchange**: To zadanie służy do usuwania przestarzałych danych dotyczących urządzeń przenośnych, które są zarządzane przy użyciu łącznika serwera Exchange. Usuwanie danych odbywa się zgodnie z interwałem skonfigurowanym dla **Ignoruj urządzenia przenośne, które są nieaktywne przez ponad (dni)** opcja **odnajdywania** właściwości konektora serwera Exchange. Aby uzyskać więcej informacji, zobacz [Zarządzanie urządzeniami przenośnymi za pomocą programu System Center Configuration Manager i Exchange](../../../mdm/deploy-use/manage-mobile-devices-with-exchange-activesync.md).  

-   Centralna lokacja administracyjna: Niedostępne   
-   **Lokacja główna**: Włączono    
-   Lokacja dodatkowa: Niedostępne  

**Usuń przestarzałe dane wykrywania**: To zadanie służy do usuwania przestarzałych danych odnajdywania z bazy danych. Dane te mogą obejmować rekordy wynikające z odnajdywania pulsu, funkcja odnajdowania sieci i metod odnajdywania usług domenowych w usłudze Active Directory (systemu, użytkowników i grup). Gdy to zadanie zostanie uruchomione w lokacji, dane powiązane z tą lokacją zostaną usunięte, a zmiany zostaną zreplikowane do innych lokacji. Aby uzyskać informacje na temat odnajdywania, zobacz [Uruchamianie odnajdywania dla programu System Center Configuration Manager](../../../core/servers/deploy/configure/run-discovery.md).  

-   Centralna lokacja administracyjna: Niedostępne    
-   **Lokacja główna**: Włączono    
-   Lokacja dodatkowa: Niedostępne  

**Usuń przestarzałe dane dotyczące użycia punktu dystrybucji**: To zadanie służy do usuwania z bazy danych przestarzałych danych dla punktów dystrybucji przechowywanych przez dłuższy niż określony czas.  

-   **Centralna lokacja administracyjna**: Włączono    
-   **Lokacja główna**: Włączono    
-   Lokacja dodatkowa: Niedostępne  

**Usuń przestarzałe dane historii stanu kondycji programu Endpoint Protection**: To zadanie służy do usuwania przestarzałych informacji stanu programu Endpoint Protection z bazy danych. Aby uzyskać więcej informacji na temat informacji o stanie programu Endpoint Protection, zobacz [Jak monitorować program Endpoint Protection w programie System Center Configuration Manager](../../../protect/deploy-use/monitor-endpoint-protection.md).  

-   Centralna lokacja administracyjna: Niedostępne    
-   **Lokacja główna**: Włączono    
-   Lokacja dodatkowa: Niedostępne  

**Usuń przestarzałe zarejestrowane urządzenia**: Począwszy od aktualizacji 1602, to zadanie jest domyślnie wyłączone. To zadanie służy do usuwania z bazy danych lokacji przestarzałych danych dotyczących urządzeń przenośnych, które nie zwróciły żadnych informacji o lokacji w wyznaczonym czasie.

To zadanie dotyczy urządzeń, które są zarejestrowane przy użyciu programu Microsoft Intune (rozwiązanie hybrydowe) lub programu Configuration Manager lokalnego zarządzania urządzeniami przenośnymi. Aby uzyskać informacje o systemach operacyjnych urządzeń, które są zarejestrowane przy użyciu programu Configuration Manager lub usługi Intune, zobacz [urządzeń przenośnych zarejestrowanych w usłudze Microsoft Intune](../../../core/plan-design/configs/supported-operating-systems-for-clients-and-devices.md#mobile-devices-enrolled-by-microsoft-intune) sekcji [obsługiwane systemy operacyjne dla klientów i urządzeń dla programu System Center Configuration Manager](../../../core/plan-design/configs/supported-operating-systems-for-clients-and-devices.md).

-   Centralna lokacja administracyjna: Niedostępne    
-   **Lokacja główna**: Niewłączona    
-   Lokacja dodatkowa: Niedostępne  

**Usuń przestarzałą historię spisu**: To zadanie służy do usuwania danych spisu przechowywanych przez dłuższy niż określony czas z bazy danych. Aby uzyskać informacje o historii spisu, zobacz [Jak używać Eksploratora zasobów do wyświetlania spisu sprzętu w programie System Center Configuration Manager](../../../core/clients/manage/inventory/use-resource-explorer-to-view-hardware-inventory.md).  

-   Centralna lokacja administracyjna: Niedostępne    
-   **Lokacja główna**: Włączono    
-   Lokacja dodatkowa: Niedostępne  

**Usuń przestarzałe dane dziennika**: To zadanie służy do usuwania przestarzałych danych dziennika używanego do rozwiązywania problemów z bazy danych. Te dane nie dotyczą działań składników programu Configuration Manager.  

> [!IMPORTANT]  
> To zadanie jest domyślnie uruchamiane codziennie w każdej lokacji. W centralnej lokacji administracyjnej oraz lokacjach głównych zadanie usuwa dane starsze niż 30 dni. Korzystając z programu SQL Server Express w lokacji dodatkowej, upewnij się, że to zadanie jest przeprowadzana codziennie i usuwa dane, które było nieaktywne przez siedem dni.  

-   **Centralna lokacja administracyjna**: Włączono    
-   **Lokacja główna**: Włączono    
-   **Lokacja dodatkowa**: Włączono  

**Usuń przestarzałą historię zadań powiadamiania**: To zadanie służy do usuwania informacji o zadaniach powiadomień klientów z bazy danych lokacji po nie zostało zaktualizowane przez określony czas. Aby uzyskać więcej informacji o powiadomieniach klienta, zobacz [zadania wdrażania klientów programu System Center Configuration Manager](../../../core/clients/manage/monitor-clients.md).  

-   Centralna lokacja administracyjna: Niedostępne    
-   **Lokacja główna**: Włączono    
-   Lokacja dodatkowa: Niedostępne  

**Usuń przestarzałe dane podsumowujące replikacji**: To zadanie służy do usuwania przestarzałych danych podsumowujących replikacji z bazy danych lokacji, gdy nie zostało zaktualizowane przez określony czas. Aby uzyskać więcej informacji, zobacz sekcję [Monitorowanie linków replikacji bazy danych i stanu replikacji](../../../core/servers/manage/monitor-hierarchy-and-replication-infrastructure.md#BKMK_MonitorRepLinksAndStatuss) w temacie [Monitorowanie infrastruktury hierarchii i replikacji w programie System Center Configuration Manager](../../../core/servers/manage/monitor-hierarchy-and-replication-infrastructure.md).  

-   **Centralna lokacja administracyjna**: Włączono    
-   **Lokacja główna**: Włączono    
-   **Lokacja dodatkowa**: Włączono  

**Usuń stare rekordy kodów dostępu**: To zadanie w lokacji najwyższego poziomu w hierarchii służy do usuwania przestarzałych danych resetowania kodu dostępu dla urządzeń z systemami Android i Windows Phone. Dane resetowania kodu dostępu jest zaszyfrowany, ale zawierają numery PIN urządzeń. Domyślnie to zadanie jest włączone i usuwa dane starsze niż jeden dzień.  

-   **Centralna lokacja administracyjna**: Włączono    
-   **Lokacja główna**: Włączono    
-   Lokacja dodatkowa: Niedostępne  

**Usuń przestarzałe dane śledzenia replikacji**: To zadanie służy do usuwania przestarzałych danych dotyczących replikacji bazy danych między lokacjami programu Configuration Manager z bazy danych. Zmiana konfiguracji tego zadania konserwacji powoduje zastosowanie tej konfiguracji do wszystkich odnośnych lokacji w hierarchii. Aby uzyskać więcej informacji, zobacz sekcję [Monitorowanie linków replikacji bazy danych i stanu replikacji](../../../core/servers/manage/monitor-hierarchy-and-replication-infrastructure.md#BKMK_MonitorRepLinksAndStatuss) w temacie [Monitorowanie infrastruktury hierarchii i replikacji w programie System Center Configuration Manager](../../../core/servers/manage/monitor-hierarchy-and-replication-infrastructure.md).  

-   **Centralna lokacja administracyjna**: Włączono    
-   **Lokacja główna**: Włączono    
-   **Lokacja dodatkowa**: Włączono  

**Usuń przestarzałe dane pomiaru oprogramowania**: To zadanie służy do usuwania przestarzałych danych pomiaru oprogramowania przechowywanych przez dłuższy niż określony czas z bazy danych. Aby uzyskać więcej informacji, zobacz [Pomiar użytkowania oprogramowania w programie System Center Configuration Manager](../../../apps/deploy-use/monitor-app-usage-with-software-metering.md).  

-   Centralna lokacja administracyjna: Niedostępne    
-   **Lokacja główna**: Włączono    
-   Lokacja dodatkowa: Niedostępne  

**Usuń przestarzałe dane podsumowania pomiaru oprogramowania**: To zadanie służy do usuwania przestarzałych danych podsumowania pomiaru oprogramowania przechowywanych przez dłuższy niż określony czas z bazy danych. Aby uzyskać więcej informacji, zobacz [Pomiar użytkowania oprogramowania w programie System Center Configuration Manager](../../../apps/deploy-use/monitor-app-usage-with-software-metering.md).  

-   Centralna lokacja administracyjna: Niedostępne    
-   **Lokacja główna**: Włączono    
-   Lokacja dodatkowa: Niedostępne  

**Usuń przestarzałe komunikaty stanu**: To zadanie służy do usuwania przestarzałych danych komunikatów stanu zgodnie z konfiguracją reguł filtru stanu z bazy danych. Aby uzyskać informacje, zobacz sekcję "Monitorowanie systemu stanu programu Configuration Manager" w temacie [korzystanie z alertów i systemu stanu programu System Center Configuration Manager](../../../core/servers/manage/use-alerts-and-the-status-system.md).  

-   **Centralna lokacja administracyjna**: Włączono    
-   **Lokacja główna**: Włączono    
-   Lokacja dodatkowa: Niedostępne  

**Usuń przestarzałe dane zagrożeń**: To zadanie służy do usuwania przestarzałych danych zagrożeń programu Endpoint Protection, przechowywanych przez dłuższy niż określony czas z bazy danych. Aby uzyskać więcej informacji na temat programu Endpoint Protection, zobacz [Program Endpoint Protection w programie System Center Configuration Manager](../../../protect/deploy-use/endpoint-protection.md).  

-   Centralna lokacja administracyjna: Niedostępne    
-   **Lokacja główna**: Włączono    
-   Lokacja dodatkowa: Niedostępne  

**Usuń przestarzałe nieznane komputery**: To zadanie służy do usuwania informacji o nieznanych komputerach z bazy danych lokacji, gdy nie zostało zaktualizowane przez określony czas. Aby uzyskać więcej informacji, zobacz [Przygotowywanie do wdrożenia na nieznanych komputerach w programie System Center Configuration Manager](../../../osd/get-started/prepare-for-unknown-computer-deployments.md).  

-   Centralna lokacja administracyjna: Niedostępne    
-   **Lokacja główna**: Włączono    
-   Lokacja dodatkowa: Niedostępne  

**Usuń przestarzałe dane koligacji urządzenia użytkownika**: To zadanie służy do usuwania przestarzałych danych koligacji urządzenia użytkownika z bazy danych. Aby uzyskać więcej informacji, zobacz [Łączenie użytkowników i urządzeń za pomocą koligacji urządzenia użytkownika w programie System Center Configuration Manager](../../../apps/deploy-use/link-users-and-devices-with-user-device-affinity.md).  

-   Centralna lokacja administracyjna: Niedostępne    
-   **Lokacja główna**: Włączono    
-   Lokacja dodatkowa: Niedostępne  

**Usuń wygasłe MDM rekordy pakietu zbiorczej rejestracji**: To zadanie służy do usuwania starych certyfikatów rejestracji zbiorczej i odpowiednie profile, po wygaśnięciu certyfikatu rejestracji. Aby uzyskać więcej informacji, zobacz [tworzyć profile certyfikatów](/sccm/protect/deploy-use/create-certificate-profiles).
-   **Centralną lokację administracyjną**: Włączono
-   **Lokacja główna**: Włączono
-   Lokacja dodatkowa: Niedostępne

**Usuń nieaktywne dane wykrywania klienta**: To zadanie służy do usuwania danych odnajdywania nieaktywnych klientów z bazy danych. Klienci są oznaczone jako nieaktywne, gdy klient jest oznaczony jako przestarzały i które są skutek konfiguracji dotyczących stanu klienta.

To zadanie działa tylko z zasobami, które są klientów programu Configuration Manager. Różni się od **Usuń przestarzałe dane wykrywania** zadań, służącego do usuwania wszystkich przestarzałych rekordów danych wykrywania. Uruchomienie tego zadania w jednej lokacji spowoduje usunięcie danych z bazy danych we wszystkich lokacjach w hierarchii. Aby uzyskać więcej informacji, zobacz [Jak skonfigurować stan klienta w programie System Center Configuration Manager](../../../core/clients/deploy/configure-client-status.md).  

> [!IMPORTANT]  
> Jeśli jest włączona, należy skonfigurować to zadanie, by było uruchamiane z większym interwałem niż **odnajdywania pulsu** harmonogramu. Umożliwia to aktywnym klientom wysłanie rekordu wykrywania interwału czasowego, aby oznaczyć swój rekord klienta jako aktywny, dlatego to zadanie nie powoduje ich usunięcia.  

-   Centralna lokacja administracyjna: Niedostępne    
-   **Lokacja główna**: Niewłączona    
-   Lokacja dodatkowa: Niedostępne  

**Usuń przestarzałe alerty**: To zadanie służy do usuwania wygasłych alertów przechowywanych przez dłuższy niż określony czas z bazy danych. Aby uzyskać więcej informacji, zobacz [Korzystanie z alertów i systemu stanu w programie System Center Configuration Manager](../../../core/servers/manage/use-alerts-and-the-status-system.md).  

-   **Centralna lokacja administracyjna**: Włączono    
-   **Lokacja główna**: Włączono    
-   Lokacja dodatkowa: Niedostępne  

**Usuń przestarzałe dane wykrywania klienta**: To zadanie służy do usuwania przestarzałych rekordów klienta z bazy danych. Rekord oznaczony jako przestarzały jest zazwyczaj zastępowany przez nowszy rekord dotyczący tego samego klienta. Nowszy rekord staje się bieżącym rekordem klienta. Aby uzyskać informacje na temat odnajdywania, zobacz [Uruchamianie odnajdywania dla programu System Center Configuration Manager](../../../core/servers/deploy/configure/run-discovery.md).  

> [!IMPORTANT]  
> Jeśli jest włączona, należy skonfigurować to zadanie, by było uruchamiane z większym interwałem niż harmonogram odnajdywania pulsu. Umożliwia to klientowi wysłanie rekordu wykrywania interwału czasowego, korygującego stan przedawnienia.  

-   Centralna lokacja administracyjna: Niedostępne    
-   **Lokacja główna**: Niewłączona    
-   Lokacja dodatkowa: Niedostępne  

**Usuń przestarzałe lasu Lokacje i podsieci wykrywania**: To zadanie służy do usuwania danych dotyczących lokacji usługi Active Directory, podsieci i domen, które nie zostały odnalezione przez metodę odnajdywania lasu usługi Active Directory w ciągu ostatnich 30 dni. Usunięcie danych wykrywania, ale nie ma wpływu na granice, które są tworzone na podstawie tych danych odnajdywania. Aby uzyskać więcej informacji, zobacz [Uruchamianie odnajdywania dla programu System Center Configuration Manager](../../../core/servers/deploy/configure/run-discovery.md).  

-   **Centralna lokacja administracyjna**: Włączono    
-   **Lokacja główna**: Włączono    
-   Lokacja dodatkowa: Niedostępne  

**Usuń rekordy stanu wdrożenia klienta oddzielone**: To zadanie służy do okresowo przeczyścić tabeli, która zawiera informacje o stanie wdrożenia klienta. To zadanie spowoduje oczyszczenie rekordy skojarzone z przestarzałe lub wycofany z eksploatacji urządzeń.  
-   **Centralna lokacja administracyjna**: Włączono    
-   **Lokacja główna**: Włączono    
-   Lokacja dodatkowa: Niedostępne

**Usuń nieużywane wersje aplikacji**: To zadanie służy do usuwania wersji aplikacji, które nie są już używane. Aby uzyskać więcej informacji, zobacz [Korygowanie i zastępowanie aplikacji w programie System Center Configuration Manager](../../../apps/deploy-use/revise-and-supersede-applications.md).  

-   Centralna lokacja administracyjna: Niedostępne    
-   **Lokacja główna**: Włączono    
-   Lokacja dodatkowa: Niedostępne  

**Oceń członków kolekcji**: Ocenę członkostwa kolekcji można skonfigurować jako składnik lokacji. Aby uzyskać więcej informacji na temat składników lokacji, zobacz [Składniki lokacji dla programu System Center Configuration Manager](../../../core/servers/deploy/configure/site-components.md).  

-   Centralna lokacja administracyjna: Niedostępne    
-   **Lokacja główna**: Włączono    
-   Lokacja dodatkowa: Niedostępne  

**Monitoruj klucze**: To zadanie służy do monitorowania integralności kluczy podstawowych bazy danych programu Configuration Manager. Klucz podstawowy to kolumna (lub połączenie kolumn) który unikatowo identyfikuje jeden wiersz i odróżnia go od innych wierszy w tabeli bazy danych programu Microsoft SQL Server.  

-   **Centralna lokacja administracyjna**: Włączono    
-   **Lokacja główna**: Włączono    
-   Lokacja dodatkowa: Niedostępne  

**Odbuduj indeksy**: To zadanie służy do odbudowywania indeksów bazy danych programu Configuration Manager. Indeks to struktura bazy danych tworzona w tabeli bazy danych w celu przyspieszenia pobierania danych. Na przykład wyszukiwanie w indeksowanej kolumnie odbywa się znacznie szybciej niż wyszukiwanie kolumny, która nie jest indeksowana.

Aby zwiększyć wydajność, indeksy bazy danych programu Configuration Manager są często aktualizowane, aby zachować synchronizację ze stale zmieniającymi dane, które są przechowywane w bazie danych. To zadanie tworzy indeksy w kolumnach bazy danych, które są unikatowe co najmniej w 50 procentach, porzuca indeksy w kolumnach, które są unikatowe w mniej niż 50 procentach oraz odtwarza wszystkie istniejące indeksy spełniające kryteria unikatowości danych.  

-   **Centralna lokacja administracyjna**: Niewłączona    
-   **Lokacja główna**: Niewłączona    
-   **Lokacja dodatkowa**: Niewłączona  

**Podsumuj dane zainstalowanego oprogramowania**: To zadanie służy do podsumowania w jednym rekordzie ogólnym danych dotyczących zainstalowanego oprogramowania z wielu rekordów. Podsumowanie danych może skompresować ilość danych przechowywanych w bazie danych programu Configuration Manager. Aby uzyskać więcej informacji, zobacz [wprowadzenie do spisu oprogramowania w programie System Center Configuration Manager](../../clients/manage/inventory\introduction-to-software-inventory.md).  

-   Centralna lokacja administracyjna: Niedostępne    
-   **Lokacja główna**: Włączono    
-   Lokacja dodatkowa: Niedostępne  

**Podsumuj dane użycia pliku pomiaru oprogramowania**: To zadanie służy do podsumowania danych z wielu rekordów użycie pliku pomiaru oprogramowania w jednym rekordzie ogólnym. Podsumowanie danych może skompresować ilość danych przechowywanych w bazie danych programu Configuration Manager.

Można użyć tego zadania z **Podsumuj miesięczne dane użycia pomiaru oprogramowania** zadań do podsumowywania danych pomiaru użytkowania oprogramowania oraz do oszczędzania przestrzeni dyskowej w bazie danych programu Configuration Manager. Aby uzyskać więcej informacji, zobacz [Pomiar użytkowania oprogramowania w programie System Center Configuration Manager](../../../apps/deploy-use/monitor-app-usage-with-software-metering.md).  

-   Centralna lokacja administracyjna: Niedostępne    
-   **Lokacja główna**: Włączono    
-   Lokacja dodatkowa: Niedostępne  

**Podsumuj miesięczne dane użycia pomiaru oprogramowania**: To zadanie służy do podsumowania danych z wielu rekordów miesięcznego użytkowania w jednym rekordzie ogólnym. Podsumowanie danych może skompresować ilość danych przechowywanych w bazie danych programu Configuration Manager.

Można użyć tego zadania z **Podsumuj pliku dane użycia pomiaru oprogramowania** zadań do podsumowywania danych pomiaru użytkowania oprogramowania oraz do oszczędzania miejsca w bazie danych programu Configuration Manager. Aby uzyskać więcej informacji, zobacz [Pomiar użytkowania oprogramowania w programie System Center Configuration Manager](../../../apps/deploy-use/monitor-app-usage-with-software-metering.md).  

-   Centralna lokacja administracyjna: Niedostępne    
-   **Lokacja główna**: Włączono    
-   Lokacja dodatkowa: Niedostępne  

**Aktualizuj dostępny element docelowy aplikacji**: To zadanie służy do program Configuration Manager ponownego obliczenia mapowania wdrożeń zasad i aplikacji do zasobów w kolekcji. Gdy wdrażasz zasady lub aplikacje do kolekcji programu Configuration Manager tworzy wstępne mapowanie między obiektami, które można wdrożyć i członków kolekcji.

Te mapowania są przechowywane w tabeli, do której można się szybko odwołać. Gdy członkostwa kolekcji ulegają zmianom, przechowywane mapowania są aktualizowane, aby odzwierciedlać wprowadzone zmiany. Istnieje jednak możliwość mapowania nie zostaną odpowiednio zsynchronizowane. Przykładowo, jeśli lokacja nie przetworzy prawidłowo pliku powiadomienia, zmiana może nie zostać uwzględniona w zmianach mapowań. To zadanie odświeża mapowanie w oparciu o bieżące członkostwo kolekcji.  

-   Centralna lokacja administracyjna: Niedostępne    
-   **Lokacja główna**: Włączono    
-   Lokacja dodatkowa: Niedostępne  

**Aktualizacja tabel wykazu aplikacji**: To zadanie służy do synchronizacji pamięci podręcznej bazy danych witryny sieci Web katalogu aplikacji z najnowszymi informacjami o aplikacji. Zmiana konfiguracji tego zadania konserwacji powoduje zastosowanie tej konfiguracji do wszystkich lokacji głównych w hierarchii.  

-   Centralna lokacja administracyjna: Niedostępne    
-   **Lokacja główna**: Włączono    
-   Lokacja dodatkowa: Niedostępne  
