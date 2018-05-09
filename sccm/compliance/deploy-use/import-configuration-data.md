---
title: 구성 데이터 가져오기
titleSuffix: Configuration Manager
description: 캐비닛 파일 형식에 포함되어 있고 지원되는 서비스 모델링 언어 스키마를 준수하는 경우 구성 데이터를 가져옵니다.
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.technology: configmgr-compliance
ms.topic: conceptual
ms.assetid: 309b9a09-a611-4ba2-90ab-dde51582cf87
author: aczechowski
manager: dougeby
ms.author: aaroncz
ms.openlocfilehash: 2a779f80f42439fe6526c05d7027c22fb191e41e
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="import-configuration-data-with-system-center-configuration-manager"></a>System Center Configuration Manager를 사용하여 구성 데이터 가져오기

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager 콘솔에서 구성 기준 및 구성 항목을 만들 수 있을 뿐만 아니라 캐비닛(.cab) 파일 형식에 포함되어 있고 지원되는 SML(서비스 모델링 언어) 스키마를 준수하는 경우 구성 데이터를 가져올 수 있습니다. 다음과 같은 구성 데이터를 가져올 수 있습니다.  

-   Microsoft 또는 다른 소프트웨어 공급업체 사이트에서 다운로드한 모범 사례 구성 데이터(구성 팩)  

-   System Center 2012 Configuration Manager 이상에서 내보낸 구성 데이터  

-   외부에서 작성되고 SML 스키마를 준수하는 구성 데이터  

 System Center 2012 Configuration Manager 사이트 서버 역할을 준수할 수 있도록 관리하는 데 도움이 되는 구성 팩에 대한 예제를 보려면 [System Center 2012 Configuration Manager 구성 팩](http://www.microsoft.com/en-us/download/details.aspx?id=30710&WT.mc_id=rss_alldownloads_all)을 참조하세요.  

구성 기준을 가져오는 경우 구성 기준에서 참조되는 일부 또는 모든 구성 항목이 캐비닛 파일에 포함될 수도 있습니다. 가져오기 프로세스 중 Configuration Manager가 구성 기준에서 참조되는 모든 구성 항목이 캐비닛 파일에 포함되어 있는지 또는 이미 Configuration Manager 사이트에 존재하는지 확인합니다. Configuration Manager가 찾을 수 없는 구성 데이터를 참조하는 구성 기준을 가져오려고 하는 경우 가져오기 프로세스가 실패합니다.  

가져오기 프로세스가 실패할 수 있는 다른 시나리오는 다음과 같습니다.  

-   구성 데이터가 Configuration Manager가 데이터베이스 또는 캐비닛 파일 자체에서 찾을 수 없는 구성 데이터를 참조합니다.  

-   구성 데이터가 이름 및 구성 데이터 버전이 같고 콘텐츠 버전은 다른 Configuration Manager 데이터베이스에 이미 존재합니다.  

-   구성 데이터가 콘텐츠 버전이 같은 Configuration Manager 데이터베이스에 이미 존재하고 있으나 해시 계산에서 해당 구성 데이터를 다른 것으로 식별합니다.  

-   이름이 같은 새 버전의 구성 데이터가 Configuration Manager 데이터베이스에 이미 존재하거나 최근에 삭제되었습니다.  

-   다중 사이트 Configuration Manager 계층 구조의 상위 사이트에서 처음 구성 데이터를 가져왔습니다. 구성 데이터는 하위 사이트가 아닌 동일한 사이트에서 업데이트해야 합니다.  

### <a name="import-configuration-data"></a>구성 데이터 가져오기  

1.  Configuration Manager 콘솔에서 **자산 및 준수** > **구성 항목** 또는 **구성 기준**을 클릭합니다.
2.  **홈** 탭의 **만들기** 그룹에서 **구성 데이터 가져오기**를 클릭합니다.  
3.  **구성 데이터 가져오기 마법사** 의 **파일 선택**페이지에서 **추가**를 누른 다음 **열기** 대화 상자에서 가져올 .cab 파일을 선택합니다.  
4.  가져온 구성 데이터를 Configuration Manager 콘솔에서 편집할 수 있게 하려면 **가져온 구성 기준 및 구성 항목의 새 복사본 만들기** 확인란을 선택합니다.  
5.  **요약** 페이지에서 수행될 작업을 검토한 다음 마법사를 완료합니다.  

가져온 구성 데이터가 **자산 및 준수** 작업 영역의 **준수 설정** 노드에 표시됩니다.  
