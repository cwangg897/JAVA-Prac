## 1주차
<https://github.com/whiteship/live-study/issues/1#issue-738266603>

### 목표
자바 소스 파일(.java)을 JVM으로 실행하는 과정 이해하기.

### 학습할 것
- JVM이란 무엇인가
- 컴파일 하는 방법
- 실행하는 방법
- 바이트코드란 무엇인가
- JIT 컴파일러란 무엇이며 어떻게 동작하는지
- JVM 구성 요소
- JDK와 JRE의 차이

### JVM(Java Virtual Machine)이란 무엇인가
JVM은 어느 OS이던지 자바 프로그램을 실행할 수 있도록 도와주는 프로그램 <br>
Java Byte Code를 OS에 맞게 해석 해주는 역할을 합니다. <br>
Byte Code는 JVM 위에서 OS상관없이 실행된다. <br>
JVM 은 운영체제 위에서 작동하며 자바 프로그램과 운영체제 사이에서 일종의 인터페이스 역할을 수행해 자바 프로그램이 운영체제나 디바이스에 종속되지 않도록 하였다.<br>

### 컴파일 하는 방법
컴파일을 위해선 컴파일 작업을 수행할 java compiler가 필요하다. java comiler는 jdk를 설치하면 bin 폴더안에 javac 라는 이름으로 설치된다. <br>
<code>javac fileName.java</code> javac 라는 명령어 주요 옵션들도 추가할 수 있다 <br>
javac fileName.java 수행하면 fileName.class이 만들어진다.



### 실행하는 방법

