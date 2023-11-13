# 프로젝트 요약
1. AWS EC2를 활용하여 서버 구축
2. Docker, Docker-Compose를 활용하여 배포환경 구축
3. Jenkins를 활용하여 CI/CD 환경 구축

# 기술스택
1. AWS EC2
2. Docker, Docker-Compose
3. Nginx
4. Jenkins

# 로컬 환경에서 배포 환경 구축
### 1. 프로젝트 빌드
1. Spring Boot 프로젝트를 빌드하여 jar 파일 생성
2. Vue 프로젝트를 빌드하여 dist 폴더 생성
### 2. nginx 설정파일 작성
- Vue 프로젝트에서 생성한 웹 페이지를 전달받기 위한 포트번호 지정
- Spring Boot 프로젝트에서 생성한 웹소켓 API를 호출하기 위한 프록시 설정
### 3. Dockerfile 작성
1. Spring Boot 프로젝트를 실행할 Dockerfile 작성
   - JRE 도커 이미지 Pull
   - 빌드 결과물인 jar 파일을 JRE 도커 이미지에 복사
   - jar 파일 실행
2. Vue 프로젝트를 실행할 Dockerfile 작성
   - Nginx 도커 이미지 Pull
   - 빌드 결과물인 dist 폴더를 Nginx 도커 이미지에 복사
   - Nginx 실행
### 4. docker-compose.yml 작성





### 1. Docker를 활용하여 Nginx 설치
1. 도커 nginx 이미지 pull
    - sudo docker pull nginx
2. pull 받은 도커 nginx 이미지를 컨테이너로 실행
    - docker run -d --name nginx -d -p 8082:80 nginx
3. 

### 1. 프로젝트 빌드 및 배포를 위한 Dockerfile 작성
1. 


### 1. AWS EC2 인스턴스 생성
1. OS Image: Amazon Machine Image 선택
2. 인스턴스 유형: t2.micro 선택
3. 안전한 AWS 접속을 위한 키페어 생성(생성한 키페어는 다운로드하여 안전하게 보관
4. 인바운드 보안규칙 설정
   - SSH 접속을 위한 22번 포트 추가
   - Nginx 서버 접속을 위한 8081번 포트 추가
   - Jenkins 서버 접속을 위한 8082번 포트 추가
5. 생성한 키페어 권한을 400으로 변경
6. ssh 명령어를 통해 EC2 인스턴스에 접속
### 2. AWS EC2 인스턴스에 Docker 설치
1. Docker 설치
2. Docker 실행
3. Docker 그룹에 사용자 추가
4. /var/run/docker.sock 권한을 666으로 변경
### 3. AWS EC2 인스턴스에 Nginx 설치
1. 도커 nginx 이미지 pull



### 3. AWS EC2 인스턴스에 Jenkins 설치
1. 도커 젠킨스 이미지 pull
2. pull 받은 젠킨스 이미지를 컨테이너로 실행
    - sudo docker run --name jenkins -d -p 8082:8080 -v /var/run/docker.sock:/var/run/docker.sock -v /home/ec2-user/jenkins:/var/jenkins_home jenkins/jenkins:lts
3. 젠킨스 도커 컨테이너에 접속하여, 젠킨스 초기 비밀번호 확인
4. 젠킨스 서버([AWS EC2 퍼블릭 IPv4 주소]:8082) 접속


# 무중단 배포 과정
