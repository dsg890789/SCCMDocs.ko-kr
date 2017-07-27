---
title: "MDM 기관 변경 | Microsoft Docs"
description: "Configuration Manager(하이브리드)에서 Intune 독립 실행형으로 또는 그 반대로 MDM 기관을 변경하는 방법에 알아봅니다."
keywords: 
author: dougeby
manager: angrobe
ms.date: 06/02/2017
ms.topic: article
ms.prod: configuration-manager
ms.technology:
- configmgr-hybrid
ms.assetid: cc397ab5-125f-4f17-905b-fab980194f49
ms.translationtype: Human Translation
ms.sourcegitcommit: 662901e850566756759fcfc61c58f3c0e56bc5aa
ms.openlocfilehash: b80fec937b50dca3ab995be281c44c3145300f9f
ms.contentlocale: ko-kr
ms.lasthandoff: 06/03/2017

---
# <a name="change-your-mdm-authority"></a>MDM 기관 변경
Configuration Manager 버전 1610 및 Microsoft Intune 버전 1705부터, Microsoft 지원에 문의하지 않고 기존의 관리 장치를 등록 취소했다가 다시 등록하지 않고도, MDM 기관을 변경할 수 있습니다.

## <a name="change-the-mdm-authority-to-intune-standalone"></a>MDM 기관을 Intune 독립 실행형으로 변경
이 섹션에서는 기존의 관리 장치를 등록 취소했다가 다시 등록하지 않고도 Configuration Manager 콘솔(하이브리드)에서 구성된 기존 Microsoft Intune 테넌트를 Intune 독립 실행형으로 변경합니다.

### <a name="key-considerations"></a>핵심 고려 사항
새 MDM 기관으로 변경한 후에는 장치가 체크 인되고 서비스와 동기화되기 전에 전환 시간(최대 8시간)이 필요할 수 있습니다. 등록된 장치가 변경 후에도 계속 관리되고 보호되도록 하려면 새 MDM 기관(Intune 독립 실행형)에서 설정을 구성해야 합니다. 를 참조하되 다음에 유의하십시오.
- 장치는 새 MDM 기관(Intune 독립 실행형)의 설정이 장치의 기존 설정을 대체하도록 변경 후에도 서비스에 연결되어야 합니다.
- MDM 기관을 변경한 후 이전 MDM 기관(하이브리드)의 일부 기본 설정(예: 프로필)이 최대 7일 동안 장치에 남아 있습니다. 새 MDM 기관에서 가능한 한 빨리 앱 및 설정(정책, 프로필, 앱 등)을 구성하고, 기존의 등록된 장치를 보유하는 사용자가 있는 사용자 그룹에 설정을 배포하는 것이 좋습니다. MDM 기관에서 변경이 수행되고 장치가 서비스에 연결되는 즉시, 새 MDM 기관에서 새 설정을 수신되므로 관리 및 보호의 부재가 나타나지 않습니다. 새 목표 정책이 장치의 기존 정책을 재정의합니다.
- 새 MDM 기관으로 변경한 후 Microsoft Intune 관리 콘솔의 준수 데이터가 정확히 보고될 때가지 최대 1주가 걸릴 수 있습니다. 그러나 Azure Active Directory 및 장치의 준수 상태는 정확하게 유지되므로 장치는 계속 보호됩니다.

### <a name="prepare-to-change-the-mdm-authority-to-intune-standalone"></a>MDM 기관을 Intune 독립 실행형으로 변경하기 위한 준비
다음 정보를 검토하여 MDM 기관 변경을 준비하세요.
- MDM 기관을 변경하는 옵션을 사용하려면 Configuration Manager 버전 1610 이상이 있어야 합니다.
- 새 MDM 기관으로 변경한 후 장치가 서비스에 연결되는 데 최대 8시간이 걸릴 수 있습니다.
- 현재 하이브리드에서 관리되는 모든 사용자는 MDM 기관 변경 전에 특히 Intune/EMS 라이선스가 할당되어야 합니다. 이를 통해 MDM 기관 변경 후에 사용자 및 해당 장치가 Intune 독립 실행형에서 관리될 수 있게 됩니다. 자세한 내용은 [사용자 계정에 Intune 라이선스 할당](https://docs.microsoft.com/intune/get-started/start-with-a-paid-subscription-to-microsoft-intune-step-4)을 참조하세요.
- MDM 기관 변경 전에 관리 사용자 계정에 Intune/EMS 라이선스가 할당되어 있는지와 관리 사용자 계정이 Intune에 로그인할 수 있는지 확인합니다. MDM 기관 변경 전에 Microsoft Intune 관리 콘솔에서 MDM 기관에는 **Configuration Manager로 설정**(하이브리드 테넌트)이 표시되어야 합니다.
- Configuration Manager 콘솔에서 모든 장치 등록 관리자 역할을 제거합니다. **관리** > **클라우드 서비스** > **Microsoft Intune 구독**으로 이동한 후 Microsoft Intune 구독을 선택하고 **속성**을 클릭한 후 **장치 등록 관리자** 탭을 클릭하고 모든 장치 등록 관리자 역할을 제거합니다.
- Configuration Manager 콘솔에서 기존 장치 범주를 제거합니다. **자산 및 준수** > **개요** > **장치 컬렉션**으로 이동한 후 **장치 범주 관리**를 선택하고 기존 장치 범주를 제거합니다.
- MDM 기관 변경 동안 최종 사용자에게 눈에 띌만한 영향은 발생하지 않습니다. 그러나 사용자가 장치를 켜고 변경 즉시 서비스에 연결하도록 이러한 변경 사항을 사용자에게 알릴 수 있습니다. 이렇게 하면 최대한 많은 장치가 가능한 한 빨리 새 기관을 통해 서비스에 연결되고 등록될 수 있게 됩니다.
- MDM 기관 변경 전에 Configuration Manager(하이브리드 테넌트)를 사용하여 iOS 장치를 관리하는 경우 이전에 Configuration Manager에서 사용했던 동일한 APNs(Apple Push Notification Service) 인증서가 갱신되고 Intune 독립 실행형에서 테넌트를 다시 설정하는 데 사용되도록 해야 합니다.

    > [!IMPORTANT]  
    > Intune 독립 실행형에 다른 APNs 인증서가 사용되면 이전에 등록된 모든 iOS 장치가 등록 취소되므로 다시 등록하는 과정을 진행해야 합니다. MDM 기관 변경 전에 Configuration Manager에서 iOS 장치를 관리하는 데 사용된 APNs 인증서를 정확히 알고 있어야 합니다. Apple Push Certificates 포털(https://identity.apple.com)에 나열된 동일한 인증서를 찾고, 해당 Apple ID가 원래 APNs 인증서를 만드는 데 사용된 사용자를 식별한 후 새 MDM 기관 변경의 일부로 동일한 APNs 인증서를 갱신하는 데 이 인증서를 사용할 수 있도록 합니다.  

### <a name="change-the-mdm-authority-to-intune-standalone"></a>MDM 기관을 Intune 독립 실행형으로 변경
MDM 기관을 Intune 독립 실행형으로 변경하는 프로세스는 다음과 같은 고급 단계를 포함합니다.  
- Configuration Manager 콘솔에서 **MDM 기관을 Microsoft Intune으로 변경** 옵션을 사용하여 기존 Microsoft Intune 구독을 제거합니다.
- Microsoft Intune 관리 콘솔에서 새 MDM 기관을 **Intune**으로 설정합니다.
- 갱신했던 동일한 APNs 인증서를 사용하여 Apple APNs 인증서를 구성합니다.
- Microsoft Intune 관리 콘솔에서 새 MDM 기관(Intune)의 새로운 설정 및 앱을 구성하고 배포합니다.
- 다음 번에 장치가 서비스에 연결되면 새 MDM 기관과 동기화되어 새 설정을 받습니다.

#### <a name="to-change-the-mdm-authority-to-intune-standalone"></a>MDM 기관을 Intune 독립 실행형으로 변경하려면
1.  Configuration Manager 콘솔에서 **관리** &gt; **개요** &gt; **Cloud Services** &gt; **Microsoft Intune 구독**으로 이동한 후 기존 Intune 구독을 삭제합니다.
2.  **MDM 기관을 Microsoft Intune으로 변경**을 클릭하고 **다음**을 클릭합니다.

    ![APNs 인증서 요청 다운로드](/sccm/mdm/deploy-use/media/mdm-change-delete-subscription.png)
3.  Configuration Manager에서 MDM 기관을 설정할 때 사용했던 Intune 테넌트에 로그인합니다.
4.  **다음** 을 클릭하여 마법사를 완료합니다.
5.  이제 MDM 기관이 다시 설정되었습니다. Intune 구독은 Configuration Manager 콘솔의 Microsoft Intune 구독 노드에 더 이상 표시되지 않습니다.
6.  이전에 사용한 동일한 Intune 테넌트를 사용하여 [Microsoft Intune 관리 콘솔](http://manage.microsoft.com)에 로그인합니다.
7.  MDM 기관이 다시 설정되었는지 확인하고 MDM 기관을 **Microsoft Intune**으로 설정합니다. MDM 기관을 변경하면 콘솔에 반영되어야 합니다. 자세한 내용은 [MDM 기관 설정 방법](https://docs.microsoft.com/en-us/intune/deploy-use/prerequisites-for-enrollment#step-2-set-mdm-authority)을 참조하세요.
<!-- [Azure portal](https://docs.microsoft.com/en-us/intune-azure/enroll-devices/set-mdm-authority) -->


### <a name="configure-the-apns-certificate"></a>APNs 인증서 구성
iOS 장치가 있는 경우 Intune에서 APNs 인증서를 구성해야 합니다.

#### <a name="to-configure-the-apns-certificate"></a>APNs 인증서를 구성하려면
1.  APNs 인증서 요청을 다운로드합니다.
    <!--The process is different depending on how you connect to Intune:
    **Azure portal**   
    In the [Azure portal](https://azure.portal.com), choose **More Services** &gt; **Monitoring + Management** &gt; **Intune**. On the **Intune** blade, choose **Device enrollment** &gt; **Apple Enrollment** &gt; **Apple MDM Push Certificate**, and then select **Download your CSR** to download and save the .csr file locally.   
    <br/>
    **Microsoft Intune administration console**   -->
    [Microsoft Intune 관리 콘솔](http://manage.microsoft.com)에서 **관리** &gt; **모바일 장치 관리** &gt; **iOS 및 Mac OS X** &gt; **APNs 인증서 업로드**로 이동한 후 **APNs 인증서 요청 다운로드**를 선택합니다. 인증서 서명 요청(.csr) 파일을 로컬로 저장합니다.
    > [!IMPORTANT]    
    > 새 인증서 서명 요청을 다운로드해야 합니다. 기존 파일은 사용하지 않습니다. 이 파일을 사용하면 실패합니다.

    ![APNs 인증서 요청 다운로드](/sccm/mdm/deploy-use/media/mdm-change-download-apns-certificate.png)

2.  [Apple Push Certificates 포털](http://go.microsoft.com/fwlink/?LinkId=269844)로 이동한 후 Configuration Manager(하이브리드)에서 사용했던 APNs 인증서를 이전에 만들고 갱신하는 데 사용한 **동일한** Apple ID로 로그인합니다.

    ![Apple Push Certificates 포털 로그인 페이지](/sccm/mdm/deploy-use/media/mdm-change-apns-portal.png)

3.  Configuration Manager(하이브리드)에서 사용했던 APNs 인증서를 선택하고 **갱신**을 클릭합니다.   

    ![APNs 갱신 대화 상자](/sccm/mdm/deploy-use/media/mdm-change-renew-apns.png)

4.  로컬로 다운로드한 APNs 인증서 서명 요청(.csr) 파일을 선택한 다음 **업로드**를 클릭합니다.

    ![Apple Push Certificates 포털 로그인 페이지](/sccm/mdm/deploy-use/media/mdm-change-renew-apns-upload.png)  
5.  동일한 APNs를 선택하고 **다운로드**를 클릭합니다. APNs(.pem) 인증서를 다운로드하고 파일을 로컬로 저장합니다.  

    ![Apple Push Certificates 포털 로그인 페이지](/sccm/mdm/deploy-use/media/mdm-change-renew-apns-download.png)

6.  이전에 사용한 것과 같은 Apple ID를 사용하여 갱신된 APNs 인증서를 Intune 테넌트에 업로드합니다.
<!--The process is different depending on how to connect to Intune:  
    **Azure portal**   
    In the [Azure portal](https://azure.portal.com), choose **More Services** &gt; **Monitoring + Management** &gt; **Intune**. On the **Intune** blade, choose **Device enrollment** &gt; **Apple Enrollment**  &gt; **Apple MDM Push Certificate**, enter your Apple ID in step 3, select the certificate (.pem) file in step 4, and then click **Upload**.     
    <br/>
    **Microsoft Intune administration console**    -->
    In the [Microsoft Intune administration console](http://manage.microsoft.com), go to **Administration** &gt; **Mobile Device Management** &gt; **iOS and Mac OS X** &gt; **Upload an APNs Certificate**, and then choose **Upload the APNs certificate**. Go to the certificate (.pem) file, choose **Open**, and then enter your **Apple ID**.   

    ![Upload the APNs certificate](/sccm/mdm/deploy-use/media/mdm-change-upload-apns-certificate.png)

### <a name="next-steps"></a>다음 단계
MDM 기관 변경이 완료되면 다음 단계를 검토합니다.
- 테넌트의 MDM 기관이 변경되었다는 사실을 Intune 서비스에서 감지하면 등록된 모든 장치로 알림 메시지를 전송하여 장치가 체크 인되고 서비스와 동기화됩니다(정기적으로 예약된 체크 인 이외로 수행). 따라서 테넌트의 MDM 기관이 하이브리드에서 Intune 독립 실행형으로 변경된 후에 전원이 켜져 있고 온라인 상태인 모든 장치는 서비스에 연결되고, 새 MDM 기관을 수신하고, Intune 독립 실행형으로 관리되게 됩니다. 이러한 서비스의 관리 및 보호가 중단되는 일은 없습니다.
- MDM 기관 변경 동안(또는 직후에) 전원이 꺼져 있거나 오프라인 상태인 장치는 전원이 켜지고 온라인 상태가 되면 새 MDM 기관에서 해당 서비스에 연결되고 서비스와 동기화됩니다.  

  iOS 장치는 APNs 인증서를 갱신하고 설정하는 데 추가 시간이 필요합니다. 따라서 iOS 장치는 초기 체크 인 요청을 받지 않습니다. iOS 장치는 MDM 기관 변경 동안(또는 직후에) 전원이 켜져 있고 온라인 상태이더라도 새 MDM 기관에서 해당 서비스에 등록되는 데 최대 8시간이 지연됩니다(예정된 다음 정기 체크 인 타이밍에 따라).    

  > [!IMPORTANT]
  > MDM 기관을 변경하는 시간과 갱신한 APNs 인증서가 새 기관으로 업로드되는 시간 중간에 iOS 장치에 대한 새 장치 등록 및 장치 체크 인을 수행하려고 하면 실패합니다. 따라서 MDM 기관을 변경한 후 가능한 한 빨리 APNs 인증서를 갱신하고 새 인증 기관에 업로드하는 것이 중요합니다.   

- 사용자는 장치에서 서비스로의 체크 인을 수동으로 시작하여 새 MDM 기관을 빠르게 변경할 수 있습니다. 회사 포털 앱을 사용하고 장치 준수 검사를 시작하여 이 작업을 쉽게 수행할 수 있습니다.
- MDM 기관이 변경되고, 장치가 체크 인되고 서비스와 동기화된 후 작업이 제대로 진행되는지 확인하려면 [Microsoft Intune 관리 콘솔](http://manage.microsoft.com)에서 장치를 찾아보세요. 이전에 Configuration Manager(하이브리드)에서 관리되던 장치는 이제 관리되는 장치로 표시됩니다.    
- MDM 기관 변경 동안 장치가 오프라인 상태일 때와 장치가 서비스로 체크 인될 때까지의 중간 기간이 있습니다. 이 중간 기간 동안 장치가 보호되고 제대로 작동되게 하기 위해 최대 7일 동안(또는 장치가 새 MDM 기관에 연결되고 기존 설정을 덮어쓰는 새 설정을 수신할 때까지) 장치에서 다음이 그대로 유지됩니다.
    - 전자 메일 프로필
    - VPN 프로필
    - 인증서 프로필
    - Wi-Fi 프로필
    - 구성 프로필
- 기존 설정을 덮어쓰고 새로 사용하려는 설정은 이전 이름과 같은 이름이어야 합니다. 그렇지 않으면 장치에서 프로필 및 정책이 중복될 수 있습니다.
    > [!TIP]   
    > 모범 사례는 MDM 기관 변경이 완료된 즉시, 모든 배포 뿐만 아니라 모든 관리 설정과 구성을 만드는 것입니다. 이렇게 하면 중간 기간 동안에도 장치가 보호되고 능동적으로 관리될 수 있습니다.   
-  MDM 기관을 변경한 후 다음 단계를 수행하여 새 장치가 새 기관에 성공적으로 등록되었는지 확인합니다.   
    - 새 장치 등록
    - 새로 등록된 장치가 Intune 관리 콘솔에 표시되어야 합니다.
    - 장치의 관리 콘솔에서 원격 잠금 등의 작업을 수행합니다. 성공한 경우 장치가 새 MDM 기관에서 관리되는 것입니다.
- 특정 장치에 문제가 있는 경우 등록을 취소했다가 다시 등록하여 가능한 한 빠른 시일 내에 장치가 새 기관에 연결되고 관리될 수 있도록 합니다.

<!-- After the change in MDM authority and devices check-in with the service, note the following:      - The updated compliance status of devices will only display in the Azure portal immediately.
- There will be a delay for compliance status of devices to display in the Intune administrative console.-->


## <a name="change-the-mdm-authority-to-configuration-manager-hybrid"></a>MDM 기관을 Configuration Manager(하이브리드)로 변경
이 섹션에서는 기존의 관리 장치를 등록 취소했다가 다시 등록하지 않고도 Intune에서 구성되고 MDM 기관이 **Microsoft Intune**(독립 실행형)으로 설정된 기존 Microsoft Intune 테넌트를 **Configuration Manager**(하이브리드)로 변경합니다.

### <a name="key-considerations"></a>핵심 고려 사항
새 MDM 기관으로 전환한 후에는 장치가 체크 인되고 서비스와 동기화되기 전에 전환 시간(최대 8시간)이 필요할 수 있습니다. 등록된 장치가 변경 후에도 계속 관리되고 보호되도록 하려면 새 MDM 기관(하이브리드)에서 설정을 구성해야 합니다. 를 참조하되 다음에 유의하십시오.
- 장치는 새 MDM 기관(Intune 독립 실행형)의 설정이 장치의 기존 설정을 대체하도록 변경 후에도 서비스에 연결되어야 합니다.
- MDM 기관을 변경한 후 이전 MDM 기관(Intune 독립 실행형)의 일부 기본 설정(예: 프로필)이 최대 7일 동안 또는 장치가 서비스에 처음 연결될 때까지 장치에 남아 있습니다. 새 MDM 기관(하이브리드)에서 가능한 한 빨리 앱 및 설정(정책, 프로필, 앱 등)을 구성하고, 기존의 등록된 장치를 보유하는 사용자가 있는 사용자 그룹에 설정을 배포하는 것이 좋습니다. MDM 기관에서 변경이 수행되고 장치가 서비스에 연결되는 즉시, 새 MDM 기관에서 새 설정을 수신되므로 관리 및 보호의 부재가 나타나지 않습니다.

### <a name="prepare-to-change-the-mdm-authority-to-configuration-manager-hybrid"></a>MDM 기관을 Configuration Manager(하이브리드)로 변경 준비
다음 정보를 검토하여 MDM 기관 변경을 준비하세요.
- MDM 기관을 변경하는 옵션을 사용하려면 Configuration Manager 버전 1610 이상이 있어야 합니다.
- 새 MDM 기관으로 변경한 후 장치가 서비스에 연결되는 데 최대 8시간이 걸릴 수 있습니다.
- Configuration Manager 콘솔에서 Intune 구독을 설정할 때 사용할 Intune 독립 실행형에서 현재 관리되는 모든 사용자가 포함된 Configuration Manager 사용자 컬렉션을 만듭니다. 이 작업은 사용자 및 해당 장치에 Configuration Manager 라이선스가 할당되고 MDM 기관 변경 후에 하이브리드 환경에서 관리되도록 하는 데 도움이 됩니다.
- IT 관리 사용자도 이 사용자 컬렉션에 포함되어야 합니다.  
- 변경 전에 MDM 기관은 Intune 관리 콘솔에서 **Microsoft Intune으로 설정**(독립 실행형)으로 표시됩니다.
- MDM 기관 변경 전에 Microsoft Intune 관리 콘솔에서 MDM 기관에는 **Microsoft Intune으로 설정**(독립 실행형 테넌트)이 표시되어야 합니다.
    > [!NOTE]    
    > MDM 기관에 **Intune 및 Office 365에서 관리**가 표시되면 Office 365 관리 MDM 장치는 MDM 기관을 **Configuration Manager**(하이브리드)로 변경하면 더 이상 관리되지 않습니다. MDM 기관을 변경하기 전에 해당 사용자에게 Intune 또는 Enterprise Mobility Suite에 대한 라이선스를 부여하는 것이 좋습니다.   

- [Microsoft Intune 관리 콘솔](http://manage.microsoft.com)에서 장치 등록 관리자 역할을 제거합니다. 자세한 내용은 [Intune에서 장치 등록 관리자 삭제](/intune-classic/deploy-use/enroll-corporate-owned-devices-with-the-device-enrollment-manager-in-microsoft-intune#delete-a-device-enrollment-manager-from-intune)를 참조하세요.
- 구성된 모든 장치 그룹 매핑을 해제합니다. 자세한 내용은 [Microsoft Intune에서 장치 그룹 매핑을 사용하여 장치 분류](/intune-classic/deploy-use/categorize-devices-with-device-group-mapping-in-microsoft-intune)를 참조하세요.
- MDM 기관 변경 동안 최종 사용자에게 눈에 띌만한 영향은 발생하지 않습니다. 그러나 사용자가 장치를 켜고 변경 즉시 서비스에 연결하도록 이러한 변경 사항을 사용자에게 알릴 수 있습니다. 이렇게 하면 최대한 많은 장치가 가능한 한 빨리 새 기관을 통해 서비스에 연결되고 등록될 수 있게 됩니다.
- MDM 기관 변경 전에 Intune 독립 실행형을 사용하여 iOS 장치를 관리하는 경우 이전에 Intune에서 사용했던 동일한 APNs(Apple Push Notification Service) 인증서가 갱신되고 Configuration Manager(하이브리드)에서 테넌트를 다시 설정하는 데 사용되도록 해야 합니다.    

    > [!IMPORTANT]  
    > 하이브리드에 다른 APNs 인증서가 사용되면 이전에 등록된 모든 iOS 장치가 등록 취소되므로 다시 등록하는 과정을 진행해야 합니다. MDM 기관 변경 전에 Intune에서 iOS 장치를 관리하는 데 사용된 APNs 인증서를 정확히 알고 있어야 합니다. Apple Push Certificates 포털(https://identity.apple.com)에 나열된 동일한 인증서를 찾고, 해당 Apple ID가 원래 APNs 인증서를 만드는 데 사용된 사용자를 식별한 후 새 MDM 기관 변경의 일부로 동일한 APNs 인증서를 갱신하는 데 이 인증서를 사용할 수 있도록 합니다.  

### <a name="change-the-mdm-authority-to-configuration-manager"></a>MDM 기관을 Configuration Manager로 변경
MDM 기관을 Configuration Manager(하이브리드)로 변경하는 프로세스는 다음과 같은 고급 단계를 포함합니다.  
- Configuration Manager 콘솔에서 Microsoft Intune 구독을 추가합니다.
- 갱신했던 동일한 APNs 인증서를 사용하여 Apple APNs 인증서를 구성합니다.
- Configuration Manager 콘솔에서 새 MDM 기관(하이브리드)의 새로운 설정 및 앱을 구성하고 배포합니다.
- 다음 번에 장치가 서비스에 연결되면 새 MDM 기관과 동기화되어 새 설정을 받습니다.

#### <a name="to-change-the-mdm-authority-to-configuration-manager"></a>MDM 기관을 Configuration Manager로 변경하려면
1.  Configuration Manager 콘솔에서 **관리** &gt; **개요** &gt; **Cloud Services** &gt; **Microsoft Intune 구독**으로 이동한 후 Intune 구독을 추가하도록 선택합니다.
2.  Intune에서 MDM 기관을 설정할 때 사용했던 Intune 테넌트에 로그인하고 **다음**을 클릭합니다.
3.  **내 MDM 기관을 Configuration Manager로 변경**을 선택하고 **다음**을 클릭합니다.
4.  계속해서 새 하이브리드 MDM 기관으로 관리할 모든 사용자가 포함될 사용자 컬렉션을 선택합니다.
5.  **다음** 을 클릭하여 마법사를 완료합니다.  
5.  이제 MDM 기관이 **Configuration Manager**로 변경됩니다.
6.  동일한 Intune 테넌트를 사용하여 [Microsoft Intune 관리 콘솔](http://manage.microsoft.com)에 로그인하고 MDM 기관이 **Configuration Manager로 설정**으로 변경되었는지 확인합니다.


### <a name="enable-ios-enrollment"></a>iOS 등록을 사용하도록 설정합니다.
iOS 장치가 있는 경우 Configuration Manager에서 APNs 인증서를 구성해야 합니다.

#### <a name="to-enable-ios-enrollment-and-configure-the-apns-certificate"></a>IOS 등록을 사용하도록 설정하고 APNs 인증서 구성

1. **인증서 서명 요청 다운로드**

    1.  Configuration Manager 콘솔에서 **관리** &gt; **Cloud Services** &gt; **Microsoft Intune 구독**으로 이동한 후 **APNs 인증서 요청 만들기**를 선택하여 **APNs CSR(인증서 서명 요청) 요청** 대화 상자를 엽니다.  
    2.  **찾아보기** 를 클릭하여 새 인증서 서명 요청(.csr) 파일을 저장할 경로를 찾습니다. 인증서 서명 요청(.csr) 파일을 로컬로 저장합니다.  
    3.  **다운로드**를 클릭합니다. 새 Microsoft Intune .csr 파일이 다운로드되고 Configuration Manager에 의해 저장됩니다.   

    > [!IMPORTANT]
    > 새 인증서 서명 요청을 다운로드해야 합니다. 기존 파일은 사용하지 않습니다. 이 파일을 사용하면 실패합니다.  

2.  [Apple Push Certificates 포털](http://go.microsoft.com/fwlink/?LinkId=269844)로 이동한 후 Intune 독립 실행형에서 사용했던 APNs 인증서를 이전에 만들고 갱신하는 데 사용한 **동일한** Apple ID로 로그인합니다.

    ![Apple Push Certificates 포털 로그인 페이지](/sccm/mdm/deploy-use/media/mdm-change-apns-portal.png)

3.  Intune 독립 실행형에서 사용했던 APNs 인증서를 선택하고 **갱신**을 클릭합니다.   

    ![APNs 갱신 대화 상자](/sccm/mdm/deploy-use/media/mdm-change-renew-apns.png)

4.  로컬로 다운로드한 APNs 인증서 서명 요청(.csr) 파일을 선택한 다음 **업로드**를 클릭합니다.

    ![Apple Push Certificates 포털 로그인 페이지](/sccm/mdm/deploy-use/media/mdm-change-renew-apns-upload.png)  
5.  동일한 APNs를 선택하고 **다운로드**를 클릭합니다. APNs(.pem) 인증서를 다운로드하고 파일을 로컬로 저장합니다.  

    ![Apple Push Certificates 포털 로그인 페이지](/sccm/mdm/deploy-use/media/mdm-change-renew-apns-download.png)

6.  이전에 사용한 것과 같은 Apple ID를 사용하여 갱신된 APNs 인증서를 하이브리드 테넌트에 업로드합니다.

    1.  Configuration Manager 콘솔에서 **관리** &gt; **Cloud Services** &gt; **Microsoft Intune 구독**으로 이동한 후 **플랫폼 구성** &gt; **iOS**를 선택합니다.  
    2.  **Microsoft Intune 구독 속성** 대화 상자에서 **APNs 인증서** 탭을 선택하고 **iOS 및 Mac OS X(MDM) 등록 사용** 확인란을 클릭하여 선택합니다.  
    3.  **찾아보기**를 클릭하고 Apple에서 다운로드한 APNs 인증서(.cer) 파일이 있는 위치로 이동합니다. Configuration Manager가 APNs 인증서 정보를 표시합니다. **확인** 을 클릭하여 APN 인증서를 Intune에 저장합니다.  

        ![Intune 구독 속성 페이지 - iOS](/sccm/mdm/deploy-use/media/mdm-change-subscription-properties-ios.png)

### <a name="enable-android-enrollment"></a>Android 등록 사용
1. Configuration Manager 콘솔에서 **관리** &gt; **Cloud Services** &gt; **Microsoft Intune 구독**으로 이동한 후 **플랫폼 구성** &gt; **Android**를 선택합니다.  
2. **Android 등록 사용**을 선택하고 **확인**을 클릭합니다.

### <a name="enable-windows-enrollment"></a>Windows 등록 사용
1. Configuration Manager 콘솔에서 **관리** &gt; **Cloud Services** &gt; **Microsoft Intune 구독**으로 이동한 후 **플랫폼 구성** &gt; **Windows**를 선택합니다.  
2. **Windows 등록 사용**을 선택하고 **확인**을 클릭합니다.

### <a name="enable-windows-phone-enrollment"></a>Windows Phone 등록 사용
1. Configuration Manager 콘솔에서 **관리** &gt; **Cloud Services** &gt; **Microsoft Intune 구독**으로 이동한 후 **플랫폼 구성** &gt; **Windows Phone**을 선택합니다.  
2. 사용하도록 설정하려는 플랫폼을 선택하고 **확인**을 클릭합니다.


### <a name="next-steps"></a>다음 단계
MDM 기관 변경이 완료되면 다음 단계를 검토합니다.
- 테넌트의 MDM 기관이 변경되었다는 사실을 Intune 서비스에서 감지하면 등록된 모든 장치로 알림 메시지를 전송하여 장치가 체크 인되고 서비스와 동기화됩니다(정기적으로 예약된 체크 인 이외로 수행). 따라서 테넌트의 MDM 기관이 Intune 독립 실행형에서 하이브리드로 변경된 후에 전원이 켜져 있고 온라인 상태인 모든 장치는 서비스에 연결되고, 새 MDM 기관을 수신하고, 하이브리드에서 관리되게 됩니다. 이러한 서비스의 관리 및 보호가 중단되는 일은 없습니다.
- MDM 기관 변경 동안(또는 직후에) 전원이 켜져 있고 온라인 상태인 장치의 경우에도 새 MDM 기관에서 해당 서비스에 등록되는 데 최대 8시간이 지연됩니다(예정된 다음 정기 체크 인 타이밍에 따라).    

  > [!IMPORTANT]
  > MDM 기관을 변경하는 시간과 갱신한 APNs 인증서가 새 기관으로 업로드되는 시간 중간에 iOS 장치에 대한 새 장치 등록 및 장치 체크 인을 수행하려고 하면 실패합니다. 따라서 MDM 기관을 변경한 후 가능한 한 빨리 APNs 인증서를 갱신하고 새 인증 기관에 업로드하는 것이 중요합니다.

- 사용자는 장치에서 서비스로의 체크 인을 수동으로 시작하여 새 MDM 기관을 빠르게 변경할 수 있습니다. 회사 포털 앱을 사용하고 장치 준수 검사를 시작하여 이 작업을 쉽게 수행할 수 있습니다.
- MDM 기관이 변경되고, 장치가 체크 인되고 서비스와 동기화된 후 작업이 제대로 진행되는지 확인하려면 Configuration Manager 콘솔에서 장치를 찾아보세요. 이전에 Intune에서 관리되던 장치는 이제 Configuration Manager 콘솔에서 관리되는 장치로 표시됩니다.    
- MDM 기관 변경 동안 장치가 오프라인 상태일 때와 장치가 서비스로 체크 인될 때까지의 중간 기간이 있습니다. 이 중간 기간 동안 장치가 보호되고 제대로 작동되게 하기 위해 최대 7일 동안(또는 장치가 새 MDM 기관에 연결되고 기존 설정을 덮어쓰는 새 설정을 수신할 때까지) 장치에서 다음이 그대로 유지됩니다.
    - 전자 메일 프로필
    - VPN 프로필
    - 인증서 프로필
    - Wi-Fi 프로필
    - 구성 프로필
- 새 MDM 기관으로 변경한 후 Microsoft Intune 관리 콘솔의 준수 데이터가 정확히 보고될 때가지 최대 1주가 걸릴 수 있습니다. 그러나 Azure Active Directory 및 장치의 준수 상태는 정확하게 유지되므로 장치는 계속 보호됩니다.
- 기존 설정을 덮어쓰고 새로 사용하려는 설정은 이전 이름과 같은 이름이어야 합니다. 그렇지 않으면 장치에서 프로필 및 정책이 중복될 수 있습니다.
    > [!TIP]   
    > 모범 사례는 MDM 기관 변경이 완료된 즉시, 모든 배포 뿐만 아니라 모든 관리 설정과 구성을 만드는 것입니다. 이렇게 하면 중간 기간 동안에도 장치가 보호되고 능동적으로 관리될 수 있습니다.   
-  MDM 기관을 변경한 후 다음 단계를 수행하여 새 장치가 새 기관에 성공적으로 등록되었는지 확인합니다.   
    - 새 장치 등록
    - 새로 등록된 장치가 Configuration Manager 콘솔에 표시되어야 합니다.
    - 장치의 관리 콘솔에서 원격 잠금 등의 작업을 수행합니다. 성공한 경우 장치가 새 MDM 기관에서 관리되는 것입니다.
- 특정 장치에 문제가 있는 경우 등록을 취소했다가 다시 등록하여 가능한 한 빠른 시일 내에 장치가 새 기관에 연결되고 관리될 수 있도록 합니다.

