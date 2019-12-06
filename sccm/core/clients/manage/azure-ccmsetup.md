---
title: Azure AD 인증 워크플로
titleSuffix: Configuration Manager
description: Azure Active Directory 인증을 사용하는 Windows 10 디바이스의 구성 관리자 클라이언트 설치 프로세스 세부 정보
ms.date: 07/03/2019
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.collection: M365-identity-device-management
ms.assetid: 9aaf466a-3f40-4468-b3cd-f0010f21f05a
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 411752ae345b6af255e8fe1e46d5d5e3a93b8900
ms.sourcegitcommit: 1bccb61bf3c7c69d51e0e224d0619c8f608e8777
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "70890369"
---
# <a name="azure-ad-authentication-workflow"></a>Azure AD 인증 워크플로

*적용 대상: System Center Configuration Manager(현재 분기)*

이 문서는 Azure AD(Azure Active Directory)에 가입된 Windows 10 디바이스의 구성 관리자 클라이언트 설치 프로세스에 관한 기술 참조입니다. 여기서는 디바이스 인증 및 클라이언트 설치의 워크플로 프로세스를 자세히 설명합니다.  
 

## <a name="azure-ad-token-request-workflow"></a>Azure AD 토큰 요청 워크플로

![Azure AD CCMSetup 워크플로 다이어그램](media/azure-ad-install-workflow.png)  

### <a name="1-azure-ad-token-request"></a>1. Azure AD 토큰 요청

Windows 10 Azure AD 도메인 가입 클라이언트는 Azure AD 매개 변수를 사용하여 토큰을 요청합니다. 다음 항목이 **ccmsetup.log**에 로깅됩니다.

- 다음 Azure AD 디바이스 토큰을 요청합니다.

    ``` Log
    Getting AAD (device) token with: ClientId = 22ed38d9-XXXX-4036-XXXX-a98452fda4fc, ResourceUrl = https://ConfigMgrService, AccountId = https://login.microsoftonline.com/common/oauth2/token
    ```

- 디바이스 토큰을 가져올 수 없으면 다음과 같이 Azure AD 사용자 토큰을 요청합니다.

    ``` Log
    Getting AAD (user) token with: ClientId = f1f9b14e-XXXX-4f17-XXXX-2593f6eee91e, ResourceUrl = https://ConfigMgrService, AccountId = X49FC29A-ECE3-XXX-A3C1-XXXXXXF035A6E
    ```

> [!NOTE]
> 클라이언트는 Azure AD에 가입할 때 WPJ(작업 공간 연결) 인증서를 가져와야 합니다. 작업 공간 연결 인증서를 찾을 수 없으면 클라이언트는 보안 토큰 서비스 통신 채널(CCM_STS)을 사용하여 요청을 만들려고 하지 않습니다. 이 동작은 클라이언트가 요청에 Azure AD 토큰을 추가할 수 없기 때문에 발생합니다. 디바이스는 일반적으로 클라이언트가 Azure AD에 제대로 가입되지 않으면 이 인증서가 없습니다.
>
> 또한 토큰이 유효하지 않으면 CMG(클라우드 관리 게이트웨이)가 내부 사이트 역할로 요청을 전달하지 못합니다. 토큰은 테넌트가 Configuration Manager에서 클라우드 관리 서비스로 등록되지 않으면 유효하지 않을 수 있습니다.


### <a name="2-configuration-manager-client-token-request"></a>2. 구성 관리자 클라이언트 토큰 요청

클라이언트에 Azure AD 토큰이 있으면 구성 관리자 클라이언트(CCM) 토큰을 요청합니다.

다음 항목이 CMG 가상 머신의 **ccmsetup.log**에 로깅됩니다.

``` Log
Getting CCM Token from STS server 'CloudManagementGateway.cloudapp.net/CCM_PROXY_MUTUALAUTH/XXXXXX037938216'
Getting CCM Token from https://CloudManagementGateway.cloudapp.net/CCM_PROXY_MUTUALAUTH/XXXXXX037938216/CCM_STS
```

#### <a name="21-cmg-gets-request"></a>2.1 CMG가 요청 가져오기

다음 항목이 **IIS.log**에 로깅됩니다.

``` Log
RD0003FF74XX2 10.0.0.4 GET /CCM_STS - 443 - HTTP/1.1 python-requests/2.20.0 - - 13.95.234.44 404 0 2 1477 154 15
```

#### <a name="22-cmg-forwards-request-to-cmg-connection-point"></a>2.2 CMG가 CMG 연결점에 요청 전달

다음 항목이 **CMGService.log**에 로깅됩니다.

``` Log
RequestUri: /CCM_PROXY_SERVERAUTH/XXXXXX037938216/CCM_STS  RequestCount: 769  RequestSize: 1081595 Bytes  ResponseCount: 769     ResponseSize: 36143 Bytes  AverageElapsedTime: 3945 ms
```

#### <a name="23-cmg-connection-point-transforms-cmg-client-request-to-management-point-client-request"></a>2.3 CMG 연결점이 CMG 클라이언트 요청을 관리 지점 클라이언트 요청으로 변환

다음 항목이 **SMS_CLOUD_PROXYCONNECTOR.log**에 로깅됩니다.

``` Log
MessageID: 3087bd34-b82c-4950-b972-e82bb0fb8385 RequestURI: https://MP.MYCORP.COM/CCM_STS EndpointName: CCM_STS ResponseHeader: HTTP/1.1 200 OK ~~ ResponseBodySize: 0 ElapsedTime: 2 ms
```

#### <a name="24-management-point-verifies-user-token-in-site-database"></a>2.4 관리 지점이 사이트 데이터베이스에서 사용자 토큰 확인

다음 항목이 **CCM_STS.log**에 로깅됩니다.

``` Log
Validated AAD token. TokenType: Device TenantId: XXXXe388-XXXX-485c-XXXX-e8e4eb41XXXX UserId: 00000000-0000-0000-0000-000000000000 DeviceId: 0XXXXX80-77XX-4XXa-X63X-67XXXXX64bb7 OnPrem_UserSid:  OnPrem_DeviceSid:

Return token to client, token type: UDA, hierarchyId: XXXX4f9c-XXXX-46a5-XXXX-7612c324XXXX, userId: 00000000-0000-0000-0000-000000000000, deviceId: GUID:XXXXaee9-cXXc-4ccd-XXXX-f1417d81XXX
```


## <a name="content-location-request"></a>콘텐츠 위치 요청

클라이언트는 CCM 토큰이 있는 응답을 받으면 이 토큰을 사용해서 CMG를 통해 사이트 정보 및 콘텐츠 위치를 요청합니다. 다음 항목이 **ccmsetup.log**에 로깅됩니다.

``` Log
Cached encrypted token for 'S-1-5-18'. Will expire at '00/99/2999 00:00:00'
Sending location request to 'CloudManagementGateway.cloudapp.net/CCM_PROXY_MUTUALAUTH/XXXXXX037938216' with payload '< Request >
Appending CCM Token to the header.
```


## <a name="client-installation"></a>클라이언트 설치

디바이스는 클라이언트 콘텐츠를 다운로드하고 설치를 시작합니다.

### <a name="communication-validation"></a>통신 유효성 검사

- CMG는 CMG, CMG 연결점 및 HTTP(S), 관리 지점 데이터베이스 요청을 통해 클라이언트 토큰이 유효한지 검사합니다.
- 클라이언트는 CMG 서비스 인증서 또는 관리 인증서를 확인합니다.
- CMG 서비스 인증서의 PKI: 클라이언트는 로컬 저장소에서 CMG 인증서의 루트 CA(인증 기관)를 요청합니다.
- 타사 CMG 서비스 인증서: 클라이언트는 인터넷에 게시된 루트 CA를 통해 인증서의 유효성을 자동으로 검사합니다.


## <a name="common-issues"></a>일반적인 문제

- 루트 CA가 없음
- CRL 확인을 사용하도록 설정함: 인터넷에 CRL을 게시하거나 명령줄에서 **/NoCRLcheck** 옵션 사용
- WPJ 인증서를 찾을 수 없음: 클라이언트가 Azure AD에 등록되었으나 Azure AD에 가입되지 않음

/NoCRLCheck는 ccmsetup 부트스트랩에만 사용하는 것이 적합합니다. 클라이언트가 완전히 작동하려면 인터넷에 CRL을 게시해야 합니다. 해결 방법으로, 사이트의 클라이언트 통신 구성에서 CRL 확인을 사용하지 않도록 설정할 수 있습니다. 그렇지 않은 경우, 위치 서비스에서 보안 설정이 새로 고쳐진 후 클라이언트가 더 이상 서버와 통신하지 못합니다.


## <a name="client-registration"></a>클라이언트 등록

![Azure AD 등록 워크플로 다이어그램](media/azure-ad-registration-workflow.png)  

### <a name="1-configuration-manager-client-request-registration"></a>1. 구성 관리자 클라이언트 요청 등록

다음 항목이 **ClientIDManagerStartup.log**에 로깅됩니다.

``` Log
[RegTask] - Client is not registered. Sending registration request for GUID:1XXXXXEF-5XX8-4XX3-XEDX-XXXFBFF78XXX ...
Registering client using AAD auth.
```

### <a name="2-configuration-manager-request-azure-ad-token-to-register-client"></a>2. 클라이언트를 등록하기 위한 Configuration Manager 요청 Azure AD 토큰

다음 항목이 **ADALOperationProvider.log**에 로깅됩니다.

``` Log
Getting AAD (user) token with: ClientId = f1f9b14e-XXXX-4f17-XXXX-2593f6eee91e, ResourceUrl = https://ConfigMgrService, AccountId = X49FC29A-ECE3-XXX-A3C1-XXXXXXF035A6E
Retrieved AAD token for AAD user '00000000-0000-0000-0000-000000000000'
```

#### <a name="21-configuration-manager-client-is-registered"></a>2.1 구성 관리자 클라이언트가 등록됨  

다음 항목이 **ClientIDManagerStartup.log**에 로깅됩니다.

``` Log
[RegTask] - Client is registered. Server assigned ClientID is GUID:1XXXXXEF-5XX8-4XX3-XEDX-XXXFBFF78XXX. Approval status 3
```

> [!NOTE]  
> 클라이언트 등록 동안 항상 인증서 유효성 검사가 실행됩니다. 이 프로세스는 Azure AD 인증 방법을 사용하여 클라이언트를 등록하는 경우에도 발생합니다.


### <a name="3-configuration-manager-client-token-request"></a>3. 구성 관리자 클라이언트 토큰 요청

사이트에서 클라이언트를 등록하면 클라이언트는 CCM 토큰을 요청합니다. CCM 토큰이 로컬 시스템 계정에 대해 암호화되고(S-1-5-18), 8시간 동안 캐시됩니다. 8시간 후에 토큰이 만료되고 클라이언트는 토큰 갱신을 요청합니다.

다음 항목이 **ClientIDManagerStartup.log**에 로깅됩니다.

``` Log
Getting CCM Token from STS server 'MP.MYCORP.COM'
Getting CCM Token from https://MP.MYCORP.COM/CCM_STS
...
Cached encrypted token for 'S-1-5-18'. Will expire at 'XX/XX/XX XX:XX:XX'
```

#### <a name="31-cmg-gets-request"></a>3.1 CMG가 요청 가져오기

다음 항목이 **IIS.log**에 로깅됩니다.

``` Log
RD0003FF74XX2 10.0.0.4 GET /CCM_STS - 443 - HTTP/1.1 python-requests/2.20.0 - - 13.95.234.44 404 0 2 1477 154 15
```

#### <a name="32-cmg-forwards-request-to-cmg-connection-point"></a>3.2 CMG가 CMG 연결점에 요청 전달

다음 항목이 **CMGService.log**에 로깅됩니다.

``` Log
RequestUri: /CCM_PROXY_SERVERAUTH/XXXXXX037938216/CCM_STS  RequestCount: 769  RequestSize: 1081595 Bytes  ResponseCount: 769     ResponseSize: 36143 Bytes  AverageElapsedTime: 3945 ms
```

#### <a name="33-cmg-connection-point-transforms-cmg-client-request-to-management-point-client-request"></a>3.3 CMG 연결점이 CMG 클라이언트 요청을 관리 지점 클라이언트 요청으로 변환

다음 항목이 **SMS_CLOUD_PROXYCONNECTOR.log**에 로깅됩니다.

``` Log
MessageID: 3087bd34-b82c-4950-b972-e82bb0fb8385 RequestURI: https://MP.MYCORP.COM/CCM_STS EndpointName: CCM_STS ResponseHeader: HTTP/1.1 200 OK ~~ ResponseBodySize: 0 ElapsedTime: 2 ms
```

#### <a name="34-management-point-verifies-user-token-in-site-database"></a>3.4 관리 지점이 사이트 데이터베이스에서 사용자 토큰 확인

다음 항목이 **CCM_STS.log**에 로깅됩니다.

``` Log
Validated AAD token. TokenType: Device TenantId: XXXXe388-XXXX-485c-XXXX-e8e4eb41XXXX UserId: 00000000-0000-0000-0000-000000000000 DeviceId: 0XXXXX80-77XX-4XXa-X63X-67XXXXX64bb7 OnPrem_UserSid:  OnPrem_DeviceSid:

Return token to client, token type: UDA, hierarchyId: XXXX4f9c-XXXX-46a5-XXXX-7612c324XXXX, userId: 00000000-0000-0000-0000-000000000000, deviceId: GUID:XXXXaee9-cXXc-4ccd-XXXX-f1417d81XXX
```
