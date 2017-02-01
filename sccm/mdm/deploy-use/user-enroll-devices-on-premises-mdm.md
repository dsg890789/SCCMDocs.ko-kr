---
title: "사용자가 온-프레미스 MDM을 사용하여 장치를 등록하는 방법 - Configuration Manager | Microsoft 문서"
description: "System Center Configuration Manager의 온-프레미스 모바일 장치 관리를 사용하여 장치를 등록하는 방법을 이해합니다."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 59004b34-b64f-4d77-898c-07bf3dc75430
caps.latest.revision: 9
caps.handback.revision: 0
author: Mtillman
ms.author: mtillman
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 991eff171dce95590a7f050e0d3b07f98c0224b3
ms.openlocfilehash: 43a30709473939829d82d822503537d448159a1c


---
# <a name="how-users-enroll-devices-with-on-premises-mobile-device-management-in-system-center-configuration-manager"></a>System Center Configuration Manager의 온-프레미스 모바일 장치 관리를 사용하여 장치를 등록하는 방법

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager 온-프레미스 모바일 장치 관리에서, 등록 권한이 부여된 사용자가 장치를 등록할 수 있으며(업데이트된 클라이언트 설정을 통해) 장치에는 필요한 사이트 시스템 역할을 호스트하는 서버와 신뢰할 수 있는 통신을 설정하기 위해 필요한 루트 인증서가 설치됩니다. 등록을 설정하는 방법에 대한 자세한 내용은 [System Center Configuration Manager의 온-프레미스 모바일 장치 관리를 위한 장치 등록 설정](../../mdm/get-started/set-up-device-enrollment-on-premises-mdm.md)을 참조하세요.  

 > [!NOTE]  
>  현재 분기의 Configuration Manager는 다음 운영 체제를 실행하는 장치에 대한 온-프레미스 모바일 장치 관리에서의 등록을 지원합니다.  
>   
>  -  Windows 10 Enterprise  
> -   Windows 10 Pro  
> -   Windows 10 Team\(Configuration Manager 버전 1602 이상\)  
> -   Windows 10 Mobile  
> -   Windows 10 Mobile Enterprise

다음 작업에서는 온\-프레미스 모바일 장치 관리에 대해 컴퓨터 및 장치를 등록하고 등록을 확인하는 방법을 설명합니다.  

-   [Windows 10 컴퓨터 등록](#bkmk_enrollDesk)  

-   [Windows 10 모바일 장치 등록](#bkmk_enrollMob)  

-   [장치 등록 확인](#bkmk_verify)  

##  <a name="a-namebkmkenrolldeska-enroll-a-windows-10-computer"></a><a name="bkmk_enrollDesk"></a> Windows 10 컴퓨터 등록  

1.  Windows 10 컴퓨터에서 **설정**으로 이동합니다.  

2.  **계정**을 클릭하고, **회사 액세스**를 클릭합니다.  

3.  회사 액세스의 **회사 또는 학교에 연결**에서, **연결**을 클릭하고, 업무용 메일 주소를 입력하고 **계속**을 클릭합니다.  

4.  등록 프록시 지점 사이트 시스템 역할을 호스트하는 서버의 FQDN을 입력하고 **계속**을 클릭합니다.  

5.  서비스에 연결 중에서, 업무용 메일 암호를 입력하고 **로그인**을 클릭합니다.  

6.  로그인 정보를 기억하기 위해 **건너뛰기** 를 클릭하면 잠시 후에 장치가 연결됩니다.  

##  <a name="a-namebkmkenrollmoba-enroll-a-windows-10-mobile-device"></a><a name="bkmk_enrollMob"></a> Windows 10 모바일 장치 등록  

1.  Windows 10 모바일 장치에서 **설정**으로 이동합니다.  

2.  **계정**을 클릭하고, **회사 액세스**를 클릭합니다.  

3.  **연결**을 클릭합니다.  

4.  업무용 메일 주소 및 등록 프록시 지점 사이트 시스템 역할을 호스트하는 서버의 FQDN을 입력합니다. **연결**을 클릭합니다.  

5.  다음 화면에서 업무용 메일 주소 및 암호를 입력한 다음 **로그인**을 클릭합니다. 잠시 후 장치가 등록됩니다. **완료**를 클릭합니다.  

##  <a name="a-namebkmkverifya-verify-device-enrollment"></a><a name="bkmk_verify"></a> 장치 등록 확인  
 Configuration Manager 콘솔에서 장치가 성공적으로 등록되었는지 확인할 수 있습니다.  

1.  Configuration Manager 콘솔을 시작합니다.  

2.  마법사를 종료하려면 **자산 및 준수** > **개요** > **장치**에 필요한 사이트 시스템 역할 간의 신뢰할 수 있는 통신에 필요합니다. 등록된 장치가 목록에 표시됩니다.  

## <a name="see-also"></a>참고 항목  
 [System Center Configuration Manager의 온-프레미스 모바일 장치 관리를 위한 장치 등록](../../mdm/deploy-use/enroll-devices-on-premises-mdm.md)



<!--HONumber=Jan17_HO4-->


