---
title: 디바이스를 대량 등록하는 방법
titleSuffix: Configuration Manager
description: Configuration Manager에서 온-프레미스 MDM (모바일 장치 관리)을 사용 하 여 자동화 된 방식으로 장치를 대량 등록 합니다.
ms.date: 01/13/2020
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: b36f5e4a-2b57-4d18-83f6-197081ac2a0a
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: ac9bfa690cc610ca4a64aedbc8049fb1f5a822f9
ms.sourcegitcommit: 4ca147f2bb3de35bd5089743c832e00bc3babd19
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/15/2020
ms.locfileid: "76035288"
---
# <a name="how-to-bulk-enroll-devices-with-on-premises-mdm-in-configuration-manager"></a>Configuration Manager에서 온-프레미스 MDM을 사용 하 여 장치를 대량 등록 하는 방법

*적용 대상: Configuration Manager (현재 분기)*

온-프레미스 MDM (모바일 장치 관리) Configuration Manager에서 대량 등록은 장치를 등록 하는 자동화 된 방법입니다. 다른 방법은 사용자가 장치를 등록 하기 위해 자격 증명을 입력 해야 하는 사용자 등록입니다. 대량 등록은 등록 패키지를 사용하여 등록 중에 디바이스를 인증합니다. 패키지는 .log kg 파일입니다 .이 파일에는 등록을 지 원하는 인증서 및 Wi-fi 프로필이 포함 될 수도 있습니다.

## <a name="bkmk_createCert"></a> 인증서 프로필 만들기

장치에 신뢰할 수 있는 루트 인증서를 자동으로 설치 하는 인증서 프로필을 포함 합니다. 이 루트 인증서는 장치와 온-프레미스 MDM에 필요한 사이트 시스템 역할 간의 신뢰할 수 있는 통신에 필요 합니다.

온-프레미스 MDM에 대 한 사이트를 준비 하는 경우 신뢰할 수 있는 루트 인증서를 내보냅니다. 등록 패키지의 인증서 프로필에서이 인증서를 사용 합니다. 신뢰할 수 있는 루트 인증서를 가져오는 방법에 대 한 자세한 내용은 [신뢰할 수 있는 루트 인증서 내보내기](/configmgr/mdm/get-started/set-up-certificates-on-premises-mdm#bkmk_exportCert)를 참조 하세요.

내보낸 인증서를 사용 하 여 인증서 프로필을 만듭니다. 자세한 내용은 [인증서 프로필을 만드는 방법](/configmgr/protect/deploy-use/create-certificate-profiles)을 참조 하세요.

## <a name="CreateWifi"></a> Wi-Fi 프로필 만들기

대량 등록 패키지의 다른 구성 요소는 Wi-fi 프로필입니다. 이 프로필은 장치에서 등록을 지원 하기 위해 네트워크에 연결할 수 있는지 확인할 수 있습니다.

Configuration Manager에서 Wi-fi 프로필을 만드는 방법에 대 한 자세한 내용은 [wi-fi 프로필을 만드는 방법](/configmgr/protect/deploy-use/create-wifi-profiles)을 참조 하세요.

### <a name="wi-fi-profile-limitations"></a>Wi-fi 프로필 제한 사항

온-프레미스 MDM 대량 등록에 대 한 Wi-fi 프로필을 만드는 경우 다음 제한 사항을 검토 합니다.

#### <a name="wi-fi-security-configurations-for-on-premises-mdm"></a>온-프레미스 MDM에 대 한 wi-fi 보안 구성

현재 Configuration Manager 분기에서는 온-프레미스 MDM에 대 한 다음 Wi-fi 보안 구성만 지원 합니다.

- 보안 유형: **WPA2-엔터프라이즈** 또는 **WPA2 개인**

- 암호화 유형: **AES** 또는 **TKIP**

- EAP 유형: **스마트 카드 또는 기타 인증서** 또는 **PEAP**

#### <a name="proxy-server"></a>프록시 서버

Configuration Manager는 Wi-fi 프로필의 프록시 서버 정보에 대 한 설정이 있지만 장치를 등록할 때 프록시를 구성 하지 않습니다. 대량 등록 장치에서 프록시 서버를 설정 해야 하는 경우:

- 장치를 등록 한 후 구성 항목을 사용 하 여 설정을 배포 합니다.

- Windows ICD (이미지 및 구성 디자이너)를 사용 하 여 두 번째 패키지를 만든 다음 대량 등록 패키지와 함께 배포 합니다.

## <a name="bkmk_createEnroll"></a> 등록 프로필 만들기

등록 프로필을 사용 하 여 장치 등록에 필요한 설정을 지정할 수 있습니다. 이러한 설정에는 [인증서 프로필](#bkmk_createCert) 및 [wi-fi 프로필이](#CreateWifi)포함 됩니다.

1. Configuration Manager 콘솔에서 **자산 및 호환성** 작업 영역으로 이동 하 고, **회사가 소유한 모든 장치**를 확장 하 고, **Windows**를 확장 하 고, **등록 프로필** 노드를 선택 합니다.

1. 리본에서 **등록 프로필 만들기**를 선택 합니다.

1. 등록 프로필 만들기 마법사의 **일반** 페이지에서 다음 정보를 지정 합니다.

    - **이름**: 프로필을 식별 하는 고유 이름입니다.

    - **설명**: 프로필을 자세히 설명 하는 선택적 필드입니다.

    - **관리 기관**: **온-프레미스** 만 선택

1. **사이트 할당** 페이지에서 장치 관리 지점을 사용 하 여 **관리 사이트 코드** 를 선택 합니다.

1. **등록 프록시 지점 선택** 페이지에서 **인트라넷만**을 선택 하 고 하나 이상의 등록 프록시 지점을 선택 합니다. 장치는 이러한 서버를 사용 하 여 등록 프로세스를 시작 합니다.

1. **신뢰할 수 있는 루트 인증서 선택** 페이지에서 신뢰할 수 있는 루트 인증서가 포함 된 인증서 프로필을 선택 합니다.

1. **Wi-fi 프로필** 페이지에서 연결할 장치에 필요한 네트워크 설정이 포함 된 wi-fi 프로필을 선택 합니다.

    > [!TIP]
    > 등록 패키지에 대해 Wi-fi 프로필을 사용 하지 않는 경우이 단계를 건너뜁니다.

1. 마법사 완료

## <a name="bkmk_createPpkg"></a>등록 패키지 만들기

등록 패키지 (ppkg)는 온-프레미스 MDM에 대 한 장치를 대량 등록 하는 데 사용 하는 파일입니다. Configuration Manager를 사용 하 여이 파일을 만듭니다. Windows ICD를 사용 하 여 비슷한 유형의 패키지를 만들 수 있지만, Configuration Manager에서 만든 패키지만 온-프레미스 MDM에 대 한 장치를 등록 하는 데 사용할 수 있습니다. Windows ICD로 만든 패키지는 등록에 필요한 UPN (사용자 계정 이름)만 제공할 수 있으며 실제 등록 프로세스를 시작할 수 없습니다.

등록 패키지를 만드는 프로세스에는 Windows 10용 Windows ADK(평가 및 배포 도구 키트)가 필요합니다. Configuration Manager 콘솔을 실행 하는 컴퓨터에서 최신 버전의 Windows ADK를 설치 합니다. ICD ( **이미징 및 구성 디자이너)** 기능 및 모든 종속성을 선택 합니다. 이 버전은 Configuration Manager 사이트에서 OS 배포에 사용 되는 버전과 일치할 필요가 없습니다. 자세한 내용은 [windows 10 용 WINDOWS ADK 다운로드](https://docs.microsoft.com/windows-hardware/get-started/adk-install)를 참조 하세요.

1. Configuration Manager 콘솔에서 **자산 및 호환성** 작업 영역으로 이동 하 고, **회사가 소유한 모든 장치**를 확장 하 고, **Windows**를 확장 하 고, **등록 프로필** 노드를 선택 합니다.

1. 기존 등록 프로필을 선택 합니다. 리본에서 **내보내기**를 선택 합니다.

1. 등록 패키지 내보내기 창에서 다음 정보를 지정 합니다.

    - **유효 기간 (일)** : 기본적으로 Configuration Manager는 2 주 (14 일)에 만료 되도록 등록 패키지를 설정 합니다. 유효 기간이 만료 된 후에는 장치 등록에 패키지를 사용할 수 없습니다. 1에서 30 사이의 정수를 입력 하십시오.

    - **패키지 파일**: 확장명이 ppkg 파일의 로컬 또는 네트워크 파일 경로를 지정 합니다.

    - **암호화 패키지**: 패키지를 암호로 보호 하려면이 옵션을 사용 하도록 설정 합니다. 패키지를 내보낸 후 Configuration Manager는 생성 된 암호를 표시 합니다. 암호를 복사 하 여 안전한 위치에 저장 합니다. 내보낸 등록 패키지는 암호 없이 사용할 수 없습니다.

        > [!IMPORTANT]
        > Configuration Manager 암호를 저장 하지 않으며 사용자 지정 하거나 변경할 수 없습니다. 암호를 표시 하는 창을 닫으면 암호를 검색할 방법이 없습니다.

1. **내보내기**를 선택합니다. Configuration Manager는 Windows ADK를 사용 하 여 등록 패키지를 만듭니다.

Configuration Manager는 유효한 등록 패키지를 계속 추적 합니다. 콘솔에서 **등록 프로필** 노드를 확장 하 고 **내보낸 패키지**를 선택 합니다.

> [!TIP]
> Configuration Manager 콘솔에서 등록 패키지를 제거 하면 장치를 등록 하는 데 사용할 수 없습니다. 이 방법을 사용 하 여 다른 사용자가 대량 등록에 사용 하지 않으려는 등록 패키지를 관리할 수 있습니다.

## <a name="bkmk_getPpkg"></a>장치 대량 등록

패키지를 사용 하 여 장치의 OOBE (기본 경험) 프로세스 전후에 장치를 등록할 수 있습니다. 등록 패키지는 OEM (원본 장비 제조업체) 프로 비전 패키지의 일부로 포함 될 수도 있습니다.

대량 등록을 위해 패키지를 사용 하려면 해당 패키지를 장치에 물리적으로 전달 해야 합니다. 사용자 요구 사항에 따라 다양 한 방법이 있습니다. 예를 들면 다음과 같습니다.

- 파일 시스템에서 복사

- 전자 메일에 첨부

- NFC (근거리 통신) 연결을 통해 복사

- 메모리 카드에서 복사

- 바코드 스캔

- 테더링된 디바이스에서 복사

- OEM 프로비저닝 패키지에 포함

### <a name="enroll-a-device-with-bulk-enrollment-package"></a>대량 등록 패키지를 사용 하 여 장치 등록

1. 장치에서. ppkg 파일을 엽니다. 필요한 경우 관리자 권한으로 실행 합니다.

1. Windows에서 패키지를 신뢰할 수 있는 원본에서 가져온 것인지 묻는 메시지가 표시 되 면 **예**를 선택 합니다.

등록 프로세스가 시작 됩니다.

## <a name="bkmk_verifyEnroll"></a>등록 확인

### <a name="verify-bulk-enrollment-on-the-device"></a>장치에서 대량 등록 확인

1. 장치에서 **설정**을 엽니다.

1. **계정**을 선택 하 고 **회사 또는 학교 액세스**를 선택 합니다. 성공적으로 등록 되 면 **면 companyapps**아래에 계정이 표시 됩니다.

1. 계정을 선택한 다음 **동기화**를 선택 합니다. 이 작업은 Configuration Manager를 사용 하 여 관리를 시작 합니다.

### <a name="verify-enrollment-in-the-console"></a>콘솔에서 등록 확인

Configuration Manager 콘솔을 사용 하 여 장치가 성공적으로 등록 되었는지 확인 합니다. Configuration Manager 콘솔에서 **자산 및 규정 준수** 작업 영역으로 이동하고 **디바이스**를 선택합니다. 장치 목록에서 등록 된 장치를 찾아보거나 검색 합니다.
