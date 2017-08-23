---
title: Instalator poprawek | Dokumentacja firmy Microsoft
description: "Dowiedz się, kiedy i jak instalować aktualizacje za pomocą instalatora poprawek dla programu Configuration Manager."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f3058277-c597-4dac-86d1-41b6f7e62b36
caps.latest.revision: "9"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 8ffc7383e895909e6e6c4b8a7875fd5f0df2220e
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="use-the-hotfix-installer-to-install-updates-for-system-center-configuration-manager"></a>Instalowanie aktualizacji programu System Center Configuration Manager przy użyciu instalatora poprawek

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Niektóre aktualizacje programu System Center Configuration Manager nie są dostępne z usługi w chmurze firmy Microsoft i są pobierane tylko poza pasmem. Przykładem jest ograniczona wersja poprawki rozwiązującej określony problem.   
Kiedy należy zainstalować aktualizacja (lub poprawkę) otrzymaną od firmy Microsoft, a aktualizacja ma nazwę pliku, która kończy się rozszerzeniem **.exe** (nie **update.exe**), użyj instalatora poprawek, który jest dołączony pobranymi plikami tej poprawki do zainstalowania aktualizacji bezpośrednio na serwerze lokacji programu Configuration Manager.  

 Jeśli plik poprawki ma **. update.exe** rozszerzenie pliku, zobacz [używanie narzędzia rejestracji aktualizacji do importowania poprawek do programu System Center Configuration Manager](../../../core/servers/manage/use-the-update-registration-tool-to-import-hotfixes.md).  

> [!NOTE]  
>  W tym temacie przedstawiono ogólne wskazówki dotyczące sposobu instalacji poprawek, które aktualizują program System Center Configuration Manager. Ze szczegółami dotyczącymi konkretnej aktualizacji można zapoznać się w odpowiadającym jej artykule Bazy wiedzy na stronach pomocy technicznej firmy Microsoft.  

##  <a name="bkmk_Overview"></a>Omówienie poprawek programu Configuration Manager  
 Poprawki dla programu Configuration Manager są podobne jak w przypadku innych produktów firmy Microsoft, takich jak SQL Server, zawierają jedną poprawkę lub pakiet (zbiór) poprawek i są opisane w artykule bazy wiedzy Microsoft Knowledge Base.  

 Pojedyncze aktualizacje obejmują jedną konkretną aktualizację dla określonej wersji programu Configuration Manager.  
Pakiety aktualizacji zawierają wiele aktualizacji dla określonej wersji programu Configuration Manager.  
Gdy aktualizacja ma postać pakietu, nie można wybrać tylko niektórych aktualizacji z pakietu do zainstalowania.  

 Jeśli planowane jest tworzenie wdrożeń w celu instalowania aktualizacji na dodatkowych komputerach, należy zainstalować pakiet aktualizacji na serwerze centralnej lokacji administracyjnej lub serwerze lokacji głównej.  

 Uruchomienie pakietu aktualizacji powoduje wykonanie następujących czynności:  

-   Wyodrębnienie plików aktualizacji dla każdego odpowiedniego składnika z pakietu aktualizacji.  

-   Uruchomienie kreatora, który przeprowadzi Cię przez proces konfigurowania aktualizacji i opcji ich wdrażania.  

-   Po ukończeniu działania kreatora aktualizacje z pakietu, które znajdują zastosowanie do serwera lokacji, są instalowane na serwerze lokacji.  

Kreator tworzy także wdrożenia, których można użyć do zainstalowania aktualizacji na dodatkowych komputerach. Aktualizacje wdraża się na dodatkowych komputerach za pomocą obsługiwanej metody wdrażania, takiej jak pakiet wdrażania oprogramowania lub program Microsoft System Center Updates Publisher 2011.  

 Kreator podczas uruchamiania tworzy na serwerze lokacji plik **cab** na użytek programu Updates Publisher 2011. Opcjonalnie można skonfigurować kreatora do tworzenia także jednego lub więcej pakietów na użytek wdrażania oprogramowania. Te wdrożenia służy do instalowania aktualizacji na składnikach, takich jak klienci lub konsola programu Configuration Manager. Użytkownik może też instalować aktualizacje ręcznie na komputerach, na których jest uruchomiony klient programu Configuration Manager.  

 Można aktualizować następujące trzy grupy w programie Configuration Manager:  

-   Role serwera programu Configuration Manager, które obejmują:  

    -   Centralna lokacja administracyjna  

    -   Lokacja główna  

    -   Lokacja dodatkowa  

    -   Zdalny dostawca programu SMS  

-   Konsola programu Configuration Manager  

-   Klient programu Configuration Manager  

> [!NOTE]  
>  **Aktualizacje ról systemu lokacji** (w tym aktualizacje bazy danych lokacji i punkty dystrybucji w chmurze) są instalowane w ramach aktualizacji serwerów lokacji i usług przez Menedżera składników lokacji.  
>   
>  Niemniej jednak aktualizacje ściągających punktów dystrybucji są obsługiwane przez Menedżera dystrybucji, a Menedżer składników lokacji.  

 Każdy pakiet aktualizacji programu Configuration Manager jest plik samowyodrębniający .exe (SFX), który zawiera pliki, które są niezbędne do zainstalowania aktualizacji na stosownych składnikach programu Configuration Manager. Najczęściej samowyodrębniający się plik exe może zawierać następujące pliki:  

|Plik|Szczegóły|  
|----------|-------------|  
|&lt;Wersja produktu\>- QFE-KB&lt;identyfikator artykułu bazy wiedzy\>-&lt;platformy\>-&lt;języka\>.exe|To jest plik aktualizacji. Wierszem polecenia dla tego pliku zarządza program Updatesetup.exe.<br /><br /> Na przykład:<br />CM1511RTM-QFE-KB123456-X 64-ENU.exe|  
|Updatesetup.exe|Ten plik .msi otoki zarządza instalacją pakietu aktualizacji.<br /><br /> Po uruchomieniu aktualizacji program Updatesetup.exe wykrywa język wyświetlania komputera, na którym został uruchomiony. Domyślnie interfejs użytkownika aktualizacji wyświetla się w języku angielskim. Jeśli jednak język wyświetlania jest obsługiwany, interfejs użytkownika wyświetla się w lokalnym języku komputera.|  
|License_&lt;język\>.rtf|W stosownej sytuacji każda aktualizacja zawiera jeden lub więcej plików licencji dla obsługiwanych języków.|  
|&lt;Produkt i typ aktualizacji >-&lt;wersji produktu\>-&lt;identyfikator artykułu bazy wiedzy\>-&lt;platformy\>.msp|Gdy aktualizacja dotyczy konsol programu Configuration Manager lub klientów, pakiet aktualizacji zawiera osobne pliki poprawek (msp) Instalatora Windows.<br /><br /> Na przykład:<br /><br /> **Aktualizacja konsoli programu Configuration Manager:** ConfigMgr1511-AdminUI-KB1234567-i386.msp<br /><br /> **Aktualizacja klienta:** ConfigMgr1511-klienta KB1234567-i386.msp<br />ConfigMgr1511-klienta KB1234567-x64.msp|  

 Domyślnie pakiet aktualizacji rejestruje swoje działania w pliku dziennika .log na serwerze lokacji. Plik dziennika ma taką samą nazwę jak pakiet aktualizacji i jest zapisywany w folderze **%SystemRoot%/Temp** .  

 Podczas uruchamiania pakiet aktualizacji wyodrębnia plik o nazwie identycznej z nazwą pakietu aktualizacji do folderu tymczasowego na komputerze, a następnie uruchamia program Updatesetup.exe. Updatesetup.exe uruchamia aktualizacji oprogramowania programu Configuration Manager &lt;wersji produktu\> &lt;numer bazy wiedzy\> kreatora.  

 Odpowiednio do zakresu aktualizacji, Kreator tworzy serię podfolderów w folderze instalacji programu System Center Configuration Manager na serwerze lokacji. Struktura folderów wygląda mniej więcej tak:   
 **\\\\&lt;Nazwa serwera\>\SMS_&lt;kod lokacji\>\Hotfix\\&lt;numer bazy wiedzy\>\\&lt;typ aktualizacji\>\\&lt;platformy\>**.  

 Szczegółowe informacje o folderach z tej struktury folderów przedstawiono w poniższej tabeli:  

|Nazwa folderu|Więcej informacji|  
|-----------------|----------------------|  
|&lt;Nazwa serwera\>|To jest nazwa serwera lokacji, na którym jest uruchamiany pakiet aktualizacji.|  
|SMS_&lt;kod lokacji\>|Jest to nazwa udziału folderu instalacyjnego programu Configuration Manager.|  
|&lt;Numer artykułu bazy wiedzy\>|To jest numer identyfikatora artykułu Bazy wiedzy dla tego pakietu aktualizacji.|  
|&lt;Typ aktualizacji\>|Są to typy aktualizacji programu Configuration Manager. Dla każdego typu aktualizacji zawartego w pakiecie aktualizacji kreator tworzy osobny folder. Nazwy folderów odpowiadają typom aktualizacji. Obejmują one następujące czynności:<br /><br /> **Serwer**: Obejmuje aktualizacje serwerów lokacji, serwery bazy danych lokacji i komputerach z uruchomionym dostawcą programu SMS.<br /><br /> **Klient**: Obejmuje aktualizacje klienta programu Configuration Manager.<br /><br /> **AdminConsole**: Obejmuje aktualizacje konsoli programu Configuration Manager<br /><br /> Oprócz powyższych typów aktualizacji Kreator tworzy folder o nazwie **SCUP**. Ten folder nie odpowiada typowi aktualizacji, tylko zawiera plik cab programu Updates Publisher.|  
|&lt;Platformy\>|To jest folder zależny od platformy. Zawiera on pliki aktualizacji specyficzne dla określonego typu procesora.  Foldery noszą nazwy:<br /><br />-x64<br /><br /> -I386|  

##  <a name="bkmk_Install"></a> Jak instalować aktualizacje  
 Aby móc instalować aktualizacje, należy najpierw zainstalować pakiet aktualizacji na serwerze lokacji. Instalacja pakietu aktualizacji uruchamia kreatora instalacji tej aktualizacji. Kreator:  

-   Wyodrębnia pliki aktualizacji  

-   Pomaga w skonfigurowaniu wdrożeń  

-   Instaluje odpowiednie aktualizacje w ramach składników serwera lokalnego komputera  

Po zainstalowaniu pakietu aktualizacji na serwerze lokacji można zaktualizować dodatkowe składniki programu Configuration Manager. W poniższej tabeli opisano akcje dotyczące aktualizacji poszczególnych składników:  

|Składnik|Instrukcje|  
|---------------|------------------|  
|Serwer lokacji|Wdróż aktualizacje na zdalnym serwerze lokacji, jeśli nie chcesz instalować pakietu aktualizacji bezpośrednio na tym zdalnym serwerze lokacji.|  
|Baza danych lokacji|W przypadku zdalnych serwerów lokacji wdróż aktualizacje serwera, obejmujące aktualizację bazy danych lokacji, jeśli nie instalujesz pakietu aktualizacji bezpośrednio na tym zdalnym serwerze lokacji.|  
|Konsola programu Configuration Manager|Po wstępnej instalacji konsoli programu Configuration Manager można zainstalować aktualizacje konsoli programu Configuration Manager na każdym komputerze, na którym jest uruchomiona konsola. Nie można modyfikować pliki instalacyjne konsoli programu Configuration Manager w celu zastosowania aktualizacji podczas wstępnej instalacji konsoli.|  
|Zdalny dostawca programu SMS|Zainstaluj aktualizacje dla każdego wystąpienia dostawcy programu SMS uruchamianego na komputerze innym niż serwer lokacji, na którym został zainstalowany pakiet aktualizacji.|  
|Klienci programu Configuration Manager|Po wstępnej instalacji klienta programu Configuration Manager możesz zainstalować aktualizacje dla klienta programu Configuration Manager na każdym komputerze, na którym działa klient.|  

> [!NOTE]  
>  Można wdrażać aktualizacje tylko na komputerach z zainstalowanym klientem programu Configuration Manager.  

 W przypadku ponownej instalacji klienta, konsoli programu Configuration Manager lub dostawcy programu SMS, należy również ponownie zainstalować aktualizacje tych składników.  

 Skorzystaj z informacji w poniższych sekcjach ułatwiają instalowanie aktualizacji na poszczególnych składników programu Configuration Manager.  

###  <a name="bkmk_servers"></a> Aktualizowanie serwerów  
 Aktualizacje dla serwerów mogą obejmować aktualizacje **lokacji**, **site database**i komputerów z uruchomionym wystąpieniem **dostawcy programu SMS**:  

####  <a name="bkmk_site"></a>Aktualizowanie lokacji  
 Aby zaktualizować lokację programu Configuration Manager, można zainstalować pakiet aktualizacji bezpośrednio na serwerze lokacji lub można wdrożyć aktualizacje na serwerze lokacji po zainstalowaniu pakietu aktualizacji w innej lokacji.  

 Podczas instalowania aktualizacji na serwerze lokacji proces instalacji aktualizacji zarządza dodatkowymi działaniami, które są wymagane do zastosowania aktualizacji, takimi jak aktualizowanie ról systemu lokacji. Wyjątkiem jest baza danych lokacji. Informacje o tym, jak zaktualizować bazę danych lokacji, zamieszczono w poniższej sekcji.  

####  <a name="bkmk_database"></a>Zaktualizuj bazę danych lokacji  
 Aby zaktualizować bazę danych lokacji, proces instalacji uruchamia w pliku o nazwie **update.sql** w bazie danych lokacji. Proces aktualizacji można skonfigurować w celu automatycznego aktualizowania bazy danych lokacji albo można ręcznie zaktualizować bazę danych lokacji później.  

 **Automatyczna aktualizacja bazy danych lokacji**  

 Po zainstalowaniu pakietu aktualizacji na serwerze lokacji, można automatycznie zaktualizować bazy danych lokacji po zainstalowaniu aktualizacji serwera. Ta decyzja dotyczy tylko serwera lokacji, w którym jest instalowany pakiet aktualizacji i nie ma zastosowania do wdrożeń, które są tworzone w celu zainstalowania aktualizacji na zdalnych serwerach lokacji.  

> [!NOTE]  
>  Gdy użytkownik chce automatycznie zaktualizować bazy danych lokacji, proces aktualizacji bazy danych niezależnie od tego czy bazy danych znajduje się na serwerze lokacji lub na komputerze zdalnym.  

> [!IMPORTANT]  
>  Przed zaktualizowaniem bazy danych lokacji Utwórz kopię zapasową bazy danych lokacji. Aktualizacji bazy danych lokacji nie można odinstalować. Aby uzyskać informacje o sposobie tworzenia kopii zapasowej dla programu Configuration Manager, zobacz [kopii zapasowych i odzyskiwania dla programu System Center Configuration Manager](../../../protect/understand/backup-and-recovery.md).  

 **Ręczna aktualizacja bazy danych lokacji**  

 Jeśli wybierzesz nie automatycznie zaktualizować bazy danych lokacji po zainstalowaniu pakietu aktualizacji na serwerze lokacji, Aktualizacja serwera nie powoduje modyfikacji bazy danych na serwerze lokacji, na którym jest uruchamiany pakiet aktualizacji. Jednak wdrożenia korzystające z pakietu utworzonego w celu wdrożenia oprogramowania lub instalowane zawsze aktualizują bazę danych lokacji.  

> [!WARNING]  
>  Kiedy aktualizacja obejmuje aktualizacje zarówno serwera lokacji i bazy danych lokacji, aktualizacja nie działa do czasu ukończenia aktualizacji na serwerze lokacji i bazy danych lokacji. Dopóki aktualizacja nie zostanie zastosowana do bazy danych lokacji, lokacja znajduje się w stanie nieobsługiwanym.  

 **Aby ręcznie zaktualizować bazę danych lokacji:**  

1.  Na serwerze lokacji Zatrzymaj usługę SMS_SITE_COMPONENT_MANAGER, a następnie zatrzymaj usługę SMS_EXECUTIVE.  

2.  Zamknij konsolę programu Configuration Manager.  

3.  Uruchom skrypt aktualizacji o nazwie **update.sql** w bazie danych lokacji. Aby uzyskać informacje o sposobie uruchamiania skryptu aktualizującego bazę danych programu SQL Server zobacz dokumentację dla używanej wersji programu SQL Server, której użyjesz dla bazy danych serwera lokacji.  

4.  Uruchom ponownie usługi zatrzymane w poprzednich krokach.  

5.  Podczas instalowania pakietu aktualizacji wyodrębnia **update.sql** w następującej lokalizacji na serwerze lokacji:  **\\\\&lt;Nazwa serwera\>\SMS_&lt;kod lokacji\>\Hotfix\\&lt;numer bazy wiedzy\>\update.sql**  

####  <a name="bkmk_provider"></a>Aktualizacja komputera z uruchomionym dostawcą programu SMS  
 Po zainstalowaniu pakietu aktualizacji zawiera aktualizacje dla dostawcy programu SMS należy wdrożyć aktualizację na każdym komputerze z uruchomionym dostawcą programu SMS. Jedynym wyjątkiem od tej zasady jest wystąpienie dostawcy programu SMS zainstalowane wcześniej na serwerze lokacji, na którym jest instalowany pakiet aktualizacji. Po zainstalowaniu pakietu aktualizacji, jest aktualizowane lokalne wystąpienie dostawcy programu SMS na serwerze lokacji.  

 Jeśli zostanie usunięty i ponownie zainstalować dostawcę programu SMS na komputerze, należy ponownie zainstalować aktualizację dostawcy programu SMS na tym komputerze.  

###  <a name="BKMK_clients"></a>Aktualizacja klientów  
 Po zainstalowaniu aktualizacji, która zawiera aktualizacje dla klienta programu Configuration Manager jest wyświetlana opcja automatycznego uaktualnienia klientów instalacji aktualizacji lub ręcznego uaktualnienia ich w późniejszym czasie. Aby uzyskać więcej informacji na temat automatycznego uaktualniania klientów, zobacz [Uaktualnianie klientów komputerów z systemem Windows](https://technet.microsoft.com/library/mt627885.aspx).  

 Aktualizacje można wdrażać za pomocą programu Updates Publisher lub pakietu wdrożeniowego oprogramowania. Można też ręcznie zainstalować aktualizację na każdym kliencie. Więcej informacji o sposobie używania wdrożeń do instalowania aktualizacji znajduje się w sekcji [Wdrażanie aktualizacji programu Configuration Manager](#BKMK_Deploy) w tym temacie.  

> [!IMPORTANT]  
>  Po zainstalowaniu aktualizacji dla klientów i pakiet aktualizacji zawiera aktualizacje dla serwerów, należy te aktualizacje serwerów zainstalować również w lokacji głównej, do której są przypisani klienci.  

Aby ręcznie zainstalować aktualizację klienta, na każdym kliencie programu Configuration Manager, należy uruchomić **Msiexec.exe** i odwołuje się do pliku msp aktualizacji klienta specyficznego dla platformy.  

 Na przykład można użyć poniższego polecenia aktualizacji klienta. Ten wiersz polecenia powoduje uruchomienie programu MSIEXEC na komputerze klienckim i przywołuje plik msp, który został wyodrębniony przez pakiet aktualizacji na serwerze lokacji: **msiexec.exe /p \\ \\ &lt;ServerName\>\SMS_&lt;Kod_lokacji\>\Hotfix\\&lt;numer bazy wiedzy\>\Client\\&lt;platformy\>\\&lt;msp\> /L\*v &lt;logfile\>REINSTALLMODE = mous REINSTALL = ALL**  

###  <a name="BKMK_console"></a>Aktualizacja konsol programu Configuration Manager  
 Aby zaktualizować konsolę programu Configuration Manager, aktualizację należy zainstalować na komputerze, na którym jest uruchomiona konsola, po zakończeniu instalowaniu konsoli.  

> [!IMPORTANT]  
>  Po zainstalowaniu aktualizacji dla konsoli programu Configuration Manager, a pakiet aktualizacji zawiera aktualizacje dla serwerów, należy te aktualizacje serwerów zainstalować również w lokacji, który jest używany z konsoli programu Configuration Manager.  

Jeśli na komputerze, jest uruchomiony klient programu Configuration Manager:  

-   Możesz zainstalować aktualizację przy użyciu wdrożenia. Więcej informacji o sposobie używania wdrożeń do instalowania aktualizacji znajduje się w sekcji [Wdrażanie aktualizacji programu Configuration Manager](#BKMK_Deploy) w tym temacie.  

-   Jeśli zalogowano się bezpośrednio na komputerze klienckim, możesz uruchomić instalację interaktywnie.  

-   Możesz zainstalować aktualizację ręcznie na każdym komputerze. Aby ręcznie zainstalować aktualizację konsoli programu Configuration Manager, na każdym komputerze, na którym uruchomiona jest konsola programu Configuration Manager, można uruchomić Msiexec.exe i odwołać się do pliku *.msp aktualizacji konsoli programu Configuration Manager.  

Na przykład można użyć następujący wiersz polecenia, aby zaktualizować konsolę programu Configuration Manager. Ten wiersz polecenia powoduje uruchomienie programu MSIEXEC na komputerze i odwołuje się do pliku msp, który został wyodrębniony przez pakiet aktualizacji na serwerze lokacji: **msiexec.exe /p \\ \\ &lt;ServerName\>\SMS_&lt;Kod_lokacji\>\Hotfix\\&lt;numer bazy wiedzy\>\AdminConsole\\&lt;platformy\>\\&lt;msp\> /L\*v &lt;logfile\>REINSTALLMODE = mous REINSTALL = ALL**  

##  <a name="BKMK_Deploy"></a> Wdrażanie aktualizacji programu Configuration Manager  
 Po zainstalowaniu pakietu aktualizacji na serwerze lokacji można jedną z następujących trzech metod wdrożyć aktualizacje na dodatkowych komputerach.  

###  <a name="BKMK_DeploySCUP"></a>Zainstaluj aktualizacje za pomocą programu Updates Publisher 2011  
 Po zainstalowaniu pakietu aktualizacji na serwerze lokacji instalacji Kreator tworzy plik katalogu dla programu Updates Publisher, którego można użyć do wdrożenia aktualizacji na odpowiednich komputerach. Kreator zawsze tworzy ten katalog, nawet jeśli wybrano opcję **Użyj pakietu i programu do wdrożenia tej aktualizacji**.  

 Katalog dla programu Updates Publisher ma nazwę **SCUPCatalog.cab** i znajduje się w następującej lokalizacji na komputerze, na którym jest uruchamiany pakiet aktualizacji: **\\\\&lt;ServerName\>\SMS_&lt;Kod_lokacji\>\Hotfix\\&lt;numer bazy wiedzy\>\SCUP\SCUPCatalog.cab**  

> [!IMPORTANT]  
>  Ponieważ plik SCUPCatalog.cab jest tworzony za pomocą ścieżek, które są specyficzne dla serwera lokacji, w którym jest instalowany pakiet aktualizacji, nie można używać na innych serwerach lokacji.  

 Po zakończeniu pracy Kreatora wykaz można zaimportować do programu Updates Publisher, a następnie użycia aktualizacji oprogramowania programu Configuration Manager do wdrażania aktualizacji. Aby uzyskać informacji dotyczących programu Updates Publisher, zobacz [Updates Publisher 2011](http://go.microsoft.com/fwlink/p/?LinkID=83449) w bibliotece TechNet programu System Center 2012.  

 Aby zaimportować plik SCUPCatalog.cab do programu Updates Publisher i opublikować aktualizacje, należy użyć następującej procedury.  

##### <a name="to-import-the-updates-to-updates-publisher-2011"></a>Aby zaimportować aktualizacje do programu Updates Publisher 2011  

1.  Uruchom konsolę programu Updates Publisher, a następnie kliknij przycisk **importu**.  

2.  Na **zaimportować typu** strony Kreatora importowania oprogramowanie aktualizacji katalogu, wybierz **Określ ścieżkę do katalogu, aby zaimportować**, a następnie wskaż plik SCUPCatalog.cab.  

3.  Kliknij przycisk **dalej**, a następnie kliknij przycisk **dalej** ponownie.  

4.  W **ostrzeżenie o zabezpieczeniach — Weryfikacja katalogu** okno dialogowe, kliknij przycisk **Akceptuj**. Zamknij kreatora po zakończeniu.  

5.  W konsoli programu Updates Publisher wybierz aktualizację, którą chcesz wdrożyć, a następnie kliknij przycisk **publikowania**.  

6.  Na **opcji publikowania** strony publikowania Kreatora aktualizacji oprogramowania, wybierz **pełnej zawartości**, a następnie kliknij przycisk **dalej**.  

7.  Ukończ pracę kreatora, aby opublikować aktualizacje.  

###  <a name="BKMK_DeploySWDist"></a>Instalowanie aktualizacji metodą wdrażania oprogramowania  
 Po zainstalowaniu pakietu aktualizacji na serwerze lokacji w lokacji głównej lub centralnej lokacji administracyjnej można skonfigurować instalację kreatora, aby utworzyć pakiety aktualizacji dla wdrożenia oprogramowania. Następnie można wdrożyć każdy pakiet do kolekcji komputerów, które chcesz zaktualizować.  

 Aby utworzyć pakiet wdrożeniowy oprogramowania, na **skonfigurować wdrożenie aktualizacji oprogramowania** strony kreatora zaznacz pole wyboru dla każdej aktualizacji typu, który chcesz zaktualizować. Dostępne typy to między innymi serwery, konsole programu Configuration Manager i klienci. Dla każdego typu aktualizacji są tworzone oddzielnie pakiety.  

> [!NOTE]  
>  Pakiety dla serwerów zawierają aktualizacje następujących składników:  
>   
>  -   Serwer lokacji  
>  -   dostawcy programu SMS  
>  -   Baza danych lokacji  

 Następnie na stronie **Configure Software Update Deployment Method (Konfigurowanie metody wdrożenia aktualizacji oprogramowania)** kreatora wybierz opcję **I will use software distribution**(Użyję dystrybucji oprogramowania). To pole wyboru nakaże kreatorowi tworzy pakietu wdrożeniowego oprogramowania.  

 Po zakończeniu pracy Kreatora utworzone w konsoli programu Configuration Manager w pakiety można wyświetlić **pakiety** w węźle **Biblioteka oprogramowania** obszaru roboczego. Standardowej procedury można następnie użyć do wdrożenia pakiety oprogramowania na klientach programu Configuration Manager. Gdy pakiet jest uruchamiany na kliencie, instaluje aktualizacje odpowiednich składników programu Configuration Manager na komputerze klienckim.  

 Aby uzyskać informacje o sposobie wdrażania pakietów na klientach programu Configuration Manager, zobacz [pakietów i programów w programie System Center Configuration Manager](../../../apps/deploy-use/packages-and-programs.md).  

###  <a name="BKMK_DeployCollections"></a>Tworzenie kolekcji w celu wdrażania aktualizacji programu Configuration Manager  
 Można wdrożyć aktualizacje na odpowiednich klientach. Poniższe informacje mogą pomóc tworzenie kolekcji urządzeń dla różnych składników programu Configuration Manager.  

|Składnik programu Configuration Manager|Instrukcje|  
|----------------------------------------|------------------|  
|Serwer centralnej lokacji administracyjnej|Utwórz kwerendę członkostwa bezpośredniego i dodaj komputer serwera centralnej lokacji administracyjnej.|  
|Wszystkie serwery lokacji głównej|Utwórz kwerendę członkostwa bezpośredniego i dodaj każdy komputer serwera lokacji głównej.|  
|Wszystkie serwery lokacji dodatkowej|Utwórz kwerendę członkostwa bezpośredniego i dodaj każdy komputer serwera lokacji dodatkowej.|  
|Wszyscy klienci x86|Utwórz kolekcję o następujących kryteriach kwerendy:<br /><br /> **Wybierz \* z SMS_R_System inner join SMS_G_System_SYSTEM na SMS_G_System_SYSTEM. ResourceID = SMS_R_System.ResourceId gdzie SMS_G_System_SYSTEM. Typem systemu = "komputer PC oparty na X86"**|  
|Wszyscy klienci x64|Utwórz kolekcję o następujących kryteriach kwerendy:<br /><br /> **Wybierz \* z SMS_R_System inner join SMS_G_System_SYSTEM na SMS_G_System_SYSTEM. ResourceID = SMS_R_System.ResourceId gdzie SMS_G_System_SYSTEM. Typem systemu = "komputer PC oparty na X64"**|  
|Wszystkie komputery z uruchomioną konsoli programu Configuration Manager|Utwórz kwerendę członkostwa bezpośredniego i dodaj każdy komputer.|  
|Komputery zdalne z uruchomionym wystąpieniem dostawcy programu SMS|Utwórz kwerendę członkostwa bezpośredniego i dodaj każdy komputer.|  

> [!NOTE]  
>  Aby zaktualizować bazę danych lokacji, wdróż aktualizację na serwerze tej lokacji.  

 Aby uzyskać informacje dotyczące sposobu tworzenia kolekcji, zobacz [Jak tworzyć kolekcje w programie System Center Configuration Manager](../../../core/clients/manage/collections/create-collections.md).  
