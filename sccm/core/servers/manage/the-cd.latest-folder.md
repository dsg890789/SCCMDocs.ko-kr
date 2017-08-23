---
title: Dysk CD. Najnowszy folder | Dokumentacja firmy Microsoft
description: "Więcej informacji na temat nowy proces aktualizacji, który dostarcza aktualizacje produktu z poziomu konsoli programu Configuration Manager."
ms.custom: na
ms.date: 05/02/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8db92d67-5d9c-4e9c-80d0-ae6fa0dd4817
caps.latest.revision: "6"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 5c39e09b44500fa2f356f83579bb2fb2c1d0e937
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="the-cdlatest-folder-for-system-center-configuration-manager"></a>Folder CD.Latest programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

System Center Configuration Manager wprowadzono nowy proces aktualizacji, który dostarcza aktualizacje produktu z poziomu konsoli programu Configuration Manager. Do obsługi tej nowej metody aktualizacji programu Configuration Manager, tworzony jest nowy folder o nazwie **dysku CD. Najnowsze** zawierający kopię plików instalacyjnych programu Configuration Manager do zaktualizowanej wersji lokacji.  

Począwszy od aktualizacji 1606, folder CD.Latest zawiera folder o nazwie **Redist** z plikami redystrybucyjnymi umożliwiającymi konfigurowanie plików do pobrania i używania. Te pliki są dopasowane do wersji plików programu Configuration Manager znajdujących się w folderze CD.Latest. Po uruchomieniu Instalatora z folderu CD.Latest musisz użyć plików dopasowanych do wersji Instalatora. W tym celu możesz przekierować Instalatora w celu pobrania nowych i bieżących plików od firmy Microsoft lub użycia plików z folderu Redist znajdującego się w folderze CD.Latest.

Jednak nośnika linii bazowej, takie jak wersji bazowej 1606 wydane w ramach października 2016, nie ma folderu redystrybucyjnego. Nie będzie można utworzyć folderu Redist, aż do zainstalowania aktualizacji w konsoli. W międzyczasie użyj folderu Redist, które zostały użyte podczas instalowania lokacji z nośnika linii bazowej.  

> [!TIP]
> Jeśli nie masz jeszcze zainstalowanej wersji 1606, upewnij się, że używane pliki redist są aktualne. Jeśli pliki redist nie były ostatnio pobierane, zaplanuj ich pobranie od firmy Microsoft przez Instalatora.   

 Następujące scenariusze są związane z tworzeniem lub aktualizowaniem folderu CD.Latest na serwerze centralnej lokacji administracyjnej lub lokacji głównej:  

-   Instalowania aktualizacji lub poprawki z poziomu konsoli programu Configuration Manager: Folder jest tworzony lub aktualizowany w folderze instalacyjnym programu Configuration Manager.  

-   Możesz uruchomić wbudowanego zadania tworzenia kopii zapasowej programu Configuration Manager: Folder jest tworzony lub aktualizowany w lokalizacji wskazanego folderu kopii zapasowej.  

-  Począwszy od wersji 1606, dysku CD. Najnowszy folder jest tworzony podczas instalowania nowej lokacji za pomocą nośnika linii bazowej (np. wersja 1606 lub 1702).

Pliki źródłowe z folderu CD.Latest są obsługiwane w następujących przypadkach:  

1.  **Tworzenie kopii zapasowej i odzyskiwanie:** Aby odzyskać lokację, należy użyć plików źródłowych z dysku CD. Najnowszy folder zgodnej z lokacją. Po uruchomieniu kopii zapasowej lokacji przy użyciu witryny wbudowanego zadania tworzenia kopii zapasowej dysku CD. Najnowszy folder wchodzi w skład kopii zapasowej.

    -   **Podczas ponownego instalowania lokacji w ramach odzyskiwania lokacji** jest ona instalowana z folderu CD.Latest zawartego w kopii zapasowej. To powoduje zainstalowanie lokacji przy użyciu wersji plików zgodnych z kopią zapasową lokacji i bazą danych lokacji.  Jeśli nie masz dostępu poprawny dysk CD. Najnowszą wersję folderu, możesz uzyskać dysku CD. Najnowszy folder o poprawne wersje plików instalacji lokacji w środowisku laboratoryjnym, a następnie zaktualizować zgodna z wersją z tej lokacji, do której chcesz odzyskać.

        > [!IMPORTANT]  
        >  Jeśli nie masz poprawnego folderu CD.Latest z dostępną zawartością, nie możesz odzyskać lokacji, a lokacja wymaga ponownego zainstalowania.  

    -   Jeśli nie masz folderu CD.Latest, ale masz działającą podrzędną lokację główną lub centralną lokację administracyjną, możesz użyć tej lokacji jako lokacji odniesienia w procesie odzyskiwania lokacji.  

2.  **Aby zainstalować podrzędną lokację główną:** Jeśli chcesz zainstalować nową podrzędną lokację główną lokacji administracji centralnej, który ma zainstalowany co najmniej jednej aktualizacji w konsoli, należy użyć Instalatora i plików źródłowych z dysku CD. Najnowszy folder z centralnej lokacji administracyjnej. Gdy Instalator zostaje uruchomiony z kopii folderu CD.Latest z centralnej lokacji administracyjnej, używa plików źródłowych instalacji, które są zgodne z wersją centralnej lokacji administracyjnej. Aby uzyskać więcej informacji, zobacz [Use the Setup Wizard to install sites](../../../core/servers/deploy/install/use-the-setup-wizard-to-install-sites.md) (Instalowanie lokacji za pomocą Kreatora instalacji).  

3.  **Aby rozszerzyć autonomiczną lokację główną:** Jeśli rozszerzasz autonomiczną lokację główną, instalując nową centralną lokację administracyjną, musisz użyć Instalatora i plików źródłowych z dysku CD. Najnowszy folder z lokacji głównej w celu zainstalowania nowej centralnej lokacji administracyjnej. W przypadku uruchomienia z kopii folderu CD.Latest z lokacji głównej zostaną użyte pliki źródłowe instalacji, które są zgodne z wersją lokacji głównej. Aby uzyskać więcej informacji, zobacz sekcję [Expand a stand-alone primary site](../../../core/servers/deploy/install/use-the-setup-wizard-to-install-sites.md#bkmk_expand) (Rozszerzanie autonomicznej lokacji głównej) w temacie [Use the Setup Wizard to install sites](../../../core/servers/deploy/install/use-the-setup-wizard-to-install-sites.md) (Instalowanie lokacji za pomocą Kreatora instalacji)

> [!IMPORTANT]  
>  Zaktualizowane pliki źródłowe folderu CD.Latest nie są obsługiwane w następujących przypadkach:  
>   
>  -   Instalowanie nowej lokacji do nowej hierarchii  
>  -   Uaktualnianie lokacji programu Microsoft System Center 2012 Configuration Manager do programu System Center Configuration Manager
