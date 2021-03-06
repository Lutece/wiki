# 웹서버와 WAS

## 웹서버란?
- 웹 서버의 가장 중요한 기능은 클라이언트(Client, 웹 브라우저, 웹 크롤러)가 요청하는 HTML 문서나 각종 리소스(Resource)를 전달하는 것
- 웹 브라우저나 웹 크롤러가 요청하는 리소스 컴퓨터에 저장되어 있는 정적(static, 컴퓨터에 저장되어 있는 이미지, html, css, js 파일 등)인 데이터이거나 동적인 결과가 될 수 있다.
- 여기서 웹 크롤러란? 검색사이트에서 다른 웹 사이트 정보를 읽어갈때 사용하는 소프트웨어
- 웹 브라우저와 웹서버
  - HTTP, Hyper Text Transfer Protocol 통신

## 웹 서버 소프트웨어의 종류
- 가장 많이 사용하는 웹 서버는 Apache, Nginx, Microsoft IIS
- Apache웹 서버는 Apache Software Foundation에서 개발한 웹서버로 오픈소스 소프트웨어(Open-source Software)이며, 거의 대부분 운영체제에서 설치 및 사용을 할 수 있다.
- Nginx는 차세대 웹서버로 불리며 더 적은 자원으로 더 빠르게 데이터를 서비스하는 것을 목적으로 만들어진 서버이며 Apache웹 서버와 마찬가지로 오픈소스 소프트웨어이다.

## 미들웨어 (MiddleWare)
- 클라이언트 쪽에 비즈니스 로직이 많을 경우, 클라이언트 관리(배포 등)로 인해 비용이 많이 발생하는 문제가 있다.
- 비즈니스 로직을 클라이언트와 DBMS사이의 미들웨어 서버에서 동작하도록 함으로써 클라이언트는 입력과 출력만 담당하도록 한다.
![middleware](/images/middleware.PNG)

## WAS (Web Application Server)란?
- WAS는 일종의 미들웨어로 웹 클라이언트(보통 웹 브라우저)의 요청 중 웹 애플리케이션이 동작하도록 지원하는 목적을 가진다.
- WAS의 중요 기본 기능
1. 프로그램 실행환경, 데이터베이스 접속 기능 제공
2. 여러개의 트랜잭션(논리적인 작업 단위) 관리
3. 비즈니스 로직을 수행
- WAS도 보통 자체적으로 웹 서버 기능을 내장하고 있다.
- 현재는 WAS가 가지고 있는 웹 서버도 정적인 콘텐츠를 처리하는 데 있어서 성능상 큰 차이가 없다.
- 규모가 커질수록 웹 서버와 WAS를 분리한다.
- 자원 이용의 효율성 및 장애 극복(failover), 배포 및 유지보수의 편의성을 위해 웹서버와 WAS를 대체로 분리한다.

## Links
- [edwith, Full-Stack Web Developer 강의](http://www.edwith.org/boostcourse-web/lecture/16665/)
