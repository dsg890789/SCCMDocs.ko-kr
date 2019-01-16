---
title: Configure iOS apps with app configuration policies
titleSuffix: Configuration Manager
description: 앱을 실행하기 전에 사용자에게 앱 구성 정책을 배포하여 iOS 8 이상을 실행 중인 디바이스의 구성 문제를 해결합니다.
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: f0a78038-ea22-4826-9c07-1771b7dd2e8d
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: a0a5cb6e609912a280f1cf0608ec298f860fe2e2
ms.sourcegitcommit: 2687489aa409a050dcacd67f17b3dad3ab7f1804
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/15/2019
ms.locfileid: "54316340"
---
# <a name="apply-settings-to-ios-apps-with-app-configuration-policies-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 앱 구성 정책을 사용하여 iOS 앱에 설정 적용

*적용 대상: System Center Configuration Manager(현재 분기)*


System Center Configuration Manager(Configuration Manager)에서 앱 구성 정책을 사용하여 사용자가 앱을 실행할 때 필요할 수 있는 설정을 배포할 수 있습니다. 예를 들어 앱에서 다음 세부 정보를 지정하도록 사용자에게 요구할 수 있습니다.
- 사용자 지정 포트 번호
- 언어 설정
- 보안 설정
- 회사 로고와 같은 브랜딩 설정

사용자가 설정을 잘못 입력하는 경우 지원 센터에서 수정해야 하며 앱 배포 속도가 느려집니다.
이러한 문제를 방지하기 위해 앱 구성 정책을 사용하여 앱을 실행하기 전에 필수 설정을 사용자에게 배포할 수 있습니다. 설정이 자동으로 사용자와 연결됩니다. 사용자는 아무 작업도 수행할 필요가 없습니다.
구성 정책을 사용자와 디바이스에 직접 배포하는 대신 Configuration Manager에서 앱 구성 정책을 사용하려면 앱을 배포할 때 배포 유형과 정책을 연결합니다. 정책 설정은 앱에서 해당 설정을 확인할 때마다(일반적으로 앱을 처음 실행할 때) 적용됩니다.

현재 앱 구성 정책은 iOS 8 이상을 실행하는 장치에서 다음과 같은 애플리케이션 유형에만 사용할 수 있습니다.

- **iOS 용 앱 패키지 (\*.ipa 파일)**
- **App Store의 iOS용 앱 패키지**

앱 설치 유형에 대한 자세한 내용은 [애플리케이션 관리 소개](/sccm/apps/understand/introduction-to-application-management)를 참조하세요.

## <a name="create-an-app-configuration-policy"></a>앱 구성 정책 만들기

1. Configuration Manager 콘솔에서 **소프트웨어 라이브러리** > **응용 프로그램 관리** > **앱 구성 정책**을 선택합니다.
2. **홈** 탭의 **앱 구성 정책** 그룹에서 **새 애플리케이션 구성 정책 만들기**를 선택합니다.
3. 앱 구성 정책 만들기 마법사의 **일반** 페이지에서 다음 정책 정보를 설정합니다.
   - **이름**. 정책의 고유 이름을 입력합니다.
   - **설명**. (선택 사항) 정책을 식별하기 쉽도록 설명을 추가할 수 있습니다.
   - **검색 및 필터링 향상을 위해 할당된 범주입니다**. (선택 사항) 범주를 만들고 정책에 할당하려면 **범주**를 선택합니다. 범주를 사용하면 Configuration Manager 콘솔에서 항목을 쉽게 정렬하고 찾을 수 있습니다.
4. **iOS 정책** 페이지에서 구성 정책 정보를 설정하는 방법을 선택합니다.
   - **이름 및 값 쌍 지정**. 중첩을 사용하지 않는 속성 목록 파일에 이 옵션을 사용할 수 있습니다.

      *이름 및 값 쌍을 지정하려면*
        1. 새로운 쌍을 추가하려면 **새로 만들기**를 선택합니다.
        2. **이름/값 쌍 추가** 대화 상자에서 다음을 지정합니다.
            - **유형**. 목록에서 지정하려는 값 형식을 선택합니다.
            - **이름**. 값을 지정하려는 속성 목록 키의 이름을 입력합니다.
            - **값**. 입력한 키에 적용할 값을 입력합니다.

   - **속성 목록 파일 찾기**. 앱 구성 XML 파일이 이미 있는 경우 또는 중첩을 사용하는 좀 더 복잡한 파일에 대해서는 이 옵션을 사용합니다.

     *속성 목록 파일을 찾으려면*

     1. **앱 구성 정책** 필드에 속성 목록 정보를 올바른 XML 형식으로 입력합니다.

        XML 속성 목록에 대한 자세한 내용은 iOS Developer Library의 [XML 속성 목록](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/PropertyLists/UnderstandXMLPlist/UnderstandXMLPlist.html)을 참조하세요.

XML 속성 목록의 형식은 구성하는 앱에 따라 달라집니다. 사용할 형식에 대한 자세한 내용은 앱 공급업체에 문의하세요.
Intune에서는 속성 목록의 다음 데이터 형식을 지원합니다.
            
            ```
            <integer>
            <real>
            <string>
            <array>
            <dict>
            <true /> or <false />
            ```
데이터 형식에 대한 자세한 내용은 iOS 개발자 라이브러리의 [속성 목록 정보](https://developer.apple.com/library/content/documentation/Cocoa/Conceptual/PropertyLists/AboutPropertyLists/AboutPropertyLists.html)를 참조하세요.
Intune은 또한 속성 목록에서 다음과 같은 토큰 형식을 지원합니다.
            
            ```
            {{userprincipalname}} - (Example: John@contoso.com)
            {{mail}} - (Example: John@contoso.com)
            {{partialupn}} - (Example: John)
            {{accountid}} - (Example: fc0dc142-71d8-4b12-bbea-bae2a8514c81)
            {{deviceid}} - (Example: b9841cd9-9843-405f-be28-b2265c59ef97)
            {{userid}} - (Example: 3ec2c00f-b125-4519-acf0-302ac3761822)
            {{username}} - (Example: John Doe)
            {{serialnumber}} - (Example: F4KN99ZUG5V2) for iOS devices
            {{serialnumberlast4digits}} - (Example: G5V2) for iOS devices
            ```

{{ 및 }} 문자는 토큰 유형에만 사용되고 다른 목적으로 사용하면 안 됩니다.
            
5. 이전에 만든 XML 파일을 가져오려면 **파일 선택**을 선택합니다.
6. **다음**을 선택합니다. XML 코드에 오류가 있는 경우 계속 진행하기 전에 이 문제를 해결해야 합니다.
7. 마법사에 표시된 단계를 완료합니다.

새 앱 구성 정책이 **소프트웨어 라이브러리** 작업 영역의 **앱 구성 정책** 노드에 표시됩니다.

## <a name="associate-an-app-configuration-policy-with-a-configuration-manager-application"></a>Configuration Manager 애플리케이션과 앱 구성 정책을 연결합니다.

앱 구성 정책을 iOS 앱 배포와 연결하려면 [애플리케이션 배포](/sccm/apps/deploy-use/deploy-applications) 항목의 절차를 사용하여 일반적인 방법으로 애플리케이션을 배포합니다.

소프트웨어 배포 마법사의 **앱 구성 정책** 페이지에서 **새로 만들기**를 선택합니다. **앱 구성 정책 선택** 대화 상자에서 애플리케이션 배포 유형과 여기에 연결할 앱 구성 정책을 선택합니다.
배포 유형이 설치되면 앱 구성 정책 설정이 자동으로 적용됩니다.

## <a name="example-format-for-the-mobile-app-configuration-xml-file"></a>모바일 앱 구성 XML 파일의 형식 예

모바일 앱 구성 파일을 만들 때 이 형식을 사용하여 다음 값 중 하나 이상을 지정할 수 있습니다.

```
<dict>
  <key>userprincipalname</key>
  <string>{{userprincipalname}}</string>
  <key>mail</key>
  <string>{{mail}}</string>
  <key>partialupn</key>
  <string>{{partialupn}}</string>
  <key>accountid</key>
  <string>{{accountid}}</string>
  <key>deviceid</key>
  <string>{{deviceid}}</string>
  <key>userid</key>
  <string>{{userid}}</string>
  <key>username</key>
  <string>{{username}}</string>
  <key>serialnumber</key>
  <string>{{serialnumber}}</string>
  <key>serialnumberlast4digits</key>
  <string>{{serialnumberlast4digits}}</string>
  <key>udidlast4digits</key>
  <string>{{udidlast4digits}}</string>
</dict>
```
