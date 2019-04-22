---
title: 비즈니스용 OneDrive 프로필
titleSuffix: Configuration Manager
description: Configuration Manager에서 비즈니스용 OneDrive 프로필을 사용하여 Windows 알려진 폴더를 비즈니스용 OneDrive로 리디렉션합니다.
ms.date: 04/11/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: e217699a-28b2-471a-b421-8fbd1d1fd638
author: mestew
ms.author: mstewart
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 22fcc8704651d75b4123e7942d14b861b3f6c099
ms.sourcegitcommit: 6f4c2987debfba5d02ee67f6b461c1a988a3e201
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59802465"
---
# <a name="onedrive-for-business-profiles"></a>비즈니스용 OneDrive 프로필

Configuration Manager 버전 1902부터 Windows 알려진 폴더를 Business용 OneDrive로 이동하기 위한 비즈니스용 OneDrive 프로필을 생성할 수 있습니다. 이러한 폴더로는 바탕 화면, 문서, 사진 등이 있습니다. 각 프로필에서 Windows 알려진 폴더를 이동하기 위한 설정을 지정할 수 있습니다. 비즈니스용 OneDrive 프로필에 대한 자세한 내용은 [알려진 Windows 폴더를 OneDrive로 리디렉션 및 이동](https://docs.microsoft.com/onedrive/redirect-known-folders)을 참조하세요. <!--3556021-->

## <a name="prerequisites"></a>필수 구성 요소

- [Office 365 테넌트 ID 찾기](https://docs.microsoft.com/onedrive/find-your-office-365-tenant-id)  

- OneDrive 동기화 클라이언트 버전 18.111.0603.0004 이상을 배포합니다. 자세한 내용은 [System Center Configuration Manager를 사용하여 OneDrive 앱 배포](https://docs.microsoft.com/onedrive/deploy-on-windows)를 참조하세요.  

## <a name="bkmk_odfb"></a>알려진 Windows 폴더를 OneDrive로 이동
<!--3556021-->
Configuration Manager를 사용하여 알려진 Windows 폴더를 비즈니스용 OneDrive로 이동합니다. 이러한 폴더로는 바탕 화면, 문서, 사진 등이 있습니다. Windows 10 업그레이드의 간소화를 위해, 작업 순서를 배포하기 전에 해당 설정을 Windows 7 클라이언트에 배포하세요. 

1. Configuration Manager 콘솔에서 **자산 및 준수** 작업 영역으로 이동하고 **규정 준수 설정**을 확장한 다음 **비즈니스용 OneDrive 프로필** 노드를 선택합니다.  

   ![비즈니스용 OneDrive 프로필 노드](media/onedrive-for-business-profiles-node.png)
2. 리본에서 **비즈니스용 OneDrive 프로필 만들기**를 선택합니다.  

3. 이 정책을 식별하는 이름을 지정하고 **다음**을 선택합니다.  

4. 이 비즈니스용 OneDrive 프로필로 프로비저닝될 플랫폼을 선택합니다. 플랫폼을 선택했으면, **다음**을 클릭합니다.

    ![비즈니스용 OneDrive 프로필에 대한 플랫폼 선택](media/onedrive-for-business-profile-select-platforms.png) 

5. **설정** 페이지에서

    1. Office 365 테넌트 ID를 지정합니다.  

    2. 다음 옵션 중 하나를 선택하여 알려진 폴더를 OneDrive로 이동합니다.  

        - **Windows 알려진 폴더를 OneDrive로 이동하도록 사용자에게 요청**: 이 옵션을 사용하면 파일을 이동하는 마법사가 표시됩니다. 사용자가 폴더 이동을 미루거나 거부하는 경우, OneDrive에서 주기적으로 알림이 제공됩니다.  

        - **Windows 알려진 폴더를 OneDrive로 자동으로 이동**: 이 정책이 디바이스에 적용되면 OneDrive 클라이언트는 알려진 폴더를 비즈니스용 OneDrive로 자동으로 리디렉션합니다.  

            - **폴더가 리디렉션된 후 사용자에게 알림 표시**: 이 옵션을 사용하도록 설정하면 OneDrive 클라이언트가 폴더를 이동한 후 사용자에게 알립니다.  

    3. **사용자가 Windows 알려진 폴더를 PC로 다시 리디렉션하지 못하도록 방지**: 사용자가 해당 폴더를 디바이스로 다시 이동할 수 있도록 클라이언트에서 비즈니스용 OneDrive 옵션을 사용하지 않도록 설정합니다.  

       ![비즈니스용 OneDrive 알려진 폴더 이동 설정](media/onedrive-for-business-profile-move-folder-settings.png)

6. 마법사를 완료하고 정책을 배포합니다.  


## <a name="deploy-the-onedrive-for-business-profile"></a>비즈니스용 OneDrive 프로필 배포

1. Configuration Manager 콘솔에서 **자산 및 준수** 작업 영역으로 이동하고 **규정 준수 설정**을 확장한 다음 **비즈니스용 OneDrive 프로필** 노드를 선택합니다.  


2. 프로필을 선택한 다음 리본의 **배포** 배포를 선택합니다.

3. 배포에 대해 다음 설정을 지정합니다.

   1. **컬렉션**: **찾아보기**를 클릭하여 프로필을 배포할 컬렉션을 선택합니다.  
   1. **경고 생성**:

      -  **규정 준수가 낮은 경우**: 알림을 생성할 클라이언트 규정 준수의 최소 백분율입니다.
      -  **날짜 및 시간**: 프로파일 규정 준수에 따라 먼저 날짜 경고가 생성되기 시작합니다.
      - **System Center Operations Manager 경고 생성**: System Center Operations Manager로 규정 준수 경고를 보냅니다.
   1. **일정**:

      - **단순 일정**: 기본적으로 이 설정은 간단한 예약을 사용하여 7일마다 규정 준수 평가를 시작합니다.
      - **사용자 지정 일정**: 규정 준수 평가를 실행할 시기를 정의합니다. 단순 일정을 구성할 경우 시작 시간은 일정을 만들 때 Configuration Manager 콘솔을 실행하는 컴퓨터의 현지 시간을 기준으로 합니다.
 
      ![비즈니스용 OneDrive 프로필 배포](media/onedrive-for-business-deploy-profile.png)

4. 비즈니스용 OneDrive 프로필을 배포하려면 **확인**을 클릭합니다.


## <a name="next-steps"></a>다음 단계

[원격 연결 프로필 만들기](/sccm/compliance/deploy-use/create-remote-connection-profiles)
