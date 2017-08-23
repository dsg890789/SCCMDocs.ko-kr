---
title: "Monitorować i planować zarządzanie energią | Dokumentacja firmy Microsoft"
description: "Dowiedz się, jak monitorować i planowanie w programie System Center Configuration Manager zarządzanie energią."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 507bf676-2679-4e4d-8831-3ffc9cf8557e
caps.latest.revision: "6"
caps.handback.revision: "0"
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.openlocfilehash: b308329635400438cebc4935efe79b46e607fd58
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="how-to-monitor-and-plan-for-power-management-in-system-center-configuration-manager"></a>Jak monitorować i planować zarządzanie energią w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Skorzystaj z poniższych informacji, aby monitorować i planować zarządzanie energią w programie System Center Configuration Manager.  

##  <a name="BKMK_How_to_use_reports"></a> Jak używać raportów do zarządzania energią  
 Zarządzanie energią w programie Configuration Manager udostępnia kilka raportów, które ułatwiają analizowanie zasilania zużycia i ustawień zasilania komputerów w organizacji. Te raporty mogą być pomocne podczas rozwiązywania problemów.  

 Aby móc korzystać z raportów dotyczących zarządzania energią, należy skonfigurować raportowanie dla swojej hierarchii. Aby uzyskać więcej informacji o raportach w programie Configuration Manager, zobacz [raportowania w programie System Center Configuration Manager](../../../../core/servers/manage/reporting.md).  

> [!NOTE]  
>  Informacje dotyczące zarządzania energią używane w codziennych raportach są przechowywane w bazie danych lokacji programu Configuration Manager przez 31 dni.  
>           Informacje dotyczące zarządzania energią używane w miesięcznych raportach są przechowywane w bazie danych lokacji programu Configuration Manager przez 13 miesięcy.  
>   
>  Podczas uruchamiania raportów podczas fazy monitorowania i zapewniania zgodności zarządzania energią, Zapisz lub wyeksportuj wyniki wszystkich raportów, które mają być przechowywane dane późniejszego porównania na wypadek, gdyby zostały później usunięte przez program Configuration Manager.  

## <a name="list-of-power-management-reports"></a>Lista raportów dotyczących zarządzania energią  
 Poniższa lista zawiera szczegóły dotyczące raportów zarządzania energią, które są dostępne w programie Configuration Manager.  

> [!NOTE]  
>  W raportach dotyczących zarządzania energią jest wyświetlana liczba fizycznych komputerów i wirtualnych komputerów w wybranej kolekcji. Jednak w raportach dotyczących zarządzania energią pokazywane są tylko informacje związane z zarządzaniem energią dla komputerów fizycznych.  

###  <a name="BKMK_Activity"></a> Raport Aktywność komputera  
 W raporcie **Aktywność komputera** przedstawiony jest wykres następujących działań komputera dla określonej kolekcji w określonym przedziale czasu:  

-   **Komputer — włączony** : komputer został włączony.  

-   **Monitor — włączony** : monitor został włączony.  

-   **Użytkownik — aktywny** : wykryto aktywność, której źródłem jest mysz lub klawiatura albo połączenie pulpitu zdalnego z komputerem.  

 Ten raport jest używany na etapach monitorowania, planowania i wymuszania w celu ułatwienia zrozumienia powiązania między aktywnością komputera, aktywnością monitora i aktywnością użytkownika w okresie 24 godzin. Jeśli raport jest uruchamiany dla kilku dni, dane z tego okresu są agregowane. Ten raport może pomóc w ustaleniu typowych godzin pracy (szczyt) i czasu poza godzinami pracy (poza szczytem) dla wybranej kolekcji w celu łatwiejszego podjęcia decyzji dotyczącej godzin, w których mają być stosowane skonfigurowane plany zarządzania energią.  

 Wykres przedstawia okresy, w których komputer może być włączony, ale nie występuje żadna aktywność użytkownika. Należy rozważyć zastosowanie bardziej restrykcyjnych ustawień zasilania w tym czasie w celu zmniejszenia kosztów energii zużywanej przez komputery, które są włączone, ale nie są używane. Komputer jest uznawany za aktywny w przypadku aktywności komputera, użytkownika lub monitora trwającej co najmniej minutę podczas godziny wyświetlanej na wykresie. Jeśli komputer nie zgłasza danych zarządzania energią, nie zostanie uwzględniony w raporcie **Aktywność komputera** .  

 Skonfiguruj ten raport przy użyciu następujących parametrów.  

#### <a name="required-report-parameters"></a>Wymagane parametry raportu  
 Aby uruchomić ten raport, należy określić następujące parametry.  

|Nazwa parametru|Opis|  
|--------------------|-----------------|  
|**Data rozpoczęcia**|Z listy rozwijanej wybierz datę rozpoczęcia dla tego raportu.|  
|**Data zakończenia (opcjonalnie)**|Z listy rozwijanej wybierz opcjonalną datę zakończenia dla tego raportu.|  
|**Nazwa kolekcji**|Z listy rozwijanej wybierz kolekcję, która ma być używana w tym raporcie.|  
|**Typ urządzenia**|Z listy rozwijanej wybierz typ komputera, dla którego chcesz utworzyć raport. Prawidłowe wartości to **wszystkie** (komputerów stacjonarnych i przenośnych) **pulpitu** (tylko komputerów stacjonarnych), i **Laptop** (tylko w przypadku komputerów przenośnych).|  

#### <a name="hidden-report-parameters"></a>Ukryte parametry raportu  
 Ten raport nie ma ukrytych parametrów, które można ustawić.  

#### <a name="report-links"></a>Linki do raportów  
 Jeśli nie określono wartości parametru **Data zakończenia (opcjonalnie)** , ten raport zawiera link do następującego raportu, który zawiera dalsze informacje.  

|Nazwa raportu|Szczegóły|  
|-----------------|-------------|  
|**Szczegóły aktywności komputera**|Użyj linku **Kliknij, aby uzyskać dodatkowe informacje** , aby wyświetlić listę aktywnych, nieaktywnych i niezgłaszających informacji komputerów dla określonej daty.<br /><br /> Aby uzyskać więcej informacji, zobacz [Computer Activity Details Report](#BKMK_Activity_Details) w tym temacie.|  

###  <a name="BKMK_Comp_Activity_by_computer"></a> Raport Aktywność komputera według komputera  
 W raporcie **Aktywność komputera według komputerów** przedstawiony jest wykres następujących aktywności określonego komputera w wybranym dniu:  

-   **Komputer — włączony** : komputer został włączony.  

-   **Monitor — włączony** : monitor został włączony.  

-   **Użytkownik — aktywny** : wykryto aktywność, której źródłem jest mysz lub klawiatura komputera albo połączenie pulpitu zdalnego z komputerem.  

 Ten raport może zostać uruchomiony niezależnie lub wywołany przez raport **Szczegóły aktywności komputera** .  

> [!NOTE]  
>  Informacje o aktywności komputera są zbierane z komputerów klienckich podczas spisu sprzętu. Zależnie od godziny, o której uruchamiany jest spis sprzętu, mogą być zbierane informacje o aktywności dotyczące zastosowanego szczytowego planu zasilania lub planu zasilania bez szczytów.  

 Skonfiguruj ten raport przy użyciu następujących parametrów.  

#### <a name="required-report-parameters"></a>Wymagane parametry raportu  
 Aby uruchomić ten raport, należy określić następujące parametry.  

|Nazwa parametru|Opis|  
|--------------------|-----------------|  
|**Data raportu**|Z listy rozwijanej wybierz datę dla tego raportu.|  
|**Nazwa komputera**|Wprowadź nazwę komputera, dla którego chcesz utworzyć raport.|  

#### <a name="hidden-report-parameters"></a>Ukryte parametry raportu  
 Ten raport nie ma ukrytych parametrów, które można ustawić.  

#### <a name="report-links"></a>Linki do raportów  
 Ten raport zawiera linki do następującego raportu, który zapewnia dodatkowe informacje na temat wybranej pozycji.  

|Nazwa raportu|Szczegóły|  
|-----------------|-------------|  
|**Szczegóły komputera**|Użyj linku **Kliknij, aby uzyskać dodatkowe informacje** , aby wyświetlić wszystkie możliwości zasilania, ustawienia zasilania i zastosowane plany zasilania dla wybranego komputera.|  

###  <a name="BKMK_Activity_Details"></a> Computer Activity Details report  
 W raporcie **Szczegóły aktywności komputera** wyświetlana jest lista aktywnych i nieaktywnych komputerów oraz możliwości ich usypiania i budzenia. Ten raport jest wywoływany przez [Computer Activity Report](#BKMK_Activity) i nie jest przeznaczony do uruchamiania bezpośrednio przez administratora lokacji.  

 Skonfiguruj ten raport przy użyciu następujących parametrów.  

#### <a name="required-report-parameters"></a>Wymagane parametry raportu  
 Aby uruchomić ten raport, należy określić następujące parametry.  

|Nazwa parametru|Opis|  
|--------------------|-----------------|  
|**Nazwa kolekcji**|Z listy rozwijanej wybierz kolekcję, która ma być używana w tym raporcie.|  
|**Data raportu**|Z listy rozwijanej wybierz datę dla tego raportu.|  
|**Godzina raportu**|Z listy rozwijanej wybierz godzinę w określonym dniu, o której ten raport ma zostać uruchomiony. Prawidłowe wartości należą do zakresu od **00:00** do **23:00**.|  
|**Stan komputera**|Z listy rozwijanej wybierz stan komputera, dla którego ten raport ma zostać uruchomiony. Prawidłowe wartości to **wszystkie** (komputerów, które były włączone lub wyłączone), **na** (komputerów, które zostały włączone), i **poza** (wyłączone w trybie uśpienia, komputery, które były włączone lub w hibernacji). Te wartości są zwracane tylko dla wybranego okresu raportowania.|  
|**Typ urządzenia**|Z listy rozwijanej wybierz typ komputera, dla którego chcesz utworzyć raport. Prawidłowe wartości to **wszystkie** (komputerów stacjonarnych i przenośnych) **pulpitu** (tylko komputerów stacjonarnych), i **Laptop** (tylko w przypadku komputerów przenośnych). Te wartości są zwracane tylko dla wybranego okresu raportowania.|  
|**Możliwość uśpienia**|Z listy rozwijanej wybierz odpowiednią opcję, jeśli chcesz, aby w raporcie były wyświetlane komputery z możliwością uśpienia. Prawidłowe wartości to **wszystkie** (zarówno komputery z możliwością i bez możliwości uśpienia), **nr** (komputerów, które mogą przejść w stan uśpienia), i **tak** (komputery, które są w stanie uśpienia).|  
|**Możliwość wybudzenia z uśpienia**|Z listy rozwijanej wybierz odpowiednią opcję, jeśli chcesz, aby w raporcie były wyświetlane komputery z możliwością wybudzenia z uśpienia. Prawidłowe wartości to **wszystkie** (zarówno komputery z możliwością i bez możliwości wybudzenia z uśpienia), **nr** (komputerów będących bez możliwości wybudzenia z uśpienia) i **tak** (komputery z możliwością wybudzenia z uśpienia).|  
|**Plan zasilania**|Z listy rozwijanej wybierz typy planów zasilania, które mają być wyświetlane w raporcie. Prawidłowe wartości to **wszystkie** (energii komputery, które nie mają zastosowane plany zarządzania, komputerów, na których zastosowano plan zarządzania energią; komputery wykluczone z zarządzania energią), **nie określono** (komputery, których nie zastosowano plan zarządzania energią), **zdefiniowane** (komputery, których zastosowano plan zarządzania energią), i **wykluczone** (komputery, które zostały wykluczone z zarządzania energią).|  
|**System operacyjny**|Z listy rozwijanej wybierz systemy operacyjne komputerów, które mają być wyświetlane w raporcie, lub wybierz pozycję **Wszystkie** w celu wyświetlenia wszystkich systemów operacyjnych.|  

#### <a name="hidden-report-parameters"></a>Ukryte parametry raportu  
 Ten raport nie ma ukrytych parametrów, które można ustawić.  

#### <a name="report-links"></a>Linki do raportów  
 Ten raport zawiera linki do następującego raportu, który zapewnia dodatkowe informacje na temat wybranej pozycji.  

|Nazwa raportu|Szczegóły|  
|-----------------|-------------|  
|**Aktywność komputera według komputerów**|Kliknij nazwę komputera, aby zobaczyć określonego działania dla tego komputera za pośrednictwem wybranego okresu raportowania. Działania te obejmują **komputera na** (komputer został włączony?), **monitorowania na** (monitor został włączony?), i **aktywnej użytkownika** (Wykryto aktywność komputera myszy, klawiatury lub połączeń usług pulpitu zdalnego).<br /><br /> Aby uzyskać więcej informacji, zobacz [Computer Activity by Computer Report](#BKMK_Comp_Activity_by_computer) w tym temacie.|  

###  <a name="BKMK_Computer_Details"></a> Raport Szczegóły komputera  
 Raport **Szczegóły komputera** przedstawia szczegółowe informacje na temat możliwości zasilania, ustawień zasilania i planów zasilania zastosowanych na określonym komputerze. Ten raport jest wywoływany przez raport **Aktywność komputera według komputerów** , raport **Komputery z wieloma planami zasilania** , raport **Możliwości zasilania** i raport **Szczegóły ustawień zasilania** . Ten raport nie jest przeznaczony do uruchamiania bezpośrednio przez administratora lokacji.  

#### <a name="required-report-parameters"></a>Wymagane parametry raportu  
 Aby uruchomić ten raport, należy określić następujące parametry.  

|Nazwa parametru|Opis|  
|--------------------|-----------------|  
|**Nazwa komputera**|Wprowadź nazwę komputera, dla którego chcesz utworzyć raport.|  
|**Tryb zasilania**|Z listy rozwijanej wybierz typ ustawień zasilania, które mają być wyświetlane w raporcie. Wybierz pozycję **Podłączony** , aby wyświetlić ustawienia zasilania skonfigurowane dla sytuacji, w której komputer jest podłączony, i pozycję **Zasilany z baterii** , aby wyświetlić ustawienia zasilania skonfigurowane dla komputera zasilanego z baterii.|  

#### <a name="hidden-report-parameters"></a>Ukryte parametry raportu  
 Ten raport nie ma ukrytych parametrów, które można ustawić.  

#### <a name="report-links"></a>Linki do raportów  
 Ten raport nie zawiera linków do innych raportów zarządzania energią.  

###  <a name="BKMK_Not_Reporting"></a> Raport Szczegóły komputerów bez zgłoszeń  
 Raport **Szczegóły komputerów bez zgłoszeń** przedstawia listę komputerów należących do określonej kolekcji, dla których nie zgłoszono żadnej aktywności dotyczącej zasilania w określonym dniu i godzinie. Ten raport jest wywoływany przez **Computer Activity Report** i nie jest przeznaczony do uruchamiania bezpośrednio przez administratora lokacji.  

> [!NOTE]  
>  Komputery zgłaszają informacje dotyczące zarządzania energią w ramach harmonogramu spisu sprzętu. Przed uznaniem komputera za niezgłaszający należy upewnić się, że zgłasza on spis sprzętu.  

 Skonfiguruj ten raport przy użyciu następujących parametrów.  

#### <a name="required-report-parameters"></a>Wymagane parametry raportu  
 Aby uruchomić ten raport, należy określić następujące parametry.  

|Nazwa parametru|Opis|  
|--------------------|-----------------|  
|**Nazwa kolekcji**|Z listy rozwijanej wybierz kolekcję, która ma być używana w tym raporcie.|  
|**Data raportu**|Z listy rozwijanej wybierz datę dla tego raportu.|  
|**Godzina raportu**|Z listy rozwijanej wybierz godzinę w określonym dniu, o której ten raport ma zostać uruchomiony. Prawidłowe wartości należą do zakresu od **00:00** do **23:00**.|  
|**Typ urządzenia**|Z listy rozwijanej wybierz typ komputera, dla którego chcesz utworzyć raport. Prawidłowe wartości to **wszystkie** (komputerów stacjonarnych i przenośnych) **pulpitu** (tylko komputerów stacjonarnych), i **Laptop** (tylko w przypadku komputerów przenośnych). Te wartości są zwracane tylko dla wybranego okresu raportowania.|  

#### <a name="hidden-report-parameters"></a>Ukryte parametry raportu  
 Ten raport nie ma ukrytych parametrów, które można ustawić.  

#### <a name="report-links"></a>Linki do raportów  
 Ten raport nie zawiera linków do innych raportów zarządzania energią.  

###  <a name="BKMK_Excluded"></a> Wykluczone komputery  
 **Wykluczone komputery** raport wyświetla listę komputerów w określonej kolekcji, które zostały wykluczone z zarządzania energią w programie Configuration Manager.  

 Skonfiguruj ten raport przy użyciu następujących parametrów.  

#### <a name="required-report-parameters"></a>Wymagane parametry raportu  
 Aby uruchomić ten raport, należy określić następujące parametry.  

|Nazwa parametru|Opis|  
|--------------------|-----------------|  
|**Kolekcja**|Z listy rozwijanej wybierz kolekcję dla tego raportu.|  
|**Przyczyna**|Z listy rozwijanej wybierz przyczynę wykluczenia komputerów z zarządzania energią. Można wyświetlić **wszystkie** (wszystkie wykluczone komputery), **wykluczone przez administratora** (tylko komputery wykluczone przez użytkownika administracyjnego), i **wykluczone przez użytkownika** (tylko komputery wykluczone przez użytkownika w programie Software Center).|  

#### <a name="hidden-report-parameters"></a>Ukryte parametry raportu  
 Ten raport nie ma ukrytych parametrów, które można ustawić.  

#### <a name="report-links"></a>Linki do raportów  
 Ten raport zawiera linki do następującego raportu, który zapewnia dodatkowe informacje na temat wybranej pozycji.  

|Nazwa raportu|Szczegóły|  
|-----------------|-------------|  
|**Szczegóły zasilania komputera**|Kliknij nazwę komputera, aby wyświetlić wszystkie możliwości zasilania, ustawienia zasilania i zastosowane plany zasilania dla wybranego komputera.<br /><br /> Aby uzyskać więcej informacji, zobacz [Computer Details Report](#BKMK_Computer_Details) w tym temacie.|  

###  <a name="BKMK_Multiple"></a> Komputery z wieloma planami zasilania  
 Raport **Komputery z wieloma planami zasilania** wyświetla listę komputerów należących do wielu kolekcji, w których stosowane są różne plany zasilania. Dla każdego komputera mającego ustawienia zasilania, które mogą powodować konflikt, w tym raporcie wyświetlana jest nazwa komputera i zastosowany plan zasilania dla każdej kolekcji, do której należy komputer.  

> [!IMPORTANT]  
>  Jeśli komputer jest członkiem wielu kolekcji, gdzie każda kolekcja ma różne plany zasilania, najmniej restrykcyjny plan zasilania zostaną zastosowane.  
>   
>  Jeśli komputer jest członkiem wielu kolekcji, gdzie każda kolekcja ma godzin wznowienia różnych, będzie można użyć godzina najbliższa północy.  

 Skonfiguruj ten raport przy użyciu następujących parametrów.  

#### <a name="required-report-parameters"></a>Wymagane parametry raportu  
 Aby uruchomić ten raport, należy określić następujące parametry.  

|Nazwa parametru|Opis|  
|--------------------|-----------------|  
|**Nazwa kolekcji**|Z listy rozwijanej wybierz kolekcję dla tego raportu.|  

#### <a name="hidden-report-parameters"></a>Ukryte parametry raportu  
 Ten raport nie ma ukrytych parametrów, które można ustawić.  

#### <a name="report-links"></a>Linki do raportów  
 Ten raport zawiera linki do następującego raportu, który zapewnia dodatkowe informacje na temat wybranej pozycji.  

|Nazwa raportu|Szczegóły|  
|-----------------|-------------|  
|**Szczegóły zasilania komputera**|Kliknij nazwę komputera, aby wyświetlić wszystkie możliwości zasilania, ustawienia zasilania i zastosowane plany zasilania dla wybranego komputera.<br /><br /> Aby uzyskać więcej informacji, zobacz [Computer Details Report](#BKMK_Computer_Details) w tym temacie.|  

###  <a name="BKMK_Consumption"></a> Raport Zużycie energii  
 Raport **Zużycie energii** zawiera następujące informacje:  

-   Wykres przedstawiający całkowite miesięczne zużycie energii przez komputery w kilowatach na godzinę (kWh) w określonej kolekcji i w określonym okresie.  

-   Wykres przedstawiający średnie miesięczne zużycie energii w kilowatach na godzinę (kWh) przez poszczególne komputery w określonej kolekcji i w określonym okresie.  

-   Tabelę przedstawiającą całkowite miesięczne zużycie energii w kilowatach na godzinę (kWh) oraz średnie zużycie energii przez komputery w określonej kolekcji i w określonym okresie.  

 Te informacje mogą ułatwić zrozumienie trendów zużycia energii w Twoim środowisku. Po zastosowaniu planu zasilania do komputerów w wybranej kolekcji zużycie energii przez komputery powinno ulec zmniejszeniu.  

> [!NOTE]  
>  Dodanie lub usunięcie elementów członkowskich z kolekcji po zastosowaniu planu zasilania będzie mieć wpływ na wyniki wyświetlane w raporcie **Zużycie energii** i może utrudnić porównanie wyników z fazy monitorowania i planowania oraz fazy wymuszania.  

 Skonfiguruj ten raport przy użyciu następujących parametrów.  

#### <a name="required-report-parameters"></a>Wymagane parametry raportu  
 Aby uruchomić ten raport, należy określić następujące parametry.  

|Nazwa parametru|Opis|  
|--------------------|-----------------|  
|**Data rozpoczęcia**|Z listy rozwijanej wybierz datę rozpoczęcia dla tego raportu.|  
|**Data zakończenia**|Z listy rozwijanej wybierz datę zakończenia dla tego raportu.|  
|**Nazwa kolekcji**|Z listy rozwijanej wybierz kolekcję dla tego raportu.|  
|**Typ urządzenia**|Z listy rozwijanej wybierz typ komputera, dla którego chcesz utworzyć raport. Prawidłowe wartości to **wszystkie** (komputerów stacjonarnych i przenośnych) **pulpitu** (tylko komputerów stacjonarnych), i **Laptop** (tylko w przypadku komputerów przenośnych). Te wartości są zwracane tylko dla wybranego okresu raportowania.|  

#### <a name="hidden-report-parameters"></a>Ukryte parametry raportu  
 Opcjonalnie można określić następujące ukryte parametry w celu zmiany zachowania tego raportu.  

|Nazwa parametru|Opis|  
|--------------------|-----------------|  
|**Komputer stacjonarny jest włączony**|Określ zużycie energii przez włączony komputer stacjonarny. Domyślna wartość to **0,07** kW na godzinę.|  
|**Komputer przenośny jest włączony**|Określ zużycie energii przez włączony komputer przenośny. Domyślna wartość to **0,02** kW na godzinę.|  
|**Komputer stacjonarny jest uśpiony**|Określ zużycie energii przez komputer stacjonarny wprowadzony w stan uśpienia. Domyślna wartość to **0,003** kW na godzinę.|  
|**Komputer przenośny jest uśpiony**|Określ zużycie energii przez komputer przenośny wprowadzony w stan uśpienia. Domyślna wartość to **0,001** kW na godzinę.|  
|**Komputer stacjonarny jest wyłączony**|Określ zużycie energii przez wyłączony komputer stacjonarny. Domyślna wartość to **0** kW na godzinę.|  
|**Komputer przenośny jest wyłączony**|Określ zużycie energii przez wyłączony komputer przenośny. Domyślna wartość to **0** kW na godzinę.|  
|**Monitor komputera stacjonarnego jest włączony**|Określ zużycie energii przez włączony monitor komputera stacjonarnego. Domyślna wartość to **0,028** kW na godzinę.|  
|**Monitor komputera przenośnego jest włączony**|Określ zużycie energii przez włączony monitor komputera przenośnego. Domyślna wartość to **0** kW na godzinę.|  

#### <a name="report-links"></a>Linki do raportów  
 Ten raport nie zawiera linków do innych raportów zarządzania energią.  

###  <a name="BKMK_Consumption_by_Day"></a> Raport Dzienne zużycie energii  
 Raport **Dzienne zużycie energii** zawiera następujące informacje:  

-   Wykres przedstawiający całkowite dzienne zużycie energii przez komputery w kilowatach na godzinę (kWh) w określonej kolekcji w ciągu ostatnich 31 dni.  

-   Wykres przedstawiający średnie dzienne zużycie energii w kilowatach na godzinę (kWh) przez poszczególne komputery w określonej kolekcji w ciągu ostatnich 31 dni.  

-   Tabelę przedstawiającą całkowite dzienne zużycie energii w kilowatach na godzinę (kWh) oraz średnie zużycie energii przez komputery w określonej kolekcji w ciągu ostatnich 31 dni.  

 Te informacje mogą ułatwić zrozumienie trendów zużycia energii w Twoim środowisku. Po zastosowaniu planu zasilania do komputerów w wybranej kolekcji zużycie energii przez komputery powinno ulec zmniejszeniu.  

> [!NOTE]  
>  Dodanie lub usunięcie elementów członkowskich z kolekcji po zastosowaniu planu zasilania będzie mieć wpływ na wyniki wyświetlane w raporcie **Zużycie energii** i może utrudnić porównanie wyników z fazy monitorowania i planowania oraz fazy wymuszania.  

 Skonfiguruj ten raport przy użyciu następujących parametrów.  

#### <a name="required-report-parameters"></a>Wymagane parametry raportu  
 Aby uruchomić ten raport, należy określić następujące parametry.  

|Nazwa parametru|Opis|  
|--------------------|-----------------|  
|**Kolekcja**|Z listy rozwijanej wybierz kolekcję dla tego raportu.|  
|**Device Type**|Z listy rozwijanej wybierz typ komputera, dla którego chcesz utworzyć raport. Prawidłowe wartości to **wszystkie** (komputerów stacjonarnych i przenośnych) **pulpitu** (tylko komputerów stacjonarnych), i **Laptop** (tylko w przypadku komputerów przenośnych). Te wartości są zwracane tylko dla wybranego okresu raportowania.|  

#### <a name="hidden-report-parameters"></a>Ukryte parametry raportu  
 Opcjonalnie można określić następujące ukryte parametry w celu zmiany zachowania tego raportu.  

|Nazwa parametru|Opis|  
|--------------------|-----------------|  
|**Komputer stacjonarny jest włączony**|Określ zużycie energii przez włączony komputer stacjonarny. Domyślna wartość to **0,07** kW na godzinę.|  
|**Komputer przenośny jest włączony**|Określ zużycie energii przez włączony komputer przenośny. Domyślna wartość to **0,02** kW na godzinę.|  
|**Komputer stacjonarny jest uśpiony**|Określ zużycie energii przez komputer stacjonarny wprowadzony w stan uśpienia. Domyślna wartość to **0,003** kW na godzinę.|  
|**Komputer przenośny jest uśpiony**|Określ zużycie energii przez komputer przenośny wprowadzony w stan uśpienia. Domyślna wartość to **0,001** kW na godzinę.|  
|**Komputer stacjonarny jest wyłączony**|Określ zużycie energii przez wyłączony komputer stacjonarny. Domyślna wartość to **0** kW na godzinę.|  
|**Komputer przenośny jest wyłączony**|Określ zużycie energii przez wyłączony komputer przenośny. Domyślna wartość to **0** kW na godzinę.|  
|**Monitor komputera stacjonarnego jest włączony**|Określ zużycie energii przez włączony monitor komputera stacjonarnego. Domyślna wartość to **0,028** kW na godzinę.|  
|**Monitor komputera przenośnego jest włączony**|Określ zużycie energii przez włączony monitor komputera przenośnego. Domyślna wartość to **0** kW na godzinę.|  

#### <a name="report-links"></a>Linki do raportów  
 Ten raport nie zawiera linków do innych raportów zarządzania energią.  

###  <a name="BKMK_Cost"></a> Raport Koszt energii  
 Raport **Koszt energii** zawiera następujące informacje:  

-   Wykres przedstawiający całkowity miesięczny koszt energii zużytej przez komputery w określonej kolekcji i w określonym okresie.  

-   Wykres przedstawiający średni miesięczny koszt energii zużytej przez poszczególne komputery w określonej kolekcji i w określonym okresie.  

-   Tabelę przedstawiającą całkowity miesięczny koszt oraz średni miesięczny koszt energii zużytej przez komputery w określonej kolekcji w ciągu ostatnich 31 dni.  

 Te informacje mogą ułatwić zrozumienie trendów kosztów energii w środowisku. Po zastosowaniu planu zasilania do komputerów w wybranej kolekcji koszt energii zużywanej przez komputery powinien ulec zmniejszeniu.  

 Skonfiguruj ten raport przy użyciu następujących parametrów.  

#### <a name="required-report-parameters"></a>Wymagane parametry raportu  
 Aby uruchomić ten raport, należy określić następujące parametry.  

|Nazwa parametru|Opis|  
|--------------------|-----------------|  
|**Data rozpoczęcia**|Z listy rozwijanej wybierz datę rozpoczęcia dla tego raportu.|  
|**Data zakończenia**|Z listy rozwijanej wybierz datę zakończenia dla tego raportu.|  
|**Koszt kWh**|Określ koszt kWh energii elektrycznej. Wartość domyślna to **0,09**.<br /><br /> Jednostkę waluty używaną w tym raporcie można zmienić w sekcji parametrów ukrytych.|  
|**Nazwa kolekcji**|Z listy rozwijanej wybierz kolekcję, która ma być używana w tym raporcie.|  
|**Typ urządzenia**|Z listy rozwijanej wybierz typ komputera, dla którego chcesz utworzyć raport. Prawidłowe wartości to **wszystkie** (komputerów stacjonarnych i przenośnych) **pulpitu** (tylko komputerów stacjonarnych), i **Laptop** (tylko w przypadku komputerów przenośnych). Te wartości są zwracane tylko dla wybranego okresu raportowania.|  

#### <a name="hidden-report-parameters"></a>Ukryte parametry raportu  
 Opcjonalnie można określić następujące ukryte parametry w celu zmiany zachowania tego raportu.  

|Nazwa parametru|Opis|  
|--------------------|-----------------|  
|**Komputer stacjonarny jest włączony**|Określ zużycie energii przez włączony komputer stacjonarny. Domyślna wartość to **0,07** kW na godzinę.|  
|**Komputer przenośny jest włączony**|Określ zużycie energii przez włączony komputer przenośny. Domyślna wartość to **0,02** kW na godzinę.|  
|**Komputer stacjonarny jest uśpiony**|Określ zużycie energii przez komputer stacjonarny wprowadzony w stan uśpienia. Domyślna wartość to **0,003** kW na godzinę.|  
|**Komputer przenośny jest uśpiony**|Określ zużycie energii przez komputer przenośny wprowadzony w stan uśpienia. Domyślna wartość to **0,001** kW na godzinę.|  
|**Komputer stacjonarny jest wyłączony**|Określ zużycie energii przez wyłączony komputer stacjonarny. Domyślna wartość to **0** kW na godzinę.|  
|**Komputer przenośny jest wyłączony**|Określ zużycie energii przez wyłączony komputer przenośny. Domyślna wartość to **0** kW na godzinę.|  
|**Monitor komputera stacjonarnego jest włączony**|Określ zużycie energii przez włączony monitor komputera stacjonarnego. Domyślna wartość to **0,028** kW na godzinę.|  
|**Monitor komputera przenośnego jest włączony**|Określ zużycie energii przez włączony monitor komputera przenośnego. Domyślna wartość to **0** kW na godzinę.|  
|**Waluta**|Określ etykietę waluty, która ma być używana w tym raporcie. Wartość domyślna to **USD ($)**.|  

#### <a name="report-links"></a>Linki do raportów  
 Ten raport nie zawiera linków do innych raportów zarządzania energią.  

###  <a name="BKMK_Cost_by_Day"></a> Raport Dzienny koszt energii  
 Raport **Dzienny koszt energii** zawiera następujące informacje:  

-   Wykres przedstawiający całkowity dzienny koszt energii zużytej przez komputery w określonej kolekcji w ciągu ostatnich 31 dni.  

-   Wykres przedstawiający średni dzienny koszt energii zużytej przez poszczególne komputery w określonej kolekcji w ciągu ostatnich 31 dni.  

-   Tabelę przedstawiającą całkowity dzienny koszt oraz średni dzienny koszt energii zużytej przez komputery w określonej kolekcji w ciągu ostatnich 31 dni.  

 Te informacje mogą ułatwić zrozumienie trendów kosztów energii w środowisku. Po zastosowaniu planu zasilania do komputerów w wybranej kolekcji koszt energii zużywanej przez komputery powinien ulec zmniejszeniu.  

 Skonfiguruj ten raport przy użyciu następujących parametrów.  

#### <a name="required-report-parameters"></a>Wymagane parametry raportu  
 Aby uruchomić ten raport, należy określić następujące parametry.  

|Nazwa parametru|Opis|  
|--------------------|-----------------|  
|**Nazwa kolekcji**|Z listy rozwijanej wybierz kolekcję, która ma być używana w tym raporcie.|  
|**Typ urządzenia**|Z listy rozwijanej wybierz typ komputera, dla którego chcesz utworzyć raport. Prawidłowe wartości to **wszystkie** (komputerów stacjonarnych i przenośnych) **pulpitu** (tylko komputerów stacjonarnych), i **Laptop** (tylko w przypadku komputerów przenośnych). Te wartości są zwracane tylko dla wybranego okresu raportowania.|  
|**Koszt kWh**|Określ koszt kWh energii elektrycznej. Wartość domyślna to **0,09**.<br /><br /> Jednostkę waluty używaną w tym raporcie można zmienić w sekcji parametrów ukrytych.|  

#### <a name="hidden-report-parameters"></a>Ukryte parametry raportu  
 Opcjonalnie można określić następujące ukryte parametry w celu zmiany zachowania tego raportu.  

|Nazwa parametru|Opis|  
|--------------------|-----------------|  
|**Komputer stacjonarny jest włączony**|Określ zużycie energii przez włączony komputer stacjonarny. Domyślna wartość to **0,07** kW na godzinę.|  
|**Komputer przenośny jest włączony**|Określ zużycie energii przez włączony komputer przenośny. Domyślna wartość to **0,02** kW na godzinę.|  
|**Komputer stacjonarny jest uśpiony**|Określ zużycie energii przez komputer stacjonarny wprowadzony w stan uśpienia. Domyślna wartość to **0,003** kW na godzinę.|  
|**Komputer przenośny jest uśpiony**|Określ zużycie energii przez komputer przenośny wprowadzony w stan uśpienia. Domyślna wartość to **0,001** kW na godzinę.|  
|**Komputer stacjonarny jest wyłączony**|Określ zużycie energii przez wyłączony komputer stacjonarny. Domyślna wartość to **0** kW na godzinę.|  
|**Komputer przenośny jest wyłączony**|Określ zużycie energii przez wyłączony komputer przenośny. Domyślna wartość to **0** kW na godzinę.|  
|**Monitor komputera stacjonarnego jest włączony**|Określ zużycie energii przez włączony monitor komputera stacjonarnego. Domyślna wartość to **0,028** kW na godzinę.|  
|**Monitor komputera przenośnego jest włączony**|Określ zużycie energii przez włączony monitor komputera przenośnego. Domyślna wartość to **0** kW na godzinę.|  
|**Waluta**|Określ etykietę waluty, która ma być używana w tym raporcie. Wartość domyślna to **USD ($)**.|  

#### <a name="report-links"></a>Linki do raportów  
 Ten raport nie zawiera linków do innych raportów zarządzania energią.  

###  <a name="BKMK_Environmental_Impact"></a> Raport Wpływ na środowisko  
 Raport **Wpływ na środowisko** zawiera następujące informacje:  

-   Wykres przedstawiający Całkowity miesięczny CO2 generowaną miesięcznie (w tonach) przez komputery w określonej kolekcji w określonym przedziale czasu.  

-   Wykres przedstawiający średnie miesięczne CO2 generowaną miesięcznie (w tonach) przez poszczególne komputery w określonej kolekcji w określonym przedziale czasu.  

-   Tabelę przedstawiającą Całkowity miesięczny CO2 wygenerowany oraz średni miesięczny CO2 generowany dla komputerów w określonej kolekcji w określonym przedziale czasu.  

 **Wpływ na środowisko** raportu oblicza ilość CO2 wygenerowanego (w tonach) na podstawie czasu, przez który komputer lub monitor był włączony w okresie 24 godzin.  

 Skonfiguruj ten raport przy użyciu następujących parametrów.  

#### <a name="required-report-parameters"></a>Wymagane parametry raportu  
 Aby uruchomić ten raport, należy określić następujące parametry.  

|Nazwa parametru|Opis|  
|--------------------|-----------------|  
|**Data rozpoczęcia raportu**|Z listy rozwijanej wybierz datę rozpoczęcia dla tego raportu.|  
|**Data zakończenia raportu**|Z listy rozwijanej wybierz datę zakończenia dla tego raportu.|  
|**Nazwa kolekcji**|Z listy rozwijanej wybierz kolekcję dla tego raportu.|  
|**Typ urządzenia**|Z listy rozwijanej wybierz typ komputera, dla którego chcesz utworzyć raport. Prawidłowe wartości to **wszystkie** (komputerów stacjonarnych i przenośnych) **pulpitu** (tylko komputerów stacjonarnych), i **Laptop** (tylko w przypadku komputerów przenośnych). Te wartości są zwracane tylko dla wybranego okresu raportowania.|  

#### <a name="hidden-report-parameters"></a>Ukryte parametry raportu  
 Opcjonalnie można określić następujące ukryte parametry w celu zmiany zachowania tego raportu.  

|Nazwa parametru|Opis|  
|--------------------|-----------------|  
|**Komputer stacjonarny jest włączony**|Określ zużycie energii przez włączony komputer stacjonarny. Domyślna wartość to **0,07** kW na godzinę.|  
|**Komputer przenośny jest włączony**|Określ zużycie energii przez włączony komputer przenośny. Domyślna wartość to **0,02** kW na godzinę.|  
|**Komputer stacjonarny jest uśpiony**|Określ zużycie energii przez komputer stacjonarny wprowadzony w stan uśpienia. Domyślna wartość to **0,003** kW na godzinę.|  
|**Komputer przenośny jest uśpiony**|Określ zużycie energii przez komputer przenośny wprowadzony w stan uśpienia. Domyślna wartość to **0,001** kW na godzinę.|  
|**Komputer stacjonarny jest wyłączony**|Określ zużycie energii przez wyłączony komputer stacjonarny. Domyślna wartość to **0** kW na godzinę.|  
|**Komputer przenośny jest wyłączony**|Określ zużycie energii przez wyłączony komputer przenośny. Domyślna wartość to **0** kW na godzinę.|  
|**Monitor komputera stacjonarnego jest włączony**|Określ zużycie energii przez włączony monitor komputera stacjonarnego. Domyślna wartość to **0,028** kW na godzinę.|  
|**Monitor komputera przenośnego jest włączony**|Określ zużycie energii przez włączony monitor komputera przenośnego. Domyślna wartość to **0** kW na godzinę.|  
|**Współczynnik emisji dwutlenku węgla (w tonach/kWh)** (mieszanka CO2)|Określ wartość współczynnika emisji dwutlenku węgla (w tonach/kWh), którą można zwykle uzyskać od dostawcy energii elektrycznej. Wartość domyślna to **0,0015** ton na kWh.|  

#### <a name="report-links"></a>Linki do raportów  
 Ten raport nie zawiera linków do innych raportów zarządzania energią.  

###  <a name="BKMK_Environmental_Impact_by_Day"></a> Raport Dzienny wpływ na środowisko  
 Raport **Dzienny wpływ na środowisko** zawiera następujące informacje:  

-   Wykres przedstawiający całkowity dzienny CO2 generowaną miesięcznie (w tonach) przez komputery w określonej kolekcji w ciągu ostatnich 31 dni.  

-   Wykres przedstawiający średni dzienny CO2 generowaną miesięcznie (w tonach) przez poszczególne komputery w określonej kolekcji w ciągu ostatnich 31 dni.  

-   Tabelę przedstawiającą całkowita codzienne CO2 generowany i średnie dzienne CO2 generowaną dziennie przez komputery w określonej kolekcji w ciągu ostatnich 31 dni.  

 **Dzienny wpływ na** raportu oblicza ilość CO2 wygenerowanego (w tonach) na podstawie czasu, przez który komputer lub monitor był włączony w okresie 24 godzin.  

#### <a name="required-report-parameters"></a>Wymagane parametry raportu  
 Aby uruchomić ten raport, należy określić następujące parametry.  

|Nazwa parametru|Opis|  
|--------------------|-----------------|  
|**Nazwa kolekcji**|Z listy rozwijanej wybierz kolekcję dla tego raportu.|  
|**Typ urządzenia**|Z listy rozwijanej wybierz typ komputera, dla którego chcesz utworzyć raport. Prawidłowe wartości to **wszystkie** (komputerów stacjonarnych i przenośnych) **pulpitu** (tylko komputerów stacjonarnych), i **Laptop** (tylko w przypadku komputerów przenośnych). Te wartości są zwracane tylko dla wybranego okresu raportowania.|  

#### <a name="hidden-report-parameters"></a>Ukryte parametry raportu  
 Opcjonalnie można określić następujące ukryte parametry w celu zmiany zachowania tego raportu.  

|Nazwa parametru|Opis|  
|--------------------|-----------------|  
|**Komputer stacjonarny jest włączony**|Określ zużycie energii przez włączony komputer stacjonarny. Wartość domyślna to **0,07** kWh.|  
|**Komputer przenośny jest włączony**|Określ zużycie energii przez włączony komputer przenośny. Wartość domyślna to **0,02** kWh.|  
|**Komputer stacjonarny jest wyłączony**|Określ zużycie energii przez wyłączony komputer stacjonarny. Wartość domyślna to **0** kWh.|  
|**Komputer przenośny jest wyłączony**|Określ zużycie energii przez wyłączony komputer przenośny. Wartość domyślna to **0** kWh.|  
|**Komputer stacjonarny jest uśpiony**|Określ zużycie energii przez komputer stacjonarny wprowadzony w stan uśpienia. Wartość domyślna to **0,003** kWh.|  
|**Komputer przenośny jest uśpiony**|Określ zużycie energii przez komputer przenośny wprowadzony w stan uśpienia. Wartość domyślna to **0,001** kWh.|  
|**Monitor komputera stacjonarnego jest włączony**|Określ zużycie energii przez włączony monitor komputera stacjonarnego. Wartość domyślna to **0,028** kWh.|  
|**Monitor komputera przenośnego jest włączony**|Określ zużycie energii przez włączony monitor komputera przenośnego. Wartość domyślna to **0** kWh.|  
|**Współczynnik emisji dwutlenku węgla (w tonach/kWh)** (mieszanka CO2)|Określ wartość współczynnika emisji dwutlenku węgla (w tonach/kWh), którą można zwykle uzyskać od dostawcy energii elektrycznej. Wartość domyślna to **0,0015** ton na kWh.|  

#### <a name="report-links"></a>Linki do raportów  
 Ten raport nie zawiera linków do innych raportów zarządzania energią.  

###  <a name="BKMK_Insomnia_Computer_Details"></a> Raport Szczegóły braku usypiania zasilania na komputerze  
 Raport **Szczegóły braku usypiania zasilania na komputerze** zawiera listę komputerów, które nie zostały wprowadzone w tryb uśpienia lub hibernacji z określonego powodu w określonym przedziale czasu. Ten raport jest wywoływany przez **Raport o braku usypiania zasilania na komputerze** i nie jest przeznaczony do uruchamiania bezpośrednio przez administratora lokacji.  

 **Raport o braku usypiania** wyświetla komputery jako **Bez możliwości uśpienia** , gdy nie można wprowadzić ich w tryb uśpienia i pozostawały włączone przez cały określony przedział czasu raportu. Raport wyświetla komputery jako **Bez możliwości hibernacji** , gdy nie można wprowadzić ich w tryb hibernacji i pozostawały włączone przez cały określony przedział czasu raportu.  

> [!NOTE]  
>  Funkcja zarządzania energią może gromadzić informacje o przyczynach uniemożliwiających komputerom przejście w tryb uśpienia lub hibernacji tylko w przypadku komputerów z systemem Windows 7 lub Windows Server 2008 R2.  

 Skonfiguruj ten raport przy użyciu następujących parametrów.  

#### <a name="required-report-parameters"></a>Wymagane parametry raportu  
 Aby uruchomić ten raport, należy określić następujące parametry.  

|Nazwa parametru|Opis|  
|--------------------|-----------------|  
|**Nazwa kolekcji**|Z listy rozwijanej wybierz kolekcję, która ma być używana w tym raporcie.|  
|**Interwał raportowania (dni)**|Określ liczbę dni, które mają zostać objęte raportem. Domyślna wartość to **7** dni.|  
|**Przyczyna bezsenności**|Z listy rozwijanej wybierz jedną z przyczyn, która może uniemożliwiać komputerom przejście w tryb uśpienia lub hibernacji.|  

#### <a name="hidden-report-parameters"></a>Ukryte parametry raportu  
 Ten raport nie ma ukrytych parametrów, które można ustawić.  

#### <a name="report-links"></a>Linki do raportów  
 Ten raport zawiera linki do następującego raportu, który zapewnia dodatkowe informacje na temat wybranej pozycji.  

|Nazwa raportu|Szczegóły|  
|-----------------|-------------|  
|**Szczegóły komputera**|Użyj linku **Kliknij, aby uzyskać dodatkowe informacje** , aby wyświetlić wszystkie możliwości zasilania, ustawienia zasilania i zastosowane plany zasilania dla wybranego komputera.<br /><br /> Aby uzyskać więcej informacji, zobacz [Computer Details Report](#BKMK_Computer_Details) w tym temacie.|  

###  <a name="BKMK_Insomnia"></a> Insomnia report  
 **Raport o braku usypiania** przedstawia listę typowych przyczyn, które uniemożliwiały włączanie stanu uśpienia i hibernacji na komputerach, oraz liczbę komputerów, których te przyczyny dotyczyły, w określonym przedziale czasu. Istnieje wiele przyczyn, które mogą uniemożliwiać wprowadzenie komputera w stan uśpienia lub hibernacji, takich jak proces uruchomiony na komputerze, otwarta sesja pulpitu zdalnego albo brak zdolności do przechodzenia w tryb uśpienia lub hibernacji. Z poziomu tego raportu można otworzyć raport **Szczegóły braku usypiania zasilania na komputerze** , który wyświetla listę komputerów, których dotyczyły poszczególne przyczyny uniemożliwiające przejście komputerów w tryb uśpienia lub hibernacji.  

 Raport dotyczący braku usypiania wyświetla komputery jako **Bez możliwości uśpienia** , gdy nie można wprowadzić ich w tryb uśpienia i pozostawały włączone przez cały określony przedział czasu raportu. Raport wyświetla komputery jako **Bez możliwości hibernacji** , gdy nie można wprowadzić ich w tryb hibernacji i pozostawały włączone przez cały określony przedział czasu raportu.  

> [!NOTE]  
>  Funkcja zarządzania energią może gromadzić informacje o przyczynach uniemożliwiających komputerom przejście w tryb uśpienia lub hibernacji tylko w przypadku komputerów z systemem Windows 7 lub Windows Server 2008 R2.  

 Skonfiguruj ten raport przy użyciu następujących parametrów.  

#### <a name="required-report-parameters"></a>Wymagane parametry raportu  
 Aby uruchomić ten raport, należy określić następujące parametry.  

|Nazwa parametru|Opis|  
|--------------------|-----------------|  
|**Nazwa kolekcji**|Z listy rozwijanej wybierz kolekcję, która ma być używana w tym raporcie.|  
|**Interwał raportowania (dni)**|Określ liczbę dni, które mają zostać objęte raportem. Domyślna wartość to **7** dni. Wartość maksymalna to **365** dni. Określ wartość **0** , aby raport został uruchomiony dziś.|  

#### <a name="hidden-report-parameters"></a>Ukryte parametry raportu  
 Ten raport nie ma ukrytych parametrów, które można ustawić.  

#### <a name="report-links"></a>Linki do raportów  
 Ten raport zawiera linki do następującego raportu, który zapewnia dodatkowe informacje na temat wybranej pozycji.  

|Nazwa raportu|Szczegóły|  
|-----------------|-------------|  
|**Szczegóły braku usypiania zasilania na komputerze**|Kliknij liczbę w kolumnie **Odnośne komputery** , aby wyświetlić listę komputerów, które nie mogły zostać wprowadzone w tryb uśpienia lub hibernacji ze względu na wybraną przyczynę.<br /><br /> Aby uzyskać więcej informacji, zobacz [Insomnia Computer Details Report](#BKMK_Insomnia_Computer_Details) w tym temacie.|  

###  <a name="BKMK_Capabilites"></a> Raport Możliwości zarządzania energią  
 Raport **Możliwości zarządzania energią** przedstawia możliwości sprzętowe zarządzania energią dla komputerów w określonej kolekcji. Ten raport jest zwykle używany w fazie monitorowania zarządzania energią w celu określenia możliwości zarządzania energią dla komputerów w organizacji. Informacje wyświetlane w tym raporcie mogą następnie służyć do tworzenia kolekcji komputerów, do których mają zostać zastosowane plany zasilania, lub komputerów wykluczonych z zarządzania energią. W tym raporcie są wyświetlane następujące możliwości zarządzania energią:  

-   **Możliwość uśpienia** — Wskazuje, czy komputer ma możliwość przejścia w tryb uśpienia, jeśli jest odpowiednio skonfigurowany.  

-   **Możliwość hibernacji** — Wskazuje, czy komputer ma możliwość przejścia w tryb hibernacji, jeśli jest odpowiednio skonfigurowany.  

-   **Możliwość przebudzenia z uśpienia** — Wskazuje, czy komputer ma możliwość wybudzenia z uśpienia, jeśli jest odpowiednio skonfigurowany.  

-   **Możliwość przebudzenia z hibernacji** — Wskazuje, czy komputer ma możliwość wybudzenia z hibernacji, jeśli jest odpowiednio skonfigurowany.  

 Wartości wyświetlane w raporcie **Możliwości zasilania** wskazują obsługę trybu uśpienia i hibernacji przez komputery zgłaszaną przez system Windows. Jednak zgłoszone wartości nie odzwierciedlają przypadków, w których ustawienia systemu Windows lub systemu BIOS uniemożliwiają działanie tych funkcji.  

 Skonfiguruj ten raport przy użyciu następujących parametrów.  

#### <a name="required-report-parameters"></a>Wymagane parametry raportu  
 Aby uruchomić ten raport, należy określić następujące parametry.  

|Nazwa parametru|Opis|  
|--------------------|-----------------|  
|**Kolekcja**|Z listy rozwijanej wybierz kolekcję dla tego raportu.|  
|**Wyświetl filtr**|Z listy rozwijanej wybierz **nieobsługiwane** do wyświetla tylko komputery w określonej kolekcji, które mogą przejść w stan uśpienia, hibernacji, wybudzenia z uśpienia lub wybudzenia z hibernacji. Wybierz **Pokaż wszystko** Aby wyświetlić wszystkie komputery w określonej kolekcji.|  

#### <a name="hidden-report-parameters"></a>Ukryte parametry raportu  
 Ten raport nie ma ukrytych parametrów, które można ustawić.  

#### <a name="report-links"></a>Linki do raportów  
 Ten raport zawiera linki do następującego raportu, który zapewnia dodatkowe informacje na temat wybranej pozycji.  

|Nazwa raportu|Szczegóły|  
|-----------------|-------------|  
|**Szczegóły komputera**|Kliknij nazwę komputera, aby wyświetlić wszystkie możliwości zasilania, ustawienia zasilania i zastosowane plany zasilania dla wybranego komputera.<br /><br /> Aby uzyskać więcej informacji, zobacz [Computer Details Report](#BKMK_Computer_Details) w tym temacie.|  

###  <a name="BKMK_Settings"></a> Raport Ustawienia zasilania  
 Raport **Ustawienia zasilania** przedstawia zagregowaną listę ustawień zasilania używanych na komputerach w określonej kolekcji. Dla każdego ustawienia zasilania są wyświetlane dostępne tryby zasilania, wartości i jednostki wraz z liczbą komputerów, które używają tych wartości. Ten raport może być używany w fazie monitorowania zarządzania energią w celu ułatwienia administratorowi zrozumienia istniejących ustawień zasilania używanych przez komputery w lokacji oraz zaplanowania optymalnych ustawień zasilania, które mają zostać zastosowane przy użyciu planu zarządzania energią. Ten raport jest również przydatny podczas rozwiązywania problemów do sprawdzania poprawności zastosowania ustawień zasilania.  

> [!NOTE]  
>  Wyświetlane ustawienia są zbierane z komputerów klienckich podczas tworzenia spisu sprzętu. Zależnie od godziny, o której uruchamiany jest spis sprzętu, mogą być zbierane informacje o ustawieniach dotyczące zastosowanego szczytowego planu zasilania lub planu zasilania bez szczytów.  

 Skonfiguruj ten raport przy użyciu następujących parametrów.  

#### <a name="required-report-parameters"></a>Wymagane parametry raportu  
 Aby uruchomić ten raport, należy określić następujące parametry.  

|Nazwa parametru|Opis|  
|--------------------|-----------------|  
|**Nazwa kolekcji**|Z listy rozwijanej wybierz kolekcję dla tego raportu.|  

#### <a name="hidden-report-parameters"></a>Ukryte parametry raportu  
 Opcjonalnie można określić następujące ukryte parametry w celu zmiany zachowania tego raportu.  

|Nazwa parametru|Opis|  
|--------------------|-----------------|  
|**Liczba lokalizacji**|Określ liczbę języków, w których mają być wyświetlane nazwy ustawień zasilania zgłaszane przez komputery klienckie. Aby był wyświetlany najpopularniejszy język, pozostaw wartość domyślną **1**. Aby wyświetlić wszystkie języki, ustaw tę wartość na **0**.|  

#### <a name="report-links"></a>Linki do raportów  
 Ten raport zawiera linki do następującego raportu, który zapewnia dodatkowe informacje na temat wybranej pozycji.  

|Nazwa raportu|Szczegóły|  
|-----------------|-------------|  
|**Szczegóły ustawień zasilania**|Kliknij liczbę komputerów w kolumnie **Komputery** , aby wyświetlić listę wszystkich komputerów, które używają ustawień zasilania w tym wierszu.<br /><br /> Aby uzyskać więcej informacji, zobacz [Power Settings Details Report](#BKMK_Settings_Details) w tym temacie.|  

###  <a name="BKMK_Settings_Details"></a> Power Settings Details report  
 Raport **Szczegóły ustawień zasilania** zawiera dodatkowe informacje o komputerach wybranych w raporcie **Ustawienia zasilania** . Ten raport jest wywoływany przez raport **Ustawienia zasilania** i nie jest przeznaczony do uruchamiania bezpośrednio przez administratora lokacji.  

#### <a name="required-report-parameters"></a>Wymagane parametry raportu  
 Aby uruchomić ten raport, należy określić następujące parametry.  

|Nazwa parametru|Opis|  
|--------------------|-----------------|  
|**Kolekcja**|Z listy rozwijanej wybierz kolekcję, która ma być używana w tym raporcie.|  
|**Identyfikator GUID ustawień zasilania**|Z listy rozwijanej wybierz identyfikator GUID ustawień zasilania, dla którego chcesz utworzyć raport. Aby uzyskać listę wszystkich ustawień zasilania i ich zastosowań, zobacz [ustawienia planu zarządzania energią dostępne](../../../../core/clients/manage/power/create-and-apply-power-plans.md#BKMK_Plans) w temacie [tworzenie i stosowanie planów zasilania w programie System Center Configuration Manager](../../../../core/clients/manage/power/create-and-apply-power-plans.md).|  
|**Power Mode**|Z listy rozwijanej wybierz typ ustawień zasilania, które mają być wyświetlane w raporcie. Wybierz pozycję **Podłączony** , aby wyświetlić ustawienia zasilania skonfigurowane dla sytuacji, w której komputer jest podłączony, i pozycję **Zasilany z baterii** , aby wyświetlić ustawienia zasilania skonfigurowane dla komputera zasilanego z baterii.|  
|**Indeks ustawień**|Z listy rozwijanej wybierz wartość nazwy wybranego ustawienia zasilania, dla której chcesz utworzyć raport. Aby na przykład wyświetlić wszystkie komputery, dla których ustawienie **Wyłącz dysk twardy po** ustawiono na **10** minut, wybierz pozycję **Wyłącz dysk twardy po** z listy rozwijanej **Nazwa ustawienia zasilania** i **10** z listy rozwijanej **Indeks ustawień**.|  

#### <a name="hidden-report-parameters"></a>Ukryte parametry raportu  
 Opcjonalnie można określić następujące ukryte parametry w celu zmiany zachowania tego raportu.  

|Nazwa parametru|Opis|  
|--------------------|-----------------|  
|**Liczba lokalizacji**|Określ liczbę języków, w których mają być wyświetlane nazwy ustawień zasilania zgłaszane przez komputery klienckie. Aby był wyświetlany najpopularniejszy język, pozostaw wartość domyślną **1**. Aby wyświetlić wszystkie języki, ustaw tę wartość na **0**.|  

#### <a name="report-links"></a>Linki do raportów  
 Ten raport zawiera linki do następującego raportu, który zapewnia dodatkowe informacje na temat wybranej pozycji.  

|Nazwa raportu|Szczegóły|  
|-----------------|-------------|  
|**Szczegóły komputera**|Kliknij nazwę komputera, aby wyświetlić wszystkie możliwości zasilania, ustawienia zasilania i zastosowane plany zasilania dla wybranego komputera.<br /><br /> Aby uzyskać więcej informacji, zobacz [Computer Details Report](#BKMK_Computer_Details) w tym temacie.|  
