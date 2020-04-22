# jar(java archive) 자바 압축파일
  - java로 만들어진 프로그램을 압축해서 라이브러리 형태로 사용할 수 있다. 
  - 다른 사람들에게 배포해서 사용하게 할 수 있다. 
  - jar 파일을 만들어서 export 외부로 배포하거나, 
  - jar 파일을 만들어서 import(library로 사용) 할 수 있다. 

# import 
  - 다른 패키지에 있는 클래스 파일을 가져와서 사용할 때 적용하는 문법이다. 
  - package 다음에 올 수 있다.
  - IDE에서 자동으로 추가를 해준다. 
  - 라이브러리를 추가하고 사용할 때도 import를 해줘야 라이브러리에 있는 
    파일을 사용할 수 있다.
  - package명 + 클래스
  ```java
    import edu.medici.magic.OddMagicSquare
  ```
  - 패키지에 있는 클래스를 다 가져오고 싶으면 *를 사용한다.
  ```java
    import edu.medici.magic.*;
  ```

# 오버로딩(메소드 오버로딩, overloading)
  - 메소드 이름이 같은데 아규먼트의 갯수나 타입이 다를 경우 다른 메소드로 판단

# 형변환(캐스팅(casting)) 

  - 기본타입 형변환 
 ```
    1) 다운캐스팅(casting, explicit(명시적))  
    큰 값을 작은 값에 담는 것   
    
    2) 업캐스팅(up-casting, implicit(암시적), (auto) promotion)
    작은 값을 큰값에 담는 것 
```
  - 참조타입 형변환  
```
    1) 부 <- 자 (부모가 자식의 타입을 그대로 받는 것, implicit(암시적))
    부모 이름(타입)으로 자식은 모든 것을 다 받을 수 있다./ up-casting, 

    2) 자 <- 부 (자식이 부모의 타입을 원하는 형태에 따라 받는 것, explicit(명시적))
    자식은 부모가 주는 타입을 자식의 형태로 맞춰서 선택적으로 받음/ down-casting
```

# oop 용어
  - 부모 parent, super, base
  - 자식 child, Sub, Derived
  - 상속 extends
  - 부모 
     |  일반화(generalization), 추상화(abstraction)
     |  상세화, 구체화(specialization)
  - 자식    

# boxing/ unboxing 
  - boxing : 기본타입을 참조타입으로 바꾸는 것
  - unboxing : 참조타입을 기본타입으로 바꾸는 것
  ``` java
  - ex) int 타입이 같기 때문에 별도 명시를 하지 않지만, 
        타입이 다른 경우 int를 명시해야한다.
     int a = 10;
     Integer aa = new Integer(a); // 기본 -> 참조
     Integer aa2 = 10; // 기본 -> 참조 
     int c = aa2; // 참조 -> 기본
     int c1 = aa.intValue(); // 참조 -> 기본  

     object o = 10; // 기본 -> 참조
     int d = (Integer)o; // 참조 -> 기본 / 기본이 obj이므로 int로 캐스팅 해줘야 바뀐다. 
  ```
# Wrapper Class 
  - 기본타입을 참조타입으로 바꿀때 사용하는 클래스(참조->기본)
  - 기본타입의 앞의 글자를 대문자로 만들면 클래스명이 된다. 
  ```
    Boolean, 
    Byte,
    Character, 
    Short, 
    Integer, 
    Long, 
    Float, 
    Double 
```
# Integer.parseInt(String str) ;
  - 문자열을 int형으로 변환할 때 사용하는 wrapper Class 메소드
  ```java
  - int passwd = Integer.parseInt("12345");
```
# static/non-static 
  - static
    객체를 생성하지 않고 바로 사용할 수 있다.
    사용할 수 있는 메모리에 올라가 있는 것

  - non-static
    메모리에 올라가 있는 상태가 아니므로 객체를 생성해야 사용할 수 있다.

  - non-static에서는 static을 사용할 수 있지만, 
    static에서는 non-static을 사용할 수 없다. 
  
  - static에서 non-static을 사용하려면 
  	1. 객체를 생성하거나, 2. static 키워드를 붙이면 된다. 

  - member field, member method에 다 사용이 가능하다.

# 오버라이딩(overriding)
  - 자식클래스에서 메서드의 역할을 변경하거나 확장 시에 상속 받은 
    메서드를 새로 정의하는 것
  - 부모 자식 관계에서 부모에 있는 메소드와 자식에 있는 메소드가 동일하면 자식의 
    메소드를 호출하는 것 
   ```java
    P p = new P // p가 부모에도 있고 자식에도 있으면, 자식에 있는 것을 호출. 단, 완벽히 같아야 한다. 이름, 타입 등 ..
   ```
# java.lang.Object의 4대 메소드
  ## 1. boolean equals(Object O)
   - 객체끼리 같은지 판단할 때 사용하는 메소드. 객체는 기본적으로 고유하다(같지 않다)
   - 다른데 왜 쓰는지? (-> 추후 설명)
    
```java
    A a = new A();
    A a2 = new A();
    System.out.println(a.equalse(a2)); // -> false
    // equals를 오버라이딩해서 값이 같으면 객체가 같다라고 판단하게 구현
    // String str = new String("아이유");
       String str2 = "아이유";
       str.equals(str2) // true 
```
  ## 2. String toString();
   - object를 문자열 타입으로 변경시켜주는 메소드
   - 객체에 대해 표현하고 있는 문자열 반환. 하위클래스는 toString 메서드를 정의
   - 객체.tostring() 하면 주소값/ 오버라이딩 할 경우 원하는 데이터 출력이 가능하다. 
   -  데이터가 내가 원하는 대로 잘 들어가 있는지 확인 할 때 사용
   
 ## 3. int hashcode();
  - 객체의 해쉬코드를 가져오는 메소드
 	- 객체를 유일하게 식별할 수 있는 정수값을 반환

  ## 4. Class getClass();
    객체의 package명+ 클래스이름을 가져오는 클래스
    
 ```java
    edu.medici.magic.OddMagicSquare
 ```
