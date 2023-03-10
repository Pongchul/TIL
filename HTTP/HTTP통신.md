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
- 연결지향 -> TCP 3 way handshake(가상 연결), SYN+ACK
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

### 시작 라인(응답 메시지)
- start-line = request-line / status-line
- status-line = HTTP-version SP status-code SP reason-phrase CRLF
- HTTP version
- HTTP status code : success request or failed request 
- 200 : success, 400: error of client request, 500 server internal error
- a statement of reason : a short human-understandable status code description

### HTTP Header
- header-field = field-name ":" OWS field-value OWS (OWS : allow spacing)
- field-name has no case syntax.
- Any additional information required for HTTP transfer
- ex) Content of the message body, size of the message body, compression, authentication, requesting client (browser) information
- There are too many standard headers.
- Can add any header if necessary.

### HTTP Message Body
- Data to be actually transferred
- HTML file, image, video, JSON etc.. All data can be transferred as bytes.

## HTTP Method
- Let's design HTTP API.
- HTTP method - GET,POST
- HTTP method - PUT,PATCH,DELETE
- HTTP method Property

### API URI setting 
- What is resourece?
- How to identify the resource?

### Separating resources from actions
- URI only identifies resources!
- Identyfiy a resource from its behavior toward it
- resource -> Noun, motion -> verb

### HTTP Method (main)
- GET : Inquiry Resource
- POST: Processing Request Data
- PUT: Replace a resource, create if it does not exist
- PATCH: Change the portion of a resource
- DELETE: Delete Resource

### HTTP Method 
- Same as GET, but except for the message portion, only return the status line and header
- OPTIONS : Describe the communicable options (methods) for the target resource (primarily used by CORS)
- CONNECT : Establish a tunnel to the server identified as the destination resource
- TRACE : Performs a message loopback test along the path to the target resource

### HTTP Method (GET)
- Resource Inquiry
- Data that you want to pass to the server is passed through query.
- You can use the message body to deliver data, but it is not recommended because there are many places that do not support it.
- 1. Message Forwarding -> 2. Server Arrival -> 3. Response data

### HTTP Method (POST)
- Processing Request Data
- Forward request data to the server via the message
- Server processes request data -> It performs all functions of processing data that comes through the message body.
- Registration of new resources with mainly delivered data, used for processing.
- 1. Message Forwarding -> 2. Create a new resource -> 3. Response Data 
- The POST method requests that the target resource processes the representation contained in the request according to the resource's unique semantics.
- When this resource URI receives a POST request, each resource must determine how to handle the request data.
- Create new Resource(Registion), Processing Request Data, If it's ambiguous to treat POST Method with another method.

### HTTP Method(PUT)
- Replacing the Resource
- Replace if there is a resource and create if there is no resource. Just Covering
- Client identifies resources
- Client knows resource location and specifies URI.

### HTTP Method(PATCH)
- Change the portion of a resource
- {"age":50} PATCH 요청했을 경우 {"username": "young","age": 20} 데이터가 {"username": "young","age": 50} 으로 부분 변경

### HTTP Method(DELETE)
- Deleting Resource

### Properties of the HTTP method
- Safe Methods(안전)
- Ideompotent Methods(멱등)
- Cacheable Methods(캐시 가능)
- ![image](https://user-images.githubusercontent.com/87809321/213038428-5761d22a-1b1d-4b81-90d3-8ecacac48f7e.png)

### Safe Methods(안전)
- Call does not change the resource.
- Q : But what if I keep paging, logs or something like that, and it fails?
- A : Safety considers only those resources. I don't take that into consideration.

### Idempotent(멱등)
- f(f(x)) = f(x)
- The result is the same whether it is called once, twice, or 100 times.
- Idempotent Method -> (POST : It's not a Idempotent! If called twice, the same payment may occur in duplicate.)
- GET, PUT, DELETE -> Even if you make the same request many times, the result is the same.
- Automatic recovery mechanism, When the server fails to respond normally due to timeout, etc., can the client make the same request again? the basis of judgment
- Idempotent does not consider changing resources in the middle due to external factors.

### Cacheable(캐시가능)
- Can I cache and use response result resources?
- GET, POST, HEAD, PATCH Cacheable
- In reality, only GET and HEAD are used as caches.

### HTTP Method Activity
- Transfer data from client to server.
- Example to HTTP API Design.

### Transfer data from client to server
- Data transfer through Query Parameter
- -> GET, Mainly sort filters (search terms)
- Data transfer through message body
- -> PUT,DELETE,POST EX) Membership, product order, resource registration, resource change

### Transfer data from client to server (Four different situations)
- static data -> images, static text documents
- dynamic data -> search, sort filter in bulletin list (search word)
- Data transfer via HTML Form -> Membership, product order, data change
- Data transfer via HTTP API ->Membership, product order, data change, Server to Server, App Client, Web Client (Ajax)

### Static Data inquiry
- Query parameters not used
- Static data can typically be viewed simply as a resource path without query parameters
- For inquiries, use GET
- images, static text documents

### Dynamic Data Inquiry
- Mainly search, sort filter in bulletin list (search word)
- Filters that reduce query conditions; used primarily for sorting conditions that sort query results
- GET uses query parameters to deliver data ( For inquiries, use GET )

### HTML Form data transfer
- When HTML Form submit tranfer from POST.
- Content-Type: Using application/x-www-form-urlencoded
- -> end the contents of the oorm through the message body (key=value, query parameter format)
- -> Processing urlencoding transmission data
- HTML Form can also be sent to GET
- Content-Type: multipart/form-data
- -> Used when transferring binary data, such as file uploads
- -> Can be transferred with the contents of different types of files and forms (so the name is multipart)

### HTML API Data Trasfer
- Server to server
- -> Back-end system communication
- Application Client
- ->Iphone, Android
- Web Client
- -> Use for communication via JavaScript instead of transferring Form from HTML (AJAX)
- -> ex) API communication with web clients such as React and VueJs
- POST, PUT, PATCH: Send data via message body
- GET : query, forwarding data to query parameters
- Content-Type: Mainly using application/json (virtually standard)

### HTTP API Design Examples
- 1) HTTP API - Collection
- -> POST-based registration
- ex) providing member management API
- 2) HTTP API - Store
- -> PUT-based registration
- ex) Static content management, remote file management
- 3) Using HTTP Form
- -> Manage Web Page Membership
- -> Supply only GET, POST

### API Design(POST Base registration) -> Member Management System
- Member List -> /members -> GET
- Member register -> /members -> POST
- Member inquiry -> /members/{id} -> GET
- Member revise -> /members/{id} -> PATCH,PUT,POST
- Member delete -> /members/{id} -> DELETE

### POST - New Resource Registration Features
- The client does not know the URI of the resource to be registered.
- -> Member register /members -> POST
- -> POST /members
- The server generates a newly registered resource URI.
- -> HTTP/1.1 201 Created
- -> Location: /members/100
- Collection
- -> Resource directories managed by the server
- -> Server creates and manages URI for resources.
- ->The collection here is -> /members

### Registering base on PUT -> API Design
- File List -> /files (GET)
- File Inquiry -> /files/{filename} (GET)
- File Registering -> /files/{filename} (PUT)
- File Delete -> /files/{filename} (DELETE)
- File Bulk Registration /files (POST)

### New Resource Registering Feature
- Client must know resource URI.
- -> File Registering /files/{filename} (PUT)
- -> PUT /files/star.jpg
- The client directly specifies the URI of the resource.
- Store
- -> Resource store managed by the client.
- -> Clients know and manage URI of resources.

### Use HTML Form
- HTML Form support only GET,POST.
- Can be solved using technologies such as AJAX -> Member API reference
- It's about pure HTML, HTML FORM.
- GET, limited by supporting POST only.

### Using HTML FORM
- member list -> /members (GET)
- member registering form -> /members/new (GET)
- member registering -> /members/new, /members (POST)
- member inquiry -> /members/{id} (GET)
- member revising form -> /members/{id}/edit (GET)
- member revising -> /members/{id}/edit, /members/{id} (POST)
- member delete -> /members/{id}/delete (POST)

### Using HTML FORM
- HTML FORM supports GET, POST only
- Control URL
- -> Use verb resource paths to address constraints
- -> The /new, /edit, /delete control URI of POST
- Use when it is ambiguous to resolve with HTTP method. (with HTTP API)

### Good URI Design Concepts
- Document(문서)
- -> Single concept (one file, object instance, database row)
- -> ex) /members/100, /files/star.jpg
- Collection(컬렉션)
- -> Resource directories managed by the server
- -> Server creates and manages URI for resources.
- -> ex) /members
- Store(스토어)
- -> Resource stores managed by clients.
- -> Clients know and manage URI of resources.
- -> ex) /files
- Controller, Control URL
- -> Execute additional processes that are difficult to resolve with documents, collections, and stores.
- -> Use verb directly
- -> ex) /members/{id}/delete

## HTTP Status Code
- HTTP Status Code(HTTP 상태 코드)

### Status Code
- 1xx (informational) : Request received and processing.
- 2xx (Successful): Request normal processing
- 3xx (Redirection): Additional action is required to complete the request.
- 4xx (Client Error): The server is unable to fulfill the request due to client errors, incorrect grammar, etc.
- 5xx (Server Error): Server error, server failed to process normal request

