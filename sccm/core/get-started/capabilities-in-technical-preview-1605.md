---
title: Funkcje w wersji zapoznawczej Technical Preview 1605 programu Configuration Manager
description: "Dowiedz się więcej o funkcjach dostępnych w wersji zapoznawczej Technical Preview programu System Center Configuration Manager, wersja 1605."
ms.custom: na
ms.date: 01/23/2017
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2bafd028-1923-4463-9e3e-ee41bc0c437b
caps.latest.revision: "36"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 8b3d472c586e704ee48e9825138c72f655d89492
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="capabilities-in-technical-preview-1605-for-system-center-configuration-manager"></a>Funkcje w wersji Technical Preview 1605 programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (wersja zapoznawcza Technical Preview)*

W tym artykule przedstawiono funkcje, które są dostępne w wersji Technical Preview programu System Center Configuration Manager, wersja 1605. Można zainstalować tę wersję, aby zaktualizować i dodać nowe funkcje do lokacji programu Configuration Manager technical preview.      Przed zainstalowaniem tej wersji technical Preview, przejrzyj temat wprowadzający [Technical Preview programu System Center Configuration Manager](../../core/get-started/technical-preview.md), aby zapoznać się z ogólne wymagania i ograniczenia dotyczące używania wersji technical preview, jak zaktualizować między wersjami i sposobu wyrazić swoją opinię na temat funkcji w wersji technical preview.  

 **Znane problemy w tej wersji Technical Preview:**  

-   Z 1605 Technical Preview Jeśli zaktualizować właściwości punktu zarządzania po jego zainstalowaniu, mogą występować błąd konsoli, co wymusza konsolę, aby zamknąć.  W takim przypadku można odinstalować punkt zarządzania i ponownie zainstaluj punkt zarządzania za pomocą odpowiednie ustawienia. Alternatywnie można zmodyfikować punktu zarządzania przed zainstalowaniem Technical Preview 1605.  

-   Gdy korzystanie ze Sklepu Windows dla firm funkcji z 1604 Technical Preview, a następnie uaktualnić Technical Preview 1605, nie będzie mógł wyświetlać dane dołączania. Wszystkie inne funkcjonalnie pozostaje uruchomiona. Jeśli użytkownik został załadowany z 1604 Technical Preview, użytkownik pozostanie został załadowany po zainstalowaniu Technical Preview 1605 i muszą podejmować żadnych dodatkowych czynności.  

 **Poniżej przedstawiono nowe funkcje, które można wypróbować z tą wersją.**  

##  <a name="BKMK_PerAppVPN"></a>Urządzenia sieci VPN dla systemu Windows 10 dla aplikacji  
 Dla urządzeń z systemem Windows 10 zarządzane przy użyciu programu Configuration Manager z usługą Intune możesz dodać listę aplikacji, które automatycznie otwarte połączenie sieci VPN, który został skonfigurowany za pomocą konsoli administracyjnej programu Configuration Manager. Istnieje możliwość ograniczenia ruchu sieci VPN do aplikacji, lub możesz zezwolić na cały ruch przez połączenie VPN.  

 **Wymagania dotyczące**:  

-   Program Configuration Manager z usługą Intune  

-   Profil sieci VPN systemu Windows 10, który został wdrożony co najmniej jedno urządzenie  

##  <a name="BKMK_InstallSU"></a>Ulepszenia sekwencja zadań instalacji aktualizacji oprogramowania  
 Do sekwencji zadań Zainstaluj aktualizacje oprogramowania zostały wprowadzone następujące udoskonalenia:  

-   Nową zmienną sekwencji zadań, SMSTSSoftwareUpdateScanTimeout, jest dostępna daje możliwość kontrolowania limitu czasu na skanowanie aktualizacji oprogramowania podczas kroku sekwencji zadań instalacji oprogramowania aktualizacji. Wartość domyślna to 30 minut.  

-   Zostały ulepszenia rejestrowania. Plik dziennika smsts.log będzie zawierać nowych wpisów dziennika, które odwołują się do innych plików dziennika, które ułatwią rozwiązywanie problemów podczas procesu instalacji aktualizacji oprogramowania.  

##  <a name="BKMK_PrepareConfigMgrClient"></a>Ulepszenia, aby przygotować klienta programu ConfigMgr dla kroku sekwencji zadań przechwytywania  
 Przygotuj klienta programu ConfigMgr krok teraz spowoduje całkowite usunięcie klienta programu Configuration Manager, a nie tylko usunięcie informacji o kluczu. Jeśli sekwencja zadań wdrażania przechwyconego obrazu systemu operacyjnego zainstaluje nowy klient programu Configuration Manager zawsze.  

##  <a name="BKMK_Grace"></a>Okres prolongaty dla wymaganych wdrożeń aplikacji  
 W niektórych przypadkach może być zapewniają użytkownikom więcej czasu w celu zainstalowania wymaganych wdrożeń aplikacji poza wszystkie terminy, które zostały skonfigurowane. Na przykład jeśli użytkownik końcowy zwrócił się tylko z urlopu, ich może być konieczne Zaczekaj, aż do postaci długiej jako zaległe aplikacji są zainstalowane wdrożeń. Jednak nadal natychmiast mogą zainstalować aplikację w dowolnym momencie, które mają.  

 Aby rozwiązać ten problem, można zdefiniować **okres prolongaty** przez wdrożenie ustawienia klienta programu Configuration Manager do kolekcji.  

 Aby skonfigurować okres prolongaty, należy wykonać następujące czynności:  

1.  Na **Agent komputera** strony ustawień klienta, należy skonfigurować nową właściwość **okres prolongaty wymuszania po wdrożeniu terminu wdrożenia (godziny)** z wartością pomiędzy **1** i **120** godzin.  

2.  W ramach nowego wdrożenia aplikacji lub we właściwościach istniejącego wdrożenia na **Planowanie** strony, zaznacz pole wyboru **Opóźnij wymuszenie dotyczące tego wdrożenia zgodnie z preferencjami użytkownika**, do okresu prolongaty zdefiniowanego w ustawieniach klienta.  

     Wszystkie wdrożenia, które mają to pole wyboru zaznaczone i które są przeznaczone dla urządzeń, na których wdrożono również ustawienie klienta będzie używać okresu prolongaty.  

 W tej wersji okres prolongaty, które można skonfigurować nie jest używany przez urządzenia klienckie. Skonfiguruj okres prolongaty, zaznacz pole wyboru aplikacja zostanie zainstalowana w pierwszym oknie-business skonfigurowanego przez użytkownika po upływie ostatecznego terminu.  

 Podobne opcje zostały dodane do Kreatora wdrażania aktualizacji oprogramowania, Kreator reguł wdrażania automatycznego i strony właściwości. Jednak te nie są obecnie implementowane w tej wersji technical preview.  

##  <a name="BKMK_Remote"></a>Nowe środowisko dla akcji urządzeniu zdalnym  
 Udoskonalono obsługę wykonywania akcji urządzenia zdalnego z konsoli programu Configuration Manager.  
Typowe akcje, takie jak **Wycofaj/wyczyść**, **resetowania kodu dostępu**, **zdalne blokowanie**, i **obejścia blokady aktywacji** można znaleźć w **akcje urządzeń zdalnych** menu użytkowcy **zasoby i zgodność** obszaru roboczego.  

 ![Nowe akcje urządzeń zdalnych zrzut ekranu](media/New-Remote-Device-Actions.png)  

 Stan dla każdego z tych działań można znaleźć w następujących miejscach:  

-   W okienku szczegółów, po wybraniu urządzenia z **urządzeń** węzła.  

-   Na **właściwości** strony dla urządzenia.  

-   Na stronie głównej **urządzeń** węzła (nie wszystkie kolumny mogą być widoczne domyślnie).  

 Aby uzyskać więcej informacji na temat obejścia blokady aktywacji systemu iOS, zobacz [Łatwiejsza ochrona urządzeń z blokady aktywacji obejścia dla programu Configuration Manager dla systemu iOS](/sccm/mdm/deploy-use/manage-ios-activation-lock), w szczególności **obejście obecnie znane problemy z blokady aktywacji w programu Configuration Manager Technical Preview** sekcji.  

##  <a name="BKMK_WSFB"></a>Sklep Windows dla aplikacji biznesowych  
 [Sklep Windows dla firm](https://www.microsoft.com/business-store) jest, gdzie można znaleźć i zakupić aplikacje dla Twojej organizacji, pojedynczo lub zbiorczo. Łącząc Sklep do programu Configuration Manager, można zarządzać aplikacjami zakupionymi zbiorczo z poziomu konsoli programu Configuration Manager, na przykład:  

-   Możesz zsynchronizować listę zakupionych aplikacji z programu Configuration Manager  

-   Aplikacje, które są synchronizowane są wyświetlane w konsoli programu Configuration Manager i można wdrażać je tak jak wszystkie inne aplikacje  

-   Co 24 godziny, Configuration Manager pobiera informacje o licencji aplikacji ze sklepu i można to sprawdzić w konsoli programu Configuration Manager  

 W wersji 1604 technical preview można zsynchronizować i wyświetlić aplikacje w Sklepie Windows dla firm w konsoli programu Configuration Manager. W tej wersji dodano możliwość tworzenia i wdrażania aplikacji programu Configuration Manager z aplikacji ze sklepu zsynchronizowane.  

### <a name="set-up-windows-store-for-business-synchronization"></a>Konfigurowanie Sklepu Windows dla firm synchronizacji  

1.  W usłudze Azure Active Directory należy zarejestrować programu Configuration Manager jako narzędzie do zarządzania "API sieci Web i/lub aplikacji sieci Web". Otrzymasz identyfikator klienta, który będzie potrzebny później.  

    1.  W węźle usługi Active Directory [https://manage.windowsazure.com](https://manage.windowsazure.com), wybierz w usłudze Azure Active Directory, a następnie kliknij przycisk **aplikacji** > **Dodaj**.  

    2.  Kliknij przycisk **Dodaj aplikację moją organizację**.  

    3.  Wprowadź nazwę aplikacji, wybierz pozycję **aplikacji sieci Web** i/lub **interfejsu API sieci Web**, następnie kliknij przycisk **dalej** strzałki.  

    4.  Wprowadź ten sam adres URL dla obu **adres URL logowania** i **identyfikator URI aplikacji**. Adres URL może być dowolny i nie musi prowadzić do faktycznego adresu. Na przykład można wprowadzić **https://&lt;domena > / sccm**.  

    5.  Ukończ pracę kreatora.  

2.  W usłudze Azure Active Directory Utwórz klucz klienta dla zarejestrowanego narzędzia do zarządzania.  

    1.  Wyróżnij utworzoną aplikację i kliknij przycisk **Konfiguruj**.  

    2.  W obszarze **klucze**, wybierz czas trwania z listy i kliknij przycisk **zapisać**. Spowoduje to utworzenie nowego klucza klienta. Nie opuścić tę stronę, dopóki nie zakończysz dołączania Sklepu Windows dla firm do programu Configuration Manager.  

3.  W Sklepie Windows dla firm należy skonfigurować programu Configuration Manager jako narzędzie do zarządzania magazynami.  

    1.  Otwórz [https://businessstore.microsoft.com/en-us/managementtools](https://businessstore.microsoft.com/managementtools) i zaloguj się w przypadku wyświetlenia monitu.  

    2.  Zaakceptuj warunki użytkowania, jeśli jest to wymagane.  

    3.  W obszarze **narzędzia do zarządzania**, kliknij przycisk **Dodaj narzędzie do zarządzania**.  

    4.  W **Wyszukaj narzędzie według nazwy**, wpisz nazwę aplikacji wcześniej utworzony w usłudze AAD, a następnie kliknij przycisk **Dodaj**.  

    5.  Kliknij przycisk **Aktywuj** obok zaimportowanej aplikacji.  

    6.  W **Pokaż aplikacje** kreatora, kliknij przycisk **tak** Jeśli chcesz zezwolić na można kupić aplikacji licencjonowanych w trybie offline.  

4.  Zakup co najmniej jedną aplikację ze Sklepu Windows dla firm.  

5.  W **administracji** obszaru roboczego w konsoli programu Configuration Manager, rozwiń węzeł **usługi w chmurze**, następnie kliknij przycisk **Sklep Windows dla firm.**  

6.  Na **Home** karcie **Utwórz** kliknij przycisk **Dodaj Sklepu Windows dla firm**.  

7.  Dodaj identyfikator dzierżawy, identyfikator klienta i klucz klienta z usługi Azure Active Directory, a następnie Ukończ pracę kreatora.  

8.  Gdy wszystko będzie gotowe, zobaczysz skonfigurowane konto **Sklepu Windows dla firm kont** listy w konsoli programu Configuration Manager.  

### <a name="try-it-out"></a>Wypróbuj  
 Spróbuj wykonać poniższe zadanie, a następnie Daj nam znać, jak Ci poszło za pomocą formularza opinii na [programu przekazywania opinii dotyczących programu Configuration Manager](https://connect.microsoft.com/ConfigurationManagervnext/ConfigMgr%20Customer%20Feedback) w witrynie Microsoft Connect:  

 Tworzenie i wdrażanie aplikacji programu Configuration Manager w Sklepie Windows dla firm w trybie offline licencjonowanej aplikacji.  

1.  W **Biblioteka oprogramowania** obszaru roboczego w konsoli programu Configuration Manager, rozwiń węzeł **Zarządzanie aplikacjami**, następnie kliknij przycisk **informacji o licencji dla aplikacji ze sklepu**.  

2.  Wybierz aplikację, którą chcesz wdrożyć, a następnie na **Home** karcie **Utwórz** kliknij przycisk **tworzenie aplikacji**.  

 Tworzenia aplikacji programu Configuration Manager zawierający Sklepu Windows dla aplikacji biznesowych. Można następnie wdrożyć i monitorować tej aplikacji, jak w przypadku innych aplikacji programu Configuration Manager.  

> [!IMPORTANT]  
>  Podczas tworzenia aplikacji programu Configuration Manager z pojedynczym typem wdrożenia aplikacji licencjonowanych w trybie offline, to można wdrożyć na urządzeniach, które są MDM zarządzane, a także zarządzać za pomocą klienta programu Configuration Manager. Jeśli spróbujesz wdrożenia aplikacji z wieloma typami wdrożeń, instalacja nie powiedzie się.  
>   
>  Obecnie nie można wdrożyć aplikacji licencjonowanych online z programem Configuration Manager.  

##  <a name="BKMK_VPP2"></a>Ogólne poprawki dotyczące aplikacje nabyte zbiorczo  

-   W tej wersji, aplikacjami zakupionymi zbiorczo w Sklepie Windows dla firm i aplikacji dla systemu iOS magazynu zostały skonsolidowane do tego samego widoku **informacji o licencji dla aplikacji do przechowywania**.  

-   Dla aplikacji systemu iOS zakupionymi zbiorczo, na karcie Apple Volume Purchase Program został usunięty z **pakiet aplikacji dla systemu iOS — przeglądarka** okno dialogowe, w kreatorze tworzenia aplikacji. Aby utworzyć aplikację zakupów zbiorczych dla systemu iOS, wykonaj następujące kroki:  

    1.  1.  W **Biblioteka oprogramowania** obszaru roboczego w konsoli programu Configuration Manager, rozwiń węzeł **Zarządzanie aplikacjami**, następnie kliknij przycisk **informacji o licencji dla aplikacji ze sklepu**.  

    2.  2.  Wybierz aplikację, którą chcesz wdrożyć, a następnie na **Home** karcie **Utwórz** kliknij przycisk **tworzenie aplikacji**.  

-   Lokalizacja, używaną do pobrania i przekaż token VPP firmy Apple dla aplikacjami zakupionymi zbiorczo w konsoli programu Configuration Manager została zmieniona. Teraz można to zrobić w **Admin** obszarze roboczym **usługi w chmurze** > **tokenów Program zakupu woluminu Apple** węzła.  

##  <a name="BKMK_VPP"></a>Ochrona danych przedsiębiorstwa (EDP)  
 Możesz utworzyć elementy konfiguracji, które pozwalają na wdrożenie zasad ochrony (EDP) danych przedsiębiorstwa, tym, co pozwala wybrać chronionych aplikacji, poziom ochrony EDP i jak znaleźć dane organizacji w sieci. Aby uzyskać więcej informacji na temat ochrony danych przedsiębiorstwa zobacz następujące tematy:  

-   [Chroń dane przedsiębiorstwa przy użyciu ochrony danych przedsiębiorstwa (EDP)](https://technet.microsoft.com/itpro/windows/keep-secure/protect-enterprise-data-using-edp)  

-   [Tworzenie i wdrażanie zasad ochrony (EDP) dane przedsiębiorstwa przy użyciu programu System Center Configuration Manager](https://technet.microsoft.com/itpro/windows/keep-secure/create-edp-policy-using-sccm)  

##  <a name="BKMK_End"></a>Użytkownicy końcowi mogą instalować aplikacje z portalu firmy  
 Lokalna Usługa zarządzania urządzeniami Przenośnymi została wprowadzona w System Center Configuration Manager w wersji 1511. W poprzednich wersjach, można wdrażać aplikacji dla urządzeń zarządzanych MDM systemu Windows 10 z celem wdrożenia **wymagane** zainstalować dla urządzeń zarządzanych MDM lokalnych.  

 W tej wersji, mogą obecnie wdrażać aplikacje z celem wdrożenia **dostępne** dla użytkowników lokalnych MDM zarządzanych komputerów z systemem Windows 10, a użytkownicy mogą teraz instalować te same aplikacje z portalu firmy.
W tej wersji technical preview Jeśli Portal firmy jest otwarty przez ponad 15 minut, użytkownik końcowy zostanie wyświetlony komunikat o błędzie. Aby obejść ten problem, uruchom ponownie Portal firmy.  

### <a name="before-you-start"></a>Przed rozpoczęciem  

#### <a name="server-prerequisites"></a>Wymagania wstępne serwera  

-   .NET 4.5 lub wyższej (wymaga ponownego uruchomienia)  

-   PowerShell 3.0 dla skryptu konfiguracji (wymaga ponownego uruchomienia)  

#### <a name="client-prerequisites"></a>Wymagania wstępne klienta  

-   Systemu Windows 10 Desktop 1511 (kompilacja 10586.218 systemu operacyjnego) lub nowszy  

#### <a name="general-prerequisites"></a>Ogólne wymagania wstępne  

-   Upewnij się, zostały ukończone [kroki przygotowania do zarządzania urządzeniami przenośnymi lokalnymi](https://technet.microsoft.com/library/mt613153.aspx) i [zarejestrowaniu urządzeń](https://technet.microsoft.com/library/mt627870.aspx).  

-   Stosowania najlepszych zainstalować środowisko podczas korzystania z portalu firmy, upewnij się, że programu Configuration Manager ma aktywnego połączenia w usłudze Microsoft Intune.  

-   Po wybraniu opcji rejestracji zbiorczej, należy skonfigurować koligację urządzenia użytkownika dla zarejestrowanych urządzeń przed podjęciem próby tego scenariusza.  

### <a name="configuration-steps"></a>Kroki konfiguracji  

#### <a name="install-the-application-catalog-roles-and-enable-mobile-device-management-support"></a>Zainstalowanie ról wykazu aplikacji i włączyć obsługę zarządzania urządzeniami przenośnymi  

1.  Dodawanie ról Usługa sieci Web wykazu aplikacji i witrynę sieci Web  

    1.  Wybierz **tryb HTTPS** i **Zezwalaj urządzeniom przenośnym na korzystanie z tego punktu usługi sieci Web katalogu aplikacji** opcji.  

    2.  Ograniczenia w tej wersji Technical Preview:  

        -   Przed wybraniem opcji, aby umożliwić urządzeniom przenośnym na łączenie odinstaluj wszelkie istniejące role katalogu aplikacji.  

        -   Upewnij się, istnieje tylko jeden zestaw ról wykazu aplikacji i role wspólnie znajdują się w systemie lokacji punktu rejestracji i ról punktu Proxy rejestracji.  

2.  Sprawdź, czy działają następujące składniki w węźle stan składnika w konsoli programu Configuration Manager:  

    -   **SMS_AWEBSVC_CONTROL_MANAGER**  

    -   **SMS_DMAPPSVC_CONTROL_MANAGER**  

    -   **SMS_DMCONTENTSVC_CONTROL_MANAGER**  

    -   **SMS_PORTALWEB_CONTROL_MANAGER**  

### <a name="configure-boundaries"></a>Konfigurowanie granic  
 Skonfiguruj wymagane granice dla intranetowe punkty dystrybucji.  

> [!NOTE]  
>  Tylko granice zakresów IPv4, są obsługiwane w tej chwili do zarządzania urządzeniami przenośnymi.  

### <a name="deploy-the-company-portal-application-and-configuration"></a>Wdrażanie aplikacji Portal firmy i konfiguracji  

1.  Użyj skryptu konfiguracji dołączone do wersji zapoznawczej technical preview do przygotowania wdrożenia aplikacji Portal firmy i konfiguracji:  

    1.  Otwórz okno polecenia programu PowerShell z podwyższonym poziomem uprawnień programu.  

    2.  Uruchom **set-executionPolicy RemoteSigned**  

    3.  Z folderu  **&lt;katalog instalacyjny programu SCCM\>\cd.latest\SMSSETUP\TOOLS\MDM** Uruchom **.\ConfigurationScript.ps1**  

     Skrypt konfiguracji wykonuje następujące czynności:  

    1.  Tworzy aplikacji programu Configuration Manager z systemu Windows aplikacja pakietu wdrożenia typu za pomocą **CompanyPortalOnPremisesMDM.appx** w tym samym folderze.  

    2.  Tworzy element konfiguracji i linii bazowej konfiguracji, który konfiguruje portalu firmy.  

    3.  Wdraża zarówno linii bazowej konfiguracji, jak i aplikacji, a następnie dodaje aplikację do wszystkich punktów dystrybucji.  

    > [!NOTE]  
    >  Jeśli role katalogu aplikacji nie znajdują się w lokacji głównej, należy wykonać następujące czynności:  
    >   
    >  -   W **zasoby i zgodność** obszaru roboczego, zlokalizuj **OnPremMDM Portal konfiguracji CI - adresów URL serwera** elementu konfiguracji  
    > -   Zmień **reguły zgodności** wartość do w pełni kwalifikowaną nazwą domeny systemu lokacji, w którym ról katalogu aplikacji znajdują się.  

2.  Po aplikacji Portal firmy i jego konfiguracja są wdrożone, należy sprawdzić, aplikacji i konfiguracji planu bazowego są zgodne dla określonego urządzenia za pomocą **wdrożeń** sekcji konsoli programu Configuration Manager. Portal firmy będzie wyświetlany jako **Portal firmy (wersja zapoznawcza Technical Preview)** w menu Start na urządzeniu.  

### <a name="try-it-out"></a>Wypróbuj  
 Spróbuj wykonać następujące zadania, a następnie Daj nam znać, jak Ci poszło za pomocą formularza opinii na [programu przekazywania opinii dotyczących programu Configuration Manager](https://connect.microsoft.com/ConfigurationManagervnext/ConfigMgr%20Customer%20Feedback) w witrynie Microsoft Connect:  

1.  Wdrażanie kilka aplikacji typy wdrożeń obsługiwane w kolekcji użytkowników z celem wdrożenia **dostępne**. Dla tej wersji technical preview aplikacje, które wymagają zatwierdzenia administratora nie są obsługiwane i nie będą wyświetlane w portalu firmy.  

2.  Użytkownicy mogą, a następnie Przeglądaj w poszukiwaniu i instalować aplikacje z portalu firmy.  

     Po otwarciu portalu firmy, zobaczą okno dialogowe uwierzytelniania o nazwie **System Center Configuration Manager** Określ poświadczenia użytkownika usługi Active Directory (albo w formie user@domain lub domena\użytkownik) do logowania.  

##  <a name="BKMK_SW1"></a>Nowe karty aktualizacji i systemów operacyjnych w programie Software Center  
 W tej wersji wprowadzono następujące zmiany zwiększające układ aplikacji programu Software Center:  

-   **Aplikacji** kartę podzielone na trzy oddzielne karty **aktualizacje**, **systemów operacyjnych** (który zarówno wcześniej znaleziono w **filtry** listy), i **aplikacji**.  

##  <a name="BKMK_ServerGroups"></a>Usługa grupy serwerów  
 Technical Preview programu System Center Configuration Manager, w wersji 1511, uwzględnione możliwość tworzenia kolekcji, w której wszystkie urządzenia w kolekcji tworzą grupę serwerów. Następnie można skonfigurować ustawienia grupy serwerów do użycia podczas wdrażania aktualizacji oprogramowania do grupy serwerów, kontroli procent komputerów, które zostały zaktualizowane w dowolnej chwili, i skonfigurować przed wdrożeniem i po wdrożeniu skrypty programu PowerShell do uruchamiania działań niestandardowych.  

 Technical Preview programu System Center Configuration Manager, wersja 1605, dodaje możliwość aktualizowania komputerów w grupie serwerów w określonej kolejności definiowanie, dodaje monitorowaniu do wyświetlenia stanu dla komputerów w grupie serwerów i zapewnia możliwość to wyczyszczenie blokad wdrożenia, który jest przydatne w przypadku klientów nie można zainstalować aktualizacji oprogramowania i uniemożliwiają innym klientom zainstalowanie ich aktualizacji oprogramowania.  

### <a name="try-it-out"></a>Wypróbuj  
 Spróbuj wykonać następujące zadania, a następnie Daj nam znać, jak Ci poszło za pomocą formularza opinii na [programu przekazywania opinii dotyczących programu Configuration Manager](https://connect.microsoft.com/ConfigurationManagervnext/ConfigMgr%20Customer%20Feedback) w witrynie Microsoft Connect:  

-   Mogę utworzyć kolekcję, która reprezentuje grupę serwera. Dla tego testu można skonfigurować reguł członkostwa zbieranie ma 2 maszyn w tej kolekcji.   

-   Można określić, że komputery w grupie serwerów zainstalować aktualizacje oprogramowania w określonej kolejności, w oparciu o ustawienia grupy serwerów dla kolekcji. Użyj przykładowych skryptów w procedurze, aby określić skrypty przed wdrożeniem i po wdrożeniu.  

-   Mogę wdrożyć aktualizacji oprogramowania do tej kolekcji. Przejrzyj pliki aby i end.txt (utworzone na podstawie przykładowe skrypty) w C:\temp i Sprawdź godziny rozpoczęcia i zakończenia wdrożenia na komputerach w grupie serwerów. Przejrzyj plik dziennika UpdatesDeployment.log, aby uzyskać więcej informacji.  

#### <a name="to-create-a-collection-for-a-server-group"></a>Aby utworzyć kolekcję grupy serwerów  

1.  [Utwórz kolekcję urządzeń](https://technet.microsoft.com/library/gg712295.aspx) zawierający komputery w grupie serwerów.  

2.  W **zasoby i zgodność** obszaru roboczego kliknij **kolekcje urządzeń**, kliknij prawym przyciskiem myszy kolekcję zawierającą komputery w grupie serwerów, a następnie kliknij przycisk **właściwości**.  

3.  Na **ogólne** wybierz opcję **wszystkie urządzenia są częścią tej samej grupy serwerów**, a następnie kliknij przycisk **ustawienia**.  

4.  Na **ustawienia grupy serwerów** Określ jeden z następujących ustawień:  

    -   **Zezwalaj na procent maszyny do aktualizacji w tym samym czasie**: Określa, że tylko niektórych odsetek klientów, są aktualizowane w dowolnym momencie. Jeśli na przykład kolekcja zawiera 10 klientów, a kolekcja jest skonfigurowana do aktualizowania 30% klientów w tym samym czasie, tylko 3 klientów zainstaluje aktualizacje oprogramowania w danym momencie.  

    -   **Zezwalaj na wiele maszyn do aktualizacji w tym samym czasie**: Określa, że tylko określonej liczby klientów są aktualizowane w dowolnym momencie.  

    -   **Określ sekwencję konserwacji**: Określa, że klienci w kolekcji będą zaktualizowane pojedynczo w sekwencji, które można skonfigurować. Klient zainstaluje tylko aktualizacje oprogramowania, po klienta, który znajduje się przed jej na liście zakończył instalowanie aktualizacji jej oprogramowania.  

5.  Określ, czy użyć skryptu przed wdrożeniem (opróżnianie węzła) czy skrypt po wdrożeniu (wznawianie węzła).  

    > [!TIP]  
    >  Poniżej przedstawiono przykłady, że można używać podczas testowania dla przed wdrożeniem i skryptów po wdrożeniu zapisujących bieżący czas do pliku tekstowego:  
    >   
    >  **Przed wdrożeniem**  
    >   
    >  `#Start`  
    >   
    >  `$a = Get-Date`  
    >   
    >  `Write-Output "Universal Time: " + $a.ToUniversalTime()  |`  
    >   
    >  `Out-File C:\temp\start.txt`  
    >   
    >  **Po wdrożeniu**  
    >   
    >  `#End`  
    >   
    >  `$a = Get-Date`  
    >   
    >  `Write-Output "Universal Time: " + $a.ToUniversalTime()  |`  
    >   
    >  `Out-File C:\temp\end.txt`  

#### <a name="to-deploy-software-updates-to-the-server-group-and-monitor-status"></a>Aby wdrożyć aktualizacje oprogramowania do grupy i monitorowanie stanu możliwości zarządzania serwerem  

1.  [Wdrażanie aktualizacji oprogramowania](https://technet.microsoft.com/library/gg712304.aspx) do kolekcji grupy serwera.  

2.  [Monitorowanie wdrożenia aktualizacji oprogramowania](https://technet.microsoft.com/library/gg712304.aspx). Oprócz standardowych widoków monitorowania dla wdrożenia aktualizacji oprogramowania nowy opis stanu jest wyświetlane, gdy klient oczekuje na jego Włącz instalacji aktualizacji oprogramowania. **Oczekiwanie na blokadę** jest wyświetlana dla tego nowego stanu.  

#### <a name="to-clear-the-deployment-locks-for-computers-in-a-server-group"></a>Aby wyczyścić blokad wdrożenia dla komputerów w grupie serwerów  

1.  W **zasoby i zgodność** obszaru roboczego kliknij **kolekcje urządzeń**i kliknij kolekcję, aby wyczyścić blokad wdrożenia.  

2.  Na **Home** karcie **wdrożenia** kliknij przycisk **wyczyść blokady wdrożenia grupy serwera**. Gdy klienci nie można zainstalować aktualizacji oprogramowania i uniemożliwiają innym klientom zainstalowanie ich aktualizacji oprogramowania, blokad wdrożenia można ręcznie wyczyścić.  

##  <a name="BKMK_ATP"></a>Obsługa usługi Windows Defender Advanced Threat Protection  
 Windows Defender Advanced Threat Protection (ATP) to nowa usługa, która pomaga firmom wykrywania, badanie i odpowiadać na zaawansowanych ataków w swoich sieciach. Dowiedz się więcej o [Windows Defender ATP](https://blogs.windows.com/windowsexperience/2016/03/01/announcing-windows-defender-advanced-threat-protection). Configuration Manager może pomóc dołączyć i monitorowanie zarządzanych urządzeń klienckich z systemem Windows 10 Anniversary Edition.  

### <a name="try-it-now"></a>Wypróbuj teraz!  
 Spróbuj wykonać następujące zadania, a następnie Daj nam znać, jak Ci poszło za pomocą formularza opinii na [programu przekazywania opinii dotyczących programu Configuration Manager](https://connect.microsoft.com/ConfigurationManagervnext/ConfigMgr%20Customer%20Feedback) w witrynie Microsoft Connect:  

-   Urządzenia zintegrowane z usługą online Windows Defender Advanced Threat Protection (ATP)  

-   Monitorowanie wdrożenia Windows Defender ATP do zarządzanych urządzeń  

 **Wymagania wstępne**  

-   Subskrypcja usługi online Windows Defender Advanced Threat Protection  

-   Klienci z systemem Windows 10 Anniversary Edition (kompilacja 14328 lub nowszej)  

-   Utwórz plik konfiguracji klienta dołączania  

    ##### <a name="how-to-create-an-onboarding-configuration-file"></a>Jak utworzyć plik konfiguracji dołączania  

    1.  Zaloguj się do usługi online Windows Defender ATP  

    2.  Polecenie **klienta dołączania** elementu menu  

    3.  Wybierz **System Center Configuration Manager** i kliknij przycisk **pakiet pobierania**.  

    4.  Pobierz plik archiwum skompresowany (.zip) i Wyodrębnij zawartość.  


##### <a name="onboard-devices-for-windows-defender-atp"></a>Urządzenia zintegrowane dla Windows Defender ATP  

1.  W konsoli programu Configuration Manager Przejdź **zasoby i zgodność** > **omówienie** > **programu Endpoint Protection** > **Windows Defender ATP zasady** i kliknij przycisk **utworzyć zasady usługi Windows Defender ATP**. Zostanie otwarty Kreator zasad systemu Windows Defender ATP.  

2.  Typ **nazwa** i **opis** dla Windows Defender ATP zasad i wybierz **dołączania**. Kliknij przycisk Dalej.  

3.  **Przeglądaj** do pliku konfiguracji dostarczane przez dzierżawcę usługi chmury Windows Defender ATP Twojej organizacji. Kliknij przycisk **Dalej**.  

4.  Określ próbki plików, są zbierane i udostępnione z zarządzanych urządzeń do analizy.  

    -   **Brak** — żadne pliki przykładowe są pobierane do analizy  

    -   **Przenośne pliki wykonywalne** — pliki takie jak program plików (.exe), łącze dynamicznie biblioteka (dll), pliki czcionki i podobnych plików, które można wykorzystać w cyberattacks są pobierane i udostępniane do analizy  

     Kliknij przycisk **Dalej**.  

5.  Przejrzyj podsumowanie, a następnie Zakończ pracę kreatora.  

6.  Teraz można wdrożyć zasady Windows Defender ATP na komputerach klienckich zarządzanych przez kliknięcie przycisku **Wdróż**.  

##### <a name="monitor-windows-defender-atp"></a>Monitor usługi Windows Defender ATP  

1.  W konsoli programu Configuration Manager Przejdź **monitorowanie** > **omówienie** > **zabezpieczeń** , a następnie kliknij przycisk **Windows Defender ATP**.  

2.  Przejrzyj pulpitu nawigacyjnego systemu Windows Defender Advanced Threat Protection.  

    -   **Stan wdrożenia agenta usługi Windows Defender** — liczbę i odsetek komputerów klientów zarządzanych kwalifikujących się z active został załadowany z zasad programu Windows Defender ATP  

    -   **Kondycja agenta programu Windows Defender ATP** — procent komputerów klienckich raportowanie stanu dla ich agenta Windows Defender ATP  

        -   **Dobra** — działa prawidłowo  

        -   **Nieaktywne** — żadne dane wysyłane do usługi w czasie  

        -   **Stan agenta** — nie jest uruchomiona usługa systemowa programu Agent w systemie Windows  

        -   **Nie został załadowany** — zasady zostały zastosowane, ale agent nie zgłosił dołączyć zasad  

##  <a name="BKMK_DHA"></a>Zaświadczanie o kondycji urządzenia lokalnego  
 Zaświadczanie o kondycji dla urządzeń z systemem Windows 10 można teraz skonfigurować do komunikacji za pomocą infrastruktury lokalnej. Administratorzy mogą określić, czy raportowania odbywa się za pośrednictwem chmury lub zasobów lokalnych. Jeśli lokalne jest wybrana na potrzeby raportowania zaświadczania o kondycji, adres URL można określić dla usługi. Dzięki temu komputery klienckie bez dostępu do Internetu włączyć i zarządzać urządzeniami przy użyciu zaświadczania o kondycji.  

### <a name="enable-health-attestation-for-on-premises-devices"></a>Włączanie zaświadczania o kondycji urządzeń lokalnych  
 W 1605 Naprawiono kilka błędów w wersji 1604 Technical Preview.  Aby wypróbować tę funkcję, należy skonfigurować usługę zaświadczania o kondycji lokalnej za pomocą ustawień agenta klienta.  

1.  W konsoli programu Configuration Manager Przejdź **administracji** > **omówienie** > **ustawień klienta**, a następnie ustaw **Użyj lokalnej usługi zaświadczania o kondycji** do **tak**.  

2.  Określ adres w polu **Adres URL lokalnej usługi zaświadczania o kondycji**, a następnie kliknij przycisk **OK**.  

##  <a name="BKMK_RestartOptions"></a>Nowe opcje dla klientów systemu Windows 10 ponownego uruchamiania po zainstalowaniu aktualizacji oprogramowania  
 Gdy aktualizacja oprogramowania wymaga ponowne uruchomienie jest wdrażany przy użyciu programu Configuration Manager i zainstalowany na komputerze, oczekuje na ponowne uruchomienie zostało zaplanowane i zostanie wyświetlone okno dialogowe ponownego uruchomienia. Obecnie dla systemu Windows 8 lub nowszym, jeśli zamknięcie lub ponowne uruchomienie komputera przy użyciu opcji zasilania systemu Windows (a nie z okna dialogowego ponownego uruchomienia), pozostaje okno dialogowe ponownego uruchomienia po ponownym uruchomieniu komputera, a komputer wymaga ponownego uruchomienia po osiągnięciu terminu. W tej wersji technical preview, opcja **zaktualizować i ponownie uruchom** i **aktualizacji i zamykania** będą dostępne na komputerach z systemem Windows 10 w opcji zasilania systemu Windows, gdy istnieje oczekujące ponowne uruchomienie komputera dla aktualizacji oprogramowania programu Configuration Manager. W przypadku skorzystania z dowolnej z tych opcji okno dialogowe ponownego uruchamiania nie zostanie wyświetlone po ponownym uruchomieniu komputera.  

##  <a name="BKMK_IMEI"></a>Wstępnie Zadeklaruj urządzenia należące do firmy z numerami IMEI lub iOS  
 Teraz możesz zidentyfikować urządzenia należące do firmy przez zaimportowanie ich stacji międzynarodowe numery identyfikujące (IMEI) urządzenia przenośne. Możesz przekazać plik wartości rozdzielanych przecinkami (.csv) zawierający numery IMEI lub możesz ręcznie wprowadzić informacje o urządzeniu.  Można również zaimportować numerów seryjnych urządzeń z systemem iOS.  Zaimportowane informacje ustawią własność rejestrowanych jako "Firmowe" urządzeń.  Licencji usługi Intune są nadal wymagane dla każdego użytkownika uzyskującego dostęp do usługi.  

### <a name="try-it-out"></a>Wypróbuj  
 Spróbuj wykonać następujące zadania, a następnie Daj nam znać, jak Ci poszło za pomocą formularza opinii na [programu przekazywania opinii dotyczących programu Configuration Manager](https://connect.microsoft.com/ConfigurationManagervnext/ConfigMgr%20Customer%20Feedback) w witrynie Microsoft Connect:  

-   Importowanie zestawu numerów IMEI w pliku CSV. Każdy wiersz może zawierać numer IMEI, a następnie pole szczegółów.  

-   Ręcznie zaimportować numery IMEI z konsoli programu Configuration Manager.  

-   Importowanie zestawu iOS numerów seryjnych w pliku CSV. Ponownie każdy wiersz zawiera wiele następuje żadnych szczegółów urządzenia.  

##### <a name="pre-declare-corporate-owned-devices-with-imei-or-ios-serial-number"></a>Wstępne deklarowanie urządzeń należących do przedsiębiorstwa przy użyciu numeru IMEI lub numeru seryjnego systemu iOS  

1.  W konsoli programu Configuration Manager Przejdź **zasoby i zgodność** > **— omówienie** > **wszystkie urządzenia należące** > **Pre-declared urządzeń**, a następnie kliknij przycisk **tworzenia urządzenia Pre-declared**. Zostanie otwarty Kreator Pre-declared urządzeń.  

2.  Określ, jak dodać informacje o urządzeniu:  

    -   **Przekaż plik CSV zawierający szczegóły i numery IMEI** — Aby przekazać listę liczb, zobacz krok nr 3.  

    -   **Ręcznie Dodaj szczegóły i numery IMEI** — Aby ręcznie wprowadzić informacje o, wpisz numer IMEI lub numer seryjny systemu iOS i szczegóły dla urządzeń, a następnie przejdź do kroku 4.  

3.  W przypadku przekazanych plików wyszukać plik CSV zawierający informacje do wstępnie Zadeklaruj urządzenia należące do firmy. Nazwa pliku musi mieć następujący format, z wyłączeniem górnym wierszu (udostępnione tylko do celów informacyjnych):  

    |**IMEI #**|**Seryjny systemu iOS**|**SYSTEM OPERACYJNY**|**Szczegóły**|
    |---|---|---|---|
    |123456789012345||SYSTEMU WINDOWS|Należące do firmy urządzenia z systemem Windows|
    |123456789012|A0BCD0EFGH0J|DLA SYSTEMU IOS|Urządzenia z systemem iOS należące do firmy|
    |123456789012346||ANDROID|Należące do firmy urządzenia z systemem Android|

     **Kolumny:**  

    -   Kolumna 1: Numer IMEI — albo IMEI numer lub iOS numer seryjny jest wymagany dla każdego wiersza  

    -   Kolumna 2: numeru seryjnego systemu iOS — tylko numery seryjne iOS może być wstępnie zadeklarowane. Użyj numeru IMEI dla innych platform urządzenia  

    -   Kolumna 3: System operacyjny urządzenia (wymagane wielkości liter):  

        -   IOS — wszystkie urządzenia z systemem iOS  

        -   System WINDOWS — zawiera Windows Phone, Windows 10 Mobile i komputerów z systemem Windows  

        -   ANDROID — wszystkie urządzenia z systemem Android  

    -   Kolumna 4: Szczegóły — informacje o urządzeniu dodatkowe, która jest wyświetlana w konsoli programu Configuration Manager  

     Kliknij przycisk **Dalej**.  

4.  Przejrzyj wyniki importowania z pliku. Wcześniej zaimportowanych IMEI lub numery seryjne ma ich szczegóły zaktualizowano o nowe szczegółowe informacje.  Kliknij przycisk **dalej** kontynuowanie lub **ponownie** do zachowania zaktualizowanych szczegółów, a następnie Zakończ pracę kreatora.  
