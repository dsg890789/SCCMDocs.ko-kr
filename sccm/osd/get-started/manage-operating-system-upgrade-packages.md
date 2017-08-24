---
title: "운영 체제 업그레이드 패키지 관리 | Microsoft 문서"
description: "System Center Configuration Manager에서 운영 체제 업그레이드 패키지를 관리하는 방법을 알아봅니다."
ms.custom: na
ms.date: 12/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b9b22655-b8c1-461f-8047-3a7e906f647a
caps.latest.revision: "12"
caps.handback.revision: "0"
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.openlocfilehash: 5fef04f26b12bced073332fd1f7b4e7c7bd7d398
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/07/2017
---
# <a name="manage-operating-system-upgrade-packages-with-system-center-configuration-manager"></a>System Center Configuration Manager를 사용하여 운영 체제 업그레이드 패키지 관리

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager의 업그레이드 패키지에는 컴퓨터의 기존 운영 체제를 업그레이드하는 데 사용되는 Windows 설치 원본 파일이 포함되어 있습니다. Configuration Manager에서 운영 체제 업그레이드 패키지를 관리하려면 다음 섹션을 참조하세요.

##  <a name="BKMK_AddOSUpgradePkgs"></a> Configuration Manager에 운영 체제 업그레이드 패키지 추가  
 운영 체제 업그레이드 패키지를 사용하려면 먼저 Configuration Manager 사이트에 패키지를 추가해야 합니다. 사이트에 운영 체제 업그레이드 패키지를 추가하려면 다음 절차를 참조하세요.  

#### <a name="to-add-an-operating-system-upgrade-package"></a>운영 체제 업그레이드 패키지를 추가하려면  

1.  Configuration Manager 콘솔에서 **소프트웨어 라이브러리**를 클릭합니다.  

2.  **소프트웨어 라이브러리** 작업 영역에서 **운영 체제**를 확장하고 **운영 체제 업그레이드 패키지**를 클릭합니다.  

3.  **홈** 탭의 **만들기** 그룹에서 **운영 체제 업그레이드 패키지 추가** 를 클릭하여 운영 체제 업그레이드 패키지 추가 마법사를 시작합니다.  

4.  **데이터 원본** 페이지에서 운영 체제 업그레이드 패키지의 설치 원본 파일에 대한 네트워크 경로를 지정합니다. 예를 들어 UNC **\\\서버\경로** 를 설치 원본 파일이 있는 위치로 지정합니다.  

    > [!NOTE]  
    >  설치 원본 파일에는 운영 체제를 설치하기 위한 Setup.exe 및 기타 파일과 폴더가 포함되어 있습니다.  

    > [!IMPORTANT]  
    >  사용자 동의 없이 변조되지 않도록 설치 소스 파일에 대한 액세스를 제한합니다.  

5.  **일반** 페이지에서 다음 정보를 지정한 후에 **다음**을 클릭합니다. 이 정보는 여러 운영 체제 설치 관리자가 있을 때 식별하는 데 유용합니다.  

    -   **이름**: 운영 체제 설치 관리자의 이름을 지정합니다.  

    -   **버전**: 운영 체제 설치 관리자의 버전을 지정합니다.  

    -   **설명**: 운영 체제 설치 관리자에 대한 간단한 설명을 지정합니다.  

6.  마법사를 완료합니다.  

 이제 배포 작업 순서에서 액세스할 수 있는 배포 지점에 운영 체제 설치 관리자를 배포할 수 있습니다.  

##  <a name="BKMK_DistributeBootImages"></a> 배포 지점에 운영 체제 이미지 배포  
 운영 체제 이미지는 다른 콘텐츠를 배포하는 것과 동일한 방식으로 배포 지점에 배포할 수 있습니다. 대부분의 경우 운영 체제를 배포하기 전에 하나 이상의 배포 지점에 운영 체제 이미지를 배포해야 합니다. 운영 체제 이미지를 배포하는 단계는 [Distribute content](../../core/servers/deploy/configure/deploy-and-manage-content.md#a-namebkmkdistributea-distribute-content)항목을 참조하세요.  

##  <a name="BKMK_OSUpgradePkgApplyUpdates"></a> 운영 체제 업그레이드 패키지에 소프트웨어 업데이트 적용  
 Configuration Manager 버전 1602부터 운영 체제 업그레이드 패키지에서 운영 체제 이미지에 새 소프트웨어 업데이트를 적용할 수 있습니다. 업그레이드 패키지에 소프트웨어 업데이트를 적용하려면 먼저 소프트웨어 업데이트 인프라를 구축하고 소프트웨어 업데이트를 동기화한 다음 사이트 서버의 콘텐츠 라이브러리에 소프트웨어 업데이트를 다운로드해야 합니다. 자세한 내용은 [소프트웨어 업데이트 배포](../../sum/deploy-use/deploy-software-updates.md)를 참조하세요.  

 지정된 일정에 적용 가능한 소프트웨어 업데이트를 업그레이드 패키지에 적용할 수 있습니다. Configuration Manager는 지정된 일정에 따라 선택된 소프트웨어 업데이트를 운영 체제 업그레이드 패키지에 적용하고 선택적으로 업데이트된 업그레이드 패키지를 배포 지점에 배포합니다. 가져올 때 적용된 소프트웨어 업데이트를 비롯하여, 운영 체제 업그레이드 패키지에 대한 정보가 사이트 데이터베이스에 저장됩니다. 처음에 추가한 이후에 업그레이드 패키지에 적용된 소프트웨어 업데이트도 사이트 데이터베이스에 저장됩니다. 마법사를 시작하여 운영 체제 업그레이드 패키지에 소프트웨어 업데이트를 적용할 때 마법사에서 사용자가 선택할 수 있도록 업그레이드 패키지에 아직 적용되지 않은 적용 가능한 소프트웨어 업데이트 목록을 검색합니다. Configuration Manager는 사이트 서버의 콘텐츠 라이브러리에서 소프트웨어 업데이트를 복사하여 운영 체제 업그레이드 패키지에 소프트웨어 업데이트를 적용합니다.  

 운영 체제 업그레이드 패키지에 소프트웨어 업데이트를 적용하려면 다음 절차를 수행하세요.  

#### <a name="to-apply-software-updates-to-an-operating-system-upgrade-package"></a>운영 체제 업그레이드 패키지에 소프트웨어 업데이트를 적용하려면  

1.  Configuration Manager 콘솔에서 **소프트웨어 라이브러리**를 클릭합니다.  

2.  **소프트웨어 라이브러리** 작업 영역에서 **운영 체제**를 확장하고 **운영 체제 업그레이드 패키지**를 클릭합니다.  

3.  소프트웨어 업데이트를 적용할 운영 체제 업그레이드 패키지를 선택합니다.  

4.  **홈** 탭의 **운영 체제 업그레이드 패키지** 그룹에서 **업데이트 예약** 을 클릭하여 마법사를 시작합니다.  

5.  **업데이트 선택** 페이지에서 운영 체제 이미지에 적용할 소프트웨어 업데이트를 선택한 후 **다음**을 클릭합니다.  

6.  **일정 설정** 페이지에서 다음 설정을 지정한 후에 **다음**을 클릭합니다.  

    1.  **일정**: 운영 체제 이미지에 소프트웨어 업데이트를 적용할 일정을 지정합니다.  

    2.  **오류 발생 시 계속**: 오류가 있어도 계속 이미지에 소프트웨어 업데이트를 적용하려면 이 옵션을 선택합니다.  

    3.  **배포 지점에 이미지 배포**: 소프트웨어 업데이트가 적용된 후에 배포 지점에서 운영 체제 이미지를 업데이트하려면 이 옵션을 선택합니다.  

7.  **요약** 페이지에서 정보를 확인한 후에 **다음**을 클릭합니다.  

8.  **완료** 페이지에서 소프트웨어 업데이트가 운영 체제 이미지에 성공적으로 적용되었는지 확인합니다.  
