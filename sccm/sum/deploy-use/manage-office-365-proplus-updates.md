---
title: Office 365 ProPlus 업데이트 관리
titleSuffix: Configuration Manager
description: Configuration Manager는 WSUS 카탈로그의 Office 365 클라이언트 업데이트를 사이트 서버와 동기화하여 업데이트를 클라이언트에 배포할 수 있게 합니다.
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.date: 03/26/2018
ms.topic: conceptual
ms.prod: configuration-manager
ms.technology: configmgr-sum
ms.assetid: eac542eb-9aa1-4c63-b493-f80128e4e99b
ms.openlocfilehash: a94ac00b8fce6098cbd829947f4e2fbdcb761b9e
ms.sourcegitcommit: c5e078b8eee87f527e5b5a0c2eb687bb9d6896c5
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34270717"
---
# <a name="manage-office-365-proplus-with-configuration-manager"></a>Configuration Manager를 사용하여 Office 365 ProPlus 관리

*적용 대상: System Center Configuration Manager(현재 분기)*

Configuration Manager를 사용하여 다음과 같은 방법으로 Office 365 ProPlus 앱을 관리할 수 있습니다.

- [Office 365 클라이언트 관리 대시보드](#office-365-client-management-dashboard): Office 365 클라이언트 관리 대시보드에서 Office 365 클라이언트 정보를 검토할 수 있습니다. Configuration Manager 버전 1802부터 그래프 섹션을 선택하면 Office 365 클라이언트 관리 대시보드에서는 관련 장치의 목록을 표시합니다. <!--1357281 -->

- [Office 365 앱 배포](#deploy-office-365-apps): 버전 1702부터 Office 365 클라이언트 관리 대시보드에서 Office 365 설치 관리자를 시작하여 초기 Office 365 앱 설치 환경을 간편하게 만들 수 있습니다. 마법사를 통해 Office 365 설치 설정을 구성하고, Office CDN(콘텐츠 배달 네트워크)에서 파일을 다운로드하고, 콘텐츠가 포함된 스크립트 응용 프로그램을 만들고 배포할 수 있습니다.    

- [Deploy Office 365 업데이트](#deploy-office-365-updates): 소프트웨어 업데이트 관리 워크플로를 사용하여 Office 365 클라이언트 업데이트를 관리할 수 있습니다. Microsoft에서 새 Office 365 클라이언트 업데이트를 Office CDN(Content Delivery Network)에 게시하면 Microsoft에서 업데이트 패키지도 WSUS(Windows Server Update Services)에 게시합니다. Configuration Manager에서 WSUS 카탈로그의 Office 365 클라이언트 업데이트를 사이트 서버로 동기화한 후에 업데이트를 클라이언트에 배포할 수 있습니다.    

- [Office 365 업데이트 다운로드 언어 추가](#add-languages-for-office-365-update-downloads): Office 365에서 지원되는 모든 언어의 업데이트를 다운로드하도록 Configuration Manager에 대한 지원을 추가할 수 있습니다. 즉, Office 365가 언어를 지원하면 Configuration Manager는 언어를 지원할 필요가 없습니다. Configuration Manager 버전 1610 이전에는 Office 365 클라이언트에 구성된 동일한 언어로 업데이트를 다운로드하고 배포해야 합니다. 

- [업데이트 채널 변경](#change-the-update-channel-after-you-enable-office-365-clients-to-receive-updates-from-configuration-manager): 그룹 정책을 사용하여 Office 365 클라이언트에 레지스트리 키 값 변경 내용을 배포하여 업데이트 채널을 변경할 수 있습니다.


## <a name="office-365-client-management-dashboard"></a>Office 365 클라이언트 관리 대시보드  
Office 365 클라이언트 관리 대시보드는 다음 정보에 대한 차트를 제공합니다.

- Office 365 클라이언트 수
- Office 365 클라이언트 버전
- Office 365 클라이언트 언어
- Office 365 클라이언트 채널     
  자세한 내용은 [Office 365 ProPlus의 업데이트 채널 개요](/DeployOffice/overview-of-update-channels-for-office-365-proplus)를 참조하세요.

Configuration Manager 콘솔에서 Office 365 클라이언트 관리 대시보드를 보려면 **소프트웨어 라이브러리** > **개요** > **Office 365 클라이언트 관리**로 이동합니다. 대시보드 맨 위에 있는 **컬렉션** 드롭다운 설정을 사용하여 특정 컬렉션 멤버별로 대시보드 데이터를 필터링합니다. Configuration Manager 버전 1802부터 그래프 섹션을 선택하면 Office 365 클라이언트 관리 대시보드에서는 관련 장치의 목록을 표시합니다.

### <a name="display-data-in-the-office-365-client-management-dashboard"></a>Office 365 클라이언트 관리 대시보드에 데이터 표시
Office 365 클라이언트 관리 대시보드에 표시되는 데이터는 하드웨어 인벤토리에서 옵니다. 하드웨어 인벤토리를 사용하도록 설정하고 대시보드에서 데이터가 표시되도록 **Office 365 ProPlus 구성** 하드웨어 인벤토리 클래스를 선택합니다. 
#### <a name="to-display-data-in-the-office-365-client-management-dashboard"></a>Office 365 클라이언트 관리 대시보드에 데이터를 표시하려면
1. 하드웨어 인벤토리를 아직 사용하도록 설정하지 않은 경우 지금 설정합니다. 자세한 내용은 [하드웨어 인벤토리 구성](\sccm\core\clients\manage\configure-hardware-inventory)을 참조하세요.
2. Configuration Manager 콘솔에서 **관리** > **클라이언트 설정** > **기본 클라이언트 설정**으로 이동합니다.  
3. **홈** 탭의 **속성** 그룹에서 **속성**을 클릭합니다.  
4. 에 **기본 클라이언트 설정** 대화 상자를 클릭 하 여 **하드웨어 인벤토리**.  
5. 에 **장치 설정을** 목록에서 클릭 **클래스 설정**.  
6. **하드웨어 인벤토리 클래스** 대화 상자에서 **Office 365 ProPlus 구성**을 선택합니다.  
7.  클릭 하 여 **확인** 변경 내용을 저장 하 고 닫습니다는 **하드웨어 인벤토리 클래스** 대화 상자. <br/>하드웨어 인벤토리가 보고되면 Office 365 클라이언트 관리 대시보드에서 데이터를 표시하기 시작합니다.

## <a name="deploy-office-365-apps"></a>Office 365 앱 배포  
버전 1702부터 초기 Office 365 앱 설치를 위해 Office 365 클라이언트 관리 대시보드에서 Office 365 설치 관리자를 시작합니다. 마법사를 통해 Office 365 설치 설정을 구성하고, Office CDN(콘텐츠 배달 네트워크)에서 파일을 다운로드하고, 파일에 대한 스크립트 응용 프로그램을 만들고 배포할 수 있습니다. Office 365가 클라이언트에 설치될 때까지 Office 365 업데이트를 적용할 수 없습니다.

이전 Configuration Manager 버전의 경우 클라이언트에서 처음으로 Office 365 앱을 설치하려면 다음 단계를 수행해야 합니다.
- ODT(Office 365 배포 도구) 다운로드
- 필요한 모든 언어 팩을 비롯하여 Office 365 설치 원본 파일을 다운로드합니다.
- 올바른 Office 버전 및 채널을 지정하는 Configuration.xml을 생성합니다.
- 클라이언트가 Office 365 앱을 설치하기 위한 레거시 패키지 또는 스크립트 응용 프로그램을 만들고 배포합니다.

### <a name="requirements"></a>요구 사항
- Office 365 설치 관리자를 실행하는 컴퓨터에서 인터넷에 액세스할 수 있어야 합니다.  
- Office 365 설치 관리자를 실행하는 사용자는 마법사에서 위치 공유가 제공되는 콘텐츠에 대한 **읽기** 및 **쓰기** 권한이 있어야 합니다.
- 404 다운로드 오류가 표시되면 다음 파일을 사용자 %temp% 폴더로 복사합니다.
  - [releasehistory.xml](http://officecdn.microsoft.com/pr/wsus/releasehistory.cab)
  - [o365client_32bit.xml](http://officecdn.microsoft.com/pr/wsus/ofl.cab)  


### <a name="to-deploy-office-365-apps-to-clients-from-the-office-365-client-management-dashboard"></a>Office 365 클라이언트 관리 대시보드에서 클라이언트에 Office 365 앱을 배포하려면
1. Configuration Manager 콘솔에서 **소프트웨어 라이브러리** > **개요** > **Office 365 클라이언트 관리**로 이동합니다.
2. 오른쪽 위 창에서 **Office 365 설치 관리자**를 클릭합니다. Office 365 클라이언트 설치 마법사가 열립니다.
3. **응용 프로그램 설정** 페이지에서 앱에 대한 이름과 설명을 제공하고 파일에 대한 다운로드 위치를 입력한 후 **다음**을 클릭합니다. 위치는 &#92;&#92;*server*&#92;*share*로 지정해야 합니다.
4. **클라이언트 설정 가져오기** 페이지에서, 기존 XML 구성 파일에서 Office 365 클라이언트 설정을 가져올지 아니면 설정을 수동으로 지정할지 여부를 지정합니다. 완료한 경우 **다음**을 클릭합니다.  

    기존 구성 파일이 있는 경우 해당 파일의 위치를 입력하고 7단계로 건너뜁니다. 위치는 &#92;&#92;*server*&#92;*share*&#92;*filename*.XML 형식으로 지정해야 합니다.
    > [!IMPORTANT]    
    > XML 구성 파일은 [Office 365 ProPlus 클라이언트에서 지원하는 언어](/DeployOffice/office2016/language-identifiers-and-optionstate-id-values-in-office-2016)만 포함해야 합니다.

5. **클라이언트 제품** 페이지에서 사용할 Office 365 제품군을 선택합니다. 포함하려는 응용 프로그램을 선택합니다. 포함해야 하는 추가 Office 제품을 선택하고 **다음**을 클릭합니다.
6. **클라이언트 설정** 페이지에서 포함할 설정을 선택하고 **다음**을 클릭합니다.
7. **배포** 페이지에서 응용 프로그램을 배포할지 여부를 선택하고 **다음**을 클릭합니다. <br/>마법사에서 패키지를 배포하지 않도록 선택한 경우 9단계로 건너뜁니다.
8. 마법사 페이지의 나머지 부분을 일반적인 응용 프로그램 배포와 마찬가지로 구성합니다. 자세한 내용은 [응용 프로그램 만들기 및 배포](/sccm/apps/get-started/create-and-deploy-an-application)를 참조하세요.
9. 마법사를 완료합니다.
10. **소프트웨어 라이브러리** > **개요** > **응용 프로그램 관리** > **응용 프로그램**에서 응용 프로그램을 배포하거나 편집할 수 있습니다.    

Office 365 설치 관리자를 사용하여 Office 365 응용 프로그램을 만들고 배포한 후에는 기본적으로 Configuration Manager가 Office 업데이트를 관리합니다. Office 365 클라이언트가 Configuration Manager에서 업데이트를 받게 하려면 [Configuration Manager를 사용하여 Office 365 업데이트 배포](#deploy-office-365-updates-with-configuration-manager)를 참조하세요.

>[!NOTE]
>Office 365 앱을 배포한 후 앱을 유지 관리하기 위한 자동 배포 규칙을 만들 수 있습니다. Office 365 앱에 대한 자동 배포 규칙을 만들려면 Office 365 클라이언트 관리 대시보드에서 **ADR 만들기**를 클릭합니다. 제품을 선택할 때 **Office 365 클라이언트**를 선택합니다. 자세한 내용은 [소프트웨어 업데이트 자동 배포](/sccm/sum/deploy-use/automatically-deploy-software-updates)를 참조하세요.


## <a name="deploy-office-365-updates"></a>Office 365 업데이트 배포
Configuration Manager 버전 1706부터 Office 365 클라이언트 업데이트가 **Office 365 클라이언트 관리** >**Office 365 업데이트** 노드로 이동되었습니다. 이 이동은 현재 ADR 구성에 영향을 주지 않습니다. 

Configuration Manager를 사용하여 Office 365 업데이트를 배포하려면 다음 단계를 따르세요.

1.  이 문서의 **Configuration Manager를 사용하여 Office 365 클라이언트 업데이트를 관리하기 위한 요구 사항** 섹션에서 Configuration Manager를 사용하여 Office 365 클라이언트 업데이트를 관리하기 위한 [요구 사항을 확인](/DeployOffice/manage-updates-to-office-365-proplus-with-system-center-configuration-manager#requirements-for-using-configuration-manager-to-manage-office-365-client-updates)합니다.  

2.  [소프트웨어 업데이트 지점을 구성](../get-started/configure-classifications-and-products.md)하여 Office 365 클라이언트 업데이트를 동기화합니다. 분류에 대한 **업데이트**를 설정하고 제품에 대한 **Office 365 클라이언트**를 선택합니다. **업데이트** 분류를 사용하도록 소프트웨어 업데이트 지점을 구성한 후 소프트웨어 업데이트를 동기화합니다.
3.  Office 365 클라이언트가 Configuration Manager에서 업데이트를 받을 수 있도록 합니다. Configuration Manager 클라이언트 설정 또는 그룹 정책을 사용하여 클라이언트를 사용하도록 설정합니다.   

    **방법 1**: Configuration Manager 버전 1606부터 Configuration Manager 클라이언트 설정을 사용하여 Office 365 클라이언트 에이전트를 관리할 수 있습니다. 이 설정을 구성하고 Office 365 업데이트를 배포한 후 Configuration Manager 클라이언트 에이전트는 Office 365 클라이언트 에이전트와 통신하여 배포 지점에서 업데이트를 다운로드하고 설치합니다. Configuration Manager는 Office 365 ProPlus 클라이언트 설정의 인벤토리를 사용합니다.    

      1.  Configuration Manager 콘솔에서 **관리** > **개요** > **클라이언트 설정**을 클릭합니다.  

      2.  적절한 장치 설정을 열어 클라이언트 에이전트를 사용하도록 설정합니다. 기본 및 사용자 지정 클라이언트 설정에 대한 자세한 내용은 [System Center Configuration Manager에서 클라이언트 설정을 구성하는 방법](../../core/clients/deploy/configure-client-settings.md)을 참조하세요.  

      3.  **소프트웨어 업데이트**를 클릭하고 **Office 365 클라이언트 에이전트 관리 사용** 설정에 대해 **예**를 선택합니다.  

    **방법 2**: Office 배포 도구 또는 그룹 정책을 사용하여 Configuration Manager에서 [Office 365 클라이언트가 업데이트를 받도록 설정](/DeployOffice/manage-updates-to-office-365-proplus-with-system-center-configuration-manager#BKMK_EnableClient)합니다.  

4. 클라이언트에 [Office 365 업데이트를 배포](deploy-software-updates.md)합니다.   

> [!Important]
> Configuration Manager 버전 1610 이전에는 Office 365 클라이언트에 구성된 동일한 언어로 업데이트를 다운로드하고 배포해야 합니다. 예를 들어 Office 365 클라이언트를 en-us 및 de-de 언어로 구성했다고 가정합니다. 사이트 서버에서 해당하는 Office 365 업데이트의 en-us 콘텐츠만 다운로드 및 배포합니다. 사용자가 소프트웨어 센터로부터 이 업데이트의 설치를 시작하면 de-de 콘텐츠를 다운로드하는 동안에는 업데이트가 중단됩니다.   

## <a name="restart-behavior-and-client-notifications-for-office-365-updates"></a>Office 365 업데이트에 대한 동작 및 클라이언트 알림 다시 시작
Office 365 클라이언트에 대한 업데이트를 배포할 때 다시 시작 동작 및 클라이언트 알림은 Configuration Manager 버전에 따라 다릅니다. 다음 표에는 클라이언트에서 Office 365 업데이트를 받을 때 제공하는 최종 사용자 환경에 대한 정보가 나와 있습니다.

|Configuration Manager 버전 |최종 사용자 환경|  
|----------------|---------------------|
|1610 이전 버전|다시 시작 플래그가 설정되고 컴퓨터를 다시 시작한 후에 업데이트가 설치됩니다.|
|1610|Office 365 앱은 업데이트를 설치하기 전에 경고 없이 종료됩니다.|
|1610(업데이트 포함) <br/>1702|다시 시작 플래그가 설정되고 컴퓨터를 다시 시작한 후에 업데이트가 설치됩니다.|
|1706|클라이언트는 업데이트를 설치하기 전에 카운트다운 대화 상자 뿐만 아니라 팝업 및 앱 내 알림을 받습니다.|
|1802| 클라이언트는 업데이트를 설치하기 전에 카운트다운 대화 상자 뿐만 아니라 팝업 및 앱 내 알림을 받습니다. </br>모든 Office 365 응용 프로그램이 Office 365 클라이언트 업데이트 적용 동안 실행되는 경우, Office 응용 프로그램은 강제로 닫히지 않습니다. 대신 업데이트 설치는 시스템 다시 시작을 요구할 때 반환합니다 <!--510006-->|

> [!Important]
>
>Configuration Manager 버전 1706에서는 다음 세부 정보에 유의하세요.
>
>- 작업 표시줄의 알림 영역에는 최종 기한이 48시간 이내이고 업데이트 콘텐츠가 다운로드된 필수 앱에 대한 알림 아이콘이 표시됩니다. 
>- 최종 기한이 7.5시간 이내이고 업데이트가 다운로드된 필수 앱에 대한 카운트다운 대화 상자가 표시됩니다. 사용자는 최종 기한 전에 최대 세 번까지 카운트다운 대화 상자를 연기할 수 있습니다. 카운트다운은 연기되면 2시간 후에 다시 표시됩니다. 카운트다운이 연기되지 않으면 30분 카운트다운이 있으며, 만료되면 업데이트가 설치됩니다.
>- 사용자가 알림 영역에서 아이콘을 클릭할 때까지 팝업 알림이 표시되지 않을 수 있습니다. 또한 알림 영역의 공간이 최소인 경우 사용자가 알림 영역을 열거나 확장해야 알림 아이콘이 표시될 수 있습니다. 
>- 사용자가 장치에서 적극적으로 작업하지 않으면 알림 및 카운트다운 대화 상자가 시작할 수 있습니다. 예를 들어 하룻밤 동안 장치가 잠겨있을 경우 장치에서 실행되는 Office 앱이 업데이트를 설치하려면 강제로 닫힐 수 있습니다. Office에서는 앱을 닫기 전에 앱 데이터를 저장하여 데이터 손실을 방지합니다. 
>- 최종 기한이 지나갔거나 가능한 한 빨리 시작되도록 구성된 경우 실행 중인 Office 응용 프로그램을 알림 없이 강제로 닫아야 할 수 있습니다. 
>- 사용자가 최종 기한 전에 Office 업데이트를 설치하는 경우 최종 기한에 도달했을 때 Configuration Manager에서 업데이트가 설치되어 있는지 확인합니다. 장치에서 업데이트가 검색되지 않으면 업데이트가 설치됩니다. 
>- 업데이트를 다운로드하기 전에 실행 중인 Office 응용 프로그램에는 인앱 알림 표시줄이 표시되지 않습니다. 업데이트를 다운로드하면 새로 열린 앱에 대한 인앱 알림만 표시됩니다.
>- 서비스 창에서 트리거되거나 업무 외 시간으로 예약된 Office 업데이트의 경우 실행 중인 Office 응용 프로그램을 강제로 닫아야만 알림 없이 업데이트를 설치할 수 있습니다. 



## <a name="add-languages-for-office-365-update-downloads"></a>Office 365 업데이트 다운로드 언어 추가
Configuration Manager의 지원 여부와 관계 없이 Office 365에서 지원되는 모든 언어에 대한 업데이트를 다운로드하도록 Configuration Manager에 대한 지원을 추가할 수 있습니다.    

> [!IMPORTANT]  
> 추가 Office 365 업데이트 언어 구성은 사이트 전체 설정입니다. 다음 절차를 사용하여 언어를 추가하면 모든 Office 365 업데이트가 소프트웨어 업데이트 다운로드 또는 소프트웨어 업데이트 배포 마법사의 **언어 선택** 페이지에서 선택한 언어 외에 추가한 언어로도 다운로드됩니다.

### <a name="to-add-support-to-download-updates-for-additional-languages"></a>추가 언어의 업데이트 다운로드 지원을 추가하려면
중앙 관리 사이트나 독립 실행형 기본 사이트의 소프트웨어 업데이트 지점에서 다음 절차를 사용합니다.
1. 명령 프롬프트에서 관리자 권한으로 *wbemtest*를 입력하여 Windows Management Instrumentation 테스터를 엽니다.
2. **연결**을 클릭한 후 *root\sms\site_&lt;siteCode&gt;* 를 입력합니다.
3. **쿼리**를 클릭한 후 다음 쿼리를 실행합니다. *select &#42; from SMS_SCI_Component where componentname ="SMS_WSUS_CONFIGURATION_MANAGER"*  
   ![WMI 쿼리](..\media\1-wmiquery.png)
4. 결과 창에서 중앙 관리 사이트 또는 독립 실행형 기본 사이트의 사이트 코드가 있는 개체를 두 번 클릭합니다.
5. **속성** 속성을 선택하고 **속성 편집**을 클릭한 후 **포함값 보기**를 클릭합니다.
![속성 편집기](..\media\2-propeditor.png)
6. 첫 번째 쿼리 결과부터 시작해서 **PropertyName** 속성의 **AdditionalUpdateLanguagesForO365**가 있는 개체를 찾을 때까지 각 개체를 엽니다.
7. **Value2**를 선택하고 **속성 편집**을 클릭합니다.  
![Value2 속성 편집](..\media\3-queryresult.png)
8. **Value2** 속성에 다른 언어를 추가하고 **속성 저장**을 클릭합니다. <br/> 예를 들면 pt-pt(포르투갈어 - 포르투갈), af-za(아프리칸스어 - 남아프리카), nn-no(노르웨이어(니노르스크) - 노르웨이) 등이 있습니다.  
![속성 편집기에서 언어 추가](..\media\4-props.png)  
9. **닫기** 클릭, **닫기** 클릭, **속성 저장** 클릭, **개체 저장** 클릭(여기에서 **닫기**를 클릭하면 값은 삭제됩니다). **닫기**를 클릭한 다음, **종료**를 클릭하여 WMI(Management Instrumentation) 테스터를 종료합니다.
10. Configuration Manager 콘솔에서 **소프트웨어 라이브러리** > **개요** > **Office 365 클라이언트 관리** > **Office 365 업데이트**로 이동합니다.
11. 이제 Office 365 업데이트를 다운로드하면 마법사에서 선택하고 이 절차에서 구성한 언어로 업데이트가 다운로드됩니다. 업데이트가 올바른 언어로 다운로드되는지 확인하려면 업데이트의 패키지 원본으로 이동한 후 파일 이름에 언어 코드가 포함된 파일을 찾습니다.  
![추가 언어가 있는 파일 이름](..\media\5-verification.png)

## <a name="updating-office-365-during-task-sequences-when-office-365-is-installed-in-the-base-image"></a>기본 이미지에 Office 365가 설치된 경우 작업 순서 중 Office 365 업데이트
이미지에 Office 365가 이미 설치된 경우 운영 체제를 설치할 때 업데이트 채널 레지스트리 키 값에 원래 설치 위치가 있을 수 있습니다. 이 경우 업데이트 검색 시 Office 365 클라이언트 업데이트가 표시되지 않습니다. 일주일에 여러 번 실행되는 예약된 Office 자동 업데이트 작업이 있습니다. 해당 작업이 실행된 후 업데이트 채널은 구성된 Office CDN URL을 가리키고 검색 결과에는 해당 업데이트가 적용 가능한 것으로 표시됩니다. <!--510452-->

해당 업데이트가 검색되도록 업데이트 채널을 설정하려면 다음 단계를 수행합니다.
1. OS(운영 체제) 기본 이미지와 같은 버전의 Office 365가 있는 컴퓨터에서 작업 스케줄러(taskschd.msc)를 열고 Office 365 자동 업데이트 작업을 식별합니다. 일반적으로 **작업 스케줄러 라이브러리** >**Microsoft**>**Office** 아래에 있습니다.
2. 자동 업데이트 작업을 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.
3. **작업** 탭으로 이동하여 **편집**을 클릭합니다. 명령 및 인수를 복사합니다. 
4. Configuration Manager 콘솔에서 작업 순서를 편집합니다.
5. 작업 순서에서 **업데이트 설치** 단계 전에 새로운 **명령줄 실행** 단계를 추가합니다. 
6. Office 자동 업데이트 예약된 작업에서 수집한 명령과 인수를 복사합니다. 
7. **확인**을 클릭합니다. 

## <a name="change-the-update-channel-after-you-enable-office-365-clients-to-receive-updates-from-configuration-manager"></a>Office 365 클라이언트가 Configuration Manager에서 업데이트를 받도록 설정한 후에 업데이트 채널 변경
Office 365 클라이언트가 Configuration Manager에서 업데이트를 받도록 설정한 후 업데이트 채널을 변경하려면 그룹 정책을 사용하여 Office 365 클라이언트에 레지스트리 키 값 변경 내용을 배포합니다. **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Office\ClickToRun\Configuration\CDNBaseUrl** 레지스트리 키를 다음 중 한 값을 사용하도록 변경합니다.

- 월 단위 채널 <br/>
<i>(이전의 현재 채널)</i>:  
  **CDNBaseUrl** = http&#58;//officecdn.microsoft.com/pr/492350f6-3a01-4f97-b9c0-c7c6ddf67d60

- 반기 채널 <br/>
<i>(이전의 지연된 채널)</i>:  
  **CDNBaseUrl** = http&#58;//officecdn.microsoft.com/pr/7ffbc6bf-bc32-4f92-8982-f9dd17fd3114

- 월 단위 채널(대상 지정)<Br/>
 <i>(현재 채널의 이전 첫 번째 릴리스)</i>:  
  **CDNBaseUrl** = http&#58;//officecdn.microsoft.com/pr/64256afe-f5d9-4f86-8936-8840a6a4f5be

- 반기 채널(대상 지정) <br/>
<i>(지연된 채널의 이전 첫 번째 릴리스)</i>:  
  **CDNBaseUrl** = http&#58;//officecdn.microsoft.com/pr/b8f9b850-328d-4355-9145-c59439a0c4cf
<!--the channel names changed in Sept 2017- https://docs.microsoft.com/en-us/DeployOffice/overview-of-update-channels-for-office-365-proplus?ui=en-US&rs=en-US&ad=US>


<!--- You can create an Office 365 app without using the Office 365 Installation Wizard. To do this, you use the Office 2016 Deployment Tool (ODT) to download Office installation source files to a network share, generate Configure.xml that specifies the correct Office version and channel, and so on. Then, create an app for the files using the normal app management process.
> [!Note]
> The Office 365 Installation Wizard was introduced in Configuration Manager version 1702 and provides an easy way to create Office 365 apps.

- [Download the Office 2016 Deployment Tool](http://aka.ms/ODT2016) from the Microsoft Download Center.  
- Review the [configuration options for the Office Deployment Tool](https://technet.microsoft.com/library/jj219426.aspx).

You can create an application just as you would with any other application in Configuration Manager from **Software Library** > **Overview** > **Application Management** > **Applications**. For details, see [Create and deploy an application](/sccm/apps/get-started/create-and-deploy-an-application).
--->

<!--- ## Next steps
Use the Office 365 Client Management dashboard in Configuration Manager to review Office 365 client information and deploy Office 365 apps. For details, see [Manage Office 365 apps](manage-office-365-apps.md). --->
