---
title: Windows 애플리케이션 만들기
titleSuffix: Configuration Manager
description: Configuration Manager에서 Windows 애플리케이션을 만들고 배포하는 방법에 대한 자세한 정보를 알아봅니다.
ms.date: 02/21/2019
ms.prod: configuration-manager
ms.technology: configmgr-app
ms.topic: conceptual
ms.assetid: 9181c84e-d74f-44ea-9bb9-f7805eb465fc
author: aczechowski
manager: dougeby
ms.author: aaroncz
ms.openlocfilehash: efc3c6248974990d194158ffaad2791a4be8a5bd
ms.sourcegitcommit: 148745e1c3d9817d8beea20684a54436210959c6
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75817723"
---
# <a name="create-windows-applications-in-configuration-manager"></a>Configuration Manager에서 Windows 애플리케이션 만들기

*적용 대상: Configuration Manager(현재 분기)*

Windows 디바이스에 대한 애플리케이션을 만들어 배포할 때는 [애플리케이션 생성](/sccm/apps/deploy-use/create-applications)에 대한 다른 Configuration Manager 요구 사항 및 절차 외에 다음 사항도 고려하세요.  



## <a name="bkmk_general"></a> 일반적인 고려 사항  

Configuration Manager는 Windows 8.1 및 Windows 10 디바이스용 Windows 앱 패키지(.appx)와 앱 번들(.appxbundle) 형식의 배포를 지원합니다.

Configuration Manager 콘솔에서 애플리케이션을 만들 때 애플리케이션 설치 파일 **형식**을 **Windows 앱 패키지(\*.appx, \*.appxbundle, \*.msix, \*.msixbundle)** 로 선택합니다. 일반적인 앱 만들기에 대한 자세한 내용은 [애플리케이션 만들기](/sccm/apps/deploy-use/create-applications)를 참조하세요. MSIX 형식에 대한 자세한 내용은 [MSIX 형식 지원](#bkmk_msix)을 참조하세요. 

> [!Note]  
> 새 Configuration Manager 기능을 활용하려면 먼저 클라이언트를 최신 버전으로 업데이트합니다. 사이트 및 콘솔을 업데이트할 때 Configuration Manager 콘솔에 새 기능이 표시되지만 클라이언트 버전도 최신 버전이 될 때까지 전체 시나리오가 작동하지 않습니다.<!--SCCMDocs issue 646-->  



## <a name="bkmk_provision"></a> 디바이스의 모든 사용자에 대해 Windows 앱 패키지 프로비전
<!--1358310-->
버전 1806부터 디바이스에서 모든 사용자에 대해 Windows 앱 패키지를 사용하여 애플리케이션을 프로비전합니다. 이 시나리오의 일반적인 한 예는 Minecraft 교육용 버전처럼 비즈니스 및 교육용 Microsoft Store의 앱을 학교에서 학생들이 사용하는 모든 디바이스에 프로비전하는 것입니다. 전에 Configuration Manager는 사용자 당 이러한 애플리케이션 설치만 지원했습니다. 새 디바이스에 로그인한 후 학생은 앱에 액세스하기를 기다려야 합니다. 앱이 모든 사용자용 디바이스에 프로비전되는 경우 더 신속하게 생산적이 될 수 있습니다.

> [!Important]  
> 디바이스에 다른 버전의 동일한 Windows 앱 패키지의 설치, 프로비저닝 및 업데이트 시 예기치 않은 결과가 발생할 수 있으니 주의하십시오. 이 동작은 앱을 프로비전하기 위해 Configuration Manager를 사용하는 경우에 발생할 수 있지만 사용자는 Microsoft 스토어에서 앱을 업데이트할 수 있습니다. 자세한 내용은 [비즈니스용 Microsoft Store에서 앱 관리](/sccm/apps/deploy-use/manage-apps-from-the-windows-store-for-business#next-steps)할 때 다음 단계 지침을 참조하세요.  

오프라인 라이선스 앱을 프로비전하면 Configuration Manager는 Windows가 Microsoft Store에서 자동으로 업데이트하도록 허용하지 않습니다.  

Configuration Manager는 다음 버전의 Windows에서 앱 프로비저닝을 지원합니다.<!--SCCMDocs-pr issue 2762-->
- 설치 작업: Windows 10 버전 1607 이상​
- 제거 작업: Windows 10 버전 1703 이상​

이 기능에 대한 Windows 앱 배포 유형을 구성하려면 **디바이스의 모든 사용자에 대해 이 애플리케이션 프로비전** 옵션을 사용하도록 설정합니다. 자세한 내용은 [애플리케이션 만들기](/sccm/apps/deploy-use/create-applications)를 참조하세요.


> [!Note]  
> 사용자가 이미 로그인한 디바이스에서 프로비전된 애플리케이션을 제거해야 할 경우 두 개의 제거 배포를 만들어야 합니다. 첫 번째 제거 배포를 디바이스를 포함하는 디바이스 컬렉션의 대상으로 지정합니다. 두 번째 제거 배포를 프로비전된 애플리케이션을 사용하여 디바이스에 이미 로그인한 사용자를 포함하는 사용자 컬렉션의 대상으로 지정합니다. 디바이스에서 프로비전된 앱을 제거하는 경우 Windows는 현재 사용자를 위해 해당 앱을 제거하지 않습니다. 



## <a name="bkmk_msix"></a> MSIX 형식 지원
<!--1357427-->

버전 1806부터 Configuration Manager는 새 Windows 10 앱 패키지(.msix) 및 앱 번들(.msixbundle) 형식을 지원합니다. Windows 10 버전 1809 이상에서 이러한 새 형식을 지원합니다.  

- MSIX에 대한 개요는 [A closer look at MSIX](https://blogs.msdn.microsoft.com/sgern/2018/06/18/a-closer-look-at-msix/)(MSIX 자세히 살펴보기)를 참조하세요.  

- 새 MSIX 앱을 만드는 방법은 [MSIX support introduced in Insider Build 17682](https://techcommunity.microsoft.com/t5/MSIX-Blog/MSIX-support-introduced-in-Insider-Build-17682/ba-p/202376)(Insider 빌드 17682에서 도입된 MSIX 지원)를 참조하세요.  


### <a name="convert-applications-to-msix"></a>애플리케이션을 MSIX로 변환
<!--3607729, fka 1359029-->

버전 1810부터 기존 Windows Installer(.msi) 애플리케이션을 MSIX 형식으로 변환합니다. 

#### <a name="prerequisites"></a>전제 조건
- Windows 10 버전 1809 이상을 실행하는 참조 디바이스  

- 이 디바이스에서 로컬 관리 권한을 가진 사용자로 Windows에 로그인  

- 이 디바이스에 다음 앱을 설치합니다.  

    - Configuration Manager 콘솔  

    - Microsoft Store에서 [MSIX 패키징 도구](https://www.microsoft.com/store/productId/9N5LW3JBCXKF)를 설치합니다.  

    - [MSIX 패키징 도구 드라이버](https://docs.microsoft.com/windows/msix/packaging-tool/mpt-known-issues#msix-packaging-tool-driver-considerations)를 설치합니다.<!--SCCMDocs-pr issue #3091-->  

이 디바이스에 다른 앱이나 서비스를 설치하지 마세요. 이 디바이스는 참조 시스템입니다. 

#### <a name="process-to-convert-applications-to-msix-format"></a>애플리케이션을 MSIX 형식으로 변환하는 프로세스
1. Configuration Manager 콘솔의 권한을 상승시키고, **소프트웨어 라이브러리** 작업 영역으로 이동하고, **애플리케이션 관리**를 확장하고, **애플리케이션** 노드를 선택합니다.  

2. Windows Installer(.msi) 배포 유형의 애플리케이션을 선택합니다.  

    > [!Note]  
    > 참조 디바이스에서 애플리케이션의 원본 콘텐츠에 액세스할 수 있어야 합니다.  
    > 
    > 애플리케이션의 이름에 특수 문자를 사용할 수 없습니다. Configuration Manager는 앱 이름을 출력 파일의 이름으로 사용합니다.  
    > 
    > 참조 디바이스에 미리 이 애플리케이션을 설치하지 마세요.  

3. 리본에서 **.MSIX로 변환**을 선택합니다.

마법사가 완료되면 MSIX 패키징 도구가 마법사에서 지정한 위치에 MSIX 파일을 만듭니다. 이 프로세스 중에 Configuration Manager는 참조 디바이스에 애플리케이션을 자동으로 설치합니다.

프로세스가 실패하면 요약 페이지는 자세한 정보가 포함된 로그 파일을 가리킵니다. 사용자 상태 캡처 시 오류가 발생하면 Windows에서 로그아웃합니다. 다시 로그인하면 이 문제가 해결될 수 있습니다.

이 MSIX 앱을 사용하려면 먼저 클라이언트가 신뢰할 수 있도록 디지털 서명해야 합니다. 이 프로세스에 대한 자세한 내용은 다음 문서를 참조하세요. 
- [MSIX - MSIX 패키징 도구 - MSIX 패키지 서명](https://blogs.msdn.microsoft.com/sgern/2018/09/06/msix-the-msix-packaging-tool-signing-the-msix-package/)
- [SignTool을 사용하여 앱 패키지에 서명하는 방법](https://docs.microsoft.com/windows/desktop/appxpkg/how-to-sign-a-package-using-signtool)

앱에 서명한 후 Configuration Manager에서 애플리케이션의 새 배포 유형을 만듭니다. 자세한 내용은 [애플리케이션의 배포 유형 만들기](/sccm/apps/deploy-use/create-applications#bkmk_create-dt)를 참조하세요.




## <a name="bkmk_uwp"></a> UWP(유니버설 Windows 플랫폼) 앱 지원  

Windows 10 디바이스에서는 LOB(기간 업무) 앱을 설치하기 위한 테스트용 로드 키가 필요하지 않습니다. 그러나 Windows에서 사이드로딩을 활성화하려면 레지스트리 키 `HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Windows\Appx\AllowAllTrustedApps`의 값이 **1**이어야 합니다.  

이 레지스트리 키를 구성하지 않으면 앱을 처음으로 디바이스에 배포할 때 Configuration Manager에서 이 값을 자동으로 **1**로 설정하게 됩니다. 이 값을 **0**으로 설정한 경우 Configuration Manager가 이 값을 자동으로 변경할 수 없으며 LOB(기간 업무) 앱의 배포가 실패합니다.  

UWP LOB(기간 업무) 앱에 디지털 서명합니다. 앱을 배포하는 각 디바이스에서 신뢰할 수 있는 코드 서명 인증서를 사용합니다. 조직 PKI의 인증서를 사용하거나, Windows에서 이미 신뢰하는 공용 루트 인증서를 제공하는 타사 공급자의 인증서를 구입합니다.  

모바일 앱 패키지에 서명하려면 다음 표를 사용하여 사용할 코드 서명 인증서의 유형을 확인합니다.

| 패키지  | Symantec  | 비 Symantec  |
|---------|---------|---------|
| Windows 10 Mobile 디바이스의 유니버설 **.appx** 패키지 | 예 | 예 |
| **.xap** 패키지 | 예 | 아니요 | 
| Windows 10 Mobile 디바이스에 설치할 Windows Phone 8.1 용으로 빌드된 **.appx** 패키지 | 예 | 아니요 | 



## <a name="bkmk_mdm-msi"></a> Windows Installer 앱을 MDM 등록 Windows 10 디바이스에 배포  

**MDM을 통한 Windows Installer(\*.msi)** 배포 유형을 사용하면 Windows Installer 기반 앱을 만들고 Windows 10을 실행하는 MDM 등록 디바이스에 배포할 수 있습니다.  

이 배포 유형을 사용하는 경우 다음 사항을 고려합니다.    

-   확장명이 MSI인 단일 파일만 업로드합니다.  

-   Configuration Manager는 파일의 제품 코드와 제품 버전을 사용하여 앱을 검색합니다.  

-   Windows는 앱의 기본 다시 시작 동작을 사용합니다. Configuration Manager는 앱 다시 시작 동작을 제어하지 않습니다.  

-   단일 사용자에 대해 사용자별 MSI 패키지가 설치됩니다.  

-   디바이스의 모든 사용자에 대해 머신별 MSI 패키지가 설치됩니다.  

-   Configuration Manager는 앱 업데이트를 지원합니다. 각 버전의 MSI 제품 코드는 동일해야 합니다.  
