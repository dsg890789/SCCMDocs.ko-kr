---
title: 예제 시나리오 - Windows Embedded 클라이언트 배포
titleSuffix: Configuration Manager
description: Windows Embedded 디바이스의 Configuration Manager 클라이언트 배포 및 관리에 대한 예제 시나리오를 참조하세요.
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: 10049c89-b37c-472b-b317-ce4f56cd4be7
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 0d6e318a9606eb4988d28a363ea40c5eec3a7cde
ms.sourcegitcommit: 148745e1c3d9817d8beea20684a54436210959c6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75825067"
---
# <a name="example-scenario-for-deploying-and-managing-configuration-manager-clients-on-windows-embedded-devices"></a>Windows Embedded 디바이스의 Configuration Manager 클라이언트 배포 및 관리에 대한 예제 시나리오

*적용 대상: Configuration Manager(현재 분기)*

이 시나리오에서는 Configuration Manager를 통해 쓰기 필터를 사용하는 Windows Embedded 디바이스를 관리하는 방법을 보여 줍니다. Embedded 디바이스가 쓰기 필터를 지원하지 않는 경우 표준 Configuration Manager 클라이언트로 동작하므로 이러한 절차가 적용되지 않습니다.  

Coho Vineyard & Winery에서는 방문자 센터를 개설할 예정이며 Windows Embedded를 실행하여 대화형 프레젠테이션을 실행하는 키오스크가 필요합니다. 새 방문자 센터로 사용할 건물은 IT 부서에서 가깝지 않으므로 원격으로 키오스크를 관리해야 합니다. 프레젠테이션을 실행하는 소프트웨어 외에도 이러한 디바이스에서 최신 맬웨어 방지 소프트웨어를 실행하여 회사 보안 정책을 준수해야 합니다. 키오스크는 방문자 센터가 열려 있는 동안 가동 중지 시간 없이 연중무휴로 실행되어야 합니다.  

 Coho에서는 이미 Configuration Manager를 실행하여 네트워크의 디바이스를 관리합니다. Configuration Manager는 Endpoint Protection을 실행하고 소프트웨어 업데이트와 애플리케이션을 설치하도록 구성되어 있습니다. 그러나 IT 팀에서는 이전에 Windows Embedded 디바이스를 관리해 본 적이 없기 때문에 Configuration Manager 관리자는 파일럿을 실행하여 리셉션 로비에서 두 개의 키오스크를 관리하고 있습니다.   

 쓰기 필터를 지원하는 이러한 Windows Embedded 디바이스를 관리하기 위해 Configuration Manager 관리자는 다음과 같은 단계를 수행하여 Configuration Manager 클라이언트를 설치하고, Endpoint Protection을 사용하여 클라이언트를 보호하고, 대화형 프레젠테이션 소프트웨어를 설치합니다.  

1. Configuration Manager 관리자(이하 관리자)는 Windows Embedded 디바이스에서 쓰기 필터를 사용하는 방법과 Configuration Manager에서 자동으로 쓰기 필터를 사용하지 않도록 설정한 후 다시 사용하도록 설정하는 방식으로 쓰기 필터 사용을 간편하게 하여 소프트웨어 설치 상태를 유지하는 방법에 대해 읽습니다.  

    자세한 내용은 [Windows Embedded 디바이스에 클라이언트 배포 계획](../../../core/clients/deploy/plan/planning-for-client-deployment-to-windows-embedded-devices.md)을 참조하세요.  

2. 관리자는 Configuration Manager 클라이언트를 설치하기 전에 Windows Embedded 디바이스를 위한 새로운 쿼리 기반 디바이스 컬렉션을 만듭니다. 회사에서는 표준 명명 형식을 사용하여 컴퓨터를 식별하기 때문에 관리자는 컴퓨터 이름의 첫 6자로 Windows Embedded 디바이스를 고유하게 식별할 수 있습니다. **WEMDVC**. 관리자는 다음 WQL 쿼리를 사용하여 이 컬렉션을 만듭니다. **select SMS_R_System.NetbiosName from SMS_R_System where SMS_R_System.NetbiosName like "WEMDVC%"**  

    이 컬렉션을 통해 관리자는 다른 디바이스와 다른 구성 옵션을 갖는 Windows Embedded 디바이스를 관리할 수 있습니다. 관리자는 이 컬렉션을 사용하여 다시 시작을 제어하고, 클라이언트 설정을 갖는 Endpoint Protection을 배포하고, 대화형 프레젠테이션 애플리케이션을 배포하게 됩니다.  

    [컬렉션을 만드는 방법](../../../core/clients/manage/collections/create-collections.md)을 참조하세요.  

3. 관리자는 프레젠테이션 애플리케이션 설치와 업그레이드에 필요할 수 있는 다시 시작이 방문자 센터 운영 시간 동안 발생하지 않도록 컬렉션의 유지 관리 기간을 구성합니다. 운영 시간은 월요일부터 일요일 09:00부터 18:00이므로 관리자는 유지 관리 기간을 매일 18:30부터 06:00까지로 구성합니다.  

4. 자세한 내용은 [유지 관리 기간을 사용하는 방법](../../../core/clients/manage/collections/use-maintenance-windows.md)을 참조하세요.  

5. 그런 다음, 관리자는 다음 설정에 대해 **예** 를 선택하여 Endpoint Protection 클라이언트를 설치하도록 사용자 지정 디바이스 클라이언트 설정을 구성한 다음, 이 사용자 지정 클라이언트 설정을 Windows Embedded 디바이스 컬렉션에 배포합니다.  

   - **클라이언트 컴퓨터에 Endpoint Protection 클라이언트 설치**  

   - **쓰기 필터를 지원하는 Windows Embedded 디바이스에 Endpoint Protection 클라이언트 설치 커밋(다시 시작 필요)**  

   - **유지 관리 기간 외에 Endpoint Protection 클라이언트 설치 및 다시 시작이 수행될 수 있도록 허용**  

     Configuration Manager 클라이언트가 설치될 때 이러한 설정으로 인해 Endpoint Protection 클라이언트가 설치되고 오버레이에만 기록되지 않고 설치의 일부로 운영 체제에 유지됩니다. 회사 보안 정책에 따라 맬웨어 방지 소프트웨어가 항상 설치되어 있어야 하며 관리자는 키오스크가 다시 시작될 경우 잠깐이라도 보호되지 않는 위험에 처하기를 원하지 않습니다.  

   > [!NOTE]  
   >  Endpoint Protection 클라이언트를 설치하는 데 필요한 다시 시작은 방문자 센터가 운영되기 전에 디바이스 설치 기간 동안 한 번만 이루어집니다. 애플리케이션 또는 소프트웨어 정의 업데이트가 정기적으로 배포되는 것과 달리, 동일한 디바이스에 Endpoint Protection 클라이언트가 설치되는 다음 시기는 회사에서 차기 버전의 Configuration Manager로 업그레이드하는 때가 될 것입니다.  

    자세한 내용은 [Endpoint Protection 구성](../../../protect/deploy-use/configure-endpoint-protection.md)을 참조하세요.  

6. 이제 클라이언트에 대한 구성 설정이 갖추어졌으므로 관리자는 Configuration Manager 클라이언트 설치를 준비합니다. 먼저 Windows Embedded 디바이스에서 쓰기 필터를 사용하지 않도록 수동으로 설정해야 관리자가 클라이언트를 설치할 수 있습니다. 관리자는 키오스크와 함께 제공된 OEM 문서를 읽고 해당 지침에 따라 쓰기 필터를 사용하지 않도록 설정합니다.  

    관리자는 회사 표준 명명 형식을 사용하도록 디바이스의 이름을 바꾼 다음, 클라이언트 원본 파일이 있는 매핑된 드라이브에서 다음 명령을 사용하여 CCMSetup을 실행함으로써 수동으로 클라이언트를 설치합니다. **CCMSetup.exe /MP:mpserver.cohovineyardandwinery.com SMSSITECODE=CO1**  

    이 명령은 클라이언트를 설치하고 **mpserver.cohovineyardandwinery.com**의 인트라넷 FQDN을 갖는 관리 지점에 클라이언트를 할당한 후에 **CO1**이라는 기본 사이트에 클라이언트를 할당합니다.  

    관리자는 클라이언트가 설치되고 사이트에 상태를 다시 보내기까지 항상 약간의 시간이 걸린다는 것을 알고 있으므로 기다렸다가 클라이언트가 성공적으로 설치되고 사이트에 할당되어 Windows Embedded 디바이스용으로 만든 컬렉션의 클라이언트로 표시되는 것을 확인합니다.  

    추가적인 확인으로, 디바이스에서 제어판의 Configuration Manager 속성을 확인하고 해당 속성을 사이트에서 관리되는 표준 Windows 컴퓨터와 비교합니다. 예를 들어 **구성 요소** 탭의 **하드웨어 인벤토리 에이전트** 에는 **사용**이 표시되고, **작업** 탭에는 **애플리케이션 배포 평가 주기** 및 **검색 데이터 컬렉션 주기**를 포함한 11개의 작업을 사용할 수 있습니다.  

    클라이언트가 성공적으로 설치 및 할당되어 관리 지점에서 클라이언트 정책을 받는다는 것을 확인한 후 관리자는 OEM의 지침을 따라 수동으로 쓰기 필터를 사용하도록 설정합니다.  

    자세한 내용은 다음을 참조하십시오.  

   -   [Windows 컴퓨터에 클라이언트를 배포하는 방법](../../../core/clients/deploy/deploy-clients-to-windows-computers.md)  

   -   [사이트에 클라이언트를 할당하는 방법](../../../core/clients/deploy/assign-clients-to-a-site.md)  

7. 이제 Windows Embedded 디바이스에 Configuration Manager 클라이언트가 설치되었으므로 관리자는 표준 Windows 클라이언트를 관리하는 것과 같은 방법으로 해당 디바이스를 관리할 수 있다는 것을 확인합니다. 예를 들어 Configuration Manager 콘솔에서 원격 제어를 사용하여 원격으로 디바이스를 관리하고 디바이스에 대한 클라이언트 정책을 시작하고 클라이언트 속성 및 하드웨어 인벤토리를 볼 수 있습니다.  

    이러한 디바이스는 Active Directory 도메인에 조인되었기 때문에 수동으로 신뢰할 수 있는 클라이언트로 승인하지 않아도 되며, Configuration Manager 콘솔에서 승인된 것을 확인합니다.  

    자세한 내용은 [클라이언트를 관리하는 방법](../../../core/clients/manage/manage-clients.md)을 참조하세요.  

8. 대화형 프레젠테이션 소프트웨어를 설치하기 위해 관리자는 **소프트웨어 배포 마법사**를 실행하고 필수 애플리케이션을 구성합니다. 마법사의 **사용자 환경** 페이지에 있는 **Windows Embedded 디바이스에 대한 쓰기 필터 처리** 섹션에서 **최종 기한에 또는 유지 관리 기간 동안 변경 내용 커밋(다시 시작해야 함)** 을 선택하는 기본 옵션을 적용합니다.  

    관리자는 다시 시작 후에 애플리케이션이 유지되고 키오스크를 이용하는 방문자가 항상 애플리케이션을 사용할 수 있도록 하기 위해 쓰기 필터에 대한 이 기본 옵션을 유지합니다. 일상적인 유지 관리 기간에 설치 및 업데이트를 위한 다시 시작이 안전하게 이루어질 수 있습니다.  

    관리자는 Windows Embedded 디바이스 컬렉션에 애플리케이션을 배포합니다.  

    자세한 내용은 [Configuration Manager에서 애플리케이션을 배포하는 방법](../../../apps/deploy-use/deploy-applications.md)을 참조하세요.  

9. 관리자는 Endpoint Protection에 대한 정의 업데이트를 구성하도록 소프트웨어 업데이트를 사용하고 자동 배포 규칙 만들기 마법사를 실행하고 **정의 업데이트** 템플릿을 선택하여 Endpoint Protection에 적합한 설정으로 마법사를 미리 채웁니다.  

     이는 마법사의 **사용자 환경** 페이지에서 다음과 같은 설정입니다.  

   - **최종 기한 동작**: **소프트웨어 설치** 확인란을 선택하지 않습니다.  

   - **Windows Embedded 디바이스에 대한 쓰기 필터 처리**: **최종 기한에 또는 유지 관리 기간 동안 변경 내용 커밋(다시 시작해야 함)** 확인란을 선택하지 않습니다.  

     관리자는 이러한 기본 설정을 유지합니다. 이 구성을 갖는 이러한 두 옵션은 Endpoint Protection에 대한 소프트웨어 업데이트 정의가 유지 관리 기간 동안 설치 및 커밋되도록 기다리지 않고 업무 시간 동안 오버레이에 설치되도록 허용합니다. 이 구성은 컴퓨터가 최신 맬웨어 방지 보호를 실행하도록 하는 회사의 보안 정책을 가장 잘 충족합니다.  

     > [!NOTE]  
     >  애플리케이션에 대한 소프트웨어 설치와 달리, Endpoint Protection에 대한 소프트웨어 업데이트 정의는 하루에도 몇 번씩 매우 자주 이루어질 수 있습니다. 소프트웨어 업데이트 정의는 대개 작은 파일입니다. 이러한 유형의 보안 관련 배포의 경우 유지 관리 기간까지 기다리기보다 항상 오버레이에 설치하는 것이 좋은 경우가 많습니다. Configuration Manager 클라이언트에서는 디바이스가 다시 시작될 경우 소프트웨어 정의 업데이트를 신속히 다시 설치합니다. 이 작업은 예정된 다음 평가까지 기다리지 않고 평가 확인을 시작하기 때문입니다.  

     관리자는 자동 배포 규칙을 위해 Windows Embedded 디바이스 컬렉션을 선택합니다.  

     자세한 내용은  
               3단계: [Endpoint Protection 구성](../../../protect/deploy-use/configure-endpoint-protection.md)의 클라이언트 컴퓨터에 정의 업데이트를 제공하도록 Configuration Manager 소프트웨어 업데이트 구성  

10. 관리자는 모든 변경 내용을 오버레이에 정기적으로 커밋하는 유지 관리 작업을 구성하기로 결정합니다. 이 작업은 소프트웨어 업데이트 정의 배포를 지원하며, 누적되어 디바이스가 다시 시작될 때마다 다시 설치해야 하는 업데이트 수를 줄입니다. 관리자의 경험상 이렇게 하면 맬웨어 방지 프로그램을 더욱 효율적으로 실행하는 데 도움이 됩니다.  

    > [!NOTE]  
    >  이러한 소프트웨어 업데이트 정의는 Embedded 디바이스가 변경 내용 커밋을 지원하는 다른 관리 작업을 실행한 경우 이미지에 자동으로 커밋됩니다. 예를 들어 새로운 버전의 대화형 프레젠테이션 소프트웨어를 설치하는 경우에도 소프트웨어 업데이트 정의에 대한 변경 내용이 커밋됩니다. 또는 매월 유지 관리 기간 동안 표준 소프트웨어 업데이트를 설치하는 경우에도 소프트웨어 업데이트 정의에 대한 변경 내용이 커밋될 수 있습니다. 그러나 표준 소프트웨어 업데이트가 실행되지 않고 대화형 프레젠테이션 소프트웨어가 그리 자주 업데이트되지 않는 이 시나리오에서는 소프트웨어 정의 업데이트가 수개월 만에 이미지에 자동으로 커밋될 수 있습니다.  

     관리자는 먼저 이름 외에 설정이 없는 사용자 지정 작업 순서를 만듭니다. 이를 위해 작업 순서 만들기 마법사를 실행합니다.  

    1. 관리자는 **새 작업 순서 만들기** 페이지에서 **새 사용자 지정 작업 순서 만들기**를 선택한 후 **다음**을 클릭합니다.  

    2. **작업 순서 정보** 페이지에서 작업 순서 이름으로 **Maintenance task to commit changes on embedded devices**를 입력한 후 **다음**을 클릭합니다.  

    3. **요약** 페이지에서 **다음**을 선택하여 마법사를 완료합니다.  

       그런 다음, 관리자는 이 사용자 지정 작업 순서를 Windows Embedded 디바이스 컬렉션에 배포하고 매월 실행되는 일정을 구성합니다. 배포 설정 과정에서 **최종 기한에 또는 유지 관리 기간 동안 변경 내용 커밋(다시 시작해야 함)** 확인란을 선택하여 다시 시작 후에 변경 내용을 유지합니다. 이 배포를 구성하기 위해 방금 만든 사용자 지정 작업 순서를 선택한 다음, **홈** 탭의 **배포** 그룹에서 **배포** 를 클릭하여 소프트웨어 배포 마법사를 시작합니다.  

    4. **일반** 페이지에서 Windows Embedded 디바이스 컬렉션을 선택한 후 **다음**을 클릭합니다.  

    5. **배포 설정** 페이지에서 **용도** 를 **필수**로 선택한 후 **다음**을 클릭합니다.  

    6. **일정 예약** 페이지에서 **새로 만들기**를 클릭하여 유지 관리 기간 동안의 주별 일정을 지정한 후 **다음**을 클릭합니다.  

    7. 관리자는 더 이상 변경하지 않고 마법사를 완료합니다.  

       자세한 내용은  
                 [작업을 자동화하는 작업 순서 관리](../../../osd/deploy-use/manage-task-sequences-to-automate-tasks.md)  

11. 관리자는 키오스크가 자동으로 실행되도록 다음 설정으로 디바이스를 구성하는 스크립트를 작성합니다.  

    - 암호가 없는 게스트 계정을 사용하여 자동으로 로그온합니다.  

    - 시작 시 자동으로 대화형 프레젠테이션 소프트웨어를 실행합니다.  

      관리자는 패키지와 프로그램을 사용하여 이 스크립트를 Windows Embedded 디바이스 컬렉션에 배포합니다. 관리자는 소프트웨어 배포 마법사를 실행할 때 **최종 기한에 또는 유지 관리 기간 동안 변경 내용 커밋(다시 시작해야 함)** 확인란을 다시 선택하여 다시 시작 후에 변경 내용을 유지합니다.  

      자세한 내용은 [패키지 및 프로그램](../../../apps/deploy-use/packages-and-programs.md)을 참조하세요.  

12. 다음 날 아침 관리자는 Windows Embedded 디바이스에 대해 다음 사항을 확인합니다.  

    - 키오스크가 게스트 계정을 사용하여 자동으로 로그온되어 있습니다.  

    - 대화형 프레젠테이션 소프트웨어가 실행 중입니다.  

    - Endpoint Protection 클라이언트가 설치되어 있고 최신 소프트웨어 업데이트 정의를 갖추고 있습니다.  

    - 디바이스가 유지 관리 기간 동안 다시 시작되었습니다.  

      자세한 내용은 다음을 참조하십시오.  

    - [Endpoint Protection을 모니터링하는 방법](../../../protect/deploy-use/monitor-endpoint-protection.md)  

    - [Configuration Manager에서 애플리케이션 모니터링](/sccm/apps/deploy-use/monitor-applications-from-the-console)  

13. 관리자는 키오스크를 모니터링하여 성공적으로 관리되고 있음을 상사에게 보고합니다. 결과적으로 방문자 센터에 20개의 키오스크를 주문했습니다.  

     쓰기 필터를 수동으로 사용하지 않도록 설정했다가 다시 사용하도록 설정해야 하는 Configuration Manager 클라이언트의 수동 설치를 방지하기 위해 관리자는 Configuration Manager 클라이언트의 설치와 사이트 할당이 이미 들어 있는 사용자 지정 이미지를 주문에 포함합니다. 또한 회사의 이름 지정 형식에 따라 디바이스의 이름을 지정했습니다.  

     키오스크는 방문자 센터 개장 일주일 전에 배송되었습니다. 이 기간 동안 키오스크를 네트워크에 연결하고 로컬 관리자가 필요 없도록 키오스크의 모든 디바이스 관리를 자동화했습니다. 관리자는 키오스크가 다음과 같이 필요한 대로 작동하는지 확인합니다.  

    -   키오스크의 클라이언트가 사이트 할당을 완료하고 Active Directory Domain Services에서 신뢰할 수 있는 루트 키를 다운로드합니다.  

    -   키오스크의 클라이언트가 Windows Embedded 디바이스 컬렉션에 자동으로 추가되고 유지 관리 기간을 사용하도록 구성됩니다.  

    -   Endpoint Protection 클라이언트가 설치되어 있고 맬웨어 방지를 위한 최신 소프트웨어 업데이트 정의를 갖추고 있습니다.  

    -   대화형 프레젠테이션 소프트웨어가 설치되어 있고 자동으로 실행되어 방문자가 사용할 수 있는 상태입니다.  

14. 이 초기 설치 후에 업데이트를 위해 다시 시작이 필요할 경우 방문자 센터가 운영되지 않는 시간에만 이루어집니다.  
