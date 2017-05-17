---
title: "Office 365 ProPlus 업데이트 관리 | Microsoft 문서"
description: "Configuration Manager는 WSUS 카탈로그의 Office 365 클라이언트 업데이트를 사이트 서버와 동기화하여 업데이트를 클라이언트에 배포할 수 있게 합니다."
keywords: 
author: dougeby
ms.author: dougeby
manager: angrobe
ms.date: 03/24/2017
ms.topic: article
ms.prod: configuration-manager
ms.service: 
ms.technology:
- configmgr-sum
ms.assetid: eac542eb-9aa1-4c63-b493-f80128e4e99b
ms.translationtype: Human Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: 016580dc6ee3c5268833db941d42416a976d201c
ms.contentlocale: ko-kr
ms.lasthandoff: 05/17/2017

---

# <a name="manage-office-365-proplus-with-configuration-manager"></a>Configuration Manager를 사용하여 Office 365 ProPlus 관리

*적용 대상: System Center Configuration Manager(현재 분기)*

Configuration Manager는 Office 365 클라이언트 업데이트를 동기화하고 Office 365가 설치된 클라이언트에 업데이트를 배포할 수 있게 합니다. Configuration Manager 버전 1610부터 Office 365 클라이언트 관리 대시보드에서 Office 365 클라이언트 정보를 검토할 수 있습니다.

Configuration Manager 버전 1602부터, Configuration Manager에서 소프트웨어 업데이트 관리 워크플로를 사용하여 Office 365 클라이언트 업데이트를 관리할 수 있습니다. Microsoft에서 새 Office 365 클라이언트 업데이트를 Office CDN(Content Delivery Network)에 게시하면 Microsoft에서 업데이트 패키지도 WSUS(Windows Server Update Services)에 게시합니다. Configuration Manager에서 WSUS 카탈로그의 Office 365 클라이언트 업데이트를 사이트 서버로 동기화한 후에 업데이트를 클라이언트에 배포할 수 있습니다.

버전 1702부터 Office 365 클라이언트 관리 대시보드에서 Office 365 설치 관리자를 시작하여 초기 Office 365 앱 설치 환경을 간편하게 만들 수 있습니다. 마법사를 통해 Office 365 설치 설정을 구성하고, Office CDN(콘텐츠 배달 네트워크)에서 파일을 다운로드하고, 콘텐츠가 포함된 스크립트 응용 프로그램을 만들고 배포할 수 있습니다.

## <a name="office-365-client-management-dashboard"></a>Office 365 클라이언트 관리 대시보드  
Configuration Manager 버전 1610부터 Configuration Manager 콘솔에서 Office 365 클라이언트 관리 대시보드를 사용할 수 있습니다. 대시보드를 보려면 **소프트웨어 라이브러리** > **개요** > **Office 365 클라이언트 관리**로 이동합니다.

대시보드는 다음에 대한 차트를 표시합니다.

- Office 365 클라이언트 수
- Office 365 클라이언트 버전
- Office 365 클라이언트 언어
- Office 365 클라이언트 채널     
자세한 내용은 [Office 365 ProPlus의 업데이트 채널 개요](https://technet.microsoft.com/library/mt455210.aspx)를 참조하세요.
<!--- - Automatic deployment rules with Office 365 apps (have Office 365 Client selected in the set of available products). --->

<!---You can take the following actions on the dashboard:
- --->

대시보드 맨 위에 있는 **컬렉션** 드롭다운 설정을 사용하여 특정 컬렉션 멤버별로 대시보드 데이터를 필터링합니다.

### <a name="display-data-in-the-office-365-client-management-dashboard"></a>Office 365 클라이언트 관리 대시보드에 데이터 표시
Office 365 클라이언트 관리 대시보드에 표시되는 데이터는 하드웨어 인벤토리에서 옵니다. 하드웨어 인벤토리를 사용하도록 설정하고 **Office 365 ProPlus 구성** 하드웨어 인벤토리를 선택해야 대시보드에 데이터를 표시할 수 있습니다.
#### <a name="to-display-data-in-the-office-365-client-management-dashboard"></a>Office 365 클라이언트 관리 대시보드에 데이터를 표시하려면
1. 하드웨어 인벤토리를 아직 사용하도록 설정하지 않은 경우 지금 설정합니다. 자세한 내용은 [하드웨어 인벤토리 구성](\sccm\core\clients\manage\configure-hardware-inventory)을 참조하세요.
2. Configuration Manager 콘솔에서 **관리** > **클라이언트 설정** > **기본 클라이언트 설정**으로 이동합니다.  
3. **홈** 탭의 **속성** 그룹에서 **속성**을 클릭합니다.  
4. 에 **기본 클라이언트 설정** 대화 상자를 클릭 하 여 **하드웨어 인벤토리**.  
5. 에 **장치 설정을** 목록에서 클릭 **클래스 설정**.  
6. **하드웨어 인벤토리 클래스** 대화 상자에서 **Office 365 ProPlus 구성**을 선택합니다.  
7.  클릭 하 여 **확인** 변경 내용을 저장 하 고 닫습니다는 **하드웨어 인벤토리 클래스** 대화 상자.  
하드웨어 인벤토리가 보고되면 Office 365 클라이언트 관리 대시보드에서 데이터를 표시하기 시작합니다.

## <a name="deploy-office-365-updates-with-configuration-manager"></a>Configuration Manager를 사용하여 Office 365 업데이트 배포
Configuration Manager를 사용하여 Office 365 업데이트를 배포하려면 다음 단계를 따르세요.

1.  항목의 **Configuration Manager를 사용하여 Office 365 클라이언트 업데이트를 관리하기 위한 요구 사항** 섹션에서 Configuration Manager를 사용하여 Office 365 클라이언트 업데이트를 관리하기 위한 [요구 사항을 확인](https://technet.microsoft.com/library/mt628083.aspx)합니다.  

2.  [소프트웨어 업데이트 지점을 구성](../get-started/configure-classifications-and-products.md)하여 Office 365 클라이언트 업데이트를 동기화합니다. 분류에 대한 **업데이트**를 설정하고 제품에 대한 **Office 365 클라이언트**를 선택합니다. Office 365 클라이언트 제품을 선택할 수 있으려면 먼저 소프트웨어 업데이트를 한 번 이상 동기화해야 할 수도 있습니다. **업데이트** 분류를 사용하도록 소프트웨어 업데이트 지점을 구성한 후 소프트웨어 업데이트를 동기화해야 합니다.
3.  Office 365 클라이언트가 Configuration Manager에서 업데이트를 받을 수 있도록 합니다. 이렇게 하려면 Configuration Manager 클라이언트 설정을 사용하거나 그룹 정책을 사용합니다. 다음 방법 중 하나를 통해 클라이언트를 사용하도록 설정합니다.  
    - 방법 1: Configuration Manager 버전 1606부터, Configuration Manager 클라이언트 설정을 사용하여 Office 365 클라이언트 에이전트를 관리할 수 있습니다. 이 설정을 구성하고 Office 365 업데이트를 배포한 후 Configuration Manager 클라이언트 에이전트는 Office 365 클라이언트 에이전트와 통신하여 배포 지점에서 Office 365 업데이트를 다운로드하고 설치합니다. Configuration Manager는 Office 365 ProPlus 클라이언트 설정의 인벤토리를 사용합니다.
      1.  Configuration Manager 콘솔에서 **관리** > **개요** > **클라이언트 설정**을 클릭합니다.  

      2.  적절한 장치 설정을 열어 클라이언트 에이전트를 사용하도록 설정합니다. 기본 및 사용자 지정 클라이언트 설정에 대한 자세한 내용은 [System Center Configuration Manager에서 클라이언트 설정을 구성하는 방법](../../core/clients/deploy/configure-client-settings.md)을 참조하세요.  

      3.  **소프트웨어 업데이트**를 클릭하고 **Office 365 클라이언트 에이전트 관리 사용** 설정에 대해 **예**를 선택합니다.  

    - 방법 2: Office 배포 도구 또는 그룹 정책을 사용하여 [Office 365 클라이언트가 Configuration Manager에서 업데이트를 받을 수 있도록 설정](https://technet.microsoft.com/library/mt628083.aspx#BKMK_EnableClient)합니다.  

4. 클라이언트에 [Office 365 업데이트를 배포](deploy-software-updates.md)합니다.   

> [!Important]
> Office 365 클라이언트를 두 개 이상의 언어로 사용하는데 더 적은 언어의 업데이트를 다운로드하면 업데이트가 설치되지 않습니다. 예를 들어 en-us 및 de-de가 포함된 Office 365 클라이언트가 있는 경우를 살펴봅니다. 사이트 서버에서 적용 가능한 Office 365 업데이트의 en-us 콘텐츠만 다운로드하고 배포합니다. 사용자가 소프트웨어 센터에서 이 업데이트의 설치를 시작하면 콘텐츠를 다운로드하는 동안 업데이트가 중단됩니다. Office 365 클라이언트와 같은 언어로 업데이트를 다운로드 및 배포해야 합니다.  


## <a name="add-other-languages-for-office-365-update-downloads"></a>Office 365 업데이트 다운로드에 다른 언어 추가
Configuration Manager 버전 1610부터는 Configuration Manager의 지원 여부에 관계 없이 Office 365에서 지원되는 모든 언어의 업데이트를 Configuration Manager에서 다운로드하도록 지원하는 기능을 추가할 수 있습니다.
> [!IMPORTANT]  
> 추가 Office 365 업데이트 언어 구성은 사이트 전체 설정입니다. 다음 절차를 사용하여 언어를 추가하면 모든 Office 365 업데이트가 소프트웨어 업데이트 다운로드 또는 소프트웨어 업데이트 배포 마법사의 언어 선택 페이지에서 선택한 언어 외에 해당 언어로도 다운로드됩니다.

### <a name="to-add-support-to-download-updates-for-additional-languages"></a>추가 언어의 업데이트 다운로드 지원을 추가하려면
소프트웨어 업데이트 지점 사이트 시스템 역할이 설치된 중앙 관리 사이트나 독립 실행형 기본 사이트에서 다음 절차를 사용합니다.
1. 명령 프롬프트에서 관리자 권한으로 *wbemtest*를 입력하여 Windows Management Instrumentation 테스터를 엽니다.
2. **연결**을 클릭한 후 *root\sms\site_&lt;siteCode&gt;*를 입력합니다.
3. **쿼리**를 클릭한 후 다음 쿼리를 실행합니다. *select &#42; from SMS_SCI_Component where componentname ="SMS_WSUS_CONFIGURATION_MANAGER"*  
   ![WMI 쿼리](..\media\1-wmiquery.png)
4. 결과 창에서 중앙 관리 사이트 또는 독립 실행형 기본 사이트의 사이트 코드가 있는 개체를 두 번 클릭합니다.
5. **속성** 속성을 선택하고 **속성 편집**을 클릭한 후 **포함값 보기**를 클릭합니다.
![속성 편집기](..\media\2-propeditor.png)
6. 첫 번째 쿼리 결과부터 시작해서 **PropertyName** 속성의 **AdditionalUpdateLanguagesForO365**가 있는 개체를 찾을 때까지 각 개체를 엽니다.
7. **Value2**를 선택하고 **속성 편집**을 클릭합니다.  
![Value2 속성 편집](..\media\3-queryresult.png)
8. **Value2** 속성에 다른 언어를 추가하고 **속성 저장**을 클릭합니다.  
예를 들면 pt-pt(포르투갈어 - 포르투갈), af-za(아프리칸스어 - 남아프리카), nn-no(노르웨이어(니노르스크) - 노르웨이) 등이 있습니다.  
![속성 편집기에서 언어 추가](..\media\4-props.png)  
9. **닫기**, **닫기**, **속성 저장**, **개체 저장**(여기에서 **닫기**를 클릭하면 값이 취소됨), **닫기**를 차례로 클릭한 다음 **종료**를 클릭하여 Windows Management Intstrumentation 테스터를 종료합니다.
10. Configuration Manager 콘솔에서 **소프트웨어 라이브러리** > **개요** > **Office 365 클라이언트 관리** > **Office 365 업데이트**로 이동합니다.
11. 이제 Office 365 업데이트를 다운로드하면 마법사에서 선택한 언어와 이 절차에서 구성한 언어로 업데이트가 다운로드됩니다. 이러한 언어로 다운로드된 업데이트를 확인하려면 업데이트의 패키지 원본으로 이동한 후 파일 이름에 언어 코드가 포함된 언어를 찾습니다.  
![추가 언어가 있는 파일 이름](..\media\5-verification.png)


## <a name="change-the-update-channel-after-you-enable-office-365-clients-to-receive-updates-from-configuration-manager"></a>Office 365 클라이언트가 Configuration Manager에서 업데이트를 받도록 설정한 후에 업데이트 채널 변경
Office 365 클라이언트가 Configuration Manager에서 업데이트를 받도록 설정한 후에 업데이트 채널을 변경하려는 경우 그룹 정책을 사용하여 레지스트리 키 값의 변경 사항을 Office 365 클라이언트에 배포할 수 있습니다. **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Office\ClickToRun\Configuration\CDNBaseUrl** 레지스트리 키를 다음 중 한 값을 사용하도록 변경합니다.

- 현재 채널:  
  **CDNBaseUrl** = http&#58;//officecdn.microsoft.com/pr/492350f6-3a01-4f97-b9c0-c7c6ddf67d60

- 지연된 채널:  
  **CDNBaseUrl** = http&#58;//officecdn.microsoft.com/pr/7ffbc6bf-bc32-4f92-8982-f9dd17fd3114

- 현재 채널의 첫 번째 릴리스:  
  **CDNBaseUrl** = http&#58;//officecdn.microsoft.com/pr/64256afe-f5d9-4f86-8936-8840a6a4f5be

- 지연된 채널의 첫 번째 릴리스:  
  **CDNBaseUrl** = http&#58;//officecdn.microsoft.com/pr/b8f9b850-328d-4355-9145-c59439a0c4cf

## <a name="deploy-office-365-apps"></a>Office 365 앱 배포  
버전 1702부터 Office 365 클라이언트 관리 대시보드에서 Office 365 설치 관리자를 시작하여 초기 Office 365 앱 설치 환경을 간편하게 만들 수 있습니다. 마법사를 통해 Office 365 설치 설정을 구성하고, Office CDN(콘텐츠 배달 네트워크)에서 파일을 다운로드하고, 파일에 대한 스크립트 응용 프로그램을 만들고 배포할 수 있습니다.

Office 365가 설치되지 않은 클라이언트에는 Office 365 업데이트를 적용할 수 없으므로 이 기능이 특히 유용합니다. 버전 1702 이전에서는 Office 365 앱을 클라이언트에 처음 설치하려면 필요한 모든 언어 팩을 포함하여 Office 365 배포 도구(ODT) 및 Office 365 설치 원본 파일을 수동으로 다운로드하고 올바른 Office 버전 및 채널을 지정하는 Configuration.xml을 생성해야 합니다. 그리고 클라이언트가 Office 365 앱을 설치하기 위한 레거시 패키지 또는 스크립트 응용 프로그램을 만들고 배포해야 합니다.

> [!NOTE]
> - Office 365 설치 관리자를 실행하는 컴퓨터에서 인터넷에 액세스할 수 있어야 합니다.  
> - Office 365 설치 관리자를 실행하는 사용자는 마법사에서 위치 공유가 제공되는 콘텐츠에 대한 **읽기** 및 **쓰기** 권한이 있어야 합니다.
> - 404 다운로드 오류가 표시되면 다음 파일을 사용자 %temp% 폴더로 복사합니다.
>    - [releasehistory.xml](http://officecdn.microsoft.com.edgesuite.net/wsus/releasehistory.cab)
>    - [o365client_32bit.xml](http://officecdn.microsoft.com/pr/wsus/ofl.cab)  
> - Office 365 설치 관리자를 사용하여 Office 365 응용 프로그램을 만들고 배포한 후에는 기본적으로 Configuration Manager가 Office 업데이트를 관리합니다. Office 365 클라이언트가 Configuration Manager에서 업데이트를 받게 하려면 [Configuration Manager를 사용하여 Office 365 업데이트 배포](#deploy-office-365-updates-with-configuration-manager)를 참조하세요.

### <a name="to-deploy-office-365-apps-to-clients-from-the-office-365-client-management-dashboard"></a>Office 365 클라이언트 관리 대시보드에서 클라이언트에 Office 365 앱을 배포하려면
1. Configuration Manager 콘솔에서 **소프트웨어 라이브러리** > **개요** > **Office 365 클라이언트 관리**로 이동합니다.
2. 오른쪽 위 창에서 **Office 365 설치 관리자**를 클릭합니다. Office 365 클라이언트 설치 마법사가 열립니다.
3. **응용 프로그램 설정** 페이지에서 앱에 대한 이름과 설명을 제공하고 파일에 대한 다운로드 위치를 입력한 후 **다음**을 클릭합니다. 위치는 &#92;&#92;*server*&#92;*share* 형식으로 지정해야 합니다.
4. **클라이언트 설정 가져오기** 페이지에서, 기존 XML 구성 파일에서 Office 365 클라이언트 설정을 가져올지 아니면 설정을 수동으로 지정할지 여부를 지정하고 **다음**을 클릭합니다.  

    기존 구성 파일이 있는 경우 해당 파일의 위치를 입력하고 7단계로 건너뜁니다. 위치는 &#92;&#92;*server*&#92;*share*&#92;*filename*.XML 형식으로 지정해야 합니다.
5. **클라이언트 제품** 페이지에서 사용할 Office 365 제품군을 선택하고, 포함할 응용 프로그램을 선택하고, 포함할 추가 Office 제품을 선택한 후 **다음**을 클릭합니다.
6. **클라이언트 설정** 페이지에서 포함할 설정을 선택하고 **다음**을 클릭합니다.
7. **배포** 페이지에서 응용 프로그램을 배포할지 여부를 선택하고 **다음**을 클릭합니다.  
마법사에서 패키지를 배포하지 않도록 선택한 경우 9단계로 건너뜁니다.
8. 마법사 페이지의 나머지 부분을 일반적인 응용 프로그램 배포와 마찬가지로 구성합니다. 자세한 내용은 [응용 프로그램 만들기 및 배포](/sccm/apps/get-started/create-and-deploy-an-application)를 참조하세요.
9. 마법사를 완료합니다.
10. Configuration Manager의 **소프트웨어 라이브러리** > **개요** > **응용 프로그램 관리** > **응용 프로그램**에서 다른 응용 프로그램과 마찬가지로 응용 프로그램을 배포 또는 편집할 수 있습니다.   

> [!IMPORTANT]
> Configuration Manager의 Office 365 응용 프로그램 마법사를 사용하여 만들고 배포하는 Office 365 앱은 **Office 365 클라이언트 에이전트 관리 사용** 소프트웨어 업데이트 클라이언트 에이전트 설정을 사용할 때까지 Configuration Manager에서 자동으로 관리되지 않습니다. 자세한 내용은 [클라이언트 설정 정보](/sccm/core/clients/deploy/about-client-settings)를 참조하세요.

>[!NOTE]
>Office 365 앱을 배포한 후 앱을 유지 관리하기 위한 자동 배포 규칙을 만들 수 있습니다. Office 365 앱에 대한 자동 배포 규칙을 만들려면 Office 365 클라이언트 관리 대시보드에서 **ADR 만들기**를 클릭하고 제품을 선택할 때 **Office 365 클라이언트**를 선택합니다. 자세한 내용은 [소프트웨어 업데이트 자동 배포](/sccm/sum/deploy-use/automatically-deploy-software-updates)를 참조하세요.

<!--- You can create an Office 365 app without using the Office 365 Installation Wizard. To do this, you use the Office 2016 Deployment Tool (ODT) to download Office installation source files to a network share, generate Configure.xml that specifies the correct Office version and channel, and so on. Then, create an app for the files using the normal app management process.
> [!Note]
> The Office 365 Installation Wizard was introduced in Configuration Manager version 1702 and provides an easy way to create Office 365 apps.

- [Download the Office 2016 Deployment Tool](http://aka.ms/ODT2016) from the Microsoft Download Center.  
- Review the [configuration options for the Office Deployment Tool](https://technet.microsoft.com/library/jj219426.aspx).

You can create an application just as you would with any other application in Configuration Manager from **Software Library** > **Overview** > **Application Management** > **Applications**. For details, see [Create and deploy an application](/sccm/apps/get-started/create-and-deploy-an-application).
--->

<!--- ## Next steps
Use the Office 365 Client Management dashboard in Configuration Manager to review Office 365 client information and deploy Office 365 apps. For details, see [Manage Office 365 apps](manage-office-365-apps.md). --->

