---
title: 지원 센터 빠른 시작
titleSuffix: Configuration Manager
description: 문제 해결을 위해 신속하게 Configuration Manager 클라이언트 상태를 캡처합니다.
ms.date: 11/27/2018
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 5cb41e2b-4c79-4da9-a432-ff869c0870f8
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 5a9865a591f6947447ebb088b5e5e25db1e9fa54
ms.sourcegitcommit: 6e42785c8c26e3c75bf59d3df7802194551f58e1
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/28/2018
ms.locfileid: "52458117"
---
# <a name="support-center-quickstart-guide"></a>지원 센터 빠른 시작 가이드

*적용 대상: System Center Configuration Manager(현재 분기)*

지원 센터에는 문제 해결 및 실시간 로그 확인을 포함한 강력한 기능이 있습니다. 이를 사용하여 단 몇 분 안에 Configuration Manager 클라이언트 컴퓨터의 상태를 캡처할 수 있습니다. 이 기능은 원격 클라이언트 액세스를 포함합니다.

클라이언트 상태를 캡처하는 종합 *문제 해결 번들* 파일(.zip)을 만듭니다. 이 번들에는 로그 파일만 포함된 것이 아닙니다. 레지스트리 설정, 클라이언트 구성 같은 다른 데이터 형식도 포함될 수 있습니다. 지원 센터 뷰어를 사용하는 지원 담당자에게 이 번들을 제공합니다.



## <a name="prerequisites"></a>필수 구성 요소

- Configuration Manager 클라이언트에 대한 로컬 관리자 권한  

- 지원 센터 설치 관리자입니다. 이 파일은 `cd.latest\SMSSETUP\Tools\SupportCenter\SupportCenterInstaller.msi`의 사이트 서버에 있습니다. 자세한 내용은 [지원 센터 - 설치](/sccm/core/support/support-center#install)를 참조하세요.  



## <a name="step-1-create-a-data-bundle-on-a-local-client"></a>1단계: 로컬 클라이언트에서 데이터 번들 만들기

1.  Configuration Manager 클라이언트에 지원 센터를 설치합니다.  

2.  **시작** 메뉴로 이동하고 **Microsoft System Center** 그룹에서 **지원 센터**를 선택합니다.  

3.  리본의 홈 탭에서 **선택한 데이터 수집**을 선택합니다. 기본적으로 지원 센터는 로그 파일, 클라이언트 구성, 운영 체제 등, 최소 데이터 집합만 수집합니다.  

4.  문제 해결 번들 파일(.zip)을 컴퓨터의 폴더에 저장합니다. 기본적으로 파일 이름은 예제(`Support_c885cdfed3c7482bba4f9e662978ec07.zip`)와 유사합니다.  



## <a name="step-2-view-the-data-bundle-using-support-center-viewer"></a>2단계: 지원 센터 뷰어를 사용하여 데이터 번들 보기

1.  **Support Center Viewer**를 시작합니다. 이 작업은 지원 센터를 설치한 모든 컴퓨터에서 실행될 수 있습니다.  

2.  **번들 열기**를 선택하고 번들 파일로 이동한 다음, **열기**를 선택합니다.  

3.  지원 센터가 파일을 처리한 후 사용 가능한 개별 탭으로 전환합니다. 지원 센터가 기본적으로 수집하는 데이터 형식을 확인합니다.  

    - **구성**  

        - Configuration Manager 클라이언트 구성  

        - 운영 체제  

        - 컴퓨터  

        - 서비스  

        - 네트워크 어댑터  

    - **로그**: 목록에서 하나 이상의 항목을 선택하고 **열기**를 선택합니다. 이 작업은 로그 뷰어에 선택한 로그 파일을 엽니다. 이 기능을 사용하여 오류 코드를 조회하고 고급 필터를 사용하여 더 신속하게 로그 파일을 분석합니다.  



## <a name="collect-more-data"></a>더 많은 데이터 수집

이러한 기본 기능 외에도 Support Center는 그 밖에 다양한 클라이언트 상태 정보를 수집할 수 있습니다. **지원 센터**를 열고 **모든 데이터 수집**을 선택합니다. 이 프로세스는 일반적으로 최신 컴퓨터에서도 몇 분 정도 지속됩니다. 지원 센터에는 다음 추가 데이터를 수집합니다.

  - **정책**: 요청된 정책 구성 및 실제 정책 구성을 포함하여 Configuration Manager 정책 설정을 수집합니다.  

  - **인증서**: 클라이언트 인증서의 공개 키 정보 지원 센터는 인증서 개인 키를 수집하지 않습니다.  

  - **클라이언트 레지스트리**: 레지스트리에서 클라이언트 구성 정보를 수집합니다. 지원 센터는 Configuration Manager 레지스트리 정보만 수집합니다.  

  - **클라이언트 WMI**: WMI의 클라이언트 구성 정보 지원 센터는 클라이언트 정책을 수집하지 않습니다.  

  - **문제 해결**: Active Directory, 관리 지점, 네트워킹, 정책 할당 및 등록과 관련된 일반적인 클라이언트 문제를 진단하는 데 도움이 되는 실시간 문제 해결 데이터  

  - **디버그 덤프**: 클라이언트의 디버그 덤프 및 관련된 프로세스를 수행합니다. 디버그 덤프는 클 수 있습니다. 클라이언트 성능 문제를 해결하는 경우에만 이 옵션을 활성화합니다.  

