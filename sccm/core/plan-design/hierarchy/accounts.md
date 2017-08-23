---
title: "Konta używane przez program Configuration Manager | Dokumentacja firmy Microsoft"
description: "Identyfikowania i zarządzania nim grup systemu Windows oraz kont w programie System Center Configuration Manager."
ms.custom: na
ms.date: 2/9/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 72d7b174-f015-498f-a0a7-2161b9929198
caps.latest.revision: "7"
caps.handback.revision: "0"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: a776667cc9f24bd4a468afea76e466c34ce66864
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="accounts-used-in-system-center-configuration-manager"></a>Konta używane w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Poniższe informacje umożliwiają poznanie grup systemu Windows oraz kont używanych w programie System Center Configuration Manager, sposobu ich używania i wszystkich wymagań.  

## <a name="windows-groups-that-configuration-manager-creates-and-uses"></a>Grupy systemu Windows tworzone i używane w programie Configuration Manager  
 Menedżer konfiguracji automatycznie tworzy, a w wielu przypadkach również automatycznie obsługuje, następujące grupy systemu Windows.  

> [!NOTE]  
>  W przypadku programu Configuration Manager tworzy grupę na komputerze, który jest członkiem domeny, grupa jest lokalną grupą zabezpieczeń. Jeżeli komputer jest kontrolerem domeny, grupa jest lokalną grupą domeny udostępnianą między wszystkimi kontrolerami w domenie.  


### <a name="configmgrcollectedfilesaccess"></a>ConfigMgr_CollectedFilesAccess  
Program Configuration Manager używa tej grupy, aby udzielić dostępu do wyświetlania plików zebranych w zapasach oprogramowania.  

Poniższa tabela zawiera listę dodatkowych szczegółów dotyczących tej grupy:  

|Szczegóły|Więcej informacji|  
|------------|----------------------|  
|Typ i lokalizacja|Ta grupa jest lokalną grupą zabezpieczeń utworzoną na serwerze lokacji głównej.<br /><br /> Po odinstalowaniu lokacji ta grupa nie zostanie automatycznie usunięta. Należy go ręcznie usunąć.|  
|Członkostwo|Menedżer konfiguracji automatycznie zarządza członkostwem grupy. Członkostwo obejmuje użytkowników administracyjnych z uprawnieniem **Wyświetl zgromadzone pliki** w zabezpieczanym obiekcie **Kolekcja** za pośrednictwem przypisanej roli zabezpieczeń.|  
|Uprawnienia|Domyślnie ta grupa ma **odczytu** uprawnienia do folderu na serwerze lokacji: **%path%\Microsoft Configuration Manager\sinv.box\FileCol**.|  

### <a name="configmgrdviewaccess"></a>ConfigMgr_DViewAccess  
 Ta grupa jest lokalną grupą zabezpieczeń tworzącą na serwerze bazy danych lokacji lub serwerze repliki bazy danych programu Configuration Manager. Nie jest obecnie używany, ale jest zarezerwowany do użytku w przyszłości.  

### <a name="configmgr-remote-control-users"></a>Użytkownicy funkcji zdalnego sterowania programu ConfigMgr  
 Narzędzia zdalne programu Configuration Manager użycie tej grupy do przechowywania kont i grup, które można skonfigurować na liście dozwolonych osób przeglądających, który jest przypisany do każdego klienta.  

 Poniższa tabela zawiera listę dodatkowych szczegółów dotyczących tej grupy:  

|Szczegóły|Więcej informacji|  
|------------|----------------------|  
|Typ i lokalizacja|Ta grupa jest lokalną grupą zabezpieczeń utworzoną w kliencie programu Configuration Manager po otrzymaniu przez klienta zasad, włączenia narzędzi zdalnych.<br /><br /> Po wyłączeniu narzędzi zdalnych na kliencie ta grupa nie zostanie automatycznie usunięta. Należy go ręcznie usunąć z każdego komputera klienckiego.|  
|Członkostwo|Domyślnie w tej grupie nie ma żadnych członków. Użytkownicy zostaną automatycznie dodani do tej grupy po dodaniu ich do listy dozwolonych osób przeglądających.<br /><br /> Za pomocą listy dozwolonych osób przeglądających można zarządzać członkostwem w tej grupie bez konieczności bezpośredniego dodawania do niej użytkowników ani grup.<br /><br /> Oprócz dopuszczonych podglądów, użytkownik administracyjny musi mieć **zdalnego sterowania** uprawnienia do **kolekcji** obiektu. To uprawnienie można przypisać za pomocą roli zabezpieczeń zdalnego operatora narzędzi.|  
|Uprawnienia|Domyślnie ta grupa nie ma uprawnień do dowolnej lokalizacji na komputerze. Jest on używany tylko do przechowywania listy dozwolonych osób przeglądających.|  

### <a name="sms-admins"></a>Administratorzy programu SMS  
 Program Configuration Manager używa tej grupy, aby udzielić dostępu do dostawcy programu SMS za pomocą Instrumentacji zarządzania Windows (WMI). Dostęp do dostawcy programu SMS jest wymagany do wyświetlania i modyfikowania obiektów w konsoli programu Configuration Manager.  

> [!NOTE]  
>  Konfiguracja administracji opartej na rolach użytkownicy administracyjni Określa, które obiekty mogą wyświetlać i zarządzać nimi przy użyciu konsoli programu Configuration Manager.  

 Poniższa tabela zawiera listę dodatkowych szczegółów dotyczących tej grupy:  

|Szczegóły|Więcej informacji|  
|------------|----------------------|  
|Typ i lokalizacja|Ta grupa jest lokalną grupą zabezpieczeń utworzoną na każdym komputerze, który ma dostawcę programu SMS.<br /><br /> Po odinstalowaniu lokacji ta grupa nie zostanie automatycznie usunięta. Należy go ręcznie usunąć.|  
|Członkostwo|Menedżer konfiguracji automatycznie zarządza członkostwem grupy. Domyślnie każdy użytkownik administracyjny w hierarchii oraz konto komputera serwera lokacji należą do grupy administratorów programu SMS na każdym komputerze dostawcy programu SMS w lokacji.|  
|Uprawnienia|Prawa i uprawnienia administratorów programu SMS są ustawiane w przystawce MMC sterowania usługą WMI. Domyślnie grupa Administratorzy SMS ma przyznane uprawnienia **włączanie konta** i **Włączanie zdalne** w przestrzeni nazw Root\SMS. Użytkownicy uwierzytelnieni mają **wykonywanie metod**, **zapis dostawcy**, i **włączanie konta**.<br /><br /> Użytkownicy administracyjni używający zdalnej konsoli programu Configuration Manager wymagają uprawnień modelu DCOM zdalnej aktywacji na komputerze serwera lokacji oraz komputerze dostawcy programu SMS. W celu ułatwienia administracji zaleca się przyznanie tych uprawnień administratorom programu SMS, a nie bezpośrednio użytkownikom lub grupom. Aby uzyskać więcej informacji, zobacz sekcję [Konfigurowanie uprawnień modelu DCOM dotyczących zdalnych konsol programu Configuration Manager](../../../core/servers/manage/modify-your-infrastructure.md#BKMK_ConfigDCOMforRemoteConsole) w temacie [Modyfikowanie infrastruktury programu System Center Configuration Manager](../../../core/servers/manage/modify-your-infrastructure.md).|  

### <a name="smssitesystemtositeserverconnectionmpltsitecode"></a>SMS_SiteSystemToSiteServerConnection_MP_&lt;kod_lokacji\>  
 Punkty zarządzania programu Configuration Manager, sterowane zdalnie z serwera lokacji używają tej grupy do łączenia z bazą danych lokacji. Ta grupa umożliwia punktowi zarządzania dostęp do folderów skrzynki odbiorczej na serwerze lokacji i w bazie danych lokacji.  

 Poniższa tabela zawiera listę dodatkowych szczegółów dotyczących tej grupy:  

|Szczegóły|Więcej informacji|  
|------------|----------------------|  
|Typ i lokalizacja|Ta grupa jest lokalną grupą zabezpieczeń utworzoną na każdym komputerze, który ma dostawcę programu SMS.<br /><br /> Po odinstalowaniu lokacji ta grupa nie zostanie automatycznie usunięta. Należy go ręcznie usunąć.|  
|Członkostwo|Menedżer konfiguracji automatycznie zarządza członkostwem grupy. Domyślnie członkostwo obejmuje konta komputerów zdalnych, na których znajduje się punkt zarządzania dla danej lokacji.|  
|Uprawnienia|Domyślnie ta grupa ma **odczytu**, **odczytu & wykonać**, i **wyświetlanie zawartości folderu** uprawnienia do **%path%\Microsoft Configuration Manager\inboxes** folderu na serwerze lokacji. Ta grupa ma dodatkowe uprawnienie **zapisu** w podfolderach należących do **skrzynek odbiorczych** w których punkt zarządzania zapisuje dane klienta.|  

### <a name="smssitesystemtositeserverconnectionsmsprovltsitecode"></a>SMS_SiteSystemToSiteServerConnection_SMSProv_&lt;kod_lokacji\>  
 Sterowane zdalnie z serwera lokacji komputery dostawcy programu SMS programu Configuration Manager, użyj tej grupy do łączenia się z serwerem lokacji.  

 Poniższa tabela zawiera listę dodatkowych szczegółów dotyczących tej grupy:  

|Szczegóły|Więcej informacji|  
|------------|----------------------|  
|Typ i lokalizacja|Ta grupa jest lokalną grupą zabezpieczeń utworzoną na serwerze lokacji.<br /><br /> Po odinstalowaniu lokacji ta grupa nie zostanie automatycznie usunięta. Należy go ręcznie usunąć.|  
|Członkostwo|Menedżer konfiguracji automatycznie zarządza członkostwem grupy. Domyślnie członkostwo obejmuje konto komputera lub konto użytkownika domeny, który służy do łączenia się z serwerem lokacji z każdego komputera zdalnego, z zainstalowanym dostawcą programu SMS dla lokacji.|  
|Uprawnienia|Domyślnie ta grupa ma **odczytu**, **odczytu & wykonać**, i **wyświetlanie zawartości folderu** uprawnienia do **%path%\Microsoft Configuration Manager\inboxes** folderu na serwerze lokacji. Ta grupa ma dodatkowe uprawnienie **zapisu** lub uprawnienia **zapisu** i **Modyfikuj** w podfolderach należących do **skrzynek odbiorczych** do których dostawca programu SMS wymaga dostępu.<br /><br /> Ta grupa ma również **odczytu**, **odczytu & wykonać**, **wyświetlanie zawartości folderu**, **zapisu**, i **Modyfikuj** uprawnienia do folderów poniżej **%path%\Microsoft Configuration Manager\OSD\boot** i **odczytu** uprawnienia do folderów poniżej **%path%\Microsoft Configuration Manager\OSD\Bin** na serwerze lokacji.|  

### <a name="smssitesystemtositeserverconnectionstatltsitecode"></a>SMS_SiteSystemToSiteServerConnection_Stat_&lt;kod_lokacji\>  
 Menedżer wysyłania plików na komputerach systemu zdalnego lokacji programu Configuration Manager używa tej grupy do łączenia się z serwerem lokacji.  

 Poniższa tabela zawiera listę dodatkowych szczegółów dotyczących tej grupy:  

|Szczegóły|Więcej informacji|  
|------------|----------------------|  
|Typ i lokalizacja|Ta grupa jest lokalną grupą zabezpieczeń utworzoną na serwerze lokacji.<br /><br /> Po odinstalowaniu lokacji ta grupa nie zostanie automatycznie usunięta. Należy go ręcznie usunąć.|  
|Członkostwo|Menedżer konfiguracji automatycznie zarządza członkostwem grupy. Domyślnie członkostwo obejmuje konto komputera lub konto użytkownika domeny używane do łączenia się z serwerem lokacji z każdego komputera zdalnego systemu lokacji z uruchomionym Menedżerem wysyłania plików.|  
|Uprawnienia|Domyślnie ta grupa ma **odczytu**, **odczytu & wykonać**, i **wyświetlanie zawartości folderu** uprawnienia do **%path%\Microsoft Configuration Manager\inboxes** folderze i jego podfolderach należących do tej lokalizacji na serwerze lokacji. Ta grupa ma dodatkowe uprawnienia **zapisu** i **Modyfikuj** do **%path%\Microsoft Configuration Manager\inboxes\statmgr.box** folderu na serwerze lokacji.|  

### <a name="smssitetositeconnectionltsitecode"></a>SMS_SiteToSiteConnection_&lt;kod_lokacji\>  
 Configuration Manager używa tej grupy, aby włączyć replikację opartą na plikach między lokacjami w hierarchii. Dla każdej lokacji zdalnej, która bezpośrednio przesyła pliki do tej witryny, ta grupa ma konta skonfigurowane jako **konta replikacji plików**.  

 Poniższa tabela zawiera listę dodatkowych szczegółów dotyczących tej grupy:  

|Szczegóły|Więcej informacji|  
|------------|----------------------|  
|Typ i lokalizacja|Ta grupa jest lokalną grupą zabezpieczeń utworzoną na serwerze lokacji.|  
|Członkostwo|Po zainstalowaniu nowej lokacji podrzędnej względem innej lokacji programu Configuration Manager automatycznie dodaje konto komputera nowej lokacji do grupy na serwerze lokacji nadrzędnej. Menedżer konfiguracji również dodaje konto komputera lokacji nadrzędnej do grupy na serwerze nowej lokacji. Jeśli określisz inne konto transferów opartych na plikach, należy dodać to konto do grupy na docelowym serwerze lokacji.<br /><br /> Po odinstalowaniu lokacji ta grupa nie zostanie automatycznie usunięta. Należy go ręcznie usunąć.|  
|Uprawnienia|Domyślnie ta grupa ma **Pełna kontrola** do **%path%\Microsoft Configuration Manager\inboxes\despoolr.box\receive** folderu.|  

## <a name="accounts-that-configuration-manager-uses"></a>Konta używane w programie Configuration Manager  
 Można skonfigurować następujące konta programu Configuration Manager.  

### <a name="active-directory-group-discovery-account"></a>Konto odnajdywania grup usługi Active Directory  
 **Konto odnajdywania grup usługi Active Directory** służy do odnajdywania lokalnych, globalnych i uniwersalnych grup zabezpieczeń, członkostwa w tych grupach oraz członkostwa w grupach dystrybucyjnych z określonych lokalizacji w usługach domenowych w usłudze Active Directory. Grupy dystrybucyjne nie są odnajdywane jako zasoby grupy.  

 To konto może być kontem komputera serwera lokacji, który przeprowadza odnajdywanie, lub kontem użytkownika systemu Windows. Musi mieć uprawnienie dostępu **Odczyt** do lokalizacji usługi Active Directory określonych do odnajdywania.  

### <a name="active-directory-system-discovery-account"></a>Konto odnajdywania systemu usługi Active Directory  
 **Konto odnajdywania systemu usługi Active Directory** służy do odnajdywania komputerów z określonych lokalizacji w Usługach domenowych Active Directory.  

 To konto może być kontem komputera serwera lokacji, który przeprowadza odnajdywanie, lub kontem użytkownika systemu Windows. Musi mieć uprawnienie dostępu **Odczyt** do lokalizacji usługi Active Directory określonych do odnajdywania.  

### <a name="active-directory-user-discovery-account"></a>Konto odnajdywania użytkowników usługi Active Directory  
 **Konto odnajdywania użytkowników usługi Active Directory** służy do odnajdywania kont użytkowników z określonych lokalizacji w usługach domenowych Active Directory.  

 To konto może być kontem komputera serwera lokacji, który przeprowadza odnajdywanie, lub kontem użytkownika systemu Windows. Musi mieć uprawnienie dostępu **Odczyt** do lokalizacji usługi Active Directory określonych do odnajdywania.  

### <a name="active-directory-forest-account"></a>Konto lasu usługi Active Directory  
 **Konto lasu usługi Active Directory** służy do odnajdywania infrastruktury sieci z lasów usługi Active Directory. Centralne Lokacje administracyjne i lokacje główne również używać do publikowania danych lokacji w usługach domenowych Active Directory dla lasu.  

> [!NOTE]  
>  Lokacje dodatkowe zawsze publikują dane w usłudze Active Directory przy użyciu konta komputera serwera lokacji dodatkowej.  

> [!NOTE]  
>  Konto lasu usługi Active Directory musi być kontem globalnym do odnajdywania i publikowania w niezaufanych lasach. Jeśli nie używasz konta komputera serwera lokacji, można wybrać tylko konto globalne.  

 To konto musi mieć uprawnienia do **odczytu** w każdym lesie usługi Active Directory, w którym ma zostać przeprowadzone odnajdywanie infrastruktury sieci.  

 To konto musi mieć uprawnienia **Pełna kontrola** w kontenerze zarządzania systemem oraz wszystkie jego obiekty podrzędne w każdym lesie usługi Active Directory, w którym będą publikowane dane lokacji.  

### <a name="asset-intelligence-synchronization-point-proxy-server-account"></a>Konto serwera proxy punktu synchronizacji analizy zasobów  
 Punkt synchronizacji analizy zasobów używa **konto synchronizacji Asset Intelligence punktu serwera Proxy serwera** dostęp do Internetu za pośrednictwem serwera proxy serwera lub zapory wymagających dostępu uwierzytelnionego.  

> [!IMPORTANT]  
>  Określ konto, które ma najniższe możliwe uprawnienia do wymaganego serwera proxy lub zapory.  

### <a name="certificate-registration-point-account"></a>Konto punktu rejestracji certyfikatu  
 **Konto punktu rejestracji certyfikatu** łączy punkt rejestracji certyfikatu z bazą danych programu Configuration Manager. Domyślnie jest używane konto komputera serwera punktu rejestracji certyfikatu, ale można skonfigurować konto użytkownika zamiast tego. Konto użytkownika należy zawsze określić, gdy punkt rejestracji certyfikatu znajduje się w niezaufanej domenie na serwerze lokacji. To konto wymaga jedynie **odczytu** dostęp do bazy danych lokacji, ponieważ systemu komunikatów o stanie obsługuje zadania zapisu.  

### <a name="capture-operating-system-image-account"></a>Konto przechwytywania obrazu systemu operacyjnego  
 Program Configuration Manager używa **konta przechwytywania obrazu systemu operacyjnego** dostępu do folderu, w którym są przechowywane obrazy przechwycone podczas wdrażania systemów operacyjnych. To konto jest wymagane w przypadku dodania do sekwencji zadań kroku **Przechwyć obraz systemu operacyjnego**.  

 Konto musi mieć uprawnienia **Odczyt** i **Zapis** w udziale sieciowym, w którym jest przechowywany przechwycony obraz.  

 Jeśli hasło do konta zostanie zmienione w systemie Windows, należy zaktualizować sekwencję zadań przy użyciu nowego hasła. Klienta programu Configuration Manager odbierze nowe hasło, przy następnym pobraniu zasad klienta.  

 W przypadku używania tego konta można utworzyć jedno konto użytkownika domeny z minimalnymi uprawnienia dostępu do wymaganych zasobów sieciowych i używać go w ramach wszystkich kont sekwencji zadań.  

> [!IMPORTANT]  
>  Nie należy przypisywać interaktywnych uprawnień logowania do tego konta.  
>   
>  Nie używaj na tym koncie konta dostępu do sieci.  

### <a name="client-push-installation-account"></a>Konto instalacji wypychanej klienta  
 **Konta instalacji wypychanej klienta** służy do łączenia się z komputerami i zainstaluj oprogramowanie klienta programu Configuration Manager, jeżeli wdrażanie klientów przy użyciu instalacji wypychanej klienta. Jeśli takie konto nie zostanie określone, do zainstalowania oprogramowania klienta będzie używane konto serwera lokacji.  

 To konto musi należeć do lokalnej **Administratorzy** na komputerach, na którym zostanie zainstalowana oprogramowanie klienta programu Configuration Manager. To konto nie wymaga **administratora domeny** praw.  

 Można określić co najmniej jeden Push konta instalacji klienta, które programu Configuration Manager kolejno próbuje użyć aż do znalezienia właściwego konta.  

> [!TIP]  
>  Aby bardziej wydajnie zarządzać aktualizacjami konta w dużych wdrożeniach usługi Active Directory, Utwórz nowe konto o innej nazwie, a następnie dodaj nowe konto do listy konta instalacji wypychanej klienta w programie Configuration Manager. Należy przewidzieć czas wystarczający dla usług domenowych Active Directory na replikację nowego konta, a następnie usuń stare konto z programu Configuration Manager i usługi domenowe Active Directory.  

> [!IMPORTANT]  
>  Nie przyznawaj temu kontu w prawo, aby zalogować się lokalnie.  

### <a name="enrollment-point-connection-account"></a>Konto połączenia punktu rejestracyjnego  
 **Konto połączenia punktu rejestracyjnego** łączy punkt rejestracyjny z bazą danych lokacji programu Configuration Manager. Domyślnie jest używane konto komputera punktu rejestracyjnego, ale można skonfigurować konto użytkownika zamiast tego. Konto użytkownika należy zawsze określić, gdy punkt rejestracyjny znajduje się w niezaufanej domenie na serwerze lokacji. To konto wymaga **odczytu** i **zapisu** dostęp do bazy danych lokacji.  

### <a name="exchange-server-connection-account"></a>Konto połączenia serwera Exchange  
 **Konto połączenia serwera Exchange** łączy serwer lokacji z określonym komputerem serwera Exchange w celu znalezienia urządzeń przenośnych łączących się z tym serwerem i zarządzania nimi. To konto wymaga poleceń cmdlet środowiska PowerShell w ramach serwera Exchange, które zapewniają wymagane uprawnienia na komputerze serwera Exchange. Aby uzyskać więcej informacji na temat poleceń cmdlet, zobacz [Zarządzanie urządzeniami przenośnymi za pomocą programu System Center Configuration Manager i Exchange](../../../mdm/deploy-use/manage-mobile-devices-with-exchange-activesync.md).  

### <a name="exchange-server-connector-proxy-server-account"></a>Konto serwera proxy łącznika serwera Exchange  
 Łącznik serwera Exchange używa **konta serwera Proxy łącznika serwera Exchange** dostęp do Internetu za pośrednictwem serwera proxy serwera lub zapory wymagających dostępu uwierzytelnionego.  

> [!IMPORTANT]  
>  Określ konto, które ma najniższe możliwe uprawnienia do wymaganego serwera proxy lub zapory.  

### <a name="management-point-connection-account"></a>Konto połączenia punktu zarządzania  
 **Konto połączenia punktu zarządzania** służy do łączenia punktu zarządzania z bazą danych lokacji programu Configuration Manager, dzięki czemu umożliwia wysyłanie i pobieranie informacji dotyczących klientów. Domyślnie jest używane konto komputera punktu zarządzania, ale można skonfigurować konto użytkownika zamiast tego. Konto użytkownika należy zawsze określić, gdy punkt zarządzania znajduje się w niezaufanej domenie na serwerze lokacji.  

 Utwórz konto z niskimi uprawnieniami, konta lokalnego na komputerze z uruchomionym programem Microsoft SQL Server.  

> [!IMPORTANT]  
>  Udziela praw interakcyjne logowanie do tego konta.  

### <a name="multicast-connection-account"></a>Konto połączenia multiemisji  
 Punkty dystrybucji, które są skonfigurowane do użycia multiemisji **konto połączenia multiemisji** odczytać informacji z bazy danych lokacji. Domyślnie jest używane konto komputera punktu dystrybucji, ale można skonfigurować konto użytkownika zamiast tego. Konto użytkownika należy zawsze określić, gdy baza danych lokacji znajduje się w niezaufanym lesie. Jeżeli na przykład centrum danych ma sieć obwodową w lesie innym niż serwer lokacji i baza danych lokacji, tego konta można używać do odczytywania informacji o multiemisji z bazy danych lokacji.  

 Jeśli tworzysz konto, należy go utworzyć jako z niskimi uprawnieniami, konta lokalnego na komputerze z uruchomionym programem Microsoft SQL Server.  

> [!IMPORTANT]  
>  Udziela praw interakcyjne logowanie do tego konta.  

### <a name="network-access-account"></a>Konto dostępu do sieci  
 Używane przez komputery klienckie **konta dostępu do sieci** kiedy nie mogą użyć lokalnego konta komputera na dostęp do zawartości w punktach dystrybucji. Dotyczy to na przykład komputerów i klientów grupy roboczej z niezaufanych domen. To konto może być również podczas wdrażania systemu operacyjnego, gdy komputer, który jest instalowany system operacyjny nie ma jeszcze konta komputera w domenie.  

> [!NOTE]  
>  Konto dostępu do sieci nigdy nie jest używana jako kontekst zabezpieczeń do uruchamiania programów, instalowania aktualizacji oprogramowania lub uruchamiania sekwencji zadań. Jest on używany tylko w przypadku uzyskiwania dostępu do zasobów w sieci.  

 Przyznaj temu kontu najniższe odpowiednie uprawnienia w zawartości wymaganej przez klienta w celu uzyskania dostępu do oprogramowania. Konto musi mieć uprawnienie **Uzyskiwanie dostępu do tego komputera z sieci** w punkcie dystrybucji lub na innym serwerze z zawartością pakietu. Można skonfigurować maksymalnie 10 kont dostępu do sieci na lokację.  

> [!WARNING]  
>  Gdy program Configuration Manager próbuje pobrać zawartość przy użyciu konta o nazwie computername$ i operacja nie powiedzie się, automatycznie ponownie próbuje użyć konta dostępu do sieci, nawet jeśli poprzednia próba zakończyła się niepowodzeniem.  

 Utwórz konto w dowolnej domenie, która zapewni wymagany dostęp do zasobów. Konto dostępu do sieci zawsze musi zawierać nazwę domeny. Przekazywanych zabezpieczeń nie jest obsługiwana dla tego konta. Jeżeli punkty dystrybucji znajdują się w wielu domenach, należy utworzyć konto w zaufanej domenie.  

> [!TIP]  
>  Aby uniknąć blokad konta, nie należy zmieniać hasła w istniejącym koncie dostępu do sieci. Zamiast tego należy utworzyć nowe konto i skonfigurować nowe konto w programie Configuration Manager. Po upłynięciu wystarczającego czasu na pobranie szczegółów nowego konta przez wszystkich klientów należy usunąć stare konto z udostępnianych folderów sieciowych, a następnie usunąć konto całkowicie.  

> [!IMPORTANT]  
>  Udziela praw interakcyjne logowanie do tego konta.
>   
>  Nie należy przyznawać temu kontu uprawnienia do dołączania komputerów do domeny. Jeżeli musisz dołączyć komputery do domeny podczas sekwencji zadań, użyj konta dołączania do domeny edytora sekwencji zadań.  

### <a name="package-access-account"></a>Konto dostępu do pakietu  
 A **konta dostępu do pakietu** pozwala ustawić uprawnień NTFS w celu określenia użytkowników i grup użytkowników, którzy mają dostęp do folderu pakietu w punktach dystrybucji. Domyślnie program Configuration Manager przypisuje dostęp tylko do ogólnych kont dostępu **użytkowników** i **Administratorzy**. Można sterować dostępem dla komputerów klienckich przy użyciu dodatkowych kont systemu Windows lub grup. Urządzenia przenośne zawsze pobierają zawartość pakietów anonimowo, więc nie używają kont dostępu do pakietów.  

 Domyślnie, gdy programu Configuration Manager utworzy udział pakietu w punkcie dystrybucji, domyślnie przyzna **odczytu** dostęp do lokalnego **użytkowników** grupy i **Pełna kontrola** do lokalnej **Administratorzy** grupy. Rzeczywiste wymagane uprawnienia są uzależnione od pakietu. Klienci w grupach roboczych lub lasach niezaufanych uzyskują dostęp do zawartości pakietu przy użyciu konta dostępu do sieci. Należy się upewnić, że konto dostępu do sieci dysponuje uprawnieniami dostępu do pakietu przy użyciu zdefiniowanych kont dostępu do pakietów.  

 Należy użyć kont w domenie mającej dostęp do punktów dystrybucji. Jeśli utworzysz lub zmienić konto, po utworzeniu pakietu ponownej dystrybucji pakietu. Aktualizacja pakietu nie zmienia uprawnień systemu plików NTFS w pakiecie.  

 Nie ma konieczności dodawania konta dostępu do sieci jako konta dostępu do pakietu, ponieważ zostanie ono dodane automatycznie w ramach członkostwa grupie Użytkownicy. Ograniczenie konta dostępu do pakietu wyłącznie do konta dostępu do sieci nie uniemożliwi klientom uzyskania dostępu do pakietu.  

### <a name="reporting-services-point-account"></a>Konto punktu usług raportowania  
 SQL Server Reporting Services używa **konta punktu usług raportowania** do pobierania danych dla raportów programu Configuration Manager z bazy danych lokacji. Określone konto użytkownika systemu Windows i hasło są szyfrowane oraz przechowywane w bazie danych usług SQL Server Reporting Services.  

### <a name="remote-tools-permitted-viewer-accounts"></a>Konta dopuszczonych poglądów narzędzi zdalnych  
 Konta określone jako **Dopuszczone podglądy** w ramach zdalnego sterowania stanowią listę użytkowników mogących korzystać z funkcji narzędzi zdalnych na klientach.  

### <a name="site-system-installation-account"></a>Konto instalacji systemu lokacji  
 Serwer lokacji używa **konta instalacji systemu lokacji** do zainstalowania, zainstaluj ponownie, odinstalowywania i konfigurowania systemów lokacji. W przypadku skonfigurowania systemu lokacji aby wymagał serwera lokacji do nawiązania połączenia z tym systemem lokacji programu Configuration Manager również używa tego konta do pobierania danych z komputera systemu lokacji po zainstalowaniu systemu lokacji i ewentualnych ról systemu lokacji. Każdy system lokacji może mieć różne konta instalacji systemu lokacji, ale można skonfigurować tylko jedno konto instalacji systemu lokacji, aby zarządzać wszystkie role systemu lokacji, w tym systemie lokacji.  

 To konto wymaga lokalnych uprawnień administracyjnych, na które administratorzy będą Instalowanie i konfigurowanie systemów lokacji. Ponadto to konto musi mieć **dostęp do tego komputera z sieci** w zasadach zabezpieczeń w systemach lokacji, które administratorzy będą zainstalować i skonfigurować.  

> [!TIP]  
>  Jeśli masz wiele kontrolerów domeny, a konta te będą używane między domenami, sprawdź, czy konta zostały zreplikowane przed skonfigurowaniem systemu lokacji.  
>   
>  Konfiguracja z określonym kontem lokalnym w każdym zarządzanym systemie lokacji jest bezpieczniejsza niż używanie kont domeny, ponieważ ogranicza ryzyko uszkodzeń spowodowanych przez osoby atakujące w razie złamania zabezpieczeń konta. Jednak konta domeny są łatwiejsze w zarządzaniu. Należy rozważyć kompromis między bezpieczeństwem a efektywną administracją.  

### <a name="smtp-server-connection-account"></a>Konto połączenia serwera SMTP  
 Serwer lokacji używa **konta połączenia serwera SMTP** do wysyłania alertów e-mail gdy serwer SMTP wymaga dostępu uwierzytelnionego.  

> [!IMPORTANT]  
>  Określ konto, które ma najniższe możliwe uprawnienia do wysyłania wiadomości e-mail.  

### <a name="software-update-point-connection-account"></a>Konto połączenia punktu aktualizacji oprogramowania  
 Serwer lokacji używa **konto połączenia punktu aktualizacji oprogramowania** dla następujących dwóch usług aktualizacji oprogramowania:  

-   Menedżer konfiguracji systemu Windows Server Update Services (WSUS), który konfiguruje ustawienia, takie jak produktu definicje, klasyfikacje i ustawienia nadrzędne.  

-   Menedżer synchronizacji programu WSUS, który wysyła do nadrzędnego serwera programu WSUS lub usługi Microsoft Update żądania synchronizacji.  

Konto instalacji systemu lokacji można instalować składniki w ramach aktualizacji oprogramowania, ale nie może wykonywać funkcji specyficznych dla aktualizacji oprogramowania w punkcie aktualizacji oprogramowania. Jeżeli punkt aktualizacji oprogramowania znajduje się w niezaufanym lesie i nie można użyć konta komputera serwera lokacji w ramach tej funkcji, należy określić to konto oprócz konta instalacji systemu lokacji.  

To konto musi być administratorem lokalnym na komputerze, na którym zainstalowano program WSUS. Należy również częścią lokalnej grupy administratorów programu WSUS.  

### <a name="software-update-point-proxy-server-account"></a>Konto serwera proxy punktu aktualizacji oprogramowania  
 Punkt aktualizacji oprogramowania używa **konto punktu aktualizacji oprogramowania serwera Proxy serwera** dostęp do Internetu za pośrednictwem serwera proxy serwera lub zapory wymagających dostępu uwierzytelnionego.  

> [!IMPORTANT]  
>  Określ konto, które ma najniższe możliwe uprawnienia do wymaganego serwera proxy lub zapory.  

### <a name="source-site-account"></a>Konto lokacji źródłowej  
 Proces migracji **konto lokacji źródłowej** dostępu do dostawcy programu SMS lokacji źródłowej. To konto wymaga uprawnień dostępu **Odczyt** w obiektach lokacji źródłowej w celu zbierania danych dotyczących zadań migracji.  

 Jeśli możesz uaktualnić punkty dystrybucji programu Configuration Manager 2007 lub Lokacje dodatkowe, które mają punkty dystrybucji kolokowane do punktów dystrybucji programu System Center Configuration Manager, to konto musi mieć również **usunąć** uprawnień do **lokacji** pomyślne usunięcie punktu dystrybucji z lokacji programu Configuration Manager 2007 podczas uaktualniania.  

> [!NOTE]  
>  Zarówno konto lokacji źródłowej, jak i konto bazy danych lokacji źródłowej mają zdefiniowany **Menedżera migracji** w **kont** węzła **administracji** obszaru roboczego w konsoli programu Configuration Manager.  

### <a name="source-site-database-account"></a>Konto bazy danych lokacji źródłowej  
 Proces migracji **konto bazy danych lokacji źródłowej** dostępu do bazy danych programu SQL Server dla lokacji źródłowej. Aby zebrać dane z bazy danych programu SQL Server lokacji źródłowej, konto bazy danych lokacji źródłowej musi mieć **odczytu** i **Execute** uprawnień do bazy danych programu SQL Server lokacji źródłowej.  

> [!NOTE]  
>  Jeśli używasz konta komputera programu System Center Configuration Manager, upewnij się, że spełnione są wszystkie poniższe:  
>   
> -   Jest elementem członkowskim grupy zabezpieczeń **Użytkownicy DCOM** w domenie, w której znajduje się lokacja programu Configuration Manager 2007.  
> -   To konto jest członkiem grupy zabezpieczeń **Administratorzy programu SMS**.  
> -   Ma ona **odczytu** uprawnienia do wszystkich obiektów programu Configuration Manager 2007.  

> [!NOTE]  
>  Zarówno konto lokacji źródłowej, jak i konto bazy danych lokacji źródłowej mają zdefiniowany **Menedżera migracji** w **kont** węzła **administracji** obszaru roboczego w konsoli programu Configuration Manager.  

### <a name="task-sequence-editor-domain-joining-account"></a>Konto dołączania do domeny edytora sekwencji zadań  
 **Konto dołączania do domeny edytora sekwencji zadań** pozwala w sekwencji zadań przyłączać do domeny komputery, w których przypadku utworzono nowe obrazy. To konto jest wymagane w przypadku dodania do sekwencji zadań kroku **Przyłącz do domeny lub grupy roboczej**, a następnie wybrania kroku **Przyłącz do domeny**. To konto można również łączyć po dodaniu kroku **Zastosuj ustawienia sieci** do zadania sekwencji, ale nie jest wymagana.  

 To konto wymaga uprawnienia **Przyłącz do domeny** względem domeny, do której będzie przyłączany komputer.  

> [!TIP]  
>  Jeśli potrzebujesz tego konta w sekwencjach zadań, możesz utworzyć jedno konto użytkownika domeny z minimalnymi uprawnieniami dostępu do wymaganych zasobów sieciowych i użyć go w odniesieniu do wszystkich kont sekwencji zadań.  

> [!IMPORTANT]  
>  Nie należy przypisywać interaktywnych uprawnień logowania do tego konta.  
>   
>  Nie używaj na tym koncie konta dostępu do sieci.  

### <a name="task-sequence-editor-network-folder-connection-account"></a>Konto łączenia z folderem sieciowym edytora sekwencji zadań  
 Sekwencja zadań używa **konto połączenia folderem sieciowym edytora sekwencji zadań** nawiązać połączenia z folderem udostępnionym w sieci. To konto jest wymagane w przypadku dodania do sekwencji zadań kroku **Połącz z folderem sieciowym**.  

 To konto wymaga uprawnienia dostępu w podanym folderze udostępnionym. Należy konto użytkownika domeny.  

> [!TIP]  
>  Jeśli potrzebujesz tego konta w sekwencjach zadań, możesz utworzyć jedno konto użytkownika domeny z minimalnymi uprawnieniami dostępu do wymaganych zasobów sieciowych i użyć go w odniesieniu do wszystkich kont sekwencji zadań.  

> [!IMPORTANT]  
>  Nie należy przypisywać interaktywnych uprawnień logowania do tego konta.  
>   
>  Nie używaj na tym koncie konta dostępu do sieci.  

### <a name="task-sequence-run-as-account"></a>Konto Uruchom jako w sekwencji zadań  
 **Konto Uruchom jako w sekwencji zadań** pozwala uruchamiać wiersze poleceń w sekwencjach zadań oraz korzystać z poświadczeń innych niż poświadczenia konta systemu lokalnego. To konto jest wymagane, jeśli Dodaj krok **Uruchom wiersz polecenia** sekwencji zadań, ale nie chcesz, aby sekwencja zadań była uruchamiana z uprawnieniami konta systemu lokalnego na zarządzanym komputerze.  

 Zdefiniuj konto ma minimalne uprawnienia wymagane do uruchomienia wiersza polecenia, który jest określony w sekwencji zadań. Konto wymaga praw interakcyjnego logowania i zwykle wymaga możliwości instalowania oprogramowania i dostępu do zasobów sieciowych.  

> [!IMPORTANT]  
>  Nie używaj na tym koncie konta dostępu do sieci.  
>   
>  Nie należy wprowadzać konta administratora domeny.  
>   
>  Nigdy nie skonfigurowano profile mobilne dla tego konta. Po uruchomieniu sekwencji zadań, pobierze profil mobilny dla konta. Spowoduje to pozostawienie profil narażony na dostęp do komputera lokalnego.  
>   
>  Ogranicz zakres konta. Utwórz na przykład różne konta Uruchom jako dla poszczególnych sekwencji zadań. W przypadku złamania zabezpieczeń jednego konta zostaną złamane wyłącznie zabezpieczenia komputerów klienckich, do których to konto ma dostęp.  
>   
>  Jeśli wiersz polecenia wymaga dostępu administracyjnego na komputerze, należy rozważyć możliwość tworzenia konta administratora lokalnego przeznaczone wyłącznie na potrzeby zadania konta Uruchom jako sekwencji na wszystkich komputerach, który będzie uruchamiana sekwencja zadań. Usuń konto, gdy nie są już potrzebne.  
