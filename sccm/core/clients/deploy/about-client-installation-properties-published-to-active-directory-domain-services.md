---
title: Active Directory의 클라이언트 설치 속성
titleSuffix: Configuration Manager
description: Active Directory 도메인 서비스에 구성 관리자 클라이언트 설치 속성 게시
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: 101d7d4d-92db-419d-b2ae-3c1c1dea68e9
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 49b2edf7234e53c3fc03542f803933463190e8c1
ms.sourcegitcommit: 148745e1c3d9817d8beea20684a54436210959c6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75825271"
---
# <a name="about-client-installation-properties-published-to-active-directory-domain-services"></a>Active Directory Domain Services에 게시된 클라이언트 설치 속성 정보

*적용 대상: Configuration Manager(현재 분기)*

Configuration Manager를 위해 Active Directory 스키마를 확장하고 Active Directory 도메인 서비스에 사이트를 게시하면 많은 클라이언트 설치 속성이 Active Directory 도메인 서비스에 게시됩니다. 컴퓨터에서 이러한 클라이언트 설치 속성을 찾을 수 있는 경우 Configuration Manager 클라이언트 배포 시 이러한 속성을 사용할 수 있습니다.  

 Active Directory 도메인 서비스를 사용하여 클라이언트 설치 속성을 게시하는 것의 이점은 다음과 같습니다.  

-   소프트웨어 업데이트 지점 기반의 클라이언트 설치와 그룹 정책 클라이언트 설치 시 각 컴퓨터에서 설정 매개 변수를 설정할 필요가 없습니다.  

-   이 정보는 자동으로 생성되므로 수동으로 설치 속성을 입력하는 데 따른 사람의 실수 위험이 없습니다.  

> [!NOTE]  
>  Configuration Manager용으로 Active Directory 스키마를 확장하는 방법과 사이트를 게시하는 방법에 대한 자세한 내용은 [Configuration Manager용으로 스키마 확장](../../plan-design/network/schema-extensions.md)을 참조하세요.  

## <a name="client-installation-properties-published-to-active-directory-domain-services"></a>Active Directory Domain Services에 게시된 클라이언트 설치 속성  
아래 목록에는 클라이언트 설치 속성이 나와 있습니다. 아래 나열된 각 항목에 대한 자세한 내용은 [클라이언트 설치 속성 정보](../../../core/clients/deploy/about-client-installation-properties.md)를 참조하세요.  

- Configuration Manager 사이트 코드  

- 사이트 서버 서명 인증서  

- 신뢰할 수 있는 루트 키  

- HTTP 및 HTTPS용 클라이언트 통신 포트  

- 대체 상태 지점. 사이트에 대체 상태 지점이 여러 개 있는 경우 설치된 첫 번째 상태 지점만 Active Directory Domain Services에 게시됩니다.  

- 클라이언트가 HTTPS만 사용하여 통신해야 함을 나타내는 설정  

- PKI 인증서에 관련된 설정:  

  -   클라이언트 PKI 인증서를 사용할 것인지 여부  

  -   인증서 선택을 위한 선택 조건. 클라이언트에 Configuration Manager용으로 사용할 수 있는 유효한 PKI 인증서가 여러 개 있으면 이 조건이 필요할 수 있습니다.  

  -   인증서 선택 프로세스 후에도 클라이언트에 유효한 인증서가 여러 개 있는 경우 사용할 인증서를 결정하기 위한 설정  

  -   신뢰할 수 있는 루트 CA 인증서 목록이 포함된 인증서 발급자 목록  

- **클라이언트 강제 설치 속성** 대화 상자의 **클라이언트** 탭에서 지정되는 client.msi 설치 속성

다음 방법 중 하나를 사용하여 다른 속성이 지정되지 않은 경우에만 클라이언트 설치(CCMSetup)에서 Active Directory Domain Services에 게시되는 속성을 사용합니다.  

-   이 문서의 뒷부분에서 설명하는 수동 설치 방법

-   이 문서의 뒷부분에서 설명하는 그룹 정책 설치 방법

> [!NOTE]  
>  클라이언트 설치 속성은 클라이언트를 설치하는 데 사용됩니다. 클라이언트가 설치되고 Configuration Manager 사이트에 할당되고 나면 할당된 사이트의 새 설정이 클라이언트 설치 속성을 덮어쓸 수도 있습니다.  

 Active Directory Domain Service를 사용하여 클라이언트 설치 속성을 가져오는 Configuration Manager 클라이언트 설치 방법을 결정하려면 다음 섹션의 세부 정보를 참조하세요.  

## <a name="client-push-installation"></a>클라이언트 강제 설치  
 클라이언트 강제 설치는 Active Directory Domain Services를 사용하여 설치 속성을 가져오지 않습니다.  

 대신 **클라이언트 강제 설치 속성** 대화 상자의 **설치 속성** 탭에서 클라이언트 설치 속성을 지정할 수 있습니다. 이러한 옵션과 클라이언트 관련 설정은 클라이언트 설치 시 클라이언트가 읽는 파일에 저장되어 있습니다.  

> [!NOTE]  
>  **설치 속성** 탭에서 클라이언트 강제 설치를 위한 CCMSetup 속성이나 대체 상태 지점 또는 신뢰할 수 있는 루트 키를 지정할 필요가 없습니다. 이러한 설정은 클라이언트 강제 설치를 사용하여 클라이언트가 설치될 때 클라이언트에 자동으로 제공됩니다.
CCMSetup는 Client.msi 속성 외에, 매개 변수 /forcereboot, /skipprereq, /logon, /BITSPriority, /downloadtimeout, /forceinstall을 지원합니다.

 사이트가 Active Directory Domain Services에 게시되는 경우 **설치 속성** 탭에서 지정하는 모든 속성이 Active Directory Domain Services에 게시됩니다. 이러한 설정은 설치 속성 없이 CCMSetup이 실행되는 클라이언트 설치에서 읽혀집니다.  

## <a name="software-update-point-based-installation"></a>소프트웨어 업데이트 지점 기반 설치  
 소프트웨어 업데이트 지점 기반의 설치 방법에서는 CCMSetup 명령줄에 설치 속성을 추가할 수 없습니다.  

 클라이언트 컴퓨터에서 그룹 정책을 사용하여 명령줄 속성이 프로비전되지 않은 경우 CCMSetup은 Active Directory Domain Services에서 설치 속성을 검색합니다.  

## <a name="group-policy-installation"></a>그룹 정책 설치  
 그룹 정책 설치 방법에서는 CCMSetup 명령줄에 설치 속성을 추가할 수 없습니다.  

 클라이언트 컴퓨터에서 명령줄 속성이 프로비전되지 않은 경우 CCMSetup은 Active Directory Domain Services에서 설치 속성을 검색합니다.  

## <a name="manual-installation"></a>수동 설치  
 CCMSetup은 다음과 같은 경우 Active Directory Domain Services에서 설치 속성을 검색합니다.  

-   CCMSetup.exe 명령 뒤에 명령줄 속성이 지정되지 않은 경우  

-   그룹 정책을 사용하여 컴퓨터에 설치 속성을 프로비전하지 않은 경우  

## <a name="logon-script-installation"></a>로그온 스크립트 설치  
 CCMSetup은 다음과 같은 경우 Active Directory Domain Services에서 설치 속성을 검색합니다.  

-   CCMSetup.exe 명령 뒤에 명령줄 속성이 지정되지 않은 경우  

-   그룹 정책을 사용하여 컴퓨터에 설치 속성을 프로비전하지 않은 경우  

## <a name="software-distribution-installation"></a>소프트웨어 배포 설치  
 CCMSetup은 다음과 같은 경우 Active Directory Domain Services에서 설치 속성을 검색합니다.  

-   CCMSetup.exe 명령 뒤에 명령줄 속성이 지정되지 않은 경우  

-   그룹 정책을 사용하여 컴퓨터에 설치 속성을 프로비전하지 않은 경우  

## <a name="installations-for-clients-that-cannot-access-active-directory-domain-services"></a>Active Directory Domain Services에 액세스할 수 없는 클라이언트의 설치  
이러한 클라이언트 컴퓨터는 Active Directory Domain Services에서 게시된 설치 속성을 읽거나 해당 속성에 액세스할 수 없습니다.

 이러한 클라이언트는 다음과 같습니다.  

-   작업 그룹 컴퓨터  

-   Active Directory Domain Services에 게시되지 않은 Configuration Manager 사이트에 할당된 클라이언트  

-   인터넷상에 있을 때 설치된 클라이언트  
