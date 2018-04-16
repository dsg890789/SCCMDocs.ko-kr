---
title: SCAP 문제 해결
titleSuffix: System Center Configuration Manager
description: SCAP 준수 설정을 구성 기준으로 가져와서 결과 내보내기
ms.custom: na
ms.date: 03/27/2018
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 27261853-1641-4826-98c6-afbb73a1209d
caps.latest.revision: 1
caps.handback.revision: 0
author: mestew
ms.author: mstewart
manager: dougeby
robots: noindex,nofollow
ms.openlocfilehash: 8270db5f0a43f1c94c876bdbd59e45ee2ca85ac6
ms.sourcegitcommit: 27da4be015f1496b7b89ebddb517a2685f1ecf74
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/28/2018
---
# <a name="troubleshoot-the-scap-extensions-for-microsoft-system-center-configuration-manager"></a>Microsoft System Center Configuration Manager용 SCAP 확장 문제 해결

*적용 대상: System Center Configuration Manager(현재 분기)*

> [!Tip]  
> 이 기능은 기술 미리 보기 버전 1803에서 [시험판 기능](/sccm/core/servers/manage/pre-release-features)으로 처음 도입되었습니다. SCAP 확장의 이 시험판 버전은 현재 지원되는 모든 버전의 Configuration Manager 현재 분기 및 LTSB 1606에 설치할 수 있습니다. 설치 파일은 1803 미리 보기부터 cd.latest\SMSSETUP\TOOLS\ConfigMgrSCAPExtension\ConfigMgrExtensionsForSCAP.msi에 있습니다. 

Microsoft System Center Configuration Manager용 SCAP 확장은 USGCB를 지원하는 ACS 기능이 포함된 SCAP 검증 도구용 SCAP 데이터 스트림에 사용하기 위한 확장입니다. 일반적으로 NIST 웹 사이트에서 다운로드한 이와 같은 USGCB SCAP 데이터 스트림에서는 문제가 발생하지 않습니다.

그러나 다음 방법을 사용하여 발생할 수 있는 문제를 진단하고 해결할 수 있습니다.

- 모든 대상 컴퓨터에 SCAP 확장 클라이언트(scmdcm.msi) 구성 요소가 설치되어 있는지 확인합니다.
- Microsoft.Sces.ScapToDcm.exe 도구의 로그 파일 출력을 검토합니다.
- SCAP 확장 사용 시 일반적으로 발생하는 문제와 해결 방법을 검토합니다.
- Microsoft에 SCAP 확장 관련 질문을 하거나 의견을 보냅니다.



## <a name="review-microsoftscesscaptodcmexe-tool-log"></a>Microsoft.Sces.ScapToDcm.exe 도구 로그 검토

Microsoft.Sces.ScapToDcm.exe 도구는 -log 매개 변수가 지정된 경우 사용자 지정 이름이 지정된 로그 파일을 생성합니다. 이 로그 파일에는 Microsoft.Sces.ScapToDcm.exe 도구를 실행한 결과에 대한 정보가 있습니다. 예를 들어 로그 파일에는 Microsoft.Sces.ScapToDcm.exe 도구를 실행하는 동안 삭제되었거나 건너뛴 XCCDF/DataStream 입력 파일의 항목 수가 있습니다.

다음 표에는 로그 파일에 표시되는 일부 정보와 각 정보 유형의 설명이 나와 있습니다.

### <a name="description-of-information-found-in-microsoftscesscaptodcmexe-log-files"></a>Microsoft.Sces.ScapToDcm.exe 로그 파일에 있는 정보에 대한 설명

| 정보 | 설명 |
| --- | --- |
| 삭제 | 테스트 유형이 지원되지 않으면 항목이 삭제될 수 있습니다. |
| Skip |OVAL 정의 ID가 잘못된 플랫폼용입니다. </br> </br> OVAL 정의 ID가 XCCDF/DataStream 입력 파일에서 참조되지 않습니다.</br> </br> OVAL 테스트 ID가 XCCDF/DataStream 입력 파일에서 참조되지 않습니다. </br> </br> XCCDF 프로필 ID에 1과 같은 @select 문을 포함하지 않습니다. </br> </br> XCCDF 프로필 ID가 값이 true인 추상 특성을 포함합니다. </br> </br> XCCDF 프로필 ID가 적격 규칙을 포함하지 않습니다.|

## <a name="common-problems-and-solutions"></a>일반적인 문제 및 솔루션

다음 표에는 문제 해결 시 참조할 수 있는 일반적으로 발생하는 몇 가지 문제와 해결 방법이 나와 있습니다.

표 1.6 일반적인 문제 및 솔루션

| 문제 | 가능한 해결 방법 |
| --- | --- |
| 기준의 상태가 **오류** 또는 **알 수 없음**으로 표시되면 IE에서 보고서를 정상적으로 표시할 수 없습니다. IE에서 &quot;보고서가 비어 있거나 올바르지 않음&quot;을 표시 | 기준을 선택하고 **평가**를 클릭하여 기준을 다시 실행한 후 기다렸다가 **준수 상태**/**마지막 평가 업데이트**를 모니터링합니다. 평가가 완료되어 마지막 평가 날짜가 현재 날짜/시간으로 업데이트되고 나면 기준을 선택하고 보고서를 다시 확인합니다. 그래도 IE에서 보고서를 확인할 수 없으면 기준이 너무 큰 것일 수 있습니다. 더 작은 일괄 처리 크기를 사용하여 콘텐츠를 다시 생성해 더 작은 자식 기준을 만듭니다. 부모 기준에서 이 문제가 발생하는 경우에는 자식 기준을 대신 배포해 봅니다. |
| 지정된 USGCB 설정을 포함하는 GPO(그룹 정책 개체)를 만들어 Windows 7을 실행하는 컴퓨터가 포함된 OU(조직 구성 단위)에 연결했는데 호환성 보고서에 일부 설정이 올바르게 구성되지 않았다는 메시지가 표시됩니다. | 그룹 정책 권한이 잘못되었거나 올바른 OU에 연결되지 않았을 수 있습니다. 그러나 새 설정이 아직 적용되지 않았을 가능성이 더 큽니다. 기본적으로 Active Directory 도메인에 속하는 클라이언트 컴퓨터의 그룹 정책은 90분마다 그룹 정책의 업데이트를 확인합니다. 따라서 정책을 올바르게 구성했더라도 설정이 적용된 것으로 표시되지 않을 수 있습니다. 또한 대부분의 컴퓨터 설정은 컴퓨터를 다시 시작해야 적용됩니다. 예를 들어 **시스템 암호화라는 설정은 암호화, 해시, 서명에 FIPS 호환 알고리즘을 사용하려는 경우 컴퓨터를 다시 시작해야 Windows에서 지정된 암호화 알고리즘을 사용할 수 있습니다. 관리자 권한으로 명령 프롬프트에 gpupdate /force 명령을 입력하여 그룹 정책 새로 고침 간격을 무시할 수 있습니다. 그룹 정책 새로 고침이 완료되면 컴퓨터를 다시 시작하여 모든 설정이 적용되도록 합니다. 자세한 내용은 기술 자료 아티클 298444 [그룹 정책 업데이트 유틸리티에 대한 설명](http://support.microsoft.com/kb/298444)을 참조하세요. |
| 데이터베이스 연결에 조직 정보를 제공하는 데 문제가 있습니다. | 데이터베이스 연결 정보를 구성하는 방법에 대한 절차 정보는 [SCAP 설치 및 구성](/sccm/compliance/plan-design/scap/install-configure-scap) 아티클을 참조하세요. 

## <a name="next-step"></a>다음 단계
> [!div class="nextstepaction"]
> [SCAP 확장 설치 및 구성](/sccm/compliance/plan-design/scap/install-configure-scap)