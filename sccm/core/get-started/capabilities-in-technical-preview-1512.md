---
title: 기술 미리 보기 1512의 기능
titleSuffix: Configuration Manager
description: System Center Configuration Manager용 Technical Preview 버전 1512에서 사용 가능한 기능에 대해 알아봅니다.
ms.date: 01/23/2017
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: e4d9e414-1346-4ed4-85d0-64d602b68731
author: aczechowski
ROBOTS: NOINDEX
manager: dougeby
ms.author: aaroncz
ms.openlocfilehash: 970f86849572d6b360c5b92a42a3d131a38fe1d7
ms.sourcegitcommit: ef3fdf21180e43afd7af6c8264524711435e426e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/24/2019
ms.locfileid: "54896467"
---
# <a name="capabilities-in-technical-preview-1512-for-system-center-configuration-manager"></a>System Center Configuration Manager용 Technical Preview 1512의 기능

*적용 대상: System Center Configuration Manager(Technical Preview)*

이 문서에서는 System Center Configuration Manager용 Technical Preview 버전 1512에서 사용 가능한 기능을 소개합니다. 이 버전을 설치하여 Configuration Manager Technical Preview 사이트를 업데이트하고 새로운 기능을 추가할 수 있습니다. 이 버전의 Technical Preview를 설치하기 전에 소개 항목인 [System Center Configuration Manager용 Technical Preview](technical-preview.md)를 검토하여 Technical Preview 사용을 위한 일반 요구 사항 및 제한 사항, 버전 업데이트 방법 및 Technical Preview의 기능에 대해 피드백 제공 방법 등에 익숙해져야 합니다.  

 다음은 이 버전에서 사용할 수 있는 새로운 기능입니다.  

##  <a name="bkmk_devicehealth"></a> 디바이스 상태 증명  
 Technical  Preview 1512부터 관리자는 Configuration Manager 콘솔에서 Windows 10 디바이스 상태 증명의 상태를 볼 수 있습니다.  이 기능은 Configuration Manager와 Microsoft Intune에서의 Configuration Manager에 사용할 수 있습니다. 디바이스 상태 증명을 사용하여 관리자는 클라이언트 컴퓨터가 신뢰할 수 있는 BIOS, TPM 및 소프트웨어 구성을 갖는지 확인할 수 있습니다. 디바이스 상태 증명을 지원하려면 클라이언트 디바이스에서 TPM 2가 설정된 Win10이 실행되고 있어야 합니다. 디바이스 상태 증명은 다음 각각에 대해 사용하도록 설정된 디바이스 수를 표시합니다.  

-   맬웨어 방지 조기 실행  

-   BitLocker  

-   보안 부팅  

-   코드 무결성  

콘솔에는 누락된 상위 상태 증명 설정과 디바이스 수도 표시됩니다.  

디바이스 상태 증명 보기를 미리 보려면 Configuration Manager에서 **모니터링** 작업 영역으로 이동한 후 **보안** 노드를 클릭하고 **상태 증명**을 클릭합니다.  

##  <a name="bkmk_viewterms"></a> 콘솔 내 사용 약관 모니터링  
Technical  Preview 1512부터 Microsoft Intune에서 Configuration Manager를 통합할 경우 Configuration Manager 콘솔을 사용하여 IT 부서에서 구성한 계약조건에 동의한 사용자와 동의하지 않은 사용자를 볼 수 있습니다.  

**요약 정보를 보려면**  

-   Configuration Manager 콘솔에서 **모니터링** > **개요** > **배포**로 이동한 후 보려는 계약조건 배포를 선택합니다.  

**자세한 정보를 보려면**  

1.  Configuration Manager 콘솔에서 **자산 및 준수** > **개요** > **준수 설정** > **계약조건**으로 이동한 후 보려는 계약조건을 선택합니다.  

2.  콘솔의 맨 아래에서 **배포** 탭을 선택하고 배포를 클릭한 후 **상태 보기**를 클릭합니다.  

##  <a name="bkmk_EPpolicy"></a> Endpoint Protection 정책 설정의 향상된 기능  
1512 Technical Preview에서 Endpoint Protection 맬웨어 방지 정책에 다음과 같은 새 설정이 추가되었습니다.  

-   실시간 보호: **다운로드 시 및 설치 전에 잠재적으로 원치 않는 애플리케이션 차단**  

    -   PUA(잠재적인 원치 않는 애플리케이션)는 명성 및 연구 기반 식별 결과에 따라 위협으로 분류됩니다. 가장 일반적으로는 원치 않는 애플리케이션 번들러 또는 번들로 묶은 애플리케이션입니다.  

    -   보호 정책 설정은 기본적으로 사용되도록 설정("예"로 설정)되어 있습니다. 사용되도록 설정되면 이 설정은 다운로드 및 설치 시에 PUA를 차단합니다. 그러나 특정 파일 또는 사용자 환경의 특정 요구를 충족 하기 위해 폴더를 제외할 수 있습니다.  

-   검색 설정: **전체 검사를 실행할 때 매핑된 네트워크 드라이브 검사**  

    -   이 설정은 아주 세부적으로 구분되어 있으므로 관리자는 예약된 전체 동안 매핑된 네트워크 드라이브를 항상 검색할 위험 없이 네트워크 파일의 주문형 검색을 수행할 수 있습니다.  

    -   이 설정을 구성에 사용하려면 먼저 **네트워크 파일 검색** 설정을 사용하도록 설정("예")해야 합니다.  

    -   기본적으로 이 설정은 전체 검색이 매핑된 네트워크 드라이브에 액세스하지 않음을 의미하는 "아니요"입니다.  

-   자동 샘플 파일 전송 설정:  

     맬웨어 방지 엔진은 추가 분석을 위해 샘플 파일을 Microsoft로 보내도록 요청할 수 있습니다. 기본적으로 이러한 샘플을 보내기 전에 항상 확인 메시지가 표시됩니다. 관리자는 이 동작을 구성하기 위해 다음 설정을 관리할 수 있습니다.  

    -   고급: **검색된 특정 항목의 악성 여부를 Microsoft가 확인할 수 있도록 자동 샘플 파일 전송 사용**:  자동 샘플 파일 전송을 활성화하려면 이 설정을 “예”로 변경합니다. 기본적으로 이 설정은 자동 샘플 파일 전송이 사용되지 않도록 설정되어 사용자가 샘플을 보내기 전에 확인 메시지가 표시되는 "아니요"로 설정되어 있습니다.   (이 설정은 System Center 2012 R2 Configuration Manager SP1에 처음 도입되었습니다.)  

    -   고급: **사용자가 자동 샘플 파일 전송 설정을 수정하도록 허용**: 이 설정은 장치에 대해 로컬 관리자 권한이 있는 사용자가 클라이언트 인터페이스에서 자동 샘플 파일 전송 설정을 변경할 수 있는지 여부를 결정합니다. 기본적으로 Configuration Manager 콘솔 내에서만 설정을 변경할 수 있고 디바이스의 로컬 관리자가 이 구성을 변경할 수 없는 "아니요"로 설정되어 있습니다.  

         예를 들어 다음은 관리자가 사용되도록 설정하며 사용자는 수정할 수 없는 Windows 10의 Windows Defender 설정입니다.  

         ![TechRef&#95;WinDefender](../../core/get-started/media/TechRef_WinDefender.png "TechRef_WinDefender")  

    또한 Endpoint Protection 맬웨어 방지 정책의 "제외 설정"에 포함된 기존의 **파일 및 폴더 제외** 설정이 디바이스 제외를 허용하도록 개선되었습니다. 예를 들어 **\device\mvfs** 같이 예외를 지정할 수 있습니다(다중 파일 시스템용). 이 정책은 디바이스 경로가 유효한지 확인하지 않습니다. 디바이스 문자열을 해석할 수 있어야 하는 클라이언트의 맬웨어 방지 엔진에 대해 Endpoint Protection 정책이 제공됩니다.  

**Endpoint Protection 정책을 사용하기 위한 필수 조건:**  

Endpoint Protection 정책을 사용하려면 먼저 Endpoint Protection 클라이언트 설정을 사용하여 Endpoint Protection 클라이언트를 설치하고 관리해야 합니다. 이렇게 하려면 Windows 7, Windows 8, Windows 8.1용 System Center Endpoint Protection 클라이언트 또는 관리되는 Windows 10용 Windows Defender를 사용합니다. [System Center Configuration Manager의 Endpoint Protection](../../protect/deploy-use/endpoint-protection.md)을 참조하세요.  
