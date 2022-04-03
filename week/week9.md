<https://catch-me-java.tistory.com/46>


## 목표
자바의 예외 처리에 대해 학습하세요.

## 학습할 것 (필수)
- 자바에서 예외 처리 방법 (try, catch, throw, throws, finally)
- 자바가 제공하는 예외 계층 구조
- Exception과 Error의 차이는?
- RuntimeException과 RE가 아닌 것의 차이는?
- 커스텀한 예외 만드는 방법


### 자바에서 예외 처리 방법 (try, catch, throw, throws, finally)
<https://wisdom-and-record.tistory.com/46>
<https://catch-me-java.tistory.com/46>
#### try
예외가 날수있는 구문 <br>

#### catch
catch로 예외를 받는것 <br>

#### throw
<pre>
throw 키워드를 이용해서 고의로 예외를 발생시킬 수도 있다.
예를 들어 사용자가 “바보”라는 닉네임을 사용하지 못하게 하고 싶다면 다음과 같이 예외를 발생시켜 프로그램을 중단시킬 수 있다.
</pre>

#### throws
<pre>
throws 키워드를 통해 메서드에 예외를 선언할 수 있다. 여러 개의 메서드를 쉼표로 구분해서 선언할 수 있다. 형태는 다음과 같다.
thorws는 메서드 선언부에 예외를 선언해둠으로써 해당 메서드를 사용하는 사람들이 어떤 예외를 처리해야 하는 지를 알려주는 역할을 한다.
</pre>


#### finally
<pre>
finally는 try-catch와 함께 예외의 발생 여부와 상관없이 항상 실행되어야 할 코드를 포함시킬 목적으로 사용된다. 
try-catch문의 끝에 선택적으로 덧붙여 사용할 수 있으며, try-catch-finally의 순서로 구성된다.
</pre>


### 자바가 제공하는 예외 계층 구조



### Exception과 Error의 차이는?
### RuntimeException과 RE가 아닌 것의 차이는?
### 커스텀한 예외 만드는 방법

### 예외 순서 (발생한다면 어찌실행되는지)
