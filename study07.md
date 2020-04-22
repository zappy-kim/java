# 인터페이스(interface)

 [인터페이스 : 선언, 추상클래스 : 공통 메소드 구현, 하위자식 : 개별 메소드 설정]

  - 구현하려고 하는 기능들을 정리해 놓은 것 
  - 추상 메소드로만 이루어진 클래스
  - 키워드는 interface라고 쓴다
  - 관계 없는 클래스들의 기능만 구현을 강요하기 위해서 사용한다. 
  - 변수는 자동으로 상수가 된다.
  ```java
    int a=1; -> public final static int A = 1;
  ```
  - 인터페이스의 이름으로 인터페이스를 생성할 수 없다.

  - 기본 접근제한자는 `private`말고 `public`을 사용하자.
  - 인터페이스의 추상 메소드를 구현하지 못하면 자식 클래스는 추상 클래스가 된다.
  - 인터페이스가 여러개일때는 ','로 구분한다.
  ```java
    Class A implements IB, IC, ID{} 
  ```
  - 인터페이스를 상속하는 키워드는 `implements`다.
  - 일반 클래스와 인터페이스가 있을 경우에는 일반 클래스가 우선이다. 
  ```java
    Class A extends B implements IC{}
  ```
  - 인터페이스는 여러개의 인터페이스를 상속할 수 있다.
  - 인터페이스끼리 상속할때는 키워드를 `extends`를 사용한다. 
  ```java
    Interface IA extends IB, IC
  ```
  - java8 추가
  ```
  - default 메소드
    (public) default 리턴타입 메소드명(){}
  - static 메소드 
    (public) static 리턴타입 메소드명(){}
 ```
  - 디폴트 메소드는 인터페이스에서 직접 사용할 수 없고, 자식객체를 구현하고 사용해야 한다.
  ```java
    IA.print(); // x
    IA.ia = new C(); // O
    ia.print();
  ```
  - static 메소드
  ```java
    (public) static 리턴타입 메소드명(){}
  ```
  - ststic 메소드는 자식 객체를 구현하지 않고, 바로 사용할 수 있다. 
  ```java
    IA.print(); // O
  ```
# instanceof 연산자
  - 객체가 어떤 인스턴스를 가지고 있는지 판별하는 연산자 
  - 인스턴스(객체)의 위치에서 확인해야함

  - reference 변수 
```java
  - public void process(People p) {
    if (p instanceof Teacher) {       //teacher타입으로 만들어진 instance가 존재하는지?
    	System.out.println("선생님 입니다.");
    }else if (p instanceof Student) {
    	System.out.println("학생 입니다.");
    }else if (p instanceof People) {       // 가장 하단에 부모 인스턴스(people)를 비교
    	System.out.println("직원 입니다."); 
    }
  } 
```
  - 인스턴스 비교를 할 때 부모타입의 인스턴스인지를 먼저 비교하면 안되고,
    자식의 인스턴스인지를 비교하고 맨 마지막에 부모의 인스턴스륿 비교해야 한다. 
    그렇지 않으면 자식 타입으로 비교가 되지 않는다. 

# 예외처리(Exception)
```
  - Throwable
     |       |
     |
  Exception Error
     |
 RuntimeException Compiletime(Checked) Exception
```
  - 예외 : 예측 가능한 오류
  - Error : 프로그램 상으로 어찌할 수 없는 오류

  - 예외처리 : 예측가능한 오류를 오류 발생없이 처리하기 위한 방법
  - try~catch, finally 
```java
    try {
     1.예외가 발생할 문장
    }catch(Exception e){
     2.예외가 발생하고 처리되는 부분
    }

    try {
     1.예외가 발생할 문장
    }catch(Exception e){
     2.예외가 발생하고 처리되는 부분
    }finally(){
     3.예외가 발생하던 발생하지 않던 반드시 실행되는 구문 (보통 connection을 close할때)
    }
     4. 
     
    1-2-4
    1-2-3-4/1-3-4 : 예외발생 x
```

   - throw new/ throws 
   ```
    throw new는 예외를 발생시키는 키워드
    throws는 예외를 던지는 키워드, 현재상황에서 처리하는 것이 아니라, 
    메소드를 호출하는 곳에서 처리하도록 예외를 던지는 키워드
  ```  
   - throw new O -> 반드시 throws를 해줘야 한다. 
   - 하지만, throws O -> 반드시 throw new를 해줄 필요는 없다. 

  # 3대 checked exception 
   - 반드시 예외처리를 해주어야 하는 패키지로 exception 처리를 하지 않으면 저장이 안됨 
  ```
   - compile type exception 
   - java.io.*
   - java.net.*
   - java.sql.*
  ```

  # User Exception(사용자 예외)
   - 발생할 예외를 개발자가 스스로 만들어서 처리를 하는 예외
      - extends Exception
      - 생성자를 오버로딩한다.
   ```java
      calss NomoneyException extends Exception{
      	NomoneyException(){
      		this(String str);
      	}
      	NomoneyExceotion(String str){
      		super(str); 
      	}
      }
   ```
   
