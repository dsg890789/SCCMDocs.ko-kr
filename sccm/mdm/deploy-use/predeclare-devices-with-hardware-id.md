---
title: "IMEI 또는 iOS 일련 번호로 장치 미리 선언"
description: "IMEI 또는 iOS 일련 번호로 회사 소유 장치 미리 선언"
ms.custom: na
ms.date: 10/06/2016
ms.reviewer: na
ms.suite: na
ms.prod: configuration-manager
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ddb4c68e-e7f7-475a-89e2-7379a86e44c4
caps.latest.revision: 3
author: NathBarn
ms.author: nathbarn
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 6cd640085e90b2945326e3fa942ae9bd7b8f7e24
ms.openlocfilehash: 2550fef062b5ef508e4c0492a5a9c63ffcb9084a

---
# <a name="predeclare-devices-with-imei-or-ios-serial-numbers"></a>IMEI 또는 iOS 일련 번호로 장치 미리 선언

*적용 대상: System Center Configuration Manager(현재 분기)*

해당 IMEI(International station Mobile Equipment Identity) 번호 또는 iOS 일련 번호를 가져와서 회사 소유의 장치를 식별할 수 있습니다. 장치 IMEI 번호를 포함한 쉼표로 구분된 값(.csv) 파일을 업로드하거나 장치 정보를 수동으로 입력할 수 있습니다.  가져온 정보에 따라 장치 목록에 "**회사**"로 등록된 장치의 **소유권**이 설정됩니다. 서비스에 액세스하는 각 사용자는 Intune 라이선스가 여전히 필요합니다.  

## <a name="predeclare-corporate-owned-devices-with-imei-or-ios-serial-number"></a>IMEI 또는 iOS 일련 번호로 회사 소유 장치 미리 선언

1.  Configuration Manager 콘솔에서 자산 및 준수 > 개요 > 모든 회사 소유 장치 > 미리 선언된 장치로 이동한 다음 미리 선언된 장치 추가를 클릭합니다. 미리 선언된 장치 마법사가 열립니다.
2.  다음과 같이 장치 정보를 추가할 방법을 지정합니다.
     -  IMEI 번호 및 세부 정보를 포함하는 .csv 파일 업로드
     -  수동으로 IMEI 번호 및 세부 정보 추가. 정보를 수동으로 입력하려면 IMEI 번호 또는 iOS 일련 번호와 장치에 대한 세부 정보를 입력합니다.

      업로드된 파일의 경우 정보가 포함된 .csv 파일을 찾아 회사 소유의 장치를 미리 선언합니다. 파일은 다음 형식이어야 합니다(참조용으로만 제공되는 맨 위 행은 제외). 각 행은 IMEI 번호 또는 iOS 일련 번호를 포함해야 합니다. iOS 장치의 일련 번호만 미리 선언할 수 있습니다. 다른 장치 플랫폼에는 IMEI 번호를 사용합니다. 다음 표에 샘플 데이터가 포함되어 있습니다.
      | IMEI #  | iOS 일련 번호 #  | OS | 세부 정보 |
      | :------------ |:---------------|:-----|:-----|
      | 123456789012345    |   | WINDOWS | 회사 소유 Windows 장치|
      |       | A1B2C3D4E5C6 |   iOS |  회사 소유 iOS 장치|
      | 223456789012345 | E6D5C4B3A210 |   iOS |    다른 iOS 장치|
      | 323456789012345 |        |   iOS |  세 번째 iOS 장치|
      | 123456789012346 |         |   Android |     회사 소유 Android 장치|

    .csv 파일의 머리글 행을 포함하지 않습니다. 위의 예제에는 설명용 헤더만 포함됩니다.

    **열에 다음 값이 허용됩니다.**    
      - 열 1: 공백 없는 IMEI 번호
      - 열 2: iOS 일련 번호
      - 열 3: 장치의 운영 체제
         - IOS - 모든 iOS 장치
         - WINDOWS - Windows Phone, Window 10 Mobile 및 Windows PC 포함
         - ANDROID - 모든 Android 장치
      - 열 4: 세부 정보(선택 사항) – Configuration Manager 콘솔에 표시되는 추가 장치 정보 1024자까지 가능합니다.

    **다음**을 클릭합니다.

3. 파일 가져오기 결과를 검토합니다. 장치 번호를 이전에 가져온 경우 Configuration Manager에 해당 장치 및 교체 **세부 정보**가 표시됩니다. 세부 정보를 덮어쓸 장치를 선택합니다. 장치 세부 정보는 장치 ID 또는 일련 번호를 다시 가져와야 수정할 수 있습니다. **다음**을 클릭하여 계속하거나 **뒤로**를 클릭하여 업데이트된 세부 정보를 유지한 다음 마법사를 완료합니다.

4. iOS 일련 번호를 포함하여 가져올 경우 해당 장치를 등록 프로필에 할당해야 합니다. 사용 가능한 프로필 목록에서 **할당할 등록 프로필**을 선택한 후 **다음**을 클릭합니다.

5. **다음**을 클릭하여 요약을 본 후 마법사를 완료합니다.



<!--HONumber=Nov16_HO1-->


