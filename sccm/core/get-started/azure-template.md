---
title: Azure에서 랩 만들기
titleSuffix: Configuration Manager
description: Azure 템플릿을 사용하여 Configuration Manager Technical Preview 랩 또는 현재 분기 평가 랩 생성 자동화
ms.date: 07/22/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 9875c443-19bf-43a0-9203-3a741f305096
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: bb64b2f13bd1fe558d90d2c4011f03fb6322b443
ms.sourcegitcommit: 3a0eaf3378632f312b46b2b8a524e286f9c4cd8e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/19/2019
ms.locfileid: "75198577"
---
# <a name="create-a-configuration-manager-lab-in-azure"></a>Azure에서 Configuration Manager 랩 만들기

*적용 대상: System Center Configuration Manager(Technical Preview)*

<!--3556017-->

이 가이드에서는 Microsoft Azure에서 Configuration Manager 랩 환경을 빌드하는 방법을 설명합니다. Azure 리소스를 사용하여 랩의 생성을 단순화하고 자동화하려면 Azure 템플릿을 사용합니다. 두 개의 Azure 템플릿이 제공됩니다. 

- Configuration Manager Technical Preview Azure 템플릿은 최신 버전의 Configuration Manager Technical Preview 분기를 설치합니다.
- Configuration Manager 현재 분기 Azure 템플릿은 최신 버전의 Configuration Manager 현재 분기 평가를 설치합니다. 

자세한 내용은 [Azure의 Configuration Manager](/sccm/core/understand/configuration-manager-on-azure)를 참조하세요.



## <a name="prerequisites"></a>필수 구성 요소

이 프로세스에는 다음 개체를 만들 수 있는 Azure 구독이 필요합니다. 
- 도메인 컨트롤러 및 MP/DP 역할에 대한 두 Standard_B2s 가상 머신
- 기본 사이트 서버 및 SQL 데이터베이스 서버에 대한 하나의 Standard_B2ms 가상 머신
- Standard_LRS 스토리지 계정

> [!Tip]  
> 잠재적인 비용을 확인하려면 [Azure 가격 계산기](https://azure.microsoft.com/pricing/calculator/)를 참조하세요.  



## <a name="process"></a>프로세스

1. [Configuration Manager Technical Preview 템플릿](https://azure.microsoft.com/resources/templates/sccm-technicalpreview/) 또는 [Configuration Manager 현재 분기 템플릿](https://azure.microsoft.com/resources/templates/sccm-currentbranch/)으로 이동합니다.  

2. **Azure에 배포**를 선택하면 Azure Portal이 열립니다.  

3. 다음 정보를 사용하여 Azure 빠른 시작 템플릿을 완료합니다.

    - 기본  

        - **구독**: VM을 만들기 위한 구독의 이름  

        - **리소스 그룹**: 이러한 VM에 사용할 리소스 그룹 선택  

        - **위치**: 이 랩 환경을 호스트하는 Azure 데이터 센터 선택  

    - 설정  

        - **접두사**: 머신의 접두사 이름입니다. 자세한 내용은 [Azure VM 정보](#azure-vm-info)를 참조하세요.  

        - **관리자 사용자 이름**: VM에 대한 관리 권한이 있는 사용자의 이름입니다. 이 사용자를 사용하여 VM에 로그인합니다.  

        - **관리자 암호**: 암호가 Azure 복잡성 요구 사항을 충족해야 합니다. 자세한 내용은 [adminPassword](https://docs.microsoft.com/rest/api/compute/virtualmachines/createorupdate#osprofile)를 참조하세요.  

    > [!Important]  
    > Azure에서 다음 설정이 필요합니다. 기본값을 사용합니다. 이러한 값을 변경하지 마세요.  
    > 
    > - **\_아티팩트 위치**: 이 템플릿에 대한 스크립트의 위치 <!-- https://raw.githubusercontent.com/Azure/azure-quickstart-templates/master/sccm-technicalpreview/ -->  
    >
    > - **\_아티팩트 위치 Sas 토큰**: sasToken은 아티팩트 위치에 액세스해야 함  
    > 
    > - **위치**: 모든 리소스의 위치

4. 사용 약관을 참조하세요. 동의하면 **위에 명시된 사용 약관에 동의함**을 선택합니다. 그런 다음, **구매**를 선택하여 계속합니다. 

Azure에서는 설정의 유효성을 검사한 다음, 배포를 시작합니다. Azure Portal에서 배포 상태를 확인합니다. 

> [!NOTE]
> 이 프로세스는 2-4시간이 걸릴 수 있습니다. Azure Portal에서 성공적인 배포를 보여 주는 경우에도 구성 스크립트는 계속 실행됩니다. 프로세스 중 VM을 다시 시작하지 마십시오.

구성 스크립트의 상태를 보려면 `<prefix>PS1` 서버에 연결하고 `%windir%\TEMP\ProvisionScript\PS1.json` 파일 보기를 확인합니다. 모든 단계가 완료로 표시되면 프로세스가 수행됩니다.

VM에 연결하려면 먼저 Azure Portal에서 각 VM에 대한 공용 IP 주소를 가져옵니다. VM에 연결할 때 도메인 이름은 `contoso.com`입니다. 배포 템플릿에서 지정한 자격 증명을 사용합니다. 자세한 내용은 [Windows를 실행하는 Azure 가상 머신에 연결 및 로그온하는 방법](https://docs.microsoft.com/azure/virtual-machines/windows/connect-logon)을 참조하세요.



## <a name="azure-vm-info"></a>Azure VM 정보

3개의 VM은 모두 다음 사양을 충족합니다.
- 150GB의 디스크 공간
- 퍼블릭 및 프라이빗 IP 주소 모두입니다. 공용 IP는 TCP 포트 3389에서 원격 데스크톱 연결만 허용하는 네트워크 보안 그룹에 있습니다. 

배포 템플릿에서 지정한 접두사는 VM 이름 접두사입니다. 예를 들어 "contoso"를 접두사로 설정한 경우 도메인 컨트롤러 머신 이름은 `contosoDC`입니다.


### `<prefix>DC01`

- Active Directory 도메인 컨트롤러
- 두 개의 CPU와 4GB의 메모리가 있는 Standard_B2s
- Windows Server 2019 Datacenter Edition

#### <a name="windows-features-and-roles"></a>Windows 기능 및 역할
- ADDS(Active Directory Domain Services)
- .NET
- RDC(원격 차등 압축)


### `<prefix>PS01`

- 두 개의 CPU와 8GB의 메모리가 있는 Standard_B2ms
- Windows Server 2016 Datacenter Edition
- SQL Server
- Windows PE가 포함된 Windows 10 ADK 
- Configuration Manager 기본 사이트

#### <a name="windows-features-and-roles"></a>Windows 기능 및 역할
- .NET
- RDC(원격 차등 압축) 
- IIS(인터넷 정보 서비스)


### `<prefix>DPMP01`

- 두 개의 CPU와 4GB의 메모리가 있는 Standard_B2s
- Windows Server 2019 Datacenter Edition
- 배포 지점
- 관리 지점

#### <a name="windows-features-and-roles"></a>Windows 기능 및 역할
- .NET
- RDC(원격 차등 압축) 
- IIS(인터넷 정보 서비스)
- BITS(Background Intelligent Transfer Service)

### `<prefix>CL01`

- Configuration Manager 현재 분기 평가 템플릿 전용
- Windows 10
- Configuration Manager 클라이언트
