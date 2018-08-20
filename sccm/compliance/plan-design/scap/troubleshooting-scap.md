---
title: SCAP 문제 해결
titleSuffix: Configuration Manager
description: Configuration Manager용 SCAP 확장 문제 해결 방법을 알아봅니다.
ms.date: 07/30/2018
ms.prod: configuration-manager
ms.technology: configmgr-compliance
ms.topic: conceptual
ms.assetid: 27261853-1641-4826-98c6-afbb73a1209d
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: bb3bcd0e7301ff2ef7baeff29de038cbd8476525
ms.sourcegitcommit: 1826664216c61691292ea2a79e836b11e1e8a118
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/31/2018
ms.locfileid: "39383282"
---
# <a name="troubleshoot-the-scap-extensions-for-configuration-manager"></a>Configuration Manager용 SCAP 확장 문제 해결

*적용 대상: System Center Configuration Manager(현재 분기)*

Configuration Manager용 SCAP 확장은 USGCB를 지원하는 ACS 기능이 포함된 SCAP 검증 도구용 SCAP 데이터 스트림에 사용하기 위한 확장입니다. 일반적으로 NIST 웹 사이트에서 다운로드한 이와 같은 USGCB SCAP 데이터 스트림에서는 문제가 발생하지 않습니다.

다음 방법을 사용하여 문제를 진단하고 해결합니다.  

- 모든 대상 컴퓨터에 SCAP 확장 클라이언트(scmdcm.msi) 구성 요소가 설치되어 있는지 확인합니다.  

- Microsoft.Sces.ScapToDcm.exe 도구의 로그 파일 출력을 검토합니다.  

- SCAP 확장 사용 시 일반적으로 발생하는 문제와 해결 방법을 검토합니다.  

- Microsoft에 SCAP 확장 관련 질문을 하거나 의견을 보냅니다.



## <a name="review-microsoftscesscaptodcmexe-log"></a>Microsoft.Sces.ScapToDcm.exe 로그 검토

Microsoft.Sces.ScapToDcm.exe 도구는 `–log` 매개 변수가 지정된 경우 사용자 지정 이름이 지정된 로그 파일을 생성합니다. 이 로그 파일에는 Microsoft.Sces.ScapToDcm.exe 도구를 실행한 결과에 대한 정보가 있습니다. 예를 들어 Microsoft.Sces.ScapToDcm.exe 도구를 실행하는 동안 삭제되었거나 건너뛴 XCCDF/DataStream 입력 파일의 항목 수가 있습니다.

다음 표에는 로그 파일에 표시되는 일부 정보와 각 정보 유형의 설명이 나와 있습니다.

### <a name="information-found-in-the-microsoftscesscaptodcmexe-log-file"></a>Microsoft.Sces.ScapToDcm.exe 로그 파일에 있는 정보

| 정보 | 설명 |
| --- | --- |
| **삭제** | 테스트 유형이 지원되지 않으면 항목이 삭제될 수 있습니다. |
| **건너뛰기** | OVAL 정의 ID가 잘못된 플랫폼용입니다. </br> </br> OVAL 정의 ID가 XCCDF/DataStream 입력 파일에서 참조되지 않습니다.</br> </br> OVAL 테스트 ID가 XCCDF/DataStream 입력 파일에서 참조되지 않습니다. </br> </br> XCCDF 프로필 ID가 1과 같은 `@select` 명령문을 포함하지 않습니다. </br> </br> XCCDF 프로필 ID가 값이 true인 추상 특성을 포함합니다. </br> </br> XCCDF 프로필 ID가 적격 규칙을 포함하지 않습니다.|



## <a name="common-problems-and-solutions"></a>일반적인 문제 및 솔루션

문제 해결 시 참조할 수 있는 일반적으로 발생하는 몇 가지 문제와 해결 방법을 소개합니다.

- 기준의 상태가 **오류** 또는 **알 수 없음**으로 표시되며 Internet Explorer에서 보고서를 정상적으로 표시할 수 없습니다. 브라우저 오류는 "보고서가 비어 있거나 올바르지 않음"입니다.  

     - 기준을 다시 실행합니다. 기준을 선택하고 **평가**를 클릭합니다. 그런 다음, **준수 상태**/**마지막 평가 업데이트**를 모니터링합니다. 평가가 완료되어 마지막 평가 날짜가 현재 날짜/시간으로 업데이트되고 나면 기준을 선택하고 보고서를 다시 확인합니다.  

     - 그래도 Internet Explorer에서 보고서를 확인할 수 없으면 기준이 너무 큰 것일 수 있습니다. 더 작은 일괄 처리 크기를 사용하여 콘텐츠를 다시 생성해 더 작은 자식 기준을 만듭니다.  

     - 부모 기준에서 이 문제가 발생하는 경우에는 자식 기준을 대신 배포해 봅니다.  

- 지정된 USGCB 설정이 포함된 그룹 정책 개체(GPO)를 만들었습니다. Windows 7을 실행하는 컴퓨터가 포함된 조직 구성 단위(OU)에 연결했습니다. 규정 준수 보고서에는 일부 설정이 올바르게 구성되어 있지 않은 것으로 나타납니다.  

     - 그룹 정책 권한이 잘못되었거나 올바른 OU에 연결되지 않았을 수 있습니다.  

     - 새 설정이 아직 적용되지 않았을 가능성이 더 큽니다. 기본적으로 Active Directory 클라이언트는 그룹 정책에 대한 업데이트를 90분마다 확인합니다. 이 사이클은 정책을 올바르게 구성했더라도 설정이 적용된 것으로 표시되지 않은 이유일 수 있으며,  

     - 많은 컴퓨터 설정이 컴퓨터를 다시 시작해야 적용됩니다. 예를 들어 **시스템 암호화: 암호화, 해시, 서명에 FIPS 호환 알고리즘 사용** 설정은 컴퓨터를 다시 시작해야 Windows에서 지정된 암호화 알고리즘을 사용할 수 있습니다. 관리자 권한으로 명령 프롬프트에서 다음 명령을 입력하여 그룹 정책 새로 고침 간격을 무시할 수 있습니다. `gpupdate /force` 그룹 정책 새로 고침이 완료되면 컴퓨터를 다시 시작하여 모든 설정을 적용합니다. 자세한 내용은 [그룹 정책 업데이트 유틸리티에 대한 설명](https://support.microsoft.com/help/298444)을 참조하세요.

- 데이터베이스 연결에 조직 정보를 제공하는 데 문제가 있습니다.  

     - 데이터베이스 연결을 구성하는 방법에 대한 자세한 내용은 [SCAP 설치 및 구성](/sccm/compliance/plan-design/scap/install-configure-scap)을 참조하세요.  
