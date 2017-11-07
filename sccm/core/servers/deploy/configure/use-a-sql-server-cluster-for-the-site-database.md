---
title: "SQL Server 클러스터"
titleSuffix: Configuration Manager
description: "SQL Server 클러스터를 사용하여 System Center Configuration Manager 사이트 데이터베이스를 호스트할 수 있습니다. 지원되는 옵션에 대한 정보를 포함합니다."
ms.custom: na
ms.date: 2/28/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: d09a82c6-bbd1-49ca-8ffe-e3ce87b85d33
caps.latest.revision: "10"
caps.handback.revision: "0"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 5ffc99b0b5c2ab21e65368ae42d3edbb48411476
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/12/2017
---
# <a name="use-a-sql-server-cluster-for-the-system-center-configuration-manager-site-database"></a>System Center Configuration Manager 사이트 데이터베이스에 SQL Server 클러스터 사용

*적용 대상: System Center Configuration Manager(현재 분기)*


 SQL Server 클러스터를 사용하여 System Center Configuration Manager 사이트 데이터베이스를 호스트할 수 있습니다. 서버 클러스터에서 지원되는 사이트 시스템 역할은 사이트 데이터베이스뿐입니다.  

> [!IMPORTANT]  
>  SQL Server 클러스터를 올바르게 설정하려면 SQL Server 설명서 라이브러리에서 제공되는 설명서와 절차를 참조합니다.  

 클러스터는 장애 조치(Failover) 지원을 제공하고 사이트 데이터베이스의 안정성을 개선할 수 있습니다. 그러나 추가적인 처리 또는 부하 분산 이점은 제공하지 않습니다. 실제로 사이트 서버가 사이트 데이터베이스에 연결하기 전에 SQL Server 클러스터의 활성 노드를 찾아야 하므로 성능이 저하될 수도 있습니다.  

 Configuration Manager를 설치하기 전에 Configuration Manager를 지원하도록 SQL Server 클러스터를 준비해야 합니다. 이 섹션의 뒷부분에 있는 필수 조건을 참조하세요.  

 Configuration Manager 설치 중에 Windows 볼륨 섀도 복사본 서비스 작성기가 Microsoft Windows Server 클러스터의 각 물리적 컴퓨터 노드에 설치됩니다. 이 경우 **백업 사이트 서버** 유지 관리 작업이 지원됩니다.  

 사이트가 설치된 후 Configuration Manager는 1시간마다 클러스터 노드 변경 내용을 확인하고, 확인된 변경 내용 중 Configuration Manager 구성 요소 설치에 영향을 주는 변경 내용(예: 노드 장애 조치(Failover) 또는 SQL Server 클러스터에 새 노드 추가)을 자동으로 관리합니다.  

## <a name="supported-options-for-using-a-sql-server-failover-cluster"></a>SQL Server 장애 조치(Failover) 클러스터 사용을 위해 지원되는 옵션은 다음과 같습니다.

다음 옵션은 사이트 데이터베이스로 사용되는 SQL Server 장애 조치(Failover) 클러스터에 대해 지원됩니다.

-   단일 인스턴스 클러스터  

-   여러 인스턴스 구성  

-   여러 활성 노드  

-   명명된 인스턴스 또는 기본 인스턴스 둘 다  

다음 필수 조건에 유의하세요.  

-   사이트 서버의 원격 사이트 데이터베이스를 사용해야 합니다. 클러스터는 사이트 시스템 서버를 포함할 수 없습니다.  

-   클러스터에 포함된 각 서버의 로컬 관리자 그룹에 사이트 서버의 컴퓨터 계정을 추가해야 합니다.  

-   Kerberos 인증을 지원하려면 각 SQL Server 클러스터 노드의 네트워크 연결에 대해 **TCP/IP** 네트워크 통신 프로토콜을 사용하도록 설정해야 합니다. **명명된 파이프** 는 반드시 사용해야 하는 것은 아니지만 Kerberos 인증 문제를 해결하는 데 사용할 수 있습니다. **SQL Server 구성 관리자** 의 **SQL Server 네트워크 구성** 아래에서 네트워크 프로토콜 설정을 구성합니다.  

-   PKI를 사용하는 경우 사이트 데이터베이스에 대해 SQL Server 클러스터를 사용할 때의 특정 인증서 요구 사항은 Configuration Manager에 대한 PKI 인증서 요구 사항을 참조하세요.  

다음 제한 사항을 고려하세요.  

-   **설치 및 구성:**  

    -   보조 사이트는 SQL Server 클러스터를 사용할 수 없습니다.  

    -   SQL Server 클러스터를 지정할 때는 사이트 데이터베이스에 대해 기본 파일 위치가 아닌 위치를 지정하는 옵션을 사용할 수 없습니다.  

-   **SMS 공급자:**  

    -   SQL Server 클러스터 또는 클러스터된 SQL Server 노드로 실행되는 컴퓨터에 SMS 공급자 인스턴스를 설치할 수는 없습니다.  

-   **데이터 복제 옵션:**  

    -   **분산 보기**를 사용하려는 경우에는 SQL Server 클러스터를 사용하여 사이트 데이터베이스를 호스트할 수 없습니다.  

-   **백업 및 복구:**  

    -   Configuration Manager는 명명된 인스턴스를 사용하는 SQL Server 클러스터에 대한 DPM(Data Protection Manager) 백업은 지원하지 않지만 SQL Server의 기본 인스턴스를 사용하는 SQL Server 클러스터에 대한 DPM 백업을 지원합니다.  

## <a name="prepare-a-clustered-sql-server-instance-for-the-site-database"></a>사이트 데이터베이스용으로 클러스터된 SQL Server 인스턴스 준비  

사이트 데이터베이스를 준비하기 위해 완료할 주요 작업은 다음과 같습니다.

-   기존 Windows Server 클러스터 환경에서 사이트 데이터베이스를 호스트할 가상 SQL Server 클러스터를 만듭니다. SQL Server 클러스터를 설치하고 설정하기 위한 구체적인 단계는 해당 SQL Server 버전 관련 설명서를 참조하세요. 예를 들어 SQL Server 2008 R2를 사용하는 경우 [SQL Server 2008 R2 장애 조치 클러스터 설치](http://go.microsoft.com/fwlink/p/?LinkId=240231)를 참조하십시오.  

-   SQL Server 클러스터의 각 컴퓨터에서 Configuration Manager로 사이트 구성 요소를 설치하지 않을 각 드라이브의 루트 폴더에 파일을 저장할 수 있습니다. 파일 이름을 **NO_SMS_ON_DRIVE.SMS**로 지정해야 합니다. 기본적으로 Configuration Manager에서는 백업과 같은 작업을 지원하기 위해 각 실제 노드에 일부 구성 요소를 설치합니다.  

-   각 Windows Server 클러스터 노드 컴퓨터의 **로컬 관리자** 그룹에 사이트 서버의 컴퓨터 계정을 추가합니다.  

-   가상 SQL Server 인스턴스에서 Configuration Manager 설치 프로그램을 실행하는 사용자 계정에 **sysadmin** SQL Server 역할을 할당합니다.  

### <a name="to-install-a-new-site-using-a-clustered-sql-server"></a>클러스터된 SQL Server를 사용하여 새 사이트를 설치하려면  
 클러스터된 사이트 데이터베이스를 사용하는 사이트를 설치하려면 사이트 설치를 위한 일반 프로세스 후에 정보를 다음과 같이 변경하여 Configuration Manager 설치 프로그램을 실행합니다.  

-   **데이터베이스 정보** 페이지에서 사이트 데이터베이스를 호스트할 가상 SQL Server 클러스터 인스턴스의 이름을 지정합니다. 가상 인스턴스는 SQL Server를 실행하는 컴퓨터의 이름을 바꿉니다.  

    > [!IMPORTANT]  
    >  가상 SQL Server 클러스터 인스턴스의 이름을 입력할 때 Windows Server 클러스터에서 만들어진 가상 Windows Server 이름을 입력해서는 안 됩니다. 가상 Windows Server 이름을 사용하는 경우에는 활성 Windows Server 클러스터 노드의 로컬 하드 드라이브에 사이트 데이터베이스가 설치됩니다. 따라서 해당 노드에서 오류가 발생하는 경우 정상적인 장애 조치(Failover)가 수행되지 않습니다.  
