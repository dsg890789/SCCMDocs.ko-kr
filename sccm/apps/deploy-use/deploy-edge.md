---
title: Microsoft Edge 버전 77 이상의 배포 및 업데이트
titleSuffix: Configuration Manager
description: Configuration Manager를 사용 하 여 Microsoft Edge, 77 이상 버전을 배포 하 고 업데이트 하는 방법
ms.date: 11/29/2019
ms.prod: configuration-manager
ms.technology: configmgr-app
ms.topic: conceptual
ms.assetid: 73b420be-5d6a-483a-be66-c4d274437508
author: mestew
ms.author: mstewart
manager: dougeby
ms.openlocfilehash: 25ff9d97fb0079373ae8ac8fe75e2d31d2f2e662
ms.sourcegitcommit: 148745e1c3d9817d8beea20684a54436210959c6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75815870"
---
# <a name="microsoft-edge-management"></a>Microsoft Edge 관리

*적용 대상: Configuration Manager(현재 분기)*

모든 새로운 Microsoft Edge는 비즈니스용으로 준비됩니다. Configuration Manager 버전 1910부터 이제 사용자에 게 [Microsoft Edge, 버전 77 이상을](https://docs.microsoft.com/deployedge/) 배포할 수 있습니다.

## <a name="bkmk_Microsoft_Edge"></a>Microsoft Edge, 버전 77 이상 배포
<!--4561024-->
관리자는 배포할 Microsoft Edge 클라이언트 버전과 함께 베타 또는 개발 채널을 선택할 수 있습니다. 각 릴리스는 고객과 커뮤니티의 학습 및 향상된 기능을 통합합니다.

### <a name="prerequisites-for-deploying"></a>배포를 위한 필수 구성 요소

Microsoft Edge 버전 77 이상 배포를 대상으로 하는 클라이언트:

- PowerShell [실행 정책](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_execution_policies)은 제한됨으로 설정할 수 없습니다.
  - 설치를 수행하기 위해 PowerShell이 실행됩니다.
  
Configuration Manager 콘솔을 실행하는 디바이스에는 다음 엔드포인트에 대한 액세스 권한이 있어야 합니다.

|위치|Windows Server Update Services와 함께|
|---|---|
|`https://edgeupdates.azurewebsites.net/api/products?view=enterprise`|Microsoft Edge 버전 77 이상의 릴리스에 대한 정보|
|`http://dl.delivery.mp.microsoft.com`|Microsoft Edge 릴리스, 버전 77 이상에 대한 콘텐츠|




### <a name="create-a-deployment"></a>배포 만들기

기본 제공 애플리케이션 환경을 사용하여 Microsoft Edge, 버전 77 이상 애플리케이션을 만들어 Microsoft Edge를 더욱 쉽게 관리할 수 있습니다.

1. 콘솔의 **소프트웨어 라이브러리** 아래에 **Microsoft Edge 관리**라는 새 노드가 있습니다.
1. 리본에서**Microsoft Edge 애플리케이션 만들기**를 선택하거나 **Microsoft Edge 관리** 노드를 마우스 오른쪽 단추로 클릭합니다.

   ![Microsoft Edge 관리 노드 마우스 오른쪽 단추 클릭 작업](./media/4561024-create-microsoft-edge-application.png)

1. 마법사의 **애플리케이션 설정** 페이지에서 앱의 콘텐츠에 대한 이름, 설명 및 위치를 지정합니다.
1. **Microsoft Edge 설정** 페이지에서 배포할 채널 및 버전을 선택합니다. 자세한 정보 링크를 누르면 [Microsoft Edge 참가자 페이지](https://www.microsoftedgeinsider.com/)로 이동할 수 있습니다.

   ![배포 마법사의 Microsoft Edge 설정 페이지](./media/4561024-edge-settings-wizard.png)

1. **배포** 페이지에서 애플리케이션을 배포할지 여부를 결정합니다. **예**를 선택하는 경우 애플리케이션에 대한 배포 설정을 지정할 수 있습니다. 배포 설정에 대 한 자세한 내용은 [응용 프로그램 배포](/configmgr/apps/deploy-use/deploy-applications#bkmk_deploy-general)를 참조 하세요.
1. 클라이언트 디바이스의 **소프트웨어 센터**에서 사용자는 애플리케이션을 보고 설치할 수 있습니다.

   ![배포 마법사의 Microsoft Edge 설정 페이지](./media/4561024-software-center-install-edge.png)

### <a name="log-files-for-deployment"></a>배포용 로그 파일

|위치|로그|Windows Server Update Services와 함께|
|---|---|---|
| 사이트 서버|SMSProv.log|앱 또는 배포 만들기가 실패할 경우 세부 정보를 표시합니다.|
| [상황에 따라 다름](/sccm/core/plan-design/hierarchy/log-files)|PatchDownloader.log| 콘텐츠 다운로드에 실패하는 경우 세부 정보 표시|
| 클라이언트|  AppEnforce.log|설치 정보 표시|

## <a name="update-microsoft-edge-version-77-and-later"></a>Microsoft Edge, 버전 77 이상 업데이트
<!--4831871-->

Configuration Manager 버전 1910부터 **Microsoft Edge Management**에서 **모든 microsoft edge 업데이트** 라는 노드가 표시 될 수 있습니다. 이 노드에 아직 업데이트가 표시 되지 않지만 Configuration Manager 준비가 되었다는 것을 알아야 합니다.

   ![모든 Microsoft Edge 업데이트 노드](./media/4831871-all-microsoft-edge-updates.png)

## <a name="next-steps"></a>다음 단계

[애플리케이션 모니터링](/configmgr/apps/deploy-use/monitor-applications-from-the-console)