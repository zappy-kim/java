# download
openjdk   : 무료
- https://jdk.java.net/java-se-ri/8
- https://github.com/ojdkbuild/ojdkbuild
- oralcejdk : 무료, 특정 API를 사용하면 유료
- eclipse : google에서 eclipse download 검색

# 자바 동작원리
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
  - 람다식
    - 필터링
    - 매핑
    - 집계
   - 변수 값이 변하지 않고 처리됨.
   - 한방향으로 진행된다.
   - 대용량 데이터 처리를 하기위해서 multi threading을 사용할 수 있다.

# jvm, jre, jdk
- jdk(java development kit) : 자바 개발 할때 필요한 API
- jre(java runtime environment) : 자바 실행할 때 필요한 프로그램
- jvm(java virtual machine) : 자바 가상 머신
jre를 설치하면 jvm은 자동으로 설치가 되고, java를 개발하고 싶으면 jdk까지 설치


