
## docker 설치 및 기본 설정

### 시스템 업그레이드 및 업데이트

> $ [[Linux command#sudo|sudo]] [[Linux command#apt|apt]]-get [[Linux command#update|update]] && sudo [[Linux command#apt-get|apt-get]] [[Linux command#upgrade|upgrade]]

### 필요 패키지 설치

> $ sudo apt-get [[Linux command#install|install]] [[Linux command#apt-transport-https|apt-transport-https]] [[Linux command#ca-certificates|ca-certificates]] [[Linux command#curl|curl]] [[Linux command#gnupg-agent|gnupg-agent]] [[Linux command#software-properties-common|software-properties-common]]
- HTTPS 기반 저장소를 지원하고, 신뢰할 수 있는 패키지 통신을 설정하며, 추가적인 소프트웨어 저장소를 관리할 도구들을 설치
- 주로 서드파티 저장소 추가 전 준비 단계로 사용
- 이 명령어는 <mark style="background: #FFF3A3A6;">보안과 관리 효율성을 강화</mark>하고, <mark style="background: #FFF3A3A6;">서드파티 저장소에서 패키지를 설치하기 위해 필요한 기본 도구들을 설정</mark>
	1. HTTPS 지원 활성화: `apt-transport-https`와 `ca-certificates` 설치.
	2. 다운로드 도구 설치: `curl` 설치.
	3. GPG 키 관리: `gnupg-agent` 설치.
	4. 추가 저장소 관리 도구: `software-properties-common` 설치.


### GPG 키 추가

### apt 저장소 추가

### 시스템 패키지 업데이트

### docker 설치

### docker 자동 시작 등록 및 설치 확인

- docker 자동 시작 등록
- docker 시작
- docker 상태 확인
### docker 실행 권한 추가

- Usermod를 통한 실행권한 추가
	- sudo usermod -aG docekr {사용자 계정}
	- logout 후 groups 확인

### docker-composen 설치

- 최신 버전의 docker-compose 설치
- docker-compose 권한 설정
- docker-compose 버전 확인

### python pip 설치

- 패키지 업데이트
- Deadsnakes 팀이 유지하는 PPA를 repository에 등록
- pip 설치
