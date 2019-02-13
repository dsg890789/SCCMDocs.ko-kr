---
title: 비즈니스용 Windows Hello 설정
titleSuffix: Configuration Manager
description: Configuration Manager와 비즈니스용 Windows Hello를 통합하는 방법을 알아봅니다.
ms.date: 12/21/2018
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: c0593c07-5dd7-4d23-a0d8-d30165f49ef7
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 71f853034133e2ec73a4d8e606c2e0c0c94841a4
ms.sourcegitcommit: 874d78f08714a509f61c52b154387268f5b73242
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56134081"
---
# <a name="windows-hello-for-business-settings-in-configuration-manager-hybrid"></a>Windows Hello for Business 설정에서 Configuration Manager (하이브리드)

*적용 대상: System Center Configuration Manager(현재 분기)*

Configuration Manager를 사용 하면 Windows Hello (이전의 Microsoft Passport for Windows), Windows 10 장치의 대체 로그인 방법인와 통합할 수 있습니다. 비즈니스용 Windows Hello는 Active Directory 또는 Azure Active Directory 계정을 사용하여 암호, 스마트 카드 또는 가상 스마트 카드를 대체합니다. 비즈니스용 Windows Hello를 통해 암호 대신 **사용자 제스처** 를 사용하여 로그인할 수 있습니다. 사용자 제스처는 단순 PIN, 생체 인식 인증 또는 외부 디바이스(예: 지문 판독기)일 수 있습니다.  

> [!Important]  
> 2017 년 12 월부터 Windows Hello for Business 설정 in Configuration Manager는 한 [사용 되지 않는 기능](/sccm/core/plan-design/changes/deprecated/removed-and-deprecated-cmfeatures)합니다. Windows Server 2016 Active Directory Federation Services RA (등록 기관 ADFS) 배포 더 나은 사용자 환경을 제공 합니다. 하며 보다 명확한 인증서 등록 환경이 더 간단 합니다. 자세한 내용은 [비즈니스용 Windows Hello](https://docs.microsoft.com/windows/access-protection/hello-for-business/hello-identity-verification)를 참조하세요.  


Configuration Manager는 다음 두 가지 방법으로 비즈니스용 Windows Hello와 통합됩니다.  

- Configuration Manager를 사용하여 사용자가 로그인하는 데 사용할 수 있는 제스처와 사용할 수 없는 제스처를 제어할 수 있습니다.  

- 비즈니스용 Windows Hello KSP(키 스토리지 공급자)에 인증 인증서를 저장할 수 있습니다. 자세한 내용은 [인증서 프로필](create-pfx-certificate-profiles.md)을 참조하세요.  

- Configuration Manager 클라이언트를 실행하는 도메인에 가입된 Windows 10 디바이스에 비즈니스용 Windows Hello 정책을 배포할 수 있습니다. 이 구성은 [도메인에 가입된 Windows 10 디바이스에서 비즈니스용 Windows Hello 구성](/sccm/protect/deploy-use/windows-hello-for-business-settings#configure-windows-hello-for-business-on-domain-joined-windows-10-devices)에서 설명합니다. Intune과 함께 Configuration Manager를 사용하는 경우(하이브리드) Windows 10 및 Windows 10 Mobile 디바이스에서 이러한 설정을 구성할 수 있지만, Configuration Manager 클라이언트를 실행하는 도메인에 가입된 디바이스에서는 구성할 수 없습니다.   

구성에 대 한 Windows Hello 비즈니스 설정에 대 한 일반적인 정보를 참조 하세요 [Windows Hello for Business 설정 Configuration Manager에서](/sccm/protect/deploy-use/windows-hello-for-business-settings)합니다.



## <a name="configure-windows-hello-for-business-settings-hybrid"></a>비즈니스용 Windows Hello 설정(하이브리드) 구성  

1. Configuration Manager 콘솔에서 **관리** > **클라우드 서비스** > **Microsoft Intune 구독**을 클릭합니다.  

2. 목록에서 Microsoft Intune 구독을 선택하고 **홈** 탭의 **구독** 그룹에서 **플랫폼 구성** > **Windows(MDM)** 를 클릭합니다.  

3. **Microsoft Intune 구독 속성** 대화 상자의 **비즈니스용 Windows Hello** 탭에서, 다음 값 중에서 등록된 모든 Windows 10 및 Windows 10 Mobile 디바이스에 영향을 주는 값을 선택합니다.  

   - **등록된 디바이스에서 비즈니스용 Windows Hello 사용 안 함** 또는 **등록된 디바이스에 비즈니스용 Windows Hello 사용** - 등록된 모든 Windows 10 및 Windows 10 모바일 디바이스에서 비즈니스용 Windows Hello를 사용하거나 사용하지 않습니다.  

   - **TPM(신뢰할 수 있는 플랫폼 모듈) 사용** - TPM(신뢰할 수 있는 플랫폼 모듈) 칩은 추가적인 데이터 보안 계층을 제공합니다. 다음 값 중 하나를 선택합니다.  

     -   **필수** (기본값) - 액세스할 수 있는 TPM이 있는 디바이스만 비즈니스용 Windows Hello를 프로비전할 수 있습니다.  

     -   **기본 설정** - 디바이스는 먼저 TPM을 사용하려고 합니다. 사용할 수 없는 경우 소프트웨어 암호화를 사용할 수 있습니다.  

   - **최소 PIN 길이 필요** - 비즈니스용 Windows Hello PIN에 필요한 최소 문자 수를 지정합니다. 4자 이상을 사용해야 합니다(기본값 6자).  

   - **최대 PIN 길이 필요** - 비즈니스용 Windows Hello PIN에 허용되는 최대 문자 수를 지정합니다. 최대 127자를 사용할 수 있습니다.  

   - **PIN에 소문자 필요** - 비즈니스용 Windows Hello PIN에 소문자를 사용해야 하는지 여부를 지정합니다. 다음 중에서 선택합니다.  

     -   **허용** - PIN에 소문자를 사용할 수 있습니다.  

     -   **필수** - PIN에 소문자를 하나 이상 포함해야 합니다.  

     -   **허용되지 않음** (기본값) - PIN에서 소문자를 사용하지 않아야 합니다.  

   - **PIN에 대문자 필요** - 비즈니스용 Windows Hello PIN에 대문자를 사용해야 하는지 여부를 지정합니다. 다음 중에서 선택합니다.  

     -   **허용** - PIN에 대문자를 사용할 수 있습니다.  

     -   **필수** - PIN에 대문자를 하나 이상 포함해야 합니다.  

     -   **허용되지 않음** (기본값) - PIN에서 대문자를 사용하지 않아야 합니다.  

   - **특수 문자 필요** - PIN에 특수 문자의 사용을 지정합니다. 다음 중에서 선택합니다.  

     - **허용** - PIN에 특수 문자를 사용할 수 있습니다.  

     - **필수** - PIN에 특수 문자를 하나 이상 포함해야 합니다.  

     - **허용되지 않음** (기본값) - PIN에 특수 문자를 사용하지 않아야 합니다(설정이 구성되지 않은 경우에도 이 동작 수행).  

       특수 문자에는 다음이 포함됩니다. **! " # $ % & ' ( ) \* + , - . / : ; < = > ? @ [ \ ] ^ _ ` { &#124; } ~**  

   - **PIN 만료(일) 필요** - 디바이스 PIN을 변경해야 할 때까지의 기간(일)을 지정합니다. 기본값은 41일입니다.  

   - **이전 PIN의 재사용 방지** - 이전에 사용된 PIN을 다시 사용하지 않도록 제한하려면 이 설정을 사용합니다. 기본값은 마지막으로 사용한 5개 PIN을 다시 사용할 수 없는 것입니다.  

   - **생체 인식 제스처 사용** - 비즈니스용 Windows Hello PIN 대신 안면 인식 또는 지문과 같은 생체 인식 인증을 사용합니다. 사용자는 생체 인식 인증에 실패하는 경우 작업 PIN을 구성해야 합니다.  

      **사용**으로 설정되면 비즈니스용 Windows Hello에서 생체 인식 인증을 허용합니다.  **사용 안 함**으로 설정되면 비즈니스용 Windows Hello에서 모든 계정 유형에 대해 생체 인식 인증을 금지합니다.  

   - **사용 가능한 경우 향상된 스푸핑 방지 사용** - 향상된 스푸핑 방지 기능을 지원하는 디바이스에서 이 기능을 사용할지 여부를 구성합니다.  

      **사용**으로 설정되면 지원될 경우 모든 사용자는 안면에 대해 스푸핑 방지 기능을 사용하도록 요구됩니다.  

   - **원격 Passport 사용** - 이 옵션이 **사용**으로 설정되면 원격 비즈니스용 Windows Hello를 데스크톱 컴퓨터 인증을 위한 휴대용 포함 디바이스로 사용할 수 있습니다. 데스크톱 컴퓨터가 Azure Active Directory에 가입되어 있어야 하고 해당 포함 디바이스는 비즈니스용 Windows Hello PIN으로 구성되어야 합니다.  

4. 작업을 마쳤으면 **확인**을 클릭합니다.  



## <a name="see-also"></a>참고 항목  

[데이터 및 사이트 인프라 보호](/sccm/protect/understand/protect-data-and-site-infrastructure)

[비즈니스용 Windows Hello](https://docs.microsoft.com/windows/security/identity-protection/hello-for-business/hello-identity-verification)  
