---
title: '온-프레미스 MDM에 대한 역할 설치 '
titleSuffix: Configuration Manager
description: System Center Configuration Manager에서 온-프레미스 모바일 디바이스 관리를 위한 사이트 시스템 역할을 설치합니다.
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: c3cf9f64-c2b9-4ace-9527-2aba6d4eef04
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 0a24edacba97dcce91057e2403585a0843a4b212
ms.sourcegitcommit: 48098f9fb2f447672bf36d50c9f58a3d26acb9ed
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53424428"
---
# <a name="install-site-system-roles-for-on-premises-mobile-device-management-in-system-center-configuration-manager"></a>System Center Configuration Manager의 온-프레미스 모바일 디바이스 관리를 위한 사이트 시스템 역할 설치

*적용 대상: System Center Configuration Manager (현재 분기)*

System Center Configuration Manager 온\-프레미스 모바일 디바이스 관리를 사용하려면 Configuration Manager 사이트 인프라에 다음과 같은 사이트 시스템 역할이 있어야 합니다.  

- 등록 지점  

- 등록 프록시 지점  

- 배포 지점  

- 디바이스 관리 지점  

- 서비스 연결 지점  

  대부분의 PC 및 디바이스가 Configuration Manager 클라이언트 소프트웨어를 사용하여 관리되는 조직에 온\-프레미스 모바일 디바이스 관리를 추가하는 경우 대부분의 사이트 시스템 역할이 기존 인프라의 일부로 이미 설치되어 있을 수 있습니다. 설치되어 있지 않은 경우 사이트 시스템 역할을 사이트에 추가하는 방법에 대한 자세한 내용은 [System Center Configuration Manager에 대한 사이트 시스템 역할 추가](../../core/servers/deploy/configure/add-site-system-roles.md)를 참조하세요.  

> [!NOTE]  
>  디바이스 관리 지점 사이트 시스템 역할에서 데이터베이스 복제본을 사용하는 경우 데이터베이스 복제본이 동기화될 때까지 새로 등록된 디바이스는 처음에 디바이스 관리 지점에 연결하지 못합니다. 이러한 연결 오류는 데이터베이스 복제본에 성공적인 연결에 필요한 새로 등록된 디바이스에 대한 정보가 없기 때문에 발생합니다. 복제본은 5분마다 동기화되므로 등록 후에 처음 5분 동안은 디바이스가 연결되지 않으며(일반적으로 2번 연결 시도 실패) 그 이후에 성공적으로 연결됩니다.  

 기존 사이트 시스템 역할을 사용하거나 새 역할을 추가하는 경우 최신 디바이스를 관리하는 데 사용되도록 구성해야 합니다. 온\-프레미스 모바일 디바이스 관리에 대해 올바르게 작동하도록 배포 지점 및 디바이스 관리 지점을 구성하려면 다음 단계를 따르세요.  

> [!NOTE]  
>  Configuration Manager의 현재 분기는 디바이스에서 온\-프레미스 모바일 디바이스 관리에 대한 배포 지점 및 디바이스 관리 지점으로의 인트라넷 연결만 지원합니다. 그러나 Mac OS X 컴퓨터도 관리하는 경우 해당 클라이언트에 이러한 사이트 시스템 역할에 대한 인터넷 연결이 필요합니다. 이 경우 배포 지점 및 디바이스 관리 지점의 속성을 구성할 때 **인트라넷 및 인터넷 연결 허용** 설정을 대신 사용해야 합니다.  

### <a name="to-configure-site-system-roles-to-manage-modern-devices"></a>최신 디바이스를 관리하도록 사이트 시스템 역할을 구성하려면  

1. Configuration Manager 콘솔에서 **관리** > **개요** > **사이트 구성** > **서버 및 사이트 시스템 역할**을 클릭합니다.  

2. 구성하려는 배포 지점 또는 디바이스 관리 지점이 있는 사이트 서버를 선택하고 **사이트 시스템**의 속성을 연 다음 FQDN이 지정되어 있는지 확인합니다. **확인**을 클릭합니다.  

3. 배포 지점 사이트 시스템 역할에 대한 속성을 엽니다. 일반 탭에서 **HTTPS**가 선택되어 있는지 확인하고 **인트라넷 전용 연결 허용**을 선택합니다.  

    또한 Configuration Manager 클라이언트를 사용하여 Mac 컴퓨터를 별도로 관리하는 경우 **인트라넷 및 인터넷 연결 허용**을 대신 사용합니다.  

   > [!NOTE]  
   >  인트라넷 연결에 대해 구성된 배포 지점에는 사이트 경계도 구성되어야 합니다. Configuration Manager의 현재 분기는 온\-프레미스 모바일 디바이스 관리에 대해 IPv4 범위 경계만 지원합니다. 사이트 경계를 구성하는 방법에 대한 자세한 내용은 [System Center Configuration Manager에 대한 사이트 경계 및 경계 그룹 정의](../../core/servers/deploy/configure/define-site-boundaries-and-boundary-groups.md)를 참조하세요.  

4. **모바일 디바이스가 이 배포 지점에 연결하도록 허용** 옆의 확인란을 클릭한 다음 **확인**을 클릭합니다.  

5. 관리 지점 사이트 시스템 역할에 대한 속성을 엽니다. 일반 탭에서 **HTTPS**가 선택되어 있는지 확인하고 **인트라넷 전용 연결 허용**을 선택합니다.  

    또한 Configuration Manager 클라이언트를 사용하여 Mac 컴퓨터를 별도로 관리하는 경우 **인트라넷 및 인터넷 연결 허용**을 대신 사용합니다.  

6. **모바일 디바이스 및 Mac 컴퓨터가 이 관리 지점을 사용할 수 있도록 허용** 옆의 확인란을 클릭합니다. **확인**을 클릭합니다.  

    이렇게 하면 관리 지점이 디바이스 관리 지점이 됩니다.  

   사이트 시스템 역할이 추가되고 최신 디바이스를 관리하도록 구성되면 해당 역할을 호스트하는 서버를 관리되는 디바이스에 등록하고 통신하기 위한 신뢰할 수 있는 엔드포인트로 구성해야 합니다. 자세한 내용은 [System Center Configuration Manager에서 온-프레미스 모바일 디바이스 관리를 위해 신뢰할 수 있는 통신에 대한 인증서 설정](../../mdm/get-started/set-up-certificates-on-premises-mdm.md)을 참조하세요.  
