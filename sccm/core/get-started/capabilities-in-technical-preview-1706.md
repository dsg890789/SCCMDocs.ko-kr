---
title: Technical Preview 1706 | Dokumentacja firmy Microsoft
description: "Dowiedz się więcej o funkcjach dostępnych w wersji zapoznawczej Technical Preview 1706 programu System Center Configuration Manager."
ms.custom: na
ms.date: 06/30/2017
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ca3b4714-2a16-495e-8a17-1d87991d5556
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: d45f504dfe0a4c7852b0e2c8ff60d54005346c02
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="capabilities-in-technical-preview-1706-for-system-center-configuration-manager"></a>Funkcje w wersji Technical Preview 1706 programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (wersja zapoznawcza Technical Preview)*

W tym artykule przedstawiono funkcje, które są dostępne w wersji Technical Preview programu System Center Configuration Manager, wersja 1706. Można zainstalować tę wersję, aby zaktualizować i dodać nowe funkcje do lokacji programu Configuration Manager technical preview. Przed zainstalowaniem tej wersji technical Preview, przejrzyj [Technical Preview programu System Center Configuration Manager](../../core/get-started/technical-preview.md) zapoznać się z ogólne wymagania i ograniczenia dotyczące używania wersji technical preview, jak zaktualizować między wersjami i sposobu wyrazić swoją opinię na temat funkcji w wersji technical preview.     


<!--  Known Issues Template   
**Known Issues in this Technical Preview:**
-   **Issue Name**. Details
    Workaround details.
-->
**Znane problemy w tej wersji Technical Preview:**

-   **Przenieś punkt dystrybucji** — nie można użyć opcji w konsoli, aby przenieść punkt dystrybucji między lokacjami w tej wersji z powodu ograniczenia wersji zapoznawczej technical preview z jednej lokacji głównej.

-   **Ustawienia zgodności urządzeń** -przeciwną zachowanie mogą wystąpić przy użyciu dwa nowe ustawienia zgodności urządzeń:
    - **Blokuj debugowanie USB na urządzeniu**
    - **Blokuj aplikacji z nieznanych źródeł**

        Na przykład, jeśli ustawiona Administratorzy **debugowanie USB bloku na urządzeniu** do **true**, wszystkie urządzenia, które nie mają włączonej obsługi debugowania USB są oznaczone jako niezgodne.

**Poniżej przedstawiono nowe funkcje, które można wypróbować z tą wersją.**  

<!--  Rough Section Template
##  FEATURE

### Procedure 1
### Try it out!  
 Try to complete the following tasks and then send us **Feedback** from the **Home** tab of the Ribbon to let us know how it worked:
 -  Task 1
 -  Task 2              
-->

## <a name="improved-boundary-groups-for-software-update-points"></a>Grupy granic ulepszone dla punktów aktualizacji oprogramowania
<!-- 1324591 -->
Ta wersja zawiera ulepszenia działania punktów aktualizacji oprogramowania z grupy granic. Poniżej przedstawiono podsumowanie nowe działanie rezerwowe:
-   Używane dla punktów aktualizacji oprogramowania używa teraz można skonfigurować czas powrotu do grup granic sąsiada, minimalny czas 120 minut.

-   Niezależne od konfiguracji rezerwowej, klient próbuje osiągnąć ostatniego punktu aktualizacji oprogramowania używanych przez 120 minut. Po nieudanym do tego serwera na 120 minut, klient sprawdzi puli punktów aktualizacji oprogramowania, aby umożliwić znalezienie nowy.

  -   Wszystkie punkty aktualizacji oprogramowania w bieżącej grupie granic klienta są dodawane do puli klienta natychmiast.

  -   Ponieważ klient próbuje użyć oryginalnego serwera na 120 minut przed znalezienia nowy, żadne dodatkowe serwery kontaktować się ze dopiero po upływie dwóch godzin.

  -   Jeśli powrotu do grupy sąsiada jest skonfigurowana co najmniej 120 minut, punkty aktualizacji oprogramowania z tej grupy granic sąsiada będzie częścią puli klienta dostępnych serwerów.

-   Po awarii do oryginalnego serwera przez 2 godziny, klient przełącza się do krótszej cykl w celu kontaktowania się nowego punktu aktualizacji oprogramowania.

    Oznacza to, jeśli klient nie może nawiązać połączenia z nowym serwerze, szybko wybiera kolejny serwer z puli serwerów dostępnych i próbuje skontaktować się z co.

  -   Ten cykl będzie wykonywany do momentu klient łączy się oprogramowania może użyć punktu aktualizacji.
  -   Dopóki klient znajdzie punkt aktualizacji oprogramowania, dodatkowe serwery są dodawane do puli serwerów dostępnych po spełnieniu rezerwowy czasu dla każdej grupy granic sąsiedniego.

Aby uzyskać więcej informacji, zobacz [punktów aktualizacji oprogramowania](/sccm/core/servers/deploy/configure/boundary-groups#software-update-points) w temacie grup granic dla bieżącej gałęzi.


## <a name="site-server-role-high-availability"></a>Wysoką dostępność roli serwera lokacji
<!-- 1128774 -->
Wysoka dostępność dla roli serwera lokacji jest rozwiązania na podstawie programu Configuration Manager do zainstalowania serwera lokacji głównej w *pasywnym* tryb. Serwer lokacji w trybie pasywnym jest dodatkowo do istniejącego serwera lokacji głównej w *Active* tryb. W trybie pasywnym serwera lokacji jest dostępna do użycia, w razie potrzeby.

Serwer lokacji podstawowej w trybie pasywnym:
-   Używa tej samej bazy danych lokacji, co serwer aktywnej lokacji.
-   Odbiera kopii aktywnej lokacji serwery biblioteki zawartości, który jest przechowywany następnie zsynchronizowany.
-   Nie zapisuje dane do bazy danych lokacji, tak długo, jak jest w trybie pasywnym.
-   Nie obsługuje instalacji lub usunięcia opcjonalne role systemu lokacji tak długo, jak jest w trybie pasywnym.

Aby serwer lokacji w trybie pasywnym aktywny tryb serwera lokacji, należy ręcznie Podwyższ go. Przełącza się na serwer aktywnej lokacji serwer lokacji pasywnych. Role systemu lokacji, które są dostępne na oryginalnym serwerze w trybie aktywnym pozostają dostępne pod warunkiem, że komputer jest dostępny. Rola serwera lokacji przełączania między trybem aktywnych i pasywnych.

Aby zainstalować serwer lokacji w trybie pasywnym, należy użyć **lokacji Kreator tworzenia serwera systemu** do skonfigurowania nowego serwera lokacji z typem **serwera lokacji głównej** i tryb **pasywnym**. Następnie Kreator uruchamia Instalator programu Configuration Manager na określonym serwerze, aby zainstalować nowy serwer lokacji w trybie pasywnym. Po zakończeniu instalacji serwera lokacji w trybie aktywnym zachowuje w trybie pasywnym serwera lokacji i jej do biblioteki zawartości zsynchronizowane z zmiany lub konfiguracje, które można wprowadzić na serwerze aktywnej lokacji.

### <a name="prerequisites-and-limitations"></a>Wymagania wstępne i ograniczenia
-   Jednym serwerze lokacji w trybie pasywnym jest obsługiwane w każdej lokacji głównej.

-   Serwer lokacji w trybie pasywnym może być lokalnym lub w chmurze na platformie Azure.

-   Zarówno w trybie aktywnym, jak i serwerów lokacji w trybie pasywnym musi być w tej samej domenie.

-   Zarówno w trybie aktywnym, jak i serwerów lokacji w trybie pasywnym musi używać tej samej bazy danych lokacji, który musi być zdalnego z komputerów wszystkich serwerów lokacji.

    -   SQL Server obsługującym bazę danych można użyć domyślnego wystąpienia o nazwie wystąpienia klastra programu SQL Server i zawsze włączonej grupy dostępności.

    -   Aby użyć tej samej bazy danych lokacji jako aktywny tryb serwera lokacji jest skonfigurowany serwer lokacji, w trybie pasywnym. Jednak serwer lokacji w trybie pasywnym nie używa tej bazy danych do czasu po jest podwyższany do aktywnego trybu.

-   Komputer, który zostanie uruchomiony w trybie pasywnym serwera lokacji:

    -   Musi spełniać [wymagania wstępne dotyczące instalowania lokacji głównej](https://docs.microsoft.com/en-us/sccm/core/servers/deploy/install/prerequisites-for-installing-sites#primary-sites-and-the-central-administration-site).

    -   Instaluje przy użyciu plików źródłowych odpowiadających wersji serwera lokacji w trybie aktywnym.

    -   Nie może mieć roli systemu lokacji z dowolnej lokacji przed zainstalowaniem lokacji w trybie pasywnym.

-   Komputerach serwera lokacji w trybie aktywnym i pasywnym można uruchomić w różnych systemach operacyjnych lub wersji dodatku service pack, tak długo, jak mogą w dalszym ciągu obsługiwany przez używaną wersję programu Configuration Manager.

-   Podwyższanie poziomu serwera lokacji w trybie pasywnym trybie aktywnym serwerem jest ręcznie. Nie ma żadnych automatycznej pracy awaryjnej.

-   Role systemu lokacji można zainstalować tylko na serwerze lokacji, który jest w trybie aktywnym.

    -   Serwer lokacji w trybie aktywnym obsługuje wszystkie role systemu lokacji. Nie można zainstalować role systemu lokacji na serwerze, gdy jest on w trybie pasywnym.

    -   Role systemu lokacji, które używają bazy danych (na przykład punkt raportowania) musi mieć tej bazy danych na serwerze, na którym znajduje się poza zarówno aktywny tryb i serwery lokacji w trybie pasywnym.

    -   Element SMS_Provider nie spowoduje zainstalowania na serwerze lokacji w trybie pasywnym. Należy nawiązać połączenie SMS_Provider witryny na ręczne podwyższenie poziomu serwera lokacji w trybie pasywnym na tryb aktywny, dlatego zaleca się [zainstalowanie co najmniej jednego dodatkowego wystąpienia dostawcy](/sccm/core/plan-design/hierarchy/plan-for-the-sms-provider) na dodatkowych komputerach.

**Znany problem**:   
W tej wersji **stan** dla następujące warunki są wyświetlane w konsoli jako wartości liczbowe zamiast tekstu do odczytu:
-   131071 — nie można zainstalować serwera lokacji
-   720895 — Dezinstalacja roli serwera lokacji nie powiodła się
-   851967 — trybu Failover nie powiodła się.

### <a name="add-a-site-server-in-passive-mode"></a>Dodawanie serwera lokacji w trybie pasywnym
1.  W konsoli przejdź do **administracji** > **konfiguracja lokacji** > **witryny** i uruchomić [lokacji Kreator dodawania ról systemu](/sccm/core/servers/deploy/configure/install-site-system-roles). Można również użyć **lokacji Kreator tworzenia serwera systemu**.

2.  Na **ogólne** Określ serwer, który będzie hostować serwer lokacji w trybie pasywnym. Serwer, z którym określisz nie może obsługiwać wszystkie role systemu lokacji, przed zainstalowaniem serwera lokacji w trybie pasywnym.

3.  Na **Wybór roli systemu** wybierz tylko **serwera lokacji głównej w trybie pasywnym**.

4.  Aby ukończyć pracę kreatora, należy podać następujące informacje, które służy do uruchamiania Instalatora i zainstaluj rolę serwera lokacji na określonym serwerze:
    -   Skopiuj pliki instalacyjne z serwera aktywnej lokacji do nowego serwera lokacji w trybie pasywnym, lub określ ścieżkę do lokalizacji, która zawiera zawartość serwera aktywnej lokacji **dysku CD. Najnowsze** folderu.

    -   Określ tego samego serwera bazy danych lokacji i nazwa bazy danych używane przez serwer lokacji w trybie aktywnym.

5.  Configuration Manager instaluje serwer lokacji w trybie pasywnym na określonym serwerze.

Stan instalacji szczegółowe, przejdź do **administracji** > **konfiguracja lokacji** > **witryny**.
-   Wyświetla stan serwera lokacji w trybie pasywnym jako **instalowanie**.

-   Wybierz serwer, a następnie kliknij przycisk **Pokaż stan** otworzyć **stan instalacji serwera lokacji** więcej szczegółowych informacji.



### <a name="promote-the-passive-mode-site-server-to-active-mode"></a>Serwer lokacji w trybie pasywnym na tryb aktywny
Jeśli chcesz zmienić serwer w trybie pasywnym na tryb aktywny, możesz to zrobić z **węzłów** okienka w **administracji** > **konfiguracja lokacji** > **witryny**. Tak długo, jak można uzyskać dostęp do wystąpienia element SMS_Provider, można uzyskać dostępu do witryny, aby wprowadzić tę zmianę.
1.  W **węzłów** okienku konsoli programu Configuration Manager, wybierz serwer lokacji w trybie pasywnym, a następnie na Wstążce wybierz **Podnieś poziom aktywny**.

2.  Prosty **stan** dla serwera podwyższasz wyświetla w **węzłów** okienko jako **promowanie**.

3.  Po zakończeniu podwyższenia poziomu **stan** przedstawia kolumny **OK** dla obu nowego *Active* tryb serwera lokacji i nowy *pasywnym* tryb serwera lokacji.

4.  W **administracji** > **konfiguracja lokacji** > **witryny**, nazwę serwera lokacji głównej zawiera teraz nazwę nowej *Active* tryb serwera lokacji.
Aby uzyskać szczegółowe informacje o tym, **monitorowanie** > **stan serwera lokacji**.
    -   **Tryb** kolumny identyfikuje serwer, który jest *Active* lub *pasywnym*.

    -   Podczas podwyższania poziomu serwera w trybie pasywnym na tryb aktywny, wybierz serwer lokacji, które są podwyższania poziomu aktywny, a następnie wybierz **Pokaż stan** na Wstążce. Spowoduje to otwarcie **stan podwyższania poziomu serwera lokacji** okna dodatkowych szczegółów na temat procesu.

Serwer lokacji w trybie aktywnym przełącza na tryb pasywny, się pasywnym Rola systemu lokacji. Wszystkie inne role systemu lokacji zainstalowanych na tym komputerze pozostają aktywne i dostępne dla klientów.


### <a name="daily-monitoring"></a>Codziennie monitorowania
Jeśli masz lokacji głównej w trybie pasywnym, należy go monitorować codziennie, aby upewnić się, że pozostaje w trybie aktywnym serwera lokacji i gotowe do użycia. Aby to zrobić, przejdź do **monitorowanie** > **stan serwera lokacji**. W tym miejscu można wyświetlić zarówno w trybie aktywnym, jak i serwerów lokacji w trybie pasywnym.

**Podsumowanie** karty:
-   **Tryb** kolumny identyfikuje serwer, który jest aktywny i pasywne.
-   **Stan** kolumny list **OK** gdy serwer w trybie pasywnym jest zsynchronizowane z serwerem trybie aktywnym.
-   Aby wyświetlić dodatkowe informacje o stanie synchronizacji zawartości, kliknij przycisk **Pokaż stan** ze stanu synchronizacji zawartości. Spowoduje to otwarcie karty Biblioteka zawartości, której możesz spróbować rozwiązać problemy z synchronizacją zawartości.

**Biblioteki zawartości** karty:
-   Widok **stanu** zawartości, który jest synchronizowany z serwera lokacji aktywny na serwerze lokacji w trybie pasywnym.
-   Można wybrać zawartości ze stanem ****, a następnie wybierz pozycję **Synchronizuj wybrane elementy** na Wstążce. Ta akcja próbuje ponownie zsynchronizować tę zawartość ze źródła zawartości na serwerze lokacji w trybie pasywnym. Podczas odzyskiwania, stan jest wyświetlany jako **w toku**, i gdy jest ona zsynchronizowana, wyświetlane jako **Powodzenie**.

### <a name="try-it-out"></a>Wypróbuj
Spróbuj wykonać następujące zadania, a następnie wyślij do nas **opinii** z **Home** kartę na Wstążce, aby poinformować nas, jak Ci poszło:
-   Lokację główną można zainstalować w trybie pasywnym.
-   I podwyższyć poziom serwera lokacji w trybie pasywnym, aby stał się aktywny tryb serwera lokacji przy użyciu konsoli i Potwierdź zmianę stanu dla obu serwerów lokacji.


## <a name="include-trust-for-specific-files-and-folders-in-a-device-guard-policy"></a>Obejmują zaufania dla określonych plików i folderów w zasadach ochrony urządzeń
<!-- 1324676 -->
W tej wersji dodano więcej możliwości [ochrony urządzeń](/sccm/protect/deploy-use/use-device-guard-with-configuration-manager) Zarządzanie zasadami

Teraz można opcjonalnie dodawać zaufania dla określonych plików, folderów w zasadach ochrony urządzeń. Dzięki temu można:

1.  Rozwiązać problemy za pomocą zachowań zarządzanych Instalatora
2.  Zaufanie aplikacji z biznesowych, których nie można wdrożyć z programu Configuration Manager
3.  Zaufanie aplikacji, które są objęte obrazu wdrożenia systemu operacyjnego.

### <a name="try-it-out"></a>Wypróbuj

1.  Podczas tworzenia zasad ochrony urządzeń, na karcie dołączenia Kreatora zasad tworzenia ochrony urządzeń, kliknij przycisk **Dodaj**.
2.  W **Dodawanie zaufanego pliku lub folderu** okna dialogowego wprowadź informacje o pliku lub folderu, który ma zostać zaufania. Można określić ścieżkę lokalną pliku lub folderu lub połączyć do zdalnego urządzenia, do którego masz uprawnienia do połączenia i określ ścieżkę pliku lub folderu na tym urządzeniu.
3.  Ukończ pracę kreatora.


## <a name="hide-task-sequence-progress"></a>Ukryj postęp sekwencji zadań
<!-- 1354291 -->
W tej wersji możesz kontrolować termin jego postęp sekwencji zadań jest wyświetlana dla użytkowników końcowych za pomocą nowej zmiennej. W sekwencji zadań, użyj **Ustaw zmienną sekwencji zadań** krok, aby ustawić wartość **TSDisableProgressUI** zmiennej, aby ukryć lub wyświetlić postęp sekwencji zadań. Służy Ustaw zmienną sekwencji zadań krok wiele razy w sekwencji zadań można zmienić wartości dla zmiennej. Dzięki temu można ukrywać lub wyświetlać postęp sekwencji zadań w różne sekcje sekwencji zadań.

#### <a name="to-hide-task-sequence-progress"></a>Aby ukryć postęp sekwencji zadań
W edytorze sekwencji zadań, użyj [Ustaw zmienną sekwencji zadań](/sccm/osd/understand/task-sequence-steps#BKMK_SetTaskSequenceVariable) krok, aby ustawić wartość **TSDisableProgressUI** zmienną **True** ukrycia postęp sekwencji zadań.

#### <a name="to-display-task-sequence-progress"></a>Aby wyświetlić postęp sekwencji zadań
W edytorze sekwencji zadań, użyj [Ustaw zmienną sekwencji zadań](/sccm/osd/understand/task-sequence-steps#BKMK_SetTaskSequenceVariable) krok, aby ustawić wartość **TSDisableProgressUI** zmienną **False** Aby wyświetlić postęp sekwencji zadań.

## <a name="specify-a-different-content-location-for-install-content-and-uninstall-content"></a>Określ inną lokalizację zawartości dla zawartości instalacji i odinstalowywania zawartości
<!-- 1097546 -->
W programie Configuration Manager dzisiaj, można określić lokalizacji instalacji, który zawiera pliki instalacyjne aplikacji. Po określeniu lokalizacji instalacji to również służy jako lokalizacji Odinstaluj zawartości aplikacji.
Na podstawie opinii, gdy chcesz odinstalować wdrożonej aplikacji i zawartość aplikacji nie znajduje się na komputerze klienckim, następnie klient pobierze wszystkie pliki instalacyjne aplikacji ponownie, zanim aplikacja zostanie odinstalowana.
Aby rozwiązać ten problem, można teraz określić zarówno instalację zawartości, lokalizacji i opcjonalnie odinstalować lokalizacji zawartości. Ponadto można nie określić lokalizację zawartości Odinstaluj.

### <a name="try-it-out"></a>Wypróbuj

1. We właściwościach typu wdrożenia aplikacji, kliknij przycisk **zawartości** kartę.
2. Skonfiguruj **zainstalować lokalizacji zawartości** normalnego.
3. Aby uzyskać **odinstalować ustawienia zawartości**, wybierz jedną z następujących czynności:
    - **Taka sama, jak zainstalować zawartość** — tej samej lokalizacji zawartości będzie używany niezależnie od tego, czy podczas instalowania lub odinstalowywania aplikacji.
    - **Brak zawartości Odinstaluj** — wybierz tę opcję, jeśli nie chcesz podać Odinstaluj lokalizacji zawartości dla aplikacji.
    - **Inna niż instalacja zawartości** — wybierz tę opcję, jeśli chcesz określić Odinstaluj lokalizacji zawartości, która różni się od lokalizacji instalacji zawartości.
5. W przypadku wybrania **różne od instalacji zawartości**, przejdź do, lub wprowadź lokalizację zawartości aplikacji, która będzie służyć do odinstalowania aplikacji.
6. Kliknij przycisk **OK** aby zamknąć okno dialogowe właściwości typu wdrożenia.


## <a name="accessibility-improvements"></a>Ulepszenia ułatwień dostępu  
<!--1253000 -->
Tej wersji zapoznawczej wprowadzono kilka ulepszeń [funkcje ułatwień dostępu](/sccm/core/understand/accessibility-features) w konsoli programu Configuration Manager. Należą do nich następujące elementy:     

**Nowe skróty klawiaturowe do przenoszenia konsoli:**
-   CTRL + M - zestawy skupić się w okienku głównym (centralna).
-   CTRL + T - ustawia okno górny węzeł w okienku nawigacji. Jeśli fokus znajduje się już w tym okienku, fokus jest ustawiona na ostatni węzeł odwiedzonych.
-   CTRL + I - zestawy fokus na pasek stron nadrzędnych poniżej Wstążki.
-   CTRL + L - ustawia okno **wyszukiwania** pola, jeśli jest dostępna.
-   CTRL + D - fokus zestawów do okienka szczegółów, jeśli jest dostępna.
-   ALT — zmiany fokusu i Wstążki.

**Ogólne ulepszenia:**
-   Ulepszona nawigacji w okienku nawigacji po wpisaniu liter nazwy węzła.
-   Nawigacji klawiatury za pośrednictwem widoku głównego i wstążki są teraz cykliczne.
-   Nawigacji klawiatury w okienku szczegółów jest teraz cykliczne. Aby powrócić do poprzedniego obiektu lub okienko, użyj klawiszy Ctrl + D, a następnie Shift + TAB.
-   Po odświeżeniu widoku obszaru roboczego, fokus jest ustawiony w okienku głównym tego obszaru roboczego.
-   Rozwiązano problem umożliwiające czytników ekranu zawiera informacje o nazwach elementów listy.
-   Dodano nazw dostępnych dla wielu formantów strony, który umożliwia czytników ekranu zawiera informacje o ważnych informacji.


## <a name="changes-to-the-azure-services-wizard-to-support-upgrade-readiness"></a>Zmiany w Kreatorze usług Azure do obsługi gotowości do uaktualnienia
<!-- 1353331 -->
Począwszy od tej wersji, użyj Kreatora usługi Azure do skonfigurowania połączenia z programu Configuration Manager do [gotowości do uaktualnienia](/sccm/core/clients/manage/upgrade/upgrade-analytics). Użyj Kreatora upraszcza konfigurację łącznika, za pomocą Kreatora wspólne dla usług Azure powiązane.   

Mimo że zmieniono metodę, aby skonfigurować połączenie, wymagania wstępne dotyczące połączenia i sposobie korzystania z gotowości do uaktualnienia pozostają niezmienione.   

### <a name="prerequisites-for-upgrade-readiness"></a>Wymagania wstępne dotyczące gotowości do uaktualnienia
Wymagania wstępne dotyczące [połączenie gotowości do uaktualnienia](/sccm/core/clients/manage/upgrade/upgrade-analytics#create-a-connection-to-upgrade-readiness) uległy zmianie w porównaniu szczegółowe dla bieżącej gałęzi programu Configuration Manager. Są one powtarzane tutaj dla wygody:  

**Wymagania wstępne**
-   Aby dodać połączenie, najpierw należy skonfigurować środowiska programu Configuration Manager [punkt połączenia z usługą](/sccm/core/servers/deploy/configure/about-the-service-connection-point) w [trybu online](/sccm/core/servers/deploy/configure/about-the-service-connection-point#a-namebkmkmodesa-modes-of-operation). Po dodaniu połączenia ze środowiskiem go spowoduje także zainstalowanie programu Microsoft Monitoring Agent na komputerze, na którym działa ta rola systemu lokacji.
-   Zarejestruj programu Configuration Manager jako narzędzie do zarządzania "API sieci Web i/lub aplikacji sieci Web" oraz możliwość uzyskania [identyfikator klienta z tej rejestracji](https://azure.microsoft.com/documentation/articles/active-directory-integrating-applications/).
-   Utwórz klucz klienta dla zarejestrowanego narzędzia do zarządzania w usłudze Azure Active Directory.
-   W portalu zarządzania Azure, podaj aplikacji sieci web w zarejestrowany z uprawnieniami do OMS, zgodnie z opisem w [Podaj programu Configuration Manager z uprawnieniami do OMS](https://azure.microsoft.com/documentation/articles/log-analytics-sccm/#provide-configuration-manager-with-permissions-to-oms).

> [!IMPORTANT]       
> Podczas konfigurowania uprawnień dostępu OMS, należy wybrać **współautora** roli i przypisz mu uprawnienia do grupy zasobów w zarejestrowany aplikacji.

Po skonfigurowaniu wymagań wstępnych, można przystąpić do utworzenia połączenia za pomocą kreatora.

### <a name="use-the-azure-services-wizard-to-configure-upgrade-readiness"></a>Użyj kreatora usług Azure, aby skonfigurować gotowości do uaktualnienia
1.  W konsoli przejdź do **administracji** > **omówienie** > **usługi w chmurze** > **usług Azure**, a następnie wybierz **Konfigurowanie usług Azure** z **Home** karty wstążki, aby uruchomić **Kreator usług Azure**.

2.  Na **usług Azure** wybierz pozycję **uaktualnienia łącznik gotowości**, a następnie kliknij przycisk **dalej**.

3.  Na **aplikacji** Określ Twojej **środowiska platformy Azure** (wersja zapoznawcza technical preview obsługuje tylko chmury publicznej). Następnie kliknij przycisk **importu** otworzyć **importowania aplikacji** okna.

4.  W **importowania aplikacji** okna, określ szczegóły dla aplikacji sieci web, która już istnieje w usługi Azure AD.
    -   Podaj przyjazną nazwę dla nazwy dzierżawy Azure AD. Następnie należy określić identyfikator dzierżawcy, nazwa aplikacji, Identyfikatora klienta, klucz tajny dla aplikacji sieci web platformy Azure i identyfikator URI aplikacji.
    -   Kliknij przycisk **Sprawdź**, a jeśli to się powiedzie, kliknij przycisk **OK** aby kontynuować.

5.   Na **konfiguracji** Określ subskrypcji, grupy zasobów i mają być używane dla tego połączenia, aby uaktualnić gotowości obszaru roboczego analizy systemu Windows.  

6.  Kliknij przycisk **dalej** można przejść do **Podsumowanie** strony, a następnie Ukończ pracę kreatora, aby utworzyć połączenie.


## <a name="new-client-settings-for-cloud-services"></a>Nowe ustawienia klienta dla usługi w chmurze
<!-- 1319883 -->

W tej wersji dodano dwa nowe ustawienia klienta programu Configuration Manager. Znajdują się one w **usługi w chmurze** sekcji.  Te ustawienia zapewniają następujące możliwości:

- Formant klientów programu Configuration Manager, które mogą uzyskiwać dostęp do bramy zarządzania skonfigurowanym chmury.
- Automatyczne rejestrowanie klientów programu Configuration Manager przyłączonych do domeny systemu Windows 10 w usłudze Azure Active Directory.

Te nowe ustawienia ułatwić wykonywanie funkcji opisanych w [Technical Preview programu Configuration Manager 1705](/sccm/core/get-started/capabilities-in-technical-preview-1705#new-capabilities-for-azure-ad-and-cloud-management).

### <a name="before-you-start"></a>Przed rozpoczęciem

Musi mieć zainstalowane i skonfigurowane Azure AD Connect między lokalnymi usługi Active Directory i dzierżawy usługi Azure AD.

Jeśli usuniesz połączenia urządzenia nie są wyrejestrowane, ale zarejestruje żadnych nowych urządzeń.

### <a name="try-it-out"></a>Wypróbuj

1. Skonfiguruj w poniższej sekcji (znalezione w usługach chmury) ustawienia klienta, korzystając z informacji w [sposób konfigurowania ustawień klienta](/sccm/core/clients/deploy/configure-client-settings).
    -   **Automatycznego rejestrowania nowych urządzeń przyłączonych do domeny systemu Windows 10 w usłudze Azure Active Directory** — ustawioną **tak** (ustawienie domyślne) lub **nr**.
    -   **Umożliwia klientom używać bramy zarządzania chmury** — ustawioną **tak** (ustawienie domyślne) lub **nr**.
2.  Wdróż ustawienia klienta w wymaganej kolekcji urządzeń.

Aby upewnić się, że urządzenie jest dołączane do usługi Azure AD, uruchom polecenie **/status dsregcmd.exe** w oknie wiersza polecenia. **AzureAdjoined** pole w wynikach **tak** Jeśli urządzenie jest usługi Azure AD przyłączony.

## <a name="create-and-run-powershell-scripts-from-the-configuration-manager-console"></a>Tworzenie i uruchamianie skryptów programu PowerShell z poziomu konsoli programu Configuration Manager
<!-- 1236459 -->

W programie Configuration Manager można wdrożyć skryptów na urządzeniach klienckich przy użyciu pakietów i programów. W tej wersji technical preview dodaliśmy nowe funkcje, które można wykonać następujące czynności:

- Importuj skryptów programu PowerShell dla programu Configuration Manager
- Edytowanie skryptów z poziomu konsoli programu Configuration Manager (w przypadku niepodpisanych skryptów tylko)
- Skrypty Oznacz jako zatwierdzone lub zabroniona, zwiększające bezpieczeństwo
- Uruchamianie skryptów w kolekcji komputerom klienckim z systemem Windows oraz lokalnych zarządzanych komputerów z systemem Windows. Nie można wdrożyć skrypty, zamiast tego są uruchamiane w najbliższym czasie rzeczywistym na urządzeniach klienckich.
- Zbadanie wyników zwróconych przez skrypt w konsoli programu Configuration Manager.


### <a name="prerequisites"></a>Wymagania wstępne

Używać skryptów, użytkownik musi należeć do odpowiedniej roli zabezpieczeń programu Configuration Manager.

- **Do zaimportowania, a także tworzenie skryptów** -Twoje konto musi mieć **Utwórz** uprawnienia dla **skryptów programu SMS** w **Menedżer ustawień zgodności** roli zabezpieczeń.
- **Do zatwierdzenia lub odmowy skrypty** -Twoje konto musi mieć **Zatwierdź** uprawnienia dla **skryptów programu SMS** w **Menedżer ustawień zgodności** roli zabezpieczeń.
- **Do uruchamiania skryptów** -Twoje konto musi mieć **Uruchom skrypt** uprawnienia dla **kolekcje** w **Menedżer ustawień zgodności** roli zabezpieczeń.

Aby uzyskać więcej informacji na temat ról zabezpieczeń programu Configuration Manager, zobacz [podstawowe informacje dotyczące administrowania opartego na rolach](/sccm/core/understand/fundamentals-of-role-based-administration).

Domyślnie użytkownicy nie można zatwierdzić skryptu, który one utworzone przez użytkownika. Ponieważ skrypty są wydajne, elastyczne i można wdrożyć na wielu urządzeniach, dodaliśmy nowe podejście daje możliwość rozdzielić role między osoby autorom tego skryptu i osoby, które zatwierdza skryptu. Zapewnia dodatkowy poziom zabezpieczeń przed uruchomieniem skryptu bez nadzoru. Można wyłączyć tego dodatkowej zatwierdzenia, aby ułatwić testowanie, szczególnie w wersji Technical Preview.

Aby umożliwić użytkownikom zatwierdzać własnych skryptów:

1. W konsoli programu Configuration Manager kliknij przycisk **Administracja**.
2. W obszarze roboczym **Administracja** rozwiń węzeł **Konfiguracja lokacji**, a następnie kliknij przycisk **Lokacje**.
3. Na liście witryn, wybierz witryny, a następnie na **Home** karcie **witryny** kliknij przycisk **ustawienia hierarchii**.
4. Na **ogólne** karcie **właściwości ustawień hierarchii** okna dialogowego polu, wyczyść pole wyboru **nie zezwalaj na skryptu autorzy mogą zatwierdzać własnych skryptów**.


### <a name="try-it-out"></a>Wypróbuj

#### <a name="import-and-edit-a-script"></a>Importowanie i edytowanie skryptu

1. W konsoli programu Configuration Manager kliknij przycisk **Biblioteka oprogramowania**.
2. W **Biblioteka oprogramowania** obszaru roboczego kliknij **skryptów**.
3. Na **Home** karcie **Utwórz** kliknij przycisk **Tworzenie skryptu**.
4. Na **skryptu** strony **Tworzenie skryptu** kreatora skonfiguruj następujące opcje:
    - **Nazwa skryptu** — wprowadź nazwę skryptu. Mimo że można tworzyć wiele skryptów o takiej samej nazwie, to zostanie utrudnić wyszukiwanie skryptów, które są potrzebne w konsoli programu Configuration Manager.
    - **Język skryptów** — obecnie tylko **PowerShell** skrypty są obsługiwane.
    - **Importuj** — importowanie skrypt programu PowerShell do konsoli. Skrypt jest wyświetlany w **skryptu** pola.
    - **Wyczyść** — usuwa bieżący skrypt z **skryptu** pola.
    - **Skrypt** -wyświetla skrypt aktualnie zaimportowany. Skrypt w tym polu, w razie potrzeby można edytować.
5. Ukończ pracę kreatora. Nowy skrypt jest wyświetlany w **skryptu** liście ze stanem **oczekiwanie na zatwierdzenie**. Zanim można było uruchomić ten skrypt na urządzeniach klienckich, należy ją zatwierdzić.


#### <a name="approve-or-deny-a-script"></a>Zatwierdzanie lub odrzucanie skryptu



Przed uruchomieniem skryptu, musi być zatwierdzony. Aby zatwierdzić skryptu:

1. W konsoli programu Configuration Manager kliknij przycisk **Biblioteka oprogramowania**.
2. W **Biblioteka oprogramowania** obszaru roboczego kliknij **skryptów**.
3. W **skryptu** wybierz skrypt, aby zaakceptować lub odrzucić, a następnie na **Home** karcie **skryptu** kliknij przycisk **Zatwierdź/Deny**.
4. W **Zatwierdź lub odmówić skryptu** okno dialogowe **Zatwierdź**, lub **Odmów** skryptu i opcjonalnie wprowadź komentarz dotyczący decyzji. Jeśli użytkownik zezwoli na skryptu, nie można uruchomić na urządzeniach klienckich.
5. Ukończ pracę kreatora. W **skryptu** listy, zobaczysz **stan zatwierdzenia** zmiany kolumny w zależności od akcja została wykonana.

#### <a name="run-a-script"></a>Uruchom skrypt

Po zatwierdzeniu skryptu, mogą być uruchamiane na kolekcję, którą wybierzesz.

1. W konsoli programu Configuration Manager kliknij przycisk **Zasoby i zgodność**.
2. W obszarze roboczym **Zasoby i zgodność** kliknij przycisk **Kolekcje urządzeń**.
3. W **kolekcje urządzeń** kliknij kolekcję urządzeń, na których chcesz uruchomić skrypt.
3. Na **Home** karcie **wszystkie systemy** kliknij przycisk **Uruchom skrypt**.
4. Na **skryptu** strony **Uruchom skrypt** kreatora wybierz skrypt z listy. Wyświetlane są tylko zatwierdzone skrypty. Kliknij przycisk **dalej**, a następnie Zakończ pracę kreatora.

#### <a name="monitor-a-script"></a>Monitor skryptu

Po uruchomieniu skryptu na urządzeniach klienckich, użyj tej procedury, aby monitorować powodzenie operacji.

1. W konsoli programu Configuration Manager kliknij **monitorowanie**.
2. W **monitorowanie** obszaru roboczego kliknij **wyniki skryptu**.
3. W **wyniki skryptu** listy, wyświetlania wyników dla każdego skryptu uruchomionego na urządzeniach klienckich. Kod zakończenia skryptu **0**, zwykle wskazuje, czy skrypt został uruchomiony pomyślnie.

## <a name="pxe-network-boot-support-for-ipv6"></a>Obsługa rozruchu środowiska PXE sieci IPv6
<!-- 1269793 -->
Można teraz włączyć obsługę rozruchu środowiska PXE sieci dla protokołu IPv6 uruchomić wdrożenia systemu operacyjnego sekwencji zadań. Po wybraniu tego ustawienia, punkty dystrybucji z włączoną obsługą środowiska PXE będzie obsługiwać protokoły IPv4 i IPv6. Ta opcja nie wymaga usług wdrażania systemu Windows i zatrzymać usług wdrażania systemu Windows, jeśli jest obecny.

#### <a name="to-enable-pxe-boot-support-for-ipv6"></a>Aby włączyć obsługę rozruchu środowiska PXE dla protokołu IPv6
Poniższa procedura umożliwia włączenie opcji do obsługi protokołu IPv6 dla środowiska PXE.

1. W konsoli programu Configuration Manager, przejdź do **administracji** > **omówienie** > **punktów dystrybucji**i kliknij przycisk **właściwości** dla punktów dystrybucji z włączoną obsługą środowiska PXE.
2. Na **PXE** wybierz opcję **obsługuje protokół IPv6** włączyć IPv6 obsługę środowiska PXE.

## <a name="manage-microsoft-surface-driver-updates"></a>Zarządzanie aktualizacjami sterownik Microsoft Surface
<!-- 1098490 -->
Można teraz używać programu Configuration Manager do zarządzania aktualizacjami sterownik Microsoft Surface.

### <a name="prerequisites"></a>Wymagania wstępne
Wszystkie punkty aktualizacji oprogramowania, należy uruchomić system Windows Server 2016.

### <a name="try-it-out"></a>Wypróbuj
Spróbuj wykonać następujące zadania, a następnie wyślij do nas **opinii** z **Home** kartę na Wstążce, aby poinformować nas, jak Ci poszło:
1. Włącz synchronizację dla Microsoft Surface sterowników. Użyj procedury [Konfigurowanie klasyfikacji i produktów](/sccm/sum/get-started/configure-classifications-and-products) i wybierz **obejmują Microsoft Surface sterowniki i aktualizacje oprogramowania układowego** na **klasyfikacje** kartę, aby włączyć sterowniki powierzchni.
2. [Synchronizuj sterowniki Microsoft Surface](/sccm/sum/get-started/synchronize-software-updates.md).
3. [Wdrażanie zsynchronizowane Microsoft Surface sterowniki](/sccm/sum/deploy-use/deploy-software-updates)

## <a name="configure-windows-update-for-business-deferral-policies"></a>Konfigurowanie usługi Windows Update dla zasad wykluczenia biznesowych
<!-- 1290890 -->
Można teraz skonfigurować zasady odroczenia urządzeń aktualizacje funkcji systemu Windows 10 lub jakości aktualizacji dla systemu Windows 10 zarządzane bezpośrednio przez usługę Windows Update dla firm. Zasadami odroczenia można zarządzać w nowym **Windows Update dla firm, zasady** węźle **Biblioteka oprogramowania** > **obsługi systemu Windows 10**.

### <a name="prerequisites"></a>Wymagania wstępne
Urządzenia z systemem Windows 10 zarządzane przez usługę Windows Update dla firm musi mieć połączenie z Internetem.

#### <a name="to-create-a-windows-update-for-business-deferral-policy"></a>Aby utworzyć Windows Update dla firm, zasady odroczenia
1. W **Biblioteka oprogramowania** > **obsługi systemu Windows 10** > **usługi Windows Update dla firm zasad**
2. Na **Home** karcie **Utwórz** grupy wybierz **tworzenia usługi Windows Update dla firm zasady** otworzyć utworzyć Windows Update dla firm Kreatora zasad.
3. Na **ogólne** Podaj nazwę i opis zasad.
4. Na **zasady odroczenia** skonfiguruj, czy mają być odroczone lub wstrzymać aktualizacje funkcji.    
    Aktualizacje funkcji są zazwyczaj nowe funkcje w systemie Windows. Po skonfigurowaniu **gałąź gotowości poziom** ustawienie, można zdefiniować czy i jak długo ma być odroczenie odbieranie aktualizacje funkcji po ich dostępności firmy Microsoft.
    - **Gałąź gotowości poziom**: Ustaw gałąź w przypadku którego urządzenia będzie odbierać aktualizacje systemu Windows (Current Branch lub Current Branch for Business).
    - **Okres odroczenia (dni)**:  Określ liczbę dni, dla których aktualizacje funkcji zostanie opóźnione. W przypadku opóźnienia, otrzymywać te aktualizacje funkcji na okres 180 dni od ich wydania.
    - **Uruchamianie funkcji aktualizacji Wstrzymaj**: Określ, czy można wstrzymać urządzeń z otrzymywania aktualizacji funkcji na okres maksymalnie 60 dni od czasu w przypadku wstrzymania aktualizacji. Po upływie maksymalna liczba dni, automatycznie wygaśnie funkcji Wstrzymaj i urządzenia rozpocznie skanowanie aktualizacji do zastosowania aktualizacji systemu Windows. Po tym skanowanie w przypadku wstrzymania aktualizacji ponownie. Aktualizacje funkcji można wznowić, usuwając zaznaczenie pola wyboru.   
5. Określ, czy mają być odroczone lub wstrzymać aktualizacje jakości.     
    Jakość aktualizacji są zwykle poprawki i ulepszenia istniejących funkcji systemu Windows i zwykle są publikowane pierwszy wtorek każdego miesiąca, jednak może być zwolnione w dowolnym momencie przez firmę Microsoft. Można określić, czy i jak długo ma być odroczenie pobiera jakość aktualizacje po ich dostępności.
    - **Okres odroczenia (dni)**: Określ liczbę dni, dla których aktualizacje funkcji zostanie opóźnione. W przypadku opóźnienia, otrzymywać te aktualizacje funkcji na okres 180 dni od ich wydania.
    - **Wstrzymaj aktualizacje jakości uruchamianie**: Określ, czy można wstrzymać urządzeniom otrzymywanie aktualizacji jakości przez okres do 35 dni od czasu w przypadku wstrzymania aktualizacji. Po upływie maksymalna liczba dni, automatycznie wygaśnie funkcji Wstrzymaj i urządzenia rozpocznie skanowanie aktualizacji do zastosowania aktualizacji systemu Windows. Po tym skanowanie w przypadku wstrzymania aktualizacji ponownie. Można wznowić jakości aktualizacji, usuwając zaznaczenie pola wyboru.
6. Wybierz **instalować aktualizacje z innymi Products Microsoft** Aby włączyć ustawienie zasad grupy, która odroczenia ustawienia mające zastosowanie do witryny Microsoft Update, a także aktualizacje systemu Windows.
7. Wybierz **zawierają sterowniki z witryny Windows Update** do automatycznego aktualizowania sterowników z aktualizacji systemu Windows. Jeśli wyczyścisz to ustawienie, aktualizacji sterownika nie można pobrać z witryny Windows Update.
8. Ukończ pracę kreatora, aby utworzyć nowe zasady opóźnienia.

#### <a name="to-deploy-a-windows-update-for-business-deferral-policy"></a>Do wdrażania aktualizacji systemu Windows dla firm, zasady odroczenia
1. W **Biblioteka oprogramowania** > **obsługi systemu Windows 10** > **usługi Windows Update dla firm zasad**
2. Na **Home** karcie **wdrożenia** grupy wybierz **wdrażania usługi Windows Update dla firm zasady**.
3. Skonfiguruj następujące ustawienia:
    - **Zasady konfiguracji do wdrożenia**: Wybierz usługi Windows Update dla firm zasady, którą chcesz wdrożyć.
    - **Kolekcja**: Kliknij przycisk **Przeglądaj** aby wybrać kolekcję, w której chcesz wdrożyć zasady.
    - **Koryguj niezgodne reguły, jeśli są obsługiwane**: Zaznacz, aby automatycznie korygować wszystkie reguły, które są niezgodne dla Instrumentacji zarządzania Windows (WMI), rejestru, skrypty i wszystkich ustawień dla urządzeń przenośnych, które są zarejestrowane przez program Configuration Manager.
    - **Zezwalaj na korygowanie poza oknem obsługi**: Jeśli okno obsługi zostało skonfigurowane dla kolekcji, w której wdrażasz zasady, Włącz tę opcję, aby pozwolić na korygowanie poza oknem obsługi wartości przy użyciu ustawień zgodności. Aby uzyskać więcej informacji dotyczących okien obsługi, zobacz [używanie okien obsługi](/sccm/core/clients/manage/collections/use-maintenance-windows).
    - **Generuj alert**: Konfiguruje alert jest generowany, gdy zgodności linii bazowej konfiguracji jest mniejsza niż określony procent określonej daty i godziny. Możesz również określić, czy chcesz wysyłać alert do programu System Center Operations Manager.
    - **Opóźnienie losowe (godziny)**: Określa okno opóźnienia, aby uniknąć nadmiernego przetwarzania w usłudze rejestracji urządzeń sieciowych. Wartość domyślna to 64 godzin.
    - **Harmonogram**: Określ harmonogram oceny zgodności oceny wdrożonego profilu na komputerach klienckich. Harmonogram może być prosty lub niestandardowy. Klienci oceniają profile po zalogowaniu się użytkownika.
4.  Ukończ pracę kreatora, aby wdrożyć profil.



## <a name="support-for-entrust-certification-authorities"></a>Obsługa Entrust urzędów certyfikacji
<!-- 1350740 -->
Program Configuration Manager obsługuje teraz Entrust urzędów certyfikacji; Dzięki temu dostarczania certyfikatów PFX na urządzeniach zarejestrowanych w programie Microsoft Intune.

Podczas dodawania roli punktu rejestracji certyfikatu w programie Configuration Manager, można skonfigurować Entrust jako urząd certyfikacji. Podczas dodawania nowego profilu certyfikatu, który wystawia certyfikaty PFX, możesz wybrać Microsoft lub Entrust urzędu certyfikacji.

**Znany problem**: W 1706 technical preview certyfikaty PFX nie są wystawiane na potrzeby urzędów certyfikacji firmy Microsoft. Nie dotyczy to profilów SCEP lub importowanych certyfikatów PFX.


## <a name="cisco-ipsec-support-for-macos-vpn-profiles"></a>Obsługa Cisco (IPsec) macOS profilów sieci VPN
<!-- 1321367 -->

Można utworzyć macOS profil sieci VPN z Cisco (IPsec) jako typ połączenia. Aby uzyskać więcej informacji, zobacz [tworzenie profilów sieci VPN](https://docs.microsoft.com/en-us/sccm/mdm/deploy-use/create-vpn-profiles#create-vpn-profiles).


## <a name="new-windows-configuration-item-settings"></a>Nowe ustawienia elementu konfiguracji systemu Windows
<!-- 1354715 -->

W tej wersji dodano następujące nowe ustawienia, których można użyć w elementach konfiguracji systemu Windows:

### <a name="password"></a>Hasło

- **Szyfrowanie urządzenia**

### <a name="device"></a>Urządzenie

- **Modyfikacja ustawień regionie (tylko wersja desktop)**
- **Modyfikacja ustawień zasilania i uśpienia**
- **Modyfikacja ustawień języka**
- **System czas modyfikacji**
- **Zmiana nazwy urządzenia**

### <a name="store"></a>Magazyn

- **Automatyczna aktualizacja aplikacji ze sklepu**
- **Użyj tylko prywatnego magazynu**
- **Uruchamianie aplikacji zdalnych magazynu**

### <a name="microsoft-edge"></a>Microsoft Edge

- **Blokowanie dostępu do informacji o: flagi**
- **Filtr SmartScreen monitu o zastąpienie**
- **Filtr SmartScreen monitu o zastąpienie plików**
- **Adres IP hosta lokalnego WebRTC**
- **Domyślny aparat wyszukiwania**
- **Adres URL OpenSearch XML**
- **Strony główne (tylko wersja desktop)**

Aby uzyskać więcej informacji na temat ustawień zgodności, zobacz [zapewnianie zgodności urządzeń](/sccm/compliance/understand/ensure-device-compliance).


## <a name="new-device-compliance-policy-rules"></a>Nowe reguły zasad zgodności urządzenia

* **Wymagany typ hasła**. Określ, czy użytkownik muszą utworzyć hasła alfanumerycznego i numeryczne hasła. Alfanumeryczne haseł również określić minimalną liczbę zestawów znaków, które muszą mieć hasłem. Są cztery zestawy znaków: Małe litery, wielkie litery, symbole i cyfry.

    **Obsługiwane na:**
    * Windows Phone 8+
    * Windows 8.1 +
    * iOS 6+
<br></br>
* **Debugowanie USB bloku na urządzeniu**. Nie masz ustawień jako debugowanie USB już jest wyłączona w systemie Android pracy urządzeń.

    **Obsługiwane na:**
    * Android 4.0+
    * Samsung Knox Standard 4.0+
<br></br>
* **Blokowanie aplikacji z nieznanych źródeł**. Wymagaj, aby urządzenia uniemożliwiały instalację aplikacji z nieznanych źródeł. Nie masz Skonfiguruj to ustawienie, jak Android pracy urządzeń zawsze ograniczyć instalacja z nieznanych źródeł.

    **Obsługiwane na:**
    * Android 4.0+
    * Samsung Knox Standard 4.0+
<br></br>
* **Wymagaj skanowania zagrożeń na aplikacje**. To ustawienie określa, że funkcja aplikacji Sprawdź, czy jest włączona na urządzeniu.

    **Obsługiwane na:**
    * System android 4.2 za pośrednictwem 4.4
    * Samsung Knox Standard 4.0+

Zobacz [tworzenie i wdrażanie zasad zgodności urządzenia](https://docs.microsoft.com/sccm/mdm/deploy-use/create-compliance-policy) próby nowe reguły zgodności urządzenia.

## <a name="new-mobile-application-management-policy-settings"></a>Nowe ustawienia zasad zarządzania aplikacjami mobilnymi
Począwszy od tej wersji, można użyć trzech nowe ustawienia zasad zarządzania aplikacjami mobilnymi:

- **Zablokuj Przechwytywanie ekranu (tylko urządzenia z systemem Android):** Określa, że możliwości przechwytywania ekranu urządzenia są blokowane podczas korzystania z tej aplikacji.

- **Wyłącz synchronizację kontaktów:** Aplikacja uniemożliwia zapisywania danych do aplikacji natywnej kontaktów na urządzeniu.

- **Wyłącz drukowanie:** Zapobiega aplikacji z drukowaniem pracy lub szkoły danych.

Zobacz [ochrona aplikacji przy użyciu zasad ochrony aplikacji w programie Configuration Manager](https://docs.microsoft.com/sccm/mdm/deploy-use/protect-apps-using-mam-policies) próby nowe ustawienia zasad ochrony aplikacji.

## <a name="android-and-ios-enrollment-restrictions"></a>Android i iOS ograniczenia rejestracji
<!-- 1290826 -->
Począwszy od tej wersji, Administratorzy mogą teraz określić czy użytkowników nie można zarejestrować urządzeń osobistych Android lub iOS w środowisku hybrydowym. Dzięki temu limit zarejestrowane urządzenia do predeclared, urządzenia należące do firmy lub zarejestrowane w usłudze Device Enrollment Program tylko urządzeń z systemem iOS.

### <a name="try-it-out"></a>Podczas próby
1. W konsoli programu Configuration Manager, w obszarze roboczym **Administracja** , wybierz pozycję **Usługi w chmurze** > **Subskrypcja usługi Microsoft Intune**.
2. Na **Home** karcie **subskrypcji** grupy, wybierz **Konfiguruj platformy** , a następnie wybierz **Android** lub **iOS**.
3. Wybierz **osobiście urządzenia należące do bloku**.

## <a name="android-for-work-application-management-policy-for-copy-paste"></a>Android pracy zasad zarządzania aplikacjami do kopiowania i wklejania
Zaktualizowaliśmy opisy ustawień dla systemu Android dla elementów roboczych konfiguracji dla **Zezwalaj na udostępnianie między pracą a profilu osobistego danych**.

|Przed 1706 Technical Preview | Nowa nazwa opcji | Zachowanie|
|-|-|-|
|Zapobieganie udostępnianiu wszelkie bariery| Domyślne ograniczenia udostępniania| Pracy na osobistych: Domyślne (Oczekiwano zablokowanie we wszystkich wersjach) <br>Osobiste do pracy: Domyślne (dozwolone w 6.x+, zablokowane na 5.x)|
|Bez ograniczeń|   Aplikacje w profilu osobistego może obsłużyć żądania z profilu pracy udostępniania| Pracy na osobistych: Dozwolone  <br>Osobiste do pracy: Dozwolone|
|Aplikacje w profilu pracy może obsłużyć żądania z osobistego udostępniania |Aplikacje w profilu pracy może obsłużyć żądania z osobistego udostępniania |Pracy na osobistych: Domyślny<br>Osobiste do pracy: Dozwolone<br>(Tylko na 5.x przydatne w przypadku, gdy osobiste do pracy jest zablokowana)|

Żadna z tych opcji bezpośrednio zapobiec kopiowania i wklejania. Dodaliśmy niestandardową wartość ustawienia usługi i aplikacji Portal firmy w 1704, które można skonfigurować w celu zapobieżenia kopiowania i wklejania. Można to skonfigurować w niestandardowy identyfikator URI.

-   OMA-URI: ./Vendor/MSFT/WorkProfile/DisallowCrossProfileCopyPaste
-   Typ wartości: Boolean

Ustawienie DisallowCrossProfileCopyPaste true zapobiega zachowanie kopiowania i wklejania między Android for Work osobistych i profili pracy.

### <a name="try-it-out"></a>Podczas próby
1. W konsoli programu Configuration Manager wybierz **zasoby i zgodność** > **omówienie** > **ustawień zgodności** > **elementy konfiguracji**.
2. Wybierz **Utwórz** Aby utworzyć nowy element konfiguracji oraz określić **nazwa** i **Android for Work**.
3. Grupy do konfigurowania ustawień urządzenia, wybierz **profilu pracy**i wybierz polecenie **dalej**.
4. Wybierz wartość dla **Zezwalaj na udostępnianie między pracą a Profile osobiste danych**, a następnie Zakończ pracę kreatora.

## <a name="device-health-attestation-assessment-for-compliance-policies-for-conditional-access"></a>Ocena zaświadczania o kondycji urządzenia dla zasady zgodności dla dostępu warunkowego
<!-- 1097546 -->
Począwszy od tej wersji możesz użyć stan zaświadczania o kondycji jako reguły zasad zgodności dla warunkowego dostępu do zasobów firmy.

### <a name="try-it-out"></a>Podczas próby
Wybierz regułę zaświadczania o kondycji w ramach oceny zasad zgodności.
