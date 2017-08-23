---
title: "Podstawowe informacje na temat zabezpieczeń | Dokumentacja firmy Microsoft"
description: "Więcej informacji na temat warstw zabezpieczeń dla programu System Center Configuration Manager."
ms.custom: na
ms.date: 12/30/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 035b7f73-8b78-4ed1-835e-a31f9a5c4a02
caps.latest.revision: "5"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: df3198885259b1db4a1aadee0db6512a1a2d4911
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="fundamentals-of-security-for-system-center-configuration-manager"></a>Podstawowe informacje na temat zabezpieczeń programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Zabezpieczenia programu System Center Configuration Manager składa się z kilku warstw. Pierwsza warstwa podano funkcje zabezpieczeń systemu Windows dla systemu operacyjnego i sieci i obejmuje:  

-   Udostępnianie plików do transferu plików między składnikami programu Configuration Manager.  

-   Listy kontroli dostępu (ACL) ułatwiające zabezpieczanie plików i kluczy rejestru.  

-   Zabezpieczeń protokołu internetowego (IPsec), aby ułatwić bezpieczną komunikację.  

-   Zasady grupy, aby ustawić zasady zabezpieczeń.  

-   Rozproszone uprawnienia Component Object Model (DCOM) dla aplikacji rozproszonych, takich jak konsoli programu Configuration Manager.  

-   Usługi domenowe Active Directory do przechowywania podmiotów zabezpieczeń.  

-   Zabezpieczenia konta Windows, w tym niektórych grup utworzonych podczas instalacji programu Configuration Manager.  

Następnie dodatkowe składniki zabezpieczeń, takie jak zapory i wykrywania nieautoryzowanego dostępu, zapewniają bardziej szczegółową ochronę całego środowiska. Certyfikaty wystawione przez branży ułatwić implementacje standardowe infrastruktury kluczy publicznych (PKI) zapewniają uwierzytelniania, podpisywania ani szyfrowania.  

Oprócz zabezpieczeń zapewnianych przez infrastrukturę serwera i sieci systemu Windows programu Configuration Manager służy do sterowania dostępem do konsoli programu Configuration Manager i jej zasobów na kilka sposobów. Domyślnie tylko lokalni administratorzy mają dostęp do plików i kluczy rejestru, które są wymagane do uruchamiania konsoli programu Configuration Manager na komputerach, w którym jest zainstalowany.  

Kolejna warstwa zabezpieczeń bazuje na dostępie przy użyciu Instrumentacji zarządzania Windows (WMI), konkretnie na dostawcy programu SMS. Dostawca programu SMS jest składnikiem programu Configuration Manager, który udziela użytkownikowi dostępu do informacji w bazie danych lokacji. Domyślnie dostęp do dostawcy jest ograniczony do członków lokalnej grupy administratorów programu SMS. Ta grupa w najpierw zawiera tylko użytkownika, który instalacji programu Configuration Manager. Aby przydzielić innym kontom uprawnienie do repozytorium modelu wspólnych informacji (CIM) i dostawcy programu SMS, należy dodać te konta do grupy administratorów programu SMS.  

Ostatnia warstwa zabezpieczeń bazuje na uprawnieniach do obiektów w bazie danych lokacji. Domyślnie lokalne konto systemowe i konto użytkownika, który został użyty do zainstalowania programu Configuration Manager umożliwia administrowanie wszystkimi obiektami w bazie danych lokacji. Można przydzielić lub odebrać uprawnienia dodatkowym użytkownikom administracyjnym w konsoli programu Configuration Manager za pomocą administracji opartej na rolach.  



## <a name="role-based-administration"></a>Administracja oparta na rolach  
 Configuration Manager korzysta z administracji opartej na rolach, aby zabezpieczać takie obiekty jak kolekcje, wdrożenia i lokacje. Ten model administrowania definiuje w sposób centralny ustawienia bezpiecznego dostępu w całej hierarchii do wszystkich witryn i ustawień lokacji oraz pozwala nimi zarządzać. Role zabezpieczeń są przypisane do użytkowników administracyjnych, a uprawnienia grupy. Uprawnienia są podłączone do różnych typów obiektów programu Configuration Manager, takich jak uprawnienia, które są używane do tworzenia lub zmiany ustawień klienta. Grupować konkretne wystąpienia obiektów, którymi zarządza, takie jak aplikacja instalująca program Microsoft Office użytkownik administracyjny zakresów zabezpieczeń. Kombinacja ról zabezpieczeń, zakresów zabezpieczeń i kolekcji określeniu obiektów, które użytkownik administracyjny można wyświetlać i zarządzać nimi. Program Configuration Manager instaluje niektóre domyślne role zabezpieczeń dla typowych zadań zarządzania. Jednak można tworzyć własne role zabezpieczeń stosownie do konkretnych potrzeb biznesowych.  

 Aby uzyskać więcej informacji, zobacz [Konfigurowanie administracji opartej na rolach dla programu System Center Configuration Manager](../../core/servers/deploy/configure/configure-role-based-administration.md).  

## <a name="securing-client-endpoints"></a>Zabezpieczanie punktów końcowych klienta  
 Komunikacja klienta z rolami systemu lokacji jest zabezpieczony za pomocą certyfikatów z podpisem własnym lub za pomocą certyfikatów PKI. Należy używać certyfikatu PKI dla komputerów klienckich, które program Configuration Manager wykryje się w Internecie, a dla klientów urządzeń przenośnych. Za pomocą protokołu HTTPS certyfikat PKI zabezpieczanie punktów końcowych klienta. Role systemu lokacji, z którymi łączą się klienci, można skonfigurować do komunikacji HTTPS lub HTTP. Komputery klienckie zawsze komunikują się przy użyciu najbardziej bezpiecznej metody, która jest dostępna. Komputery klienckie tylko wrócić do przy użyciu mniej bezpieczną metodę komunikacji HTTP w intranecie, jeśli role systemu lokacji, które umożliwiają komunikację HTTP.  

 Aby uzyskać więcej informacji, zobacz [szyfrowania określa informacje techniczne dotyczące programu System Center Configuration Manager](../../protect/deploy-use/cryptographic-controls-technical-reference.md).  

## <a name="configuration-manager-accounts-and-groups"></a>Konta i grupy programu Configuration Manager  
 Dla większości operacji lokacji programu Configuration Manager przy użyciu konta systemu lokalnego. Niektóre zadania zarządzania może być konieczne do tworzenia i obsługi dodatkowych kont. Podczas instalacji są tworzone różne domyślne grupy i role serwera SQL. Trzeba będzie ręcznie dodawać konta użytkownika lub komputera do domyślnych grup i ról serwera SQL.  

 Aby uzyskać więcej informacji, zobacz [Konta używane w programie System Center Configuration Manager](../../core/plan-design/hierarchy/accounts.md).  

## <a name="privacy"></a>Ochrona prywatności  
 Mimo że produkty przeznaczone do zarządzania przedsiębiorstwem oferują wiele zalet, ponieważ umożliwiają wydajne zarządzanie wieloma klientami, należy wziąć pod uwagę ich wpływ na prywatność użytkowników w organizacji. System Center Configuration Manager udostępnia wiele narzędzi do zbierania danych i monitorowania urządzeń. Niektóre narzędzia mogą budzić zastrzeżenia co do zachowania poufności.  

 Na przykład po zainstalowaniu klienta programu Configuration Manager wiele ustawień zarządzania są domyślnie włączone. Powoduje to, że oprogramowanie klienta do wysyłania informacji do lokacji programu Configuration Manager. Informacje o kliencie są przechowywane w bazie danych programu Configuration Manager, a informacje nie są wysyłane do firmy Microsoft. Przed zaimplementowaniem programu System Center Configuration Manager, należy wziąć pod uwagę wymagania dotyczące ochrony prywatności.  
