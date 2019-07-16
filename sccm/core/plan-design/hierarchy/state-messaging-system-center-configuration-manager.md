---
title: 상태 메시지
titleSuffix: Configuration Manager
description: 지원되는 Configuration Manager 버전의 상태 메시지에 대한 설명입니다.
ms.date: 02/26/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: f04c0a71-57bc-4443-a47c-592373050d04
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: a83a7100819718dc8bd5fa74f0e4a317b4b47e44
ms.sourcegitcommit: f9654cd1a3af6d67de52fedaccceb2e22dafc159
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67676729"
---
# <a name="state-messages-in-configuration-manager"></a>Configuration Manager의 상태 메시지 

*적용 대상: System Center Configuration Manager(현재 분기)*

상태 메시지에는 구성 관리자 클라이언트의 상태에 대한 간결한 정보가 포함되어 있습니다. 상태 메시징 시스템은 소프트웨어 업데이트 및 구성 설정과 같은 Configuration Manager의 특정 구성 요소에서 사용합니다.

구성 관리자 클라이언트는 대체 상태 지점 또는 관리 지점 사이트 시스템에 상태 메시지를 보내 작업의 현재 상태를 보고합니다. 보고서를 만들어 구성 관리자 클라이언트에서 보낸 상태 메시지를 볼 수 있습니다.

상태 메시지를 사용하는 각 Configuration Manager 기능은 상태 메시지 토픽 형식에 따라 식별됩니다. 이 문서에 나열된 상태 메시지 토픽 형식은 상태 메시지와 관련된 Configuration Manager 기능을 정의하는 데 사용할 수 있습니다.

> [!NOTE]  
> 일반적으로 상태 메시지 ID 값이 영(0)이면 토픽 형식이 알 수 없는 상태임을 나타냅니다.

## <a name="300-statetopictypesumassignmentcompliance"></a>300 STATE_TOPICTYPE_SUM_ASSIGNMENT_COMPLIANCE

|      상태 메시지 ID     |  상태 메시지 설명 |
|:-------------|:------|
| 0 | 준수 상태 알 수 없음|
| 1 | 규정 | 
| 2 | 비호환 | 

## <a name="301-statetopictypesumassignmentenforcement"></a>301 STATE_TOPICTYPE_SUM_ASSIGNMENT_ENFORCEMENT

|       상태 메시지 ID     |  상태 메시지 설명 |
|:-------------|:------|
| 0  | 적용 상태 알 수 없음 |
| 1  | 업데이트 설치 중        | 
| 2  | 다시 시작 대기 중          | 
| 3  | 다른 설치 작업이 완료될 때까지 대기 중         | 
| 4  | 업데이트가 성공적으로 설치됨          | 
| 5  | 시스템 다시 시작 보류 중         | 
| 6  | 업데이트를 설치하지 못함         | 
| 7  | 업데이트 다운로드 중   | 
| 8  | 업데이트 다운로드됨    | 
| 9  | 업데이트를 다운로드하지 못함     | 
| 10 | 설치 전 유지 관리 기간 대기 중         | 
| 11 | 오케스트레이션 대기 중         | 

## <a name="302-statetopictypesumassignmentevaluation"></a>302 STATE_TOPICTYPE_SUM_ASSIGNMENT_EVALUATION

|     상태 메시지 ID     |  상태 메시지 설명 |
|:-------------|:------|      
| 0 | 평가 상태 알 수 없음|                 
| 1 |평가 활성화됨      |
| 2 |평가 성공      |
| 3 |평가 실패      |


## <a name="400-statetopictypesumcidetection"></a>400 STATE_TOPICTYPE_SUM_CI_DETECTION

|     상태 메시지 ID     |  상태 메시지 설명 |
|:-------------|:------|
| 0 | 검색 상태 알 수 없음|
| 1 | 필요 없음   |
| 2 | 검색되지 않음    |
| 3 | 검색   |

## <a name="401-statetopictypesumcicompliance"></a>401 STATE_TOPICTYPE_SUM_CI_COMPLIANCE

|     상태 메시지 ID     |  상태 메시지 설명 |
|:-------------|:------|
| 0 | 준수 상태 알 수 없음|
| 1 |규정     |
| 2 |비호환     |
| 3 |충돌 검색됨    |
| 4 |오류      |
| 5 |알 수 없음     |
| 6 |부분 준수   |
| 7 |준수가 구성되지 않음    |

## <a name="402-statetopictypesumcienforcement"></a>402 STATE_TOPICTYPE_SUM_CI_ENFORCEMENT

|     상태 메시지 ID     |  상태 메시지 설명 |
|:-------------|:------|
| 0  | 적용 상태 알 수 없음|
| 1  |적용 시작됨          |
| 2  |적용에서 콘텐츠 대기 중         |
| 3  | 다른 설치 작업이 완료될 때까지 대기 중        |
| 4  |설치 전 유지 관리 기간 대기 중         |
| 5  |설치 전 다시 시작 필요         |
| 6  |일반 오류        |
| 7  |보류 중인 설치         |
| 8  |업데이트 설치 중          |
| 9  |시스템 다시 시작 보류 중        |
| 10 |업데이트가 성공적으로 설치됨         |
| 11 |업데이트를 설치하지 못함        |
| 12 |업데이트 다운로드 중        |
| 13 | 업데이트 다운로드됨        |
| 14 |업데이트를 다운로드하지 못함        |

## <a name="500-statetoptctypesumupdatedetection"></a>500 STATE_TOPTCTYPE_SUM_UPDATE_DETECTION

|     상태 메시지 ID     |  상태 메시지 설명 |
|:-------------|:------|
|0 |검색 상태 알 수 없음|
| 1 | 업데이트 필요 없음  |
| 2 | 업데이트 필요   |
| 3 | 업데이트 설치됨  |

## <a name="501-statetopictypesumupdatesourcescan"></a>501 STATE_TOPICTYPE_SUM_UPDATE_SOURCE_SCAN

|     상태 메시지 ID     |  상태 메시지 설명 |
|:-------------|:------|
| 0 |검사 상태 알 수 없음|
| 1 | 검사에서 콘텐츠 대기 중   |
| 2 | 검사 실행 중    |
| 3 | 검사 완료    |
| 4 | 검사 다시 시도 보류 중   |
| 5 | 검사 실패   |
| 6 | 검사가 완료되었지만 오류 발생 |

## <a name="700-statetopictyperesyncstatemsg"></a>700 STATE_TOPICTYPE_RESYNC_STATE_MSG

상태 ID가 없습니다.

## <a name="701-statetopictypesystemheartbeat"></a>701 STATE_TOPICTYPE_SYSTEM_HEARTBEAT

상태 ID가 없습니다.

## <a name="702-statetopictypeckdupdate"></a>702 STATE_TOPICTYPE_CKD_UPDATE
 
상태 ID가 없습니다.

## <a name="800-statetopictypeclientdeployment"></a>800 STATE_TOPICTYPE_CLIENT_DEPLOYMENT

|     상태 메시지 ID     |  상태 메시지 설명 |
|:-------------|:------|
| 100 |클라이언트 배포가 시작되었습니다.      |       
| 101 |다운로드 대기 중       |       
| 102 |배포가 예약됨       |       
| 103 | 배포 전 기간 대기 중 |
| 104 |배포를 건너뜀       |       
| 301 |알 수 없는 클라이언트 배포 오류 |       
| 302 |ccmsetup 서비스를 만들지 못함  |       
| 303 |ccmsetup 서비스를 삭제하지 못함 |       
| 304 |시스템 드라이브에 FBWF(파일 기반 쓰기 필터)가 설정된 경우 포함된 운영 체제에 설치할 수 없음 |       
| 305 |Windows 2000에서 기본 보안 모드가 유효하지 않음  |       
| 306 |ccmsetup 다운로드 프로세스를 시작하지 못했음  |       
| 307 |잘못된 ccmsetup 명령줄 |       
| 308 |주소에서 WINHTTP를 통해 파일을 다운로드하지 못함 |       
| 309 |주소에서 BITS를 통해 파일을 다운로드하지 못함 |       
| 310 |BITS 버전을 설치하지 못함 |       
| 311 |필수 구성 요소 파일의 MS 서명이 완료되었는지 확인할 수 없음  |       
| 312 |디스크가 가득 차서 파일을 복사하지 못함 |       
| 313 |Client.msi 설치에 실패하고 MSI 오류가 발생함 |       
| 314 |ccmsetup.xml 매니페스트 파일을 로드하지 못함 |       
| 315 |클라이언트 인증서를 가져오지 못함  |       
| 316 |필수 구성 요소 파일의 MS 서명이 완료 안 됨 |       
| 317 |설치를 계속하려면 다시 부팅 필요  |       
| 318 |MP 및 클라이언트 버전이 일치하지 않으므로 MP에서 클라이언트를 설치할 수 없음 |       
| 319 |운영 체제 또는 서비스 팩이 지원되지 않음  |       
| 320 |배포가 지원되지 않음       |       
| 321 |비트가 누락됨        |       
| 322 |원본 폴더를 사용할 수 없음       |       
| 323 |Appv가 지원되지 않음              |       
| 324 |잘못된 사이트 버전              |       
| 325 |필수 구성 요소 해시 불일치       |       
| 326 |MDM 등록을 취소하지 못함      |       
| 327 |MDM 등록이 검색됨      |       
| 328 |Intune이 검색됨       |       
| 329 |데이터 통신 연결 네트워크가 허용되지 않음      |       
| 400 |클라이언트 배포에 성공했습니다. |  
| 401 |배포에 성공했으며 다시 부팅이 필요함     |       
| 402 |배포에 성공했으며 다시 부팅에 성공함     |
| 500 |클라이언트 할당이 시작되었습니다.|
| 601 |알 수 없는 클라이언트 할당 오류|
| 602 |다음 사이트 코드가 잘못됨|
| 603 |MP에 할당하지 못함|
| 604 |기본 관리 지점을 검색하지 못함|
| 605 |사이트 서명 인증서를 다운로드하지 못함|
| 606 |사이트 코드를 자동으로 검색하지 못함|
| 607 |사이트를 할당하지 못함, 클라이언트 버전이 사이트 버전보다 높음|
| 608 |Active Directory Domain Services 및 SLP에서 사이트 버전을 가져오지 못함|
| 609 |클라이언트 버전을 가져오지 못함|
| 700 |클라이언트 할당이 성공했습니다.|

## <a name="801-statetopictypedeviceclientdeployment"></a>801 STATE_TOPICTYPE_DEVICE_CLIENT_DEPLOYMENT

상태 ID가 없습니다.

## <a name="810-statetopictypeclientcomanagement"></a>810 STATE_TOPICTYPE_CLIENT_COMANAGEMENT

|     상태 메시지 ID     |  상태 메시지 설명 |
|:-------------|:------|
| 100 | 등록 상태   |
| 101 | 등록이 예약됨   |
| 102 | 등록이 취소됨   |
| 105 | 등록이 시작됨   |
| 106 | 등록이 성공했으나 프로비전되지 않음
| 107 | 등록이 성공했으며 프로비전됨
| 108 | 등록에 활성 사용자가 없음   |
| 110 | 등록이 실패함   |


## <a name="820--statetopictypeclientwufb"></a>820 STATE_TOPICTYPE_CLIENT_WUFB

|     상태 메시지 ID     |  상태 메시지 설명 |
|:-------------|:------|
| 1 | 비즈니스용 Windows 업데이트 클라이언트 상태| 

## <a name="900-statetopictypebranchdp"></a>900 STATE_TOPICTYPE_BRANCH_DP

|     상태 메시지 ID     |  상태 메시지 설명 |
|:-------------|:------|
| 1 | 디스크 공간   | 

## <a name="901-statetopictyperemotedpmonitoring"></a>901 STATE_TOPICTYPE_REMOTE_DP_MONITORING

상태 ID가 없습니다.

## <a name="902-statetopictypepulldpmonitoring"></a>902 STATE_TOPICTYPE_PULL_DP_MONITORING

상태 ID가 없습니다.

## <a name="903-statetopictypedpusage"></a>903 STATE_TOPICTYPE_DP_USAGE

상태 ID가 없습니다.

## <a name="1000--statetopictypeclientframeworkcomm"></a>1000 STATE_TOPICTYPE_CLIENT_FRAMEWORK_COMM

|     상태 메시지 ID     |  상태 메시지 설명 |
|:-------------|:------|
| 1 | 클라이언트가 관리 지점과 성공적으로 통신함 |
| 2 | 클라이언트가 관리 지점과 통신하지 못함 |

## <a name="1001-statetopictypeclientframeworklocal"></a>1001 STATE_TOPICTYPE_CLIENT_FRAMEWORK_LOCAL

|     상태 메시지 ID     |  상태 메시지 설명 |
|:-------------|:------|
| 1 |클라이언트가 로컬 인증서 저장소에서 성공적으로 인증서를 검색함    |
| 2 |클라이언트가 로컬 인증서 저장소에서 인증서를 검색하지 못함 |

## <a name="1002-statetopictypedeviceclientframeworkcomm"></a>1002 STATE_TOPICTYPE_DEVICE_CLIENT_FRAMEWORK_COMM

상태 ID가 없습니다.

## <a name="1003-statetopictypedeviceclientframeworklocal"></a>1003 STATE_TOPICTYPE_DEVICE_CLIENT_FRAMEWORK_LOCAL

상태 ID가 없습니다.

## <a name="1004-statetopictypedeviceclientframeworkcertificate"></a>1004 STATE_TOPICTYPE_DEVICE_CLIENT_FRAMEWORK_CERTIFICATE

상태 ID가 없습니다.

## <a name="1005-statetopictypedeviceclientwipe"></a>1005 STATE_TOPICTYPE_DEVICE_CLIENT_WIPE

상태 ID가 없습니다.

## <a name="1006-statetopictypedeviceclientretire"></a>1006 STATE_TOPICTYPE_DEVICE_CLIENT_RETIRE

상태 ID가 없습니다.

## <a name="1007-statetopictypedeviceclientwipeintune"></a>1007 STATE_TOPICTYPE_DEVICE_CLIENT_WIPE_INTUNE

상태 ID가 없습니다.

## <a name="1008-statetopictypedeviceclientretireintune"></a>1008 STATE_TOPICTYPE_DEVICE_CLIENT_RETIRE_INTUNE

상태 ID가 없습니다.

## <a name="1009-statetopictypedeviceclientdevicelock"></a>1009 STATE_TOPICTYPE_DEVICE_CLIENT_DEVICELOCK

상태 ID가 없습니다.

## <a name="1010-statetopictypedeviceclientdevicelockintune"></a>1010 STATE_TOPICTYPE_DEVICE_CLIENT_DEVICELOCK_INTUNE

상태 ID가 없습니다.

## <a name="1011-statetopictypedeviceclientdevicepinreset"></a>1011 STATE_TOPICTYPE_DEVICE_CLIENT_DEVICEPINRESET

상태 ID가 없습니다.

## <a name="1012-statetopictypedeviceclientdevicepinresetintune"></a>1012 STATE_TOPICTYPE_DEVICE_CLIENT_DEVICEPINRESET_INTUNE

상태 ID가 없습니다.

## <a name="1013-statetopictypedeviceclientdevicepinresetonprem"></a>1013 STATE_TOPICTYPE_DEVICE_CLIENT_DEVICEPINRESET_ONPREM

상태 ID가 없습니다.

## <a name="1014-statetopictypedeviceclientdevicealbypass"></a>1014 STATE_TOPICTYPE_DEVICE_CLIENT_DEVICEALBYPASS

상태 ID가 없습니다.

## <a name="1015-statetopictypedeviceclientdevicealbypassintune"></a>1015 STATE_TOPICTYPE_DEVICE_CLIENT_DEVICEALBYPASS_INTUNE

상태 ID가 없습니다.

## <a name="1100-statetopictypeclientframeworkmodereadiness"></a>1100 STATE_TOPICTYPE_CLIENT_FRAMEWORK_MODEREADINESS

|     상태 메시지 ID     |  상태 메시지 설명 |
|:-------------|:------|
| 1 |클라이언트의 기본 모드가 준비 안 됨  |
| 2 |클라이언트의 기본 모드가 준비됨     |


## <a name="1300-statetopictypeclienthealth"></a>1300 STATE_TOPICTYPE_CLIENT_HEALTH

|     상태 메시지 ID     |  상태 메시지 설명 |
|:-------------|:------|
| 1 | 성공|
| 2 | 성공하지 못함 |

## <a name="1401-statetopictypestatereport"></a>1401 STATE_TOPICTYPE_STATE_REPORT

상태 ID가 없습니다.

## <a name="1500-statetopictypecaltrackut"></a>1500 STATE_TOPICTYPE_CAL_TRACK_UT

상태 ID가 없습니다.

## <a name="1502-statetopictypecaltrackmt"></a>1502 STATE_TOPICTYPE_CAL_TRACK_MT

상태 ID가 없습니다.

## <a name="1503-statetopictypecaltrackml"></a>1503 STATE_TOPICTYPE_CAL_TRACK_ML

상태 ID가 없습니다. 

## <a name="1600-statetopictypeuseraffinity"></a>1600 STATE_TOPICTYPE_USER_AFFINITY

|     상태 메시지 ID     |  상태 메시지 설명 |
|:-------------|:------|
| 1 |사용자 선호도가 설정됨       |
| 2 |사용자 선호도가 제거됨       |

## <a name="1700-statetopictypeappciscan"></a>1700 STATE_TOPICTYPE_APP_CI_SCAN

상태 ID가 없습니다.

## <a name="1701-statetopictypeappcicompliance"></a>1701 STATE_TOPICTYPE_APP_CI_COMPLIANCE

상태 ID가 없습니다.

## <a name="1702-statetopictypeappcienforcement"></a>1702 STATE_TOPICTYPE_APP_CI_ENFORCEMENT

|     상태 메시지 ID     |  상태 메시지 설명 |
|:-------------|:------|
| 1000  |성공한 구성 항목           |
| 1001 |성공한 구성 항목이 이미 설치됨         |
| 1002 |성공한 구성 항목이 실행 전임          |
| 1003 |성공한 구성 항목 빠른 상태          |
| 2000 |진행 중인 구성 항목           |
| 2001 |진행 중인 구성 항목이 콘텐츠 대기 중         |
| 2002 |진행 중인 구성 항목이 설치 중          |
| 2003 |진행 중인 구성 항목이 다시 부팅 대기 중         |
| 2004 |진행 중인 구성 항목이 유지 관리 기간 대기 중        |
| 2005 |진행 중인 대기 항목 일정 대기 중         |
| 2006 |진행 중인 구성 항목이 종속 콘텐츠 다운로드 중     |
| 2007 |진행 중인 구성 항목이 종속성 설치 중        |
| 2008 |진행 중인 구성 항목이 다시 부팅 보류 중         |
| 2009 |진행 중인 구성 항목이 콘텐츠를 다운로드함         |
| 2010 |진행 중인 구성 항목이 업데이트 보류 중         |
| 2011 |진행 중인 구성 항목이 사용자 다시 연결 대기 중        |
| 2012 |진행 중인 구성 항목이 사용자 로그아웃 대기 중         |
| 2013 |진행 중인 구성 항목이 사용자 로그인 대기 중         |
| 2014 |진행 중인 구성 항목이 설치 대기 중         |
| 2015 |진행 중인 구성 항목이 다시 시도 대기 중         |
| 2016 |진행 중인 구성 항목이 presmode 대기 중         |
| 2017 |진행 중인 구성 항목이 오케스트레이션 대기 중        |
| 2018 |진행 중인 구성 항목이 네트워크 대기 중         |
| 2019 |진행 중인 구성 항목이 VE 업데이트 보류 중         |
| 2020 |진행 중인 구성 항목이 VE 업데이트 중         |
| 3000 |구성 항목 요구 사항에 맞지 않음           |
| 3001 |구성 항목 요구 사항에 맞지 않아 호스트에 적용할 수 없음        |
| 4000 |구성 항목 알 수 없음           |
| 5000 |구성 항목 오류            |
| 5001 |구성 항목 오류 평가 중          |
| 5002 |구성 항목 오류 설치 중          |
| 5003 |구성 항목 오류 콘텐츠 검색 중         |
| 5004 |구성 항목 오류 종속성 설치 중         |
| 5005 |구성 항목 오류 콘텐츠 종속성 검색 중        |
| 5006 |구성 항목 오류 규칙 충돌          |
| 5007 |구성 항목 오류 다시 시도 대기 중          |
| 5008 |구성 항목 오류 대체 제거 중        |
| 5009 |구성 항목 오류 대체 다운로드 중         |
| 5010 |구성 항목 오류 VE 업데이트 중          |
| 5011 |구성 항목 오류 라이선스 설치 중         |
| 5012 |구성 항목 오류 검색에서 모든 신뢰할 수 있는 앱 허용       |
| 5013 |구성 항목 오류 사용 가능한 라이선스 없음         |
| 5014 |구성 항목 오류 OS가 지원되지 않음          |
| 6000 |구성 항목 시작이 성공함            |
| 6010 |구성 항목 시작 오류            |
| 6020 |구성 항목 시작 알 수 없음|

## <a name="1703-statetopictypeappciassignmentevaluatio"></a>1703 STATE_TOPICTYPE_APP_CI_ASSIGNMENT_EVALUATIO

상태 ID가 없습니다.

## <a name="1704-statetopictypeappcilaunch"></a>1704 STATE_TOPICTYPE_APP_CI_LAUNCH

상태 ID가 없습니다.

## <a name="1800-statetopictypeeventintrinsic"></a>1800 STATE_TOPICTYPE_EVENT_INTRINSIC

상태 ID가 없습니다.

## <a name="1801-statetopictypeeventextrinsic"></a>1801 STATE_TOPICTYPE_EVENT_EXTRINSIC

상태 ID가 없습니다.

## <a name="1900-statetopictypeepaminfection"></a>1900 STATE_TOPICTYPE_EP_AM_INFECTION

상태 ID가 없습니다.

## <a name="1901-statetopictypeepamhealth"></a>1901 State_Topictype_Ep_Am_Health

상태 ID가 없습니다.

## <a name="1902-statetopictypeepmalware"></a>1902 STATE_TOPICTYPE_EP_MALWARE

상태 ID가 없습니다.

## <a name="1950-statetopictypeatphealthstatus"></a>1950 STATE_TOPICTYPE_ATP_HEALTH_STATUS

상태 ID가 없습니다.

## <a name="2001-statetopictypeepclientdeployment"></a>2001 STATE_TOPICTYPE_EP_CLIENT_DEPLOYMENT

|     상태 메시지 ID     |  상태 메시지 설명 |
|:-------------|:------|
| 1 |Endpoint Protection이 관리되지 않음   |
| 2 |Endpoint Protection이 설치 대기 중  |
| 3 |Endpoint Protection이 관리됨   |
| 4 |Endpoint Protection 설치에 실패함  |
| 5 |Endpoint Protection 다시 부팅 보류 중  |
| 6 |Endpoint Protection이 지원되지 않음   |
| 7 |Endpoint Protection이 공동 관리됨   |

## <a name="2002-statetopictypeepclientpolicyapplication"></a>2002 STATE_TOPICTYPE_EP_CLIENT_POLICYAPPLICATION

|     상태 메시지 ID     |  상태 메시지 설명 |
|:-------------|:------|
| 0 |Endpoint Protection 정책 적용 상태를 알 수 없음    |
| 1 |Endpoint Protection 정책 적용이 성공함    |
| 2 |Endpoint Protection 정책 적용이 실패함    |

## <a name="2003-statetopictypeclientaction"></a>2003 STATE_TOPICTYPE_CLIENT_ACTION

|     상태 메시지 ID     |  상태 메시지 설명 |
|:-------------|:------|
| 0 |  알 수 없음    |
| 1 |  활성    |
| 2 |  비활성    |

## <a name="2100-statetopictypewpclientdeployment"></a>2100 STATE_TOPICTYPE_WP_CLIENT_DEPLOYMENT

|     상태 메시지 ID     |  상태 메시지 설명 |
|:-------------|:------|
| 1 | 절전 모드 해제 프록시가 설치되지 않음    |
| 2 | 절전 모드 해제 프록시가 설치 대기 중   |
| 3 | 절전 모드 해제 프록시가 설치됨    |
| 4 | 절전 모드 해제 프록시를 설치하지 못함   |
| 5 | 절전 모드 해제 프록시가 다시 부팅 대기 중   |
| 6 | 이 OS에서는 절전 모드 해제 프록시가 지원되지 않음  |
| 7 | 절전 모드 해제 프록시 서버가 옵트아웃됨   |
| 8 | 절전 모드 해제 프록시 제거가 실패함   |
| 9 | 절전 모드 해제 프록시 런타임이 지원되지 않음   |

## <a name="2200-statetopictypefdm"></a>2200 STATE_TOPICTYPE_FDM

상태 ID가 없습니다.

## <a name="2201-statetopictypeccmcertbinding"></a>2201 STATE_TOPICTYPE_CCM_CERT_BINDING

상태 ID가 없습니다.

## <a name="2202-statetopictypeserverstatistic"></a>2202 STATE_TOPICTYPE_SERVER_STATISTIC

상태 ID가 없습니다.

## <a name="3000-statetopictypedmwnschannel"></a>3000 STATE_TOPICTYPE_DM_WNS_CHANNEL

|     상태 메시지 ID     |  상태 메시지 설명 |
|:-------------|:------|
|0 | Windows 푸시 알림 서비스 채널이 설정됨|

## <a name="4000-statetopictypemdmdeviceproperty"></a>4000 STATE_TOPICTYPE_MDM_DEVICE_PROPERTY

상태 ID가 없습니다.

## <a name="4002-statetopictypemdmclientidenitity"></a>4002 STATE_TOPICTYPE_MDM_CLIENT_IDENITITY

상태 ID가 없습니다.

## <a name="4003-statetopictypemdmapplicationrequest"></a>4003 STATE_TOPICTYPE_MDM_APPLICATION_REQUEST

상태 ID가 없습니다.

## <a name="4004-statetopictypemdmapplicationstate"></a>4004 STATE_TOPICTYPE_MDM_APPLICATION_STATE

상태 ID가 없습니다.

## <a name="4005-statetopictypemdmlicensedevicerelation"></a>4005 STATE_TOPICTYPE_MDM_LICENSE_DEVICE_RELATION

상태 ID가 없습니다.

## <a name="4006-statetopictypemdmlicensekeys"></a>4006 STATE_TOPICTYPE_MDM_LICENSE_KEYS

상태 ID가 없습니다.

## <a name="4007-statetopictypemdmpolicyassignment"></a>4007 STATE_TOPICTYPE_MDM_POLICY_ASSIGNMENT

상태 ID가 없습니다.

## <a name="4008-statetopictypemdmandroidcount"></a>4008 STATE_TOPICTYPE_MDM_ANDROID_COUNT

상태 ID가 없습니다.

## <a name="4009-statetopictypemdmslkstatus"></a>4009 STATE_TOPICTYPE_MDM_SLK_STATUS

상태 ID가 없습니다.

## <a name="4010-statetopictypemdmusercompanytermacceptance"></a>4010 STATE_TOPICTYPE_MDM_USER_COMPANY_TERM_ACCEPTANCE

상태 ID가 없습니다.

## <a name="4022-statetopictypemdmdepsyncnowstatus"></a>4022 STATE_TOPICTYPE_MDM_DEP_SYNCNOW_STATUS

상태 ID가 없습니다.

## <a name="4023-statetopictypemdmmamstoreappsync"></a>4023 STATE_TOPICTYPE_MDM_MAM_STORE_APP_SYNC

상태 ID가 없습니다.

## <a name="5000-statetopictypecertificateenrollment"></a>5000 STATE_TOPICTYPE_CERTIFICATE_ENROLLMENT

|     상태 메시지 ID     |  상태 메시지 설명 |
|:-------------|:------|
| 1 |챌린지 발급됨         |
| 2 |챌린지 발급에 실패        |
| 3 |요청 만들기 실패        |
| 4 |요청 제출에 실패        |
| 5 |챌린지 유효성 검사에 성공       |
| 6 |챌린지 유효성 검사에 실패       |
| 7 |발급에 실패         |
| 8 |발급 보류 중         |
| 9 |발급됨          |
| 10 |응답 처리 실패       |
| 11 |응답 보류 중         |
| 12 |등록 성공         |
| 13 |등록이 필요하지 않음         |
| 14 |해지됨          |
| 15 |컬렉션에서 제거됨        |
| 16 |갱신이 확인됨         |
| 17 |설치 실패        |
| 18 |설치됨         |
| 19 |삭제 실패         |
| 20 |삭제됨         |
| 21 |갱신이 요청됨        |


## <a name="5001-statetopictypecertificatecrp"></a>5001 STATE_TOPICTYPE_CERTIFICATE_CRP

|     상태 메시지 ID     |  상태 메시지 설명 |
|:-------------|:------|
| 1 |챌린지 발급됨         |
| 2 |챌린지 발급에 실패        |
| 3 |요청 만들기 실패        |
| 4 |요청 제출에 실패        |
| 5 |챌린지 유효성 검사에 성공       |
| 6 |챌린지 유효성 검사에 실패       |
| 7 |발급에 실패         |
| 8 |발급 보류 중         |
| 9 |발급됨          |
| 10 |응답 처리 실패       |
| 11 |응답 보류 중         |
| 12 |등록 성공         |
| 13 |등록이 필요하지 않음         |
| 14 |해지됨          |
| 15 |컬렉션에서 제거됨        |
| 16 |갱신이 확인됨         |
| 17 |설치 실패        |
| 18 |설치됨         |
| 19 |삭제 실패         |
| 20 |삭제됨         |
| 21 |갱신이 요청됨        |

## <a name="5200-statetopictyperesourceaccessstatus"></a>5200 STATE_TOPICTYPE_RESOURCE_ACCESS_STATUS

|     상태 메시지 ID     |  상태 메시지 설명 |
|:-------------|:------|
| 1 | 상태 고정 설정 성공       |
| 2 | 상태 고정 설정 실패       |
| 3 | 상태 고정 설정 지원되지 않음      |
| 4 | 상태 고정 설정 진행 중      |

## <a name="6000-statetopictyperemoteappsubscriptionstatus"></a>6000 STATE_TOPICTYPE_REMOTEAPP_SUBSCRIPTION_STATUS

상태 ID가 없습니다.

## <a name="6001-statetopictyperemoteappsubscriptionsyncstatus"></a>6001 STATE_TOPICTYPE_REMOTEAPP_SUBSCRIPTION_SYNC_STATUS

상태 ID가 없습니다.

## <a name="6002-statetopictyperemoteappauthcookiessyncstatus"></a>6002 STATE_TOPICTYPE_REMOTEAPP_AUTHCOOKIES_SYNC_STATUS

상태 ID가 없습니다.

## <a name="6003-statetopictyperemoteapplicationssyncstatus"></a>6003 STATE_TOPICTYPE_REMOTEAPPLICATIONS_SYNC_STATUS

상태 ID가 없습니다.

## <a name="6004-statetopictyperemoteapplockresult"></a>6004 STATE_TOPICTYPE_REMOTEAPP_LOCK_RESULT

상태 ID가 없습니다.

## <a name="7000-statetopictypeusercompanytermacceptance"></a>7000 STATE_TOPICTYPE_USER_COMPANY_TERM_ACCEPTANCE

상태 ID가 없습니다.

## <a name="7001-statetopictypepfxcertificate"></a>7001 STATE_TOPICTYPE_PFX_CERTIFICATE

|     상태 메시지 ID     |  상태 메시지 설명 |
|:-------------|:------|
| 1 |챌린지 발급됨    |
| 2 |챌린지 발급에 실패   |
| 3 |요청 만들기 실패   |
| 4 |요청 제출에 실패   |
| 5 |챌린지 유효성 검사에 성공  |
| 6 |챌린지 유효성 검사에 실패  |
| 7 |발급에 실패    |
| 8 |발급 보류 중    |
| 9 |발급됨     |
| 10 |응답 처리 실패  |
| 11 |응답 보류 중    |
| 12 |등록 성공    |
| 13 |등록이 필요하지 않음    |
| 14 |해지됨     |
| 15 |컬렉션에서 제거됨   |
| 16 |갱신이 확인됨    |
| 17 |설치 실패   |
| 18 |설치됨    |
| 19 |삭제 실패    |
| 20 |삭제됨    |
| 21 |갱신이 요청됨   |

## <a name="7010-statetopictypeconditionalaccesscompliance"></a>7010 STATE_TOPICTYPE_CONDITIONAL_ACCESS_COMPLIANCE

|     상태 메시지 ID     |  상태 메시지 설명 |
|:-------------|:------|
|| 1 | 준수 성공    |
| 2 | mp에서 준수 실패   |
| 3 | 클라이언트에서 준수 실패   |
| 4 | Intune에서 준수 실패   |
| 5 | AAD에서 준수 실패   |
| 6 | 준수 comgmt Intune   |

## <a name="7200-statetopictypesuperpeerupdatecachemap"></a>7200 STATE_TOPICTYPE_SUPER_PEER_UPDATE_CACHE_MAP

|     상태 메시지 ID     |  상태 메시지 설명 |
|:-------------|:------|
| 1 |피어 캐시 원본이 추가됨       |
| 2 |피어 캐시 원본이 제거됨      |

## <a name="7201-statetopictypesuperpeerupdateconfig"></a>7201 STATE_TOPICTYPE_SUPER_PEER_UPDATE_CONFIG

|     상태 메시지 ID     |  상태 메시지 설명 |
|:-------------|:------|
| 1 |피어 캐시 원본이 비활성화됨       |
| 2 |피어 캐시 원본이 활성임       |

## <a name="7202-statetopictypedownloadaggregatedata"></a>7202 STATE_TOPICTYPE_DOWNLOAD_AGGREGATE_DATA
|     상태 메시지 ID     |  상태 메시지 설명 |
|:-------------|:------|
| 1 |집계 데이터 업로드 다운로드       |

## <a name="7203-statetopictypepeersourcereqrejectionstats"></a>7203 STATE_TOPICTYPE_PEERSOURCE_REQ_REJECTION_STATS

|     상태 메시지 ID     |  상태 메시지 설명 |
|:-------------|:------|
| 1 |피어 원본 거부 데이터 업로드     |

## <a name="7300-statetopictypeproxytraffic"></a>7300 STATE_TOPICTYPE_PROXY_TRAFFIC

상태 ID가 없습니다.

## <a name="7301-statetopictypeproxyconnection"></a>7301 STATE_TOPICTYPE_PROXY_CONNECTION

상태 ID가 없습니다.

## <a name="7302-statetopictypesrsusagedata"></a>7302 STATE_TOPICTYPE_SRS_USAGE_DATA

상태 ID가 없습니다.

## <a name="7303-statetopictypeproxytrafficidentity"></a>7303 STATE_TOPICTYPE_PROXY_TRAFFIC_IDENTITY

상태 ID가 없습니다.

## <a name="8001-statetopictypehasreport"></a>8001 STATE_TOPICTYPE_HAS_REPORT

|     상태 메시지 ID     |  상태 메시지 설명 |
|:-------------|:------|
| 1 |상태 증명 지원됨      |
| 2 |상태 증명 지원되지 않음      |

## <a name="statetopictypedeviceclientedplog"></a>STATE_TOPICTYPE_DEVICE_CLIENT_EDPLOG

상태 ID가 없습니다.

## <a name="8003-statetopictypeenablelostmode"></a>8003 STATE_TOPICTYPE_ENABLE_LOSTMODE

상태 ID가 없습니다.

## <a name="8004-statetopictypedisablelostmode"></a>8004 STATE_TOPICTYPE_DISABLE_LOSTMODE

상태 ID가 없습니다.

## <a name="8005-statetopictypelocatedevice"></a>8005 STATE_TOPICTYPE_LOCATE_DEVICE

상태 ID가 없습니다.

## <a name="8006-statetopictyperebootdevice"></a>8006 STATE_TOPICTYPE_REBOOT_DEVICE

상태 ID가 없습니다.

## <a name="8007-statetopictypelogoutuser"></a>8007 STATE_TOPICTYPE_LOGOUTUSER

상태 ID가 없습니다.

## <a name="8008-statetopictypeuserslist"></a>8008 STATE_TOPICTYPE_USERSLIST

상태 ID가 없습니다.

## <a name="8009-statetopictypedeleteuser"></a>8009 STATE_TOPICTYPE_DELETEUSER

상태 ID가 없습니다.

## <a name="8010-statetopictypecleanpcretaininguserdata"></a>8010 STATE_TOPICTYPE_CLEANPCRETAININGUSERDATA

상태 ID가 없습니다.

## <a name="8011-statetopictypecleanpcwithoutretaininguserdata"></a>8011 STATE_TOPICTYPE_CLEANPCWITHOUTRETAININGUSERDATA

상태 ID가 없습니다.

## <a name="8012-statetopictypesetdevicename"></a>8012 STATE_TOPICTYPE_SETDEVICENAME

상태 ID가 없습니다.

## <a name="9000-statetopictypebookcicompliance"></a>9000 STATE_TOPICTYPE_BOOK_CI_COMPLIANCE

상태 ID가 없습니다.

## <a name="9001-statetopictypebookcienforcement"></a>9001 STATE_TOPICTYPE_BOOK_CI_ENFORCEMENT

상태 ID가 없습니다.

## <a name="next-steps"></a>다음 단계

- [Description of state messaging in Configuration Manager](https://support.microsoft.com/help/4459394/description-of-state-messaging-in-system-center-configuration-manager)\(Configuration Manager의 상태 메시징에 대한 설명\)
- [Software updates management whitepaper for Configuration Manager](https://www.microsoft.com/download/details.aspx?id=44578)\(Configuration Manager에 대한 소프트웨어 업데이트 관리 백서\)
