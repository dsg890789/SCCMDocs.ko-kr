---
title: "Porty używane przez program Configuration Manager | Dokumentacja firmy Microsoft"
description: "Więcej informacji na temat portów wymaganych i dostosowania, które korzysta z programu System Center Configuration Manager dla połączeń."
ms.custom: na
ms.date: 3/20/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c6777fb0-0754-4abf-8a1b-7639d23e9391
caps.latest.revision: "8"
caps.handback.revision: "0"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 78caa69e10f5d386daab1e61e484d4d134469708
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="ports-used-in-system-center-configuration-manager"></a>Porty używane w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

System Center Configuration Manager jest systemem rozproszonych klient/serwer. Rozproszony charakter programu Configuration Manager oznacza, że można nawiązać połączenia między serwerami lokacji, systemami lokacji i klientami. Niektóre połączenia używają portów, których nie można skonfigurować, a niektóre obsługują niestandardowe porty określone. Należy sprawdzić, czy są dostępne porty wymagane użycie technologii, takich jak zapory, routery, serwery proxy lub protokołu IPsec filtrowania portów.  

> [!NOTE]  
>  Jeśli obsługa klientów internetowych przy użyciu mostkowania SSL, oprócz wymagań dotyczących portów, masz może umożliwia niektórych czasownikom i nagłówkom HTTP na przechodzenie przez zaporę.   

 Obowiązujące listy portów są używane przez program Configuration Manager i nie obejmują informacji dotyczących standardowych usług systemu Windows, takich jak ustawienia zasad grupy dla usług domenowych w usłudze Active Directory lub uwierzytelnianie Kerberos. Informacje o usługach i portach systemu Windows Server znajdują się w temacie [Service overview and network port requirements for the Windows Server system (Omówienie usługi i wymagania dotyczące portów sieciowych w systemie Windows Server)](http://go.microsoft.com/fwlink/p/?LinkID=123652).  

##  <a name="BKMK_ConfigurablePorts"></a> Porty, które można konfigurować  
 Menedżer konfiguracji umożliwia konfigurowanie portów do następujących typów komunikacji:  

-   Punkt witryny sieci Web katalogu aplikacji z punktem usługi sieci web katalogu aplikacji  

-   Punkt proxy rejestracji z punktem rejestracyjnym  

-   Systemy lokacji klienta, których działają usługi IIS  

-   Klient z Internetem (zgodnie z ustawieniami serwera proxy)  

-   Punkt aktualizacji oprogramowania z Internetem (zgodnie z ustawieniami serwera proxy)  

-   Punkt aktualizacji oprogramowania z serwerem WSUS  

-   Serwer lokacji z serwerem bazy danych lokacji  

-   Punkty usług raportowania  

    > [!NOTE]  
    >  Porty, które są używane przez rolę systemu lokacji punktu usług raportowania są skonfigurowane w usługach SQL Server Reporting Services. Porty te są następnie używane przez program Configuration Manager podczas komunikacji z punktem usług raportowania. Należy przejrzeć te porty, które definiują informacji o filtrze IP dla zasad IPsec lub w celu skonfigurowania zapory.  

Domyślnie port HTTP, który jest używany do komunikacji systemu lokacji klienta jest port 80, a domyślnym portem HTTPS jest 443. Podczas instalacji lub we właściwościach lokacji dla lokacji programu Configuration Manager można zmienić portów dla komunikacji systemu lokacji klienta za pośrednictwem protokołu HTTP lub HTTPS.  

Porty, które są używane przez rolę systemu lokacji punktu usług raportowania są skonfigurowane w usługach SQL Server Reporting Services. Porty te są następnie używane przez program Configuration Manager podczas komunikacji z punktem usług raportowania. Należy przejrzeć te porty podczas definiowania informacji o filtrze IP dla zasad IPsec lub w celu skonfigurowania zapory.  

##  <a name="BKMK_NonConfigurablePorts"></a> Porty, których nie można konfigurować  
Menedżer konfiguracji nie pozwala konfigurować portów do następujących typów komunikacji:  

-   Między lokacjami  

-   Serwer lokacji z systemem lokacji  

-   Konsola programu Configuration Manager do dostawcy programu SMS  

-   Konsola programu Configuration Manager z Internetem  

-   Połączenia z usługami w chmurze, takich jak Microsoft Intune i punkty dystrybucji w chmurze  

##  <a name="BKMK_CommunicationPorts"></a> Porty używane przez systemy lokacji i klientów programu Configuration Manager  
W poniższych sekcjach opisano porty, które są używane do komunikacji w programie Configuration Manager. Strzałki w tytułach sekcji oznaczają kierunek komunikacji:  

-   --> Oznacza, że jeden komputer inicjuje komunikację, a drugi zawsze odpowiada  

-   &lt;--> Oznacza, że każdy komputer może zainicjować komunikację  

###  <a name="BKMK_PortsAI"></a>Punkt synchronizacji analizy zasobów--> program Microsoft  

|Opis|UDP|TCP|  
|-----------------|---------|---------|  
|Protokół HTTPS|--|443|  

###  <a name="BKMK_PortsAI-to-SQL"></a>Punkt synchronizacji analizy zasobów--> program SQL Server  

|Opis|UDP|TCP|  
|-----------------|---------|---------|  
|SQL przez TCP|--|1433 (patrz adnotacja 2, **alternatywny port dostępne**)|  

###  <a name="BKMK_PortsAppCatalogService-SQL"></a>Punkt usługi sieci web katalogu aplikacji--> program SQL Server  

|Opis|UDP|TCP|  
|-----------------|---------|---------|  
|SQL przez TCP|--|1433 (patrz adnotacja 2, **alternatywny port dostępne**)|  

###  <a name="BKMK_PortsAppCatalogWebSitePoint_AppCatalogWebServicePoint"></a>Punkt witryny sieci Web katalogu aplikacji--> punkt usługi sieci web katalogu aplikacji  

|Opis|UDP|TCP|  
|-----------------|---------|---------|  
|Protokół HTTP|--|80 (patrz adnotacja 2, **alternatywny port dostępne**)|  
|Protokół HTTPS|--|443 (patrz adnotacja 2, **alternatywny port dostępne**)|  

###  <a name="BKMK_PortsClient-AppCatalogWebsitePoint"></a>Klient--> Punkt witryny sieci Web katalogu aplikacji  

|Opis|UDP|TCP|  
|-----------------|---------|---------|  
|Protokół HTTP|--|80 (patrz adnotacja 2, **alternatywny port dostępne**)|  
|Protokół HTTPS|--|443 (patrz adnotacja 2, **alternatywny port dostępne**)|  

###  <a name="BKMK_PortsClient-ClientWakeUp"></a> Klient -- &gt; klient  
 Oprócz portów wymienionych w poniższej tabeli serwera proxy wznawiania używa także protokołu komunikatów sterowania Internetem (ICMP) komunikatów żądania echa z jednego klienta z innym klientem gdy są skonfigurowane dla serwera proxy wznawiania.

Ta komunikacja służy do potwierdzenia, czy drugi komputer kliencki w sieci został wybudzony. Protokół ICMP jest czasami określany jako polecenia TCP/IP Ping. Protokół ICMP nie ma numeru protokołu UDP ani TCP, dlatego nie został wymieniony w poniższej tabeli. Jednak aby komunikacja z serwerem proxy wznawiania powiodła się, zapory oparte na hostach na tych komputerach klienckich lub pośredniczących urządzeniach sieciowych muszą zezwalać na ruch ICMP.  

|Opis|UDP|TCP|  
|-----------------|---------|---------|  
|Wake On LAN|9 (patrz adnotacja 2, **alternatywny port dostępne**)|--|  
|Serwer proxy wznawiania|25536 (patrz adnotacja 2, **alternatywny port dostępne**)|--|  

###  <a name="BKMK_PortsClient-PolicyModule"></a> Klient -- &gt; moduł zasad programu Configuration Manager (usługa rejestracji urządzeń sieciowych)  

|Opis|UDP|TCP|  
|-----------------|---------|---------|  
|Protokół HTTP||80|  
|Protokół HTTPS|--|443|  

###  <a name="BKMK_PortsClient-CloudDP"></a>Klient--> Punkt dystrybucji w chmurze  

|Opis|UDP|TCP|  
|-----------------|---------|---------|  
|Protokół HTTPS|--|443|  

###  <a name="BKMK_PortsClient-DP"></a>Klient--> Punkt dystrybucji  

|Opis|UDP|TCP|  
|-----------------|---------|---------|  
|Protokół HTTP|--|80 (patrz adnotacja 2, **alternatywny port dostępne**)|  
|Protokół HTTPS|--|443 (patrz adnotacja 2, **alternatywny port dostępne**)|  

###  <a name="BKMK_PortsClient-DP2"></a>Klient--> Punkt dystrybucji skonfigurowany do multiemisji  

|Opis|UDP|TCP|  
|-----------------|---------|---------|  
|Blok komunikatów serwera (SMB)|--|445|  
|Protokół multiemisji|63000–64000|--|  

###  <a name="BKMK_PortsClient-DP3"></a>Klient--> Punkt dystrybucji skonfigurowany do środowiska PXE  

|Opis|UDP|TCP|  
|-----------------|---------|---------|  
|Protokół DHCP|67 i 68|--|  
|Protokół TFTP (Trivial File Transfer Protocol)|69 (patrz adnotacja 4, **Demon Trivial FTP (TFTP)**)|--|  
|Protokół BINL (Boot Information Negotiation Layer)|4011|--|  

###  <a name="BKMK_PortsClient-FSP"></a>Klient--> Rezerwowy punkt stanu  

|Opis|UDP|TCP|  
|-----------------|---------|---------|  
|Protokół HTTP|--|80 (patrz adnotacja 2, **alternatywny port dostępne**)|  

###  <a name="BKMK_PortsClient-GCDC"></a>Klient--> Kontroler domeny wykazu globalnego  
 Klient programu Configuration Manager nie kontaktuje się z serwerem wykazu globalnego, gdy jest komputerem grupy roboczej lub został skonfigurowany do komunikacji tylko przez Internet.  

|Opis|UDP|TCP|  
|-----------------|---------|---------|  
|Protokół LDAP wykazu globalnego|--|3268|  
|Protokół LDAP SSL wykazu globalnego|--|3269|  

###  <a name="BKMK_PortsClient-MP"></a>Klient--> Punkt zarządzania  

|Opis|UDP|TCP|  
|-----------------|---------|---------|  
|Powiadomienie klienta (domyślna komunikacja przed powrotem do komunikacji HTTP lub HTTPS)|--|10123 (patrz adnotacja 2, **alternatywny port dostępne**)|  
|Protokół HTTP|--|80 (patrz adnotacja 2, **alternatywny port dostępne**)|  
|Protokół HTTPS|--|443 (patrz adnotacja 2, **alternatywny port dostępne**)|  

###  <a name="BKMK_PortsClient-SUP"></a>Klient--> Punkt aktualizacji oprogramowania  

|Opis|UDP|TCP|  
|-----------------|---------|---------|  
|Protokół HTTP|--|80 lub 8530 (patrz adnotacja 3, **Windows Server Update Services**)|  
|Protokół HTTPS|--|443 lub 8531 (patrz adnotacja 3, **Windows Server Update Services**)|  

###  <a name="BKMK_PortsClient-SMP"></a>Klient--> Punkt migracji stanu  

|Opis|UDP|TCP|  
|-----------------|---------|---------|  
|Protokół HTTP|--|80 (patrz adnotacja 2, **alternatywny port dostępne**)|  
|Protokół HTTPS|--|443 (patrz adnotacja 2, **alternatywny port dostępne**)|  
|Blok komunikatów serwera (SMB)|--|445|  

###  <a name="BKMK_PortsConsole-Client"></a>Konsola programu Configuration Manager--> Klient  

|Opis|UDP|TCP|  
|-----------------|---------|---------|  
|Zdalne sterowanie (sterowanie)|--|2701|  
|Pomoc zdalna (RDP i RTC)|--|3389|  

###  <a name="BKMK_PortsConsole-Internet"></a>Konsola programu Configuration Manager--> Internet  

|Opis|UDP|TCP|  
|-----------------|---------|---------|  
|Protokół HTTP|--|80|  

###  <a name="BKMK_PortsConsole-RSP"></a>Konsola programu Configuration Manager--> punkt usług raportowania  


|Opis|UDP|TCP|
|-----------------|---------|---------|   
|Protokół HTTP|--|80 (patrz adnotacja 2, **alternatywny port dostępne**)|  
|Protokół HTTPS|--|443 (patrz adnotacja 2, **alternatywny port dostępne**)|  

###  <a name="BKMK_PortsConsole-Site"></a>Konsola programu Configuration Manager--> serwer lokacji  

|Opis|UDP|TCP|  
|-----------------|---------|---------|  
|Zdalne wywołanie procedury (połączenie początkowe z usługą WMI w celu zlokalizowania systemu dostawcy)|--|135|  

###  <a name="BKMK_PortsConsole-Provider"></a>Konsola programu Configuration Manager--> Dostawca programu SMS  

|Opis|UDP|TCP|  
|-----------------|---------|---------|  
|Mapowanie punktów końcowych wywołań RPC|135|135|  
|Zdalne wywołanie procedury|--|DYNAMICZNE (patrz adnotacja 6, **Porty dynamiczne**)|  

###  <a name="BKMK_PortsCertificateRegistationPoint_PolicyModule"></a>Moduł zasad programu Configuration Manager (Usługa rejestracji urządzeń sieciowych —) > Punkt rejestracji certyfikatu  

|Opis|UDP|TCP|  
|-----------------|---------|---------|  
|Protokół HTTPS|--|443 (patrz adnotacja 2, **alternatywny port dostępne**)|  

###  <a name="BKMK_PortsDist_MP"></a>Punkt dystrybucji--> punkt zarządzania  
 Punkt dystrybucji komunikuje się z punktem zarządzania w następujących scenariuszach:  

-   Aby zgłosić stan wstępnie przygotowanej zawartości  

-   Aby zgłosić podsumowanie danych dotyczących użycia  

-   Aby zgłosić weryfikację zawartości  

-   Aby zgłosić stan pobierania pakietu (ściągający punkt dystrybucji)

|Opis|UDP|TCP|  
|-----------------|---------|---------|  
|Protokół HTTP|--|80 (patrz adnotacja 2, **alternatywny port dostępne**)|  
|Protokół HTTPS|--|443 (patrz adnotacja 2, **alternatywny port dostępne**)|  

###  <a name="BKMK_PortsEndpointProtection_Internet"></a>Punkt programu Endpoint Protection--> Internet  

|Opis|UDP|TCP|  
|-----------------|---------|---------|  
|Protokół HTTP|--|80|  

###  <a name="BKMK_PortsEP-to-SQL"></a>Punkt programu Endpoint Protection--> program SQL Server  

|Opis|UDP|TCP|  
|-----------------|---------|---------|  
|SQL przez TCP|--|1433 (patrz adnotacja 2, **alternatywny port dostępne**)|  

###  <a name="BKMK_PortsEnrollmentProxyEnrollmentPoint"></a>Punkt proxy rejestracji--> punkt rejestracyjny  

|Opis|UDP|TCP|  
|-----------------|---------|---------|  
|Protokół HTTPS|--|443 (patrz adnotacja 2, **alternatywny port dostępne**)|  

###  <a name="BKMK_PortsEnrollmentEnrollmentSQL"></a>Punkt rejestracji--> program SQL Server  

|Opis|UDP|TCP|  
|-----------------|---------|---------|  
|SQL przez TCP|--|1433 (patrz adnotacja 2, **alternatywny port dostępne**)|  

###  <a name="BKMK_PortsExchangeConnectorHosted"></a> Łącznik serwera Exchange -- &gt; Exchange Online  

|Opis|UDP|TCP|  
|-----------------|---------|---------|  
|Zdalne zarządzanie systemem Windows przez protokół HTTPS|--|5986|  

###  <a name="BKMK_PortsExchangeConnectorOnPrem"></a>Łącznik serwera Exchange--> Lokalny serwer Exchange  

|Opis|UDP|TCP|  
|-----------------|---------|---------|  
|Zdalne zarządzanie systemem Windows przez protokół HTTP|--|5985|  

###  <a name="BKMK_PortsMacEnrollmentProxyPoint"></a>Komputer Mac--> punkt proxy rejestracji  

|Opis|UDP|TCP|  
|-----------------|---------|---------|  
|Protokół HTTPS|--|443|  

###  <a name="BKMK_PortsMP-DC"></a>Punkt zarządzania--> kontroler domeny  

|Opis|UDP|TCP|  
|-----------------|---------|---------|  
|Protokół LDAP (Lightweight Directory Access Protocol)|--|389|  
|Protokół LDAP (połączenie Secure Sockets Layer [SSL])|636|636|  
|Protokół LDAP wykazu globalnego|--|3268|  
|Protokół LDAP SSL wykazu globalnego|--|3269|  
|Mapowanie punktów końcowych wywołań RPC|135|135|  
|Zdalne wywołanie procedury|--|DYNAMICZNE (patrz adnotacja 6, **Porty dynamiczne**)|  

###  <a name="BKMK_PortsMP-Site"></a>Punkt zarządzania &lt; --> serwer lokacji  
 (patrz adnotacja 5, **Komunikacja między serwerem lokacji a systemami lokacji**)  

|Opis|UDP|TCP|  
|-----------------|---------|---------|  
|Mapowanie punktów końcowych wywołań RPC|--|135|  
|Zdalne wywołanie procedury|--|DYNAMICZNE (patrz adnotacja 6, **Porty dynamiczne**)|  
|Blok komunikatów serwera (SMB)|--|445|  

###  <a name="BKMK_PortsMP-SQL"></a>Punkt zarządzania--> program SQL Server  

|Opis|UDP|TCP|  
|-----------------|---------|---------|  
|SQL przez TCP|--|1433 (patrz adnotacja 2, **alternatywny port dostępne**)|  

###  <a name="BKMK_PortsMobileDeviceClient-EnrollmentProxyPoint"></a>Urządzenie przenośne--> punkt proxy rejestracji  

|Opis|UDP|TCP|  
|-----------------|---------|---------|  
|Protokół HTTPS|--|443|  

###  <a name="BKMK_PortsMobileDeviceClient-WindowsIntune"></a>Urządzenie przenośne--> program Microsoft Intune  

|Opis|UDP|TCP|  
|-----------------|---------|---------|  
|Protokół HTTPS|--|443|  

###  <a name="BKMK_PortsRSP-SQL"></a>Raportowanie punkt usług--> program SQL Server  

|Opis|UDP|TCP|  
|-----------------|---------|---------|  
|SQL przez TCP|--|1433 (patrz adnotacja 2, **alternatywny port dostępne**)|  

###  <a name="BKMK_PortsIntuneConnector-WindowsIntune"></a>Usługi punktu połączenia--> program Microsoft Intune  

|Opis|UDP|TCP|  
|-----------------|---------|---------|  
|Protokół HTTPS|--|443|
Aby uzyskać więcej informacji, zobacz [wymagania dotyczące dostępu do Internetu](/sccm/core/servers/deploy/configure/about-the-service-connection-point#bkmk_urls) punktu połączenia usługi.

###  <a name="BKMK_PortsAppCatalogWebServicePoint_SiteServer"></a>Serwer lokacji &lt; --> punkt usługi sieci web katalogu aplikacji  

|Opis|UDP|TCP|  
|-----------------|---------|---------|  
|Blok komunikatów serwera (SMB)|--|445|  
|Mapowanie punktów końcowych wywołań RPC|135|135|  
|Zdalne wywołanie procedury|--|DYNAMICZNE (patrz adnotacja 6, **Porty dynamiczne**)|  

###  <a name="BKMK_PortsAppCatalogWebSitePoint_SiteServer"></a>Serwer lokacji &lt; --> punkt witryny sieci Web katalogu aplikacji  

|Opis|UDP|TCP|  
|-----------------|---------|---------|  
|Blok komunikatów serwera (SMB)|--|445|  
|Mapowanie punktów końcowych wywołań RPC|135|135|  
|Zdalne wywołanie procedury|--|DYNAMICZNE (patrz adnotacja 6, **Porty dynamiczne**)|  

###  <a name="BKMK_PortsSite-AISP"></a>Serwer lokacji &lt; --> punkt synchronizacji analizy zasobów  

|Opis|UDP|TCP|  
|-----------------|---------|---------|  
|Blok komunikatów serwera (SMB)|--|445|  
|Mapowanie punktów końcowych wywołań RPC|135|135|  
|Zdalne wywołanie procedury|--|DYNAMICZNE (patrz adnotacja 6, **Porty dynamiczne**)|  

###  <a name="BKMK_PortsSite-Client"></a>Serwer lokacji--> Klient  

|Opis|UDP|TCP|  
|-----------------|---------|---------|  
|Wake On LAN|9 (patrz adnotacja 2, **alternatywny port dostępne**)|--|  

###  <a name="BKMK_PortsSiteServer-CloudDP"></a>Serwer lokacji--> punkt dystrybucji w chmurze  

|Opis|UDP|TCP|  
|-----------------|---------|---------|  
|Protokół HTTPS|--|443|  

###  <a name="BKMK_PortsSite-DP"></a>Serwer lokacji--> punkt dystrybucji  
 (patrz adnotacja 5, **Komunikacja między serwerem lokacji a systemami lokacji**)  

|Opis|UDP|TCP|  
|-----------------|---------|---------|  
|Blok komunikatów serwera (SMB)|--|445|  
|Mapowanie punktów końcowych wywołań RPC|135|135|  
|Zdalne wywołanie procedury|--|DYNAMICZNE (patrz adnotacja 6, **Porty dynamiczne**)|  

###  <a name="BKMK_PortsSite-DC"></a>Serwer lokacji--> kontroler domeny  

|Opis|UDP|TCP|  
|-----------------|---------|---------|  
|Protokół LDAP (Lightweight Directory Access Protocol)|--|389|  
|Protokół LDAP (połączenie Secure Sockets Layer [SSL])|636|636|  
|Protokół LDAP wykazu globalnego|--|3268|  
|Protokół LDAP SSL wykazu globalnego|--|3269|  
|Mapowanie punktów końcowych wywołań RPC|135|135|  
|Zdalne wywołanie procedury|--|DYNAMICZNE (patrz adnotacja 6, **Porty dynamiczne**)|  

###  <a name="BKMK_PortsCertificateRegistrationPoint_SiteServer"></a>Serwer lokacji &lt; --> punkt rejestracji certyfikatu  

|Opis|UDP|TCP|  
|-----------------|---------|---------|  
|Blok komunikatów serwera (SMB)|--|445|  
|Mapowanie punktów końcowych wywołań RPC|135|135|  
|Zdalne wywołanie procedury|--|DYNAMICZNE (patrz adnotacja 6, **Porty dynamiczne**)|  

###  <a name="BKMK_PortsEndpointProtection_SiteServer"></a>Serwer lokacji &lt; --> punkt programu Endpoint Protection  

|Opis|UDP|TCP|  
|-----------------|---------|---------|  
|Blok komunikatów serwera (SMB)|--|445|  
|Mapowanie punktów końcowych wywołań RPC|135|135|  
|Zdalne wywołanie procedury|--|DYNAMICZNE (patrz adnotacja 6, **Porty dynamiczne**)|  

###  <a name="BKMK_EnrollmentPoint_SiteServer"></a>Serwer lokacji &lt; --> punkt rejestracyjny  

|Opis|UDP|TCP|  
|-----------------|---------|---------|  
|Blok komunikatów serwera (SMB)|--|445|  
|Mapowanie punktów końcowych wywołań RPC|135|135|  
|Zdalne wywołanie procedury|--|DYNAMICZNE (patrz adnotacja 6, **Porty dynamiczne**)|  

###  <a name="BKMK_EnrollmentProxyPoint_SiteServer"></a>Serwer lokacji &lt; --> punkt proxy rejestracji  

|Opis|UDP|TCP|  
|-----------------|---------|---------|  
|Blok komunikatów serwera (SMB)|--|445|  
|Mapowanie punktów końcowych wywołań RPC|135|135|  
|Zdalne wywołanie procedury|--|DYNAMICZNE (patrz adnotacja 6, **Porty dynamiczne**)|  

###  <a name="BKMK_PortsSite-FSP"></a>Serwer lokacji &lt; --> rezerwowy punkt stanu  
 (patrz adnotacja 5, **Komunikacja między serwerem lokacji a systemami lokacji**)  

|Opis|UDP|TCP|  
|-----------------|---------|---------|  
|Blok komunikatów serwera (SMB)|--|445|  
|Mapowanie punktów końcowych wywołań RPC|135|135|  
|Zdalne wywołanie procedury|--|DYNAMICZNE (patrz adnotacja 6, **Porty dynamiczne**)|  

###  <a name="BKMK_PortSite-Internet"></a>Serwer lokacji--> Internet  

|Opis|UDP|TCP|  
|-----------------|---------|---------|  
|Protokół HTTP|--|80 (patrz adnotacja 1, **port serwera Proxy**)|  

###  <a name="BKMK_PortsIssuingCA_SiteServer"></a>Serwer lokacji &lt; --> urząd wystawiający certyfikaty (CA)  
 Ta komunikacja odbywa się podczas wdrażania profilów certyfikatów przy użyciu punkt rejestracji certyfikatu. Komunikacja nie jest używany przez każdy serwer lokacji w hierarchii. Zamiast tego jest używany tylko dla serwera lokacji na szczycie hierarchii.  

|Opis|UDP|TCP|  
|-----------------|---------|---------|  
|Mapowanie punktów końcowych wywołań RPC|135|135|  
|Zdalne wywołanie procedury (model DCOM)|--|DYNAMICZNE (patrz adnotacja 6, **Porty dynamiczne**)|  

###  <a name="BKMK_PortsSite-RSP"></a>Serwer lokacji &lt; --> punkt usług raportowania  
 (patrz adnotacja 5, **Komunikacja między serwerem lokacji a systemami lokacji**)  

|Opis|UDP|TCP|  
|-----------------|---------|---------|  
|Blok komunikatów serwera (SMB)|--|445|  
|Mapowanie punktów końcowych wywołań RPC|135|135|  
|Zdalne wywołanie procedury|--|DYNAMICZNE (patrz adnotacja 6, **Porty dynamiczne**)|  

###  <a name="BKMK_PortsSite-Site"></a>Serwer lokacji &lt; --> serwer lokacji  

|Opis|UDP|TCP|  
|-----------------|---------|---------|  
|Blok komunikatów serwera (SMB)|--|445|  

###  <a name="BKMK_PortsSite-SQL"></a>Serwer lokacji--> program SQL Server  

|Opis|UDP|TCP|  
|-----------------|---------|---------|  
|SQL przez TCP|--|1433 (patrz adnotacja 2, **alternatywny port dostępne**)|  

 Podczas instalacji lokacji, która używa zdalnego serwera SQL do obsługi bazy danych lokacji należy otworzyć następujące porty między serwerem lokacji a serwerem SQL:  

|Opis|UDP|TCP|  
|-----------------|---------|---------|  
|Blok komunikatów serwera (SMB)|--|445|  
|Mapowanie punktów końcowych wywołań RPC|135|135|  
|Zdalne wywołanie procedury|--|DYNAMICZNE (patrz adnotacja 6, **Porty dynamiczne**)|  

###  <a name="BKMK_PortsSite-Provider"></a>Serwer lokacji--> Dostawca programu SMS  

|Opis|UDP|TCP|  
|-----------------|---------|---------|  
|Blok komunikatów serwera (SMB)|--|445|  
|Mapowanie punktów końcowych wywołań RPC|135|135|  
|Zdalne wywołanie procedury|--|DYNAMICZNE (patrz adnotacja 6, **Porty dynamiczne**)|  

###  <a name="BKMK_PortsSite-SUP"></a>Serwer lokacji &lt; --> punkt aktualizacji oprogramowania  
 (patrz adnotacja 5, **Komunikacja między serwerem lokacji a systemami lokacji**)  

|Opis|UDP|TCP|  
|-----------------|---------|---------|  
|Blok komunikatów serwera (SMB)|--|445|  
|Protokół HTTP|--|80 lub 8530 (patrz adnotacja 3, **Windows Server Update Services**)|  
|Protokół HTTPS|--|443 lub 8531 (patrz adnotacja 3, **Windows Server Update Services**)|  

###  <a name="BKMK_PortsSite-SMP"></a>Serwer lokacji &lt; --> punkt migracji stanu  
 (patrz adnotacja 5, **Komunikacja między serwerem lokacji a systemami lokacji**)  

|Opis|UDP|TCP|  
|-----------------|---------|---------|  
|Blok komunikatów serwera (SMB)|--|445|  
|Mapowanie punktów końcowych wywołań RPC|135|135|  

###  <a name="BKMK_PortsProvider-SQL"></a> Dostawca programu SMS -- &gt; program SQL Server  

|Opis|UDP|TCP|  
|-----------------|---------|---------|  
|SQL przez TCP|--|1433 (patrz adnotacja 2, **alternatywny port dostępne**)|  

###  <a name="BKMK_PortsSUP-Internet"></a>Punkt aktualizacji oprogramowania--> Internet  

|Opis|UDP|TCP|  
|-----------------|---------|---------|  
|Protokół HTTP|--|80 (patrz adnotacja 1, **port serwera Proxy**)|  

###  <a name="BKMK_PortsSUP-WSUS"></a>Punkt aktualizacji oprogramowania--> nadrzędny serwer WSUS  

|Opis|UDP|TCP|  
|-----------------|---------|---------|  
|Protokół HTTP|--|80 lub 8530 (patrz adnotacja 3, **Windows Server Update Services**)|  
|Protokół HTTPS|--|443 lub 8531 (patrz adnotacja 3, **Windows Server Update Services**)|  

###  <a name="BKMK_PortsSQL-SQL"></a> SQL Server --&gt; SQL Server  
 Międzylokacyjna replikacja bazy danych wymaga programu SQL Server w jednej lokacji do komunikowania się bezpośrednio z serwerem SQL w swojej lokacji nadrzędnych i podrzędnych.  

|Opis|UDP|TCP|  
|-----------------|---------|---------|  
|Usługi SQL Server|--|1433 (patrz adnotacja 2, **alternatywny port dostępne**)|  
|SQL Server Service Broker|--|4022 (patrz adnotacja 2, **alternatywny port dostępne**)|  

> [!TIP]  
>  Menedżer konfiguracji nie wymaga usługi SQL Server Browser, która używa portu UDP 1434.  

###  <a name="BKMK_PortsStateMigrationPoint-to-SQL"></a>Stan punktu migracji--> program SQL Server  

|Opis|UDP|TCP|  
|-----------------|---------|---------|  
|SQL przez TCP|--|1433 (patrz adnotacja 2, **alternatywny port dostępne**)|  



###  <a name="BKMY_PortNotes"></a> Adnotacje dotyczące portów używanych przez systemy lokacji i klientów programu Configuration Manager  

1.  **Port serwera proxy**: Nie można skonfigurować tego portu, ale można go przekierować przez skonfigurowany serwer proxy.  

2.  **Alternatywny port dostępne**: Alternatywny port można zdefiniować w programie Configuration Manager dla tej wartości. Jeżeli zdefiniowano port niestandardowy, należy go zastąpić podczas definiowania informacji o filtrze IP dla zasad IPsec lub w celu skonfigurowania zapory.  

3.  **Windows Server Update Services (WSUS)**: Aby używała portów 80/443 lub portów 8530/8531 do komunikacji z klientem można zainstalować programu WSUS. Po uruchomieniu programu WSUS w systemie Windows Server 2012 lub Windows Server 2016, usługi WSUS są skonfigurowane, aby domyślnie używać portu 8530 do połączeń HTTP oraz portu 8531 dla protokołu HTTPS.  

     Po przeprowadzeniu instalacji można zmienić port. Nie jest konieczne używanie tego samego numeru portu w całej hierarchii lokacji.  

    -   Jeżeli port protokołu HTTP to 80, port protokołu HTTPS musi mieć wartość 443.  

    -   Jeśli port protokołu HTTP jest inny, HTTPS port musi być 1 lub nowszą, na przykład 8530 i 8531.   

    > [!NOTE]  
    >  W przypadku skonfigurowania punktu aktualizacji oprogramowania do używania protokołu HTTPS należy również otworzyć port HTTP. Dane niezaszyfrowane, np. umowy EULA do konkretnych aktualizacji, używają portu HTTP.  

4.  **Demon Trivial FTP (TFTP)**: Usługa systemowa demona Trivial FTP (TFTP) nie wymaga nazwy użytkownika ani hasła i jest integralną częścią usług wdrażania systemu Windows (WDS). Usługa demona Trivial TFTP implementuje obsługę protokołu TFTP zdefiniowanego przez następujące dokumenty RFC:  

    -   RFC 350: TFTP  

    -   RFC 2347: Opcja rozszerzenia  

    -   RFC 2348: Opcja rozmiaru bloku  

    -   RFC 2349: Limit czasu interwału i transfer opcje rozmiaru  

     Protokół TFTP jest przeznaczony do obsługi bezdyskowych środowisk rozruchowych. Demony TFTP nasłuchują w porcie UDP 69, ale odpowiadają z dynamicznie przydzielonego portu o wysokim numerze. W związku z tym w włączenie tego portu umożliwia usłudze TFTP odbieranie przychodzących żądań TFTP, ale nie zezwala na wybranym serwerze odpowiadać na te żądania. Nie można włączyć na wybranym serwerze odpowiadanie na przychodzące żądania TFTP, chyba że serwer TFTP jest skonfigurowany pod kątem odpowiadał za pośrednictwem portu 69.  

5.  **Komunikacja między serwerem lokacji a systemami lokacji**: Domyślnie komunikacja między serwerem lokacji a systemami lokacji jest dwukierunkowe. Serwer lokacji inicjuje komunikację w celu skonfigurowania systemu lokacji, a następnie większość systemów lokacji łączy się ponownie z serwerem lokacji, aby wysłać informacje o stanie. Punkty usług raportowania i punkty dystrybucji nie wysyłają informacji o stanie. W przypadku wybrania **wymagają serwera lokacji do nawiązania połączenia z tym systemem lokacji** właściwości systemu lokacji po zainstalowaniu systemu lokacji, systemu lokacji nie będzie inicjował komunikacji z serwerem lokacji. Zamiast tego serwer lokacji inicjuje komunikację i używa konta instalacji systemu lokacji do uwierzytelniania na serwerze systemu lokacji.  

6.  **Porty dynamiczne**: Porty dynamiczne (znane również jako porty efemeryczne) używają zakresu numerów portów zdefiniowanego przez wersję systemu operacyjnego. Więcej informacji o domyślnych zakresach portów znajduje się w temacie [Service overview and network port requirements for Windows (Omówienie usługi i wymagania dotyczące portów sieciowych w systemie Windows)](http://go.microsoft.com/fwlink/p/?LinkId=317965).  

##  <a name="BKMK_AdditionalPorts"></a> Dodatkowe listy portów  
 Poniższe sekcje zawierają dodatkowe informacje o portach używanych przez program Configuration Manager.  

###  <a name="BKMK_ClientShares"></a> Udziały klient-serwer  
 Klienci łączą się z udziałami UNC przy użyciu bloku komunikatów serwera (SMB). Na przykład:  

-   Ręczna instalacja klienta określający programu CCMSetup.exe **/source:** właściwość wiersza polecenia  

-   Klienci Endpoint Protection, którzy pobierają pliki definicji ze ścieżki UNC

|Opis|UDP|TCP|  
|-----------------|---------|---------|  
|Blok komunikatów serwera (SMB)|--|445|  

###  <a name="BKMK_SQLPorts"></a> Połączenia z programem Microsoft SQL Server  
 Do komunikacji z aparatem bazy danych programu SQL Server oraz replikacji międzylokacyjnej można użyć domyślnego portu programu SQL Server lub określić porty niestandardowe:  

-   Do komunikacji międzylokacyjnej są używane następujące usługi:  

    -   SQL Server Service Broker, która domyślnie określa port TCP 4022;  

    -   Usługi SQL Server, która domyślnie określa port TCP 1433.  

-   Komunikacja wewnątrzlokacyjna między aparatem bazy danych programu SQL Server i różne role systemu lokacji programu Configuration Manager domyślnie określa port TCP 1433.  

- Configuration Manager używa tego samego porty i protokoły do komunikowania się z każdej repliki grupy dostępności SQL, który jest hostem bazy danych lokacji tak, jakby replika była autonomicznego wystąpienia programu SQL Server.

Gdy używasz usługi Azure i bazy danych lokacji znajduje się za wewnętrzny lub zewnętrzny moduł równoważenia obciążenia, skonfiguruj następujące wyjątki zapory dla każdej repliki, a następnie dodaj reguły dla następujących portów równoważenia obciążenia:
 - SQL przez TCP: TCP 1433
 - SQL Server Service Broker: TCP 4022
 - Blok komunikatów serwera (SMB): TCP 445
 - Program mapowania punktów końcowych RPC: TCP 135

> [!WARNING]  
>  Menedżer konfiguracji nie obsługuje portów dynamicznych. Nazwane wystąpienia (gdy są używane) programu SQL Server domyślnie używają portów dynamicznych do połączeń z aparatem bazy danych, dlatego należy ręcznie skonfigurować port statyczny, który będzie używany do komunikacji wewnątrzlokacyjnej.  

 Następujące role systemu lokacji komunikują się bezpośrednio z bazą danych program SQL Server:  

-   Punkt usługi sieci Web Wykaz aplikacji  

-   Rola punktu rejestracji certyfikatu  

-   Rola punktu rejestracyjnego  

-   Punkt zarządzania  

-   Serwer lokacji  

-   Punkt usług raportowania  

-   dostawcy programu SMS  

-   Program SQL Server--> program SQL Server  

Jeżeli program SQL Server hostuje bazę danych z więcej niż jednej lokacji, każda baza danych musi używać osobnego wystąpienia programu SQL Server, a każde z tych wystąpień musi być skonfigurowane przy użyciu unikatowego zestawu portów.  

Jeśli Zapora jest włączona na komputerze serwera SQL, upewnij się, że jest skonfigurowana, aby umożliwić porty używane przez wdrożenie. Ponadto Konfigurowanie zapór, znajdujących się na dodatkowych lokalizacjach sieciowych między komputerami, które komunikują się z programem SQL Server, aby zezwolić na te same porty.  

Na przykład sposobu konfigurowania programu SQL Server do używania konkretnego portu zobacz [jak: Konfigurowanie serwera do nasłuchiwania na konkretnym porcie TCP (SQL Server Configuration Manager)](http://go.microsoft.com/fwlink/p/?LinkID=226349) w bibliotece TechNet programu SQL Server.  


### <a name="bkmk_discovery"></a> Odnajdywania i publikowania
Następujące porty są używane do odnajdywania i publikowaniu informacji o lokacji:
 - Lightweight Directory Access Protocol (LDAP): 389
 - LDAP (połączenie Secure Sockets Layer [SSL]): 636


 - Protokół LDAP wykazu globalnego: 3268
 - Protokół LDAP SSL wykazu globalnego: 3269


 - Program mapowania punktów końcowych RPC: 135
 - RPC: Dynamicznie przydzielane porty TCP wysoka


 - TCP: 1024: 5000
 - TCP:  49152: 65535


###  <a name="BKMK_External"></a> Połączenia zewnętrzne nawiązywane przez program Configuration Manager  
 Klienci programu Configuration Manager i systemy lokacji mogą nawiązywać następujące połączenia zewnętrzne:  

-   [Punkt synchronizacji analizy zasobów-- &gt; firmy Microsoft](#BKMK_PortsAI)  

-   [Punkt ochrony punktu końcowego-- &gt; Internet](#BKMK_PortsEndpointProtection_Internet)  

-   [Klient-- &gt; kontroler domeny wykazu globalnego](#BKMK_PortsClient-GCDC)  

-   [Konsola programu Configuration Manager-- &gt; Internet](#BKMK_PortsConsole-Internet)  

-   [Punkt zarządzania-- &gt; kontrolera domeny](#BKMK_PortsMP-DC)  

-   [Serwer lokacji-- &gt; kontrolera domeny](#BKMK_PortsSite-DC)  

-   [Serwer lokacji &lt;  --  &gt; wystawiającego certyfikaty urzędu certyfikacji (CA)](#BKMK_PortsIssuingCA_SiteServer)  

-   [Punkt aktualizacji oprogramowania-- &gt; Internet](#BKMK_PortsSUP-Internet)  

-   [Punkt aktualizacji oprogramowania-- &gt; nadrzędny serwer WSUS](#BKMK_PortsSUP-WSUS)  

-   [Usługa punktu połączenia — &gt; Microsoft Intune](#BKMK_PortsIntuneConnector-WindowsIntune)  

###  <a name="BKMK_IBCMports"></a> Wymagania instalacji systemów lokacji obsługujących klientów internetowych  
 Punkty zarządzania i punkty dystrybucji obsługujące klientów internetowych, punkt aktualizacji oprogramowania i rezerwowy punkt stanu instalacji i naprawy należy użyć następujące porty:  

-   Serwer lokacji--> system lokacji: Mapowania punktów końcowych RPC używa portu 135 protokołów UDP i TCP.  

-   Serwer lokacji--> system lokacji: Dynamiczne porty TCP usługi RPC  

-   Serwer lokacji &lt; --> system lokacji: Bloki komunikatów serwera (SMB) za pomocą protokołu TCP port 445

Instalacje aplikacji i pakietów w punktach dystrybucji wymagają następujących portów usługi RPC:  

-   Serwer lokacji--> punkt dystrybucji: Program mapowania punktów końcowych RPC używa portu 135 protokołów UDP i TCP

-   Serwer lokacji--> punkt dystrybucji: Dynamiczne porty TCP usługi RPC  

Aby ułatwić ochronę ruchu między serwerem lokacji a systemami lokacji, używaj protokołu IPsec. Jeśli jest konieczne ograniczenie portów dynamicznych używanych przez usługę RPC, możesz użyć narzędzia konfiguracji Microsoft RPC (rpccfg.exe) i skonfigurować ograniczony zakres portów dla pakietów RPC. Więcej informacji o narzędziu konfiguracji usługi RPC znajduje się w temacie [Jak skonfigurować wywoływanie RPC w taki sposób, aby używało pewnych portów, i jak ułatwić zabezpieczanie tych portów za pomocą zasad IPsec](http://go.microsoft.com/fwlink/p/?LinkId=124096).  

> [!IMPORTANT]  
>  Przed zainstalowaniem tych systemów lokacji, upewnij się, że usługa Rejestr zdalny jest uruchomiona na serwerze systemu lokacji i że określono konto instalacji systemu lokacji, jeśli system lokacji znajduje się w innym lesie usługi Active Directory bez relacji zaufania.  

###  <a name="BKMK_PortsClientInstall"></a> Porty używane przez instalację klienta programu Configuration Manager  
Porty używane podczas instalacji klienta zależą od metody wdrażania klienta. Aby lista portów używanych w poszczególnych metodach wdrażania klienta, zobacz **porty używane podczas wdrażania klienta programu Configuration Manager** w [zapory systemu Windows i ustawienia portu dla klientów w programie System Center Configuration Manager](../../../core/clients/deploy/windows-firewall-and-port-settings-for-clients.md) tematu. Aby uzyskać informacje o sposobie konfigurowania Zapory systemu Windows na kliencie instalacji klienta komunikacji i po instalacji, zobacz [zapory systemu Windows i ustawienia portu dla klientów w programie System Center Configuration Manager](../../../core/clients/deploy/windows-firewall-and-port-settings-for-clients.md).  

###  <a name="BKMK_MigrationPorts"></a> Porty używane przez migrację  
Serwer lokacji, która jest uruchamiana migracja korzysta z kilku portów nawiązać połączenia z odpowiednimi lokacjami w hierarchii źródłowej do zbierania danych z baz danych programu SQL Server lokacji źródłowych i udostępnianie punktów dystrybucji.  

 Informacje te porty, zobacz [konfiguracje wymagane do migracji](../../../core/migration/prerequisites-for-migration.md#BKMK_Required_Configurations) w sekcji [wymagania wstępne dotyczące migracji w programie System Center Configuration Manager](../../../core/migration/prerequisites-for-migration.md) tematu.  

###  <a name="BKMK_ServerPorts"></a> Porty używane przez system Windows Server  
 W poniższej tabeli wymieniono niektóre najważniejsze porty używane przez system Windows Server oraz ich odpowiednich funkcji. Bardziej szczegółowy wykaz wymagań dotyczących usług i portów sieciowych systemu Windows Server znajduje się w temacie [Omówienie usług i wymagania dotyczące portów sieciowych dla systemu Windows Server](http://go.microsoft.com/fwlink/p/?LinkID=123652).  

|Opis|UDP|TCP|  
|-----------------|---------|---------|  
|System nazw domen (DNS)|53|53|  
|Protokół DHCP|67 i 68|--|  
|Rozpoznawanie nazw NetBIOS|137|--|  
|Usługa datagramów NetBIOS|138|--|  
|Usługa sesji NetBIOS|--|139|  
