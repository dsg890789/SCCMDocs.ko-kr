---
title: Linux 및 UNIX에 대한 하드웨어 인벤토리
titleSuffix: Configuration Manager
description: System Center Configuration Manager에서 Linux 및 UNIX에 대한 하드웨어 인벤토리를 사용하는 방법을 알아봅니다.
ms.date: 02/22/2017
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: 1026d616-2a20-4fb2-8604-d331763937f8
author: aczechowski
manager: dougeby
ms.author: aaroncz
ms.openlocfilehash: 68e60611356cbaea3dc14a42776e89ecdc951008
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="hardware-inventory-for-linux-and-unix-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 Linux 및 UNIX에 대한 하드웨어 인벤토리

*적용 대상: System Center Configuration Manager(현재 분기)*

Linux 및 UNIX용 System Center Configuration Manager 클라이언트는 하드웨어 인벤토리를 지원합니다. 하드웨어 인벤토리를 수집하면 리소스 탐색기 또는 Configuration Manager 보고서에서 인벤토리 보기를 실행하고, 이러한 정보를 사용하여 다음과 같은 작업을 사용하도록 설정하는 컬렉션 및 쿼리를 만들 수 있습니다.  

-   소프트웨어 배포  

-   유지 관리 기간 적용  

-   사용자 지정 클라이언트 설정 배포  

 Linux 및 UNIX 서버에 대한 하드웨어 인벤토리에서는 표준 기반 CIM(Common Information Model) 서버를 사용합니다. CIM 서버는 소프트웨어 서비스(또는 데몬)로 실행되며, DMTF(Distributed Management Task Force) 표준을 기반으로 하는 관리 인프라를 제공합니다. CIM 서버는 Windows 기반 컴퓨터에서 사용할 수 있는 관리 인프라 WMI(Windows Management Infrastructure) CIM 기능과 유사한 기능을 제공합니다.  

 누적 업데이트 1부터는 Linux 및 UNIX용 클라이언트에 **Open Group** 의 오픈 소스 **omiserver**버전 1.0.6이 사용됩니다. (누적 업데이트 1 이전 버전의 클라이언트에서는 **nanowbem** 이 CIM 서버로 사용되었습니다.)  

 CIM 서버는 Linux 및 UNIX용 클라이언트의 일부로 설치됩니다. Linux 및 UNIX용 클라이언트는 CIM 서버와 직접 통신하고 CIM 서버의 WS-MAN 인터페이스를 사용하지 않습니다. 클라이언트를 설치하면 CIM 서버의 WS-MAN 포트를 사용할 수 없습니다. Microsoft는 현재 OMI(개방형 관리 인프라) 프로젝트를 통해 오픈 소스로 제공되는 CIM 서버를 개발했습니다. OMI 프로젝트에 대한 자세한 내용은 [Open Group](http://go.microsoft.com/fwlink/p/?LinkId=262317) 웹 사이트를 참조하세요.  

 Linux 및 UNIX 서버의 하드웨어 인벤토리는 기존의 Win32 WMI 클래스 및 속성을 Linux 및 UNIX 서버의 해당 클래스 및 속성으로 매핑하여 작동합니다. 이러한 클래스 및 속성의 일대일 매핑을 통해 Linux 및 UNIX 하드웨어 인벤토리를 Configuration Manager와 통합할 수 있습니다. Linux 및 UNIX 서버의 인벤토리 데이터는 Configuration Manager 콘솔 및 보고서에 Windows 기반 컴퓨터의 인벤토리와 함께 표시됩니다. 이러한 방법으로 유형이 다른 관리 환경을 일관적으로 제공합니다.  

> [!TIP]  
>  **운영 체제** 클래스에 **캡션** 값을 사용하여 쿼리 및 컬렉션에서 다양한 Linux 및 UNIX 운영 체제를 식별할 수 있습니다.  

##  <a name="BKMK_ConfigHardwareforLnU"></a> Linux 및 UNIX 서버에 대한 하드웨어 인벤토리 구성  
 기본 클라이언트 설정을 사용하거나 사용자 지정 클라이언트 장치 설정을 만들어 하드웨어 인벤토리를 구성할 수 있습니다. 사용자 지정 클라이언트 장치 설정을 사용하면 Linux 및 UNIX 서버에서만 수집하려는 클래스 및 속성을 구성할 수 있습니다. Linux 및 UNIX 서버에서 전체 및 델타 인벤토리를 수집할 시기에 대한 사용자 지정 일정을 지정할 수도 있습니다.  

 Linux 및 UNIX용 클라이언트에서는 다음과 같이 Linux 및 UNIX 서버에서 사용할 수 있는 하드웨어 인벤토리 클래스를 지원합니다.  

-   Win32_BIOS  

-   Win32_ComputerSystem  

-   Win32_DiskDrive  

-   Win32_DiskPartition  

-   Win32_NetworkAdapter  

-   Win32_NetworkAdapterConfiguration  

-   Win32_OperatingSystem  

-   Win32_Process  

-   Win32_Service  

-   Win32Reg_AddRemovePrograms  

-   SMS_LogicalDisk  

-   SMS_Processor  

 이러한 인벤토리 클래스의 일부 속성은 Configuration Manager에서 Linux 및 UNIX 컴퓨터에 사용할 수 없습니다.  

##  <a name="BKMK_OperationsforHardwareforLnU"></a> 하드웨어 인벤토리에 대한 작업  
 Linux 및 UNIX 서버에서 하드웨어 인벤토리를 수집한 후에는 다른 컴퓨터에서 수집한 인벤토리를 보는 것과 같은 방식으로 해당 정보를 보고 사용할 수 있습니다.  

-   리소스 탐색기를 사용하면 Linux 및 UNIX 서버의 하드웨어 인벤토리에 대한 세부 정보를 볼 수 있습니다.  

-   특정 하드웨어 구성에 따라 쿼리 만들기  

-   특정 하드웨어 구성을 기반으로 하는 쿼리 기반 컬렉션을 만듭니다.  

-   하드웨어 구성에 대한 특정 세부 정보를 표시하는 보고서를 실행합니다.  

 Linux 또는 UNIX 서버의 하드웨어 인벤토리는 클라이언트 설정에 구성하는 일정에 따라 실행됩니다. 기본적으로 7일마다 실행됩니다. Linux 및 UNIX용 클라이언트는 전체 인벤토리 주기 및 델타 인벤토리 주기를 모두 지원합니다.  

 또한 Linux 또는 UNIX 서버의 클라이언트를 하드웨어 인벤토리를 즉시 실행하도록 강제할 수 있습니다. 하드웨어 인벤토리를 실행하려면 하드웨어 인벤토리 주기를 시작하도록 클라이언트에서 **루트** 자격 증명을 사용하여 **/opt/microsoft/configmgr/bin/ccmexec-rs hinv**명령을 실행합니다.  

 하드웨어 인벤토리에 대한 작업은 클라이언트 로그 파일인 **scxcm.log**에 입력됩니다.  

##  <a name="BKMK_CustomHINVforLinux"></a> 개방형 관리 인프라를 사용하여 사용자 지정 하드웨어 인벤토리를 만드는 방법  
 Linux 및 UNIX용 클라이언트는 OMI(개방형 관리 인프라)를 사용하여 만들 수 있는 사용자 지정 하드웨어 인벤토리를 지원합니다. 이렇게 하려면 다음 단계를 사용합니다.  

1.  OMI 원본을 사용하여 사용자 지정 인벤토리 공급자 만들기  

2.  새로운 공급자를 사용하여 인벤토리를 보고하도록 컴퓨터 구성  

3.  새 공급자를 지원하기 위해 Configuration Manager를 사용하도록 설정  

###  <a name="BKMK_LinuxProvider"></a> Linux 및 UNIX 컴퓨터에 대한 사용자 지정 하드웨어 인벤토리 공급자 만들기  
 Linux 및 UNIX용 Configuration Manager 클라이언트에 대한 사용자 지정 하드웨어 인벤토리 공급자를 만들려면 **OMI Source - v.1.0.6**을 사용하고 OMI 시작 가이드에 있는 다음 지침을 따릅니다. 이 프로세스에는 새 공급자의 스키마를 정의하는 MOF(Managed Object Format) 파일 만들기가 포함됩니다. 나중에 MOF 파일을 Configuration Manager로 가져와서 새 사용자 지정 인벤토리 클래스를 지원할 수 있습니다.  

 OMI Source v.1.0.6, 및 OMI 시작 가이드 모두 [Open Group](http://go.microsoft.com/fwlink/p/?LinkId=262317) 웹 사이트에서 다운로드할 수 있습니다. 이 다운로드는 OpenGroup.org 웹 사이트의 **OMI(개방형 관리 인프라)** 웹 페이지에 있는 [문서](http://go.microsoft.com/fwlink/p/?LinkId=286805)탭에 있습니다.  

###  <a name="BKMK_AddProvidertoLinux"></a> 사용자 지정 하드웨어 인벤토리 공급자를 사용하여 Linux 또는 UNIX를 실행하는 각 컴퓨터 구성  
 사용자 지정 인벤토리 공급자를 만든 후에는 수집할 인벤토리가 있는 각 컴퓨터에 공급자 라이브러리 파일을 복사하고 등록해야 합니다.  

1.  공급자 라이브러리를 인벤토리를 수집하려는 각 Linux 및 UNIX 컴퓨터에 복사합니다. 공급자 라이브러리의 이름은 **XYZ_MyProvider.so**와 유사합니다.  

2.  그런 다음 각 Linux 및 UNIX 컴퓨터에서 공급자 라이브러리를 OMI 서버에 등록합니다. OMI 서버는 Linux 및 UNIX용 Configuration Manager 클라이언트를 설치할 때 설치되지만 사용자 지정 공급자는 수동으로 등록해야 합니다. 공급자를 등록하려면 **/opt/microsoft/omi/bin/omireg XYZ_MyProvider.so**명령줄을 사용합니다.  

3.  새 공급자를 등록한 후에는 **omicli** 도구를 사용하여 공급자를 테스트합니다. Linux 및 UNIX용 **omicli** 도구는 Linux 및 UNIX용 Configuration Manager 클라이언트를 설치할 때 각 Linux 및 UNIX 컴퓨터에 설치됩니다. 예를 들면 여기서 **XYZ_MyProvider** 는 만든 공급자 이름이며, 컴퓨터에 **/opt/microsoft/omi/bin/omicli ei root/cimv2 XYZ_MyProvider**명령을 실행합니다.  

     **omicli** 및 사용자 지정 공급자 테스트에 대한 자세한 내용은 OMI 시작 가이드를 참조하세요.  

> [!TIP]  
>  사용자 지정 공급자를 배포 하 고 각 Linux 및 UNIX 클라이언트 컴퓨터에서 사용자 지정 공급자를 등록 하려면 소프트웨어 배포를 사용 합니다.  

###  <a name="BKMK_AddLinuxProvidertoCM"></a> Configuration Manager에서 새 인벤토리 클래스 사용  
 Linux 및 UNIX 컴퓨터에서 새 공급자가 보고하는 인벤토리에 대해 Configuration Manager로 보고하려면 먼저 사용자 지정 공급자의 스키마를 정의하는 MOF(Managed Object Format) 파일을 가져와야 합니다.  

 사용자 지정 MOF 파일을 Configuration Manager로 가져오려면 [System Center Configuration Manager에서 하드웨어 인벤토리를 구성하는 방법](../../../../core/clients/manage/inventory/configure-hardware-inventory.md)을 참조하세요.  
