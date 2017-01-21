---
title: "Configuration Manager와 장치 등록 관리자를 사용하여 장치 등록"
description: "System Center Configuration Manager와 장치 등록 관리자 계정을 사용하여 회사 소유 장치를 등록합니다."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2905f26e-7859-497d-b995-5ff48261efa2
caps.latest.revision: 8
author: NathBarn
ms.author: nathbarn
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 1134bb2f04152288e72d40b1b1083f415cb4e900
ms.openlocfilehash: 287815a534c1fba8af8f5d212c6321bda93fc44f


---
# <a name="enroll-devices-with-device-enrollment-manager-with-configuration-manager"></a>Configuration Manager와 장치 등록 관리자를 사용하여 장치 등록

*적용 대상: System Center Configuration Manager(현재 분기)*

조직에서는 System Center Configuration Manager 및 Intune을 사용하여 단일 사용자 계정으로 많은 수의 모바일 장치를 관리할 수 있습니다. *장치 등록 관리자* 계정은 5개가 넘는 장치를 등록할 수 있는 권한이 있는 특수한 Intune 계정입니다.  

## <a name="enroll-corporate-owned-devices-with-the-device-enrollment-manager"></a>장치 등록 관리자로 회사 소유 장치 등록  
 예를 들어, 저장소 관리자나 감독자에게 장치 등록 관리자 사용자 계정을 할당하여 다음 작업을 수행하도록 할 수 있습니다.  

-   관리를 위해 장치 등록  

-   회사 포털 앱을 사용하여 회사 앱 설치  

-   소프트웨어 설치 및 제거  

-   회사 데이터에 대한 액세스 구성  


장치 등록 관리자 계정을 사용하여 관리되는 장치에 다음과 같은 제한 사항이 적용됩니다.

- 저장소 관리자는 회사 포털에서 장치를 리셋할 수 없습니다.  
-  장치가 작업 영역에 연결되거나 Azure Active Directory에 연결될 수 없습니다. 이렇게 되면 해당 장치가 조건부 액세스를 사용할 수 없습니다.
-  장치 등록 관리자를 사용하여 관리되는 장치에 회사 앱을 배포하려면 **필수 설치**인 회사 포털 앱을 장치 등록 관리자의 사용자 계정에 배포합니다. 그런 다음 장치 등록 관리자는 회사 포털 앱을 시작하여 추가 앱을 설치할 수 있습니다.
- 성능 향상을 위해 회사 포털 앱은 로컬 장치만 표시합니다. 다른 DEM 장치의 원격 관리는 Configuration Manager 콘솔에서 관리자만 수행할 수 있습니다.
- 회사 포털 웹 사이트는 장치 등록 관리자 계정에 사용할 수 없습니다. 회사 포털 앱을 사용합니다.

 **장치 등록 관리자 시나리오의 예:**   
식당에는 서빙 직원을 위한 POS 태블릿과 주방 직원을 위한 주문 모니터가 필요합니다. 직원들이 회사 데이터에 액세스하거나 사용자로 로그온할 필요는 없습니다. Intune 관리자는 장치 등록 관리자 계정을 만들고 해당 계정을 사용하여 회사 소유의 장치를 등록합니다. 또는 관리자는 식당 관리자에게 장치 등록 관리자 자격 증명을 제공하여 장치를 등록하고 관리할 수 있도록 합니다.  

 관리자는 역할별 앱을 식당의 장치에 배포할 수 있습니다. 또한 관리자는 콘솔에서 장치를 선택하고 모바일 장치 관리에서 사용을 중지할 수도 있습니다.  

#### <a name="add-a-device-enrollment-manager"></a>장치 등록 관리자 추가  

1.  Configuration Manager 콘솔에서 **관리**를 클릭합니다.  

2.  **관리** 작업 영역에서 **클라우드 서비스**를 확장하고 **Microsoft Intune 구독**을 클릭합니다. 장치 등록 관리자를 추가할 Microsoft Intune 구독을 선택한 후 **속성**을 클릭합니다.  

3.  Microsoft Intune 구독 속성 대화 상자에서 **장치 등록 관리자** 탭을 클릭합니다.  

4.  **추가/제거**를 클릭합니다.  

5.  **장치 등록 관리자** 대화 상자에서 장치 등록 관리자로 추가할 사용자의 사용자 이름을 입력하고 **검색**을 클릭합니다. 장치 등록 관리자로 추가할 사용자를 선택하고 **추가**를 클릭합니다.  

6.  장치 등록 관리자가 될 사용자 계정을 확인하고 **추가/제거**를 클릭합니다.  서비스 및 Intune 관리자가 될 수 없는 *장치 등록 관리자*에 액세스하는 각 사용자에게는 구독 라이선스가 필요합니다. 이 기능을 사용하기 전에 다른 라이선스를 추가해야 하는지 여부를 결정합니다.  

7.  이제 장치 등록 관리자는 최종 사용자가 회사 포털에서 BYOD(bring-your-own-device) 시나리오일 때 이용하는 동일한 절차를 통해 모바일 장치를 등록할 수 있습니다.  

#### <a name="delete-a-device-enrollment-manager-from-intune"></a>Intune에서 장치 등록 관리자 삭제  

1.  Configuration Manager 콘솔에서 **관리**를 클릭합니다.  

2.  **관리** 작업 영역에서 **클라우드 서비스**를 확장하고 **Microsoft Intune 구독**을 클릭합니다. 장치 등록 관리자를 추가할 Microsoft Intune 구독을 선택한 후 **속성**을 클릭합니다.  

3.  Microsoft Intune 구독 속성 대화 상자에서 **장치 등록 관리자** 탭을 클릭합니다.  

4.  삭제하려는 장치 등록 관리자를 **검색**하고 **제거**를 클릭한 후 **확인**을 클릭합니다.  

 장치 등록 관리자를 삭제해도 등록된 장치에는 영향을 주지 않습니다. 장치 등록 관리자를 삭제하는 경우:  

-   등록된 장치는 영향을 받지 않습니다.  

-   등록된 장치는 계속 완벽하게 관리됩니다.  

-   삭제된 장치 등록 관리자 계정의 자격 증명은 회사 포털에 로그온하여 앱에 액세스할 수 있도록 유효한 상태로 유지됩니다.  

-   삭제된 장치 등록 관리자 계정 자격 증명으로는 여전히 장치를 초기화하거나 사용 중지할 수 없습니다.  

-   등록된 장치에 대한 삭제된 장치 등록 관리자 계정의 관계는 유지되지만 추가 장치를 등록할 수는 없습니다.



<!--HONumber=Nov16_HO1-->


