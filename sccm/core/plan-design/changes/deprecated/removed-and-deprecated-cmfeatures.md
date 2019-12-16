---
title: 사용되지 않는 기능
titleSuffix: Configuration Manager
description: Configuration Manager에서 더 이상 지원하지 않는 기능에 대해 알아보세요.
ms.date: 11/29/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 287a6324-ae65-4d38-b2ef-198d47c91231
author: mestew
ms.author: mstewart
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: edcb5a5eed46f4b58799789014115c1b454cb7a5
ms.sourcegitcommit: 1bccb61bf3c7c69d51e0e224d0619c8f608e8777
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74660753"
---
# <a name="removed-and-deprecated-features-for-configuration-manager"></a>Configuration Manager에서 제거되는 기능과 이후 지원되지 않는 기능

*적용 대상: Configuration Manager(현재 분기)*

이 문서에서는 사용되지 않거나 Configuration Manager에 대한 지원에서 제거된 기능을 나열합니다. 사용되지 않는 기능은 향후 업데이트에서 제거될 예정입니다. 향후 이러한 변경 사항은 Configuration Manager 사용에 영향을 줄 수 있습니다.  

이 정보는 향후 릴리스에서 변경 대상입니다. 사용되지 않는 각 Configuration Manager 기능을 포함하지 않을 수 있습니다.

## <a name="deprecated-features"></a>사용되지 않는 기능

다음 기능은 사용되지 않습니다. 지금은 사용할 수 있지만 Microsoft에서 향후 지원을 종료할 계획입니다.

|기능|처음 중단 발표|제거된&nbsp;지원|  
|-----------|---|--------------|  
| [Windows Analytics](/sccm/core/clients/manage/monitor-windows-analytics) 및 [업그레이드 준비](/sccm/core/clients/manage/upgrade-readiness) 통합. 자세한 내용은 [KB 4521815: 2020년 1월 31일 Windows Analytics 사용 중지](https://support.microsoft.com/help/4521815/windows-analytics-retirement)를 참조하세요. | 2019년 10월 14일 | 2020년 1월 31일 |
|Azure 콘텐츠 공유를 위한 구현이 변경되었습니다. 콘텐츠 지원 클라우드 관리 게이트웨이를 사용합니다. 나중에는 기존 클라우드 배포 지점을 만들 수 없습니다.|2019년 2월|TBD<sup>[참고 1](#bkmk_note1)</sup>|
|클라우드 관리 게이트웨이 및 클라우드 배포 지점에 대한 클래식 서비스 배포. 자세한 내용은 [CMG 계획](/sccm/core/clients/manage/cmg/plan-cloud-management-gateway#azure-resource-manager)을 참조하세요.|2018년 11월|TBD<sup>[참고 1](#bkmk_note1)</sup>|

### <a name="bkmk_note1"></a> 참고 1: 제거된 지원 TBD

특정 시간 범위가 결정될 것입니다(TBD). 새 프로세스나 기능으로 변경하는 것이 좋지만, 곧 사용되지 않는 프로세스나 기능을 계속 사용할 수 있습니다.

## <a name="unsupported-and-removed-features"></a>지원되지 않는 기능 및 제거된 기능

다음 기능은 더 이상 지원되지 않습니다. 경우에 따라 이 기능은 제품에 더 이상 포함되지 않습니다.

|기능|처음 중단 발표|제거된&nbsp;지원|  
|-----------|---|--------------|  
| 조건부 액세스의 준수 정책에 대한 디바이스 상태 증명 평가 <!--1235616 aka 3608202--> 자세한 내용은 [Configuration Manager에서 관리되는 PC용 Office 365 서비스에 대한 액세스 관리](/sccm/mdm/deploy-use/manage-access-to-o365-services-for-pcs-managed-by-sccm#step-1-configure-compliance-policy)를 참조하세요.| 2019년 7월 3일 | 버전 1910 |
| Configuration Manager 회사 포털 앱 | 2019년 5월 21일 | 버전 1910 |
| 애플리케이션 카탈로그 웹 사이트 지점과 웹 서비스 지점 등, 두 사이트 서비스 역할을 포함한 애플리케이션 카탈로그. 자세한 정보는 [애플리케이션 카탈로그 제거](/sccm/apps/plan-design/plan-for-and-configure-application-management#bkmk_remove-appcat)를 참조하세요. | 2019년 5월 21일 | 버전 1910 |
|Configuration Manager의 비즈니스용 Windows Hello의 인증서 기반 인증<br>자세한 내용은 [비즈니스용 Windows Hello 설정](/sccm/protect/deploy-use/windows-hello-for-business-settings)을 참조하세요.|2017년 12월|버전 1910|
|Mac 및 Linux용 System Center Endpoint Protection<br>자세한 내용은 [지원 종료 블로그 게시물](https://go.microsoft.com/fwlink/?linkid=870182)을 참조하세요.|2018년 10월|2018년 12월 31일|
|온-프레미스 조건부 액세스<br>자세한 내용은 [하이브리드 MDM의 개념](/sccm/mdm/understand/hybrid-mobile-device-management)을 참조하세요.|2019년 1월 30일|2019년 9월 1일|
|MDM(하이브리드 모바일 디바이스 관리)<br>자세한 내용은 [하이브리드 MDM의 개념](/sccm/mdm/understand/hybrid-mobile-device-management)을 참조하세요.<br><br>2019년 2월 말로 예정된 1902 Intune 서비스 릴리스부터, 신규 고객은 새 하이브리드 연결을 만들 수 없습니다.<!--Intune feature 2683117-->|2018년 8월 14일|2019년 9월 1일|
|애플리케이션 카탈로그 웹 사이트 지점에 대한 **Silverlight 사용자 환경**은 더 이상 지원되지 않습니다. 사용자는 새로운 소프트웨어 센터를 사용해야 합니다. 자세한 내용은 [소프트웨어 센터 구성](/sccm/apps/plan-design/plan-for-software-center#bkmk_userex)을 참조하세요.<!--1358309-->|2017년 8월 11일| 버전 1806|
|이전 버전의 Software Center입니다.<br><br>새 소프트웨어 센터에 대한 자세한 내용은 [애플리케이션 관리 계획 및 구성](/sccm/apps/plan-design/plan-for-and-configure-application-management##bkmk_userex)을 참조하세요.|2016년 12월 13일|1802 버전|
|Configuration Manager를 사용한 VHD(가상 하드 디스크) 관리 <br><br>이 사용 중단에은 새 VHD를 만들거나 작업 순서를 사용하여 VHD를 관리하는 옵션의 제거 및 Configuration Manager 콘솔에서 가상 하드 디스크 노드의 제거가 포함됩니다. <br><br>기존 VHD는 삭제되지는 않지만 Configuration Manager 콘솔 내에서 더 이상 액세스할 수 없습니다.  |2017년 1월 6일 |버전 1710|
|작업 순서: <br /> - 동적 디스크로 변환 <br /> - 배포 도구 설치 |2016년 11월 18일|버전 1710|
|업그레이드 평가 도구<br><br>업그레이드 평가 도구를 사용하려면 Configuration Manager 및 ACT(Application Compatibility Toolkit) 6.x가 둘 다 필요합니다. ACT의 최종 버전은 Windows 10 v1511 ADK에 함께 제공되었습니다. ACT에 대한 추가 업데이트는 없으므로 업그레이드 평가 도구에 대한 지원은 중단됩니다. <br><br>업그레이드 평가 도구는 [Upgrade Readiness](/sccm/core/clients/manage/upgrade/upgrade-analytics) 기능으로 대체됩니다. 2016년 9월 12일에 사용 고지 사항이 [UAT에 대한 다운로드 페이지](https://www.microsoft.com/software-download/windows10)에 추가되었습니다. | 2016년 9월 12일  | 2017년 7월 11일 |
|NLB(네트워크 부하 분산) 클러스터 사용 소프트웨어 업데이트 지점 | 2016년 2월 27일 | 버전 1702 |
|작업 순서: <br /> - OSDPreserveDriveLetter  <br /><br /> 기본적으로 운영 체제 배포 시 Windows 설치 프로그램이 이제 사용하기에 가장 적합한 드라이브 문자(일반적으로 C:)를 결정합니다. 다른 드라이브를 사용하도록 지정하려면 운영 체제 적용 작업 순서 단계에서 위치를 변경할 수 있습니다. **이 운영 체제를 적용할 위치를 선택하십시오** 설정으로 이동합니다. **특정 논리적 드라이브 문자**를 선택하고 사용하려는 드라이브를 선택합니다. |2016년 6월 20일 |버전 1606 |
|NAP(네트워크 액세스 보호) - System Center 2012 Configuration Manager에 있음|2015년 7월 10일|버전 1511|  
|대역 외 관리 - System Center 2012 Configuration Manager에 있음|2015년 10월 16일|버전 1511|

### <a name="features-removed-in-version-1511"></a>버전 1511에서 제거된 기능

다음 섹션에는 버전 1511에서 제거된 기능에 대한 추가 정보가 포함됩니다.

#### <a name="bkmk_amt"></a> 대역 외 관리  

Configuration Manager에서 Configuration Manager 콘솔 내의 AMT 기반 컴퓨터에 대한 기본 지원이 제거되었습니다.  

- [Configuration Manager용 Intel SCS 추가 기능](https://www.intel.com/content/www/us/en/software/setup-configuration-software.html)을 사용하는 경우 AMT 기반 컴퓨터가 완전히 관리되는 상태로 유지됩니다. 추가 기능을 사용하면 AMT를 관리할 최신 기능에 액세스하고 Configuration Manager가 해당 변경 사항을 통합할 수 있을 때까지 도입된 제한 사항을 제거할 수 있습니다.  

- System Center 2012 Configuration Manager의 대역 외 관리는 이 변경 사항에 의해 영향을 받지 않습니다.  

#### <a name="bkmk_nap"></a> 네트워크 액세스 보호

Configuration Manager에서 네트워크 액세스 보호에 대한 지원이 제거되었습니다. 이 기능은 Windows Server 2012 R2부터 사용되지 않으며 Windows 10에서 제거됩니다.  

네트워크 액세스 보호를 위한 대체 방법은 *네트워크 정책 및 액세스 서비스 개요* 의 [사용되지 않는 기능](https://technet.microsoft.com/library/hh831683.aspx)섹션을 참조하세요.

## <a name="see-also"></a>참고 항목

- [제거되는 기능과 사용되지 않는 기능](/sccm/core/plan-design/changes/deprecated/removed-and-deprecated)
- [Microsoft 지원 기간](https://support.microsoft.com/lifecycle)
- [Configuration Manager 현재 분기 버전에 대한 지원](/sccm/core/servers/manage/current-branch-versions-supported)
