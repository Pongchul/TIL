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
