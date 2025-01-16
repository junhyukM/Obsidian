
##### docker 설치

###### 시스템 업그레이드 및 업데이트

> $ [[Linux command#sudo|sudo]] [[Linux command#apt|apt]]-get [[Linux command#update|update]] && sudo [[Linux command#apt-get|apt-get]] [[Linux command#upgrade|upgrade]]


###### 필요 패키지 설치

> $ sudo apt-get [[Linux command#install|install]] [[Linux command#apt-transport-https|apt-transport-https]] [[Linux command#ca-certificates|ca-certificates]] [[Linux command#curl|curl]] [[Linux command#gnupg-agent|gnupg-agent]] [[Linux command#software-properties-common|software-properties-common]]

###### GPG 키 추가

###### apt 저장소 추가

###### 시스템 패키지 업데이트

###### docker 설치

###### docker 자동 시작 등록 및 설치 확인

- docker 자동 시작 등록
- docker 시작
- docker 상태 확인
###### docker 실행 권한 추가

- Usermod를 통한 실행권한 추가
	- sudo usermod -aG docekr {사용자 계정}
	- logout 후 groups 확인

###### docker-composen 설치

- 최신 버전의 docker-compose 설치
- docker-compose 권한 설정
- docker-compose 버전 확인

###### python pip 설치

- 패키지 업데이트
- Deadsnakes 팀이 유지하는 PPA를 repository에 등록
- pip 설치
