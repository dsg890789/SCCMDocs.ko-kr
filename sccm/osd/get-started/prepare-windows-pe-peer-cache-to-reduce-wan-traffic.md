---
title: "WAN 트래픽을 줄이기 위해 Windows PE 피어 캐시 준비"
titleSuffix: Configuration Manager
description: "Windows PE 피어 캐시는 로컬 배포 지점이 없는 경우 로컬 피어로부터 콘텐츠를 가져와 WAN 트래픽을 최소화하도록 Windows PE에서 작동합니다."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-osd
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 6c64f276-b88c-4b1e-8073-331876a03038
caps.latest.revision: "11"
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.openlocfilehash: bb0ed6809d1350c4ce28e20d1a83082a51c2e687
ms.sourcegitcommit: 1132886e07d0c0a87dcc7eeef4577dd8d8840023
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/01/2017
---
# <a name="prepare-windows-pe-peer-cache-to-reduce-wan-traffic-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 WAN 트래픽을 줄이기 위해 Windows PE 피어 캐시 준비

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager에서 새 운영 체제를 배포할 때 작업 순서를 실행하는 컴퓨터가 배포 지점에서 콘텐츠를 다운로드하는 대신 Windows PE 피어 캐시를 사용하여 로컬 피어(피어 캐시 원본)에서 콘텐츠를 가져올 수 있습니다. 따라서 로컬 배포 지점이 없는 지점 시나리오에서 WAN(광역 네트워크) 트래픽을 최소화할 수 있습니다.  

 Windows PE 피어 캐시는 [Windows BranchCache](http://technet.microsoft.com/library/mt617255\(TechNet.10\).aspx#bkmk_branchcache)와 비슷하지만 Windows PE(사전 설치 환경)에서 작동합니다. Windows PE 피어 캐시를 사용하는 클라이언트에 설명하는 데 다음과 같은 용어가 사용됩니다.  

-   **피어 캐시 클라이언트** 는 Windows PE 피어 캐시를 사용하도록 구성된 컴퓨터입니다.  

-   **피어 캐시 원본** 은 피어 캐시를 사용하도록 구성되어 있는 클라이언트로, 콘텐츠를 요청하는 다른 피어 캐시 클라이언트에 해당 콘텐츠를 제공합니다.  

다음 섹션을 사용하여 피어 캐시를 관리합니다.

##  <a name="BKMK_PeerCacheObjects"></a> 피어 캐시 원본에 저장된 개체  
 Windows PE 피어 캐시를 사용하도록 구성된 작업 순서는 Windows PE에서 실행되는 동안 다음과 같은 콘텐츠 개체를 가져올 수 있습니다.  

-   운영 체제 이미지  

-   드라이버 패키지  

-   패키지 및 프로그램(클라이언트는 전체 운영 체제에서 작업 순서를 계속 실행할 때 해당 작업 순서가 원래는 Windows PE에서 실행 시 피어 캐시에 대해 구성된 경우 피어 캐시 원본에서 이 콘텐츠를 가져옵니다.)  

-   추가 부팅 이미지  

 다음 콘텐츠 개체는 피어 캐시를 사용하여 전송하지 않습니다. 대신 배포 지점에서 전송되거나 환경에서 Windows BranchCache를 구성한 경우에는 Windows BranchCache를 통해 전송됩니다.  

-   응용 프로그램  

-   소프트웨어 업데이트  

##  <a name="BKMK_PeerCacheWork"></a> Windows PE 피어 캐시 작동 방식  
 배포 지점은 없으며 여러 클라이언트가 Windows PE 피어 캐시를 사용할 수 있도록 설정된 지점 시나리오를 고려해 보겠습니다. 피어 캐시를 사용하도록 구성된 작업 순서를 피어 캐시 원본의 일부가 되도록 구성된 여러 클라이언트에 배포합니다. 작업 순서를 실행하는 첫 번째 클라이언트는 콘텐츠를 포함하여 피어에 대한 요청을 브로드캐스트합니다. 해당 콘텐츠를 찾지 못하므로 WAN을 통해 배포 지점에서 콘텐츠를 가져옵니다. 클라이언트는 새 이미지를 설치하고 다른 클라이언트에 대한 피어 캐시 원본 역할을 할 수 있도록 해당 Configuration Manager 클라이언트 캐시에 콘텐츠를 저장합니다. 다음 클라이언트는 작업 순서를 실행할 때 피어 캐시 원본에 대해 서브넷에서 요청을 브로드캐스트하며, 그러면 첫 번째 클라이언트가 응답하여 캐시된 콘텐츠를 제공합니다.  

##  <a name="BKMK_PeerCacheDetermine"></a> Windows PE 피어 캐시 원본의 일부가 될 클라이언트 확인  
 Windows PE 피어 캐시 원본으로 선택할 컴퓨터를 확인하는 데 도움이 되도록 고려해야 할 몇 가지 사항이 다음에 설명되어 있습니다.  

-   Windows PE 피어 캐시 원본은 항상 전원이 켜져 있고 피어 캐시 클라이언트에서 사용할 수 있는 데스크톱 컴퓨터여야 합니다.  

-   Windows PE 피어 캐시에는 이미지를 저장할 만큼 충분한 크기의 클라이언트 캐시가 있어야 합니다.  

##  <a name="BKMK_PeerCacheRequirements"></a> Windows PE 피어 캐시 원본을 사용하기 위한 클라이언트 요구 사항  
 클라이언트에서 Windows PE 피어 캐시 원본을 사용하려면 다음 요구 사항을 충족해야 합니다.  

-   Configuration Manager 클라이언트가 네트워크의 다음 포트를 통해 통신할 수 있어야 합니다.  

    -   피어 캐시 원본을 찾기 위한 초기 네트워크 브로드캐스트용 포트. 기본 포트는 8004입니다.  

    -   피어 캐시 원본에서 콘텐츠를 다운로드하기 위한 포트(HTTP 및 HTTPS). 기본 포트는 8003입니다.  

        > [!TIP]  
        >  클라이언트는 사용할 수 있는 콘텐츠가 있을 때 HTTPS를 사용하여 다운로드합니다. 그러나 HTTP 또는 HTTPS에 동일한 포트 번호가 사용됩니다.  

-   배포하는 이미지를 보관하고 저장하기에 충분한 공간이 있도록 클라이언트에 [Configuration Manager 클라이언트에 대한 클라이언트 캐시를 구성](../../core/clients/manage/manage-clients.md#BKMK_ClientCache)합니다. Windows PE 피어 캐시는 클라이언트 캐시의 구성 또는 동작에 영향을 주지 않습니다.  

-   작업 순서 배포를 위한 배포 옵션을 작업 순서를 실행하기 전에 콘텐츠를 로컬에 다운로드로 구성해야 합니다.  

##  <a name="BKMK_PeerCacheConfigure"></a> Windows PE 피어 캐시 구성  
 다음과 같은 방법을 사용하면 특정 클라이언트가 피어 캐시 원본 역할을 할 수 있도록 피어 캐시 콘텐츠를 프로비전할 수 있습니다.  

-   콘텐츠를 보유하고 있는 피어 캐시 원본을 찾을 수 없는 피어 캐시 클라이언트는 배포 지점에서 콘텐츠를 다운로드합니다.  작업 순서가 캐시된 콘텐츠를 보존하도록 구성되어 있으면 피어 캐시를 사용하도록 설정하는 클라이언트 설정을 수신하는 클라이언트가 피어 캐시 원본이 됩니다.  

-   피어 캐시 클라이언트는 다른 피어 캐시 클라이언트(피어 캐시 원본)에서 콘텐츠를 가져올 수 있습니다.  이 클라이언트는 피어 캐시용으로 구성되므로 캐시된 콘텐츠를 보존하도록 구성된 작업 순서를 실행할 때 피어 캐시 원본이 됩니다.  

-   클라이언트가 선택적인 [패키지 콘텐츠 다운로드](../understand/task-sequence-steps.md#BKMK_DownloadPackageContent) 단계를 포함하는 작업 순서를 실행합니다. 이 단계는 Windows PE 피어 캐시 작업 순서에 포함된 관련 콘텐츠를 사전 준비하는 데 사용됩니다. 이 방법을 사용하는 경우의 특징은 다음과 같습니다.  

    -   클라이언트가 배포 중인 이미지를 설치할 필요가 없습니다.  

    -   작업 순서에서는 **패키지 콘텐츠 다운로드** 옵션 외에 **Configuration Manager 클라이언트 캐시** 옵션도 사용해야 합니다. 클라이언트가 다른 피어 캐시 클라이언트의 피어 캐시 원본 역할을 할 수 있도록 클라이언트 캐시에 콘텐츠를 저장하는 데 이 옵션을 사용합니다.  

 다음 절차를 통해 클라이언트에서 Windows PE 피어 캐시 및 피어 캐시를 지원하는 작업 순서를 구성할 수 있습니다.  

### <a name="to-configure-the-windows-pe-peer-cache-source-computers"></a>Windows PE 피어 캐시 원본 컴퓨터를 구성하려면  

1.  Configuration Manager 콘솔에서 **관리** > **클라이언트 설정**으로 이동하여 새 **사용자 지정 클라이언트 장치 설정**을 만들거나 기존 설정 개체를 편집합니다. **기본 클라이언트 설정** 개체에 대해서도 피어 캐시를 구성할 수 있습니다.  

    > [!TIP]  
    >  이 구성을 수신할 클라이언트를 관리하려면 사용자 지정 설정 개체를 사용합니다. 예를 들어 이동이 잦은 사용자의 노트북에서는 피어 캐시를 구성하지 않는 것이 좋습니다. 이동 시에 자주 사용하는 시스템의 경우 다른 피어 캐시 클라이언트에 콘텐츠를 제공할 수 있는 원본으로 사용하기에 적합하지 않을 수 있습니다.  
    >   
    >  또한 **기본 클라이언트 설정**의 일부분으로 이 설정을 구성할 때는 환경의 모든 클라이언트에 구성이 적용됩니다.  

2.  **Windows PE 피어 캐시**에서 **전체 OS의 Configuration Manager 클라이언트가 콘텐츠를 공유하도록 설정** 을 **예**로 설정합니다.  

    -   기본적으로는 HTTP만 사용하도록 설정됩니다. 클라이언트가 HTTPS를 통해 콘텐츠를 다운로드할 수 있도록 설정하려면 **클라이언트 피어 통신에 HTTPS 사용** 을 **예**로 설정합니다.  

    -   기본적으로 브로드캐스트용 포트는 8004로 설정되고 콘텐츠 다운로드용 포트는 8003으로 설정됩니다. 이 두 포트는 모두 변경할 수 있습니다.  

3.  피어 캐시 원본으로 선택하는 클라이언트에 클라이언트 설정을 저장하고 배포합니다.  

 이 설정 개체를 사용하여 구성한 장치는 피어 캐시 원본으로 작동하도록 구성됩니다. 필요한 포트와 프로토콜을 구성하려면 이러한 설정을 잠재적 피어 캐시 클라이언트에 배포해야 합니다.  

###  <a name="BKMK_PeerCacheConfigureTS"></a> Windows PE 피어 캐시에 대해 작업 순서 구성  
 작업 순서를 구성할 때는 다음 작업 순서 변수를 작업 순서 배포 대상 컬렉션에 대한 컬렉션 변수로 사용합니다.  

-   **SMSTSPeerDownload**  

     값: TRUE  

     클라이언트가 Windows PE 피어 캐시를 사용할 수 있도록 합니다.  

-   **SMSTSPeerRequestPort**  

     값: <포트 번호\>  

     클라이언트 설정에 구성된 기본 포트인 8004를 사용하지 않는 경우에는 초기 브로드캐스트에 사용할 네트워크 포트의 사용자 지정 값으로 이 변수를 구성해야 합니다.  

-   **SMSTSPreserveContent**  

     값: TRUE  

     이 변수는 배포 후 Configuration Manager 클라이언트 캐시에 보존할 작업 순서의 콘텐츠에 플래그를 지정합니다. 이 변수를 사용하는 것은 SMSTSPersisContent를 사용하는 것과는 다릅니다. SMSTSPersisContent는 작업 시퀀스 기간 동안만 콘텐츠를 보존하며 Configuration Manager 클라이언트 캐시가 아닌 작업 순서 캐시를 사용합니다.  

 자세한 내용은 [작업 순서 기본 제공 변수](../understand/task-sequence-built-in-variables.md)를 참조하세요.  

###  <a name="BKMK_PeerCacheValidate"></a> Windows PE 피어 캐시 정상 사용 여부 확인  
 Windows PE 피어 캐시를 사용하여 작업 순서를 배포 및 설치한 후에는 작업 순서를 실행한 클라이언트에서 **smsts.log** 를 확인하여 프로세스에서 피어 캐시를 정상적으로 사용했는지 확인할 수 있습니다.  

 이 로그에서 다음과 같은 항목을 찾습니다. 여기서 <*SourceServerName*>은 클라이언트가 콘텐츠를 가져온 컴퓨터를 식별합니다. 이 컴퓨터는 배포 지점 서버가 아닌 피어 캐시 원본이어야 합니다. 기타 세부 정보는 로컬 환경 및 구성에 따라 달라집니다.  

-   *<![LOG[Downloaded file from http:// <SourceServerName\>:8003/SCCM_BranchCache$/SS10000C/sccm?/install.wim to C:\\_SMSTaskSequence\Packages\SS10000C\install.wim ]LOG]!><time="14:24:33.329+420" date="06-26-2015" component="ApplyOperatingSystem" context="" type="1" thread="1256" file="downloadcontent.cpp:1626">*  
