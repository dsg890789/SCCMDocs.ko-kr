---
title: "Podstawowe informacje na temat zarządzania klienta | Dokumentacja firmy Microsoft"
description: "Więcej informacji na temat zadań uruchamianych w celu zarządzania klientami programu System Center Configuration Manager."
ms.custom: na
ms.date: 12/30/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8d4e5641-354e-4439-8b4f-620a760e233d
caps.latest.revision: "4"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 0fee4f4ba462e59859ac93c4218b67cb26bdd6f6
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="fundamentals-of-client-management-tasks-for-system-center-configuration-manager"></a>Podstawy zadań zarządzania klientami dla programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Po zainstalowaniu klientów programu System Center Configuration Manager, istnieje kilka zadań uruchamianych w celu zarządzania klientami.  Niektóre zadania są uruchamiane z poziomu konsoli programu Configuration Manager. Inne zadania są uruchamiane z poziomu aplikacji klienta programu Configuration Manager. Przy użyciu oprogramowania klienckiego programu Configuration Manager została zainstalowana aplikacja klienta programu Configuration Manager.

## <a name="configuration-manager-console-tasks"></a>Zadania konsoli programu Configuration Manager
 W konsoli programu Configuration Manager można wykonywać różne zadania zarządzania klientami:  

-   Wdrażanie aplikacji, aktualizacji oprogramowania, skryptów konserwacji i systemów operacyjnych. Skonfiguruj instalację na określoną datę i godzinę, udostępnić użytkownikom do instalacji, gdy są żądane oprogramowanie lub skonfigurować aplikacje, które ma zostać odinstalowany.  

-   Poprawa ochrony komputerów przed złośliwym oprogramowaniem i zagrożeniami bezpieczeństwa oraz powiadamianie o wykryciu problemów.  

-   Definiowanie ustawień konfiguracji klienta, które chcesz monitorować i korygować, jeśli są one zgodne.  

-   Zbieranie informacji o spisie sprzętu i oprogramowania, w tym informacji o monitorowaniu i uzgadnianiu licencji firmy Microsoft.  

-   Rozwiązywanie problemów z komputerami przy użyciu zdalnego sterowania.  

-   Implementowanie ustawień zarządzania energią w celu zarządzania i monitorowania zużycia energii przez komputery.  

Konsola programu Configuration Manager monitoruje poprzednich zadań w najbliższym czasie rzeczywistym. Powiadomienia i stan informacje dla każdego zadania są dostępne w konsoli programu Configuration Manager. Do przechwytywania danych i historycznej analizy trendów, Użyj zintegrowanych funkcji raportowania programu SQL Server Reporting Services. Klienci przesyłają dane do lokacji w formie stanu klienta.  Informacje o stanie klienta zawiera dane o kondycji i aktywności klienta i są wyświetlane w konsoli lub za pomocą wbudowanych raportów programu Configuration Manager. Te dane ułatwiają identyfikację komputerów, które nie odpowiadają, a w niektórych przypadkach problemy zostaną rozwiązane automatycznie.  

 Więcej informacji o zadaniach zarządzania dla klientów znajduje się w tematach [Jak zarządzać klientami w programie System Center Configuration Manager](../../core/clients/manage/manage-clients.md) i [Jak zarządzać klientami dla serwerów z systemami Linux i UNIX w programie System Center Configuration Manager](../../core/clients/manage/manage-clients-for-linux-and-unix-servers.md). Aby dowiedzieć się więcej o używaniu raportów, zobacz   
            [Wprowadzenie do raportowania w programie System Center Configuration Manager](../../core/servers/manage/introduction-to-reporting.md).  

## <a name="configuration-manager-client-application"></a>Aplikacja klienta programu Configuration Manager  
 Po zainstalowaniu oprogramowania klienckiego programu Configuration Manager zainstalowano zbyt aplikacji klienta programu Configuration Manager. W przeciwieństwie do programu Software Center aplikacji klienta programu Configuration Manager jest przeznaczony dla działu pomocy technicznej, a nie dla użytkownika końcowego. Niektóre opcje konfiguracji wymagają posiadania lokalnych uprawnień administracyjnych, a inne wymagają technicznej wiedzy na temat działania aplikacji klienta programu Configuration Manager. Za pomocą tej aplikacji można wykonywać na kliencie następujące zadania:  

-   Wyświetlanie właściwości klienta, takich jak numer kompilacji, przypisana lokacja, zarządzanie wskaż na nim komunikuje się z i określa, czy klient używa certyfikatów infrastruktury kluczy publicznych (PKI) lub certyfikatu z podpisem własnym.  

-   Upewnij się, czy klient pomyślnie pobrał zasadę klienta po zainstalowaniu klienta programu po raz pierwszy. Upewnij się również, że ustawienia klienta są włączone lub wyłączone zgodnie z oczekiwaniami, zgodnie z ustawieniami klienta, które są konfigurowane w konsoli programu Configuration Manager.  

-   Uruchamianie akcji klienta. Na przykład pobierania zasad klienta, gdy było ostatnich zmian konfiguracji w konsoli programu Configuration Manager i nie chcesz czekać na następną zaplanowaną czasu.  

-   Ręcznie przypisać klienta do lokacji programu Configuration Manager lub przy próbie znalezienia lokacji. Następnie określenie sufiksu systemu nazw domen (DNS, Domain Name System) dla punktów zarządzania, które publikują w systemie DNS.  

-   Konfigurowanie pamięci podręcznej klienta, który przechowuje tymczasowo pliki. Usuń pliki w pamięci podręcznej, jeśli potrzebujesz więcej miejsca na dysku do zainstalowania oprogramowania.  

-   Konfigurowanie ustawień dla internetowego zarządzania klientami  

-   Wyświetlanie linii bazowych konfiguracji, które zostały wdrożone na klientach, inicjowanie oceny zgodności i wyświetlanie raportów zgodności  
