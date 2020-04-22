
# API(Application Programming Interface)
 - 약속, 규칙
 - 프로그래밍을 구현하기 위해 정리해 놓은 규칙
 ```
 - url, method
   http://www.medici.co.kr/bigdata/name/{id=1} o
   http://www.medici.co.kr/bigdata/{id=1}  x
```
 - method api
```java
   class People { 
 	 private String name;
 	 public void setName(String name) {
    	this.name = name;
 	}
 }
```
```java
   class Main{ 
   	public static void main(String[] args) {
   		People p = new People();
   		p.setName("김이박");
  }
 }
```
# 생성자
  - 생성자는 클래스이름과 동일하고 리턴타입이 없다.
  - 객체를 생성할 때 가장 먼저 호출되는 것
  - 값을 초기화할 때 사용한다.
  - argument의 개수에 따라서 여러개 사용 할 수 있다.
    : 생성자의 오버로딩이라고 한다. 
  - default 생성자는 생성자를 만들지 않아도 자동 생성된다.
  - argument가 있는 생성자를 만들게 되면 반드시 default 생성자를
    만들어야 한다.  
    
# this/super 키워드
 - this : 자기 자신의 클래스에서 자기자신의 레퍼런스를 가리킬 때 사용되는 키워드
 ```java
  - People p = new People();
                 this();
```
 - this는 생성자로도 사용이 가능하고, 
   자기자신의 멤버 필드나 멤버 메소드를 가져올때도 사용한다.
 ```java
   Class People{
      private String name;

      public setName(String name) {
        this.name = name;
      }
 }
   ```
  - super : 자식에서 부모를 가리키는 레퍼런스
  - super는 부모의 생성자를 호출할 수 있다.
  - super는 부모의 멤버필드와 멤버 메소드에 접근할 수 있다.
  - super는 자식에서 부모의 생성자를 호출할 수 있다.   

# block 변수와 member field의 우선순위
  - block 변수와 member field의 이름이 같으면 block 변수가 우선순위가 높다. 
    block 변수를 사용한다. 
  - 같은 이름을 동일하게 주었을 때는 block변수가 우선 순위이다. this로 구분


# 관계 연산자 
  - >, <, >=, <=, ==, !=

# 논리 연산자
  - &&. ||, !
  - A && B : A도 만족하고 B도 만족할 경우 True를 리턴(연산자를 두개 사용하는 것이 속도가 더 빠름)
  - A || B : A와 B 둘중에 하나만 만족하면 True를 리턴(연산자를 두개 사용하는 것이 속도가 더 빠름)
  -  !A    : A값의 반대값 (true-> false, false-> true)

# 삼항 연산자
  - a>10? "ok" : "false" ;
  - 조건식이 만족하면 그 다음 문장이 실행되고, 아니면 : 다음 문장이 실행된다. 

# 단축 대입연산자
  - +=, -=, /=, %=
  - i += 1, i = i+1; 
  - i -= 1, i = i-1;
  - i /= 1, i = i/1; (몫)
  - i %= 1, i = i%i; (나머지)

# 반복문 for 
  - 어떤 기준값이 존재하고 일정한 증감이 있을 경우에 반복하는 반복문
  ```java
  - for(int i=0; i<10; i++) {
      ...
    }
```
# 반복문 while
  - 해당하는 조건일 경우에만 반복을 하고, 조건을 만족하지 않을 경우에는 빠져나간다. 
  - 무한 루프가 걸릴 수 있기 때문에, 빠져나가는 조건을 만들어 두는 것이 좋다. 
  
  ```java
  - int i = 0;
  	while(i <= 10){
  		i = i+1;
  	}
```
# 반복문 do ~ while
  - do에 있는 문장은 반드시 한번 실행되고, while에 있는 조건을 만족할 동안 do안에 있는 문장을
    반복실행한다. 
    
    ```java
  - do {
  	  Scanner scanner = new Scanner();
  	  scanner.nextInt();
  	}while(i < 10); 
    ```

# 배열
  - 같은 타입의 나열
  - 참조타입이든 기본타입이든 다 사용할 수 있다.
  - 배열은 기본적으로 참조타입이다. 
  - 배열은 index 번호를 가지고 접근해서 데이터를 가져오거나 넣을 수 있다. 
  - 배열 사용방법
  
  ```java
  1) int[ ] a;           // 배열선언 
     a = new int[5];     // 배열생성
     a[0] =1; a[1] =2; a[2] =3;  //배열 값 입력
  2) int[] a = new int [] {1,2,3,4,5};
  3) int[] a = {1,2,3,4,5;}
    ```

  - 배열의 길이를 구할때는 length를 사용한다.
  ```java
- 2차원 배열 int[][] a = new int [5][5];
- 3차원 배열 int[][][] a = new int [5][5][5];
  ```

# enhanced for 
  - iterator pattern
  - 값을 꺼낼때만 사용(*)
  - 값을 넣을때 사용하면 오류가 발생할 수 있다. 
  
  ```java
  - for(type 변수 : array or collection 형태의 변수) {
  			System.out.print(a);
  	}```

# break/continue
  - break : 나를 감싸고 있는 가장 가까운 반복문 하나를 빠져나오는 키워드
  - continue : 반복문을 실행하다가 해당 문을 만나면 한스텝을 증가시키는 키워드 

# 증감 연산자
  - ++, -- 
  - count++ : count = count +1;
  - count-- : count = count -1;
  
```java
  - int count = 0;
    count++; // count = 0;
             // count = 1; (후연산자/실행 시점 이후 증가)
  - int count = 0;
    ++count; // count = 1;
             // count = 1; (전연산자/실행시점 증가)
```
# shallow copy vs deep copy
```java
  - shallow copy(얕은 복사) -> 값이 변경
		int[ ] a = {1, 2, 3, 4, 5};
		int[ ] c = new int [5];
		
		c = a; // shallow copy
		a[2] = 100; 
		for ( int i : c ) {
			System.out.println( i + ",");
		}
    ```

  - deep copy(깊은 복사) -> 값이 변경되지 않음
  
  ```java
  	int [ ] a1 = {1,2,3,4,5};
		int [ ] c1 = new int [5];
		
		// a1 값들을 c1에 공간에 다 복사해 넣어라. 
		System.arraycopy(a1, 0, c1, 0, a1.length);
		a1[2] = 100;
		System.out.println(c1[2]);
```
