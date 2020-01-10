---
title: 리소스 탐색기 기본 인벤토리 클래스
titleSuffix: Configuration Manager
description: 리소스 탐색기에 표시되는 클래스를 보여 줍니다.
ms.date: 11/12/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 1d333f4c-0f85-4278-b421-064cf01529a5
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: a8202dbcb677b2313982a538db0982a21c2fc761
ms.sourcegitcommit: 148745e1c3d9817d8beea20684a54436210959c6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75824268"
---
# <a name="resource-explorer-default-inventory-classes"></a>리소스 탐색기 기본 인벤토리 클래스

*적용 대상: Configuration Manager(현재 분기)*

이 문서에서는 리소스 탐색기의 기본 인벤토리 클래스에 대해 설명합니다.

기본 인벤토리 클래스는 다음과 같습니다.

## <a name="1394-controller"></a>1394 컨트롤러

네임스페이스: root\cimv2

클래스 Win32_1394Controller


- (String) DeviceID

- (UInt16) Availability

- (String) Caption

- (UInt32) ConfigManagerErrorCode

- (Boolean) ConfigManagerUserConfig

- (String) Description

- (Boolean) ErrorCleared

- (String) ErrorDescription

- (DateTime) InstallDate

- (UInt32) LastErrorCode

- (String) Manufacturer

- (UInt32) MaxNumberControlled

- (String) Name

- (String) PNPDeviceID

- (UInt16) PowerManagementCapabilities[]

- (Boolean) PowerManagementSupported

- (UInt16) ProtocolSupported

- (String) Status

- (UInt16) StatusInfo

- (String) SystemName

- (DateTime) TimeOfLastReset



## <a name="account-sid"></a>계정 SID

네임스페이스: root\cimv2

클래스 Win32_AccountSID

- (String) Element

- (String) Setting



## <a name="activesync-service"></a>ActiveSync 서비스

네임스페이스: root\SmsDm

클래스 SMS_ActiveSyncService


- (UInt32) MajorVersion

- (UInt32) MinorVersion

- (String) LastSyncTime



## <a name="amt-agent"></a>AMT 에이전트

네임스페이스: root\cimv2\sms

클래스 SMS_AMTObject


- (UInt32) DeviceID

- (String) AMT

- (String) AMTApps

- (String) BiosVersion

- (String) BuildNumber

- (String) Flash

- (String) LegacyMode

- (String) Netstack

- (UInt32) ProvisionMode

- (UInt32) ProvisionState

- (String) RecoveryBuildNum

- (String) RecoveryVersion

- (String) Sku

- (UInt32) TLSMode

- (String) VendorID

- (UInt32) ZTCEnabled



## <a name="appv-client-application"></a>AppV 클라이언트 애플리케이션

네임스페이스: root\AppV

클래스 AppvClientApplication


- (String) ApplicationId

- (String) PackageId

- (String) PackageVersionId

- (Boolean) EnabledForUser

- (Boolean) EnabledGlobally

- (String) Name

- (String) TargetPath

- (String) Version



## <a name="appv-client-package"></a>AppV 클라이언트 패키지

네임스페이스: root\AppV

클래스 AppvClientPackage


- (String) PackageId

- (String) VersionId

- (String) Assets[]

- (String) DeploymentMachineData

- (String) DeploymentUserData

- (Boolean) HasAssetIntelligence

- (Boolean) InUse

- (Boolean) IsPublishedGlobally

- (Boolean) IsPublishedToUser

- (String) Name

- (UInt64) PackageSize

- (String) Path

- (UInt16) PercentLoaded

- (String) UserConfigurationData

- (String) Version



## <a name="autostart-software"></a>자동 시작 Software

네임스페이스: root\cimv2\sms

클래스 SMS_AutoStartSoftware


- (String) FilePropertiesHash

- (String) BinFileVersion

- (String) BinProductVersion

- (String) Description

- (String) FileName

- (String) FilePropertiesHashEx

- (String) FileVersion

- (String) Location

- (String) Product

- (String) ProductVersion

- (String) Publisher

- (String) StartupType

- (String) StartupValue



## <a name="baseboard"></a>베이스보드

네임스페이스: root\cimv2

클래스 Win32_BaseBoard


- (String) Tag

- (String) Caption

- (String) ConfigOptions[]

- (String) Description

- (Boolean) HostingBoard

- (Boolean) HotSwappable

- (DateTime) InstallDate

- (String) Manufacturer

- (String) Model

- (String) Name

- (String) OtherIdentifyingInfo

- (String) PartNumber

- (Boolean) PoweredOn

- (String) Product

- (Boolean) Removable

- (Boolean) Replaceable

- (String) RequirementsDescription

- (Boolean) RequiresDaughterBoard

- (String) SerialNumber

- (String) SKU

- (String) SlotLayout

- (Boolean) SpecialRequirements

- (String) Status

- (String) Version



## <a name="battery"></a>배터리

네임스페이스: root\cimv2

클래스 Win32_Battery


- (String) DeviceID

- (UInt16) Availability

- (UInt16) BatteryStatus

- (String) Caption

- (UInt16) Chemistry

- (UInt32) ConfigManagerErrorCode

- (Boolean) ConfigManagerUserConfig

- (String) Description

- (UInt32) DesignCapacity

- (UInt64) DesignVoltage

- (Boolean) ErrorCleared

- (String) ErrorDescription

- (UInt16) EstimatedChargeRemaining

- (UInt32) EstimatedRunTime

- (UInt32) ExpectedLife

- (UInt32) FullChargeCapacity

- (DateTime) InstallDate

- (UInt32) LastErrorCode

- (UInt32) MaxRechargeTime

- (String) Name

- (String) PNPDeviceID

- (UInt16) PowerManagementCapabilities[]

- (Boolean) PowerManagementSupported

- (String) SmartBatteryVersion

- (String) Status

- (UInt16) StatusInfo

- (String) SystemName

- (UInt32) TimeOnBattery

- (UInt32) TimeToFullCharge



## <a name="bitlocker"></a>BitLocker

네임스페이스: root\cimv2\security\MicrosoftVolumeEncryption

클래스 Win32_EncryptableVolume


- (String) DeviceID

- (String) DriveLetter

- (String) PersistentVolumeID

- (UInt32) ProtectionStatus



## <a name="bitlocker-encryption-details"></a>BitLocker 암호화 세부 정보

네임스페이스: root\cimv2

클래스 Win32_BitLockerEncryptionDetails


- (String) BitlockerPersistentVolumeId

- (SInt32) Compliant

- (SInt32) ConversionStatus

- (String) DeviceId

- (String) DriveLetter

- (SInt32) EncryptionMethod

- (String) EnforcePolicyDate

- (Boolean) IsAutoUnlockEnabled

- (SInt32) KeyProtectorTypes[]

- (String) MbamPersistentVolumeId

- (SInt32) MbamVolumeType

- (String) NoncomplianceDetectedDate

- (SInt32) ProtectionStatus

- (SInt32) ReasonsForNonCompliance[]



## <a name="bitlocker-policy"></a>BitLocker 정책

네임스페이스: root\cimv2

클래스 Win32Reg_MBAMPolicy


- (String) EncodedComputerName

- (UInt32) EncryptionMethod

- (UInt32) FixedDataDriveAutoUnlock

- (UInt32) FixedDataDriveEncryption

- (UInt32) FixedDataDrivePassphrase

- (String) KeyName

- (String) LastConsoleUser

- (UInt32) MBAMMachineError

- (UInt32) MBAMPolicyEnforced

- (UInt32) OsDriveEncryption

- (UInt32) OsDriveProtector

- (DateTime) UserExemptionDate



## <a name="boot-configuration"></a>부팅 구성

네임스페이스: root\cimv2

클래스 Win32_BootConfiguration


- (String) Name

- (String) BootDirectory

- (String) ConfigurationPath

- (String) Description

- (String) LastDrive

- (String) ScratchDirectory

- (String) SettingID

- (String) TempDirectory



## <a name="browser-helper-object"></a>브라우저 도우미 개체

네임스페이스: root\cimv2\sms

클래스 SMS_BrowserHelperObject


- (String) FilePropertiesHash

- (String) BinFileVersion

- (String) BinProductVersion

- (String) CLSID

- (String) Description

- (String) FileName

- (String) FilePropertiesHashEx

- (String) FileVersion

- (String) Product

- (String) ProductVersion

- (String) Publisher

- (String) Version



## <a name="ccm_rax"></a>CCM_RAX

네임스페이스: root\ccm\cimodels

클래스 CCM_RAXInfo


- (String) AppID

- (String) FeedURL

- (String) UserSID



## <a name="cd-rom"></a>CD-ROM

네임스페이스: root\cimv2

클래스 Win32_CDROMDrive


- (String) DeviceID

- (UInt16) Availability

- (UInt16) Capabilities[]

- (String) CapabilityDescriptions[]

- (String) Caption

- (String) CompressionMethod

- (UInt32) ConfigManagerErrorCode

- (Boolean) ConfigManagerUserConfig

- (UInt64) DefaultBlockSize

- (String) Description

- (String) Drive

- (Boolean) DriveIntegrity

- (Boolean) ErrorCleared

- (String) ErrorDescription

- (String) ErrorMethodology

- (UInt16) FileSystemFlags

- (UInt32) FileSystemFlagsEx

- (String) ID

- (DateTime) InstallDate

- (UInt32) LastErrorCode

- (String) Manufacturer

- (UInt64) MaxBlockSize

- (UInt32) MaximumComponentLength

- (UInt64) MaxMediaSize

- (Boolean) MediaLoaded

- (String) MediaType

- (UInt64) MinBlockSize

- (String) Name

- (Boolean) NeedsCleaning

- (UInt32) NumberOfMediaSupported

- (String) PNPDeviceID

- (UInt16) PowerManagementCapabilities[]

- (Boolean) PowerManagementSupported

- (String) RevisionLevel

- (UInt32) SCSIBus

- (UInt16) SCSILogicalUnit

- (UInt16) SCSIPort

- (UInt16) SCSITargetId

- (UInt64) Size

- (String) Status

- (UInt16) StatusInfo

- (String) SystemName

- (String) VolumeName

- (String) VolumeSerialNumber



## <a name="client-events"></a>클라이언트 이벤트

네임스페이스: root\ccm\invagt

클래스 ClientEvents


- (String) EventName

- (UInt16) Count



## <a name="computer-system"></a>컴퓨터 시스템

네임스페이스: root\cimv2

클래스 Win32_ComputerSystem


- (String) Name

- (UInt16) AdminPasswordStatus

- (Boolean) AutomaticResetBootOption

- (Boolean) AutomaticResetCapability

- (UInt16) BootOptionOnLimit

- (UInt16) BootOptionOnWatchDog

- (Boolean) BootROMSupported

- (String) BootupState

- (String) Caption

- (UInt16) ChassisBootupState

- (SInt16) CurrentTimeZone

- (Boolean) DaylightInEffect

- (String) Description

- (String) Domain

- (UInt16) DomainRole

- (UInt16) FrontPanelResetStatus

- (Boolean) InfraredSupported

- (String) InitialLoadInfo[]

- (DateTime) InstallDate

- (UInt16) KeyboardPasswordStatus

- (String) LastLoadInfo

- (String) Manufacturer

- (String) Model

- (String) NameFormat

- (Boolean) NetworkServerModeEnabled

- (UInt32) NumberOfProcessors

- (String) OEMLogoBitmap

- (String) OEMStringArray[]

- (SInt64) PauseAfterReset

- (UInt16) PowerManagementCapabilities[]

- (Boolean) PowerManagementSupported

- (UInt16) PowerOnPasswordStatus

- (UInt16) PowerState

- (UInt16) PowerSupplyState

- (String) PrimaryOwnerContact

- (String) PrimaryOwnerName

- (UInt16) ResetCapability

- (SInt16) ResetCount

- (SInt16) ResetLimit

- (String) Roles[]

- (String) Status

- (String) SupportContactDescription[]

- (UInt16) SystemStartupDelay

- (String) SystemStartupOptions[]

- (UInt8) SystemStartupSetting

- (String) SystemType

- (UInt16) ThermalState

- (UInt64) TotalPhysicalMemory

- (String) UserName

- (UInt16) WakeUpType



## <a name="computer-system-ex"></a>컴퓨터 시스템 확장

네임스페이스: root\cimv2

클래스 CCM_ComputerSystemExtended


- (String) Name

- (UInt16) PCSystemType



## <a name="computer-system-product"></a>컴퓨터 시스템 제품

네임스페이스: root\cimv2

클래스 Win32_ComputerSystemProduct


- (String) IdentifyingNumber

- (String) Name

- (String) Version

- (String) Caption

- (String) Description

- (String) SKUNumber

- (String) UUID

- (String) Vendor



## <a name="sms-advanced-client-ports"></a>SMS 고급 클라이언트 포트

네임스페이스: root\cimv2

클래스 Win32Reg_SMSAdvancedClientPorts


- (String) InstanceKey

- (UInt32) HttpsPortName

- (UInt32) PortName



## <a name="sms-advanced-client-ssl-configurations"></a>SMS 고급 클라이언트 SSL 구성

네임스페이스: root\cimv2

클래스 Win32Reg_SMSAdvancedClientSSLConfiguration


- (String) InstanceKey

- (String) CertificateSelectionCriteria

- (String) CertificateStore

- (UInt32) ClientAlwaysOnInternet

- (UInt32) HttpsStateFlags

- (String) InternetMPHostName

- (UInt32) SelectFirstCertificate



## <a name="sms-advanced-client-state"></a>SMS 고급 클라이언트 상태

네임스페이스: root\ccm

클래스 CCM_InstalledComponent


- (String) Name

- (String) DisplayName

- (String) Version



## <a name="connected-device"></a>연결된 디바이스

네임스페이스: root\SmsDm

클래스 SMS_ActiveSyncConnectedDevice


- (String) DeviceOEMInfo

- (String) DeviceType

- (String) OS_Major

- (String) OS_Minor

- (String) OS_Platform

- (String) ProcessorArchitecture

- (String) ProcessorLevel

- (String) ProcessorRevision

- (String) InstalledClientID

- (String) InstalledClientServer

- (String) InstalledClientVersion

- (String) LastSyncTime

- (String) OS_AdditionalInfo

- (String) OS_Build



## <a name="sms_defaultbrowser"></a>SMS_DefaultBrowser

네임스페이스: root\cimv2\sms

클래스 SMS_DefaultBrowser


- (String) BrowserProgId



## <a name="desktop"></a>데스크톱

네임스페이스: root\cimv2

클래스 Win32_Desktop


- (String) Name

- (UInt32) BorderWidth

- (String) Caption

- (Boolean) CoolSwitch

- (UInt32) CursorBlinkRate

- (String) Description

- (Boolean) DragFullWindows

- (UInt32) GridGranularity

- (UInt32) IconSpacing

- (String) IconTitleFaceName

- (UInt32) IconTitleSize

- (Boolean) IconTitleWrap

- (String) Pattern

- (Boolean) ScreenSaverActive

- (String) ScreenSaverExecutable

- (Boolean) ScreenSaverSecure

- (UInt32) ScreenSaverTimeout

- (String) SettingID

- (String) Wallpaper

- (Boolean) WallpaperStretched

- (Boolean) WallpaperTiled



## <a name="desktop-monitor"></a>데스크톱 모니터

네임스페이스: root\cimv2

클래스 Win32_DesktopMonitor


- (String) DeviceID

- (UInt16) Availability

- (UInt32) Bandwidth

- (String) Caption

- (UInt32) ConfigManagerErrorCode

- (Boolean) ConfigManagerUserConfig

- (String) Description

- (UInt16) DisplayType

- (Boolean) ErrorCleared

- (String) ErrorDescription

- (DateTime) InstallDate

- (Boolean) IsLocked

- (UInt32) LastErrorCode

- (String) MonitorManufacturer

- (String) MonitorType

- (String) Name

- (UInt32) PixelsPerXLogicalInch

- (UInt32) PixelsPerYLogicalInch

- (String) PNPDeviceID

- (UInt16) PowerManagementCapabilities[]

- (Boolean) PowerManagementSupported

- (UInt32) ScreenHeight

- (UInt32) ScreenWidth

- (String) Status

- (UInt16) StatusInfo

- (String) SystemName



## <a name="device-info"></a>디바이스 정보

네임스페이스: 예약됨

클래스 Device_Info


- (String) CertExpiry

- (String) DeviceName

- (String) Manufacturer

- (String) Model

- (String) OS



## <a name="mdm-devdetail"></a>MDM DevDetail

네임스페이스: root\cimv2\mdm\dmmap

클래스 MDM_DevDetail_Ext01


- (String) InstanceID

- (String) ParentID

- (String) DeviceHardwareData

- (String) WLANMACAddress



## <a name="disk"></a>디스크

네임스페이스: root\cimv2

클래스 Win32_DiskDrive


- (String) DeviceID

- (UInt16) Availability

- (UInt32) BytesPerSector

- (UInt16) Capabilities[]

- (String) CapabilityDescriptions[]

- (String) Caption

- (String) CompressionMethod

- (UInt32) ConfigManagerErrorCode

- (Boolean) ConfigManagerUserConfig

- (UInt64) DefaultBlockSize

- (String) Description

- (Boolean) ErrorCleared

- (String) ErrorDescription

- (String) ErrorMethodology

- (UInt32) Index

- (DateTime) InstallDate

- (String) InterfaceType

- (UInt32) LastErrorCode

- (String) Manufacturer

- (UInt64) MaxBlockSize

- (UInt64) MaxMediaSize

- (Boolean) MediaLoaded

- (String) MediaType

- (UInt64) MinBlockSize

- (String) Model

- (String) Name

- (Boolean) NeedsCleaning

- (UInt32) NumberOfMediaSupported

- (UInt32) Partitions

- (String) PNPDeviceID

- (UInt16) PowerManagementCapabilities[]

- (Boolean) PowerManagementSupported

- (UInt32) SCSIBus

- (UInt16) SCSILogicalUnit

- (UInt16) SCSIPort

- (UInt16) SCSITargetId

- (UInt32) SectorsPerTrack

- (UInt64) Size

- (String) Status

- (UInt16) StatusInfo

- (String) SystemName

- (UInt64) TotalCylinders

- (UInt32) TotalHeads

- (UInt64) TotalSectors

- (UInt64) TotalTracks

- (UInt32) TracksPerCylinder



## <a name="partition"></a>파티션

네임스페이스: root\cimv2

클래스 Win32_DiskPartition


- (String) DeviceID

- (UInt16) Access

- (UInt16) Availability

- (UInt64) BlockSize

- (Boolean) Bootable

- (Boolean) BootPartition

- (String) Caption

- (UInt32) ConfigManagerErrorCode

- (Boolean) ConfigManagerUserConfig

- (String) Description

- (UInt32) DiskIndex

- (Boolean) ErrorCleared

- (String) ErrorDescription

- (String) ErrorMethodology

- (UInt32) HiddenSectors

- (UInt32) Index

- (DateTime) InstallDate

- (UInt32) LastErrorCode

- (String) Name

- (UInt64) NumberOfBlocks

- (String) PNPDeviceID

- (UInt16) PowerManagementCapabilities[]

- (Boolean) PowerManagementSupported

- (Boolean) PrimaryPartition

- (String) Purpose

- (Boolean) RewritePartition

- (UInt64) Size

- (UInt64) StartingOffset

- (String) Status

- (UInt16) StatusInfo

- (String) SystemName

- (String) Type



## <a name="dma"></a>DMA

네임스페이스: root\cimv2

클래스 Win32_DeviceMemoryAddress

- (UInt64) StartingAddress

- (String) Caption

- (String) Description

- (UInt64) EndingAddress

- (DateTime) InstallDate

- (String) MemoryType

- (String) Name

- (String) Status



## <a name="dma-channel"></a>DMA 채널

네임스페이스: root\cimv2

클래스 Win32_DMAChannel


- (UInt32) DMAChannel

- (UInt16) AddressSize

- (UInt16) Availability

- (Boolean) BurstMode

- (UInt16) ByteMode

- (String) Caption

- (UInt16) ChannelTiming

- (String) Description

- (DateTime) InstallDate

- (UInt32) MaxTransferSize

- (String) Name

- (UInt32) Port

- (String) Status

- (UInt16) TransferWidths[]

- (UInt16) TypeCTiming

- (UInt16) WordMode



## <a name="driver---vxd"></a>드라이버 - VxD

네임스페이스: root\cimv2

클래스 Win32_DriverVXD


- (String) Name

- (String) SoftwareElementID

- (UInt16) SoftwareElementState

- (UInt16) TargetOperatingSystem

- (String) Version

- (String) BuildNumber

- (String) Caption

- (String) CodeSet

- (String) Control

- (String) Description

- (String) DeviceDescriptorBlock

- (String) IdentificationCode

- (DateTime) InstallDate

- (String) LanguageEdition

- (String) Manufacturer

- (String) OtherTargetOS

- (String) PM_API

- (String) SerialNumber

- (UInt32) ServiceTableSize

- (String) Status

- (String) V86_API



## <a name="embedded-device-information"></a>임베디드 디바이스 정보

네임스페이스: root\cimv2\sms

클래스 CCM_EmbeddedDeviceInformation


- (String) DeviceType

- (String) Model

- (String) OEMName



## <a name="environment"></a>환경

네임스페이스: root\cimv2

클래스 Win32_Environment


- (String) Name

- (String) UserName

- (String) Caption

- (String) Description

- (DateTime) InstallDate

- (String) Status

- (Boolean) SystemVariable

- (String) VariableValue



## <a name="firmware"></a>펌웨어

네임스페이스: root\cimv2\sms

클래스 SMS_Firmware


- (Boolean) UEFI

- (Boolean) SecureBoot



## <a name="usm-folder-redirection-health"></a>USM 폴더 리디렉션 상태

네임스페이스: root\cimv2\sms

클래스 SMS_FolderRedirectionHealth


- (String) FolderName

- (String) SID

- (UInt8) HealthStatus

- (DateTime) LastSuccessfulSyncTime

- (UInt8) LastSyncStatus

- (DateTime) LastSyncTime

- (Boolean) OfflineAccessEnabled

- (String) OfflineFileNameFolderGUID

- (Boolean) Redirected



## <a name="ide-controller"></a>IDE 컨트롤러

네임스페이스: root\cimv2

클래스 Win32_IDEController


- (String) DeviceID

- (UInt16) Availability

- (String) Caption

- (UInt32) ConfigManagerErrorCode

- (Boolean) ConfigManagerUserConfig

- (String) Description

- (Boolean) ErrorCleared

- (String) ErrorDescription

- (DateTime) InstallDate

- (UInt32) LastErrorCode

- (String) Manufacturer

- (UInt32) MaxNumberControlled

- (String) Name

- (String) PNPDeviceID

- (UInt16) PowerManagementCapabilities[]

- (Boolean) PowerManagementSupported

- (UInt16) ProtocolSupported

- (String) Status

- (UInt16) StatusInfo

- (String) SystemName

- (DateTime) TimeOfLastReset



## <a name="add-remove-programs-64"></a>프로그램 추가/제거(64)

네임스페이스: root\cimv2

클래스 Win32Reg_AddRemovePrograms64


- (String) ProdID

- (String) DisplayName

- (String) InstallDate

- (String) Publisher

- (String) Version



## <a name="add-remove-programs"></a>프로그램 추가/제거

네임스페이스: root\cimv2

클래스 Win32Reg_AddRemovePrograms


- (String) ProdID

- (String) DisplayName

- (String) InstallDate

- (String) Publisher

- (String) Version



## <a name="installed-executable"></a>설치된 실행 파일

네임스페이스: root\cimv2\sms

클래스 SMS_InstalledExecutable


- (String) ExecutableName

- (String) ProductCode

- (String) BinFileVersion

- (String) BinProductVersion

- (String) Description

- (String) FilePropertiesHash

- (String) FilePropertiesHashEx

- (UInt32) FileSize

- (String) FileVersion

- (Boolean) HasPatchAdded

- (String) InstalledFilePath

- (Boolean) IsSystemFile

- (Boolean) IsVitalFile

- (UInt32) Language

- (String) Product

- (String) ProductVersion

- (String) Publisher



## <a name="installed-software"></a>설치된 소프트웨어

네임스페이스: root\cimv2\sms

클래스 SMS_InstalledSoftware


- (String) SoftwareCode

- (String) ARPDisplayName

- (String) ChannelCode

- (String) ChannelID

- (String) CM_DSLID

- (String) EvidenceSource

- (DateTime) InstallDate

- (UInt32) InstallDirectoryValidation

- (String) InstalledLocation

- (String) InstallSource

- (UInt32) InstallType

- (UInt32) Language

- (String) LocalPackage

- (String) MPC

- (UInt32) OsComponent

- (String) PackageCode

- (String) ProductID

- (String) ProductName

- (String) ProductVersion

- (String) Publisher

- (String) RegisteredUser

- (String) ServicePack

- (String) SoftwarePropertiesHash

- (String) SoftwarePropertiesHashEx

- (String) UninstallString

- (String) UpgradeCode

- (UInt32) VersionMajor

- (UInt32) VersionMinor



## <a name="irq-table"></a>IRQ 테이블

네임스페이스: root\cimv2

클래스 Win32_IRQResource


- (UInt32) IRQNumber

- (UInt16) Availability

- (String) Caption

- (String) Description

- (Boolean) Hardware

- (DateTime) InstallDate

- (String) Name

- (Boolean) Shareable

- (String) Status

- (UInt16) TriggerLevel

- (UInt16) TriggerType

- (UInt32) Vector



## <a name="keyboard"></a>키보드

네임스페이스: root\cimv2

클래스 Win32_Keyboard


- (String) DeviceID

- (UInt16) Availability

- (String) Caption

- (UInt32) ConfigManagerErrorCode

- (Boolean) ConfigManagerUserConfig

- (String) Description

- (Boolean) ErrorCleared

- (String) ErrorDescription

- (DateTime) InstallDate

- (Boolean) IsLocked

- (UInt32) LastErrorCode

- (String) Layout

- (String) Name

- (UInt16) NumberOfFunctionKeys

- (UInt16) Password

- (String) PNPDeviceID

- (UInt16) PowerManagementCapabilities[]

- (Boolean) PowerManagementSupported

- (String) Status

- (UInt16) StatusInfo

- (String) SystemName



## <a name="load-order-group"></a>로드 순서 그룹

네임스페이스: root\cimv2

클래스 Win32_LoadOrderGroup


- (String) Name

- (String) Caption

- (String) Description

- (Boolean) DriverEnabled

- (UInt32) GroupOrder

- (DateTime) InstallDate

- (String) Status



## <a name="logical-disk"></a>논리 디스크

네임스페이스: root\cimv2\sms

클래스 SMS_LogicalDisk


- (String) DeviceID

- (UInt16) Access

- (UInt16) Availability

- (UInt64) BlockSize

- (String) Caption

- (Boolean) Compressed

- (UInt32) ConfigManagerErrorCode

- (Boolean) ConfigManagerUserConfig

- (String) Description

- (UInt32) DriveType

- (Boolean) ErrorCleared

- (String) ErrorDescription

- (String) ErrorMethodology

- (String) FileSystem

- (UInt64) FreeSpace

- (DateTime) InstallDate

- (UInt32) LastErrorCode

- (UInt32) MaximumComponentLength

- (UInt32) MediaType

- (String) Name

- (UInt64) NumberOfBlocks

- (String) PNPDeviceID

- (UInt16) PowerManagementCapabilities[]

- (Boolean) PowerManagementSupported

- (String) ProviderName

- (String) Purpose

- (UInt64) Size

- (String) Status

- (UInt16) StatusInfo

- (Boolean) SupportsFileBasedCompression

- (String) SystemName

- (String) VolumeName

- (String) VolumeSerialNumber



## <a name="memory"></a>메모리

네임스페이스: root\cimv2

클래스 CCM_LogicalMemoryConfiguration


- (String) Name

- (UInt64) AvailableVirtualMemory

- (UInt64) TotalPageFileSpace

- (UInt64) TotalPhysicalMemory

- (UInt64) TotalVirtualMemory



## <a name="device-bluetooth"></a>디바이스 Bluetooth

네임스페이스: 예약됨

클래스 Device_Bluetooth


- (Boolean) Enabled



## <a name="device-camera"></a>디바이스 카메라

네임스페이스: 예약됨

클래스 Device_Camera


- (Boolean) Enabled



## <a name="device-certificates"></a>디바이스 인증서

네임스페이스: 예약됨

클래스 Device_Certificates


- (String) Thumbprint

- (String) Type

- (String) IssuedBy

- (String) IssuedTo

- (DateTime) ValidFrom

- (DateTime) ValidTo



## <a name="device-client"></a>디바이스 클라이언트

네임스페이스: 예약됨

클래스 Device_Client


- (Boolean) DownloadWhenRoaming

- (Boolean) SyncWhenRoaming



## <a name="device-client-agent-version"></a>디바이스 클라이언트 에이전트 버전

네임스페이스: 예약됨

클래스 Device_ClientAgentVersion


- (String) Version



## <a name="device-computer-system"></a>디바이스 컴퓨터 시스템

네임스페이스: 예약됨

클래스 Device_ComputerSystem


- (String) CellularTechnology

- (String) DeviceClientID

- (String) DeviceManufacturer

- (String) DeviceModel

- (String) DMVersion

- (String) FirmwareVersion

- (String) HardwareVersion

- (String) IMEI

- (String) IMSI

- (UInt8) IsActivationLockEnabled

- (UInt8) Jailbroken

- (String) MEID

- (String) OEM

- (String) PhoneNumber

- (String) PlatformType

- (UInt32) ProcessorArchitecture

- (UInt32) ProcessorLevel

- (UInt32) ProcessorRevision

- (String) Product

- (String) ProductVersion

- (String) SerialNumber

- (String) SoftwareVersion

- (String) SubscriberCarrierNetwork



## <a name="device-display"></a>디바이스 디스플레이

네임스페이스: 예약됨

클래스 Device_Display


- (UInt32) HorizontalResolution

- (UInt64) NumberOfColors

- (UInt32) VerticalResolution



## <a name="device-email"></a>디바이스 메일

네임스페이스: 예약됨

클래스 Device_Email


- (String) OwnerEmailAddress

- (String) SyncDomain

- (String) SyncServer

- (String) SyncUser

- (String) Type



## <a name="device-encryption"></a>디바이스 암호화

네임스페이스: 예약됨

클래스 Device_Encryption


- (UInt32) EmailEncryptionAlgorithm

- (UInt32) EmailEncryptionNegotiation

- (Boolean) EmailEncryptionRequired

- (Boolean) EmailSigningAlgorithm

- (Boolean) EmailSigningRequired

- (Boolean) EncryptionCompliance

- (Boolean) PhoneMemoryEncrypted

- (Boolean) StorageCardEncrypted



## <a name="device-exchange"></a>디바이스 Exchange

네임스페이스: 예약됨

클래스 Device_Exchange


- (Boolean) ConflictResolution

- (SInt32) HTMLEmailTruncation

- (UInt32) MailFormat

- (UInt32) MaxCalendarAge

- (UInt32) MaxEmailAge

- (SInt32) MaxMailFileAttachmentSize

- (UInt32) OffPeakSyncFrequency

- (UInt32) PeakDays

- (String) PeakEndTime

- (String) PeakStartTime

- (UInt32) PeakSyncFrequency

- (SInt32) PlainTextEmailTruncation

- (Boolean) SendEmailImmediately

- (Boolean) SyncCalendar

- (Boolean) SyncContacts

- (Boolean) SyncEmail

- (Boolean) SyncTasks

- (Boolean) SyncWhenRoaming



## <a name="device-installed-applications"></a>디바이스 설치된 애플리케이션

네임스페이스: 예약됨

클래스 Device_InstalledApplications


- (String) Name

- (String) Version



## <a name="device-irda"></a>디바이스 IrDA

네임스페이스: 예약됨

클래스 Device_IrDA


- (Boolean) Enabled



## <a name="mobile-device-location"></a>모바일 디바이스 위치

네임스페이스: 예약됨

클래스 MDM_RemoteFind


- (Real32) Latitude

- (Real32) Longitude



## <a name="device-memory"></a>디바이스 메모리

네임스페이스: 예약됨

클래스 Device_Memory


- (UInt64) ProgramFree

- (UInt64) ProgramTotal

- (UInt64) RemovableStorageFree

- (UInt64) RemovableStorageTotal

- (UInt64) StorageFree

- (UInt64) StorageTotal



## <a name="device-os-information"></a>디바이스 OS 정보

네임스페이스: 예약됨

클래스 Device_OSInformation


- (String) Language

- (String) Platform

- (String) Version



## <a name="device-password"></a>디바이스 암호

네임스페이스: 예약됨

클래스 Device_Password


- (Boolean) AllowRecoveryPassword

- (UInt32) AutolockTimeout

- (Boolean) Enabled

- (UInt32) Expiration

- (UInt32) History

- (UInt32) MaxAttemptsBeforeWipe

- (UInt32) MinComplexChars

- (UInt32) MinLength

- (UInt8) PasswordQuality

- (UInt32) Type



## <a name="device-policy"></a>디바이스 정책

네임스페이스: 예약됨

클래스 Device_Policy


- (String) Name

- (Boolean) Enforced



## <a name="device-power"></a>디바이스 전원

네임스페이스: 예약됨

클래스 Device_Power


- (UInt32) BacklightACTimeout

- (UInt32) BacklightBatTimeout

- (SInt32) BackupPercent

- (SInt32) BatteryPercent



## <a name="mobile-device-security-status"></a>모바일 디바이스 보안 상태

네임스페이스: 예약됨

클래스 MDM_SecurityStatus


- (UInt32) HardwareEncryptionCaps

- (UInt8) PasscodeCompliant

- (UInt8) PasscodeCompliantWithProfiles

- (UInt8) PasscodePresent

- (UInt8) RequireEncryption



## <a name="device-windows-security-policy"></a>디바이스 Windows 보안 정책

네임스페이스: 예약됨

클래스 Device_WindowsSecurityPolicy


- (UInt32) ID

- (String) Name

- (UInt32) Value



## <a name="device-wlan"></a>디바이스 WLAN

네임스페이스: 예약됨

클래스 Device_WLAN


- (Boolean) Enabled

- (String) EthernetMAC

- (String) WiFiMAC



## <a name="modem"></a>모뎀

네임스페이스: root\cimv2

클래스 Win32_POTSModem


- (String) DeviceID

- (UInt16) AnswerMode

- (String) AttachedTo

- (UInt16) Availability

- (String) BlindOff

- (String) BlindOn

- (String) Caption

- (String) CompatibilityFlags

- (UInt16) CompressionInfo

- (String) CompressionOff

- (String) CompressionOn

- (UInt32) ConfigManagerErrorCode

- (Boolean) ConfigManagerUserConfig

- (String) ConfigurationDialog

- (String) CountriesSupported[]

- (String) CountrySelected

- (String) CurrentPasswords[]

- (String) DCB

- (String) Default

- (String) Description

- (String) DeviceLoader

- (String) DeviceType

- (UInt16) DialType

- (DateTime) DriverDate

- (Boolean) ErrorCleared

- (String) ErrorControlForced

- (UInt16) ErrorControlInfo

- (String) ErrorControlOff

- (String) ErrorControlOn

- (String) ErrorDescription

- (String) FlowControlHard

- (String) FlowControlOff

- (String) FlowControlSoft

- (String) InactivityScale

- (UInt32) InactivityTimeout

- (UInt32) Index

- (DateTime) InstallDate

- (UInt32) LastErrorCode

- (UInt32) MaxBaudRateToPhone

- (UInt32) MaxBaudRateToSerialPort

- (UInt16) MaxNumberOfPasswords

- (String) Model

- (String) ModemInfPath

- (String) ModemInfSection

- (String) ModulationBell

- (String) ModulationCCITT

- (UInt16) ModulationScheme

- (String) Name

- (String) PNPDeviceID

- (String) PortSubClass

- (UInt16) PowerManagementCapabilities[]

- (Boolean) PowerManagementSupported

- (String) Prefix

- (String) Properties

- (String) ProviderName

- (String) Pulse

- (String) Reset

- (String) ResponsesKeyName

- (UInt8) RingsBeforeAnswer

- (String) SpeakerModeDial

- (String) SpeakerModeOff

- (String) SpeakerModeOn

- (String) SpeakerModeSetup

- (String) SpeakerVolumeHigh

- (UInt16) SpeakerVolumeInfo

- (String) SpeakerVolumeLow

- (String) SpeakerVolumeMed

- (String) Status

- (UInt16) StatusInfo

- (String) StringFormat

- (Boolean) SupportsCallback

- (Boolean) SupportsSynchronousConnect

- (String) SystemName

- (String) Terminator

- (DateTime) TimeOfLastReset

- (String) Tone

- (String) VoiceSwitchFeature



## <a name="motherboard"></a>마더보드

네임스페이스: root\cimv2

클래스 Win32_MotherboardDevice


- (String) DeviceID

- (UInt16) Availability

- (String) Caption

- (UInt32) ConfigManagerErrorCode

- (Boolean) ConfigManagerUserConfig

- (String) Description

- (Boolean) ErrorCleared

- (String) ErrorDescription

- (DateTime) InstallDate

- (UInt32) LastErrorCode

- (String) Name

- (String) PNPDeviceID

- (UInt16) PowerManagementCapabilities[]

- (Boolean) PowerManagementSupported

- (String) PrimaryBusType

- (String) RevisionNumber

- (String) SecondaryBusType

- (String) Status

- (UInt16) StatusInfo

- (String) SystemName


## <a name="nap-client"></a>NAP 클라이언트

네임스페이스: root\Nap

클래스 NAP_Client


- (String) name

- (String) description

- (String) fixupURL

- (Boolean) napEnabled

- (String) napProtocolVersion

- (String) probationTime

- (UInt32) systemIsolationState



## <a name="nap-system-health-agent"></a>NAP 시스템 상태 에이전트

네임스페이스: root\Nap

클래스 NAP_SystemHealthAgent


- (UInt32) ID

- (String) description

- (UInt32) fixupState

- (String) friendlyName

- (String) infoClsid

- (Boolean) isBound

- (UInt8) percentage

- (String) registrationDate

- (String) vendorName

- (String) version



## <a name="network-adapter"></a>네트워크 어댑터

네임스페이스: root\cimv2

클래스 Win32_NetworkAdapter


- (String) DeviceID

- (String) AdapterType

- (Boolean) AutoSense

- (UInt16) Availability

- (String) Caption

- (UInt32) ConfigManagerErrorCode

- (Boolean) ConfigManagerUserConfig

- (String) Description

- (Boolean) ErrorCleared

- (String) ErrorDescription

- (UInt32) Index

- (DateTime) InstallDate

- (Boolean) Installed

- (UInt32) LastErrorCode

- (String) MACAddress

- (String) Manufacturer

- (UInt32) MaxNumberControlled

- (UInt64) MaxSpeed

- (String) Name

- (String) NetworkAddresses[]

- (String) PermanentAddress

- (String) PNPDeviceID

- (UInt16) PowerManagementCapabilities[]

- (Boolean) PowerManagementSupported

- (String) ProductName

- (String) ServiceName

- (UInt64) Speed

- (String) Status

- (UInt16) StatusInfo

- (String) SystemName

- (DateTime) TimeOfLastReset



## <a name="network-adapter-configuration"></a>네트워크 어댑터 구성

네임스페이스: root\cimv2

클래스 Win32_NetworkAdapterConfiguration


- (UInt32) Index

- (Boolean) ArpAlwaysSourceRoute

- (Boolean) ArpUseEtherSNAP

- (String) Caption

- (String) DatabasePath

- (Boolean) DeadGWDetectEnabled

- (String) DefaultIPGateway[]

- (UInt8) DefaultTOS

- (UInt8) DefaultTTL

- (String) Description

- (Boolean) DHCPEnabled

- (DateTime) DHCPLeaseExpires

- (DateTime) DHCPLeaseObtained

- (String) DHCPServer

- (String) DNSDomain

- (String) DNSDomainSuffixSearchOrder[]

- (Boolean) DNSEnabledForWINSResolution

- (String) DNSHostName

- (String) DNSServerSearchOrder[]

- (Boolean) DomainDNSRegistrationEnabled

- (UInt32) ForwardBufferMemory

- (Boolean) FullDNSRegistrationEnabled

- (UInt16) GatewayCostMetric[]

- (UInt8) IGMPLevel

- (String) IPAddress[]

- (UInt32) IPConnectionMetric

- (Boolean) IPEnabled

- (Boolean) IPFilterSecurityEnabled

- (Boolean) IPPortSecurityEnabled

- (String) IPSecPermitIPProtocols[]

- (String) IPSecPermitTCPPorts[]

- (String) IPSecPermitUDPPorts[]

- (String) IPSubnet[]

- (Boolean) IPUseZeroBroadcast

- (String) IPXAddress

- (Boolean) IPXEnabled

- (String) IPXFrameType

- (UInt32) IPXMediaType

- (String) IPXNetworkNumber[]

- (String) IPXVirtualNetNumber

- (UInt32) KeepAliveInterval

- (UInt32) KeepAliveTime

- (String) MACAddress

- (UInt32) MTU

- (UInt32) NumForwardPackets

- (Boolean) PMTUBHDetectEnabled

- (Boolean) PMTUDiscoveryEnabled

- (String) ServiceName

- (String) SettingID

- (UInt32) TcpipNetbiosOptions

- (UInt32) TcpMaxConnectRetransmissions

- (UInt32) TcpMaxDataRetransmissions

- (UInt32) TcpNumConnections

- (Boolean) TcpUseRFC1122UrgentPointer

- (UInt16) TcpWindowSize

- (Boolean) WINSEnableLMHostsLookup

- (String) WINSHostLookupFile

- (String) WINSPrimaryServer

- (String) WINSScopeID

- (String) WINSSecondaryServer



## <a name="network-client"></a>네트워크 클라이언트

네임스페이스: root\cimv2

클래스 Win32_NetworkClient


- (String) Name

- (String) Caption

- (String) Description

- (DateTime) InstallDate

- (String) Manufacturer

- (String) Status



## <a name="network-login-profile"></a>네트워크 로그인 프로필

네임스페이스: root\cimv2

클래스 Win32_NetworkLoginProfile


- (String) Name

- (DateTime) AccountExpires

- (UInt32) AuthorizationFlags

- (UInt32) BadPasswordCount

- (String) Caption

- (UInt32) CodePage

- (String) Comment

- (UInt32) CountryCode

- (String) Description

- (UInt32) Flags

- (String) FullName

- (String) HomeDirectory

- (String) HomeDirectoryDrive

- (DateTime) LastLogoff

- (DateTime) LastLogon

- (String) LogonHours

- (String) LogonServer

- (UInt64) MaximumStorage

- (UInt32) NumberOfLogons

- (String) Parameters

- (DateTime) PasswordAge

- (DateTime) PasswordExpires

- (UInt32) PrimaryGroupId

- (UInt32) Privileges

- (String) Profile

- (String) ScriptPath

- (String) SettingID

- (UInt32) UnitsPerWeek

- (String) UserComment

- (UInt32) UserId

- (String) UserType

- (String) Workstations



## <a name="nt-eventlog-file"></a>NT 이벤트 로그 파일

네임스페이스: root\cimv2

클래스 Win32_NTEventlogFile


- (String) Name

- (UInt32) AccessMask

- (Boolean) Archive

- (String) Caption

- (Boolean) Compressed

- (String) CompressionMethod

- (DateTime) CreationDate

- (String) Description

- (String) Drive

- (String) EightDotThreeFileName

- (Boolean) Encrypted

- (String) EncryptionMethod

- (String) Extension

- (String) FileName

- (UInt64) FileSize

- (String) FileType

- (String) FSName

- (Boolean) Hidden

- (DateTime) InstallDate

- (UInt64) InUseCount

- (DateTime) LastAccessed

- (DateTime) LastModified

- (String) LogfileName

- (String) Manufacturer

- (UInt32) MaxFileSize

- (UInt32) NumberOfRecords

- (UInt32) OverwriteOutDated

- (String) OverWritePolicy

- (String) Path

- (Boolean) Readable

- (String) Sources[]

- (String) Status

- (Boolean) System

- (String) Version

- (Boolean) Writeable



## <a name="office365proplusconfigurations"></a>Office 365 ProPlus 구성

네임스페이스: root\cimv2

클래스 Office365ProPlusConfigurations


- (String) KeyName

- (String) AutoUpgrade

- (String) CCMManaged

- (String) CDNBaseUrl

- (String) cfgUpdateChannel

- (String) ClientCulture

- (String) ClientFolder

- (String) GPOChannel

- (String) GPOOfficeMgmtCOM

- (String) InstallationPath

- (String) LastScenario

- (String) LastScenarioResult

- (String) OfficeMgmtCOM

- (String) Platform

- (String) SharedComputerLicensing

- (String) UpdateChannel

- (String) UpdatePath

- (String) UpdatesEnabled

- (String) UpdateUrl

- (String) VersionToReport



## <a name="office-addin"></a>Office 추가 기능

네임스페이스: root\ccm\InvAgt

클래스 CCM_OfficeAddin


- (String) Architecture

- (String) ID

- (String) OfficeApp

- (String) Type

- (UInt32) AverageLoadTimeInMilliseconds

- (String) CLSID

- (String) CompanyName

- (UInt32) CrashCount

- (String) Description

- (UInt32) ErrorCount

- (String) FileName

- (UInt64) FileSize

- (UInt32) FileTimestamp

- (String) FileVersion

- (String) FriendlyName

- (String) FriendlyNameHash

- (String) IdHash

- (UInt32) LoadBehavior

- (UInt32) LoadCount

- (UInt32) LoadFailCount

- (String) ProductName

- (String) ProductVersion



## <a name="office-client-metric"></a>Office 클라이언트 메트릭

네임스페이스: root\ccm\InvAgt

클래스 CCM_OfficeClientMetric


- (String) OfficeApp

- (UInt32) CompatibilityErrorCount

- (UInt32) CrashedSessionCount

- (UInt32) MacroCompileErrorCount

- (UInt32) MacroRuntimeErrorCount

- (UInt32) SessionCount



## <a name="office-device-summary"></a>Office 디바이스 요약

네임스페이스: root\ccm\InvAgt

클래스 CCM_OfficeDeviceSummary


- (Boolean) IsProPlusInstalled

- (Boolean) IsTelemetryEnabled



## <a name="office-document-metric"></a>Office 문서 메트릭

네임스페이스: root\ccm\InvAgt

클래스 CCM_OfficeDocumentMetric


- (String) OfficeApp

- (UInt32) TotalCloudDocs

- (UInt32) TotalLegacyDocs

- (UInt32) TotalLocalDocs

- (UInt32) TotalMacroDocs

- (UInt32) TotalNonMacroDocs

- (UInt32) TotalUncDocs



## <a name="office-document-solution"></a>Office 문서 솔루션

네임스페이스: root\ccm\InvAgt

클래스 CCM_OfficeDocumentSolution


- (String) DocumentSolutionId

- (String) OfficeApp

- (UInt32) CompatibilityErrorCount

- (UInt32) CrashCount

- (String) ExampleFileName

- (UInt32) LoadCount

- (UInt32) LoadFailCount

- (UInt32) MacroCompileErrorCount

- (UInt32) MacroRuntimeErrorCount

- (String) Type



## <a name="office-macro-error"></a>Office 매크로 오류

네임스페이스: root\ccm\InvAgt

클래스 CCM_OfficeMacroError


- (String) DocumentSolutionId

- (UInt32) ErrorCode

- (UInt32) Count

- (UInt64) LastOccurrence

- (String) Type



## <a name="office-product-info"></a>Office 제품 정보

네임스페이스: root\ccm\InvAgt

클래스 CCM_OfficeProductInfo


- (String) ProductName

- (String) ProductVersion

- (String) Architecture

- (String) Channel

- (UInt32) IsProPlusInstalled

- (String) Language

- (String) LicenseState



## <a name="office-vba-rule-violation"></a>Office Vba 규칙 위반

네임스페이스: root\ccm\InvAgt

클래스 CCM_OfficeVbaRuleViolation


- (UInt32) RuleId

- (UInt32) FileCount

- (String) OfficeApp



## <a name="office-vbasummary"></a>Office VbaSummary

네임스페이스: root\ccm\InvAgt

클래스 CCM_OfficeVbaScanResultsSummary


- (UInt32) Design

- (UInt32) Design64

- (UInt32) DuplicateVba

- (Boolean) HasResults

- (UInt32) HasVba

- (UInt32) Inaccessible

- (UInt32) Issues

- (UInt32) Issues64

- (UInt32) IssuesNone

- (UInt32) IssuesNone64

- (UInt32) Locked

- (UInt32) NoVba

- (UInt32) Protected

- (UInt32) RemLimited

- (UInt32) RemLimited64

- (UInt32) RemSignificant

- (UInt32) RemSignificant64

- (UInt32) Score

- (UInt32) Score64

- (UInt32) Total

- (UInt32) Validation

- (UInt32) Validation64



## <a name="operating-system"></a>운영 체제

네임스페이스: root\cimv2

클래스 Win32_OperatingSystem


- (String) Name

- (String) BootDevice

- (String) BuildNumber

- (String) BuildType

- (String) Caption

- (String) CodeSet

- (String) CountryCode

- (String) CSDVersion

- (SInt16) CurrentTimeZone

- (Boolean) Debug

- (String) Description

- (Boolean) Distributed

- (UInt8) ForegroundApplicationBoost

- (UInt64) FreePhysicalMemory

- (UInt64) FreeSpaceInPagingFiles

- (UInt64) FreeVirtualMemory

- (DateTime) InstallDate

- (DateTime) LastBootUpTime

- (DateTime) LocalDateTime

- (String) Locale

- (String) Manufacturer

- (UInt32) MaxNumberOfProcesses

- (UInt64) MaxProcessMemorySize

- (String) MUILanguages[]

- (UInt32) NumberOfLicensedUsers

- (UInt32) NumberOfProcesses

- (UInt32) NumberOfUsers

- (UInt32) OperatingSystemSKU

- (String) Organization

- (String) OSArchitecture

- (UInt32) OSLanguage

- (UInt32) OSProductSuite

- (UInt16) OSType

- (String) OtherTypeDescription

- (String) PlusProductID

- (String) PlusVersionNumber

- (Boolean) Primary

- (UInt32) ProductType

- (String) RegisteredUser

- (String) SerialNumber

- (UInt16) ServicePackMajorVersion

- (UInt16) ServicePackMinorVersion

- (UInt64) SizeStoredInPagingFiles

- (String) Status

- (String) SystemDevice

- (String) SystemDirectory

- (UInt64) TotalSwapSpaceSize

- (UInt64) TotalVirtualMemorySize

- (UInt64) TotalVisibleMemorySize

- (String) Version

- (String) WindowsDirectory



## <a name="operating-system-ex"></a>운영 체제 확장

네임스페이스: root\cimv2

클래스 CCM_OperatingSystemExtended


- (String) Name

- (UInt32) SKU



## <a name="operating-system-recovery-configuration"></a>운영 체제 복구 구성

네임스페이스: root\cimv2

클래스 Win32_OSRecoveryConfiguration


- (String) Name

- (Boolean) AutoReboot

- (String) Caption

- (String) DebugFilePath

- (String) Description

- (Boolean) KernelDumpOnly

- (Boolean) OverwriteExistingDebugFile

- (Boolean) SendAdminAlert

- (String) SettingID

- (Boolean) WriteDebugInfo

- (Boolean) WriteToSystemLog



## <a name="optional-feature"></a>선택적 기능

네임스페이스: root\cimv2

클래스 Win32_OptionalFeature


- (String) Name

- (String) Caption

- (String) Description

- (DateTime) InstallDate

- (UInt32) InstallState

- (String) Status



## <a name="page-file-setting"></a>페이지 파일 설정

네임스페이스: root\cimv2

클래스 Win32_PageFileSetting


- (String) Name

- (String) Caption

- (String) Description

- (UInt32) InitialSize

- (UInt32) MaximumSize

- (String) SettingID



## <a name="parallel-port"></a>병렬 포트

네임스페이스: root\cimv2

클래스 Win32_ParallelPort


- (String) DeviceID

- (UInt16) Availability

- (UInt16) Capabilities[]

- (String) CapabilityDescriptions[]

- (String) Caption

- (UInt32) ConfigManagerErrorCode

- (Boolean) ConfigManagerUserConfig

- (String) Description

- (Boolean) DMASupport

- (Boolean) ErrorCleared

- (String) ErrorDescription

- (DateTime) InstallDate

- (UInt32) LastErrorCode

- (UInt32) MaxNumberControlled

- (String) Name

- (Boolean) OSAutoDiscovered

- (String) PNPDeviceID

- (UInt16) PowerManagementCapabilities[]

- (Boolean) PowerManagementSupported

- (UInt16) ProtocolSupported

- (String) Status

- (UInt16) StatusInfo

- (String) SystemName

- (DateTime) TimeOfLastReset



## <a name="bios"></a>BIOS

네임스페이스: root\cimv2

클래스 Win32_BIOS


- (String) Name

- (String) SoftwareElementID

- (UInt16) SoftwareElementState

- (UInt16) TargetOperatingSystem

- (String) Version

- (UInt16) BiosCharacteristics[]

- (String) BIOSVersion[]

- (String) BuildNumber

- (String) Caption

- (String) CodeSet

- (String) CurrentLanguage

- (String) Description

- (String) IdentificationCode

- (UInt16) InstallableLanguages

- (DateTime) InstallDate

- (String) LanguageEdition

- (String) ListOfLanguages[]

- (String) Manufacturer

- (String) OtherTargetOS

- (Boolean) PrimaryBIOS

- (DateTime) ReleaseDate

- (String) SerialNumber

- (String) SMBIOSBIOSVersion

- (UInt16) SMBIOSMajorVersion

- (UInt16) SMBIOSMinorVersion

- (Boolean) SMBIOSPresent

- (String) Status



## <a name="pcmcia-controller"></a>PCMCIA 컨트롤러

네임스페이스: root\cimv2

클래스 Win32_PCMCIAController


- (String) DeviceID

- (UInt16) Availability

- (String) Caption

- (UInt32) ConfigManagerErrorCode

- (Boolean) ConfigManagerUserConfig

- (String) Description

- (Boolean) ErrorCleared

- (String) ErrorDescription

- (DateTime) InstallDate

- (UInt32) LastErrorCode

- (String) Manufacturer

- (UInt32) MaxNumberControlled

- (String) Name

- (String) PNPDeviceID

- (UInt16) PowerManagementCapabilities[]

- (Boolean) PowerManagementSupported

- (UInt16) ProtocolSupported

- (String) Status

- (UInt16) StatusInfo

- (String) SystemName

- (DateTime) TimeOfLastReset



## <a name="physical-memory"></a>실제 메모리

네임스페이스: root\cimv2

클래스 Win32_PhysicalMemory


- (String) CreationClassName

- (String) Tag

- (String) BankLabel

- (UInt64) Capacity

- (String) Caption

- (UInt16) DataWidth

- (String) Description

- (String) DeviceLocator

- (UInt16) FormFactor

- (Boolean) HotSwappable

- (DateTime) InstallDate

- (UInt16) InterleaveDataDepth

- (UInt32) InterleavePosition

- (String) Manufacturer

- (UInt16) MemoryType

- (String) Model

- (String) Name

- (String) OtherIdentifyingInfo

- (String) PartNumber

- (UInt32) PositionInRow

- (Boolean) PoweredOn

- (Boolean) Removable

- (Boolean) Replaceable

- (String) SerialNumber

- (String) SKU

- (UInt32) Speed

- (String) Status

- (UInt16) TotalWidth

- (UInt16) TypeDetail

- (String) Version



## <a name="physicaldisk"></a>실제 디스크

네임스페이스: root\microsoft\windows\storage

클래스 MSFT_PhysicalDisk


- (String) ObjectId

- (UInt64) AllocatedSize

- (UInt16) BusType

- (UInt16) CannotPoolReason[]

- (Boolean) CanPool

- (String) Description

- (String) DeviceId

- (UInt16) EnclosureNumber

- (String) FirmwareVersion

- (String) FriendlyName

- (UInt16) HealthStatus

- (Boolean) IsIndicationEnabled

- (Boolean) IsPartial

- (UInt64) LogicalSectorSize

- (String) Manufacturer

- (UInt16) MediaType

- (String) Model

- (UInt16) OperationalStatus[]

- (String) OtherCannotPoolReasonDescription

- (String) PartNumber

- (String) PhysicalLocation

- (UInt64) PhysicalSectorSize

- (String) SerialNumber

- (UInt64) Size

- (UInt16) SlotNumber

- (String) SoftwareVersion

- (UInt32) SpindleSpeed

- (UInt16) SupportedUsages[]

- (String) UniqueId

- (UInt16) Usage



## <a name="pnp-device-driver"></a>PNP 디바이스 드라이버

네임스페이스: root\cimv2

클래스 Win32_PnpEntity


- (String) DeviceID

- (UInt16) Availability

- (String) Caption

- (String) ClassGuid

- (UInt32) ConfigManagerErrorCode

- (Boolean) ConfigManagerUserConfig

- (String) CreationClassName

- (String) Description

- (Boolean) ErrorCleared

- (String) ErrorDescription

- (DateTime) InstallDate

- (UInt32) LastErrorCode

- (String) Manufacturer

- (String) Name

- (String) PNPDeviceID

- (UInt16) PowerManagementCapabilities[]

- (Boolean) PowerManagementSupported

- (String) Service

- (String) Status

- (UInt16) StatusInfo

- (String) SystemCreationClassName

- (String) SystemName



## <a name="pointing-device"></a>포인팅 디바이스

네임스페이스: root\cimv2

클래스 Win32_PointingDevice


- (String) DeviceID

- (UInt16) Availability

- (String) Caption

- (UInt32) ConfigManagerErrorCode

- (Boolean) ConfigManagerUserConfig

- (String) Description

- (UInt16) DeviceInterface

- (UInt32) DoubleSpeedThreshold

- (Boolean) ErrorCleared

- (String) ErrorDescription

- (UInt16) Handedness

- (String) HardwareType

- (String) InfFileName

- (String) InfSection

- (DateTime) InstallDate

- (Boolean) IsLocked

- (UInt32) LastErrorCode

- (String) Manufacturer

- (String) Name

- (UInt8) NumberOfButtons

- (String) PNPDeviceID

- (UInt16) PointingType

- (UInt16) PowerManagementCapabilities[]

- (Boolean) PowerManagementSupported

- (UInt32) QuadSpeedThreshold

- (UInt32) Resolution

- (UInt32) SampleRate

- (String) Status

- (UInt16) StatusInfo

- (UInt32) Synch

- (String) SystemName



## <a name="portable-battery"></a>휴대용 배터리

네임스페이스: root\cimv2

클래스 Win32_PortableBattery


- (String) DeviceID

- (UInt16) Availability

- (UInt16) BatteryStatus

- (UInt16) CapacityMultiplier

- (String) Caption

- (UInt16) Chemistry

- (UInt32) ConfigManagerErrorCode

- (Boolean) ConfigManagerUserConfig

- (String) Description

- (UInt32) DesignCapacity

- (UInt64) DesignVoltage

- (Boolean) ErrorCleared

- (String) ErrorDescription

- (UInt16) EstimatedChargeRemaining

- (UInt32) EstimatedRunTime

- (UInt32) ExpectedLife

- (UInt32) FullChargeCapacity

- (DateTime) InstallDate

- (UInt32) LastErrorCode

- (String) Location

- (String) ManufactureDate

- (String) Manufacturer

- (UInt16) MaxBatteryError

- (UInt32) MaxRechargeTime

- (String) Name

- (String) PNPDeviceID

- (UInt16) PowerManagementCapabilities[]

- (Boolean) PowerManagementSupported

- (String) SmartBatteryVersion

- (String) Status

- (UInt16) StatusInfo

- (String) SystemName

- (UInt32) TimeOnBattery

- (UInt32) TimeToFullCharge



## <a name="ports"></a>포트

네임스페이스: root\cimv2

클래스 Win32_PortResource

- (UInt64) StartingAddress

- (Boolean) Alias

- (String) Caption

- (String) Description

- (UInt64) EndingAddress

- (DateTime) InstallDate

- (String) Name

- (String) Status



## <a name="power-capabilities"></a>전원 기능

네임스페이스: root\CCM\powermanagementagent

클래스 CCM_PwrMgmtSystemPowerCapabilities


- (UInt32) PreferredPMProfile

- (Boolean) ApmPresent

- (Boolean) BatteriesAreShortTerm

- (Boolean) FullWake

- (Boolean) LidPresent

- (String) MinDeviceWakeState

- (Boolean) ProcessorThrottle

- (String) RtcWake

- (Boolean) SystemBatteriesPresent

- (Boolean) SystemS1

- (Boolean) SystemS2

- (Boolean) SystemS3

- (Boolean) SystemS4

- (Boolean) SystemS5

- (Boolean) UpsPresent

- (Boolean) VideoDimPresent



## <a name="power-configurations"></a>전원 구성

네임스페이스: root\CCM\policy\machine\actualconfig

클래스 CCM_PowerConfig


- (String) PowerConfigID

- (UInt32) DurationInSec

- (String) NonPeakPowerPlan

- (String) NonPeakPowerPlanName

- (String) PeakPowerPlan

- (String) PeakPowerPlanName

- (String) PeakStartTimeHoursMin

- (String) WakeUpTimeHoursMin



## <a name="power-management-insomnia-reasons"></a>전원 관리 절전 모드 불가 이유

네임스페이스: root\CCM\powermanagementagent

클래스 CCM_PwrMgmtLastSuspendError


- (String) Requester

- (String) RequesterType

- (String) RequestType

- (DateTime) Time

- (UInt32) AdditionalCode

- (String) AdditionalInfo

- (String) RequesterInfo

- (Boolean) UnknownRequester



## <a name="power-management-daily"></a>일일 전원 관리

네임스페이스: root\CCM\powermanagementagent

클래스 CCM_PwrMgmtActualDay


- (DateTime) Date

- (String) TypeOfEvent

- (UInt32) hr0_1

- (UInt32) hr1_2

- (UInt32) hr10_11

- (UInt32) hr11_12

- (UInt32) hr12_13

- (UInt32) hr13_14

- (UInt32) hr14_15

- (UInt32) hr15_16

- (UInt32) hr16_17

- (UInt32) hr17_18

- (UInt32) hr18_19

- (UInt32) hr19_20

- (UInt32) hr2_3

- (UInt32) hr20_21

- (UInt32) hr21_22

- (UInt32) hr22_23

- (UInt32) hr23_0

- (UInt32) hr3_4

- (UInt32) hr4_5

- (UInt32) hr5_6

- (UInt32) hr6_7

- (UInt32) hr7_8

- (UInt32) hr8_9

- (UInt32) hr9_10

- (UInt32) minutesTotal



## <a name="power-client-opt-out-settings"></a>전원 클라이언트 옵트아웃 설정

네임스페이스: root\ccm\ClientSDK

클래스 CCM_PowerManagementClientOptoutSetting


- (Boolean) AdminAllowOptout

- (Boolean) EffectiveClientOptOut

- (Boolean) IsClientOptOut



## <a name="power-management-monthly"></a>월간 전원 관리

네임스페이스: root\CCM\powermanagementagent

클래스 CCM_PwrMgmtMonth


- (DateTime) MonthStart

- (UInt32) minutesComputerActive

- (UInt32) minutesComputerOn

- (UInt32) minutesComputerShutdown

- (UInt32) minutesComputerSleep

- (UInt32) minutesMonitorOn

- (UInt32) minutesTotal

- (String) TypeOfEvent



## <a name="power-settings"></a>전원 설정

네임스페이스: root\cimv2\sms

클래스 SMS_PowerSettings


- (String) GUID

- (String) ACSettingIndex

- (String) ACValue

- (String) DCSettingIndex

- (String) DCValue

- (String) Name

- (String) UnitSpecifier



## <a name="print-jobs"></a>인쇄 작업

네임스페이스: root\cimv2

클래스 Win32_PrintJob


- (String) Name

- (String) Caption

- (String) DataType

- (String) Description

- (String) Document

- (String) DriverName

- (DateTime) ElapsedTime

- (String) HostPrintQueue

- (DateTime) InstallDate

- (UInt32) JobId

- (String) JobStatus

- (String) Notify

- (String) Owner

- (UInt32) PagesPrinted

- (String) Parameters

- (String) PrintProcessor

- (UInt32) Priority

- (UInt32) Size

- (DateTime) StartTime

- (String) Status

- (UInt32) StatusMask

- (DateTime) TimeSubmitted

- (UInt32) TotalPages

- (DateTime) UntilTime



## <a name="printer-configuration"></a>프린터 구성

네임스페이스: root\cimv2

클래스 Win32_PrinterConfiguration


- (String) Name

- (UInt32) BitsPerPel

- (String) Caption

- (Boolean) Collate

- (UInt32) Color

- (UInt32) Copies

- (String) Description

- (String) DeviceName

- (UInt32) DisplayFlags

- (UInt32) DisplayFrequency

- (UInt32) DitherType

- (UInt32) DriverVersion

- (Boolean) Duplex

- (String) FormName

- (UInt32) HorizontalResolution

- (UInt32) ICMIntent

- (UInt32) ICMMethod

- (UInt32) LogPixels

- (UInt32) MediaType

- (UInt32) Orientation

- (UInt32) PaperLength

- (String) PaperSize

- (UInt32) PaperWidth

- (UInt32) PelsHeight

- (UInt32) PelsWidth

- (UInt32) PrintQuality

- (UInt32) Scale

- (String) SettingID

- (UInt32) SpecificationVersion

- (UInt32) TTOption

- (UInt32) VerticalResolution

- (UInt32) XResolution

- (UInt32) YResolution



## <a name="printer-device"></a>프린터 디바이스

네임스페이스: root\cimv2

클래스 Win32_Printer


- (String) DeviceID

- (UInt32) Attributes

- (UInt16) Availability

- (UInt32) AveragePagesPerMinute

- (UInt16) Capabilities[]

- (String) CapabilityDescriptions[]

- (String) Caption

- (UInt32) ConfigManagerErrorCode

- (Boolean) ConfigManagerUserConfig

- (UInt32) DefaultPriority

- (String) Description

- (UInt16) DetectedErrorState

- (String) DriverName

- (Boolean) ErrorCleared

- (String) ErrorDescription

- (UInt32) HorizontalResolution

- (DateTime) InstallDate

- (UInt32) JobCountSinceLastReset

- (UInt16) LanguagesSupported[]

- (UInt32) LastErrorCode

- (String) Location

- (String) Name

- (UInt16) PaperSizesSupported[]

- (String) PNPDeviceID

- (String) PortName

- (UInt16) PowerManagementCapabilities[]

- (Boolean) PowerManagementSupported

- (String) PrinterPaperNames[]

- (UInt32) PrinterState

- (UInt16) PrinterStatus

- (String) PrintJobDataType

- (String) PrintProcessor

- (String) SeparatorFile

- (String) ServerName

- (String) ShareName

- (Boolean) SpoolEnabled

- (DateTime) StartTime

- (String) Status

- (UInt16) StatusInfo

- (String) SystemName

- (DateTime) TimeOfLastReset

- (DateTime) UntilTime

- (UInt32) VerticalResolution



## <a name="process"></a>프로세스

네임스페이스: root\cimv2

클래스 Win32_Process


- (String) Handle

- (String) Caption

- (DateTime) CreationDate

- (String) Description

- (String) ExecutablePath

- (UInt16) ExecutionState

- (UInt32) HandleCount

- (DateTime) InstallDate

- (UInt64) KernelModeTime

- (UInt32) MaximumWorkingSetSize

- (UInt32) MinimumWorkingSetSize

- (String) Name

- (String) OSName

- (UInt64) OtherOperationCount

- (UInt64) OtherTransferCount

- (UInt32) PageFaults

- (UInt32) PageFileUsage

- (UInt32) ParentProcessId

- (UInt32) PeakPageFileUsage

- (UInt64) PeakVirtualSize

- (UInt32) PeakWorkingSetSize

- (UInt32) Priority

- (UInt64) PrivatePageCount

- (UInt32) ProcessId

- (UInt32) QuotaNonPagedPoolUsage

- (UInt32) QuotaPagedPoolUsage

- (UInt32) QuotaPeakNonPagedPoolUsage

- (UInt32) QuotaPeakPagedPoolUsage

- (UInt64) ReadOperationCount

- (UInt64) ReadTransferCount

- (UInt32) SessionId

- (String) Status

- (DateTime) TerminationDate

- (UInt32) ThreadCount

- (UInt64) UserModeTime

- (UInt64) VirtualSize

- (String) WindowsVersion

- (UInt64) WorkingSetSize

- (UInt64) WriteOperationCount

- (UInt64) WriteTransferCount



## <a name="processor"></a>프로세서

네임스페이스: root\cimv2\sms

클래스 SMS_Processor


- (String) DeviceID

- (UInt16) AddressWidth

- (UInt16) Architecture

- (UInt16) Availability

- (UInt16) BrandID

- (String) Caption

- (UInt32) ConfigManagerErrorCode

- (Boolean) ConfigManagerUserConfig

- (String) CPUHash

- (String) CPUKey

- (UInt16) CpuStatus

- (UInt32) CurrentClockSpeed

- (UInt16) CurrentVoltage

- (UInt16) DataWidth

- (String) Description

- (Boolean) ErrorCleared

- (String) ErrorDescription

- (UInt32) ExtClock

- (UInt16) Family

- (DateTime) InstallDate

- (Boolean) Is64Bit

- (Boolean) IsHyperthreadCapable

- (Boolean) IsHyperthreadEnabled

- (Boolean) IsMobile

- (Boolean) IsTrustedExecutionCapable

- (Boolean) IsVitualizationCapable

- (UInt32) L2CacheSize

- (UInt32) L2CacheSpeed

- (UInt32) L3CacheSize

- (UInt32) L3CacheSpeed

- (UInt32) LastErrorCode

- (UInt16) Level

- (UInt16) LoadPercentage

- (String) Manufacturer

- (UInt32) MaxClockSpeed

- (String) Name

- (UInt32) NormSpeed

- (UInt32) NumberOfCores

- (UInt32) NumberOfLogicalProcessors

- (String) OtherFamilyDescription

- (Boolean) PartOfDomain

- (UInt32) PCache

- (String) PNPDeviceID

- (UInt16) PowerManagementCapabilities[]

- (Boolean) PowerManagementSupported

- (String) ProcessorId

- (UInt16) ProcessorType

- (UInt16) Revision

- (String) Role

- (String) SocketDesignation

- (String) Status

- (UInt16) StatusInfo

- (String) Stepping

- (String) SystemName

- (String) UniqueId

- (UInt16) UpgradeMethod

- (String) Version

- (UInt32) VoltageCaps

- (String) Workgroup



## <a name="protected-volume-information"></a>보호된 볼륨 정보

네임스페이스: root\cimv2\sms

클래스 CCM_ProtectedVolumeInfo


- (String) Name

- (String) DriveLetter

- (UInt32) ProtectionType



## <a name="protocol"></a>프로토콜

네임스페이스: root\cimv2

클래스 Win32_NetworkProtocol


- (String) Name

- (String) Caption

- (Boolean) ConnectionlessService

- (String) Description

- (Boolean) GuaranteesDelivery

- (Boolean) GuaranteesSequencing

- (DateTime) InstallDate

- (UInt32) MaximumAddressSize

- (UInt32) MaximumMessageSize

- (Boolean) MessageOriented

- (UInt32) MinimumAddressSize

- (Boolean) PseudoStreamOriented

- (String) Status

- (Boolean) SupportsBroadcasting

- (Boolean) SupportsConnectData

- (Boolean) SupportsDisconnectData

- (Boolean) SupportsEncryption

- (Boolean) SupportsExpeditedData

- (Boolean) SupportsFragmentation

- (Boolean) SupportsGracefulClosing

- (Boolean) SupportsGuaranteedBandwidth

- (Boolean) SupportsMulticasting

- (Boolean) SupportsQualityofService



## <a name="quick-fix-engineering"></a>빠른 수정 엔지니어링

네임스페이스: root\cimv2

클래스 Win32_QuickFixEngineering


- (String) HotFixID

- (String) ServicePackInEffect

- (String) Caption

- (String) Description

- (String) FixComments

- (DateTime) InstallDate

- (String) InstalledBy

- (String) InstalledOn

- (String) Name

- (String) Status



## <a name="ccm-recently-used-applications"></a>CCM 최근에 사용한 애플리케이션

네임스페이스: root\cimv2\sms

클래스 CCM_RecentlyUsedApps


- (String) ExplorerFileName

- (String) FolderPath

- (String) LastUserName

- (String) AdditionalProductCodes

- (String) CompanyName

- (String) FileDescription

- (String) FilePropertiesHash

- (UInt32) FileSize

- (String) FileVersion

- (DateTime) LastUsedTime

- (UInt32) LaunchCount

- (String) msiDisplayName

- (String) msiPublisher

- (String) msiVersion

- (String) OriginalFileName

- (String) ProductCode

- (UInt32) ProductLanguage

- (String) ProductName

- (String) ProductVersion

- (String) SoftwarePropertiesHash



## <a name="registry"></a>레지스트리

네임스페이스: root\cimv2

클래스 Win32_Registry


- (String) Name

- (String) Caption

- (UInt32) CurrentSize

- (String) Description

- (DateTime) InstallDate

- (UInt32) MaximumSize

- (UInt32) ProposedSize

- (String) Status



## <a name="scsi-controller"></a>SCSI 컨트롤러

네임스페이스: root\cimv2

클래스 Win32_SCSIController


- (String) DeviceID

- (UInt16) Availability

- (String) Caption

- (UInt32) ConfigManagerErrorCode

- (Boolean) ConfigManagerUserConfig

- (UInt32) ControllerTimeouts

- (String) Description

- (String) DeviceMap

- (String) DriverName

- (Boolean) ErrorCleared

- (String) ErrorDescription

- (String) HardwareVersion

- (UInt32) Index

- (DateTime) InstallDate

- (UInt32) LastErrorCode

- (String) Manufacturer

- (UInt32) MaxDataWidth

- (UInt32) MaxNumberControlled

- (UInt64) MaxTransferRate

- (String) Name

- (String) PNPDeviceID

- (UInt16) PowerManagementCapabilities[]

- (Boolean) PowerManagementSupported

- (UInt16) ProtectionManagement

- (UInt16) ProtocolSupported

- (String) Status

- (UInt16) StatusInfo

- (String) SystemName

- (DateTime) TimeOfLastReset



## <a name="serial-port-configuration"></a>직렬 포트 구성

네임스페이스: root\cimv2

클래스 Win32_SerialPortConfiguration


- (String) Name

- (Boolean) AbortReadWriteOnError

- (UInt32) BaudRate

- (Boolean) BinaryModeEnabled

- (UInt32) BitsPerByte

- (String) Caption

- (Boolean) ContinueXMitOnXOff

- (Boolean) CTSOutflowControl

- (String) Description

- (Boolean) DiscardNULLBytes

- (Boolean) DSROutflowControl

- (Boolean) DSRSensitivity

- (String) DTRFlowControlType

- (UInt32) EOFCharacter

- (UInt32) ErrorReplaceCharacter

- (Boolean) ErrorReplacementEnabled

- (UInt32) EventCharacter

- (Boolean) IsBusy

- (String) Parity

- (Boolean) ParityCheckEnabled

- (String) RTSFlowControlType

- (String) SettingID

- (String) StopBits

- (UInt32) XOffCharacter

- (UInt32) XOffXMitThreshold

- (UInt32) XOnCharacter

- (UInt32) XOnXMitThreshold

- (UInt32) XOnXOffInFlowControl

- (UInt32) XOnXOffOutFlowControl



## <a name="serial-ports"></a>직렬 포트

네임스페이스: root\cimv2

클래스 Win32_SerialPort


- (String) DeviceID

- (UInt16) Availability

- (Boolean) Binary

- (UInt16) Capabilities[]

- (String) CapabilityDescriptions[]

- (String) Caption

- (UInt32) ConfigManagerErrorCode

- (Boolean) ConfigManagerUserConfig

- (String) Description

- (Boolean) ErrorCleared

- (String) ErrorDescription

- (DateTime) InstallDate

- (UInt32) LastErrorCode

- (UInt32) MaxBaudRate

- (UInt32) MaximumInputBufferSize

- (UInt32) MaximumOutputBufferSize

- (UInt32) MaxNumberControlled

- (String) Name

- (Boolean) OSAutoDiscovered

- (String) PNPDeviceID

- (UInt16) PowerManagementCapabilities[]

- (Boolean) PowerManagementSupported

- (UInt16) ProtocolSupported

- (String) ProviderType

- (Boolean) SettableBaudRate

- (Boolean) SettableDataBits

- (Boolean) SettableFlowControl

- (Boolean) SettableParity

- (Boolean) SettableParityCheck

- (Boolean) SettableRLSD

- (Boolean) SettableStopBits

- (String) Status

- (UInt16) StatusInfo

- (Boolean) Supports16BitMode

- (Boolean) SupportsDTRDSR

- (Boolean) SupportsElapsedTimeouts

- (Boolean) SupportsIntTimeouts

- (Boolean) SupportsParityCheck

- (Boolean) SupportsRLSD

- (Boolean) SupportsRTSCTS

- (Boolean) SupportsSpecialCharacters

- (Boolean) SupportsXOnXOff

- (Boolean) SupportsXOnXOffSet

- (String) SystemName

- (DateTime) TimeOfLastReset



## <a name="server-feature"></a>서버 기능

네임스페이스: root\cimv2

클래스 Win32_ServerFeature


- (UInt32) ID

- (String) Name

- (UInt32) ParentID



## <a name="services"></a>서비스

네임스페이스: root\cimv2

클래스 Win32_Service


- (String) Name

- (Boolean) AcceptPause

- (Boolean) AcceptStop

- (String) Caption

- (UInt32) CheckPoint

- (String) Description

- (Boolean) DesktopInteract

- (String) DisplayName

- (String) ErrorControl

- (UInt32) ExitCode

- (DateTime) InstallDate

- (String) PathName

- (UInt32) ProcessId

- (UInt32) ServiceSpecificExitCode

- (String) ServiceType

- (Boolean) Started

- (String) StartMode

- (String) StartName

- (String) State

- (String) Status

- (String) SystemName

- (UInt32) TagId

- (UInt32) WaitHint



## <a name="shares"></a>공유

네임스페이스: root\cimv2

클래스 Win32_Share


- (String) Name

- (UInt32) AccessMask

- (Boolean) AllowMaximum

- (String) Caption

- (String) Description

- (DateTime) InstallDate

- (UInt32) MaximumAllowed

- (String) Path

- (String) Status

- (UInt32) Type



## <a name="sw-licensing-product"></a>SW 라이선스 제품

네임스페이스: root\cimv2

클래스 SoftwareLicensingProduct


- (String) ID

- (String) ApplicationID

- (String) Description

- (DateTime) EvaluationEndDate

- (UInt32) GracePeriodRemaining

- (UInt32) LicenseStatus

- (String) MachineURL

- (String) Name

- (String) OfflineInstallationId

- (String) PartialProductKey

- (String) ProcessorURL

- (String) ProductKeyID

- (String) ProductKeyURL

- (String) UseLicenseURL



## <a name="sw-licensing-service"></a>SW 라이선스 서비스

네임스페이스: root\cimv2

클래스 SoftwareLicensingService


- (String) Version

- (String) ClientMachineID

- (UInt32) IsKeyManagementServiceMachine

- (UInt32) KeyManagementServiceCurrentCount

- (String) KeyManagementServiceMachine

- (String) KeyManagementServiceProductKeyID

- (UInt32) PolicyCacheRefreshRequired

- (UInt32) RequiredClientCount

- (UInt32) VLActivationInterval

- (UInt32) VLRenewalInterval



## <a name="software-shortcut"></a>소프트웨어 바로 가기

네임스페이스: root\cimv2\sms

클래스 SMS_SoftwareShortcut


- (String) ShortcutKey

- (String) BinFileVersion

- (String) BinProductVersion

- (String) Description

- (String) FilePropertiesHash

- (String) FilePropertiesHashEx

- (UInt32) FileSize

- (String) FileVersion

- (UInt32) Language

- (String) ParentName

- (String) Product

- (String) ProductCode

- (String) ProductVersion

- (String) Publisher

- (String) ShortcutName

- (UInt32) ShortcutType

- (String) TargetExecutable



## <a name="sms_softwaretag"></a>SMS_SoftwareTag

네임스페이스: root\cimv2\sms

클래스 SMS_SoftwareTag


- (String) TagCreatorRegid

- (String) UniqueID

- (String) DisplayVersion

- (Boolean) EntitlementRequired

- (String) ProductName

- (String) SoftwareCreator

- (String) SoftwareCreatorRegid

- (String) SoftwareLicensor

- (String) SoftwareLicensorRegid

- (String) TagCreator

- (SInt32) VersionMajor

- (SInt32) VersionMinor



## <a name="sound-devices"></a>사운드 디바이스

네임스페이스: root\cimv2

클래스 Win32_SoundDevice


- (String) DeviceID

- (UInt16) Availability

- (String) Caption

- (UInt32) ConfigManagerErrorCode

- (Boolean) ConfigManagerUserConfig

- (String) Description

- (UInt16) DMABufferSize

- (Boolean) ErrorCleared

- (String) ErrorDescription

- (DateTime) InstallDate

- (UInt32) LastErrorCode

- (String) Manufacturer

- (UInt32) MPU401Address

- (String) Name

- (String) PNPDeviceID

- (UInt16) PowerManagementCapabilities[]

- (Boolean) PowerManagementSupported

- (String) ProductName

- (String) Status

- (UInt16) StatusInfo

- (String) SystemName



## <a name="system-account"></a>시스템 계정

네임스페이스: root\cimv2

클래스 Win32_SystemAccount


- (String) Domain

- (String) Name

- (String) Caption

- (String) Description

- (DateTime) InstallDate

- (String) SID

- (UInt8) SIDType

- (String) Status



## <a name="system-boot-data"></a>System Boot Data

네임스페이스: root\CCM

클래스 CCM_SystemBootData


- (UInt64) SystemStartTime

- (UInt32) BiosDuration

- (UInt16) BootDiskMediaType

- (UInt32) BootDuration

- (UInt32) EventLogStart

- (UInt32) GPDuration

- (String) OSVersion

- (UInt32) UpdateDuration



## <a name="system-boot-summary"></a>시스템 부팅 요약

네임스페이스: root\CCM

클래스 CCM_SystemBootSummary


- (UInt32) AverageBootFrequency

- (UInt32) LatestBiosDuration

- (UInt32) LatestBootDuration

- (UInt32) LatestCoreBootDuration

- (UInt32) LatestEventLogStart

- (UInt32) LatestGPDuration

- (UInt32) LatestUpdateDuration

- (UInt32) MaxBiosDuration

- (UInt32) MaxBootDuration

- (UInt32) MaxCoreBootDuration

- (UInt32) MaxEventLogStart

- (UInt32) MaxGPDuration

- (UInt32) MaxUpdateDuration

- (UInt32) MedianBiosDuration

- (UInt32) MedianBootDuration

- (UInt32) MedianCoreBootDuration

- (UInt32) MedianEventLogStart

- (UInt32) MedianGPDuration

- (UInt32) MedianUpdateDuration



## <a name="system-console-usage"></a>시스템 콘솔 용도

네임스페이스: root\cimv2\sms

클래스 SMS_SystemConsoleUsage


- (DateTime) SecurityLogStartDate

- (String) TopConsoleUser

- (UInt32) TotalConsoleTime

- (UInt32) TotalConsoleUsers

- (UInt32) TotalSecurityLogTime



## <a name="system-console-user"></a>시스템 콘솔 사용자

네임스페이스: root\cimv2\sms

클래스 SMS_SystemConsoleUser


- (String) SystemConsoleUser

- (DateTime) LastConsoleUse

- (UInt32) NumberOfConsoleLogons

- (UInt32) TotalUserConsoleMinutes



## <a name="system-devices"></a>시스템 디바이스

네임스페이스: root\cimv2\sms

클래스 CCM_SystemDevices


- (String) Name

- (String) CompatibleIDs[]

- (String) DeviceID

- (String) HardwareIDs[]

- (Boolean) IsPnP



## <a name="system-drivers"></a>시스템 드라이버

네임스페이스: root\cimv2

클래스 Win32_SystemDriver


- (String) Name

- (Boolean) AcceptPause

- (Boolean) AcceptStop

- (String) Caption

- (String) Description

- (Boolean) DesktopInteract

- (String) DisplayName

- (String) ErrorControl

- (UInt32) ExitCode

- (DateTime) InstallDate

- (String) PathName

- (UInt32) ServiceSpecificExitCode

- (String) ServiceType

- (Boolean) Started

- (String) StartMode

- (String) StartName

- (String) State

- (String) Status

- (String) SystemName

- (UInt32) TagId



## <a name="system-enclosure"></a>시스템 엔클로저

네임스페이스: root\cimv2

클래스 Win32_SystemEnclosure


- (String) Tag

- (Boolean) AudibleAlarm

- (String) BreachDescription

- (String) CableManagementStrategy

- (String) Caption

- (UInt16) ChassisTypes[]

- (SInt16) CurrentRequiredOrProduced

- (String) Description

- (UInt16) HeatGeneration

- (Boolean) HotSwappable

- (DateTime) InstallDate

- (Boolean) LockPresent

- (String) Manufacturer

- (String) Model

- (String) Name

- (UInt16) NumberOfPowerCords

- (String) OtherIdentifyingInfo

- (String) PartNumber

- (Boolean) PoweredOn

- (Boolean) Removable

- (Boolean) Replaceable

- (UInt16) SecurityBreach

- (UInt16) SecurityStatus

- (String) SerialNumber

- (String) ServiceDescriptions[]

- (UInt16) ServicePhilosophy[]

- (String) SKU

- (String) SMBIOSAssetTag

- (String) Status

- (String) TypeDescriptions[]

- (String) Version

- (Boolean) VisibleAlarm



## <a name="tape-drive"></a>테이프 드라이브

네임스페이스: root\cimv2

클래스 Win32_TapeDrive


- (String) DeviceID

- (UInt16) Availability

- (UInt16) Capabilities[]

- (String) CapabilityDescriptions[]

- (String) Caption

- (UInt32) Compression

- (String) CompressionMethod

- (UInt32) ConfigManagerErrorCode

- (Boolean) ConfigManagerUserConfig

- (UInt64) DefaultBlockSize

- (String) Description

- (UInt32) ECC

- (UInt32) EOTWarningZoneSize

- (Boolean) ErrorCleared

- (String) ErrorDescription

- (String) ErrorMethodology

- (UInt32) FeaturesHigh

- (UInt32) FeaturesLow

- (String) ID

- (DateTime) InstallDate

- (UInt32) LastErrorCode

- (String) Manufacturer

- (UInt64) MaxBlockSize

- (UInt64) MaxMediaSize

- (UInt32) MaxPartitionCount

- (String) MediaType

- (UInt64) MinBlockSize

- (String) Name

- (Boolean) NeedsCleaning

- (UInt32) NumberOfMediaSupported

- (UInt32) Padding

- (String) PNPDeviceID

- (UInt16) PowerManagementCapabilities[]

- (Boolean) PowerManagementSupported

- (UInt32) ReportSetMarks

- (String) Status

- (UInt16) StatusInfo

- (String) SystemName



## <a name="time-zone"></a>표준 시간대

네임스페이스: root\cimv2

클래스 Win32_TimeZone


- (String) StandardName

- (SInt32) Bias

- (String) Caption

- (SInt32) DaylightBias

- (UInt32) DaylightDay

- (UInt8) DaylightDayOfWeek

- (UInt32) DaylightHour

- (UInt32) DaylightMillisecond

- (UInt32) DaylightMinute

- (UInt32) DaylightMonth

- (String) DaylightName

- (UInt32) DaylightSecond

- (UInt32) DaylightYear

- (String) Description

- (String) SettingID

- (UInt32) StandardBias

- (UInt32) StandardDay

- (UInt8) StandardDayOfWeek

- (UInt32) StandardHour

- (UInt32) StandardMillisecond

- (UInt32) StandardMinute

- (UInt32) StandardMonth

- (UInt32) StandardSecond

- (UInt32) StandardYear



## <a name="tpm"></a>TPM

네임스페이스: root\CIMv2\Security\MicrosoftTpm

클래스 Win32_Tpm


- (Boolean) IsActivated_InitialValue

- (Boolean) IsEnabled_InitialValue

- (Boolean) IsOwned_InitialValue

- (UInt32) ManufacturerId

- (String) ManufacturerVersion

- (String) ManufacturerVersionInfo

- (String) PhysicalPresenceVersionInfo

- (String) SpecVersion



## <a name="tpm-status"></a>TPM 상태

네임스페이스: root\cimv2\sms

클래스 SMS_TPM


- (Boolean) IsReady

- (UInt32) Information

- (Boolean) IsApplicable



## <a name="ts-issued-license"></a>TS 발급 라이선스

네임스페이스: root\cimv2

클래스 Win32_TSIssuedLicense


- (UInt32) LicenseId

- (DateTime) ExpirationDate

- (DateTime) IssueDate

- (UInt32) KeyPackId

- (UInt32) LicenseStatus

- (String) sHardwareId

- (String) sIssuedToComputer

- (String) sIssuedToUser



## <a name="ts-license-key-pack"></a>TS 라이선스 키 팩

네임스페이스: root\cimv2

클래스 Win32_TSLicenseKeyPack


- (UInt32) KeyPackId

- (UInt32) AvailableLicenses

- (String) Description

- (UInt32) IssuedLicenses

- (UInt32) KeyPackType

- (UInt32) ProductType

- (String) ProductVersion

- (UInt32) TotalLicenses



## <a name="uninterruptible-power-supply"></a>무정전 전원 공급 장치

네임스페이스: root\cimv2

클래스 Win32_UninterruptiblePowerSupply


- (String) DeviceID

- (UInt16) ActiveInputVoltage

- (UInt16) Availability

- (Boolean) BatteryInstalled

- (Boolean) CanTurnOffRemotely

- (String) Caption

- (String) CommandFile

- (UInt32) ConfigManagerErrorCode

- (Boolean) ConfigManagerUserConfig

- (String) Description

- (Boolean) ErrorCleared

- (String) ErrorDescription

- (UInt16) EstimatedChargeRemaining

- (UInt32) EstimatedRunTime

- (UInt32) FirstMessageDelay

- (DateTime) InstallDate

- (Boolean) IsSwitchingSupply

- (UInt32) LastErrorCode

- (Boolean) LowBatterySignal

- (UInt32) MessageInterval

- (String) Name

- (String) PNPDeviceID

- (Boolean) PowerFailSignal

- (UInt16) PowerManagementCapabilities[]

- (Boolean) PowerManagementSupported

- (UInt32) Range1InputFrequencyHigh

- (UInt32) Range1InputFrequencyLow

- (UInt32) Range1InputVoltageHigh

- (UInt32) Range1InputVoltageLow

- (UInt32) Range2InputFrequencyHigh

- (UInt32) Range2InputFrequencyLow

- (UInt32) Range2InputVoltageHigh

- (UInt32) Range2InputVoltageLow

- (UInt16) RemainingCapacityStatus

- (String) Status

- (UInt16) StatusInfo

- (String) SystemName

- (UInt32) TimeOnBackup

- (UInt32) TotalOutputPower

- (UInt16) TypeOfRangeSwitching

- (String) UPSPort



## <a name="usb-controller"></a>USB 컨트롤러

네임스페이스: root\cimv2

클래스 Win32_USBController


- (String) DeviceID

- (UInt16) Availability

- (String) Caption

- (UInt32) ConfigManagerErrorCode

- (Boolean) ConfigManagerUserConfig

- (String) Description

- (Boolean) ErrorCleared

- (String) ErrorDescription

- (DateTime) InstallDate

- (UInt32) LastErrorCode

- (String) Manufacturer

- (UInt32) MaxNumberControlled

- (String) Name

- (String) PNPDeviceID

- (UInt16) PowerManagementCapabilities[]

- (Boolean) PowerManagementSupported

- (UInt16) ProtocolSupported

- (String) Status

- (UInt16) StatusInfo

- (String) SystemName

- (DateTime) TimeOfLastReset



## <a name="usb-device"></a>USB 디바이스

네임스페이스: root\cimv2

클래스 Win32_USBDevice


- (String) DeviceID

- (String) Caption

- (String) ClassGuid

- (UInt32) ConfigManagerErrorCode

- (Boolean) ConfigManagerUserConfig

- (String) CreationClassName

- (String) Description

- (String) Manufacturer

- (String) Name

- (String) PNPDeviceID

- (String) Service

- (String) Status

- (String) SystemCreationClassName

- (String) SystemName



## <a name="usm-user-profile"></a>USM 사용자 프로필

네임스페이스: root\cimv2

클래스 Win32_UserProfile


- (String) SID

- (UInt8) HealthStatus

- (String) LastAttemptedProfileDownloadTime

- (String) LastAttemptedProfileUploadTime

- (String) LastBackgroundRegistryUploadTime

- (DateTime) LastDownloadTime

- (DateTime) LastUploadTime

- (DateTime) LastUseTime

- (Boolean) Loaded

- (String) LocalPath

- (UInt32) RefCount

- (Boolean) RoamingConfigured

- (String) RoamingPath

- (Boolean) RoamingPreference

- (Boolean) Special

- (UInt32) Status



## <a name="video-controller"></a>비디오 컨트롤러

네임스페이스: root\cimv2

클래스 Win32_VideoController


- (String) DeviceID

- (UInt16) AcceleratorCapabilities[]

- (String) AdapterCompatibility

- (String) AdapterDACType

- (UInt32) AdapterRAM

- (UInt16) Availability

- (String) CapabilityDescriptions[]

- (String) Caption

- (UInt32) ColorTableEntries

- (UInt32) ConfigManagerErrorCode

- (Boolean) ConfigManagerUserConfig

- (UInt32) CurrentBitsPerPixel

- (UInt32) CurrentHorizontalResolution

- (UInt64) CurrentNumberOfColors

- (UInt32) CurrentNumberOfColumns

- (UInt32) CurrentNumberOfRows

- (UInt32) CurrentRefreshRate

- (UInt16) CurrentScanMode

- (UInt32) CurrentVerticalResolution

- (String) Description

- (UInt32) DeviceSpecificPens

- (UInt32) DitherType

- (DateTime) DriverDate

- (String) DriverVersion

- (Boolean) ErrorCleared

- (String) ErrorDescription

- (UInt32) ICMIntent

- (UInt32) ICMMethod

- (String) InfFilename

- (String) InfSection

- (DateTime) InstallDate

- (String) InstalledDisplayDrivers

- (UInt32) LastErrorCode

- (UInt32) MaxMemorySupported

- (UInt32) MaxNumberControlled

- (UInt32) MaxRefreshRate

- (UInt32) MinRefreshRate

- (Boolean) Monochrome

- (String) Name

- (UInt16) NumberOfColorPlanes

- (UInt32) NumberOfVideoPages

- (String) PNPDeviceID

- (UInt16) PowerManagementCapabilities[]

- (Boolean) PowerManagementSupported

- (UInt16) ProtocolSupported

- (UInt32) ReservedSystemPaletteEntries

- (UInt32) SpecificationVersion

- (String) Status

- (UInt16) StatusInfo

- (String) SystemName

- (UInt32) SystemPaletteEntries

- (DateTime) TimeOfLastReset

- (UInt16) VideoArchitecture

- (UInt16) VideoMemoryType

- (UInt16) VideoMode

- (String) VideoModeDescription

- (String) VideoProcessor



## <a name="virtual-application-packages"></a>가상 애플리케이션 패키지

네임스페이스: root\Microsoft\appvirt\client

클래스 Package


- (String) PackageGUID

- (UInt64) CachedLaunchSize

- (UInt16) CachedPercentage

- (UInt64) CachedSize

- (UInt64) LaunchSize

- (String) Name

- (String) SftPath

- (UInt64) TotalSize

- (String) Version

- (String) VersionGUID



## <a name="virtual-applications"></a>가상 애플리케이션

네임스페이스: root\Microsoft\appvirt\client

클래스 Application


- (String) Name

- (String) Version

- (String) CachedOsdPath

- (UInt32) GlobalRunningCount

- (DateTime) LastLaunchOnSystem

- (Boolean) Loading

- (String) OriginalOsdPath

- (String) PackageGUID



## <a name="virtual-machine-64"></a>가상 머신(64)

네임스페이스: root\cimv2

클래스 Win32Reg_SMSGuestVirtualMachine64


- (String) InstanceKey

- (String) PhysicalHostName

- (String) PhysicalHostNameFullyQualified



## <a name="virtual-machine"></a>가상 컴퓨터

네임스페이스: root\cimv2

클래스 Win32Reg_SMSGuestVirtualMachine


- (String) InstanceKey

- (String) PhysicalHostName

- (String) PhysicalHostNameFullyQualified



## <a name="virtual-machine-details"></a>가상 머신 정보

네임스페이스: root\vm\VirtualServer

클래스 VirtualMachine


- (String) Name

- (UInt32) CpuUtilization

- (UInt64) DiskBytesRead

- (UInt64) DiskBytesWritten

- (UInt64) DiskSpaceUsed

- (UInt64) HeartbeatCount

- (UInt32) HeartbeatInterval

- (UInt32) HeartbeatPercentage

- (UInt32) HeartbeatRate

- (UInt64) NetworkBytesReceived

- (UInt64) NetworkBytesSent

- (UInt64) PhysicalMemoryAllocated

- (UInt32) Uptime



## <a name="volume"></a>볼륨

네임스페이스: root\cimv2

클래스 Win32_Volume


- (String) DeviceID

- (UInt16) Access

- (Boolean) Automount

- (UInt16) Availability

- (UInt64) BlockSize

- (UInt64) Capacity

- (String) Caption

- (Boolean) Compressed

- (UInt32) ConfigManagerErrorCode

- (Boolean) ConfigManagerUserConfig

- (String) CreationClassName

- (String) Description

- (Boolean) DirtyBitSet

- (String) DriveLetter

- (UInt32) DriveType

- (Boolean) ErrorCleared

- (String) ErrorDescription

- (String) ErrorMethodology

- (String) FileSystem

- (UInt64) FreeSpace

- (Boolean) IndexingEnabled

- (DateTime) InstallDate

- (String) Label

- (UInt32) LastErrorCode

- (UInt32) MaximumFileNameLength

- (String) Name

- (UInt64) NumberOfBlocks

- (String) PNPDeviceID

- (UInt16) PowerManagementCapabilities[]

- (Boolean) PowerManagementSupported

- (String) Purpose

- (Boolean) QuotasEnabled

- (Boolean) QuotasIncomplete

- (Boolean) QuotasRebuilding

- (UInt32) SerialNumber

- (String) Status

- (UInt16) StatusInfo

- (Boolean) SupportsDiskQuotas

- (Boolean) SupportsFileBasedCompression

- (String) SystemCreationClassName

- (String) SystemName



## <a name="ccm_webappinstallinfo"></a>CCM_WebAppInstallInfo

네임스페이스: root\ccm\cimodels

클래스 CCM_WebAppInstallInfo


- (String) AppDeliveryTypeId

- (UInt32) AppDtRevision

- (String) TargetURL

- (String) UserSID

- (String) URLFileName

- (String) URLPath



## <a name="sms_windows8application"></a>SMS_Windows8Application

네임스페이스: root\cimv2\sms

클래스 SMS_Windows8Application


- (String) FullName

- (String) ApplicationName

- (String) Architecture

- (Boolean) ConfigMgrManaged

- (String) DependencyApplicationNames

- (String) FamilyName

- (String) InstalledLocation

- (Boolean) IsFramework

- (String) Publisher

- (String) PublisherId

- (String) Version



## <a name="sms_windows8applicationuserinfo"></a>SMS_Windows8ApplicationUserInfo

네임스페이스: root\cimv2\sms

클래스 SMS_Windows8ApplicationUserInfo


- (String) FullName

- (String) UserSecurityId

- (String) InstallState

- (String) UserAccountName



## <a name="windows-update"></a>Windows Update

네임스페이스: root\cimv2

클래스 Win32Reg_SMSWindowsUpdate


- (String) InstanceKey

- (UInt32) AUOptions

- (UInt32) NoAutoUpdate

- (UInt32) UseWUServer



## <a name="windows-update-agent-version"></a>Windows Update 에이전트 버전

네임스페이스: root\cimv2\sms

클래스 Win32_WindowsUpdateAgentVersion


- (String) Version



## <a name="write-filter-state"></a>쓰기 필터 상태

네임스페이스: root\cimv2\sms

클래스 CCM_WriteFilterState


- (Boolean) WriteFilterEnabled
