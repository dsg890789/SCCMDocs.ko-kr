---
title: 앱별 VPN에 대한 PFN(패키지 패밀리 이름) 찾기
titleSuffix: Configuration Manager
description: 앱별 VPN을 구성할 수 있도록 패키지 패밀리 이름을 찾는 두 가지 방법에 대해 알아봅니다.
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.technology: configmgr-protect
ms.topic: conceptual
ms.assetid: 47118499-3d26-4c25-bfde-b129de7eaa59
author: mestew
ms.author: mstewart
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 546cf0178993a364a4e1121e8236372162ab8481
ms.sourcegitcommit: 1bccb61bf3c7c69d51e0e224d0619c8f608e8777
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "70892307"
---
# <a name="find-a-package-family-name-pfn-for-per-app-vpn"></a>앱별 VPN에 대한 PFN(패키지 패밀리 이름) 찾기

*적용 대상: System Center Configuration Manager(현재 분기)*


앱별 VPN을 구성할 수 있도록 두 가지 방법으로 PFN을 찾을 수 있습니다.

## <a name="find-a-pfn-for-an-app-thats-installed-on-a-windows-10-computer"></a>Windows 10 컴퓨터에 설치되어 있는 앱용 PFN 찾기

사용하고 있는 앱이 Windows 10 컴퓨터에 이미 설치되어 있는 경우 [Get-AppxPackage](https://technet.microsoft.com/library/hh856044.aspx) PowerShell cmdlet을 사용하여 PFN을 가져올 수 있습니다.

Get-AppxPackage 구문은 다음과 같습니다.

``` Syntax
Get-AppxPackage [[-Name] <String> ] [[-Publisher] <String> ] [-AllUsers] [-User <String> ] [ <CommonParameters>]
```

> [!NOTE]
> PFN을 검색하려면 PowerShell을 관리자로 실행해야 할 수 있습니다.

예를 들어 컴퓨터에 설치된 모든 유니버설 앱에 대한 정보를 가져오려면 `Get-AppxPackage`를 사용합니다.

이름 또는 이름의 일부를 알고 있는 앱에 대한 정보를 가져오려면 `Get-AppxPackage *<app_name>`을 사용합니다. 앱의 전체 이름을 모를 경우 와일드카드 문자를 사용하는 것이 특히 유용합니다. 예를 들어 OneNote에 대한 정보를 가져오려면 `Get-AppxPackage *OneNote`를 사용합니다.


OneNote에 대해 검색된 정보는 다음과 같습니다.

`Name                   : Microsoft.Office.OneNote`

`Publisher              : CN=Microsoft Corporation, O=Microsoft Corporation, L=Redmond, S=Washington, C=US`

`Architecture           : X64`

`ResourceId             :`

`Version                : 17.6769.57631.0`

`PackageFullName        : Microsoft.Office.OneNote_17.6769.57631.0_x64__8wekyb3d8bbwe`

`InstallLocation        : C:\Program Files\WindowsApps`

`\Microsoft.Office.OneNote_17.6769.57631.0_x64__8wekyb3d8bbwe`

`IsFramework            : False`

**`PackageFamilyName      : Microsoft.Office.OneNote_8wekyb3d8bbwe`**

`PublisherId            : 8wekyb3d8bbwe`



## <a name="find-a-pfn-if-the-app-is-not-installed-on-a-computer"></a>앱이 컴퓨터에 설치되어 있지 않은 경우 PFN 찾기

1. [https://www.microsoft.com/en-us/store/apps](https://www.microsoft.com/store/apps ) 로 이동
2. 검색 창에 앱의 이름을 입력합니다. 이 예제에서는 OneNote를 검색합니다.
3. 앱에 대한 링크를 클릭합니다. 액세스하는 URL의 끝에 일련의 문자가 있습니다. 이 예제에서 URL은 다음과 같습니다. `https://www.microsoft.com/store/apps/onenote/9wzdncrfhvjl`
4. 다른 탭에서 다음 URL `https://bspmts.mp.microsoft.com/v1/public/catalog/Retail/Products/<app id>/applockerdata`를 붙여넣어 `<app id>`를 https://www.microsoft.com/store/apps 에서 얻은 앱 ID로 대체합니다(3단계에서 URL의 끝에 있는 일련의 문자). 이 OneNote 예제에서는 `https://bspmts.mp.microsoft.com/v1/public/catalog/Retail/Products/9wzdncrfhvjl/applockerdata`를 붙여넣습니다.

Edge에서 원하는 정보가 표시됩니다. Internet Explorer에서 **열기**를 클릭하여 정보를 확인합니다. PFN 값은 첫 번째 줄에 지정됩니다. 예제의 경우 결과가 표시되는 방법은 다음과 같습니다.

``` JSON
{
  "packageFamilyName": "Microsoft.Office.OneNote_8wekyb3d8bbwe",
  "packageIdentityName": "Microsoft.Office.OneNote",
  "windowsPhoneLegacyId": "ca05b3ab-f157-450c-8c49-a1f127f5e71d",
  "publisherCertificateName": "CN=Microsoft Corporation, O=Microsoft Corporation, L=Redmond, S=Washington, C=US"
}
```
