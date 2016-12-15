---
title: "Windows Embedded 응용 프로그램 만들기 | Microsoft 문서"
description: "Windows Embedded 장치용 응용 프로그램을 만들고 배포할 때 고려해야 할 사항을 확인합니다."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 16acfd63-0c40-424c-82f4-8c63f7f1c30b
caps.latest.revision: 7
author: robstackmsft
ms.author: robstack
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 557888d1f1f899e3198c430bbe5ccdd44178f824
ms.openlocfilehash: cb0c22f3060ba654778dca958d620f1e1725b93c


---
# <a name="create-windows-embedded-applications-with-system-center-configuration-manager"></a>System Center Configuration Manager를 사용하여 Windows Embedded 응용 프로그램 만들기

*적용 대상: System Center Configuration Manager(현재 분기)*

응용 프로그램을 만들기 위한 다른 System Center Configuration Manager 요구 사항 및 절차 외에도 Windows Embedded 장치에 대한 응용 프로그램을 만들어 배포할 때는 다음 사항을 고려해야 합니다.  

## <a name="general-considerations"></a>일반적인 고려 사항  

-   쓰기 필터를 사용하도록 설정된 Windows Embedded 장치에 응용 프로그램을 배포할 경우 앱 배포 중 장치에서 쓰기 필터를 사용하지 않도록 설정할지를 지정할 수 있습니다. 그런 다음 앱 배포 후 쓰기 필터를 다시 시작할 수 있습니다. 쓰기 필터가 비활성화되어 있지 않으면 소프트웨어가 임시 오버레이에 배포됩니다. 즉, 다른 배포에서 변경 내용을 강제로 영구 적용하는 경우가 아니면 장치를 다시 시작할 때 소프트웨어가 더 이상 설치되지 않습니다.  

-   Windows Embedded 장치에 응용 프로그램을 배포하는 경우 장치가 유지 관리 기간이 구성된 컬렉션의 구성원이어야 합니다. 이에 따라 쓰기 필터의 비활성 및 활성 시점과 장치가 다시 시작하는 시점을 관리할 수 있습니다.  

-   쓰기 필터 동작을 제어하는 설정은 이름이 **최종 기한에 또는 유지 관리 기간에 변경 내용 커밋(다시 시작해야 함)**인 확인란입니다.  

## <a name="tips-for-deploying-applications"></a>응용 프로그램 배포에 대한 팁  

**쓰기 필터를 사용하도록 설정된 Windows Embedded 장치에는 사용 가능한 응용 프로그램이 아니라 필수 응용 프로그램을 사용합니다.** 쓰기 필터를 사용하도록 설정된 Windows Embedded 장치에서는 사용자가 소프트웨어 센터를 통해 앱을 설치할 수 없으므로, 이러한 장치에는 항상 **사용 가능**이 아닌 **필수** 배포용 응용 프로그램을 배포합니다. 일반적으로 Windows Embedded 운영 체제를 실행하는 컴퓨터에서는 여러 사용자에 대해 동일한 방식으로 실행해야 하는 단일 응용 프로그램을 실행하는 경우가 많으므로 이렇게 배포해도 문제가 없습니다. 이로 인해 이러한 장치는 IT 부서에서 엄격하게 관리되고 통제됩니다. 필수 응용 프로그램이 이 시나리오에 적합합니다.

 그러나 사용자가 임베디드 장치에서 쓰기 필터를 사용할 때 둘 이상의 응용 프로그램을 실행하는 경우 해당 사용자에게 다음과 같은 제한 사항을 알려 주십시오.  

-   사용자는 소프트웨어 센터에서 필수 소프트웨어를 설치할 수 없습니다.  

-   사용자는 소프트웨어 센터의 옵션 탭에서 근무 시간을 변경할 수 없습니다.  

-   사용자는 필수 응용 프로그램의 설치를 연기할 수 없습니다.  

또한 Configuration Manager에서 소프트웨어 설치 및 업데이트를 위해 변경 내용을 커밋하는 경우 권한이 낮은 사용자는 유지 관리 기간 동안 로그온할 수 없습니다. 이 기간 동안에는 장치가 서비스되고 있으므로 사용할 수 없음을 알리는 메시지가 표시됩니다.  

**사용자가 사용 조건에 동의해야 응용 프로그램을 사용할 수 있는 경우에는 쓰기 필터를 사용하도록 설정된Windows Embedded 장치에 응용 프로그램을 배포하지 마세요.** Configuration Manager에서 임베디드 장치에 소프트웨어를 설치할 수 있도록 쓰기 필터를 사용하지 않도록 설정하면 권한이 낮은 사용자는 장치에 로그온할 수 없습니다. 설치를 위해 사용자가 사용 조건에 동의해야 하는 경우에는 설치가 불가능하여 설치에 실패합니다. 설치를 위해 사용자 작업이 필요한 경우에는 Windows Embedded 장치에 소프트웨어를 배포하지 않도록 합니다. 적용되는 플랫폼 목록을 사용하면 이러한 운영 체제를 필터링할 수 있습니다.  



<!--HONumber=Dec16_HO1-->


