---
title: "Podstawy zarządzania urządzeniami | Dokumentacja firmy Microsoft"
description: "Dowiedz się, jak używać programu System Center Configuration Manager do zarządzania urządzeniami."
ms.custom: na
ms.date: 12/04/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2bca3db9-115a-451d-8c93-f073ceefe0c7
caps.latest.revision: "6"
author: arob98
ms.author: angrobe
manager: angrobe
ms.openlocfilehash: 45d84122a86da880268c93ecd994250df6b76c8a
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="fundamentals-of-managing-devices-with-system-center-configuration-manager"></a>Podstawy zarządzania urządzeniami w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

System Center Configuration Manager można zarządzać dwie szerokie kategorie urządzeń:

-   *Klienci* są urządzeniami, takimi jak stacje robocze, laptopy, serwerów i urządzeń przenośnych, w którym instalować oprogramowanie klienta programu Configuration Manager. Niektóre funkcje zarządzania, takie jak spis sprzętu, wymagają tego oprogramowania klienta.  

-   *Zarządzane urządzenia* mogą obejmować *klientów*, ale zazwyczaj to urządzenie przenośne, których nie zainstalowano oprogramowania klienckiego programu Configuration Manager. Tego rodzaju urządzenia można zarządzać za pomocą usługi Intune lub wbudowanego na lokalnego zarządzania urządzeniami przenośnymi w programie Configuration Manager.

Można również grupować i zidentyfikować urządzenia, na podstawie użytkownika, a nie tylko od typu klienta.

## <a name="managing-devices-with-the-configuration-manager-client"></a>Zarządzanie urządzeniami z klientem programu Configuration Manager

Istnieją dwa sposoby zarządzać urządzeniem za pomocą oprogramowania klienckiego programu Configuration Manager. Pierwszym sposobem jest wykrywanie urządzenia w sieci, a następnie wdrożyć oprogramowanie klienckie na tym urządzeniu. Innym sposobem jest ręcznie zainstaluj oprogramowanie klienckie na nowym komputerze, a następnie dołącz lokacji po dołączeniu go do sieci komputera. W celu odnalezienia urządzeń, których nie zainstalowano oprogramowania klienckiego, uruchom co najmniej jednego z wbudowanych metod odnajdywania. Po odnalezieniu urządzenia użyj jednej z kilku metod instalowania oprogramowania klienckiego. Aby uzyskać informacje na temat korzystania z funkcji odnajdywania, zobacz [Uruchamianie odnajdywania dla programu System Center Configuration Manager](../../core/servers/deploy/configure/run-discovery.md).  

 Po odnajdywania urządzeń, które można uruchomić oprogramowanie klienta programu Configuration Manager, można użyć jednej z kilku metod instalowania oprogramowania. Gdy oprogramowanie zostanie zainstalowane, a klient przypisany do lokacji głównej, możesz rozpocząć zarządzanie urządzeniem.  Typowe metody instalacji to:

 - Wypychana instalacja klienta.

 - Instalacja oparta na aktualizacji oprogramowania.

 - Zasady grupy.

 - Instalacja ręczna na komputerze.
 - W tym klienta jako części wdrażanego obrazu systemu operacyjnego.  


 Po zainstalowaniu klienta możesz uprościć zadania związane z zarządzaniem urządzeniami, używając kolekcji. Kolekcje są grupami urządzeń lub użytkowników, którzy tworzenia, aby zarządzać nimi grupowo. Na przykład możesz zainstalować aplikację dla urządzeń przenośnych na wszystkich urządzeniach przenośnych, które rejestruje programu Configuration Manager. Jeśli jest to możliwe, należy użyć kolekcji wszystkie urządzenia przenośne.  

 Aby uzyskać więcej informacji zobacz następujące tematy:  

-   [Wybieranie rozwiązania do zarządzania urządzeniami programu System Center Configuration Manager](../../core/plan-design/choose-a-device-management-solution.md)  

-   [Metody instalacji klientów w programie System Center Configuration Manager](../../core/clients/deploy/plan/client-installation-methods.md)  

-   [Wprowadzenie do kolekcji w programie System Center Configuration Manager](../../core/clients/manage/collections/introduction-to-collections.md)  

### <a name="client-settings"></a>Ustawienia klienta  
 Podczas pierwszej instalacji programu Configuration Manager, wszyscy klienci w hierarchii są skonfigurowane przy użyciu domyślnych ustawień klienta, które można zmienić. Ustawienia klienta obejmują następujące opcje konfiguracji:

 -  Jak często urządzenia komunikują się z lokacją.

 -  Czy klient jest skonfigurowana dla aktualizacji oprogramowania i innych operacji zarządzania.

 -  Czy użytkownicy mogą rejestrować swoje urządzenia przenośne tak, że są one zarządzane przez program Configuration Manager.  

Można tworzyć niestandardowe ustawienia klienta i przypisać je do kolekcji.  Członkowie kolekcji są konfigurowane z niestandardowymi ustawieniami, a następnie można utworzyć wielu klientów niestandardowych ustawień, które są stosowane w określonej kolejności (w kolejności liczbowej).  Jeśli występują konflikty ustawień, ustawienie o najniższej liczbie porządkowej zastępuje pozostałe ustawienia.  

Na poniższym diagramie przedstawiono przykład sposobu tworzenia i stosowania niestandardowych ustawień klienta.  

 ![Ustawienia klienta](media/ClientSettings.gif)  

 Aby dowiedzieć się więcej na temat ustawień klientów, zobacz  
                [Jak skonfigurować ustawienia klienta w programie System Center Configuration Manager](../../core/clients/deploy/configure-client-settings.md) i [Informacje o ustawieniach klienta w programie System Center Configuration Manager](../../core/clients/deploy/about-client-settings.md).

## <a name="managing-devices-without-the-configuration-manager-client"></a>Zarządzanie urządzeniami bez klienta programu Configuration Manager  
 Program Configuration Manager obsługuje zarządzanie niektórych urządzeń, których nie zainstalowano oprogramowania klienckiego, a nie są zarządzane przez usługę Intune. Aby uzyskać więcej informacji, zobacz [zarządzanie urządzeniami przenośnymi za pomocą infrastruktury lokalnej w programie System Center Configuration Manager](../../mdm/understand/manage-mobile-devices-with-on-premises-infrastructure.md) i [zarządzanie urządzeniami przenośnymi za pomocą programu System Center Configuration Manager i Exchange](../../mdm/deploy-use/manage-mobile-devices-with-exchange-activesync.md).  

## <a name="user-based-management"></a>Zarządzanie oparte na użytkownika  
 Program Configuration Manager obsługuje kolekcji użytkowników usług domenowych w usłudze Active Directory. Gdy używasz kolekcji użytkowników, można zainstalować oprogramowania na wszystkich komputerach, że członkowie użycia kolekcji. Aby upewnić się, że wdrażanego oprogramowania instalowany tylko na urządzeniach, które są określone jako główne urządzenie użytkownika, należy skonfigurować koligację urządzenia użytkownika. Każdy użytkownik może mieć przynajmniej jedno urządzenie podstawowe.  

 Jednym ze sposobów, że użytkownicy mogą zarządzać wdrażaniem oprogramowania jest użycie **Centrum oprogramowania** interfejsu klienta. **Centrum oprogramowania** jest automatycznie instalowany na komputerach klienckich i jest uruchamiany z **Start** menu. **Centrum oprogramowania** pozwala użytkownikom na zarządzanie oprogramowaniem i wykonaj następujące czynności:  

-   Zainstaluj oprogramowanie.  

-   Zaplanowanie automatycznej instalacji poza godzinami pracy oprogramowania.  

-   Skonfiguruj kiedy podczas programu Configuration Manager może instalować oprogramowanie na urządzeniu.  

-   Konfigurowanie ustawień dostępu do zdalnego sterowania, jeśli zdalne sterowanie jest skonfigurowana w programie Configuration Manager.  

-   Skonfiguruj opcje zarządzania energią, jeśli administrator konfiguruje tę opcję.  


 Łącza w **Centrum oprogramowania** umożliwia użytkownikom łączenie się **katalogu aplikacji**, gdzie mogą Przeglądaj w poszukiwaniu, zainstaluj oraz żądań oprogramowania. **Katalogu aplikacji** służy również do konfigurowania ustawień preferencji, czyszczenie urządzeń przenośnych, a jeśli je skonfigurowano, podaj urządzeniem podstawowym koligacji urządzeń użytkownika.   

 Użytkownicy mogą również uzyskać dostęp **katalogu aplikacji** za pośrednictwem przeglądarki, intranetu lub Internetu sesji.  
