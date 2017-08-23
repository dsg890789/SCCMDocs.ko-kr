---
title: "Wymagania wstępne dotyczące lokacji | Dokumentacja firmy Microsoft"
description: "Dowiedz się, jak skonfigurować komputer z systemem Windows jako serwera systemu lokacji programu System Center Configuration Manager."
ms.custom: na
ms.date: 1/17/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1392797b-76cb-46b4-a3e4-8f349ccaa078
caps.latest.revision: "5"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 0b1d2d619d6cdaf36cc22ef461ea1505b5cacc41
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="site-and-site-system-prerequisites-for-system-center-configuration-manager"></a>Witryny i wymagania wstępne systemu lokacji dla programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*


 Komputery z systemem Windows muszą mieć określone konfiguracje, aby zapewnić obsługę ich użycia jako serwery systemu lokacji programu System Center Configuration Manager.  


 Dla niektórych produktów takie jak Windows Server Update Services (WSUS) dla oprogramowania punktu aktualizacji, należy zapoznać się z dokumentacją produktu, aby zidentyfikować dodatkowe wymagania wstępne i ograniczenia dotyczące użycia tego produktu. W tym miejscu są uwzględniane tylko konfiguracje, które są stosowane bezpośrednio do użytku z programem Configuration Manager.   

> [!NOTE]  
>  W styczeń 2016 r. Obsługa wygasł dla programu .NET Framework 4.0, 4.5 i 4.5.1. Aby uzyskać więcej informacji, zobacz [Zasady dotyczące cyklu pomocy technicznej w zakresie programu Microsoft .NET Framework — często zadawane pytania](https://support.microsoft.com/gp/framework_faq?WT.mc_id=azurebg_email_Trans_943_NET452_Update) w witrynie support.microsoft.com.  

## <a name="bkmk_generalprerewq"></a>Wymagania dotyczące serwera lokacji głównej i ograniczenia
**Poniższe informacje dotyczą wszystkich serwerach systemu lokacji:**

-   Każdy serwer systemu lokacji musi używać 64-bitowym systemie operacyjnym. Jedynym wyjątkiem jest dystrybucji Rola systemu lokacji punktu, który można zainstalować w niektórych 32-bitowych systemach operacyjnych.  

-   Systemy lokacji nie są obsługiwane w instalacjach Server Core każdego systemu operacyjnego. Wyjątkiem jest to, że instalacje Server Core są obsługiwane dla roli lokacji punktu dystrybucji systemu, bez środowiska PXE i multiemisji.  

-   Po zainstalowaniu serwera systemu lokacji nie jest obsługiwane do zmiany:  

    -   Nazwa domeny w domenie, w którym znajduje się komputer systemu lokacji (nazywane również **zmiana nazw domen**).  

    -   Członkostwo w domenie komputera.  

    -   Nazwa komputera.  

  Jeśli zmiana któregoś z tych, należy najpierw usunąć rolę systemu lokacji z komputera i ponownej instalacji roli po zakończeniu zmiany. Jeśli ma to wpływ na komputerze serwera lokacji, należy odinstalować lokację i zainstalować ponownie lokacji po zakończeniu zmiany.  

-   Role systemu lokacji nie są obsługiwane w wystąpieniu klastra systemu Windows Server. Jedynym wyjątkiem jest serwer bazy danych lokacji.  

-   Nie jest obsługiwane Zmienianie typu uruchamiania lub "Logowanie w trybie" ustawienia dla usługi programu Configuration Manager. Jeśli to zrobisz, może uniemożliwić prawidłowe działanie najważniejszych usług.  

##  <a name="bkmk_2012Prereq"></a>Wymagania wstępne dotyczące systemu Windows Server 2012 i nowszych systemów operacyjnych  
###  <a name="bkmk_2012sspreq"></a>Serwer lokacji: centralnej lokacji administracyjnej i lokacji głównej  
  **Windows Server role i funkcje:**  

-   .NET framework 3.5 z dodatkiem SP1 (lub nowszy)  

-   .NET framework 4.5.2  

-   Kompresja RDC  

**Zestaw Windows ADK:**  

-   Przed zainstalowaniem lub uaktualnieniem centralnej lokacji administracyjnej lub lokacji głównej, należy zainstalować wersję systemu Windows Assessment and Deployment Kit (ADK), który wymaga wersji programu Configuration Manager w przypadku instalowania lub uaktualniania do.  

    -   Wersja 1511 programu Configuration Manager wymaga wersji systemu Windows 10 RTM (10.0.10240) zestawu Windows adk.  

-   Aby uzyskać więcej informacji na temat tego wymagania, zobacz [wymagania dotyczące infrastruktury dla wdrożenia systemu operacyjnego](/sccm/osd/plan-design/infrastructure-requirements-for-operating-system-deployment).  

**Pakiet redystrybucyjny Visual C++:**  

-   Configuration Manager instaluje pakiet redystrybucyjny Microsoft Visual C++ 2013 na każdym komputerze instalującym serwer lokacji.  

-   Centralne Lokacje administracyjne i lokacje główne wymagają x86 i x64 wersje odpowiedniego pliku pakietu redystrybucyjnego.  

###  <a name="bkmk_2012secpreq"></a>Serwer lokacji: lokacji dodatkowej  
**Windows Server role i funkcje:**  

-   .NET framework 3.5 z dodatkiem SP1 (lub nowszy)  

-   .NET framework 4.5.2  

-   Kompresja RDC  

**Pakiet redystrybucyjny Visual C++:**  

-   Configuration Manager instaluje pakiet redystrybucyjny Microsoft Visual C++ 2013 na każdym komputerze instalującym serwer lokacji.  

-   Lokacje dodatkowe wymagają tylko x64 wersji.  

**Domyślne role systemu lokacji:**  

-   Domyślnie lokacja dodatkowa instaluje **punkt zarządzania** i **punktu dystrybucji**.  

-   Upewnij się, że serwer lokacji dodatkowej spełnia wymagania wstępne dotyczące tych ról systemu lokacji.  

###  <a name="bkmk_2012dbpreq"></a>Serwer bazy danych  
**Usługa Rejestr zdalny:**  

-   Podczas instalacji lokacji programu Configuration Manager należy włączyć usługę Rejestr zdalny na komputerze, który będzie hostem bazy danych lokacji.  

**Program SQL Server:**  

-   Przed zainstalowaniem centralnej lokacji administracyjnej lub lokacji głównej należy zainstalować obsługiwanej wersji programu SQL Server do obsługi bazy danych lokacji.  

-   Przed zainstalowaniem lokacji dodatkowej można zainstalować obsługiwanej wersji programu SQL Server.  

-   Jeśli wybierzesz opcję zainstalowania programu SQL Server Express w ramach instalacji lokacji dodatkowej programu Configuration Manager, upewnij się, że komputer spełnia wymagania do uruchomienia programu SQL Server Express.  

###  <a name="bkmk_2012smsprovpreq"></a>Serwer dostawcy programu SMS  
**Zestaw Windows ADK:**  

-   Komputer, na którym jest instalowane wystąpienie dostawcy programu SMS musi mieć wymaganą wersję zestawu Windows ADK, który wymaga programu Configuration Manager w przypadku instalowania lub uaktualniania do wersji.  

    -   Wersja 1511 programu Configuration Manager wymaga wersji systemu Windows 10 RTM (10.0.10240) zestawu Windows adk.  

-   Aby uzyskać więcej informacji na temat tego wymagania, zobacz [wymagania dotyczące infrastruktury dla wdrożenia systemu operacyjnego](/sccm/osd/plan-design/infrastructure-requirements-for-operating-system-deployment).  

###  <a name="bkmk_2012acwspreq"></a>Punkt witryny sieci Web katalogu aplikacji  
**Windows Server role i funkcje:**  

-   .NET framework 3.5 z dodatkiem SP1 (lub nowszy)  

-   .NET framework 4.5.2:  

    -   PROGRAM ASP.NET 4.5  

**Konfiguracja programu IIS:**  

-   Wspólne funkcje HTTP:  

    -   Dokument domyślny  

    -   Zawartość statyczna  

-   Projektowanie aplikacji:  

    -   ASP.NET 3.5 (wraz z automatycznie wybranymi opcjami)  

    -   ASP.NET 4.5 (wraz z automatycznie wybranymi opcjami)  

    -   Rozszerzenia architektury .NET 3.5  

    -   Rozszerzenia architektury .NET 4.5  

-   Zabezpieczenia:  

    -   Uwierzytelnianie systemu Windows  

-   Zgodność 6 zarządzania usług IIS:  

    -   Zgodność z metabazą usług IIS 6  

###  <a name="bkmk_2012ACwsitepreq"></a>Punkt usługi sieci web katalogu aplikacji  
**Windows Server role i funkcje:**  

-   .NET framework 3.5 z dodatkiem SP1 (lub nowszy)  

-   .NET framework 4.5.2:  

    -   ASP.NET 4.5:  

        -   Aktywacja HTTP (wraz z automatycznie wybranymi opcjami)  

**Konfiguracja programu IIS:**  

-   Wspólne funkcje HTTP:  

    -   Dokument domyślny  

-   Zgodność 6 zarządzania usług IIS:  

    -   Zgodność z metabazą usług IIS 6  

-   Projektowanie aplikacji:  

    -   ASP.NET 3.5 (wraz z automatycznie wybranymi opcjami)  

    -   Rozszerzenia architektury .NET 3.5  

    -   ASP.NET 4.5 (wraz z automatycznie wybranymi opcjami)  

    -   Rozszerzenia architektury .NET 4.5  

**Pamięć komputera:**  

-   Komputer obsługujący tę rolę systemu lokacji musi mieć co najmniej 5% komputera wolnej pamięci, aby włączyć rolę systemu lokacji do przetwarzania żądań.  

-   Gdy ta rola systemu lokacji jest kolokowana z inną rolą systemu lokacji, która ma ten sam wymóg, to wymagania dotyczące pamięci dla komputera nie rosną, ale pozostaje na minimalnym poziomie 5%.  

###  <a name="bkmk_2012AIpreq"></a>Punkt synchronizacji analizy zasobów  
**Windows Server role i funkcje:**  

-   .NET framework 4.5.2  

###  <a name="bkmk_2012crppreq"></a>Punkt rejestracji certyfikatu  
**Windows Server role i funkcje:**  

-   .NET framework 4.5.2:  

    -   Aktywacja HTTP  

**Konfiguracja programu IIS:**  

-   Projektowanie aplikacji:  

    -   ASP.NET 3.5 (wraz z automatycznie wybranymi opcjami)  

    -   ASP.NET 4.5 (wraz z automatycznie wybranymi opcjami)  

-   Zgodność 6 zarządzania usług IIS:  

    -   Zgodność z metabazą usług IIS 6  

    -   Zgodność z usługą WMI dla usług IIS 6  

###  <a name="bkmk_2012dppreq"></a>Punkt dystrybucji  
**Windows Server role i funkcje:**  

-   Kompresja RDC  

**Konfiguracja programu IIS:**  

-   Projektowanie aplikacji:  

    -   Rozszerzenia ISAPI  

-   Zabezpieczenia:  

    -   Uwierzytelnianie systemu Windows  

-   Zgodność 6 zarządzania usług IIS:  

    -   Zgodność z metabazą usług IIS 6  

    -   Zgodność z usługą WMI dla usług IIS 6  

**Środowiska PowerShell:**  

-   W systemie Windows Server 2012 lub nowszym, PowerShell 3.0 lub 4.0 jest wymagana przed zainstalowaniem punktu dystrybucji.  

**Pakiet redystrybucyjny Visual C++:**  

-   Configuration Manager instaluje pakiet redystrybucyjny Microsoft Visual C++ 2013 na każdym komputerze udostępniającym punkt dystrybucji.  

-   Instalowana wersja zależy od platformy komputera (x86 lub x64).  

**Microsoft Azure:**  

-   Usługi w chmurze w systemie Microsoft Azure służy do obsługi punktu dystrybucji.  

**Do obsługi środowiska PXE lub multiemisji:**  

-   Instalowanie i konfigurowanie roli usługi wdrażania systemu Windows (WDS) systemu Windows Server.  

    > [!NOTE]  
    >  Usługi wdrażania systemu Windows automatycznie instalowane i konfigurowane podczas konfigurowania punktu dystrybucji do obsługi środowiska PXE lub multiemisji na serwerze z systemem Windows Server 2012 lub nowszym.  

> [!NOTE]  
> Rola systemu lokacji punktu dystrybucji nie wymaga usługi inteligentnego transferu w tle (BITS). Po skonfigurowaniu usługi BITS na komputerze punktu dystrybucji usługi BITS na komputerze punktu dystrybucji nie jest używana do przyspieszania pobierania zawartości przez klientów używających usługi BITS.  

###  <a name="bkmk_2012EPPpreq"></a>Punkt programu Endpoint Protection  
**Windows Server role i funkcje:**  

-   .NET framework 3.5 z dodatkiem SP1 (lub nowszy)  

###  <a name="bkmk_2012Enrollpreq"></a>Punkt rejestracji  
**Windows Server role i funkcje:**  

-   .NET framework 3.5 (lub nowszy)  

-   .NET framework 4.5.2:  

     Podczas instalowania tej roli systemu lokacji programu Configuration Manager automatycznie instaluje program .NET Framework 4.5.2. Ta instalacja może spowodować przełączenie serwera do ponownego uruchomienia komputera w stanie oczekiwania. Gdy oczekuje na ponowny rozruch dla programu .NET Framework aplikacje .NET może się nie powieść dopiero po ponownym uruchomieniu serwera i zakończeniu instalacji.  

    -   Aktywacja HTTP (wraz z automatycznie wybranymi opcjami)  

    -   PROGRAM ASP.NET 4.5  


**Konfiguracja programu IIS:**  

-   Wspólne funkcje HTTP:  

    -   Dokument domyślny  

-   Projektowanie aplikacji:  

    -   ASP.NET 3.5 (wraz z automatycznie wybranymi opcjami)  

    -   Rozszerzenia architektury .NET 3.5  

    -   ASP.NET 4.5 (wraz z automatycznie wybranymi opcjami)  

    -   Rozszerzenia architektury .NET 4.5  

-   Zgodność 6 zarządzania usług IIS:  

    -   Zgodność z metabazą usług IIS 6  

**Pamięć komputera:**  

-   Komputer obsługujący tę rolę systemu lokacji musi mieć co najmniej 5% komputera wolnej pamięci, aby włączyć rolę systemu lokacji do przetwarzania żądań.  

-   Gdy ta rola systemu lokacji jest kolokowana z inną rolą systemu lokacji, która ma ten sam wymóg, to wymagania dotyczące pamięci dla komputera nie rosną, ale pozostaje na minimalnym poziomie 5%.  

###  <a name="bkmk_2012EnrollProxpreq"></a>Punkt proxy rejestracji  
**Windows Server role i funkcje:**  

-   .NET framework 3.5 (lub nowszy)  

-   .NET framework 4.5.2  

     Podczas instalowania tej roli systemu lokacji programu Configuration Manager automatycznie instaluje program .NET Framework 4.5.2. Ta instalacja może spowodować przełączenie serwera do ponownego uruchomienia komputera w stanie oczekiwania. Gdy oczekuje na ponowny rozruch dla programu .NET Framework aplikacje .NET może się nie powieść dopiero po ponownym uruchomieniu serwera i zakończeniu instalacji.  

**Konfiguracja programu IIS:**  

-   Wspólne funkcje HTTP:  

    -   Dokument domyślny  

    -   Zawartość statyczna  

-   Projektowanie aplikacji:  

    -   ASP.NET 3.5 (wraz z automatycznie wybranymi opcjami)  

    -   ASP.NET 4.5 (wraz z automatycznie wybranymi opcjami)  

    -   Rozszerzenia architektury .NET 3.5  

    -   Rozszerzenia architektury .NET 4.5  

-   Zabezpieczenia:  

    -   Uwierzytelnianie systemu Windows  

-   Zgodność 6 zarządzania usług IIS:  

    -   Zgodność z metabazą usług IIS 6  

**Pamięć komputera:**  

-   Komputer obsługujący tę rolę systemu lokacji musi mieć co najmniej 5% komputera wolnej pamięci, aby włączyć rolę systemu lokacji do przetwarzania żądań.  

-   Gdy ta rola systemu lokacji jest kolokowana z inną rolą systemu lokacji, która ma ten sam wymóg, to wymagania dotyczące pamięci dla komputera nie rosną, ale pozostaje na minimalnym poziomie 5%.  

###  <a name="bkmk_2012FSPpreq"></a>Rezerwowy punkt stanu  
Domyślna konfiguracja usług IIS jest wymagany z następującymi dodatkami:  

-   Zgodność 6 zarządzania usług IIS:  

    -   Zgodność z metabazą usług IIS 6  

###  <a name="bkmk_2012MPpreq"></a>Punkt zarządzania  
**Windows Server role i funkcje:**  

-   .NET framework 4.5.2  

-   Rozszerzenia serwera usługi BITS (i automatycznie wybieranych opcji) lub usługi inteligentnego transferu w tle (BITS) (wraz z automatycznie wybranymi opcjami)  

**Konfiguracja programu IIS:**  

-   Projektowanie aplikacji:  

    -   Rozszerzenia ISAPI  

-   Zabezpieczenia:  

    -   Uwierzytelnianie systemu Windows  

-   Zgodność 6 zarządzania usług IIS:  

    -   Zgodność z metabazą usług IIS 6  

    -   Zgodność z usługą WMI dla usług IIS 6  

###  <a name="bkmk_2012RSpoint"></a>Punkt usług raportowania  
**Windows Server role i funkcje:**  

-   .NET framework 4.5.2  

**Usługi Usługi SQL Server Reporting Services:**  

-   Należy zainstalować i skonfigurować co najmniej jedno wystąpienie programu SQL Server do obsługi programu SQL Server Reporting Services, zanim punkt instalacji raportowania usług.  

-   Wystąpienie, używanego programu SQL Server Reporting Services może być tego samego wystąpienia używanego w bazie danych lokacji.  

-   Ponadto wystąpienie, którego używasz może współużytkowane z innymi produktami System Center, tak długo, jak innymi produktami System Center nie mają ograniczeń dotyczących udostępniania wystąpienia programu SQL Server.  

###  <a name="bkmk_SCPpreq"></a>Punkt połączenia usługi  
**Windows Server role i funkcje:**  

-   .NET framework 4.5.2  

     Podczas instalowania tej roli systemu lokacji programu Configuration Manager automatycznie instaluje program .NET Framework 4.5.2. Ta instalacja może spowodować przełączenie serwera do ponownego uruchomienia komputera w stanie oczekiwania. Gdy oczekuje na ponowny rozruch dla programu .NET Framework aplikacje .NET może się nie powieść dopiero po ponownym uruchomieniu serwera i zakończeniu instalacji.  

**Pakiet redystrybucyjny Visual C++:**  

-   Configuration Manager instaluje pakiet redystrybucyjny Microsoft Visual C++ 2013 na każdym komputerze udostępniającym punkt dystrybucji.  

-   Rola systemu lokacji wymaga x64 wersji.  

###  <a name="bkmk_2012SUPpreq"></a>Punkt aktualizacji oprogramowania  
**Windows Server role i funkcje:**  

-   .NET framework 3.5 z dodatkiem SP1 (lub nowszy)  

-   .NET framework 4.5.2  

Domyślna konfiguracja usług IIS jest wymagany.

**Windows Server Update Services:**  

-   Przed zainstalowaniem punktu aktualizacji oprogramowania, należy zainstalować rolę serwera systemu Windows, Windows Server Update Services na komputerze.  

-   Aby uzyskać więcej informacji, zobacz [Planowanie aktualizacji oprogramowania w programie System Center Configuration Manager](../../../sum/plan-design/plan-for-software-updates.md).  

### <a name="state-migration-point"></a>punkt migracji stanu  
Domyślna konfiguracja usług IIS jest wymagany.  

##  <a name="bkmk_2008"></a>Wymagania wstępne dotyczące systemu Windows Server 2008 R2 i Windows Server 2008  
Windows Server 2008 i Windows Server 2008 R2 znajdują się teraz w rozszerzonej pomocy technicznej i nie są już dostępne podstawowe wsparcie, zgodnie z opisem [Microsoft Cykl wsparcia technicznego produktów](https://support.microsoft.com/lifecycle). Aby uzyskać więcej informacji na temat wsparcia w przyszłości dla tych systemów operacyjnych jako serwerów systemu lokacji z programem Configuration Manager, zobacz [usunięte i przestarzałe funkcje programu System Center Configuration Manager](../../../core/plan-design/changes/removed-and-deprecated-features.md).  

**Poniższe wymagania dotyczą wszystkich .NET Framework:**  

-   Przed zainstalowaniem ról systemu lokacji, należy zainstalować pełną wersję programu .NET Framework. Na przykład, zobacz [Microsoft .NET Framework 4 (Autonomiczny Instalator)](http://go.microsoft.com/fwlink/p/?LinkId=193048). Profil klienta programu .NET Framework 4 jest niewystarczający dla tego wymagania.  

**Poniższe informacje dotyczą wszystkich wymagań aktywacji usługi Windows Communication Foundation (WCF):**  

-   Aktywację programu WCF można skonfigurować jako część funkcji .NET Framework w systemie Windows na serwerze systemu lokacji. Na przykład systemu Windows Server 2008 R2, należy uruchomić **Kreatora dodawania funkcji** Aby zainstalować dodatkowe funkcje na serwerze. Na **Wybieranie funkcji** rozwiń pozycję **funkcje programu .NET Framework 3.5.1**, rozwiń węzeł **aktywacji WCF**, a następnie zaznacz pola wyboru dla obu **Aktywacja HTTP** i **Aktywacja bez HTTP** Aby włączyć te opcje.  

###  <a name="bkmk_2008sspreq"></a>Serwer lokacji: centralnej lokacji administracyjnej i lokacji głównej  
**.NET framework:**  

-   .NET framework 3.5 z dodatkiem SP1 (lub nowszy)  

-   .NET framework 4.5.2  

**Funkcja systemu Windows:**  

-   Kompresja RDC  

**Zestaw Windows ADK:**  

-   Przed zainstalowaniem lub uaktualnieniem centralnej lokacji administracyjnej lub lokacji głównej, należy zainstalować wersję zestawu Windows ADK, który wymaga programu Configuration Manager w przypadku instalowania lub uaktualniania do wersji.  

    -   Wersja 1511 programu Configuration Manager wymaga wersji systemu Windows 10 RTM (10.0.10240) zestawu Windows adk.  

-   Aby uzyskać więcej informacji na temat tego wymagania, zobacz [wymagania dotyczące infrastruktury dla wdrożenia systemu operacyjnego](/sccm/osd/plan-design/infrastructure-requirements-for-operating-system-deployment).  

**Pakiet redystrybucyjny Visual C++:**  

-   Configuration Manager instaluje pakiet redystrybucyjny Microsoft Visual C++ 2013 na każdym komputerze instalującym serwer lokacji.  

-   Centralne Lokacje administracyjne i lokacje główne wymagają x86 i x64 wersje odpowiedniego pliku pakietu redystrybucyjnego.  

###  <a name="bkmk_2008secpreq"></a>Serwer lokacji: lokacji dodatkowej  
**.NET framework:**  

-   .NET framework 3.5 z dodatkiem SP1 (lub nowszy)  

-   .NET framework 4.5.2  

**Pakiet redystrybucyjny Visual C++:**  

-   Configuration Manager instaluje pakiet redystrybucyjny Microsoft Visual C++ 2013 na każdym komputerze instalującym serwer lokacji.  

-   Lokacje dodatkowe wymagają tylko x64 wersji.  

**Domyślne role systemu lokacji:**  

-   Domyślnie lokacja dodatkowa instaluje **punkt zarządzania** i **punktu dystrybucji**.  

-   Upewnij się, że serwer lokacji dodatkowej spełnia wymagania wstępne dotyczące tych ról systemu lokacji.  

###  <a name="bkmk_2008dbpreq"></a>Serwer bazy danych  
**Usługa Rejestr zdalny:**  

-   Podczas instalacji lokacji programu Configuration Manager należy włączyć usługę Rejestr zdalny na komputerze, który będzie hostem bazy danych lokacji.  

**Program SQL Server:**  

-   Przed zainstalowaniem centralnej lokacji administracyjnej lub lokacji głównej należy zainstalować obsługiwanej wersji programu SQL Server do obsługi bazy danych lokacji.  

-   Przed zainstalowaniem lokacji dodatkowej można zainstalować obsługiwanej wersji programu SQL Server.  

-   Jeśli wybierzesz opcję zainstalowania programu SQL Server Express w ramach instalacji lokacji dodatkowej programu Configuration Manager, upewnij się, że komputer spełnia wymagania do uruchomienia programu SQL Server Express.  

###  <a name="bkmk_2008smsprovpreq"></a>Serwer dostawcy programu SMS  
**Zestaw Windows ADK:**  

-   Komputer, na którym jest instalowane wystąpienie dostawcy programu SMS musi mieć wymaganą wersję zestawu Windows ADK, który wymaga programu Configuration Manager w przypadku instalowania lub uaktualniania do wersji.  

    -   Wersja 1511 programu Configuration Manager wymaga wersji systemu Windows 10 RTM (10.0.10240) zestawu Windows adk.  

-   Aby uzyskać więcej informacji na temat tego wymagania, zobacz [wymagania dotyczące infrastruktury dla wdrożenia systemu operacyjnego](/sccm/osd/plan-design/infrastructure-requirements-for-operating-system-deployment).  

###  <a name="bkmk_2008acwspreq"></a>Punkt witryny sieci Web katalogu aplikacji  
**.NET framework:**  

-   .NET framework 4.5.2  

**Konfiguracja programu IIS:**

Domyślna konfiguracja usług IIS jest wymagany z następującymi dodatkami:  

-   Wspólne funkcje HTTP:  

    -   Zawartość statyczna  

    -   Dokument domyślny  

-   Projektowanie aplikacji:  

    -   ASP.NET (wraz z automatycznie wybranymi opcjami)  

         W niektórych scenariuszach, na przykład w przypadku usług IIS jest zainstalowana lub ponownie skonfigurować po zainstalowaniu programu .NET Framework 4.5.2 Musisz jawnie włączyć platformę ASP.NET w wersji 4.5. Na przykład na komputerze 64-bitowym systemem .NET Framework w wersji 4.0.30319 uruchom następujące polecenie: **%windir%\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe -i-Włącz**  

-   Zabezpieczenia:  

    -   Uwierzytelnianie systemu Windows  

-   Zgodność 6 zarządzania usług IIS:  

    -   Zgodność z metabazą usług IIS 6  

###  <a name="bkmk_2008ACwsitepreq"></a>Punkt usługi sieci web katalogu aplikacji  
**.NET framework:**  

-   .NET framework 3.5 z dodatkiem SP1 (lub nowszy)  

-   .NET framework 4.5.2  

**Aktywacja systemu Windows Communication Foundation (WCF):**  

-   Aktywacja HTTP  

-   Aktywacja bez HTTP  

**Konfiguracja programu IIS:**

Domyślna konfiguracja usług IIS jest wymagany z następującymi dodatkami:  

-   Projektowanie aplikacji:  

    -   ASP.NET (wraz z automatycznie wybranymi opcjami)  

         W niektórych scenariuszach, na przykład w przypadku usług IIS jest zainstalowana lub ponownie skonfigurować po zainstalowaniu programu .NET Framework 4.5.2 Musisz jawnie włączyć platformę ASP.NET w wersji 4.5. Na przykład na komputerze 64-bitowym systemem .NET Framework w wersji 4.0.30319 uruchom następujące polecenie: **%windir%\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe -i-Włącz**  

-   Zgodność 6 zarządzania usług IIS:  

    -   Zgodność z metabazą usług IIS 6  

**Pamięć komputera:**  

-   Komputer obsługujący tę rolę systemu lokacji musi mieć co najmniej 5% komputera wolnej pamięci, aby włączyć rolę systemu lokacji do przetwarzania żądań.  

-   Gdy ta rola systemu lokacji jest kolokowana z inną rolą systemu lokacji, która ma ten sam wymóg, to wymagania dotyczące pamięci dla komputera nie rosną, ale pozostaje na minimalnym poziomie 5%.  

###  <a name="bkmk_2008AIpreq"></a>Punkt synchronizacji analizy zasobów  
**.NET framework:**  

-   .NET framework 4.5.2  

###  <a name="bkmk_2008crppreq"></a>Punkt rejestracji certyfikatu  
**.NET framework:**  

-   .NET framework 4.5.2  

-   Aktywacja HTTP  

**Konfiguracja programu IIS:**

Domyślna konfiguracja usług IIS jest wymagany z następującymi dodatkami:  

-   Zgodność 6 zarządzania usług IIS:  

    -   Zgodność z metabazą usług IIS 6  

    -   Zgodność z usługą WMI dla usług IIS 6  

###  <a name="bkmk_2008dppreq"></a>Punkt dystrybucji  
**Konfiguracja programu IIS:**

Można użyć domyślnej konfiguracji programu IIS lub konfiguracji niestandardowej. Aby użyć niestandardowej konfiguracji programu IIS, należy włączyć następujące opcje dla usług IIS:  

-   Projektowanie aplikacji:  

    -   Rozszerzenia ISAPI  

-   Zabezpieczenia:  

    -   Uwierzytelnianie systemu Windows  

-   Zgodność 6 zarządzania usług IIS:  

    -   Zgodność z metabazą usług IIS 6  

    -   Zgodność z usługą WMI dla usług IIS 6  

Użycie niestandardowej konfiguracji programu IIS, należy usunąć opcje, które nie są wymagane, takie jak następujące:  

-   Wspólne funkcje HTTP:  

    -   Przekierowywanie HTTP  

-   Narzędzia i skrypty zarządzania usługami IIS  

**Funkcja systemu Windows:**  

-   Kompresja RDC  

**Pakiet redystrybucyjny Visual C++:**  

-   Configuration Manager instaluje pakiet redystrybucyjny Microsoft Visual C++ 2013 na każdym komputerze udostępniającym punkt dystrybucji.  

-   Instalowana wersja zależy od platformy komputera (x86 lub x64).  

**Microsoft Azure:**  

-   Usługi w chmurze na platformie Azure służy do obsługi punktu dystrybucji.  

**Do obsługi środowiska PXE lub multiemisji:**  

-   Instalowanie i konfigurowanie roli usługi wdrażania systemu Windows (WDS) systemu Windows Server.  

    > [!NOTE]  
    >  Usługi wdrażania systemu Windows automatycznie instalowane i konfigurowane podczas konfigurowania punktu dystrybucji do obsługi środowiska PXE lub multiemisji na serwerze z systemem Windows Server 2012 lub nowszym.  

> [!NOTE]  
> Rola systemu lokacji punktu dystrybucji nie wymaga usługi inteligentnego transferu w tle (BITS). Po skonfigurowaniu usługi BITS na komputerze punktu dystrybucji usługi BITS na komputerze punktu dystrybucji nie jest używana do przyspieszania pobierania zawartości przez klientów używających usługi BITS.  


###  <a name="bkmk_2008EPPpreq"></a>Punkt programu Endpoint Protection  
**.NET framework:**  

-   .NET framework 3.5 z dodatkiem SP1 (lub nowszy)  

###  <a name="bkmk_2008Enrollpreq"></a>Punkt rejestracji  
**.NET framework:**  

-   .NET framework 4.5.2  

     Podczas instalowania tej roli systemu lokacji, jeśli serwer nie ma obsługiwanej wersji programu .NET Framework zainstalowana, programu Configuration Manager automatycznie instaluje program .NET Framework 4.5.2. Ta instalacja może spowodować przełączenie serwera do ponownego uruchomienia komputera w stanie oczekiwania. Gdy oczekuje na ponowny rozruch dla programu .NET Framework aplikacje .NET może się nie powieść dopiero po ponownym uruchomieniu serwera i zakończeniu instalacji.  

**Aktywacja systemu Windows Communication Foundation (WCF):**  

-   Aktywacja HTTP  

-   Aktywacja bez HTTP  

**Konfiguracja programu IIS:**

Domyślna konfiguracja usług IIS jest wymagany z następującymi dodatkami:  

-   Projektowanie aplikacji:  

    -   ASP.NET (wraz z automatycznie wybranymi opcjami)  

         W niektórych scenariuszach, na przykład w przypadku usług IIS jest zainstalowana lub ponownie skonfigurować po zainstalowaniu programu .NET Framework 4.5.2 Musisz jawnie włączyć platformę ASP.NET w wersji 4.5. Na przykład na komputerze 64-bitowym systemem .NET Framework w wersji 4.0.30319 uruchom następujące polecenie: **%windir%\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe -i-Włącz**  

**Pamięć komputera:**  

-   Komputer obsługujący tę rolę systemu lokacji musi mieć co najmniej 5% komputera wolnej pamięci, aby włączyć rolę systemu lokacji do przetwarzania żądań.  

-   Gdy ta rola systemu lokacji jest kolokowana z inną rolą systemu lokacji, która ma ten sam wymóg, to wymagania dotyczące pamięci dla komputera nie rosną, ale pozostaje na minimalnym poziomie 5%.  

###  <a name="bkmk_2008EnrollProxpreq"></a>Punkt proxy rejestracji  
**.NET framework:**  

-   .NET framework 4.5.2  

     Podczas instalowania tej roli systemu lokacji, jeśli serwer nie ma obsługiwanej wersji programu .NET Framework zainstalowana, programu Configuration Manager automatycznie instaluje program .NET Framework 4.5.2. Ta instalacja może spowodować przełączenie serwera do ponownego uruchomienia komputera w stanie oczekiwania. Gdy oczekuje na ponowny rozruch dla programu .NET Framework aplikacje .NET może się nie powieść dopiero po ponownym uruchomieniu serwera i zakończeniu instalacji.  

**Aktywacja systemu Windows Communication Foundation (WCF):**  

-   Aktywacja HTTP  

-   Aktywacja bez HTTP  

**Konfiguracja programu IIS:**

Domyślna konfiguracja usług IIS jest wymagany z następującymi dodatkami:  

-   Projektowanie aplikacji:  

    -   ASP.NET (wraz z automatycznie wybranymi opcjami)  

         W niektórych scenariuszach, na przykład w przypadku usług IIS jest zainstalowana lub ponownie skonfigurować po zainstalowaniu programu .NET Framework 4.5.2 Musisz jawnie włączyć platformę ASP.NET w wersji 4.5. Na przykład na komputerze 64-bitowym systemem .NET Framework w wersji 4.0.30319 uruchom następujące polecenie: **%windir%\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe -i-Włącz**  

**Pamięć komputera:**  

-   Komputer obsługujący tę rolę systemu lokacji musi mieć co najmniej 5% komputera wolnej pamięci, aby włączyć rolę systemu lokacji do przetwarzania żądań.  

-   Gdy ta rola systemu lokacji jest kolokowana z inną rolą systemu lokacji, która ma ten sam wymóg, to wymagania dotyczące pamięci dla komputera nie rosną, ale pozostaje na minimalnym poziomie 5%.  

###  <a name="bkmk_2008FSPpreq"></a>Rezerwowy punkt stanu  
**Konfiguracja programu IIS:**

Domyślna konfiguracja usług IIS jest wymagany z następującymi dodatkami:  

-   Zgodność 6 zarządzania usług IIS:  

    -   Zgodność z metabazą usług IIS 6  

###  <a name="bkmk_2008MPpreq"></a>Punkt zarządzania  
**.NET framework:**  

-   .NET framework 4.5.2  

**Konfiguracja programu IIS:**

Można użyć domyślnej konfiguracji programu IIS lub konfiguracji niestandardowej. Każdy punkt zarządzania, należy włączyć do obsługi urządzeń przenośnych wymaga dodatkowej konfiguracji programu IIS dla ASP.NET (wraz z wybranymi automatycznie opcjami).

W niektórych scenariuszach, na przykład w przypadku usług IIS jest zainstalowana lub ponownie skonfigurować po zainstalowaniu programu .NET Framework 4.5.2 Musisz jawnie włączyć platformę ASP.NET w wersji 4.5. Na przykład na komputerze 64-bitowym systemem .NET Framework w wersji 4.0.30319 uruchom następujące polecenie: **%windir%\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe -i-Włącz**  


Aby użyć niestandardowej konfiguracji programu IIS, należy włączyć następujące opcje dla usług IIS:  

-   Projektowanie aplikacji:  

    -   Rozszerzenia ISAPI  

-   Zabezpieczenia:  

    -   Uwierzytelnianie systemu Windows  

-   Zgodność 6 zarządzania usług IIS:  

    -   Zgodność z metabazą usług IIS 6  

    -   Zgodność z usługą WMI dla usług IIS 6  


Użycie niestandardowej konfiguracji programu IIS, należy usunąć opcje, które nie są wymagane, takie jak następujące:  

-   Wspólne funkcje HTTP:  

    -   Przekierowywanie HTTP  

-   Narzędzia i skrypty zarządzania usługami IIS  

**Funkcja systemu Windows:**  

-   BITY rozszerzenia serwera (i automatycznie wybieranych opcji), lub usługi inteligentnego transferu w tle (BITS) (wraz z automatycznie wybranymi opcjami)  

###  <a name="bkmk_2008RSpoint"></a>Punkt usług raportowania  
**.NET framework:**  

-   .NET framework 4.5.2  

**Usługi Usługi SQL Server Reporting Services:**  

-   Należy zainstalować i skonfigurować co najmniej jedno wystąpienie programu SQL Server do obsługi programu SQL Server Reporting Services, zanim punkt instalacji raportowania usług.  

-   Wystąpienie, używanego programu SQL Server Reporting Services może być tego samego wystąpienia używanego w bazie danych lokacji.  

-   Ponadto wystąpienie, którego używasz może współużytkowane z innymi produktami System Center, tak długo, jak innymi produktami System Center nie mają ograniczeń dotyczących udostępniania wystąpienia programu SQL Server.  

###  <a name="bkmk_2008SCPpreq"></a>Punkt połączenia usługi  
**.NET framework:**  

-   .NET framework 4.5.2  

     Podczas instalowania tej roli systemu lokacji, jeśli serwer nie ma obsługiwanej wersji programu .NET Framework zainstalowana, programu Configuration Manager automatycznie instaluje program .NET Framework 4.5.2. Ta instalacja może spowodować przełączenie serwera do ponownego uruchomienia komputera w stanie oczekiwania. Gdy oczekuje na ponowny rozruch dla programu .NET Framework aplikacje .NET może się nie powieść dopiero po ponownym uruchomieniu serwera i zakończeniu instalacji.  

**Pakiet redystrybucyjny Visual C++:**  

-   Configuration Manager instaluje pakiet redystrybucyjny Microsoft Visual C++ 2013 na każdym komputerze udostępniającym punkt dystrybucji.  

-   Rola systemu lokacji wymaga x64 wersji.  

###  <a name="bkmk_2008SUPpreq"></a>Punkt aktualizacji oprogramowania  
**.NET framework:**  

-   .NET framework 3.5 z dodatkiem SP1 (lub nowszy)  

-   .NET framework 4.5.2  

**Konfiguracja programu IIS:**

Domyślna konfiguracja usług IIS jest wymagany.  

**Windows Server Update Services:**  

-   Należy zainstalować rolę systemu Windows Server, Windows Server Update Services na komputerze przed zainstalowaniem punktu aktualizacji oprogramowania.  

-   Aby uzyskać więcej informacji, zobacz [Planowanie aktualizacji oprogramowania w programie System Center Configuration Manager](../../../sum/plan-design/plan-for-software-updates.md).

###  <a name="bkmk_2008SMPpreq"></a>Punkt migracji stanu  
**Konfiguracja programu IIS:**

Domyślna konfiguracja usług IIS jest wymagany.  
