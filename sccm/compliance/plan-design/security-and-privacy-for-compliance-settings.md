---
title: "준수 설정에 대한 보안 및 개인 정보 | System Center Configuration Manager"
description: "System Center Configuration Manager에서 준수 설정에 대한 보안 모범 사례에 대해 알아봅니다."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1c409244-6778-4970-a99c-d2508c9cf62b
caps.latest.revision: 5
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 1134bb2f04152288e72d40b1b1083f415cb4e900
ms.openlocfilehash: 93b0f19cade91a987900c128fdbd80bb68bc186f


---
# <a name="security-and-privacy-for-compliance-settings-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 준수 설정에 대한 보안 및 개인 정보

*적용 대상: System Center Configuration Manager(현재 분기)*


## <a name="security-best-practices-for-compliance-settings"></a>준수 설정에 대한 보안 모범 사례  

|보안 모범 사례|추가 정보|  
|----------------------------|----------------------|  
|중요한 데이터를 모니터링하지 마세요.|정보 공개를 방지하려면 잠재적으로 중요한 정보를 모니터링하는 구성 항목을 구성하지 마세요.|  
|최종 사용자가 수정할 수 있는 데이터를 사용하도록 호환성 규칙을 구성하지 않습니다.|구성 선택 항목에 대한 레지스트리 설정과 같이 사용자가 수정할 수 있는 데이터를 기반으로 한 준수 규칙을 만드는 경우 준수 결과를 신뢰할 수 없습니다.|  
|신뢰할 수 있는 게시자의 유효한 디지털 서명이 있는 경우에만 외부 원본에서 Microsoft System Center 구성 팩 및 기타 구성 데이터를 가져옵니다.|게시된 구성 데이터는 게시 원본을 확인하고 데이터가 변조되지 않았음을 확인할 수 있도록 디지털 서명될 수 있습니다. 디지털 서명 확인 검사에 실패하는 경우 경고를 받고 가져오기를 계속할 것인지 묻는 메시지가 표시됩니다. 데이터의 원본 및 무결성을 확인할 수 없는 경우 서명되지 않은 데이터를 가져오지 마세요.|  
|참조 컴퓨터를 보호하도록 액세스 제어 구현|관리자가 참조 컴퓨터를 검색하여 레지스트리 또는 파일 시스템 설정을 구성할 때 참조 컴퓨터가 손상되지 않았는지 확인합니다.|  
|참조 컴퓨터를 찾아볼 때 통신 채널을 보호합니다.|네트워크를 통해 데이터를 전송할 때 데이터가 변조되지 않도록 하려면 Configuration Manager 콘솔을 실행하는 컴퓨터와 참조 컴퓨터 간에 IPSec(인터넷 프로토콜 보안) 또는 SMB(서버 메시지 블록)를 사용합니다.|  
|준수 설정 관리자 역할 기반 보안 역할이 부여된 관리자를 제한하고 모니터링합니다.|**준수 설정 관리자** 역할이 부여된 관리자는 모든 장치 및 계층의 모든 사용자에게 구성 항목을 배포할 수 있습니다. 구성 항목은 매우 강력할 수 있고 예를 들어 스크립트 및 레지스트리 재구성을 포함할 수 있습니다.|  

## <a name="privacy-information-for-compliance-settings"></a>준수 설정에 대한 개인 정보  
 준수 설정을 사용하여 클라이언트 장치가 구성 기준에서 배포하는 구성 항목이 규격을 준수하는지 여부를 평가할 수 있습니다. 일부 설정은 준수하지 않는 경우 자동으로 재구성될 수 있습니다. 호환성 정보는 관리 지점에 의해 사이트 서버로 전송되고 사이트 데이터베이스에 저장됩니다. 장치에서 관리 지점으로 정보를 보낼 때 정보가 암호화되지만 사이트 데이터베이스에는 암호화된 형식으로 저장되지 않습니다. 정보는 사이트 유지 관리 작업인 **오래된 구성 관리 데이터 삭제** 에 의해 90일마다 삭제될 때까지 데이터베이스에 유지됩니다. 삭제 간격은 필요에 따라 구성할 수 있습니다. 호환성 정보는 Microsoft로 전송되지 않습니다.  

 기본적으로 장치는 준수 설정을 평가하지 않습니다. 또한 구성 항목과 구성 기준을 구성한 다음 장치에 배포해야 합니다.  



<!--HONumber=Nov16_HO1-->


