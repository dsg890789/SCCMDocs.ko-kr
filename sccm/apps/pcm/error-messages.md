---
title: 오류 메시지
titleSuffix: Configuration Manager
description: Package Conversion Manager의 오류 메시지에 대해 알아봅니다.
ms.date: 08/24/2018
ms.prod: configuration-manager
ms.technology: configmgr-app
ms.topic: conceptual
ms.assetid: 0d3cf6e1-b295-4b05-821d-e9f57c74ca14
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 62c4453cc383fa14eebf6e66c2582b878aaebae2
ms.sourcegitcommit: 759098de944b8f7d5eedfc2bae2cb9a6ba15276f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/30/2018
ms.locfileid: "43297198"
---
# <a name="technical-reference-for-package-conversion-manager-error-messages"></a>Package Conversion Manager 오류 메시지에 대한 기술 참조

*적용 대상: System Center Configuration Manager(현재 분기)*

<!--1357861-->

이 문서에서는 Package Conversion Manager에서 표시하는 오류 메시지에 대해 설명합니다. 오류의 가능한 원인과 오류를 수정하는 방법도 포함되어 있습니다. Package Conversion Manager는 **PCMTrace.log**에 오류 메시지를 기록합니다. 세부 정보 표시 수준을 제어하는 방법을 비롯한 자세한 내용은 [로그 파일](/sccm/apps/pcm/troubleshoot-pcm#log-files)을 참조하세요.


#### <a name="application-creation-failed-with-the-following-exception"></a>응용 프로그램 만들기가 실패했으며 다음 예외가 발생했습니다.

응용 프로그램 개체를 Configuration Manager 서버로 전송하는 동안 지정된 예외가 발생했습니다.

Configuration Manager에서 권한을 확인하고 연결 유효성을 검사한 후에 다시 시도합니다. 이렇게 해도 문제가 해결되지 않으면 **PCMtrace.log**(세부 정보 표시 수준 4) 및 **SMSProv.log** 파일을 점검합니다.


#### <a name="conversion-error--applies-to-a-package-transform-status"></a>변환 오류 – 패키지 변환 상태에 적용됩니다.

패키지를 변환하는 동안 일반 예외가 발생했습니다. **PCMtrace.log** 파일(세부 정보 표시 수준 4)을 확인하세요.

네트워크 공유(패키지 데이터 원본)에 대한 사용자 권한을 확인하고 연결 유효성을 검사한 후에 다시 시도합니다. 이렇게 해도 문제가 해결되지 않으면 **PCMtrace.log** 파일(세부 정보 표시 수준 4)을 점검합니다.


#### <a name="did-not-find-a-converted-package-and-its-resultant-application-in-the-workflow-outputs"></a>변환된 패키지 및 변환 결과로 생성된 응용 프로그램을 워크플로 출력에서 찾을 수 없습니다.
응용 프로그램(변환된 패키지/프로그램)이 삭제되었습니다.

종속 패키지/프로그램이 존재하도록 종속 패키지/프로그램을 수정합니다.


#### <a name="objects-were-not-created-successfully"></a>개체를 만들지 못했습니다.
다양한 원인이 있을 수 있습니다.

Configuration Manager에서 권한을 확인하고 연결 유효성을 검사한 후에 다시 시도합니다. 이렇게 해도 문제가 해결되지 않으면 **PCMtrace.log** 파일(세부 정보 표시 수준 4) 및 **SMSProv.log** 파일을 점검합니다.


#### <a name="please-close-the-wizard-and-resolve-any-issues-with-the-selected-package-see-pcmtracelog-for-more-details"></a>마법사를 닫고 선택한 패키지의 모든 문제를 해결하세요. 자세한 내용은 PCMTrace.Log를 참조하세요.
다양한 원인이 있을 수 있습니다.

Configuration Manager에서 권한을 확인하고 연결 유효성을 검사한 후에 다시 시도합니다. 이렇게 해도 문제가 해결되지 않으면 **PCMtrace.log** 파일(세부 정보 표시 수준 4) 및 **SMSProv.log** 파일을 점검합니다.


#### <a name="some-deployment-types-are-missing-detection-methods-all-deployment-types-must-have-detection-methods"></a>일부 배포 유형에 검색 방법이 없습니다. 모든 배포 유형에는 검색 방법이 있어야 합니다.
검색 방법이 프로그램에서 누락되었습니다.

**수정 및 변환** 프로세스 중에 검색 방법을 하나 이상 추가합니다.


#### <a name="there-was-an-error-preparing-the-package-for-conversion"></a>변환용 패키지를 준비하는 동안 오류가 발생했습니다.
다양한 원인이 있을 수 있습니다.

Configuration Manager에서 권한을 확인하고 연결 유효성을 검사한 후에 다시 시도합니다. 이렇게 해도 문제가 해결되지 않으면 **PCMtrace.log** 파일(세부 정보 표시 수준 4) 및 **SMSProv.log** 파일을 점검합니다.


