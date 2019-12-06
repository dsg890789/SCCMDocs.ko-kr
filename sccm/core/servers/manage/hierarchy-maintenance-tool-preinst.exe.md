---
title: 계층 유지 관리 도구
titleSuffix: Configuration Manager
description: 계층 유지 관리 도구의 기능과 사용 이유를 이해합니다. 명령줄 옵션 참조를 포함합니다.
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: cead6825-6113-4ba5-a381-ac3598dfee86
author: mestew
ms.author: mstewart
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: c033b7a48aeaf4821a67a277f23b2f672115d105
ms.sourcegitcommit: 1bccb61bf3c7c69d51e0e224d0619c8f608e8777
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "65497540"
---
# <a name="hierarchy-maintenance-tool-preinstexe-for-system-center-configuration-manager"></a>System Center Configuration Manager용 계층 구조 유지 관리 도구(Preinst.exe)

*적용 대상: System Center Configuration Manager(현재 분기)*

계층 유지 관리 도구(Preinst.exe)는 계층 구조 관리자 서비스가 실행되는 동안 System Center Configuration Manager 계층 구조 관리자에 명령을 전달합니다. 계층 유지 관리 도구는 Configuration Manager 사이트를 설치할 때 자동으로 설치됩니다. Preinst.exe는 사이트 서버의 \\&lt;*사이트 서버 이름*>\SMS_&lt;*사이트 코드*\bin\X64\00000409 공유 폴더에 있습니다.  

 다음과 같은 경우에 계층 유지 관리 도구를 사용할 수 있습니다.  

-   보안 키 교환이 필요할 때 사이트 간의 첫 공개 키 교환을 수동으로 수행해야 하는 상황이 있습니다. 자세한 내용은 이 항목의 [사이트 간에 수동으로 공개 키 교환](#BKMK_ManuallyExchangeKeys) 를 참조하십시오.  

-   더 이상 사용할 수 없는 대상 사이트에 대한 활성 작업을 제거하는 경우  

-   설치를 사용하여 사이트를 제거할 수 없을 때 Configuration Manager 콘솔에서 사이트 서버를 삭제하는 경우. 예를 들어 먼저 설치를 실행하여 사이트를 제거하지 않고 Configuration Manager 사이트를 실제로 제거하는 경우 사이트 정보가 상위 사이트의 데이터베이스에 계속 유지되며 상위 사이트가 하위 사이트와 계속 통신합니다. 이 문제를 해결하기 위해서는 계층 유지 관리 도구를 실행하여 상위 사이트의 데이터베이스에 하위 사이트를 수동으로 삭제해야 합니다.  

-   서비스를 개별적으로 중지할 필요 없이 사이트의 Configuration Manager 서비스를 모두 중지하려면  

-   사이트를 복구할 때 CHILDKEYS 옵션을 사용하여 여러 자식 사이트에서 복구 사이트로 공개 키를 배포할 수 있습니다.  

계층 유지 관리 도구를 실행하려면 현재 사용자에게 로컬 컴퓨터에 대한 관리자 권한이 있어야 합니다. 또한 사용자에게 명시적으로 사이트 - 관리자 보안 권한이 있어야 합니다. 사용자가 이 권한을 가진 그룹의 구성원이기 때문에 이 권한을 상속하는 것으로는 부족합니다.  

## <a name="hierarchy-maintenance-tool-command-line-options"></a>계층 유지 관리 도구 명령줄 옵션  
계층 유지 관리 도구를 사용할 때는 중앙 관리 사이트, 기본 사이트 또는 보조 사이트 서버에서 로컬로 실행해야 합니다.  

계층 유지 관리 도구를 실행할 때는 preinst.exe /&lt;옵션\> 구문을 사용해야 합니다. 명령줄 옵션은 다음과 같습니다.  

 **/DELJOB &lt;*사이트 코드*>** - 현재 사이트에서 지정된 대상 사이트로 모든 작업 또는 명령을 삭제하려면 사이트에서 이 옵션을 사용합니다.  

 **/DELSITE &lt;*제거할 하위 사이트 코드*>** - 상위 사이트의 사이트 데이터베이스에서 하위 사이트의 데이터를 삭제하려면 상위 사이트에서 이 옵션을 사용합니다. 일반적으로 이 옵션은 사이트 서버 컴퓨터에서 사이트를 제거하기 전에 사이트 서버 컴퓨터를 사용 중지하는 경우 사용합니다.  

> [!NOTE]  
>  /DELSITE 옵션을 사용해서는 컴퓨터에서 제거할 자식 사이트 코드 매개 변수로 지정된 사이트가 제거되지는 않습니다. 이 옵션은 Configuration Manager 사이트 데이터베이스에서 사이트 정보를 제거하기만 합니다.  

**/DUMP &lt;*사이트 코드*>** - 사이트가 설치되는 드라이브의 루트 폴더에 사이트 제어 이미지를 기록하려면 로컬 사이트 서버에서 이 옵션을 사용합니다. 폴더에 특정 사이트 제어 이미지를 기록하거나 계층의 모든 사이트 제어 파일을 기록할 수 있습니다.  

-   /DUMP &lt;*사이트 코드*>는 지정된 사이트에 대한 사이트 제어 이미지만 기록하고,  

-   /DUMP는 모든 사이트의 사이트 제어 파일을 기록합니다.  

이미지는 사이트 제어 파일의 이진 표현으로서 Configuration Manager 사이트 데이터베이스에 저장됩니다. 덤프된 사이트 제어 파일 이미지는 기본 이미지와 보류 중인 델타 이미지를 합한 것입니다.  

계층 유지 관리 도구로 사이트 제어 파일 이미지를 덤프한 후에는 파일 이름이 sitectrl_&lt;*사이트 코드*>.ct0 형식이 됩니다.  

**/STOPSITE** - Configuration Manager 사이트 구성 요소 관리자 서비스의 종료 주기를 시작하려면 로컬 사이트 서버에서 이 옵션을 사용합니다. 이를 통해 사이트가 부분적으로 다시 설정됩니다. 이 종료 주기가 실행되면 사이트 서버와 원격 사이트 시스템에서 일부 Configuration Manager 서비스가 중지됩니다. 이러한 서비스는 다시 설치하도록 플래그가 지정됩니다. 이 종료 주기의 결과로 서비스가 다시 설치될 때 일부 암호가 자동으로 변경됩니다.  

> [!NOTE]  
>  사이트 구성 요소 관리자의 종료, 재설치 및 암호 변경 기록을 확인하려면 이 명령줄 옵션을 사용하기 전에 이 구성 요소에 로깅을 사용하도록 설정합니다.  

종료 주기가 시작된 후에는 응답하지 않는 구성 요소 또는 컴퓨터를 모두 건너뛰며 자동으로 진행됩니다. 그러나 종료 주기 동안 사이트 구성 요소 관리자 서비스에서 원격 사이트 시스템에 액세스할 수 없는 경우 사이트 구성 요소 관리자 서비스가 다시 시작될 때 원격 사이트 시스템에 설치된 구성 요소가 다시 설치됩니다. 사이트 구성 요소 관리자 서비스가 다시 시작되면 다시 설치하도록 플래그가 지정된 모든 서비스를 다시 설치하며, 성공할 때까지 반복해서 시도합니다.  

Service Manager를 사용하여 사이트 구성 요소 관리자 서비스를 다시 시작할 수 있습니다. 이 서비스가 다시 시작된 후에는 영향을 받는 모든 서비스가 제거된 후 다시 설치되고 다시 시작됩니다. /STOPSITE 옵션을 사용하여 종료 주기를 시작한 후에는 사이트 구성 요소 관리자 서비스가 다시 시작된 후의 다시 설치 주기를 방지할 수 없습니다.  

**/KEYFORPARENT** - 사이트의 공개 키를 부모 사이트에 배포하려면 사이트에서 이 옵션을 사용합니다.  

/KEYFORPARENT 옵션은 프로그램 파일 드라이브 루트에 있는 &lt;*사이트 코드*>.CT4 파일에 사이트 공개 키를 배치합니다. 이 옵션을 사용하여 preinst.exe를 실행한 후에는 &lt;*사이트 코드*>.CT4 파일을 상위 사이트의 ...\Inboxes\hman.box 폴더(hman.box\pubkey가 아님)로 수동 복사합니다.  

**/KEYFORCHILD** - 사이트의 공개 키를 자식 사이트에 배포하려면 사이트에서 이 옵션을 사용합니다.  

/KEYFORCHILD 옵션은 프로그램 파일 드라이브 루트에 있는 &lt;*사이트 코드*>.CT5 파일에 사이트 공개 키를 배치합니다. 이 옵션을 사용하여 preinst.exe를 실행한 후에는 &lt;*사이트 코드*>.CT5 파일을 하위 사이트의 ...\Inboxes\hman.box 폴더(hman.box\pubkey가 아님)로 수동 복사합니다.  

**/CHILDKEYS** - 복구하는 사이트의 자식 사이트에서 이 옵션을 사용할 수 있습니다. 여러 자식 사이트의 공개 키를 복구하는 사이트에 배포하려면 이 옵션을 사용합니다.  

/CHILDKEYS 옵션은 이 옵션을 실행하는 사이트의 키와 해당 사이트의 모든 하위 사이트 공개 키를 &lt;*사이트 코드*>.CT6 파일에 배치합니다.  

이 옵션을 사용하여 preinst.exe를 실행한 후에는 &lt;*사이트 코드*>.CT6 파일을 복구하는 사이트의 ...\Inboxes\hman.box 폴더(hman.box\pubkey가 아님)로 수동 복사합니다.  

**/PARENTKEYS** - 복구하는 사이트의 부모 사이트에서 이 옵션을 사용할 수 있습니다. 모든 부모 사이트의 공개 키를 복구하는 사이트에 배포하려면 이 옵션을 사용합니다.  

/PARENTKEYS 옵션은 이 옵션을 실행하는 사이트의 키와 해당 사이트 상위의 각 상위 사이트의 키를 &lt;사이트 코드\>.CT7 파일에 배치합니다.  

이 옵션을 사용하여 preinst.exe를 실행한 후에는 &lt;*사이트 코드*>.CT7 파일을 복구하는 사이트의 ...\Inboxes\hman.box 폴더(hman.box\pubkey가 아님)로 수동 복사합니다.  

##  <a name="BKMK_ManuallyExchangeKeys"></a> 사이트 간에 수동으로 공개 키 교환  
기본적으로 Configuration Manager 사이트에는 **보안 키 교환 필요** 옵션이 사용됩니다. 보안 키 교환이 필요할 때 사이트 간의 첫 공개 키 교환을 수동으로 수행해야 하는 두 가지 상황이 있습니다.  

-   Configuration Manager를 지원하도록 Active Directory 스키마를 확장하지 않은 경우  

-   Configuration Manager 사이트에서 사이트 데이터를 Active Directory에 게시하지 않는 경우  

계층 유지 관리 도구를 사용하여 각 사이트의 공개 키를 내보낼 수 있습니다. 공개 키를 내보낸 후에는 사이트 간에 수동으로 키를 교환해야 합니다.  

> [!NOTE]  
>  공개 키를 수동으로 교환한 후에는 부모 사이트 서버에서 사이트 구성 변경 내용과 Active Directory Domain Services에 대한 사이트 정보 게시가 기록된 **hman.log** 로그 파일을 검토하여 기본 사이트에서 새 공개 키가 처리되었는지 확인할 수 있습니다.  

#### <a name="to-manually-transfer-the-child-site-public-key-to-the-parent-site"></a>자식 사이트 공개 키를 부모 사이트에 수동으로 전송하려면  

1.  자식 사이트에 로그온해 있는 동안 명령 프롬프트를 열고 **Preinst.exe**위치로 이동합니다.  

2.  다음을 입력하여 자식 사이트의 공개 키를 내보냅니다. **Preinst /keyforparent**  

3.  /keyforparent 옵션은 시스템 드라이브 루트에 있는 **&lt;사이트 코드\>.CT4** 파일에 하위 사이트의 공개 키를 배치합니다.  

4.  **&lt;사이트 코드\>.CT4** 파일을 상위 사이트의 **&lt;설치 디렉터리\>\inboxes\hman.box** 폴더로 이동합니다.  

#### <a name="to-manually-transfer-the-parent-site-public-key-to-the-child-site"></a>부모 사이트 공개 키를 자식 사이트에 수동으로 전송하려면  

1.  부모 사이트에 로그온해 있는 동안 명령 프롬프트를 열고 **Preinst.exe**위치로 이동합니다.  

2.  다음을 입력하여 부모 사이트의 공개 키를 내보냅니다. **Preinst /keyforchild**.  

3.  /keyforchild 옵션은 시스템 드라이브 루트에 있는 **&lt;사이트 코드\>.CT5** 파일에 상위 사이트의 공개 키를 배치합니다.  

4.  **&lt;사이트 코드\>.CT5** 파일을 하위 사이트의 **&lt;설치 디렉터리\>\inboxes\hman.box** 디렉터리로 이동합니다.  
