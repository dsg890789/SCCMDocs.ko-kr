---
title: 컬렉션 관리
titleSuffix: Configuration Manager
description: Configuration Manager에서 일반적인 컬렉션 관리 작업을 수행합니다.
ms.date: 08/17/2018
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: e102fd1a-76df-4d8e-b1b0-10ee18318f67
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 5d7c967ce02c009cd9659c7956f7ca79f4a34faf
ms.sourcegitcommit: be8c0182db9ef55a948269fcbad7c0f34fd871eb
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/23/2018
ms.locfileid: "42755975"
---
# <a name="how-to-manage-collections-in-configuration-manager"></a>Configuration Manager에서 컬렉션을 관리하는 방법

*적용 대상: System Center Configuration Manager(현재 분기)*

이 문서의 개요 정보를 참조하여 Configuration Manager에서 컬렉션에 대한 관리 작업을 수행할 수 있습니다.  

> [!NOTE]  
>  구성 관리자 컬렉션을 만드는 방법에 대한 자세한 내용은 [컬렉션을 만드는 방법](/sccm/core/clients/manage/collections/create-collections)을 참조하세요.  



## <a name="bkmk_device"></a> 장치 컬렉션을 관리하는 방법  

 **자산 및 준수** 작업 영역에서 **장치 컬렉션**을 선택하고 관리할 컬렉션을 선택한 다음 관리 작업을 선택합니다.  


#### <a name="show-members"></a>멤버 표시
 **장치** 노드의 임시 노드에 선택한 컬렉션의 멤버인 모든 리소스를 표시합니다.


#### <a name="add-selected-items"></a>선택한 항목 추가
 다음 옵션이 제공됩니다. 

 - **선택한 항목을 기존 장치 컬렉션에 추가**: **컬렉션 선택** 대화 상자를 엽니다. 선택한 컬렉션의 구성원을 추가할 컬렉션을 선택하세요. 선택한 컬렉션이 **컬렉션 포함** 멤버 관리 규칙을 사용하여 이 컬렉션에 포함됩니다.  

 - **선택한 항목을 새 장치 컬렉션에 추가**: 새 컬렉션을 만들 수 있는 **장치 컬렉션 만들기 마법사**를 엽니다. 선택한 컬렉션이 **컬렉션 포함** 멤버 관리 규칙을 사용하여 이 컬렉션에 포함됩니다.  


 자세한 내용은 [컬렉션을 만드는 방법](/sccm/core/clients/manage/collections/create-collections)을 참조하세요.


#### <a name="install-client"></a>클라이언트를 설치 합니다.
 **클라이언트 설치 마법사**를 엽니다. 이 마법사는 클라이언트 강제 설치를 사용하여 선택한 컬렉션의 모든 컴퓨터에서 구성 관리자 클라이언트를 설치합니다. 자세한 내용은 [클라이언트 강제 설치](/sccm/core/clients/deploy/deploy-clients-to-windows-computers#BKMK_ClientPush)를 참조하세요.


#### <a name="run-script"></a>스크립트 실행
 컬렉션에 있는 모든 클라이언트에서 PowerShell 스크립트를 실행하는 **스크립트 실행** 마법사를 엽니다. 자세한 내용은 [PowerShell 스크립트 만들기 및 실행](/sccm/apps/deploy-use/create-deploy-scripts)을 참조하세요.


#### <a name="manage-affinity-requests"></a>선호도 요청 관리
 **사용자 장치 선호도 요청 관리** 대화 상자를 엽니다. 보류 중인 요청을 승인하거나 거부하여 선택한 컬렉션의 장치에 대해 사용자 장치 선호도를 설정합니다. 자세한 내용은 [사용자 장치 선호도를 사용하여 사용자와 장치 연결](/sccm/apps/deploy-use/link-users-and-devices-with-user-device-affinity)을 참조하세요.


#### <a name="clear-required-pxe-deployments"></a>필수 PXE 배포를 취소 합니다.
 선택한 컬렉션의 모든 멤버에서 필수 PXE 부팅 배포를 지웁니다. 자세한 내용은 [PXE를 사용하여 네트워크를 통해 Windows 배포](/sccm/osd/deploy-use/use-pxe-to-deploy-windows-over-the-network)를 참조하세요.


#### <a name="update-membership"></a>멤버 자격을 업데이트 합니다.
 선택한 컬렉션에 대 한 멤버 자격을 평가합니다. 멤버가 많은 컬렉션의 경우 이 업데이트를 완료하려면 다소 시간이 걸릴 수 있습니다. 업데이트가 완료된 후 **새로 고침** 작업을 사용하여 새 컬렉션 멤버로 화면 표시를 업데이트합니다.


#### <a name="add-resources"></a>리소스 추가
 **컬렉션에 리소스 추가** 대화 상자를 엽니다. 선택한 컬렉션에 추가할 새 리소스를 검색하세요. 업데이트가 진행되는 동안 선택한 컬렉션에 대한 아이콘이 모래 시계 기호를 표시합니다.


#### <a name="client-notification"></a>클라이언트 알림
 선택한 장치 컬렉션의 모든 클라이언트에게 즉시 다음 작업 중 하나를 수행하도록 지시합니다.

 - **컴퓨터 정책 다운로드**: 장치 정책을 새로 고칩니다. 자세한 내용은 [Configuration Manager 클라이언트에 대한 정책 검색 시작](/sccm/core/clients/manage/manage-clients#BKMK_PolicyRetrieval)을 참조하세요.  

 - **사용자 정책 다운로드**: 사용자 정책을 새로 고칩니다.  

 - **검색 데이터 수집**: DDR(검색 데이터 레코드)을 전송하도록 클라이언트를 트리거합니다. 자세한 내용은 [하트비트 검색](/sccm/core/servers/deploy/configure/about-discovery-methods#bkmk_aboutHeartbeat)을 참조하세요.  

 - **소프트웨어 인벤토리 수집**: 소프트웨어 인벤토리 주기를 실행하도록 클라이언트를 트리거합니다. 자세한 내용은 [소프트웨어 인벤토리 소개](/sccm/core/clients/manage/inventory/introduction-to-software-inventory)를 참조하세요.  

 - **하드웨어 인벤토리 수집**: 하드웨어 인벤토리 주기를 실행하도록 클라이언트를 트리거합니다. 자세한 내용은 [하드웨어 인벤토리 소개](/sccm/core/clients/manage/inventory/introduction-to-hardware-inventory)를 참조하세요.  

 - **응용 프로그램 배포 평가**: 응용 프로그램 배포 평가 주기를 실행하도록 클라이언트를 트리거합니다. 자세한 내용은 [배포의 재평가 일정](/sccm/core/clients/deploy/about-client-settings#schedule-re-evaluation-for-deployments)을 참조하세요.  

 - **소프트웨어 업데이트 배포 평가**: 소프트웨어 업데이트 배포 평가 주기를 실행하도록 클라이언트를 트리거합니다. 자세한 내용은 [소프트웨어 업데이트 소개](/sccm/sum/understand/software-updates-introduction)를 참조하세요.  

 - **다음 소프트웨어 업데이트 지점으로 전환**: 다음 사용 가능한 소프트웨어 업데이트 지점으로 전환하도록 클라이언트를 트리거합니다. 자세한 내용은 [소프트웨어 업데이트 지점 전환](/sccm/sum/plan-design/plan-for-software-updates#BKMK_SUPSwitching)을 참조하세요.  

 - **디바이스 상태 증명 평가**: 최신 장치 성능 상태를 확인하고 보내도록 Windows 10 클라이언트를 트리거합니다. 자세한 내용은 [상태 증명](/sccm/core/servers/manage/health-attestation)을 참조하세요.  

 - **조건부 액세스 준수 확인**: 조건부 액세스 준수를 확인하도록 클라이언트를 트리거합니다. 자세한 내용은 [PC용 O365 서비스에 대한 액세스 관리](/sccm/mdm/deploy-use/manage-access-to-o365-services-for-pcs-managed-by-sccm)를 참조하세요.  


#### <a name="endpoint-protection"></a>Endpoint Protection
 선택한 장치 컬렉션의 모든 클라이언트에게 즉시 다음 작업 중 하나를 수행하도록 지시합니다.

 - **전체 검사**: *전체* 맬웨어 방지 검사를 실행하도록 Endpoint Protection 또는 Windows Defender를 트리거합니다.  

 - **빠른 검사**: *빠른* 맬웨어 방지 검사를 실행하도록 Endpoint Protection 또는 Windows Defender를 트리거합니다.  

 - **정의 다운로드**: 최신 맬웨어 방지 정의를 다운로드하도록 Endpoint Protection 또는 Windows Defender를 트리거합니다.  


 자세한 내용은 [Configuration Manager의 Endpoint Protection](/sccm/protect/deploy-use/endpoint-protection)을 참조하세요.


#### <a name="export"></a>내보내기
 MOF(Managed Object Format) 파일에 이 컬렉션을 내보낼 수 있는 **컬렉션 내보내기 마법사**를 엽니다. 그런 다음 이 파일을 다른 Configuration Manager 사이트에서 보관하거나 가져올 수 있습니다. 컬렉션을 내보낼 때 참조된 컬렉션은 내보내지지 않습니다. 참조된 컬렉션은 **포함** 또는 **제외** 규칙을 사용하여 선택된 컬렉션이 참조합니다.


#### <a name="copy"></a>복사
 선택한 컬렉션의 복사본을 만듭니다. 새 컬렉션은 선택한 컬렉션을 제한 컬렉션으로 사용합니다.


#### <a name="refresh"></a>새로 고침
 보기를 새로 고칩니다.


#### <a name="delete"></a>삭제
 선택한 컬렉션을 삭제 합니다. 사이트 데이터베이스에서 컬렉션의 모든 리소스를 삭제할 수도 있습니다. 

 Configuration Manager에 기본 제공된 컬렉션을 삭제할 수 없습니다. 기본 제공 컬렉션 목록이 필요하면 [컬렉션 소개](/sccm/core/clients/manage/collections/introduction-to-collections#built-in-collections)를 참조하세요.


#### <a name="simulate-deployment"></a>배포 시뮬레이트
 **응용 프로그램 배포 시뮬레이트 마법사**를 엽니다. 이 마법사를 통해 응용 프로그램을 설치하거나 제거하지 않고도 응용 프로그램 배포 결과를 테스트할 수 있습니다. 자세한 내용은 [응용 프로그램 배포 시뮬레이트](/sccm/apps/deploy-use/simulate-application-deployments)를 참조하세요.


#### <a name="deploy"></a>배포:
 다음 옵션이 표시됩니다.  

 - **응용 프로그램**: **소프트웨어 배포 마법사**를 엽니다. 선택한 컬렉션에 대한 응용 프로그램 배포를 선택하고 구성하세요. 자세한 내용은 [응용 프로그램 배포](/sccm/apps/deploy-use/deploy-applications)를 참조하세요.  

 - **프로그램**: **소프트웨어 배포 마법사**를 엽니다. 선택한 컬렉션에 대한 패키지 및 프로그램 배포를 선택하고 구성하세요. 자세한 내용은 [패키지 및 프로그램](/sccm/apps/deploy-use/packages-and-programs)을 참조하세요.  

 - **구성 기준**: **구성 기준 배포** 대화 상자를 엽니다. 선택한 컬렉션에 대한 하나 이상의 구성 기준 배포를 구성하세요. 자세한 내용은 [구성 기준 배포 방법](/sccm/compliance/deploy-use/deploy-configuration-baselines)을 참조하세요.  

 - **작업 순서**: **소프트웨어 배포 마법사**를 엽니다. 선택한 컬렉션에 대한 작업 순서 배포를 선택하고 구성하세요. 자세한 내용은 [작업을 자동화하는 작업 순서 관리](/sccm/osd/deploy-use/manage-task-sequences-to-automate-tasks#BKMK_DeployTS)를 참조하세요.  

 - **소프트웨어 업데이트**: **소프트웨어 업데이트 배포 마법사**를 엽니다. 선택한 컬렉션의 리소스에 대해 소프트웨어 업데이트 배포를 구성하세요. 자세한 내용은 [소프트웨어 업데이트 관리](/sccm/sum/understand/software-updates-introduction)를 참조하세요.  


#### <a name="clear-server-group-deployment-locks"></a>서버 그룹 배포 잠금 제거
 컬렉션에 대한 모든 서버 그룹 배포 잠금을 수동으로 해제합니다. 자세한 내용은 [서버 그룹 제공](/sccm/sum/deploy-use/service-a-server-group)을 참조하세요.


#### <a name="move"></a>이동
 선택한 컬렉션을 **장치 컬렉션** 노드에 있는 다른 폴더로 이동합니다. 


#### <a name="properties"></a>속성
 자세한 내용은 [컬렉션 속성](#BKMK_CollProp)을 참조하세요.  



## <a name="bkmk_user"></a> 사용자 컬렉션을 관리하는 방법  

 **자산 및 준수** 작업 영역에서 **사용자 컬렉션**을 선택하고 관리할 컬렉션을 선택한 다음 관리 작업을 선택합니다.  

 > [!Note]  
 > 다음 작업은 사용자 컬렉션에서 사용할 수 있지만 동작은 장치 컬렉션에서와 동일합니다. 사용자 컬렉션과 그 안에 있는 사용자에 적용된다는 점만 다릅니다. 자세한 내용은 [장치 컬렉션을 관리하는 방법](#bkmk_device) 아래에서 해당 작업을 참조하세요.  

 - **멤버 표시**  
 - **선택한 항목 추가**  
     - **선택한 항목을 기존 사용자 컬렉션에 추가**  
     - **선택한 항목을 새 사용자 컬렉션에 추가**  
 - **선호도 요청 관리**  
 - **멤버 자격 업데이트**  
 - **리소스 추가**  
 - **내보내기**  
 - **복사**  
 - **새로 고침**  
 - **삭제**  
 - **배포 시뮬레이트**  
 - **배포**  
     - **응용 프로그램**  
     - **프로그램**  
     - **구성 기준**   
 - **이동**  
 - **데이터 액세스**



##  <a name="BKMK_CollProp"></a> 컬렉션 속성  

 컬렉션에 대한 **속성** 대화 상자를 열면 다음 옵션을 보고 구성할 수 있습니다.  

#### <a name="general"></a>일반
 컬렉션 이름 및 제한 컬렉션을 비롯한 선택한 컬렉션에 대한 일반 정보를 보고 구성합니다.

#### <a name="membership-rules"></a>멤버 자격 규칙
 이 컬렉션의 멤버 자격을 정의 하는 멤버 자격 규칙을 구성합니다. 자세한 내용은 [컬렉션을 만드는 방법](/sccm/core/clients/manage/collections/create-collections)을 참조하세요.  

#### <a name="power-management"></a>전원 관리
 선택한 컬렉션에 있는 컴퓨터에 할당 되는 전원 관리 옵션을 구성합니다. 자세한 내용은 [전원 관리 소개](/sccm/core/clients/manage/power/introduction-to-power-management)를 참조하세요.  

#### <a name="deployments"></a>배포
 선택한 컬렉션의 구성원에게 배포한 모든 소프트웨어를 표시합니다.  

#### <a name="maintenance-windows"></a>유지 관리 기간
 선택한 컬렉션의 구성원에게 적용되는 유지 관리 기간을 보고 구성합니다. 자세한 내용은 [유지 관리 기간을 사용하는 방법](/sccm/core/clients/manage/collections/use-maintenance-windows)을 참조하세요.

#### <a name="collection-variables"></a>컬렉션 변수
 이 컬렉션에 적용 하 고 작업 순서에서 사용할 수 있도록 변수를 구성합니다. 자세한 내용은 [How to set task sequence variables](/sccm/osd/understand/using-task-sequence-variables#bkmk_set)\(작업 순서 변수 설정 방법\)를 참조하세요.  

#### <a name="distribution-point-groups"></a>배포 지점 그룹
 선택한 컬렉션의 구성원에게 게 하나 이상의 배포 지점 그룹을 연결합니다. 자세한 내용은 [콘텐츠 및 콘텐츠 인프라 관리](/sccm/core/servers/deploy/configure/manage-content-and-content-infrastructure)를 참조하세요.

#### <a name="security"></a>보안
 연결된 역할 및 보안 범위에서 선택한 컬렉션에 대한 권한이 있는 관리자를 표시합니다. 자세한 내용은 [역할 기반 관리의 기본 사항](/sccm/core/understand/fundamentals-of-role-based-administration)을 참조하세요.  

#### <a name="alerts"></a>경고 
 클라이언트 상태와 Endpoint Protection에 대해 경고가 생성되는 때를 구성합니다. 자세한 내용은 [클라이언트 상태를 구성하는 방법](/sccm/core/clients/deploy/configure-client-status) 및 [Endpoint Protection 상태를 모니터링하는 방법](/sccm/protect/deploy-use/monitor-endpoint-protection)을 참조하세요.  
