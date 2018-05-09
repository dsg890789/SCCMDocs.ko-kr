---
title: '장치 등록 설정 '
titleSuffix: Configuration Manager
description: System Center Configuration Manager의 온-프레미스 모바일 장치 관리를 위해 장치를 등록할 수 있는 권한을 사용자에게 부여합니다.
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: 9ffaea91-1379-4b86-9953-b25e152f56a9
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 7d0424b662df4baba7374685dd7631347501352c
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="set-up-device-enrollment-for-on-premises-mobile-device-management-in-system-center-configuration-manager"></a>System Center Configuration Manager의 온-프레미스 모바일 장치 관리를 위한 장치 등록 설정

*적용 대상: System Center Configuration Manager(현재 분기)*

사용자가 System Center Configuration Manager 온\-프레미스 모바일 장치 관리에 장치를 등록할 수 있게 하려면 사용자에게 해당 권한을 부여해야 합니다. 사용자에게 장치를 등록하기 위한 권한을 부여하려면 아래 작업을 수행합니다.

-   [사용자가 최신 장치를 등록할 수 있도록 하는 등록 프로필 만들기](#bkmk_createProf)  

-   [등록된 장치에 대한 추가 클라이언트 설정 지정](#bkmk_addClient)  

-   [사용자가 최신 장치 등록 프로필을 받을 수 있도록 설정](#bkmk_enableUsers)  

-   [등록할 장치에 루트 인증서 저장](#bkmk_storeCert)  

##  <a name="bkmk_createProf"></a> 사용자가 최신 장치를 등록할 수 있도록 하는 등록 프로필 만들기  
 사용자가 최신 장치를 등록할 수 있도록 허용하기 위한 설정을 푸시하려면 Configuration Manager 사이트에서 검색된 모든 사용자에게 적용되는 기본 클라이언트 설정에 새 등록 프로필을 추가할 수 있습니다.  

1.  Configuration Manager 콘솔에서 **관리** > **개요** > **클라이언트 설정**을 클릭하고 **기본 클라이언트 설정**을 연 다음 **등록**을 선택합니다.  

2.  장치 설정에서 최신 장치의 폴링 간격을 지정합니다.  

3.  사용자 설정에서 **Allow users to enroll modern devices(최신 장치 등록 허용)** 에 대해 **예**를 선택합니다.  

4.  **최신 장치 등록 프로필** 옆에 있는 **프로필 설정...** 을 클릭한 후 **만들기...** 를 클릭합니다.  

5.  등록 프로필 만들기에서 등록 프로필의 이름을 입력하고 등록 프로필이 있는 사용자가 사용하게 하려는 관리 사이트 코드를 선택합니다. **확인** 을 여러 번 클릭하여 기본 설정 페이지를 종료합니다.  

> [!NOTE]  
>  검색된 사용자의 하위 집합에 등록 프로필을 배포하려는 경우 사용자 컬렉션을 사용한 다음 해당 컬렉션에 배포할 사용자 지정 클라이언트 설정을 만듭니다. 사용자 지정 클라이언트 설정을 만드는 방법에 대한 자세한 내용은 [System Center Configuration Manager에서 클라이언트 설정을 구성하는 방법](../../core/clients/deploy/configure-client-settings.md)을 참조하세요.  

##  <a name="bkmk_addClient"></a> 등록된 장치에 대한 추가 클라이언트 설정 지정  
 최신 장치에 대한 등록 프로필을 설정할 뿐만 아니라, 등록된 장치를 구성하도록 추가 클라이언트 설정을 지정할 수도 있습니다.  클라이언트 설정을 지정하는 방법에 대한 자세한 내용은 [System Center Configuration Manager에서 클라이언트 설정을 구성하는 방법](../../core/clients/deploy/configure-client-settings.md)을 참조하세요.  

 일부 클라이언트 설정은 온\-프레미스 모바일 장치 관리에 사용할 수 없습니다. Configuration Manager의 현재 분기에서는 온\-프레미스 모바일 장치 관리에 대해 다음 클라이언트 설정을 지원합니다.  

-   등록 - 이러한 설정은 관리되는 장치에 대한 등록 프로필을 지정합니다. 등록 프로필을 설정하는 방법에 대한 자세한 내용은 [사용자가 최신 장치를 등록할 수 있도록 하는 등록 프로필 만들기](#bkmk_createProf)섹션을 참조하세요.  

-   클라이언트 정책 - 이러한 설정은 장치에 클라이언트 정책을 다운로드하기 위한 빈도를 지정합니다. 또한 정책 폴링을 통해 대상 사용자를 지정하는 설정을 사용할 수 있습니다. 클라이언트 정책 설정에 대한 자세한 내용은 [System Center Configuration Manager의 클라이언트 설정 정보](../../core/clients/deploy/about-client-settings.md)에서 클라이언트 정책 섹션을 참조하세요.  

-   소프트웨어 배포 - 이 설정은 소프트웨어 배포를 위해 클라이언트 장치를 평가하는 간격을 설정합니다. 소프트웨어 배포 설정에 대한 자세한 내용은 [System Center Configuration Manager의 클라이언트 설정 정보](../../core/clients/deploy/about-client-settings.md)에서 소프트웨어 배포 섹션을 참조하세요.  

    > [!NOTE]  
    >  온\-프레미스 모바일 장치 관리의 경우 소프트웨어 배포 설정만 기본 클라이언트 설정으로 사용할 수 있습니다. Configuration Manager의 현재 분기에서는 소프트웨어 배포 설정을 사용자 지정 클라이언트 설정과 함께 사용할 수 없습니다.  

##  <a name="bkmk_enableUsers"></a> 사용자가 최신 장치 등록 프로필을 받을 수 있도록 설정  
 사용자가 온\-프레미스 모바일 장치 관리에 대한 등록 프로필이 있는 수정된 클라이언트 설정을 받으려면 Active Directory 검색 방법을 통해 검색되어야 합니다. 등록 프로필이 필요한 모든 사람이 프로필을 받도록 하려면 Active Directory 사용자에 대해 검색을 실행합니다. 사용자를 검색하는 방법에 대한 자세한 내용은 [System Center Configuration Manager에 대한 검색 실행](../../core/servers/deploy/configure/run-discovery.md)을 참조하세요.  

##  <a name="bkmk_storeCert"></a> 등록할 장치에 루트 인증서 저장  
 루트 인증서가 Active Directory와의 도메인 연결 프로세스의 일부로 발급되었으므로 도메인 연결 장치가 있는 사용자에게 사이트 시스템 역할을 호스트하는 서버와의 신뢰할 수 있는 통신에 필요한 루트 인증서가 이미 있을 것입니다. 도메인에 연결되지 않은 컴퓨터 및 모바일 장치의 경우 등록이 수행되려면 루트 인증서가 장치에 수동으로 설치되어 있어야 합니다. 이러한 장치는 필요한 루트 인증서를 자동으로 보유하게 되지 않습니다.  

 수동 설치를 위해서는 내보낸 인증서 파일이 장치에 제공되어야 합니다. 이 작업은 메일, OneDrive, SD 카드, USB 소형 드라이브 또는 사용자의 요구에 가장 적합한 방법을 사용하여 수행할 수 있습니다.  

 장치에서 사용하려는 루트 인증서는 [웹 서버 인증서와 동일한 루트를 가진 인증서 내보내기](../../mdm/get-started/set-up-certificates-on-premises-mdm.md#bkmk_exportCert)에서 내보낸 인증서입니다.  

1.  장치에 등록하려면 루트 인증서 파일을 찾아 두 번 클릭합니다.  

2.  인증서 창에서 **인증서 설치...** 를 클릭합니다.  

3.  인증서 가져오기 마법사에서 **로컬 컴퓨터**를 선택하고 **다음**을 클릭합니다.  

4.  사용자 계정 컨트롤 창에서 **예**를 클릭합니다.  

5.  **모든 인증서를 다음 저장소에 저장**을 선택하고 **찾아보기**를 클릭합니다.  

6.  **신뢰할 수 있는 루트 인증 기관**을 클릭하고 **확인**을 클릭한 후 **다음**을 클릭합니다.  

7.  **마침**을 클릭합니다.  
