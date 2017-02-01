---

title: "인터넷 연결 없이 업데이트 동기화 - Configuration Manager | Microsoft 문서"
description: "인터넷에서 연결이 끊어진 최상위 소프트웨어 업데이트 지점에서 소프트웨어 업데이트 동기화를 실행합니다."
keywords: 
author: dougeby
ms.author: dougeby
manager: angrobe
ms.date: 01/23/2017
ms.topic: article
ms.prod: configuration-manager
ms.service: 
ms.technology:
- configmgr-sum
ms.assetid: 1a997c30-8e71-4be5-89ee-41efb2c8d199
translationtype: Human Translation
ms.sourcegitcommit: 89158debdf4c345a325feeb608db2215a88ed81b
ms.openlocfilehash: fd9c1e9418ff1956c6ef98753e23a293440179be



---

# <a name="synchronize-software-updates-from-a-disconnected-software-update-point"></a>연결이 끊긴 소프트웨어 업데이트 지점에서 소프트웨어 업데이트 동기화  

*적용 대상: System Center Configuration Manager(현재 분기)*

 최상위 사이트의 소프트웨어 업데이트 지점이 인터넷에서 연결이 끊기면 WSUSUtil 도구의 내보내기 및 가져오기 기능을 사용하여 소프트웨어 업데이트 메타데이터를 동기화해야 합니다. Configuration Manager 계층 구조에 속하지 않는 기존 WSUS 서버를 동기화 원본으로 선택할 수 있습니다. 이 항목에서는 WSUSUtil 도구의 내보내기 및 가져오기 기능을 사용하는 방법에 대한 정보를 제공합니다.  

 소프트웨어 업데이트 메타데이터를 내보내거나 가져오려면 지정된 내보내기 서버의 WSUS 데이터베이스에서 소프트웨어 업데이트 메타데이터를 내보낸 다음, 로컬에 저장된 사용 조건 파일을 연결이 끊긴 소프트웨어 업데이트 지점에 복사하고, 연결이 끊긴 소프트웨어 업데이트 지점의 WSUS 데이터베이스로 소프트웨어 업데이트 메타데이터를 가져와야 합니다.  

 소프트웨어 업데이트 메타데이터를 내보낼 내보내기 서버를 식별하려면 다음 표를 참조하세요.  

|소프트웨어 업데이트 지점|연결된 소프트웨어 업데이트 지점의 업스트림 업데이트 원본|연결이 끊긴 소프트웨어 업데이트 지점의 내보내기 서버|  
|---------------------------|-----------------------------------------------------------------|------------------------------------------------------------|  
|중앙 관리 사이트|Microsoft Update(인터넷)<br /><br /> 기존 WSUS 서버|Configuration Manager 사용 환경에 필요한 소프트웨어 업데이트 분류, 제품 및 언어를 사용하여 Microsoft Update와 동기화할 WSUS 서버를 선택합니다.|  
|독립 실행형 기본 사이트|Microsoft Update(인터넷)<br /><br /> 기존 WSUS 서버|Configuration Manager 사용 환경에 필요한 소프트웨어 업데이트 분류, 제품 및 언어를 사용하여 Microsoft Update와 동기화할 WSUS 서버를 선택합니다.|  

 내보내기 프로세스를 시작하기 전에, 선택한 내보내기 서버에서 소프트웨어 업데이트 동기화가 완료되어 최신 소프트웨어 업데이트 메타데이터가 동기화되었는지 확인합니다. 소프트웨어 업데이트 동기화가 성공적으로 완료되었는지 확인하려면 다음 절차를 수행하세요.  

#### <a name="to-verify-that-software-updates-synchronization-has-completed-successfully-on-the-export-server"></a>내보내기 서버에서 소프트웨어 업데이트 동기화가 성공적으로 완료되었는지 확인하려면  

1.  WSUS 관리 콘솔을 열고 내보내기 서버의 WSUS 데이터베이스에 연결합니다.  

2.  WSUS 관리 콘솔에서 **동기화**를 클릭합니다. 결과 창에 소프트웨어 업데이트 동기화 시도 목록이 표시됩니다.  

3.  결과 창에서 최신 소프트웨어 업데이트 동기화 시도를 찾아 성공적으로 완료되었는지 확인합니다.  

> [!IMPORTANT]  
>  소프트웨어 업데이트 메타데이터를 내보내려면 내보내기 서버에서 WSUSUtil 도구를 로컬로 실행해야 하며, 소프트웨어 업데이트 메타데이터를 가져오려면 연결이 끊긴 소프트웨어 업데이트 지점 서버에서도 이 도구를 실행해야 합니다. 그리고, WSUSUtil 도구를 실행하는 사용자가 각 서버의 로컬 관리자 그룹의 구성원이어야 합니다.  

## <a name="export-process-for-software-updates"></a>소프트웨어 업데이트를 위한 내보내기 프로세스  
 소프트웨어 업데이트 내보내기 프로세스는 두 가지 주요 단계로 구성됩니다. 그 중 하나는 로컬로 저장된 사용 조건 파일을 연결이 끊긴 소프트웨어 업데이트 지점에 복사하는 단계이고, 다른 하나는 내보내기 서버의 WSUS 데이터베이스에서 소프트웨어 업데이트 메타데이터를 내보내는 단계입니다.  

 연결이 끊긴 소프트웨어 업데이트 지점에 로컬 사용 조건 메타데이터를 복사하려면 다음 절차를 수행하세요.  

#### <a name="to-copy-local-files-from-the-export-server-to-the-disconnected-software-update-point-server"></a>내보내기 서버에서 연결이 끊긴 소프트웨어 업데이트 지점 서버로 로컬 파일을 복사하려면  

1.  내보내기 서버에서 소프트웨어 업데이트 및 소프트웨어 업데이트를 위한 사용 조건이 저장된 폴더로 이동합니다. 기본적으로 WSUS 서버는 <*WSUS 설치 드라이브*>WSUS\WSUSContent\\에 파일을 저장합니다. 여기서 *WSUS 설치 드라이브*는 WSUS가 설치된 드라이브입니다.  

2.  이 위치의 모든 파일과 폴더를 연결이 끊긴 소프트웨어 업데이트 지점 서버의 WSUSContent 폴더로 복사합니다.  

 내보내기 서버의 WSUS 데이터베이스에서 소프트웨어 업데이트 메타데이터를 내보내려면 다음 절차를 수행하세요.  

#### <a name="to-export-software-updates-metadata-from-the-wsus-database-on-the-export-server"></a>내보내기 서버의 WSUS 데이터베이스에서 소프트웨어 업데이트 메타데이터를 내보내려면  

1.  내보내기 서버의 명령 프롬프트에서 WSUSutil.exe가 포함된 폴더로 이동합니다. 이 도구는 기본적으로 %*ProgramFiles*%\Update Services\Tools에 있습니다. 예를 들어 이 도구가 기본 위치에 있다면 **cd %ProgramFiles%\Update Services\Tools**를 입력합니다.  

2.  소프트웨어 업데이트 메타데이터를 패키지 파일로 내보내려면 다음과 같이 입력합니다.  

     **wsusutil.exe export**  *packagename*  *logfile*  

     예를 들면 다음과 같습니다.  

     **wsusutil.exe export export.cab export.log**  

     이 형식은 다음과 같이 요약할 수 있습니다. WSUSutil.exe 뒤에 내보내기 옵션, 내보내기 작업 중에 만든 내보내기 .cab 파일 이름, 로그 파일 이름이 옵니다. WSUSutil.exe는 내보내기 서버에서 메타데이터를 내보내고 작업의 로그 파일을 만듭니다.  

    > [!NOTE]  
    >  현재 폴더에서 패키지(.cab 파일) 및 로그 파일 이름이 고유해야 합니다.  

3.  내보내기 패키지를 가져오기 WSUS 서버의 WSUSutil.exe가 포함된 폴더로 이동합니다.  

    > [!NOTE]  
    >  패키지를 이 폴더로 이동하면 가져오기 작업을 더 쉽게 수행할 수 있습니다. 이 패키지를 가져오기 서버에서 액세스 가능한 어떤 위치로든 이동한 다음 WSUSutil.exe를 실행할 때 해당 위치를 지정하면 됩니다.  

## <a name="import-software-updates-metadata"></a>소프트웨어 업데이트 메타데이터 가져오기  
 내보내기 서버에서 연결이 끊긴 소프트웨어 업데이트 지점으로 소프트웨어 업데이트를 가져오려면 다음 절차를 수행하세요.  

> [!IMPORTANT]  
>  신뢰할 수 없는 원본에서 내보낸 데이터는 가져오지 마십시오. 신뢰할 수 없는 원본에서 콘텐츠를 가져오면 WSUS 서버의 보안이 손상될 수 있습니다.  

#### <a name="to-import-metadata-to-the-database-of-the-import-server"></a>가져오기 서버의 데이터베이스로 메타데이터를 가져오려면  

1.  가져오기 WSUS 서버의 명령 프롬프트에서 WSUSutil.exe가 포함된 폴더로 이동합니다. 이 도구는 기본적으로 %*ProgramFiles*%\Update Services\Tools에 있습니다.  

2.  다음과 같이 입력합니다.  

     **wsusutil.exe import**  *packagename*  *logfile*  

     예를 들면 다음과 같습니다.  

     **wsusutil.exe import export.cab import.log**  

     이 형식은 다음과 같이 요약할 수 있습니다. WSUSutil.exe 뒤에 import 명령, 내보내기 작업 중에 만든 패키지 파일(.cab) 이름, 패키지 파일의 경로(패키지 파일이 다른 폴더에 있는 경우) 및 로그 파일 이름이 옵니다. WSUSutil.exe는 내보내기 서버에서 메타데이터를 가져오고 작업의 로그 파일을 만듭니다.  

## <a name="next-steps"></a>다음 단계
처음으로 소프트웨어 업데이트를 동기화한 후 또는 새 분류나 제품을 사용할 수 있게 되면 [새 분류 및 제품을 구성](configure-classifications-and-products.md)하여 소프트웨어 업데이트를 새 기준과 동기화해야 합니다.

소프트웨어 업데이트를 필요한 기준과 동기화한 후 [소프트웨어 업데이트에 대한 설정을 관리](manage-settings-for-software-updates.md)합니다.  



<!--HONumber=Jan17_HO4-->


