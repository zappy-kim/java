# 함수형 프로그래밍(functional programming)
  - y = f(x) 형태의 함수로 구성된 프로그래밍 기법
  - 데이터를 파라미터로 전달하고 결과를 받는 코드로 구성
  - 객체지향 프로그래밍보다 효율적인 경우
  - 대용량 데이터 처리에 유리하다. 
    - 데이터를 포장해서 객체를 생성하는 것 보다는 데이터를 바로 처리하는 것이 속도에 유리하다.
    - 멀티코어 CPU에서 데이터를 병렬 처리하고 취합할 때 객체보다는 함수가 유리함
  - 이벤트 지향 프로그래밍
    - 반복적인 이벤트는 핸들러 객체보다는 핸들러 함수가 적합함

- 현대 프로그래밍 기법
  - 객체지향 프로그래밍 + 함수형 프로그래밍

# JAVA8에서 함수형 프로그래밍 지원
- 람다식(Lambda Expression)을 언어 차원에서 제공
    - 람다 계산법에서 사용된 식을 프로그래밍 언어에 접목
    - 익명함수(Anonymous fuction)을 생성하기 위한 식
    - (타입 매개변수) -> {실행문; }
    
- 자바에서 람다식을 수용한 이유
    - 코드가 매우 간결하다. 
    - 컬렉션 요소(대용량 데이터)를 필터링 또는 매핑해서 쉽게 집계할 수 있다. 

# 람다식(Lambda Expressions)
  - java는 람다식을 함수적 인터페이스의 익명 구현 객체로 취급
  - 함수적 인터페이스 : 한개의 메소드를 가지고 있는 인터페이스를 말한다. 
  - 람다식 -> 파라미터를 가진 코드 블록 -> 익명 객체 구현
  ```java
  ex)
  Runnable runnable = () -> {}
                  || 
  Runnable runnable = new Runnable() {
  	public void run(){
  		System.out.println();
  	}
  }
```

# 람다식 기본문법
  - 함수적 스타일의 람다식을 작성하는 방법
  ```java
    (타입 + 파라미터 변수) -> {실행문;}
    (int a) -> {System.out.println(a);}
  ```
  - 파라미터 타입은 런타임시에 대입값에 따라 자동으로 인식하기 때문에 생략 가능
  ```java
    (a) -> {System.out.println(a);}
  ```
  - 하나의 파라미터만 있을 경우에는 괄호() 생략 가능 
  ```java
    a -> {System.out.println(a);}
  ```
  - 하나의 실행문만 있다면 중괄호 ({}) 생략가능
  ```java
    a -> System.out.println(a); // (생략 x)
    
    a -> {
    	  int c = a+20;
    	  System.out.println(a);
    }
  ```
  - 파라미터 변수가 없으면 괄호()를 생략 할 수 없음
  ```java
    () -> {System.out.println(); }
  ```
  - 리턴값이 있는 경우, return문을 사용
  ```java
    (x.y) -> {return x+y;} 
  ```
  - 중괄호({})에 return문만 있을 경우, 중괄호를 생략 가능
  ```java
    (x,y) -> x+y
  ```

# 타겟 타입(target type)
  - 람다식이 대입되는 인터페이스를 말한다. 
  - 익명 구현 객체를 만들 때 사용할 인터페이스다.
  - 인터페이스 변수 = 람다식; 
  ```java
    IA ia = (x, y) -> x + y;
  ```
# 함수형 인터페이스(functional interface)
  - 모든 인터페이스는 람다식의 타겟 타입이 될 수 없다. 
     - 람다식은 하나의 메소드를 정의하기 때문
     - 하나의 추상 메소드만 선언된 인터페이스만 타겟 타입이 될 수 있음

  - 함수형 인터페이스
     - 하나의 추상 메소드만 선언된 인터페이스를 말한다. 

  - @ FuctionalInterface 어노테이션
     - 하나의 추상 메소드만을 가지는지 컴파일러가 체크 하도록 함
     - 두개 이상의 추상 메소드가 선언되어 있으면 컴파일 오류 발생 
     - 이 어노테이션을 사용하면 체크를 해줄 뿐 아니라 하나의 메소드를 가진 인터페이스가 
     있으면 함수형 인터페이스라고 보면 된다.

  - 파라미터 변수와 리턴값이 없는 람다식
  ```java
    @ FunctionalInterface
    public interface MyInterface{
    	public void print();
    }

    MyFuncInterface mfi = () -> {... ;} 
    mfi.print();
  ```
  - 한 개의 추상메소드를 가지는 인터페이스는 모두 람다식 사용이 가능하다. 

# 제네릭, 지네릭(Generics)
  - 1) 전용타입
  ```java
    ArrayList list = new ArrayList();
    list.add(Object o);
    Object o = list.get(i);
    String card = ((Cardlist.get(i)).getCard();

    ArrayList<card> list = new ArrayList<card>();
    // ArrayList<card> list = new ArrayList<>();
    List.add(Card o);
    String card2 = list.get(i).getCard();
  ```
  - 2) 타입을 파라미터화 해서 컴파일시 구체적인 타입이 결정되도록 하는 방법
    - Java5부터 새로 추가된 내용
    - 컬렉션, 람다식(함수형 인터페이스), 스트림, NIO에서 널리 사용됨

  - 3) 제네릭을 사용해서 얻는 이점
    - 미리 타입을 지정해서 casting을 하지 않고 사용할 수 있다. 
    - 컴파일시 강한 타입 체크를 할 수 있다. 
    - 실행시 타입 에러가 나는 것 보다 컴파일시에 미리 타입을 체크해서 에러를 사전에 방지한다.
  

 # 제네릭 타입(Generic Type) 
  - 타입을 파라미터로 가지는 클래스와 인터페이스를 말한다. 
     . 선언시 클래스 또는 인터페이스 이름 뒤에 "<>" 기호가 붙는다. 
     . "<>" 사이에는 타입 파라미터가 위치한다. 
  - 타입 파라미터
     . 일반적으로 대문자 알파벳 한문자로 표현한다. 
     . 개발 코드에서는 타입 파라미터 자리에 구체적인 타입을 지정해야 한다. 

  - 제니릭 타입을 사용하지 않을 때 
  ```java
    public class Box{
    	private Object object;
    	public void set(Object object){
    		this.object = object;
    	}
    	public get(){
    		return object;
    	}
    }

    Box box = new Box();
    box.set("hi~");
    String str = (String)box.get();
  ```

  - 제네릭 타입을 사용할 때 
  ```java
    public Class Box<T> {
    	private T t;
    	public T get(){
    		return t;
    	}
    	public void set(T t){
    		this.t = t;
    	}
    }
    Box<String> box = new Box<String>();
    public class Box<String> {
    	private String t;
    	public void set(String t){
    		this.t = t;
    	}
    	public String get(){
    		return t;
    	}
    }

    Box<String> box = new Box<String>();
    box.set("hi~");
    String str = box.get();
   ```
