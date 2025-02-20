
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

> $ sudo apt-get install [[Linux command#docker-ce|docker-ce]] [[Linux command#docker-ce-cli|docker-ce-cli]] [[Linux command#containerd.io|containerd.io]] [[Linux command#-y|-y]]

- Docker의 핵심 엔진(Docker CE), CLI 툴(Docker CE CLI), 컨테이너 런타임(Containerd)을 설치하고, 설치 중 사용자 확인 없이 자동으로 진행하도록 설정
	1. **`sudo`**: 관리자 권한으로 실행
	2. **`apt-get install`**: 패키지 설치 명령어
	3. **`docker-ce`**: Docker 커뮤니티 에디션을 설치
	4. **`docker-ce-cli`**: Docker의 커맨드라인 툴을 설치
	5. **`containerd.io`**: Docker 컨테이너를 실행할 런타임 패키지 설치
	6. **`-y`**: 설치 중 자동으로 모든 확인을 'yes'로 처리

- **Docker 엔진 설치**: `docker-ce` 패키지를 설치하여 Docker 엔진을 설정
- **CLI 툴 설치**: `docker-ce-cli`로 명령줄에서 Docker를 관리할 수 있게 설정
- **컨테이너 런타임 설치**: `containerd.io`를 설치하여 컨테이너 실행을 위한 런타임을 제공

### docker 자동 시작 등록 및 설치 확인

> $ sudo [[Linux command#systemctl|systemctl]] [[Linux command#enable|enable]] docker
- docker 자동 시작 등록

> $ sudo systemctl [[Linux command#start|start]] docker
- docker 시작

> $ sudo systemctl [[Linux command#status|status]] docker
- docker 상태 확인

### docker 실행 권한 추가

- Usermod를 통한 실행권한 추가

> $ sudo [[Linux command#usermod|usermod]] [[Linux command#-a (in -aG)|-a]][[Linux command#-G|G]] docker minjh
- sudo usermod -aG docekr {사용자 계정}
- 사용자 `minjh`를 `docker` 그룹에 추가하여, 비관리자 권한으로 Docker 명령어를 사용할 수 있도록 설정

> $ [[Linux command#groups|groups]]
> $ docker [[Linux command#ps (in docker)|ps]] [[Linux command#-a|-a]]
> $ docker [[Linux command#images|images]]
- logout 후 groups 확인
- **`groups`**:
    - 현재 사용자가 속한 그룹 목록을 확인
- **`docker ps -a`**:
    - Docker 컨테이너 전체(실행 중 + 정지된 상태)의 목록을 확인
- **`docker images`**:
    - 현재 시스템에 저장된 Docker 이미지 목록을 확인
### docker-compose 설치

> $ sudo curl [[Linux command#-L|-L]] "https://github.com/docker/compose/releases/latest/download/docker-compose-$(uname -s)-$(uname -m)" [[Linux command#-o /etc/apt/keyrings/docker.gpg|-o]] /usr/local/bin/docker-compose
- `curl`을 사용 최신 버전 Docker Compose 바이너리를 다운로드하고 `/usr/local/bin/docker-compose`에 저장
- 시스템과 아키텍처에 맞는 바이너리를 동적으로 선택하여 다운로드

> $ sudo [[Linux command#chmod|chmod]] [[Linux command#+x|+x]] /usr/local/bin/docker-compose
- docker-compose 권한 설정

> $ docker-compose [[Linux command#-v|-v]]
- docker-compose 버전 확인

### python pip 설치

> $ sudo apt update && sudo apt upgrade [[Linux command#-y|–y]]
> $ sudo apt install [[Linux command#software-properties-common|software-properties-common]] -y
- 패키지 업데이트, 패키지 업그레이드
- PAA 추가를 위한 필수 도구 설치

> sudo [[Linux command#add-apt-repository|add-apt-repository]] [[Linux command#ppa deadsnakes/ppa|ppa:deadsnakes/ppa]]
- Deadsnakes 팀이 유지하는 PPA를 repository에 등록

> sudo apt [[Linux command#install|install]] [[Linux command#python3-pip|python3-pip]] [[Linux command#python3-venv|python3-venv]]
- Python 3용 패키지 관리자`pip`와 가상 환경`venv`을 설치