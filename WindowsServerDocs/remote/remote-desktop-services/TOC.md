# [원격 데스크톱 서비스](welcome-to-rds.md)
## [시작](rds-get-started.md)
### [RDS의 새로운 기능](rds-whats-new.md)
### [지원되는 RDS 구성](rds-supported-config.md)
### [Windows 10 VDI에 대해 지원되는 보안 구성](rds-vdi-supported-config.md)
### [원격 데스크톱 서비스의 포스터 계획](rds-poster.md)
### [원격 데스크톱 서비스 호스팅 파트너](rds-hosting-partners.md)
## [계획 및 디자인](rds-plan-and-design.md)
### [어디에서나 빌드](rds-plan-build-anywhere.md)
### [다양한 종류의 사용자에게 제공](rds-plan-cater-to-users.md)
### [어디에서나 액세스](rds-plan-access-from-anywhere.md)
### [고가용성](rds-plan-high-availability.md)
### [Multi-Factor Authentication](rds-plan-mfa.md)
### [데이터 저장소 보안 적용](rds-plan-secure-data-storage.md)
### [그래픽 렌더링 기술 선택](rds-graphics-virtualization.md)
### [모든 디바이스에서 연결](rds-plan-connect-from-any-device.md)
### [지불 방법 선택](rds-plan-choose-how-you-pay.md)
### [RDS 및 VDI 배포에서의 Office 2016](https://docs.microsoft.com/deployoffice/rds-office-vdi-rdsh)
#### [비영구 환경에서 Outlook 검색 처리](https://docs.microsoft.com/deployoffice/rds-outlook-search)
#### [비즈니스 및 VDI 환경용 OneDrive](https://docs.microsoft.com/deployoffice/rds-onedrive-business-vdi)
### [데스크톱 호스팅 참조 아키텍처](Desktop-Hosting-Reference-Architecture.md)
#### [원격 데스크톱 서비스 아키텍처](Desktop-hosting-logical-architecture.md)
#### [데스크톱 호스팅 서비스](Desktop-hosting-service.md)
#### [원격 데스크톱 서비스 역할](rds-roles.md)
#### [데스크톱 호스팅을 위한 Azure 서비스 및 고려 사항](Azure-services-and-considerations-for-desktop-hosting.md)
## [빌드 및 배포](rds-build-and-deploy.md)
### [ARM 및 Azure Marketplace로 개념 증명 RDS 환경 배포](rds-in-azure.md)
### [원격 데스크톱 서비스 배포를 Windows Server 2016으로 마이그레이션](migrate-rds-role-services.md)
### [RDS CAL(원격 데스크톱 서비스 클라이언트 액세스 라이선스) 마이그레이션](migrate-rds-cals.md)
### [원격 데스크톱 서비스 배포를 Windows Server 2016으로 업그레이드](upgrade-to-rds.md)
#### [원격 데스크톱 세션 호스트 서버 업그레이드](upgrade-to-rdsh.md)
#### [원격 데스크톱 가상화 호스트 서버 업그레이드](upgrade-to-rdvh.md)
### [원격 데스크톱 서비스 인프라 배포](rds-deploy-infrastructure.md)
### [원격 데스크톱 서비스 컬렉션 생성 및 배포](rds-create-collection.md)
### [사용자에 대한 원격 데스크톱 웹 클라이언트 설정](clients/remote-desktop-web-client-admin.md)
### [사용자에 대한 전자 메일 검색 설정](rds-email-discovery.md)
### [원격 데스크톱 배포 라이선스](rds-client-access-license.md)
#### [라이선스 서버 활성화](rds-activate-license-server.md)
#### [라이선스 서버에 RDS CAL 설치](rds-install-cals.md)
#### [배포에 사용된 CAL 추적](rds-track-cals.md)
### [Azure 서비스 통합](rds-integrate-with-azure.md)
#### [RDS를 사용한 다단계 인증 사용 방법 알아보기](/azure/multi-factor-authentication/nps-extension-remote-desktop-gateway)
#### [RDS 배포에 Azure AD Domain Services 통합](rds-azure-adds.md)
#### [Azure AD 응용 프로그램 프록시로 원격 데스크톱 게시](/azure/active-directory/application-proxy-publish-remote-desktop)
### 고가용성을 위해 RDS 환경 확장
#### [RD 세션 호스트 팜을 사용하여 기존 RDS 컬렉션 확장](rds-scale-rdsh-farm.md)
#### [RD 연결 브로커 인프라에 고가용성 추가](rds-connection-broker-cluster.md)
#### [RD 웹 및 RD 게이트웨이 웹 프런트에 고가용성 추가](rds-rdweb-gateway-ha.md)
#### [UPD 저장소용 2-노드 저장소 공간 다이렉트 파일 시스템 배포](rds-storage-spaces-direct-deployment.md)
#### [개인 세션 데스크톱 환경 배포 및 관리](rds-personal-session-desktops.md)
#### [RDS용 VM 만들기](rds-prepare-vms.md)
### [RDS 환경에 대한 재해 복구 설정](rds-disaster-recovery.md)
#### [지리적 중복 RDS 배포 만들기](rds-multi-datacenter-deployment.md)
#### [RDS에 대한 Azure Site Recovery 설정](rds-disaster-recovery-with-azure.md)
##### [RDS 구성 요소에 대한 재해 복구 활성화](rds-enable-dr-with-asr.md)
##### [재해 복구 계획 만들기](rds-disaster-recovery-plan.md)

## [실행 및 조정](rds-run-and-tune.md)
### [원격 데스크톱 서비스에 사용할 RemoteFX vGPU 설치 및 구성](rds-remotefx-vgpu.md)
### [개인 데스크톱 세션 컬렉션 관리](rds-manage-personal-collection.md)
### [VDI 데스크톱에 대한 권장 구성](rds-vdi-recommendations.md)
### [Windows 10, 버전 1803, VDI(가상 데스크톱 인프라) 역할에 대한 최적화](rds-vdi-recommendations-1803.md)
### [RDS 컬렉션에서 사용자 관리](rds-user-management.md)
### [Windows Server에서 PowerShell을 사용한 RDS 타이틀 "작업 리소스" 사용자 지정](rds-work-resources.md)
### [성능 카운터를 사용한 앱 성능 문제 진단](rds-rdsh-performance-counters.md)

## [추가 원격 데스크톱 지원](rds-get-support.md)
## [원격 데스크톱 클라이언트](clients/remote-desktop-clients.md)
### 일반 정보
#### [어떤 클라이언트가 가장 적합한가요?](clients/remote-desktop-app-compare.md)
#### [원격 데스크톱 URI 체계](clients/remote-desktop-uri.md)
#### [원격 데스크톱 클라이언트 FAQ](clients/remote-desktop-client-faq.md)
#### [관리되는 앱 및 데스크톱에 대한 개인 정보 설정](clients/remote-privacy-settings.md)
#### [원격 데스크톱 연결 문제 해결](clients/troubleshoot-remote-desktop-connections.md)
### Windows용 원격 데스크톱 클라이언트
#### [시작하기](clients/windows.md)
#### [Windows 클라이언트의 새로운 기능](clients/windows-whatsnew.md)
### Android용 원격 데스크톱 클라이언트
#### [시작하기](clients/remote-desktop-android.md)
#### [Android 클라이언트의 새로운 기능](clients/android-whatsnew.md)
### iOS용 원격 데스크톱 클라이언트
#### [시작하기](clients/remote-desktop-ios.md)
#### [iOS 클라이언트의 새로운 기능](clients/ios-whatsnew.md)
### Mac용 원격 데스크톱 클라이언트
#### [시작하기](clients/remote-desktop-mac.md)
#### [MacOS 클라이언트의 새로운 기능](clients/mac-whatsnew.md)
### 원격 데스크톱 웹 클라이언트
#### [원격 데스크톱 웹 클라이언트에 액세스](clients/remote-desktop-web-client.md)
#### [웹 클라이언트의 새로운 기능](clients/web-client-whatsnew.md)
### 원격 데스크톱용 PC 설정
#### [지원되는 PC](clients/remote-desktop-supported-config.md)
#### [PC에 원격 데스크톱 액세스 권한 부여](clients/remote-desktop-allow-access.md)
#### [네트워크 외부로부터 PC에 대한 액세스 권한 부여](clients/remote-desktop-allow-outside-access.md)
#### [PC에서 RD 수신 대기 포트 변경](clients/change-listening-port.md)