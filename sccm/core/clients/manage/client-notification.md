---
title: 클라이언트 알림
titleSuffix: Configuration Manager
description: 중앙 Configuration Manager 콘솔에서 즉각적인 작업을 수행하여 클라이언트를 관리합니다.
ms.date: 11/27/2018
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: deb8aac8-2bd9-4980-a25b-5f8d93051226
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: f190522300090247cdca0affa9d993fe46201668
ms.sourcegitcommit: 874d78f08714a509f61c52b154387268f5b73242
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56122035"
---
# <a name="client-notification-in-configuration-manager"></a>Configuration Manager의 클라이언트 알림

*적용 대상: System Center Configuration Manager(현재 분기)*

원격 클라이언트에 대해 즉각적인 작업을 수행하려면 Configuration Manager 콘솔에서 클라이언트 알림 작업을 보냅니다. 개별 장치 또는 장치 컬렉션에 대해 이러한 작업을 시작합니다. 



## <a name="actions"></a>작업

다음 작업은 홈 탭의 장치 또는 컬렉션 그룹의 리본에 있습니다. 


### <a name="install-client"></a>클라이언트 설치

**클라이언트 설치 마법사**를 엽니다. 이 마법사는 클라이언트 강제 설치를 사용하여 Configuration Manager 클라이언트를 설치합니다. 자세한 내용은 [클라이언트 강제 설치](/sccm/core/clients/deploy/deploy-clients-to-windows-computers#BKMK_ClientPush)를 참조하세요.

#### <a name="permissions"></a>사용 권한
이 작업에는 **컬렉션** 개체에 대한 **리소스 수정** 및 **읽기** 권한이 필요합니다. 

다음 기본 제공 역할은 기본적으로 이 권한을 가집니다.
- 애플리케이션 관리자  
- 전체 관리자  
- 인프라 관리자  
- 운영 관리자  
- OS 배포 관리자  

클라이언트를 푸시해야 하는 모든 사용자 지정 역할에 이 권한을 추가합니다.


### <a name="run-script"></a>스크립트 실행

컬렉션에 있는 모든 클라이언트에서 PowerShell 스크립트를 실행하는 **스크립트 실행** 마법사를 엽니다. 자세한 내용은 [PowerShell 스크립트 만들기 및 실행](/sccm/apps/deploy-use/create-deploy-scripts)을 참조하세요.

#### <a name="permissions"></a>사용 권한
이 작업에는 **컬렉션** 개체에 대한 **스크립트 실행** 권한이 필요합니다. 

다음 기본 제공 역할은 기본적으로 이 권한을 갖습니다.
- 전체 관리자  
- 인프라 관리자  
- 운영 관리자  

스크립트 실행이 필요한 모든 사용자 지정 역할에 이 권한을 추가합니다.


### <a name="start-cmpivot"></a>CMPivot 시작

대상 장치에 대해 실시간 쿼리를 실행하는 **CMPivot**을 시작합니다. 자세한 내용은 [CMPivot](/sccm/core/servers/manage/cmpivot)을 참조하세요.

#### <a name="permissions"></a>사용 권한
이 작업에는 [스크립트 실행](#run-script) 작업과 동일한 권한이 필요합니다. 



## <a name="client-notification"></a>클라이언트 알림

이 작업은 홈 탭의 장치 또는 컬렉션 그룹에서 리본의 **클라이언트 알림** 메뉴에 있습니다.


#### <a name="permissions"></a>사용 권한
<!--SCCMDocs-pr issue #2972--> 1810 버전부터 클라이언트 알림 작업에서 컬렉션 개체에 대해 **리소스 알림** 권한이 필요합니다. 이 권한은 **클라이언트 알림** 메뉴의 모든 작업에 적용됩니다. 

다음 기본 제공 역할은 기본적으로 이 권한을 갖습니다.
- 전체 관리자  
- 인프라 관리자  

클라이언트 알림 작업이 필요한 모든 사용자 지정 역할에 이 권한을 추가합니다.


### <a name="download-computer-policy"></a>컴퓨터 정책 다운로드

장치 정책을 새로 고칩니다. 자세한 내용은 [Configuration Manager 클라이언트에 대한 정책 검색 시작](/sccm/core/clients/manage/manage-clients#BKMK_PolicyRetrieval)을 참조하세요.  


### <a name="download-user-policy"></a>사용자 정책 다운로드

사용자 정책을 새로 고칩니다.  


### <a name="collect-discovery-data"></a>검색 데이터 수집

DDR(검색 데이터 레코드)을 전송하도록 클라이언트를 트리거합니다. 자세한 내용은 [하트비트 검색](/sccm/core/servers/deploy/configure/about-discovery-methods#bkmk_aboutHeartbeat)을 참조하세요.  


### <a name="collect-software-inventory"></a>소프트웨어 인벤토리 수집

소프트웨어 인벤토리 주기를 실행하도록 클라이언트를 트리거합니다. 자세한 내용은 [소프트웨어 인벤토리 소개](/sccm/core/clients/manage/inventory/introduction-to-software-inventory)를 참조하세요.  


### <a name="collect-hardware-inventory"></a>하드웨어 인벤토리 수집

하드웨어 인벤토리 주기를 실행하도록 클라이언트를 트리거합니다. 자세한 내용은 [하드웨어 인벤토리 소개](/sccm/core/clients/manage/inventory/introduction-to-hardware-inventory)를 참조하세요.  


### <a name="evaluate-application-deployments"></a>애플리케이션 배포 평가

애플리케이션 배포 평가 주기를 실행하도록 클라이언트를 트리거합니다. 자세한 내용은 [배포의 재평가 일정](/sccm/core/clients/deploy/about-client-settings#schedule-re-evaluation-for-deployments)을 참조하세요.  


### <a name="evaluate-software-update-deployments"></a>소프트웨어 업데이트 배포 평가

소프트웨어 업데이트 배포 평가 주기를 실행하도록 클라이언트를 트리거합니다. 자세한 내용은 [소프트웨어 업데이트 소개](/sccm/sum/understand/software-updates-introduction)를 참조하세요.  


### <a name="switch-to-the-next-software-update-point"></a>다음 소프트웨어 업데이트 지점으로 전환

다음 사용 가능한 소프트웨어 업데이트 지점으로 전환하도록 클라이언트를 트리거합니다. 자세한 내용은 [소프트웨어 업데이트 지점 전환](/sccm/sum/plan-design/plan-for-software-updates#BKMK_SUPSwitching)을 참조하세요.  


### <a name="evaluate-device-health-attestation"></a>디바이스 상태 증명 평가

최신 장치 성능 상태를 확인하고 보내도록 Windows 10 클라이언트를 트리거합니다. 자세한 내용은 [상태 증명](/sccm/core/servers/manage/health-attestation)을 참조하세요.  


### <a name="check-conditional-access-compliance"></a>조건부 액세스 규정 준수 확인

조건부 액세스 규정 준수를 확인하도록 클라이언트를 트리거합니다. 자세한 내용은 [PC용 O365 서비스에 대한 액세스 관리](/sccm/mdm/deploy-use/manage-access-to-o365-services-for-pcs-managed-by-sccm)를 참조하세요.  


### <a name="wake-up"></a>절전 모드 해제

1810 버전부터 일시 중지된 장치를 완전 전원 모드로 복귀하도록 트리거합니다.


### <a name="restart"></a>다시 시작

선택한 장치를 다시 시작하도록 트리거합니다. 



## <a name="endpoint-protection"></a>Endpoint Protection

다음 작업은 **Endpoint Protection** 메뉴에 있습니다. 이 메뉴는 홈 탭의 컬렉션 그룹에 있는 리본에 있습니다. 하나 이상의 장치를 선택하면 이러한 작업이 리본의 **선택한 개체** 탭에 표시됩니다.

자세한 내용은 [Configuration Manager의 Endpoint Protection](/sccm/protect/deploy-use/endpoint-protection)을 참조하세요.

#### <a name="permissions"></a>사용 권한
이 작업에는 **컬렉션** 개체에 대한 **보안 적용** 권한이 필요합니다. 

다음 기본 제공 역할은 기본적으로 이 권한을 갖습니다.
- 전체 관리자  
- Endpoint Protection Manager  
- 운영 관리자  

Endpoint Protection 작업을 트리거해야 하는 모든 사용자 지정 역할에 이 권한을 추가합니다.


### <a name="full-scan"></a>전체 검사

Endpoint Protection 또는 Windows Defender가 *전체* 맬웨어 방지 검사를 실행하도록 트리거합니다.  


### <a name="quick-scan"></a>빠른 검사

*빠른* 맬웨어 방지 검사를 실행하도록 Endpoint Protection 또는 Windows Defender를 트리거합니다.  


### <a name="download-definition"></a>정의 다운로드

최신 맬웨어 방지 정의를 다운로드하도록 Endpoint Protection 또는 Windows Defender를 트리거합니다.  



## <a name="see-also"></a>참고 항목

- [클라이언트를 관리하는 방법](/sccm/core/clients/manage/manage-clients)
- [컬렉션을 관리하는 방법](/sccm/core/clients/manage/collections/manage-collections)
