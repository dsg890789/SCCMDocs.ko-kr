---
title: "앱 구성 정책을 사용하여 iOS 앱 구성 | System Center Configuration Manager"
description: "앱을 실행하기 전에 사용자에게 앱 구성 정책을 배포하여 iOS 8 이상을 실행 중인 장치의 구성 문제를 해결합니다."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.technology:
- configmgr-app
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 74d5d776-e37d-45de-bdba-43541b03d12c
caps.latest.revision: 10
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 1134bb2f04152288e72d40b1b1083f415cb4e900
ms.openlocfilehash: 9cbf28afbbe69f9a027ffad2a699b9d6b625e690


---
# <a name="configure-ios-apps-with-app-configuration-policies-in-system-center-configuration-manager"></a>Configure iOS apps with app configuration policies in System Center Configuration Manager

*적용 대상: System Center Configuration Manager(현재 분기)*


System Center Configuration Manager에서 앱 구성 정책을 사용하여 사용자가 앱을 실행할 때 필요할 수 있는 설정을 제공할 수 있습니다. 예를 들어 사용자가 앱에서 다음 사항을 지정해야 할 수 있습니다.
- 사용자 지정 포트 번호
- 언어 설정
- 보안 설정
- 회사 로고와 같은 브랜딩 설정

사용자가 이러한 설정을 잘못 입력하면 지원 센터의 부담이 증가하며 새 앱 도입도 지연됩니다.
앱 구성 정책을 사용하는 경우 사용자가 앱을 실행하기 전에 정책에서 이러한 설정을 사용자에게 배포할 수 있으므로 이러한 문제를 방지할 수 있습니다. 배포한 설정은 자동으로 제공되므로 사용자가 아무런 작업을 수행하지 않아도 됩니다.
사용자 및 장치에 이러한 정책을 직접 배포하지는 않으며, 대신, 응용 프로그램을 배포할 때 배포 유형과 정책을 연결합니다. 정책 설정은 앱에서 해당 설정을 확인할 때마다(일반적으로는 앱을 처음 실행할 때) 사용됩니다.

앱 구성 정책은 현재 iOS 8 이상을 실행하는 장치에서만 사용할 수 있으며, 다음과 같은 응용 프로그램 유형을 지원합니다.

- **iOS용 앱 패키지(*.ipa 파일)**
- **App Store의 iOS용 앱 패키지**

앱 설치 유형에 대한 자세한 내용은 [응용 프로그램 관리 소개](/sccm/apps/understand/introduction-to-application-management)를 참조하세요.

## <a name="create-an-app-configuration-policy"></a>앱 구성 정책 만들기

1. Configuration Manager 콘솔에서 **소프트웨어 라이브러리** > **응용 프로그램 관리** > **앱 구성 정책**을 클릭합니다.
3. **홈** 탭의 **앱 구성 정책** 그룹에서 **새 응용 프로그램 구성 정책 만들기**를 클릭합니다.
4. **앱 구성 정책 만들기 마법사**의 **일반** 페이지에서 다음 정보를 지정합니다.
    - **이름**: 정책의 고유 이름을 지정합니다.
    - **설명**: 필요에 따라 식별하는 데 도움이 되는 정책에 대한 설명을 지정합니다.
    - **검색 및 필터링을 향상시키기 위해 할당된 범주**: **범주**를 클릭하여 범주를 만들고 정책에 할당할 수 있습니다. 이렇게 하면 Configuration Manager 콘솔에서 항목을 쉽게 정렬하고 찾을 수 있습니다.
5. **iOS 정책** 페이지에서 구성 정책 정보를 지정하는 방법을 선택합니다.
    - **이름 및 값 쌍 지정**: 중첩을 사용하지 않는 속성 목록 파일에 이 옵션을 사용할 수 있습니다.
    이름/값 쌍을 지정하려면
        - 새로운 쌍을 추가하려면 **새로 만들기**를 클릭합니다.
        - **이름/값 쌍 추가** 대화 상자에서 다음을 지정합니다.
            - **형식**: 목록에서 지정하려는 값 형식을 선택합니다.
            - **이름**: 값을 지정하려는 속성 목록 키의 이름을 입력합니다.
            - **값**: 입력한 키에 적용할 값을 입력합니다.
        - 속성 목록 파일 찾기: 앱 구성 XML 파일이 이미 있는 경우 또는 중첩을 사용하는 좀 더 복잡한 파일에 대해서는 이 옵션을 사용합니다.
        속성 목록 파일을 찾아보려면
            - **앱 구성 정책** 필드에 속성 목록 정보를 올바른 XML 형식으로 입력합니다.
            XML 속성 목록에 대한 자세한 내용은 iOS Developer Library의 [XML 속성 목록](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/PropertyLists/UnderstandXMLPlist/UnderstandXMLPlist.html)을 참조하세요.
            XML 속성 목록의 형식은 구성하는 앱에 따라 달라집니다. 사용해야 하는 정확한 형식에 대한 자세한 내용은 앱 공급업체에 문의하세요.
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
            또한 Intune은 속성 목록에서 다음과 같은 토큰 형식을 지원합니다.
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

            The {{ and }} characters are used by token types only and must not be used for other purposes.
            ```
            **파일 선택**을 클릭하여 이전에 만든 XML 파일을 가져올 수도 있습니다.
6. **다음**을 클릭합니다. XML 코드에 오류가 있는 경우 계속 진행하기 전에 이 문제를 해결해야 합니다.
6. 마법사를 완료합니다.

새 앱 구성 정책이 **소프트웨어 라이브러리** 작업 영역의 **앱 구성 정책** 노드에 표시됩니다.

## <a name="associate-an-app-configuration-policy-with-a-configuration-manager-application"></a>Configuration Manager 응용 프로그램과 앱 구성 정책을 연결합니다.

앱 구성 정책을 iOS 앱 배포와 연결하려면 [응용 프로그램 배포](/sccm/apps/deploy-use/deploy-applications) 항목의 절차를 사용하여 일반적인 방법으로 응용 프로그램을 배포합니다.
**소프트웨어 배포 마법사**의 **앱 구성 정책** 페이지에서 **새로 만들기**를 클릭합니다. 그런 다음 **앱 구성 정책 선택** 대화 상자에서 응용 프로그램 배포 유형과 여기에 연결할 앱 구성 정책을 선택합니다.
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



<!--HONumber=Nov16_HO1-->


