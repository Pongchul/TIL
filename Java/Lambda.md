# Java 람다식

## 1. 람다식
---
+ y = f(x) 형태의 함수로 구성된 프로그래밍 기법
+ 데이터 포장 객체를 생성후 처리하는 것 보다 데이터를 바로 처리하는 것이 속도에 유리
+ 자바는 람다식을 함수적 인터페이스의 익명 구현 객체로 취급
    - 함수적 인터페이스 : 한 개의 메서드를 가지고 있는 인터페이스

```java
Runnable runnable = new Runnable(){
    public void run(){ ...} // 익명 구현 객체
}

Runnable runnable = () -> {...} // 람다식
// () 는 run의 ()를 의미하고, {}는 run 뒤의 중괄호를 의미
```
매개변수는 ()로 들어오고 코드 블록은 {}이다. 람다식은 인터페이스의 메서드를 구현한 익명 구현 객체가 된다.  
<br>

## 2. 람다식 기본 문법
---
```java
(타입 매개변수,..) -> {실행문;...}
(int a) -> { System.out.println(a); }

매개 타입은 런타임시 대입값에 따라 타입 자동 인식 -> 생략 가능
(a) -> { System.out.println(a); }

매개변수가 하나일 경우 () 생략 가능
a -> { System.out.println(a); }

실행문이 하나일 경우 중괄호 생략 가능
a -> System.out.println(a); 

매개변수가 없다면 괄호 생략 불가능
() -> System.out.println(a);

리턴값이 있는 경우 return 문 사용
(x,y) -> { return x+y; }

중괄호에 return 문만 있다면 리턴 생략 가능
(x,y) -> return x+y; 
```
<br>