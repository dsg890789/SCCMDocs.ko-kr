---
title: Aktualizacje | Dokumentacja firmy Microsoft
description: "Więcej informacji na temat metody obsługi w konsoli o nazwie ** aktualizacje i obsługa ** który można łatwo zlokalizować i zainstalować zalecane aktualizacje."
ms.custom: na
ms.date: 07/31/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3a832943-580a-4a40-b454-961d0854ac2b
caps.latest.revision: "51"
caps.handback.revision: "0"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: d46aca88111d4ee0e96b75ca5a3ec57aa4274d6d
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="updates-for-system-center-configuration-manager"></a>Aktualizacje programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

System Center Configuration Manager korzysta z metody obsługi w konsoli o nazwie **aktualizacje i obsługa**. Ta metoda w konsoli ułatwia znajdowanie i instalowanie zalecanych aktualizacji infrastruktury programu Configuration Manager. Obsługi w konsoli jest uzupełniana przez aktualizacje poza pasmem, takie jak poprawki przeznaczone dla klientów chcących rozwiązać problemy, które mogą dotyczyć ich środowiska.  

> [!TIP]  
> Podczas zarządzania w lokacji programu System Center Configuration Manager i infrastruktury hierarchii, warunki *uaktualnienia*, *aktualizacji*, i *zainstalować* służą do opisywania trzy oddzielne pojęcia. Aby dowiedzieć się, jak każdego terminu jest używany, zobacz [o uaktualnienie, aktualizacji i instalacji](/sccm/core/understand/upgrade-update-install).


 **Poniższe tematy ułatwią zrozumienie, jak znaleźć i zainstalować różne typy aktualizacji programu System Center Configuration Manager:**  

-   [Instalacja aktualizacji w konsoli programu System Center Configuration Manager](../../../core/servers/manage/install-in-console-updates.md)  

-   [Użyj narzędzia połączenia z usługą programu System Center Configuration Manager](../../../core/servers/manage/use-the-service-connection-tool.md)  

-   [Używanie narzędzia rejestracji aktualizacji do importowania poprawek do programu System Center Configuration Manager](../../../core/servers/manage/use-the-update-registration-tool-to-import-hotfixes.md)  

-   [Użyj Instalatora poprawek do instalowania aktualizacji dla programu System Center Configuration Manager](../../../core/servers/manage/use-the-hotfix-installer-to-install-updates.md)  


Jeśli używasz gałęzi Technical Preview, zobacz [Technical Preview programu System Center Configuration Manager](/sccm/core/get-started/technical-preview) Aby uzyskać dodatkowe informacje dotyczące tego oddziału.


##  <a name="bkmk_Baselines"></a> Wersje linii bazowej i aktualizacji  
 Pierwszej wersji programu System Center Configuration Manager bieżącej gałęzi była wersji 1511, której wersji linii bazowej. Nowsze wersje linii bazowej zawierają wersję 1606 i 1702:

-   Po zainstalowaniu nowej lokacji w nowej hierarchii korzystaj z najnowszej wersji linii bazowej.  

-   Używasz wersji linii bazowej do uaktualnienia programu System Center 2012 Configuration Manager. Po uaktualnieniu do programu System Center Configuration Manager nie umożliwia wersje bazowe Pozostań na bieżąco i zamiast tego używać tylko [aktualizacje w konsoli](/sccm/core/servers/manage/install-in-console-updates) aktualizacji do najnowszej wersji.  

-   Okresowo są wydawane linii bazowej dodatkowe wersje. Korzystając z najnowszej wersji linii bazowej do zainstalowania nowej hierarchii, możesz uniknąć instalowania z nieaktualną wersją programu Configuration Manager następuje uaktualnienie dodatkowe infrastruktury można wyświetlić dane.  

Po zainstalowaniu wersji linii bazowej dodatkowe wersje programu Configuration Manager są dostępne jako aktualizacje w konsoli. Aktualizacje w konsoli umożliwiają zaktualizowanie infrastruktury do najnowszej wersji programu Configuration Manager.  

-   Zainstalowanie aktualizacji w konsoli powoduje zaktualizowanie wersji lokacji najwyższego poziomu.  

-   Aktualizacje, które będą instalowane w centralnej lokacji administracyjnej automatycznie zainstalować w podrzędnych lokacjach głównych, o ile nie jest blokowane przez okno obsługi, które zostały skonfigurowane w lokacji głównej.  

-   Należy ręcznie zaktualizować Lokacje dodatkowe do nowej wersji aktualizacji z poziomu konsoli.  

W przypadku zainstalowania aktualizacji pliki instalacyjne dla danej wersji aktualizacji są przechowywane na serwerze lokacji w folderze o nazwie CD.Latest. Aby uzyskać więcej informacji o tych plikach, zobacz [CD. Najnowszy folder programu System Center Configuration Manager](../../../core/servers/manage/the-cd.latest-folder.md).  

-   Możesz użyć plików na dysku CD. Najnowszy folder podczas odzyskiwania lokacji i zainstalować dodatkowe Lokacje w hierarchii, która nie korzysta już z wersji linii bazowej.  

-   Plików w folderze CD.Latest nie można używać do instalowania pierwszej lokacji nowej hierarchii ani do uaktualniania lokacji programu System Center 2012 Configuration Manager.  

Niektóre aktualizacje programu Configuration Manager są dostępne jako aktualizacje w konsoli dla istniejącej infrastruktury oraz jako nowa wersja linii bazowej.  

Poniżej przedstawiono wersje programu Configuration Manager dostępne jako linie bazowe lub aktualizacje albo jako oba te elementy:  

|Wersja |Data udostępnienia|[Data zakończenia wsparcia](/sccm/core/servers/manage/current-branch-versions-supported) |Linia bazowa|Aktualizacja w konsoli|  
|-------------|-----------|------------|--------------|------------------------|  
|[1706](/sccm/core/plan-design/changes/whats-new-in-version-1706)<br /><br /> 5.00.8540.1000|31 lipca 2017 r.|31 lipca 2018|Nie|Tak|
|[1702](/sccm/core/plan-design/changes/whats-new-in-version-1702)<br /><br /> 5.00.8498.1000|27 marca 2017 r.| 27 marca 2018|Tak|Tak|
|[1610](/sccm/core/plan-design/changes/whats-new-in-version-1610)<br /><br /> 5.00.8458.1000|18 listopada 2016 r.| 18 listopada 2017 r.|Nie|Tak|
|[1606](/sccm/core/plan-design/changes/whats-new-in-version-1606)<br /><br /> 5.00.8412.1000|22 lipca 2016 r.| 22 lipca 2017 r.|Nie|Tak|
|[1606](/sccm/core/plan-design/changes/whats-new-in-version-1606) z pakiet zbiorczy poprawek 1606 (KB3186654) </br></br>5.00.8412.1307 *(Uwaga 1)* |12 października 2016 r.| 12 października 2017 r.|Tak|Nie|
| 1602<br /><br /> 5.00.8355.1000|11 marca 2016 r.| 11 marca 2017 r.|Nie|Tak| 
| 1511 <br /><br /> 5.00.8325.1000|8 grudnia 2015 r.| 8 grudnia 2016 r.|Tak|Nie|  


*(Uwaga 1)*  Nośnika linii bazowej 1606 i 1702 są dostępne jako część programu Microsoft System Center 2016 lub System Center Configuration Manager (Current Branch i długoterminowe obsługi gałęzi) udostępnia w [Centrum usługi licencji woluminu](https://www.microsoft.com/Licensing/servicecenter/Downloads/DownloadsAndKeys.aspx) (firmy Microsoft VLSC). Na przykład w centrum VLSC można wyszukiwać *System Center Config Mgr (bieżącej gałęzi i LTSB)*, i jednocześnie 1606 i 1702 nośnika linii bazowej wersji są zwracane i dostępny do pobrania.

Aby sprawdzić wersję lokacji programu Configuration Manager, w lewym górnym rogu konsoli, gdzie są wyświetlane nowe wersje lokacji i konsoli, wybierz pozycję **Program System Center Configuration Manager — informacje** .  

##  <a name="bkmk_inconsole"></a> Aktualizacje w konsoli i obsługa  
 Realizując produkcji instalację gotowy programu System Center Configuration Manager, nazywana także bieżącej gałęzi, większość aktualizacji, które będą instalowane są dostępne za pomocą aktualizacji i obsługi kanału. Ta metoda umożliwia wyszukiwanie, pobieranie oraz udostępnianie aktualizacji dotyczących bieżącej wersji i konfiguracji infrastruktury. Obejmuje ona tylko aktualizacje zalecane przez firmę Microsoft dla wszystkich klientów.   
 Należą do nich następujące elementy:  

-   Nowe wersje, takie jak wersja 1610, 1702 lub 1706.  

-   Aktualizacje obejmujące nowe funkcje bieżącej wersji.

-   Poprawki dla danej wersji programu Configuration Manager i że muszą zainstalować wszyscy klienci.

Aktualizacje w konsoli zapewniają większą stabilność i zawierają rozwiązania często występujących problemów. Zastępują one aktualizacje dostępne dla wcześniejszych wersji produktu w postaci dodatków Service Pack, aktualizacji zbiorczych, poprawek dla wszystkich klientów i rozszerzenia usługi Microsoft Intune. Te aktualizacje mogą być stosowane do następujących elementów:  

-   Serwery głównych i centralnych lokacji administracyjnych  

-   Role i serwery systemu lokacji  

-   Wystąpienia dostawcy programu SMS  

-   Konsole programu Configuration Manager  

-   Klienci programu Configuration Manager  

Configuration Manager odnajduje nowe aktualizacje podczas synchronizacji z roli systemu lokacji punktu Usługi połączenia z usługą w chmurze firmy Microsoft i Centrum pobierania:  

-   Gdy punkt połączenia usługi jest w trybie online, lokacja jest codziennie synchronizowana z firmą Microsoft w celu automatycznego wyszukiwania nowych aktualizacji dotyczących danej infrastruktury.  Aby pobrać aktualizacje i plików redystrybucyjnych aktualizacji, korzysta z komputera, który hostuje rolę systemu lokacji punktu połączenia usługi **systemu** kontekstu do poniższej lokalizacji w Internecie: go.microsoft.com i witrynie download.microsoft.com. Aby uzyskać informacje o dodatkowych lokalizacji punktu połączenia usługi łączy się z, zobacz [wymagania dotyczące dostępu do Internetu](../../../core/servers/deploy/configure/about-the-service-connection-point.md#bkmk_urls) w [o połączenia z usługą punktu w programie System Center Configuration Manager](../../../core/servers/deploy/configure/about-the-service-connection-point.md).  

-   Gdy punkt połączenia usługi jest w trybie offline, użyj narzędzia połączenia usługi, aby ręcznie zsynchronizować zawartość z usługą firmy Microsoft w chmurze. Aby uzyskać więcej informacji, zobacz [Używanie narzędzia połączenia z usługą w programie System Center Configuration Manager](../../../core/servers/manage/use-the-service-connection-tool.md).  

-   Aktualizacje w konsoli eliminują konieczność osobnego znajdowania i instalowania poszczególnych aktualizacji, dodatków Service Pack oraz nowych funkcji.  

-   Możesz instalować tylko wybrane aktualizacje w konsoli, a w przypadku instalowania niektórych aktualizacji możesz wybrać funkcje do włączenia i używania. Aby uzyskać więcej informacji, zobacz [Włącz funkcje opcjonalne aktualizacji](../../../core/servers/manage/install-in-console-updates.md#bkmk_options).  

W przypadku instalowania aktualizacji w konsoli:  

-   Automatycznie jest przeprowadzane sprawdzanie wymagań wstępnych. Możesz również przeprowadzić ten test przed rozpoczęciem instalacji.  

-   Aktualizacja jest automatycznie instalowana w centralnej lokacji administracyjnej (jeśli istnieje) i w lokacjach głównych. Można kontrolować, gdy każdy serwer lokacji głównej mogą aktualizować swoją infrastrukturę, używając [usługi systemu windows dla serwerów lokacji](../../../core/servers/manage/service-windows.md).  

-   Po zaktualizowaniu serwera lokacji są automatycznie aktualizowane wszystkie powiązane role systemu lokacji (w tym wystąpienia dostawcy programu SMS). Konsole programu Configuration Manager monitować użytkownika konsoli, aby zaktualizować konsolę, po zainstalowaniu aktualizacji w lokacji.  

-   Aktualizacja klienta programu Configuration Manager, można wybrać opcję przetestowania aktualizacji w środowisku przedprodukcyjnym lub zastosować aktualizację natychmiast do wszystkich klientów.  

-   Po zaktualizowaniu lokacji głównej lokacje dodatkowe nie są automatycznie aktualizowane. Musisz zainicjować aktualizację lokacji dodatkowej.  

> [!NOTE]  
>  Wersja produkcyjna programu System Center Configuration Manager (wersji current branch), długoterminowe obsługi gałęzi i Technical Preview programu System Center Configuration Manager różni się od wersji. W związku z tym aktualizacje dotyczące jedna gałąź nie są dostępne jako aktualizacje w konsoli do innych działów. Aby uzyskać więcej informacji o dostępnych gałęzie, zobacz [która gałąź programu Configuration Manager należy używać?](/sccm/core/understand/which-branch-should-i-use)

##  <a name="bkmk_outofband"></a> Poprawki poza pasmem  
Niektóre poprawki wydane z ograniczoną dostępność w celu rozwiązania określonych problemów, lub mają zastosowanie do wszystkich klientów, ale nie można zainstalować przy użyciu metody w konsoli. Są one oferowane poza pasmem i nie można ich odnaleźć w usłudze firmy Microsoft w chmurze.  

Zwykle informacje o poprawkach poza pasmem z obsługą klienta firmy Microsoft, artykułu bazy wiedzy lub [blogu zespołu programu System Center Configuration Manager](https://blogs.technet.microsoft.com/configmgrteam) gdy szukamy pozwalających rozwiązać problem z wdrożeniem programu Configuration Manager.  

Te poprawki są instalowane ręcznie przy użyciu jednej z dwóch metod:  

-   **Narzędzie rejestracji aktualizacji:** To narzędzie umożliwia ręczne zaimportowanie poprawki do konsoli programu Configuration Manager, w którym można zainstalować aktualizacji jako użytkownik w konsoli aktualizacji, które są wykrywane automatycznie. Ta metoda jest używana w przypadku aktualizacji korzystających z następującej struktury nazw plików: **.update.exe**.  Pełna nazwa pliku dla tego typu poprawki podobny: **&lt;Produkt\>-&lt;wersji produktu\>-&lt;identyfikator artykułu bazy wiedzy\>-ConfigMgr.Update.exe**.  

     Aby uzyskać więcej informacji, zobacz [używanie narzędzia rejestracji aktualizacji do importowania poprawek do programu System Center Configuration Manager](../../../core/servers/manage/use-the-update-registration-tool-to-import-hotfixes.md).  

-   **Instalator poprawek:** To narzędzie umożliwia ręczne zainstalowanie poprawki, której nie można zainstalować przy użyciu metody w konsoli. Ta metoda jest używana w przypadku poprawek korzystających z następującej struktury nazw plików: **&lt;Product\>-&lt;product version\>-&lt;KB article ID\>-&lt;platform\>-&lt;language\>.exe**.

     Aby uzyskać więcej informacji, zobacz [używania Instalatora poprawek do instalowania aktualizacji dla programu System Center Configuration Manager](../../../core/servers/manage/use-the-hotfix-installer-to-install-updates.md).
