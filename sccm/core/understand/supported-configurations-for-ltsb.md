---
title: "Obsługiwane konfiguracje dla LTSB | Dokumentacja firmy Microsoft"
description: "Dowiedz się, które systemy operacyjne i produkty zależne działają z długoterminowe obsługi gałęzi programu System Center Configuration Manager."
ms.custom: na
ms.date: 5/10/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f0f818d4-7f45-402f-8758-dc88bc024953
caps.latest.revision: "0"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 31bddee83b2365cfa903077ffaa1d7116b194378
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="supported-configurations-for-the-long-term-servicing-branch-of-system-center-configuration-manager"></a>Obsługiwane konfiguracje dla długoterminowego gałęzi obsługi programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (długoterminowej obsługi oddziału)*

Skorzystaj z informacji w tym temacie, aby zrozumieć, jakie systemów operacyjnych i zależności produktu są obsługiwane przez długoterminowe Servicing Branch (LTSB) programu Configuration Manager.
Jeśli nie zaznaczono inaczej, w tym lub LTSB określonych tematów, te same konfiguracje i ograniczenia dotyczące wersji Current Branch 1606 zastosować LTSB.  Gdy występują konflikty, skorzystaj z informacji, która ma zastosowanie do używanej wersji. Zazwyczaj LTSB jest bardziej ograniczony niż bieżącej gałęzi.

## <a name="general-statement-of-support"></a>Ogólne zestawienie pomocy technicznej
Następujące produkty i technologie, są obsługiwane przez gałęzi programu Configuration Manager. Jednak włączenie ich do tej zawartości nie express to rozszerzenia obsługi produktu lub wersji poza cykl pomocy technicznej poszczególnych tego produktu. Produkty, które wykraczają poza wsparcia technicznego, nie są obsługiwane do użytku z programem Configuration Manager. Aby uzyskać więcej informacji, odwiedź stronę [cykl życia pomocy technicznej firmy Microsoft](http://go.microsoft.com/fwlink/p/?LinkId=208270) witryny sieci Web i Odczyt [Microsoft wsparcia technicznego](http://go.microsoft.com/fwlink/p/?LinkId=31976).

Ponadto produktów i wersji produktu, które nie są wymienione w poniższych tematach nie są obsługiwane, chyba że ma zostać ogłaszane na [Enterprise Mobility + Security Blog](https://blogs.technet.microsoft.com/enterprisemobility/).

**Ograniczenia dotyczące wsparcia w przyszłości:** LTSB ma ograniczoną obsługę przyszłych systemów operacyjnych klienta i serwera oraz zależności produktu. Na liście platform LTSB u użytkowania wydania:

**System Windows:**
- Obsługiwane są tylko jakość i bezpieczeństwo aktualizacji systemu Windows.
- Brak obsługi jest dodawany do bieżącej gałęzi (CB) bieżącej gałęzi dla business (CBB) lub LTSB systemu Windows 10.
-   Brak obsługi dla nowych wersji głównych systemu Windows Server.

**Program SQL Server:**
- Jakość i aktualizacji zabezpieczeń lub niewielkie uaktualnienia, takie jak dodatków service pack jest obsługiwany dla programu SQL Server.
- Brak obsługi dla nowych wersji głównych programu SQL Server.  

## <a name="site-systems-and-servers"></a>Systemy lokacji i serwerów
LTSB obsługuje następujące systemy operacyjne Windows komputera jako systemy lokacji.  Każdy system operacyjny ma te same wymagania i ograniczenia jako tego samego wpis w [obsługiwane systemy operacyjne dla serwerów systemu lokacji](/sccm/core/plan-design/configs/supported-operating-systems-for-site-system-servers).  Na przykład instalacji Server Core systemu Windows 2012 R2 musi być x64 wersji, jest obsługiwana tylko do obsługi punktu dystrybucji i nie obsługuje środowiska PXE lub multiemisji.

**Obsługiwane systemy operacyjne:**
- Windows Server 2016
- Windows Server 2012 R2 (x 64): Standard, Datacenter
- Windows Server 2012 (x 64): Standard, Datacenter
- Windows Server 2008 R2 z dodatkiem SP1 (x 64): Standard, Enterprise i Datacenter
- Windows Server 2008 z dodatkiem SP2 (x 86, x 64): Standard, Enterprise i Datacenter *(patrz Uwaga 1)*
- Windows 10 Enterprise LTSB 2015 (x86, x64)
- Windows 10 Enterprise LTSB 2016 (x86, x64)
- Windows 8.1 (x86, x64): Professional, Enterprise
- W systemie Windows 7 z dodatkiem SP1 (x 86, x 64): Professional, Enterprise i Ultimate
- Instalacja Server Core systemu Windows Server 2012
- Instalacja Server Core systemu Windows Server 2012 R2    

*Należy pamiętać, 1*: Ten system operacyjny nie jest obsługiwany dla serwerów lokacji i ról systemu lokacji, z wyjątkiem punktu dystrybucji i punktu dystrybucji ściągania. Można nadal używać tego systemu operacyjnego jako punkt dystrybucji, do momentu ogłoszenia zaniechania tej obsługi lub zakończenia okresu rozszerzonej pomocy technicznej tego systemu operacyjnego. Aby uzyskać więcej informacji, zobacz [instalacji programu System Center Configuration Manager CB i LTSB zakończy się niepowodzeniem w systemie Windows Server 2008](https://support.microsoft.com/help/4015095).

## <a name="client-management"></a>Zarządzanie klientami
W poniższych sekcjach podano klienckie systemy operacyjne, którymi można zarządzać w programie LTSB. LTSB nie obsługuje dodawania nowych systemów operacyjnych jako obsługiwanych klientów.

### <a name="windows-computers"></a>Komputery z systemem Windows
LTSB służy do zarządzania następujących systemów operacyjnych komputera z systemem Windows przy użyciu oprogramowania klienckiego programu Configuration Manager dostępnej w programie Configuration Manager. Aby uzyskać więcej informacji, zobacz [jak wdrożyć klientów na komputerach z systemem Windows w programie System Center Configuration Manager](/sccm/core/clients/deploy/deploy-clients-to-windows-computers).

**Obsługiwane systemy operacyjne:**
- Windows Server 2016
- Windows Server 2012 R2 (x 64): Standard, Datacenter (Uwaga 1)
- Windows Server 2012 (x 64): Standard, Datacenter (Uwaga 1)
- Windows Storage Server 2012 R2 (x 64)
- Windows Storage Server 2012 (x 64)
- Windows Server 2008 R2 z dodatkiem SP1 (x 64): Standard, Enterprise i Datacenter (Uwaga 1)
- Windows Storage Server 2008 R2 (x 86, x 64): Workgroup, Standard i Enterprise
- Windows Server 2008 z dodatkiem SP2 (x 86, x 64): Standard, Enterprise i Datacenter (Uwaga 1)
- Windows 10 Enterprise LTSB 2015 (x86, x64)
- Windows 10 Enterprise LTSB 2016 (x86, x64)
- Windows 8.1 (x86, x64): Professional, Enterprise
- W systemie Windows 7 z dodatkiem SP1 (x 86, x 64): Professional, Enterprise i Ultimate
- Instalacja Server Core systemu Windows Server 2012 R2 (x64) (Uwaga 2)
- Instalacja Server Core systemu Windows Server 2012 (x64) (Uwaga 2)
- Instalacja Server Core systemu Windows Server 2008 R2 z dodatkiem SP1 (x64)
- Instalacja Server Core systemu Windows Server 2008 z dodatkiem SP2 (x86, x64)

**(Uwaga 1)**  Wersje Datacenter są obsługiwane, ale nie są certyfikowane dla programu Configuration Manager.  
**(Uwaga 2)**  Do obsługi instalacji wypychanej klienta, komputera, na którym działa ta wersja systemu operacyjnego należy uruchomić usługę roli serwera plików dla roli serwera usług plików i magazynowania. Aby uzyskać informacji na temat instalowania funkcji systemu Windows na komputerze instalacja Server Core, zobacz [instalowania ról i funkcji serwera na serwerze Server Core](https://technet.microsoft.com/library/jj574158(v=ws.11).aspx) w bibliotece TechNet systemu Windows Server 2012.

### <a name="windows-embedded"></a>Windows Embedded
LTSB służy do zarządzania następującymi urządzeniami Windows Embedded, instalując oprogramowanie klienckie na urządzeniu.  Aby uzyskać więcej informacji, zobacz [Planowanie wdrożenia klientów na urządzeniach Windows Embedded w programie System Center Configuration Manager](/sccm/core/clients/deploy/plan/planning-for-client-deployment-to-windows-embedded-devices).

**Wymagania i ograniczenia:**  

-   Wszystkie funkcje klienta są obsługiwane przez obsługiwane Windows Embedded systemów, które nie mają włączonych filtrów zapisu.  

-   Wszystkich funkcji oprócz zarządzania energią obsługuje klientów korzystających z jednego z następujących czynności:  

    -   Rozszerzone filtry zapisu (EWF)    

    -   Filtrów zapisu opartych na plikach pamięci RAM (FBWF)    

    -   Ujednolicone filtry zapisu (UWF)  

-   Wykaz aplikacji nie jest obsługiwany na urządzeniach z systemem Windows Embedded.  

-   Przed można monitorować wykryte złośliwe oprogramowanie na urządzeniach Windows Embedded oparte na systemie Windows XP, należy zainstalować pakiet skryptów Microsoft Windows WMI na urządzeniu osadzonym. Windows Embedded Target Designer należy zainstalować ten pakiet. *WBEMDISP. Biblioteki DLL* i *WBEMDISP. TLB* plików musi istnieć i być zarejestrowane w folderze %windir%\System32\WBEM na urządzeniu osadzony zapewnienie wykrytego złośliwego oprogramowania.  

**Obsługiwane systemy operacyjne:**  
-   Windows 10 Enterprise LTSB 2016 (x86, x64)  
-   Windows 10 Enterprise LTSB 2015 (x86, x64)  
-   Windows Embedded 8.1 Industry (x86, x64)    
-   Alokowania komputera z systemem Windows (x86, x64)    
-   Windows Embedded POSReady 7 (x86, x64)    
-   Windows Embedded Standard 7 z dodatkiem SP1 (x 86, x 64)    
-   Windows Embedded POSReady 2009 (x86)   
-   Windows Embedded Standard 2009 (x86)  

### <a name="windows-ce"></a>Windows CE  
 Urządzenia z systemem Windows CE można zarządzać w programie Configuration Manager starszego klienta urządzenia przenośnego dostępnej w programie Configuration Manager.  

**Wymagania i ograniczenia:**  

-   Klient urządzenia przenośnego wymaga 0,78 MB miejsca do magazynowania zainstalować klienta. Urządzenie przenośne może wymagać do 256 KB dodatkowego miejsca do logowania.    

-   Funkcje dotyczące tych urządzeń przenośnych zależą od platformy i klienta typu. Aby uzyskać informacje o rodzaju funkcje zarządzania, które program Configuration Manager obsługuje starszego klienta urządzenia przenośnego, zobacz [wybór rozwiązania do zarządzania urządzeniami programu System Center Configuration Manager](/sccm/core/plan-design/choose-a-device-management-solution).  

**Obsługiwane systemy operacyjne:**  

-   Windows CE 7.0 (ARM i x86 procesorów)  

**Obsługiwane języki:**  
-   Chiński (uproszczony i tradycyjny)    
-   Angielski (USA)    
-   Francuski (Francja)    
-   niemiecki    
-   włoski    
-   japoński  
-   koreański  
-   portugalski (Brazylia)  
-   rosyjski  
-   Hiszpański (Hiszpania)  

### <a name="mac-computers"></a>Komputery Mac  
 LTSB można użyć do zarządzania komputerami z systemem Mac OS X przy użyciu klienta programu Configuration Manager dla komputerów Mac.

Pakiet instalacyjny klienta Mac nie jest dostarczany na nośnikach programu Configuration Manager. Możesz pobrać go jako część pobierania "klienci dla dodatkowych systemów operacyjnych" z [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=525184).  

Obsługa systemów operacyjnych Mac jest ograniczona do wymienionych w tej sekcji. Obsługa nie ma dodatkowych systemów operacyjnych, które mogą być obsługiwane przez przyszłej aktualizacji do pakietów instalacyjnych klienta Mac dla bieżącej gałęzi.

Aby uzyskać więcej informacji, zobacz [jak wdrożyć klientów na komputerach Mac w programie System Center Configuration Manager](/sccm/core/clients/deploy/deploy-clients-to-macs).

**Obsługiwane wersje:**  
-   Mac OS X 10.9 (Mavericks)  
-   Mac OS X 10.10 (Yosemite)  
-   Mac OS X 10.11 (El Capitan)  

## <a name="linux-and-unix-servers"></a>Serwery z systemami Linux i UNIX
LTSB służy do zarządzania serwerami Linux i UNIX przy użyciu klienta programu Configuration Manager dla systemów Linux i UNIX.

Pakiety instalacyjne klienta systemów Linux i UNIX nie są dostarczane na nośnikach programu Configuration Manager. Możesz pobrać je jako część pobierania "klienci dla dodatkowych systemów operacyjnych" z [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=525184). Oprócz pakietów instalacyjnych klienta pobranie klienta obejmuje skrypt instalacyjny, który służy do zarządzania instalacją klienta na każdym komputerze.

Obsługa systemów operacyjnych Linux i UNIX jest ograniczona do wymienionych w tej sekcji. Obsługa nie ma dodatkowych systemów operacyjnych, które mogą być obsługiwane przez przyszłej aktualizacji do pakietów klienta systemu Linux i UNIX dla bieżącej gałęzi.

**Wymagania i ograniczenia:**  

-   Aby przejrzeć zależnościach plików systemów operacyjnych klienta dla systemów Linux i UNIX, zobacz [wymagania wstępne dotyczące wdrażania klientów na serwerach Linux i UNIX](/sccm/core/clients/deploy/plan/planning-for-client-deployment-to-linux-and-unix-computers#bkmk_clientdeployprereqforlnu).  
-   Omówienie funkcji zarządzania obsługiwanych przez komputery z systemem Linux lub UNIX, zobacz [jak wdrożyć klientów na serwerach UNIX i Linux w programie System Center Configuration Manager](/sccm/core/clients/deploy/deploy-clients-to-unix-and-linux-servers).  
-   W przypadku obsługiwanych wersji systemów Linux i UNIX wymieniona wersja obejmuje wszystkie kolejne wersje pomocnicze. Na przykład deklarowana jest obsługa CentOS w wersji 6, obejmuje to także wszelkie kolejne wersje pomocnicze systemu CentOS 6, na przykład CentOS 6.3. Podobnie deklarowana Obsługa systemu operacyjnego z dodatkiem service pack, takie jak SUSE Linux Enterprise Server 11 z dodatkiem SP1, obsługa obejmuje także kolejne dodatki service Pack dla danej wersji systemu operacyjnego.
-   Aby uzyskać informacji na temat pakietów instalacyjnych klienta i agenta uniwersalnego, zobacz [jak wdrożyć klientów na serwerach UNIX i Linux w programie System Center Configuration Manager](/sccm/core/clients/deploy/deploy-clients-to-unix-and-linux-servers).


**Obsługiwane wersje:**   
Obsługiwane są następujące wersje przy użyciu podanego pliku tar.  
### <a name="aix"></a>AIX  

|Wersja|Plik|  
|-|-|  
|W wersji 5.3 (Power)|CCM-Aix53ppc. &lt;kompilacji\>tar|  
|W wersji 6.1 (Power)|CCM-Aix61ppc. &lt;kompilacji\>tar|  
|W wersji 7.1 (Power)|CCM-Aix71ppc. &lt;kompilacji\>tar|  

### <a name="centos"></a>CentOS  

|Wersja|Plik|  
|-|-|  
|W wersji 5 x86|CCM-Universalx86. &lt;kompilacji\>tar|  
|W wersji 5 x64|CCM-Universalx64. &lt;kompilacji\>tar|  
|W wersji 6 x86|CCM-Universalx86. &lt;kompilacji\>tar|  
|W wersji 6 x64|CCM-Universalx64. &lt;kompilacji\>tar|  
|Wersja 7 x64|CCM-Universalx64. &lt;kompilacji\>tar|  

### <a name="debian"></a>Debian  

|Wersja|Plik|    
|-|-|  
|W wersji 5 x86|CCM-Universalx86. &lt;kompilacji\>tar|  
|W wersji 5 x64|CCM-Universalx64. &lt;kompilacji\>tar|  
|W wersji 6 x 86|CCM-Universalx86. &lt;kompilacji\>tar|  
|W wersji 6 x64|CCM-Universalx64. &lt;kompilacji\>tar|  
|Wersja 7 x86|CCM-Universalx86. &lt;kompilacji\>tar|  
|Wersja 7 x64|CCM-Universalx64. &lt;kompilacji\>tar|  
|W wersji 8 x86|CCM-Universalx86. &lt;kompilacji\>tar|  
|W wersji 8 x64|CCM-Universalx64. &lt;kompilacji\>tar|  

### <a name="hp-ux"></a>HP-UX  

|Wersja|Plik|  
|-|-|  
|Wersja 11iv2 IA64|CCM-HpuxB.11.23i64. &lt;kompilacji\>tar|  
|Wersja 11iv2 PA-RISC|CCM-HpuxB.11.23PA. &lt;kompilacji\>tar|  
|Wersja 11iv3 IA64|CCM-HpuxB.11.31i64. &lt;kompilacji\>tar|  
|Wersja 11iv3 PA-RISC|CCM-HpuxB.11.31PA. &lt;kompilacji\>tar|  

### <a name="oracle-linux"></a>Oracle Linux  

|Wersja|Plik|    
|-|-|  
|W wersji 5 x86|CCM-Universalx86. &lt;kompilacji\>tar|  
|W wersji 5 x64|CCM-Universalx64. &lt;kompilacji\>tar|  
|W wersji 6 x86|CCM-Universalx86. &lt;kompilacji\>tar|  
|W wersji 6 x64|CCM-Universalx64. &lt;kompilacji\>tar|  
|Wersja 7 x64|CCM-Universalx64. &lt;kompilacji\>tar|  

### <a name="red-hat-enterprise-linux-rhel"></a>Red Hat Enterprise Linux (RHEL)  

|Wersja|Plik|  
|-|-|  
|W wersji 4 x86|CCM-RHEL4x86. &lt;kompilacji\>tar|  
|W wersji 4 x64|CCM-RHEL4x64. &lt;kompilacji\>tar|  
|W wersji 5 x86|CCM-Universalx86. &lt;kompilacji\>tar|  
|W wersji 5 x64|CCM-Universalx64. &lt;kompilacji\>tar|  
|W wersji 6 x86|CCM-Universalx86. &lt;kompilacji\>tar|  
|W wersji 6 x64|CCM-Universalx64. &lt;kompilacji\>tar|  
|Wersja 7 x64|CCM-Universalx64. &lt;kompilacji\>tar|  

### <a name="solaris"></a>Solaris  

|Wersja|Plik|   
|-|-|  
|W wersji 9 SPARC|CCM-Sol9sparc. &lt;kompilacji\>tar|  
|W wersji 10 x86|CCM-Sol10x86. &lt;kompilacji\>tar|  
|W wersji 10 SPARC|CCM-Sol10sparc. &lt;kompilacji\>tar|  
|W wersji 11 x86|CCM-Sol11x86. &lt;kompilacji\>tar|  
|W wersji 11 SPARC|CCM-Sol11sparc. &lt;kompilacji\>tar|  

### <a name="suse-linux-enterprise-server-sles"></a>SUSE Linux Enterprise Server (SLES)  

|Wersja|Plik|  
|-|-|  
|W wersji 9 x86|CCM-SLES9x86. &lt;kompilacji\>tar|  
|Z dodatkiem SP1 w wersji 10 x86|CCM-Universalx86. &lt;kompilacji\>tar|  
|Z dodatkiem SP1 w wersji 10 x64|CCM-Universalx64. &lt;kompilacji\>tar|  
|Z dodatkiem SP1 w wersji 11 x86|CCM-Universalx86. &lt;kompilacji\>tar|  
|Z dodatkiem SP1 w wersji 11 x64|CCM-Universalx64. &lt;kompilacji\>tar|  
|W wersji 12 x64|CCM-Universalx64. &lt;kompilacji\>tar|  

### <a name="ubuntu"></a>Ubuntu  

|Wersja|Plik|    
|-|-|  
|Wersja 10.04 LTS x86|CCM-Universalx86. &lt;kompilacji\>tar|  
|Wersja 10.04 LTS x64|CCM-Universalx64. &lt;kompilacji\>tar|  
|Wersja 12.04 LTS x86|CCM-Universalx86. &lt;kompilacji\>tar|  
|Wersja 12.04 LTS x64|CCM-Universalx64. &lt;kompilacji\>tar|  
|Wersja 14.04 LTS x86|CCM-Universalx86. &lt;kompilacji\>tar|  
|Wersja 14.04 LTS x64|CCM-Universalx64. &lt;kompilacji\>tar|  

### <a name="exchange-server-connector"></a>Łącznik serwera Exchange
 LTSB obsługuje ograniczone Zarządzanie urządzeń łączących się z wystąpienia serwera Exchange, bez konieczności instalowania oprogramowania klienta. Aby uzyskać więcej informacji, zobacz [Zarządzanie urządzeniami przenośnymi za pomocą programu System Center Configuration Manager i Exchange](/sccm/mdm/deploy-use/manage-mobile-devices-with-exchange-activesync).

 **Wymagania i ograniczenia:**  

-   Menedżer konfiguracji oferuje ograniczone zarządzanie urządzeniami przenośnymi. Ograniczone zarządzanie jest dostępna, gdy używany jest łącznik serwera Exchange dla urządzeń obsługujących program Exchange Active Sync (EAS), łączących się z serwerem Exchange Server lub Exchange Online.  

-   Aby uzyskać więcej informacji na temat funkcji zarządzania obsługiwanych przez Menedżera konfiguracji dla urządzeń przenośnych zarządzanych przez łącznik serwera Exchange, zobacz [wybór rozwiązania do zarządzania urządzeniami programu System Center Configuration Manager](/sccm/core/plan-design/choose-a-device-management-solution).  

**Obsługiwane wersje programu Exchange Server:**  
-   Exchange Server 2010 z dodatkiem SP1  
-   Exchange Server 2010 z dodatkiem SP2  
-   Exchange Server 2013  

> [!NOTE]
> LTSB nie obsługuje zarządzania urządzeń łączących się za pośrednictwem usługi online, takich jak Exchange Online (Office 365).


## <a name="configuration-manager-console"></a>Konsola programu Configuration Manager
LTSB obsługuje następujące systemy operacyjne do uruchamiania konsoli programu Configuration Manager. Każdy komputer, który jest hostem konsoli musi mieć minimalnej wersji .NET Framework 4.5.2, z wyjątkiem systemu Windows 10, która wymaga co najmniej programu .NET Framework 4.6.

**Obsługiwane systemy operacyjne:**
- Windows Server 2016
- Windows Server 2012 R2 (x 64): Standard, Datacenter
- Windows Server 2012 (x 64): Standard, Datacenter
- Windows Server 2008 R2 z dodatkiem SP1 (x 64): Standard, Enterprise i Datacenter
- Windows Server 2008 z dodatkiem SP2 (x 86, x 64): Standard, Enterprise i Datacenter
- Windows 10 Enterprise LTSB 2016 (x86, x64)
- Windows 10 Enterprise LTSB 2015 (x86, x64)
- Windows 8.1 (x86, x64): Professional, Enterprise
- W systemie Windows 7 z dodatkiem SP1 (x 86, x 64): Professional, Enterprise i Ultimate


## <a name="sql-server-versions-supported-for-the-site-database-and-reporting-point"></a>Wersje programu SQL Server obsługuje bazy danych lokacji lub punkt raportowania
LTSB obsługuje następujące wersje programu SQL Server do hostowania bazy danych lokacji i punkt raportowania. Dla każdego obsługiwanych wersji, wymagania dotyczące tej samej konfiguracji i ograniczenia, które są widoczne w [pomocy technicznej dla wersji programu SQL Server](/sccm/core/plan-design/configs/support-for-sql-server-versions) dla bieżącej gałęzi dotyczą LTSB.  Obejmuje to korzystanie z klastra programu SQL Server lub grupy dostępności AlwaysOn programu SQL Server.  

**Obsługiwane wersje:**

- Program SQL Server 2016: Wersje Standard, Enterprise
- Program SQL Server 2014 SP2: Wersje Standard, Enterprise
- SQL Server 2014 z dodatkiem SP1: Wersje Standard, Enterprise
- SQL Server 2012 z dodatkiem SP3: Wersje Standard, Enterprise
- SQL Server 2008 R2 z dodatkiem SP3: Standard, Enterprise i Datacenter
- Program SQL Server 2016 Express
- SQL Server 2014 Express z dodatkiem SP2
- SQL Server 2014 Express SP1
- SQL Server 2012 Express SP3

## <a name="support-for-active-directory-domains"></a>Obsługa domen usługi Active Directory
Wszystkie systemy lokacji LTSB muszą być elementami członkowskimi obsługiwanej domeny usługi Active Directory systemu Windows. Obsługa domen usługi Active Directory ma te same wymagania i ograniczenia, jak te, które są widoczne w [Obsługa domen usługi Active Directory](/sccm/core/plan-design/configs/support-for-active-directory-domains), ale jest ograniczone do następujących poziomów funkcjonalności domeny:

**Obsługiwane poziomy:**
- Windows Server 2008
- Windows Server 2008 R2
- Windows Server 2012
- Windows Server 2012 R2

## <a name="additional-support-topics-that-apply-to-the-long-term-servicing-branch"></a>Tematy dodatkowego pomocy technicznej, które są stosowane do gałęzi obsługi długoterminowe
Informacje zawarte w następujących tematach Current Branch dotyczą LTSB:
- [Wartości dotyczące rozmiarów i skalowania](/sccm/core/plan-design/configs/size-and-scale-numbers)
- [Wymagania wstępne dla lokacji i systemu lokacji](/sccm/core/plan-design/configs/site-and-site-system-prerequisites)
- [Opcje wysokiej dostępności](/sccm/protect/understand/high-availability-options)
- [Zalecany sprzęt](/sccm/core/plan-design/configs/recommended-hardware)
- [Obsługa funkcji systemu Windows i sieci](/sccm/core/plan-design/configs/support-for-windows-features-and-networks)
- [Obsługa środowisk wirtualizacji](/sccm/core/plan-design/configs/support-for-virtualization-environments)
