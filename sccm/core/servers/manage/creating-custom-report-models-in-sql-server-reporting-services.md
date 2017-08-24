---
title: "사용자 지정 보고서 만들기 | Microsoft 문서"
description: "비즈니스 요구 사항을 충족하는 보고서 모델을 정의한 다음 Configuration Manager에 보고서 모델을 배포합니다."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f2df88b4-c348-4dcf-854a-54fd6eedf485
caps.latest.revision: "5"
caps.handback.revision: "0"
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.openlocfilehash: 9951dd9333ebef00c7acd5d72b20a02382e3206c
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/07/2017
---
# <a name="creating-custom-report-models-for-system-center-configuration-manager-in-sql-server-reporting-services"></a>SQL Server Reporting Services에서 System Center Configuration Manager에 대한 사용자 지정 보고서 모델 만들기

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager에 샘플 보고서 모델이 포함되어 있지만, 고유한 비즈니스 요구 사항에 맞게 보고서 모델을 정의한 다음 Configuration Manager에 보고서 모델을 배포하여 새 모델 기반 보고서를 만들 때 사용할 수 있습니다. 다음 표에는 기본 보고서 모델을 만들고 배포하는 단계가 나와 있습니다.  

> [!NOTE]  
>  더 다양한 고급 보고서 모델을 만드는 단계는 이 항목의 [SQL Server Reporting Services에서 고급 보고서 모델을 만드는 단계](#AdvancedReportModel) 섹션을 참조하십시오.  

|단계|설명|추가 정보|  
|----------|-----------------|----------------------|  
|SQL Server Business Intelligence Development Studio가 설치되어 있는지 확인합니다.|보고서 모델은 SQL Server Business Intelligence Development Studio를 사용하여 디자인되고 작성됩니다. 사용자 지정 보고서 모델을 만들 컴퓨터에 SQL Server Business Intelligence Development Studio가 설치되어 있는지 확인합니다.|SQL Server Business Intelligence Development Studio에 대한 자세한 내용은 SQL Server 2008 설명서를 참조하십시오.|  
|보고서 모델 프로젝트 만들기|보고서 모델 프로젝트에는 데이터 원본의 정의(.ds 파일), 데이터 원본 뷰의 정의(.dsv 파일) 및 보고서 모델(.smdl 파일)이 포함됩니다.|자세한 내용은 이 항목에서 [보고서 모델 프로젝트를 만들려면](#BKMK_CreateReportModelProject) 섹션을 참조하세요.|  
|보고서 모델의 데이터 원본 정의|보고서 모델 프로젝트를 만든 다음에는 비즈니스 데이터를 추출할 데이터 원본 하나를 정의해야 합니다. 일반적으로 이 원본은 Configuration Manager 사이트 데이터베이스입니다.|자세한 내용은 이 항목의 [보고서 모델의 데이터 원본을 정의하려면](#BKMK_DefineReportModelDataSource) 섹션을 참조하십시오.|  
|보고서 모델의 데이터 원본 뷰 정의|보고서 모델 프로젝트에서 사용하는 데이터 원본을 정의하고 나면 다음 단계는 프로젝트의 데이터 원본 뷰를 정의하는 것입니다. 데이터 원본 뷰는 하나 이상의 데이터 원본에 기반한 논리 데이터 모델입니다. 데이터 원본 뷰는 기본 데이터 원본에 포함된 실제 개체(예: 테이블 및 뷰)에 대한 액세스 권한을 캡슐화합니다. SQL Server Reporting Services는 데이터 원본 뷰에서 보고서 모델을 생성합니다.<br /><br /> 데이터 원본 뷰를 사용하면 지정한 데이터에 대한 유용한 표현을 제공하여 모델 디자인 프로세스를 쉽게 진행할 수 있습니다. 기본 데이터 원본을 변경하지 않고도 데이터 원본 뷰에서 테이블과 필드의 이름을 변경하고 집계 필드 및 파생 테이블을 추가할 수 있습니다. 효율적인 모델을 만들려면 사용하려는 데이터 원본 뷰에 해당 테이블만 추가합니다.|자세한 내용은 이 항목의 [보고서 모델의 데이터 원본 뷰를 정의하려면](#BKMK_DefineReportModelDataSourceView) 섹션을 참조하십시오.|  
|보고서 모델 만들기|보고서 모델은 데이터베이스 위의 계층으로, 비즈니스 엔터티, 필드 및 역할을 식별합니다. 보고서 모델이 게시되면 보고서 작성기 사용자가 이러한 모델을 사용하여 데이터베이스 구조에 익숙해지거나 쿼리를 이해하고 작성하지 않고도 보고서를 개발할 수 있습니다. 모델은 한 이름으로 그룹화되는 관련 보고서 항목의 집합, 이러한 비즈니스 항목 간에 미리 정의된 관계, 미리 정의된 계산으로 구성됩니다. 모델은 SMDL(Semantic Model Definition Language)이라는 XML 언어를 사용하여 정의됩니다. 보고서 모델 파일의 파일 이름 확장명은 .smdl입니다.|자세한 내용은 이 항목에서 [보고서 모델을 만들려면](#BKMK_CreateReportModel) 섹션을 참조하세요.|  
|보고서 모델 게시|방금 만든 모델을 사용하여 보고서를 작성하려면 이 모델을 보고서 서버에 게시해야 합니다. 데이터 원본 및 데이터 원본 뷰는 모델을 게시할 때 해당 모델에 포함됩니다.|자세한 내용은 이 항목에서 [SQL Server Reporting Services에서 사용할 보고서 모델을 게시하려면](#BKMK_PublishReportModel) 섹션을 참조하세요.|  
|Configuration Manager에 보고서 모델 배포|**보고서 만들기 마법사**에서 사용자 지정 보고서 모델을 사용하여 모델 기반 보고서를 만들려면 먼저 Configuration Manager에 보고서 모델을 배포해야 합니다.|자세한 내용은 이 항목에서 [Configuration Manager에 사용자 지정 보고서 모델을 배포하려면](#BKMK_DeployReportModel) 섹션을 참조하세요.|  

## <a name="steps-for-creating-a-basic-report-model-in-sql-server-reporting-services"></a>SQL Server Reporting Services에서 기본 보고서 모델을 만드는 단계  
 다음 절차를 사용하면 사이트의 사용자가 Configuration Manager 데이터베이스의 단일 뷰에서 데이터를 기반으로 한 특정 모델 기반 보고서를 작성하는 데 사용할 수 있는 기본 보고서 모델을 만들 수 있습니다. 보고서 작성자에게 사이트의 클라이언트 컴퓨터에 대한 정보를 나타내는 보고서 모델을 만듭니다. 이 정보는 Configuration Manager 데이터베이스의 **v_R_System** 뷰에서 가져옵니다.  

 이러한 절차를 수행하는 컴퓨터에 SQL Server Business Intelligence Development Studio를 설치했는지, 그리고 이 컴퓨터에 보고 서비스 지점 서버에 대한 네트워크 연결이 있는지 확인합니다. SQL Server Business Intelligence Development Studio에 대한 자세한 내용은 SQL Server 2008 설명서를 참조하십시오.  

###  <a name="BKMK_CreateReportModelProject"></a> 보고서 모델 프로젝트를 만들려면  

1.  바탕 화면에서 **시작**, **Microsoft SQL Server 2008**, **SQL Server Business Intelligence Development Studio**를 차례로 클릭합니다.  

2.  Microsoft Visual Studio에 **SQL Server Business Intelligence Development Studio** 가 열리면 **파일**, **새로 만들기**, **프로젝트**를 차례로 클릭합니다.  

3.  **새 프로젝트** 대화 상자의 **템플릿** 목록에서 **보고서 모델 프로젝트** 를 선택합니다.  

4.  **이름** 입력란에서 이 보고서 모델의 이름을 지정합니다. 예를 들어 **Simple_Model**이라고 입력합니다.  

5.  보고서 모델 프로젝트를 만들려면 **확인**을 클릭합니다.  

6.  **솔루션 탐색기** 에 **Simple_Model**솔루션이 표시됩니다.  

    > [!NOTE]  
    >  **솔루션 탐색기** 창이 표시되지 않는 경우 **보기**를 클릭한 다음 **솔루션 탐색기**를 클릭합니다.  

###  <a name="BKMK_DefineReportModelDataSource"></a> 보고서 모델의 데이터 원본을 정의하려면  

1.  **SQL Server Business Intelligence Development Studio** 의 **솔루션 탐색기**창에서 **데이터 원본** 을 마우스 오른쪽 단추로 클릭하여 **새 데이터 원본 추가**를 선택합니다.  

2.  **데이터 원본 마법사 시작** 페이지에서 **다음**을 클릭합니다.  

3.  **연결 정의 방법 선택** 페이지에서 **기존 연결 또는 새 연결을 사용하여 데이터 원본 만들기** 를 선택했는지 확인한 다음 **새로 만들기**를 클릭합니다.  

4.  **연결 관리자** 대화 상자에서 데이터 원본의 다음 연결 속성을 지정합니다.  

    -   **서버 이름**: Configuration Manager 사이트 데이터베이스 서버의 이름을 입력하거나 목록에서 선택합니다. 기본 인스턴스 대신 명명된 인스턴스로 작업하는 경우 &lt;*데이터베이스 서버*>\\&lt;*인스턴스 이름*>을 입력합니다.  

    -   **indows 인증 사용**을 선택합니다.  

    -   **데이터베이스 이름 선택 또는 입력** 목록에서 Configuration Manager 사이트 데이터베이스의 이름을 선택합니다.  

5.  데이터베이스 연결을 확인하려면 **연결 테스트**를 클릭합니다.  

6.  연결이 되면 **확인** 을 클릭하여 **연결 관리자** 대화 상자를 닫습니다. 연결되지 않으면 입력한 정보가 올바른지 확인한 다음 다시 **연결 테스트** 를 클릭합니다.  

7.  **연결 정의 방법 선택** 페이지에서 **기존 연결 또는 새 연결을 사용하여 데이터 원본 만들기** 를 선택했는지 확인한 다음 방금 지정한 데이터 원본이 **데이터 연결**에 선택되어 있는지 확인하고 **다음**을 클릭합니다.  

8.  **데이터 원본 이름**에서 데이터 원본의 이름을 지정한 후 **마침**을 클릭합니다. 예를 들어 **Simple_Model**이라고 입력합니다.  

9. 이제 **데이터 원본** 노드 아래의 **솔루션 탐색기** 에 **Simple_Model.ds** 라는 데이터 원본이 표시됩니다.  

    > [!NOTE]  
    >  기존 데이터 원본의 속성을 편집하려면 **솔루션 탐색기** 창의 **데이터 원본** 폴더에서 데이터 원본을 두 번 클릭하여 데이터 원본 디자이너에 데이터 원본 속성을 표시합니다.  

###  <a name="BKMK_DefineReportModelDataSourceView"></a> 보고서 모델의 데이터 원본 뷰를 정의하려면  

1.  **솔루션 탐색기**에서 **데이터 원본 뷰** 를 마우스 오른쪽 단추로 클릭하여 **새 데이터 원본 뷰 추가**를 선택합니다.  

2.  **데이터 원본 뷰 마법사 시작** 페이지에서 **다음**을 클릭합니다. **데이터 원본 선택** 페이지가 표시됩니다.  

3.  **관계형 데이터 원본** 창에서 **Simple_Model** 데이터 원본을 선택했는지 확인하고 **다음**을 클릭합니다.  

4.  **테이블 및 뷰 선택** 페이지의 **사용 가능한 개체** 목록에서 보고서 모델에 사용할 **v_R_System (dbo)**뷰를 선택합니다.  

    > [!TIP]  
    >  **사용 가능한 개체** 목록에서 뷰를 찾으려면 목록 맨 위의 **이름** 제목을 클릭하여 개체를 사전순으로 정렬합니다.  

5.  뷰를 선택한 후 **>** 를 클릭하여 **포함된 개체** 를 선택합니다.  

6.  **이름 일치** 페이지가 표시되면 기본 선택 항목을 적용한 후 **다음**을 클릭합니다.  

7.  필요한 개체를 선택한 경우 **다음**을 클릭한 후 데이터 원본 뷰의 이름을 지정합니다. 예를 들어 **Simple_Model**이라고 입력합니다.  

8.  **마침**을 클릭합니다. **솔루션 탐색기** 의 **데이터 원본 뷰** 폴더에 **Simple_Model.dsv**데이터 원본 뷰가 표시됩니다.  

###  <a name="BKMK_CreateReportModel"></a> To create the report model  

1.  **솔루션 탐색기**에서 **보고서 모델** 을 마우스 오른쪽 단추로 클릭하여 **새 보고서 모델 추가**를 선택합니다.  

2.  **보고서 모델 마법사 시작** 페이지에서 **다음**을 클릭합니다.  

3.  **데이터 원본 뷰 선택** 페이지의 **사용 가능한 데이터 원본 뷰** 목록에서 데이터 원본 뷰를 선택하고 **다음**을 클릭합니다. 이 예에서는 **Simple_Model.dsv**를 선택합니다.  

4.  **보고서 모델 생성 규칙을 선택하십시오.** 페이지에서 기본값을 적용하고 **다음**을 클릭합니다.  

5.  **모델 통계 수집** 페이지에서 **모델을 생성하기 전에 모델 통계 업데이트** 가 선택되었는지 확인하고 **다음**을 클릭합니다.  

6.  **마법사 완료** 페이지에서 보고서 모델의 이름을 지정합니다. 이 예에서는 **Simple_Model** 이 표시되는지 확인합니다.  

7.  마법사를 완료하고 보고서 모델을 만들려면 **실행**을 클릭합니다.  

8.  마법사를 끝내려면 **마침**을 클릭합니다. 디자인 창에 보고서 모델이 표시됩니다.  

###  <a name="BKMK_PublishReportModel"></a> SQL Server Reporting Services에서 사용할 보고서 모델을 게시하려면  

1.  **솔루션 탐색기**에서 보고서 모델을 마우스 오른쪽 단추로 클릭하여 **배포**를 선택합니다. 이 예에서는 보고서 모델이 **Simple_Model.smdl**입니다.  

2.  **SQL Server Business Intelligence Development Studio** 창의 왼쪽 아래에서 배포 상태를 검토합니다. 배포가 완료되면 **배포했습니다.** 가 표시됩니다. 배포하지 못한 경우 **출력** 창에 실패 원인이 표시됩니다. 이제 SQL Server Reporting Services 웹 사이트에서 새 보고서 모델을 사용할 수 있습니다.  

3.  **파일**, **모두 저장**을 차례로 클릭한 다음 **SQL Server Business Intelligence Development Studio**를 닫습니다.  

###  <a name="BKMK_DeployReportModel"></a> To deploy the custom report model to Configuration Manager  

1.  보고서 모델 프로젝트를 만든 폴더로 이동합니다. 예: %*USERPROFILE*%\Documents\Visual Studio 2008\Projects\\*&lt;프로젝트 이름\>.*  

2.  보고서 모델 프로젝트 폴더에서 컴퓨터의 임시 폴더로 다음 파일을 복사합니다.  

    -   *&lt;모델 이름\>* **.dsv**  

    -   *&lt;모델 이름\>* **.smdl**  

3.  텍스트 편집기(예: 메모장)를 사용하여 이전 파일을 엽니다.  

4.  *&lt;모델 이름\>***.dsv** 파일에서 다음과 같이 표시된 파일의 첫 줄을 찾습니다.  

     **&lt;DataSourceView xmlns="http://schemas.microsoft.com/analysisservices/2003/engine"\>**  

     이 줄을 다음과 같이 편집합니다.  

     **&lt;DataSourceView xmlns="http://schemas.microsoft.com/analysisservices/2003/engine" xmlns:xsi="RelationalDataSourceView"\>**  

5.  파일 내용 전체를 Windows 클립보드에 복사합니다.  

6.  *&lt;모델 이름\>***.dsv** 파일을 닫습니다.  

7.  *&lt;모델 이름\>***.smdl** 파일에서 다음과 같이 표시된 파일의 마지막 세 줄을 찾습니다.  

     `</Entity>`  

     `</Entities>`  

     `</SemanticModel>`  

8.  *&lt;모델 이름\>***.dsv** 파일의 내용을 파일의 마지막 줄(**&lt;SemanticModel\>**) 바로 앞에 붙여넣습니다.  

9. *&lt;모델 이름\>***.smdl** 파일을 저장하고 닫습니다.  

10. *&lt;모델 이름\>***.smdl** 파일을 Configuration Manager 사이트 서버의 *%programfiles%*\Microsoft Configuration Manager\AdminConsole\XmlStorage\Other 폴더에 복사합니다.  

    > [!IMPORTANT]  
    >  보고서 모델 파일을 Configuration Manager 사이트 서버로 복사한 후 Configuration Manager 콘솔을 끝내고 다시 시작해야 **보고서 만들기 마법사**에서 보고서 모델을 사용할 수 있습니다.  

##  <a name="AdvancedReportModel"></a> SQL Server Reporting Services에서 고급 보고서 모델을 만드는 단계  
 다음 절차를 사용하면 사이트의 사용자가 Configuration Manager 데이터베이스의 여러 뷰에서 데이터를 기반으로 한 특정 모델 기반 보고서를 작성하는 데 사용할 수 있는 고급 보고서 모델을 만들 수 있습니다. 보고서 작성자에게 클라이언트 컴퓨터 및 이러한 컴퓨터에 설치된 운영 체제에 대한 정보를 나타내는 보고서 모델을 만듭니다. 이 정보는 Configuration Manager 데이터베이스의 다음 뷰에서 가져옵니다.  

-   **V_R_System**: 검색된 컴퓨터와 Configuration Manager 클라이언트에 대한 정보가 포함되어 있습니다.  

-   **V_GS_OPERATING_SYSTEM**: 클라이언트 컴퓨터에 설치된 운영 체제에 대한 정보가 포함되어 있습니다.  

 이전 뷰에서 선택한 항목이 지정된 이름으로 하나의 목록에 통합된 다음, 보고서 작성기에서 특정 보고서에 포함할 수 있도록 보고서 작성자에게 표시됩니다.  

 이러한 절차를 수행하는 컴퓨터에 SQL Server Business Intelligence Development Studio를 설치했는지, 그리고 이 컴퓨터에 보고 서비스 지점 서버에 대한 네트워크 연결이 있는지 확인합니다. SQL Server Business Intelligence Development Studio에 대한 자세한 내용은 SQL Server 설명서를 참조하십시오.  

#### <a name="to-create-the-report-model-project"></a>To create the report model project  

1.  바탕 화면에서 **시작**, **Microsoft SQL Server 2008**, **SQL Server Business Intelligence Development Studio**를 차례로 클릭합니다.  

2.  Microsoft Visual Studio에 **SQL Server Business Intelligence Development Studio** 가 열리면 **파일**, **새로 만들기**, **프로젝트**를 차례로 클릭합니다.  

3.  **새 프로젝트** 대화 상자의 **템플릿** 목록에서 **보고서 모델 프로젝트** 를 선택합니다.  

4.  **이름** 입력란에서 이 보고서 모델의 이름을 지정합니다. 예를 들어 **Advanced_Model**이라고 입력합니다.  

5.  보고서 모델 프로젝트를 만들려면 **확인**을 클릭합니다.  

6.  **솔루션 탐색기** 에 **Advanced_Model**솔루션이 표시됩니다.  

    > [!NOTE]  
    >  **솔루션 탐색기** 창이 표시되지 않는 경우 **보기**를 클릭한 다음 **솔루션 탐색기**를 클릭합니다.  

#### <a name="to-define-the-data-source-for-the-report-model"></a>보고서 모델의 데이터 원본을 정의하려면  

1.  **SQL Server Business Intelligence Development Studio** 의 **솔루션 탐색기**창에서 **데이터 원본** 을 마우스 오른쪽 단추로 클릭하여 **새 데이터 원본 추가**를 선택합니다.  

2.  **데이터 원본 마법사 시작** 페이지에서 **다음**을 클릭합니다.  

3.  **연결 정의 방법 선택** 페이지에서 **기존 연결 또는 새 연결을 사용하여 데이터 원본 만들기** 를 선택했는지 확인한 다음 **새로 만들기**를 클릭합니다.  

4.  **연결 관리자** 대화 상자에서 데이터 원본의 다음 연결 속성을 지정합니다.  

    -   **서버 이름**: Configuration Manager 사이트 데이터베이스 서버의 이름을 입력하거나 목록에서 선택합니다. 기본 인스턴스 대신 명명된 인스턴스로 작업하는 경우 &lt;*데이터베이스 서버*>\\&lt;*인스턴스 이름*>을 입력합니다.  

    -   **indows 인증 사용**을 선택합니다.  

    -   **데이터베이스 이름 선택 또는 입력** 목록에서 Configuration Manager 사이트 데이터베이스의 이름을 선택합니다.  

5.  데이터베이스 연결을 확인하려면 **연결 테스트**를 클릭합니다.  

6.  연결이 되면 **확인** 을 클릭하여 **연결 관리자** 대화 상자를 닫습니다. 연결되지 않으면 입력한 정보가 올바른지 확인한 다음 다시 **연결 테스트** 를 클릭합니다.  

7.  **연결 정의 방법 선택** 페이지에서 **기존 연결 또는 새 연결을 사용하여 데이터 원본 만들기** 를 선택했는지 확인한 다음 방금 지정한 데이터 원본이 **데이터 연결** 목록 상자에 선택되어 있는지 확인하고 **다음**을 클릭합니다.  

8.  **데이터 원본 이름**에서 데이터 원본의 이름을 지정한 후 **마침**을 클릭합니다. 예를 들어 **Advanced_Model**이라고 입력합니다.  

9. 이제 **데이터 원본** 노드 아래의 **솔루션 탐색기** 에 **Advanced_Model.ds** 라는 데이터 원본이 표시됩니다.  

    > [!NOTE]  
    >  기존 데이터 원본의 속성을 편집하려면 **솔루션 탐색기** 창의 **데이터 원본** 폴더에서 데이터 원본을 두 번 클릭하여 데이터 원본 디자이너에 데이터 원본 속성을 표시합니다.  

#### <a name="to-define-the-data-source-view-for-the-report-model"></a>보고서 모델의 데이터 원본 뷰를 정의하려면  

1.  **솔루션 탐색기**에서 **데이터 원본 뷰** 를 마우스 오른쪽 단추로 클릭하여 **새 데이터 원본 뷰 추가**를 선택합니다.  

2.  **데이터 원본 뷰 마법사 시작** 페이지에서 **다음**을 클릭합니다. **데이터 원본 선택** 페이지가 표시됩니다.  

3.  **관계형 데이터 원본** 창에서 **Advanced_Model** 데이터 원본을 선택했는지 확인하고 **다음**을 클릭합니다.  

4.  **테이블 및 뷰 선택** 페이지의 **사용 가능한 개체** 목록에서 보고서 모델에 사용할 다음 뷰를 선택합니다.  

    -   **v_R_System (dbo)**  

    -   **v_GS_OPERATING_SYSTEM (dbo)**  

     각 뷰를 선택한 후 **>** 를 클릭하여 **포함된 개체** 를 선택합니다.  

    > [!TIP]  
    >  **사용 가능한 개체** 목록에서 뷰를 찾으려면 목록 맨 위의 **이름** 제목을 클릭하여 개체를 사전순으로 정렬합니다.  

5.  **이름 일치** 대화 상자가 나타나면 기본 선택 항목을 적용한 후 **다음**을 클릭합니다.  

6.  필요한 개체를 선택한 경우 **다음**을 클릭한 후 데이터 원본 뷰의 이름을 지정합니다. 예를 들어 **Advanced_Model**이라고 입력합니다.  

7.  **마침**을 클릭합니다. **솔루션 탐색기** 의 **데이터 원본 뷰** 폴더에 **Advanced_Model.dsv**데이터 원본 뷰가 표시됩니다.  

#### <a name="to-define-relationships-in-the-data-source-view"></a>데이터 원본 뷰에서 관계를 정의하려면  

1.  **솔루션 탐색기**에서 **Advanced_Model.dsv** 를 두 번 클릭하여 디자인 창을 엽니다.  

2.  **v_R_System** 창의 제목 표시줄을 마우스 오른쪽 단추로 클릭하여 **테이블 바꾸기**를 선택한 다음 **새 명명된 쿼리**를 클릭합니다.  

3.  **명명된 쿼리 만들기** 대화 상자에서 **테이블 추가** 아이콘(일반적으로 리본의 마지막 아이콘)을 클릭합니다.  

4.  **테이블 추가** 대화 상자에서 **뷰** 탭을 클릭하고 목록에서 **V_GS_OPERATING_SYSTEM** 을 선택한 후 **추가**를 클릭합니다.  

5.  **닫기** 를 클릭하여 **테이블 추가** 대화 상자를 닫습니다.  

6.  **명명된 쿼리 만들기** 대화 상자에서 다음 정보를 지정합니다.  

    -   **이름** : 쿼리의 이름을 지정합니다. 예를 들어 **Advanced_Model**이라고 입력합니다.  

    -   **설명** : 쿼리의 설명을 지정합니다. 이 예에서는 **예제 보고 서비스 보고서 모델**이라고 입력합니다.  

7.  **v_R_System** 창의 개체 목록에서 보고서 모델에 표시할 항목을 다음 중에서 선택합니다.  

    -   **ResourceID**  

    -   **ResourceType**  

    -   **Active0**  

    -   **AD_Domain_Name0**  

    -   **AD_SiteName0**  

    -   **Client0**  

    -   **Client_Type0**  

    -   **Client_Version0**  

    -   **CPUType0**  

    -   **Hardware_ID0**  

    -   **User_Domain0**  

    -   **User_Name0**  

    -   **Netbios_Name0**  

    -   **Operating_System_Name_and0**  

8.  **v_GS_OPERATING_SYSTEM** 상자의 개체 목록에서 보고서 모델에 표시할 항목을 다음 중에서 선택합니다.  

    -   **ResourceID**  

    -   **Caption0**  

    -   **CountryCode0**  

    -   **CSDVersion0**  

    -   **Description0**  

    -   **InstallDate0**  

    -   **LastBootUpTime0**  

    -   **Locale0**  

    -   **Manufacturer0**  

    -   **Version0**  

    -   **WindowsDirectory0**  

9. 이러한 뷰의 개체를 보고서 작성자에게 하나의 목록으로 표시하려면 조인을 사용하여 두 테이블 또는 뷰 간의 관계를 지정해야 합니다. 두 뷰에 모두 표시되는 **ResourceID**개체를 사용하여 두 뷰를 조인할 수 있습니다.  

10. **v_R_System** 창에서 **ResourceID** 개체를 클릭한 상태로 유지하며 **v_GS_OPERATING_SYSTEM** 창으로 **ResourceID** 개체를 끌어 옵니다.  

11. **확인**을 클릭합니다.  

12. **Advanced_Model** 창이 **v_R_System** 창으로 바뀌고 **v_R_System** 및 **v_GS_OPERATING_SYSTEM** 뷰의 보고서 모델에 필요한 모든 개체가 포함됩니다. 이제 데이터 원본 뷰 디자이너에서 **v_GS_OPERATING_SYSTEM** 창을 삭제할 수 있습니다. **v_GS_OPERATING_SYSTEM** 창의 제목 표시줄을 마우스 오른쪽 단추로 클릭하여 **DSV에서 테이블 삭제**를 선택합니다. **개체 삭제** 대화 상자에서 **확인** 을 클릭하여 삭제를 확인합니다.  

13. **파일**을 클릭한 다음 **모두 저장**을 클릭합니다.  

#### <a name="to-create-the-report-model"></a>To create the report model  

1.  **솔루션 탐색기**에서 **보고서 모델** 을 마우스 오른쪽 단추로 클릭하여 **새 보고서 모델 추가**를 선택합니다.  

2.  **보고서 모델 마법사 시작** 페이지에서 **다음**을 클릭합니다.  

3.  **데이터 원본 뷰 선택** 페이지의 **사용 가능한 데이터 원본 뷰** 목록에서 데이터 원본 뷰를 선택하고 **다음**을 클릭합니다. 이 예에서는 **Simple_Model.dsv**를 선택합니다.  

4.  **보고서 모델 생성 규칙을 선택하십시오.** 페이지에서 기본값을 그대로 두고 **다음**을 클릭합니다.  

5.  **모델 통계 수집** 페이지에서 **모델을 생성하기 전에 모델 통계 업데이트** 가 선택되었는지 확인하고 **다음**을 클릭합니다.  

6.  **마법사 완료** 페이지에서 보고서 모델의 이름을 지정합니다. 이 예에서는 **Advanced_Model** 이 표시되는지 확인합니다.  

7.  마법사를 완료하고 보고서 모델을 만들려면 **실행**을 클릭합니다.  

8.  마법사를 끝내려면 **마침**을 클릭합니다.  

9. 디자인 창에 보고서 모델이 표시됩니다.  

#### <a name="to-modify-object-names-in-the-report-model"></a>보고서 모델에서 개체 이름을 수정하려면  

1.  **솔루션 탐색기**에서 보고서 모델을 마우스 오른쪽 단추로 클릭하여 **뷰 디자이너**를 선택합니다. 이 예에서는 **Advanced_Model.smdl**을 선택합니다.  

2.  보고서 모델 디자인 뷰에서 개체 이름을 마우스 오른쪽 단추로 클릭하여 **이름 바꾸기**를 선택합니다.  

3.  선택한 개체의 새 이름을 입력한 다음 Enter 키를 누릅니다. 예를 들어 **CSD_Version_0** 이라는 개체 이름을 **Windows 서비스 팩 버전**으로 바꿀 수 있습니다.  

4.  개체 이름을 바꿨으면 **파일**을 클릭한 다음 **모두 저장**을 클릭합니다.  

#### <a name="to-publish-the-report-model-for-use-in-sql-server-reporting-services"></a>SQL Server Reporting Services에서 사용할 보고서 모델을 게시하려면  

1.  **솔루션 탐색기**에서 **Advanced_Model.smdl** 을 마우스 오른쪽 단추로 클릭하여 **배포**를 선택합니다.  

2.  **SQL Server Business Intelligence Development Studio** 창의 왼쪽 아래에서 배포 상태를 검토합니다. 배포가 완료되면 **배포했습니다.** 가 표시됩니다. 배포하지 못한 경우 **출력** 창에 실패 원인이 표시됩니다. 이제 SQL Server Reporting Services 웹 사이트에서 새 보고서 모델을 사용할 수 있습니다.  

3.  **파일**, **모두 저장**을 차례로 클릭한 다음 **SQL Server Business Intelligence Development Studio**를 닫습니다.  

#### <a name="to-deploy-the-custom-report-model-to-configuration-manager"></a>To deploy the custom report model to Configuration Manager  

1.  보고서 모델 프로젝트를 만든 폴더로 이동합니다. 예: %*USERPROFILE*%\Documents\Visual Studio 2008\Projects\\*&lt;프로젝트 이름\>.*  

2.  보고서 모델 프로젝트 폴더에서 컴퓨터의 임시 폴더로 다음 파일을 복사합니다.  

    -   *&lt;모델 이름\>* **.dsv**  

    -   *&lt;모델 이름\>* **.smdl**  

3.  텍스트 편집기(예: 메모장)를 사용하여 이전 파일을 엽니다.  

4.  *&lt;모델 이름\>***.dsv** 파일에서 다음과 같이 표시된 파일의 첫 줄을 찾습니다.  

     **&lt;DataSourceView xmlns="http://schemas.microsoft.com/analysisservices/2003/engine"\>**  

     이 줄을 다음과 같이 편집합니다.  

     **&lt;DataSourceView xmlns="http://schemas.microsoft.com/analysisservices/2003/engine" xmlns:xsi="RelationalDataSourceView"\>**  

5.  파일 내용 전체를 Windows 클립보드에 복사합니다.  

6.  *&lt;모델 이름\>***.dsv** 파일을 닫습니다.  

7.  *&lt;모델 이름\>***.smdl** 파일에서 다음과 같이 표시된 파일의 마지막 세 줄을 찾습니다.  

     `</Entity>`  

     `</Entities>`  

     `</SemanticModel>`  

8.  *&lt;모델 이름\>***.dsv** 파일의 내용을 파일의 마지막 줄(**&lt;SemanticModel\>**) 바로 앞에 붙여넣습니다.  

9. *&lt;모델 이름\>***.smdl** 파일을 저장하고 닫습니다.  

10. *&lt;모델 이름\>***.smdl** 파일을 Configuration Manager 사이트 서버의 *%programfiles%*\Microsoft Configuration Manager\AdminConsole\XmlStorage\Other 폴더에 복사합니다.  

    > [!IMPORTANT]  
    >  보고서 모델 파일을 Configuration Manager 사이트 서버로 복사한 후 Configuration Manager 콘솔을 끝내고 다시 시작해야 **보고서 만들기 마법사**에서 보고서 모델을 사용할 수 있습니다.  
