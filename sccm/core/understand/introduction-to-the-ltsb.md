---
title: "Wprowadzenie do długoterminowego gałęzi obsługi | Dokumentacja firmy Microsoft"
description: "Więcej informacji na temat długoterminowej gałęzi obsługi programu System Center Configuration Manager."
ms.custom: na
ms.date: 05/01/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 694bc29f-a7fd-4e06-815a-1a9c5e9ac563
caps.latest.revision: "0"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 91c1ca860069c6ebe0d20230c4620bf3f68735a2
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="introduction-to-the-long-term-servicing-branch-of-system-center-configuration-manager"></a>Wprowadzenie do długoterminowego gałęzi obsługi programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (długoterminowej obsługi oddziału)*

Długoterminowe Servicing Branch (LTSB) programu System Center Configuration Manager jest gałęzią różne Menedżera konfiguracji, który został zaprojektowany jako opcji do zainstalowania dostępne dla wszystkich klientów. Jednak jest jedyną opcją dla klientów, którzy let wygaśnięcie ich Software Assurance (SA) lub prawa równoważne subskrypcji programu Configuration Manager.


W oparciu o 1606 wersji programu Configuration Manager, LTSB ma ograniczone funkcje w porównaniu do bieżącej gałęzi programu Configuration Manager.

 > [!TIP]   
 > Jeśli szukasz informacji na temat oddziały **systemu Windows Server**, zobacz [systemu Windows Server 2016 nowe Current Branch dla firm opcji obsługi]( https://blogs.technet.microsoft.com/windowsserver/2016/07/12/windows-server-2016-new-current-branch-for-business-servicing-option/).

## <a name="features-that-are-not-available-in-the-ltsb-of-configuration-manager"></a>Funkcje, które nie są dostępne w LTSB Configuration Manager
Bieżąca gałąź programu Configuration Manager obsługuje następujące funkcje, które jest niedostępne, gdy używasz LTSB:

-   W konsoli aktualizacji dodawać nowe funkcje i ulepszenia.
-   Obsługa nowo wydanego systemów operacyjnych do użycia jako serwery lokacji i klientów.
-   Korzystanie z subskrypcji usługi Microsoft Intune do obsługi.
    -   Usługa Intune w konfiguracji zarządzania urządzeniami Przenośnymi hybrydowych urządzeń przenośnych
    -   Lokalne zarządzanie urządzeniami Przenośnymi
-   Nawigacyjnym obsługi systemu Windows 10 i plany obsługi, w tym obsługę najnowszych systemu Windows 10 Current Branch (CB) i Current Branch dla wersji Business (CBB).  
-   Obsługa w przyszłych wersjach systemu Windows Server i Windows 10 LTSB
-   Analiza zasobów
-   Chmurowe punkty dystrybucji
-   Usługi Exchange Online jako łącznik programu Exchange    

Mimo że obsługi dla tych funkcji nie są dostępne z LTSB, niektóre funkcje są widoczne w konsoli programu Configuration Manager, ale nie zostanie wybrana lub używane.


## <a name="find-documentation-for-the-ltsb"></a>Znajdź dokumentację dotyczącą LTSB
LTSB jest oparty na wersji Current Branch 1606. Dokumentacja produktu, użyj [dokumentacji Current Branch](https://docs.microsoft.com/sccm/), ostrzeżenia i ograniczenia, które są specyficzne dla LTSB. Te zastrzeżenia i ograniczenia są identyfikowane w następujących tematach online:

-     [Wprowadzenie do długoterminowego gałęzi obsługi](introduction-to-the-ltsb.md): (W tym temacie)
-     [Zainstaluj długoterminowej gałęzi obsługi](install-the-ltsb.md)
-     [Uaktualnij długoterminowej obsługi gałęzi do bieżącej gałęzi](convert-to-current-branch.md)
-     [Obsługiwane konfiguracje dla wersji Long-Term Servicing Branch](supported-configurations-for-ltsb.md)
-   [Zarządzanie długoterminowej gałęzi obsługi programu Configuration Manager](manage-the-ltsb.md)

Podając odniesienie Current Branch dokumentacji LTSB szczegółowe informacje, które dotyczą wersji 1606 dotyczą również LTSB. Funkcje lub szczegóły, które są wprowadzane z wersją 1610 lub nowsze nie są obsługiwane przez LTSB.


## <a name="licensing-overview-for-the-ltsb"></a>Omówienie licencji dla LTSB   
Klienci z active Software Assurance (SA) licencji programu System Center Configuration Manager lub z prawami równoważne subskrypcji, począwszy od 1 do października 2016 r. mają prawa do korzystania z tego wydania wersji 1606 października 2016 programu System Center Configuration Manager. Klienci z uprawnieniami do programu System Center Configuration Manager na lub po 1 października 2016 r., będą dostępne dwa opcje licencjonowanego podczas instalacji: Bieżąca gałąź i długoterminowych obsługi Branch (LTSB).

Klienci, które mają prawa bezterminowo do programu System Center Configuration Manager lub zezwalające na SA lub subskrypcji wygaśnięcie po 1 października można zainstalować wersji programu System Center Configuration Manager LTSB są aktualne w momencie wygaśnięcia.

[Zakończenie warunki i postanowienia dla produktów można zakupić za pośrednictwem programów licencjonowania zbiorowego firmy Microsoft można znaleźć tutaj](http://go.microsoft.com/fwlink/?LinkId=800052).

Zobacz [licencji programu System Center Configuration Manager i gałęzie](learn-more-editions.md) Aby uzyskać więcej informacji na temat licencjonowania dla gałęzi programu Configuration Manager.

## <a name="next-steps"></a>Następne kroki

Jeśli zdecydujesz, że LTSB programu Configuration Manager jest poprawne gałęzie w danym środowisku [zainstalować nowy LTSB](/sccm/core/understand/install-the-ltsb#install-a-new-site) lokacji w ramach nowej hierarchii, lub [uaktualniania lokacji programu System Center 2012 Configuration Manager](/sccm/core/understand/install-the-ltsb#upgrade-from-system-center-2012-configuration-manager) i hierarchii.

Jeśli nie masz nośnika instalacyjnego, zobacz [dokumentacji programu System Center 2016](https://technet.microsoft.com/system-center-docs/system-center) Aby uzyskać informacje dotyczące sposobu uzyskania programu System Center 2016, w tym nośnika można użyć do zainstalowania LTSB System Center Configuration Manager.  
