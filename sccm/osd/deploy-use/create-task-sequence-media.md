---
title: 작업 순서 미디어 만들기
titleSuffix: Configuration Manager
description: Configuration Manager 환경의 대상 컴퓨터에 OS를 배포하는 작업 순서 미디어를 만듭니다.
ms.date: 05/02/2019
ms.prod: configuration-manager
ms.technology: configmgr-osd
ms.topic: conceptual
ms.assetid: 90498b4b-6a9b-43cd-b465-1d6c9a52df1c
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 101cee8ed63cacfc41481b2df69b42e1760d8837
ms.sourcegitcommit: 1bccb61bf3c7c69d51e0e224d0619c8f608e8777
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "65082811"
---
# <a name="create-task-sequence-media"></a>작업 순서 미디어 만들기

*적용 대상: System Center Configuration Manager(현재 분기)*

참조 컴퓨터에서 OS 이미지를 캡처하거나 현재 Configuration Manager 환경에 있는 대상 컴퓨터에 OS를 배포하기 위해 미디어를 사용할 수 있습니다. 이때 만들 수 있는 미디어는 CD, DVD 세트, USB 플래시 드라이브 등입니다.  

미디어는 주로 네트워크에 연결되지 않은 대상 컴퓨터 또는 Configuration Manager 사이트에 낮은 대역폭으로 연결된 대상 컴퓨터에 운영 체제를 배포하는 데 사용됩니다. 그러나 미디어를 사용하여 기존 Windows OS 외부에서 OS 배포를 시작할 수도 있습니다. 이 방법은 기존 OS가 없거나, OS가 작동하지 않거나, 하드 디스크를 재분할하려는 경우에 유용합니다.  

배포 미디어에는 부팅 가능한 미디어, 독립 실행형 미디어, 사전 준비된 미디어 등이 있습니다. 미디어의 콘텐츠는 사용할 미디어 유형에 따라 달라집니다. 예를 들어, 독립 실행형 미디어는 OS 배포하는 작업 순서를 포함합니다. 다른 유형의 미디어는 관리 지점에서 작업 순서를 검색합니다.  

> [!IMPORTANT]  
> 작업 순서 미디어를 만들려면 Configuration Manager 콘솔을 실행하는 컴퓨터의 관리자여야 합니다. 관리자가 아닌 경우 작업 순서 미디어 만들기 마법사를 시작할 때 관리자 자격 증명에 대한 메시지가 표시됩니다.  


## <a name="BKMK_PlanCaptureMedia"></a> 미디어 캡처

미디어 캡처를 사용하면 참조 컴퓨터에서 OS 이미지를 캡처할 수 있습니다. 미디어 캡처에는 참조 컴퓨터를 시작하는 부팅 이미지와, OS 이미지를 캡처하는 작업 순서가 포함되어 있습니다.

미디어 캡처를 만드는 방법에 대한 자세한 내용은 [미디어 캡처 만들기](/sccm/osd/deploy-use/create-capture-media)를 참조하세요.  


## <a name="BKMK_PlanBootableMedia"></a> 부팅 가능한 미디어

부팅 가능한 미디어는 다음 구성 요소를 포함합니다.

- 부팅 이미지
- 선택적 [시작 전 명령](/sccm/osd/understand/prestart-commands-for-task-sequence-media) 및 필수 파일
- Configuration Manager 이진 파일

대상 컴퓨터는 시작할 때 네트워크에 연결하여 네트워크에서 작업 순서, OS 이미지 및 기타 필수 콘텐츠를 검색합니다. 작업 순서는 이 미디어에 포함되어 있지 않으므로 미디어를 다시 만들지 않고도 작업 순서나 콘텐츠를 변경할 수 있습니다.  

> [!IMPORTANT]  
> 부팅 가능한 미디어에서 패키지는 암호화되지 않습니다. 미디어에 암호를 추가하는 방법과 같은 적합한 보안 방법을 활용하여 권한 없는 사용자로부터 패키지 콘텐츠를 보호합니다.  

부팅 가능한 미디어를 만드는 방법에 대한 자세한 내용은 [부팅 가능한 미디어 만들기](/sccm/osd/deploy-use/create-bootable-media)를 참조하세요.  


## <a name="BKMK_PlanPrestagedMedia"></a> 사전 준비된 미디어

사전 준비된 미디어를 사용하면 프로비저닝 프로세스 전에 부팅 가능한 미디어와 OS 이미지를 하드 디스크에 적용할 수 있습니다. 사전 준비된 미디어는 Windows 이미지(WIM) 파일입니다. 이러한 미디어는 제조업체가 운영 체제 미설치 컴퓨터에 설치하거나 프로덕션 Configuration Manager 환경에 연결되지 않은 엔터프라이즈 준비 센터에 설치할 수 있습니다.  

사전 준비된 미디어에는 대상 컴퓨터를 시작하는 데 사용되는 부팅 이미지와 대상 컴퓨터에 적용되는 OS 이미지가 포함됩니다. 사전 준비된 미디어에 포함할 애플리케이션, 패키지 및 드라이버 패키지를 지정할 수도 있습니다. OS를 배포하는 작업 순서는 미디어에 포함되지 않습니다. 사전 준비된 미디어를 사용하는 작업 순서를 배포할 때 클라이언트는 먼저 로컬 작업 순서 캐시에서 유효한 콘텐츠를 확인합니다. 콘텐츠를 찾을 수 없거나 콘텐츠가 수정된 경우 클라이언트는 배포 지점 또는 피어에서 콘텐츠를 다운로드합니다.  

사전 준비된 미디어는 새 컴퓨터를 최종 사용자에게 배송하기 전에 컴퓨터의 하드 드라이브에 적용합니다. 사전 준비된 미디어를 적용한 후에 컴퓨터를 처음으로 시작하면 Windows PE에서 시작합니다. 또한 OS 배포 프로세스를 완료하는 작업 순서를 찾기 위해 관리 지점에 연결합니다.  

> [!IMPORTANT]  
> 사전 준비된 미디어의 패키지는 암호화되지 않습니다. 미디어에 암호를 추가하는 방법과 같은 적합한 보안 방법을 활용하여 권한 없는 사용자로부터 패키지 콘텐츠를 보호합니다.  

사전 준비된 미디어를 만드는 방법에 대한 자세한 내용은 [사전 준비된 미디어 만들기](/sccm/osd/deploy-use/create-prestaged-media)를 참조하세요.  


## <a name="BKMK_PlanStandaloneMedia"></a> 독립 실행형 미디어

독립 실행형 미디어에는 OS를 배포하는 데 필요한 모든 항목이 들어 있습니다. 이 콘텐츠에는 작업 순서와 그 밖의 모든 필수 콘텐츠가 포함됩니다. 독립 실행형 미디어에는 OS 배포에 필요한 모든 항목이 저장되므로 독립 실행형 미디어에 필요한 디스크 공간은 다른 미디어 유형에 필요한 디스크 공간보다 훨씬 더 큽니다.  

독립 실행형 미디어를 만드는 방법에 대한 자세한 내용은 [독립 실행형 미디어 만들기](/sccm/osd/deploy-use/create-stand-alone-media)를 참조하세요.  


## <a name="considerations-when-using-https"></a>HTTPS 사용 시 고려 사항

HTTPS 통신을 사용하도록 관리 지점과 배포 지점을 구성하는 경우 중앙 관리 사이트가 아닌 기본 사이트에 부팅 미디어 및 사전 준비된 미디어를 만들어야 합니다. 또한 다음 사항을 고려하여 미디어를 동적으로 구성할 것인지 또는 사이트 기반으로 구성할 것인지 결정해야 합니다.  

- 미디어를 동적 미디어로 구성하려면 모든 기본 사이트에 미디어를 만드는 데 사용한 사이트의 루트 CA(인증 기관)가 있어야 합니다. 계층 내 모든 기본 사이트에 루트 CA를 가져올 수 있습니다.  

- Configuration Manager 계층 구조 내의 기본 사이트에서 서로 다른 루트 CA를 사용할 경우 각 사이트에 사이트 기반 미디어를 사용해야 합니다.  
