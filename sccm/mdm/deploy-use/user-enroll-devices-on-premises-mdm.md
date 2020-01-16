---
title: 사용자가 디바이스를 등록하는 방법
titleSuffix: Configuration Manager
description: 사용자가 Configuration Manager에서 온-프레미스 MDM (모바일 장치 관리)을 사용 하 여 장치를 등록 하는 방법을 이해 합니다.
ms.date: 01/13/2020
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: 59004b34-b64f-4d77-898c-07bf3dc75430
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: e2d1eb0476eec975a458222134eb33ab8469cbb6
ms.sourcegitcommit: 4ca147f2bb3de35bd5089743c832e00bc3babd19
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/15/2020
ms.locfileid: "76035215"
---
# <a name="how-users-enroll-devices-with-on-premises-mdm-in-configuration-manager"></a>사용자가 Configuration Manager에서 온-프레미스 MDM을 사용 하 여 장치를 등록 하는 방법

*적용 대상: Configuration Manager (현재 분기)*

Configuration Manager 온-프레미스 MDM (모바일 장치 관리)을 사용 하 여 사용자는 자신의 장치를 등록할 수 있습니다. 여기에는 두 가지 필수 구성 요소가 있습니다.

- 클라이언트 설정을 사용 하 여 사용자에 게 등록할 수 있는 권한을 부여 합니다.

- 장치에 필요한 신뢰할 수 있는 루트 인증서를 설치 합니다.

등록을 설정 하는 방법에 대 한 자세한 내용은 [온-프레미스 MDM에 대 한 장치 등록 설정](/configmgr/mdm/get-started/set-up-device-enrollment-on-premises-mdm)을 참조 하세요.

## <a name="bkmk_enrollDesk"></a>Windows 10 등록

1. Windows 10 컴퓨터에서 **설정**으로 이동합니다.

1. **계정**을 선택 하 고 **회사 또는 학교 액세스**를 선택 합니다.

1. **연결**을 선택 하 고 UPN (사용자 계정 이름)을 입력 한 다음 **계속**을 선택 합니다. UPN은 전자 메일 주소와 같을 수 있습니다 (예: jdoe@contoso.com).

1. 등록 프록시 지점의 FQDN (정규화 된 도메인 이름)을 입력 하 고 **계속**을 선택 합니다.

1. 암호를 입력 하 고 **로그인**을 선택 합니다.

1. Windows에서이 작업에 대 한 로그인 정보를 기억할 필요가 없으므로 **건너뛰기**를 선택 합니다.

잠시 후 장치가 Configuration Manager 등록 됩니다.

## <a name="bkmk_enrollMob"></a>Windows 10 Mobile 등록

1. Windows 10 모바일 디바이스에서 **설정**으로 이동합니다.

1. **계정**을 선택 하 고 **회사 액세스**를 선택 합니다.

1. **연결**을 선택합니다.

1. UPN 및 등록 프록시 지점의 FQDN을 입력 합니다. 그런 다음 **연결**을 선택합니다.

1. 다음 화면에서 UPN 및 암호를 입력 한 다음 **로그인**을 선택 합니다.

잠시 후 장치가 Configuration Manager 등록 됩니다. **완료**를 선택합니다.

## <a name="bkmk_verify"></a>등록 확인

Configuration Manager 콘솔을 사용 하 여 장치가 성공적으로 등록 되었는지 확인 합니다. Configuration Manager 콘솔에서 **자산 및 규정 준수** 작업 영역으로 이동하고 **디바이스**를 선택합니다. 장치 목록에서 등록 된 장치를 찾아보거나 검색 합니다.
