
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

> $ sudo [[Linux command#mkdir|mkdir]] [[Linux command#-p|-p]] /etc/apt/keyrings

- APT를 위한 키 저장소 디렉토리를 안전하게 준비하기 위한 단계
	- `/etc/apt/keyrings` 디렉토리를 생성
	- 디렉토리가 이미 존재하면 아무 작업도 수행하지 않고 넘어감
	- 이 디렉토리는 보안 키 파일(GPG 키)을 저장하기 위한 디렉토리로 사용

> $ [[Linux command#curl|curl]] [[Linux command#-fsSL(curl 옵션)|-fsSL]] https://download.docker.com/linux/ubuntu/gpg | [[Linux command#(파이프)|^]] sudo [[Linux command#gpg|gpg]] [[Linux command#--dearmor|--dearmor]] [[Linux command#-o /etc/apt/keyrings/docker.gpg|-o /etc/apt/keyrings/docker.gpg]]

- Docker 저장소의 GPG 키가 적절한 형식으로 변환되어 APT가 저장소를 신뢰할 수 있도록 설정
	1. Docker 저장소에서 제공하는 GPG 키 파일을 안전하게 다운로드
	2. `|`:  <mark style="background: #FFF3A3A6;">앞 명령어의 출력을 뒤 명령어의 입력으로 전달</mark>
		- <mark style="background: #BBFABBA6;">다운로드한 데이터를 gpg 명령어로 전달</mark>
	3. GPG 키 데이터를 바이너리 형식으로 변환 후 `/etc/apt/keyrings/docker.gpg`에 저장

### apt 저장소 추가

>  $ [[Linux command#echo|echo]] [[Linux command#"deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https //download.docker.com/linux/ubuntu $(lsb_release -cs) stable"|"deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https //download.docker.com/linux/ubuntu $(lsb_release -cs) stable"]] |[[Linux command#(파이프)|^]] sudo [[Linux command#tee|tee]] /etc/apt/sources.list.d/docker.list [[Linux command#> (리다이렉션)|>]] [[Linux command#/dev/null|/dev/null]]

- Docker 저장소를 APT 소스 리스트에 추가하는 명령어
- <mark style="background: #FFF3A3A6;">`/etc/apt/sources.list.d/docker.list` 파일에 Docker 저장소 정보가 추가</mark>
- <mark style="background: #FFF3A3A6;">APT는 이 저장소를 통해 Docker 관련 패키지를 검색하고 설치 가능</mark>
	1. `echo`:
		- APT 저장소에 추가할 Docker 저장소 정보를 생성
	2. `arch=$(dpkg --print-architecture)`:
		- 현재 시스템의 CPU 아키텍처를 자동으로 삽입
	3. `signed-by=/etc/apt/keyrings/docker.gpg`:
		- 패키지 서명을 검증하기 위한 GPG 키를 지정
	4. `$(lsb_release -cs)`:
		- 현재 Ubuntu 버전의 코드네임을 자동으로 삽입
	5. `| sudo tee /etc/apt/sources.list.d/docker.list`:
		- 생성된 저장소 정보를 `/etc/apt/sources.list.d/docker.list` 파일에 저장
	6.  `> /dev/null`:
		- 명령어 실행 중 발생하는 출력을 화면에 표시하지 않음

### 시스템 패키지 업데이트

> $ sudo [[Linux command#apt-get|apt-get]] [[Linux command#update|update]]

- 패키지 목록 업데이트

### docker 설치

> $ sudo apt-get install docker-ce docker-ce-cli containerd.io -y



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
