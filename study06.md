변수명 일괄변경 : 변경 변수명 클릭 후 오른쪽버튼 refactor> rename
--------------------------------------------------------------

# JCF(Java Collection Framework)
 - 자료구조
 - 데이터를 구조적으로 정리하는 방법
 - 어떤 형태로 저장할 것인가
 
- collection

 |set 계열|	list 계열| Map 계열|
 | :---: | :---: | :---: |
 |순서 x	|	순서 o | key, value가 한쌍으로 존재|
 |중복 x	|	중복 o |key가 중복되면 안됨. key로 가져오면, value가 리턴된다|	 
 |HashSet |	ArrayList	 | HashMap|
 |XXXSet |	LinkedList|	xxxMap|
 | ...	 |	Vector	 | ...|

  - set을 꺼낼때는 foreach를 통해서만 뽑을 수 있음


# Vector/ ArrayList 
 - Vector는 동기화 되어있는 list 자료구조
 - ArrayList는 비동기화 되어있는 list 자료구조

 - 동기화는 Vector라는 그릇에 데이터를 저장할 때 다른 사람이 접근 못하게 막고
   데이터를 처리하는 형태
 - 비동기는  ArrayList라는 그릇에 데이터를 저장할 때 다른 사람이 접근해서 데이터가 깨질 수도 있음
 - 동시에 여러사람이 하나의 데이터에 접근하는 경우 vertor를 사용하는 것이 더 좋음


# 콘솔에서 입력받는 방법
``` java
 Scanner scanner = new Scanner(System.in);
 		 int num = scanner.nextInt();
```
