---
title: "Instalowanie lokacji za pomocą nośnika linii bazowej 1606 | Dokumentacja firmy Microsoft"
description: Zainstaluj lub Uaktualnij do LTSB programu System Center Configuration Manager.
ms.custom: na
ms.date: 05/01/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f4f9a5fd-f573-4b99-ad93-b2c76812e922
caps.latest.revision: "0"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 39653604ba5fd8e1fe9dd4d42889221d983f9bec
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="install-and-upgrade-with-the-version-1606-baseline-media-for-system-center-configuration-manager"></a>Instalowanie i uaktualnianie z wersji 1606 nośnika linii bazowej programu System Center Configuration Manager

*Dotyczy:  Program System Center Configuration Manager (Current Branch), (długoterminowej obsługi Branch)*

Po uruchomieniu Instalatora z nośnika linii bazowej 1606 wersji programu Configuration Manager, można zainstalować gałęzi obsługi długoterminowe lub lokacją bieżącej gałęzi programu System Center Configuration Manager.

Nośnika linii bazowej jest dostępna na dysku DVD jako część programu Microsoft System Center 2016 lub wersji programu System Center Configuration Manager (Current Branch i długoterminowe obsługi gałęzi 1606). Aby zapoznać się z nośnika linii bazowej, zobacz [wersje linii bazowej i aktualizacji](/sccm/core/servers/manage/updates#baseline-and-udpate-versions).


Gdy używasz nośnika linii bazowej 1606 wersji jest lokacji instalacji lub uaktualnienia do:
- A *lokacji bieżącej gałęzi* będący odpowiednikiem lokacji, która została pierwszy zainstalowany za pomocą nośnika linii bazowej 1511, a następnie zaktualizować ją do wersji 1606 plus 1606 pakiet poprawek - KB3186654.
-   *Lokacji LTSB* będący odpowiednikiem lokacji bieżącej gałęzi, która uruchamia pakiet zbiorczy poprawek wersji 1606 plus 1606 - KB3186654. Nośnika linii bazowej zawiera już ten pakiet zbiorczy poprawek.  Ale LTSB nie obsługuje wszystkie funkcje lub możliwości dostępne w bieżącej gałęzi, zgodnie z opisem w [wprowadzenie do długoterminowe obsługi gałęzi programu System Center Configuration Manager](introduction-to-the-ltsb.md).

Jeśli nie masz doświadczenia z różnych oddziałów programu System Center Configuration Manager, zobacz [która gałąź programu Configuration Manager należy używać](which-branch-should-i-use.md).




## <a name="changes-to-setup-with-the-1606-baseline-media"></a>Zmiany w instalacji z nośnika linii bazowej 1606
Nośnika linii bazowej 1606 wprowadzono następujące zmiany do instalacji programu Configuration Manager.

### <a name="branch-and-edition"></a>Gałęzi i wersji
Po uruchomieniu Instalatora jest teraz wyświetlana strona licencjonowania, w którym można wybrać gałęzi programu Configuration Manager do zainstalowania. Można wybrać Current Branch lub LTSB jako licencjonowanej instalacji lub można wybrać wersję ewaluacyjną bieżącej gałęzi jako instalację bez licencji.

Aby uzyskać więcej informacji, zobacz [licencjonowania i gałęzi programu System Center Configuration Manager](learn-more-editions.md).

### <a name="software-assurance-expiration"></a>Software Assurance wygaśnięcia
Podczas instalacji, istnieje możliwość wprowadzenia **Data wygaśnięcia Software Assurance** wartość. Jest to wartość opcjonalna wskazanym jako wygodny monitu.

> [!NOTE]
> Microsoft nie można zweryfikować datę wygaśnięcia, wprowadź i nie będzie używać tej daty sprawdzanie oryginalności licencji.  Należy zamiast tego należy używać go jako przypomnienie daty wygaśnięcia. Jest to przydatne, ponieważ programu Configuration Manager okresowo sprawdza, czy nowe aktualizacje oprogramowania oferowanych online, a stan licencji gwarancji oprogramowania powinna być bieżącego na kwalifikować się do korzystania z tych dodatkowych aktualizacji.    

- Można określić wartość daty na **klucz produktu** strony Kreatora instalacji po uruchomieniu Instalatora w wersji System Center Configuration Manager 1606 nośnika linii bazowej.
- Ta data można również określić, wybierając **właściwości ustawień hierarchii** > **licencjonowania** w konsoli programu Configuration Manager.

Aby uzyskać więcej informacji, zobacz "Software Assurance umów" w [licencjonowania i gałęzi programu System Center Configuration Manager](learn-more-editions.md).


### <a name="additional-pre-upgrade-configurations"></a>Dodatkowe konfiguracje przed uaktualnieniem
Przed rozpoczęciem uaktualnienia programu System Center 2012 Configuration Manager do LTSB, należy wykonać następujące dodatkowe czynności w ramach Lista kontrolna uaktualniania wstępnego.  
Odinstaluj role systemu lokacji, które nie obsługują LTSB:
- Punkt synchronizacji analizy zasobów
- Łącznik usługi Microsoft Intune
- Chmurowe punkty dystrybucji

Aby uzyskać więcej informacji, zobacz [uaktualnienia do programu System Center Configuration Manager](/sccm/core/servers/deploy/install/upgrade-to-configuration-manager).


### <a name="new-scripted-installation-options"></a>Nowe opcje skryptowej instalacji
Nośnika linii bazowej 1606 wersja obsługuje nowy klucz pliku skryptu instalacji nienadzorowanej przy użyciu skryptu instalacji nowej lokacji najwyższego poziomu. Dotyczy to instalowanie nowej autonomicznej lokacji głównej lub dodawanie centralnej lokacji administracyjnej w ramach scenariusza rozszerzania lokacji.

Zainstaluj licencjonowaną gałęzi za pomocą skryptu instalacji nienadzorowanej, należy dodać do sekcji Opcje skryptu poniższej sekcji, nazwy kluczy i wartości. Nie trzeba było ich użyć do skryptu instalacji wersji ewaluacyjnej bieżącej gałęzi:  

 **SABranchOptions**
-   **Nazwa klucza: SAActive**
  - Wartości: 0 lub 1.  
  - Szczegóły:  bez licencji wersji ewaluacyjnej Current Branch instaluje 0 i 1 instaluje licencjonowaną wersję.   

- **CurrentBranch**
  - Wartości: 0 lub 1.  
  - Szczegóły:  Gałąź obsługi długoterminowe instaluje 0 i 1 instaluje bieżącej gałęzi.  

Na przykład, Zainstaluj licencjonowaną wersję Current Branch, których można użyć:

  **Nazwa klucza: SABranchOptions**
   -    **SAActive = 1**
   - **CurrentBranch = 1**


> [!IMPORTANT]  
> **SABranchOptions** działa tylko w przypadku instalacji z nośnika linii bazowej. Nie ma zastosowania po uruchomieniu Instalatora z dysku CD. Najnowszy folder lokacji została wcześniej zainstalowana przy użyciu wersji 1606 nośnika linii bazowej.
>
> **SABranchOptions** nie ma zastosowania do skryptową uaktualnienia programu System Center 2012 Configuration Manager i zawsze powoduje bieżącej gałęzi.

Aby uzyskać więcej informacji, zobacz [użyć wiersza polecenia do zainstalowania lokacji programu System Center Configuration Manager](/sccm/core/servers/deploy/install/use-a-command-line-to-install-sites).


## <a name="install-a-new-site"></a>Zainstalować nową lokację
Używanie 1606 nośnika linii bazowej do zainstalowania nowej lokacji albo gałęzi, użyj witryny planowania, przygotowywania, i procedury instalacji opisane w [witryn instalowania programu System Center Configuration Manager](/sccm/core/servers/deploy/install/installing-sites) tematu, dodając następujące zagadnienia dotyczące instalacji:

- Podczas instalacji należy wybrać gałęzi Menedżera konfiguracji, który ma zostać zainstalowany, a następnie można określić szczegółów umowy Software Assurance.
- Wszystkie lokacje w tej samej hierarchii należy uruchomić na tym samym oddziale. Mieć hierarchii o różnych LTSB i bieżącej gałęzi w różnych lokacjach nie jest obsługiwane.
-   Nowa instalacja przy użyciu skryptu. Aby uzyskać więcej informacji, zobacz "New inicjowanych przez skrypty opcje instalacji" w tym artykule.

## <a name="expand-a-stand-alone-primary-site"></a>Rozszerzenia autonomicznej lokacji głównej
Po rozwinięciu autonomicznej lokacji głównej, która uruchamia LTSB.  Proces nie różni się od używanego dla bieżącej gałęzi witryny o jedno zastrzeżenie::

- Podczas instalowania nowej centralnej lokacji administracyjnej musisz użyć Instalatora z oryginalnego nośnika źródłowego użytego do zainstalowania lokacji LTSB. Instalator jest uruchamiany z dysku CD. Najnowsze folderu, w tym scenariuszu nie jest obsługiwane.

Aby uzyskać więcej informacji na temat rozszerzania lokacji, zobacz "Rozszerzania autonomicznej lokacji głównej" w [instalowanie lokacji za pomocą Kreatora instalacji](/sccm/core/servers/deploy/install/use-the-setup-wizard-to-install-sites).

## <a name="upgrade-from-system-center-2012-configuration-manager"></a>Uaktualnianie programu System Center 2012 Configuration Manager
Podczas uaktualniania programu System Center 2012 Configuration Manager, użyj witryny planowania, przygotowywania i procedur zgodnie z opisem w [uaktualnienia do programu System Center Configuration Manager](/sccm/core/servers/deploy/install/upgrade-to-configuration-manager) temacie, ale bez następujące zmiany:

**Uaktualnij do bieżącej gałęzi:**
- Podczas instalacji musisz wybrać bieżącej gałęzi, i określeniu szczegółów umowy programu Software Assurance.
-   Nowa instalacja przy użyciu skryptu. Aby uzyskać więcej informacji, zobacz "New inicjowanych przez skrypty opcje instalacji" w tym artykule.

**Uaktualnij do LTSB:**  
- Dodatkowe kroki polegające na poniższe liście kontrolnej przed uaktualnieniem.
- Podczas instalacji należy wybrać LTSB i określeniu szczegółów umowy programu Software Assurance.
- Można uaktualnić tylko lokacji z uruchomionym programem System Center 2012 Configuration Manager z dodatkiem Service Pack 2 lub System Center 2012 R2 Configuration Manager z dodatkiem Service Pack 1.

### <a name="in-place-upgrade-paths-for-the-1606-baseline-media"></a>Ścieżki uaktualniania dla nośnika linii bazowej 1606 w miejscu
Nośnika linii bazowej 1606 służy do uaktualnienia do wersji licencjonowanej programu System Center Configuration Manager następujące:
- System Center 2012 Configuration Manager z dodatkiem Service Pack 2.
- System Center 2012 R2 Configuration Manager z dodatkiem Service Pack 1.

Umożliwia także ten nośnik do uaktualnienia wersji ewaluacyjnej nielicencjonowane bieżącej gałęzi do w pełni licencjonowanej wersji Current Branch.

Ten nośnik nie obsługuje uaktualnienia:
- Inne wersje programu System Center 2012 Configuration Manager.
- Menedżer konfiguracji 2007 lub starszym.
- Release candidate instalację programu System Center Configuration Manager.

## <a name="about-the-cdlatest-folder-and-the-ltsb"></a>O dysku CD. Najnowszy folder i LTSB
Poniżej wymieniono ograniczenia dotyczące używania nośnika, który tworzy programu Configuration Manager na dysku CD. Najnowszy folder na serwerze lokacji. Te limity mają zastosowanie do lokacji z programem LTSB:

Nośnika na dysku CD. Najnowszy folder jest obsługiwana dla:
- Usługa Site recovery.
- Obsługa lokacji.
- Instalowanie dodatkowych podrzędnych lokacji głównych.

Nośnika na dysku CD. Najnowszy folder nie jest obsługiwana dla:  
- Instalowanie centralnej lokacji administracyjnej w ramach scenariusza rozszerzania lokacji.

Aby uzyskać więcej informacji, zobacz [dysku CD. Najnowszy folder](/sccm/core/servers/manage/the-cd.latest-folder).

## <a name="backup-recovery-and-site-maintenance-for-the-ltsb"></a>Kopia zapasowa, odzyskiwania i obsługa lokacji LTSB
Aby utworzyć kopię zapasową, odzyskiwanie lub uruchom konserwacji lokacji w lokacji z uruchomionym programem LTSB, użyj wskazówki i procedury z [kopii zapasowych i odzyskiwania dla programu System Center Configuration Manager](/sccm/protect/understand/backup-and-recovery).  

Użyj Menedżera konfiguracji Instalatora z dysku CD. Folder najnowszej kopii zapasowej lokacji LTSB.
