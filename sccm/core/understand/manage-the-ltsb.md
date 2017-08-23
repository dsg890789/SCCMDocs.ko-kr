---
title: "Zarządzanie LTSB | Dokumentacja firmy Microsoft"
description: "Różnice dotyczące zarządzania dla LTSB programu System Center Configuration Manager."
ms.custom: na
ms.date: 05/01/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8da2887a-fd8e-438c-b926-849c121f7fdf
caps.latest.revision: "0"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 9c6f349ead906532a7a58df74609de976769e251
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="manage-the-long-term-servicing-branch-of-configuration-manager"></a>Zarządzanie długoterminowe obsługi gałęzi programu Configuration Manager

*Dotyczy: System Center Configuration Manager (długoterminowej obsługi oddziału)*

Gdy używasz długoterminowe Servicing Branch (LTSB) programu System Center Configuration Manager poniżej mogą ułatwić zrozumienie ważnych zmian, które mają wpływ na sposób zarządzania infrastrukturą.

Ponieważ LTSB jest odpowiednikiem wersji Current Branch 1606 (z pewnymi wyjątkami jak integracja usługi Intune i funkcje dotyczące chmury), większość zadań używanych w przypadku planowania, wdrażania, konfiguracji i bieżące zarządzanie są takie same.

Na przykład LTSB obsługuje taką samą liczbę witryn, typów lokacji, klientów i infrastruktury ogólne, jako bieżącej gałęzi. W takim przypadku używane wskazówki znalezionych w lokacji i hierarchii tematy dotyczące planowania i projektowania dla bieżącej gałęzi. Podobnie dla funkcji z LTSB, które są obsługiwane przez obu gałęzi, takich jak aktualizacje oprogramowania i wdrożenia systemu operacyjnego, należy używać wskazówki znaleziono w tych sekcjach dokumentacji bieżącej gałęzi, z zastrzeżeniami z nie mieli dostęp do funkcji wprowadzone po wersji 1606 bieżącej gałęzi.

Poniższe sekcje zawierają informacje o zarządzanie zadaniami, które nie są podobne.

## <a name="updates-and-servicing"></a>Aktualizacje i obsługa
Tylko krytyczne aktualizacje zabezpieczeń stają się dostępne jako aktualizacje w konsoli w LTSB.  

Informacje o regularne aktualizacje dla następnych wersji Current Branch są widoczne w konsoli, ale nie są udostępniane na LTSB. Nie zostaną pobrane, a nie może zostać zainstalowana.

Aby obsługiwać aktualizacje w konsoli dla krytycznych poprawek, LTSB lokacji wymaga użycia [punkt połączenia z usługą](/sccm/core/servers/deploy/configure/about-the-service-connection-point). Ta rola systemu lokacji można skonfigurować w trybie offline lub online, co jest wykonywane dla bieżącej gałęzi. LTSB zbiera i przesyła tych samych danych telemetrycznych i użycie jako bieżącej gałęzi.

LTSB obsługuje korzystanie z instalatora poprawek i narzędzia rejestracji aktualizacji zgodnie z opisem dla bieżącej gałęzi.

Aby uzyskać ogólne informacje dotyczące aktualizacji i obsługi, zobacz [aktualizacje programu Configuration Manager](/sccm/core/servers/manage/updates).


## <a name="changes-for-site-expansion-and-the-cdlatest-folder"></a>Zmiany dotyczące rozszerzania lokacji i dysku CD. Najnowszego folderu
Po uruchomieniu LTSB i są rozszerzania autonomicznej lokacji głównej, instalując nową centralną lokację administracyjną, musisz użyć Instalatora i plików źródłowych z nośnika linii bazowej 1606 wersji. Dla bieżącej gałęzi uruchom Instalatora i użyć plików źródłowych z dysku CD. Najnowszy folder.

Mimo że rozszerzenia lokacji nie uruchamia Instalatora z dysku CD. Najnowszy folder, możesz nadal używać dysku CD. Najnowszy folder site Recovery, a także do zainstalowania nowej podrzędnej lokacji głównej, jeśli pierwsza lokacja LTSB była centralną lokację administracyjną.

Aby uzyskać więcej informacji na temat rozszerzania lokacji, zobacz [rozszerzenia autonomicznej lokacji głównej](/sccm/core/servers/deploy/install/use-the-setup-wizard-to-install-sites#expand-a-stand-alone-primary-site). Aby uzyskać więcej informacji o dysku CD. Najnowszy folder, zobacz [CD. Najnowszy folder](/sccm/core/servers/manage/the-cd.latest-folder).


## <a name="recovery"></a>Odzyskiwanie
Po odzyskaniu lokacji należy przywrócić witryny lub bazy danych lokacji do jego oryginalnej gałęzi. Nie można odzyskać bazy danych lokacji bieżącej gałęzi do instalacji LTSB lub na odwrót.
