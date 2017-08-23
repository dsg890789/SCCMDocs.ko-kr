---
title: Funkcje w wersji zapoznawczej Technical Preview 1702 programu Configuration Manager
description: "Dowiedz się więcej o funkcjach dostępnych w wersji zapoznawczej Technical Preview programu System Center Configuration Manager, wersja 1702."
ms.custom: na
ms.date: 02/24/2017
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: aedd608d-6db3-4ea5-851d-70f2dcda6bb5
caps.latest.revision: "5"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 3bdbcd1a3c64a1d50f2f6219b2a5e17d60979864
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="capabilities-in-technical-preview-1702-for-system-center-configuration-manager"></a>Funkcje w wersji Technical Preview 1702 programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (wersja zapoznawcza Technical Preview)*

W tym artykule przedstawiono funkcje, które są dostępne w wersji Technical Preview programu System Center Configuration Manager, wersja 1702. Można zainstalować tę wersję, aby zaktualizować i dodać nowe funkcje do lokacji programu Configuration Manager technical preview. Przed zainstalowaniem tej wersji technical Preview, przejrzyj temat wprowadzający [Technical Preview programu System Center Configuration Manager](../../core/get-started/technical-preview.md), aby zapoznać się z ogólne wymagania i ograniczenia dotyczące używania wersji technical preview, jak zaktualizować między wersjami i sposobu wyrazić swoją opinię na temat funkcji w wersji technical preview.    


**Poniżej przedstawiono nowe funkcje, które można wypróbować z tą wersją.**  

##  <a name="send-feedback-from-the-configuration-manager-console"></a>Wyślij opinię z konsoli programu Configuration Manager

Ta wersja zapoznawcza wprowadza nowe opcje opinii w konsoli programu Configuration Manager. Opcje opinii umożliwia wysyłanie opinii bezpośrednio do zespół deweloperów i opinie UserVoice Menedżera konfiguracji witryny sieci Web.  

>Można znaleźć **opinii** opcji:
-  Na Wstążce, w lewym karcie Narzędzia główne w każdym węźle.  
   ![Wstążka](./media/feedback-home.png)

-  Po kliknięciu prawym przyciskiem myszy dowolnego obiektu w konsoli.   
    ![Kopiowanie kliknięcia](./media/feedback-option.png)   

Wybieranie **opinii** Otwiera przeglądarkę, aby UserVoice programu Configuration Manager feedback witryny sieci Web, https://configurationmanager.uservoice.com/forums/300492-ideas.
##  <a name="changes-for-updates-and-servicing"></a>Zmiany dotyczące aktualizacji i obsługi
Poniżej zostały wprowadzone w tej wersji zapoznawczej.

**Prostsze opcje aktualizacji**  
Przy następnym infrastruktury kwalifikuje się w przypadku aktualizacji co najmniej dwa pobrać tylko najnowszą aktualizację. Na przykład, jeśli bieżąca wersja lokacji jest dwa lub więcej starsze niż najnowszej wersji, która jest dostępna, tylko że najnowsza wersja aktualizacji jest pobierany automatycznie.  

Masz opcję, aby pobrać i zainstalować inne dostępne aktualizacje, nawet wtedy, gdy nie są one najbardziej aktualnej wersji. Jednak zostanie wyświetlone ostrzeżenie, że aktualizacja została zastąpiona nowszą. Aby pobrać aktualizację, która jest *dostępne do pobrania*, wybierz aktualizację, w konsoli, a następnie kliknij przycisk **Pobierz**.

**Ulepszone czyszczenie starszych aktualizacji**   
Dodano funkcję automatycznego czyszczenia, która usuwa zbędne pobrane pliki z folderu "EasySetupPayload" na serwerze lokacji.  


## <a name="peer-cache-improvements"></a>Ulepszenia pamięci podręcznej elementów równorzędnych
Począwszy od tej wersji, komputerze źródła równorzędnej pamięci podręcznej żądania zawartości podczas odrzuci komputer źródłowy równorzędnej pamięci podręcznej spełnia żadnego z następujących warunków:  
 -  Jest w trybie niskim poziomie naładowania baterii.
 -  Obciążenie procesora CPU przekracza 80% w czasie żądanej zawartości.
 -  We/Wy dysku ma *AvgDiskQueueLength* przekraczający 10.
 -  Brak dostępnego połączenia z tym komputerem.   

Można skonfigurować te ustawienia przy użyciu klasy konfiguracji agenta klienta dla funkcji źródło elementu równorzędnego (*SMS_WinPEPeerCacheConfig*) gdy używasz zestawu SDK System Center Configuration Manager.

Gdy komputer odrzuci zawartości, komputera wysyłającego żądanie będzie wyszukiwać źródła alternatywne zawartości formularza w puli lokalizacji źródła zawartości.   

## <a name="azurediscovery"></a>Azure Active Directory Domain Services umożliwia zarządzanie urządzeniami, użytkownikami i grupami

Z tej wersji technical preview można zarządzać urządzeniami, które są przyłączone do usług domenowych w usłudze Azure Active Directory (AD) w wersji zarządzane domeny. Umożliwia również odnajdywanie urządzeń, użytkowników i grup w domenie z różnych metod odnajdywania programu Configuration Manager.

Infrastruktura lokacji wersji zapoznawczej technical preview, klientów i domeny usług domenowych Azure AD musi uruchomić na platformie Azure.


### <a name="set-up-configuration-manager-to-use-azure-ad"></a>Ustaw Konfigurowanie programu Configuration Manager przy użyciu usługi Azure AD
Aby korzystać z usługi Azure AD z programem Configuration Manager, będą potrzebne następujące czynności:
-   Subskrypcja platformy Azure.
-   Azure AD z usługami domenowymi (DS).
-   Lokacja programu Configuration Manager, która działa na maszynie Wirtualnej platformy Azure, w której jest dołączony do usługi Azure AD.
-   Klientów programu Configuration Manager, które są uruchamiane w tym samym środowisku usługi Azure AD.

Aby skonfigurować usługi domenowe Azure AD, zobacz [wprowadzenie do usług domenowych Azure AD](https://docs.microsoft.com/azure/active-directory-domain-services/active-directory-ds-getting-started).

### <a name="discover-resources"></a>Odnajdywanie zasobów
Po ustawieniu konfiguracji programu Configuration Manager do uruchamiania w usłudze Azure AD umożliwia następujących metod odnajdywania usługi Active Directory wyszukiwania usługi Azure AD dla zasobów:  
- Odnajdywanie systemu usługi Active Directory
- odnajdywanie użytkownika usługi Active Directory
- Odnajdywanie grupy usługi Active Directory  

Dla każdej używanej metody Edytuj zapytanie LDAP do wyszukiwania struktury jednostek organizacyjnych programu Azure AD, zamiast kontenerów, które są typowe dla lokalnej usługi Active Directory. Teraz należy skierować zapytanie wyszukiwania usługi Active Directory w ramach subskrypcji platformy Azure.  

W poniższych przykładach użyto usługi Azure AD z *contoso.onmicrosoft.com*:
 - **Odnajdywanie systemu**   
Usługi Azure AD przechowuje urządzeń bez względu na **komputerów AADDC** jednostki Organizacyjnej.  Skonfiguruj następujące ustawienia:  
  - *Komputery LDAP://OU=AADDC, DC = contoso, DC = onmicrosoft, DC = com*  


- **Odnajdowanie użytkowników** AAD przechowuje użytkowników w obszarze **użytkowników AADDC** jednostki Organizacyjnej.  Skonfiguruj następujące ustawienia:
  - *Użytkownicy LDAP://OU=AADDC, DC = contoso, DC = onmicrosoft, DC = com*


- **Odnajdywanie grupy**  
Usługi Azure AD nie ma jednostkę Organizacyjną, która przechowuje grup. Zamiast tego należy używać tej samej struktury ogólne jako System lub użytkownik zapytania i skonfiguruj zapytanie LDAP do punktu z jednostką organizacyjną, która zawiera grupy, czy ma zostać przeprowadzone odnajdywanie.

Zobacz następujące tematy, aby uzyskać więcej informacji na temat usługi Azure AD:  
 - [Azure Active Directory Domain Services](https://azure.microsoft.com/en-us/services/active-directory-ds) w witrynie azure.microsoft.com.
 - [Dokumentacja usługi domenowe Active Directory](https://docs.microsoft.com/azure/active-directory-domain-services) w witrynie docs.microsoft.com.

## <a name="conditional-access-device-compliance-policy-improvements"></a>Ulepszenia zasad zgodności urządzenia dostępu warunkowego

Dostępny jest nowy reguły zasad zgodności urządzenia możesz zablokować dostęp do zasobów firmy, które obsługują dostęp warunkowy, gdy użytkownicy korzystają z aplikacji, które są częścią listę niezgodnych aplikacji. Lista niezgodnych aplikacji można definiować przez administratora podczas dodawania nowej reguły zgodne **aplikacji, których nie można zainstalować**. Ta zasada wymaga administratora, aby wprowadzić **Nazwa aplikacji**, **identyfikator aplikacji**i **wydawcę aplikacji** (opcjonalnie), podczas dodawania do listy niezgodnych aplikacji. To ustawienie dotyczy tylko urządzeń iOS i Android.

Ponadto pomaga organizacjom ograniczyć wycieku danych za pośrednictwem niezabezpieczonej aplikacji i zapobiec zużycie nadmiernej ilości danych za pośrednictwem niektórych aplikacji.

- Dowiedz się więcej [sposób działania zasad zgodności urządzenia](https://docs.microsoft.com/sccm/protect/deploy-use/device-compliance-policies).
- Dowiedz się więcej [jak utworzyć zasady zgodności urządzeń](https://docs.microsoft.com/sccm/protect/deploy-use/create-compliance-policy).

### <a name="try-it-out"></a>Podczas próby

**Scenariusz:** Określenie aplikacji, które mogą być przyczyną wyciekowi danych przez wysyłanie danych firmowych poza firmę lub który powodują nadmiernej ilości danych użycia, następnie [Tworzenie zasad zgodności urządzeń dostępu warunkowego](https://docs.microsoft.com/sccm/protect/deploy-use/create-compliance-policy) dodaje te aplikacje do listy niezgodnych aplikacji. Spowoduje to zablokowanie dostępu do zasobów firmy, które obsługują dostęp warunkowy, dopóki użytkownik może usunąć zablokowanych aplikacji.

## <a name="antimalware-client-version-alert"></a>Alert wersji klienta ochrony przed złośliwym oprogramowaniem
Począwszy od tej wersji zapoznawczej, ochrony punktu końcowego Menedżera konfiguracji zawiera alert, jeśli więcej niż 20% (ustawienie domyślne) zarządzanych klientów są przy użyciu wygasłe wersji klienta ochrony przed złośliwym kodem (tj. klient usługi Windows Defender lub program Endpoint Protection).

### <a name="try-it-out"></a>Podczas próby
Upewnij się, że program Endpoint Protection jest włączony na wszystkich klientach stacjonarnych i serwerów za pomocą zasad ustawień klienta. Możesz teraz przeglądać **wersji klienta ochrony przed złośliwym kodem** i **stan wdrożenia programu Endpoint Protection** przechodząc **zasoby i zgodność** > **omówienie** > **urządzeń** > **wszystkie komputery stacjonarne i klienci służą**. Aby sprawdzić, czy alert, Wyświetl **alerty** w **monitorowanie** obszaru roboczego. W przypadku więcej niż 20% zarządzanych klientów używana wygasła wersja ochrony przed złośliwym oprogramowaniem, wersja klienta ochrony przed złośliwym kodem jest nieaktualna zostanie wyświetlony alert. Ten alert nie jest wyświetlany na **monitorowanie** > **omówienie** kartę. Aby zaktualizować klientów wygasłe ochrony przed złośliwym kodem, Włącz aktualizacje oprogramowania dla klientów ochrony przed złośliwym oprogramowaniem.

Aby skonfigurować wartość procentowa, o której alert jest generowany, rozwiń węzeł **monitorowanie** > **alerty** > **wszystkie alerty**, kliknij dwukrotnie **klienci ochrony przed złośliwym kodem nieaktualny** i zmodyfikuj **Zgłoś alert, jeśli wartość procentowa zarządzanych klientów z nieaktualną wersją klienta ochrony przed złośliwym kodem jest więcej niż** opcji.

## <a name="compliance-assessment-for-windows-update-for-business-updates"></a>Oceny zgodności dla usługi Windows Update dla firm aktualizacji
Można teraz skonfigurować reguły zgodności zasad aktualizacji do uwzględnienia Windows Update dla firm oceny wyniku częścią oceny dostępu warunkowego.
> [!IMPORTANT]
> Musi mieć system Windows 10 niejawnego kompilacji w wersji zapoznawczej 15019 lub nowszym używane do oceny zgodności dla usługi Windows Update dla firm aktualizacji.

### <a name="allow-windows-update-for-business-to-manage-windows-10-updates"></a>Zezwalaj na Windows Update dla firm w celu zarządzania aktualizacjami systemu Windows 10
Aby zebrać informacji o oceny zgodności dla usługi Windows Update dla firm aktualizacje, umożliwia skonfigurowanie ustawień jawnie zezwolić na aktualizacje systemu Windows dla firm w celu zarządzania aktualizacjami systemu Windows 10 agenta klienta poniższej procedury.
1. W konsoli programu Configuration Manager przejdź do obszaru **Administracja** > **Ustawienia klienta**.
2. We właściwościach ustawień klienta, przejdź do **aktualizacji oprogramowania**i wybierz **tak** dla **aktualizuje Zarządzanie systemem Windows 10 z usługą Windows Update dla firm** ustawienie.

### <a name="create-a-compliance-policy-for-windows-update-for-business-assessment"></a>Tworzenie zasad zgodności dla usługi Windows Update dla firm oceny
1. W konsoli programu Configuration Manager, przejdź do **zasoby i zgodność** > **ustawień zgodności** > **zasady zgodności**.
2. Kliknij przycisk **Utwórz zasady zgodności** lub wybierz istniejące zasady zgodności, aby zmodyfikować.
3. Na stronie Ogólne Podaj nazwę i opis, wybierz **reguły zgodności dla urządzeń zarządzanych za pomocą klienta programu Configuration Manager**, Ustaw ważność niezgodności dla raportowania i kliknij przycisk **dalej**.
4. Na stronie obsługiwane platformy wybierz **systemu Windows 10**, a następnie kliknij przycisk **dalej**.
5. Na stronie reguły kliknij **nowy...** , a następnie **warunku** wybierz **wymagają usługi Windows Update dla firm zgodności**. **Wartość** automatycznie mają ustawioną wartość **True**.

Nowe zasady zostaną wyświetlone w węźle **Zasady zgodności** w obszarze roboczym **Zasoby i zgodność** .

### <a name="deploy-a-compliance-policy"></a>Wdrażanie zasad zgodności
1. W konsoli programu Configuration Manager, przejdź do **zasoby i zgodność** > **ustawień zgodności**, a następnie kliknij przycisk **zasady zgodności**.
2. Na karcie **Narzędzia główne** w grupie **Wdrażanie** kliknij przycisk **Wdróż**.
3. W oknie dialogowym **Wdrażanie zasad zgodności** kliknij przycisk **Przeglądaj** , aby wybrać kolekcję użytkowników, dla której chcesz wdrożyć zasady.
   Ponadto można wybrać opcje generowania alertów w przypadku niezgodności zasad, a także skonfigurować harmonogram oceny zasad pod kątem zgodności.
4. Gdy wszystko będzie gotowe, kliknij przycisk **OK**.

### <a name="monitor-the-compliance-policy"></a>Monitorowanie zasad zgodności
Po utworzeniu zasad zgodności można monitorować wyniki zgodności w konsoli programu Configuration Manager. Aby uzyskać więcej informacji, zobacz [monitorowanie zasad zgodności](https://docs.microsoft.com/en-us/sccm/protect/deploy-use/create-compliance-policy#monitor-the-compliance-policy).


## <a name="improvements-to-software-center-settings-and-notification-messages-for-high-impact-task-sequences"></a>Ulepszenia w ustawieniach Centrum oprogramowania i komunikaty powiadomień dla sekwencji zadań o dużym wpływie na działanie
Ta wersja zawiera następujące ulepszenia w ustawieniach Centrum oprogramowania i komunikaty powiadomień poważnych wdrożenia sekwencji zadań:

- W oknie właściwości dla sekwencji zadań można teraz skonfigurować wszystkie sekwencje zadań, w tym sekwencji zadań systemu operacyjnego jako wdrożenie wysokiego ryzyka. Wszystkie sekwencje zadań, która spełnia określone warunki automatycznie jest zdefiniowany jako dużym znaczeniu. Aby uzyskać więcej informacji, zobacz [zarządzania wdrożeniami o wysokim ryzyku](http://docs.microsoft.com/sccm/protect/understand/settings-to-manage-high-risk-deployments).
- W oknie właściwości dla sekwencji zadań można użyć domyślnego komunikatu powiadomienia lub utworzyć własne niestandardowe powiadomienie w przypadku wdrożeń o dużym znaczeniu.
- We właściwościach sekwencji zadań można skonfigurować właściwości, które obejmują upewnij ponownego uruchomienia wymaganych, Centrum oprogramowania rozmiar pobierania sekwencji zadań i szacowany czas wykonywania.
- W komunikacie wdrożenia poważnych domyślne w miejscu uaktualnia teraz stanów automatycznie migracji aplikacji, danych i ustawień. Wcześniej, domyślną wiadomość do wszelkich instalacji systemu operacyjnego wskazuje, że wszystkie aplikacje, dane i ustawienia, może spowodować utratę, który nie jest spełniony dla uaktualnienia w miejscu.

### <a name="set-a-task-sequence-as-a-high-impact-task-sequence"></a>Ustawianie sekwencji zadań za pomocą sekwencji zadań o dużym wpływie na działanie
Użyj poniższej procedury, aby ustawić sekwencji zadań jako dużym znaczeniu.
> [!NOTE]
> Wszystkie sekwencje zadań, która spełnia określone warunki automatycznie jest zdefiniowany jako dużym znaczeniu. Aby uzyskać więcej informacji, zobacz [zarządzania wdrożeniami o wysokim ryzyku](http://docs.microsoft.com/sccm/protect/understand/settings-to-manage-high-risk-deployments).

1. W konsoli programu Configuration Manager, przejdź do **Biblioteka oprogramowania** > **systemów operacyjnych** > **sekwencje zadań**.
2. Wybierz sekwencję zadań do edycji, a następnie kliknij przycisk **właściwości**.
3. Na **powiadomienie użytkownika** wybierz opcję **to sekwencję zadań poważnych**.

### <a name="create-a-custom-notification-for-high-risk-deployments"></a>Utwórz niestandardowe powiadomienie w przypadku wdrożeń o wysokim ryzyku
1. W konsoli programu Configuration Manager, przejdź do **Biblioteka oprogramowania** > **systemów operacyjnych** > **sekwencje zadań**.
2. Wybierz sekwencję zadań do edycji, a następnie kliknij przycisk **właściwości**.
3. Na **powiadomienie użytkownika** wybierz opcję **używać tekstu niestandardowego**.
>  [!NOTE]
>  Tekst powiadomienia użytkownika można ustawić tylko podczas **to sekwencję zadań poważnych** jest zaznaczone.

4. Skonfiguruj następujące ustawienia (maksymalnie 255 znaków dla każdego pola tekstowego):

   **Tekst nagłówka powiadomienia użytkownika**: Określa niebieski tekst wyświetlany na powiadomienie użytkownika Centrum oprogramowania. Na przykład w domyślnie powiadomienie użytkownika, ta sekcja zawiera przypominać "Potwierdź do uaktualnienia systemu operacyjnego na tym komputerze".

   **Tekst komunikatu powiadomienia użytkownika**: Istnieją trzy pola tekstowe zawierających treść niestandardowe powiadomienie.
   - 1. pole tekstowe: Określa główną część tekstu, zwykle zawierającego instrukcje dla użytkownika. Na przykład w domyślnie powiadomienie użytkownika, ta sekcja zawiera coś takie jak "Uaktualnianie systemu operacyjnego zajmie trochę czasu i komputer może być kilka razy ponownie."
   - pole tekstowe 2: Określa pogrubioną w głównej części tekstu. Na przykład w domyślnie powiadomienie użytkownika, ta sekcja zawiera coś takie jak "to uaktualnienie w miejscu instaluje nowy system operacyjny i automatycznie przeprowadzanie migracji aplikacji, danych i ustawień".
   - pole tekstowe 3: Określa ostatni wiersz tekstu w polu pogrubiony tekst. Na przykład w domyślnie powiadomienie użytkownika, ta sekcja zawiera przypominać "kliknij przycisk Instaluj, aby rozpocząć. W przeciwnym razie kliknij przycisk Anuluj."   

   Załóżmy, że możesz skonfigurować następujące powiadomienie niestandardowych we właściwościach.

   ![Niestandardowe powiadomienie w sekwencji zadań](.\media\user-notification.png)

   Pojawi się następujący komunikat powiadomienia, gdy użytkownik końcowy otworzy instalacji w programie Software Center.

   ![Niestandardowe powiadomienie w sekwencji zadań](.\media\user-notification-enduser.png)

### <a name="configure-software-center-properties"></a>Skonfiguruj właściwości Centrum oprogramowania
Poniższa procedura umożliwia skonfigurowanie szczegóły sekwencji zadań wyświetlana w Centrum oprogramowania. Te informacje są wyłącznie w celach informacyjnych.  
1. W konsoli programu Configuration Manager, przejdź do **Biblioteka oprogramowania** > **systemów operacyjnych** > **sekwencje zadań**.
2. Wybierz sekwencję zadań do edycji, a następnie kliknij przycisk **właściwości**.
3. Na **ogólne** kartę, dostępne są następujące ustawienia w programie Software Center:
  - **Wymagane jest ponowne uruchomienie**: Umożliwia użytkownikowi wiedzieć, czy ponowne uruchomienie jest wymagane podczas instalacji.
  - **Pobierz rozmiar (MB)**: Określa, ile megabajtów jest wyświetlana w Centrum oprogramowania dla sekwencji zadań.  
  - **Szacowany czas wykonywania (minuty)**: Określa szacowany czas wykonywania w minutach, które jest wyświetlane w Centrum oprogramowania dla sekwencji zadań.


## <a name="check-for-running-executable-files-before-installing-an-application"></a>Sprawdź, czy uruchamianie plików wykonywalnych przed zainstalowaniem aplikacji

W  *<deployment type name>*  **właściwości** okno dialogowe typu wdrożenia, na karcie zachowanie instalacji można teraz określić jedną więcej pliki wykonywalne, jeśli uruchomiony, blokuje instalację typu wdrożenia. Użytkownik musi zamknąć plik wykonywalny uruchomiona (lub może zostać zamknięty w automatycznie w przypadku wdrożeń z celem wymagane) przed wdrożeniem można było zainstalować typ.

### <a name="try-it-out"></a>Wypróbować jej możliwości.

1.  We właściwościach typu wdrożenia programu Configuration Manager wybierz **zainstalować zachowanie** kartę.
2.  Wybierz **Dodaj** można dodać co najmniej jedną nazwę pliku wykonywalnego chcesz wyszukać. Można również dodać nazwę wyświetlaną, aby ułatwić użytkownikom identyfikację aplikacje na liście.
3.  Jeśli wdrożenie ma cel w Kreatorze wdrażania oprogramowania wymagane Opcjonalnie możesz **automatycznie Zamknij wszystkie uruchomione pliki wykonywalne określone na karcie zachowanie instalacji okna dialogowego właściwości typu wdrożenia**.

Jeśli aplikacja została wdrożona jako **dostępne**i użytkownik końcowy próbuje zainstalować aplikację, będą oni musieli podać do Zamknij wszystkie uruchomione pliki wykonywalne określona zanim można kontynuować instalacji.

Jeśli aplikacja została wdrożona jako **wymagane**wraz z opcją **automatycznie Zamknij wszystkie uruchomione pliki wykonywalne określone na karcie zachowanie instalacji okna dialogowego właściwości typu wdrożenia** jest zaznaczone, zobaczą okno dialogowe, które informuje, że pliki wykonywalne określonego zostaną automatycznie zamknięte po osiągnięciu ostatecznego terminu instalacji aplikacji. Można zaplanować tych okien dialogowych w **ustawień klienta** > **Agent komputera**. Jeśli nie chcesz, aby użytkownik końcowy, aby wyświetlić te komunikaty, wybierz **Ukryj w programie Software Center i wszystkie powiadomienia** na **środowisko użytkownika** we właściwościach wdrożenia.

Jeśli aplikacja została wdrożona jako **wymagane** wraz z opcją **automatycznie Zamknij wszystkie uruchomione pliki wykonywalne określone na karcie zachowanie instalacji okna dialogowego właściwości typu wdrożenia** nie jest zaznaczone, a następnie instalacja aplikacji zakończy się niepowodzeniem, jeśli jeden lub więcej określonych aplikacji jest uruchomione.

## <a name="create-pfx-certificates-with-s-mime-support"></a>Tworzenie certyfikatów PFX z obsługą S MIME

Teraz możesz utworzyć profil certyfikatu PFX, który obsługuje szyfrowanie S/MIME i wdrażanie dla użytkowników.  Ten certyfikat może następnie używane S/MIME szyfrowania i odszyfrowywania na urządzeniach zarejestrowanych przez użytkownika.

Ponadto można określić wiele urzędów certyfikacji (CA) na wiele ról systemu lokacji punktu rejestracji certyfikatu i przypisywane żądaniach procesu urzędów certyfikacji jako część profilu certyfikatu.

Dla urządzeń z systemem iOS można skojarzyć profil certyfikatu PFX do profilu poczty e-mail i włączenia szyfrowania S/MIME.  Następnie to umożliwi S/MIME w klienta natywnego poczty e-mail w systemie iOS i kojarzy prawidłowy certyfikat szyfrowania S/MIME do niego.

Aby uzyskać więcej informacji na temat certyfikatów w programie Configuration Manager, zobacz [wprowadzenie do profilów certyfikatów w programie System Center Configuration Manager]( https://docs.microsoft.com/sccm/protect/deploy-use/introduction-to-certificate-profiles).


## <a name="new-compliance-settings-for-ios-devices"></a>Nowe ustawienia zgodności dla urządzeń z systemem iOS

Dodano nowe ustawienia, których można używać we wszystkich elementach konfiguracji dla urządzeń z systemem iOS. Są to ustawienia, które wcześniej były dostępne w programie Microsoft Intune w konfiguracji autonomicznej i są teraz dostępne podczas korzystania z usługi Intune z programem Configuration Manager. Jeśli potrzebujesz pomocy z dowolnymi spośród tych ustawień, zobacz [ustawienia zasad systemu iOS w programie Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/ios-policy-settings-in-microsoft-intune).

- **Synchronizowanie danych z zarządzanych aplikacji usługi iCloud**
- **Programowi handoff na kontynuowanie działań na innym urządzeniu**
- **Udostępnianie zdjęć w ramach usługi iCloud**
- **Biblioteka zdjęć w usłudze iCloud**
- **Zaufania nowych autorów aplikacji przedsiębiorstwa**
- **Zezwalaj użytkownikom na pobieranie zawartości ze sklepu iBook oznaczonej jako "Erotyka"** (tylko tryb nadzorowany)
- **Wymuś łączyć obserwowanie firmy Apple, aby korzystać z nadgarstka wykrywania**
- **Hasło dla wychodzących żądań funkcji AirPlay**
- **Zmodyfikuj ustawienia konta** (tylko tryb nadzorowany)
- **Zmiany ustawień użycia danych komórkowych aplikacji** (tylko tryb nadzorowany)
- **ERASE całej zawartości i wszystkich ustawień** (tylko tryb nadzorowany)
- **Konfigurowanie ograniczeń urządzenia** (tylko tryb nadzorowany)
- **Użyj parowanie hostów w celu kontrolowania urządzenia może być sparowane urządzenie iOS** (tylko tryb nadzorowany)
- **Instalowanie profilów konfiguracji i certyfikatów** (tylko tryb nadzorowany)
- **Zmiana nazwy urządzenia** (tylko tryb nadzorowany)
- **Modyfikowanie kodu dostępu** (tylko tryb nadzorowany)
- **Parowanie Apple Watch** (tylko tryb nadzorowany)
- **Modyfikacja ustawień powiadomień** (tylko tryb nadzorowany)
- **Wallpaper modyfikacji** (tylko tryb nadzorowany)
- **Modyfikacja ustawień diagnostyki przesyłanie** (tylko tryb nadzorowany)
- **Modyfikacja Bluetooth** (tylko tryb nadzorowany)
- **AirDrop** (tylko tryb nadzorowany)
- **Użyj programowi siri na wykonywanie zapytań o zawartość wygenerowaną przez użytkowników z Internetu** (tylko tryb nadzorowany)
- **Używanie programu Siri niestosownych wyrażeń filtru** (tylko tryb nadzorowany)
- **Zwracania wyników z Internetu w przez wyszukiwanie Spotlight** (tylko tryb nadzorowany)
- **Word definicji wyszukiwania** (tylko tryb nadzorowany)
- **Klawiatury predykcyjnej** (tylko tryb nadzorowany)
- **Korekty automatycznej** (tylko tryb nadzorowany)
- **Klawiatura sprawdzanie** (tylko tryb nadzorowany)
- **Skróty klawiaturowe** (tylko tryb nadzorowany)
<!--- - **Enterprise app trust settings modification** --->
- **Instalowanie aplikacji przy użyciu programu Apple Configurator i tylko iTunes** (tylko tryb nadzorowany)
- **Pobieranie aplikacji automatyczne** (tylko tryb nadzorowany)
- **Zmiany ustawień aplikacji Find My Friends** (tylko tryb nadzorowany)
- **Dostęp do sklepu iBooks** (tylko tryb nadzorowany)
- **Komunikaty aplikacji** (tylko tryb nadzorowany)
- **Podkasty** (tylko tryb nadzorowany)
- **Muzyka Apple** (tylko tryb nadzorowany)
- **iTunes radiowych** (tylko tryb nadzorowany)
- **Grupy dyskusyjne firmy Apple** (tylko tryb nadzorowany)
- **Centrum gier** (tylko tryb nadzorowany)
- **Traktuj AirDrop jako niezarządzane miejsca docelowego**

## <a name="android-for-work-support"></a>Android obsługę pracy

Począwszy od wersji Technical Preview 1702 można powiązać z konta Google dzierżawy hybrydowego zarządzania urządzeniami Przenośnymi. Dzięki temu można wykonać następujące czynności:

- Rejestrowanie [obsługiwane urządzenia z systemem Android](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012) jako Android for Work, tworzenie profili pracy na tych zarejestrowanych urządzeń
- Zatwierdź aplikacji w Play pracy magazynu, zsynchronizować je z konsoli programu Configuration Manager, a następnie wdrożyć je w profilach pracy urządzeń
- Tworzenie i wdrażanie elementów konfiguracji, aby skonfigurować ustawienia profilu i hasło pracy dla tych urządzeń
- Tworzenie i wdrażanie elementów zasad zgodności i profilów dostępu do zasobów dla systemu Android dla urządzeń z pracy, jak już dla urządzeń z systemem Android
- Przeprowadzić selektywne czyszczenie danych w systemie Android pracy urządzeń

Po zarejestrowaniu urządzenia jako Android for Work tworzy profil pracy na urządzeniu które Intune można zarządzać. Ten profil pracy istnieje side-by-side z osobistego profilu na urządzeniu z systemem Android. Użytkownicy mogą łatwo przełączać pracy profilu aplikacji oraz osobiste profilu aplikacji. Nie można zarządzać elementów w profilu osobistego. Aplikacje osobiste i dane pozostają niezarządzane. Configuration Manager ma pełną kontrolę nad profilu pracy i jego zawartość i można go usunąć z urządzenia.

Android for Work to platforma oddzielne z systemem Android, a następnie należy zdecydować, który formularz Zarządzanie dla urządzeń z systemem Android, które obsługują profile pracy.

### <a name="try-it-out"></a>Wypróbuj
W poniższych sekcjach opisano systemu Android do zarządzania pracą.

#### <a name="enable-android-for-work-management"></a>Włącz systemu Android do zarządzania pracą
1. Utwórz konto Google na https://accounts.google.com/SignUp do użycia jako dla systemu Android dla konta administratora pracy, która zostanie skojarzona z wszystkich systemu Android dla zadania zarządzania dla tej dzierżawy usługi Intune. Może to być konto Google współużytkowane przez administratorów, którzy zarządzają urządzeń z systemem Android. To jest konto Google, używana do zarządzania i publikowanie aplikacji w Play dla konsoli pracy w organizacji. Aby zatwierdzić aplikacji w Play pracy magazynu, aby zachować informacje o nazwę konta i hasło będą używają tego konta.
2. Włączanie rejestracji systemu Android przez powiązanie konto Google do dzierżawy usługi Intune zarządzane w programie Configuration Manager:
  1. Przejdź do **administracji** > **omówienie** > **usługi w chmurze** > **subskrypcje usługi Microsoft Intune** i wybierz swoją subskrypcję usługi Intune.
  2. Na wstążce kliknij **Konfiguruj platformy** > **Android** i upewnij się, że **włączyć Android rejestracji** jest zaznaczony.
  3. Na wstążce kliknij **Konfiguruj platformy** > **Android for Work**.
  4. W oknie dialogowym kliknij **skonfigurować Android for Work, w konsoli usługi Intune**. W przeglądarce sieci web zostanie otwarta konsola usługi Intune.
  5. Poświadczenia administratora usługi Intune można używać do logowania do portalu usługi Intune.
  6. Kliknij przycisk **Konfiguruj** otworzyć Android ze sklepu Google Play pracy witryny sieci Web.
  7. W witrynie firmy Google logowania wprowadź poświadczenia konta Google z kroku 1, a następnie podaj informacje o Twojej firmie.
3. Po powrocie do portalu usługi Intune Android for Work jest włączony i ma trzy opcje rejestracji dla systemu Android dla pracy urządzeń:
  - **Zarządzanie wszystkimi urządzeniami jako Android** — (wyłączony) wszystkich urządzeń z systemem Android urządzeń, które obsługują Android for Work, w tym zostanie zarejestrowane jako urządzenia z konwencjonalnej systemem Android
  - **Zarządzanie urządzeniami obsługiwane jako Android for Work** — (włączone) zarejestrowane wszystkie urządzenia Android for Work jako systemu Android dla urządzeń w pracy. Urządzenia Android, która nie obsługuje Android for Work jest zarejestrowany jako urządzenie Android konwencjonalnych.
  - **Zarządzanie urządzenia obsługiwane przez użytkowników tylko w tych grupach jako Android for Work** -(testowanie) umożliwia target Android do zarządzania pracą do określonych użytkowników. Tylko członkowie wybranych grup, którzy rejestrują urządzenia obsługującego Android for Work są rejestrowane jako systemu Android dla urządzeń w pracy. Wszystkie inne zarejestrowane jako urządzenia z systemem Android.
  
> [!NOTE]
> Zapobiega to znany problem **Zarządzaj obsługiwanych urządzeniach użytkowników tylko w tych grupach jako Android for Work** opcję działać zgodnie z oczekiwaniami. Urządzenia użytkowników w określonej usłudze Azure AD grupy będą rejestrowane jako Android zamiast Android for Work. Aby przetestować Android for Work, należy użyć **Zarządzanie wszystkich obsługiwanych urządzeń jako Android for Work**.


  Aby włączyć Android rejestracji pracy, musi wybierz jedną z opcji dolnej dwa. **Zarządzaj obsługiwanych urządzeniach użytkowników tylko w tych grupach jako Android for Work** opcji musi mieć należy najpierw zdefiniować grupy zabezpieczeń usługi Azure Active Directory.

Zobaczysz nazwę konta i nazwę organizacji w portalu usługi Intune po zakończeniu wiązania; w tym momencie możesz zamknąć obie przeglądarki.

#### <a name="approve-and-deploy-android-for-work-apps"></a>Zatwierdzanie i wdrażanie systemu Android dla aplikacji służbowych
Wykonaj poniższe kroki zatwierdzania aplikacji w Play pracy magazynu, zsynchronizować je z konsoli programu Configuration Manager i wdrażać je dla Android zarządzanych urządzeń w pracy. Wdrażanie aplikacji na profilach pracy użytkowników, musisz zatwierdzić aplikacji w Play do pracy, a następnie synchronizacji aplikacji za pomocą konsoli programu Configuration Manager.

1. Otwórz przeglądarkę i przejdź do: https://play.google.com/work.
2. Zaloguj się przy użyciu konta administratora usługi Google, związana z dzierżawy usługi Intune.
3. Przeglądanie w poszukiwaniu aplikacji, które chcesz wdrożyć w środowisku i kliknij przycisk **Zatwierdź** dla każdego z nich.
4. W konsoli programu Configuration Manager, przejdź do **administratora** > **omówienie** > **usługi w chmurze** > **Android for Work** i kliknij przycisk **synchronizacji**.
5. Poczekaj, aż do 10 minut zsynchronizować aplikacje, a następnie przejdź **Biblioteka oprogramowania** > **omówienie** > **Zarządzanie aplikacjami** > **informacji o licencji dla aplikacji ze sklepu**.
6. Kliknij aplikację synchronizowane z Play do pracy, a następnie kliknij przycisk **tworzenie aplikacji**.
7. Zakończ pracę kreatora i kliknij przycisk **Zamknij**.
8. Przejdź do **Biblioteka oprogramowania** > **omówienie** > **Zarządzanie aplikacjami** > **aplikacji**, wybierz systemu Android dla aplikacji służbowych i wdrażanie w zwykły sposób.

Aby zsynchronizować Play dla aplikacji do pracy z programem Configuration Manager, należy go zatwierdzić co najmniej jedną aplikację na Play pracy witryny sieci Web.

#### <a name="enroll-an-android-for-work-device"></a>Rejestrowanie dla systemu Android dla pracy urządzenia
Jak rejestrować systemu Android dla urządzeń pracy jest podobny do rejestracji dla systemu Android. Pobierz i uruchom aplikację Portal firmy dla systemu Android na swoim urządzeniu przenośnym. Pojawi się monit można utworzyć profilu pracy w ramach procesu rejestracji.  Po utworzeniu profilu pracy, musisz przełączyć się do zarządzanej wersji portalu firmy. Zarządzane Portal firmy jest oznaczane małych Aktówki pomarańczowy w prawym dolnym rogu.

#### <a name="create-and-deploy-a-configuration-item"></a>Tworzenie i wdrażanie elementu konfiguracji
Android for Work ma dwie grupy ustawienie pozycji konfiguracji:
- Hasło
- Profil pracy

Można skonfigurować treści współużytkują profili pracy, a także następujące elementy konfiguracji na urządzeniach z systemem Android 6 lub nowszy:
- Zachowanie aplikacji z prośbą o określonych uprawnień
- Określa, czy powiadomienia do aplikacji w obrębie profilu pracy są widoczne na ekranie blokady

To spróbować utworzyć element konfiguracji, za pomocą standardowych przepływu pracy, wybierz **Android for Work** na **ogólne** strony i skonfiguruj ustawienia dla każdej grupy ustawień, Dodawanie elementu konfiguracji do linii bazowej i wdrażanie w zwykły sposób. Te ustawienia zostaną zastosowane tylko na urządzeniach zarejestrowanych jako systemu Android do pracy oraz nie te, które zarejestrowane jako Android.

#### <a name="perform-selective-wipe"></a>Przeprowadzić selektywne czyszczenie danych
Urządzenia zarejestrowane jako Android for Work tylko można selektywnie wyczyścić ponieważ tylko Zarządzanie profilu pracy. Chroni to ten profil z spowoduje wyczyszczenie urządzenia. Wykonywanie czyszczenia selektywnego w systemie Android pracy urządzenia powoduje usunięcie profilu pracy, w tym wszystkie aplikacje i dane i wyrejestrowanie urządzenia.

Aby selektywnie wyczyścić Android pracy urządzenia, użyj normalnych [selektywnego czyszczenia urządzenia](https://docs.microsoft.com/sccm/mdm/deploy-use/wipe-lock-reset-devices#selective-wipe) w konsoli programu Configuration Manager.

#### <a name="known-issues-for-android-for-work"></a>Znane problemy dotyczące Android for Work
**Konfigurowanie synchronizacji harmonogramu Android o przyczynach profile poczty e-mail pracy je, aby nie można wdrożyć** jedną z opcji w interfejsie użytkownika programu ConfigMgr dla systemu Android dla profilów poczty e-mail pracy jest "Harmonogram". Na innych platformach dzięki temu administrator, aby skonfigurować harmonogram do synchronizowania poczty e-mail i innych danych konta poczty e-mail do wdrożonej w urządzeniach przenośnych. Jednak nie działać pracy profilów poczty e-mail dla systemu Android i wybranie opcji dowolnego innego niż "Nie skonfigurowano" spowoduje, że profil nie można wdrożyć na żadnych urządzeniach.
