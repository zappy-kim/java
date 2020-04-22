
# 두 개 이상의 타입 파라미터 선언
```java
 class A <K,Y...>{}
 interface IB<K, V...> {}

 public class product<T,M>{
 	private T kind;
 	private M model;

 	public T getkind(){return this.kind;}
 	public M getModel(){return this.model;}
 	public void setKind(T kind){
 		this.kind = kind;
 	}
 	public void setModel(M model){
 		this.model = model;
 	}
 }

 product <TV, String> product = new Product<TV, String>();
 product <TV, String> product = new Product<>();
```

# 제네릭 메소드
  - 파라미터 변수 타입과 리턴 타입으로 타입 파라미터를 갖는 메소드를 말한다. 
  - 제네릭 메소드 선언방법
    - 리턴 타입 앞에 "<>"기호를 추가하고 타입 파라미터를 기술한다.
    - 타입 파라미터를 리턴타입과 파라미터 변수에 사용한다.
  ```java
 . public <타입 파라미터, .... > 리턴타입 메소드명(파라미터 변수, ....){}
 . public <T> Box<T> boxing (T t){...}
 ```

  - 제네릭 메소드를 호출하는 두가지 방법
    - 리턴타입 변수 = <구체적 타입> 메소드명(파라미터 값) // 명시적으로 구체적인 타입을 지정
```java
- Box<Integer> box = <Integer> boxing(100);  //  타입 파라미터를 명시적으로 Integer로 지정
```
    - 리턴타입 변수 = 메소드명(파라미터 값);        //파라미터값을 보고 구체적 타입을 추정
```java
- Box<Integer> box = boxing(100);            // 타입 파라미터를 Integer로 추정
```
```java
public class Box<T>{
	
}

public class Util{
	public static <T> Box<T> boxing(T t) {
		Box<T> box= new Box<T>();
		box.set(t);
		return box;
	}
}
```

# 구체적인 타입을 제한할 필요가 있을 경우
  - 상속 및 구현 관계를 이용해서 타입을 제한할 수 있다.
  - public <T extends 상위타입> 리턴타입 메소드명(파라미터 변수, ...){}
    - 상위타입은 클래스 뿐만 아니라 인터페이스도 가능하다. 
    - 인터페이스라고 해서 implements를 사용하지 않고 extends로 사용한다.

  - 타입파라미터를 대체할 구체적인 타입
    - 상위타입이거나 하위 또는 구현 클래스만 지정할 수 있다.

  - 주의할 사항
    - 메소드의 중괄호{} 안에서 타입 파라미터 변수로 사용 가능한 것은 상위 타입의 멤버(필드, 메소드)로 제한된다.
    - 하위 타입에만 있는 필드와 메소드는 사용할 수 없다.
    
    ```java
       public <t extends Number> int compare(T t1, T t2){
    	double v1 = t1.doubleValue();   //Number 클래스에 있는 doubleValue() 메소드 사용가능
     	double v2 = t2.doubleValue();
    	return Double.compare(v1, v2);
    }
    ```

# 와일드 카드 타입
  - 제네릭 타입을 파라미터 변수나 리턴타입으로 사용할 때 타입 파라미터를 제한할 목적으로 사용
  - <T extends 상위타입 or 인터페이스>는 제네릭 타입과 제네릭 메소드를 선언할 때 제한을 한다.
  ```java
   public static void registerCourse(Course<?> course){} 
   public static void registerCourseStudent(Course<? extends Student>course){} 
   public static void registerCourseWorker(Course<? super Worker> course){} 
  ````
  
# 와일드 카드의 세가지 타입
```
   A
   |
   B  
 |  |
 C  E
 |
 D
```
  - 제네릭 타입<?> : Unbounded Wildcards(제한없음)
    - 타입 파라미터를 대치하는 구체적인 타입으로 모든 클래스나 인터페이스 타입이 올 수 있다. 
  - 제네릭 타입<? extends 상위타입> : Upper Bounded Wildcards(상위 클래스 제한)
    - 타입 파라미터를 대치하는 구체적인 타입으로 상위타입이나 하위 타입만 올 수 있다.
    - 상위타입 : B > C,D,E 
  - 제네릭 타입<? super 하위타입> : Lower bounded Wildcards(하위 클래스 제한)
    - 타입 파라미터를 대치하는 구체적인 타입으로 하위타입이나 상위 타입이 올 수 있다.
    - 하위타입 : B > B,A
    
# 스트림(stream)
  - 스트림은 반복자다. 
  - 컬렉션(배열포함)의 요소를 하나씩 참조해서 람다식을 처리할 수 있는 반복자다. 
  
 ```java
  java7
  List<String> list = new Arrays.asList("아이유","유재석","장도연");
  Iterator<String> iterator = list.iterator();
  while(iterator.hasNext()) {
  	String name = iterator.next();
  	System.out.println(name);
  }
```
```java
  List<String> list = Arrays.asList("아이유","유재석","장도연");
  Stream<String> stream = list.stream();
  stream.forEach(name -> System.out.println(name));
```
  
  - 스트림의 특징
    - 람다식으로 요소 처리 코드를 제공한다.
    - 스트림이 제공하는 대부분의 요소처리 메소드는 함수형 인터페이스의 파라미터 타입을 가진다 
    - 파라미터 값으로 람다식 또는 메소드 참조를 대입할 수 있다.
    - 내부 반복자를 사용하게 되어 병렬 처리가 쉬워진다. 
      - 외부반복자 : 개발자가 코드로 직접 컬렉션 요소를 반복해서 요청하고 가져오는 코드 패턴
      - 내부반복자 : 컬렉션 내부에서 요소들을 반복시키고 개발자는 요소당 처리해야할 코드만 제공하는 패턴
      - 내부반복자의 이점 : 개발자는 요소 처리 코드에만 집중하게 한다.
        멀티코어 CPU를 최대한 활용하기 위해 요소들을 분배시켜 병렬처리 작업을 할 수 있다.
      - 병렬처리 : 한가지 작업을 서브 작업으로 나누고, 서브 작업들을 분리된 스레드에서 병렬적으로 처리한 후, 
        서브 작업들의 결과들을 최종 결합하는 방법
        - 자바는 ForkJoinPool이라는 프레임워크를 이용해서 병렬 처리를 한다. (JAVA API)

# 스트림 파이프라인
  - 중간처리와 최종처리
  - 리덕션(Rediction)
    - 대량의 데이터를 가공해서 축소하는 것을 말한다 (합계, 평균, 카운팅, 최대값, 최소값 등을 집계하는 것)
    - 요소가 리덕션의 결과물로 바로 집계할 수 없을 경우 중간처리가 필요하다. (중간처리 : 필터링, 매핑, 정렬, 그룹핑)
    - 중간처리한 요소를 최종 처리해서 리덕션 결과물을 산출한다. 

  - 스트림은 중간 처리와 최종 처리를 파이프라인(pipelines)으로 해결한다.
    - 파이프라인(pipelines) : 스트림을 파이프처럼 이어 놓은 것을 말한다.
      - 중간 처리 메소드(필터링, 매핑, 정렬)는 중간 처리된 스트림을 리턴하고
      - 이 스트림에서 다시 중간처리 메소드를 호출해서 파이프 라인을 형성하게 된다.
      - 스트림소스(컬렉션, 배열, 파일) -> 오리지널(중간) -> 필터로 처리(중간) -> 매핑처리(중간) -> 집계처리(최종)
      
    - 최종 스트림의 집계 기능이 시작되기 전까지는 중간 처리는 지연(lazy)된다.
      - 최종 스트림이 시작하면 비로소 컬렉션에서 요소가 하나씩 중간 스트림에서 처리되고 최종 스트림까지 오게 된다.  

  - 중간처리 메소드와 최종처리 메소드로 분류할 수 있다. 
  - 중간처리 메소드인지 최종처리 메소드인지 구별을 해야 한다. 
    - 중간처리 메소드 : 필터링, 매핑, 정렬
    - 최종처리 메소드 : 합계, 평균, 최소값, 최대값 
  - 리턴타입을 보면 구분 할 수 있다.
    - 중간처리 메소드 : 리턴타입이 스트림
    - 최종처리 메소드 : 리턴타입이 기본타입이거나 Optionalxxx 

# 필터링
  - 중간처리 기능으로 요소를 걸러내는 역할을 한다 
  - distinct()
    - stream : equals() 메소드가 true로 나오면 동일한 객체로 판단하고 중복을 제거
    - IntStream, LongStream, DoubleStream : 동일값일 경우 중복을 제거
  - filter() 
    - 파라미터 값으로 주어진 Predicate가 true를 리턴하는 요소만!! 필터링
  

