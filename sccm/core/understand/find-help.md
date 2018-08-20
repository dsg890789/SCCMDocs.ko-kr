---
title: 도움말 찾기
titleSuffix: Configuration Manager
description: Configuration Manager에 대해 자세히 알아보기 위해 관련 리소스를 찾습니다.
ms.date: 07/30/2018
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 86810629-cf2a-43e8-86a2-847444119fc1
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: e6be541a1b26961684f0577f2540132b81f50b7a
ms.sourcegitcommit: 1826664216c61691292ea2a79e836b11e1e8a118
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/31/2018
ms.locfileid: "39385476"
---
# <a name="find-help-for-using-configuration-manager"></a>Configuration Manager 사용 도움말 찾기

*적용 대상: System Center Configuration Manager(현재 분기)*

이 문서에서는 다음 섹션에 Configuration Manager를 사용하기 위한 도움말을 찾도록 여러 리소스를 제공합니다.  

- [제품 설명서](#bkmk_Info)  

- [제품 피드백 공유](#product-feedback)  

- [Configuration Manager 팀 블로그 팔로우](#BKMK_ProductGroupBlog)  

- [지원 옵션 및 커뮤니티 리소스](#BKMK_SupportOptions)  

제품 접근성에 대한 도움말은 [접근성 기능](/sccm/core/understand/accessibility-features)을 참조하세요.  



##  <a name="bkmk_Info"></a>제품 설명서  

최신 제품 설명서에 액세스하려면 [라이브러리 인덱스](https://docs.microsoft.com/sccm/)에서 시작하세요.  

<a name="BKMK_SearchTips"></a>  

검색에 대한 팁, 피드백 제공 및 제품 설명서 사용에 대한 자세한 내용은 [문서 사용 방법](/sccm/core/understand/use-docs)을 참조합니다.  



<a name="product-feedback"></a>  

## <a name="BKMK_1806Feedback"></a> 1806 버전부터 시작하는 제품 피드백

Configuration Manager 버전 1806부터 제품 피드백은 콘솔에서 직접 보낼 수 있습니다. 로그를 첨부해야 하는 경우 [피드백 허브](#BKMK_FeedbackHub)를 사용합니다. 수행할 수 있는 작업은 다음과 같습니다. <!--1357542-->

  - **웃는 얼굴 보내기**: 좋아하는 것에 대한 피드백을 보냅니다.
  - **찡그린 얼굴 보내기**: 싫어하는 것에 대한 피드백을 보냅니다.
  - **제안 보내기**: [UserVoice 웹 사이트](https://configurationmanager.uservoice.com/)로 이동하여 아이디어를 공유합니다.

![Configuration Manager 1806에서 피드백 제출](media/1806-send-a-smile.png)


### <a name="send-a-smile"></a>웃는 얼굴 보내기

좋아하는 것에 대한 피드백을 보내려면 아래 지침을 따릅니다. 
1. 콘솔의 오른쪽 위 모서리에서 웃는 얼굴을 클릭합니다. 
2. 드롭다운 메뉴에서 **웃는 얼굴 보내기**를 선택합니다.
3. 텍스트 상자를 사용하여 좋아하는 것에 대해 설명합니다. 
4. 이메일 주소와 스크린샷을 공유할지 여부를 선택합니다. 
5. **피드백 제출**을 클릭합니다.
     - 인터넷에 연결되어 있지 않으면 아래쪽의 **저장**을 클릭합니다. [나중에 제출할 수 있도록 저장한 피드백 보내기](#BKMK_NoInternet) 섹션의 지침에 따라 Microsoft에 보냅니다. 

![Configuration Manager 1806에서 피드백 양식 제출](media/1806-feedback-form.png)


### <a name="send-a-frown"></a>찡그린 얼굴 보내기

싫어하는 것에 대한 피드백을 보내려면 아래 지침을 따릅니다.

1. 콘솔의 오른쪽 위 모서리에서 웃는 얼굴을 클릭합니다. 
2. 드롭다운 메뉴에서 **찡그린 얼굴**을 선택합니다.
3. 텍스트 상자를 사용하여 싫어하는 것에 대해 설명합니다. 
4. 이메일 주소와 스크린샷을 공유할지 여부를 선택합니다. 
5. **피드백 제출**을 클릭합니다.
     - 인터넷에 연결되어 있지 않으면 아래쪽의 **저장**을 클릭합니다. [나중에 제출할 수 있도록 저장한 피드백 보내기](#BKMK_NoInternet) 섹션의 지침에 따라 Microsoft에 보냅니다.  


### <a name="information-sent-with-feedback"></a>피드백과 함께 전송되는 정보
 
   - OS 빌드 정보
   - Configuration Manager 계층 구조 ID
   - 제품 빌드 정보
   - 언어 정보
   - 장치 식별자 
       - HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SQMClient:MachineId


### <a name="BKMK_NoInternet"></a> 나중에 제출할 수 있도록 저장한 피드백 보내기

1. **피드백 제공** 창 아래쪽에서 **저장**을 클릭합니다. 
2. .zip 파일을 저장합니다. 로컬 머신에 인터넷 액세스 권한이 없는 경우 인터넷에 연결된 머신에 파일을 복사합니다. 
3. 필요한 경우 `cd.latest\SMSSETUP\Tools\UploadOfflineFeedback\UploadOfflineFeedback.exe`에 있는 UploadOfflineFeedback.exe를 복사합니다.
    - cd.latest 폴더에 대한 자세한 내용은 [CD.Latest 폴더](../servers/manage/the-cd.latest-folder.md)를 참조하세요.

4. 인터넷에 연결된 머신에서 명령 프롬프트를 엽니다. 
5. 다음 명령을 실행합니다. `UploadOfflineFeedback.exe -f c:\folder\location_of.zip`
    
    - 필요에 따라 다음 항목을 지정할 수 있습니다.
        -  `-t, --timeout` 데이터 전송에 대한 시간 제한(초)입니다. 0은 무제한입니다. 기본값은 30입니다.
        - `-s --silent` 콘솔에 로깅하지 않음(--verbose와 결합할 수 없음)
        - `-v, --verbose` 콘솔에 자세한 정보 로깅 출력(--silent와 결합할 수 없음)
        - `--help` 도움말 화면 표시



##  <a name="BKMK_FeedbackHub"></a> 1802 및 이전 버전에 대한 제품 피드백

Windows 10에 기본 제공된 [피드백 허브 앱](https://support.microsoft.com/help/4021566/windows-10-send-feedback-to-microsoft-with-feedback-hub-app)을 통해 잠재적인 제품 결함을 보고합니다. **새 피드백을 추가**할 때 **엔터프라이즈 관리** 범주를 선택하고 다음과 같은 하위 범주가 중 하나를 선택해야 합니다.
 - Configuration Manager 클라이언트
 - Configuration Manager 콘솔
 - Configuration Manager OS 배포
 - Configuration Manager 서버

Configuration Manager에서 [UserVoice 페이지](https://configurationmanager.uservoice.com/)를 계속 사용하여 새로운 기능 아이디어에 투표하세요.


##  <a name="BKMK_ProductGroupBlog"></a>Configuration Manager 팀 블로그  

Configuration Manager 엔지니어링 및 파트너 팀은 [Enterprise Mobility + Security 블로그](https://cloudblogs.microsoft.com/enterprisemobility/?product=system-center-configuration-manager)를 사용하여 Configuration Manager 및 관련 기술에 대한 기술 정보와 기타 소식을 제공합니다. 이러한 블로그 게시물은 제품 설명서와 지원 정보를 보완합니다.  


##  <a name="BKMK_SupportOptions"></a> 지원 옵션 및 커뮤니티 리소스  

다음 링크는 지원 옵션 및 커뮤니티 리소스에 대한 정보를 제공합니다.  

-   [Microsoft 지원](https://aka.ms/cmcbsupport)  

-   [Configuration Manager 커뮤니티: System Center Configuration Manager(현재 분기) 서바이벌 가이드](https://social.technet.microsoft.com/wiki/contents/articles/33035.system-center-configuration-manager-current-branch-survival-guide.aspx )  

-   [Configuration Manager 포럼 페이지](https://social.technet.microsoft.com/Forums/en-US/home?category=ConfigMgrCB)  
    <!-- NOTE: the above URL requires "en-US" for the category to work -->