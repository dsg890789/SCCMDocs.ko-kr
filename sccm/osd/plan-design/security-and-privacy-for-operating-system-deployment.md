---
title: OS 배포를 위한 보안 및 개인정보
titleSuffix: Configuration Manager
description: Configuration Manager에서 OS 배포의 보안 및 개인 정보 보호 모범 사례에 대해 알아봅니다.
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.technology: configmgr-osd
ms.topic: conceptual
ms.assetid: 5ee5928f-3d72-4b00-8156-1e0d1030a96c
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4b37bcf8fc1079ff1eaaa3d70cb3c1c8297a2685
ms.sourcegitcommit: 79c51028f90b6966d6669588f25e8233cf06eb61
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 07/19/2019
ms.locfileid: "68340373"
---
# <a name="security-and-privacy-for-os-deployment-in-configuration-manager"></a>Configuration Manager에서 OS 배포의 보안 및 개인 정보 보호

*적용 대상: System Center Configuration Manager(현재 분기)*

이 문서에는 Configuration Manager의 OS 배포 기능에 대한 보안 및 개인 정보 보호 관련 정보가 포함되어 있습니다.  



##  <a name="bkmk_security"></a> OS 배포에 대한 보안 모범 사례  

Configuration Manager를 사용하여 운영 체제를 배포할 때 따라야 할 보안 모범 사례는 다음과 같습니다.  


### <a name="implement-access-controls-to-protect-bootable-media"></a>부팅 가능한 미디어를 보호하기 위해 액세스 제어 구현

부팅 가능한 미디어를 만들 때에는 미디어 보안을 위해 항상 암호를 지정합니다. 암호를 지정하더라도 중요한 정보가 포함된 파일만 암호화되므로 모든 파일을 덮어쓸 수 있습니다.  

공격자가 암호화 공격을 사용하여 클라이언트 인증 인증서를 얻지 못하도록 미디어에 대한 실제 액세스를 제어합니다.  

클라이언트에서 변조된 콘텐츠 또는 클라이언트 정책을 설치하지 못하도록 콘텐츠가 해시되고 원래 정책과 함께 사용되어야 합니다. 콘텐츠 해시가 실패하거나 콘텐츠가 정책과 일치하는지 확인하는 경우 클라이언트는 부팅 가능한 미디어를 사용하지 않습니다. 콘텐츠만 해시됩니다. 정책은 해시되지 않지만 암호를 지정할 때 암호화되고 보호됩니다. 이 동작은 공격자가 정책을 손쉽게 수정하지 못하게 합니다.  


### <a name="use-a-secure-location-when-you-create-media-for-os-images"></a>OS 이미지용 미디어를 만들 때 보안 위치 사용

권한이 없는 사용자가 보안 위치에 액세스할 수 있는 경우 사용자가 만든 파일을 변조할 수 있습니다. 또한 사용 가능한 모든 디스크 공간을 사용하여 미디어를 만들지 못할 수 있습니다.  


### <a name="protect-certificate-files"></a>인증서 파일 보호 

강력한 암호로 인증서 파일(.pfx)을 보호합니다. 네트워크에 저장하는 경우 Configuration Manager로 가져올 때 네트워크 채널 보호

부팅 가능한 미디어에 사용하는 클라이언트 인증 인증서를 가져오는 데 암호가 필요한 경우, 이 구성은 공격자로부터 인증서를 보호하는 데 도움이 됩니다.  

공격자가 인증서 파일을 변조하지 못하도록 네트워크 위치와 사이트 서버 사이에 SMB 서명 또는 IPsec을 사용합니다.  


### <a name="block-or-revoke-any-compromised-certificates"></a>손상된 인증서 차단 또는 해지 

클라이언트 인증서가 손상된 경우 Configuration Manager에서 인증서를 차단합니다. PKI 인증서라면 해지합니다.  

부팅 가능한 미디어 및 PXE 부팅을 사용하여 OS를 배포하려면 프라이빗 키와 함께 클라이언트 인증 인증서를 사용해야 합니다. 인증서가 손상될 경우 **관리** 작업 영역, **보안** 노드의 **인증서** 노드에서 해당 인증서를 차단합니다.  


### <a name="secure-the-communication-channel-between-the-site-server-and-the-sms-provider"></a>사이트 서버와 SMS 공급자 간 통신 채널 보호

SMS 공급자가 사이트 서버에서 원격 위치에 있는 경우 통신 채널의 보안을 유지하여 부팅 이미지를 보호합니다.

부팅 이미지를 수정하면 SMS 공급자가 사이트 서버가 아닌 서버에서 실행 중인 경우 부팅 이미지가 공격에 취약해집니다. SMB 서명 또는 IPsec을 사용하여 이러한 컴퓨터 간의 네트워크 채널을 보호해야 합니다.  


### <a name="enable-distribution-points-for-pxe-client-communication-only-on-secure-network-segments"></a>보안 네트워크 세그먼트에서만 배포 지점의 PXE 클라이언트 통신을 사용하도록 설정

클라이언트가 PXE 부팅 요청을 보내는 경우 요청이 유효한 PXE 지원 배포 지점에서 서비스되는지 확인할 방법이 없습니다. 이 시나리오에는 다음과 같은 보안 위험이 있습니다.  

- PXE 요청에 응답하는 Rogue 배포 지점에서 변조된 이미지를 클라이언트에 제공할 수 있습니다.  

- 공격자는 PXE에서 사용하는 TFTP 프로토콜에 대해 중간자 개입 공격을 시작할 수 있습니다. 이 공격은 OS 파일과 함께 악성 코드를 보낼 수 있습니다. 공격자는 악성 클라이언트를 생성하여 TFTP 요청을 배포 지점으로 직접 보낼 수도 있습니다.  

- 공격자는 악성 클라이언트를 사용하여 배포 지점에 대한 서비스 거부 공격을 시작할 수 있습니다.  

심층 방어를 사용하여 클라이언트가 PXE 지원 배포 지점에 액세스하는 네트워크 세그먼트를 보호합니다.  

> [!WARNING]  
>  이러한 보안 위험 때문에 경계 네트워크와 같은 신뢰할 수 없는 네트워크에서는 PXE 통신에 배포 지점을 사용하지 않도록 설정해야 합니다.  


### <a name="configure-pxe-enabled-distribution-points-to-respond-to-pxe-requests-only-on-specified-network-interfaces"></a>PXE 사용 배포 지점이 지정된 네트워크 인터페이스에서만 PXE 요청에 응답하도록 구성  

배포 지점이 모든 네트워크에서 PXE 요청에 응답하도록 허용할 경우 PXE 서비스가 신뢰할 수 없는 네트워크에 노출될 수 있습니다.  


### <a name="require-a-password-to-pxe-boot"></a>PXE 부팅 시 암호 요구

PXE 부팅에 암호가 필요한 경우 이 구성은 PXE 부팅 프로세스에 대한 보안 수준을 강화합니다. 이 구성은 악성 클라이언트가 Configuration Manager 계층 구조에 조인하지 못하도록 합니다.  


### <a name="restrict-content-in-os-images-used-for-pxe-boot-or-multicast"></a>PXE 부팅 또는 멀티캐스트에 사용되는 OS 이미지의 콘텐츠 제한

PXE 부팅 또는 멀티캐스트에 사용하는 이미지에 중요한 데이터가 들어 있는 LOB(기간 업무) 애플리케이션 또는 소프트웨어를 포함하지 마세요.  

PXE 부팅 및 멀티캐스트와 관련된 고유한 보안 위험 때문에 악성 컴퓨터가 OS 이미지를 다운로드할 경우의 위험을 줄여야 합니다.  


### <a name="restrict-content-installed-by-task-sequence-variables"></a>작업 순서 변수로 설치된 콘텐츠 제한

작업 순서 변수를 사용하여 설치된 애플리케이션 패키지에 중요한 데이터가 들어 있는 LOB(기간 업무) 애플리케이션 또는 소프트웨어를 포함하지 마세요.  

작업 순서 변수를 사용하여 소프트웨어를 배포하면 컴퓨터 및 해당 소프트웨어를 받을 권한이 없는 사용자에게 설치될 수 있습니다.  


### <a name="secure-the-network-channel-when-migrating-user-state"></a>사용자 상태를 마이그레이션할 때 네트워크 채널 보호

사용자 상태를 마이그레이션하는 경우 SMB 서명 또는 IPsec을 사용하여 클라이언트와 상태 마이그레이션 지점 간 네트워크 채널을 보호합니다.  

HTTP를 통한 초기 연결 후에 사용자 상태 마이그레이션 데이터는 SMB를 사용하여 전송됩니다. 네트워크 채널의 보안을 유지하지 않을 경우 공격자가 이 데이터를 읽고 수정할 수 있습니다.  


### <a name="use-the-latest-version-of-usmt"></a>최신 버전의 USMT 사용

Configuration Manager를 지원하는 USMT(사용자 환경 마이그레이션 도구)의 최신 버전을 사용합니다.  

최신 버전의 USMT는 사용자 상태 데이터를 마이그레이션할 때 더욱 강력한 보안과 제어력을 제공합니다.  


### <a name="manually-delete-folders-on-state-migration-points-when-you-decommission-them"></a>서비스 해제 시 상태 마이그레이션 지점의 폴더를 수동으로 삭제  

Configuration Manager 콘솔의 상태 마이그레이션 지점 속성에서 상태 마이그레이션 지점 폴더를 제거해도 사이트에서 실제 폴더가 삭제되지 않습니다. 사용자 상태 마이그레이션 데이터의 정보 공개를 방지하려면 수동으로 네트워크 공유를 제거하고 해당 폴더를 삭제합니다.  


### <a name="dont-configure-the-deletion-policy-to-immediately-delete-user-state"></a>사용자 상태를 즉시 삭제하도록 삭제 정책을 구성하지 않음  

상태 마이그레이션 지점에 대한 삭제 정책을 구성하여 삭제 표시된 데이터를 즉시 제거하고 공격자가 유효한 컴퓨터보다 먼저 사용자 상태 데이터를 검색할 경우 사이트에서 사용자 상태 데이터를 즉시 삭제합니다. **다음 시간 이후에 삭제** 간격을 충분히 길게 설정하여 사용자 상태 데이터가 성공적으로 복원되었는지 확인합니다.  


### <a name="manually-delete-computer-associations"></a>컴퓨터 연결을 수동으로 삭제 

사용자 상태 마이그레이션 데이터 복원이 완료되고 확인되면 컴퓨터 연결을 수동으로 삭제합니다.

Configuration Manager에서는 컴퓨터 연결을 자동으로 제거하지 않습니다. 더 이상 필요하지 않은 컴퓨터 연결을 수동으로 삭제하여 사용자 상태 데이터의 ID를 보호합니다.  


### <a name="manually-back-up-the-user-state-migration-data-on-the-state-migration-point"></a>상태 마이그레이션 지점에서 사용자 상태 마이그레이션 데이터를 수동으로 백업  

Configuration Manager 백업은 사용자 상태 마이그레이션 데이터를 사이트 백업에 포함하지 않습니다.  


### <a name="implement-access-controls-to-protect-the-prestaged-media"></a>미리 준비된 미디어를 보호하기 위해 액세스 제어 구현  

공격자가 암호화 공격을 사용하여 클라이언트 인증 인증서와 중요한 데이터를 얻지 못하도록 미디어에 대한 실제 액세스를 제어합니다.  


### <a name="implement-access-controls-to-protect-the-reference-computer-imaging-process"></a>참조 컴퓨터 이미징 프로세스를 보호하기 위해 액세스 제어 구현  

OS 이미지를 캡처하는 데 사용하는 참조 컴퓨터가 보안 환경에 있는지 확인합니다. 예상치 못한 소프트웨어나 악성 소프트웨어가 설치되어 캡처된 이미지에 실수로 포함되지 않도록 적절한 액세스 제어를 사용합니다. 이미지를 캡처하는 경우 대상 네트워크 위치가 안전한지 확인합니다. 이 프로세스는 이미지를 캡처한 후 이미지가 변조되지 않도록 하는 데 도움이 됩니다.  


### <a name="always-install-the-most-recent-security-updates-on-the-reference-computer"></a>참조 컴퓨터에 항상 최신 보안 업데이트 설치  

참조 컴퓨터에 최신 보안 업데이트가 있으면 새 컴퓨터가 처음 시작될 때 보안상 취약한 기간이 줄어듭니다.  


### <a name="implement-access-controls-when-deploying-an-os-to-an-unknown-computer"></a>알 수 없는 컴퓨터에 OS를 배포하는 경우 액세스 제어 구현

알 수 없는 컴퓨터에 OS를 배포해야 하는 경우 권한 없는 컴퓨터가 네트워크에 연결할 수 없도록 액세스 제어를 구현합니다.  

알 수 없는 컴퓨터를 프로비저닝하면 필요에 따라 새 컴퓨터를 배포할 수 있어 편리합니다. 하지만 이러한 컴퓨터는 공격자를 네트워크에서 신뢰할 수 있는 클라이언트로 허용할 수도 있습니다. 네트워크에 대한 실제 액세스를 제한하고 클라이언트를 모니터링하여 권한이 없는 컴퓨터를 감지해야 합니다. 

PXE 시작 OS 배포에 응답하는 컴퓨터는 프로세스 중에 모든 데이터가 삭제될 수 있습니다. 이 동작으로 인해 실수로 다시 포맷된 시스템의 가용성이 저하될 수 있습니다.  


### <a name="enable-encryption-for-multicast-packages"></a>멀티캐스트 패키지에 암호화 사용  

모든 OS 배포 패키지에서 Configuration Manager가 멀티캐스트를 사용하여 패키지를 전송할 때 암호화를 사용하도록 설정할 수 있습니다. 이 구성은 악성 컴퓨터가 멀티캐스트 세션에 조인하는 것을 방지하는 데 도움이 됩니다. 또한 공격자가 전송을 변조하지 못하도록 방지합니다.  


### <a name="monitor-for-unauthorized-multicast-enabled-distribution-points"></a>권한이 없는 멀티캐스트를 사용하는 배포 지점에 대한 모니터링  

공격자가 네트워크에 액세스할 수 있는 경우 악성 멀티캐스트 서버를 구성하여 OS 배포를 스푸핑할 수 있습니다.  


### <a name="when-you-export-task-sequences-to-a-network-location-secure-the-location-and-secure-the-network-channel"></a>작업 순서를 네트워크 위치로 내보내는 경우 해당 위치와 네트워크 채널의 보안을 유지해야 합니다.

네트워크 폴더에 액세스할 수 있는 사용자를 제한합니다.  

공격자가 내보내는 작업 순서를 변조하지 못하도록 네트워크 위치와 사이트 서버 사이에 SMB 서명 또는 IPsec을 사용합니다.  


### <a name="if-you-use-the-task-sequence-run-as-account-take-additional-security-precautions"></a>작업 순서 실행 계정을 사용하는 경우 추가 보안 예방 조치를 수행하세요.

[작업 순서 실행 계정](/sccm/core/plan-design/hierarchy/accounts#task-sequence-run-as-account)을 사용하는 경우 다음 예방 조치 단계를 수행합니다.  

- 계정 권한을 최소한으로 사용합니다.  

- 이 계정에 네트워크 액세스 계정을 사용하지 마세요.  

- 계정을 도메인 관리자 계정으로 만들면 안 됩니다.  

- 이 계정에 대해 로밍 프로필을 구성해서는 안 됩니다. 작업 순서가 실행될 때 계정의 로밍 프로필이 다운로드되어 프로필이 로컬 컴퓨터의 액세스에 취약한 상태가 됩니다.  

- 계정 범위를 제한해야 합니다. 예를 들어 작업 순서별로 다른 작업 순서 계정을 만듭니다. 이 경우 하나의 계정이 손상되면 해당 계정에 액세스할 수 있는 클라이언트 컴퓨터만 손상됩니다. 명령줄에 컴퓨터에 대한 관리 액세스 권한이 필요한 경우 작업 순서 실행 계정 전용의 로컬 관리자 계정을 만드는 것이 좋습니다. 작업 순서를 실행하는 모든 컴퓨터에 이 로컬 계정을 만들고 더 이상 필요 없는 계정을 즉시 삭제합니다.  


### <a name="restrict-and-monitor-the-administrative-users-who-are-granted-the-os-deployment-manager-security-role"></a>OS 배포 관리자 보안 역할이 부여된 관리자 제한 및 모니터링

**OS 배포 관리자** 보안 역할이 부여된 관리자는 자체 서명된 인증서를 만들 수 있습니다. 그런 다음, 이러한 인증서를 사용하여 클라이언트를 가장하고 Configuration Manager에서 클라이언트 정책을 가져올 수 있습니다.  


### <a name="use-enhanced-http-to-reduce-the-need-for-a-network-access-account"></a>네트워크 액세스 계정이 필요 없는 고급 HTTP 사용

버전 1806부터 몇몇 OS 배포 시나리오에서 [고급 HTTP](/sccm/core/plan-design/hierarchy/enhanced-http)를 사용하면 특정 배포 지점에서 콘텐츠를 다운로드할 때 네트워크 액세스 계정이 필요하지 않습니다. 자세한 내용은 [작업 순서 및 네트워크 액세스 계정](/sccm/osd/plan-design/planning-considerations-for-automating-tasks#BKMK_TSNetworkAccessAccount)을 참조하세요.<!--1358278--> 



## <a name="security-issues-for-os-deployment"></a>OS 배포의 보안 문제  

OS 배포는 네트워크에 있는 컴퓨터에 가장 안전한 운영 체제와 구성을 배포하는 편리한 방법이지만 다음과 같은 보안 위험이 있습니다.  


### <a name="information-disclosure-and-denial-of-service"></a>정보 공개 및 서비스 거부  

공격자가 Configuration Manager 인프라를 제어할 수 있는 경우에는 모든 작업 순서를 실행할 수 있습니다. 이 프로세스에는 모든 클라이언트 컴퓨터의 하드 드라이브 포맷이 포함될 수 있습니다. 작업 순서는 도메인 및 볼륨 라이선스 키에 연결할 수 있는 권한을 가진 계정과 같은 중요한 정보를 포함하도록 구성될 수 있습니다.  


### <a name="impersonation-and-elevation-of-privileges"></a>가장 및 권한 승격  

작업 순서는 컴퓨터를 도메인에 연결할 수 있으므로 Rogue 컴퓨터가 인증된 네트워크 액세스를 얻게 될 수 있습니다. 

부팅 가능한 작업 순서 미디어 및 PXE 부팅 배포에 사용되는 클라이언트 인증 인증서를 보호합니다. 클라이언트 인증 인증서를 캡처하면 이 프로세스를 통해 공격자가 인증서의 프라이빗 키를 가져올 수 있습니다. 이 인증서를 사용하면 공격자가 네트워크의 유효한 클라이언트로 가장할 수 있습니다. 이 시나리오에서는 Rogue 컴퓨터가 중요한 데이터를 포함할 수 있는 정책을 다운로드할 수 있습니다.  

네트워크 액세스 계정을 사용하여 상태 마이그레이션 지점에 저장된 데이터에 액세스하는 클라이언트는 실질적으로 동일한 ID를 공유합니다. 이러한 클라이언트는 네트워크 액세스 계정을 사용하는 다른 클라이언트의 상태 마이그레이션 데이터에 액세스할 수 있습니다. 데이터는 암호화되므로 원래 클라이언트만 데이터를 읽을 수 있지만 데이터가 변조 또는 삭제될 수 있습니다.  


### <a name="client-authentication-to-the-state-migration-point-is-achieved-by-using-a-configuration-manager-token-that-is-issued-by-the-management-point"></a>관리 지점에서 발급한 Configuration Manager 토큰을 사용하여 상태 마이그레이션 지점에 대한 클라이언트 인증이 수행됩니다.  

Configuration Manager는 상태 마이그레이션 지점에 저장된 데이터 양을 제한하거나 관리하지 않습니다. 공격자는 사용 가능한 디스크 공간을 차지하고 서비스 거부를 유발할 수 있습니다.  


### <a name="if-you-use-collection-variables-local-administrators-can-read-potentially-sensitive-information"></a>컬렉션 변수를 사용하는 경우 잠재적으로 로컬 관리자가 중요 정보를 읽을 수 있습니다.  

컬렉션 변수를 사용하면 운영 체제를 유연하게 배포할 수 있지만 이 기능으로 인해 정보가 노출될 수 있습니다.  



##  <a name="bkmk_privacy"></a> OS 배포에 대한 개인 정보 보호 관련 정보  

OS가 없는 컴퓨터에 OS를 배포하는 것 외에도 Configuration Manager를 사용하여 한 컴퓨터에서 다른 컴퓨터로 사용자 파일과 설정을 마이그레이션할 수 있습니다. 관리자는 개인적 데이터 파일, 구성 설정 및 브라우저 쿠키를 포함하여 전송할 정보를 구성합니다.  

Configuration Manager는 정보를 상태 마이그레이션 지점에 저장하고 전송 및 저장 중에 암호화합니다. 상태 정보와 연결된 새 컴퓨터만 저장된 정보를 검색할 수 있습니다. 새 컴퓨터가 정보를 검색하는 키를 분실한 경우 컴퓨터 연합 인스턴스 개체에 대한 **복구 정보 보기** 권한이 있는 Configuration Manager 관리자가 정보에 액세스하고 정보를 새 컴퓨터에 연결할 수 있습니다. 새 컴퓨터에서 상태 정보가 복원되면 기본적으로 만 하루 뒤에 데이터가 삭제됩니다. 삭제하도록 표시한 데이터를 상태 마이그레이션 지점에서 제거하는 시점을 구성할 수 있습니다. Configuration Manager는 상태 마이그레이션 정보를 사이트 데이터베이스에 저장하지 않고 Microsoft로 보내지 않습니다.  

부팅 미디어를 사용하여 OS 이미지를 배포하는 경우 항상 기본 옵션을 사용하여 부팅 미디어를 암호로 보호합니다. 암호는 작업 순서에 저장된 모든 변수를 암호화하지만 변수에 저장되지 않은 정보는 쉽게 노출될 수 있습니다.  

OS 배포는 작업 순서를 사용하여 배포 프로세스 중에 애플리케이션 및 소프트웨어 업데이트 설치를 비롯한 여러 가지 작업을 수행할 수 있습니다. 또한 작업 순서를 구성할 때 소프트웨어 설치에 영향을 미치는 개인 정보 보호에 대해 주의해야 합니다.  

Configuration Manager는 기본적으로 OS 배포를 구현하지 않습니다. 사용자 상태 정보를 수집하거나 작업 순서 또는 부팅 이미지를 만들기 전에 여러 구성 단계를 수행해야 합니다.  

OS 배포를 구성하려면 먼저 개인 정보 보호 요구 사항을 검토하세요.  



## <a name="see-also"></a>참고 항목

[진단 및 사용 현황 데이터](/sccm/core/plan-design/diagnostics/diagnostics-and-usage-data)

[Configuration Manager에 대한 보안 및 개인 정보](/sccm/core/plan-design/security/security-and-privacy)
