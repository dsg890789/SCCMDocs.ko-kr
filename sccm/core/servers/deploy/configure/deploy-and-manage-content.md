---
title: "Wdróż zawartość | Dokumentacja firmy Microsoft"
description: "Po zainstalowaniu punktów dystrybucji programu System Center Configuration Manager, Oto jak można rozpocząć wdrażania zawartości."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d50dcca0-4419-449d-a487-73abcadf328f
caps.latest.revision: "6"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 36b08285ef78d0acb9ba9c44abe2d57e311d44b3
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="deploy-and-manage-content-for-system-center-configuration-manager"></a>Wdrażanie i zarządzanie zawartością programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Po zainstalowaniu punktów dystrybucji programu System Center Configuration Manager, można rozpocząć wdrażania zawartości. Zazwyczaj zawartości przesyła do punktów dystrybucji w sieci, ale istnieje inne opcje, aby pobrać zawartość do punktów dystrybucji. Po przesyła zawartość do punktu dystrybucji, można zaktualizować, ponownie rozesłać, usuwanie i sprawdź poprawność tej zawartości w punktach dystrybucji.  

##  <a name="bkmk_distribute"></a>Dystrybucja zawartości  
 Zazwyczaj dystrybucji zawartości do punktów dystrybucji, aby była ona dostępna na komputerach klienckich. (Wyjątkiem jest użycie opcji dystrybucji zawartości na żądanie dla określonego wdrożenia).  Podczas dystrybucji zawartości program Configuration Manager przechowuje pliki zawartości w pakiecie, a następnie dystrybuuje pakiet do punktu dystrybucji. Typy zawartości, którą można dystrybuować:  

-   Typy wdrożenia aplikacji  

-   Pakiety  

-   Pakiety wdrożeniowe  

-   Pakiety sterowników  

-   Obrazy systemu operacyjnego  

-   Instalatorzy systemu operacyjnego  

-   Obrazy rozruchowe  

-   Sekwencje zadań  

Podczas tworzenia pakietu zawierającego pliki źródłowe, takiego jak wdrożenie typu lub wdrożenia pakietu aplikacji, witryna, w której zostaje utworzony pakiet staje się właścicielem lokacji dla źródła zawartości pakietu. Menedżer konfiguracji kopiuje pliki źródłowe ze ścieżki plików źródłowych określonej dla obiektu do biblioteki zawartości na serwerze lokacji, który jest właścicielem źródła zawartości pakietu.  Następnie w programie Configuration Manager replikuje informacje do dodatkowych lokacji. (Zobacz [biblioteki zawartości](../../../../core/plan-design/hierarchy/the-content-library.md) Aby uzyskać więcej informacji na ten temat.)  

Użyj poniższej procedury do dystrybucji zawartości do punktów dystrybucji.  

#### <a name="to-distribute-content-on-distribution-points"></a>Aby przeprowadzić dystrybucję zawartości w punktach dystrybucji  

1.  W konsoli programu Configuration Manager kliknij przycisk **Biblioteka oprogramowania**.  

2.  W **Biblioteka oprogramowania** obszaru roboczego, wybierz jedną z następujących kroków dla typu zawartości, którą chcesz dystrybuować:  

    -   **Aplikacje**: Rozwiń węzeł **Zarządzanie aplikacjami** > **aplikacji**, a następnie wybierz aplikacje, które chcesz dystrybuować.  

    -   **Pakiety**: Rozwiń węzeł **Zarządzanie aplikacjami** >  **pakiety**, a następnie wybierz pakiety, które chcesz dystrybuować.  

    -   **Pakiety wdrożeniowe**: Rozwiń węzeł **aktualizacji oprogramowania** >  **pakiety wdrożeniowe**, a następnie wybierz pakiety wdrożeniowe, które chcesz dystrybuować.  

    -   **Pakiety sterowników**: Rozwiń węzeł **systemów operacyjnych** >  **pakiety sterowników**, a następnie wybierz pakiety sterowników, które chcesz dystrybuować.  

    -   **Obrazy systemu operacyjnego**: Rozwiń węzeł **systemów operacyjnych** >  **obrazów systemu operacyjnego**, a następnie wybierz obrazy systemu operacyjnego, które chcesz dystrybuować.  

    -   **Instalatorzy systemu operacyjnego**: Rozwiń węzeł **systemów operacyjnych** > **instalatorzy systemu operacyjnego**, a następnie wybierz instalatorów systemu operacyjnego, które chcesz dystrybuować.  

    -   **Obrazy rozruchowe**: Rozwiń węzeł **systemów operacyjnych** >  **obrazów rozruchowych**, a następnie wybierz obrazy rozruchowe, które chcesz dystrybuować.  

    -   **Sekwencje zadań**: Rozwiń węzeł **systemów operacyjnych** >  **sekwencje zadań**, a następnie wybierz sekwencję, którą chcesz rozesłać. Mimo że sekwencje zadań nie zawierają zawartości, mają jednak powiązane zależności zawartości, które są dystrybuowane.  

        > [!NOTE]  
        >  Jeśli zmodyfikujesz sekwencji zadań, należy ponownie rozesłać zawartość.  

3.  Na karcie **Narzędzia główne** w grupie **Wdrażanie** kliknij przycisk **Dystrybuuj zawartość**. Otwiera kreatora dystrybucji zawartości.  

4.  Na **ogólne** , sprawdź, że wymieniona zawartość jest zawartością, którą chcesz rozesłać, wybierz, czy program Configuration Manager, aby wykrywać zależności zawartości skojarzone z wybraną zawartością oraz Dodaj zależności do dystrybucji, a następnie kliknij przycisk **dalej**.  

    > [!NOTE]  
    >  Istnieje możliwość skonfigurowania **Wykryj powiązane zależności zawartości i dodaj je do tej dystrybucji** ustawienie tylko dla typu zawartości aplikacji. Menedżer konfiguracji automatycznie skonfiguruje to ustawienie dla sekwencji zadań, a nie może być modyfikowany.  

5.  Na **zawartości** karcie, jeśli wyświetlana, sprawdź, czy wymieniona zawartość jest zawartością, którą chcesz rozesłać, a następnie kliknij przycisk **dalej**.  

    > [!NOTE]  
    >  **Zawartości** tylko wtedy, gdy zostanie wyświetlona strona **Wykryj powiązane zależności zawartości i dodaj je do tej dystrybucji** jest wybrane ustawienie **ogólne** stronie kreatora.  

6.  Na **miejsce docelowe zawartości** kliknij przycisk **Dodaj**, wybierz jedną z następujących czynności, a następnie wykonaj odpowiednie czynności:  

    -   **Kolekcje**: Wybierz **kolekcje użytkowników** lub **kolekcje urządzeń**, kliknij kolekcję skojarzoną z co najmniej jednej grupy punktów dystrybucji, a następnie kliknij przycisk **OK**.  

        > [!NOTE]  
        >  Są wyświetlane tylko kolekcje, które są skojarzone z grupą punktów dystrybucji. Aby uzyskać więcej informacji o kojarzeniu kolekcji z grupami punktów dystrybucji, zobacz [Zarządzanie grupami punktów dystrybucji](../../../../core/servers/deploy/configure/install-and-configure-distribution-points.md#bkmk_manage) w [zainstalować i skonfigurować punkty dystrybucji programu System Center Configuration Manager](../../../../core/servers/deploy/configure/install-and-configure-distribution-points.md) tematu.  

    -   **Punkt dystrybucji**: Wybierz istniejący punkt dystrybucji, a następnie kliknij przycisk **OK**. Punkty dystrybucji, które wcześniej odebrały zawartość nie są wyświetlane.  

    -   **Grupy punktów dystrybucji**: Wybierz istniejącą grupę punktów dystrybucji, a następnie kliknij przycisk **OK**. Grupy punktów dystrybucji, które wcześniej odebrały zawartość nie są wyświetlane.  

    Po zakończeniu dodawania miejsc docelowych zawartości kliknij **dalej**.  

7.  Na **Podsumowanie** strony, przed kontynuowaniem sprawdź ustawienia dystrybucji. Aby przeprowadzić dystrybucję zawartości do wybranych miejsc docelowych, kliknij przycisk **dalej**.  

8.  **Postępu** strony wyświetlany postęp dystrybucji.  

9. **Potwierdzenie** zostanie wyświetlona strona, czy zawartość została pomyślnie przypisana do punktów. Do monitorowania dystrybucji zawartości, zobacz [monitorowania zawartości ma dystrybuowane z System Center Configuration Manager](../../../../core/servers/deploy/configure/monitor-content-you-have-distributed.md).  

##  <a name="bkmk_prestage"></a>Użyj wstępnie przygotowanej zawartości  
 Można wstępnie przygotować pliki zawartości aplikacji i typów pakietów:  

-   W konsoli programu Configuration Manager, należy wybrać wymaganą zawartość, a następnie użyć **Tworzenie kreatora przygotowanego pliku zawartości** można utworzyć skompresowany, wstępnie przygotowany plik zawartości obejmujący pliki oraz skojarzone metadane wybranej zawartości.  

-   Następnie można ręcznie zaimportować zawartość na serwerze lokacji, lokacji dodatkowej lub punktu dystrybucji.  

-   Podczas importowania wstępnie przygotowanego pliku zawartości na serwerze lokacji pliki zawartości są dodawane do biblioteki zawartości na serwerze lokacji, a następnie rejestrowane w bazie danych serwera lokacji.  

-   Podczas importowania wstępnie przygotowanego pliku zawartości w punkcie dystrybucji pliki zawartości są dodawane do biblioteki zawartości w punkcie dystrybucji, a komunikat o stanie są wysyłane do serwera lokacji, które informują witryny, czy zawartość jest dostępna w punkcie dystrybucji.  

**Ograniczenia i zagadnienia dotyczące wstępnie przygotowanej zawartości:**  

-   **Gdy punkt dystrybucji jest zlokalizowany na serwerze lokacji**, nie należy włączać punktu dystrybucji dla wstępnie przygotowanej zawartości. Zamiast tego należy użyć procedury w programie [jak wstępnie przygotować zawartość w punkcie dystrybucji na serwerze lokacji](#bkmk_dpsiteserver).  

-   **Gdy punkt dystrybucji jest skonfigurowany jako punkt dystrybucji ściągania**, nie należy włączać punktu dystrybucji dla wstępnie przygotowanej zawartości. Konfiguracja wstępnie przygotowanej zawartości dla punktu dystrybucji zastępuje konfigurację punktu dystrybucji ściągania. Ściągający punkt dystrybucji skonfigurowany do obsługi wstępnie przygotowanej zawartości nie ściąga zawartości ze źródłowego punktu dystrybucji i nie będzie otrzymywać zawartości z serwera lokacji.  

-   **Biblioteka zawartości należy utworzyć w punkcie dystrybucji przed można wstępnie przygotować zawartość w punkcie dystrybucji**. Dystrybucja zawartości za pośrednictwem sieci, co najmniej jeden raz przed wstępnym przygotowaniem zawartości do punktu dystrybucji.  

-   **Podczas wstępnego przygotowywania zawartości dla pakietu o długiej ścieżce źródła pakietu** (na przykład ponad 140 znaków) Narzędzie wiersza polecenia Extract Content może zakończyć się niepowodzeniem pomyślnie wyodrębnić zawartości tego pakietu do biblioteki zawartości.  

Aby uzyskać informacje o tym, kiedy należy wstępnie przygotować pliki zawartości, zobacz *wstępnie przygotowanej zawartości* w [zarządzanie przepustowością sieci związane z zarządzaniem zawartością](/sccm/core/plan-design/hierarchy/manage-network-bandwidth) tematu.  

Użyj poniższych sekcji, aby wstępnie przygotować zawartość.  

###  <a name="BKMK_CreatePrestagedContentFile"></a>Krok 1. Tworzenie wstępnie przygotowanego pliku zawartości  
 Można utworzyć skompresowany, wstępnie przygotowany plik zawartości obejmujący pliki oraz skojarzone metadane zawartości wybrane w konsoli programu Configuration Manager. Poniższa procedura umożliwia utworzenie wstępnie przygotowanego pliku zawartości.  

##### <a name="to-create-a-prestaged-content-file"></a>Aby utworzyć wstępnie przygotowany plik zawartości  

1.  W konsoli programu Configuration Manager kliknij przycisk **Biblioteka oprogramowania**.  

2.  W **Biblioteka oprogramowania** obszaru roboczego, wybierz jedną z następujących kroków dla typu zawartości, którą chcesz wstępnie przygotować:  

    -   **Aplikacje**: Rozwiń węzeł **Zarządzanie aplikacjami**, kliknij przycisk **aplikacji**, a następnie wybierz aplikacje, które chcesz wstępnie przygotować.  

    -   **Pakiety**: Rozwiń węzeł **Zarządzanie aplikacjami**, kliknij przycisk **pakiety**, a następnie wybierz pakiety, które chcesz wstępnie przygotować.  

    -   **Pakiety sterowników**: Rozwiń węzeł **systemów operacyjnych**, kliknij przycisk **pakiety sterowników**, a następnie wybierz pakiety sterowników, które chcesz wstępnie przygotować.  

    -   **Obrazy systemu operacyjnego**: Rozwiń węzeł **systemów operacyjnych**, kliknij przycisk **obrazów systemu operacyjnego**, a następnie wybierz obrazy systemu operacyjnego, które chcesz wstępnie przygotować.  

    -   **Instalatorzy systemu operacyjnego**: Rozwiń węzeł **systemów operacyjnych**, kliknij przycisk **instalatorzy systemu operacyjnego**, a następnie wybierz instalatorów systemu operacyjnego, które chcesz wstępnie przygotować.  

    -   **Obrazy rozruchowe**: Rozwiń węzeł **systemów operacyjnych**, kliknij przycisk **obrazów rozruchowych**, a następnie wybierz obrazy rozruchowe, które chcesz wstępnie przygotować.  

    -   **Sekwencje zadań**: Rozwiń węzeł **systemów operacyjnych**, kliknij przycisk **sekwencje zadań**, a następnie wybierz sekwencję, którą chcesz wstępnie przygotować.  

3.  Na **Home** karcie **wdrożenia** kliknij przycisk **Utwórz wstępnie przygotowany plik zawartości**. Otwiera kreatora tworzenia przygotowanego zawartości pliku.  

    > [!NOTE]  
    >  **W przypadku aplikacji:** Na **Home** karcie **aplikacji** kliknij przycisk **Utwórz wstępnie przygotowany plik zawartości**.  
    >   
    >  **W przypadku pakietów:** Na **Home** karcie &lt; *PackageName*> kliknij przycisk **Utwórz wstępnie przygotowany plik zawartości**.  

4.  Na **ogólne** kliknij przycisk **Przeglądaj**, wybierz lokalizację wstępnie przygotowanego pliku zawartości, określ nazwę pliku, a następnie kliknij **zapisać**. Wstępnie przygotowanego pliku zawartości na serwerach lokacji głównej, serwerach lokacji dodatkowych lub punktów dystrybucji służy do importowania zawartości i metadanych.  

5.  W przypadku aplikacji wybierz **Eksportuj wszystkie zależności** aby program Configuration Manager wykrył i dodał zależności powiązane z aplikacją do wstępnie przygotowanego pliku zawartości. Domyślnie to ustawienie jest włączone.  

6.  W **komentarze administratora**wprowadź opcjonalne komentarze dotyczące wstępnie przygotowanego pliku zawartości, a następnie kliknij przycisk **dalej**.  

7.  Na **zawartości** upewnij się, że wymieniona zawartość jest zawartością, który chcesz dodać do wstępnie przygotowanego pliku zawartości, a następnie kliknij przycisk **dalej**.  

8.  Na **lokalizacje zawartości** określ punkty dystrybucji, z których mają zostać pobrane pliki zawartości dla wstępnie przygotowanego pliku zawartości. Można wybrać więcej niż jeden punkt dystrybucji do pobrania zawartości. Punkty dystrybucji są wymienione w sekcji lokalizacje zawartości. **Zawartości** kolumny Wyświetla, ile wybranych pakietów lub aplikacje są dostępne w każdym punkcie dystrybucji. Configuration Manager rozpoczyna się od pierwszego punktu dystrybucji na liście, można pobrać wybranej zawartości, a następnie przejdzie do kolejnych pozycji z listy w celu pobrania pozostałej zawartości wymaganej przez wstępnie przygotowany plik zawartości. Kliknij przycisk **Przenieś w górę** lub **Przenieś w dół** Aby zmienić kolejność priorytetów punktów dystrybucji. W przypadku punktów dystrybucji na liście nie zawierają całej wybranej zawartości, należy dodać punkty dystrybucji do listy z zawartością lub zamknąć kreatora, rozesłać zawartość do co najmniej jednego punktu dystrybucji i uruchom ponownie kreatora.  

9. Na **Podsumowanie** Potwierdź szczegóły. Możesz wrócić do poprzedniej strony i wprowadzić zmiany. Kliknij przycisk **dalej** utworzyć wstępnie przygotowany plik zawartości.  

10. **Postępu** zostanie wyświetlona zawartość dodawana do wstępnie przygotowanego pliku zawartości.  

11. Na **zakończenia** , sprawdź, czy wstępnie przygotowany plik zawartości został pomyślnie utworzony, a następnie kliknij przycisk **Zamknij**.  

###  <a name="BKMK_AssignContentToDistributionPoint"></a>Krok 2. Przypisz zawartość do punktów dystrybucji  
 Po utworzeniu wstępnie przygotowanego pliku zawartości, należy przypisać zawartość do punktów dystrybucji.  

> [!NOTE]  
>  Gdy Użyj wstępnie przygotowanego pliku zawartości, aby odzyskać bibliotekę zawartości na serwerze lokacji i nie trzeba wstępnie przygotować pliki zawartości w punkcie dystrybucji, możesz pominąć tę procedurę.  

 Użyj poniższej procedury, aby przypisać zawartość we wstępnie przygotowanego pliku zawartości do punktów dystrybucji.  

> [!IMPORTANT]  
>  Sprawdź, czy punkty dystrybucji, które mają zostać wstępnie przygotowane, są skonfigurowane jako wstępnie przygotowanych punktów dystrybucji lub czy zawartość jest dystrybuowana do punktów dystrybucji za pośrednictwem sieci.  

##### <a name="to-assign-the-content-to-distribution-points"></a>Aby przypisać zawartość do punktów dystrybucji  

1.  W konsoli programu Configuration Manager kliknij przycisk **Biblioteka oprogramowania**.  

2.  W **Biblioteka oprogramowania** obszaru roboczego, wybierz jedną z następujących kroków dla typu zawartości wybranej podczas tworzenia wstępnie przygotowanego pliku zawartości:  

    -   **Aplikacje**: Rozwiń węzeł **Zarządzanie aplikacjami**, kliknij przycisk **aplikacji**, a następnie wybierz wstępnie przygotowane aplikacje.  

    -   **Pakiety**: Rozwiń węzeł **Zarządzanie aplikacjami**, kliknij przycisk **pakiety**, a następnie wybierz wstępnie przygotowane pakiety.  

    -   **Pakiety wdrożeniowe**: Rozwiń węzeł **aktualizacji oprogramowania**, kliknij przycisk **pakiety wdrożeniowe**, a następnie wybierz wstępnie przygotowane pakiety wdrożeniowe.  

    -   **Pakiety sterowników**: Rozwiń węzeł **systemów operacyjnych**, kliknij przycisk **pakiety sterowników**, a następnie wybierz wstępnie przygotowane pakiety sterowników.  

    -   **Obrazy systemu operacyjnego**: Rozwiń węzeł **systemów operacyjnych**, kliknij przycisk **obrazów systemu operacyjnego**, a następnie wybierz wstępnie przygotowane obrazy systemu operacyjnego.  

    -   **Instalatorzy systemu operacyjnego**: Rozwiń węzeł **systemów operacyjnych**, kliknij przycisk **instalatorzy systemu operacyjnego**, a następnie wybierz instalatorów systemu operacyjnego, wstępnie przygotowane.  

    -   **Obrazy rozruchowe**: Rozwiń węzeł **systemów operacyjnych**, kliknij przycisk **obrazów rozruchowych**, a następnie wybierz wstępnie przygotowane obrazy rozruchowe.  

3.  Na karcie **Narzędzia główne** w grupie **Wdrażanie** kliknij przycisk **Dystrybuuj zawartość**. Otwiera kreatora dystrybucji zawartości.  

4.  Na **ogólne** , sprawdź, że wymieniona zawartość jest zawartością, którą wstępnie, wybierz, czy program Configuration Manager, aby wykrywać zależności zawartości skojarzone z wybraną zawartością oraz Dodaj zależności do dystrybucji, a następnie kliknij przycisk **dalej**.  

    > [!NOTE]  
    >  Istnieje możliwość skonfigurowania **Wykryj powiązane zależności zawartości i dodaj je do tej dystrybucji** ustawienie tylko dla typu zawartości aplikacji. Menedżer konfiguracji automatycznie skonfiguruje to ustawienie dla sekwencji zadań, a nie może być modyfikowany.  

5.  Na **zawartości** strony, jeśli wyświetlana, sprawdź, czy wymieniona zawartość jest zawartością, którą chcesz rozesłać, a następnie kliknij przycisk **dalej**.  

    > [!NOTE]  
    >  **Zawartości** tylko wtedy, gdy zostanie wyświetlona strona **Wykryj powiązane zależności zawartości i dodaj je do tej dystrybucji** jest wybrane ustawienie **ogólne** stronie kreatora.  

6.  Na **miejsce docelowe zawartości** kliknij przycisk **Dodaj**, wybierz jedną z poniższych opcji obejmujących punkty dystrybucji przeznaczone do wstępnego przygotowania, a następnie przejdź do następnego kroku:  

    -   **Kolekcje**: Wybierz **kolekcje użytkowników** lub **kolekcje urządzeń**, kliknij kolekcję skojarzoną z co najmniej jednej grupy punktów dystrybucji, a następnie kliknij przycisk **OK**.  

        > [!NOTE]  
        >  Są wyświetlane tylko kolekcje, które są skojarzone z grupą punktów dystrybucji.  Aby uzyskać więcej informacji, zobacz [Zarządzanie grupami punktów dystrybucji](../../../../core/servers/deploy/configure/install-and-configure-distribution-points.md#bkmk_manage) w [zainstalować i skonfigurować punkty dystrybucji programu System Center Configuration Manager](../../../../core/servers/deploy/configure/install-and-configure-distribution-points.md) tematu.  

    -   **Punkt dystrybucji**: Wybierz istniejący punkt dystrybucji, a następnie kliknij przycisk **OK**. Punkty dystrybucji, które wcześniej odebrały zawartość nie są wyświetlane.  

    -   **Grupy punktów dystrybucji**: Wybierz istniejącą grupę punktów dystrybucji, a następnie kliknij przycisk **OK**. Grupy punktów dystrybucji, które wcześniej odebrały zawartość nie są wyświetlane.  

    Po zakończeniu dodawania miejsc docelowych zawartości kliknij **dalej**.  

7.  Na **Podsumowanie** strony, przed kontynuowaniem sprawdź ustawienia dystrybucji. Aby przeprowadzić dystrybucję zawartości do wybranych miejsc docelowych, kliknij przycisk **dalej**.  

8.  **Postępu** strony wyświetlany postęp dystrybucji.  

9. **Potwierdzenie** zostanie wyświetlona strona, czy zawartość została pomyślnie przypisana do punktów dystrybucji. Do monitorowania dystrybucji zawartości, zobacz [monitorowania zawartości ma dystrybuowane z System Center Configuration Manager](../../../../core/servers/deploy/configure/monitor-content-you-have-distributed.md).  

###  <a name="BKMK_ExportContentFromPrestagedContentFile"></a>Krok 3. Wyodrębnienie zawartości ze wstępnie przygotowanego pliku zawartości  
 Po utworzeniu wstępnie przygotowanego pliku zawartości i przypisaniu zawartości do punktów dystrybucji, można wyodrębnić pliki zawartości do biblioteki zawartości w lokacji serwera lub punktu dystrybucji. Zazwyczaj kopiowany na dysk przenośny, takich jak dysk USB, wstępnie przygotowany plik zawartości lub zawartość na nośniku, na przykład dysk DVD jest nagrywana i jest dostępny w lokalizacji lokacji serwera lub punktu dystrybucji wymagającego zawartości.  

 Aby ręcznie wyodrębnić pliki zawartości ze wstępnie przygotowanego pliku zawartości za pomocą narzędzia wiersza polecenia Extract Content, należy użyć następującej procedury.  

> [!IMPORTANT]  
>  Po uruchomieniu narzędzia wiersza polecenia Extract Content narzędzie tworzy plik tymczasowy podczas tworzenia wstępnie przygotowanego pliku zawartości. Następnie plik jest kopiowany do folderu docelowego, a plik tymczasowy zostanie usunięty. Musi mieć wystarczające miejsce na dysku na plik tymczasowy lub proces nie powiedzie się. Plik tymczasowy zostanie utworzony w następującej lokalizacji:  
>   
>  -   Plik tymczasowy zostanie utworzony w folderze wskazanym jako folder docelowy wstępnie przygotowanego pliku zawartości.  

> [!IMPORTANT]  
>  Użytkownik uruchamiający narzędzie wiersza polecenia Extract Content musi mieć **administratora** uprawnienia na komputerze, na którym jest wyodrębniana wstępnie przygotowana zawartość.  

##### <a name="to-extract-the-content-files-from-the-prestaged-content-file"></a>Aby wyodrębnić pliki zawartości ze wstępnie przygotowanego pliku zawartości  

1.  Skopiuj wstępnie przygotowany plik zawartości na komputerze, z którym chcesz wyodrębnić zawartość.  

2.  Skopiuj narzędzie wiersza polecenia Extract Content z &lt; *Ścieżka_instalacji_programu_configmgr*> \bin\\&lt;*platformy*> na komputer, z którym chcesz wyodrębnić wstępnie przygotowany plik zawartości.  

3.  Otwórz wiersz polecenia i przejdź do lokalizacji folderu zawierającego wstępnie przygotowany plik zawartości oraz narzędzie Extract Content.  

    > [!NOTE]  
    >  Można wyodrębnić co najmniej jeden wstępnie przygotowany pliki zawartości na serwerze lokacji, serwera lokacji dodatkowej lub punktu dystrybucji.  

4.  Typ **extractcontent/p:**&lt;*Lokalizacjawstępnieprzygotowanegopliku*>**\\**&lt;*Nazwawstępnieprzygotowanegopliku*> **/S** Aby zaimportować pojedynczy plik.  

     Typ **extractcontent/p:**&lt;*Lokalizacjawstępnieprzygotowanegopliku*> **/S** zaimportować wszystkie wstępnie przygotowane pliki we wskazanym folderze.  

     Na przykład wpisz **extractcontent /P:D:\PrestagedFiles\MyPrestagedFile.pkgx /S** gdzie `D:\PrestagedFiles\` to Lokalizacjawstępnieprzygotowanegopliku, `MyPrestagedFile.pkgx` to nazwa wstępnie przygotowanego pliku, i `/S` informuje programu Configuration Manager, by wyodrębnić jedynie pliki zawartości, które są nowsze niż aktualnie w punkcie dystrybucji.  

     Podczas wyodrębniania wstępnie przygotowanego pliku zawartości na serwerze lokacji pliki zawartości są dodawane do biblioteki zawartości na serwerze lokacji, a następnie dostępność zawartości zostanie zarejestrowana w bazie danych serwera lokacji. Podczas eksportowania wstępnie przygotowanego pliku zawartości w punkcie dystrybucji pliki zawartości są dodawane do biblioteki zawartości w punkcie dystrybucji, punkt dystrybucji wyśle komunikat o stanie do nadrzędnego serwera lokacji podstawowej, a następnie dostępność zawartości zostanie zarejestrowana w bazie danych lokacji.  

    > [!IMPORTANT]  
    >  W poniższym scenariuszu należy zaktualizować zawartość wyodrębnioną ze wstępnie przygotowanego pliku zawartości, gdy zawartość jest aktualizowana do nowej wersji:  
    >   
    >  1.  Możesz utworzyć wstępnie przygotowany plik zawartości w wersji 1 pakietu.  
    >  2.  Pliki źródłowe pakietu aktualizacji w wersji 2.  
    >  3.  Wyodrębniania wstępnie przygotowanego pliku zawartości (wersja 1 pakietu) w punkcie dystrybucji.  
    >   
    > Menedżer konfiguracji nie przeprowadzi automatycznej dystrybucji pakietu w wersji 2 do punktu dystrybucji. Należy utworzyć nowy wstępnie przygotowanego pliku zawartości, która zawiera nową wersję pliku, a następnie wyodrębnić zawartość, aktualizacji punktu dystrybucji w celu dystrybuowania plików, które uległy zmianie lub ponownie rozesłać wszystkie pliki w pakiecie.  

###  <a name="bkmk_dpsiteserver"></a>Jak wstępnie przygotować zawartość w punkcie dystrybucji na serwerze lokacji  
 Punkt dystrybucji jest zainstalowany na serwerze lokacji, musi użyć poniższej procedury Aby pomyślnie przygotować zawartość. Jest to spowodowane pliki zawartości znajdują się już w bibliotece zawartości.  

 Gdy punkt dystrybucji nie jest włączone dla wstępnie przygotowanej zawartości lub gdy punkt dystrybucji nie znajduje się na serwerze lokacji, zobacz [Użyj wstępnie przygotowanej zawartości](#bkmk_prestage) w tym temacie.  

##### <a name="to-prestage-content-on-distribution-points-located-on-a-site-server"></a>Aby wstępnie przygotować zawartość w punktach dystrybucji znajduje się na serwerze lokacji  

1.  Wykonaj następujące kroki, aby sprawdzić, czy punkt dystrybucji nie jest włączona dla wstępnie przygotowanej zawartości.  

    1.  W konsoli programu Configuration Manager kliknij przycisk **Administracja**.  

    2.  W **administracji** obszaru roboczego kliknij **punktów dystrybucji**, a następnie wybierz punkt dystrybucji, który znajduje się na serwerze lokacji.  

    3.  Na karcie **Narzędzia główne** w grupie **Właściwości** kliknij przycisk **Właściwości**.  

    4.  Na **ogólne** karcie, upewnij się, że **Włącz ten punkt dystrybucji dla wstępnie przygotowanej zawartości** nie zaznaczono pola wyboru.  

2.  Tworzenie wstępnie przygotowanego pliku zawartości przy użyciu [krok 1: Utwórz wstępnie przygotowany plik zawartości](#BKMK_CreatePrestagedContentFile) w tym temacie.  

3.  Przypisz zawartość do punktu dystrybucji przy użyciu [krok 2: Przypisz zawartość do punktów dystrybucji](#BKMK_AssignContentToDistributionPoint) w tym temacie.  

4.  Na serwerze lokacji wyodrębnienie zawartości ze wstępnie przygotowanego pliku zawartości przy użyciu [krok 3: Wyodrębnienie zawartości ze wstępnie przygotowany plik zawartości](#BKMK_ExportContentFromPrestagedContentFile) w tym temacie.  

    > [!NOTE]  
    >  Gdy punkt dystrybucji znajduje się w lokacji pomocniczej, odczekaj przynajmniej 10 minut, a następnie za pomocą konsoli programu Configuration Manager połączonej z nadrzędną lokacją podstawową, przypisz zawartość do punktu dystrybucji w lokacji dodatkowej.  

##  <a name="bkmk_manage"></a>Zarządzanie dystrybuowaną zawartość  
 Masz następujące opcje zarządzania zawartością:  
 - [Aktualizacja zawartości](#update-content)
 - [Ponowna dystrybucja zawartości](#redistribute-content)
 - [Usuwanie zawartości](#remove-content)
 - [Sprawdzanie poprawności zawartości](#validate-content)

### <a name="update-content"></a>Aktualizacja zawartości
Po zaktualizowaniu lokalizacji plików źródłowych do wdrożenia przez dodanie nowych plików lub zastąpienie istniejących plików ich nowszą wersją można zaktualizować pliki zawartości w punktach dystrybucji przy użyciu **Aktualizuj punkty dystrybucji** lub **Aktualizuj zawartość** akcji:  
-   Pliki zawartości są kopiowane ze ścieżki plików źródłowych do biblioteki zawartości w lokacji będącej właścicielem źródła zawartości pakietu  
-   Wersja pakietu jest zwiększany  
-   Każde wystąpienie biblioteki zawartości na serwerach lokacji i w dystrybucji punktów aktualizacji tylko te pliki, które zostały zmienione  

> [!WARNING]  
>  Wersja pakietu aplikacji ma zawsze numer 1. Po zaktualizowaniu zawartości dla typu wdrożenia aplikacji programu Configuration Manager utworzy nowy identyfikator zawartości typu wdrożenia i odwołania do pakietu nowy identyfikator zawartości.  

#### <a name="to-update-content-on-distribution-points"></a>Aby zaktualizować zawartość w punktach dystrybucji  

1.  W konsoli programu Configuration Manager kliknij przycisk **Biblioteka oprogramowania**.  

2.  W **Biblioteka oprogramowania** obszaru roboczego, wybierz jedną z następujących kroków dla typu zawartości, którą chcesz dystrybuować:  

    -   **Aplikacje**: Rozwiń węzeł **Zarządzanie aplikacjami** > **aplikacji**, a następnie wybierz aplikacje, które chcesz dystrybuować. Kliknij przycisk **typy wdrożeń** , a następnie wybierz typ wdrożenia, który chcesz zaktualizować.  

    -   **Pakiety**: Rozwiń węzeł **Zarządzanie aplikacjami** > **pakiety**, a następnie wybierz pakiety, które chcesz zaktualizować.  

    -   **Pakiety wdrożeniowe**: Rozwiń węzeł **aktualizacji oprogramowania** > **pakiety wdrożeniowe**, a następnie wybierz pakiety wdrożeniowe, które chcesz zaktualizować.  

    -   **Pakiety sterowników**: Rozwiń węzeł **systemów operacyjnych** > **pakiety sterowników**, a następnie wybierz pakiety sterowników, które chcesz zaktualizować.  

    -   **Obrazy systemu operacyjnego**: Rozwiń węzeł **systemów operacyjnych** > **obrazów systemu operacyjnego**, a następnie wybierz obrazy systemu operacyjnego, które chcesz zaktualizować.  

    -   **Instalatorzy systemu operacyjnego**: Rozwiń węzeł **systemów operacyjnych** > **instalatorzy systemu operacyjnego**, a następnie wybierz instalatorów systemu operacyjnego, które chcesz zaktualizować.  

    -   **Obrazy rozruchowe**: Rozwiń węzeł **systemów operacyjnych** >  **obrazów rozruchowych**, a następnie wybierz obrazy rozruchowe, które chcesz zaktualizować.  

3.  Na **Home** karcie **wdrożenia** kliknij przycisk **Aktualizuj punkty dystrybucji**, a następnie kliknij przycisk **OK** Aby potwierdzić zamiar aktualizacji zawartości.  

    > [!NOTE]  
    >  Aby zaktualizować zawartość dla aplikacji, kliknij przycisk **typy wdrożeń** , kliknij prawym przyciskiem myszy typ wdrożenia, kliknij pozycję **Aktualizuj zawartość**, a następnie kliknij przycisk **OK** aby potwierdzić zamiar odświeżenia zawartości.  

    > [!NOTE]  
    >  Podczas aktualizowania zawartości obrazów rozruchowych, zostanie otwarty Kreator zarządzania punktem dystrybucji. Przejrzyj informacje na **Podsumowanie** strony, a następnie Ukończ pracę kreatora, aby zaktualizować zawartość.  

### <a name="redistribute-content"></a>Ponowna dystrybucja zawartości
Można ponownie rozesłać pakietu, aby skopiować wszystkie pliki zawartości w pakiecie do punktów dystrybucji lub grupy punktów dystrybucji, a tym samym zastąpić istniejące pliki.  

 Użyj tej operacji do naprawienia plików zawartości w pakiecie lub ponownego wysłania zawartości, jeśli jej wstępne rozesłanie zakończy się niepowodzeniem. Można ponownie rozesłać pakietu za pomocą:  

-   Właściwości pakietu  
-   Właściwości punktu dystrybucji  
-   Właściwości grupy punktów dystrybucji.  


#### <a name="to-redistribute-content-from-package-properties"></a>Aby ponownie rozesłać zawartość przy użyciu właściwości pakietu  

1.  W konsoli programu Configuration Manager kliknij przycisk **Biblioteka oprogramowania**.  

2.  W **Biblioteka oprogramowania** obszaru roboczego, wybierz jedną z następujących kroków dla typu zawartości, którą chcesz dystrybuować:  

    -   **Aplikacje**: Rozwiń węzeł **Zarządzanie aplikacjami** >  **aplikacji**, a następnie wybierz aplikację, którą chcesz ponownie dystrybuować.  

    -   **Pakiety**: Rozwiń węzeł **Zarządzanie aplikacjami** > **pakiety**, a następnie wybierz pakiet, który chcesz ponownie dystrybuować.  

    -   **Pakiety wdrożeniowe**: Rozwiń węzeł **aktualizacji oprogramowania** >  **pakiety wdrożeniowe**, a następnie wybierz pakiet wdrożeniowy, który chcesz ponownie dystrybuować.  

    -   **Pakiety sterowników**: Rozwiń węzeł **systemów operacyjnych** > **pakiety sterowników**, a następnie wybierz pakiet sterowników, który chcesz ponownie dystrybuować.  

    -   **Obrazy systemu operacyjnego**: Rozwiń węzeł **systemów operacyjnych** > **obrazów systemu operacyjnego**, a następnie wybierz obraz systemu operacyjnego, który chcesz ponownie dystrybuować.  

    -   **Instalatorzy systemu operacyjnego**: Rozwiń węzeł **systemów operacyjnych** > **instalatorzy systemu operacyjnego**, a następnie wybierz Instalatora systemu operacyjnego, który chcesz ponownie dystrybuować.  

    -   **Obrazy rozruchowe**: Rozwiń węzeł **systemów operacyjnych** >  **obrazów rozruchowych**, a następnie wybierz obraz rozruchowy, który chcesz ponownie dystrybuować.  

3.  Na karcie **Narzędzia główne** w grupie **Właściwości** kliknij przycisk **Właściwości**.  

4.  Kliknij przycisk **lokalizacje zawartości** , a następnie wybierz punkt dystrybucji lub grupę punktów dystrybucji, w której chcesz ponownie rozesłać zawartość, kliknij przycisk **Ponowna dystrybucja**, a następnie kliknij przycisk **OK**.  

#### <a name="to-redistribute-content-from-distribution-point-properties"></a>Aby ponownie rozesłać zawartość przy użyciu właściwości punktu dystrybucji  

1.  W konsoli programu Configuration Manager kliknij przycisk **Administracja**.  

2.  W **administracji** obszaru roboczego kliknij **punktów dystrybucji**, a następnie wybierz punkt dystrybucji, w którym chcesz wykonać ponowną dystrybucję zawartości.  

3.  Na karcie **Narzędzia główne** w grupie **Właściwości** kliknij przycisk **Właściwości**.  

4.  Kliknij przycisk **zawartości** , a następnie wybierz zawartość do ponownego rozesłania, kliknij przycisk **Ponowna dystrybucja**, a następnie kliknij przycisk **OK**.  

#### <a name="to-redistribute-content-from-distribution-point-group-properties"></a>Aby ponownie rozesłać zawartość przy użyciu właściwości grupy punktów dystrybucji  

1.  W konsoli programu Configuration Manager kliknij przycisk **Administracja**.  

2.  W **administracji** obszaru roboczego, kliknij przycisk **grupy punktów dystrybucji**, a następnie wybierz grupę punktów dystrybucji, w którym chcesz wykonać ponowną dystrybucję zawartości.  

3.  Na karcie **Narzędzia główne** w grupie **Właściwości** kliknij przycisk **Właściwości**.  

4.  Kliknij przycisk **zawartości** , a następnie wybierz zawartość do ponownego rozesłania, kliknij przycisk **Ponowna dystrybucja**, a następnie kliknij przycisk **OK**.  

    > [!IMPORTANT]  
    >  Zawartość pakietu zostanie rozesłana ponownie do wszystkich punktów dystrybucji w grupie punktów dystrybucji.  


#### <a name="use-the-sdk-to-force-replication-of-content"></a>Używanie zestawu SDK, aby wymusić replikację zawartości
Można użyć **RetryContentReplication** metody klasy Instrumentacji zarządzania Windows (WMI) z usługi SDK programu Configuration Manager, aby wymusić Menedżera dystrybucji, aby skopiować zawartość z lokalizacji źródłowej do biblioteki zawartości.  

Tylko wymusić replikację, gdy po wystąpiły problemy dotyczące normalnej replikacji zawartości (zazwyczaj potwierdzona przy użyciu węzła monitorowania konsoli) należy ponownie rozesłać zawartość przy użyciu tej metody.   

Aby uzyskać więcej informacji o tej opcji zestawu SDK, zobacz [RetryContentReplication metody w klasie SMS_CM_UpdatePackages](https://msdn.microsoft.com/library/mt762092(CMSDK.16).aspx) w witrynie MSDN. Microsoft.com.

### <a name="remove-content"></a>Usuwanie zawartości
Jeśli nie jest już wymagany zawartości w punktach dystrybucji, można usunąć pliki zawartości w punkcie dystrybucji.  

-   Właściwości pakietu  
-   Właściwości punktu dystrybucji  
-   Właściwości grupy punktów dystrybucji.  

Jednakże gdy zawartość jest powiązana z innym pakietem rozesłanym do tego samego punktu dystrybucji, nie można usunąć zawartość.  

#### <a name="to-remove-package-content-files-from-distribution-points"></a>Aby usunąć pliki zawartości pakietu z punktów dystrybucji  

1.  W konsoli programu Configuration Manager kliknij przycisk **Biblioteka oprogramowania**.  

2.  W **Biblioteka oprogramowania** obszaru roboczego, wybierz jedną z następujących kroków dla typu zawartości, którą chcesz usunąć:  

    -   **Aplikacje**: Rozwiń węzeł **Zarządzanie aplikacjami** > **aplikacji**, a następnie wybierz aplikację, którą chcesz usunąć.  

    -   **Pakiety**: Rozwiń węzeł **Zarządzanie aplikacjami** > **pakiety**, a następnie wybierz pakiet, który chcesz usunąć.  

    -   **Pakiety wdrożeniowe**: Rozwiń węzeł **aktualizacji oprogramowania** > **pakiety wdrożeniowe**, a następnie wybierz pakiet wdrożeniowy, który chcesz usunąć.  

    -   **Pakiety sterowników**: Rozwiń węzeł **systemów operacyjnych** > **pakiety sterowników**, a następnie wybierz pakiet sterowników, który chcesz usunąć.  

    -   **Obrazy systemu operacyjnego**: Rozwiń węzeł **systemów operacyjnych** > **obrazów systemu operacyjnego**, a następnie wybierz obraz systemu operacyjnego, który chcesz usunąć.  

    -   **Instalatorzy systemu operacyjnego**: Rozwiń węzeł **systemów operacyjnych** > **instalatorzy systemu operacyjnego**, a następnie wybierz Instalatora systemu operacyjnego, który chcesz usunąć.  

    -   **Obrazy rozruchowe**: Rozwiń węzeł **systemów operacyjnych** > **obrazów rozruchowych**, a następnie wybierz obraz rozruchowy, który chcesz usunąć.  

3.  Na karcie **Narzędzia główne** w grupie **Właściwości** kliknij przycisk **Właściwości**.  

4.  Kliknij przycisk **lokalizacje zawartości** , a następnie wybierz punkt dystrybucji lub grupę punktów dystrybucji, z którego chcesz usunąć zawartość, kliknij przycisk **Usuń**, a następnie kliknij przycisk **OK**.  

#### <a name="to-remove-package-content-from-distribution-point-properties"></a>Aby usunąć zawartość pakietu przy użyciu właściwości punktu dystrybucji  

1.  W konsoli programu Configuration Manager kliknij przycisk **Administracja**.  

2.  W **administracji** obszaru roboczego kliknij **punktów dystrybucji**, a następnie wybierz punkt dystrybucji, w której chcesz usunąć zawartość.  

3.  Na karcie **Narzędzia główne** w grupie **Właściwości** kliknij przycisk **Właściwości**.  

4.  Kliknij przycisk **zawartości** , a następnie wybierz zawartość do usunięcia, kliknij przycisk **Usuń**, a następnie kliknij przycisk **OK**.  

#### <a name="to-remove-content-from-distribution-point-group-properties"></a>Aby usunąć zawartość z właściwości grupy punktów dystrybucji  

1.  W konsoli programu Configuration Manager kliknij przycisk **Administracja**.  

2.  W **administracji** obszaru roboczego kliknij **grupy punktów dystrybucji**, a następnie wybierz grupę punktów dystrybucji, w której chcesz usunąć zawartość.  

3.  Na karcie **Narzędzia główne** w grupie **Właściwości** kliknij przycisk **Właściwości**.  

4.  Kliknij przycisk **zawartości** , a następnie wybierz zawartość do usunięcia, kliknij przycisk **Usuń**, a następnie kliknij przycisk **OK**.  


### <a name="validate-content"></a>Sprawdzanie poprawności zawartości
Proces weryfikacji zawartości sprawdza integralność plików zawartości w punktach dystrybucji. Można włączyć weryfikację zawartości zgodnie z harmonogramem lub można ręcznie zainicjować weryfikację zawartości przy użyciu właściwości punktów dystrybucji i pakietów.  

 Po rozpoczęciu procesu weryfikacji zawartości, programu Configuration Manager sprawdzi pliki zawartości w punktach dystrybucji, a jeśli skrót pliku okaże się niespodziewany w odniesieniu do plików w punkcie dystrybucji, programu Configuration Manager utworzy komunikat o stanie, który można sprawdzić w **monitorowanie** obszaru roboczego.  

 Aby uzyskać więcej informacji o konfigurowaniu harmonogramu weryfikacji zawartości, zobacz [konfiguracje punktów dystrybucji](../../../../core/servers/deploy/configure/install-and-configure-distribution-points.md#bkmk_configs) w [zainstalować i skonfigurować punkty dystrybucji programu System Center Configuration Manager](../../../../core/servers/deploy/configure/install-and-configure-distribution-points.md) tematu.  


#### <a name="to-initiate-content-validation-for-all-content-on-a-distribution-point"></a>Aby zainicjować weryfikację zawartości dla całej zawartości w punkcie dystrybucji  

1.  W konsoli programu Configuration Manager kliknij przycisk **Administracja**.  

2.  W **administracji** obszaru roboczego kliknij **punktów dystrybucji**, a następnie wybierz punkt dystrybucji, w którym chcesz zweryfikować zawartość.  

3.  Na karcie **Narzędzia główne** w grupie **Właściwości** kliknij przycisk **Właściwości**.  

4.  Na **zawartości** , a następnie wybierz pakiet, w którym chcesz zweryfikować zawartość, kliknij przycisk **weryfikacji**, kliknij przycisk **OK**, a następnie kliknij przycisk **OK**. Inicjuje procesu weryfikacji zawartości pakietu w punkcie dystrybucji.  

5.  Aby wyświetlić wyniki procesu weryfikacji zawartości w **monitorowanie** obszaru roboczego, rozwiń węzeł **stan dystrybucji**i kliknij przycisk **stan zawartości** węzła. Jest wyświetlana zawartość poszczególnych typów pakietu (na przykład aplikacja, pakiet aktualizacji oprogramowania i obraz rozruchowy). Aby uzyskać więcej informacji o monitorowaniu stanu zawartości, zobacz [monitorowania zawartości ma dystrybuowane z System Center Configuration Manager](../../../../core/servers/deploy/configure/monitor-content-you-have-distributed.md).  

#### <a name="to-initiate-content-validation-for-a-package"></a>Aby zainicjować weryfikację zawartości pakietu  

1.  W konsoli programu Configuration Manager kliknij przycisk **Biblioteka oprogramowania**.  

2.  W **Biblioteka oprogramowania** obszaru roboczego, wybierz jedną z następujących kroków dla typu zawartości, którą chcesz zweryfikować:  

    -   **Aplikacje**: Rozwiń węzeł **Zarządzanie aplikacjami** > **aplikacji**, a następnie wybierz aplikację, którą chcesz zweryfikować.  

    -   **Pakiety**: Rozwiń węzeł **Zarządzanie aplikacjami** > **pakiety**, a następnie wybierz pakiet, który chcesz zweryfikować.  

    -   **Pakiety wdrożeniowe**: Rozwiń węzeł **aktualizacji oprogramowania** > **pakiety wdrożeniowe**, a następnie wybierz pakiet wdrożeniowy, który chcesz zweryfikować.  

    -   **Pakiety sterowników**: Rozwiń węzeł **systemów operacyjnych** > **pakiety sterowników**, a następnie wybierz pakiet sterowników, który chcesz zweryfikować.  

    -   **Obrazy systemu operacyjnego**: Rozwiń węzeł **systemów operacyjnych** > **obrazów systemu operacyjnego**, a następnie wybierz obraz systemu operacyjnego, który chcesz zweryfikować.  

    -   **Instalatorzy systemu operacyjnego**: Rozwiń węzeł **systemów operacyjnych** >  **instalatorzy systemu operacyjnego**, a następnie wybierz Instalatora systemu operacyjnego, który chcesz zweryfikować.  

    -   **Obrazy rozruchowe**: Rozwiń węzeł **systemów operacyjnych** > **obrazów rozruchowych**, a następnie wybierz obraz rozruchowy, który chcesz wstępnie przygotować.  

3.  Na karcie **Narzędzia główne** w grupie **Właściwości** kliknij przycisk **Właściwości**.  

4.  Na **lokalizacje zawartości** , a następnie wybierz punkt dystrybucji lub grupę punktów dystrybucji, w których chcesz zweryfikować zawartość, kliknij przycisk **weryfikacji**, kliknij przycisk **OK**, a następnie kliknij przycisk **OK**. Uruchamia proces weryfikacji zawartości zawartości na wybranym punkcie dystrybucji lub grupę punktów dystrybucji.  

5.  Aby wyświetlić wyniki procesu weryfikacji zawartości w **monitorowanie** obszaru roboczego, rozwiń węzeł **stan dystrybucji**i kliknij przycisk **stan zawartości** węzła. Jest wyświetlana zawartość poszczególnych typów pakietu (na przykład aplikacja, pakiet aktualizacji oprogramowania i obraz rozruchowy). Aby uzyskać więcej informacji o monitorowaniu stanu zawartości, zobacz [monitorowania zawartości ma dystrybuowane z System Center Configuration Manager](../../../../core/servers/deploy/configure/monitor-content-you-have-distributed.md).  
