---
title: "유니코드 및 ASCII 지원 | Microsoft 문서"
description: "System Center Configuration Manager 개체의 유니코드 및 ASCII 문자 지원에 대해 알아봅니다."
ms.custom: na
ms.date: 3/1/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2bdec799-905f-48bc-aed5-2d92134739e8
caps.latest.revision: 6
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Human Translation
ms.sourcegitcommit: b35e747c8c297d61bb549b9767c4318f51e5fdb4
ms.openlocfilehash: 18f1c64c1f27001a0fdfbab4236d09a5bc279272
ms.contentlocale: ko-kr
ms.lasthandoff: 05/17/2017


---
# <a name="unicode-and-ascii-support-in-system-center-configuration-manager"></a>System Center Configuration Manager의 유니코드 및 ASCII 지원

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager에서는 유니코드 문자를 사용하여 대부분의 개체를 만듭니다. 그러나 여러 개체는 ASCII 문자만 지원하거나 다른 제한이 있습니다.  

 다음 섹션에는 ASCII 문자 집합의 문자만 사용하거나 추가 제한 사항이 있는 개체가 나와 있습니다.  

-   [ASCII 문자를 사용하는 개체](#BKMK_ASCIIchar)  

-   [추가 제한 사항](#BKMK_OtherCharLimitations)  

-   [지역화되지 않은 Configuration Manager 개체](#BKMK_LangNonLocalize)  

##  <a name="BKMK_ASCIIchar"></a> ASCII 문자를 사용하는 개체  
 Configuration Manager에서는 다음 개체를 만들 때 ASCII 문자 집합만 지원합니다.  

-   사이트 코드  

-   모든 사이트 시스템 서버의 컴퓨터 이름  

-   다음 Configuration Manager 계정:  

    > [!NOTE]  
    >  이러한 계정은 러시아어로 실행되는 사이트에서 ASCII 문자와 RUS 문자를 지원합니다.  

    -   클라이언트 강제 설치 계정  

    -   성능 상태 참조 게시 계정  

    -   성능 상태 참조 쿼리 계정  

    -   관리 지점 데이터베이스 연결 계정  

    -   네트워크 액세스 계정  

    -   패키지 액세스 계정  

    -   표준 보낸 사람 계정  

    -   사이트 시스템 설치 계정  

    -   소프트웨어 업데이트 지점 연결 계정  

    -   소프트웨어 업데이트 지점 프록시 서버 계정  

    > [!NOTE]  
    >  역할 기반 관리를 위해 지정하는 계정은 유니코드를 지원합니다.  
    >   
    >  보고 서비스 지점 계정은 RUS 문자를 제외하고 유니코드를 지원합니다.  

-   사이트 서버 및 사이트 시스템에 대한 FQDN(정규화된 도메인 이름)  

-   Configuration Manager의 설치 경로  

-   SQL Server 인스턴스 이름  

-   다음 사이트 시스템 역할의 경로:  

    -   응용 프로그램 카탈로그 웹 서비스 지점  

    -   응용 프로그램 카탈로그 웹 사이트 지점  

    -   등록 지점  

    -   등록 프록시 지점  

    -   보고 서비스 지점  

    -   상태 마이그레이션 지점  

-   다음 폴더의 경로:  

    -   클라이언트 상태 마이그레이션 데이터가 저장되는 폴더  

    -   Configuration Manager 보고서가 포함되는 폴더  

    -   Configuration Manager 백업이 저장되는 폴더  

    -   사이트 설치의 설치 원본 파일이 저장되는 폴더  

    -   설치에 사용되는 필수 조건 다운로드가 저장되는 폴더  

-   다음 개체의 경로:  

    -   IIS 웹 사이트  

    -   가상 응용 프로그램 설치 경로  

    -   가상 응용 프로그램 이름  

-   AMT 및 대역 외 관리를 위한 다음 개체:  

    -   AMT 기반 컴퓨터의 FQDN  

    -   AMT 기반 컴퓨터의 컴퓨터 이름  

    -   도메인 NetBIOS 이름  

    -   무선 프로필 이름과 SSID  

    -   신뢰할 수 있는 루트 인증 기관 이름  

    -   CA(인증 기관) 이름 및 템플릿 이름  

    -   IDE 리디렉션 이미지 파일의 파일 이름 및 경로  

    -   AMT 데이터 저장소의 콘텐츠  

-   부팅 미디어 .ISO 파일 이름  

##  <a name="BKMK_OtherCharLimitations"></a> 추가 제한 사항  
 다음은 지원되는 문자 집합과 언어 버전에 대한 추가 제한 사항입니다.  

-   Configuration Manager에서는 사이트 서버 컴퓨터의 로캘 변경을 지원하지 않습니다.  

-   엔터프라이즈 CA(인증 기관)는 DBCS(더블바이트 문자 집합)를 사용하는 클라이언트 컴퓨터 이름을 지원하지 않습니다. 사용할 수 있는 클라이언트 컴퓨터 이름은 IA5 문자 집합의 PKI 제한으로 제한됩니다. 또한 Configuration Manager에서는 DBCS를 사용하는 CA 이름이나 주체 이름 값을 지원하지 않습니다.  

##  <a name="BKMK_LangNonLocalize"></a> 지역화되지 않은 Configuration Manager 개체  
 Configuration Manager 데이터베이스는 저장하는 대부분의 개체에 유니코드를 지원하며, 가능한 경우 컴퓨터의 로캘과 일치하는 운영 체제 언어로 이 정보를 표시합니다. 클라이언트 인터페이스 또는 Configuration Manager 콘솔에서 컴퓨터의 운영 체제 언어로 정보를 표시하려면 컴퓨터의 로캘이 사이트에 설치하는 클라이언트 또는 서버 언어와 일치해야 합니다.  

 그러나 여러 Configuration Manager 개체는 유니코드를 지원하지 않으며 ASCII를 사용하여 데이터베이스에 저장되거나 추가적인 언어 제한 사항을 갖습니다. 이 정보는 항상 ASCII 문자를 사용하여 표시되거나 개체를 만들 때 사용한 언어로 표시됩니다.  

