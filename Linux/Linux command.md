
##### sudo
- "Superuser DO"의 약자로, 리눅스 및 유닉스 계열 운영체제에서 특정 명령어를 <mark style="background: #FFF3A3A6;">슈퍼유저(관리자 권한)</mark>로 실행하도록 허용하는 명령어  

> 활용 예시
>> [[docker 기본 환경 설정 2차#GPG 키 추가|(1)]] [[docker 기본 환경 설정 1차#시스템 업그레이드 및 업데이트|(2)]]...
---
##### apt
- "Advanced Package Tool"의 약자로, Debian 계열 리눅스 시스템(예: Ubuntu)에서 사용되는 패키지 관리 도구
- 운영체제에서 <mark style="background: #FFF3A3A6;">소프트웨어 패키지를 설치, 업그레이드, 삭제, 검색</mark>하는 작업을 간편하게 수행

 > 활용 예시
 > > [[docker 기본 환경 설정 1차#시스템 업그레이드 및 업데이트|(1)]] 
---

##### apt-get
- 패키지 관리 명령어로, 패키지를 검색, 설치, 업그레이드, 제거하는 데 사용
- 주로 스크립트와 시스템 관리에서 사용
- <mark style="background: #FFF3A3A6;">apt-get</mark>과 <mark style="background: #FFF3A3A6;">apt-cache</mark>의 주요 기능을 통합 -> <mark style="background: #FFB86CA6;">apt</mark> (Ubuntu 16.04 이후)
	- 스크립트 작성 및 세부 제어가 필요한 경우에는 apt-get 사용하는 것이 적합

 > 활용 예시
 > > [[docker 기본 환경 설정 1차#시스템 업그레이드 및 업데이트|(1)]] 
---

##### update
- 현재 시스템에서 사용하는 패키지의 목록을 업데이트하는 작업
	- 패키지 목록을 최신 상태로 동기화
	- 사용 중인 패키지 저장소에 있는 최신 버전의 <mark style="background: #FFF3A3A6;">정보를</mark> 다운로드
	- 실제로 패키지를 설치하거나 업그레이드 하지 않음

 > 활용 예시
 > > [[docker 기본 환경 설정 1차#시스템 업그레이드 및 업데이트|(1)]] 
---

##### upgrade
- `update`로 가져온 최신 패키지 정보를 바탕으로 설치된 패키지를 업그레이드
	- 현재 시스템에 설치된 패키지 중 업그레이드 가능한 패키지를 새로운 버전으로 업데이트
	- 패키지를 업데이트하더라도 새로운 패키지 설치나 기존 패키지 제거는 수행하지 않음
	- 이미 설치된 패키지의 새 버전이 다운로드 및 설치

 > 활용 예시
 > > [[docker 기본 환경 설정 1차#시스템 업그레이드 및 업데이트|(1)]] 
---

##### install
- apt-get의 서브 명령어로, <mark style="background: #FFF3A3A6;">지정된 패키지를 설치</mark>

 > 활용 예시
 > > [[docker 기본 환경 설정 1차#필요 패키지 설치|(1)]] 
---

##### apt-transport-https
- HTTPS 프로토콜을 사용하여 <mark style="background: #FFF3A3A6;">패키지 저장소와 통신할 수 있도록 지원</mark>하는 패키지
	- 기본적으로 APT는 HTTP 프로토콜만 지원
	- HTTPS를 사용하는 안전한 저장소(예: 외부 저장소)를 추가하기 위해 설치 필요

 > 활용 예시
 > > [[docker 기본 환경 설정 1차#필요 패키지 설치|(1)]] 
---

##### ca-certificates
- SSL/TLS 인증서를 검증하기 위한 신뢰할 수 있는 인증서 모음
	- <mark style="background: #FFF3A3A6;">HTTPS 통신 시 서버의 신뢰성을 검증</mark>
	- 패키지 저장소에 HTTPS 프로토콜을 사용하는 경우 필수적

 > 활용 예시
 > > [[docker 기본 환경 설정 1차#필요 패키지 설치|(1)]] 
---

##### curl
- 데이터를 전송하기 위한 명령줄 도구. 주로 HTTP, HTTPS, FTP와 같은 프로토콜로 작업
	- 인터넷에서 데이터를 다운로드하거나 API 요청 등을 수행할 때 사용
	- 예를 들어, 특정 키나 파일을 다운로드하여 패키지 설치 전 준비 작업을 수행할 때 사용
- 데이터를 전송하거나 가져오기 위한 명령줄 도구로, <mark style="background: #FFF3A3A6;">일반적으로 URL을 통해 파일 또는 데이터를 다운로드</mark>

 > 활용 예시
 > > [[docker 기본 환경 설정 1차#필요 패키지 설치|(1)]] [[docker 기본 환경 설정 1차#GPG 키 추가|(2)]]
---

##### gnupg-agent
- GNU Privacy Guard(GPG) <mark style="background: #FFF3A3A6;">암호화 키를 관리하는 에이전트</mark>
	- APT 패키지 시스템에서 패키지의 무결성과 신뢰성을 확인하기 위해 GPG 키를 사용
	- GPG 키와 관련된 작업(키 추가, 관리 등)에 사용

 > 활용 예시
 > > [[docker 기본 환경 설정 1차#필요 패키지 설치|(1)]] 
---

##### software-properties-common
- 추가 소프트웨어 저장소(PPA)를 관리하기 위한 유틸리티
	- `add-apt-repository` 명령어를 제공
	- 서드파티 저장소(PPA)를 쉽게 추가/제거할 수 있도록 지원

 > 활용 예시
 > > [[docker 기본 환경 설정 1차#필요 패키지 설치|(1)]] 
---

##### mkdir
- "make directory"의 약자로,<mark style="background: #FFF3A3A6;"> 새 디렉토리를 생성</mark>하는 명령어
	- 지정된 경로에 새로운 디렉터리 생성

 > 활용 예시
 > > [[docker 기본 환경 설정 1차#GPG 키 추가|(1)]] 
---

##### -p
- "parent"의 약자로, 부모 디렉토리도 함께 생성하도록 지시하는 옵션
	- 경로 중간에 존재하지 않는 디렉토리가 있다면, 이를 자동으로 생성
	- `/etc/apt/keyrings`에서 `apt`나 `keyrings` 디렉토리가 없다면 `-p`가 없을 경우 오류가 발생
	- `-p`를 사용하면 <mark style="background: #FFF3A3A6;">전체 경로를 한 번에 생성</mark>

 > 활용 예시
 > > [[docker 기본 환경 설정 1차#GPG 키 추가|(1)]] 
---

##### -fsSL(curl 옵션)
- 각 옵션의 의미
	- **`-f`**: 실패 시 오류를 반환(HTTP 응답 코드가 400 이상일 경우 종료)
	- **`-s`**: "silent" 모드로 작동하여 진행률 표시를 숨김
	- **`-S`**: `-s`와 함께 사용되어 오류가 발생하면 메시지를 출력
	- **`-L`**: 리디렉션이 있는 경우 최종 URL로 따라가서 다운로드
- 옵션들의 역할
	- 지정된 <mark style="background: #FFF3A3A6;">URL의 데이터를 안정적으로 가져옴</mark>
	- 에러 발생 시 알리고, 리디렉션을 자동으로 처리

 > 활용 예시
 > > [[docker 기본 환경 설정 1차#GPG 키 추가|(1)]] 
---

##### | (파이프)
- 앞 명령어의 출력을 뒤 명령어의 입력으로 전달

 > 활용 예시
 > > [[docker 기본 환경 설정 1차#GPG 키 추가|(1)]] 
---

##### gpg
- GNU Privacy Guard(GPG)로, 데이터를 암호화하거나 서명을 검증할 수 있는 도구
	- 전달받은 GPG 키 데이터를 처리

 > 활용 예시
 > > [[docker 기본 환경 설정 1차#GPG 키 추가|(1)]] 
---

##### --dearmor
- GPG 키 데이터를 바이너리 형식으로 변환
	- APT는 바이너리 형식의 GPG 키를 필요로 함
	- 텍스트 형식(ASCII 아머)에서 바이너리 형식으로 변환하여 APT가 사용할 수 있도록 처리

 > 활용 예시
 > > [[docker 기본 환경 설정 1차#GPG 키 추가|(1)]] 
---

##### -o /etc/apt/keyrings/docker.gpg
- **`-o`**:
    - 출력 파일을 지정.
    - 변환된 바이너리 GPG 키를 저장할 파일 경로를 명시
- **`/etc/apt/keyrings/docker.gpg`**:
    - 변환된 GPG 키 파일의 저장 경로
    - `/etc/apt/keyrings`는 APT와 관련된 키를 보관하기 위해 사용되는 디렉터리

 > 활용 예시
 > > [[docker 기본 환경 설정 1차#GPG 키 추가|(1)]] 
---

##### echo
- 지정된 문자열을 출력하는 명령어
	- `echo`를 사용하여 APT 소스 리스트에 추가할 내용 출력

 > 활용 예시
 > > [[docker 기본 환경 설정 1차#apt 저장소 추가|(1)]] 
---

##### "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
- APT 패키지 관리자가 사용할 Docker 저장소의 정보
- **`deb`**:
    - APT에 추가할 저장소 형식을 지정
    - `deb`은 바이너리 패키지가 있는 저장소를 의미
- **`[arch=$(dpkg --print-architecture)`**:
    - `arch`는 시스템의 CPU 아키텍처를 지정
    - `$(dpkg --print-architecture)`:
        - 현재 시스템의 CPU 아키텍처를 반환
        - 예: `amd64`, `arm64` 등
- **`signed-by=/etc/apt/keyrings/docker.gpg`**:
    - 이 저장소의 패키지 신뢰를 보장하기 위해 사용할 GPG 키 파일 경로를 지정
    - 여기서는 `/etc/apt/keyrings/docker.gpg`에 저장된 키를 사용
- **`https://download.docker.com/linux/ubuntu`**:
    - Docker 저장소의 URL
    - Ubuntu용 Docker 패키지가 이 저장소에 저장되어 있음
- **`$(lsb_release -cs)`**:
    - 현재 Ubuntu 버전의 코드네임을 반환
    - 예: `focal`(20.04), `jammy`(22.04) 등
- **`stable`**:
    - 안정화된 버전의 패키지를 설치하기 위한 저장소를 지정

 > 활용 예시
 > > [[docker 기본 환경 설정 1차#apt 저장소 추가|(1)]] 
---

##### tee
- 입력을 받아 출력으로 전달하고, 동시에 파일에 기록
	- 파이프(`|`)를 통해 전달받은 내용을 파일에 기록
	- 뒤이어 나오는 경로 파일에 저장

 > 활용 예시
 > > [[docker 기본 환경 설정 1차#apt 저장소 추가|(1)]] 
---

##### > (리다이렉션)
- 출력을 파일이나 장치로 리다이렉트

 > 활용 예시
 > > [[docker 기본 환경 설정 1차#apt 저장소 추가|(1)]] 
---

##### /dev/null
- Linux에서 "블랙홀" 역할을 하는 특수 파일
	- 데이터가 `/dev/null`로 보내지면 아무 작업도 하지 않고 버려짐
	- 뒤이어 나오는 경로 파일에 저장

 > 활용 예시
 > > [[docker 기본 환경 설정 1차#apt 저장소 추가|(1)]] 
---
