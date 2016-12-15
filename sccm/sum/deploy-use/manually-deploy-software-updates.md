---

title: "소프트웨어 업데이트 수동 배포 | Microsoft 문서"
description: "업데이트를 수동으로 배포하려면 Configuration Manager 콘솔에서 업데이트를 선택하고 수동으로 배포하거나, 업데이트 그룹에 업데이트를 추가하고 그룹을 배포합니다."
keywords: 
author: dougeby
ms.author: dougeby
manager: angrobe
ms.date: 12/07/2016
ms.topic: article
ms.prod: configuration-manager
ms.service: 
ms.technology:
- configmgr-sum
ms.assetid: 57184274-5fea-4d79-a2b4-22e08ed26daf
translationtype: Human Translation
ms.sourcegitcommit: 78524abd4c45f0b7402d6f1e85afc60bb72ab0ee
ms.openlocfilehash: d736715f1f2c92b4c91f156ecb8abe3513811a34


---

#  <a name="a-namebkmkmanualdeploya-manually-deploy-software-updates"></a><a name="BKMK_ManualDeploy"></a> 소프트웨어 업데이트 수동 배포  

*적용 대상: System Center Configuration Manager(현재 분기)*

 수동 소프트웨어 업데이트 배포는 Configuration Manager 콘솔에서 소프트웨어 업데이트를 선택하고 배포 프로세스를 수동으로 시작하는 프로세스입니다. 또는 선택한 소프트웨어 업데이트를 업데이트 그룹에 추가한 다음 이 업데이트 그룹을 수동으로 배포할 수 있습니다. 먼저 수동 배포를 사용하여 클라이언트 장치에 필수 소프트웨어 업데이트를 최신 버전으로 유지하는 것이 일반적인 방법입니다. 그다음에 지속적인 월별 소프트웨어 업데이트 배포를 관리할 ADR을 만듭니다. 또한 수동 방법을 사용하면 대역 외 소프트웨어 업데이트를 배포할 수 있습니다. 적합한 배포 방법을 확인하려면 [소프트웨어 업데이트 배포](deploy-software-updates.md)를 참조하세요.

 다음 섹션에서는 소프트웨어 업데이트를 수동으로 배포하는 단계를 제공합니다.  

##  <a name="a-namebkmk1searchcriteriaa-step-1-specify-search-criteria-for-software-updates"></a><a name="BKMK_1SearchCriteria"></a> 1단계: 소프트웨어 업데이트에 대한 검색 조건 지정  
 Configuration Manager 콘솔에는 수천 개의 소프트웨어 업데이트가 표시될 수 있습니다. 소프트웨어 업데이트 수동 배포를 위한 워크플로의 첫 단계는 배포할 소프트웨어 업데이트를 확인하는 것입니다. 예를 들어 50개 이상의 클라이언트 장치에 필요하고 **보안** 또는 **위험** 소프트웨어 업데이트 분류에 속하는 모든 소프트웨어 업데이트를 검색하는 기준을 제공할 수 있습니다.  

> [!IMPORTANT]  
>  단일 소프트웨어 업데이트 배포에 포함할 수 있는 최대 소프트웨어 업데이트 수는 1000개입니다.  

#### <a name="to-specify-search-criteria-for-software-updates"></a>소프트웨어 업데이트에 대한 검색 조건을 지정하려면  

1.  Configuration Manager 콘솔에서 **소프트웨어 라이브러리**를 클릭합니다.  

2.  소프트웨어 라이브러리 작업 영역에서 **소프트웨어 업데이트**를 확장하고 **모든 소프트웨어 업데이트**를 클릭합니다. 동기화된 소프트웨어 업데이트가 표시됩니다.  

    > [!NOTE]  
    >  **모든 소프트웨어 업데이트** 노드에서 Configuration Manager는 지난 30일 이내에 배포되고 **위험** 및 **보안**으로 분류된 소프트웨어 업데이트만 표시합니다.  

3.  검색 창에서 다음 단계 중 하나 또는 둘 다를 사용하여 필요한 소프트웨어 업데이트를 확인하기 위해 필터링을 수행합니다.  

    -   검색 텍스트 상자에 소프트웨어 업데이트를 필터링할 검색 문자열을 입력합니다. 예를 들어 특정 소프트웨어 업데이트에 대한 문서 ID 또는 공지 ID를 입력하거나 여러 소프트웨어 업데이트의 타이틀에 표시될 문자열을 입력합니다.  

    -   **조건 추가**를 클릭하고, 소프트웨어 업데이트를 필터링하는 데 사용할 조건을 선택하고, **추가**를 클릭한 다음, 조건에 대한 값을 입력합니다.  

4.  **검색** 을 클릭하여 소프트웨어 업데이트를 필터링합니다.  

    > [!TIP]  
    >  선택적으로 **검색** 탭과 **저장** 그룹에 필터 기준을 저장할 수 있습니다.  

##  <a name="a-namebkmk2updategroupa-step-2-create-a-software-update-group-that-contains-the-software-updates"></a><a name="BKMK_2UpdateGroup"></a> 2단계: 소프트웨어 업데이트를 포함하는 소프트웨어 업데이트 그룹 만들기  
 소프트웨어 업데이트 그룹을 활용하면 배포 준비 과정에서 소프트웨어 업데이트를 효과적으로 구성할 수 있습니다. 소프트웨어 업데이트를 소프트웨어 업데이트 그룹에 수동으로 추가하거나 Configuration Manager를 통해 ADR을 사용하면 소프트웨어 업데이트를 새로운 또는 기존 소프트웨어 업데이트 그룹에 자동으로 추가할 수 있습니다. 새 소프트웨어 업데이트 그룹에 소프트웨어 업데이트를 수동으로 추가하려면 다음 절차를 따르세요.  

#### <a name="to-manually-add-software-updates-to-a-new-software-update-group"></a>새 소프트웨어 업데이트 그룹에 소프트웨어 업데이트를 수동으로 추가하려면  

1.  Configuration Manager 콘솔에서 **소프트웨어 라이브러리**를 클릭합니다.  

2.  소프트웨어 라이브러리 작업 영역에서 **소프트웨어 업데이트**를 클릭합니다.  

3.  새 소프트웨어 업데이트 그룹에 추가할 소프트웨어 업데이트를 선택합니다.  

4.  **홈** 탭의 **업데이트** 그룹에서 **소프트웨어 업데이트 그룹 만들기**를 클릭합니다.  

5.  소프트웨어 업데이트 그룹의 이름을 지정하고 선택적으로 설명을 입력합니다. 이때 소프트웨어 업데이트 그룹에 어떤 유형의 소프트웨어 업데이트가 있는지 쉽게 알 수 있도록 충분한 정보를 제공하는 이름과 설명을 사용합니다. 계속하려면 **만들기**를 클릭합니다.  

6.  **소프트웨어 업데이트 그룹** 노드를 클릭하여 새 소프트웨어 업데이트 그룹을 표시합니다.  

7.  소프트웨어 업데이트 그룹을 선택하고 **홈** 탭의 **업데이트** 그룹에서 **구성원 표시** 를 클릭하여 그룹에 포함된 소프트웨어 업데이트의 목록을 표시합니다.  

##  <a name="a-namebkmk3downloadcontenta-step-3-download-the-content-for-the-software-update-group"></a><a name="BKMK_3DownloadContent"></a> 3단계: 소프트웨어 업데이트 그룹에 대한 콘텐츠 다운로드  
 소프트웨어 업데이트를 배포하기 전에 선택적으로 소프트웨어 업데이트 그룹에 포함된 소프트웨어 업데이트의 콘텐츠를 다운로드할 수 있습니다. 소프트웨어 업데이트를 배포하기 전에 배포 지점에서 해당 콘텐츠를 사용할 수 있는지 확인하려면 이 작업을 선택하면 됩니다. 이렇게 하면 콘텐츠 제공과 관련해 발생할 수 있는 예기치 않은 문제를 최소화할 수 있습니다. 이 단계는 건너뛸 수 있습니다. 그 다음에는 콘텐츠가 배포 프로세스의 일부로 배포 지점에 다운로드되고 복사됩니다. 소프트웨어 업데이트 그룹에 소프트웨어 업데이트에 대한 콘텐츠를 다운로드하려면 다음 절차를 따르세요.  



#### <a name="to-download-content-for-the-software-update-group"></a>소프트웨어 업데이트 그룹에 대해 콘텐츠를 다운로드하려면
[!INCLUDE[downloadupdates](..\includes\downloadupdates.md)]
<!--- 1.  In the Configuration Manager console, click **Software Library**.  

2.  In the Software Library workspace, expand **Software Updates**, and click **Software Update Groups**.  

3.  Select the software update group for which you want to download content.  

4.  On the **Home** tab, in the **Update Group** group, click **Download**. The **Download Software Updates Wizard** opens.  

5.  On the **Deployment Package** page, configure the following settings:  

    1.  **Select deployment package**: Select this setting to use an existing deployment package for the software updates in the deployment.  

        > [!NOTE]  
        >  Software updates that have already been downloaded to the selected deployment package are not downloaded again.  

    2.  **Create a new deployment package**: Select this setting to create a new deployment package for the software updates in the deployment. Configure the following settings:  

        -   **Name**: Specifies the name of the deployment package. This must be a unique name that describes the package content. It is limited to 50 characters.  

        -   **Description**: Specifies the description of the deployment package. The package description provides information about the package contents and is limited to 127 characters.  

        -   **Package source**: Specifies the location of the software update source files.  Type a network path for the source location, for example, **\\\server\sharename\path**, or click **Browse** to find the network location. You must create the shared folder for the deployment package source files before you proceed to the next page.  

            > [!NOTE]  
            >  The deployment package source location that you specify cannot be used by another software deployment package.  

            > [!IMPORTANT]  
            >  The SMS Provider computer account and the user that is running the wizard to download the software updates must both have **Write** NTFS permissions on the download location. You should carefully restrict access to the download location in order to reduce the risk of attackers tampering with the software update source files.  

            > [!IMPORTANT]  
            >  You can change the package source location in the deployment package properties after Configuration Manager creates the deployment package. But if you do so, you must first copy the content from the original package source to the new package source location.  

     Click **Next**.  

6.  On the Distribution Points page, select the distribution points or distribution point groups that are used to host the software update files defined in the new deployment package, and then click **Next**.  

7.  On the Distribution Settings page, specify the following settings:  

    -   **Distribution priority**: Use this setting to specify the distribution priority for the deployment package. The distribution priority applies when the deployment package is sent to distribution points at child sites. Distribution packages are sent in priority order: **High**, **Medium**, or **Low**. Packages with identical priorities are sent in the order in which they were created. If there is no backlog, the package will process immediately regardless of its priority. By default, packages are sent using **Medium** priority.  

    -   **Distribute the content for this package to preferred distribution points**: Use this setting to enable on-demand content distribution to preferred distribution points. When this setting is enabled, the management point creates a trigger for the distribution manager to distribute the content to all preferred distribution points when a client requests the content for the package and the content is not available on any preferred distribution points. For more information about preferred distribution points and on-demand content, see [Content source location scenarios](../../core/plan-design/hierarchy/fundamental-concepts-for-content-management.md#bkmk_CSLscenarios).  

    -   **Prestaged distribution point settings**: Use this setting to specify how you want to distribute content to prestaged distribution points. Choose one of the following options:  

        -   **Automatically download content when packages are assigned to distribution points**: Use this setting to ignore the prestage settings and distribute content to the distribution point.  

        -   **Download only content changes to the distribution point**: Use this setting to prestage the initial content to the distribution point, and then distribute content changes to the distribution point.  

        -   **Manually copy the content in this package to the distribution point**: Use this setting to always prestage content on the distribution point. This is the default setting.  

         For more information about prestaging content to distribution points, see [Use Prestaged content](../../core/servers/deploy/configure/deploy-and-manage-content.md#bkmk_prestage).  

     Click **Next**.  

8.  On the Download Location page, specify location that Configuration Manager will use to download the software update source files. As needed, use the following options:  

    -   **Download software updates from the Internet**: Select this setting to download the software updates from the location on the Internet. This is the default setting.  

    -   **Download software updates from a location on the local network**: Select this setting to download software updates from a local folder or shared network folder. Use this setting when the computer running the wizard does not have Internet access.  

        > [!NOTE]  
        >  When you use this setting, download the software updates from any computer with Internet access, and then copy the software updates to a location on the local network that is accessible from the computer running the wizard.  

     Click **Next**.  

9. On the Language Selection page, specify the languages for which the selected software updates are to be downloaded, and then click **Next**. Configuration Manager downloads the software updates only if they are available in the selected languages. Software updates that are not language-specific are always downloaded.  

10. On the Summary page, verify the settings that you selected in the wizard, and then click **Next** to download the software updates.  

11. On the Completion page, verify that the software updates were successfully downloaded, and then click **Close**. --->

#### <a name="to-monitor-content-status"></a>콘텐츠 상태를 모니터링하려면
1. 소프트웨어 업데이트에 대해 콘텐츠 상태를 모니터링하려면 Configuration Manager 콘솔에서 **모니터링**을 클릭합니다.  

2. 모니터링 작업 영역에서 **배포 상태**를 확장한 후 **콘텐츠 상태**를 클릭합니다.  

3. 이전에 확인했던 소프트웨어 업데이트 패키지를 선택하여 소프트웨어 업데이트 그룹의 소프트웨어 업데이트를 다운로드합니다.  

4. **홈** 탭의 **콘텐츠** 그룹에서 **상태 보기**를 클릭합니다.  

##  <a name="a-namebkmk4deployupdategroupa-step-4-deploy-the-software-update-group"></a><a name="BKMK_4DeployUpdateGroup"></a> 4단계: 소프트웨어 업데이트 그룹 배포  
 배포할 소프트웨어 업데이트를 결정하고 이 소프트웨어 업데이트를 소프트웨어 업데이트 그룹에 추가하고나면 소프트웨어 업데이트 그룹에서 이 소프트웨어 업데이트를 수동으로 배포할 수 있습니다. 소프트웨어 업데이트 그룹에서 소프트웨어 업데이트를 수동으로 배포하려면 다음 절차를 따르세요.  

#### <a name="to-manually-deploy-the-software-updates-in-a-software-update-group"></a>소프트웨어 업데이트 그룹에서 소프트웨어 업데이트를 수동으로 배포하려면  

1.  Configuration Manager 콘솔에서 **소프트웨어 라이브러리**를 클릭합니다.  

2.  소프트웨어 라이브러리 작업 영역에서 **소프트웨어 업데이트**를 확장한 다음 **소프트웨어 업데이트 그룹**을 클릭합니다.  

3.  배포하려는 소프트웨어 업데이트 그룹을 선택합니다.  

4.  **홈** 탭의 **배포** 그룹에서 **배포**를 클릭합니다. **소프트웨어 업데이트 배포 마법사** 가 열립니다.  

5.  일반 페이지에서 다음 설정을 구성합니다.  

    -   **이름**: 배포의 이름을 지정합니다. 배포에는 배포의 용도를 설명하고 Configuration Manager 사이트의 다른 배포로부터 구별해주는 고유 이름이 있어야 합니다. 기본적으로 Configuration Manager에서는 **Microsoft 소프트웨어 업데이트 -** <*날짜*><*시간*> 형식으로 된 배포 이름을 자동으로 제공합니다.  

    -   **설명**: 배포의 설명을 지정합니다. 이를 통해 배포에 대한 요약 설명과 Configuration Manager 사이트의 다른 배포로부터 해당 배포를 식별 및 구별하는 데 도움이 되는 기타 관련 정보를 제공합니다. 설명 필드는 선택 사항이며 길이는 256자로 제한되어 있고 기본값은 공백입니다.  

    -   **소프트웨어 업데이트/소프트웨어 업데이트 그룹**: 표시된 소프트웨어 업데이트 그룹 또는 소프트웨어 업데이트가 올바른지 확인합니다.  

    -   **배포 템플릿 선택**: 이전에 저장된 배포 템플릿을 적용할지 여부를 지정합니다. 배포 템플릿에 여러 공통 소프트웨어 업데이트 배포 속성을 포함하도록 구성한 후 그 뒤에 소프트웨어 업데이트를 배포할 때 이 템플릿을 적용하면 비슷한 배포 간에 일관성을 유지할 수 있고 시간을 절약할 수 있습니다.  

    -   **컬렉션**: 배포에 대해 해당되는 컬렉션을 지정합니다. 컬렉션의 구성원은 배포에 정의된 소프트웨어 업데이트를 받습니다.  

6.  배포 설정 페이지에서 다음 설정을 구성합니다.  

    -   **배포 유형**: 소프트웨어 업데이트 배포의 배포 유형을 지정합니다. 필수 소프트웨어 업데이트 배포를 만들려면 **필수** 를 선택합니다. 이 경우 소프트웨어 업데이트는 구성된 설치 최종 기한 안에 클라이언트에 자동으로 설치됩니다. 사용자가 소프트웨어 센터에서 설치할 수 있는 선택적 소프트웨어 업데이트 배포를 만들려면 **사용 가능** 을 선택합니다.  

        > [!IMPORTANT]  
        >  소프트웨어 업데이트 배포를 만든 후 나중에 배포 유형을 변경할 수 없습니다.  

        > [!NOTE]  
        >  **필수** 로 배포된 소프트웨어 업데이트 그룹은 백그라운드로 다운로드되고 BITS 설정이 구성된 경우 이 설정을 따릅니다.  
        > 그러나 **사용 가능** 으로 배포된 소프트웨어 업데이트 그룹은 포그라운드로 다운로드되고 BITS 설정을 무시합니다.  

    -   **필수 배포를 위해 클라이언트의 최대 절전 모드를 해제하도록 Wake-On-LAN 사용**: 배포에 있는 하나 이상의 소프트웨어 업데이트가 필요한 컴퓨터에 절전 모드 해제 패킷을 보내도록 최종 기한에 Wake-On-LAN을 사용할지 여부를 지정합니다. 이 설정을 선택하면 설치 최종 기한 시점에 절전 모드인 모든 컴퓨터는 절전 모드에서 해제되므로 소프트웨어 업데이트 설치를 시작할 수 있습니다. 이 경우 배포 내의 소프트웨어 업데이트가 필요하지 않은 절전 모드 클라이언트는 작동을 시작하지 않습니다. 기본적으로 이 설정은 사용되지 않으며 **배포 유형** 이 **필수**로 설정된 경우에만 사용할 수 있습니다.  

        > [!WARNING]  
        >  이 옵션을 사용하려면 먼저 컴퓨터와 네트워크에 Wake-On-LAN을 구성해야 합니다.  

    -   **세부 정보 수준**: 클라이언트 컴퓨터에서 보고하는 상태 메시지에 대해 세부 정보 수준을 지정합니다.  

7.  일정 페이지에서 다음 설정을 구성합니다.  

    -   **일정 평가**: 사용 가능한 시간 및 설치 최종 기한 시간이 UTC 또는 Configuration Manager 콘솔을 실행하는 컴퓨터의 현지 시간 중 어느 시간에 따라 평가되는지 지정합니다.  

        > [!NOTE]  
        >  현지 시간을 선택한 다음 **소프트웨어를 사용할 수 있는 시간** 또는 **설치 최종 기한**에 대해 **가능한 한 빨리**를 선택하면 업데이트를 사용할 수 있거나 업데이트가 클라이언트에 설치될 때 Configuration Manager 콘솔을 실행하는 컴퓨터의 현재 시간이 평가하는 데 사용됩니다. 클라이언트가 다른 표준 시간대에 있는 경우 이러한 작업은 평가 시간 클라이언트의 시간에 도달 하면 발생 합니다.  

    -   **소프트웨어를 사용할 수 있는 시간**: 클라이언트에서 소프트웨어 업데이트를 사용할 수 있는 시점을 지정하려면 다음 설정 중 하나를 선택합니다.  

        -   **가능하면 빨리**: 배포 내의 소프트웨어 업데이트를 클라이언트에서 가능한 한 빨리 사용할 수 있도록 하려면 이 설정을 선택합니다. 배포가 만들어지면 클라이언트 정책이 업데이트되고, 클라이언트는 다음 클라이언트 정책 폴링 주기에서 배포를 인식하게 되며, 그런 다음 소프트웨어 업데이트가 설치용으로 제공됩니다.  

        -   **시간 지정**: 배포 내의 소프트웨어 업데이트를 클라이언트에서 특정 날짜 및 시간에 사용할 수 있도록 하려면 이 설정을 선택합니다. 배포가 만들어지면 클라이언트 정책이 업데이트되고 클라이언트는 다음 클라이언트 정책 폴링 주기에서 배포를 인식하게 됩니다. 그러나 배포 내의 소프트웨어 업데이트는 지정된 날짜 및 시간이 지날 때까지 설치용으로 사용할 수 없습니다.  

    -   **설치 최종 기한**:배포 내의 소프트웨어 업데이트에 대한 설치 최종 기한을 지정하려면 다음 설정 중 하나를 선택합니다.  

        > [!NOTE]  
        >  배포 설정 페이지에서 **배포 유형** 이 **필수** 로 설정된 경우에만 설치 최종 기한 설정을 구성할 수 있습니다.  

        -   **가능하면 빨리**: 배포 내의 소프트웨어 업데이트를 가능한 한 빨리 자동으로 설치하려면 이 설정을 선택합니다.  

        -   **시간 지정**: 배포 내의 소프트웨어 업데이트를 특정 날짜 및 시간에 자동으로 설치하려면 이 설정을 선택합니다.  

        > [!NOTE]  
        >  실제 설치 최종 기한 시간은 사용자가 구성하는 특정 시간에 최대 2시간의 임의 시간을 더한 시간입니다. 이 설정을 사용하면 대상 컬렉션의 모든 클라이언트 컴퓨터가 배포 내의 소프트웨어 업데이트를 동시에 설치하는 데서 발생할 영향을 최소화할 수 있습니다.  
        >   
        >  필수 소프트웨어 업데이트에 대해 설치 임의 설정 지연 시간을 사용하지 않도록 **컴퓨터 에이전트** 클라이언트 설정인 **최종 기한 임의 설정 사용 안 함** 을 구성할 수 있습니다. 자세한 내용은 [Computer Agent](../../core/clients/deploy/about-client-settings.md#computer-agent)을 참조하세요.  

8.  사용자 환경 페이지에서 다음 설정을 구성합니다.  

    -   **사용자 알림**: 구성된 **소프트웨어를 사용할 수 있는 시간** 에 클라이언트 컴퓨터에 소프트웨어 센터 내 소프트웨어 업데이트의 알림을 표시할지 여부와 클라이언트 컴퓨터에 사용자 알림을 표시할지 여부를 지정합니다. 배포 설정 페이지에서 **배포 유형** 이 **사용 가능** 으로 설정된 경우 **소프트웨어 센터에 모든 알림 숨기기**를 선택할 수 없습니다.  

    -   **최종 기한 동작**: *배포 설정 페이지에서 **배포 유형*이 **필수***로 설정된 경우에만 사용 가능합니다.*   
    소프트웨어 업데이트 배포에 대해 최종 기한에 도달하는 경우 수행할 동작을 지정합니다. 배포 내의 소프트웨어 업데이트를 설치할지 여부를 지정합니다. 또한 구성된 유지 관리 기간에 관계없이 소프트웨어 업데이트 설치 후 시스템 다시 시작을 수행할지 여부를 지정합니다. 유지 관리 기간에 대한 자세한 내용은 [유지 관리 기간을 사용하는 방법](../../core/clients/manage/collections/use-maintenance-windows.md)을 참조하세요.  

    -   **장치 다시 시작 동작**: *배포 설정 페이지에서 **배포 유형*이 **필수***로 설정된 경우에만 사용 가능합니다.*    
    소프트웨어 업데이트가 설치된 후 설치 완료를 위해 시스템 다시 시작이 필요한 경우 서버 및 워크스테이션에서 시스템 다시 시작을 보류할지 여부를 지정합니다.  

        > [!IMPORTANT]  
        >  시스템 다시 시작의 보류는 서버 환경을 비롯해 소프트웨어 업데이트를 설치하는 컴퓨터가 기본적으로 다시 시작하지 않도록 하려는 경우에 유용한 방법입니다. 그러나 이렇게 하면 컴퓨터를 보안이 설정되지 않은 상태로 둘 수 있으며 반면에 강제 다시 시작을 허용하면 소프트웨어 업데이트 설치를 즉시 완료하는 데 도움이 됩니다.

    -   **Windows Embedded 장치에 대한 쓰기 필터 처리**: 쓰기 필터가 활성화된 Windows Embedded 장치에 소프트웨어 업데이트를 배포할 경우 소프트웨어 업데이트를 임시 오버레이에 설치하도록 지정하고 변경 내용을 나중에 커밋하거나 설치 최종 기한에 또는 유지 관리 기간 중 커밋하도록 지정할 수 있습니다. 유지 관리 기간 동안이나 설치 최종 기한에 변경 내용을 커밋하는 경우 장치를 다시 시작해야 하며 변경 내용이 장치에 유지됩니다.  

        > [!NOTE]  
        >  소프트웨어 업데이트를 Windows Embedded 장치에 배포할 경우 해당 장치가 유지 관리 기간이 구성된 컬렉션의 구성원인지 확인하세요.  

    - **다시 시작 시의 소프트웨어 업데이트 배포 재평가 동작**: Configuration Manager 버전 1606부터는 클라이언트가 소프트웨어 업데이트를 설치하고 다시 시작된 직후에 소프트웨어 업데이트 준수 검사를 실행하도록 소프트웨어 업데이트 배포를 구성하려면 이 설정을 선택합니다. 이렇게 하면 클라이언트가 다시 시작된 후 해당하는 추가 소프트웨어 업데이트를 확인한 다음, 동일한 유지 관리 기간 동안 해당 업데이트를 설치하여 규격을 준수할 수 있습니다.

9. 경고 페이지에서 Configuration Manager 및 System Center Operations Manager가 이 배포에 대해 경고를 생성하는 방식을 구성합니다. 배포 설정 페이지에서 **배포 유형** 이 **필수** 로 설정된 경우에만 경고를 구성할 수 있습니다.  

    > [!NOTE]  
    >  **소프트웨어 라이브러리** 작업 영역의 **소프트웨어 업데이트** 노드에서 최근 소프트웨어 업데이트 경고를 살펴볼 수 있습니다.  

10. 다운로드 설정 페이지에서 다음 설정을 구성합니다.  

    -   저속 네트워크에 연결되어 있거나 대체 콘텐츠 위치를 사용 중인 클라이언트에서 소프트웨어 업데이트를 다운로드 및 설치할지 여부를 지정합니다.  

    -   기본 배포 지점에서 소프트웨어 업데이트의 콘텐츠를 사용할 수 없을 때 클라이언트가 대체 배포 지점에서 소프트웨어 업데이트를 다운로드 및 설치할지 여부를 지정합니다.  

    -   **클라이언트가 동일한 서브넷에 있는 다른 클라이언트와 콘텐츠를 공유하도록 허용**: 콘텐츠 다운로드를 위해 BranchCache를 사용할지 여부를 지정합니다. BranchCache에 대한 자세한 내용은 [콘텐츠 관리 관련 개념](../../core/plan-design/hierarchy/fundamental-concepts-for-content-management.md#branchcache)을 참조하세요.  

    -   배포 지점에서 소프트웨어 업데이트를 사용할 수 없는 경우 인트라넷에 연결된 클라이언트가 Microsoft 업데이트에서 소프트웨어 업데이트를 다운로드할지 여부를 지정합니다.  

    -   은 설치 최종 기한에 도달한 후 클라이언트에서 요금제 인터넷 연결을 사용하여 콘텐츠를 다운로드하도록 허용할지 여부를 지정합니다. 때로 인터넷 공급자는 사용자가 요금제 인터넷 연결을 사용할 경우 보내고 받는 데이터 양을 기준으로 요금을 청구하기도 합니다.  

    > [!NOTE]  
    >  클라이언트는 배포 내 소프트웨어 업데이트에 대해 관리 지점에서 콘텐츠 위치를 요청합니다. 다운로드 동작은 배포 지점, 배포 패키지 및 이 페이지의 설정 등을 어떻게 구성했는지에 따라 달라집니다. 자세한 내용은 [Content source location scenarios](../../core/plan-design/hierarchy/content-source-location-scenarios.md)을 참조하세요.  

11. [3단계: 소프트웨어 업데이트 그룹에 대한 콘텐츠 다운로드](#BKMK_3DownloadContent)를 수행한 경우 배포 패키지, 배포 지점 및 언어 선택 페이지는 표시되지 않으며 마법사의 15단계로 건너뛸 수 있습니다.  

    > [!IMPORTANT]  
    >  이전에 사이트 서버의 콘텐츠 라이브러리에 다운로드한 소프트웨어 업데이트는 다시 다운로드되지 않습니다. 이는 소프트웨어 업데이트에 대한 새 배포 패키지를 만든 경우에도 마찬가지입니다. 이전에 이미 모든 소프트웨어 업데이트가 다운로드된 경우 마법사는 15단계 **언어 선택** 페이지로 건너뜁니다.  

12. 배포 패키지 페이지에서 기존 배포 패키지를 선택하거나 다음 설정을 구성하여 새 배포 패키지를 지정하세요.  

    1.  **이름**: 배포 패키지의 이름을 지정합니다. 이 이름은 패키지 콘텐츠를 설명하는 고유 이름이어야 하며 길이는 50자로 제한됩니다.  

    2.  **설명**: 배포 패키지에 대한 정보를 제공하는 설명을 지정합니다. 설명의 길이는 127자로 제한됩니다.  

    3.  **패키지 원본**: 소프트웨어 업데이트 원본 파일의 위치를 지정합니다.  원본 위치의 네트워크 경로(예: **\\\server\sharename\path**)를 입력하거나 **찾아보기** 를 클릭하여 네트워크 위치를 검색합니다. 다음 페이지를 진행하기 전에 배포 패키지 원본 파일에 대한 공유 폴더를 만들어야 합니다.  

        > [!NOTE]  
        >  지정되는 배포 패키지 원본 위치는 다른 소프트웨어 배포 패키지에서 사용할 수 없습니다.  

        > [!IMPORTANT]  
        >  SMS 공급자 컴퓨터 계정 및 소프트웨어 업데이트 다운로드를 위해 마법사를 실행하는 사용자는 모두 다운로드 위치에 대해 **쓰기** NTFS 권한을 보유해야 합니다. 공격자가 소프트웨어 업데이트 원본 파일을 변조하는 위험을 줄이기 위해 다운로드 위치에 대한 액세스 권한은 신중하게 제한해야 합니다.  

        > [!IMPORTANT]  
        >  Configuration Manager에서 배포 패키지를 만든 후 배포 패키지 속성에서 패키지 원본 위치를 변경할 수 있습니다. 그러나 이렇게 하려면 먼저 콘텐츠를 원래 패키지 원본에서 새 패키지 원본 위치로 복사해야 합니다.  

    4.  **보내기 우선 순위**: 배포 패키지의 보내기 우선 순위를 지정합니다. Configuration Manager는 패키지를 배포 지점에 보낼 때 배포 패키지의 보내기 우선 순위를 사용합니다. 배포 패키지는 높음, 중간 또는 낮음의 우선 순위에 따라 보내집니다. 우선 순위가 서로 같은 패키지들은 만들어진 순서에 따라 보내집니다. 백로그가 없는 경우 패키지는 우선 순위에 관계없이 즉시 처리됩니다.  

13. 배포 지점 페이지에서 소프트웨어 업데이트 파일을 호스트할 배포 지점 또는 배포 지점 그룹을 지정합니다. 배포 지점에 대한 자세한 내용은 [배포 지점 구성](../../core/servers/deploy/configure/install-and-configure-distribution-points.md#bkmk_configs) 섹션을 참조하세요.  

14. 다운로드 위치 페이지에서 소프트웨어 업데이트 파일을 인터넷에서 다운로드할지, 아니면 로컬 네트워크에서 다운로드할지를 지정합니다. 다음 설정을 구성합니다.  

    -   **인터넷에서 소프트웨어 업데이트 다운로드**: 인터넷의 지정한 위치에서 소프트웨어 업데이트를 다운로드하려면 이 설정을 선택합니다. 이 설정은 기본값으로 사용 가능합니다.  

    -   **내 네트워크 위치에서 소프트웨어 업데이트 다운로드**: 로컬 폴더 또는 공유 네트워크 폴더에서 소프트웨어 업데이트를 다운로드하려면 이 설정을 선택합니다. 이 설정은 마법사를 실행하는 컴퓨터에서 인터넷에 액세스할 수 없는 경우에 유용합니다. 소프트웨어 업데이트는 인터넷에 액세스할 수 있는 모든 컴퓨터에서 미리 다운로드할 수 있으며 로컬 네트워크상의 위치에 저장한 후 다음에 설치할 때 액세스할 수 있습니다.  

15. 언어 선택 페이지에서 선택한 소프트웨어 업데이트를 다운로드할 언어를 선택합니다. 소프트웨어 업데이트는 선택한 언어로 사용할 수 있는 경우에만 다운로드됩니다. 특정 언어에 한정되지 않는 소프트웨어 업데이트는 항상 다운로드됩니다. 기본적으로 마법사는 소프트웨어 업데이트 지점 속성에서 구성한 언어를 선택합니다. 다음 페이지로 진행하기 전에 하나 이상의 언어를 선택해야 합니다. 소프트웨어 업데이트에서 지원되지 않는 언어만 선택한 경우 해당 소프트웨어 업데이트의 다운로드는 실패합니다.  

16. 요약 페이지에서 설정을 검토합니다. 설정을 배포 템플릿으로 저장하려면 **템플릿으로 저장**을 클릭하고 이름을 입력한 후 템플릿에 포함하려는 설정을 선택하고 **저장**을 클릭합니다. 구성된 설정을 변경하려면 관련된 마법사 페이지를 클릭한 후 설정을 변경합니다.  

    > [!WARNING]  
    >  템플릿 이름에는 영숫자 ASCII 문자와 **\\** (백슬래시) 또는 **‘** (작은따옴표)를 사용할 수 있습니다.  

17. **다음** 을 클릭하여 소프트웨어 업데이트를 배포합니다.  

 마법사를 완료하면 Configuration Manager에서는 소프트웨어 업데이트를 사이트 서버의 콘텐츠 라이브러리에 다운로드하고, 소프트웨어 업데이트를 구성된 배포 지점에 배포한 다음, 소프트웨어 업데이트 그룹을 대상 컬렉션 내 클라이언트에 배포합니다. 배포 프로세스에 대한 자세한 내용은 [Software update deployment process](../understand/software-updates-introduction.md#BKMK_DeploymentProcess)(소프트웨어 업데이트 배포 프로세스)를 참조하세요.

## <a name="next-steps"></a>다음 단계
[소프트웨어 업데이트 모니터링](monitor-software-updates.md)



<!--HONumber=Dec16_HO2-->


