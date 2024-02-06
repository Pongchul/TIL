# JWT (Json Web Token)

![그림1](https://img1.daumcdn.net/thumb/R1280x0.fpng/?fname=http://t1.daumcdn.net/brunch/service/user/dkta/image/mZyUgQW1H1vk_TFaK2FZbvZqyBM.png)

## 1. JWT란?

+ JWT(Json Web Token)은 Json 객체에 인증에 필요한 정보들을 담은 후 비밀키로 서명한 토큰
+ 공식적으로 인증(Authentication) & 권한허가(Authorization) 방식으로 사용

---
<br>

## 2. JWT 사용하는 이유는 ?

+ 사용자 인증에 필요한 모든 정보는 토큰 자체에 포함하기 때문에 별도의 인증 저장소가 필요없다는 것
+ 분산 마이크로 서비스 환경에서 중앙 집중식 인증 서버와 데이터베이스에 의존하지 않는 쉬운 인증 및 인가 방법을 제공.
+ JWT는 유저를 인증하고 식별하기 위한 토큰(Token) 기반 인증이다. 토큰 자체에 사용자의 권한 정보나 서비스를 사용하기 위한 정보가 포함된다. 
+ JWT를 사용하면 RESTful과 같은 무상태(Stateless)인 환경에서 사용자 데이터를 주고받을 수 있게 된다. 
+ 세션(Session)을 사용하게 될 경우에는 쿠키 등을 통해 사용자를 식별하고 서버에 세션을 저장했지만, JWT와 같은 토큰을 클라이언트에 저장하고 요청시 HTTP 헤더에 토큰을 첨부하는 것만으로도 단순하게 데이터를 요청하고 응답을 받아올 수 있다.
---

<br>

## 3. JWT 구조

![그림2](https://velog.velcdn.com/images/mon99745/post/3b9ee855-0c68-4600-9f97-6f59586fc3cb/image.png)
+ JWT는 "."을 구분자로 나누어 세 가지 문자열의 조합이다. "."을 기준으로 좌측부터 헤더(Header), 페이로드(Payload), 시그니처(Signature)를 의미한다.
+ Header 에는 JWT 에서 사용할 타입과 해시 알고리즘의 종류가 담겨있다.
+ Payload 는 서버에서 첨부한 사용자 권한 정보와 데이터가 담겨있다.
+ Signature 에는 Header, Payload 를 Base64 URL-safe Encode 를 한 이후 Header 에 명시된 해시함수를 적용하고, 개인키(Private Key)로 서명한 전자서명이 담겨있다.
+ 전자서명에는 비대칭 암호화 알고리즘을 사용하므로 암호화를 위한 키와 복호화를 위한 키가 다르다. 암호화(전자서명)에는 개인키를, 복호화(검증)에는 공개키를 사용한다.
---

<br>

## 4. JWT 인증 과정