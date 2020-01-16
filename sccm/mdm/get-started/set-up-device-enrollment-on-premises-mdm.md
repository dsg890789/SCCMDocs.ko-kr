---
title: 온-프레미스 MDM에 대 한 등록 설정
titleSuffix: Configuration Manager
description: Configuration Manager에서 온-프레미스 MDM (모바일 장치 관리)에 대 한 장치를 등록할 수 있는 권한을 사용자에 게 부여 합니다.
ms.date: 01/09/2020
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: 9ffaea91-1379-4b86-9953-b25e152f56a9
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 28a39319acfe7fd75677a9eeb979b2f6b0d6641d
ms.sourcegitcommit: 4ca147f2bb3de35bd5089743c832e00bc3babd19
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/15/2020
ms.locfileid: "76035185"
---
# <a name="set-up-device-enrollment-for-on-premises-mdm-in-configuration-manager"></a>Configuration Manager에서 온-프레미스 MDM에 대 한 장치 등록 설정

*적용 대상: Configuration Manager (현재 분기)*

온-프레미스 MDM (모바일 장치 관리)을 설정 하는 마지막 단계는 사용자가 장치를 등록할 수 있도록 하는 것입니다. Configuration Manager 클라이언트 설정을 사용 하 여 온-프레미스 MDM에서 장치를 등록할 수 있는 권한을 사용자에 게 부여 합니다.

## <a name="bkmk_createProf"></a> 등록 프로필 만들기

사용자가 모바일 장치를 등록할 수 있도록 허용 하는 데 필요한 설정을 푸시 하려면 기본 클라이언트 설정에 새 등록 프로필을 추가 합니다. 그런 다음이 프로필은 Configuration Manager 사이트의 모든 사용자에 게 적용 됩니다.

> [!NOTE]
> 이 프로세스는 모든 장치 및 사용자에 게 자동으로 적용 되는 **기본 클라이언트 설정을**사용 합니다. 또는 사용자 지정 클라이언트 설정을 만든 다음 선택한 컬렉션에 배포할 수 있습니다. 이 대체 방법에는 하나 이상의 사용자 지정 클라이언트 설정, *장치* 설정 및 *사용자* 설정에 대 한 설정이 필요 합니다. 자세한 내용은 [클라이언트 설정을 구성하는 방법](/configmgr/core/clients/deploy/configure-client-settings)을 참조하세요.

1. Configuration Manager 콘솔에서 **관리** 작업 영역으로 이동하여 **클라이언트 설정** 노드를 선택합니다. **기본 클라이언트 설정을** 열고 **등록** 그룹을 선택 합니다.

1. 장치 설정에서 **최신 장치에 대 한 폴링 간격 (분)** 을 지정 합니다. 기본적으로이 간격은 60 분입니다.

1. 사용자 설정에서 **사용자가 최신 장치를 등록할 수 있도록 허용**하는 옵션을 사용 하도록 설정 합니다.

1. **최신 장치 등록 프로필**에 대해 **프로필 설정**을 선택 합니다. 등록 프로필 창에서 **만들기**를 선택 합니다.

1. 등록 프로필 만들기 창에서 다음 정보를 지정 합니다.

    - 등록 프로필에 대 한 고유 하 고 설명이 포함 된 **이름** 입니다.

    - 프로필에 대 한 추가 정보를 제공 하는 선택적 **설명** 입니다.

    - 장치 관리 지점을 포함 하는 **관리 사이트 코드** 를 선택 합니다. **확인** 을 선택 하 여 저장 하 고 닫습니다.

## <a name="bkmk_addClient"></a>추가 클라이언트 설정 구성

등록 후 장치를 구성 하기 위한 추가 클라이언트 설정이 있습니다. 보다 일반적인 정보 [는 클라이언트 설정을 구성 하는 방법](/configmgr/core/clients/deploy/configure-client-settings)을 참조 하세요.

Configuration Manager은 온-프레미스 MDM에 대해 다음과 같은 클라이언트 설정을 지원 합니다.

- **클라이언트 정책**: 이러한 설정은 장치에 클라이언트 정책을 다운로드 하는 빈도를 지정 합니다. 사용자 정책에 대 한 설정을 사용 하도록 설정할 수도 있습니다. 자세한 내용은 [클라이언트 설정 정보-클라이언트 정책](/configmgr/core/clients/deploy/about-client-settings#client-policy)을 참조 하세요.

- **소프트웨어 배포**: 소프트웨어 배포를 평가 하는 간격을 설정 합니다. 자세한 내용은 [클라이언트 설정 정보-소프트웨어 배포](/configmgr/core/clients/deploy/about-client-settings#software-deployment)를 참조 하세요.

    > [!NOTE]
    > 온-프레미스 MDM의 경우 소프트웨어 배포 설정만 기본 클라이언트 설정으로 사용할 수 있습니다.

## <a name="bkmk_enableUsers"></a>사용자 검색

사용자가 온-프레미스 MDM에 대 한 등록 프로필을 사용 하 여 클라이언트 설정을 수신 하는 경우 사이트는 Active Directory에서 사용자 계정을 검색 합니다. 등록 프로필이 필요한 모든 사람이 프로필을 받도록 하려면 Active Directory 사용자에 대해 검색을 실행합니다. 자세한 내용은 [사용자 검색 Active Directory](/configmgr/core/servers/deploy/configure/about-discovery-methods#bkmk_aboutUser)를 참조 하세요.

## <a name="bkmk_storeCert"></a>신뢰할 수 있는 루트 인증서 설치

도메인에 가입 된 장치는 사이트 시스템 역할을 호스트 하는 서버와 신뢰할 수 있는 통신을 위한 신뢰 루트 인증서를 가져옵니다. Active Directory 인증서 서비스는 신뢰할 수 있는 루트 인증서를 자동으로 배포 합니다. 도메인에 가입 되지 않은 컴퓨터 및 모바일 장치에는 등록을 허용 하는 다른 방법을 통해이 인증서를 설치 해야 합니다.

> [!NOTE]
> 공용 인증 기관에서 웹 서버 인증서를 발급 한 경우 대부분의 장치는 이미 이러한 Ca를 신뢰 합니다. 디자인에 이러한 공용 Ca 중 하나를 사용 하는 경우이 단계를 수행할 필요가 없습니다.

[신뢰할 수 있는 루트 인증서를 내보낸](/configmgr/mdm/get-started/set-up-certificates-on-premises-mdm#bkmk_exportCert)후 등록 해야 하는 장치에 인증서를 설치 해야 합니다. 예를 들어 도메인에 가입 되지 않은 장치는 Active Directory에서 자동으로 가져올 수 없습니다. 사용자가 사용 하는 프로세스는 다음과 같은 요인에 따라 달라 집니다.

- 특정 장치 유형 및 기술 기능
- OS 버전
- 비즈니스, 보안 및 사용자 환경 요구 사항

다음 목록에는 장치에 신뢰할 수 있는 루트 인증서를 제공 하 고 설치 하는 몇 가지 예제 메서드가 포함 되어 있습니다.

- 파일 공유

- 메일 첨부 파일

- 메모리 카드

- 테더링된 디바이스

- 클라우드 스토리지(예: OneDrive)

- NFC(근거리 통신) 연결

- 바코드 스캐너

- OOBE(첫 실행 경험) 프로비저닝 패키지

### <a name="manually-install-the-trusted-root-certificate-in-windows"></a>Windows에서 신뢰할 수 있는 루트 인증서 수동 설치

1. 등록할 장치에서 파일 탐색기를 통해 신뢰할 수 있는 루트 인증서 파일 (.cer)로 이동 하 여 **엽니다** .

1. 인증서 창에서 **인증서 설치**를 선택 합니다.

1. 인증서 가져오기 마법사에서 **로컬 컴퓨터**를 선택 하 고 **다음** 을 선택 하 여 관리자 권한으로 계속 합니다.

1. 인증서 저장소 페이지에서 **모든 인증서를 다음 저장소에**저장을 선택한 다음 **찾아보기**를 선택 합니다.

1. 인증서 저장소 선택 창에서 **신뢰할 수 있는 루트 인증 기관**을 선택 하 고 **확인**을 선택 합니다.

1. 마법사를 완료 하 고 마법사를 완료 합니다.

## <a name="next-step"></a>다음 단계

> [!div class="nextstepaction"]
> [디바이스 등록](/configmgr/mdm/deploy-use/enroll-devices-on-premises-mdm)
