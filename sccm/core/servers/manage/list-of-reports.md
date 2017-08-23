---
title: "Lista raportów | Dokumentacja firmy Microsoft"
description: "Przejrzyj listę raportów dostępnych w programie Configuration Manager. Należą one do różnych kategorii."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b7332ed3-8003-454b-bb12-1fdf8721425c
caps.latest.revision: "10"
caps.handback.revision: "0"
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.openlocfilehash: 1480c38a6a3afef76b2e8759eaafd47d28f978f4
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="list-of-reports-in-system-center-configuration-manager"></a>Lista raportów w programie System Center Configuration Manager.

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Wiele wbudowanych raportów są dostarczane z System Center Configuration Manager, obejmujące wiele zadań raportowania, które można wykonywać. W tych raportach można również używać instrukcji SQL, co pozwoli na tworzenie własnych raportów. Skorzystaj z informacji w tym temacie, aby dowiedzieć się więcej na temat raportów dostępnych w programie Configuration Manager.  

## <a name="list-of-built-in-configuration-manager-reports"></a>Lista wbudowanych raportów programu Configuration Manager  
 Następujące raporty są uwzględnione w programie Configuration Manager. Należą one do różnych kategorii.  

### <a name="administrative-security"></a>Zabezpieczenia administracyjne  
 Następujące raporty są wyświetlane w obszarze **zabezpieczenia administracyjne** kategorii.  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Dziennik działań administracyjnych**|Przedstawia rekord zmian administracyjnych wprowadzonych w przypadku użytkowników administracyjnych, ról zabezpieczeń, zakresów zabezpieczeń oraz kolekcji.|  
|**Przydziały zabezpieczeń użytkowników administracyjnych**|Przedstawia dane użytkowników administracyjnych, skojarzone z nimi role zabezpieczeń oraz zakresy zabezpieczeń skojarzone z każdą rolą zabezpieczeń dla każdego użytkownika.|  
|**Obiekty zabezpieczane w ramach pojedynczego zakresu zabezpieczeń**|Przedstawia obiekty zabezpieczane w ramach określonego zakresu zabezpieczeń i przypisane tylko do tego zakresu zabezpieczeń. Ten raport nie zawiera obiektów skojarzonych z więcej niż jednym zakresem zabezpieczeń.|  
|**Zabezpieczenia określonych lub wielu obiektów programu Configuration Manager**|Przedstawia obiekty możliwe do zabezpieczenia, zakresy zabezpieczeń skojarzone z obiektami i użytkowników administracyjnych z uprawnieniami do obiektów.|  
|**Podsumowanie ról zabezpieczeń**|Wyświetla role zabezpieczeń i administratorów programu Configuration Manager skojarzonych z poszczególnymi rolami.|  
|**Podsumowanie zakresów zabezpieczeń**|Przedstawia zakresy zabezpieczeń oraz użytkowników administracyjnych programu Configuration Manager i grupy zabezpieczeń skojarzonych z każdym zakresem.|  

### <a name="alerts"></a>Alerty  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Ocena alertu**|Przedstawia podsumowanie wszystkich przełożonych alertów, które zostały wygenerowane między określonymi datami rozpoczęcia i zakończenia.|  
|**Alerty generowane najczęściej**|Przedstawia podsumowanie alertów, które były najczęściej generowane w okresie od określonej daty do daty bieżącej dla określonego obszaru funkcji.|  

### <a name="asset-intelligence"></a>Analiza zasobów  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Sprzęt 01A - podsumowanie komputerów w określonej kolekcji**|Przedstawia widok podsumowania analizy zasobów dla komputerów w określonej kolekcji.|  
|**Sprzęt 03A — użytkownicy podstawowi komputerów**|Przedstawia użytkowników oraz liczbę komputerów, na których dana osoba jest użytkownikiem podstawowym.|  
|**Sprzęt 03B - komputery określonego użytkownika podstawowego konsoli**|Przedstawia wszystkie komputery, dla których określony użytkownik jest użytkownikiem podstawowym konsoli.|  
|**Oprogramowanie 04A - komputery z wieloma użytkownikami (współużytkowane)**|Przedstawia komputery, które nie mają użytkownika podstawowego, ponieważ procent czasu logowania do konsoli dla żadnego z użytkowników nie przekracza 66%.|  
|**Sprzęt 05A - użytkownicy konsoli na określonym komputerze**|Przedstawia wszystkich użytkowników konsoli na określonym komputerze.|  
|**Sprzęt 06A - komputery dla których konsoli nie można ustalić użytkowników**|Pomaga użytkownikom administracyjnym w identyfikowaniu komputerów, na których należy włączyć rejestrowanie zabezpieczeń.|  
|**Sprzęt 07b - urządzenia USB według producenta**|Przedstawia urządzenia USB pogrupowane według producenta.|  
|**Sprzęt 07B - urządzenia USB według producenta i opisu**|Przedstawia urządzenia USB pogrupowane według producenta i opisu.|  
|**Sprzęt 07C - komputery z określonym urządzeniem USB**|Przedstawia wszystkie komputery z określonym urządzeniem USB.|  
|**Sprzęt 07D - urządzenia USB na określonym komputerze**|Przedstawia wszystkie urządzenia USB na określonym komputerze.|  
|**Sprzęt 08A - sprzęt który nie jest gotowy do aktualizacji oprogramowania**|Przedstawia sprzęt, który nie spełnia minimalnych wymagań sprzętowych.|  
|**Sprzęt 09A - wyszukiwanie komputerów**|Wyświetla podsumowanie Menedżera zasobów dotyczące komputerów spełniających kryteria filtrów słów kluczowych dotyczących nazwy komputera, lokacji programu Configuration Manager, domeny, najczęstszego użytkownika konsoli, systemu operacyjnego, producenta lub modelu.|  
|**Sprzęt 10A - komputery w określonej kolekcji które uległy zmianie w określonym przedziale czasu**|Przedstawia listę komputerów w określonej kolekcji, dla których klasa sprzętu została zmieniona w określonym przedziale czasu.|  
|**Sprzęt 10B - zmiany na określonym komputerze w określonym przedziale czasu**|Przedstawia klasy, które zostały zmienione na określonym komputerze w określonym przedziale czasu.|  
|**Licencja 01A - Księga licencji zbiorczych firmy Microsoft dla deklaracje licencyjne firmy Microsoft**|Przedstawia spis wszystkich tytułów oprogramowania firmy Microsoft, które są dostępne w ramach programu licencjonowania zbiorowego firmy Microsoft.|  
|**Licencja 01B — elementy księgi licencji grupowych Microsoft wg kanału sprzedaży**|Identyfikuje i przedstawia kanał sprzedaży dla uwzględnionego w spisie oprogramowania z licencją zbiorczą firmy Microsoft.|  
|**Licencja 01C - komputery z określonym licencjonowania zbiorowego firmy Microsoft księgi elementu i kanałem sprzedaży**|Identyfikuje i przedstawia komputery z określonym elementem księgi licencji zbiorczych firmy Microsoft.|  
|**Licencja 01D - produkty w księdze licencji grupowych Microsoft na określonym komputerze**|Identyfikuje i przedstawia wszystkie elementy księgi licencji zbiorczych firmy Microsoft na określonym komputerze.|  
|**Licencja 02A — liczba licencji wygasną, według przedziałów czasu**|Przedstawia liczbę licencji, które wkrótce wygasną, według określonego przedziału czasu. Są w nim wyświetlane produkty, których licencje są zarządzane przez usługę licencjonowania oprogramowania.|  
|**Licencja 02B - komputery z licencjami bliskimi wygaśnięcia**|Przedstawia określone komputery z licencjami, które wkrótce wygasną.|  
|**Licencja 02C - informacje dotyczące licencji na określonym komputerze**|Przedstawia produkty na określonym komputerze, których licencje są zarządzane przez usługę licencjonowania oprogramowania.|  
|**Licencja 03A - liczba licencji według stanu licencji**|Przedstawia produkty, których licencje są zarządzane przez usługę licencjonowania oprogramowania, uporządkowane według stanu licencji.|  
|**Licencja 03B - komputery z określonym stanem licencji**|Przedstawia produkty, których licencje są zarządzane przez usługę licencjonowania oprogramowania, z określonym stanem licencji.|  
|**Licencja 04A - liczba produktów zarządzanych przez usługę licencjonowania oprogramowania**|Przedstawia liczbę produktów, których licencje są zarządzane przez usługę licencjonowania oprogramowania.|  
|**Licencja 04B - komputery z określonym produktem zarządzanym przez usługę licencjonowania oprogramowania**|Przedstawia komputery zarządzane przez usługę licencjonowania oprogramowania, które zawierają określony produkt.|  
|**Licencja 05A - komputery z usługą zarządzania kluczami**|Przedstawia komputery, które działają jako serwery zarządzania kluczami.|  
|**Licencja 06A - liczba procesorów dla produktów licencjonowanych na procesor**|Przedstawia liczbę procesorów komputerów z produktami firmy Microsoft, które obsługują licencjonowanie w trybie na procesor.|  
|**Licencja 06B — komputery z określonym produktem obsługującym licencję w trybie na procesor**|Przedstawia listę komputerów, na których zainstalowano określony produkt firmy Microsoft obsługujący licencjonowanie w trybie na procesor.|  
|**Licencja 14A - raport dotyczący uzgodnienia programu licencjonowania zbiorowego firmy Microsoft**|Przedstawia uzgodnienia związane z licencjami oprogramowania zakupionymi za pośrednictwem umowy licencjonowania zbiorowego firmy Microsoft oraz rzeczywistą liczbę ze spisu.|  
|**Licencja 14B - listy nie można odnaleźć w MVLS spisu oprogramowania firmy Microsoft**|Ten raport przedstawia tytuły oprogramowania firmy Microsoft w użyciu, których nie znaleziono w umowie licencji zbiorowych firmy Microsoft.|  
|**Licencja 15A - raport uzgadniania ogólnych licencji**|Przedstawia uzgadnianie dotyczące zakupionych ogólnych licencji oprogramowania oraz rzeczywistą liczbę ze spisu.|  
|**Licencja 15B - ogólny raport uzgadniania licencji według komputera**|Przedstawia komputery, na których zainstalowano licencjonowany produkt w określonej wersji.|  
|**Oprogramowanie 01A - podsumowanie zainstalowanego oprogramowania w określonej kolekcji**|Przedstawia podsumowanie zainstalowanego oprogramowania uporządkowane według liczby wystąpień w spisie.|  
|**Oprogramowanie 02A - rodziny produktów dla określonej kolekcji**|Przedstawia rodziny produktów i liczbę programów w rodzinie dla określonej kolekcji.|  
|**Oprogramowanie 02B - kategorie produktów w określonej rodzinie produktów**|Przedstawia kategorie produktów w określonej rodzinie produktów oraz liczbę programów w kategorii.|  
|**Oprogramowanie 02C - oprogramowanie w określonej rodzinie i kategorii produktów**|Przedstawia wszystkie programy, które należą do określonej kategorii i rodziny produktów.|  
|**Oprogramowanie 02D - komputery z zainstalowanym określonym oprogramowaniem**|Przedstawia wszystkie komputery, na których zainstalowano określone oprogramowanie.|  
|**Oprogramowanie 02E - oprogramowanie zainstalowane na określonym komputerze**|Przedstawia wszystkie programy zainstalowane na określonym komputerze.|  
|**Oprogramowanie 03A — oprogramowanie bez kategorii**|Przedstawia oprogramowanie skategoryzowane jako nieznane lub nienależące do żadnej kategorii.|  
|**Oprogramowanie 04A - oprogramowanie skonfigurowane do automatycznego uruchamiania na komputerach**|Przedstawia listę programów skonfigurowanych do automatycznego uruchamiania na komputerach.|  
|**Oprogramowanie 04B - komputery z określonym oprogramowaniem skonfigurowanym do automatycznego uruchamiania**|Przedstawia wszystkie komputery z określonym oprogramowaniem skonfigurowanym do automatycznego uruchamiania.|  
|**Oprogramowanie 04C - oprogramowanie skonfigurowane do automatycznego uruchamiania na określonym komputerze**|Przedstawia zainstalowane oprogramowanie skonfigurowane do automatycznego uruchamiania na określonym komputerze.|  
|**Oprogramowanie 05A - obiekty Pomocnik przeglądarki**|Przedstawia obiekty pomocnicze przeglądarki zainstalowane na komputerach w określonej kolekcji.|  
|**Oprogramowanie 05B - komputery z określonym obiektem Pomocnik przeglądarki**|Przedstawia wszystkie komputery z określonym obiektem pomocniczym przeglądarki.|  
|**Oprogramowanie 05C - obiekty Pomocnik przeglądarki na określonym komputerze**|Przedstawia wszystkie obiekty pomocnicze przeglądarki na określonym komputerze.|  
|**Oprogramowanie 06A - wyszukiwanie zainstalowanego oprogramowania**|Ten raport przedstawia podsumowanie zainstalowanego oprogramowania uporządkowane według liczby wystąpień na podstawie kryteriów wyszukiwania dla nazwy produktu, wydawcy lub wersji.|  
|**Oprogramowanie 06B - oprogramowanie według nazwy produktu**|Przedstawia podsumowanie zainstalowanego oprogramowania uporządkowane według liczby wystąpień na podstawie określonej nazwy produktu.|  
|**Oprogramowanie 07A - ostatnio używane programy wykonywalne według liczby komputerów**|Przedstawia programy wykonywalne, które były ostatnio używane, oraz liczbę komputerów, na których ich używano. Aby wyświetlanie tego raportu było możliwe, w tej lokacji należy włączyć pomiar użytkowania oprogramowania.|  
|**Oprogramowanie 07B — komputery których ostatnio używany określony program wykonywalny**|Przedstawia komputery, na których ostatnio używano określonego programu wykonywalnego po włączeniu ustawienia klienta dotyczącego pomiaru użytkowania oprogramowania.|  
|**Oprogramowanie 07C - ostatnio używane programy wykonywalne na określonym komputerze**|Przedstawia pliki wykonywalne, których ostatnio używano na określonym komputerze po włączeniu ustawienia klienta dotyczącego pomiaru użytkowania oprogramowania.|  
|**Oprogramowanie 08A - ostatnio używane programy wykonywalne według liczby użytkowników**|Przedstawia ostatnio używane programy wykonywalne oraz liczbę użytkowników, którzy ostatnio z nich korzystali po włączeniu ustawienia klienta dotyczącego pomiaru użytkowania oprogramowania.|  
|**Oprogramowanie 08B - użytkownicy którzy używali ostatnio określonego programu wykonywalnego**|Przedstawia użytkowników, którzy ostatnio używali określonego programu wykonywalnego po włączeniu ustawienia klienta dotyczącego pomiaru użytkowania oprogramowania.|  
|**Oprogramowanie 08C - ostatnio używane programy wykonywalne według określonego użytkownika**|Przedstawia programy wykonywalne ostatnio używane przez określonego użytkownika po włączeniu ustawienia klienta dotyczącego pomiaru użytkowania oprogramowania.|  
|**Oprogramowanie 09A - rzadko używane oprogramowanie**|Przedstawia tytuły oprogramowania, które nie były używane w określonym przedziale czasu.|  
|**Oprogramowanie 09B - komputery z rzadko używanym oprogramowaniem**|Przedstawia komputery z zainstalowanym oprogramowaniem, które nie było używane w określonym przedziale czasu. Określony przedział czasu opiera się na wartości podanej w raporcie „Oprogramowanie 09A — rzadko używane oprogramowanie”.|  
|**Oprogramowane 10A - tytuły oprogramowania z określonymi zdefiniowanymi wieloma etykietami niestandardowymi**|Przedstawia tytuły oprogramowania w oparciu o dopasowanie wszystkich określonych kryteriów etykiet niestandardowych. Aby zawęzić wyniki wyszukiwania tytułu oprogramowania, można wybrać maksymalnie trzy etykiety niestandardowe.|  
|**Oprogramowanie 10B - komputery z zainstalowanym tytułem oprogramowania z etykietą niestandardową określonych**|Przedstawia wszystkie komputery w tej kolekcji, na których zainstalowano tytuł oprogramowania z określoną etykietą niestandardową.|  
|**Oprogramowanie 11A - tytuły oprogramowania ze zdefiniowaną określoną etykietą niestandardową**|Przedstawia tytuły oprogramowania w oparciu o dopasowanie co najmniej jednego określonego kryterium etykiet niestandardowych.|  
|**Oprogramowanie 12A - tytuły oprogramowania bez etykiety niestandardowej**|Przedstawia wszystkie tytuły oprogramowania, które nie mają zdefiniowanej etykiety niestandardowej.|  
|**Oprogramowanie 14A - Search for tagiem identyfikacji oprogramowania z włączonym**|Przedstawia liczbę zainstalowanych programów z włączonym znacznikiem identyfikacji programu.|  
|**Oprogramowanie 14B - komputery z określonym znacznikiem identyfikacji włączonym zainstalowanego oprogramowania**|Przedstawia wszystkie komputery, na których zainstalowano oprogramowanie z włączonym znacznikiem identyfikacji programu.|  
|**Oprogramowanie 14C - identyfikator tagu włączone oprogramowanie zainstalowane na określonym komputerze**|Przedstawia wszystkie programy z określonym włączonym znacznikiem identyfikacji programu, które zainstalowano na określonym komputerze.|  

### <a name="client-push"></a>Wypychane przez klienta  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Szczegóły stanu instalacji wypychanych klienta**|Przedstawia informacje na temat procesu wypychanej instalacji klienta dla wszystkich lokacji.|  
|**Szczegóły stanu instalacji wypychanych klienta dla określonej lokacji**|Przedstawia informacje na temat procesu wypychanej instalacji klienta dla określonej lokacji.|  
|**Podsumowanie stanu instalacji wypychanych klienta**|Przedstawia widok podsumowania stanu wypychanej instalacji klienta dla wszystkich lokacji.|  
|**Podsumowanie dla określonej lokacji stanu instalacji wypychanych klienta**|Przedstawia widok podsumowania stanu wypychanej instalacji klienta dla określonej lokacji.|  

### <a name="client-status"></a>Stan klienta  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Szczegóły korygowania klienta**|Przedstawia szczegóły akcji korygowania klienta dla określonej kolekcji.|  
|**Podsumowanie korygowania klienta**|Przedstawia podsumowanie akcji korygowania klienta dla określonej kolekcji.|  
|**Historia stanu klienta**|Przedstawia widok historycznych danych dotyczących ogólnego stanu klienta w lokacji.|  
|**Podsumowanie stanu klienta**|Przedstawia wyniki sprawdzania aktywnych klientów dla danej kolekcji.|  
|**Czas klienta na zażądanie zasady**|Przedstawia odsetek klientów, którzy zażądali zasad co najmniej raz w ciągu ostatnich 30 dni. Każdy dzień reprezentuje procent łącznej liczby klientów, którzy zażądali zasad od pierwszego dnia cyklu.|  
|**Klienci w których nie powiodło się sprawdzenie szczegółów**|Przedstawia szczegółowe informacje dotyczące klientów, dla których wystąpiły błędy sprawdzania klienta dla określonej kolekcji.|  
|**Szczegóły nieaktywnych klientów**|Przedstawia szczegółową listę nieaktywnych klientów dla danej kolekcji.|  

### <a name="company-resource-access"></a>Dostęp do zasobów firmy  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Historia wystawiania certyfikatów**|Przedstawia historię certyfikatów, które zostały wystawione przez punkt rejestracji certyfikatu dla użytkowników i urządzeń w określonym przedziale czasu.|  
|**Lista zasobów według stanu wystawienia certyfikatu**|Przedstawia urządzenia lub użytkowników w określonym stanie wystawiania certyfikatu po dokonaniu oceny określonego profilu certyfikatu.|  
|**Lista zasobów z certyfikatami bliskimi wygaśnięcia**|Przedstawia urządzenia lub użytkowników z certyfikatami wygasającymi w określonym dniu lub wcześniej.|  

### <a name="compliance-and-settings-management"></a>Zarządzanie zgodnością i ustawieniami  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Historia zgodności linii bazowej konfiguracji**|Przedstawia historię zmian zgodności linii bazowej konfiguracji dla określonego przedziału dat.|  
|**Historia zgodności elementu konfiguracji**|Przedstawia historię zmian zgodności elementu konfiguracji dla określonego przedziału dat.|  
|**Szczegóły zgodnych reguł elementów konfiguracji w linii bazowej konfiguracji dla zasobu**|Przedstawia informacje o regułach, które zostały ocenione jako zgodne dla określonego elementu konfiguracji oraz dla określonego urządzenia lub użytkownika.|  
|**Szczegóły będących w konflikcie reguł elementów konfiguracji w linii bazowej konfiguracji dla zasobu**|Przedstawia informacje o regułach w elemencie konfiguracji wdrożonym do określonego użytkownika lub urządzenia, które powodują konflikt z innymi regułami zawartymi w tym samym wdrożonym elemencie konfiguracji.|  
|**Szczegóły błędów elementów konfiguracji w linii bazowej konfiguracji dla zasobu**|Przedstawia informacje o błędach wygenerowanych przez określony element konfiguracji dla określonego urządzenia lub użytkownika.|  
|**Szczegóły niezgodnych reguł elementów konfiguracji w linii bazowej konfiguracji dla zasobu**|Przedstawia informacje o regułach, które zostały ocenione jako niezgodne dla określonego elementu konfiguracji oraz dla określonego urządzenia lub użytkownika.|  
|**Szczegóły skorygowanych reguł elementów konfiguracji w linii bazowej konfiguracji dla zasobu**|Przedstawia informacje o regułach skorygowanych przez określony element konfiguracji dla określonego urządzenia lub użytkownika.|  
|**Lista zasobów według stanu zgodności elementu konfiguracji w linii bazowej konfiguracji**|Przedstawia urządzenia lub użytkowników w określonym stanie zgodności po dokonaniu oceny określonego elementu konfiguracji.|  
|**Lista zasobów według stanu zgodności dla linii bazowej konfiguracji**|Przedstawia urządzenia lub użytkowników w określonym stanie zgodności po dokonaniu oceny określonej linii bazowej konfiguracji.|  
|**Lista reguł w konflikcie z określoną regułą zasobu**|Przedstawia listę reguł, które powodują konflikt z określoną regułą dla elementu konfiguracji wdrożonego do określonego urządzenia.|  
|**Lista nieznanych zasobów linii bazowej konfiguracji**|Przedstawia listę urządzeń lub użytkowników, którzy nie zgłosili jeszcze żadnych danych zgodności dla określonej linii bazowej konfiguracji.|  
|**Lista nieznanych zasobów pozycji bazowej konfiguracji**|Przedstawia listę urządzeń lub użytkowników, którzy nie zgłosili jeszcze żadnych danych zgodności dla określonego elementu konfiguracji.|  
|**Reguł i błędów elementów konfiguracji w linii bazowej konfiguracji dla zasobu podsumowania**|Przedstawia podsumowanie stanu zgodności reguł i wszelkich błędów ustawień dla określonego elementu konfiguracji wdrożonego do określonego urządzenia lub użytkownika.|  
|**Podsumowanie zgodności według linii bazowej konfiguracji**|Przedstawia podsumowanie ogólnej zgodności wdrożonych linii bazowych konfiguracji w hierarchii.|  
|**Podsumowanie zgodności według elementów konfiguracji dla linii bazowej konfiguracji**|Przedstawia podsumowanie zgodności elementów konfiguracji w określonej linii bazowej konfiguracji.|  
|**Podsumowanie zgodności według zasad konfiguracji**|Przedstawia podsumowanie zgodności zasad konfiguracji.|  
|**Podsumowanie zgodności linii bazowej konfiguracji dla kolekcji**|Przedstawia podsumowanie ogólnej zgodności określonej linii bazowej konfiguracji wdrożonej w określonej kolekcji.|  
|**Lista niezgodnych aplikacji i urządzeń dla określonego użytkownika**|Zawiera informacje o użytkownikach i urządzeniach z zainstalowanymi aplikacjami niezgodnymi z wybranymi zasadami.|  
|**Podsumowanie użytkowników z niezgodnymi aplikacjami**|Zawiera informacje o użytkownikach z zainstalowanymi aplikacjami niezgodnymi z wybranymi zasadami.|  
|**Akceptacja warunków i postanowień**|Zawiera elementy warunków i postanowień oraz ich wersje zaakceptowane przez każdego użytkownika.|  

### <a name="device-management"></a>Zarządzanie urządzeniami  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Wszyscy klienci urządzeń przenośnych**|Przedstawia informacje o wszystkich klientach urządzeń przenośnych. Urządzenia zarządzane przez łącznik serwera programu Exchange nie są uwzględniane.|  
|**Problemy z certyfikatami na urządzeniach przenośnych, które są zarządzane przez klienta programu Configuration Manager dla systemu Windows CE, które nie są w dobrej kondycji**|Wyświetla szczegółowe informacje dotyczące problemów z certyfikatami na urządzeniach przenośnych, które są zarządzane przez klienta programu Configuration Manager dla systemu Windows CE.|  
|**Niepowodzenie wdrożenia klienta dla urządzeń przenośnych, które są zarządzane przez klienta programu Configuration Manager dla systemu Windows CE**|Wyświetla szczegółowe informacje dotyczące niepowodzenia wdrożenia na urządzeniach przenośnych, które są zarządzane przez klienta programu Configuration Manager dla systemu Windows CE.|  
|**Szczegóły stanu wdrażania klienta dla urządzeń przenośnych, które są zarządzane przez klienta programu Configuration Manager dla systemu Windows CE**|Wyświetla informacje o stanie urządzeń przenośnych, które są zarządzane przez klienta programu Configuration Manager dla systemu Windows CE.|  
|**Powodzenie wdrożenia klienta dla urządzeń przenośnych, które są zarządzane przez klienta programu Configuration Manager dla systemu Windows CE**|Wyświetla szczegółowe informacje dotyczące powodzenia wdrożenia na urządzeniach przenośnych, które są zarządzane przez klienta programu Configuration Manager dla systemu Windows CE.|  
|**Problemy z komunikacją na urządzeniach przenośnych, które są zarządzane przez klienta programu Configuration Manager dla systemu Windows CE, które nie są w dobrej kondycji**|Ten raport zawiera szczegółowe informacje dotyczące problemów z komunikacją na urządzeniach przenośnych, które są zarządzane przez klienta programu Configuration Manager dla systemu Windows CE.|  
|**Stan zgodności dla urządzeń przenośnych, które są zarządzane przez łącznik serwera Exchange**|Przedstawia podsumowanie stanu zgodności z domyślnymi zasadami skrzynki pocztowej programu Exchange ActiveSync dla urządzeń przenośnych zarządzanych przez łącznik serwera programu Exchange.|  
|**Liczba urządzeń przenośnych według ustawień wyświetlania**|Przedstawia liczbę urządzeń przenośnych według ustawień wyświetlania.|  
|**Liczba urządzeń przenośnych według systemu operacyjnego**|Przedstawia liczbę urządzeń przenośnych według systemu operacyjnego.|  
|**Liczba urządzeń przenośnych według pamięci programu**|Przedstawia liczbę urządzeń przenośnych według pamięci programu.|  
|**Liczba urządzeń przenośnych według konfiguracji pamięci magazynu**|Liczba urządzeń przenośnych według konfiguracji pamięci magazynu|  
|**Informacje o kondycji urządzeń przenośnych, które są zarządzane przez klienta programu Configuration Manager dla systemu Windows CE**|Wyświetla szczegółowe informacje o kondycji urządzeń przenośnych, które są zarządzane przez klienta programu Configuration Manager dla systemu Windows CE.|  
|**Podsumowanie kondycji urządzeń przenośnych, zarządzanych przez klienta programu Configuration Manager dla systemu Windows CE**|Wyświetla informacje podsumowania kondycji urządzeń przenośnych, które są zarządzane przez klienta programu Configuration Manager dla systemu Windows CE.|  
|**Nieaktywne urządzenia przenośne, które są zarządzane przez łącznik serwera Exchange**|Przedstawia urządzenia przenośne zarządzane przez łącznik serwera programu Exchange, które nie łączyły się z serwerem programu Exchange w ciągu określonej liczby dni.|  
|**Lista urządzeń zarejestrowanych przez użytkownika w programie Microsoft Intune**|Wyświetla wszystkie urządzenia, które użytkownik zarejestrował w usłudze Microsoft Intune.|  
|**Lista urządzeń uporządkowana według stanu dostępu warunkowego**|Zawiera informacje o bieżącym stanie zgodności i dostępu warunkowego urządzeń. Tego raportu można używać z zasadami dostępu warunkowego. Ten raport jest dostępny od wersji 1602 programu Configuration Manager.|  
|**Zgodność z dostępem warunkowym dla użytkownika**|Zawiera on szczegółowe informacje na temat zgodności z dostępem warunkowym dla określonego użytkownika, łącznie z nazwą urządzenia i platformą, stanem zgodności urządzenia i datą ostatniej oceny urządzenia. Ten raport jest dostępny od wersji 1602 programu Configuration Manager.|  
|**Problemy z klientami lokalnymi na urządzeniach przenośnych, które są zarządzane przez klienta programu Configuration Manager dla systemu Windows CE, które nie są w dobrej kondycji**|Ten raport zawiera szczegółowe informacje na temat problemów z klientami lokalnymi na urządzeniach przenośnych, które są zarządzane przez klienta programu Configuration Manager dla systemu Windows CE.|  
|**Informacje o kliencie urządzenia przenośnego**|Wyświetla informacje o urządzeniach przenośnych, które mają zainstalowanego klienta programu Configuration Manager. Z tego raportu można skorzystać, aby sprawdzić, które urządzenia przenośne mogą się pomyślnie komunikować z punktem zarządzania.|  
|**Szczegóły zgodności urządzeń przenośnych dotyczące łącznika serwera Exchange**|Przedstawia szczegóły zgodności urządzenia przenośnego dla domyślnych zasad skrzynki pocztowej programu Exchange ActiveSync, które zostały skonfigurowane przy użyciu łącznika serwera programu Exchange.|  
|**Urządzenia przenośne według systemu operacyjnego**|Przedstawia urządzenia przenośne według systemu operacyjnego.|  
|**Urządzenia przenośne ze złamanymi ograniczeniami lub z odblokowanym**|Przedstawia urządzenia przenośne ze złamanymi ograniczeniami lub z odblokowanym dostępem.|  
|**Urządzenia przenośne, które nie są zarządzane ponieważ mimo zarejestrowania nie zostały przypisane do lokacji**|Przedstawia urządzenia przenośne, które ukończyły rejestrację w programie Configuration Manager i mają certyfikat, ale nie można ukończyć przypisywanie lokacji.|  
|**Urządzenia przenośne z określoną ilością wolnej pamięci programu**|Przedstawia wszystkie urządzenia przenośne z określoną ilością wolnej pamięci programu.|  
|**Urządzenia przenośne z określoną ilością wolnej wymiennej pamięci magazynu**|Przedstawia wszystkie urządzenia przenośne z określoną ilością wolnej pamięci magazynu wymiennego.|  
|**Urządzenia przenośne z problemami dotyczącymi odnowienia certyfikatu**|Przedstawia zarejestrowane urządzenia przenośne, którym nie udało się odnowić certyfikatu. Jeśli certyfikat nie zostanie odnowiony przed upływem okresu wygaśnięcia, urządzenie przenośne będzie niezarządzane.|  
|**Urządzenia przenośne z niewielką ilością wolnej pamięci (poniżej wielkości określonej w KB) programu**|Przedstawia urządzenia przenośne, dla których pamięć programu jest mniejsza niż określony rozmiar w KB.|  
|**Urządzenia przenośne z niskim wolnej wymiennej pamięci magazynu (poniżej wielkości określonej w KB)**|Przedstawia urządzenia przenośne, dla których pamięć magazynu wymiennego jest mniejsza niż określony rozmiar w KB.|  
|**Liczba urządzeń zarejestrowanych przez użytkownika w usłudze Windows Intune**|Ten raport przedstawia użytkowników subskrypcję Microsoft Intune i z łączną liczbą urządzeń zarejestrowanych dla każdego użytkownika.|  
|**Oczekujące żądania czyszczenia dla urządzeń przenośnych**|Przedstawia oczekujące żądania czyszczenia danych dla urządzeń przenośnych.|  
|**Ostatnio zarejestrowane i przypisane urządzenia przenośne**|Przedstawia urządzenia przenośne, które ostatnio zarejestrowane w programie Configuration Manager i przypisane do lokacji.|  
|**Ostatnio wyczyszczone urządzenia przenośne**|Przedstawia listę urządzeń przenośnych, które zostały ostatnio pomyślnie wyczyszczone.|  
|**Ustawienia podsumowania dla urządzeń przenośnych, które są zarządzane przez łącznik serwera Exchange**|Przedstawia liczbę urządzeń przenośnych, na których zastosowano ustawienia poszczególnych zasad domyślnych skrzynek pocztowych Exchange ActiveSync, które są zarządzane przez łącznik serwera programu Exchange.|  
|**Szczegółowy stan kluczy ładowania bezpośredniego systemu Windows RT**|Przedstawia szczegółowe informacje o stanie dla określonego klucza ładowania bezpośredniego w systemie Windows RT.|  
|**Podsumowanie kluczy ładowania bezpośredniego systemu Windows RT**|Przedstawia stan kluczy ładowania bezpośredniego w systemie Windows RT.|  

### <a name="driver-management"></a>Zarządzanie sterownikami  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Wszystkie sterowniki**|Przedstawia listę wszystkich sterowników.|  
|**Wszystkie sterowniki dla określonej platformy**|Przedstawia wszystkie sterowniki dla określonej platformy.|  
|**Wszystkie sterowniki w określonym obrazie rozruchowym**|Przedstawia wszystkie sterowniki w określonym obrazie rozruchowym.|  
|**Wszystkie sterowniki określonej kategorii**|Przedstawia wszystkie sterowniki w określonej kategorii.|  
|**Wszystkie sterowniki określonego pakietu**|Przedstawia wszystkie sterowniki w określonym pakiecie.|  
|**Kategorie określonego sterownika**|Przedstawia kategorie dla określonego sterownika.|  
|**Komputery, których nie powiodła się instalacja sterowników dla określonej kolekcji**|Przedstawia komputery, na których nie można zainstalować sterowników dla określonej kolekcji.|  
|**Raport dla określonej kolekcji dopasowania katalogu sterowników**|Przedstawia raport dopasowania wykazu sterowników dla określonej kolekcji.|  
|**Raport dla określonego komputera dopasowania katalogu sterowników**|Przedstawia raport dopasowania wykazu sterowników dla określonego komputera.|  
|**Raport dla określonego urządzenia na określonym komputerze dopasowania katalogu sterowników**|Przedstawia raport dopasowania wykazu sterowników dla określonego urządzenia na określonym komputerze.|  
|**Sterownik raport dopasowania wykazu dla komputerów w określonej kolekcji z określonym urządzeniem**|Przedstawia raport dopasowania wykazu sterowników dla komputerów w określonej kolekcji z określonym urządzeniem.|  
|**Sterowniki, których nie można zainstalować na określonym komputerze**|Przedstawia sterowniki, których nie można zainstalować na określonym komputerze.|  
|**Obsługiwane platformy dla określonego sterownika**|Przedstawia obsługiwane platformy dla określonego sterownika.|  

### <a name="endpoint-protection"></a>Program Endpoint Protection  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Raport aktywności ochrony przed złośliwym oprogramowaniem**|Przedstawia omówienie działania oprogramowania chroniącego przed złośliwym kodem.|  
|**Ogólny stan ochrony przed złośliwym oprogramowaniem i historii**|Przedstawia ogólny stan i historię oprogramowania chroniącego przed złośliwym kodem.|  
|**Szczegóły złośliwego oprogramowania na komputerze**|Przedstawia szczegółowe informacje dotyczące określonego komputera oraz listę zainstalowanego na nim złośliwego oprogramowania.|  
|**Zainfekowane komputery**|Przedstawia listę komputerów, na których wykryto określone zagrożenie.|  
|**Użytkownicy z największą liczbą zagrożeń**|Przedstawia listę użytkowników z największą liczbą wykrytych zagrożeń.|  
|**Lista zagrożeń użytkownika**|Przedstawia listę zagrożeń znalezionych na określonym koncie użytkownika.|  

### <a name="hardware---cd-rom"></a>Sprzęt — CD-ROM  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Informacje o napędach CD-ROM dla określonego komputera**|Przedstawia informacje o napędach CD-ROM na określonym komputerze.|  
|**Komputery dla określonego producenta napędów CD-ROM**|Przedstawia listę komputerów z napędem CD-ROM od określonego producenta.|  
|**Liczba napędów CD-ROM według producentów**|Przedstawia liczbę napędów CD-ROM na producenta uwzględnionych w spisie.|  
|**Historia - Historia napędów CD-ROM dla określonego komputera**|Przedstawia historię spisu napędów CD-ROM na określonym komputerze.|  

### <a name="hardware---disk"></a>Sprzęt — dysk  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Komputery z dyskami twardymi określonego rozmiaru**|Przedstawia listę komputerów z dyskami twardymi o określonym rozmiarze.|  
|**Komputery z niewielką ilością wolnego miejsca (mniej niż określony %) na dysku**|Przedstawia listę komputerów w określonej kolekcji, które mają mniej wolnego miejsca na dysku niż określona wartość.|  
|**Komputery z mało wolnego miejsca na dysku (mniejszą niż określona liczba MB)**|Przedstawia listę komputerów i dysków z małą ilością wolnego miejsca. Ilość wolnego miejsca do sprawdzenia jest wyrażona w megabajtach.|  
|**Liczba konfiguracji dysku fizycznego**|Przedstawia liczbę dysków twardych w spisie uporządkowanych według pojemności dysku.|  
|**Informacje o dyskach dla określonego komputera - dyski logiczne**|Przedstawia podsumowanie informacji o dyskach logicznych na określonym komputerze.|  
|**Informacje o dyskach dla określonego komputera - partycje**|Przedstawia podsumowanie informacji o partycjach dysków na określonym komputerze.|  
|**Informacje o dyskach dla określonego komputera - dyski fizyczne**|Przedstawia podsumowanie informacji o dyskach fizycznych na określonym komputerze.|  
|**Historia - Historia miejsca na dyskach logicznych dla określonego komputera**|Przedstawia historię spisu napędów dysków logicznych na określonym komputerze.|  

### <a name="hardware---general"></a>Sprzęt — ogólne  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Informacje dotyczące określonego komputera**|Przedstawia podsumowanie informacji o określonym komputerze.|  
|**Komputery w określonej grupie roboczej lub domenie**|Przedstawia listę komputerów w określonej grupie roboczej lub domenie.|  
|**Klasy spisu przypisane do określonej kolekcji**|Przedstawia klasy spisu przypisane do określonej kolekcji.|  
|**Klasy spisu włączone na określonym komputerze**|Przedstawia klasy spisu włączone na określonym komputerze.|  

### <a name="hardware---memory"></a>Sprzęt — pamięć  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Komputery których pamięć fizyczna uległa zmianie**|Przedstawia listę komputerów, na których ilość pamięci RAM zmieniła się od ostatniego cyklu spisu.|  
|**Komputery z określoną ilością pamięci**|Przedstawia listę komputerów, które mają określoną ilość pamięci RAM (całkowita ilość pamięci fizycznej zaokrąglona do najbliższego MB).|  
|**Komputery z niewielką ilością wolnej pamięci (mniejszą lub równą określonej w MB)**|Przedstawia listę komputerów z małą ilością pamięci. Ilość pamięci do sprawdzenia jest wyrażona w megabajtach.|  
|**Liczba konfiguracji pamięci**|Przedstawia liczbę komputerów w spisie uporządkowanych według ilości pamięci RAM.|  
|**Informacje o pamięci dla określonego komputera**|Przedstawia podsumowanie informacji o pamięci na określonym komputerze.|  

### <a name="hardware---modem"></a>Sprzęt — Modem  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Komputery dla określonego producenta modemu**|Przedstawia listę komputerów z modemem oferowanym przez określonego producenta.|  
|**Liczba modemów według producenta**|Przedstawia liczbę modemów w spisie dla każdego producenta modemów.|  
|**Informacje dotyczące modemu dla pojedynczego komputera**|Przedstawia podsumowanie informacji o modemie na określonym komputerze.|  

### <a name="hardware---network-adapter"></a>Sprzęt — karta sieciowa  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Komputery z określoną kartą sieciową**|Przedstawia listę komputerów z określoną kartą sieciową.|  
|**Liczba kart sieciowych według typu**|Przedstawia liczbę kart sieciowych w spisie uporządkowanych według typu.|  
|**Informacje dotyczące karty sieciowej dla określonego komputera**|Przedstawia informacje o kartach sieciowych zainstalowanych na określonym komputerze.|  

### <a name="hardware---processor"></a>Sprzęt — procesor  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Komputery z procesorem o określonej szybkości**|Przedstawia listę komputerów z procesorem o określonej szybkości.|  
|**Komputery wyposażone w szybkie procesory (większe niż lub równej określonej szybkości zegara)**|Przedstawia listę komputerów z procesorami o szybkości większej niż określona.|  
|**Komputery wyposażone w wolne procesory (o szybkości mniejszej lub równej określonej szybkości zegara)**|Przedstawia listę komputerów z procesorami działającymi z określoną szybkością zegara lub wolniej.|  
|**Liczba szybkości procesora**|Przedstawia liczbę komputerów w spisie uporządkowanych według szybkości procesora.|  
|**Informacje dotyczące procesora dla pojedynczego komputera**|Przedstawia informacje o procesorach zainstalowanych na określonym komputerze.|  

### <a name="hardware---scsi"></a>Sprzęt — SCSI  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Komputery z określoną kartą SCSI typem**|Przedstawia listę komputerów z zainstalowaną określoną kartą SCSI.|  
|**Liczba typów kart SCSI**|Przedstawia liczbę kart SCSI w spisie uporządkowanych według typu karty.|  
|**Informacje dotyczące karty SCSI dla pojedynczego komputera**|Przedstawia informacje o kartach SCSI zainstalowanych na określonym komputerze.|  

### <a name="hardware---sound-card"></a>Sprzęt — karta dźwiękowa  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Komputery z określoną kartą dźwiękową**|Przedstawia listę komputerów z określoną kartą dźwiękową.|  
|**Liczba kart dźwiękowych**|Przedstawia liczbę komputerów w spisie uporządkowanych według typu karty dźwiękowej.|  
|**Informacje o karty dźwiękowej dla pojedynczego komputera**|Przedstawia podsumowanie informacji o karcie dźwiękowej na określonym komputerze.|  

### <a name="hardware---video-card"></a>Sprzęt — karta wideo  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Komputery z określoną kartą graficzną**|Przedstawia listę komputerów z określoną kartą wideo.|  
|**Liczba kart graficznych według typu**|Przedstawia listę wszystkich kart wideo zainstalowanych na komputerach oraz liczbę kart wideo każdego typu.|  
|**Informacje dotyczące karty graficznej dla pojedynczego komputera**|Przedstawia informacje o kartach wideo zainstalowanych na określonym komputerze.|  

### <a name="migration"></a>Migracja  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Klienci na liście wykluczeń**|Przedstawia klientów wykluczonych z migracji.|  
|**Zależność od kolekcji programu Configuration manager**|Przedstawia obiekty zależne od kolekcji hierarchii źródłowej.|  
|**Właściwości zadania migracji**|Przedstawia zawartość określonego zadania migracji.|  
|**Zadania migracji**|Przedstawia listę zadań migracji.|  
|**Obiekty niezmigrowane**|Przedstawia listę obiektów, dla których ostatnia próba migracji zakończyła się niepowodzeniem.|  

### <a name="network"></a>Sieć  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Liczba adresów IP według podsieci**|Przedstawia liczbę adresów IP w spisie dla każdej podsieci IP.|  
|**IP - wszystkie podsieci według maski podsieci**|Przedstawia listę podsieci i masek podsieci IP.|  
|**IP — komputery w określonej podsieci**|Przedstawia listę komputerów i informacje o adresie IP dla określonej podsieci IP.|  
|**IP - informacje dotyczące określonego komputera**|Przedstawia podsumowanie informacji na temat adresu IP na określonym komputerze.|  
|**IP - informacje dotyczące określonego adresu IP**|Przedstawia podsumowanie informacji na temat określonego adresu IP.|  
|**MAC - komputery z określonym adresem MAC**|Przedstawia nazwę komputera i adres IP dla komputerów z określonym adresem MAC.|  

### <a name="network-access-protection"></a>Ochrona dostępu do sieci  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Porównanie aktualizacji oprogramowania zainstalowanych przez wdrożenia aktualizacji oprogramowania i korygowanie translatora adresów SIECIOWYCH.**|Przedstawia podsumowanie porównania aktualizacji oprogramowania zainstalowanych w ramach wdrożeń aktualizacji oprogramowania i korekty ochrony dostępu do sieci.|  
|**Częstotliwość komputer był podlegających korygowaniu w określonym przedziale czasu**|Przedstawia częstotliwość, z którą komputer był korygowany w określonym przedziale czasu.|  
|**Lista komputerów które zainstalowana określona aktualizacja oprogramowania przy użyciu funkcji korygowania w określonym przedziale czasu**|Przedstawia listę komputerów, na których zainstalowano określoną aktualizację oprogramowania przy użyciu funkcji korygowania w określonym przedziale czasu (w dniach).|  
|**Lista komputerów które będą niezgodne na podstawie wybranych aktualizacji oprogramowania**|Przedstawia listę komputerów, które będą niezgodne na podstawie wybranych aktualizacji oprogramowania.|  
|**Lista komputerów, których nie można wykryć usługi translatora adresów SIECIOWYCH**|Przedstawia listę komputerów, na których nie można wykryć usługi ochrony dostępu do sieci.|  
|**Lista komputerów uprawnionych ochrony dostępu do sieci**|Przedstawia listę komputerów, na których usługa ochrony dostępu do sieci nie została uruchomiona lub jej stan jest nieznany.|  
|**Lista zasad translatora adresów sieciowych**|Przedstawia zasady ochrony dostępu do sieci oraz ich daty obowiązywania.|  
|**Lista niezgodnych komputerów podlegających korygowaniu od ostatniego interwału sondowania**|Przedstawia listę niezgodnych komputerów podlegających korygowaniu oraz ich ostatnich znanych czasów oceny.|  
|**Lista niezgodnych komputerów podlegających korygowaniu w określonym przedziale czasu**|Przedstawia listę niezgodnych komputerów podlegających korygowaniu w określonym przedziale czasu.|  
|**Lista błędów korygowania w określonym przedziale czasu**|Przedstawia listę błędów korygowania dla określonej liczby dni.|  
|**Lista aktualizacji oprogramowania zainstalowanych przy użyciu funkcji korygowania**|Przedstawia aktualizacje oprogramowania zainstalowane przy użyciu funkcji korygowania w określonym przedziale czasu.|  
|**Podsumowanie niezgodnych komputerów podlegających korygowaniu od ostatniego interwału sondowania**|Przedstawia podsumowanie niezgodnych komputerów podlegających korygowaniu od ostatniego interwału sondowania.|  
|**Podsumowanie niezgodnych komputerów podlegających korygowaniu w określonym przedziale czasu**|Przedstawia podsumowanie niezgodnych komputerów podlegających korygowaniu w określonym przedziale czasu.|  

### <a name="operating-system"></a>System operacyjny  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Historia wersji systemu operacyjnego na komputerze**|Przedstawia historię spisu dla systemu operacyjnego na określonym komputerze.|  
|**Komputery z określonym systemem operacyjnym**|Przedstawia komputery z określonym systemem operacyjnym.|  
|**Komputery z określonym systemem operacyjnym i dodatkiem service pack**|Przedstawia komputery z określonym systemem operacyjnym i dodatkiem Service Pack.|  
|**Liczba wersji systemu operacyjnego**|Przedstawia liczbę komputerów w spisie uporządkowanych według systemu operacyjnego.|  
|**Liczba systemów operacyjnych i dodatków service pack**|Przedstawia liczbę komputerów w spisie uporządkowanych według kombinacji systemu operacyjnego i dodatku Service Pack.|  
|**Usługi - komputery z uruchomioną określoną usługą**|Przedstawia listę komputerów z uruchomioną określoną usługą.|  
|**Usługi - komputery z uruchomionym serwerem dostępu zdalnego**|Przedstawia listę komputerów z uruchomionym serwerem dostępu zdalnego.|  
|**Usługi - informacje dotyczące określonego komputera usług**|Przedstawia podsumowanie informacji o usługach na określonym komputerze.|  
|**Komputery z systemem Windows Server**|Przedstawia listę komputerów z systemem operacyjnym Windows Server.|  

### <a name="out-of-band-management"></a>Zarządzanie poza pasmem  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Komputery z kontrolerami zarządzania poza pasmem**|Przedstawia listę komputerów z kontrolerami zarządzania poza pasmem.|  
|**Poza aktywność konsoli zarządzania poza pasmem**|Przedstawia listę komunikatów o stanie identyfikujących aktywność konsoli zarządzania poza pasmem.|  
|**Stan zainicjowania klientem poza pasmem zarządzania**|Przedstawia listę komputerów, których obsługa administracyjna została zainicjowana na potrzeby zarządzania poza pasmem.|  

### <a name="power-management"></a>Zarządzanie energią  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Zarządzanie energią - aktywność komputera**|Przedstawia wykres aktywności monitora, komputera i użytkownika dla określonej kolekcji w określonym przedziale czasu.|  
|**Zarządzanie energią - aktywność komputera według komputera**|Przedstawia wykres aktywności monitora, komputera i użytkownika dla określonego komputera w określonym dniu.|  
|**Zarządzanie energią - szczegóły aktywności komputera**|Przedstawia listę możliwości uśpienia i przebudzenia komputerów w określonej kolekcji w określonym dniu i o określonej godzinie.|  
|**Zarządzanie energią — szczegóły komputera**|Przedstawia szczegółowe informacje na temat możliwości zasilania, ustawień zasilania i planów zasilania zastosowanych na określonym komputerze.|  
|**Zarządzanie energią - szczegóły komputerów bez zgłoszeń**|Przedstawia listę komputerów niezgłaszających żadnej aktywności związanej z zasilaniem dla określonej daty i godziny.|  
|**Zarządzanie energią — wykluczone komputery**|Przedstawia listę komputerów wykluczonych z planu zasilania.|  
|**Zarządzanie energią - komputery z wieloma planami zasilania**|Przedstawia listę komputerów, na których zastosowano wiele ustawień zasilania powodujących konflikt.|  
|**Zarządzanie energią - pobór energii**|Przedstawia całkowite miesięczne zużycie energii (w kWh) dla określonej kolekcji w określonym przedziale czasu.|  
|**Zarządzanie energią - pobór energii wg dnia**|Przedstawia całkowite zużycie energii (w kWh) dla określonej kolekcji w ciągu ostatnich 31 dni.|  
|**Zarządzanie energią - koszt energii**|Przedstawia całkowity miesięczny koszt zużycia energii dla określonej kolekcji w określonym przedziale czasu.|  
|**Zarządzanie energią - koszt energii wg dnia**|Przedstawia całkowity koszt zużycia energii dla określonej kolekcji w ciągu ostatnich 31 dni.|  
|**Zarządzanie energią — wpływ na środowisko**|Przedstawia wykres emisji dwutlenku węgla (CO2) generowanego przez określoną kolekcję w określonym przedziale czasu.|  
|**Zarządzanie energią — wpływ na środowisko wg dnia**|Przedstawia wykres emisji dwutlenku węgla (CO2) generowanego przez określoną kolekcję w ciągu ostatnich 31 dni.|  
|**Zarządzanie energią - szczegóły braku usypiania komputera**|Przedstawia szczegółowe informacje dotyczące komputerów, które nie były wprowadzane w stan uśpienia ani hibernacji w określonym przedziale czasu.|  
|**Zarządzanie energią — raport o braku usypiania**|Przedstawia listę typowych przyczyn, które uniemożliwiały włączanie stanu uśpienia i hibernacji na komputerach, oraz liczbę komputerów, których te przyczyny dotyczyły, w określonym przedziale czasu.|  
|**Zarządzanie energią — możliwości zasilania**|Przedstawia możliwości zarządzania energią dla komputerów w określonej kolekcji.|  
|**Zarządzanie energią — ustawienia zasilania**|Przedstawia zagregowaną listę ustawień zasilania używanych na komputerach w określonej kolekcji.|  
|**Zarządzanie energią - szczegóły ustawień zasilania**|Używane, aby wyświetlić więcej informacji o komputerach, które zostały określone w **zarządzanie energią — ustawienia zasilania** raportu.|  

### <a name="replication-traffic"></a>Ruch związany z replikacją  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Globalny danych replikacji ruchu na jedno łącze (wykres liniowy)**|Przedstawia całkowity ruch związany z replikacją danych globalnych za pomocą określonego linku dla określonej liczby dni.|  
|**Globalny danych replikacji ruchu na jedno łącze (wykres kołowy)**|Przedstawia całkowity ruch związany z replikacją danych globalnych za pomocą określonego linku dla określonej liczby dni.|  
|**Ruch związany z replikacją hierarchii według łącza**|Przedstawia całkowity ruch związany z replikacją dla każdego linku w hierarchii w ciągu określonej liczby dni.|  
|**Hierarchii pierwszych dziesięciu replikacji grupy ruchu na jedno łącze (wykres kołowy)**|Przedstawia ruch związany z replikacją dla dziesięciu najczęściej używanych grup replikacji w całej hierarchii, które są identyfikowane za pomocą linku.|  
|**Ruch związany z replikacją łącza**|Przedstawia całkowity ruch związany z replikacją dla wszystkich danych w ciągu określonej liczby dni.|  
|**Ruch związany z grupami replikacji na jedno łącze**|Przedstawia ruch sieciowy związany z grupami replikacji dla określonego linku replikacji bazy danych w ciągu określonej liczby dni.|  
|**Witryna danych replikacji ruchu na jedno łącze (wykres liniowy)**|Przedstawia całkowity ruch związany z replikacją danych lokacji za pomocą określonego linku w ciągu określonej liczby dni.|  
|**Witryna danych replikacji ruchu na jedno łącze (wykres kołowy)**|Przedstawia całkowity ruch związany z replikacją danych lokacji za pomocą określonego linku w ciągu określonej liczby dni.|  
|**Całkowita liczba replikacją hierarchii (wykres liniowy)**|Przedstawia replikację zagregowanych danych hierarchii — lokacji i globalnych — w każdym kierunku linku w ciągu określonej liczby dni.|  
|**Całkowita liczba replikacją hierarchii (wykres kołowy)**|Przedstawia replikację zagregowanych danych hierarchii — lokacji i globalnych — w każdym kierunku linku w ciągu określonej liczby dni.|  

### <a name="site---client-information"></a>Lokacja — informacje o kliencie  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Raport o stanie szczegółowym przypisywania klienta**|Przedstawia szczegółowe informacje na temat stanu przypisywania klientów.|  
|**Szczegóły niepowodzenia przypisywania klienta**|Przedstawia szczegółowe informacje na temat niepowodzeń przypisywania klientów.|  
|**Szczegóły stanu przypisywania klientów**|Przedstawia omówienie stanu przypisywania klientów.|  
|**Szczegóły powodzenia przypisywania klienta**|Przedstawia szczegółowe informacje na temat pomyślnie przypisanych klientów.|  
|**Raport niepowodzeń wdrażania klientów**|Przedstawia szczegółowe informacje na temat klientów, których nie można było wdrożyć.|  
|**Szczegóły stanu wdrożenia klienta**|Przedstawia podsumowanie informacji na temat stanu instalacji klientów.|  
|**Raport powodzeń wdrażania klientów**|Przedstawia szczegółowe informacje na temat klientów, którzy zostali pomyślnie wdrożeni.|  
|**Klienci bez możliwości komunikacji protokołu HTTPS**|Przedstawia szczegółowe informacje na temat każdego klienta w lokacji, dla którego uruchomiono narzędzie sprawdzania gotowości do komunikacji przy użyciu protokołu HTTPS i który został zgłoszony jako klient bez możliwości komunikacji przy użyciu protokołu HTTPS.|  
|**Komputery przypisane, ale niezainstalowane dla określonej lokacji**|Przedstawia listę komputerów, które zostały przypisane do określonej lokacji, ale raportowanie nie odbywa się w tej lokacji.|  
|**Komputery z określoną wersją klienta programu Configuration Manager**|Wyświetla listę komputerów z określoną wersją oprogramowania klienckiego programu Configuration Manager.|  
|**Liczba klientów i protokół używany do komunikacji**|Przedstawia podsumowanie metod komunikacji używanych przez klientów (protokół HTTP lub HTTPS).|  
|**Liczba klientów przypisanych i zainstalowanych dla każdej lokacji**|Przedstawia liczbę komputerów przypisanych i zainstalowanych w każdej lokacji. Klienci z lokalizacją sieciową skojarzoną z wieloma lokacjami są traktowani jako zainstalowani, jeśli ich raportowanie dotyczy tej lokacji.|  
|**Liczba klientów z obsługą komunikacji protokołu HTTPS**|Przedstawia szczegółowe informacje na temat każdego klienta w lokacji, dla którego uruchomiono narzędzie sprawdzania gotowości do komunikacji przy użyciu protokołu HTTPS i który został zgłoszony jako klient z możliwością komunikacji przy użyciu protokołu HTTPS lub bez tej możliwości.|  
|**Liczba klientów dla każdej lokacji**|Wyświetla liczbę klientów programu Configuration Manager zainstalowane według kodu lokacji.|  
|**Klientów liczba programu Configuration Manager według wersji klienta**|Wyświetla liczbę komputerów wykrytych przez wersję klienta programu Configuration Manager.|  
|**Szczegóły problemu raportowanego do punktu stanu powrotu dla określonej kolekcji**|Przedstawia szczegółowe informacje na temat problemów zgłoszonych przez klientów w określonej kolekcji, jeśli przypisano do nich rezerwowy punkt stanu.|  
|**Szczegóły problemu raportowanego do punktu stanu powrotu dla określonej lokacji**|Przedstawia szczegółowe informacje na temat problemów zgłoszonych przez klientów w określonej lokacji, jeśli przypisano do nich rezerwowy punkt stanu.|  
|**Podsumowanie problemów raportowanych do punktu stanu powrotu**|Przedstawia informacje na temat wszystkich problemów zgłoszonych przez klientów, jeśli przypisano do nich rezerwowy punkt stanu.|  
|**Podsumowanie problemów raportowanych do punktu stanu powrotu dla określonej kolekcji**|Przedstawia podsumowanie informacji na temat problemów zgłoszonych przez klientów w określonej kolekcji, jeśli przypisano do nich rezerwowy punkt stanu.|  

### <a name="site---discovery-and-inventory-information"></a>Lokacja — odnajdywania i informacje o spisie  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Klienci, którzy nie zgłosili się ostatnio (w ciągu określonej liczby dni)**|Przedstawia listę klientów, którzy nie raportowali danych odnajdowania, spisu sprzętu ani spisu oprogramowania w ciągu określonej liczby dni.|  
|**Komputery odnalezione przez określoną lokację**|Przedstawia listę wszystkich komputerów wykrytych według określonej lokacji i daty ostatniego odnajdowania.|  
|**Komputery odnalezione ostatnio według metody odnajdywania**|Przedstawia listę komputerów, które zostały odnalezione w ciągu określonej liczby dni, oraz listę agentów, którzy je odnaleźli. Komputer może pojawić się więcej niż jeden raz na liście, jeśli został odnaleziony przez wielu agentów.|  
|**Komputery nieodnalezione ostatnio (w ciągu określonej liczby dni)**|Przedstawia listę komputerów, które nie zostały ostatnio odnalezione, i liczbę dni od momentu ich odnalezienia.|  
|**Komputery niespisane ostatnio (w ciągu określonej liczby dni)**|Przedstawia liczbę komputerów, które nie były ostatnio umieszczane w spisie, oraz czas ich ostatniego umieszczenia w spisie.|  
|**Komputery, które mogą współdzielić sam Unikatowy identyfikator programu Configuration Manager**|Przedstawia listę komputerów, których nazwy zostały zmienione. Zmiana nazwy jest możliwym objawem dwa komputera identyfikatora unikatowego programu Configuration Manager z innego komputera.|  
|**Komputery ze zduplikowanymi adresami MAC**|Przedstawia komputery korzystające z tego samego adresu MAC.|  
|**Liczba komputerów w domenach zasobów lub grupach roboczych**|Przedstawia liczbę komputerów w każdej grupie roboczej lub domenie zasobów.|  
|**Informacje dotyczące odnajdywania określonego komputera**|Przedstawia listę agentów i lokacji, przy użyciu których odnaleziono określony komputer.|  
|**Daty spisu dla określonego komputera**|Przedstawia datę i godzinę ostatniego uruchomienia spisu na określonym komputerze.|  

### <a name="site---general"></a>Lokacja — ogólne  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Komputery w określonej lokacji**|Przedstawia listę komputerów w określonej lokacji.|  
|**Stan lokacji w hierarchii**|Przedstawia listę lokacji w hierarchii oraz informacje na temat wersji i stanu lokacji.|  
|**Stan aktualizacji programu Configuration Manager w hierarchii**|Wyświetla informacje o aktualizacji lokacji programu Configuration Manager w hierarchii.|  

### <a name="site---server-information"></a>Lokacja — informacje o serwerze  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Role systemu lokacji i serwery systemu lokacji dla określonej lokacji**|Przedstawia listę serwerów systemu lokacji i ich ról systemu lokacji dla określonej lokacji.|  

### <a name="software---companies-and-products"></a>Oprogramowanie — firmy i produkty  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Wszystkie spisane produkty określonego producenta oprogramowania**|Przedstawia listę produktów programowych i ich wersji oferowanych przez określonego producenta oprogramowania.|  
|**Wszyscy producenci oprogramowania**|Przedstawia listę wszystkich firm produkujących oprogramowanie uwzględnione w spisie.|  
|**Wszystkie aplikacje systemu Windows**|Przedstawia podsumowanie zainstalowanych aplikacji systemu Windows uporządkowanych według liczby wystąpień na podstawie kryteriów wyszukiwania dla nazwy aplikacji, architektury lub wydawcy.|  
|**Komputery z określonym produktem**|Przedstawia listę komputerów, na których znajduje się określony produkt uwzględniony w spisie, wraz z wersją tego produktu.|  
|**Komputery z określonym produktem nazwa i wersja**|Przedstawia listę komputerów, na których znajduje się określona wersja produktu uwzględniona w spisie.|  
|**Komputery z określonym oprogramowaniem zarejestrowanym w aplecie Dodaj Usuń programy**|Przedstawia podsumowanie wszystkich komputerów z określonym oprogramowaniem zarejestrowanym w aplecie Dodaj/Usuń programy lub Programy i funkcje.|  
|**Liczba wszystkich spisanych produktów i ich wersji**|Przedstawia listę programów i wersji uwzględnionych w spisie oraz liczbę komputerów, na których zainstalowano każdy z nich.|  
|**Liczba spisanych produktów i wersji określonego produktu**|Przedstawia listę wersji określonego produktu uwzględnionych w spisie oraz liczbę komputerów, na których zainstalowano każdą z nich.|  
|**Liczba wszystkich wystąpień oprogramowania zarejestrowanego w aplecie Dodaj / Usuń programy**|Przedstawia podsumowanie wszystkich wystąpień oprogramowania zainstalowanego i zarejestrowanego przy użyciu apletu Dodaj/Usuń programy lub Programy i funkcje na komputerach w określonej kolekcji.|  
|**Liczba wystąpień określonego oprogramowania zarejestrowanego w aplecie Dodaj / Usuń programy**|Przedstawia liczbę wystąpień dla określonych pakietów oprogramowania zainstalowanych i zarejestrowanych w aplecie Dodaj/Usuń programy lub Programy i funkcje.|  
|**Instalacje określonych aplikacji systemu Windows**|Przedstawia listę wszystkich komputerów z określoną aplikacją systemu Windows.|  
|**Produkty na określonym komputerze**|Przedstawia podsumowanie programów uwzględnionych w spisie i ich producentów na określonym komputerze.|  
|**Oprogramowanie zarejestrowane w aplecie Dodaj Usuń programy na określonym komputerze**|Przedstawia podsumowanie wszystkich programów zainstalowanych na określonym komputerze, które zarejestrowano w aplecie Dodaj/Usuń programy lub Programy i funkcje.|  
|**Aplikacje systemu Windows zainstalowane dla określonego użytkownika.**|Przedstawia wszystkie aplikacje systemu Windows zainstalowane dla określonego użytkownika.|  

### <a name="software---files"></a>Oprogramowanie — pliki  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Wszystkie spisane pliki określonego produktu**|Przedstawia podsumowanie plików uwzględnionych w spisie i skojarzonych z określonym programem.|  
|**Wszystkie spisane pliki na określonym komputerze**|Przedstawia podsumowanie wszystkich plików uwzględnionych w spisie i przechowywanych na określonym komputerze.|  
|**Porównanie spisu oprogramowania na dwóch komputerach**|Przedstawia różnice między spisami oprogramowania zgłoszonymi dla dwóch określonych komputerów.|  
|**Komputery z określonym plikiem**|Przedstawia listę komputerów, na których zgromadzono dane spisu oprogramowania dla określonej nazwy pliku. Komputer może pojawić się więcej niż jeden raz na liście, jeśli zawiera wiele kopii pliku.|  
|**Liczba komputerów z określoną nazwą pliku**|Przedstawia liczbę komputerów, na których zgromadzono dane spisu oprogramowania dla określonego pliku.|  

### <a name="software-distribution---application-monitoring"></a>Dystrybucja oprogramowania — monitorowanie aplikacji  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Wszystkie wdrożenia aplikacji (zaawansowane)**|Przedstawia szczegółowe podsumowanie informacji na temat wszystkich wdrożeń aplikacji.|  
|**Wszystkie wdrożenia aplikacji (basic)**|Przedstawia podsumowanie informacji na temat wszystkich wdrożeń aplikacji.|  
|**Zgodność aplikacji**|Przedstawia informacje na temat zgodności dla określonej aplikacji w określonej kolekcji.|  
|**Wdrożenia aplikacji na zasób**|Przedstawia aplikacje wdrożone do określonego urządzenia lub użytkownika.|  
|**Szczegóły błędów infrastruktury aplikacji**|Przedstawia błędy infrastruktury aplikacji.  Mogą być to zarówno wewnętrzne błędy infrastruktury, jak i błędy wynikające z nieprawidłowych reguł dotyczących wymagań.|  
|**Szczegółowy stan użytkowania aplikacji**|Przedstawia szczegóły użycia zainstalowanych aplikacji.|  
|**Podsumowanie stanu użycia aplikacji**|Przedstawia podsumowanie użycia zainstalowanych aplikacji.|  
|**Wdrożenia sekwencji zadań zawierające aplikację**|Przedstawia wdrożenia sekwencji zadań, które umożliwiają zainstalowanie określonej aplikacji.|  
|**Żądania użytkowników dla aplikacji systemu Android**|Przedstawia użytkowników, którzy zażądali zainstalowania aplikacji systemu Android.|  
|**aplikacje systemu iOS z nieudanymi wdrożeniami (aplikacja jest już zainstalowana)**|Zawiera informacje o zgodności wybranej aplikacji systemu iOS wdrożonej jako „Pakiet aplikacji dla systemu iOS ze sklepu App Store”, który został skojarzony z zasadami zarządzania aplikacjami mobilnymi. Ten raport zawiera informacje o użytkownikach i urządzeniach, dla których instalacja aplikacji nie powiodła się, ponieważ aplikacja została już ręcznie zainstalowana przez użytkownika.|  

### <a name="software-distribution---collections"></a>Dystrybucja oprogramowania — kolekcje  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Wszystkie kolekcje**|Przedstawia wszystkie kolekcje w hierarchii.|  
|**Wszystkie zasoby w określonej kolekcji**|Przedstawia wszystkie zasoby w określonej kolekcji.|  
|**Okna obsługi dostępne dla określonego klienta**|Przedstawia wszystkie okna obsługi, które można zastosować do określonego klienta.|  

### <a name="software-distribution---content"></a>Dystrybucja oprogramowania — zawartość  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Wszystkie aktywne dystrybucje zawartości**|Przedstawia wszystkie punkty dystrybucji, w których zawartość jest obecnie instalowana lub usuwana.|  
|**Cała zawartość**|Przedstawia wszystkie aplikacje i pakiety w lokacji.|  
|**Cała zawartość w określonym punkcie dystrybucji**|Przedstawia całą zawartość aktualnie instalowaną w określonym punkcie dystrybucji.|  
|**Wszystkie punkty dystrybucji**|Przedstawia informacje na temat punktów dystrybucji dla każdej lokacji.|  
|**Wszystkie komunikaty o stanie dla określonego pakietu w określonym punkcie dystrybucji**|Przedstawia wszystkie komunikaty o stanie dla określonego pakietu w określonym punkcie dystrybucji.|  
|**Stan dystrybucji zawartości aplikacji**|Przedstawia informacje na temat stanu dystrybucji zawartości aplikacji.|  
|**Aplikacje przeznaczone dla grupy punktów dystrybucji**|Przedstawia informacje na temat zawartości aplikacji, która została wdrożona do określonej grupy punktów dystrybucji.|  
|**Aplikacje niezsynchronizowane w dystrybucji określonej grupie punktów**|Przedstawia aplikacje, dla których skojarzone pliki zawartości nie zostały zaktualizowane do najnowszej wersji w określonej grupie punktów dystrybucji.|  
|**Grupy punktów dystrybucji**|Przedstawia informacje na temat określonej grupy punktów dystrybucji.|  
|**Podsumowanie użycia punktu dystrybucji**|Przedstawia podsumowanie użycia każdego z punktów dystrybucji.|  
|**Stan dystrybucji określonego pakietu**|Przedstawia stan dystrybucji zawartości określonego pakietu w każdym punkcie dystrybucji.|  
|**Pakiety przeznaczone do grupy punktów dystrybucji**|Przedstawia informacje na temat pakietów przeznaczonych dla określonej grupy punktów dystrybucji.|  
|**Pakiety niezsynchronizowane w dystrybucji określonej grupie punktów**|Przedstawia pakiety, dla których skojarzone pliki zawartości nie zostały zaktualizowane do najnowszej wersji w określonej grupie punktów dystrybucji.|  

### <a name="software-distribution---package-and-program-deployment"></a>Dystrybucja oprogramowania - wdrażanie pakietów i programów  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Wszystkie wdrożenia określonego pakietu lub programu**|Przedstawia informacje na temat wszystkich wdrożeń określonego pakietu i programu.|  
|**Wszystkie wdrożenia pakietów i programów**|Przedstawia wszystkie wdrożenia pakietów i programów w danej lokacji.|  
|**Wszystkie wdrożenia pakietów i programów w określonej kolekcji**|Przedstawia wszystkie wdrożenia pakietów i programów do określonej kolekcji.|  
|**Wszystkie wdrożenia pakietów i programów na określonym komputerze**|Przedstawia wszystkie wdrożenia pakietów i programów zastosowane na określonym komputerze.|  
|**Wszystkie wdrożenia pakietów i programów dla określonego użytkownika**|Przedstawia wszystkie wdrożenia pakietów i programów do określonego użytkownika.|  

### <a name="software-distribution---package-and-program-deployment-status"></a>Dystrybucja oprogramowania — stan pakietów i programów wdrożenia  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Wszystkie wdrożenia zasobów systemu pakietów i programów o stanie**|Przedstawia wszystkie wdrożenia pakietów i programów dla lokacji oraz podsumowanie stanu każdego wdrożenia.|  
|**Wszystkie zasoby systemu dla określonego wdrożenia pakietu i programu w określonym stanie**|Przedstawia listę zasobów w określonym stanie dla określonego wdrożenia pakietu i programu.|  
|**Wykres - godzinny stan o wykonania wdrożenia pakietu i programu**|Przedstawia wartość procentową liczby komputerów, na których pomyślnie zainstalowano pakiet, dla każdej godziny od momentu utworzenia wdrożenia pakietu i programu. W tym raporcie można śledzić średni czas wdrażania pakietu i programu.|  
|**Stan wdrażania pakietów i programów dla określonego klienta i wdrożenia**|Przedstawia komunikaty o stanie zgłoszone dla określonego komputera oraz wdrożenia pakietu i programu.|  
|**Stan określonego wdrożenia pakietu i programu**|Przedstawia podsumowanie stanu określonego wdrożenia pakietu i programu.|  

### <a name="software-metering"></a>Pomiar użytkowania oprogramowania  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Wszystkie reguły zliczania oprogramowania zastosowanie do tej lokacji**|Przedstawia listę wszystkich reguł pomiaru użytkowania oprogramowania w lokacji.|  
|**Komputery, które mierzonym programem, ale program ten nie został uruchomiony od określonej daty**|Przedstawia wszystkie komputery z zainstalowaną określoną mierzoną aplikacją zgłoszoną w spisie oprogramowania, która nie była uruchamiana od określonej daty.|  
|**Komputery które uruchomiły określony zliczany program**|Przedstawia listę komputerów, na których uruchamiano programy zgodne z określoną regułą pomiaru użytkowania oprogramowania w określonym miesiącu i roku.|  
|**Współbieżne użycie wszystkich zliczanych programów**|Przedstawia maksymalną liczbę użytkowników, którzy jednocześnie uruchamiali każdy mierzony program w określonym miesiącu i roku.|  
|**Analiza trendu współbieżnego użycia określonego zliczanego programu**|Przedstawia maksymalną liczbę użytkowników, którzy jednocześnie uruchamiali określony mierzony program w każdym miesiącu ostatniego roku.|  
|**Zainstaluj podstawa dla wszystkich zliczanych programów**|Przedstawia liczbę komputerów z zainstalowanymi mierzonymi programami zgłoszonymi w spisie oprogramowania. Ten raport wymaga przeprowadzania spisu oprogramowania na mierzonych komputerach.|  
|**Postęp podsumowania zliczania oprogramowania**|Przedstawia czas ostatniego przetwarzania zbiorczych danych pomiarów użytkowania na serwerze lokacji.  Tylko dane pomiarów użytkowania przetworzone przed tymi datami zostaną uwzględnione w raportach pomiaru użytkowania oprogramowania.|  
|**Godzina Podsumowanie użycia określonego zliczanego programu**|Przedstawia średnią liczbę użyć określonego programu w ciągu ostatnich 90 dni z podziałem na godziny i dni.|  
|**Całkowite użycie wszystkich zliczanych programów**|Przedstawia liczbę użytkowników, którzy uruchamiali programy pasujące do każdej reguły pomiaru użytkowania oprogramowania lokalnie lub za pomocą usług terminalowych w określonym miesiącu i roku.|  
|**Całkowite użycie wszystkich zliczanych programów na serwerach terminali systemu Windows**|Przedstawia liczbę użytkowników, którzy uruchamiali programy pasujące do każdej reguły pomiaru użytkowania oprogramowania za pomocą usług terminalowych w określonym miesiącu i roku.|  
|**Analiza trendu łącznego użycia określonego zliczanego programu**|Przedstawia liczbę użytkowników, którzy uruchamiali programy pasujące do określonej reguły pomiaru użytkowania oprogramowania lokalnie lub za pomocą usług terminalowych w każdym miesiącu przez ostatni rok.|  
|**Analiza trendu łącznego użycia określonego zliczanego programu na serwerach terminali systemu Windows**|Przedstawia liczbę użytkowników, którzy uruchamiali programy pasujące do określonej reguły pomiaru użytkowania oprogramowania za pomocą usług terminalowych w każdym miesiącu przez ostatni rok.|  
|**Użytkownicy którzy uruchomili określony zliczany program**|Przedstawia listę użytkowników, którzy uruchamiali programy zgodne z określoną regułą pomiaru użytkowania oprogramowania w określonym miesiącu i roku.|  

### <a name="software-updates---a-compliance"></a>Aktualizacje oprogramowania — zgodność  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Zgodność 1 - zgodność ogólna**|Przedstawia ogólne dane zgodności dla grupy aktualizacji oprogramowania.|  
|**Zgodność 2 - określona aktualizacja oprogramowania**|Przedstawia dane zgodności określonej aktualizacji oprogramowania.|  
|**Zgodność 3 - grupa aktualizacji (według aktualizacji)**|Przedstawia dane zgodności aktualizacji oprogramowania zdefiniowanych w ramach grupy aktualizacji oprogramowania.|  
|**Zgodność 4 - aktualizacje według dostawcy miesiąca i roku**|Przedstawia dane zgodności aktualizacji oprogramowania wydawanych przez dostawcę w określonym miesiącu i roku.|  
|**Zgodność 5 — określony komputer**|Ten raport zwraca dane zgodności aktualizacji oprogramowania dla określonego komputera.  Aby ograniczyć ilość zwracanych informacji, można określić dostawcę i klasyfikację aktualizacji oprogramowania.|  
|**Zgodność 6 - stany określonej aktualizacji oprogramowania (pomocniczy)**|Przedstawia liczbę i procent komputerów w każdym stanie zgodności dla określonej aktualizacji oprogramowania.|  
|**Zgodność 7 - komputery z określonym stanem zgodności dla grupy aktualizacji (pomocniczy)**|Przedstawia wszystkie komputery w kolekcji, które mają określony ogólny stan zgodności względem grupy aktualizacji oprogramowania.|  
|**Zgodność 8 - komputery w określonym stanie zgodności dla aktualizacji (pomocniczy)**|Przedstawia wszystkie komputery w kolekcji, które mają określony ogólny stan zgodności dla aktualizacji oprogramowania.|  

### <a name="software-updates---b-deployment-management"></a>Aktualizacje oprogramowania — Zarządzanie wdrażaniem B  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Zarządzanie 1 - wdrożenia grupy aktualizacji**|Przedstawia wszystkie wdrożenia, które zawierają wszystkie aktualizacje oprogramowania zdefiniowane w określonej grupie aktualizacji oprogramowania.|  
|**Zarządzanie 2 - aktualizacje wymagane lecz Niewdrożone**|Przedstawia wszystkie aktualizacje oprogramowania dla określonego dostawcy, które zostały wykryte jako wymagane na komputerach klienckich, ale które nie zostały wdrożone do określonej kolekcji.|  
|**Zarządzanie 3 - aktualizacje we wdrożeniu**|Przedstawia aktualizacje oprogramowania, które znajdują się w określonym wdrożeniu.|  
|**Zarządzanie 4 - wdrożenia przeznaczone dla kolekcji**|Przedstawia wszystkie wdrożenia aktualizacji oprogramowania, które są przeznaczone dla określonej kolekcji.|  
|**Zarządzanie 5 - wdrożenia przeznaczone dla komputera**|Przedstawia wszystkie wdrożenia aktualizacji oprogramowania, które są przeznaczone dla określonego komputera.|  
|**Zarządzanie 6 - wdrożenia zawierające określoną aktualizację**|Przedstawia wszystkie wdrożenia zawierające określoną aktualizację oprogramowania i skojarzoną kolekcję docelową dla wdrożenia.|  
|**Zarządzanie 7 - aktualizacje wdrożenia z niepełną zawartością**|Przedstawia aktualizacje oprogramowania w określonym wdrożeniu, dla których nie pobrano całej powiązanej zawartości, co uniemożliwiło klientom zainstalowanie aktualizacji i osiągnięcie 100% zgodności wdrożenia.|  
|**Zarządzanie 8 - komputery z niepełną zawartością (pomocniczy)**|Przedstawia wszystkie komputery, które wymagają określonej aktualizacji oprogramowania zawartej w określonym wdrożeniu, którego obsługa administracyjna nie jest inicjowana w punkcie dystrybucji.|  

### <a name="software-updates---c-deployment-states"></a>Aktualizacje oprogramowania — stany wdrożeń C  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Stany 1 - stany wymuszenia wdrożenia**|Przedstawia stany wymuszania dla określonego wdrożenia aktualizacji oprogramowania. Zwykle jest to drugi etap oceny wdrożenia.|  
|**Stany 2 - stany oceny wdrożenia**|Przedstawia stany oceniania dla określonego wdrożenia aktualizacji oprogramowania. Zwykle jest to pierwszy etap oceny wdrożenia.|  
|**Stany 3 — stany wdrożenia i komputera**|Przedstawia stany wszystkich aktualizacji oprogramowania określonego wdrożenia dla określonego komputera.|  
|**Stany 4 - komputery z określonym stanem wdrożenia (pomocniczy)**|Przedstawia wszystkie komputery w określonym stanie dla wdrożenia aktualizacji oprogramowania.|  
|**Stany 5 - stany aktualizacji we wdrożeniu (pomocniczy)**|Przedstawia podsumowanie stanów dla aktualizacji oprogramowania związanej z określonym wdrożeniem.|  
|**Stany 6 — komputery z określonym stanem wymuszenia dla aktualizacji (pomocniczy)**|Przedstawia wszystkie komputery w określonym stanie wymuszania dla określonej aktualizacji oprogramowania.|  

### <a name="software-updates---d-scan"></a>Aktualizacje oprogramowania — skanowanie D  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Skanowanie 1 - ostatnie stany skanowania według kolekcji**|Przedstawia liczbę komputerów dla określonej kolekcji w każdym stanie skanowania zgodności zwróconym przez klientów podczas ostatniego skanowania pod kątem zgodności.|  
|**Skanowanie 2 — stany ostatniego skanowania według lokacji**|Przedstawia liczbę komputerów przypisanych do określonej lokacji w każdym stanie skanowania zgodności zwróconym przez klientów podczas ostatniego skanowania pod kątem zgodności.|  
|**Skanowanie 3 - klienci w kolekcji raportujący określony stan (pomocniczy)**|Przedstawia wszystkie komputery dla określonej kolekcji i określonego stanu skanowania zgodności podczas ich ostatniego skanowania pod kątem zgodności.|  
|**Skanowanie 4 — klienci w lokacji raportujący określony stan (pomocniczy)**|Przedstawia wszystkie komputery przypisane do określonej lokacji i z określonym stanem skanowania zgodności podczas ich ostatniego skanowania pod kątem zgodności.|  

### <a name="software-updates---e-troubleshooting"></a>Aktualizacje oprogramowania — Rozwiązywanie problemów E  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Rozwiązywanie problemów 1 — błędy skanowania**|Przedstawia błędy skanowania w lokacji oraz liczbę komputerów, na których występuje każdy z błędów.|  
|**Rozwiązywanie problemów 2 – błędy wdrożenia**|Przedstawia błędy wdrożenia w lokacji oraz liczbę komputerów, na których występuje każdy z błędów.|  
|**Rozwiązywanie problemów 3 - komputery z niepowodzeniem skanowania z powodu określonego błędu (pomocniczy)**|Przedstawia listę komputerów, których skanowanie nie powiodło się z powodu określonego błędu.|  
|**Rozwiązywanie problemów 4 - komputery z niepowodzeniem z powodu określonego błędu wdrożenia (pomocniczy)**|Przedstawia listę komputerów, na których wdrażanie aktualizacji nie powiodło się z powodu określonego błędu.|  

### <a name="state-migration"></a>Migracja stanu  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Informacje o migracji stanu dla określonego komputera źródłowego**|Przedstawia informacje na temat migracji stanu dla określonego komputera.|  
|**Informacje o migracji stanu dla określonego punktu migracji stanu**|Przedstawia informacje na temat migracji stanu dla określonego punktu migracji stanu.|  
|**Punkty migracji stanu dla określonej lokacji**|Przedstawia punkty migracji stanu dla określonej lokacji.|  

### <a name="status-messages"></a>Komunikaty o stanie  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Wszystkie komunikaty z określonym Identyfikatorem komunikatu**|Przedstawia listę komunikatów o stanie z określonym identyfikatorem komunikatu.|  
|**Klienci raportujący błędy w ciągu ostatnich 12 godzin dla określonej lokacji**|Przedstawia listę komputerów i składników zgłaszających błędy w ciągu ostatnich 12 godzin oraz liczbę zgłoszonych błędów.|  
|**Komunikaty składników z ostatnich 12 godzin**|Przedstawia listę komunikatów składników z ostatnich 12 godzin dla określonego kodu lokacji, komputera i składnika.|  
|**Komunikaty składników z ostatniej godziny**|Wyświetla listę komunikatów o stanie utworzonych w ciągu ostatniej godziny przez określony składnik na określonym komputerze w określonej lokacji programu Configuration Manager.|  
|**Liczba komunikatów składników z ostatniej godziny dla określonej lokacji**|Przedstawia liczbę komunikatów o stanie zgłoszonych w ciągu ostatniej godziny w określonej lokacji i uporządkowanych według składnika i ważności.|  
|**Liczba błędów w ciągu ostatnich 12 godzin**|Przedstawia liczbę komunikatów o stanie błędów składników serwera w ciągu ostatnich 12 godzin.|  
|**Błędy krytyczne (według składnika)**|Przedstawia listę komputerów zgłaszających błędy krytyczne uporządkowaną według składnika.|  
|**Błędy krytyczne (według nazwy komputera)**|Przedstawia listę komputerów zgłaszających błędy krytyczne uporządkowaną według nazwy komputera.|  
|**Ostatnie 1000 komunikatów dla określonego komputera (błędy i ostrzeżenia)**|Przedstawia podsumowanie ostatniego 1000 komunikatów o stanie składnika wskazujących na błąd i ostrzeżenie dla określonego komputera.|  
|**Ostatnie 1000 komunikatów dla określonego komputera (błędy ostrzeżenia i informacje)**|Przedstawia podsumowanie ostatniego 1000 komunikatów o stanie składnika wskazujących na błąd, ostrzeżenie i informacje dla określonego komputera.|  
|**Ostatnie 1000 komunikatów dla określonego komputera (błędy)**|Przedstawia podsumowanie ostatniego 1000 komunikatów o stanie składnika wskazujących na błąd dla określonego komputera.|  
|**Ostatnie 1000 komunikatów dla określonego składnika serwera**|Przedstawia podsumowanie ostatniego 1000 komunikatów o stanie dla określonego składnika serwera.|  

### <a name="status-messages---audit"></a>Komunikaty o stanie — inspekcja  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Wszystkie komunikaty audytu dla określonego użytkownika**|Przedstawia podsumowanie wszystkich komunikatów inspekcji dla określonego użytkownika. Komunikaty inspekcji opisują akcje wykonywane w konsoli programu Configuration Manager, które dodawania, modyfikowania i usuwania obiektów w programie Configuration Manager.|  
|**Sterowanie zdalne - wszystkie komputery zdalnie sterowane przez określonego użytkownika**|Przedstawia podsumowanie komunikatów o stanie wskazujących na zdalne sterowanie komputerami klienckimi przez określonego użytkownika.|  
|**Sterowanie zdalne - wszystkie informacje dotyczące sterowania zdalnego**|Przedstawia podsumowanie komunikatów o stanie powiązanych ze zdalnym sterowaniem komputerami klienckimi.|  

### <a name="task-sequence---deployment-status"></a>Sekwencja zadań — stan wdrożenia  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Wszystkie zasoby systemowe dla wdrożenia sekwencji zadań w określonym stanie**|Przedstawia listę komputerów docelowych dla określonego wdrożenia sekwencji zadań w określonym stanie wdrożenia.|  
|**Wszystkie zasoby systemowe dla wdrożenia sekwencji zadań, który znajduje się w określonym stanie i że jest dostępne dla nieznanych komputerów**|Przedstawia listę komputerów docelowych dla określonego wdrożenia sekwencji zadań w określonym stanie wdrożenia.|  
|**Liczba zasobów systemowych, które mają wdrożenia sekwencji zadań przypisane, ale nie został jeszcze uruchomiony**|Przedstawia liczbę komputerów z zaakceptowanymi sekwencjami zadań, dla których nie uruchomiono sekwencji zadań.|  
|**Historia wdrożenia sekwencji zadań na komputerze**|Przedstawia stan każdego kroku wdrożenia sekwencji zadań na określonym komputerze docelowym. Jeśli żadne rekordy nie zostaną zwrócone, sekwencja zadań nie została uruchomiona na komputerze.|  
|**Lista komputerów które został przekroczony czas uruchamiania wdrożenia sekwencji zadań**|Przedstawia listę komputerów, dla których czas uruchamiania sekwencji zadań jest dłuższy niż określona wartość.|  
|**Czas wykonywania dla określonego wdrożenia sekwencji zadań na określonym komputerze docelowym**|Przedstawia całkowity czas pomyślnego wykonywania określonej sekwencji zadań na określonym komputerze.|  
|**Uruchom czasu dla każdego kroku wdrożenia sekwencji zadań na określonym komputerze docelowym**|Przedstawia czas wykonywania każdego kroku określonego wdrożenia sekwencji zadań na określonym komputerze docelowym.|  
|**Stan określonego wdrożenia sekwencji zadań dla określonego komputera**|Przedstawia podsumowanie stanu określonego wdrożenia sekwencji zadań na określonym komputerze.|  
|**Stan wdrożenia sekwencji zadań na nieznanym komputerze docelowym**|Przedstawia stan określonego wdrożenia sekwencji zadań na określonym nieznanym komputerze docelowym.|  
|**Podsumowanie stanu określonego wdrożenia sekwencji zadań**|Przedstawia podsumowanie stanu wszystkich zasobów przeznaczonych do użycia we wdrożeniu.|  
|**Podsumowanie stanu określonego wdrożenia sekwencji zadań dostępne dla nieznanych komputerów**|Przedstawia podsumowanie stanu wszystkich zasobów przeznaczonych do użycia w określonym wdrożeniu dostępnym dla kolekcji zawierającej nieznane komputery.|  

### <a name="task-sequence---deployments"></a>Sekwencja zadań — wdrożenia  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Wszystkie zasoby systemowe obecnie w określonej grupie lub fazie określonego wdrożenia sekwencji zadań**|Przedstawia listę komputerów, które obecnie działają w ramach określonej grupy lub fazy określonego wdrożenia sekwencji zadań.|  
|**Wszystkie zasoby systemowe, których wdrożenie sekwencji zadań w określonej grupie lub fazie zakończyło się niepowodzeniem**|Przedstawia listę komputerów, na których wystąpiły błędy w ramach określonej grupy lub fazy określonego wdrożenia sekwencji zadań.|  
|**Wszystkie wdrożenia sekwencji zadań**|Przedstawia szczegóły wszystkich wdrożeń sekwencji zadań inicjowanych w bieżącej lokacji.|  
|**Wszystkie wdrożenia sekwencji zadań dostępne dla nieznanych komputerów**|Przedstawia szczegóły wszystkich wdrożeń sekwencji zadań inicjowanych z lokacji, które zostały wdrożone w kolekcjach zawierających nieznane komputery.|  
|**Liczba niepowodzeń w każdej fazie lub grupie określonej sekwencji zadań**|Przedstawia liczbę błędów w każdej fazie lub grupie określonej sekwencji zadań.|  
|**Liczba niepowodzeń w każdej fazie lub grupie określonego wdrożenia sekwencji zadań**|Przedstawia liczbę błędów w każdej fazie lub grupie określonego wdrożenia sekwencji zadań.|  
|**Stan wdrożenia wszystkich wdrożeń sekwencji zadań**|Przedstawia ogólny postęp wszystkich wdrożeń sekwencji zadań.|  
|**Postęp wykonywanej sekwencji zadań**|Przedstawia postęp określonej sekwencji zadań.|  
|**Postęp wykonywanego wdrożenia sekwencji zadań**|Przedstawia podsumowanie informacji na temat określonego wdrożenia sekwencji zadań.|  
|**Postęp wszystkich wdrożeń dla określonej sekwencji zadań**|Przedstawia postęp wszystkich wdrożeń określonej sekwencji zadań.|  
|**Raport podsumowania wdrożenia sekwencji zadań**|Przedstawia podsumowanie informacji na temat określonego wdrożenia sekwencji zadań.|  

### <a name="task-sequence---progress"></a>Sekwencja zadań — postęp  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Wykres - tygodniowy postęp sekwencji zadań**|Przedstawia tygodniowy postęp sekwencji zadań od daty wdrożenia.|  
|**Postęp sekwencji zadań**|Przedstawia postęp określonej sekwencji zadań.|  
|**Postęp wszystkich sekwencji zadań**|Przedstawia podsumowanie postępu wszystkich sekwencji zadań.|  
|**Postęp sekwencji zadań wdrożeń systemu operacyjnego**|Przedstawia postęp wszystkich sekwencji zadań powodujących wdrażanie systemów operacyjnych.|  
|**Stan wszystkich nieznanych komputerów**|Przedstawia listę komputerów, które były nieznane podczas uruchamiania na nich wdrożenia sekwencji zadań, oraz informacje wskazujące, czy komputery są teraz znane.|  

### <a name="task-sequences---references"></a>Sekwencje zadań — odwołania  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Zawartość z odwołaniami określonej sekwencji zadań**|Przedstawia zawartość, do której odwołuje się sekwencja zadań.|  

### <a name="upgrade-assessment"></a>Ocena uaktualnienia  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Stan aplikacji dla określonego komputera**|Przedstawia zgodność aplikacji zainstalowanych na komputerze dla określonego systemu operacyjnego.|  
|**Status aplikacji dla komputerów w określonej kolekcji**|Przedstawia stan ogólny dla komputerów w kolekcji, co pozwala na ich ocenę pod względem uaktualniania do określonego systemu operacyjnego w oparciu o aplikacje na każdym komputerze. Ten raport służy do określania, które komputery mają zgodne aplikacje przed wdrożeniem systemu operacyjnego.|  
|**Podsumowanie stanu aplikacji**|Przedstawia podsumowanie stanu aplikacji dla określonego systemu operacyjnego. Ten raport służy do określania zgodności aplikacji przed wdrożeniem systemu operacyjnego.|  
|**Komputery z zainstalowaną określoną aplikacją**|Przedstawia komputery z zainstalowaną określoną aplikacją.|  
|**Komputery z określonym urządzeniem**|Przedstawia komputery z określonym urządzeniem sprzętowym.|  
|**Stan urządzenia sprzętowego dla określonego komputera**|Przedstawia stan zgodności urządzeń sprzętowych, które znajdują się na określonym komputerze, dla określonego systemu operacyjnego.|  
|**Stan urządzenia sprzętowego dla komputerów w określonej kolekcji**|Przedstawia stan ogólny urządzeń sprzętowych dla określonego systemu operacyjnego dla komputerów w określonej kolekcji. Ten raport służy do określania zgodności sprzętu przed wdrożeniem systemu operacyjnego.|  
|**Podsumowanie stanu urządzeń sprzętowych**|Przedstawia podsumowanie stanu urządzeń sprzętowych dla określonego systemu operacyjnego. Ten raport służy do określania zgodności urządzeń sprzętowych przed wdrożeniem systemu operacyjnego.|  
|**Wymagania sprzętowe systemu operacyjnego**|Przedstawia minimalne i zalecane kryteria dotyczące sprzętu dla systemów operacyjnych.|  
|**Status wymagań systemu operacyjnego dla komputerów w określonej kolekcji**|Przedstawia stan wymagań systemu operacyjnego dla określonego systemu operacyjnego dla komputerów w określonej kolekcji. Ten raport służy do określania, czy komputer spełnia określone wymagania systemu operacyjnego dotyczące szybkości procesora CPU, rozmiaru pamięci i miejsca na dysku twardym.|  
|**Podsumowanie oceny uaktualnienia**|Przedstawia podsumowanie oceny uaktualnienia. Ten raport służy do oceniania ogólnego stanu na potrzeby zgodności uaktualniania.|  

### <a name="user---device-affinity"></a>Użytkownik — koligacja urządzenia  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Powiązania koligacji urządzeń użytkownika oczekujące według kolekcji**|Przedstawia wszystkie oczekujące przypisania koligacji urządzenia użytkownika w oparciu o dane użycia dla elementów członkowskich kolekcji.|  
|**Powiązania koligacji urządzeń użytkownika na kolekcję**|Przedstawia wszystkie skojarzenia urządzenia użytkownika dla określonej kolekcji, a następnie grupuje wyniki według typu kolekcji (np. użytkownik lub urządzenie).|  

### <a name="user-data-and-profiles-health"></a>Kondycja profili i danych użytkownika  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Raport kondycji przekierowania folderów — szczegóły**|Przedstawia szczegóły stanu kondycji przekierowania folderu dla każdego z przekierowanych folderów dla danego użytkownika.|  
|**Mobilnego raport o kondycji profilu użytkownika — szczegóły**|Przedstawia szczegóły stanu kondycji profilu użytkownika mobilnego dla określonego użytkownika.|  
|**Raport dane użytkownika i kondycja profilów - szczegóły**|Przedstawia szczegóły błędu lub ostrzeżenia dotyczącego przekierowania folderu lub profilu użytkownika mobilnego po przejściu do szczegółów liczby z raportu podsumowania.|  
|**Dane użytkownika raport i kondycja profilów - podsumowanie**|Przedstawia podsumowanie stanów kondycji przekierowania folderu i profili użytkowników mobilnych.|  

### <a name="users"></a>Użytkownicy  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Komputery z określoną nazwą użytkownika**|Przedstawia listę komputerów, które były używane przez określonego użytkownika.|  
|**Liczba użytkowników według domeny**|Przedstawia liczbę użytkowników w każdej domenie.|  
|**Użytkownicy w określonej domenie**|Przedstawia listę użytkowników i ich komputerów w określonej domenie.|  

### <a name="virtual-applications"></a>Aplikacje wirtualne  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Wyniki środowiska wirtualnego App-V**|Przedstawia informacje o określonym środowisku wirtualnym, które znajduje się w określonym stanie względem wybranej kolekcji.|  
|**Wyniki środowiska wirtualnego App-V dla zasobu**|Przedstawia informacje o określonym środowisku wirtualnym przy określonym zasobie i dowolnym typie wdrożenia tego środowiska.|  
|**Status środowiska wirtualnego App-V**|Przedstawia informacje na temat zgodności określonego środowiska wirtualnego z określoną kolekcją.|  
|**Komputery z określoną aplikacją wirtualną**|Przedstawia podsumowanie komputerów z określonym skrótem aplikacji App-V utworzonym przy użyciu aplikacji Application Virtualization Management Sequencer.|  
|**Komputery z określonym pakietem aplikacji wirtualnych**|Przedstawia listę komputerów z określonym pakietem aplikacji App-V.|  
|**Liczba wszystkich wystąpień pakietów aplikacji wirtualnych**|Przedstawia liczbę wykrytych pakietów aplikacji App-V.|  
|**Liczba wszystkich wystąpień aplikacji wirtualnych**|Przedstawia liczbę wykrytych aplikacji App-V.|  

### <a name="wake-on-lan"></a>Wake On LAN  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Wszystkie komputery ustawione na aktywność funkcji Wake On LAN**|Przedstawia listę komputerów przeznaczonych do użycia na potrzeby działania Wake On LAN podczas wdrażania określonego typu.|  
|**Wszystkie obiekty oczekujące na wznowienie**|Przedstawia obiekty zaplanowane do wznowienia.|  
|**Wszystkie lokacje z włączoną funkcją Wake On LAN**|Przedstawia listę wszystkich lokacji w hierarchii, które zostały włączone dla działania Wake On LAN.|  
|**Błędy otrzymane podczas wysyłania pakietów wznowienia w określonym przedziale czasu**|Przedstawia błędy odebrane podczas wysyłania pakietów do komputerów w zdefiniowanym okresie.|  
|**Historia aktywności funkcji Wake On LAN**|Przedstawia historię działania wznawiania w danym okresie.|  
|**Szczegóły stanu wdrażania serwera Proxy wznawiania**|Przedstawia informacje na temat stanu wdrożenia serwera proxy wznawiania dla każdego urządzenia w określonej kolekcji.|  
|**Podsumowanie stanu wdrażania serwera Proxy wznawiania**|Przedstawia podsumowanie stanu wdrożenia serwera proxy wznawiania w określonej kolekcji.|  
