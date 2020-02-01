
## download
openjdk   : 무료
- https://jdk.java.net/java-se-ri/8
- https://github.com/ojdkbuild/ojdkbuild
- oralcejdk : 무료, 특정 API를 사용하면 유료
- eclipse : google에서 eclipse download 검색


## 자바 동작원리 
- one source multiuse
  하나의 소스를 만들면 플랫폼에 상관없이 똑같은 결과를 얻을 수 있다.
- 플랫폼(Operating System, os) 독립적인 프로그래밍
- 컨셉 : 가전기기 통합 oak 코드명으로 제작이 되었음
  * Sum Micro Systems -> Oralce
  * 만든사람 : James Gosling(제임스 고슬링)

- HelloWorld.java 파일을 만들고 javac HelloWorld.java
  -> HelloWorld.class   실행파일(Bytecode)
- 실행 java HelloWorld (.class)
- 함수형 프로그래밍(functional programming) 지원[JDK8/JDK1.8]
  - 람다식 : 필터링, 매필, 집계
- 변수 값이 변하지 않고 처리되며, 한방향으로 진행된다.
- 대용량 데이터 처리를 하기위해서 multi threading을 사용할 수 있다.


## jvm, jre, jdk
- jdk(java development kit) : 자바 개발 할때 필요한 API
- jre(java runtime environment) : 자바 실행할 때 필요한 프로그램
- jvm(java virtual machine) : 자바 가상 머신
jre를 설치하면 jvm은 자동으로 설치가 되고, java를 개발하고 싶으면 jdk까지 설치


## OOP(Object Oriented Programming) 객체 지향 프로그래밍
 - 객체란 행위(method)와 속성(attribute)을 갖는 모든 것
 - 컴포넌트단위(객체)로 클래스를 만들어서 필요한 시점에 조합해서 사용할 수 있도록 하는 것
 - 각 클래스는 자신의 기능이나 역할을 하도록 구현되며, 계층구조를 구성함에 따라서 기능이 실행이 될수도 있고 안될수도 있다.
- 구현된 클래스는 필요한 시점에 호출할 수 있다. 


## 명명법(프로그램 규칙)
- 파스칼(pascal) : 처음에 시작할 때 대문자 그다음 소문자 의미 바뀌면 대문자 소문자
   ex) class CoffeeMachine 클래스, 인터페이스
- 카멜(camel) : 처음에 시작할 때 소문자 의미 바뀔때 첫글자 대문자 소문자
   ex) public void makeCoffee(); 메소드, 변수명
- 헝가리언(hungarian) : 타입 축약 + 이름
   ex) txtName, lblNumber 타입을 줄여서 이름과 붙여사용, GUI(Swing)
- 전체 대문자 : 상수, 변하지 않는 값을 지정할 때
   ex) Math.PI = 3.14, System.out.println(Math.PI); 3.14가 나온다.
- 전체 소문자 : 예약어, 키워드, 패키지
   ex) public, new, void, class , com.sk.sales


## 주석
```
 '//' : 한줄 주석
 /* */ : 여러줄 주석
 /** */ : API Document 만들때 사용되는 주석
```


## Package
- 비슷한 클래스들의 묶음(모음)
  www.sk.co.kr(X)
  kr.co.sk.sales(O) : 영업파트 관련 코드들이 들어감
  kr.co.sk.common(O) : 공통으로 사용하는 코드들이 들어감
- 파일 맨 상단에 작성을 하며, 패키지는 .밑으로 하나씩 폴더로 구성되어 있다.


