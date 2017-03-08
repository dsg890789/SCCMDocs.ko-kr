---
title: "IMEI 또는 iOS 일련 번호로 장치 미리 선언 | Microsoft 문서"
description: "IMEI 또는 iOS 일련 번호로 회사 소유 장치 미리 선언"
ms.custom: na
ms.date: 03/05/2017
ms.reviewer: na
ms.suite: na
ms.prod: configuration-manager
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ddb4c68e-e7f7-475a-89e2-7379a86e44c4
caps.latest.revision: 3
author: mtillman
ms.author: mtillman
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 0fd410a6572acce685dc6cdb954c1c2d97d5ed8b
ms.openlocfilehash: 2aa9c8c65904e573b6a81ac865e09d1cf2458509
ms.lasthandoff: 12/16/2016

---
# <a name="predeclare-devices-with-imei-or-ios-serial-numbers"></a>IMEI 또는 iOS 일련 번호로 장치 미리 선언

*적용 대상: System Center Configuration Manager(현재 분기)*

해당 IMEI(International station Mobile Equipment Identity) 번호 또는 iOS 일련 번호를 가져와서 회사 소유의 장치를 식별할 수 있습니다. 장치 IMEI 번호를 포함한 쉼표로 구분된 값(.csv) 파일을 업로드하거나 장치 정보를 수동으로 입력할 수 있습니다.  가져온 정보에 따라 장치 목록에 **회사**로 등록된 장치의 **소유권**이 설정됩니다. 서비스에 액세스하는 각 사용자는 Intune 라이선스가 여전히 필요합니다.  

## <a name="how-to-predeclare-corporate-owned-devices"></a>회사 소유 장치를 미리 선언하는 방법

1.    Configuration Manager 콘솔에서 **자산 및 준수** > **개요** > **모든 회사 소유 장치** > **미리 선언된 장치**로 이동합니다.

2.  **미리 선언된 장치 만들기**를 클릭합니다. 미리 선언된 장치 만들기 마법사가 열립니다.

3.    다음과 같이 장치 정보를 추가할 방법을 선택합니다.

     -    **IMEI 또는 일련 번호와 세부 정보가 포함된 CSV 파일 업로드**

        이 옵션에 대해 **찾아보기**를 클릭하고 정보가 포함된 .csv 파일을 지정하여 회사 소유의 장치를 미리 선언합니다. .csv 파일의 형식을 올바르게 지정해야 합니다. 자세한 내용은 [.csv 파일을 업로드하기 위한 형식](#format-for-uploading-csv-files)을 참조하세요.

     -    **수동으로 IMEI 또는 일련 번호와 세부 정보 추가**

        정보를 수동으로 입력하려면 IMEI 번호 또는 iOS 일련 번호와 장치에 대한 세부 정보를 입력합니다. 계속하기 전에 오류 또는 경고를 수정합니다.

    **다음**을 클릭합니다.

4. .csv 파일을 업로드한 경우 파일 가져오기의 결과를 검토합니다. 장치 번호를 이전에 가져온 경우 Configuration Manager에 해당 장치 및 교체 **세부 정보**가 표시됩니다. 세부 정보를 덮어쓸 장치를 선택합니다. 장치 세부 정보는 장치 ID 또는 일련 번호를 다시 가져와야 수정할 수 있습니다.

  수동 번호 입력을 선택한 경우 미리 선언하려는 장치에 대한 양식을 작성합니다.

  **다음** 을 클릭하여 계속합니다.

4. 목록에 iOS 일련 번호가 포함된 경우 사용 가능한 프로필 목록에서 **할당할 등록 프로필**을 선택한 후 **다음**을 클릭합니다.

5. **다음**을 클릭하여 세부 정보를 검토하고 **다음**을 다시 클릭하여 데이터를 업로드합니다.

6. **닫기**를 클릭하여 설치를 완료합니다.

## <a name="format-for-uploading-csv-files"></a>.csv 파일을 업로드하기 위한 형식

IMEI 또는 일련 번호로 장치를 식별하는 데 사용하는 .csv 파일은 다음 형식이어야 합니다(참조용으로만 제공되는 맨 위 행은 제외). 각 행은 IMEI 번호 또는 iOS 일련 번호를 포함해야 합니다. iOS 장치의 일련 번호만 미리 선언할 수 있습니다. 다른 장치 플랫폼에는 IMEI 번호를 사용합니다. 다음 표에 샘플 데이터가 포함되어 있습니다.

| IMEI #  | iOS 일련 번호 #  | OS | 세부 정보 |
|------------ |---------------|-----|-----|
| 123456789012345    |   | WINDOWS | 회사 소유 Windows 장치|
|   | A1B2C3D4E5C6 | IOS |     회사 소유 iOS 장치|
| 223456789012345 | E6D5C4B3A210 |   IOS |     다른 iOS 장치|
| 323456789012345 |        |   IOS |     세 번째 iOS 장치|
| 123456789012346 |         |   ANDROID |     회사 소유 Android 장치|

.csv 파일의 머리글 행을 포함하지 않습니다. 다음 예제에서는 CSV 형식의 동일한 샘플 데이터를 보여 줍니다.

```
123456789012345,,WINDOWS,Company-owned Windows device
,A1B2C3D4E5C6,IOS,Company-owned iOS device
223456789012345,E6D5C4B3A210,IOS,Another iOS device
323456789012345,,IOS,A third iOS device
123456789012346,,ANDROID,Company-owned Android device
```

.csv 파일의 열에는 다음 값이 허용됩니다.

| 열 1 | 열 2 | 열 3 | 열 4 |
|---|---|---|---|
|공백 없는 IMEI 번호 | iOS 일련 번호 | IOS, WINDOWS 또는 ANDROID | 선택적 장치 세부 정보(1024자까지 가능) |

