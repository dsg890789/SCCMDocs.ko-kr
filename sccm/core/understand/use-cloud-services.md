---
title: "Użyj usługi w chmurze z programem Configuration Manager | Dokumentacja firmy Microsoft"
description: "Zainicjuj obsługę zasobów w chmurze programu System Center Configuration Manager uzupełnienie infrastruktury lokalnej."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 24fca61e-9cdb-447a-ad7a-f4d2e4fd6704
caps.latest.revision: "10"
caps.handback.revision: "0"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 52f7c63d155d5c34f0f12e13020767dec1867dab
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="use-cloud-services-with-system-center-configuration-manager"></a>Korzystanie z usług w chmurze w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

System Center Configuration Manager obsługuje kilka opcji działających w chmurze. Te można uzupełnić infrastrukturę lokalną i mogą pomóc w rozwiązywaniu problemów biznesowych, takich jak:  

-   Jak zarządzać BYOD (przy użyciu usługi Intune do zarządzania urządzeniami przenośnymi).  

-   Jak dostarczanie zasobów zawartości klientom izolowanym i zasobom w intranecie, poza zaporą firmową (przy użyciu punktów dystrybucji w chmurze).  

-   Jak skalować w poziomie infrastruktury, gdy sprzętu fizycznego nie jest dostępna lub nie jest logicznie umieszczone na różnych potrzeb (używając maszyny wirtualne Microsoft Azure).  

Mimo że udostępnianie zasobów chmury nie jest element, który należy wykonać przed wdrożeniem programu Configuration Manager, korzystne może okazać się poznanie tych opcji przed osiągnięciem późnego etapu planowania hierarchii. Wykorzystanie zasobów chmury może zaoszczędzić oszczędność pieniędzy i czasu, podczas rozwiązywania problemów biznesowych nie infrastruktury lokalnej.  

## <a name="cloud-based-resources-you-can-use-with-configuration-manager"></a>Zasoby oparte na chmurze, których można używać z programem Configuration Manager  
 Każda opcja charakteryzuje się innymi wymaganiami, w związku z czym należy zapoznać się szczegółowo z każdą z nich, aby zrozumieć związane z nią charakterystyczne wymagania, ograniczenia i potencjalne koszty dodatkowe.  

-   Informacje dotyczące punktów dystrybucji w chmurze, zobacz [zainstalować punkty dystrybucji w chmurze](/sccm/core/servers/deploy/configure/install-cloud-based-distribution-points-in-microsoft-azure).

-   Aby uzyskać więcej informacji na temat usługi Azure, zobacz [Azure](http://go.microsoft.com/fwlink/p/?LinkId=262965) w bibliotece MSDN.  

### <a name="azure-virtual-machines-for-cloud-based-infrastructure"></a>Maszyny wirtualne platformy Azure (dla infrastruktury opartej na chmurze)  
 Menedżer konfiguracji obsługuje wykorzystanie komputerów działających na maszynach wirtualnych na platformie Azure, tak samo, jak uruchomienia lokalnie w fizycznej sieci firmowej. Maszyn wirtualnych platformy Azure możesz używać w następujących scenariuszach:  

-   **Scenariusz 1:** Można uruchomić programu Configuration Manager na maszynie wirtualnej i przy jego użyciu zarządzać klientami zainstalowanymi na innych maszynach wirtualnych.  

-   **Scenariusz 2:** Można uruchomić programu Configuration Manager na maszynie wirtualnej i przy jego użyciu zarządzać klientami, którzy nie działają na platformie Azure.  

-   **Scenariusz 3:** Różne role systemu lokacji programu Configuration Manager można uruchamiać na maszynach wirtualnych podczas uruchamiania innych ról w fizycznej sieci firmowej (z odpowiednią łącznością sieciową na potrzeby komunikacji).  

Te same wymagania dotyczące sieci, systemów operacyjnych i wymagania sprzętowe, które dotyczą instalowania programu Configuration Manager w fizycznej sieci firmowej również zastosować do instalacji programu Configuration Manager na platformie Azure.  

Subskrypcja platformy Azure jest wymagany do użycia maszyn wirtualnych platformy Azure. Wiąże się z opłatami na podstawie liczby maszyn wirtualnych, których używasz, konfiguracji i użycia zasobów w chmurze.  

Ponadto Lokacje programu Configuration Manager i klientów z systemami na maszynach wirtualnych platformy Azure obowiązują te same wymagania licencyjne co w przypadku instalacji lokalnych.  

### <a name="azure-services-for-cloud-based-distribution-points"></a>Usług Azure (dla punktów dystrybucji w chmurze)  
 Usługa Azure służy do punktu dystrybucji programu Configuration Manager, który jest nazywany też punktem dystrybucji w chmurze o nazwie hosta. Możesz [użyć punktu dystrybucji w chmurze w programie System Center Configuration Manager](../../core/plan-design/hierarchy/use-a-cloud-based-distribution-point.md) równolegle z lokalnymi punktami dystrybucji oraz punktami dystrybucji wdrożonymi na maszynach wirtualnych platformy Azure.  

 Sytuacja ta różni się od korzystania z maszyny wirtualnej platformy Azure, na której wdrożono rolę systemu lokacji. Punkty dystrybucji w chmurze:  

-   Uruchom jako usługa na platformie Azure, nie na maszynie wirtualnej.  

-   Automatycznie skalować, aby spełnić zwiększona zawartości żądania od klientów.  

-   Obsługa klientów internetowych i intranetowych.  

Do używania Azure do punktów dystrybucji hosta jest wymagana jest subskrypcja platformy Azure. Wiąże się z opłatami na podstawie ilości danych transferowanych do i z usługi.  

### <a name="microsoft-intune-for-mobile-device-management"></a>Microsoft Intune (do zarządzania urządzeniami przenośnymi)  
 Można je zintegrować swoją subskrypcję Microsoft Intune z programem Configuration Manager w celu umożliwienia zarządzania urządzeniami przy użyciu usługi Intune. Integracja ta:  

-   Jest nazywana konfiguracją hybrydową, i rozszerza programu Configuration Manager (lub usługi Intune, w zależności od perspektywy) do obsługi różnych urządzeń.  

-   Wymaga programu Microsoft Intune Connector roli systemu lokacji.  

-   Wymaga oddzielnej subskrypcji usługi Intune z odpowiednią liczbą licencji dla urządzeń, którymi można zarządzać przy użyciu usługi Intune.  

Mimo że usługa Intune używa usługi Azure, nie wymaga niezależnej konfiguracji platformy Azure ani nie wiąże się z dodatkowymi kosztami poza subskrypcją usługi Intune.  

### <a name="additional-configuration-manager-capabilities"></a>Dodatkowe funkcje programu Configuration Manager  
 Niektóre funkcje programu Configuration Manager mogą łączyć się usług w chmurze, takich jak:  

-   Windows Server Update Services (WSUS).  

-   Menedżer konfiguracji usługi chmury, do pobierania aktualizacji dla programu Configuration Manager.  

Te dodatkowe możliwości nie wymagają posiadania subskrypcji platformy Azure. Nie masz konfigurowania określonych połączeń, certyfikatów i usług w chmurze. Zamiast tego zarządza nimi automatycznie przez program Configuration Manager dla Ciebie. Wszystko, co należy zrobić to zapewnić odpowiednie systemy lokacji i urządzenia mają dostęp do internetowych adresów URL.  

##  <a name="BKMK_CloudSec"></a>Zabezpieczenia usług w chmurze  
 Configuration Manager używa certyfikatów do udostępnienia i dostępu do zawartości na platformie Azure oraz do zarządzania usługami, których używasz. Configuration Manager szyfruje dane przechowywane na platformie Azure, ale nie zapewnia dodatkowych zabezpieczeń i kontroli danych poza zapewnianymi przez platformę Azure.  

 Aby uzyskać więcej informacji zobacz szczegóły w scenariuszach różnych zasobów chmurowych. Można również znaleźć w poniższych tematach zabezpieczeń platformy Azure:  

-   [Azure: Opis zarządzania kontami zabezpieczeń w systemie Azure](http://go.microsoft.com/fwlink/p/?LinkId=262968)  

-   [Przegląd zabezpieczeń platformy Azure](http://go.microsoft.com/fwlink/p/?LinkId=262970)  

-   [Get Past skrzyżowaniach zabezpieczeń w migracja do chmury](http://go.microsoft.com/fwlink/p/?LinkId=262971)  

-   [Bezpieczeństwo danych w Azure część 1 z 2](http://go.microsoft.com/fwlink/p/?LinkId=262974)  
