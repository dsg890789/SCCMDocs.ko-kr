---
title: 데스크톱 Analytics에서 자산
titleSuffix: Configuration Manager
description: 장치, 앱, Office 앱, Office 추가 기능 및 데스크톱 Analytics에서 Office 매크로에 대해 알아봅니다.
ms.date: 01/25/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: d07198cf-49bb-4712-8c63-063b4302cc11
author: aczechowski
ms.author: aaroncz
manager: dougeby
ROBOTS: NOINDEX
ms.collection: M365-identity-device-management
ms.openlocfilehash: 149c5f2a4469a353c6dce6fde86527ca95518484
ms.sourcegitcommit: 874d78f08714a509f61c52b154387268f5b73242
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56755288"
---
# <a name="assets-in-desktop-analytics"></a>데스크톱 Analytics에서 자산 

> [!Note]  
> 이 정보는 정식으로 발표 되기 전에 대폭 수정 될 수 있는 미리 보기 서비스에 연결 합니다. Microsoft는 여기에 제공된 정보와 관련하여 명시적이거나 묵시적인 어떤 보증도 하지 않습니다.  

데스크톱 Analytics에 데이터를 보고 하는 장치를 다음 자산 인벤토리를 제공 합니다.
- 장치  
- 하드웨어 드라이버  
- 설치 된 앱  
- Office 앱  
- Office 추가 기능  
- Office 매크로  

서비스 포털에서 선택 **자산** 데스크톱 분석 메뉴에서.


## <a name="devices"></a>장치

합니다 **장치** 탭 데스크톱 Analytics에 등록 하는 조직의 모든 장치에 대 한 키 정보를 표시 합니다. 열 또는 특정 값에 대 한 필터에서 정렬할 수 있습니다.

> [!NOTE]  
> 대시보드의 장치 수를 보고 되지 않습니다 예상 되는 경우 사용자 환경에 대 한 참조를 참조 하십시오 [데스크톱 Analytics 문제 해결](/sccm/desktop-analytics/troubleshooting)합니다.  



## <a name="apps"></a>앱

합니다 **앱** Windows 장치에서 검색 서비스에서는 모든 설치 된 앱을 탭 합니다.

**주목할 만한** 2% 이상의 등록 된 장치에 설치 된 앱입니다. <!--You can change the threshold of "noteworthy" by {doing something}.--> 

구성 된 **중요도** 는 다음 범주 중 하나를 설정 하 여 앱:

- 중요
- 중요 한
- 무시
- 검토 되지 않음

앱 목록에서 선택한 **편집**합니다. 이 작업에는 앱에 대 한 세부 정보가 표시 됩니다. 선택 된 **중요도** 값을 설정 하 고 드롭다운 메뉴입니다. 할당할 수도 있습니다는 **소유자**합니다. 모든 변경 하는 경우 선택 **저장할**합니다. 


## <a name="office-apps"></a>Office 앱

합니다 **Office 앱** 탭의 앱 탭 비슷합니다. Microsoft Word 또는 Excel 등의 앱만 표시 하 고 분류 또는 주목할 수 없습니다. 중요도 Office 앱에 대 한 소유자를 다른 앱과 동일한 방식으로 설정 합니다.


## <a name="office-add-ins"></a>Office 추가 기능

합니다 **Office 추가 기능의** 도구, 예를 들어, Microsoft Azure Information Protection 또는 분석 도구를 지 원하는 표시를 탭 합니다. 이 탭과 유사 하며 응용 프로그램 탭에서 중요 한 수를 포함 합니다. 앱에서와 마찬가지로 중요도 및 소유자를 설정 합니다. 


## <a name="office-macros"></a>Office 매크로

합니다 **Office 매크로** 탭 표시 여부를 모든 장치 최근에 액세스 매크로 포함할 수 있는 모든 파일입니다. 

<!-- (For a detailed list of these file types, see [File formats supported in the 2007 Office system (corrected)](https://blogs.technet.microsoft.com/office_resource_kit/2009/04/04/file-formats-supported-in-the-2007-office-system-corrected/) at the Office IT Pro blog.)
 -->

> [!NOTE]  
> 사용 하는 경우는 [Readiness Toolkit](https://aka.ms/readinesstoolkit) Office 추가 기능 및 VBA 매크로 대 한 Visual Basic의 경우이 탭도 표시 됩니다 해당 장치에서 추가 데이터입니다. 
> 
> Readiness Toolkit 데스크톱 Analytics를 사용 하는 데 필요가 없습니다.  



## <a name="next-steps"></a>다음 단계

- [데스크톱 Analytics 배포 계획에 알아봅니다](/sccm/desktop-analytics/about-deployment-plans)  

- [보안 및 기능 업데이트에 알아봅니다](/sccm/desktop-analytics/about-updates)  

