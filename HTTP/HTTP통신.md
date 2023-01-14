# 모든 개발자를 위한 HTTP 웹 기본 지식 ##

- [모든 개발자를 위한 HTTP 웹 기본 지식 - 김영한님](https://www.inflearn.com/course/http-%EC%9B%B9-%EB%84%A4%ED%8A%B8%EC%9B%8C%ED%81%AC/dashboard)

<br>


## 인터넷 네트워크
- 인터넷 통신
- IP (Internet Protocol)
- TCP,UDP
- PORT
- DNS 

<br>

### 인터넷 통신
- 인터넷 통신 여러 가지 노드를 걸쳐 통신을 한다.
- 클라이언트와 서버 사이에서 복잡한 인터넷 망이 있는데 어떻게 통신을 할까?


### IP (Internet Protocol)
- 지정한 IP주소에 데이터 전달
- 패킷(Packet)이라는 통신 단위로 데이터 전달

### IP 프로토콜의 한계
- 비연결성
- - 패킷을 받을 대상이 없거나 서비스 불능 상태여도 패킷을 전송
- 비신뢰성
- - 중간에 패킷이 사라지면?
- - 패킷이 순서대로 오지 않으면?
- 프로그램 구분
- - 같은 IP를 사용하는 서버에서 통신하는 애플리케이션이 둘 이상이면?

### TCP/UDP
- 애플리케이션계층 - HTTP,FTP
- 전송계층 - TCP,UDP
- 인터넷계층 - IP
- 네트워크 인터페이스 

### TCP (Transfer Control Protocol)
- 두 개의 호스트를 연결하고 데이터 스트림을 교환하게 해주는 중요한 네트워크 프로토콜

### TCP/IP 패킷 정보
- IP ( 출발지 IP, 목적지 IP, 기타 등등...)
- TCP (출발지 PORT, 목적지 PORT, 전송 제어, 순서, 검증 정보 등등..)

### TCP 특징
- 연결지향 -> TCP 3 way handshake(가상 연결)
- 데이터 전달 보증
- 순서 보장
- 신뢰할 수 있는 프로토콜
- 현재는 대부분 TCP 사용

### DNS (Domain Name System)
- 도메인 명을 IP 주소로 변환

### 네이버를 주소창에 치면 일어나는 순서
- 1. 사용자가 웹 브라우저를 통해 naver.com을 입력한다.
- 2. 사용자가 입력한 URL 주소 중에서 도메인 네임 부분을 DNS 서버에서 검색한다.
- 3. DNS 서버에서 해당 모데인 네임에 해당하는 IP 주소를 찾아 사용자가 입력한 URL 정보와 함께 전달한다.
- 4. 웹 페이지 URL 정보와 전달받은 IP 주소는 HTTP 프로토콜을 사용하여 HTTP 요청 메시지를 생성한다.
- 5. 이렇게 생성된 HTTP 요청 메시지는 TCP 프로토콜을 사용하여 인터넷을 거쳐 해당 IP 주소의 컴퓨터로 전송된다.
- 6. 이렇게 도착한 HTTP 요청 메시지는 HTTP 프로토콜을 사용하여 웹 페이지 URL 정보로 변환된다.
- 7. 웹 서버는 도착한 웹 페이지 URL 정보에 해당하는 데이터를 검색한다.
- 8. 검색된 웹 페이지 데이터는 또다시 HTTP 프로토콜을 사용하여 HTTP 응답 메시지를 생성한다.
- 9. 이렇게 생성된 HTTP 응답 메시지는 TCP 프로토콜을 사용하여 인터넷을 거쳐 원래 컴퓨터로 전송된다.
- 10. 도착한 HTTP 응답 메시지는 HTTP 프로토콜을 사용하여 웹 페이지 데이터로 변환된다.
- 11. 변환된 웹 페이지 데이터는 웹 브라우저에 의해 출력되어 사용자가 볼 수 있게 된다.

## URI와 웹 브라우저 요청 흐름
- URI (Uniform Resource Identifier)
- URI = URL (Uniform Resource Locator) + URN (Uniform Resource Name)
- URL -> foo://example.com:8042/over/there?name=ferret#nose
- scheme authority path query fragment 이 순서
- URN -> urn:example:animal:ferret:nose

### URI, URN
- Uniform : 리소스를 식별하는 통일된 방식
- Resource : 자원, URI로 식별할 수 있는 모든 것
- Identifier : 다른 항목과 구분하는데 필요한 정보
- Name : 리소스에 이름을 부여
- 위치는 변할 수 있지만, 이름은 변하지 않는다.
- urn:isbn:8960777331 (책의 isbn URN)
- URN 이름만으로 실제 리소스를 찾을 수 있는 방법이 보편화 되지 않는다.

### URL 전체 문법
- scheme://[userinfo@]host:[:port][/path][?query][#fragment]
- https://www.google.com:443/search?q=hello&hl=ko
- 주로 프로토콜 사용 (프로토콜 : 어떤 방식으로 자원에 접근할 것인가 하는 약속 규칙)
- ex) http->80, https->443
- https는 http에 보안 추가 (HTTP Secure)

### URL
- host -> 호스트명 즉 도메인명 또는 IP주소를 직접 사용가능하다.
- port -> 접속 포트,일반적으로 생략하는데 생략시 http->80, https->443
- path -> 리소스 경로,계층적 구조 ex)/home/file1.jpg, /members/100, /items/iphone12
- query -> key=value의 형태이며 ?로 시작, &로 추가 가능하다. query parameter, query string 등으로 불림, 웹서버에 제공하는 파라미터,문자형태 ex) ?keyA=value&keyB=valueB
- fragment -> html 내부 북마크 등에 사용, 서버에 전송하는 정보가 아니다.

### 웹 브라우저의 요청 흐름
- 웹 브라우저(IP : 100.100.100.1), 구글 서버(IP : 200.200.200.2)
- https://www.google.com/search?q=hello&hl=ko 요청을 보냈을 때
- GET/search?q=hello&hl=ko HTTP/1.1 Host: www.google.com 이런 양식으로 요청 메시지를 보낸다.
- 웹 브라우저가 HTTP 메시지를 생성한 후 SOCKET 라이브러리를 통해 전달하여 TCP/IP 패킷과 HTTP 메시지를 포함하여 보낸다.
- 그 후엔 구글에서도 응답 패킷을 전달하면 웹 브라우저에 HTML 렌더링이 된다.

## HTTP(Hyper Text Transfer Protocol)
- 모든 것이 HTTP
- 클라이언트 서버 구조
- Stateful, Stateless
- 비 연결성(connectionless)
- HTTP 메시지

### 모든 것이 HTTP
- HTML, TEXT, IMAGE, 음성, 영상, 파일, JSON, XML(API)
- 거의 모든 형태의 데이터 전송이 가능하다.
- 서버간에 데이터를 주고 받을 때도 대부분 HTTP를 사용한다
- 지금은 HTTP 시대 !
- HTTP/1.1 (1997): 가장 많이 사용, 우리에게 가장 중요한 버전 (RFC2068 -> RFC2616 -> RFC7230~7235
- HTTP/2 (2015) : 성능개선
- HTTP/3 진행중 : TCP 대신 UDP 사용, 성능 개선
- TCP:HTTP/1.1, HTTP/2 -> UDP:HTTP/3

### HTTP 특징
- 클라이언트 서버 구조: Request Response구조, 클라이언트는 서버에 요청을 보내고, 응답을 대기, 서버가 요청에 대한 결과를 만들어서 응답
- 무상태 프로토콜(Stateless), 비연결성
- HTTP 메시지
- 단순함, 확장 가능

### 무상태 프로토콜(Stateless)
- 서버가 클라이언트의 상태를 보존X
- 장점: 서버 확장성 높음( Scale-out )
- 단점 : 클라이언트가 추가 데이터 전송

### Stateful, Stateless 차이
- 상태 유지 : 중간에 다른 점원으로 바뀌면 안된다. 즉 항상 같은 서버가 유지되어야 한다. ( 중간에 다른 점원으로 바뀔 때 상태 정보를 다른 점원에게 미리 알려줘야 한다.)
- 무상태 : 중간에 다른 점원으로 바뀌어도 된다. 즉 아무 서버나 호출해도 된다.
- 갑자기 고객이 증가해도 점원을 대거 투입할 수 있다.
- 갑자기 클라이언트 요청이 증가해도 서버를 대거 투입할 수 있다.
- 무상태는 응답 서버를 쉽게 바꿀 수 있다. -> 무한한 서버 증설 가능
- 모든 것을 무상태로 설계할 수 있는 경우도 있고 없는 경우도 있다.
- 무상태 (로그인이 필요 없는 단순한 서비스 소개 화면), 상태 유지(로그인)

### 비 연결성(connectionless)
- HTTP는 기본이 연결을 유지하지 않는 모델
- 일반적으로 초 단위의 이하의 빠른 속도로 응답
- 1시간 동안 수천명이 서비스를 사용해도 실제 서버에서 동시에 처리하는 요청은 수시백 이하로 매우 작음
- 서버 자원을 매우 효율적으로 사용할 수 있음

### 비연결성의 한계 및 극복
- TCP/IP 연결을 새로 맺어야 한다. -> 3 way handshake 시간을 추가한다.
- 웹 브라우저로 사이트를 요청하면 HTML 뿐만 아니라 자바스크립트, css, 추가 이미지 등 수많은 자원이 함께 다운로드
- 지금은 HTTP 지속 연결로 문제해결
- HTTP/2, HTTP/3에서 더 많은 최적화

## HTTP 메시지
![HttpStructure](https://user-images.githubusercontent.com/87809321/212208789-c54553fd-0861-4638-b518-f7d9002f93b8.png)

### 시작 라인(요청 메시지)
- start-line => request-line/status-line
- request-line => method SP(공백) request-target SP HTTP-version CRLF(엔터)
- HTTP 메서드 (GET:조회) => 종류 : GET,POST,PUT,DELETE ...
- 요청 대상(/search?q=hello&hl=ko)
- HTTP version
- absolute-path[?query](절대경로[?쿼리])
- 절대경로 =>  "/"로 시작하는 경로
