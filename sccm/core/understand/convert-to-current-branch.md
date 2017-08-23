---
title: "Uaktualnij długoterminowej obsługi gałęzi do bieżącej gałęzi | Dokumentacja firmy Microsoft"
description: "Dowiedz się, jak przekonwertować oddziale długoterminowe obsługi lokacji bieżącej gałęzi."
ms.custom: na
ms.date: 2/8/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ec5b54cf-62b7-4ed1-9bb3-e8c63b9641c8
caps.latest.revision: "0"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 6e7edc85630d22c5bbba1ff66bd1199903db76db
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="upgrade-the-long-term-servicing-branch-to-the-current-branch"></a>Uaktualnij długoterminowej obsługi gałęzi do bieżącej gałęzi

*Dotyczy: System Center Configuration Manager (długoterminowej obsługi oddziału)*

Użyj w tym temacie informacje na temat uaktualniania (Konwertuj) lokacji i hierarchii, która używa długoterminowe Servicing Branch (LTSB) programu Configuration Manager do bieżącej gałęzi.

Jeśli masz bieżącej umowy Software Assurance (lub podobny licencja), które udziela praw do korzystania z bieżącej gałęzi, możesz przekonwertować LTSB instalacji bieżącej gałęzi.  Jest to jednokierunkowe konwersji, ponieważ nie jest obsługiwane do konwertowania LTSB lokacji bieżącej gałęzi.

Jeśli masz wiele lokacji, wystarczy przekonwertować lokacji najwyższej warstwy w hierarchii. Po przekonwertowaniu lokacji najwyższego poziomu:
- Podrzędne Lokacje główne automatycznie przekonwertować.
-   Należy ręcznie zaktualizować Lokacje dodatkowe przy użyciu konsoli programu Configuration Manager.

## <a name="run-setup-to-convert-the-long-term-servicing-branch"></a>Uruchom Instalatora, aby przekonwertować gałąź obsługi długoterminowe
W lokacji najwyższego poziomu w hierarchii, należy uruchomić Instalatora programu Configuration Manager z kwalifikujących się nośnika linii bazowej i wybrać **lokacji obsługi**.  Następnie gdy wyświetlana strona licencjonowania, wybierz opcję dla bieżącej gałęzi i Zakończ pracę kreatora.

Jeśli witryny został przekonwertowany na bieżącej gałęzi, wcześniej niedostępne funkcje i możliwości są dostępne do użycia.

> [!NOTE]  
> Kwalifikowanie nośnika linii bazowej jest nośnika, który ma wersję, która będzie równa lub późniejsza niż LTSB instalacji.

Na przykład ponieważ LTSB jest oparty na wersji 1606, nie możesz użyć nośnika linii bazowej 1511 do przekonwertowania na bieżącej gałęzi. Zamiast tego należy uruchomić Instalatora z tej samej wersji 1606 nośnika linii bazowej użytym do zainstalowania lokacji LTSB i wybierz opcję licencjonowania dla bieżącej gałęzi.  Alternatywnie nowsze linii bazowej bieżącej gałęzi zostało zwolnione, można uruchomić Instalatora z tego nośnika linii bazowej.

Aby uzyskać listę wersji linii bazowej, zobacz **wersje linii bazowej i aktualizacji** w [aktualizacji programu Configuration Manager](/sccm/core/servers/manage/updates).

## <a name="use-the-configuration-manager-console-to-convert-the-long-term-servicing-branch"></a>Konwertuj długoterminowej gałąź obsługi za pomocą konsoli programu Configuration Manager
Jeśli witryna jest uruchamiana LTSB, służy Poniższa opcja w konsoli programu Configuration Manager do przekonwertowania na bieżącej gałęzi:

 1. W konsoli przejdź do **administracji** > **konfiguracja lokacji** > **witryny**, a następnie otwórz **ustawienia hierarchii**.  

 2. Wybierz opcję, aby przekonwertować bieżącej gałęzi, a następnie wybierz pozycję **Zastosuj**.  

Jeśli witryny został przekonwertowany na bieżącej gałęzi, wcześniej niedostępne funkcje i możliwości są dostępne do użycia.
