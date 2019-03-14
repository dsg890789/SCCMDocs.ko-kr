---
title: 데스크톱 Analytics에서 배포 계획
titleSuffix: Configuration Manager
description: 데스크톱 Analytics에서 배포 계획에 알아봅니다.
ms.date: 01/25/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 0f369f3a-f251-4f34-9302-1bdc6ea5d139
author: aczechowski
ms.author: aaroncz
manager: dougeby
ROBOTS: NOINDEX
ms.collection: M365-identity-device-management
ms.openlocfilehash: ce726ffa0dfc8a46bd0891e50ff087ad4931d901
ms.sourcegitcommit: 874d78f08714a509f61c52b154387268f5b73242
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56755453"
---
# <a name="about-deployment-plans-in-desktop-analytics"></a>데스크톱 Analytics에서 배포 계획에 대 한 

> [!Note]  
> 이 정보는 정식으로 발표 되기 전에 대폭 수정 될 수 있는 미리 보기 서비스에 연결 합니다. Microsoft는 여기에 제공된 정보와 관련하여 명시적이거나 묵시적인 어떤 보증도 하지 않습니다.  

수집 하 고 조직에서 장치, 응용 프로그램 및 드라이버 데이터를 분석 하는 데스크톱 분석 합니다. 이 분석 및 입력에 따라 Windows 10 및 Office 365 ProPlus 배포 계획을 만들려면 서비스를 사용할 수 있습니다. 배포 계획에는 다음과 같은 기능이 있습니다.  

- 자동으로 파일럿에 포함 장치를 것이 좋습니다.  

- 호환성 문제를 식별 하 고 완화 조치를 제안 합니다.  

- 이전, 도중 및 업데이트 이후 배포의 상태를 평가 합니다.  

- 배포의 진행 상태  


배포 계획의 일환으로, 다음 작업을 수행할 수 있습니다.  

 - 배포 하려는 어떤 제품 및 버전을 정의 합니다. Windows 10, Office 365 ProPlus의 경우 또는 둘 다  

 - 어떤 그룹을 배포 하려는 장치를 선택 합니다.  

 - 배포에 대 한 준비 규칙 만들기  

 - 앱 및 Office 추가 기능의 중요도 정의 합니다.  

 - 자동 권장 사항에 따라 파일럿 장치를 선택 합니다.  

 - 앱 및 데스크톱 Analytics에서 권장 사항에 따라 Office 추가 기능을 사용 하 여 문제를 해결 하는 방법 결정  


데스크톱 Analytics 배포 계획 데이터를 매일 새로 고칩니다. 24 시간 동안 변경 내용이 나타나지 않을 수 있습니다. 이러한 변경으로는 중요도를 앱에 할당 또는 파일럿에 포함 하려면 장치를 선택 합니다.  

데스크톱 Analytics를 Configuration Manager에 연결 하는 경우 배포 계획에서 컬렉션을 선택 합니다. 이 통합 데스크톱 분석 데이터를 기반으로 컬렉션에 Windows 또는 Office를 배포할 수 있습니다. 

Configuration Manager를 사용 하지 않는 경우에 Log Analytics에 그룹을 만들 수 있습니다. 자세한 내용은 [컴퓨터 그룹에서 Log Analytics 로그 검색](https://docs.microsoft.com/azure/log-analytics/log-analytics-computer-groups)합니다. 



## <a name="readiness-rules"></a>준비 규칙

다음 준비 상태 규칙은 배포 계획에 사용할 수 있습니다.

- 여부 장치가 Windows 업데이트에서 드라이버를 자동으로 받습니다. Windows Update에서 드라이버 업데이트를 수신 하는 장치의 경우 준비 상태 평가의 일부로 식별 하는 모든 드라이버 문제를 자동으로 표시 됩니다 **준비**합니다.  

- 낮은은 Windows 앱에 대 한 count 임계값을 설치 합니다. 앱이이 임계값 보다 높은 비율로 컴퓨터에 설치, 배포 계획으로 앱 표시 **Noteworthy**합니다. 이 태그는 파일럿 단계 동안 테스트 하려면이 얼마나 중요 한지를 결정할 수 있습니다 의미 합니다.  

- 32 비트에서 Office 365 ProPlus 업데이트에 64 비트에서 64 비트 버전 Windows의 장치입니다. 이 동작은 기본에 설명 합니다.  

- Office의 이전 버전에서 업데이트 하는 경우에 해당 앱 Office의 최신 버전에 없는 경우에 이전 Office 앱을 그대로 둡니다. 기본적으로이 동작에 없습니다.  

- 낮은은 Office 추가 기능에 대 한 count 임계값을 설치 합니다. 기본 임계값은 `2%`합니다. 이 임계값 보다 추가 기능 자동으로 설정 됩니다 *낮은 설치 수*입니다. 데스크톱 분석 하지는 파일럿 기간 동안 이러한 추가 기능을 확인 합니다. 

    배포 계획에서 추가 기능으로 표시 추가 기능에서이 임계값 보다 높은 비율로 컴퓨터에 설치 된 경우 *Noteworthy*합니다. 그런 다음 파일럿 단계 테스트의 중요성을 결정할 수 있습니다.   



## <a name="importance"></a>중요도

배포 계획의 일부로 설정 합니다 *중요도* 앱 및 Office 추가 기능입니다. 데스크톱 분석 대상 장치에 설치 되어 이러한 앱을 검색 합니다. 이 설정은 데스크톱 Analytics 배포 파일럿 단계에 포함 하는 장치를 확인할 수 있습니다. 

표시 된 앱 또는 추가 기능에서 2% 보다 작은 대상된 장치에 설치 되어 있으면 **낮은 설치 수**입니다. 두 % 기본 값입니다. 10% 0%에서 준비 설정에 대 한 임계값을 조정할 수 있습니다. 이러한 앱 및 추가 기능에 자동으로 데스크톱 분석 표시 **업그레이드할 준비가**합니다.  

앱 및 추가 기능 선택의 중요도 **위험**, **중요**, 또는 **중요 하지 않은**합니다. 중요 하거나 중요 한으로 하나를 표시 하는 경우 데스크톱 분석 해당 앱 또는 추가 기능을 사용 하 여 일부 장치를 파일럿 배포에 포함 합니다. 서비스를 파일럿 실행에 중요 한 앱 또는 추가 기능에서 더 많은 인스턴스를 포함합니다. 앱을 표시 하거나 추가 기능에서 중요 하지 않은 것으로, 데스크톱 Analytics 자동으로로 설정 합니다 **업그레이드할 준비가**합니다.



## <a name="pilot-devices"></a>파일럿 장치

데스크톱 분석 전역 파일럿 설정 사용 하 여 중요 정보를 결합합니다. 그런 다음 장치 파일럿 배포 중 이어야 합니다 하는 권장 사항을 만듭니다. 권장 되는 파일럿 배포에는 여러 하드웨어 구성 사용 하 여 장치 및 모든 중대 및 중요 앱의 인스턴스가 하나 이상 포함 됩니다. 앱 위험으로 표시 된 경우 서비스는 파일럿에서 해당 앱을 사용 하 여 더 많은 장치를 권장 합니다.



## <a name="deployment-plans-in-configuration-manager"></a>Configuration Manager에서 배포 계획

배포 계획을 만든 후 제품을 배포 하려면 Configuration Manager를 사용 합니다. 한 번 배포 시작 데스크톱 분석 계획의 설정에 따라 배포를 모니터링 합니다.

<!--more on deployment plans in SCCM-->

<!-- test comment-->

## <a name="next-steps"></a>다음 단계

- [데스크톱 분석 자산에 대 한 알아봅니다](/sccm/desktop-analytics/about-assets): 장치, 앱, Office 앱, Office 추가 기능 및 Office 매크로  

- [보안 및 기능 업데이트에 알아봅니다](/sccm/desktop-analytics/about-updates)  

- [배포 계획 만들기](/sccm/desktop-analytics/create-deployment-plans)  
