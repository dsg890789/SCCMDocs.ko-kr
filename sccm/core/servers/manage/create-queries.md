---
title: "쿼리 만들기 | Microsoft 문서"
description: "System Center Configuration Manager에서 쿼리를 만들고 가져오는 방법을 알아봅니다. 예제 쿼리 및 팁이 포함되어 있습니다."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 868049d3-3209-47ec-b34a-9cc26941893a
caps.latest.revision: 5
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Human Translation
ms.sourcegitcommit: 2087badc9dd1d216352dce232b145a786783ac89
ms.openlocfilehash: 9f38d86ff6227bb6ea88c358a3d61242372d449e
ms.contentlocale: ko-kr
ms.lasthandoff: 05/18/2017


---
# <a name="how-to-create-queries-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 쿼리를 만드는 방법

*적용 대상: System Center Configuration Manager(현재 분기)*

이 항목을 사용하여 System Center Configuration Manager에서 쿼리를 만들거나 가져오는 데 도움을 얻을 수 있습니다.  

##  <a name="BKMK_Create"></a> 쿼리를 만드는 방법  
 이 절차를 사용하여 Configuration Manager에서 쿼리를 만듭니다.  

#### <a name="to-create-a-query"></a>쿼리를 만들려면  

1.  Configuration Manager 콘솔에서 **모니터링**을 선택합니다.  

2.  **모니터링** 작업 영역에서 **쿼리**를 선택합니다. 그런 후 **홈** 탭의 **만들기** 그룹에서 **쿼리 만들기**를 선택합니다.  

3.  **쿼리 만들기 마법사** 의 **일반**탭에서 쿼리에 대한 고유한 이름과 설명(옵션)을 지정합니다.  

4.  새 쿼리의 기준으로 사용할 기존 쿼리를 가져오려면 **쿼리 문 가져오기**를 선택합니다. **쿼리 찾아보기** 대화 상자에서 가져올 기존 쿼리를 선택하고 **확인**을 선택합니다.  

5.  **개체 형식** 목록에서 쿼리가 반환할 개체 형식을 선택합니다. 다음 표는 검색할 수 있는 개체 형식의 몇 가지 예제를 설명합니다.  

    |개체 형식|설명|  
    |-----------------|-----------------|  
    |**시스템 리소스**|장치의 NetBIOS 이름, 클라이언트 버전, 클라이언트 IP 주소 및 Active Directory Domain Services 정보와 같은 일반적인 시스템 특성을 검색하려면 사용합니다.|  
    |**사용자 리소스**|사용자 이름, 사용자 그룹 이름 및 보안 그룹 이름과 같은 일반적인 사용자 정보를 검색하려면 사용합니다.|  
    |**배포**|배포 이름, 일정 및 배포된 컬렉션과 같은 배포의 일반적인 특성을 검색하려면 사용합니다.|  

6.  **쿼리 문 편집**을 선택하여 *&lt;쿼리 이름\>* **문 속성** 대화 상자를 엽니다.  

7.  *&lt;쿼리 이름\>* **문 속성** 대화 상자의 **일반** 탭에서 이 쿼리가 반환되는 특성 및 표시되는 방식을 지정합니다. 새 특성을 추가하려면 **새로 만들기** 아이콘을 선택합니다. WQL(WMI Query Language)에서 쿼리를 직접 입력 또는 편집하려면 **쿼리 언어 표시**를 선택할 수도 있습니다. WMI 쿼리의 예제를 보려면 이 항목의 [Example WQL queries](#BKMK_Example) 섹션을 참조하세요.  

    > [!TIP]  
    > 다음 MSDN 참조 설명서를 사용하여 사용자 고유의 WQL 쿼리를 작성할 수 있습니다.  
    >   
    > -   [WQL(WMI의 경우 SQL)](http://go.microsoft.com/fwlink/p/?LinkId=256653)  
    > -   [WHERE 절](http://go.microsoft.com/fwlink/p/?LinkId=256654)  
    > -   [WQL 연산자](http://go.microsoft.com/fwlink/p/?LinkId=256655)  

8.  *&lt;쿼리 이름\>* **문 속성** 대화 상자의 **조건** 탭에서 쿼리의 결과를 구체화하는 데 사용되는 조건을 지정합니다. 예를 들어 쿼리 결과에 **XYZ** 사이트 코드를 갖는 리소스만 반환할 수 있습니다. 쿼리에 대한 여러 조건을 구성할 수 있습니다.  

    > [!IMPORTANT]  
    > 조건 없는 쿼리를 만들면 쿼리가 **모든 시스템** 컬렉션의 모든 장치를 반환합니다.  

9. *&lt;쿼리 이름\>* **문 속성** 대화 상자의 **조인** 탭에서 두 개의 서로 다른 특성의 데이터를 쿼리 결과에 결합할 수 있습니다. 쿼리 결과에 대해 서로 다른 특성을 선택하면 Configuration Manager가 자동으로 쿼리 조인을 만들지만 **조인** 탭에서 고급 옵션을 제공합니다. System Center 2012 Configuration Manager가 지원하는 특성 클래스가 다음 표에 나와 있습니다.  

    |조인 유형|설명|  
    |---------------|-----------------|  
    |내부|일치하는 결과만 표시 - 자동으로 생성되는 조인에서 항상 사용합니다.|  
    |왼쪽|기본 특성에 대한 모든 결과와 조인 특성에 대해 일치하는 결과만 표시합니다.|  
    |오른쪽|조인 특성에 대한 모든 결과와 기본 특성에 대해 일치하는 결과만 표시합니다.|  
    |전체|기본 특성과 조인 특성 양쪽에 대해 모든 결과를 표시합니다.|  

     조인 작업을 사용하는 방법에 대한 자세한 내용은 SQL Server 설명서를 참조하세요.  

10. *&lt;쿼리 이름\>* **문 속성** 대화 상자를 닫으려면 **확인**을 클릭합니다.  

11. **쿼리 만들기 마법사** 의 **일반**탭에서 이 쿼리의 결과가 컬렉션의 멤버로 제한되지 않는지, 지정된 컬렉션의 멤버로 제한되는지, 쿼리를 실행할 때마다 컬렉션을 확인할지 여부를 지정합니다.  

12. 쿼리 만들기 마법사를 완료합니다. **모니터링** 작업 영역의 **쿼리** 노드에 새 쿼리가 표시됩니다.  

##  <a name="BKMK_Import"></a> 쿼리를 가져오는 방법  
 이 절차를 사용하여 쿼리를 Configuration Manager로 가져올 수 있습니다. 쿼리를 내보내는 방법에 대한 자세한 내용은 [System Center Configuration Manager에서 쿼리를 관리하는 방법](../../../core/servers/manage/manage-queries.md)을 참조하세요.  

#### <a name="to-import-a-query"></a>쿼리를 가져오려면  

1.  Configuration Manager 콘솔에서 **모니터링**을 선택합니다.  

2.  **모니터링** 작업 영역에서 **쿼리**를 선택합니다. **홈** 탭의 **만들기** 그룹에서 **개체 가져오기**를 선택합니다.  

3.  **개체 가져오기 마법사** 의 **MOF 파일 이름**페이지에서 **찾아보기**를 선택하여 가져올 쿼리가 포함된 MOF(Managed Object Format) 파일을 선택합니다.  

4.  가져올 쿼리에 대한 정보를 검토한 다음 마법사를 완료합니다. **모니터링** 작업 영역의 **쿼리** 노드에 새 쿼리가 표시됩니다.  

##  <a name="BKMK_Example"></a> Example WQL queries

이 섹션에서는 계층에서 사용하거나 다른 용도로 수정할 수 있는 WMI 쿼리 예제를 설명합니다. 이러한 쿼리를 사용하려면 **쿼리 문 속성** 대화 상자에서 **쿼리 언어 표시**를 선택합니다. 그런 다음 쿼리를 복사한 후 **쿼리 문** 필드에 붙여 넣습니다.  

> [!TIP]  
> 문자열을 나타내려면 와일드카드 문자 `%`을 사용합니다. 예를 들어 `%Visio%`는 Microsoft Office Visio 2010을 반환합니다.  

### <a name="computers-that-run-windows-7"></a>Windows 7을 실행하는 컴퓨터

Windows 7을 실행하는 모든 컴퓨터의 NetBIOS 이름 및 운영 체제 버전을 반환하려면 다음 쿼리를 사용합니다.  

> [!TIP]  
> Windows Server 2008 R2를 실행하는 컴퓨터를 반환하려면 `%Workstation 6.1%`를 `%Server 6.1%`로 변경합니다.  

```  
select SMS_R_System.NetbiosName,  
SMS_R_System.OperatingSystemNameandVersion from    
SMS_R_System where   
SMS_R_System.OperatingSystemNameandVersion like "%Workstation 6.1%"  
```  

### <a name="computers-with-a-specific-software-package-installed"></a>특정 소프트웨어 패키지가 설치된 컴퓨터  

특정 소프트웨어 패키지가 설치된 모든 컴퓨터의 NetBIOS 이름 및 소프트웨어 패키지 이름을 반환하려면 다음 쿼리를 사용합니다. 이 예제는 Microsoft Visio 버전이 설치된 모든 컴퓨터를 표시합니다. `%Visio%`를 쿼리할 소프트웨어 패키지로 바꿉니다.  

> [!TIP]  
> 이 쿼리는 Windows 제어판의 프로그램 목록에 표시되는 이름을 사용하여 소프트웨어 패키지를 검색합니다.  

```  
select SMS_R_System.NetbiosName,   
SMS_G_System_ADD_REMOVE_PROGRAMS.DisplayName from    
SMS_R_System inner join SMS_G_System_ADD_REMOVE_PROGRAMS on   
SMS_G_System_ADD_REMOVE_PROGRAMS.ResourceId =   
SMS_R_System.ResourceId where   
SMS_G_System_ADD_REMOVE_PROGRAMS.DisplayName like "%Visio%"  
```  

### <a name="computers-that-are-in-a-specific-active-directory-domain-services-organizational-unit"></a>특정 Active Directory Domain Services 조직 구성 단위에 있는 컴퓨터

지정된 OU(조직 구성 단위)에 있는 모든 컴퓨터의 NetBIOS 이름 및 OU 이름을 반환하려면 다음 쿼리를 사용합니다. `OU Name` 텍스트를 쿼리하려는 OU의 이름으로 바꿉니다.  

```  
select SMS_R_System.NetbiosName,   
SMS_R_System.SystemOUName from    
SMS_R_System where   
SMS_R_System.SystemOUName = "OU Name"  
```  

### <a name="computers-with-a-specific-netbios-name"></a>특정 NetBIOS 이름을 가진 컴퓨터

특정 문자열로 시작하는 모든 컴퓨터의 NetBIOS 이름을 반환하려면 다음 쿼리를 사용합니다. 이 예제에서 쿼리는 `ABC`로 시작하는 NetBIOS 이름이 있는 모든 컴퓨터를 반환합니다.  

```  
select SMS_R_System.NetbiosName from    
SMS_R_System where SMS_R_System.NetbiosName like "ABC%"  
```  

###  <a name="BKMK_DeviceType"></a> 특정 유형의 장치

장치 유형은 리소스 클래스 **sms_r_system** 및 특성 이름 **AgentEdition**의 Configuration Manager 데이터베이스에 저장됩니다. 지정하는 장치 유형의 에이전트 버전과 일치하는 장치만 검색하려면 다음 쿼리를 사용합니다.  

```  
Select SMS_R_System.ClientEdition from SMS_R_System where SMS_R_System.ClientEdition = <Device ID>  
```  

*&lt;장치 ID\>*에 대해 다음 값 중 하나를 사용합니다.  

|장치 유형|AgentEdition의 값|  
|-----------------|---------------------------|  
|Windows 데스크톱 또는 랩톱 컴퓨터|0|  
|Windows ARM 기반 장치(Windows RT 실행)|1|  
|Windows Mobile 6.5|2|  
|Nokia Symbian|3|  
|Windows Phone|4|  
|Mac 컴퓨터|5|  
|Windows CE|6|  
|Windows Embedded|7|  
|iOS|8|  
|iPad|9|  
|iPod Touch|10|  
|Android|11|  
|Intel System-on-a-Chip|12|  
|Unix 및 Linux 서버|13|  

 예를 들어 쿼리가 Mac 컴퓨터만 반환하도록 하려면 다음 쿼리를 사용합니다.  

```  
Select SMS_R_System.ClientEdition from SMS_R_System where SMS_R_System.ClientEdition = 5  
```  

## <a name="see-also"></a>참고 항목  
 [System Center Configuration Manager의 쿼리 작업 및 유지 관리](../../../core/servers/manage/operations-and-maintenance-for-queries.md)

