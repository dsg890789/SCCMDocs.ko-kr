---
title: Office 365 ProPlus 업데이트 관리
titleSuffix: Configuration Manager
description: Configuration Manager는 WSUS 카탈로그의 Office 365 클라이언트 업데이트를 사이트 서버와 동기화하여 업데이트를 클라이언트에 배포할 수 있게 합니다.
author: mestew
ms.author: mstewart
manager: dougeby
ms.date: 12/06/2019
ms.topic: conceptual
ms.prod: configuration-manager
ms.technology: configmgr-sum
ms.assetid: eac542eb-9aa1-4c63-b493-f80128e4e99b
ms.collection: M365-identity-device-management
ms.openlocfilehash: 083dbbbd14b7364c88abfb6471ea1505657586ae
ms.sourcegitcommit: 66e7363108e37ea8bb5d36fca0231829d48ac612
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 12/06/2019
ms.locfileid: "74899524"
---
# <a name="manage-office-365-proplus-with-configuration-manager"></a>Configuration Manager를 사용하여 Office 365 ProPlus 관리

*적용 대상: System Center Configuration Manager(현재 분기)*

Configuration Manager를 사용하여 다음과 같은 방법으로 Office 365 ProPlus 앱을 관리할 수 있습니다.

- [Office 365 앱 배포](#deploy-office-365-apps): [Office 365 클라이언트 관리 대시보드](/sccm/sum/deploy-use/office-365-dashboard)에서 Office 365 설치 관리자를 시작하여 초기 Office 365 앱 설치 환경을 간편하게 만들 수 있습니다. 마법사를 통해 Office 365 설치 설정을 구성하고, Office CDN(콘텐츠 배달 네트워크)에서 파일을 다운로드하고, 콘텐츠가 포함된 스크립트 애플리케이션을 만들고 배포할 수 있습니다.

- [Deploy Office 365 업데이트](#deploy-office-365-updates): 소프트웨어 업데이트 관리 워크플로를 사용하여 Office 365 클라이언트 업데이트를 관리할 수 있습니다. Microsoft에서 새 Office 365 클라이언트 업데이트를 Office CDN(Content Delivery Network)에 게시하면 Microsoft에서 업데이트 패키지도 WSUS(Windows Server Update Services)에 게시합니다. Configuration Manager에서 WSUS 카탈로그의 Office 365 클라이언트 업데이트를 사이트 서버로 동기화한 후에 업데이트를 클라이언트에 배포할 수 있습니다.    

- [Office 365 업데이트 다운로드 언어 추가](#bkmk_o365_lang): Office 365에서 지원되는 모든 언어의 업데이트를 다운로드하도록 Configuration Manager에 대한 지원을 추가할 수 있습니다. 즉, Office 365가 언어를 지원하면 Configuration Manager는 언어를 지원할 필요가 없습니다. Configuration Manager 버전 1610 이전에는 Office 365 클라이언트에 구성된 동일한 언어로 업데이트를 다운로드하고 배포해야 합니다.

- [업데이트 채널 변경](#bkmk_channel): 그룹 정책을 사용하여 Office 365 클라이언트에 레지스트리 키 값 변경 내용을 배포하여 업데이트 채널을 변경할 수 있습니다.

Office 365 클라이언트 정보를 검토하고 이러한 Office 365 관리 작업 중 일부를 시작하려면 [Office 365 클라이언트 관리 대시보드](/sccm/sum/deploy-use/office-365-dashboard)를 사용합니다.

## <a name="deploy-office-365-apps"></a>Office 365 앱 배포  
초기 Office 365 앱 설치를 위해 Office 365 클라이언트 관리 대시보드에서 Office 365 설치 관리자를 시작합니다. 마법사를 통해 Office 365 설치 설정을 구성하고, Office CDN(콘텐츠 배달 네트워크)에서 파일을 다운로드하고, 파일에 대한 스크립트 애플리케이션을 만들고 배포할 수 있습니다. 클라이언트에 Office 365가 설치되고 [Office 자동 업데이트 작업](https://docs.microsoft.com/deployoffice/overview-of-the-update-process-for-office-365-proplus)이 실행될 때까지 Office 365 업데이트를 적용할 수 없습니다. 테스트를 위해 업데이트 작업을 수동으로 실행할 수 있습니다.

이전 Configuration Manager 버전의 경우 클라이언트에서 처음으로 Office 365 앱을 설치하려면 다음 단계를 수행해야 합니다.
- ODT(Office 365 배포 도구) 다운로드
- 필요한 모든 언어 팩을 비롯하여 Office 365 설치 원본 파일을 다운로드합니다.
- 올바른 Office 버전 및 채널을 지정하는 Configuration.xml을 생성합니다.
- 클라이언트가 Office 365 앱을 설치하기 위한 레거시 패키지 또는 스크립트 애플리케이션을 만들고 배포합니다.

### <a name="requirements"></a>요구 사항
- Office 365 설치 관리자를 실행하는 컴퓨터에서 인터넷에 액세스할 수 있어야 합니다.  
- Office 365 설치 관리자를 실행하는 사용자는 마법사에서 제공한 콘텐츠 위치 공유에 대해 **읽기** 및 **쓰기** 권한이 있어야 합니다.
- 404 다운로드 오류가 표시되면 다음 파일을 사용자 %temp% 폴더로 복사합니다.
  - [releasehistory.xml](https://officecdn.microsoft.com/pr/wsus/releasehistory.cab)
  - [o365client_32bit.xml](https://officecdn.microsoft.com/pr/wsus/ofl.cab)  

### <a name="deploy-office-365-apps-using-configuration-manager-version-1806-or-higher"></a>Configuration Manager 버전 1806 이상을 사용하여 Office 365 앱 배포: 
Configuration Manager 1806부터 Office 사용자 지정 도구가 Configuration Manager 콘솔에서 Office 365 설치 관리자와 통합됩니다. Office 365에 대한 배포를 만들 때 최신 Office 관리 효율성 설정을 동적으로 구성할 수 있습니다. <!--1358149-->

1. Configuration Manager 콘솔에서 **소프트웨어 라이브러리** > **개요** > **Office 365 클라이언트 관리**로 이동합니다.
2. 오른쪽 위 창에서 **Office 365 설치 관리자**를 클릭합니다. Office 365 클라이언트 설치 마법사가 열립니다.
3. **애플리케이션 설정** 페이지에서 앱에 대한 이름과 설명을 제공하고 파일에 대한 다운로드 위치를 입력한 후 **다음**을 클릭합니다. 위치는 &#92;&#92;*server*&#92;*share*로 지정해야 합니다.
4. **Office 설정** 페이지에서 **Office 사용자 지정 도구로 이동**을 클릭합니다. 그러면 [간편 실행용 Office 사용자 지정 도구](https://config.office.com)가 열립니다.
5. Office 365 설치에 대해 원하는 설정을 구성합니다. 구성이 완료되면 페이지의 오른쪽 위에 있는 **제출**을 클릭합니다. 
6. **배포** 페이지에서 지금 배포할지 또는 나중에 배포할지 결정합니다. 나중에 배포하려는 경우에는, **소프트웨어 라이브러리** > **애플리케이션 관리** > **애플리케이션**에서 애플리케이션을 찾을 수 있습니다.  
7. **요약** 페이지에서 설정을 확인합니다. 
8. Office 365 클라이언트 설치 마법사가 완료되면 **다음**을 클릭한 후 **닫기**를 클릭합니다. 

### <a name="deploy-office-365-apps-using-configuration-manager-version-1802-and-prior"></a>Configuration Manager 1802 이전 버전을 사용하여 Office 365 앱 배포:

1. Configuration Manager 콘솔에서 **소프트웨어 라이브러리** > **개요** > **Office 365 클라이언트 관리**로 이동합니다.
2. 오른쪽 위 창에서 **Office 365 설치 관리자**를 클릭합니다. Office 365 클라이언트 설치 마법사가 열립니다.
3. **애플리케이션 설정** 페이지에서 앱에 대한 이름과 설명을 제공하고 파일에 대한 다운로드 위치를 입력한 후 **다음**을 클릭합니다. 위치는 &#92;&#92;*server*&#92;*share*로 지정해야 합니다.
4. **클라이언트 설정 가져오기** 페이지에서, 기존 XML 구성 파일에서 Office 365 클라이언트 설정을 가져올지 아니면 설정을 수동으로 지정할지 여부를 지정합니다. 완료한 경우 **다음**을 클릭합니다.  

    기존 구성 파일이 있는 경우 해당 파일의 위치를 입력하고 7단계로 건너뜁니다. 위치는 &#92;&#92;*server*&#92;*share*&#92;*filename*.XML 형식으로 지정해야 합니다.
    > [!IMPORTANT]    
    > XML 구성 파일은 [Office 365 ProPlus 클라이언트에서 지원하는 언어](https://docs.microsoft.com/deployoffice/office2016/language-identifiers-and-optionstate-id-values-in-office-2016)만 포함해야 합니다.

5. **클라이언트 제품** 페이지에서 사용할 Office 365 제품군을 선택합니다. 포함하려는 애플리케이션을 선택합니다. 포함해야 하는 추가 Office 제품을 선택하고 **다음**을 클릭합니다.
6. **클라이언트 설정** 페이지에서 포함할 설정을 선택하고 **다음**을 클릭합니다.
7. **배포** 페이지에서 애플리케이션을 배포할지 여부를 선택하고 **다음**을 클릭합니다. <br/>마법사에서 패키지를 배포하지 않도록 선택한 경우 9단계로 건너뜁니다.
8. 마법사 페이지의 나머지 부분을 일반적인 애플리케이션 배포와 마찬가지로 구성합니다. 자세한 내용은 [애플리케이션 만들기 및 배포](/sccm/apps/get-started/create-and-deploy-an-application)를 참조하세요.
9. 마법사를 완료합니다.
10. **소프트웨어 라이브러리** > **개요** > **애플리케이션 관리** > **애플리케이션**에서 애플리케이션을 배포하거나 편집할 수 있습니다.    

Office 365 설치 관리자를 사용하여 Office 365 애플리케이션을 만들고 배포한 후에는 기본적으로 Configuration Manager가 Office 업데이트를 관리하지 않습니다. Office 365 클라이언트가 Configuration Manager에서 업데이트를 받게 하려면 [Configuration Manager를 사용하여 Office 365 업데이트 배포](#deploy-office-365-updates)를 참조하세요.

Office 365 앱을 배포한 후 앱을 유지 관리하기 위한 자동 배포 규칙을 만들 수 있습니다. Office 365 앱에 대한 자동 배포 규칙을 만들려면 [Office 365 클라이언트 관리 대시보드](/sccm/sum/deploy-use/office-365-dashboard)에서 **ADR 만들기**를 클릭합니다. 제품을 선택할 때 **Office 365 클라이언트**를 선택합니다. 자세한 내용은 [소프트웨어 업데이트 자동 배포](/sccm/sum/deploy-use/automatically-deploy-software-updates)를 참조하세요.


## <a name="drill-through-required-office-365-updates"></a>필수 Office 365 업데이트를 통한 드릴스루
<!--4224414-->
*(1906 버전에서 도입됨)*

규정 준수 통계를 드릴스루하여 특정 Office 365 소프트웨어 업데이트가 필요한 디바이스를 확인할 수 있습니다. 디바이스 목록을 보려면 디바이스가 속한 업데이트 및 컬렉션을 볼 수 있는 사용 권한이 필요합니다. 장치 목록으로 드릴 다운 합니다.

1. **소프트웨어 라이브러리** > **Office 365 클라이언트 관리** > **Office 365 업데이트**로 가기.
1. 하나 이상의 디바이스에 필요한 업데이트를 선택합니다.
1. **요약** 탭을 확인하고 **통계**에서 원형 차트를 찾습니다.
1. 원형 차트 옆에 있는 **필수 보기** 하이퍼링크를 선택하여 디바이스 목록으로 드릴다운합니다.
1. 이 작업에서는 업데이트를 필요로 하는 디바이스를 볼 수 있는 **디바이스**의 임시 노드로 이동합니다. 목록에서 새 컬렉션 만들기와 같이 노드에 대한 조치를 취할 수도 있습니다.


## <a name="deploy-office-365-updates"></a>Office 365 업데이트 배포

Configuration Manager를 사용하여 Office 365 업데이트를 배포하려면 다음 단계를 따르세요.

1. 이 문서의 **Configuration Manager를 사용하여 Office 365 클라이언트 업데이트를 관리하기 위한 요구 사항** 섹션에서 Configuration Manager를 사용하여 Office 365 클라이언트 업데이트를 관리하기 위한 [요구 사항을 확인](/DeployOffice/manage-updates-to-office-365-proplus-with-system-center-configuration-manager#requirements-for-using-configuration-manager-to-manage-office-365-client-updates)합니다.  

2. [소프트웨어 업데이트 지점을 구성](../get-started/configure-classifications-and-products.md)하여 Office 365 클라이언트 업데이트를 동기화합니다. 분류에 대한 **업데이트**를 설정하고 제품에 대한 **Office 365 클라이언트**를 선택합니다. **업데이트** 분류를 사용하도록 소프트웨어 업데이트 지점을 구성한 후 소프트웨어 업데이트를 동기화합니다.
3. Office 365 클라이언트가 Configuration Manager에서 업데이트를 받을 수 있도록 합니다. Configuration Manager 클라이언트 설정 또는 그룹 정책을 사용하여 클라이언트를 사용하도록 설정합니다.

    **방법 1**: Configuration Manager 버전 1606부터 Configuration Manager 클라이언트 설정을 사용하여 Office 365 클라이언트 에이전트를 관리할 수 있습니다. 이 설정을 구성하고 Office 365 업데이트를 배포한 후 Configuration Manager 클라이언트 에이전트는 Office 365 클라이언트 에이전트와 통신하여 배포 지점에서 업데이트를 다운로드하고 설치합니다. Configuration Manager는 Office 365 ProPlus 클라이언트 설정의 인벤토리를 사용합니다.    

      1. Configuration Manager 콘솔에서 **관리** > **개요** > **클라이언트 설정**을 클릭합니다.  

      2. 적절한 디바이스 설정을 열어 클라이언트 에이전트를 사용하도록 설정합니다. 기본 및 사용자 지정 클라이언트 설정에 대한 자세한 내용은 [System Center Configuration Manager에서 클라이언트 설정을 구성하는 방법](../../core/clients/deploy/configure-client-settings.md)을 참조하세요.  

      3. **소프트웨어 업데이트**를 클릭하고 **Office 365 클라이언트 에이전트 관리 사용** 설정에 대해 **예**를 선택합니다.  

    **방법 2**: Office 배포 도구 또는 그룹 정책을 사용하여 Configuration Manager에서 [Office 365 클라이언트가 업데이트를 받도록 설정](/DeployOffice/manage-updates-to-office-365-proplus-with-system-center-configuration-manager#BKMK_EnableClient)합니다.  

4. 클라이언트에 [Office 365 업데이트를 배포](deploy-software-updates.md)합니다.

> [!Important]
> - Configuration Manager 버전 1706부터 Office 365 클라이언트 업데이트가 **Office 365 클라이언트 관리** >**Office 365 업데이트** 노드로 이동되었습니다. 이러한 이동은 현재 ADR 구성에 영향을 주지 않습니다. 
> - Configuration Manager 버전 1610 이전에는 Office 365 클라이언트에 구성된 동일한 언어로 업데이트를 다운로드하고 배포해야 합니다. 예를 들어 Office 365 클라이언트를 en-us 및 de-de 언어로 구성했다고 가정합니다. 사이트 서버에서 해당하는 Office 365 업데이트의 en-us 콘텐츠만 다운로드 및 배포합니다. 사용자가 소프트웨어 센터로부터 이 업데이트의 설치를 시작하면 de-de 콘텐츠를 다운로드하는 동안에는 업데이트가 중단됩니다. 

> [!NOTE]  
>
> Office 365 ProPlus를 최근에 설치한 경우 설치한 방법에 따라 업데이트 채널이 아직 설정되지 않았을 수 있습니다. 그러한 경우 배포된 업데이트가 적용할 수 없는 상태로 검색됩니다. Office 365 ProPlus를 설치할 때 [예약된 자동 업데이트 작업](https://docs.microsoft.com/deployoffice/overview-of-the-update-process-for-office-365-proplus)이 만들어집니다. 이 경우 업데이트 채널을 설정하고 업데이트가 적용할 수 있는 상태로 검색되도록 하려면 이 작업을 한 번 이상 실행해야 합니다.
>
> Office 365 ProPlus를 최근에 설치했는데 배포된 업데이트가 검색되지 않는 경우, 테스트를 위해 Office 자동 업데이트 작업을 수동으로 시작한 다음, 클라이언트에서 [소프트웨어 업데이트 배포 평가 주기](https://docs.microsoft.com/sccm/sum/understand/software-updates-introduction#scan-for-software-updates-compliance-process)를 시작할 수 있습니다. 작업 순서에서 이 작업을 수행하는 방법에 대한 지침은 [작업 순서에서 Office 365 ProPlus 업데이트](https://docs.microsoft.com/sccm/sum/deploy-use/manage-office-365-proplus-updates#updating-office-365-proplus-in-a-task-sequence)를 참조하세요.

## <a name="restart-behavior-and-client-notifications-for-office-365-updates"></a>Office 365 업데이트에 대한 동작 및 클라이언트 알림 다시 시작
Office 365 클라이언트에 대한 업데이트를 배포할 때 다시 시작 동작 및 클라이언트 알림은 Configuration Manager 버전에 따라 다릅니다. 다음 표에는 클라이언트에서 Office 365 업데이트를 받을 때 제공하는 최종 사용자 환경에 대한 정보가 나와 있습니다.

|Configuration Manager 버전 |최종 사용자 환경|  
|----------------|---------------------|
|1706, 1710|클라이언트는 업데이트를 설치하기 전에 카운트다운 대화 상자 뿐만 아니라 팝업 및 앱 내 알림을 받습니다.|
|1802| 클라이언트는 업데이트를 설치하기 전에 카운트다운 대화 상자 뿐만 아니라 팝업 및 앱 내 알림을 받습니다. </br>모든 Office 365 애플리케이션이 Office 365 클라이언트 업데이트 적용 동안 실행되는 경우, Office 애플리케이션은 강제로 닫히지 않습니다. 대신 업데이트 설치는 시스템 다시 시작을 요구할 때 반환합니다. <!--510006-->|


> [!Important]
>
>Configuration Manager 버전 1706에서는 다음 세부 정보에 유의하세요.
>
>- 작업 표시줄의 알림 영역에는 최종 기한이 48시간 이내이고 업데이트 콘텐츠가 다운로드된 필수 앱에 대한 알림 아이콘이 표시됩니다. 
>- 최종 기한이 7.5시간 이내이고 업데이트가 다운로드된 필수 앱에 대한 카운트다운 대화 상자가 표시됩니다. 사용자는 최종 기한 전에 최대 세 번까지 카운트다운 대화 상자를 연기할 수 있습니다. 카운트다운은 연기되면 2시간 후에 다시 표시됩니다. 카운트다운이 연기되지 않으면 30분 카운트다운이 있으며, 만료되면 업데이트가 설치됩니다.
>- 사용자가 알림 영역에서 아이콘을 클릭할 때까지 팝업 알림이 표시되지 않을 수 있습니다. 또한 알림 영역의 공간이 최소인 경우 사용자가 알림 영역을 열거나 확장해야 알림 아이콘이 표시될 수 있습니다. 
>- 사용자가 디바이스에서 적극적으로 작업하지 않으면 알림 및 카운트다운 대화 상자가 시작할 수 있습니다. 예를 들어 하룻밤 동안 디바이스가 잠겨있을 경우 디바이스에서 실행되는 Office 앱이 업데이트를 설치하려면 강제로 닫힐 수 있습니다. Office에서는 앱을 닫기 전에 앱 데이터를 저장하여 데이터 손실을 방지합니다. 
>- 최종 기한이 지나갔거나 가능한 한 빨리 시작되도록 구성된 경우 실행 중인 Office 응용 프로그램을 알림 없이 강제로 닫아야 할 수 있습니다. 
>- 사용자가 최종 기한 전에 Office 업데이트를 설치하는 경우 최종 기한에 도달했을 때 Configuration Manager에서 업데이트가 설치되어 있는지 확인합니다. 디바이스에서 업데이트가 검색되지 않으면 업데이트가 설치됩니다. 
>- 업데이트를 다운로드하기 전에 실행 중인 Office 응용 프로그램에는 인앱 알림 표시줄이 표시되지 않습니다. 업데이트를 다운로드하면 새로 열린 앱에 대한 인앱 알림만 표시됩니다.
>- 서비스 창에서 트리거되거나 업무 외 시간으로 예약된 Office 업데이트의 경우 실행 중인 Office 응용 프로그램을 강제로 닫아야만 알림 없이 업데이트를 설치할 수 있습니다. 
>- 자세한 내용은 [Office 365에 대한 최종 사용자 업데이트 알림](https://docs.microsoft.com/deployoffice/end-user-update-notifications-for-office-365-proplus)을 참조하세요.


## <a name="bkmk_o365_lang"></a>Office 365 업데이트 다운로드 언어 추가
Office 365에서 지원되는 모든 언어의 업데이트를 다운로드하도록 Configuration Manager에 대한 지원을 추가할 수 있습니다.

### <a name="download-updates-for-additional-languages-in-version-1902"></a>1902 버전의 추가 언어 업데이트 다운로드
<!--3555955-->

Configuration Manager 버전 1902부터 업데이트 워크플로는 **Office 365 Client Update**의 여러 추가 언어와 **Windows Update**용 38개 언어를 구분합니다.

필요한 언어를 선택하려면 다음 위치에서 **언어 선택** 페이지를 사용합니다.
- 자동 배포 규칙 만들기 마법사
- 소프트웨어 업데이트 배포 마법사
- 소프트웨어 업데이트 다운로드 마법사
- 자동 배포 규칙 속성

**언어 선택** 페이지에서 **Office 365 클라이언트 업데이트**를 선택하고, **편집**을 클릭합니다. Office 365에 필요한 언어를 추가한 다음 **OK**를 클릭합니다.

![Office 365에 필요한 언어를 추가하는 스크린샷](media/office-update-languages-selection.png)

### <a name="to-add-support-to-download-updates-for-additional-languages-in-version-1810-and-earlier"></a>1810년 이전 버전의 추가 언어에 대한 업데이트를 다운로드하기 위한 지원을 추가합니다.

중앙 관리 사이트나 독립 실행형 기본 사이트의 소프트웨어 업데이트 지점에서 다음 절차를 사용합니다.

> [!IMPORTANT]  
> 추가 Office 365 업데이트 언어 구성은 사이트 전체 설정입니다. 다음 절차를 사용하여 언어를 추가하면 모든 Office 365 업데이트가 소프트웨어 업데이트 다운로드 또는 소프트웨어 업데이트 배포 마법사의 **언어 선택** 페이지에서 선택한 언어 외에 추가한 언어로도 다운로드됩니다.

1. 명령 프롬프트에서 관리자 권한으로 *wbemtest*를 입력하여 Windows Management Instrumentation 테스터를 엽니다.
2. **연결**을 클릭한 후 *root\sms\site_&lt;siteCode&gt;* 를 입력합니다.
3. **쿼리**를 클릭한 후 다음 쿼리를 실행합니다. *select &#42; from SMS_SCI_Component where componentname ="SMS_WSUS_CONFIGURATION_MANAGER"*  
   ![WMI 쿼리](../media/1-wmiquery.png)
4. 결과 창에서 중앙 관리 사이트 또는 독립 실행형 기본 사이트의 사이트 코드가 있는 개체를 두 번 클릭합니다.
5. **속성** 속성을 선택하고 **속성 편집**을 클릭한 후 **포함값 보기**를 클릭합니다.
   ![속성 편집기](../media/2-propeditor.png)
6. 첫 번째 쿼리 결과부터 시작해서 **PropertyName** 속성의 **AdditionalUpdateLanguagesForO365**가 있는 개체를 찾을 때까지 각 개체를 엽니다.
7. **Value2**를 선택하고 **속성 편집**을 클릭합니다.  
   ![Value2 속성 편집](../media/3-queryresult.png)
8. **Value2** 속성에 다른 언어를 추가하고 **속성 저장**을 클릭합니다. <br/> 예를 들면 pt-pt(포르투갈어 - 포르투갈), af-za(아프리칸스어 - 남아프리카), nn-no(노르웨이어(니노르스크) - 노르웨이) 등이 있습니다. 예제 언어에 `pt-pt,af-za,nn-no`를 입력할 수 있습니다. 언어 사이에 공백을 사용하지 마십시오.
 
   ![속성 편집기에서 언어 추가](../media/4-props.png)  
9. **닫기** 클릭, **닫기** 클릭, **속성 저장** 클릭, **개체 저장** 클릭(여기에서 **닫기**를 클릭하면 값은 삭제됩니다). **닫기**를 클릭한 다음, **종료**를 클릭하여 WMI(Management Instrumentation) 테스터를 종료합니다.
10. Configuration Manager 콘솔에서 **소프트웨어 라이브러리** > **개요** > **Office 365 클라이언트 관리** > **Office 365 업데이트**로 이동합니다.
11. 이제 Office 365 업데이트를 다운로드하면 마법사에서 선택하고 이 절차에서 구성한 언어로 업데이트가 다운로드됩니다. 업데이트가 올바른 언어로 다운로드되는지 확인하려면 업데이트의 패키지 원본으로 이동한 후 파일 이름에 언어 코드가 포함된 파일을 찾습니다.  
    ![추가 언어가 있는 파일 이름](../media/5-verification.png)

## <a name="updating-office-365-proplus-in-a-task-sequence"></a>작업 순서에서 Office 365 ProPlus 업데이트
[소프트웨어 업데이트 설치](https://docs.microsoft.com/sccm/osd/understand/task-sequence-steps#BKMK_InstallSoftwareUpdates) 작업 순서 단계를 사용하여 Office 365 업데이트를 설치할 때 배포된 업데이트가 사용할 수 없는 상태로 검색될 수 있습니다.  이 문제는 예약된 Office 자동 업데이트 작업이 한 번 이상 실행되지 않은 경우에 발생할 수 있습니다([Office 365 업데이트 배포](https://docs.microsoft.com/sccm/sum/deploy-use/manage-office-365-proplus-updates#deploy-office-365-updates)의 참고 참조). 예를 들어, 이 단계를 실행하기 직전에 Office 365 ProPlus가 설치된 경우 이 문제가 발생할 수 있습니다.

배포된 업데이트가 제대로 검색되도록 업데이트 채널이 설정되었는지 확인하려면 다음 방법 중 하나를 사용합니다.

**방법 1:**
1. 같은 버전의 Office 365 ProPlus가 있는 머신에서 작업 스케줄러(taskschd.msc)를 열고 Office 365 자동 업데이트 작업을 식별합니다. 일반적으로 **작업 스케줄러 라이브러리** >**Microsoft**>**Office** 아래에 있습니다.
2. 자동 업데이트 작업을 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.
3. **작업** 탭으로 이동하여 **편집**을 클릭합니다. 명령 및 인수를 복사합니다. 
4. Configuration Manager 콘솔에서 작업 순서를 편집합니다.
5. 작업 순서에서 **소프트웨어 업데이트 설치** 단계 전에 새로운 **명령줄 실행** 단계를 추가합니다. Office 365 ProPlus가 동일한 작업 순서의 일부로 설치되는 경우 Office가 설치된 후 이 단계가 실행되는지 확인합니다.
6. Office 자동 업데이트 예약된 작업에서 수집한 명령과 인수를 복사합니다. 
7. **확인**을 클릭합니다. 

**방법 2:**
1. 같은 버전의 Office 365 ProPlus가 있는 머신에서 작업 스케줄러(taskschd.msc)를 열고 Office 365 자동 업데이트 작업을 식별합니다. 일반적으로 **작업 스케줄러 라이브러리** >**Microsoft**>**Office** 아래에 있습니다.
2. Configuration Manager 콘솔에서 작업 순서를 편집합니다.
3. 작업 순서에서 **소프트웨어 업데이트 설치** 단계 전에 새로운 **명령줄 실행** 단계를 추가합니다. Office 365 ProPlus가 동일한 작업 순서의 일부로 설치되는 경우 Office가 설치된 후 이 단계가 실행되는지 확인합니다.
4. 명령줄 필드에 예약된 작업을 실행하는 명령줄을 입력합니다. 아래 예를 참조하여 따옴표로 묶인 문자열이 1단계에서 식별한 작업의 이름 및 경로와 일치하는지 확인합니다.  

    예: `schtasks /run /tn "\Microsoft\Office\Office Automatic Updates 2.0"`
5. **확인**을 클릭합니다. 

## <a name="bkmk_channel"></a> Office 365 클라이언트가 Configuration Manager에서 업데이트를 받도록 설정한 후에 업데이트 채널 변경

Office 365 ProPlus를 배포한 후 그룹 정책 또는 ODT (Office 배포 도구)를 사용 하 여 업데이트 채널을 변경할 수 있습니다. 예를 들어 반기 채널에서 반기 채널 (대상 지정)로 장치를 이동할 수 있습니다. 채널을 변경 하는 경우 Office는 전체 버전을 다시 설치 하거나 다운로드 하지 않고도 자동으로 업데이트 됩니다. 자세한 내용은 [조직에서 장치에 대 한 Office 365 ProPlus 업데이트 채널 변경](https://docs.microsoft.com//deployoffice/change-update-channels)을 참조 하세요.


## <a name="next-steps"></a>다음 단계

Configuration Manager의 Office 365 클라이언트 관리 대시보드를 사용하여 Office 365 클라이언트 정보를 검토하고 Office 365 앱을 배포합니다. 자세한 내용은 [Office 365 클라이언트 관리 대시보드](/sccm/sum/deploy-use/office-365-dashboard)를 참조하세요.
