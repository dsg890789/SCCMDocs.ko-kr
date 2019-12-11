---
title: 사용자에 게 앱 배포 기술 참조
titleSuffix: Configuration Manager
description: 사용자에 대 한 응용 프로그램 배포 문제 해결 기술 참조 Configuration Manager.
ms.date: 11/04/2019
ms.prod: configuration-manager
ms.technology: configmgr-app
ms.topic: troubleshooting
ms.assetid: b8e9dbfe-a046-4e06-8dec-cf0bc41ba095
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 59a2a1873a712184430cfe6c499b7d8b1067b207
ms.sourcegitcommit: 1bccb61bf3c7c69d51e0e224d0619c8f608e8777
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74823343"
---
# <a name="application-deployment-policy-for-users"></a>사용자에 대 한 응용 프로그램 배포 정책

*적용 대상: System Center Configuration Manager(현재 분기)*

응용 프로그램을 사용자 컬렉션에 배포 하는 경우 배포에 대 한 정책은 필수 배포에 대해서만 생성 됩니다. 사용 가능한 배포의 경우 사용자가 소프트웨어 센터에서 응용 프로그램을 설치 하려고 할 때 정책이 만들어집니다. 이 문서에서는 필수 배포 및 사용 가능한 배포에 대 한 배포 프로세스를 설명 합니다.

> [!TIP]
> 클라이언트 로그를 검토 하는 데 필요한 모든 정보는 [시작 하기 전에](/sccm/apps/understand/app-deployment-technical-reference#before-you-begin) 섹션에서 참조 하는 SQL 쿼리를 실행 하 여 가져올 수 있습니다.

## <a name="required-deployments"></a>필수 배포

사용자 컬렉션에 대 한 필수 응용 프로그램 배포에 대 한 정책은 배포를 만들 때 컬렉션의 모든 사용자를 대상으로 합니다. 이러한 배포에 대 한 클라이언트 쪽 처리는 장치 컬렉션에 대 한 필수 배포와 유사 합니다. 배포 활성화는 정의 된 사용 가능한 시간에 발생 하며, 지정 된 최종 기한 시간에 적용 됩니다. 자세한 내용은 [장치 컬렉션에 응용 프로그램 배포](/sccm/apps/understand/device-deployment-technical-reference)를 참조 하세요.

## <a name="available-deployments"></a>사용 가능한 배포

사용 가능한 것으로 사용자 컬렉션에 배포 되는 응용 프로그램은 다르게 동작 합니다. 이 동작을 변경 하면 관리자가 정책에 대 한 리소스 경합을 일으키지 않고 응용 프로그램을 사용자가 사용할 수 있도록 설정할 수 있습니다. 사용자가 소프트웨어 센터를 시작 하면 해당 사용자에 대해 사용할 수 있는 응용 프로그램 목록이 실시간으로 관리 지점에서 쿼리 됩니다. 이 요청은 관리 지점에서 `CMUserService_WindowsAuth` 가상 디렉터리에 적용 되며 클라이언트의 **SCClient_ [UserName] .log** 에서 볼 수 있습니다.

```text
Using endpoint Url: https://MP.CONTOSO.COM:443/CMUserService_WindowsAuth, Windows authentication
```

관리 지점에서이 요청을 받으면 `usp_GetApplicationPropertyValuesFiltered` 저장 프로시저를 실행 하 여 사용자가 사용할 수 있는 응용 프로그램 목록을 쿼리 합니다. 이 활동은 관리 지점의 **Userservice** 에서 추적할 수 있습니다.

```text
GetFilteredApplications, startItem = 0, max rows = 60, search text = '', filter = '', user = CONTOSO\UserName, api = 4.0, source = UserService_WinAuth_SoftwareCenter, platform = <OSPlatform>
GetFilteredApplications: returned 1 rows out of 1 total
```

소프트웨어 센터에서 목록을 수신 하 고 사용자가 설치할 수 있는 응용 프로그램을 표시 합니다. 사용자가 응용 프로그램을 클릭 하면 응용 프로그램에 대 한 추가 정보가 관리 지점에서 쿼리 됩니다. 여기에는 usp_GetApplicationInfo, usp_GetAppModelApplicationSupersedence usp_ 같은 저장 프로시저 실행이 포함 됩니다. GetDeploymentTypeForAnApp 등

사용자가 응용 프로그램을 선택 하 고 **설치** 단추를 클릭 하면 응용 프로그램을 평가 하는 DCM 에이전트 작업이 생성 되 면 배포가 활성화 됩니다. 응용 프로그램을 적용할 수 있는 경우 응용 프로그램을 다운로드 하 고 적용 하기 위해 다른 DCM 에이전트 작업을 만듭니다. 이 활동은 클라이언트의 **Dcmagent .log** 에서 추적할 수 있습니다.

## <a name="next-steps"></a>다음 단계

- [응용 프로그램 배포 클라이언트 구성 요소 이해](/sccm/apps/understand/client-components-technical-reference)
