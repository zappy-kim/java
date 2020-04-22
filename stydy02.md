# 시스템변수 생성
- java_home
- C:\Program Files\ojdkbuild\java-1.8.0-openjdk-1.8.0.232-2

# path 위치 재설정
- %JAVA_HOME%\bin
- %JAVA_HOME%\jre\bin

# cmd 창에서 확인
- java -version
- javap java.lang.Object

------------------------

# pbv vs pbr
기본타입은 value를 주고 value를 받는다.
참조타입은 reference를 주고 reference를 받는다.

## 1. pass by value
 - assign by value
 - immutable
 
``` java EX) 
int a = 10l
int b = a; // a -> b
c = a+20;
System.out.println(a);  // 10 -> 값이 변하지 않음 
                        // a값이 변하려면 a에 재할당을 해야한다. 

```

## 2. pass by reference
 - assign by reference
 - mutable

``` java EX)
int[] c = {1,2,3,4,5};
int[] d = new int[5];
d = c;
c[2] = 100;
System.out.println(d[2]); // 100 -> d를 변경하지 않았음에도 값이 변경 
```
# parameter/arguement 
 - 메소드의 괄호안에 타입+변수명의 형태로 받을 값을 지정해주는 것을 이야기한다. 
 ```java
   P p = new P(); 
   p.setName(String name); // P클래스에 name이라는 변수로 값을 넣어준다. 
   ```

# 접근제한자(access modifier)
```
private   - : 같은 클래스 내에서만 접근 가능 
(default)   : 같은 패키지 내에서만 접근 가능/ 접근제한자가 없다.
protected # : 상속 o public, 상속 x default
public    + : 모든 곳에서 접근이 가능
```
```java
package com.medici.testa;
public class A{
	private int money = 10;
	public void sendMoney() {
	  System.out.println("돈을 보냅니다.");
	}
} 
```
```java
package com.medici.testb;
public class B{
	int money2 = 20;
	void getMoney() {
	System.out.println("돈을 받습니다.");
	}
} 
```

# OOP의 3대 특징
```
 - 은닉성(encapsulation)
   : member field private, member method public
 - 상속성(inheritance)
   : 부모에 있는 member(member field, member method)를 물려 받는 것
 - 다형성(polymorphism)
   : 다양한 형태를 나타내는 성질
     부모에 있는 메소드가 자식의 형태에 따라 다양하게 호출되는 것 
```

# 초기화
- member field에 값을 선언하지 않으면 참조타입은 null로 초기화가 되고,
기본타입은 기본타입의 기본값으로 초기화가 된다. 

```java
Class A{
	int sum;  // member field, 전역변수
	          // sum = 0;
}
```

# 은닉성
 - private 변수명, public 메소드
 - Main 출력 시 private 변수는 접근할 수 없으나, public인 메소드로 접근이 가능함 
```java
Class People{
	private int age;
	public void setAge(int age){
		this.age = age;
	}
	public int getAge(){
		return age;
	}
}
```
```java
Class Main{
	public static void main(String[] args) {
	People p = new People();
	P.age = 10; // x
	p.getAge; //o
	}
}
```

# 상속성(inheritance)
 - 부모에 있는 member(member field, member method)를 물려 받는 것
 ```java
 - 상속키워드  extends
   자식클래스 extends 부모 클래스

   Class Student extends People{
       ... 
   }
  ```

 - 상속이 되는 의미는 is 단계이다. 
 - Student(자식) is People(부모)이 true인 관계이다.

# Class(클래스)
 - 속성(attribute)과 행위(method)가 들어있는 설계도
 - 설계도, 붕어빵 틀
 - 블루프린트(청사진)
 - .java

# Object(.class)
 - instance, 오브젝트
 - 건물, 붕어빵
 - .class
``` java
 P(클래스/.java) p = new P(인스턴스/.class)
```

# 메모리 4대 특징
```
 - 자식이 생성되면 부모도 생성된다. (자생부생)
 - 자식이 설계도에 올라가면 부모도 설계도에 올라간다. (자설부설)
 - 생성된 주소는 부모의 주소를 가리킨다. (생주부주)
 - 설계도에 공개된 메소드만 사용이 가능하다. (설공메사) 
```

# if문
```java
  if(조건식) { 
 	//조건식이 참일경우 실행되는 문장
   }else {
    // 조건식이 거짓일 경우 실행되는 문장 
   }
```
```java
 if(조건식 1) {
    // 조건식 1이 만족할 경우 실행되는 문장.
   }else if(조건식 2) {
 	// 조건식 2가 만족할 경우 실행되는 문장.
   }else {
 	//조건식 1도 만족 x, 조건식 2도 만족 x 경우 실행되는 문장
   }
```
```java
 - if(조건식) {
 	조건식이 만족할 경우 실행하는 문장
   }
    조건식이 만족하지 않을 경우에는 여기가 실행 
```

# 지역변수
- local variable(지역변수)은 초기값을 설정해 주어야 한다. 
```java
public void localvar() {
	int a;
	int b = 10;
	int c = b+a; // a는 오류가 발생한다. 
	       		 // a에 초기값을 지정해줘야한다. 
}
```

# String Class(문자열 클래스)
 - 문자열을 받을때 사용하는 참조타입 클래스
 - 참조타입이지만 기본타입의 성질을 갖고 있는 클래스
 ```
 - 특징
  - immutable
    값을 재할당 하기 전까지는 값이 변하지 않는다.
  - concatenation
    String타입을 만나는 순간 String 타입이 된다.
```
```java
   String s = new String("가나다"); // 참조타입
   String s1 = "가나다"             // 기본타입
   System.out.println(s==s1);                  // False
   System.out.println(s.equals(s1));           // True
   System.out.println(s.eqialsIgnoreCase(s1)); // True
  ```
```java
 - imutable, 다시 할당 할때까지 안바뀜 
 String str = "라마바";   // int a =10
   str.replace("라","가");  // int c = a+20;
   System.out.println(str); // System.out.println(a); 
   // 결과 : 라마바  
```
```java
 - Concatenation, String타입을 만나는 순간 String 타입이 된다. 
 System.out.println(1+2+3+"하하하");   // 6하하하
 System.out.println("하하하"+1+2);     // 하하하12
 System.out.println("하하하"+1+(2+3)); // 하하하15
 System.out.println(1+"하하하"+2+3);   // 1하하하23
 System.out.println((1+2)+3+"하하하"); // 6하하하 
 ```
