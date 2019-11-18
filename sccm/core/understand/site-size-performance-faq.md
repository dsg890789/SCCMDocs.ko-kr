---
title: 사이트 크기 조정 및 성능 FAQ
titleSuffix: Configuration Manager
description: System Center Configuration Manager의 사이트 크기 조정 및 성능에 관한 일반적인 질문에 대한 대답
author: aczechowski
ms.author: aaroncz
ms.prod: configuration-manager
ms.topic: conceptual
ms.date: 04/19/2019
ms.openlocfilehash: 93ddf18f78667058b137368a4948ac3d4dc38288
ms.sourcegitcommit: 9e80902f586342e5eea48febb6da7594f2cc9c34
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/11/2019
ms.locfileid: "73912980"
---
# <a name="system-center-configuration-manager-site-sizing-and-performance-faq"></a>System Center Configuration Manager 사이트 크기 조정 및 성능 FAQ

*적용 대상: System Center Configuration Manager(현재 분기)*

이 문서에서는 Configuration Manager 사이트 크기 조정 지침 및 일반적인 성능 문제에 관한 질문과 대답을 다룹니다.

## <a name="machine-and-disk-configuration-faqs-and-examples"></a>컴퓨터 및 디스크 구성 FAQ 및 예제

### <a name="how-should-i-format-the-disks-on-my-site-server-and-sql-server"></a>내 사이트 서버 및 SQL Server에서 디스크를 포맷하려면 어떻게 해야 하나요?

두 개 이상의 서로 다른 볼륨에서 Configuration Manager 받은 편지함 및 SQL 파일을 구분합니다. 이 구분을 통해 해당 볼륨에서 수행하는 다양한 종류의 I/O에 대한 클러스터 할당 크기를 최적화할 수 있습니다. 

사이트 서버 받은 편지함을 호스팅하는 볼륨에 대해서는 4K 또는 8K 할당 단위의 NTFS를 사용합니다. ReFS는 작은 파일에 대해서도 64k를 씁니다. Configuration Manager는 다수의 작은 파일을 포함하므로 ReFS는 불필요한 디스크 오버헤드를 발생시킬 수 있습니다.

SQL 데이터베이스 파일이 포함된 디스크에 대해서는 64K 할당 단위의 NTFS 또는 ReFS 포맷을 사용합니다.

### <a name="how-and-where-should-i-lay-out-my-sql-database-files"></a>내 SQL 데이터베이스 파일을 어떻게 그리고 어디에 레이아웃해야 하나요?

SSD(반도체 드라이브) 및 Azure Premium Storage의 최신 배열은 소수의 디스크를 사용하여 단일 볼륨에서 높은 IOPS를 제공할 수 있습니다. 일반적으로 추가 처리량이 아닌 추가 스토리지를 위해 배열에 더 많은 드라이브를 추가합니다. 실제 스핀들 기반 디스크를 사용하는 경우 단일 볼륨에 생성할 수 있는 것보다 더 많은 IOPS가 필요할 수도 있습니다. 총 권장 IOPS와 *.mdf* 파일의 디스크 공간에 60%, *.ldf* 파일에 20% 및 로그와 데이터 임시 파일에 20%를 할당하는 것이 좋습니다. *.ldf* 및 임시 파일은 모두 할당된IOPS의 40%(20% + 20%)가 있는 단일 볼륨에 상주할 수 있습니다.

SQL Server 2016 이전의 SQL Server는 기본적으로 하나의 1개의 임시 데이터 파일을 만듭니다. SQL 잠금을 방지하고 단일 파일에 액세스할 때까지 기다리려면 더 많은 파일을 만들어야 합니다. 만들어야 할 최선의 임시 데이터 파일 수는 커뮤니티 의견에 따라 4개에서 8개까지 달라집니다. 테스트해 보니 4개에서 8개 간의 차이가 크지 않은 것으로 나타났으므로 *동일한 크기*의 임시 데이터 파일 4개를 만들 수 있습니다. tempdb 데이터 파일은 전체 데이터베이스 크기의 20 ~ 25%가 되어야 합니다.

### <a name="are-there-any-other-recommendations-for-disk-setup"></a>디스크 설정에 대한 다른 권장 사항이 있습니까?

구성 가능한 경우 RAID 컨트롤러 메모리를 쓰기 작업에 70% 및 읽기 작업에 30%로 설정합니다. 일반적으로 사이트 데이터베이스에 대해서는 RAID 10 배열 구성을 사용합니다. I/O 요구 사항이 낮거나 고속 SSD를 사용하는 경우 RAID 1도 허용됩니다. 더 큰 디스크 배열의 경우 고장 디스크를 자동으로 교체하도록 예비 디스크를 구성합니다.

**예: 실제 디스크가 있는 물리적 컴퓨터** 

클라이언트 수가 **100,000**인 공동 배치된 사이트 서버와 SQL Server에 대한 [크기 조정 지침](../plan-design/configs/site-size-performance-guidelines.md#general-sizing-guidelines)은 사이트 서버 받은 편지함에 1200 IOPS 및 SQL Server 파일에 5000 IOPS입니다.

결과적으로 디스크 구성은 다음과 같을 수 있습니다.

| 드라이브<sup>1</sup> | RAID | 형식 | 볼륨 콘텐츠 | 필요한 최소 IOPS| 제공되는 대략적인 IOPS<sup>2</sup>  |
|----------------|-----------|-------------|----------------------|---------------------|------------------|
| 2x10k          | 1         | -           | Windows              |                     | -                |
| 6x15k          | 10        | NTFS 8k     | ConfigMgr 받은 편지함    |     1700            | 1751             |
| 12x15k         | 10        | 64k ReFS    | SQL .mdf             | 60%*5000 = 3000     | 3476             |
| 8x15k          | 10        | 64k ReFS    | SQL .ldf, 임시 파일 | 40%*5000 = 2000     | 2322             |

1. 권장 예비 디스크는 포함하지 않습니다. 
2. 이 값은 [예제 디스크 구성](../plan-design/configs/site-size-performance-guidelines.md#example-disk-configurations)의 값입니다. 

### <a name="i-use-hyper-v-on-windows-server-how-should-i-configure-the-disks-for-my-configuration-manager-vms-for-best-performance"></a>Windows Server에서 Hyper-V를 사용하고 있는데요. 최고의 성능을 위해 내 Configuration Manager VM에 대한 디스크를 어떻게 구성해야 하나요?

Hyper-V는 하드웨어 리소스(CPU 코어 및 패스 스루 스토리지)가 가상 머신(VM)에 전용으로 100% 사용되는 경우 실제 서버와 유사한 성능을 제공합니다. 고정 크기 *.vhd* 또는 *.vhdx* 디스크 파일을 사용하면 I/O 성능에 최소 1 ~ 5% 영향을 줍니다. 동적으로 확장하는 *.vhd* 또는 *.vhdx* 디스크 파일을 사용하면 Configuration Manager 워크로드에 대한 I/O 성능에 최대 25%의 영향을 줍니다. 동적으로 확장하는 디스크가 필요한 경우 추가 25% IOPS 성능을 배열에 추가하여 보정합니다.

VM 내에서 Configuration Manager 사이트 서버 또는 SQL을 실행하는 경우 Hyper-V 호스트 OS 드라이브를 VM OS 및 데이터 드라이브에서 격리합니다.

VM 최적화에 대한 자세한 내용은 [Hyper-V Server 성능 조정](/windows-server/administration/performance-tuning/role/hyper-v-server/)을 참조하세요.

**예: Hyper-V VM 기반 사이트 서버** 

클라이언트 수가 **150,000**인 공동 배치된 사이트 서버와 SQL Server에 대한 [크기 조정 지침](../plan-design/configs/site-size-performance-guidelines.md#general-sizing-guidelines)은 사이트 서버 받은 편지함에 1800 IOPS 및 SQL Server 파일에 7400 IOPS입니다.

결과적으로 디스크 구성은 다음과 같을 수 있습니다.

| 드라이브<sup>1</sup> | RAID | 형식<sup>2</sup> | 볼륨 콘텐츠 | 필요한 최소 IOPS| 제공되는 대략적인 IOPS<sup>3</sup>  |
|----------------|-----------|----------------|---------------------------|----------------------|------------------|
| 2x10k          | 1         | -              | Hyper-V 호스트 OS           | -                    | -                |
| 2x10k          | 1         | -              | (VM) 사이트 서버 OS       | -                    | -                |
| 2xSSD SAS      | 1         | NTFS 8k        | (VM) ConfigMgr 받은 편지함    | 1800                 | 7539             |
| 4xSSD SAS      | 10        | 64k ReFS       | (VM) 호스트 SQL(모든 파일) | 7400                 | 14346            |

1. 권장 예비 디스크는 포함하지 않습니다. 
2. VM 드라이브용 고정 크기 패스 스루 *.vhdx*를 기본 볼륨에 전용으로 사용합니다. 
3. 이 값은 [예제 디스크 구성](../plan-design/configs/site-size-performance-guidelines.md#example-disk-configurations)의 값입니다. 

### <a name="are-there-any-suggestions-for-configuration-manager-environments-in-microsoft-azure"></a>Microsoft Azure의 Configuration Manager 환경에 대한 어떤 제안이 있나요?

먼저 [Azure의 Configuration Manager 질문과 대답](configuration-manager-on-azure.md)을 읽으세요.

Premium Storage 디스크를 활용하는 Azure IaaS(서비스 제공 인프라) VM은 IOPS가 높을 수 있습니다. 이러한 VM에서는 추가 IOPS보다 예상 디스크 공간 필요에 맞게 추가 디스크를 구성합니다.

Azure Storage는 기본적으로 중복이며 가용성을 위해 여러 개의 디스크가 필요하지 않습니다. 추가 공간 및 성능을 제공하려면 디스크 관리자 또는 스토리지 공간에서 디스크를 스트라이프할 수 있습니다.

Premium Storage 성능을 최대화하고 Azure IaaS VM에서 SQL Server를 실행하는 방법에 대한 자세한 내용 및 권장 사항은 다음을 참조하세요.

- [애플리케이션 성능 최적화](/azure/storage/storage-premium-storage-performance#optimize-application-performance)
 
- [디스크 지침](/azure/virtual-machines/windows/sql/virtual-machines-windows-sql-performance#disks-guidance)

**예: Azure 기반 사이트 서버** 

클라이언트 수가 **50,000**인 공동 배치된 사이트 서버와 SQL Server에 대한 [크기 조정 지침](../plan-design/configs/site-size-performance-guidelines.md#general-sizing-guidelines)은 8개 코어, 32GB, 사이트 서버 받은 편지함에 1200 IOPS 및 SQL Server 파일에 2800 IOPS입니다.

그 결과 Azure 컴퓨터는 다음과 같은 디스크 구성을 가진 DS13v2(8개 코어, 56GB)가 될 수 있습니다.

| 드라이브 | 형식 | 포함 | 필요한 최소 IOPS| 제공되는 대략적인 IOPS<sup>1</sup>  |
|------------------|---------------|--------------------|----------------------|------------------|
| &lt;표준&gt; | -             | 사이트 서버 OS     | -                    | -                |
| 1xP20(512 GB)    | NTFS 8k       | ConfigMgr 받은 편지함  | 1200                 | 2334             |
| 1xP30(1024 GB)   | 64k ReFS      | SQL(모든 파일<sup>2</sup>) | 2800                 | 3112             |

1. 이 값은 [예제 디스크 구성](../plan-design/configs/site-size-performance-guidelines.md#example-disk-configurations)의 값입니다.
2. [Azure 지침](/azure/virtual-machines/windows/sql/virtual-machines-windows-sql-performance#disks-guidance)은 사용 가능한 공간을 초과하지 않고 추가 디스크 I/O 배포를 허용하는 경우 로컬 SSD 기반 *D:* 드라이브에 TempDB 배치를 허용합니다.

**예: Azure 기반 사이트 서버(즉시 성능 향상용)** 

Azure 디스크 처리량은 VM의 크기에 따라 제한됩니다. 앞의 Azure 예제에 나오는 구성은 미래의 확장 또는 추가 성능을 제한할 수 있습니다. Azure VM의 초기 배포 시 추가 디스크를 추가하는 경우 사전 투자를 최소화하면서 미래의 처리 능력을 증가시키기 위해 Azure VM 크기를 증가시킬 수 있습니다. 나중에 더 복잡한 마이그레이션을 수행해야 하는 것보다는 요구 사항이 변경됨에 따라 사이트 성능을 증가시키도록 사전에 계획하는 것이 훨씬 더 간단합니다.

앞의 Azure 예제에서 디스크를 변경하여 IOPS가 어떻게 변경되는지 확인해 보세요.

**DS13v2** 

| 드라이브<sup>1</sup> | 형식 | 포함 | 필요한 최소 IOPS| 제공되는 대략적인 IOPS<sup>2</sup>  |
|------------------|---------------|--------------------|----------------------|------------------|
| &lt;표준&gt; | -             | 사이트 서버 OS     | -                    | -                |
| 2xP20(1024 GB)   | NTFS 8k       | ConfigMgr 받은 편지함  | 1200                 | 3984             |
| 2xP30(2048 GB)   | 64k ReFS      | SQL(모든 파일<sup>3</sup>) | 2800                 | 3984             |

1. 스토리지 공간을 사용하여 디스크를 스트라이프합니다.
2. 이 값은 [예제 디스크 구성](../plan-design/configs/site-size-performance-guidelines.md#example-disk-configurations)의 값입니다. VM 크기는 성능을 제한합니다.
3. [Azure 지침](/azure/virtual-machines/windows/sql/virtual-machines-windows-sql-performance#disks-guidance)은 사용 가능한 공간을 초과하지 않고 추가 디스크 I/O 배포를 허용하는 경우 로컬 SSD 기반 *D:* 드라이브에 TempDB 배치를 허용합니다.

나중에 더 높은 성능이 필요하면 VM 크기를 CPU 및 메모리가 2배인 DS14v2로 증가시킬 수 있습니다. 해당 VM 크기에 허용되는 추가 디스크 대역폭 덕분에 이전에 구성된 디스크에서 사용 가능한 디스크 IOPS도 즉시 향상됩니다.

**DS14v2**

| 드라이브<sup>1</sup> | RAID | 형식 | 포함 | 필요한 최소 IOPS| 제공되는 대략적인 IOPS<sup>2</sup>  |
|------------------|---------------|--------------------|----------------------|------------------|
| &lt;표준&gt; | -             | 사이트 서버 OS     | -                    | -                |
| 2xP20(1024 GB)   | NTFS 8k       | ConfigMgr 받은 편지함  | 1200                 | 4639             |
| 2xP30(2048 GB)   | 64k ReFS      | SQL(모든 파일<sup>3</sup>) | 2800                 | 6182             |

1. 스토리지 공간을 사용하여 디스크를 스트라이프합니다.
2. 이 값은 [예제 디스크 구성](../plan-design/configs/site-size-performance-guidelines.md#example-disk-configurations)의 값입니다. VM 크기는 성능을 제한합니다.
3. [Azure 지침](/azure/virtual-machines/windows/sql/virtual-machines-windows-sql-performance#disks-guidance)은 사용 가능한 공간을 초과하지 않고 추가 디스크 I/O 배포를 허용하는 경우 로컬 SSD 기반 *D:* 드라이브에 TempDB 배치를 허용합니다.

## <a name="other-common-sql-server-related-performance-questions"></a>SQL Server 관련 성능에 관한 다른 일반적인 질문 

### <a name="is-it-better-to-run-with-sql-colocated-with-the-site-server-or-run-it-on-a-remote-server"></a>SQL을 사이트 서버와 공동 배치하고 실행하는 것이 더 낫습니까, 아니면 원격 서버에서 실행하는 것이 더 낫습니까?

단일 서버의 크기가 적절하거나 두 서버 간의 네트워크 연결이 충분하다고 가정하면 두 방법 모두 적절하게 수행될 수 있습니다.

원격 SQL을 선택하면 추가 서버의 사전 및 운영 비용이 필요하지만 이는 대부분의 대규모 고객 서비스에서 일반적인 현상입니다. 이 구성의 이점은 다음과 같습니다.

- SQL Always On 등과 같은 사이트 가용성 옵션 증가
- 사이트 처리에 대한 오버헤드를 줄이면서 리소스 사용량이 많은 보고 실행 가능
- 상황에 따라 재해 복구 단순화
- 보안 관리 용이
- SQL 관리에 대한 역할 분리(예: 별도 DBA 팀 편성)

공동 배치된 SQL은 서버가 한 대만 필요하며 이 방법은 대부분의 소규모 고객 서비스에 일반적입니다. 이 구성의 이점은 다음과 같습니다.

- 컴퓨터, 라이선스 및 유지 관리에 대한 비용 절감
- 사이트의 실패 지점 감소
- 가동 중지 시간의 계획에 대한 관리 개선

### <a name="how-much-ram-should-i-allocate-for-sql"></a>SQL에 RAM을 얼마나 할당해야 하나요?

기본적으로 SQL은 서버의 사용 가능한 메모리를 모두 사용하므로 OS 및 컴퓨터의 다른 프로세스에 사용할 메모리가 남지 않을 가능성이 있습니다. 잠재적 성능 문제를 방지하려면 SQL에 메모리를 명시적으로 할당해야 합니다. SQL server와 공동 배치된 사이트 서버의 경우 OS가 파일 캐싱 및 다른 작업을 위한 RAM을 충분히 확보하는지 확인합니다. SMSExec 및 기타 Configuration Manager 프로세스를 위해 남아 있는 RAM이 충분한지 확인합니다. SQL을 원격 서버에서 실행하는 경우 *대부분*의 메모리를 SQL에 할당하지만 메모리를 전부 할당하는 것은 아닙니다. 초기 지침은 [크기 조정 지침](../plan-design/configs/site-size-performance-guidelines.md#general-sizing-guidelines)을 검토하세요. 

SQL Server 메모리 할당은 자연수 GB로 반올림하여 지정해야 합니다. 또한 RAM이 대량으로 증가함에 따라 SQL이 더 높은 비율을 갖도록 할 수 있습니다. 예를 들어 사용 가능한 RAM이 256GB 이상인 경우 SQL에 최대 95%를 할당하도록 구성할 수 있습니다. 이렇게 할당해도 OS용 메모리는 충분히 남습니다. 페이지 파일 모니터링은 OS 및 모든 Configuration Manager 프로세스에 대한 메모리가 충분한지 확인하는 좋은 방법입니다.

### <a name="cores-are-cheap-these-days-should-i-just-add-a-bunch-of-them-to-my-sql-server"></a>코어는 최근 값이 쌉니다. 내 SQL Server에 그 중의 일부를 추가하기만 하면 되나요?

실제 코어가 16개보다 많은데 SQL Server에 RAM이 부족하면 메모리 경합 문제가 발생할 수 있습니다. Configuration Manager 워크로드는 SQL에 코어당 최소 3 ~ 4GB의 RAM을 사용할 수 있을 때 더 잘 수행됩니다. SQL Server에 코어를 추가하는 경우 반드시 RAM을 그에 비례하여 증가시켜야 합니다.

### <a name="will-sql-always-on-impact-my-performance"></a>SQL Always On이 성능에 영향을 주나요?

일반적으로 SQL Always On은 SQL 복제 서버 간에 충분한 네트워킹을 사용할 수 있으면 성능에 거의 영향을 주지 않습니다. SQL Always On 사용량이 많은 환경에서는 데이터베이스 로그 *.ldf* 파일이 빠르게 증가할 수 있습니다. 그러나 로그 파일 공간은 데이터베이스 백업이 성공한 후 자동으로 해제됩니다. Configuration Manager 데이터베이스에 대한 SQL 작업을 추가하여 백업을 수행하세요(예: 매 24시간마다, 그리고 매 6시간마다 *.ldf* 백업). SQL 백업 전략에 대한 추가 정보를 포함하여 SQL Always On 및 Configuration Manager에 대한 자세한 내용은 [가용성이 높은 데이터베이스를 위한 SQL Server Always On](/sccm/core/servers/deploy/configure/sql-server-alwayson-for-a-highly-available-site-database)을 참조하세요.

### <a name="should-i-enable-sql-compression-on-my-database"></a>내 데이터베이스에서 SQL 압축을 사용해야 하나요?

SQL 압축은 Configuration Manager 데이터베이스에 대해 권장되지 않습니다. Configuration Manager 데이터베이스에서 압축을 사용해도 기능상 문제는 없지만 테스트 결과에서는 시스템에 대한 잠재적 크기 조정 가능 성능 영향에 비해 크기 절감 효과가 그리 크지 않은 것으로 나타났습니다.

### <a name="should-i-enable-sql-encryption-on-my-database"></a>내 데이터베이스에서 SQL 암호화를 사용해야 하나요?

Configuration Manager 데이터베이스의 모든 비밀은 이미 안전하게 저장되지만 SQL 암호화를 추가하면 또 다른 보안 계층을 추가할 수 있습니다. 데이터베이스에서 암호화를 사용해도 기능상 문제는 없지만 암호화를 위해 선택하는 테이블 및 사용 중인 SQL의 버전에 따라 성능이 25%까지 저하될 수 있습니다. 따라서 특히 대규모 환경에서는 암호화를 주의 깊게 사용해야 합니다. 또한 암호화된 데이터를 성공적으로 복구할 수 있도록 백업 및 복구 계획을 업데이트해야 합니다.

### <a name="what-version-of-sql-should-i-run"></a>어떤 버전의 SQL를 실행해야 하나요?

지원되는 SQL 버전은 [SQL Server 버전 지원](../plan-design/configs/support-for-sql-server-versions.md)을 참조하세요. 성능 관점에서 모든 지원되는 SQL 버전은 필요한 성능 기준을 충족합니다. 그러나 SQL 2012 및 SQL 2016 또는 더 최신 버전의 성능이 Configuration Manager 워크로드의 일부 측면에서 SQL 2014보다 나은 경향이 있습니다. 또한 SQL 2012 호환성 수준(110)에서 SQL 2014를 실행하면 일반적으로 성능이 향상됩니다. 설치 시 SQL 2014 및 SQL 2012에서 실행되는 Configuration Manager 데이터베이스는 호환성 수준 110으로 설정됩니다. SQL 2016 이상은 해당 SQL 버전의 기본 호환성 수준(예: SQL 2016의 경우 130)으로 설정됩니다. SQL 현재 항목을 업그레이드하더라도 다음 주요 Configuration Manager 현재 분기 버전을 설치할 때까지 호환성 수준이 업데이트되지 않습니다. 

SQL 2016 이상에서 특정 SQL 쿼리에 이상한 시간 초과 또는 속도 저하가 발견되면(예: 관리 콘솔에서 RBAC를 사용하는 경우) Configuration Manager 데이터베이스의 SQL 호환성 수준을 110으로 변경해 보세요. SQL 2014 및 더 최신 버전의 SQL에서 SQL 호환성 수준 110으로 실행하는 방법은 완전하게 지원됩니다. 자세한 내용은 [특정 Configuration Manager 데이터베이스 쿼리에서 SQL 쿼리 시간 초과 또는 콘솔 속도 저하](https://support.microsoft.com/help/3196320/sql-query-times-out-or-console-slow-on-certain-configuration-manager-d)를 참조하세요.

2018년 1월 현재 여러 가지 알려진 성능 관련 또는 기타 잠재적 문제 때문에 다음 SQL 버전을 *사용하지 않는* 것이 좋습니다.

- SQL 2012 SP3 CU1 ~ CU5
- SQL 2014 SP1 CU6 ~ SP2 CU2
- SQL 2016 RTM ~ CU3, SP1 CU3 ~ CU5

### <a name="should-i-implement-any-additional-sql-indexing-tasks"></a>추가 SQL 인덱싱 작업을 구현해야 하나요?

예. SQL 성능을 개선하기 위해 주 1회 정도 인덱스를 업데이트하고 하루에 한 번 정도 통계를 업데이트하세요. Configuration Manager 및 SQL 커뮤니티에서 사용할 수 있는 타사 스크립트 및 추가 정보는 이러한 작업을 최적화하는 데 도움이 될 수 있습니다.

대규모 사이트에서는 사용 패턴에 따라 일부 SQL 테이블(예: CI\_CurrentComplianceStatusDetails, HinvChangeLog)이 클 수 있습니다. 이들을 한 개씩 줄이거나 이들에 대한 유지 관리 방법을 변경해야 할 수 있습니다.

### <a name="when-should-i-use-full-sql-server-instead-of-sql-express-on-my-secondary-sites"></a>내 보조 사이트에서 SQL Express 대신 전체 SQL Server를 사용해야 하는 경우는 언제인가요?

SQL Express는 보조 사이트에 대한 성능상의 함의가 별로 없으며 대부분의 고객에게 적당합니다. 또한 이는 배포와 관리가 쉬우며 모든 규모의 거의 모든 고객에게 권장되는 구성입니다.

전체 SQL Server 설치가 필요할 수 있는 한 가지 상황이 있습니다. 환경에 다수의 배포 지점 및 패키지 또는 소스가 있는 경우 SQL Express의 10GB 크기 제한을 초과할 수 있습니다. 패키지 수에 배포 지점 수를 곱한 수가 4,000,000보다 많은 경우(예: 콘텐츠 2,000개를 포함하는 2,000개의 DP) 보조 사이트에서 전체 SQL Server 사용을 고려하세요. 

### <a name="should-i-change-maxdop-settings-on-my-database"></a>내 데이터베이스에서 MaxDOP 설정을 변경해야 하나요?

대부분의 상황에서 전체 처리 성능을 위해 설정을 0(사용 가능한 모든 프로세서 사용)으로 유지하는 것이 최적입니다.

대부분의 Configuration Manager 관리자는 [SQL Server의 "최대 병렬 처리 수준" 구성 옵션에 대한 권장 사항 및 지침](https://support.microsoft.com/help/2806535/recommendations-and-guidelines-for-the-max-degree-of-parallelism-confi)을 따릅니다. 대부분의 최신 대형 하드웨어에서이 지침을 따르면 권장 최대 설정이 8이 됩니다. 그러나 프로세서 수에 비해 많은 수의 작은 쿼리를 실행하는 경우 더 높은 수로 설정하면 도움이 될 수 있습니다. 더 많은 코어를 사용할 수 있는 대규모 사이트에서는 8로 제한하는 것이 반드시 최선의 설정은 아닙니다. 

코어가 8개보다 많은 SQL Server에서는 먼저 설정 0으로 시작하고 성능 문제 또는 과도한 잠금을 경험할 때만 변경하세요. 0에서 성능 문제가 발생하여 MaxDOP를 변경해야 하는 경우 해당 사이트의 SQL 서버 크기 조정에 대한 최소 권장 코어 수 이상의 새로운 값으로 시작하세요. 이 값보다 낮게 설정하면 거의 틀림없이 성능에 부정적 영향을 줍니다. 예를 들어 100,000 클라이언트 사이트에 대한 원격 SQL Server에는 12개 이상의 코어가 필요합니다. SQL Server에 코어가 16개인 경우 MaxDOP 설정값 12를 사용하여 테스트를 시작하세요.

## <a name="other-common-performance-related-questions"></a>그 밖의 일반적인 성능 관련 질문

### <a name="which-folders-on-the-site-server-or-other-roles-should-i-exclude-for-antivirus-software"></a>바이러스 백신 소프트웨어를 위해 사이트 서버의 어떤 폴더(또는 다른 역할)를 제외해야 하나요?

모든 시스템에서 바이러스 백신 보호를 사용하지 않도록 설정하는 것은 신중해야 합니다. 대량의 보안 환경에서는 최적의 성능을 위해 *활성 모니터링*을 사용하지 않도록 설정하는 것이 좋습니다.

권장 바이러스 백신 제외에 대한 자세한 내용은 [Configuration Manager 2012와 현재 분기 사이트 서버, 사이트 시스템 및 클라이언트에 대한 권장 바이러스 백신 제외](https://support.microsoft.com/help/327453/recommended-antivirus-exclusions-for-configuration-manager-2012-and-cu)를 참조하세요.

### <a name="what-can-i-do-to-make-wsus-perform-better-when-its-used-with-configuration-manager"></a>Configuration Manager와 함께 사용할 때 WSUS를 더 잘 수행하려면 어떻게 해야 하나요?

몇 가지 주요 IIS 설정(예: WsusPool 큐 길이 및 WsusPool 프라이빗 메모리 제한)을 변경하면 더 작은 설치에서도 WSUS 성능이 개선될 수 있습니다. 자세한 내용은 [권장 하드웨어](../plan-design/configs/recommended-hardware.md)를 참조하세요.

또한 WSUS를 실행하는 운영 체제에 대해 최신 업데이트가 설치되었는지 확인하세요.

- Windows Server 2012: 2017년 10월 이후 릴리스된 "보안만"이 아닌 모든 누적 업데이트 ([KB4041690](https://support.microsoft.com/help/4041690/windows-server-2012-update-kb4041690))
- Windows Server 2012 R2: 2017년 8월 이후 릴리스된 "보안만"이 아닌 모든 누적 업데이트 ([KB4039871](https://support.microsoft.com/help/4039871/windows-8-1-windows-server-2012-r2-update-kb4039871))
- Window Server 2016: 2017년 8월 이후 릴리스된 "보안만"이 아닌 모든 누적 업데이트 ([KB4039396](https://support.microsoft.com/help/4039396/windows-10-update-kb4039396))

### <a name="what-type-of-maintenance-should-i-run-on-my-wsus-servers"></a>내 WSUS 서버에서 어떤 종류의 유지 관리를 실행해야 하나요?

[Microsoft WSUS 및 Configuration Manager SUP 유지 관리 전체 가이드](https://support.microsoft.com/help/4490644/complete-guide-to-microsoft-wsus-and-configuration-manager-sup-maint)를 참조하세요.

### <a name="i-want-to-set-up-basic-performance-monitoring-for-my-site-what-should-i-watch"></a>내 사이트에 대해 기본 성능 모니터링을 설정하려고 합니다. 무엇을 감시해야 하나요?

기존 서버 성능 모니터링은 일반적인 Configuration Manager에 대해 효과적으로 작동합니다. 또한 Configuration Manager, SQL Server 및 Windows Server에 대한 여러 System Center Operations Manager 관리 팩을 이용하여 서버의 기본적인 상태를 모니터링할 수도 있습니다. 또한 Configuration Manager가 제공하는 Windows Performance Monitor(PerfMon) 카운터를 직접 모니터링할 수도 있습니다. 여러 받은 편지함의 백로그에서 잠재적인 사이트 성능 문제 또는 백로그의 조기 경고 기호를 모니터링합니다.

## <a name="see-also"></a>참고 항목

- [사이트 크기 조정 및 성능 지침](../plan-design/configs/site-size-performance-guidelines.md)
- [Azure의 Configuration Manager 질문과 대답](configuration-manager-on-azure.md)
