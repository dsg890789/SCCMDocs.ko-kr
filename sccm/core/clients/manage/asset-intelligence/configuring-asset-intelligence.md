---
title: Asset Intelligence 구성
titleSuffix: Configuration Manager
description: System Center Configuration Manager에서 Asset Intelligence를 설정합니다.
ms.date: 2/22/2017
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 08e0382d-de05-4a76-ba5c-7223173f7066
author: mestew
ms.author: mstewart
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 88a127f4dffa42c94f27727801519dfec77c855a
ms.sourcegitcommit: f9654cd1a3af6d67de52fedaccceb2e22dafc159
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67677793"
---
# <a name="configure-asset-intelligence-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 Asset Intelligence 구성

*적용 대상: System Center Configuration Manager(현재 분기)*

Asset Intelligence는 소프트웨어 라이선스 사용을 인벤토리에 포함하고 관리합니다.   

## <a name="steps-to-configure-asset-intelligence"></a>Asset Intelligence 구성 단계  
   

- **1단계**: Asset Intelligence 보고서에 필요한 인벤토리 데이터를 수집하려면 [System Center Configuration Manager에서 하드웨어 인벤토리를 확장하는 방법](../../../../core/clients/manage/inventory/extend-hardware-inventory.md)에 설명된 대로 하드웨어 인벤토리 클라이언트 에이전트를 사용하도록 설정해야 합니다.
- **2단계**: [Asset Intelligence 하드웨어 인벤토리 보고 클래스를 사용하도록 설정합니다](#BKMK_EnableAssetIntelligence).  
- **3단계**: [Asset Intelligence 동기화 지점 설치](#BKMK_InstallAssetIntelligenceSynchronizationPoint)
- **4단계**: [성공 로그온 이벤트 감사를 사용하도록 설정](#BKMK_EnableSuccessLogonEvents)  
- **5단계**: [소프트웨어 라이선스 정보 가져오기](#BKMK_ImportSoftwareLicenseInformation)  
- **6단계**: [Asset Intelligence 유지 관리 작업 구성](#BKMK_ConfigureMaintenanceTasks) 


###  <a name="BKMK_EnableAssetIntelligence"></a> Enable Asset Intelligence hardware inventory reporting classes  
 Configuration Manager 사이트에 Asset Intelligence를 사용하도록 설정하려면 Asset Intelligence 하드웨어 인벤토리 보고 클래스를 하나 이상 사용하도록 설정해야 합니다. **Asset Intelligence** 홈페이지 또는 **관리** 작업 영역, **클라이언트 설정** 노드, 클라이언트 설정 속성에서 클래스를 사용하도록 설정할 수 있습니다. 다음 절차 중 하나를 수행하십시오.  

##### <a name="to-enable-asset-intelligence-hardware-inventory-reporting-classes-from-the-asset-intelligence-home-page"></a>Asset Intelligence 홈페이지에서 Asset Intelligence 하드웨어 인벤토리 보고 클래스를 사용하도록 설정하려면  

1.  Configuration Manager 콘솔에서 **자산 및 준수** > **Asset Intelligence**를 선택합니다.  

3.  **홈** 탭의 **Asset Intelligence** 그룹에서 **인벤토리 클래스 편집**을 선택합니다.   

4.  Asset Intelligence 보고를 사용하도록 설정하려면 **모든 Asset Intelligence 보고 클래스 사용** 또는 **선택한 Asset Intelligence 보고 클래스만 사용**을 선택하고 표시된 클래스 중 하나 이상의 보고 클래스를 선택합니다.  

    > [!NOTE]  
    >  이 절차를 사용하여 사용하도록 설정한 하드웨어 인벤토리 클래스에 종속된 Asset Intelligence 보고서는 클라이언트가 데이터를 검색하여 하드웨어 인벤토리로 반환할 때까지 데이터를 표시하지 않습니다.  


##### <a name="to-enable-asset-intelligence-hardware-inventory-reporting-classes-from-client-settings-properties"></a>클라이언트 설정 속성에서 Asset Intelligence 하드웨어 인벤토리 보고 클래스를 사용하도록 설정하려면  

1.  Configuration Manager 콘솔에서 **관리** >  **클라이언트 설정** > **기본 클라이언트 에이전트 설정**을 선택합니다. 사용자 지정 클라이언트 설정을 만들었다면 해당 설정을 선택할 수 있습니다.  

3.  **홈** 탭의 **속성** 그룹에서 **속성**을 선택합니다.   

4.  **하드웨어 인벤토리** > **클래스 설정**을 선택합니다. 을 참조하세요.  

5.  **범주별 필터링** > **Asset Intelligence 보고 클래스**를 선택합니다. 클래스의 목록은 Asset Intelligence 하드웨어 인벤토리 보고 클래스로만 새로 고쳐집니다.  

6.  목록에서 보고 클래스를 하나 이상 선택합니다.  

    > [!NOTE]  
    >  이 절차를 사용하여 사용하도록 설정한 하드웨어 인벤토리 클래스에 종속된 Asset Intelligence 보고서는 클라이언트가 데이터를 검색하여 하드웨어 인벤토리로 반환할 때까지 데이터를 표시하지 않습니다.  
  

###  <a name="BKMK_InstallAssetIntelligenceSynchronizationPoint"></a> Install an Asset Intelligence Synchronization Point  

Asset Intelligence 동기화 지점 사이트 시스템 역할은 Configuration Manager 사이트를 System Center Online에 연결하여 Asset Intelligence 카탈로그 정보를 동기화하는 데 사용됩니다. Asset Intelligence 동기화 지점은 Configuration Manager 계층 구조의 최상위 사이트에 위치한 사이트 시스템에만 설치할 수 있으며 TCP 포트 443을 사용하여 System Center Online과 동기화하는 인터넷 액세스가 필요합니다.

새 Asset Intelligence 카탈로그 정보를 다운로드하는 것 외에도 Asset Intelligence 동기화 지점을 통해 사용자 지정 소프트웨어 타이틀 정보를 System Center Online에 분류를 위해 업로드할 수 있습니다. Microsoft에서는 모든 업로드된 소프트웨어 타이틀을 공개 정보로 처리합니다. 사용자 지정 소프트웨어 타이틀에 기밀 정보나 비공개 정보가 포함되지 않도록 하세요. 소프트웨어 타이틀 분류를 요청하는 방법에 대한 자세한 내용은 [범주화되지 않은 소프트웨어 타이틀에 대한 카탈로그 업데이트 요청](../../../../core/clients/manage/asset-intelligence/operations-for-asset-intelligence.md#BKMK_RequestCatalogUpdate)을 참조하세요.  

##### <a name="to-install-an-asset-intelligence-synchronization-point-site-system-role"></a>Asset Intelligence 동기화 지점 사이트 시스템 역할을 설치하려면  

1.  Configuration Manager 콘솔에서 **관리**> **사이트 구성** > **서버 및 사이트 시스템 역할**을 선택합니다.  

3.  기존 또는 새 사이트 시스템 서버에 Asset Intelligence 동기화 지점 사이트 시스템 역할을 추가합니다.  

    -  **새 사이트 시스템 서버**: **홈** 탭의 **만들기** 그룹에서 **사이트 시스템 서버 만들기**를 선택하여 마법사를 선택합니다.   

        > [!NOTE]  
        >  기본적으로 Configuration Manager에서 사이트 시스템 역할을 설치할 때 사용 가능한 첫 번째 NTFS 포맷의 하드 디스크 드라이브(사용 가능한 하드 디스크 공간이 가장 큼)에 설치 파일이 설치됩니다. Configuration Manager가 특정 드라이브에 설치되지 않도록 하려면 사이트 시스템 서버를 설치하기 전에 No_sms_on_drive.sms라는 빈 파일을 만들고 드라이브의 루트 폴더에 복사합니다.  

    -  **기존 사이트 시스템 서버**: Asset Intelligence 동기화 지점 사이트 시스템 역할을 설치할 서버를 선택합니다. 서버를 선택하면 서버에 이미 설치되어 있는 사이트 시스템 역할의 목록이 세부 정보 창에 나타납니다.  

         **홈** 탭의 **서버** 그룹에서 **사이트 시스템 역할 추가**를 선택하여 마법사를 시작합니다.  

4.  **일반** 페이지를 완료합니다. 기존 사이트 시스템 서버에 Asset Intelligence 동기화 지점을 추가할 때에는 이전에 구성된 값을 확인해야 합니다.  

5.  **시스템 역할 선택** 페이지의 사용 가능한 역할 목록에서 **Asset Intelligence 동기화 지점**을 선택합니다.  

6.  **Asset Intelligence 동기화 지점 연결 설정** 페이지에서 **다음**을 선택합니다.  

     기본적으로 **이 Asset Intelligence 동기화 지점 사용** 설정이 선택되어 있으며 이 페이지에서는 구성할 수 없습니다. System Center Online에서는 TCP 포트 443에 대해서만 네트워크 트래픽이 허용되므로 **SSL 포트 번호** 설정은 마법사의 이 페이지에서 구성할 수 없습니다.  

7.  선택적으로 System Center Online 인증 인증서(.pfx) 파일 경로를 지정할 수 있습니다. 일반적으로 사이트 역할이 설치되는 동안 연결 인증서가 자동으로 프로비전되므로 인증서 경로를 지정하지 않습니다.  

8.  **프록시 서버 설정** 페이지에서 Asset Intelligence 동기화 지점이 System Center Online에 연결하여 카탈로그를 동기화할 때 프록시 서버를 사용할지 여부와 자격 증명을 사용하여 프록시 서버에 연결할지 여부를 지정합니다.  

    > [!WARNING]  
    >  System Center Online에 연결하기 위해 프록시 서버가 필요한 경우 프록시 서버 인증용으로 구성된 계정에 대해 사용자 계정 암호가 만료되면 연결 인증서도 삭제될 수 있습니다.  

9. **동기화 일정** 페이지에서 일정에 따라 Asset Intelligence 카탈로그를 동기화할지 지정합니다. 동기화 일정을 사용하도록 설정하는 경우 단순 또는 사용자 지정 동기화 일정을 지정합니다. 예약된 동기화를 진행하는 동안 Asset Intelligence 동기화 지점이 System Center Online에 연결되어 최신 Asset Intelligence 카탈로그를 검색합니다. Configuration Manager 콘솔의 Asset Intelligence 노드에서 Asset Intelligence 카탈로그를 수동으로 동기화할 수 있습니다. Asset Intelligence 카탈로그를 수동으로 동기화하는 단계는 [System Center Configuration Manager에서 Asset Intelligence에 대한 작업](../../../../core/clients/manage/asset-intelligence/operations-for-asset-intelligence.md)의 [Asset Intelligence 카탈로그를 수동으로 동기화하려면](../../../../core/clients/manage/asset-intelligence/operations-for-asset-intelligence.md#BKMK_ManuallySynchronizeCatalog) 섹션을 참조하세요.  

10. 마법사 완료 

###  <a name="BKMK_EnableSuccessLogonEvents"></a> Enable auditing of success logon events  
 네 가지 Asset Intelligence 보고서에 클라이언트 컴퓨터의 Windows 보안 이벤트 로그에서 수집된 정보가 표시됩니다. 다음은 성공 로그온 이벤트의 감사를 사용하도록 컴퓨터 보안 정책 로그온 설정을 구성하는 방법입니다.  

##### <a name="to-enable-success-logon-event-logging-by-using-a-local-security-policy"></a>로컬 보안 정책을 사용하여 성공 로그온 이벤트 로깅을 사용하도록 설정하려면  

1.  Configuration Manager 클라이언트 컴퓨터에서 **시작** > **관리 도구** > **로컬 보안 정책**을 선택합니다.  

2.  **로컬 보안 정책** 대화 상자의 **보안 설정**에서 **로컬 정책**을 확장한 다음 **감사 정책**을 선택합니다.  

3.  결과 창에서 **로그온 이벤트 감사**를 두 번 클릭하고 **성공** 확인란이 선택되었는지 확인한 다음 **확인**을 선택합니다.  

##### <a name="to-enable-success-logon-event-logging-by-using-an-active-directory-domain-security-policy"></a>Active Directory 도메인 보안 정책을 사용하여 성공 로그온 이벤트 로깅을 사용하도록 설정하려면  

1.  도메인 컨트롤러 컴퓨터에서 **시작**을 선택하고 **관리 도구**를 가리킨 후 **도메인 보안 정책**을 선택합니다.  

2.  **로컬 보안 정책** 대화 상자의 **보안 설정**에서 **로컬 정책**을 확장한 다음 **감사 정책**을 선택합니다.  

3.  결과 창에서 **로그온 이벤트 감사**를 두 번 클릭하고 **성공** 확인란이 선택되었는지 확인한 다음 **확인**을 선택합니다.  

###  <a name="BKMK_ImportSoftwareLicenseInformation"></a> Import software license information  
 다음 섹션에서는 소프트웨어 라이선스 가져오기 마법사를 사용하여 Microsoft 및 일반 소프트웨어 라이선스 정보를 Configuration Manager 사이트 데이터베이스로 가져오는 데 필요한 절차에 대해 설명합니다. 소프트웨어 라이선스 정보를 라이선스 계정 파일에서 사이트 데이터베이스로 가져올 때 사이트 서버 컴퓨터 계정은 소프트웨어 라이선스 정보를 가져오는 데 사용되는 파일 공유에 대한 NTFS 파일 시스템의 **모든 권한** 권한이 필요합니다.  

> [!IMPORTANT]  
>  소프트웨어 라이선스 정보를 사이트 데이터베이스로 가져올 때 기존 소프트웨어 라이선스 정보를 덮어씁니다. 소프트웨어 라이선스 가져오기 마법사를 사용하는 소프트웨어 라이선스 정보 파일에 필요한 모든 소프트웨어 라이선스 정보의 전체 목록이 포함되어있는지 확인합니다.  

##### <a name="to-import-software-license-information-into-the-asset-intelligence-catalog"></a>Asset Intelligence 카탈로그에 소프트웨어 라이선스 정보를 가져오려면  

1.  **자산 및 준수** 작업 영역에서 **Asset Intelligence**를 선택합니다.  

2.  **홈** 탭의 **Asset Intelligence** 그룹에서 **소프트웨어 라이선스 가져오기**를 선택합니다.   

4.  **가져오기** 페이지에서 MVLS(Microsoft Volume Licensing) 파일(.xml 또는 .csv) 또는 일반 라이선스 계정 파일(.csv)을 가져올지 여부를 지정합니다. 일반 라이선스 계정 파일 만들기에 대한 자세한 내용은 이 항목의 뒷부분에 나오는 [가져오기를 위한 일반 라이선스 계정 정보 파일 만들기](#BKMK_CreateGeneralLicenseStatement) 섹션을 참조하세요.  

    > [!WARNING]  
    >  Asset Intelligence 카탈로그에 가져올 수 있는 .csv 형식의 MVLS 파일을 다운로드하려면 [Microsoft 볼륨 라이선스 서비스 센터](http://go.microsoft.com/fwlink/p/?LinkId=226547)를 참조하세요. 이 정보에 액세스하려면 웹 사이트에 등록된 계정이 있어야 합니다. .xml 형식의 MVLS 파일을 가져오는 방법에 대한 자세한 내용은 Microsoft 계정 담당자에게 문의해야 합니다.  

5.  라이선스 계정 파일에 대한 UNC 경로를 입력하거나 **찾아보기** 를 선택하여 네트워크 공유 폴더 및 파일을 선택합니다.  

    > [!NOTE]  
    >  라이선스 정보 파일에 대한 승인되지 않은 액세스를 차단하려면 공유 폴더가 올바르게 보안되어야 하며 마법사가 실행되고 있는 컴퓨터의 컴퓨터 계정에 라이선스 가져오기 파일이 들어 있는 공유에 대해 모든 권한이 있어야 합니다.  

6. 마법사를 완료합니다.  

###  <a name="BKMK_CreateGeneralLicenseStatement"></a> 가져오기를 위한 일반 라이선스 계정 정보 파일 만들기  
 일반 라이선스 계정은 쉼표로 구분된(.csv) 파일 형식으로 수동으로 만든 라이선스 가져오기 파일을 사용하여 Asset Intelligence 카탈로그에 가져올 수도 있습니다.  

> [!NOTE]  
>  **Name**, **Publisher**, **Version**및 **EffectiveQuantity** 필드만 데이터를 채우라고 요구하지만 라이선스 가져오기 파일의 첫 번째 열에 있는 모든 필드가 입력되어야 합니다. 모든 날짜 필드는 월/일/연도(예: 08/04/2008) 형식으로 표시되어야 합니다.  

Asset Intelligence는 일반 라이선스 계정에서 지정하는 제품을 제품 이름 및 제품 버전을 사용하여 일치시키지만 게시자 이름은 사용하지 않습니다. 사이트 데이터베이스에 저장된 제품 이름과 정확하게 일치하는 일반 라이선스 계정의 제품 이름을 사용해야 합니다. Asset Intelligence는 일반 라이선스 계정에서 부여된 **EffectiveQuantity**의 숫자를 가져와서 해당 숫자를 Configuration Manager 인벤토리에서 확인한 설치된 제품 숫자와 비교합니다.  

> [!TIP]  
>  Configuration Manager 사이트 데이터베이스에 저장된 제품 이름의 전체 목록을 가져오려면 사이트 데이터베이스에서 다음 쿼리를 실행합니다. SELECT ProductName0 FROM v_GS_INSTALLED_SOFTWARE.  

 제품에 대한 정확한 버전을 지정하거나 버전의 일부(예: 주 버전만)를 지정할 수 있습니다. 다음 예제는 특정 제품에 대한 일반 라이선스 계정 버전 항목과 일치하는 결과 버전을 제공합니다.  

|일반 라이선스 계정 항목|사이트 데이터베이스 항목 일치|  
|-------------------------------------|------------------------------------|  
|이름: "MySoftware", ProductVersion0:"2"|ProductName0: "Mysoftware", ProductVersion0: "2.01.1234"<br /><br /> ProductName0: "MySoftware", ProductVersion0: "2.02.5678"<br /><br /> ProductName0: "MySoftware", ProductVersion0: "2.05.1234"<br /><br /> ProductName0: "MySoftware", ProductVersion0: "2.05.5678"<br /><br /> ProductName0: "MySoftware", ProductVersion0: "2.05.3579.000"<br /><br /> ProductName0: "MySoftware", ProductVersion0: "2.10.1234"|  
|이름: "MySoftware", Version "2.05"|ProductName0: "MySoftware", ProductVersion0: "2.05.1234"<br /><br /> ProductName0: "MySoftware", ProductVersion0: "2.05.5678"<br /><br /> ProductName0: "MySoftware", ProductVersion0: "2.05.3579.000"|  
|이름: "Mysoftware", Version "2"<br /><br /> 이름: "Mysoftware", Version "2.05"|가져오는 동안 오류가 발생했습니다. 여러 항목이 동일한 제품 버전과 일치하는 경우 가져오기에 실패합니다.|  
  

##### <a name="to-create-a-general-license-statement-import-file-by-using-microsoft-excel"></a>Microsoft Excel을 사용하여 일반 라이선스 계정 가져오기 파일을 만들려면  

1.  Microsoft Excel을 열고 새 스프레드시트를 만듭니다.  

2.  새 스프레드시트의 첫 번째 행에 소프트웨어 라이선스 데이터 필드 이름을 모두 입력합니다.  

3.  새 스프레드시트의 두 번째 및 이후의 행에 필요에 따라 소프트웨어 라이선스 정보를 입력합니다. 가져올 각 소프트웨어 라이선스에 대해 필요한 소프트웨어 라이선스 데이터 필드의 모든 후속 행이 입력되어야 합니다. 스프레드시트에 입력한 소프트웨어 타이틀 이름은 하드웨어 인벤토리가 실행된 후 클라이언트 컴퓨터의 리소스 탐색기에 표시되는 소프트웨어 타이틀과 같아야 합니다.  

4.  파일을 .csv 형식으로 저장합니다.  

5.  .csv 파일을 Asset Intelligence 카탈로그로 소프트웨어 라이선스 정보를 가져오는 데 사용했던 파일 공유에 복사합니다.  

6.  Configuration Manager 콘솔에서 소프트웨어 라이선스 가져오기 마법사를 사용하여 새로 만든 .csv 파일을 가져옵니다.  

7.  Asset Intelligence **라이선스 15A – 제3자 소프트웨어 조정 보고서**를 실행하여 라이선스 정보를 Asset Intelligence 카탈로그에 성공적으로 가져왔는지 확인합니다.  

> [!NOTE]  
>  테스트 목적으로 사용할 수 있는 일반 소프트웨어 라이선스 파일의 예를 보려면 [System Center Configuration Manager에서 Asset Intelligence 일반 라이선스 가져오기 파일 예제](../../../../core/clients/manage/asset-intelligence/example-asset-intelligence-general-license-import.md)를 참조하세요.  

#### <a name="sample-table-to-describe-software-licenses"></a>소프트웨어 라이선스를 설명하는 샘플 표  
 일반 라이선스 계정 가져오기 파일을 만들 때 다음 표의 정보를 사용하여 Asset Intelligence 카탈로그에 가져올 소프트웨어 라이선스를 설명할 수 있습니다.  

|열 이름|데이터 형식|필수|예|  
|-----------------|---------------|--------------|-------------|  
|Name|최대 255자|예|소프트웨어 타이틀|  
|Publisher|최대 255자|예|소프트웨어 게시자|  
|Version|최대 255자|예|소프트웨어 타이틀 버전|  
|언어|최대 255자|예|소프트웨어 타이틀 언어|  
|EffectiveQuantity|정수 값|예|구매한 라이선스 수|  
|PONumber|최대 255자|아니요|구매 주문 정보|  
|ResellerName|최대 255자|아니요|재판매인 정보|  
|DateOfPurchase|다음 형식의 날짜 값:  MM/DD/YYYY|아니요|라이선스 구매 날짜|  
|SupportPurchased|비트 값|아니요|0 또는 1: 예는 0, 아니요는 1 입력|  
|SupportExpirationDate|다음 형식의 날짜 값:  MM/DD/YYYY|아니요|구매한 지원의 종료 날짜|  
|설명|최대 255자|아니요|선택적 설명|  

###  <a name="BKMK_ConfigureMaintenanceTasks"></a> Configure Asset Intelligence maintenance tasks  
 다음 유지 관리 작업을 Asset Intelligence에 사용할 수 있습니다.  

-   **인벤토리 정보를 사용하여 애플리케이션 타이틀 확인**: 소프트웨어 인벤토리에 보고된 소프트웨어 타이틀이 Asset Intelligence 카탈로그 내 소프트웨어 타이틀과 일치하는지 확인합니다. 기본적으로 이 작업은 사용하도록 설정되어 있으며 토요일 오전 12시 이후부터 오전 5시 이전 사이에 실행되도록 예약되어 있습니다. 이 유지 관리 작업은 Configuration Manager 계층 구조의 최상위 사이트에서만 사용할 수 있습니다.  

-   **설치된 소프트웨어 데이터 요약**: **자산 및 규정 준수** 작업 영역의 **Asset Intelligence** 노드 아래 **인벤토리에 포함된 소프트웨어** 노드에 표시되는 정보를 제공합니다. 작업을 실행하면 Configuration Manager가 기본 사이트에서 인벤토리에 포함된 모든 소프트웨어 타이틀 수를 수집합니다. 기본적으로 이 작업은 사용하도록 설정되어 있으며 매일 오전 12시 이후부터 오전 5시 이전 사이에 실행되도록 예약되어 있습니다. 이 유지 관리 작업은 기본 사이트에서만 사용할 수 있습니다.  

##### <a name="to-configure-asset-intelligence-maintenance-tasks"></a>Asset Intelligence 유지 관리 작업을 구성하려면  

1.  Configuration Manager 콘솔에서 **관리** > **사이트 구성** > **사이트**를 선택합니다.  

3.  Asset Intelligence 유지 관리 작업을 구성할 수 있는 사이트를 선택합니다.  

4.  **홈** 탭의 **설정** 그룹에서 **사이트 유지 관리**를 선택합니다. 작업을 선택하고 **편집**을 선택하여 설정을 수정합니다. 

    사이트의 사용량이 적은 시간대로 기간을 설정하는 것이 좋습니다. 기간은 작업을 실행할 수 있는 시간 간격입니다. **작업 속성** 대화 상자에서 지정한 **Start after** (다음 이후 시작) 및 **가장 늦은 시작 시간** 으로 정의됩니다.  

    현재 날짜를 선택하고 **Start after** (다음 이후 시작) 시간을 현재 시간 이후 몇 분 후로 설정하여 작업을 바로 시작할 수 있습니다.  

7.  **확인**을 선택하여 설정을 저장합니다. 이제 작업 일정에 따라 작업이 실행됩니다.  

    > [!NOTE]  
    >  처음 작업을 실행할 때 실패하는 경우 Configuration Manager가 작업을 성공적으로 실행할 때까지 또는 작업이 실행할 수 있는 기간까지 작업을 다시 실행하려고 시도합니다.  
