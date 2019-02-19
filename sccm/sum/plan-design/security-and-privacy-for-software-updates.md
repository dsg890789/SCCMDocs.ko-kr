---
title: 소프트웨어 업데이트에 대한 보안 및 개인 정보
titleSuffix: Configuration Manager
description: 소프트웨어 업데이트에 대한 이러한 보안 모범 사례를 따르고 Configuration Manager에서 개인 정보를 처리하는 방식을 알아봅니다.
author: aczechowski
manager: dougeby
ms.date: 10/06/2016
ms.topic: conceptual
ms.prod: configuration-manager
ms.technology: configmgr-sum
ms.assetid: 41d6d5d8-ba84-4efb-b105-4d1eed239824
ms.author: aaroncz
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2dee37b0cc55c35b6bd5286acbd18e39c2f5c40c
ms.sourcegitcommit: 874d78f08714a509f61c52b154387268f5b73242
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56125224"
---
# <a name="security-and-privacy-for-software-updates-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 소프트웨어 업데이트에 대한 보안 및 개인 정보

*적용 대상: System Center Configuration Manager(현재 분기)*

이 항목에는 System Center Configuration Manager에서 소프트웨어 업데이트에 대한 보안 및 개인 정보가 포함되어 있습니다.  

##  <a name="BKMK_Security_HardwareInventory"></a> 소프트웨어 업데이트에 대한 보안 모범 사례  
 클라이언트에 소프트웨어 업데이트를 배포할 경우 다음 보안 모범 사례를 따르십시오.  

-   소프트웨어 업데이트 패키지에 대한 기본 권한은 변경하지 마십시오.  

     기본적으로 소프트웨어 업데이트 패키지는 관리자에게 **모든 권한** 과 사용자에게 **읽기** 액세스 권한을 허용하도록 설정되어 있습니다. 이 권한을 변경하면 공격자가 소프트웨어 업데이트를 추가, 제거 또는 삭제할 수도 있습니다.  

-   소프트웨어 업데이트의 다운로드 위치에 대한 액세스를 제어합니다.  

     SMS 공급자 및 사이트 서버용 컴퓨터 계정과 소프트웨어 업데이트를 다운로드 위치에 실제로 다운로드하는 관리자는 다운로드 위치에 대해 **쓰기** 액세스 권한을 보유해야 합니다. 공격자가 다운로드 위치 내 소프트웨어 업데이트 원본 파일을 무단 변경할 위험을 최소화하기 위해 다운로드 위치에 대한 액세스를 제한해야 합니다.  

     또한 다운로드 위치에 UNC 공유를 사용하는 경우 소프트웨어 업데이트 원본 파일이 네트워크를 통해 전송될 때 무단 변경될 위험을 방지하기 위해 IPsec 또는 SMB 서명을 사용하여 네트워크 채널을 보호합니다.  

-   배포 시간을 평가하는 데 UTC를 사용합니다.  

     UTC 대신 현지 시간을 사용하는 경우 사용자가 자신의 컴퓨터에서 표준 시간대를 변경하여 소프트웨어 업데이트의 설치를 지연시킬 수도 있습니다.  

-   WSUS(Windows Server Update Services)에서 SSL을 사용하도록 설정하고 WSUS를 보호하기 위한 모범 사례를 준수합니다.  

     Configuration Manager에서 사용하는 WSUS 버전에 대한 보안 모범 사례를 확인 및 준수합니다.  

    > [!IMPORTANT]  
    >  소프트웨어 업데이트 지점에서 WSUS 서버에 대해 SSL 통신을 사용하도록 설정할 경우 WSUS 서버에 SSL에 대한 가상 루트를 구성해야 합니다.  

-   CRL 확인을 사용하도록 설정합니다.  

     기본적으로 Configuration Manager에서는 소프트웨어 업데이트가 컴퓨터에 배포되기 전에 서명을 검사하기 위해 CRL(인증서 해지 목록)을 확인하지 않습니다. 인증서가 사용될 때마다 CRL을 확인하면 해지된 인증서를 사용할 경우보다는 보안성이 향상되지만, 연결 지연이 발생할 수 있고 CRL 확인을 수행하는 컴퓨터에서 처리 부하가 증가합니다.  

     소프트웨어 업데이트에 대해 CRL 확인을 사용하는 방법에 대한 자세한 내용은 [System Center Configuration Manager에서 소프트웨어 업데이트에 CRL 확인을 사용하는 방법](../get-started/manage-settings-for-software-updates.md#crl-checking-for-software-updates)을 참조하세요.  

-   사용자 지정 웹 사이트를 사용하도록 WSUS를 구성합니다.  

     소프트웨어 업데이트 지점에 WSUS를 설치할 경우 기존 IIS 기본 웹 사이트를 사용하거나 사용자 지정 WSUS 웹 사이트를 만들 수 있습니다. IIS가 다른 Configuration Manager 사이트 시스템 또는 다른 애플리케이션에서 사용하는 웹 사이트를 공유하지 않고 전용 가상 웹 사이트에 있는 WSUS 서비스를 호스트하도록 하려면 WSUS에 사용자 지정 웹 사이트를 만듭니다.  

     자세한 내용은 [사용자 지정 웹 사이트를 사용하도록 WSUS 구성](plan-for-software-updates.md#BKMK_CustomWebSite)을 참조하세요.  

##  <a name="BKMK_Privacy_HardwareInventory"></a> 소프트웨어 업데이트에 대한 개인 정보  
 소프트웨어 업데이트 작업에서는 클라이언트 컴퓨터를 검색하여 필요한 소프트웨어 업데이트를 확인한 다음 이 정보를 다시 사이트 데이터베이스에 보냅니다. 소프트웨어 업데이트 프로세스 중 Configuration Manager는 컴퓨터 및 로그온 계정을 식별하는 정보를 클라이언트와 서버 간에 전송합니다.  

 Configuration Manager에는 소프트웨어 배포 프로세스에 대한 상태 정보가 유지됩니다. 상태 정보는 전송 또는 스토리지 중에 암호화되지 않습니다. 또한 상태 정보는 Configuration Manager 데이터베이스에 저장되며 데이터베이스 유지 관리 작업에 의해 삭제됩니다. Microsoft로 전송되는 상태 정보는 없습니다.  

 클라이언트 컴퓨터에 소프트웨어 업데이트를 설치할 때 Configuration Manager 소프트웨어 업데이트는 해당 업데이트에 대한 소프트웨어 사용 조건에 따라 사용해야 합니다. 이 소프트웨어 사용 조건은 System Center Configuration Manager에 대한 소프트웨어 사용 조건과 별개입니다. Configuration Manager를 사용하여 소프트웨어 업데이트를 설치하기 전에는 항상 소프트웨어 사용 조건을 살펴보고 이에 동의해야 합니다.  

 Configuration Manager는 소프트웨어 업데이트를 기본적으로 구현하지 않으며 몇 개의 구성 단계를 거쳐야 정보를 수집할 수 있습니다.  

 소프트웨어 업데이트를 구성하려면 먼저 개인 정보 취급 방침 요구 사항을 검토하십시오.  
