## [[docker 기본 환경 설정 1차]] 에서 추가되는 내용 + 기타 개발 환경 구축

### Miniconda 다운로드 및 설치

> $ mkdir [[Linux command#-p|-p]] miniconda3
> $ [[Linux command#wget|wget]] https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh [[Linux command#-o /etc/apt/keyrings/docker.gpg|-O]] miniconda3/miniconda.sh
> $ [[Linux command#bash|bash]] miniconda3/miniconda.sh [[Linux command#-b|-b]] [[Linux command#-u|-u]] [[Linux command#-p|-p]] miniconda3

- 상위 디렉터리가 없을 경우 함께 생성하며, `miniconda3`라는 이름의 디렉터리 생성
- 설치 스크립트 다운로드
- 설치된 스트립트 실행하여 Miniconda3 설치


- base 가상환경 활성 및 비활성
	- `$ source miniconda3/bin/activate`
		- miniconda3의 기본 가상환경(base) 활성화 
	- `$ conda init`
		- conda를 초기화하는 명령
		- conda를 셸에 통합하여 가상환경 관리 명령을 편리하게 설정
	- `$ source miniconda3/bin/deactive`
		- 가상환경 비활성화

### NodeJS 설치

> $ [[Linux command#curl|curl]] [[Linux command#-fsSL(curl 옵션)|-fsSL]] https://deb.nodesource.com/setup_18.x |[[Linux command#(파이프)|^]] sudo [[Linux command#-E|-E]] bash - &&\

- Node.js 설치 스크립트를 가져와 실행

> $ sudo apt install nodejs  
> $ sudo apt install npm
> $ sudo npm install [[Linux command#-g|-g]] yarn
> $ sudo yarn -v

- Node.js 설치
- Node.js의 패키지 관리자(NPM)를 설치
- Yarn 패키지 관리자를 전역 설치
- Yarn의 버전 확인

### Jupyter 설치

> $ mkdir -p docker/jupyter && cd docker/jupyter

- docker/jupyter 디렉터리를 생성, 이미 존재하면 넘어감
- docker/jupyter 디렉터리로 이동

> $ vi Dockerfile
> 
> FROM python:3.12  `docker설치를 위한 base image가져오기`
> WORKDIR /app   `jupyter 에서 사용하기 위한 작업 디렉토리 추후 볼륨과 연결`
> RUN pip install jupyter    `jupyter설치`
>EXPOSE 8888  `사용 port `
>ENV NAME World  `환경설정`
>CMD ["jupyter", "notebook", "--ip=0.0.0.0", "--port=8888", "--no-browser", "--allow-root"] `notebook설치`

- Docker file 생성

- **vi Dockerfile** : 명령어 입력 후 하단의 내용대로 기입한 후 저장
- `i` : 내용 수정 가능하게 함(insert)
- `wq` : 저장하고 종료

> $ docker [[Linux command#build|build]] [[Linux command#-t|-t]] my-jupyter-notebook

- Docker 이미지를 빌드하여 my-jupyter-notebook 이라는 이름으로 저장

> $ mkdir notebooks
> $ [[Linux command#vi|vi]] docker-compose.yaml
> 
> version: "3"
> services:
>   jupyter:  
>     image : my-jupyter-notebook
>     container_name: jupyter-container
>     volumes:
>      - ./notebooks:/app
>     restart: always
>     ports:
>      - 8888:8888

- notebooks 라는 디렉터리 생성
- Docker compose 설정 파일을 생성
	- docker-compose.yaml

> $ docker-compose [[Linux command#up|up]] [[Linux command#-d|-d]]

- 설정된 컨테이너를 백그라운드에서 실행

> $ docker [[Linux command#ps (in docker)|ps]] -a

- docker 기동 상태 확인

> $ docker-compose [[Linux command#logs|logs]]

- 실행 중인 컨테이너의 로그 확인

> [http://localhost:8888/lab](http://localhost:8888/lab)

- 위의 주소로 주피터 노트북 실행