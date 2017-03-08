# 이해 및 탐색
## [운영 체제 배포 소개](understand/introduction-to-operating-system-deployment.md)
## [작업 순서 단계](understand/task-sequence-steps.md)
## [작업 순서 동작 변수](understand/task-sequence-action-variables.md)
## [작업 순서 기본 제공 변수](understand/task-sequence-built-in-variables.md)
## [작업 순서 미디어에 대한 시작 전 명령](understand/prestart-commands-for-task-sequence-media.md)

# 계획 및 디자인
## [운영 체제 배포를 위한 인프라 요구 사항](plan-design/infrastructure-requirements-for-operating-system-deployment.md)
## [작업 자동화에 대한 계획 고려 사항](plan-design/planning-considerations-for-automating-tasks.md)
## [운영 체제 배포의 보안 및 개인 정보](plan-design/security-and-privacy-for-operating-system-deployment.md)
## [운영 체제 배포 상호 운용성 계획](plan-design/planning-for-operating-system-deployment-interoperability.md)

# 시작
## [운영 체제 배포를 위한 사이트 시스템 역할 준비](get-started/prepare-site-system-roles-for-operating-system-deployments.md)
## [운영 체제 배포 준비](get-started/prepare-for-operating-system-deployment.md)
### [부팅 이미지 관리](get-started/manage-boot-images.md)
#### [부팅 이미지 사용자 지정](get-started/customize-boot-images.md)

### [운영 체제 이미지 관리](get-started/manage-operating-system-images.md)
#### [운영 체제 이미지 사용자 지정](get-started/customize-operating-system-images.md)

### [운영 체제 업그레이드 패키지 관리](get-started/manage-operating-system-upgrade-packages.md)
### [드라이버 관리](get-started/manage-drivers.md)
### [사용자 상태 관리](get-started/manage-user-state.md)
### [알 수 없는 컴퓨터 배포 준비](get-started/prepare-for-unknown-computer-deployments.md)
### [사용자를 대상 컴퓨터에 연결](get-started/associate-users-with-a-destination-computer.md)

## [WAN 트래픽을 줄이기 위해 Windows PE 피어 캐시 준비](get-started/prepare-windows-pe-peer-cache-to-reduce-wan-traffic.md)

# 배포 및 사용
## [엔터프라이즈 운영 체제를 배포하는 시나리오](deploy-use/scenarios-to-deploy-enterprise-operating-systems.md)
### [최신 버전으로 Windows 업그레이드](deploy-use/upgrade-windows-to-the-latest-version.md)
### [새 버전의 Windows로 기존 컴퓨터 새로 고침](deploy-use/refresh-an-existing-computer-with-a-new-version-of-windows.md)
### [새 컴퓨터에 새 버전의 Windows 설치(완전 복구)](deploy-use/install-new-windows-version-new-computer-bare-metal.md)
### [기존 컴퓨터 바꾸기 및 설정 전송](deploy-use/replace-an-existing-computer-and-transfer-settings.md)

## [엔터프라이즈 운영 체제를 배포하는 방법](deploy-use/methods-to-deploy-enterprise-operating-systems.md)
### [PXE를 사용하여 네트워크를 통해 Windows 배포](deploy-use/use-pxe-to-deploy-windows-over-the-network.md)
### [소프트웨어 센터를 사용하여 네트워크를 통해 Windows 배포](deploy-use/use-software-center-to-deploy-windows-over-the-network.md)
### [부팅 가능한 미디어를 사용하여 네트워크를 통해 Windows 배포](deploy-use/use-bootable-media-to-deploy-windows-over-the-network.md)
### [독립 실행형 미디어를 사용하여 네트워크를 사용하지 않고 Windows 배포](deploy-use/use-stand-alone-media-to-deploy-windows-without-using-the-network.md)
### [멀티캐스트를 사용하여 네트워크를 통해 Windows 배포](deploy-use/use-multicast-to-deploy-windows-over-the-network.md)
### [팩터리 또는 로컬 저장소에 OEM에 대한 이미지 만들기](deploy-use/create-an-image-for-an-oem-in-factory-or-a-local-depot.md)
### [Windows to Go 배포](deploy-use/deploy-windows-to-go.md)

## [Windows as a Service 관리](deploy-use/manage-windows-as-a-service.md)
## [운영 체제 배포 모니터링](deploy-use/monitor-operating-system-deployments.md)

## [작업을 자동화하는 작업 순서 관리](deploy-use/manage-task-sequences-to-automate-tasks.md)
### [운영 체제를 설치하는 작업 순서 만들기](deploy-use/create-a-task-sequence-to-install-an-operating-system.md)
### [운영 체제를 업그레이드하는 작업 순서 만들기](deploy-use/create-a-task-sequence-to-upgrade-an-operating-system.md)
### [운영 체제를 캡처하는 작업 순서 만들기](deploy-use/create-a-task-sequence-to-capture-an-operating-system.md)
### [사용자 상태를 캡처 및 복원하는 작업 순서 만들기](deploy-use/create-a-task-sequence-to-capture-and-restore-user-state.md)
### [작업 순서를 사용하여 가상 하드 디스크 관리](deploy-use/use-a-task-sequence-to-manage-virtual-hard-disks.md)

## [사용자 지정 작업 순서 시나리오](deploy-use/custom-task-sequence-scenarios.md)
### [사용자 지정 작업 순서 만들기](deploy-use/create-a-custom-task-sequence.md)
### [비운영 체제 배포에 대한 작업 순서 만들기](deploy-use/create-a-task-sequence-for-non-operating-system-deployments.md)
### [BIOS-UEFI 변환을 관리하는 작업 순서 단계](deploy-use/task-sequence-steps-to-manage-bios-to-uefi-conversion.md)

## [작업 순서 미디어 만들기](deploy-use/create-task-sequence-media.md)
### [독립 실행형 미디어 만들기](deploy-use/create-stand-alone-media.md)
### [사전 준비된 미디어 만들기](deploy-use/create-prestaged-media.md)
### [부팅 가능한 미디어 만들기](deploy-use/create-bootable-media.md)
### [미디어 캡처 만들기](deploy-use/create-capture-media.md)
