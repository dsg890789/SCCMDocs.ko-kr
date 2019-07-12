---
title: 타사 업데이트 사용
titleSuffix: Configuration Manager
description: Configuration Manager의 타사 업데이트 사용
ms.date: 07/30/2018
ms.prod: configuration-manager
ms.technology: configmgr-sum
ms.topic: conceptual
ms.assetid: 946b0f74-0794-4e8f-a6af-9737d877179b
author: mestew
ms.author: mstewart
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 821f37f7c4b001fdf49d805dcdca2eef40cdce74
ms.sourcegitcommit: 20bbb870baf624c7809d3972f2d09a8d2df79cda
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 07/08/2019
ms.locfileid: "67623419"
---
# <a name="enable-third-party-updates"></a>타사 업데이트 사용 

*적용 대상: System Center Configuration Manager 버전 1806*

버전 1806부터 Configuration Manager 콘솔에서 **타사 소프트웨어 업데이트 카탈로그** 노드를 사용하면 타사 카탈로그를 구독하고 SUP(소프트웨어 업데이트 지점)에 해당 업데이트를 게시한 다음, 클라이언트에 업데이트를 배포할 수 있습니다.  <!--1357605, 1352101, 1358714-->



## <a name="prerequisites"></a>필수 구성 요소 
- 타사 소프트웨어 업데이트에 대한 원본 이진 콘텐츠를 저장하려면 최상위 소프트웨어 업데이트 지점의 WSUSContent 폴더에 충분한 디스크 공간이 있어야 합니다.
    - 필요한 스토리지 양은 공급 업체, 업데이트 유형 및 배포를 위해 게시하는 특정 업데이트에 따라 다릅니다.
    - 더 많은 여유 공간을 사용하여 WSUSContent 폴더를 다른 드라이브로 이동해야 하는 경우 [WSUS가 로컬로 업데이트를 저장하는 위치를 변경하는 방법](https://blogs.technet.microsoft.com/sus/2008/05/19/wsus-how-to-change-the-location-where-wsus-stores-updates-locally/) 블로그 게시물을 참조하세요.
- 타사 소프트웨어 업데이트 동기화 서비스는 인터넷 액세스가 필요합니다.
    - 파트너 카탈로그 목록의 경우 HTTPS 포트 443을 통해 download.microsoft.com이 필요합니다. 
    -  모든 타사 카탈로그에 인터넷으로 액세스하고 콘텐츠 파일을 업데이트합니다. 포트 443 이외의 포트가 추가로 필요할 수 있습니다.
    - 타사 업데이트는 SUP와 동일한 프록시 설정을 사용합니다.

## <a name="additional-requirements-when-the-sup-is-remote-from-the-top-level-site-server"></a>SUP가 최상위 사이트 서버에서 원격일 때 추가 요구 사항 

1. SSL은 원격일 경우 SUP에서 사용하도록 설정되어야 합니다. 이를 위해 내부 인증 기관 또는 공용 공급자를 통해 생성된 서버 인증 인증서가 필요합니다.
    - [WSUS에서 SSL 구성](/windows-server/administration/windows-server-update-services/deploy/2-configure-wsus#25-secure-wsus-with-the-secure-sockets-layer-protocol)
        - WSUS에서 SSL을 구성하는 경우 일부 웹 서비스 및 가상 디렉터리는 항상 HTTP이며 HTTPS가 아닙니다. 
        - Configuration Manager는 HTTP를 통해 WSUS 콘텐츠 디렉터리에서 소프트웨어 업데이트 패키지에 대한 타사 콘텐츠를 다운로드합니다.   
    - [SUP에서 SSL 구성](../get-started/install-a-software-update-point.md#configure-ssl-communications-to-wsus)

2. [소프트웨어 업데이트 지점 구성 요소 속성]에서 타사 업데이트 WSUS 서명 인증서 구성을 **Configuration Manager에서 업데이트 관리**로 설정하는 경우 자체 서명된 WSUS 서명 인증서를 만들려면 다음 구성이 필요합니다. 
   - SUP 서버에서 원격 레지스트리를 사용하도록 설정해야 합니다.
   -  **WSUS 서버 연결 계정**에는 SUP/WSUS 서버에 대한 원격 레지스트리 액세스 권한이 있어야 합니다. 


3. Configuration Manager 사이트 서버에서 다음 레지스트리 키를 만듭니다. 
    - `HKLM\Software\Microsoft\Update Services\Server\Setup`에서 `1` 값으로 **EnableSelfSignedCertificates**라는 새 DWORD를 만듭니다. 

4. 원격 SUP 서버의 신뢰할 수 있는 게시자 및 신뢰할 수 있는 루트 저장소에 자체 서명된 WSUS 서명 인증서를 설치하도록 설정하려면 다음이 필요합니다.
   - **WSUS 서버 연결 계정**에는 SUP 서버에 대한 원격 관리 액세스 권한이 있어야 합니다.

     이 항목이 가능하지 않은 경우 로컬 컴퓨터의 WSUS 저장소에서 신뢰할 수 있는 게시자 및 신뢰할 수 있는 루트 저장소로 인증서를 내보냅니다. 

> [!NOTE] 
>**WSUS 서버 연결 계정**은 SUP의 사이트 시스템 역할 속성에서 **프록시 및 계정 설정** 탭을 확인하여 식별할 수 있습니다. 계정을 지정하지 않은 경우 사이트 서버의 컴퓨터 계정을 사용합니다.

## <a name="enable-third-party-updates-on-the-sup"></a>SUP에서 타사 업데이트 사용
이 옵션을 사용하는 경우 Configuration Manager 콘솔에서 타사 업데이트 카탈로그를 구독할 수 있습니다. 그런 다음, 해당 업데이트를 WSUS에 게시하고 클라이언트에 배포할 수 있습니다. 사용을 위해 해당 기능을 설정하고 사용하려면 계층당 한 번씩 다음 단계를 수행해야 합니다. 최상위 SUP의 WSUS 서버를 교체하는 경우 이 단계를 다시 수행해야 합니다. 

1. Configuration Manager 콘솔에서 **관리** 작업 영역으로 이동합니다. **사이트 구성**을 확장하고 **사이트** 노드를 선택합니다.
2. 계층에서 최상위 사이트를 선택합니다. 리본에서 **사이트 구성 요소 구성**를 클릭하고 **소프트웨어 업데이트 지점**을 선택합니다.
3. **타사 업데이트** 탭으로 전환합니다. **타사 소프트웨어 업데이트 사용** 옵션을 선택합니다.

    ![타사 업데이트 SUP 속성 스크린샷](media/third-party-sup-properties.PNG)


## <a name="configure-the-wsus-signing-certificate"></a>WSUS 서명 인증서 구성
Configuration Manager에서 자체 서명된 인증서를 사용하여 타사 WSUS 서명 인증서를 자동으로 관리하도록 할지, 아니면 사용자가 인증서를 수동으로 구성해야 할지를 결정해야 합니다. 

### <a name="automatically-manage-the-wsus-signing-certificate"></a>WSUS 서명 인증서 자동 관리
PKI 인증서를 사용하기 위한 요구 사항이 없는 경우 타사 업데이트에 대한 서명 인증서를 자동으로 관리하도록 선택할 수 있습니다. WSUS 인증서 관리는 동기화 주기의 일부로 수행되며 `wsyncmgr.log`에 기록됩니다. 

1. Configuration Manager 콘솔에서 **관리** 작업 영역으로 이동합니다. **사이트 구성**을 확장하고 **사이트** 노드를 선택합니다.
2. 계층에서 최상위 사이트를 선택합니다. 리본에서 **사이트 구성 요소 구성**를 클릭하고 **소프트웨어 업데이트 지점**을 선택합니다.
3. **타사 업데이트** 탭으로 전환합니다. **Configuration Manager가 인증서 관리** 옵션을 선택합니다. 
4. 새 인증서 형식인 **타사 WSUS 서명**이 **관리** 작업 영역의 **보안** 아래 **인증서** 노드에서 만들어집니다.  

### <a name="manually-manage-the-wsus-signing-certificate"></a>WSUS 서명 인증서 수동 관리
PKI 인증서를 사용해야 하는 것처럼 인증서를 수동으로 구성해야 할 경우 [System Center Updates Publisher](../tools/updates-publisher-options.md#update-server) 또는 다른 도구를 사용하여 구성해야 합니다.  

1. [System Center Updates Publisher](../tools/updates-publisher-options.md#update-server)를 사용하여 서명 인증서를 구성합니다.
2. Configuration Manager 콘솔에서 **관리** 작업 영역으로 이동합니다. **사이트 구성**을 확장하고 **사이트** 노드를 선택합니다.
3. 계층에서 최상위 사이트를 선택합니다. 리본에서 **사이트 구성 요소 구성**를 클릭하고 **소프트웨어 업데이트 지점**을 선택합니다.
4. **타사 업데이트** 탭으로 전환합니다. **수동으로 인증서 관리** 옵션을 선택합니다.


## <a name="enable-third-party-updates-on-the-clients"></a>클라이언트에서 타사 업데이트 사용
클라이언트 설정의 클라이언트에서 타사 업데이트를 사용합니다. 이 설정은 [인트라넷 Microsoft 업데이트 서비스 위치에 대해 서명된 업데이트 허용](https://docs.microsoft.com/windows-server/administration/windows-server-update-services/deploy/4-configure-group-policy-settings-for-automatic-updates#allow-signed-updates-from-an-intranet-microsoft-update-service-location)에 대한 Windows 업데이트 에이전트 정책을 설정합니다. 이 클라이언트는 또한 클라이언트의 신뢰할 수 있는 게시자 저장소에 WSUS 서명 인증서를 설치합니다. 인증서 관리 로깅은 클라이언트의 `updatesdeployment.log` 에 표시됩니다.  타사 업데이트에 사용하려는 각 사용자 지정 클라이언트 설정에 이러한 단계를 실행합니다. 자세한 내용은 [클라이언트 설정 정보](/sccm/core/clients/deploy/about-client-settings#enable-third-party-software-updates) 문서를 참조하세요.

1. Configuration Manager 콘솔에서 **관리** 작업 공간으로 이동하여 **클라이언트 설정** 노드를 선택합니다.
2. 기존 사용자 지정 클라이언트 설정을 선택하거나 새로 만듭니다. 
3. 왼쪽에 있는 **소프트웨어 업데이트** 탭을 선택합니다. 이 탭이 없는 경우 **소프트웨어 업데이트** 상자가 사용하도록 설정됐는지 확인합니다.
4. **타사 소프트웨어 업데이트 사용**을 **예**로 설정합니다. 


## <a name="add-a-custom-catalog"></a>사용자 지정 카탈로그 추가
*파트너 카탈로그*는 Microsoft에 이미 등록된 정보가 포함된 소프트웨어 공급업체 카탈로그입니다. 파트너 카탈로그를 사용하여 추가 정보를 지정하지 않고도 가탈로그를 구독할 수 있습니다. 추가하는 카탈로그는 *사용자 지정 카탈로그*라고 합니다. 타사 업데이트 공급업체에서 Configuration Manager로 사용자 지정 카탈로그를 추가할 수 있습니다. 사용자 지정 카탈로그는 https를 사용해야 하며 업데이트는 디지털 서명해야 합니다. 

1. **소프트웨어 업데이트 라이브러리** 작업 영역으로 이동하여 **소프트웨어 업데이트**를 확장하고 **타사 소프트웨어 업데이트 카탈로그** 노드를 선택합니다. 
   
     ![타사 업데이트 노드 스크린 샷](media/third-party-updates-node.PNG)
2. 리본에서 **사용자 지정 카탈로그 추가**를 클릭합니다. 

     ![타사 업데이트가 사용자 지정 카탈로그를 추가](media/third-party-updates-custom-catalog.png)
1. **일반** 페이지에서 다음 항목을 지정합니다. 
    - **다운로드 URL**: 사용자 지정 카탈로그의 유효한 HTTPS 주소입니다.
    - **게시자**: 카탈로그를 게시하는 조직의 이름입니다. 
    - **이름**: Configuration Manager 콘솔에 표시할 카탈로그의 이름입니다. 
    - **설명**: 카탈로그에 대한 설명입니다. 
    - **지원 URL**(선택 사항): 카탈로그에 대한 도움말을 볼 수 있는 웹 사이트의 유효한 HTTPS 주소입니다. 
    - **지원 담당자**(선택 사항): 카탈로그에 대한 도움을 받을 수 있는 담당자 정보입니다. 
2. **다음**을 클릭하여 카탈로그 요약을 검토하고 **타사 소프트웨어 업데이트 사용자 지정 카탈로그 마법사**를 완료하기 위해 계속 진행합니다.


## <a name="subscribe-to-a-third-party-catalog-and-sync-updates"></a>타사 카탈로그 구독 및 업데이트 동기화
Configuration Manager 콘솔에서 타사 공급업체 카탈로그를 구독하면 카탈로그에서 모든 업데이트에 대한 메타데이터는 SUP용 WSUS 서버에 동기화됩니다. 메타 데이터 동기화를 사용하면 클라이언트가 업데이트가 적용 가능한지 여부를 확인할 수 있습니다. 구독하려는 각 타사 카탈로그에 대한 다음 단계를 수행합니다.  

1. Configuration Manager 콘솔에서 **소프트웨어 라이브러리** 작업 영역으로 이동합니다. **소프트웨어 업데이트**를 확장해 **타사 소프트웨어 업데이트 카탈로그** 노드를 선택합니다.  
2. 구독할 카탈로그를 선택하고 리본 메뉴에서 **카탈로그 구독**을 클릭합니다. 
    ![타사 업데이트가 사용자 지정 카탈로그를 추가](media/third-party-updates-subscribe.png)
3. 카탈로그 인증서를 검토하고 승인합니다.  
   > [!NOTE]
   > 
   > 타사 소프트웨어 업데이트 카탈로그를 구독하면 마법사에서 검토하고 승인하는 인증서가 사이트에 추가됩니다. 이 인증서는 **타사 소프트웨어 업데이트 카탈로그** 형식입니다. 이 인증서를 **관리** 작업 영역의 **보안** 아래 **인증서** 노드에서 관리할 수 있습니다.  
4. 마법사를 완료합니다. 초기 구독 후 카탈로그를 몇 분 내에 다운로드해야 합니다. 
    - 카탈로그는 7일마다 자동으로 동기화됩니다.
    - 리본 메뉴에서 **지금 동기화**를 클릭하여 강제로 동기화합니다.
5. 카탈로그를 다운로드하면 제품 메타데이터를 WSUS 데이터베이스에서 Configuration Manager 데이터베이스로 동기화해야 합니다. [수동으로 소프트웨어 업데이트 동기화를 시작](../get-started/synchronize-software-updates.md#manually-start-software-updates-synchronization)하여 제품 정보를 동기화합니다.
6. 제품 정보를 동기화하면 [원하는 제품을 동기화하기 위해 SUP](../get-started/configure-classifications-and-products.md#to-configure-classifications-and-products-to-synchronize)를 Configuration Manager로 구성합니다.  
7. [수동으로 소프트웨어 업데이트 동기화를 시작](../get-started/synchronize-software-updates.md#manually-start-software-updates-synchronization)하여 신제품 업데이트를 Configuration Manager로 동기화합니다.  
8. 동기화를 완료하면 **모든 업데이트** 노드에서 타사 업데이트를 확인할 수 있습니다. 이러한 업데이트는 게시를 선택할 때까지 **메타데이터 전용** 업데이트로 게시됩니다. 
     - 파란색 화살표가 있는 아이콘은 메타데이터 전용 소프트웨어 업데이트를 나타냅니다. ![메타데이터 전용 소프트웨어 업데이트 아이콘](media/MetadataOnly.png)


## <a name="publish-and-deploy-third-party-software-updates"></a>타사 소프트웨어 업데이트 게시 및 배포 
**모든 업데이트** 노드에 타사 업데이트가 포함된 경우 배포를 위해 게시해야 하는 업데이트를 선택할 수 있습니다. 업데이트를 게시할 때 공급업체에서 다운로드된 이진 파일은 최상위 SUP의 WSUSContent 디렉터리에 배치됩니다. 

1. Configuration Manager 콘솔에서 **소프트웨어 라이브러리** 작업 영역으로 이동합니다. **소프트웨어 업데이트**를 확장해 **모든 소프트웨어 업데이트** 노드를 선택합니다.
2. **조건 추가**를 클릭하여 업데이트 목록을 필터링합니다. 예를 들어 HP의 모든 업데이트를 보려면 **HP**에 대한 **공급업체** 를 추가합니다.  
3. 조직에서 필요한 업데이트를 선택합니다. **타사 소프트웨어 업데이트 콘텐츠 게시**를 클릭합니다.
    - 이 작업은 공급 업체에서 업데이트 바이너리를 다운로드한 다음, 최상위 소프트웨어 업데이트 지점의 WSUSContent 폴더에 저장합니다. 
4. [수동으로 소프트웨어 업데이트 동기화를 시작](../get-started/synchronize-software-updates.md#manually-start-software-updates-synchronization)하여 게시된 업데이트의 상태를 메타데이터 전용에서 콘텐츠로 배포할 수 있는 업데이트로 변경합니다. 
    >[!NOTE]
    >타사 소프트웨어 업데이트 콘텐츠를 게시하면 콘텐츠 서명에 사용된 모든 인증서가 사이트에 추가됩니다. 이러한 인증서는 **타사 소프트웨어 업데이트 콘텐츠** 형식입니다. 이 인증서를 **관리** 작업 영역의 **보안** 아래 **인증서** 노드에서 관리할 수 있습니다.  

5. SMS_ISVUPDATES_SYNCAGENT.log의 진행률을 검토합니다. 로그는 사이트 시스템 로그 폴더의 최상위 소프트웨어 업데이트 지점에 있습니다.
6. [소프트웨어 업데이트 배포](../deploy-use/deploy-software-updates.md) 프로세스를 사용하여 업데이트를 배포합니다. 
7. **소프트웨어 업데이트 배포 마법사**의 **다운로드 위치** 페이지에서 **인터넷에서 소프트웨어 업데이트를 다운로드**하기 위한 기본 옵션을 선택합니다. 이 시나리오에서 콘텐츠는 배포 패키지의 콘텐츠를 다운로드하는 데 사용되는 소프트웨어 업데이트 지점에 게시됩니다.
8. 클라이언트는 준수 결과를 확인할 수 있기 전에 업데이트를 평가하고 검사를 실행해야 합니다.  **소프트웨어 업데이트 검사 주기**를 실행하여 클라이언트의 Configuration Manager 제어판에서 이 주기를 수동으로 트리거할 수 있습니다.


## <a name="monitoring-progress-of-third-party-software-updates"></a>타사 소프트웨어 업데이트의 진행률 모니터링 

타사 소프트웨어 업데이트 동기화는 최상위 기본 소프트웨어 업데이트 지점에서 SMS_ISVUPDATES_SYNCAGENT 구성 요소에 의해 처리됩니다. 이 구성 요소에서 상태 메시지를 보거나 SMS_ISVUPDATES_SYNCAGENT.log에서 자세한 상태를 확인할 수 있습니다. 이 로그는 사이트 시스템 로그 폴더의 최상위 소프트웨어 업데이트 지점에 있습니다. 기본적으로 이 경로는 C:\Program Files\Microsoft Configuration Manager\Logs입니다. 일반 소프트웨어 업데이트 관리 프로세스 모니터링에 대한 자세한 내용은 [소프트웨어 업데이트 모니터링](../deploy-use/monitor-software-updates.md)을 참조하세요. 

## <a name="known-issues"></a>알려진 문제

- 콘솔을 실행 중인 머신은 WSUS에서 업데이트를 다운로드하여 업데이트 패키지에 추가하는 데 사용됩니다. 콘솔 머신에서 WSUS 서명 인증서를 신뢰할 수 있어야 합니다. 신뢰할 수 없은 경우 타사 업데이트를 다운로드하는 동안 서명 확인의 문제가 발생할 수 있습니다. 
- 타사 소프트웨어 업데이트 동기화 서비스는 SCUP 같은 다른 애플리케이션, 도구 또는 스크립트가 WSUS에 추가한 메타데이터 전용 업데이트에 콘텐츠를 게시할 수 없습니다. **타사 소프트웨어 업데이트 콘텐츠 게시** 작업은 이러한 업데이트에서 실패합니다. 이 기능이 아직 지원하지 않는 타사 업데이트를 배포해야 하는 경우 해당 업데이트를 배포하는 데 기존 프로세스 전체를 사용합니다.  
-  Configuration Manager에는 카탈로그 cab 파일 형식에 대한 새 버전이 있습니다. 이 새 버전에는 공급업체의 이진 파일에 대한 인증서가 포함됩니다. 이러한 인증서는 카탈로그를 승인하고 신뢰하면 **관리** 작업 영역의 **보안** 아래 **인증서** 노드에 추가됩니다.  
     - 다운로드 URL이 https이고 업데이트에 서명한 경우 여전히 이전 카탈로그 cab 파일 버전을 사용할 수 있습니다. 이진 파일에 대한 인증서가 cab 파일에 있지 않고 이미 승인됐으므로 콘텐츠를 게시하지 못합니다. **인증서** 노드에서 인증서를 찾아 차단 해제한 다음, 다시 업데이트를 게시하여 이 문제를 해결할 수 있습니다. 다른 인증서로 서명된 여러 업데이트를 게시하는 경우 사용되는 각 인증서를 차단 해제해야 합니다.
     - 자세한 내용은 아래 상태 메시지 테이블에서 11523 및 11524 상태 메시지를 참조하세요.
-  최상위 소프트웨어 업데이트 지점에서의 타사 소프트웨어 업데이트 동기화 서비스에 인터넷 액세스용 프록시 서버가 필요한 경우 디지털 서명 확인에 실패할 수 있습니다. 이 문제를 완화하려면 사이트 시스템에서 WinHTTP 프록시 설정을 구성합니다. 자세한 내용은 [Netsh commands for WinHTTP](https://go.microsoft.com/fwlink/p/?linkid=199086)\(WinHTTP용 Netsh 명령\)를 참조하세요.

## <a name="status-messages"></a>상태 메시지

| MessageID       | 심각도           | 설명 | 가능한 원인| 가능한 해결 방법
| ------------- |-------------| -----|----|----|
| 11516     | 오류 |콘텐츠에 서명이 없으므로 "업데이트 ID"를 업데이트하기 위해 콘텐츠를 게시하지 못했습니다.  올바른 서명이 있는 콘텐츠만 게시할 수 있습니다.  |Configuration Manager는 서명되지 않은 업데이트가 게시되는 것을 허용하지 않습니다.| 대신 업데이트를 게시합니다. </br></br>서명된 업데이트를 공급업체에서 사용할 수 있는지 확인합니다.|
| 11523  | 경고 |  카탈로그 "X"에는 콘텐츠 서명 인증서가 포함되지 않으므로 이 카탈로그에서 업데이트에 대한 업데이트 콘텐츠를 게시하려는 시도는 콘텐츠 서명 인증서를 추가하고 승인할 때까지는 실패할 수 있습니다. | 이 메시지는 이전 버전의 cab 파일 형식을 사용하는 카탈로그를 가져올 때 표시될 수 있습니다.|콘텐츠 서명 인증서가 포함된 업데이트된 카탈로그를 가져오려면 카탈로그 공급자에게 문의하세요. </br> </br> 이진 파일에 대한 인증서가 cab 파일에 포함되지 않으므로 콘텐츠를 게시하지 못합니다. **인증서** 노드에서 인증서를 찾아 차단 해제한 다음, 다시 업데이트를 게시하여 이 문제를 해결할 수 있습니다. 다른 인증서로 서명된 여러 업데이트를 게시하는 경우 사용되는 각 인증서를 차단 해제해야 합니다.|
| 11524| 오류  | 업데이트 메타데이터 누락으로 업데이트 "ID"를 게시하지 못했습니다. | 이 업데이트는 Configuration Manager 외부에서 WSUS에 동기화되었을 수 있습니다.| 해당 콘텐츠를 게시하기 전에 이 업데이트를 Configuration Manager와 동기화합니다.  </br> </br>업데이트를 **메타데이터 전용**으로 게시하는 데 외부 도구를 사용한 경우 동일한 도구를 사용하여 업데이트 콘텐츠를 게시합니다.|



## <a name="working-with-third-party-updates-video"></a>타사 업데이트 비디오 작업
<iframe width="560" height="315" src="https://www.youtube.com/embed/ai8rLCLtuTI?rel=0" frameborder="0" allowfullscreen></iframe>



## <a name="next-step"></a>다음 단계
> [!div class="nextstepaction"]
> [소프트웨어 업데이트 배포](./deploy-software-updates.md)
