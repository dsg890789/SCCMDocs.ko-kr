---
title: Tworzenie aplikacji | Dokumentacja firmy Microsoft
description: "Tworzenie i wdrażanie aplikacji i typów wdrożeń w programie System Center Configuration Manager."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cc230ff4-7056-4339-a0a6-6a44cdbb2857
caps.latest.revision: "14"
caps.handback.revision: "0"
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.openlocfilehash: 4d048d4f9ab01b28e6c21a38cca4d82c85030618
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="create-applications-with-system-center-configuration-manager"></a>Tworzenie aplikacji w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Aplikacji programu System Center Configuration Manager zawiera pliki i informacje, które są wymagane do wdrożenia oprogramowania na urządzeniu. Aplikacja ma co najmniej jeden typ wdrożenia obejmujący pliki instalacyjne i informacje niezbędne do zainstalowania oprogramowania. Typ wdrożenia ma również zasady określające, kiedy i jak oprogramowanie zostanie wdrożone.  

 Aplikacje można utworzyć przy użyciu następujących metod:  

-   Automatyczne tworzenie aplikacji i typów wdrożenia przez odczytanie plików instalacyjnych aplikacji.  

-   ręczne utworzenie aplikacji, a następnie dodanie typów wdrożenia.  

-   Zaimportowanie aplikacji z pliku.  

> [!NOTE]  
>  [Tworzenie aplikacji dla urządzeń przenośnych](../../mdm/deploy-use/create-applications.md) zawiera szczegółowe informacje dotyczące tworzenia systemu iOS, Windows Phone i aplikacji systemu Android.  

Poniższe kroki umożliwiają utworzenie aplikacji programu Configuration Manager i typów wdrożeń.  

## <a name="start-the-create-application-wizard"></a>Uruchom Kreatora tworzenia aplikacji  

1.  W konsoli programu Configuration Manager wybierz **Biblioteka oprogramowania** > **Zarządzanie aplikacjami** > **aplikacji**.  

3.  Na **Home** karcie **Utwórz** grupy, wybierz **tworzenie aplikacji**.  

## <a name="specify-whether-you-want-to-automatically-detect-application-information-or-manually-define-the-information"></a>Określ, czy chcesz automatycznie Wykryj informacje o aplikacji, lub ręcznie zdefiniować informacji o  

-   Automatycznie wykryj informacje o aplikacji, jeśli chcesz utworzyć prostą aplikację z pojedynczym typem wdrożenia, takich jak plik Instalatora Windows, który nie ma zależności ani wymagań. Po utworzeniu aplikacji przy użyciu tej procedury można ją edytować w miarę potrzeby, aby dodawać lub zmieniać typy wdrożeń oraz dodawać metody wykrywania, zależności lub wymagania.  

-   Ręcznie określ informacje o aplikacji do tworzenia bardziej złożone aplikacje mające wiele typów wdrożeń, zależności, metod wykrywania lub wymagań.  

### <a name="automatically-detect-application-information"></a>Automatycznie wykryj informacje o aplikacji  

1.  Na **ogólne** strony kreatora tworzenia aplikacji wybierz **automatycznie Wykryj informacje o tej aplikacji z plików instalacyjnych**.  

2.  W **typu** listy rozwijanej, wybierz typ pliku instalacyjnego aplikacji którego chcesz użyć do wykrywania informacji o aplikacji. Informacje o dostępnych typach instalacji znajdują się w sekcji [Typy wdrożeń obsługiwane przez program Configuration Manager](/sccm/apps/deploy-use/create-applications#deployment-types-supported-by-configuration-manager) w tym temacie.  

3.  W **lokalizacji** Określ ścieżkę UNC (w postaci  *\\ \\serwera\\udostępnianie\\\filename*) lub łącze do pliku instalacyjnego aplikacji, które chcesz użyć do wykrywania informacji o aplikacji magazynu. Można też kliknąć przycisk **Przeglądaj**, aby przejść do lokalizacji pliku instalacyjnego.  

    > [!IMPORTANT]  
    >  Po wybraniu **Instalatora Windows (\*pliku .msi)** w ustawieniu typu aplikacji wszystkie pliki w folderze określonym przez użytkownika zostaną zaimportowane z aplikacją i będą wysyłane do punktów dystrybucji. Upewnij się, że folder zostanie zawiera tylko pliki, które są niezbędne do zainstalowania aplikacji. Menedżer konfiguracji został sprawdzony pod kątem obsługi maksymalnie 20 000 plików aplikacji w pakiecie aplikacji. Jeśli aplikacja ma więcej plików, należy rozważyć utworzenie wielu aplikacji zawierających mniejszą liczbę plików.  

    >  Musi mieć dostęp do ścieżki UNC, do której ma aplikacji i wszelkich podfolderów z zawartością aplikacji.  

4.  Na **Importuj informacje** strony kreatora tworzenia aplikacji przejrzyj informacje, które zostały zaimportowane, a następnie wybierz pozycję **dalej**. Jeśli to konieczne, możesz wybrać **Wstecz** aby wrócić do poprzedniej strony i poprawić błędy.  

5.  Na **ogólne informacje** strony kreatora tworzenia aplikacji Podaj następujące informacje:  

    > [!NOTE]  
    >  Niektóre z tych informacji mogą już być podane, jeśli zostały uzyskane automatycznie z plików instalacyjnych aplikacji. Wyświetlane opcje mogą się ponadto różnić w zależności od typu tworzonej aplikacji.  

    -   Ogólne informacje o aplikacji, takie jak nazwa aplikacji, komentarze, wersja i opcjonalne informacje w celu znalezienia aplikacji w konsoli programu Configuration Manager.  

    -   **Program instalacyjny**— Określ program instalacyjny oraz wszelkie wymagane właściwości, które są niezbędne do zainstalowania typu wdrożenia aplikacji.  

        > [!TIP]  
        >  Jeśli program instalacyjny nie jest wyświetlana, wybierz **Przeglądaj** i przejdź do lokalizacji programu instalacyjnego.  

    -   **Zachowanie podczas instalowania**— Określ, czy typ wdrożenia aplikacji zostanie zainstalowany tylko dla obecnie zalogowanego użytkownika lub dla wszystkich użytkowników. Można również określić, że typ wdrożenia zostanie zainstalowany dla wszystkich użytkowników, jeśli Jeśli jest wdrażana dla użytkownika jest wdrożony na urządzeniu lub tylko do określonego użytkownika.  

    -   **Użyj automatycznego połączenia VPN (jeśli jest skonfigurowane)**— Jeśli profil sieci VPN został wdrożony na urządzeniu, na którym uruchomiono aplikację, uruchom połączenie sieci VPN po uruchomieniu aplikacji (Windows 8.1 i Windows Phone 8.1 tylko).  

         Na urządzeniach Windows Phone 8.1 automatyczne połączenia VPN nie są obsługiwane, jeśli więcej niż jeden profil sieci VPN został wdrożony na urządzeniu.  

         Aby uzyskać więcej informacji na temat profilów sieci VPN, zobacz [profilów sieci VPN](../../protect/deploy-use/vpn-profiles.md).  

6.  Wybierz **dalej**, przejrzyj informacje o aplikacji na **Podsumowanie** strony, a następnie Zakończ pracę Kreatora tworzenia aplikacji.  

Nowa aplikacja pojawi się w **aplikacji** węzła konsoli programu Configuration Manager, i ukończeniu tworzenia aplikacji. Informacje o dodawaniu większej liczby typów wdrożenia do aplikacji znajdują się w sekcji [Tworzenie typów wdrożenia aplikacji](/sccm/apps/deploy-use/create-applications#create-deployment-types-for-the-application) w tym temacie.  

### <a name="manually-specify-application-information"></a>Ręcznie określ informacje o aplikacji  

1.  Na **ogólne** strony kreatora tworzenia aplikacji wybierz **ręcznie określ informacje o aplikacji**, a następnie wybierz pozycję **dalej**.  

2.  Określ ogólne informacje o aplikacji, takie jak nazwa aplikacji, komentarze, wersja i opcjonalne informacje w celu znalezienia aplikacji w konsoli programu Configuration Manager.  

3.  Na **katalogu aplikacji** strony kreatora tworzenia aplikacji Podaj następujące informacje:  

    -   **Wybrany język**— z listy rozwijanej wybierz wersję językową aplikacji, którą chcesz skonfigurować. Wybierz **Dodaj lub usuń** Aby skonfigurować więcej języków aplikacji.  

    -   **Nazwa zlokalizowanej aplikacji**— Określ nazwę aplikacji w języku wybranym **wybrany język** listy rozwijanej.  

        > [!IMPORTANT]  
        >  Podaj zlokalizowaną nazwę aplikacji dla każdej skonfigurowanej wersji.  

    -   **Kategorie użytkowników**— wybierz **Edytuj** Aby określić kategorie aplikacji w języku wybranym **wybrany język** listy rozwijanej. Użytkownicy Centrum oprogramowania można używać owych wybranych kategorii do filtrowania i sortowania dostępnych aplikacji.  

    -   **Dokumentacja użytkownika**— wybierz **Przeglądaj** Aby określić adres URL lub ścieżkę UNC i plik nazwę pliku, który użytkownicy Centrum oprogramowania mogą odczytać w celu uzyskania dodatkowych informacji o tej aplikacji.  

    -   **Tekst łącza**— Określ tekst, który będzie wyświetlany zamiast adresu URL aplikacji.  

    -   **Adres URL aplikacji prywatności**— Określ adres URL prowadzący do zasad zachowania poufności informacji dla aplikacji.  

    -   **Zlokalizowany opis**— wprowadź opis dla tej aplikacji w języku wybranym **wybrany język** listy rozwijanej.  

    -   **Słowa kluczowe**— wprowadź listę słów kluczowych w języku wybranym **wybrany język** listy rozwijanej. Słowa kluczowe ułatwią użytkownikom Centrum oprogramowania wyszukiwanie aplikacji.  

    -   **Ikona**— wybierz **Przeglądaj** aby wybrać ikonę tej aplikacji spośród dostępnych ikon. Jeśli nie określisz ikony, ikona domyślna będzie używany dla tej aplikacji.  

    -   **Wyświetlaj jako polecaną aplikację i wyróżnij w portalu firmy**— wybierz tę opcję, aby wyróżnić aplikację w portalu firmy.  

4.  Na **typy wdrożeń** strony kreatora tworzenia aplikacji wybierz **Dodaj** do utworzenia nowego typu wdrożenia.  

 Aby uzyskać więcej informacji, zobacz [tworzenia typów wdrożenia dla aplikacji](/sccm/apps/deploy-use/create-applications#create-deployment-types-for-the-application).  

5.  Wybierz **dalej**, przejrzyj informacje o aplikacji na **Podsumowanie** strony, a następnie Zakończ pracę Kreatora tworzenia aplikacji.  

Nowa aplikacja pojawi się w **aplikacji** węzła konsoli programu Configuration Manager.  

##  <a name="create-deployment-types-for-the-application"></a>Tworzenie typów wdrożenia dla aplikacji  
 W przypadku wybrania **automatycznie Zidentyfikuj informacje o tym typie wdrożenia z plików instalacyjnych** na **ogólne** strony kreatora tworzenia typu wdrożenia nie należy zakończyć niektórych czynności następujących procedur.  

## <a name="start-the-create-deployment-type-wizard"></a>Uruchomienie Kreatora tworzenia typu wdrożenia  

1.  W konsoli programu Configuration Manager wybierz **Biblioteka oprogramowania** > **Zarządzanie aplikacjami** > **aplikacji**.  

3.  Wybierz aplikację, a następnie na **Home** karcie **aplikacji** grupy, wybierz **Utwórz typ wdrożenia**.  

> [!TIP]  
>  Można również uruchomić Kreatora tworzenia typu wdrożenia z Kreatora tworzenia aplikacji i **typy wdrożeń** karcie *< nazwa aplikacji\>*  **właściwości** okno dialogowe.  

## <a name="specify-whether-you-want-to-automatically-detect-deployment-type-information-or-manually-set-up-the-information"></a>Określ, czy mają być automatycznie Wykryj informacje o typie wdrożenia, lub ręcznie skonfigurować informacje  
 Użyj jednej z następujących procedur, aby wykrywać automatycznie lub ręcznie skonfigurować informacje o typie wdrożenia.  

### <a name="automatically-detect-deployment-type-information"></a>Automatycznie wykryj informacje o typie wdrożenia  

1.  Na **ogólne** strony kreatora tworzenia typu wdrożenia wybierz **automatycznie Zidentyfikuj informacje o tym typie wdrożenia z plików instalacyjnych**.  

2.  W **typu** wybierz typ pliku instalacyjnego aplikacji, którego chcesz użyć do wykrywania informacji o typie wdrożenia.  

3.  W **lokalizacji** Określ ścieżkę UNC (w postaci  *\\ \\serwera\\udostępnianie\\filename*) lub określić linku do plików instalacyjnych aplikacji oraz zawartość, której chcesz użyć do wykrywania informacji o typie wdrożenia w sklepie. Można również wybrać **Przeglądaj** aby wskazać plik instalacyjny.  

    > [!NOTE]  
    >  Musi mieć dostęp do ścieżki UNC, do której ma aplikacji i wszelkich podfolderów z zawartością aplikacji.  

4.  Na **Importuj informacje** strony kreatora tworzenia typu wdrożenia Przejrzyj informacje, które zostały zaimportowane, a następnie wybierz pozycję **dalej**. Można również wybrać **Wstecz** aby wrócić do poprzedniej strony i poprawić błędy.  

5.  Na **ogólne informacje** strony kreatora tworzenia typu wdrożenia Podaj następujące informacje:  

    > [!NOTE]  
    >  Niektóre informacje o typie wdrożenia mogą już być obecne, jeśli zostały odczytane z plików instalacyjnych aplikacji. Ponadto wyświetlane opcje mogą się różnić w zależności od tworzonego typu wdrożenia.  

    -   Ogólne informacje o typie wdrożenia, takie jak nazwa, komentarze administratora oraz dostępne języki.  

    -   **Program instalacyjny**— Określ program instalacyjny oraz wszelkie właściwości niezbędne do zainstalowania typu wdrożenia.  

    -   **Zachowanie podczas instalowania**— Określ, czy do zainstalowania typu wdrożenia dla bieżącego użytkownika lub dla wszystkich użytkowników. Można również określić, czy do zainstalowania typu wdrożenia dla wszystkich użytkowników, jeśli jest wdrażana na urządzeniu, lub czy zainstalować wdrożenia wpisz do użytkownika tylko wtedy, gdy jest wdrożony dla użytkownika.  

    -   **Użyj automatycznego połączenia VPN (jeśli jest skonfigurowane)**— Jeśli profil sieci VPN został wdrożony na urządzeniu, na którym uruchomiono aplikację, uruchom połączenie sieci VPN po uruchomieniu aplikacji (Windows 8.1 i Windows Phone 8.1 tylko). Jeśli wiele profilów sieci VPN zostały wdrożone na urządzeniu Windows 8.1, pierwszy wdrożonego profilu sieci VPN jest używany domyślnie.  

         Na urządzeniach Windows Phone 8.1 automatyczne połączenia VPN nie są obsługiwane, jeśli więcej niż jeden profil sieci VPN został wdrożony na urządzeniu.  

         Aby uzyskać więcej informacji na temat profilów sieci VPN, zobacz [profilów sieci VPN w programie System Center Configuration Manager](../../protect/deploy-use/vpn-profiles.md).  

6.  Wybierz **dalej**, a następnie przejdź do [określenie opcji zawartości typu wdrożenia](/sccm/apps/deploy-use/create-applications#specify-content-options-for-the-deployment-type).  

### <a name="manually-set-up-the-deployment-type-information"></a>Ręcznie skonfigurować informacje o typie wdrożenia  

1.  Na **ogólne** strony kreatora tworzenia typu wdrożenia wybierz **ręcznie określ informacje o typie wdrożenia**.  

2.  W **typu** , wybierz typ pliku instalacyjnego aplikacji, którego chcesz użyć do wykrywania informacji o typie wdrożenia. Można wybrać typy instalacji używane w przypadku automatycznego wykrywania informacji o typie wdrożenia, a można też określić skrypt instalacji typu wdrożenia.  

3.  Na **ogólne informacje** strony kreatora tworzenia typu wdrożenia Określ nazwę typu wdrożenia, opcjonalny opis oraz języki, w których chcesz udostępnić ten typ wdrożenia, a następnie wybierz **dalej**.  

4.  Przejdź do sekcji [Określenie opcji zawartości typu wdrożenia](/sccm/apps/deploy-use/create-applications#specify-content-options-for-the-deployment-type).  

##  <a name="specify-content-options-for-the-deployment-type"></a>Określenie opcji zawartości typu wdrożenia  

1.  Na **zawartości** strony kreatora tworzenia typu wdrożenia Podaj następujące informacje:  

    -   **Lokalizacja zawartości**— Określ lokalizację zawartości dla tego typu wdrożenia, lub wybierz **Przeglądaj** wybrać folder zawartości typu wdrożenia.  

        > [!IMPORTANT]  
        >  Konto System na komputerze serwera lokacji musi mieć uprawnienia do określonej lokalizacji zawartości.  

    -   **Odinstaluj ustawienia zawartości**— określ jedną z następujących opcji:
        - **Taka sama, jak zainstalować zawartość**— wybierz tę opcję, jeśli instalowania i odinstalowywania zawartości są takie same. Jest to zachowanie domyślne.
        - **Nie odinstalowania zawartości**— wybierz tę opcję, jeśli aplikacja nie wymaga zawartości do odinstalowania.
        - **Inna niż instalacja zawartości**— wybierz tę opcję, jeśli zawartość Odinstaluj różni się od instalacji zawartości.

4. W przypadku wybrania **różne od instalacji zawartości**, przejdź do, lub wprowadź lokalizację zawartości aplikacji, który służy do odinstalowania aplikacji.
5. Kliknij przycisk **OK** aby zamknąć okno dialogowe właściwości typu wdrożenia.

    -   **Utrwal zawartość w pamięci podręcznej klienta**— wybierz tę opcję, aby określić, czy zawartość powinna być przechowywana w pamięci podręcznej na komputerze klienckim przez czas nieokreślony, nawet jeśli została już uruchomiona. Mimo że ta opcja może być przydatne w przypadku niektórych wdrożeń, takich jak Instalator Windows — oprogramowania wymagającego kopii lokalnej był dostępny do zastosowania aktualizacji, zmniejsza ilości dostępnej pamięci podręcznej. Wybierz tę opcję, może spowodować dużego wdrożenia Niepowodzenie w późniejszym czasie, jeśli pamięć podręczna nie ma wystarczająco dużo miejsca.  

    -   **Zezwalaj klientom na współużytkowanie zawartości z innymi klientami w tej samej podsieci**— wybierz tę opcję, aby zmniejszyć obciążenie sieci, zezwalając klientom na pobieranie zawartości z innych klientów lokalnych w sieci, w których znajduje się już pobrana zawartość w pamięci podręcznej. Ta opcja korzysta z technologii Windows BranchCache.  

    -   **Program instalacyjny**— Określ nazwę programu instalacyjnego oraz wszelkie wymagane parametry instalacji lub wybierz **Przeglądaj** aby wskazać plik instalacyjny.  

    -   **Instalacja rozpocznie się za**— Opcjonalnie określ folder zawierający program instalacyjny typu wdrożenia. Ten folder może być ścieżką bezwzględną na kliencie lub ścieżką do folderu punktu dystrybucji, który zawiera pliki instalacyjne.  

    -   **Program dezinstalacyjny**— Opcjonalnie określ nazwę programu dezinstalacyjnego oraz wszelkie wymagane parametry, lub wybierz **Przeglądaj** ich wyszukanie.  

    -   **Dezinstalacja rozpocznie się za**— Opcjonalnie określ folder zawierający program dezinstalacyjny typu wdrożenia. Ten folder może być ścieżką bezwzględną na kliencie lub ścieżką względną wobec folderu punktu dystrybucji, który zawiera pakiet.  

    -   **Uruchom program instalacyjny i dezinstalacyjny jako proces 32-bitowy na klientach 64-bitowych**— Użyj 32-bitowych lokalizacje plików i rejestru na komputerach z systemem Windows, aby uruchomić program instalacyjny typu wdrożenia.  

2.  Wybierz **dalej**.  

## <a name="set-up-detection-methods-to-indicate-the-presence-of-the-deployment-type-windows-pcs-only"></a>Konfigurowanie metod wykrywania obecności typu wdrożenia (tylko komputery z systemem Windows)  
 Ta procedura konfiguruje metodę wykrywania, która wskazuje, czy typ wdrożenia jest już zainstalowany.  

1.  Na **metody wykrywania** strony kreatora tworzenia typu wdrożenia wybierz **Konfiguruj reguły do wykrycia obecności tego typu wdrożenia**, a następnie wybierz pozycję **Dodaj klauzulę**.  

    > [!NOTE]  
    >  Można również wybrać opcję **Użyj skryptu niestandardowego do wykrycia obecności tego typu wdrożenia**. Aby uzyskać więcej informacji, zobacz [Użyj niestandardowego skryptu w celu sprawdzenia obecności typu wdrożenia](/sccm/apps/deploy-use/create-applications#Use-a-custom-script-to-check-for-the-presence-of-a-deployment-type).  

2.  W oknie dialogowym **Reguła wykrywania** z listy rozwijanej **Typ ustawienia** wybierz metodę, której chcesz używać do wykrywania obecności typu wdrożenia. Można wybrać jedną z następujących metod:  

    -   **System plików**— ta metoda służy do wykrywania, czy określony plik lub folder istnieje na urządzeniu klienckim, co wskazuje, że aplikacja jest zainstalowana.  

        > [!NOTE]  
        >  **System plików** typ nie obsługuje określania w polu Ścieżka ścieżki UNC do udziału sieciowego. Na urządzeniu klienta można określić wyłącznie ścieżkę lokalną.  
        >   
        >  Aby sprawdzić lokalizacje plików 32-bitowych pod kątem określonego pliku lub folderu, wybierz opcję **ten plik lub folder jest skojarzony z aplikacją 32-bitowych na 64-bitowym** pierwszy. Jeśli plik lub folder nie zostaną znalezione, zostaną przeszukane lokalizacje plików 64-bitowych.  

    -   **Rejestru**— ta metoda służy do wykrywania, czy określony klucz rejestru lub wartość rejestru istnieje na urządzeniu klienckim, co wskazuje, że aplikacja jest zainstalowana.  

        > [!NOTE]  
        >  Aby sprawdzić lokalizacje 32-bitowego rejestru pod kątem obecności określonego klucza rejestru, wybierz opcję **ten klucz rejestru jest skojarzony z aplikacją 32-bitowych na 64-bitowym** pierwszy. Jeśli klucz rejestru nie zostaną znaleziony, zostaną przeszukane lokalizacje plików 64-bitowych.  

    -   **Instalator Windows**— ta metoda służy do wykrywania, czy określony plik Instalatora Windows istnieje na urządzeniu klienckim, co wskazuje, że aplikacja jest zainstalowana.  

3.  Określ informacje szczegółowe dotyczące pozycji, której chcesz użyć do wykrywania, czy ten typ wdrożenia został zainstalowany. Możesz na przykład użyć pliku, folderu, klucza rejestru, wartości rejestru lub kodu produktu Instalatora Windows.  

4.  Określ szczegóły dotyczące wartości, którą chcesz ocenić na podstawie pozycji użytej do wykrycia, czy dany typ wdrożenia został zainstalowany. Na przykład, jeśli używany plik, aby sprawdzić, czy dany typ wdrożenia został zainstalowany, możesz wybrać **aby wskazywanie obecności tej aplikacji w systemie docelowym musi istnieć ustawienie systemu plików**.  

5.  Wybierz **dalej** zamknąć **reguły wykrywania** okno dialogowe.  

###  <a name="use-a-custom-script-to-check-for-the-presence-of-a-deployment-type"></a>Użyj niestandardowego skryptu w celu sprawdzenia obecności typu wdrożenia  

1.  Na **metody wykrywania** strony kreatora tworzenia typu wdrożenia wybierz **Użyj skryptu niestandardowego do wykrycia obecności tego typu wdrożenia** polu, a następnie wybierz pozycję **Edytuj**.  

2.  W oknie dialogowym **Edytor skryptów** z listy rozwijanej **Typ skryptu** wybierz język skryptu, którego chcesz używać do wykrywania obecności typu wdrożenia.  

3.  W **skryptu zawartość** wprowadź skrypt, którego chcesz użyć. Możesz również wkleić w tym polu zawartość istniejącego skryptu lub wybrać **Otwórz** aby przejść do istniejącego zapisanego skryptu. Program Configuration Manager sprawdza wyniki skryptu, odczytując wartości zapisane w strumieniu wyjściowym Standard Out (STDOUT), w strumieniu wyjściowym Standard Error (STDERR) oraz kod zakończenia ze skryptu. Jeśli kod zakończenia ma wartość niezerową, oznacza to, że działanie skryptu zakończyło się niepowodzeniem, a stan wykrywania aplikacji jest nieznany. Jeśli kod zakończenia to zero, a STDOUT zawiera dane, stan wykrywania aplikacji jest zainstalowany.  

 Skorzystaj z poniższej tabeli, aby zobaczyć sposób użycia dane wyjściowe skryptu, aby sprawdzić, czy aplikacja jest zainstalowana.  

|Kod zakończenia skryptu|Szczegóły|
|--------------------------------|-----------------|
|0|**Dane odczytane ze strumienia wyjściowego STDOUT**— pusty<br /><br /> **Dane odczytane ze strumienia wyjściowego STDERR**— pusty<br /><br /> **Wynik skryptu**— Powodzenie<br /><br /> **Stan wykrywania aplikacji**— nie jest zainstalowany|  
|0|**Dane odczytane ze strumienia wyjściowego STDOUT**— pusty<br /><br /> **Dane odczytane ze strumienia wyjściowego STDERR**— niepuste<br /><br /> **Wynik skryptu**— błąd<br /><br /> **Stan wykrywania aplikacji**— nieznany|  
|0|**Dane odczytane ze strumienia wyjściowego STDOUT**— niepuste<br /><br /> **Dane odczytane ze strumienia wyjściowego STDERR**— pusty<br /><br /> **Wynik skryptu**— Powodzenie<br /><br /> **Stan wykrywania aplikacji**— zainstalowany|  
|0|**Dane odczytane ze strumienia wyjściowego STDOUT**— niepuste<br /><br /> **Dane odczytane ze strumienia wyjściowego STDERR**— niepuste<br /><br /> **Wynik skryptu**— Powodzenie<br /><br /> **Stan wykrywania aplikacji**— zainstalowany|  
|Wartość niezerowa|**Dane odczytane ze strumienia wyjściowego STDOUT**— pusty<br /><br /> **Dane odczytane ze strumienia wyjściowego STDERR**— pusty<br /><br /> **Wynik skryptu**— błąd<br /><br /> **Stan wykrywania aplikacji**— nieznany|  
|Wartość niezerowa|**Dane odczytane ze strumienia wyjściowego STDOUT**— pusty<br /><br /> **Dane odczytane ze strumienia wyjściowego STDERR**— niepuste<br /><br /> **Wynik skryptu**— błąd<br /><br /> **Stan wykrywania aplikacji**— nieznany|  
|Wartość niezerowa|**Dane odczytane ze strumienia wyjściowego STDOUT**— niepuste<br /><br /> **Dane odczytane ze strumienia wyjściowego STDERR**— pusty<br /><br /> **Wynik skryptu**— błąd<br /><br /> **Stan wykrywania aplikacji**— nieznany|  
|Wartość niezerowa|**Dane odczytane ze strumienia wyjściowego STDOUT**— niepuste<br /><br /> **Dane odczytane ze strumienia wyjściowego STDERR**— niepuste<br /><br /> **Wynik skryptu**— błąd<br /><br /> **Stan wykrywania aplikacji**— nieznany|  

Poniższa tabela zawiera Microsoft Visual Basic (VB) przykładowe skrypty, które służy do pisania własnych skryptów wykrywania aplikacji.  

|Przykładowy skrypt Visual Basic|Opis|  
|--------------------------------|-----------------|  
|**WScript.Quit(1)**|Skrypt zwraca kod zakończenia o wartości innej niż zero, co oznacza, że jego niepomyślne wykonanie. W takiej sytuacji stan wykrywania aplikacji będzie nieznany.|  
|**WScript.StdErr.Write "Skrypt nie powiodło się"**<br /><br /> **WScript.Quit(0)**|Skrypt zwraca kod zakończenia o wartości wynoszącej zero, jednak wartość strumienia wyjściowego STDERR nie będzie pusta, co oznacza niepomyślne wykonanie skryptu. W takiej sytuacji stan wykrywania aplikacji będzie nieznany.|  
|**WScript.Quit(0)**|Skrypt zwraca kod zakończenia o wartości zero, co oznacza jego pomyślne wykonanie. Wartość strumienia wyjściowego STDOUT jest jednak pusta, co oznacza, że aplikacja nie jest zainstalowana.|  
|**WScript.StdOut.Write "aplikacja jest zainstalowane"**<br /><br /> **WScript.Quit(0)**|Skrypt zwraca kod zakończenia o wartości zero, co oznacza jego pomyślne wykonanie. Wartość strumienia wyjściowego STDOUT nie jest pusta, co oznacza, że aplikacja jest zainstalowana.|  
|**WScript.StdOut.Write "aplikacja jest zainstalowane"**<br /><br /> **WScript.StdErr.Write "Ukończone"**<br /><br /> **WScript.Quit(0)**|Skrypt zwraca kod zakończenia o wartości zero, co oznacza jego pomyślne wykonanie. Wartości strumieni wyjściowych STDOUT i STDERR nie są puste, co oznacza, że aplikacja jest zainstalowana.|  

 > [!NOTE]  
 >  Maksymalny rozmiar skryptu, jakiego można użyć, to 32 kilobajty (KB).  

4.  Wybierz **OK** zamknąć **Edytor skryptów** okno dialogowe.  

## <a name="specify-user-experience-options-for-the-deployment-type"></a>Określenie opcji czynności użytkownika dotyczących typu wdrożenia  
 Te ustawienia określają, jak aplikacja zostanie zainstalowana na urządzeniach i jakie użytkownik będzie widział.  

1.  Na **środowisko użytkownika** strony kreatora tworzenia typu wdrożenia Podaj następujące informacje:  

    -   **Zachowanie podczas instalacji**— z listy rozwijanej wybierz jedną z następujących opcji:  

        -   **Zainstaluj dla użytkownika**— aplikacja zostanie zainstalowana tylko dla użytkownika, do której aplikacja jest wdrażana.  

        -   **Zainstaluj dla systemu**— aplikacja zostanie zainstalowana tylko raz i będzie dostępna dla wszystkich użytkowników.  

        -   **Zainstaluj dla systemu, jeśli zasób jest urządzeniem; w przeciwnym razie zainstaluj dla użytkownika**— Jeśli aplikacja jest wdrażana na urządzeniu, zostanie zainstalowany dla wszystkich użytkowników. Jeśli aplikacja jest wdrażana dla użytkownika, zostanie zainstalowana tylko dla tego użytkownika.  

    -   **Wymagane zalogowanie**— Określ wymagania dotyczące logowania dla tego typu wdrożenia przy użyciu następujących opcji:  

        -   **Tylko wtedy, gdy użytkownik jest zalogowany**  

        -   **Określa, czy użytkownik jest zalogowany**  

        -   **Tylko wtedy, gdy użytkownik nie jest zalogowany**  

        > [!NOTE]  
        >  Domyślnie ta opcja **tylko, gdy użytkownik jest zalogowany**, i nie można zmienić, jeśli wybrano **zainstaluj dla użytkownika** w **zachowanie podczas instalacji** listy rozwijanej.  

    -   **Widoczność programu instalacyjnego**— Określ tryb, w którym typ wdrażania będzie uruchamiany na urządzeniach klienckich. Dostępne są następujące opcje:  

        -   **Zmaksymalizowane**— typ wdrożenia zostanie uruchomiony w trybie zmaksymalizowanym na urządzeniach klienckich. Użytkownicy będą widzieć wszystkie działania instalacyjne.  

        -   **Normalny**— typ wdrożenia zostanie uruchomiony w trybie normalnym na podstawie ustawień domyślnych systemu i programu. Jest to tryb domyślny.  

        -   **Zminimalizowany**— typ wdrożenia zostanie uruchomiony w trybie zminimalizowanym na urządzeniach klienckich. Użytkownicy będą widzieć działanie instalacji w obszarze powiadomień lub na pasku zadań.  

        -   **Ukryte**— typ wdrożenia zostanie ukryta na urządzeniach klienckich, a użytkownicy nie będą widzieć żadnych działań instalacyjnych.  

    -   **Zezwalaj użytkownikom na wyświetlanie i interakcji z instalacją programu**— Określ, czy użytkownik może interakcyjnie przeprowadzić instalację typu wdrożenia, aby skonfigurować opcje instalacji.  

        > [!NOTE]  
        >  Ta opcja jest włączona domyślnie w przypadku wybrania **zainstaluj dla użytkownika** opcji **zachowanie podczas instalacji** listy rozwijanej.  

    -   **Maksymalny dozwolony czas wykonywania (w minutach)**— Podaj maksymalny czas, który program powinien być wykonywany na komputerze klienckim. To ustawienie musi być liczbą całkowitą większą niż zero. Domyślne ustawienie to 120 minut.  

         Ta wartość jest używana do:  

        -   Monitorowania wyników typu wdrożenia.  

        -   Sprawdź, czy typ wdrożenia zostanie zainstalowany, gdy na urządzeniach klienckich są zdefiniowane okna obsługi. Jeśli okno obsługi, program zostanie uruchomiony tylko wtedy, gdy jest wystarczająco dużo czasu jest dostępna w oknie obsługi, aby pomieścić **maksymalny dozwolony czas wykonywania** ustawienie.  

        > [!IMPORTANT]  
        >  Może wystąpić konflikt, jeśli **maksymalny dozwolony czas wykonywania** jest większa od czasu zaplanowanego okna obsługi. Jeśli maksymalny czas wykonywania ustawiony przez użytkownika będzie większy od długości każdego z dostępnych okien obsługi, typ wdrożenia nie zostanie uruchomiony.  

2.  **Szacowany czas instalacji (w minutach)**— Określ szacowany czas trwania instalacji typu wdrożenia. Ta informacja będzie wyświetlana użytkownikom Centrum oprogramowania.  

## <a name="specify-requirements-for-the-deployment-type"></a>Określenie wymagań dotyczących typu wdrożenia  

1.  Na **wymagania** strony kreatora tworzenia typu wdrożenia wybierz **Dodaj** otworzyć **tworzenie wymagania** okna dialogowego i Dodaj nowe wymaganie.  

    > [!NOTE]  
    >  Możesz także dodać nowe wymagania na **wymagania** karcie *< Nazwa typu wdrożenia\>*  **właściwości** okno dialogowe.  

2.  Z listy rozwijanej **Kategoria** wybierz, czy wymaganie dotyczy urządzenia, czy użytkownika, lub wybierz opcję **Niestandardowe**, aby użyć poprzednio utworzonego warunku globalnego. Po wybraniu **niestandardowy**, można także **Utwórz** Aby utworzyć nowy warunek globalny. Aby uzyskać więcej informacji o warunkach globalnych, zobacz [tworzenie warunków globalnych](../../apps/deploy-use/create-global-conditions.md).  

    > [!IMPORTANT]  
    >  Wszystkie wymagania należącego do kategorii **użytkownika** i warunku **urządzenie podstawowe** zostanie zignorowana, jeśli wdrożysz aplikację w kolekcji urządzeń.  
    >   
    >  Jeśli utworzono pakiet systemu Windows oraz program lub sekwencję zadań wymagającą systemu Windows 10 przy użyciu programu System Center 2012 R2 Configuration Manager SP1, a następnie dokonano aktualizacji programu System Center Configuration Manager, wymagania dotyczące systemu Windows 10 mogą zostać usunięte. Aby rozwiązać ten problem, należy ponownie określić wymagania. Należy pamiętać, że chociaż wymaganie został usunięty z wyświetlania wymagania, są nadal przetwarzane prawidłowo na urządzeniach.  

3.  W **warunku** listy rozwijanej wybierz warunek, którego chcesz użyć do oceny, czy użytkownik lub urządzenie spełnia wymagania instalacyjne. Zawartość tej listy różni się w zależności od wybranej kategorii.  

4.  W **Operator** listy rozwijanej wybierz operator, który zostanie użyty do porównania wybranego warunku z podaną wartością w celu oceny, czy użytkownik lub urządzenie spełnia wymagania instalacyjne. Dostępni operatorzy różnią się w zależności od wybranego warunku.  

    > [!IMPORTANT]  
    >  Dostępne wymagania będą się różnić w zależności od typu urządzenia, która używa typu wdrożenia.  

5.  W **wartość** określ wartości, które będą używane z wybranym warunkiem i Operator służący do oceny, czy użytkownik lub urządzenie spełnia wymagania instalacyjne. Dostępne wartości różnią się w zależności od wybranych warunku i operatora.  

6.  Wybierz **OK** Aby zapisać wymaganie i zamknąć **tworzenie wymagania** okno dialogowe.  

## <a name="specify-dependencies-for-the-deployment-type"></a>Określenie zależności dotyczących typu wdrożenia  
 Zależności definiują jeden lub więcej typów wdrożeń z innej aplikacji, którą należy zainstalować przed zainstalowaniem typu wdrożenia. Można ustawić zależnych typów wdrożeń można automatycznie zainstalować przed zainstalowaniem typu wdrożenia.  

> [!IMPORTANT]  
>  W niektórych przypadkach typ wdrożenia jest zależny od typu wdrożenia, który również ma zależności. Maksymalna liczba obsługiwanych zależności w łańcuchu wynosi pięć.  

1.  Na **zależności** strony kreatora tworzenia typu wdrożenia wybierz **Dodaj** Jeśli chcesz określić typy wdrożeń, które należy zainstalować przed zainstalowaniem tego typu wdrożenia.  

    > [!IMPORTANT]  
    >  Można także dodać nowe zależności na **zależności** karcie *< Nazwa typu wdrożenia\>*  **właściwości** okno dialogowe.  

2.  W **Dodawanie zależności** oknie dialogowym wybierz **Dodaj**.  

3.  W **Określ wymaganą aplikację** okno dialogowe, wybierz istniejącą aplikację i jedno wdrożenie aplikacji typów do użycia jako zależność.  

    > [!TIP]  
    >  Możesz wybrać **widoku** Aby wyświetlić właściwości wybranej aplikacji lub typu wdrożenia.  

4.  Wybierz **OK** zamknąć **Określ wymaganą aplikację** okno dialogowe.  

5.  Jeśli chcesz, aby aplikacja zależna była instalowana automatycznie, wybierz opcję **automatyczna instalacja** obok aplikacji.  

    > [!NOTE]  
    >  Aplikacja zależna nie trzeba wdrażać była instalowana automatycznie.  

6.  W **Dodawanie zależności** okno dialogowe, w obszarze **Nazwa grupy zależności**, wprowadź nazwę umożliwiającą odwoływanie się do tej grupy zależności aplikacji.  

7.  Można też użyć **Zwiększ priorytet** i **Zmniejsz priorytet** przycisków, aby zmienić kolejność, w jakiej są oceniane poszczególne zależności.  

8.  Wybierz **OK** zamknąć **Dodawanie zależności** okno dialogowe.  

## <a name="confirm-the-deployment-type-settings-and-finish-the-wizard"></a>Potwierdzenie ustawień typu wdrożenia i Zakończ pracę kreatora  

1.  Na **Podsumowanie** strony kreatora tworzenia typu wdrożenia Przejrzyj akcje wykonywane przez kreatora. Wybierz **dalej** do utworzenia typu wdrożenia, lub wybierz **Wstecz** aby wrócić i zmienić ustawienia typu wdrożenia.  

2.  Po **postępu** Przejrzyj akcje wykonane przez kreatora, a następnie wybierz pozycję zakończenie, **Zamknij** aby zakończyć pracę kreatora.  

3.  Jeśli Kreator tworzenia typu wdrożenia został uruchomiony z Kreatora tworzenia aplikacji, nastąpi powrót do **typy wdrożeń** strony kreatora tworzenia aplikacji.  

## <a name="set-up-additional-options-for-deployment-types-that-contain-virtual-applications"></a>Konfigurowanie dodatkowych opcji typów wdrożeń zawierających aplikacje wirtualne  
 Poniższe procedury umożliwiają konfigurowanie dodatkowych opcji typów wdrożeń zawierających aplikacje wirtualne.  

### <a name="set-up-content-options-for-application-virtualization-app-v-deployment-types"></a>Ustaw opcje zawartości dla typów wdrożeń Application Virtualization (App-V)  

1.  W konsoli programu Configuration Manager wybierz **Biblioteka oprogramowania** > **aplikacji**.  

2.  W **aplikacji** listy, wybierz aplikację, która ma typ wdrożenia programu App-V. Następnie na **Home** karcie **właściwości** grupy, wybierz **właściwości**.  

3.  W *< nazwa aplikacji\>*  **właściwości** na okna dialogowego **typy wdrożeń** karcie, wybierz typ wdrożenia programu App-V, a następnie wybierz **Edytuj**.  

4.  W *< Nazwa typu wdrożenia\>*  **właściwości** na okna dialogowego **zawartości** kartę, skonfiguruj następujące opcje, jeśli jest to wymagane:  

    -   **Utrwal zawartość w pamięci podręcznej klienta**— wybierz tę opcję, aby upewnić się, że zawartość dla tego typu wdrożenia nie zostanie usunięta z pamięci podręcznej klienta programu Configuration Manager.  

    -   **Załaduj zawartość do pamięci podręcznej programu App-V przed uruchomieniem**— wybierz tę opcję, aby upewnić się, że cała zawartość dla aplikacji wirtualnej zostanie załadowana do pamięci podręcznej programu App-V przed uruchomieniem aplikacji. Zaznaczenie tej opcji gwarantuje również, że zawartość aplikacji nie jest przypięty w pamięci podręcznej i można je usunąć zgodnie z wymaganiami.  

5.  Wybierz **OK** zamknąć *< Nazwa typu wdrożenia\>*  **właściwości** okno dialogowe.  

6.  Wybierz **OK** zamknąć *< nazwa aplikacji\>*  **właściwości** okno dialogowe.  

### <a name="set-up-publishing-options-for-app-v-deployment-types"></a>Ustawianie opcji typów wdrożeń App-V publikowania  

1.  W konsoli programu Configuration Manager wybierz **Biblioteka oprogramowania** > **aplikacji**.  

3.  W **aplikacji** listy, wybierz aplikację, która ma typ wdrożenia programu App-V. Następnie na **Home** karcie **właściwości** grupy, wybierz **właściwości**.  

4.  W *< nazwa aplikacji\>*  **właściwości** na okna dialogowego **typy wdrożeń** karcie, wybierz typ wdrożenia programu App-V, a następnie wybierz **Edytuj**.  

5.  W *< Nazwa typu wdrożenia\>*  **właściwości** na okna dialogowego **publikowania** , a następnie wybierz elementy aplikacji wirtualnej, który chcesz opublikować.  

6.  Wybierz **OK** zamknąć *< Nazwa typu wdrożenia\>*  **właściwości** okno dialogowe.  

7.  Wybierz **OK** zamknąć *< nazwa aplikacji\>*  **właściwości** okno dialogowe.  

## <a name="import-an-application"></a>Importuj aplikację  
 Użyj poniższej procedury, aby zaimportować aplikację do programu Configuration Manager. Aby uzyskać informacje o sposobie eksportowania aplikacji, zobacz [zadania zarządzania dla aplikacji programu System Center Configuration Manager](../../apps/deploy-use/management-tasks-applications.md).  

1.  W konsoli programu Configuration Manager wybierz **Biblioteka oprogramowania** > **Zarządzanie aplikacjami** > **aplikacji**.   

3.  Na **Home** karcie **Utwórz** grupy, wybierz **Importuj aplikację**.  

4.  Na **ogólne** strony **Kreatora importowania aplikacji**, wybierz **Przeglądaj**, a następnie określ ścieżkę UNC do pliku zip, który ma aplikacji do zaimportowania.  

5.  Na **zawartość pliku** wybierz akcję, która będzie wykonywana, gdy aplikację, którą próbowano zaimportować jest duplikatem istniejącej aplikacji. Możesz utworzyć nową aplikację lub zignorować duplikat i dodać nową poprawkę do istniejącej aplikacji.  

6.  Na **Podsumowanie** Przejrzyj akcje wykonywane, a następnie Zakończ pracę kreatora.  

 Nowa aplikacja pojawi się w węźle **Aplikacje**.  

> [!TIP]  
>  Polecenia cmdlet programu Windows PowerShell **Export-CMApplication** ma taką samą funkcję jak tej procedury. Aby uzyskać więcej informacji, zobacz [Export-CMApplication](https://technet.microsoft.com/library/jj821738.aspx) w Microsoft System Center 2012 Configuration Manager z dodatkiem SP1 Cmdlet Reference.  

##  <a name="deployment-types-supported-by-configuration-manager"></a>Typy wdrożeń obsługiwane przez program Configuration Manager  

|Nazwa typu wdrożenia|Więcej informacji|  
|--------------------------|----------------------|  
|**Instalator systemu Windows (\*pliku .msi)**|Tworzy typ wdrożenia na podstawie pliku Instalatora systemu Windows.|  
|**Pakiet aplikacji systemu Windows (\*appx, \*.appxbundle)**|Tworzy typ wdrożenia dla systemu operacyjnego Windows 8 lub Windows RT albo nowszego na podstawie pliku pakietu aplikacji systemu Windows lub pakietu zbioru aplikacji systemu Windows.|  
|**Pakiet aplikacji systemu Windows (w Sklepie Windows)**|Tworzy typ wdrożenia dla systemu Windows 8, Windows RT lub nowszego przez określenie linku do aplikacji w Sklepie Windows lub przejrzenie sklepu i wskazanie wymaganej aplikacji, które są wymagane.<br /><br /> Jeśli chcesz wdrożyć aplikację jako łącze do Sklepu Windows, upewnij się, że ustawienie zasad grupy **Wyłącz aplikację sklep** ustawiono **wyłączone** lub **nieskonfigurowane**. Jeśli to ustawienie jest włączone, klienci nie będą mogli połączyć się ze Sklepem Windows w celu pobrania i zainstalowania aplikacji.<br /><br /> Typy wdrożeń systemu Windows 8 korzystające z linku do sklepu są zawsze oceniane przed innymi typami wdrożeń, niezależnie od ich priorytetu.|  
|**Instalator skryptowy**|Tworzy typ wdrożenia określający skrypt uruchamiany na urządzeniach klienckich w celu zainstalowania zawartości lub wykonaj akcję.|  
|**Microsoft Application Virtualization 4**|Tworzy typ wdrożenia na podstawie manifestu aplikacji Microsoft Application Virtualization 4|  
|**Microsoft Application Virtualization 5**|Tworzy typ wdrożenia na podstawie pliku pakietu aplikacji Microsoft Application Virtualization 5.|  
|**Pakiet aplikacji Windows Phone (\*plik xap)**|Tworzy typ wdrożenia na podstawie pliku pakietu aplikacji systemu Windows Phone.|  
|**Pakiet aplikacji Windows Phone (w Sklepie Windows Phone)**|Tworzy typ wdrożenia przez określenie linku do aplikacji w sklepie Windows Phone Store.|  
|**Przenośne pliku Cabinet systemu Windows**|Tworzy typ wdrożenia dla urządzeń z systemem Windows Mobile na podstawie pliku cabinet systemu Windows Mobile (CAB).|  
|**Pakiet aplikacji dla systemu iOS (\*plik IPA)**|Tworzy typ wdrożenia na podstawie pliku pakietu aplikacji dla systemu iOS.|  
|**Pakiet aplikacji dla systemu iOS ze sklepu z aplikacjami**|Tworzy typ wdrożenia za pośrednictwem łącza do aplikacji dla systemu iOS ze sklepu App Store.|  
|**Pakiet aplikacji dla systemu Android (\*pliku apk)**|Tworzy typ wdrożenia na podstawie pliku pakietu aplikacji dla systemu Android.|  
|**Pakiet aplikacji dla systemu Android w witrynie Google Play**|Tworzy typ wdrożenia za pośrednictwem łącza do aplikacji w witrynie Google Play.|  
|**Mac OS X**|Tworzy typ wdrożenia dla komputerów Mac na podstawie pliku *.cmmac, który został utworzony przy użyciu narzędzia CMAppUtil.<br /><br /> Dotyczy tylko na komputerach Mac, na którym jest uruchomiony klient programu Configuration Manager.|  
|**Aplikacja sieci Web**|Tworzy typ wdrożenia określający łącze do aplikacji sieci web. Typ wdrożenia instaluje skrót do aplikacji sieci web na urządzeniu użytkownika.<br /><br /> Po zainstalowaniu programu Intune managed browser dla systemu iOS lub urządzeń z systemem Android, którymi zarządzasz, można zapewnić, że użytkowników tylko przy użyciu programu managed browser do otwarcia aplikacji. Aby to zrobić, należy użyć jednej z następujących formatów wystarczy podać link do aplikacji przez zastąpienie **http:** z **http-intunemam:** lub **https:** z **https-intunemam:**<br /><br /> - **http-intunemam: / / < ścieżka do aplikacji sieci web\>**<br /><br /> - **HTTPS-intunemam: / / < ścieżka do aplikacji sieci web\>**<br /><br /> Aby upewnić się, że aplikacje, które chcesz skojarzyć z przeglądarką zarządzaną są instalowane tylko na urządzeń iOS i Android, można użyć wymagań aplikacji programu Configuration Manager.<br /><br /> Aby uzyskać więcej informacji o usłudze Intune managed browser, zobacz [Zarządzanie Internetu dostępu za pomocą zasad programu managed browser](../../apps/deploy-use/manage-internet-access-using-managed-browser-policies.md).|  
|**Instalator Windows korzystający z zarządzania urządzeniami Przenośnymi (\*.msi)**|Ten typ Instalatora umożliwia tworzenie i wdrażanie aplikacji opartych na Instalatorze Windows na komputerach z systemem Windows 10.<br /><br /> W przypadku korzystania z instalatora tego typu należy wziąć pod uwagę następujące kwestie:<br><br>-Należy przekazać tylko pojedynczy plik z rozszerzeniem msi.<br /><br /> Kod produktu i wersja produktu pliku są używane do wykrywania aplikacji.<br /><br /> Domyślne zachowanie ponownego uruchamiania aplikacji będą używane. Menedżer konfiguracji nie jest to kontrolowane.<br /><br /> -Dla pojedynczego użytkownika zostaną zainstalowane pakiety MSI poszczególnych użytkowników.<br /><br /> Dla wszystkich użytkowników urządzenia zostaną zainstalowane pakiety MSI na maszynach.<br /><br /> -Pakiety MSI podwójne obecnie instalować tylko dla wszystkich użytkowników na urządzeniu.<br /><br /> — Aktualizacje aplikacji są obsługiwane, jeśli kod produktu MSI dla każdej wersji jest taki sam.|  
