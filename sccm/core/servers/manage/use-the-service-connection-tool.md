---
title: "서비스 연결 도구 | Microsoft 문서"
description: "Configuration Manager 클라우드 서비스에 연결하여 사용 정보를 수동으로 업로드할 수 있는 이 도구에 대해 알아봅니다."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6e4964c5-43cb-4372-9a89-b62ae6a4775c
caps.latest.revision: 11
author: Brenduns
ms.author: brenduns
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: b4642186e42745640f088b7046e70019616935ea
ms.openlocfilehash: 9a5cd5ce3ce6868b44768d3cbe7b7c594f44d42c
ms.lasthandoff: 12/16/2016


---
# <a name="use-the-service-connection-tool-for-system-center-configuration-manager"></a>System Center Configuration Manager의 서비스 연결 도구 사용

*적용 대상: System Center Configuration Manager(현재 분기)*

Configuration Manager 사이트 시스템 서버가 인터넷에 연결되어 있지 않지만 Configuration Manager의 최신 업데이트로 최신 상태를 유지하려는 경우 **서비스 연결 도구** 를 사용합니다.  

 이 도구를 사용하면 Configuration Manager 클라우드 서비스에 연결하여 계층 구조에 대한 사용 정보를 수동으로 업로드하고 업데이트를 다운로드할 수 있습니다. 클라우드 서비스에서 배포에 올바른 업데이트를 제공할 수 있으려면 사용 데이터를 업로드해야 합니다.  

## <a name="prerequisites-for-using-the-service-connection-tool"></a>서비스 연결 도구를 사용하기 위한 필수 조건
필수 조건 및 알려진 문제는 다음과 같습니다.

**필수 조건:**

-   서비스 연결 지점이 설치되어 있고 **오프라인, 주문형 연결**로 설정되었습니다.  

-   명령 프롬프트에서 도구를 실행해야 합니다.  

-   도구가 실행되는 각 컴퓨터(서비스 연결 지점 컴퓨터 및 인터넷에 연결된 컴퓨터)는 x64비트 시스템이고 다음 요소가 설치되어 있어야 합니다.  

    -   **Visual C++ 재배포 가능 패키지** x86 및 x64 파일 모두.   기본적으로 Configuration Manager는 서비스 연결 지점을 호스트하는 컴퓨터에 x64 버전을 설치합니다.  

         Visual C++ 파일의 복사본을 다운로드하려면 Microsoft 다운로드 센터에서 [Visual Studio 2013용 Visual C++ 재배포 가능 패키지](http://www.microsoft.com/download/details.aspx?id=40784) 를 방문하세요.  

    -   .NET Framework 4.5.2 이상  

-   이 도구를 실행하는 데 사용할 계정에는 다음과 같은 권한이 있어야 합니다.
    -   서비스 연결 지점을 호스트하는(도구가 실행되는) 컴퓨터에 대한**로컬 관리자** 권한
    -   사이트 데이터베이스에 대한**읽기** 권한  



-   파일 및 업데이트를 저장할 수 있는 충분한 여유 공간이 있는 USB 드라이브나, 서비스 연결 지점 컴퓨터와 인터넷에 액세스할 수 있는 컴퓨터 간에 파일을 전송하는 다른 방법이 필요합니다. 이 시나리오에서는 사이트와 관리되는 컴퓨터가 인터넷에 직접 연결되어 있지 않다고 가정합니다.  



## <a name="use-the-service-connection-tool"></a>서비스 연결 도구 사용  

 서비스 연결 도구(**serviceconnectiontool.exe**)는 Configuration Manager 설치 미디어의 **%path%\smssetup\tools\ServiceConnectionTool** 폴더에 있습니다. 항상 사용하는 Configuration Manager 버전과 일치하는 서비스 연결 도구를 사용합니다.


 이 절차에서 명령줄 예제는 다음 파일 이름과 폴더 위치를 사용합니다. 이러한 경로와 파일 이름 대신 사용자 환경 및 기본 설정에 맞는 대체 경로와 이름을 사용해도 됩니다.  

-   서버 간 전송을 위해 데이터가 저장되는 USB 스틱의 경로: **D:\USB\\**  

-   사이트에서 내보낸 데이터가 포함된 .cab 파일의 이름: **UsageData.cab**  

-   Configuration Manager에 대해 다운로드한 업데이트가 서버 간 전송을 위해 저장되는 빈 폴더의 이름: **UpdatePacks**  

서비스 연결 지점을 호스트하는 컴퓨터:  

-   관리자 권한으로 명령 프롬프트를 열고 디렉터리를 **serviceconnectiontool.exe**가 포함된 위치로 변경합니다.  

     기본적으로 이 도구는 Configuration Manager 설치 미디어의 **%path%\smssetup\tools\ServiceConnectionTool** 폴더에 있습니다. 서비스 연결 도구가 작동하려면 이 폴더의 모든 파일이 동일한 폴더에 있어야 합니다.  

다음 명령을 실행하면 이 도구에서 사용 정보를 포함하는 .cab 파일을 준비하고 지정된 위치로 복사합니다. .cab 파일의 데이터는 사이트가 수집하도록 구성된 진단 사용 현황 데이터의 수준을 기반으로 합니다. [System Center Configuration Manager의 진단 및 사용 현황 데이터](../../../core/plan-design/diagnostics/diagnostics-and-usage-data.md)를 참조하세요.  다음 명령을 실행하여 .cab 파일을 만듭니다.  

-   **serviceconnectiontool.exe -prepare -usagedatadest D:\USB\UsageData.cab**  

모든 내용이 포함된 ServiceConnectionTool 폴더를 USB 드라이브에 복사하거나, 3 및 4단계를 사용할 컴퓨터에서 사용할 수 있도록 해야 합니다.  

### <a name="overview"></a>개요
**서비스 연결 도구를 사용하는 세 가지 기본 단계는 다음과 같습니다.**  

1.  **준비**: 이 단계에서는 사용 데이터를 .cab 파일에 넣고 USB 드라이브(또는 지정한 대체 전송 위치)에 저장합니다.  

2.  **연결**: 이 단계에서는 인터넷에 연결하여 데이터를 업로드하고 업데이트를 다운로드하는 원격 컴퓨터에서 도구를 실행합니다.  

3.  **가져오기**: 이 단계에서는 Configuration Manager 콘솔에서 업데이트를 보고 설치할 수 있도록 Configuration Manager 업데이트를 사이트로 가져옵니다.  

버전1606부터, Microsoft에 연결할 때 한 번에 여러 .cab 파일을 업로드하고(각기 다른 계층 구조에서) 프록시 서버 및 프록시 서버의 사용자를 지정할 수 있습니다.   

**여러.cab 파일을 업로드하려면**
 -  별도 계층 구조에서 내보내는 각.cab 파일을 동일한 폴더에 배치합니다. 각 파일의 이름은 고유해야 하며, 필요한 경우 수동으로 바꿀 수 있습니다.
 -  그런 다음 Microsoft로 데이터를 업로드하는 명령을 실행할 때 .cab 파일이 포함된 폴더를 지정합니다. 업데이트 1606 전에는, 한 번에 단일 계층 구조의 데이터만 업로드할 수 있었고, 도구에서 폴더의 .cab 파일의 이름을 지정하도록 요구했습니다.
 -  나중에 계층 구조의 서비스 연결 지점에서 가져오기 작업을 실행할 때 도구에서 해당 계층 구조의 데이터만 자동으로 가져옵니다.  

**프록시 서버를 지정하려면**  
다음과 같은 선택적 매개 변수를 사용하여 프록시 서버를 지정할 수 있습니다. 이러한 매개 변수를 사용하는 방법에 대한 자세한 내용은 이 항목의 명령줄 매개 변수 섹션에서 사용할 수 있습니다.
  - **-proxyserveruri [FQDN_of_proxy_sever]**  이 매개 변수를 사용하여 이 연결에 사용할 프록시 서버를 지정합니다.
  -  **-proxyusername [username]**  프록시 서버의 사용자를 지정해야 할 때 이 매개 변수를 사용합니다.



### <a name="to-use-the-service-connection-tool"></a>서비스 연결 도구를 사용하려면  

1.  서비스 연결 지점을 호스트하는 컴퓨터:  

    -   관리자 권한으로 명령 프롬프트를 열고 디렉터리를 **serviceconnectiontool.exe**가 포함된 위치로 변경합니다.   

2.  다음 명령을 실행하면 이 도구에서 사용 정보를 포함하는 .cab 파일을 준비하고 지정된 위치로 복사할 수 있습니다.  

    -   **serviceconnectiontool.exe -prepare -usagedatadest D:\USB\UsageData.cab**  

    둘 이상의 계층 구조에서.cab 파일을 동시에 업로드하는 경우 폴더의 각.cab 파일에 고유한 이름이 있어야 합니다. 폴더에 추가하는 파일의 이름을 수동으로 바꿀 수 있습니다.

    Configuration Manager 클라우드 서비스에 업로드하기 위해 수집되는 사용 현황 정보를 보려는 경우 다음 명령을 실행하여 .csv 파일과 동일한 데이터를 내보낸 다음 Excel과 같은 응용 프로그램을 사용하여 볼 수 있습니다.  

    -   **serviceconnectiontool.exe -export -dest D:\USB\UsageData.csv**  

3.  준비 단계가 완료되면 인터넷에 연결된 컴퓨터로 USB 드라이브를 이동(또는 내보낸 데이터를 다른 방법으로 전송)합니다.  

4.  인터넷에 연결된 컴퓨터에서 관리자 권한으로 명령 프롬프트를 열고 디렉터리를  **serviceconnectiontool.exe** 도구의 복사본과 해당 폴더의 추가 파일이 포함된 위치로 변경합니다.  

5.  다음 명령을 실행하여 사용 정보 업로드 및 Configuration Manager 업데이트 다운로드를 시작합니다.  

    -   **serviceconnectiontool.exe -connect -usagedatasrc D:\USB -updatepackdest D:\USB\UpdatePacks**

    이 명령줄의 추가 예제에 대해서는 이 항목의 뒷부분에 있는 [명령줄 옵션](../../../core/servers/manage/use-the-service-connection-tool.md#bkmk_cmd) 섹션을 참조하세요.

    > [!NOTE]  
    >  Configuration Manager 클라우드 서비스에 연결하는 명령줄을 실행하면 다음과 유사한 오류가 발생할 수 있습니다.  
    >   
    >  -   처리되지 않은 예외: System.UnauthorizedAccessException:  
    >   
    >      'C:\  
    >     Users\br\AppData\Local\Temp\extractmanifestcab\95F8A562.sql' 경로에 대한 액세스가 거부되었습니다.  
    >   
    > 이 오류는 무시해도 되며 오류 창을 닫고 계속할 수 있습니다.  

6.  Configuration Manager 업데이트 다운로드가 완료되면 서비스 연결 지점을 호스트하는 컴퓨터로 USB 드라이브를 이동(또는 내보낸 데이터를 다른 방법으로 전송)합니다.  

7.  서비스 연결 지점을 호스트하는 컴퓨터에서 관리자 권한으로 명령 프롬프트를 열고 디렉터리를 **serviceconnectiontool.exe**가 포함된 위치로 변경한 후 다음 명령을 실행합니다.  

    -   **serviceconnectiontool.exe -import -updatepacksrc D:\USB\UpdatePacks**  

8.  가져오기가 완료되면 명령 프롬프트를 닫아도 됩니다. 해당 계층 구조에 대한 업데이트만 가져옵니다.  

9. Configuration Manager 콘솔을 열고 **관리** >**클라우드 서비스** > **업데이트 및 서비스**로 이동합니다. 이제 가져온 업데이트를 설치할 수 있습니다. 업데이트를 설치하는 방법에 대한 자세한 내용은 [System Center Configuration Manager의 콘솔 내 업데이트 설치](../../../core/servers/manage/install-in-console-updates.md)를 참조하세요.  

## <a name="bkmk_cmd"></a> 명령줄 옵션  
 서비스 연결 지점 도구에 대한 도움말 정보를 보려면 도구가 포함된 폴더에서 명령 프롬프트를 열고  **serviceconnectiontool.exe**명령을 실행합니다.  

|명령줄 옵션|세부 정보|  
|---------------------------|-------------|  
|**-prepare -usagedatadest [drive:][path][filename.cab]**|이 명령은 현재 사용 데이터를 .cab 파일에 저장합니다.<br /><br /> 서비스 연결 지점을 호스트하는 서버에서 **로컬 관리자** 권한으로 이 명령을 실행합니다.<br /><br /> 예:   **-prepare -usagedatadest D:\USB\Usagedata.cab**|    
|**-connect -usagedatasrc [드라이브:][경로] -updatepackdest [드라이브:][경로] -proxyserveruri [프록시 서버의 FQDN] -proxyusername [사용자 이름]** <br /> <br /> 1606 이전의 Configuration Manager 버전을 사용하는 경우 .cab 파일의 이름을 지정해야 하며 프록시 서버에 대한 옵션을 사용할 수 없습니다.  지원되는 명령 매개 변수는 다음과 같습니다. <br /> **-connect -usagedatasrc [드라이브:][경로][파일 이름] -updatepackdest [드라이브:][경로]** |이 명령은 Configuration Manager 클라우드 서비스에 연결하여 지정된 위치에서 사용 현황 데이터.cab 파일을 업로드하고 사용 가능한 업데이트 팩 및 콘솔 콘텐츠를 다운로드합니다. 프록시 서버에 대한 옵션은 선택 사항입니다.<br /><br /> 이 명령은 인터넷에 연결할 수 있는 컴퓨터에 대한 **로컬 관리자** 권한으로 실행합니다.<br /><br /> 프록시 서버를 사용하지 않고 연결하는 예: **-connect -usagedatasrc D:\USB\ -updatepackdest D:\USB\UpdatePacks** <br /><br /> 프록시 서버를 사용하는 경우 연결하는 예: **-connect -usagedatasrc D:\USB\Usagedata.cab -updatepackdest D:\USB\UpdatePacks -proxyserveruri itgproxy.redmond.corp.microsoft.com -proxyusername Meg** <br /><br /> 1606 이전 버전을 사용하는 경우 .cab 파일의 파일 이름을 지정해야 하며 프록시 서버를 지정할 수 없습니다. 다음과 같은 예제 명령줄을 사용하세요. **-connect -usagedatasrc D:\USB\Usagedata.cab -updatepackdest D:\USB\UpdatePacks**|      
|**-import -updatepacksrc [drive:][path]**|이 명령은 이전에 다운로드한 업데이트 팩과 콘솔 콘텐츠를 Configuration Manager 콘솔로 가져옵니다.<br /><br /> 서비스 연결 지점을 호스트하는 서버에서 **로컬 관리자** 권한으로 이 명령을 실행합니다.<br /><br /> 예:  **-import -updatepacksrc D:\USB\UpdatePacks**|  
|**-export -dest [drive:][path][filename.csv]**|이 명령은 사용 데이터를 .csv 파일로 내보내며, 그런 후에 파일을 볼 수 있습니다.<br /><br /> 서비스 연결 지점을 호스트하는 서버에서 **로컬 관리자** 권한으로 이 명령을 실행합니다.<br /><br /> 예: **-export -dest D:\USB\usagedata.csv**|  

