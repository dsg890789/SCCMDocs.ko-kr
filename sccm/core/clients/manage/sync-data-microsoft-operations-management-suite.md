---
title: "데이터 동기화 | Microsoft Operations Management Suite | System Center Configuration Manager"
description: "System Center Configuration Manager의 데이터를 Microsoft Operations Management Suite에 동기화합니다."
ms.custom: na
ms.date: 10/13/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 33bcf8b3-a6b6-4fc9-bb59-70a9621b2b0d
caps.latest.revision: 9
author: nbigman
ms.author: nbigman
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 0fbce476b8a9b91a88354fb4abfadfd2526ca5e8
ms.openlocfilehash: 5786f0734ce186601f5173003b9b133ed6ae8b11

---
# <a name="sync-data-from-configuration-manager-to-the-microsoft-operations-management-suite"></a>Configuration Manager의 데이터를 Microsoft Operations Management Suite에 동기화합니다.

*적용 대상: System Center Configuration Manager(현재 분기)*

Microsoft OMS(Operations Management Suite) 커넥터를 사용하여 System Center Configuration Manager의 데이터(예: 사용자 컬렉션)를 OMS에 동기화할 수 있습니다. 이렇게 하면 Configuration Manager 배포의 데이터가 OMS에 표시됩니다.

## <a name="add-an-oms-connection-to-configuration-manager"></a>Configuration Manager에 OMS 연결 추가

OMS 연결을 추가하려면 Configuration Manager 환경에서 먼저 [서비스 연결 지점](../../../core/servers/deploy/configure/about-the-service-connection-point.md)을 [온라인 모드](https://azure.microsoft.com/en-us/documentation/articles/resource-group-create-service-principal-portal/)로 구성해야 합니다. 사용자 환경에 OMS 연결을 추가하면 이 사이트 시스템 역할을 실행하는 컴퓨터에 Microsoft Monitoring Agent도 설치됩니다.
1.  **관리** 작업 영역에서 **OMS 커넥터**를 선택합니다. 리본에서 "Operations Management Suite에 대한 연결 만들기"를 클릭합니다. 그러면 **Operation Management Suite 연결 마법사**가 열립니다. **다음**을 선택합니다.
2.  **일반** 화면에서 다음 정보가 있는지 확인하고 **다음**을 선택합니다.

    * Configuration Manager를 "웹 응용 프로그램 및/또는 웹 API" 관리 도구로 등록했으며 [이 등록의 클라이언트 ID](https://azure.microsoft.com/documentation/articles/active-directory-integrating-applications/)가 있습니다.
    * Azure Active Directory에서 등록된 관리 도구에 대한 클라이언트 키를 만듭니다.
    * Azure 관리 포털에서 [Configuration Manager에 OMS에 대한 사용 권한 제공](https://azure.microsoft.com/en-us/documentation/articles/log-analytics-sccm/#provide-configuration-manager-with-permissions-to-oms)에 설명된 대로 OMS에 액세스할 수 있는 권한을 등록된 웹앱에 제공했습니다.

3.  **Azure Active Directory** 화면에서 해당 **테넌트**, **클라이언트 ID** 및 **클라이언트 비밀 키**를 제공하여 OMS에 대한 연결 설정을 구성하고 **다음**을 선택합니다.
4.  **OMS 연결 구성** 화면에서 **Azure 구독**, **Azure 리소스 그룹** 및 **Operations Management Suite 작업 영역**에 정보를 입력하여 연결 설정을 제공합니다.
5.  **요약** 화면에서 연결 설정을 확인하고 **다음**을 선택합니다. **진행률** 화면에 연결 상태가 표시되며 **완료**여야 합니다.

> [!NOTE]
> 계층 구조의 최상위 계층 사이트에 OMS를 연결해야 합니다. OMS를 독립 실행형 기본 사이트에 연결한 다음 사용자 환경에 중앙 관리 사이트를 추가하는 경우 OMS 연결을 삭제하고 새 계층 구조 내에서 다시 만들어야 합니다.

Configuration Manager를 OMS에 연결한 후 컬렉션을 추가하거나 제거하고 OMS 연결의 속성을 볼 수 있습니다.

## <a name="viewing-microsoft-operations-management-suite-connection-properties-in-configuration-manager"></a>Configuration Manager에서 Microsoft Operations Management Suite 연결 속성 보기

1.  **클라우드 서비스**로 이동한 다음 **OMS 커넥터**를 선택하여 **OMS 연결 속성** 페이지를 엽니다.
2.  이 페이지에는 다음 두 개의 탭이 있습니다.
  * **Azure Active Directory** 탭에는 **테넌트**, **클라이언트 ID**, **클라이언트 비밀 키 만료**가 표시되며, 만료된 경우 **클라이언트 비밀 키**를 **확인**할 수 있습니다.
  * **OMS 연결 속성** 탭에는 **Azure 구독**, **Azure 리소스 그룹**, **Operations Management Suite 작업 영역**과 **Operations Management Suite에서 데이터를 가져올 수 있는 장치 컬렉션** 목록이 표시됩니다. **추가** 및 **제거** 단추를 사용하여 허용되는 컬렉션을 수정합니다.



<!--HONumber=Nov16_HO1-->


