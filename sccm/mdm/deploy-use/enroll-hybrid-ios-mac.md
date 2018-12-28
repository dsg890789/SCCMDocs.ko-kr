---
title: Microsoft Intune에서 iOS 및 Mac 하이브리드 디바이스 관리 설정
titleSuffix: Configuration Manager
description: System Center Configuration Manager 및 Microsoft Intune에서 iOS 디바이스 관리 설정
ms.date: 08/11/2017
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: 5eae4400-58ca-4c71-804c-6a585cd3df5d
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: a1357c54b0f848374ea15727bb6265f68400f88c
ms.sourcegitcommit: 48098f9fb2f447672bf36d50c9f58a3d26acb9ed
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53422371"
---
# <a name="set-up-ios-hybrid-device-management-with-system-center-configuration-manager-and-microsoft-intune"></a>System Center Configuration Manager 및 Microsoft Intune로 iOS 하이브리드 디바이스 관리 설정

*적용 대상: System Center Configuration Manager (현재 분기)*

Configuration Manager 및 Intune에서는 iPhone, iPad 및 Mac 사용자가 회사 메일 및 리소스에 액세스할 수 있도록 iOS 및 macOS 디바이스 등록을 사용하도록 설정합니다. 사용자가 Intune 회사 포털 앱을 설치하면 해당 디바이스를 정책 대상으로 지정할 수 있습니다. iOS 및 Mac 디바이스를 관리하려면 먼저 Apple의 APNs(Apple Push Notification Service) 인증서를 가져와야 합니다. 이 인증서를 사용하면 Intune에서는 Apple의 디바이스 관리 서비스와의 연결을 설정하여 iOS 및 Mac 디바이스를 관리할 수 있습니다.  

 회사 소유의 iOS 디바이스도 등록할 수 있습니다.  [회사 소유 디바이스 등록](enroll-company-owned-devices.md)을 참조하세요.  

**전제 조건**<br>
플랫폼에 대한 등록을 설정하려면 먼저 [하이브리드 MDM 설정](setup-hybrid-mdm.md)에서 필수 조건 및 절차를 완료합니다.

iOS 디바이스 등록을 지원하려면 다음 단계를 수행해야 합니다.  

## <a name="download-a-certificate-signing-request"></a>인증서 서명 요청 다운로드
Apple에서 APNs 인증서를 요청하려면 인증서 서명 요청 파일이 필요합니다.  

1.  Configuration Manager 콘솔의 **관리 작업** 영역에서 **클라우드 서비스**> **Microsoft Intune 구독**으로 이동합니다.  

2.  **홈** 탭에서 **APNs 인증서 요청 만들기**를 클릭합니다. **APNs CSR(인증서 서명 요청) 요청** 대화 상자가 열립니다.  

3.  **찾아보기** 를 클릭하여 새 인증서 서명 요청 파일을 저장할 경로를 찾습니다. 인증서 서명 요청 파일을 로컬로 저장합니다.  

4.  **다운로드**를 클릭합니다. 새 Microsoft Intune 인증서 서명 요청 파일이 다운로드되고 Configuration Manager에 의해 저장됩니다. 인증서 서명 요청 파일은 APC(Apple Push Certificate) 포털에서 트러스터 관계 인증서를 요청하는 데 사용됩니다.  

## <a name="request-an-mdm-push-certificate-from-apple"></a>Apple에서 MDM 푸시 인증서 요청
MDM 푸시 인증서를 사용하면 관리 서비스, Intune 및 등록된 iOS 모바일 디바이스 간에 트러스트 관계를 설정할 수 있습니다.  

1.  브라우저에서 [Apple Push Certificates 포털](http://go.microsoft.com/fwlink/?LinkId=269844) 로 이동한 다음 회사 Apple ID로 로그인합니다. 나중에 APNs 인증서를 갱신하기 위해 이 Apple ID를 사용해야 합니다.  

2.  인증서 서명 요청(.csr) 파일을 사용하여 마법사를 완료합니다. MDM 푸시 인증서를 다운로드하고 pem 파일을 로컬로 저장합니다. 이 인증서(.pem) 파일은 APN(Apple Push Notification) 서버와 Intune의 모바일 디바이스 관리 기관 간의 트러스트 관계를 설정하는 데 사용됩니다.  

> [!NOTE]  
>  구성 관리자 콘솔에서 iOS 등록을 사용하도록 설정할 때까지 APNs(Apple Push Notification service) 인증서를 Intune으로 업로드하지 마세요.  

## <a name="enable-enrollment-and-upload-the-mdm-push-certificate"></a>등록 사용 및 MDM 푸시 인증서 업로드
IOS 등록을 사용하도록 설정하려면 APNs 인증서를 업로드합니다.  

1.  Configuration Manager 콘솔의 **관리 작업** 영역에서 **클라우드 서비스** > **Microsoft Intune 구독**으로 이동합니다.  

2.  **홈** 탭의 **구독** 그룹에서 **플랫폼 구성** > **iOS**를 클릭합니다.  

3.  **Microsoft Intune 구독 속성** 대화 상자에서 **iOS** 탭을 선택하고 **iOS 등록 사용** 확인란을 클릭하여 선택합니다.  
4.  **찾아보기**를 클릭하고 Apple에서 다운로드한 APNs 인증서(.cer) 파일이 있는 위치로 이동합니다. Configuration Manager가 APNs 인증서 정보를 표시합니다. **확인** 을 클릭하여 APN 인증서를 Intune에 저장합니다.  

설정한 후에는 사용자에게 디바이스를 등록하는 방법을 알려 주어야 합니다. [디바이스 등록에 대해 최종 사용자에게 알릴 내용](https://docs.microsoft.com/intune/end-user-educate)을 참조하세요. 이 정보는 Microsoft Intune 및 Configuration Manager에서 관리되는 모바일 디바이스에 적용됩니다.

## <a name="configure-enrollment-restrictions"></a>등록 제한 구성

개인적으로 소유한 디바이스를 차단하여 등록할 수 있는 디바이스를 제한할 수 있습니다. 이 사용자가 회사 포털을 사용하여 해당 디바이스를 등록하지 않도록 방지합니다. 개인 소유 디바이스를 차단하는 경우 다음 디바이스만을 등록할 수 있습니다.
- [미리 선언된 디바이스](predeclare-devices-with-hardware-id.md)
- [Apple Configurator 관리되는 디바이스](ios-hybrid-enrollment-using-apple-configurator.md)
- [DEP(장비 등록 프로그램) 관리되는 디바이스](ios-device-enrollment-program-for-hybrid.md)
- [디바이스 등록 관리자 계정](enroll-devices-with-device-enrollment-manager.md)을 사용하여 등록한 디바이스

### <a name="to-enable-enrollment-restrictions"></a>등록 제한을 사용하려면
1.  Configuration Manager 콘솔의 **관리 작업** 영역에서 **클라우드 서비스** > **Microsoft Intune 구독**으로 이동합니다.
2.  **홈** 탭의 **구독** 그룹에서 **플랫폼 구성** > **iOS**를 클릭합니다.
3.  **개인적으로 소유한 디바이스 차단**을 선택하여 회사 소유 디바이스에 대한 등록을 제한합니다.

> [!div class="button"]
> [< 이전 단계](create-service-connection-point.md)  [다음 단계 >](set-up-additional-management.md)
