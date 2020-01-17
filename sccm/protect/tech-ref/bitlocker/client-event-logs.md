---
title: 클라이언트 이벤트 로그
titleSuffix: Configuration Manager
description: Windows 이벤트 로그에서 가능한 BitLocker (MBAM) 클라이언트 항목에 대 한 기술 참조
ms.date: 11/29/2019
ms.prod: configuration-manager
ms.technology: configmgr-protect
ms.topic: conceptual
ms.assetid: c38b6963-cb1f-40ed-a888-e19d401ec3fc
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 228d96ad71b81d4e544e1f8906dbcf6bb032858b
ms.sourcegitcommit: 148745e1c3d9817d8beea20684a54436210959c6
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75819032"
---
# <a name="client-event-logs"></a>클라이언트 이벤트 로그

*적용 대상: Configuration Manager(현재 분기)*

<!--3601034-->

BitLocker 관리 정책을 배포할 Configuration Manager 클라이언트에서 Windows 이벤트 뷰어를 사용 하 여 BitLocker 클라이언트 이벤트 로그를 확인 합니다. [관리](#admin) 및 [운영](#operational) 이벤트 로그에 대 한 **응용 프로그램 및 서비스 로그**, **Microsoft**, **Windows**, **mbam** 으로 이동 합니다.

## <a name="admin"></a>관리자

### <a name="2-volumeenactmentfailed"></a>2: VolumeEnactmentFailed

MBAM 정책을 적용하는 중 오류가 발생했습니다.

#### <a name="error-code--2144272219"></a>오류 코드: -2144272219

세부 정보: BitLocker 드라이브 암호화는 씬 프로비저닝된 저장소 에서만 사용 된 공간만 암호화를 지원 합니다.

이 오류는 BitLocker를 사용 하 여 Windows 10 버전 1803 이전 버전을 실행 하는 가상 컴퓨터를 암호화 하려고 할 때 발생 합니다. 이전 버전의 Windows 10에서는 전체 디스크 암호화를 지원 하지 않습니다. BitLocker 관리 정책은 전체 디스크 암호화를 적용 합니다.

#### <a name="error-code--2147024774"></a>오류 코드: -2147024774

세부 정보: 시스템 호출에 전달 된 데이터 영역이 너무 작습니다.

이 문제를 해결하려면 컴퓨터를 다시 시작하세요.

### <a name="4-transferstatusdatafailed"></a>4: TransferStatusDataFailed

암호화 상태 데이터를 전송하는 중 오류가 발생했습니다.

### <a name="8-systemvolumenotfound"></a>8: SystemVolumeNotFound

시스템 볼륨이 누락되었습니다. SystemVolume은 운영 체제 드라이브를 암호화하는 데 필요합니다.

### <a name="9-tpmnotfound"></a>9: TPMNotFound

TPM 하드웨어가 누락되었습니다. TPM은 TPM 보호기로 운영 체제 드라이브를 암호화하는 데 필요합니다.

### <a name="10-machinehwexempted"></a>10: MachineHWExempted

컴퓨터가 암호화에서 제외됩니다. 컴퓨터의 하드웨어 상태: 제외

### <a name="11-machinehwunknown"></a>11: MachineHWUnknown

컴퓨터가 암호화에서 제외됩니다. 컴퓨터의 하드웨어 상태: 알 수 없음

### <a name="12-hwcheckfailed"></a>12: HWCheckFailed

하드웨어 예외 검사를 하지 못했습니다.

### <a name="13-userisexempted"></a>13: UserIsExempted

사용자가 암호화에서 제외됩니다.

### <a name="14-useriswaiting"></a>14: UserIsWaiting

사용자가 예외를 요청했습니다.

### <a name="15-userexemptioncheckfailed"></a>15: UserExemptionCheckFailed

사용자 예외 검사를 하지 못했습니다.

### <a name="16-userpostponed"></a>16: UserPostponed

사용자가 암호화 프로세스를 연기했습니다.

### <a name="17-tpminitializationfailed"></a>17: TPMInitializationFailed

TPM 초기화를 하지 못했습니다. 사용자가 BIOS 변경 사항을 거부했습니다.

### <a name="18-coreservicedown"></a>18: CoreServiceDown

MBAM 복구 및 하드웨어 서비스에 연결할 수 없습니다.

#### <a name="error-code--2147024809"></a>오류 코드: -2147024809

세부 정보: 매개 변수가 잘못되었습니다.

이 오류는 웹 사이트가 HTTPS가 아니거나 클라이언트에 PKI 인증서가 없는 경우에 발생 합니다.

### <a name="20-policymismatch"></a>20: PolicyMismatch

BitLocker 관리 정책이 충돌 하거나 손상 되었습니다.

### <a name="21-conflictingosvolumepolicies"></a>21: ConflictingOSVolumePolicies

검색된 OS 볼륨 암호화 정책이 충돌합니다. OS 드라이브 보호기와 관련된 BitLocker 정책을 확인하세요.

### <a name="22-conflictingfddvolumepolicies"></a>22: ConflictingFDDVolumePolicies

검색된 고정 데이터 드라이브 볼륨 암호화 정책이 충돌합니다. 고정 데이터 드라이브 드라이브 보호기와 관련 된 BitLocker 정책을 확인 하십시오.

### <a name="27-encryptionfailednodra"></a>27: EncryptionFailedNoDra

암호화 중 오류가 발생했습니다. Windows 8.1 이전 머신의 경우 FIPS 모드에서는 DRA(데이터 복구 에이전트) 보호기가 필요합니다.

### <a name="34-tpmlockoutresetfailed"></a>34: TpmLockOutResetFailed

TPM 잠금을 다시 설정 하지 못했습니다.

### <a name="36-tpmownerauthretrievalfailed"></a>36: TpmOwnerAuthRetrievalFailed

MBAM 서비스에서 TPM 소유자 인증을 검색 하지 못했습니다.

### <a name="37-wmiproviderdllsearchpathupdatefailed"></a>37: WmiProviderDllSearchPathUpdateFailed

WMI 공급자에 대 한 DLL 검색 경로를 업데이트 하지 못했습니다.

### <a name="38-timedoutwaitingforwmiprovider"></a>38: TimedOutWaitingForWmiProvider

에이전트를 중지 합니다. MBAM WMI 공급자 인스턴스를 기다리는 동안 시간이 초과 되었습니다.

## <a name="operational"></a>운영

### <a name="1-volumeenactmentsuccessful"></a>1: VolumeEnactmentSuccessful

BitLocker 관리 정책을 적용 했습니다.

### <a name="3-transferstatusdatasuccessful"></a>3: TransferStatusDataSuccessful

암호화 상태 데이터가 전송되었습니다.

### <a name="19-coreserviceup"></a>19: CoreServiceUp

MBAM 복구 및 하드웨어 서비스에 연결되었습니다.

### <a name="28-tpmownerauthescrowed"></a>28: TpmOwnerAuthEscrowed

TPM OwnerAuth가 위탁되었습니다.

### <a name="29-recoverykeyescrowed"></a>29: RecoveryKeyEscrowed

볼륨의 BitLocker 복구 키가 에스크로되었습니다.

### <a name="30-recoverykeyreset"></a>30: RecoveryKeyReset

볼륨의 BitLocker 복구 키가 업데이트되었습니다.

### <a name="31-enforcepolicydateset"></a>31: EnforcePolicyDateSet

볼륨의 정책 적용 날짜...가 설정되었습니다.

### <a name="32-enforcepolicydatecleared"></a>32: EnforcePolicyDateCleared

볼륨의 정책 적용 날짜...가 지워졌습니다.

### <a name="33-tpmlockoutresetsucceeded"></a>33: TpmLockOutResetSucceeded

TPM 잠금을 다시 설정 했습니다.

### <a name="35-tpmownerauthretrievalsucceeded"></a>35: TpmOwnerAuthRetrievalSucceeded

MBAM 서비스에서 TPM 소유자 인증을 검색 했습니다.

### <a name="39-removabledrivemounted"></a>39: RemovableDriveMounted

이동식 드라이브가 탑재 되었습니다.

### <a name="40-removabledrivedismounted"></a>40: Removable드라이브 분리 됨

이동식 드라이브가 분리 되었습니다.

### <a name="41-failedtoenactendpointunreachable"></a>41: FailedToEnactEndpointUnreachable 수 없음

MBAM 복구 및 하드웨어 서비스에 연결 하지 못하여 BitLocker 관리 정책이 볼륨에 성공적으로 적용 되지 못했습니다.

### <a name="42-failedtoenactlockedvolume"></a>42: FailedToEnactLockedVolume

잠긴 볼륨 상태에서 BitLocker 관리 정책을 볼륨에 성공적으로 적용 하지 못했습니다.

### <a name="43-transferstatusdatafailedendpointunreachable"></a>43: 전송자 Statusdatafailedendpoint도달할 수 없음

MBAM 준수 및 상태 서비스에 연결 하지 못하여 암호화 상태 데이터가 전송 되지 않았습니다.

## <a name="see-also"></a>참고 항목

이러한 로그를 사용 하는 방법에 대 한 자세한 내용은 [BitLocker 이벤트 로그](/configmgr/protect/tech-ref/bitlocker/about-event-logs)를 참조 하세요.

문제 해결에 대 한 자세한 내용은 [BitLocker 문제 해결](/configmgr/protect/tech-ref/bitlocker/troubleshoot)을 참조 하세요.
