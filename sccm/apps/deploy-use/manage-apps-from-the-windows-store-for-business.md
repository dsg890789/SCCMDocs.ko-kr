---
title: 비즈니스용 Microsoft Store
titleSuffix: Configuration Manager
description: Configuration Manager를 사용하여 비즈니스용 Microsoft Store에서 앱을 관리하고 배포합니다.
ms.date: 07/30/2018
ms.prod: configuration-manager
ms.technology: configmgr-app
ms.topic: conceptual
ms.assetid: 8cdb22a6-72d7-41f5-9bed-c098b1bcf675
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: d0a32357001f37f537f13fe85e71a41f9cb658ac
ms.sourcegitcommit: 874d78f08714a509f61c52b154387268f5b73242
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56122443"
---
# <a name="manage-apps-from-the-microsoft-store-for-business-with-configuration-manager"></a>Configuration Manager를 사용하여 비즈니스용 Microsoft Store에서 앱 관리

[비즈니스용 Microsoft Store](https://www.microsoft.com/business-store)는 조직을 위한 Windows 앱을 찾고 구매하는 곳입니다. Configuration Manager에 스토어를 연결하면 구매한 앱 목록이 동기화됩니다. Configuration Manager 콘솔에서 이러한 앱을 보고 다른 앱을 배포하는 것처럼 배포합니다.


## <a name="bkmk_apps"></a> 온라인 및 오프라인 앱

비즈니스용 Microsoft Store에서는 두 가지 유형의 앱을 지원합니다.

- **온라인**: 이 라이선스 유형에서는 사용자와 디바이스가 저장소에 연결하여 앱과 해당 라이선스를 가져와야 합니다. Windows 10 디바이스는 Azure AD(Active Directory) 도메인에 가입된 디바이스여야 합니다.  

- **오프라인**: 이 유형을 사용하면 캐시 앱 및 라이선스를 온-프레미스 네트워크 내에서 직접 배포할 수 있습니다. 디바이스를 스토어에 연결하거나 인터넷에 연결할 필요가 없습니다.

비즈니스용 Microsoft Store에 대해 [자세히 알아보세요](https://docs.microsoft.com/microsoft-store/microsoft-store-for-business-overview).

Configuration Manager에서는 Configuration Manager 클라이언트를 사용하는 Windows 10 디바이스 및 Microsoft Intune을 사용하는 Windows 10 디바이스 모두에서 비즈니스용 Microsoft Store 앱을 관리하도록 지원합니다. Configuration Manager는 온라인 및 오프라인 앱에 대해 다음과 같은 기능을 제공합니다.


|기능|오프라인 앱|온라인 앱|
|------------|------------|------------|
|Configuration Manager에 앱 데이터 동기화<br>(24시간마다 동기화 발생)|예|예|
|스토어 앱에서 Configuration Manager 애플리케이션 만들기|예|예|
|스토어에서 무료 앱 지원|예|예|
|스토어에서 유료 앱 지원|아니요|예<sup>1</sup>|
|사용자 또는 디바이스 컬렉션에 대한 필수 배포 지원|예|예|
|사용자 또는 디바이스 컬렉션에 대한 사용 가능한 배포 지원|예|예|
|스토어에서 LOB(기간 업무) 앱 지원|예|예|
|디바이스의 모든 사용자를 위해 스토어 앱 프로비전<sup>2</sup><!--1358310-->|예|예|

- <sup>1</sup> Configuration Manager 클라이언트를 통해 사용이 허가된 온라인 앱을 Windows 10 장치에 배포하려면 Windows 10, 버전 1703 이상을 실행하고 있어야 합니다.  

- <sup>2</sup> 버전 1806부터 가능합니다. 자세한 내용은 [Windows 애플리케이션 만들기](/sccm/apps/get-started/creating-windows-applications#bkmk_provision)를 참조하세요.  


### <a name="deploying-online-apps-using-the-microsoft-store-for-business-to-devices-that-run-the-configuration-manager-client"></a>Configuration Manager 클라이언트를 실행하는 디바이스에 비즈니스용 Microsoft Store를 사용하여 온라인 앱 배포

전체 Configuration Manager 클라이언트를 실행하는 디바이스에 비즈니스용 Microsoft Store 앱을 배포하기 전에 다음 사항을 고려하세요.

- 전체 기능을 사용하려면 디바이스가 Windows 10, 버전 1703 이상을 실행하고 있어야 합니다.  

- 디바이스는 비즈니스용 Microsoft Store를 관리 도구로 등록한 동일한 테넌트에서 Azure AD에 가입되어 있어야 합니다.  

- 로컬 관리자 계정이 디바이스에 로그인하면 비즈니스용 Microsoft Store 앱에 액세스할 수 없습니다.  

- 디바이스는 비즈니스용 Microsoft Store에 인터넷을 통해 실시간으로 연결되어 있어야 합니다. 프록시 구성을 포함한 자세한 내용은 [필수 구성 요소](https://docs.microsoft.com/microsoft-store/prerequisites-microsoft-store-for-business)를 참조하세요.  


### <a name="notes-for-devices-running-earlier-versions-of-windows-10"></a>Windows 10의 이전 버전을 실행하는 디바이스에 대한 참고 사항

Configuration Manager 클라이언트가 있고 Windows 10 버전 1607 이하를 실행하는 디바이스에는 다음과 같은 기능이 적용됩니다.  

다음 방법 중 하나를 사용하여 디바이스에 앱 설치를 강제하는 경우:  

- 사용자가 앱 설치  

- 배포가 해당 설치 최종 기한에 도달   

- 필수 배포에 대한 설치 후 재평가  

그런 다음, 다음과 같은 동작이 발생합니다.  

- Configuration Manager 클라이언트가 비즈니스용 Microsoft Store 앱을 실행하여 앱을 “강제”합니다.  

- 사용자는 스토어에서 설치를 완료해야 합니다.  

- Configuration Manager 콘솔에서 앱 배포 상태가 실패하고 다음 오류를 보고합니다. “Microsoft Store 앱이 클라이언트 PC에서 열렸으며 사용자가 설치를 완료하기를 기다리고 있습니다.”  

다음 애플리케이션 평가 주기에서:  

- 사용자가 스토어에서 응용 프로그램을 설치한 경우 응용 프로그램에서 **성공** 상태를 보고합니다.  

- 사용자가 스토어에서 앱을 설치하려고 시도하지 않은 경우:  

    - 필수 배포의 경우 Configuration Manager 클라이언트가 스토어 앱을 다시 시작하려고 시도합니다.  

    - 사용 가능한 배포는 다시 강제되지 않습니다.


#### <a name="further-notes-for-devices-running-earlier-versions-of-windows-10"></a>Windows 10의 이전 버전을 실행하는 디바이스에 대한 추가 참고 사항:

- 비즈니스용 Microsoft Store에서 LOB(기간 업무) 앱을 배포할 수 없습니다.  

- 스토어에서 유료 앱을 배포할 경우 사용자가 스토어에 로그인하고 직접 앱을 구매해야 합니다.  

- 소비자 버전의 Microsoft Store에 대한 액세스를 사용하지 않는 그룹 정책을 배포하는 경우 비즈니스용 Microsoft Store의 배포가 작동하지 않습니다. 이 동작은 비즈니스용 Microsoft Store를 사용하는 경우에도 발생합니다.  



## <a name="bkmk_setup"></a> 비즈니스용 Microsoft Store 동기화 설정

조직에서 획득한 앱 목록을 동기화하면 Configuration Manager 콘솔에서 이러한 앱을 볼 수 있습니다.

Configuration Manager 사이트를 Azure AD 및 비즈니스용 Microsoft Store에 연결합니다. 이 프로세스의 자세한 내용과 세부 정보는 [Azure 서비스 구성](/sccm/core/servers/deploy/configure/azure-services-wizard)을 참조하세요. **비즈니스용 Microsoft Store** 서비스에 대한 연결을 만듭니다.


### <a name="bkmk_config"></a> 추가 정보 및 구성 

Azure Services 마법사의 **앱** 페이지에서, 먼저 **Azure 환경** 및 **웹앱**을 구성합니다. 그런 다음, 페이지 하단의 **자세한 정보** 섹션을 읽습니다. 이 정보에는 비즈니스용 Microsoft Store 포털에 대한 다음 추가 작업이 포함됩니다.  

- Configuration Manager를 스토어 관리 도구로 구성합니다. 자세한 내용은 [관리 공급자 구성](https://docs.microsoft.com/microsoft-store/configure-mdm-provider-microsoft-store-for-business)을 참조하세요.  

- 오프라인 사용이 허가된 앱에 대한 지원을 활성화합니다. 자세한 내용은 [오프라인 앱 배포](https://docs.microsoft.com/microsoft-store/distribute-offline-apps)를 참조하세요.  

- 하나 이상의 앱을 구매합니다. 자세한 내용은 [앱 찾기 및 구매](https://docs.microsoft.com/microsoft-store/find-and-acquire-apps-overview)를 참조하세요.  

Azure Services 마법사의 **구성** 페이지에서 다음 정보를 지정합니다.  

- **비즈니스용 Microsoft 스토어 앱 콘텐츠 스토리지 경로**: 폴더를 포함한 공유 네트워크 경로를 지정합니다. 예: `\\server\share\folder` 사이트 서버가 스토어와 동기화되면 콘텐츠가 이 위치에 캐시됩니다. Configuration Manager에서 애플리케이션을 만들면 사이트 서버가 이 로컬 캐시의 앱 콘텐츠를 사이트의 콘텐츠 라이브러리로 복사합니다.  

- **언어 선택**:  스토어에서 동기화할 언어를 선택하고 소프트웨어 센터의 사용자에게 표시합니다. 예를 들어 사용자가 독일어로 Windows를 구성하면 소프트웨어 센터는 스토어 앱용 독일어 문자열을 표시합니다. 이 동작을 실행하려면 언어가 동기화되고 특정 애플리케이션에 존재해야 합니다.    

- **기본 언어**: 사용자의 언어를 사용할 수 없는 경우 사용할 기본 언어를 선택합니다.  



## <a name="bkmk_deploy"></a> 비즈니스용 Microsoft Store 앱에서 Configuration Manager 응용 프로그램을 만들고 배포합니다.

동기화 후 다른 앱과 유사한 스토어 앱을 만들고 배포합니다.

1.  Configuration Manager 콘솔의 **소프트웨어 라이브러리** 작업 영역에서 **애플리케이션 관리**를 확장한 다음 **스토어 앱에 대한 라이선스 정보**를 클릭합니다.  

2.  배포하려는 앱을 선택한 다음, 리본에서 **응용 프로그램 만들기**를 클릭합니다.  

이 사이트는 비즈니스용 Microsoft Store 앱을 포함하는 Configuration Manager 애플리케이션을 만듭니다. 

그런 다음, 이 응용 프로그램을 다른 Configuration Manager 응용 프로그램과 마찬가지로 배포하고 모니터링합니다. 자세한 내용은 다음 아티클을 참조하세요.  
- [애플리케이션 배포](/sccm/apps/deploy-use/deploy-applications)
- [콘솔에서 애플리케이션 모니터링](/sccm/apps/deploy-use/monitor-applications-from-the-console)

> [!IMPORTANT]  
> Microsoft Intune에 등록된 디바이스의 경우 원래 디바이스를 등록한 사용자만 배포된 앱을 사용할 수 있습니다. 다른 사용자는 앱에 액세스할 수 없습니다.



## <a name="next-steps"></a>다음 단계

**소프트웨어 라이브러리** 작업 영역에서 **애플리케이션 관리**를 확장한 다음 **스토어 앱에 대한 라이선스 정보**를 클릭합니다.

관리하는 각 스토어 앱에 대한 다음 정보를 봅니다.
- 앱 이름
- 앱 플랫폼
- 소유한 앱의 라이선스 수
- 사용 가능한 라이선스 수

온라인 앱을 배포한 후에는 해당 앱에 대한 모든 업데이트가 Microsoft Store에서 직접 제공됩니다. 또한 Configuration Manager는 온라인 앱의 버전 준수를 확인하지 않으며 Windows는 설치된 앱을 보고합니다.  

Configuration Manager 클라이언트를 사용하여 Windows 10 디바이스에 오프라인 앱을 배포할 때 사용자가 Configuration Manager 배포에 외부의 응용 프로그램을 업데이트할 수 없습니다. 오프라인 앱에 대한 업데이트의 제어는 학급과 같은 다중 사용자 환경에서 특히 중요합니다. [그룹 정책](https://docs.microsoft.com/windows/configuration/stop-employees-from-using-microsoft-store#a-href-idblock-store-group-policyablock-microsoft-store-using-group-policy)을 사용하여 Microsoft Store를 사용하지 않도록 설정할 수 있습니다. 

비즈니스용 Microsoft Store 관리자가 오프라인 앱을 구매한 후에 스토어를 통해 사용자에게 앱을 게시하지 마세요. 이렇게 구성하면 사용자가 온라인으로 설치하거나 업데이트할 수 없습니다. 사용자는 Configuration Manager를 통해서만 오프라인 앱 업데이트를 수신하게 됩니다. 
