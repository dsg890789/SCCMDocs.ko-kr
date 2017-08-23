---
title: Pakiety i programy | Dokumentacja firmy Microsoft
description: "Obsługują wdrożeń, które używają pakiety i programy lub aplikacje z System Center Configuration Manager."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: caad0507-9913-415a-b13d-d36f8f0a1b80
caps.latest.revision: "8"
caps.handback.revision: "0"
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.openlocfilehash: 6146bcf4e5aa9df6fe0b8cf71898e488ecf217cc
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="packages-and-programs-in-system-center-configuration-manager"></a>Pakiety i programy w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

System Center Configuration Manager nadal obsługuje pakiety i programy, które były używane w programie Configuration Manager 2007. Wdrożenie korzystające z pakietów i programów może być odpowiedniejsze od wdrożenia korzystającego z aplikacji, gdy wdraża się poniższe elementy:  

- Aplikacje na serwerach Linux i UNIX
- Skrypty nieinstalujące aplikacji na komputerze, na przykład skrypt defragmentacji dysku komputera.
- „Jednorazowe” skrypty, które nie muszą być stale monitorowane.  
- Skrypty uruchamiane zgodnie z cyklicznym harmonogramem, które nie mogą korzystać z globalnej ewaluacji.

W trakcie migracji pakietów z wcześniejszej wersji programu Configuration Manager, można je wdrożyć w hierarchii programu Configuration Manager. Po zakończeniu migracji pakiety są widoczne w węźle **Pakiety** w obszarze roboczym **Biblioteka oprogramowania**.

Można modyfikować i wdrażać te pakiety w taki sam sposób jak w przypadku przy użyciu funkcji dystrybucji oprogramowania. **Importuj pakiet w Kreatorze definicji** pozostaje w programie Configuration Manager można importować pakiety ze starszych wersji. Anonse są konwertowane na wdrożenia podczas migracji z programu Configuration Manager 2007 do hierarchii programu Configuration Manager.  

> [!NOTE]  
>  Microsoft System Center Configuration Manager Package Conversion Manager można użyć w celu skonwertowania pakietów i programów do aplikacji programu Configuration Manager.  
>   
>  Aby uzyskać więcej informacji, zobacz [Configuration Manager Package Conversion Manager](https://technet.microsoft.com/library/hh531519.aspx).  

Pakiety mogą korzystać z niektórych nowych funkcji programu Configuration Manager, w tym grup punktów dystrybucji i monitorowania. Aplikacje Microsoft Application Virtualization (App-V) nie mogą być dystrybuowane za pomocą pakietów i programów w programie Configuration Manager. Aby dystrybuować aplikacje wirtualne, należy utworzyć je jako aplikacje programu Configuration Manager.  

##  <a name="create-a-package-and-program"></a>Tworzenie pakietów i programów  
 Użyj jednej z tych procedur ułatwiających tworzenie lub importowaniu pakietów i programów.  

### <a name="create-a-package-and-program-using-the-create-package-and-program-wizard"></a>Tworzenie pakietu i programu za pomocą Kreatora tworzenia pakietu i programu.  

1.  W konsoli programu Configuration Manager wybierz **Biblioteka oprogramowania** > **Zarządzanie aplikacjami** > **pakiety**.  

3.  W **Home** karcie **Utwórz** grupy, wybierz **tworzenia pakietu**.  

4.  Na **pakietu** strony **Kreatora tworzenia pakietu i programu**, podaj następujące informacje:  

    -   **Nazwa**: Określ nazwę pakietu składającą się z maksymalnie 50 znaków.  

    -   **Opis elementu**: Określ opis dla tego pakietu składającą się z maksymalnie 128 znaków.  

    -   **Producent** (opcjonalnie): Podaj nazwę producenta, która pomoże identyfikować pakiet w konsoli programu Configuration Manager. Ta nazwa może się składać z maksymalnie 32 znaków.

    -   **Język** (opcjonalnie): Podaj wersję językową pakietu, maksymalnie 32 znaki.  

    -   **Wersja** (opcjonalnie):  Określ numer wersji pakietu, maksymalnie 32 znaki.

    -   **Ten pakiet zawiera pliki źródłowe**: To ustawienie wskazuje, czy pakiet wymaga plików źródłowych znajdować się na urządzeniach klienckich. Domyślnie to pole wyboru jest wyczyszczone, a Menedżer konfiguracji nie używa punktów dystrybucji dla pakietu. Gdy to pole wyboru jest zaznaczone, punkty dystrybucji są używane.  

    -   **Folder źródłowy**: Jeśli pakiet zawiera pliki źródłowe, wybierz **Przeglądaj** otworzyć **Ustawianie folderu źródłowego** okna dialogowego, a następnie określ lokalizację plików źródłowych pakietu.  

        > [!NOTE]  
        >  Konto komputera serwera lokacji musi mieć uprawnienia dostępu Odczyt we wskazanym folderze źródłowym.  

5.  Na **typu programu** strony **Kreatora tworzenia pakietu i programu**, wybierz typ programu do tworzenia, a następnie wybierz pozycję **dalej**. Można utworzyć program dla komputera lub urządzenia albo pominąć ten krok i utworzyć program później.  

    > [!TIP]  
    >  Aby utworzyć nowy program dla istniejącego pakietu, należy najpierw wybrać pakiet. Następnie w **Home** karcie **pakietu** grupy, wybierz **Utwórz Program** otworzyć **Kreatora tworzenia programu**.  

6.  Użyj jednej z następujących procedur, aby utworzyć program standardowy lub program urządzenia.  

    #### <a name="create-a-standard-program"></a>Utworzyć program standardowy  

  1.  Na **typu programu** strony **Kreatora tworzenia pakietu i programu**, wybierz **Program standardowy**, a następnie wybierz pozycję **dalej**.     

    2.  Na **Program standardowy** Podaj następujące informacje:  

        -   **Nazwa:** Określ nazwę programu składającą się z maksymalnie 50 znaków.  

            > [!NOTE]  
            >  Nazwa programu musi być unikatowa w ramach pakietu. Po utworzeniu programu nie można zmodyfikować jego nazwy.  

        -   **Wiersz polecenia**: Wprowadź wiersz polecenia, można użyć do uruchamiania tego programu lub wybierz **Przeglądaj** aby przejść do lokalizacji pliku.  

            Jeśli nazwa pliku nie ma określonego rozszerzenia, programu Configuration Manager próbuje użyć .com, .exe i .bat jako możliwych rozszerzeń.  

             Gdy program jest uruchamiany na kliencie, programu Configuration Manager najpierw szuka nazwy pliku wiersza polecenia w pakiecie szuka go w lokalnym folderze systemu Windows i przeszukuje lokalną *% path %*. Jeśli pliku nie uda się znaleźć, działanie programu zakończy się niepowodzeniem.  

        -   **Folder początkowy** (opcjonalnie): Określ folder, w którym program będzie uruchamiany, maksymalnie 127 znaków. Ten folder może być ścieżką bezwzględną na kliencie lub ścieżką względną wobec folderu punktu dystrybucji zawierającego pakiet.

        -   **Uruchom**: Określ tryb, w którym program będzie uruchamiany na komputerach klienckich. Wybierz jedną z poniższych opcji:  

            -   **Normalny**: Program jest uruchamiany w trybie normalnym na podstawie ustawień domyślnych systemu i programu. Jest to tryb domyślny.  

            -   **Zminimalizowany**: Program będzie uruchamiany w trybie zminimalizowanym na urządzeniach klienckich. Użytkownicy będą widzieć działanie instalacji w obszarze powiadomień lub na pasku zadań.  

            -   **Zmaksymalizowane**: Program będzie uruchamiany w trybie zmaksymalizowanym na urządzeniach klienckich. Użytkownicy widzą wszystkie działania instalacyjne.  

            -   **Ukryte**: Program będzie uruchamiany ukryte na urządzeniach klienckich. Użytkownicy nie widzieć żadnego działania instalacyjnego.  

        -   **Program można uruchomić**: Określ, czy program ma być uruchamiany tylko wtedy, gdy użytkownik jest zalogowany, tylko wtedy, gdy żaden użytkownik nie jest podpisany w lub niezależnie od tego, czy użytkownik jest zalogowany na komputerze klienckim.  

        -   **Tryb uruchamiania**: Określ, czy program ma być uruchamiany z uprawnieniami administracyjnymi czy uprawnieniami użytkownika, który jest aktualnie zalogowany.  

        -   **Zezwalaj użytkownikom na wyświetlanie i interakcji z instalacją programu**: Użyj tego ustawienia, jeśli jest dostępne określić, czy zezwalać użytkownikom na interakcję z instalacją programu. To pole wyboru jest dostępne tylko wtedy, gdy **tylko wtedy, gdy użytkownik nie jest zalogowany** lub **czy użytkownik jest zalogowany** został wybrany do **Program można uruchomić** i kiedy **Uruchom z prawami administracyjnymi** został wybrany do **tryb uruchamiania**.  

        -   **Tryb dysku**: Określ informacje o sposobie ten program jest uruchamiany w sieci. Wybierz jedną z następujących opcji:  

            -   **Jest uruchamiany z nazwą UNC**: Określ, czy program ma być uruchamiany z nazwą Universal Naming Convention (UNC). To jest ustawienie domyślne.  

            -   **Wymaga litery dysku**: Określ, czy program wymaga litery dysku do pełnej kwalifikacji jego lokalizacji. Dla tego ustawienia programu Configuration Manager można używać dowolnej litery dysku na kliencie.  

            -   **Wymaga określonej litery dysku** : Określ, czy program wymaga określonej litery dysku określanej przez użytkownika do pełnej kwalifikacji jego lokalizacji (na przykład **Z:**). Jeśli określona litera dysku będzie już używana na kliencie, program nie zostanie uruchomiony.  

        -   **Ponowne łączenie się z punktem dystrybucji po zalogowaniu w**: Użyj tego pola wyboru wskazująca, czy komputer kliencki z punktem dystrybucji po zalogowaniu użytkownika. To pole wyboru jest domyślnie wyczyszczone.  

  3.  Na **wymagania** strony **Kreatora programu, tworzenia pakietu i** Podaj następujące informacje:  

        -   **Uruchom najpierw inny program**: Użyj tego ustawienia można identyfikować pakiet i program, który jest uruchamiany przed uruchomieniem tego pakietu i programu.  

        -   **Wymagania dotyczące platformy**: Wybierz **ten program można uruchomić na dowolnej platformie** lub **ten program można uruchomić tylko na określonych platformach**, a następnie wybierz systemy operacyjne, które muszą być uruchomione klientów, aby można było zainstalować pakiet i program.  

        -   **Szacowane miejsce na dysku**: Określ ilość miejsca na dysku, który program wymaga, aby uruchomić na komputerze. Dla tego ustawienia można wybrać opcję **Unknown** (ustawienie domyślne) lub ustawić liczbę całkowitą nie mniejszą od zera. Jeśli zostanie podana wartość, należy wskazać dla niej jednostkę.  

        -   **Maksymalny dozwolony czas wykonywania (w minutach)**: Określ maksymalny czas, który program powinien być wykonywany na komputerze klienckim. Dla tego ustawienia można wybrać opcję **Unknown** (ustawienie domyślne) lub ustawić liczbę całkowitą większą od zera.  

             Wartością domyślną jest 120 minut.  

            > [!IMPORTANT]  
            >  Jeśli używasz okna obsługi dla kolekcji, na którym działa ten program, może wystąpić konflikt, jeśli **maksymalny dozwolony czas wykonywania** jest większa od czasu zaplanowanego okna obsługi. Jednak jeśli maksymalny czas wykonywania jest ustawiony na **nieznany**, program zaczyna być uruchamiana podczas okna obsługi i kontynuuje uruchamianie w razie potrzeby po zamknięciu okna obsługi. Jeżeli użytkownik ustawi maksymalnego czasu działania do określonego okresu, który przekracza długość dowolnej z dostępnych okien obsługi, program nie działa.  

             Jeśli wartość jest równa **nieznany**, programu Configuration Manager Ustawia maksymalny dozwolony czas wykonywania na 12 godzin (720 minut).  

            > [!NOTE]  
            >  Jeśli zostanie przekroczona maksymalna dozwolonego czasu wykonywania (ustawionego przez użytkownika lub jako wartość domyślna), programu Configuration Manager zatrzymuje program, jeśli **Uruchom z prawami administracyjnymi** jest zaznaczone i **Zezwalaj użytkownikom na wyświetlanie i interakcji z instalacją programu** nie jest zaznaczone.  

  4.  Wybierz **dalej**.  

    #### <a name="create-a-device-program"></a>Utworzyć program urządzenia  

  1.  Na **typu programu** strony **Kreatora tworzenia pakietu i programu**, wybierz pozycję **Program dla urządzenia**, a następnie wybierz pozycję **dalej**.  

  2.  Na **Program dla urządzenia** strony, podaj następujące informacje:  

        -   **Nazwa**: Określ nazwę programu składającą się z maksymalnie 50 znaków.  

            > [!NOTE]  
            >  Nazwa programu musi być unikatowa w ramach pakietu. Po utworzeniu programu nie można zmodyfikować jego nazwy.  

        -   **Komentarz** (opcjonalnie): Podaj komentarz dla tego programu urządzenia składający się z maksymalnie 127 znaków.  

        -   **Folder pobierania**: Określ nazwę folderu na urządzeniu z systemem Windows CE, w którym będą przechowywane pliki źródłowe pakietu. Wartość domyślna to **\Temp\\\**.  

        -   **Wiersz polecenia**: Wprowadź wiersz polecenia, można użyć do uruchamiania tego programu lub wybierz **Przeglądaj** aby przejść do lokalizacji pliku.  

        -   **Uruchom wiersz polecenia w folderze pobierania**: Wybierz tę opcję, aby uruchomić program z wcześniej wskazanego folderu pobierania.  

        -   **Uruchom wiersz polecenia z tego folderu**: Wybierz tę opcję, aby określić inny folder, z którego ma zostać uruchomiony program.  

    3.  Na **wymagania** strony, podaj następujące informacje:  

        -   **Szacowane miejsce na dysku**: Określ ilość miejsca na dysku wymaganego oprogramowania. Jest on wyświetlany użytkownikom urządzeń przenośnych przed zainstalowaniem programu.  

        -   **Pobierz program**: Podaj informacje na temat kiedy ten program może być pobierany na urządzenia przenośne. Do wyboru są następujące opcje: **Jak najszybciej**, **Tylko przez szybką sieć** i **Tylko gdy urządzenie jest zadokowane**.  

        -   **Dodatkowe wymagania**: Określ wszelkie dodatkowe wymagania dotyczące tego programu. Są one wyświetlane użytkownikom przed zainstalowaniem oprogramowania. Na przykład można powiadamiać użytkowników, że przed uruchomieniem tego programu trzeba zamknąć wszystkie inne aplikacje.  

  4.  Wybierz **dalej**.  

  7.  Na **Podsumowanie** Przejrzyj akcje, które zostaną wykonane, a następnie Zakończ pracę kreatora.  

 Sprawdź, czy nowy pakiet i program są wyświetlane w **pakiety** węzła **Biblioteka oprogramowania** obszaru roboczego.  

## <a name="create-a-package-and-program-from-a-package-definition-file"></a>Tworzenie pakietu i programu na podstawie pliku definicji pakietu  

1.  W konsoli programu Configuration Manager wybierz **Biblioteka oprogramowania** > **Zarządzanie aplikacjami** > **pakiety**.  

3.  Na **Home** karcie **Utwórz** grupy, wybierz **Utwórz pakiet z definicji**.  

4.  Na **definicja pakietu** strony **Utwórz pakiet w Kreatorze definicji**, wybierz istniejący plik definicji pakietu lub **Przeglądaj** aby otworzyć nowy plik definicji pakietu. Po określeniu nowego pliku definicji pakietu wybierz go z **definicja pakietu** listy, a następnie wybierz pozycję **dalej**.  

5.  Na **pliki źródłowe** strony, podaj informacje o wszelkich wymaganych plikach źródłowych dla pakietu i programu, a następnie wybierz **dalej**.  

6.  Jeśli pakiet wymaga plików źródłowych na **Folder źródłowy** Określ lokalizację, z którego pliki źródłowe mają można uzyskać, a następnie wybierz pozycję **dalej**.  

7.  Na **Podsumowanie** Przejrzyj akcje, które zostaną wykonane, a następnie Zakończ pracę kreatora. Nowy pakiet i program są wyświetlane w **pakiety** węzła **Biblioteka oprogramowania** obszaru roboczego.  

 Aby uzyskać więcej informacji na temat plików definicji pakietu, zobacz [o formacie pliku definicji pakietu](/sccm/apps/deploy-use/packages-and-programs#about-the-package-definition-file-format) w tym temacie.  

##  <a name="deploy-packages-and-programs"></a>Wdrażanie pakietów i programów  

1.  W konsoli programu Configuration Manager wybierz **Biblioteka oprogramowania** > **Zarządzanie aplikacjami** > **pakiety**.  

2.  Wybierz pakiet, który chcesz wdrożyć, a następnie w **Home** karcie **wdrożenia** grupy, wybierz **Wdróż**.  

3.  Na **ogólne** strony **Kreatora wdrażania oprogramowania**, określ nazwę pakietu i programu, można wdrożyć, do której chcesz wdrożyć pakiet i program oraz opcjonalne komentarze dotyczące wdrażania kolekcji.  

     Wybierz opcję **Użyj domyślnych grup punktów dystrybucji powiązanych z tą kolekcją**, jeśli chcesz umieścić zawartość pakietu w domyślnej grupie punktów dystrybucji kolekcji. Jeśli wybrana Kolekcja nie została skojarzona z grupą punktów dystrybucji, ta opcja jest niedostępna.  

4.  Na **zawartości** wybierz pozycję **Dodaj**, a następnie wybierz punkty dystrybucji lub grupy punktów dystrybucji, do których chcesz wdrożyć zawartość, która jest skojarzona z tym pakietem i programem.  

5.  Na **ustawienia wdrażania** strony, wybierz cel wdrożenia i określ opcje dla pakietów wznawiania i połączeń taryfowych:  

    -   **Cel**: Wybierz spośród opcji:  

        -   **Dostępne**: Jeśli aplikacja jest wdrażana dla użytkownika, użytkownik będzie widział opublikowany pakiet i program w wykazie aplikacji i może zainstalować ją na żądanie. Jeśli pakiet i program są wdrażane na urządzeniu, użytkownik będzie ją widział w Centrum oprogramowania i zainstalować ją na żądanie.  

        -   **Wymagane**: Pakiet i program są wdrażane automatycznie zgodnie ze skonfigurowanym harmonogramem. Użytkownik może jednak śledzić stan wdrożenia pakietu i programu oraz zainstalować je przed upływem ostatecznego terminu przy użyciu Centrum oprogramowania.  

    -   **Wyślij pakiety wznawiania**: Jeśli dla celu wdrożenia wybrano opcję **wymagane** i ta opcja jest zaznaczona, jest wysłany pakiet wznawiania do komputerów, przed zainstalowaniem wdrożenia do wznawiania w ostatecznym terminie instalacji. Aby użyć tej opcji, należy skonfigurować komputery do używania funkcji Wake On LAN.  

    -  **Zezwalaj klientom mierzonego połączenia internetowego na pobieranie zawartości po upływie ostatecznego terminu instalacji, co może pociągnąć za sobą dodatkowe koszty**: Zaznacz tę opcję, jeśli są wymagane.  

    > [!NOTE]  
    >  Opcja **Wykonaj wstępne wdrożenie oprogramowania na główne urządzenie użytkownika** nie jest dostępna podczas wdrażania pakietów i programów.  

6.  Na **Planowanie** strony, skonfiguruj, kiedy ten pakiet i program zostaną wdrożone lub udostępnione na urządzeniach klienckich.  

     Opcje na tej stronie będą się różnić w zależności od tego, czy ustawiono akcję wdrożenia **dostępne** lub **wymagane**.  

7.  Jeśli dla celu wdrożenia wybrano opcję **wymagane**, skonfiguruj zachowanie ponownego uruchamiania dla programu **zachowanie ponownego uruchamiania** menu rozwijanego. Wybierz jedną z następujących opcji:  

    |Zachowanie ponownego uruchamiania|Więcej informacji|  
    |--------------------|----------------------|  
    |Nigdy nie uruchamiaj ponownie wdrożonego programu|Program nie będzie można ponownie uruchomić na komputerze klienckim, nawet jeśli program zakończyło się niepowodzeniem lub zostały zmienione pliki programu.|  
    |Zawsze uruchamiaj ponownie program|Program będzie zawsze uruchamiana ponownie na kliencie, gdy wdrożenie jest zaplanowane, nawet jeśli program został już uruchomiony pomyślnie. Może to być przydatne w przypadku używania wdrożeń cyklicznych, w ramach których program jest aktualizowany, na przykład o oprogramowanie antywirusowe.|  
    |Uruchom ponownie, jeśli poprzednia próba nie powiodła się|Program jest uruchamiany ponownie, gdy wdrożenie jest zaplanowane tylko wtedy, gdy nie powiodła się poprzednia próba uruchomienia.|  
    |Uruchom ponownie, jeśli poprzednia próba powiodła się|Program jest uruchomiony ponownie tylko wtedy, gdy wcześniej został uruchomiony pomyślnie na kliencie. To ustawienie jest przydatne w przypadku używania cyklicznych anonsów, w których program jest cyklicznie aktualizowany, gdy każda aktualizacja wymaga pomyślnego zainstalowania poprzedniej aktualizacji.|  

8. Na stronie **Środowisko użytkownika** określ następujące informacje:  

    -   **Zezwalaj użytkownikom na uruchamianie programu niezależnie od przypisań**: Jeśli opcja jest włączona, użytkownicy mogą instalować to oprogramowanie z Centrum oprogramowania niezależnie od wszelkich zaplanowanych czasów instalacji.  

    -   **Instalacja oprogramowania**: Umożliwia zainstalowanie poza skonfigurowanymi oknami obsługi oprogramowania.  

    -   **Ponowne uruchomienie systemu (Jeśli wymagane w celu ukończenia instalacji)**: Jeśli instalacji oprogramowania wymagane jest ponowne uruchomienie urządzenia, aby zakończyć, Zezwalaj na to poza skonfigurowanymi oknami obsługi.  

    -   **Urządzenia osadzone**: Podczas wdrażania pakietów i programów na urządzeniach Windows Embedded, które mają włączoną filtru zapisu, można określić, że pakiety i programy zostanie zainstalowany na tymczasowej nakładce oraz zatwierdzić zmiany później. Alternatywnie możesz zatwierdzić zmiany, w ostatecznym terminie instalacji bądź w oknie konserwacji. Po zatwierdzeniu zmian w ostatecznym terminie instalacji bądź w oknie obsługi, wymagane jest ponowne uruchomienie i trwale zapisać zmiany na urządzeniu.  

        > [!NOTE]  
        >  Po wdrożeniu pakietu lub programu na urządzeniu z systemem Windows Embedded upewnij się, że urządzenie należy do kolekcji ze skonfigurowanym oknem obsługi. Aby uzyskać więcej informacji o sposobie oknach obsługi używanych podczas wdrażania pakietów i programów na urządzeniach Windows Embedded, zobacz [aplikacji tworzenia systemu Windows Embedded](../../apps/get-started/creating-windows-embedded-applications.md).  

9. Na stronie **Punkty dystrybucji** określ następujące informacje:  

    -   **Opcje wdrażania**: Określ akcje, które klient powinien wykonać, aby uruchomić zawartość programu. Można określić zachowanie klienta znajdującego się w granicach szybkiej sieci lub wolnej bądź zawodnej sieci.  

    -   **Zezwalaj klientom na współużytkowanie zawartości z innymi klientami w tej samej podsieci**: Wybierz tę opcję, aby zmniejszyć obciążenie sieci, zezwalając klientom na pobieranie zawartości z innymi klientami w sieci, na których już pobrana zawartość w pamięci podręcznej. Ta opcja korzysta z usługi Windows BranchCache i jest dostępna na komputerach z systemem operacyjnym Windows Vista SP2 lub nowszym.  

    -   **Zezwalaj klientom na użycie rezerwowej lokalizacji źródła zawartości**:  

        -  **W wersji wcześniejszej niż 1610**: Możesz wybrać **Zezwalaj na rezerwową lokalizację źródła zawartości pola wyboru** aby umożliwić klientom spoza granic grupy, aby wrócić i skorzystać z dystrybucji punktów jako lokalizacji źródłowej zawartości podczas preferowane punkty dystrybucji nie są dostępne.

        - **Wersja 1610 i nowsze**: Nie można skonfigurować **Zezwalaj na rezerwową lokalizację źródła zawartości**.  Zamiast tego należy skonfigurować relacje między grupami granic, które określania, kiedy klient można rozpocząć wyszukiwanie grup dodatkowe granic dla lokalizacji poprawne źródło zawartości.

10. Na **Podsumowanie** Przejrzyj akcje, które zostaną wykonane, a następnie Zakończ pracę kreatora.  

     Wdrożenia można obejrzeć w węźle **Wdrożenia** obszaru roboczego **Monitorowanie** i w okienku szczegółów na karcie wdrożenia pakietu po wybraniu wdrożenia. Aby uzyskać więcej informacji, zobacz [monitorować pakiety i programy](/sccm/apps/deploy-use/packages-and-programs#monitor-packages-and-programs) w tym temacie.  

> [!IMPORTANT]  
>  Jeśli została skonfigurowana opcja **Uruchom program z punktu dystrybucji** na **punktów dystrybucji** strony **Kreatora wdrażania oprogramowania**, nie czyść zaznaczenia opcji **skopiuj zawartość tego pakietu do udziału pakietu w punktach dystrybucji** , ponieważ umożliwia to uruchamianie pakietu z punktów dystrybucji.  

##  <a name="monitor-packages-and-programs"></a>Monitor pakiety i programy  
 Aby monitorować wdrożenia pakietów i programów, należy użyć tych samych procedur, które służą do monitorowania aplikacji zgodnie z opisem w [monitorowania aplikacji](/sccm/apps/deploy-use/monitor-applications-from-the-console).  

 Pakiety i programy zawierają także szereg wbudowanych raportów, które umożliwiają monitorowanie informacji o stanie wdrożenia pakietów i programów. Te raporty mają kategorię **Dystrybucja oprogramowania — pakiety i programy** oraz **Dystrybucja oprogramowania — stan wdrażania pakietów i programów**.  

 Aby uzyskać więcej informacji o sposobie konfiguracji raportowania w programie Configuration Manager, zobacz [raportowania w programie System Center Configuration Manager](../../core/servers/manage/reporting.md).  

##  <a name="manage-packages-and-programs"></a>Zarządzać pakietami i programami  
 W **Biblioteka oprogramowania** obszaru roboczego, rozwiń węzeł **Zarządzanie aplikacjami**, wybierz **pakiety**, wybierz pakiet, którym chcesz zarządzać, a następnie wybierz zadanie zarządzania z poniższej tabeli:  

|Zadanie|Więcej informacji|  
|----------|----------------------|  
|**Utwórz wstępnie przygotowany plik zawartości**|Otwiera **Tworzenie kreatora przygotowanego pliku zawartości**, co pozwala utworzyć plik, który zawiera zawartości pakietu, które mogą być importowane ręcznie do innej lokacji. Przydaje się to, gdy przepustowość sieci między serwerem lokacji i punktem dystrybucji jest mała.|  
|**Utwórz Program**|Otwiera **Kreatora tworzenia programu**, co pozwala utworzyć nowy program dla tego pakietu.|  
|**Eksportowanie**|Otwiera **Kreatora eksportowania pakietu**, który pozwala wyeksportować wybrany pakiet i jego zawartość do pliku.<br /><br /> Aby uzyskać informacje o sposobie importowania pakietów i programów, zobacz [tworzyć pakiety i programy](/sccm/apps/deploy-use/packages-and-programs#create-packages-and-programs) w tym temacie.|  
|**Wdrażanie**|Otwiera **Kreatora wdrażania oprogramowania**, co umożliwia wdrożenie wybranego pakietu i programu w kolekcji. Aby uzyskać więcej informacji, zobacz [wdrażać pakiety i programy](/sccm/apps/deploy-use/packages-and-programs#deploy-packages-and-programs) w tym temacie.|  
|**Dystrybuuj zawartość**|Otwiera **kreatora dystrybucji zawartości**, co umożliwia wysyłanie zawartości skojarzonej z pakietem i programem do wybranych punktów dystrybucji lub grup punktów dystrybucji.|  
|**Aktualizuj punkty dystrybucji**|Aktualizuje punkty dystrybucji o najnowszą zawartość dla wybranego pakietu i programu.|  

##  <a name="about-the-package-definition-file-format"></a>O formacie pliku definicji pakietu  
 Pliki definicji pakietów to skrypty, których można użyć w celu automatyzacji tworzenia pakietów i programów z programu Configuration Manager. Udostępniają one wszystkie informacje programu Configuration Manager potrzebuje do utworzenia pakietu i programu, z wyjątkiem lokalizacji plików źródłowych pakietu. Każdy plik definicji pakietu to plik tekstu ASCII lub UTF-8 używającą z formatem pliku .ini i zawiera następujące sekcje:  

###  <a name="pdf"></a>[PDF]  
 W tej sekcji wskazywany jest plik definicji pakietu. Zawiera ona następujące informacje:  

-   **Wersja**: Określ wersję formatu pliku definicji pakietu, który jest używany przez plik. Odpowiada to wersji programu System Management Server (SMS) lub programu Configuration Manager, dla której plik został zapisany. Ten wpis jest wymagany.  

###  <a name="package-definition"></a>[Package Definition]  
 Określ właściwości pakietów i programów. Udostępnia ona następujące informacje:  

-   **Nazwa**: Nazwa pakietu, maksymalnie 50 znaków.  

-   **Wersja** (opcjonalnie): Wersja pakietu, maksymalnie 32 znaki.  

-   **Ikona** (opcjonalnie): Plik zawierający ikonę do używania tego pakietu. Jeśli jest określony, ta ikona zastąpi domyślną ikonę pakietu w konsoli programu Configuration Manager.

-   **Wydawca**: Wydawca pakietu, maksymalnie 32 znaki.

-   **Język**: Wersja językowa pakietu, maksymalnie 32 znaki.

-   **Komentarz** (opcjonalnie): Komentarz dotyczący pakietu, maksymalnie 127 znaków.

-   **ContainsNoFiles**: Ten wpis wskazuje, czy źródło jest skojarzony z pakietem.  

-   **Programy**: Programy, które są zdefiniowane dla tego pakietu. Każda nazwa programu odpowiada sekcji **[Program]** w tym pliku definicji pakietu.  

     Przykład:  

     `Programs=Typical, Custom, Uninstall`  

-   **MIFFileName**: Nazwa pliku Management Information Format (MIF), który zawiera stan pakietu, maksymalnie 50 znaków.  

-   **MIFName**: Nazwa pakietu (do dopasowania formatu MIF), maksymalnie 50 znaków.  

-   **MIFVersion**: Numer wersji pakietu (do dopasowania formatu MIF), maksymalnie 32 znaki.  

-   **MIFPublisher**: Wydawca oprogramowania pakietu (do dopasowania formatu MIF), maksymalnie 32 znaki.  

###  <a name="program"></a>[Program]  
 Dla każdego programu określonego w **programy** wpis w **[Package Definition]** sekcja pliku definicji pakietu musi zawierać sekcję [Program] z definicją tego programu. Każda sekcja Program zawiera następujące informacje:  

-   **Nazwa**: Nazwa programu, maksymalnie 50 znaków. Ten wpis musi być unikatowy w ramach pakietu. Ta nazwa jest używana podczas definiowania anonsów. Na komputerach klienckich nazwa programu jest pokazywana w obszarze **Uruchom programy anonsowane** w Panelu sterowania.  

-   **Ikona** (opcjonalnie): Określ plik zawierający ikonę do używania tego programu. Jeśli jest określony, ta ikona zastąpi domyślną ikonę programu w konsoli programu Configuration Manager i jest wyświetlana na komputerach klienckich podczas anonsowania programu.

-   **Komentarz** (opcjonalnie): Komentarz dotyczący programu, maksymalnie 127 znaków.

-   **CommandLine**: Określ wiersz polecenia dla programu, maksymalnie 127 znaków. To polecenie jest względne wobec folderu źródłowego pakietu.

-   **StartIn**: Określ folder roboczy dla programu, maksymalnie 127 znaków. Ten wpis może być ścieżką bezwzględną na komputerze klienckim lub ścieżką względną wobec folderu źródłowego pakietu.

-   **Uruchom**: Określ tryb, w którym program będzie uruchamiany. Można określić wartość **Minimized**, **Maximized** lub **Hidden**. Jeśli tego wpisu nie będzie, program będzie uruchamiany w trybie normalnym.  

-   **AfterRunning**: Określ dowolną akcję specjalną, która występuje po pomyślnym zakończeniu działania programu. Dostępne opcje to **SMSRestart**, **ProgramRestart** i **SMSLogoff**. Jeśli tego wpisu nie będzie, program nie wykonuje akcji specjalnej.  

-   **EstimatedDiskSpace**: Określ ilość miejsca na dysku, który program wymaga, aby uruchomić na komputerze. Dla tego ustawienia można wybrać opcję **Unknown** (ustawienie domyślne) lub ustawić liczbę całkowitą nie mniejszą od zera. Jeśli zostanie podana wartość, należy wskazać dla niej jednostkę.  

     Przykład:  

     `EstimatedDiskSpace=38MB`  

-   **EstimatedRunTime**: Określ szacowany czas (w minutach), jaki program powinien być wykonywany na komputerze klienckim. Dla tego ustawienia można wybrać opcję **Unknown** (ustawienie domyślne) lub ustawić liczbę całkowitą większą od zera.  

     Przykład:  

     `EstimatedRunTime=25`  

-   **SupportedClients**: Określ procesory i systemy operacyjne, na których ten program będzie uruchamiany. Podawane platformy muszą być rozdzielane przecinkami. Jeśli tego wpisu nie będzie, sprawdzanie obsługiwanych platform jest wyłączone dla tego programu.  

-   **SupportedClientMinVersionX**, **SupportedClientMaxVersionX**: Określ zakres numerów wersji systemów operacyjnych, które są określone w jego początek i koniec **SupportedClients** wpisu.  

     Przykład:  

    ```  
    SupportedClients=Win NT (I386),Win NT (IA64),Win NT (x64)  
    Win NT (I386) MinVersion1=5.00.2195.4  
    Win NT (I386) MaxVersion1=5.00.2195.4  
    Win NT (I386) MinVersion2=5.10.2600.2  
    Win NT (I386) MaxVersion2=5.10.2600.2  
    Win NT (I386) MinVersion3=5.20.0000.0  
    Win NT (I386) MaxVersion3=5.20.9999.9999  
    Win NT (I386) MinVersion4=5.20.3790.0  
    Win NT (I386) MaxVersion4=5.20.3790.2  
    Win NT (I386) MinVersion5=6.00.0000.0  
    Win NT (I386) MaxVersion5=6.00.9999.9999  
    Win NT (IA64) MinVersion1=5.20.0000.0  
    Win NT (IA64) MaxVersion1=5.20.9999.9999  
    Win NT (x64) MinVersion1=5.20.0000.0  
    Win NT (x64) MaxVersion1=5.20.9999.9999  
    Win NT (x64) MinVersion2=5.20.3790.0  
    Win NT (x64) MaxVersion2=5.20.9999.9999  
    Win NT (x64) MinVersion3=5.20.3790.0  
    Win NT (x64) MaxVersion3=5.20.3790.2  
    Win NT (x64) MinVersion4=6.00.0000.0  
    Win NT (x64) MaxVersion4=6.00.9999.9999   
    ```  

-   **AdditionalProgramRequirements** (opcjonalnie): Podaj inne informacje i wymagania dotyczące komputerów klienckich, maksymalnie 127 znaków.

-   **CanRunWhen**: Określ stan użytkownika, którego program wymaga, aby uruchomić na komputerze klienckim. Dostępne wartości to **UserLoggedOn**, **NoUserLoggedOn** i **AnyUserStatus**. Wartość domyślna to **UserLoggedOn**.  

-   **UserInputRequired**: Określ, czy program wymaga interakcji z użytkownikiem. Dostępne wartości to **True** i **False**. Wartość domyślna to **True**. Ten wpis jest ustawiony na wartość **False**, jeśli wpis **CanRunWhen** nie jest ustawiony na wartość **UserLoggedOn**.  

-   **AdminRightsRequired**: Określ, czy program wymaga poświadczeń administracyjnych na komputerze do uruchomienia. Dostępne wartości to **True** i **False**. Wartość domyślna to **False**. Ten wpis jest ustawiony na wartość **True**, jeśli wpis **CanRunWhen** nie jest ustawiony na wartość **UserLoggedOn**.  

-   **UseInstallAccount**: Określ, czy program używa konta instalacji oprogramowania klienta, gdy jest uruchamiany na komputerach klienckich. Wartością domyślną jest **False**. Ten wpis jest też ustawiony na wartość **False**, jeśli wpis **CanRunWhen** jest ustawiony na wartość **UserLoggedOn**.  

-   **DriveLetterConnection**: Określ, czy program wymaga połączenia z literą dysku do plików pakietu, które znajdują się w punkcie dystrybucji. Można określić wartość **True** lub **False**. Wartość domyślna to **False**, co pozwala programowi na używanie połączenia Universal Naming Convention (UNC). Jeśli ta wartość jest równa **True**, następna dostępna litera dysku jest użyta (począwszy od Z: Wstecz).  

-   **SpecifyDrive** (opcjonalnie): Określ literę dysku, którego program wymaga, aby nawiązać połączenie plików pakietu w punkcie dystrybucji. Określenie tej wartości wymusza stosowanie wskazanej litery dysku w połączeniach klienta z punktami dystrybucji.

-   **ReconnectDriveAtLogon**: Określ, czy komputer kliencki z punktem dystrybucji po zalogowaniu użytkownika. Dostępne wartości to **True** i **False**. Wartość domyślna to **False**.  

-   **DependentProgram**: Określ program, w tym pakiecie, który musi zostać uruchomiony przed bieżącym programem. Ten wpis ma format **DependentProgram**=<**nazwa_programu>**, gdzie **<nazwa_programu\>** to wpis **Name** dla danego programu w pliku definicji pakietu. Jeśli nie ma żadnych programów zależnych, ten wpis należy pozostawić pusty.  

     Przykład:  

     DependentProgram=Admin  
    DependentProgram=  

-   **Przypisanie**: Określ, w jaki sposób program jest przypisywany użytkownikom. Ta wartość może być: **FirstUser** (tylko pierwszy użytkownik, który loguje się do klienta, uruchamia program) lub **EveryUser** (każdy użytkownik, który się zaloguje, uruchamia program). Gdy wpis **CanRunWhen** nie jest ustawiony na wartość **UserLoggedOn**, ten wpis jest ustawiony na wartość **FirstUser**.  

-   **Wyłączone**: Określ, czy ten program może być anonsowany dla klientów. Dostępne wartości to **True** i **False**. Wartość domyślna to **False**.  
