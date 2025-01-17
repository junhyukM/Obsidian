## [[docker 기본 환경 설정 1차]] 에서 추가되는 내용 + 기타 개발 환경 구축


### Miniconda 다운로드 및 설치

> $ mkdir -p miniconda3
> $ wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh -O miniconda3/miniconda.sh
> $ bash miniconda3/miniconda.sh -b -u -p miniconda3

- 상위 디렉터리가 없을 경우 함께 생성하며, `miniconda3`라는 이름의 디렉터리 생성
- 


- base 가상환경 활성 및 비활성
	- `$ source miniconda3/bin/activate`
	- `$ conda init`
	- `$ source miniconda3/bin/deactive`


### NodeJS 설치


### Jupyter 설치