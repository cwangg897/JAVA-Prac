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
<pre>
자바에서는 실행 시 발생할 수 있는 오류(Exception & Error)를 클래스로 정의하고 있다. 예외와 에러의 상속계층도는 다음과 같다.
</pre>
<img src="https://user-images.githubusercontent.com/79621675/161512614-5f7ad8db-6606-4745-b9bd-961bcf422a17.png" width=500 />


### Exception과 Error의 차이는?
<pre>
"Exception"은 내장 클래스 "Throwable"의 하위 클래스이기도합니다. 예외는 런타임 환경에서 발생하는 예외적 인 조건입니다. 예외의 대부분은 프로그램의 코드로 인해 발생하지만 예외는 복구 할 수 있으므로 프로그램 자체에서 예외를 처리 할 수 있습니다. 예외는 3 개의 키워드 "try", "catch", "throw"를 사용하여 처리됩니다. 

" Error "는 빌트인 클래스 "Throwable"의 서브 클래스입니다. 오류는 시스템 자원 부족으로 인해 발생하는 중대한 조건이며 프로그램 코드로 처리 할 수 없습니다. 
컴파일러는 발생에 대한 지식이 없으므로 오류는 항상 검사되지 않은 유형입니다. 오류는 항상 런타임 환경에서 발생합니다.
</pre>

### 오류 및 예외의 주요 차이점
- 시스템 리소스가 부족한 경우에만 오류가 발생하지만 코드에 문제가있는 경우 예외가 발생합니다.
- 오류는 복구 할 수 없지만 예외를 처리 할 코드를 준비하면 예외를 복구 할 수 있습니다.
- 오류는 결코 처리 할 수 없지만 예외를 throw하는 코드가 try 및 catch 블록 내에 작성된 경우 예외가 코드에 의해 처리 될 수 있습니다.
- 오류가 발생하면 프로그램이 비정상적으로 종료됩니다. 반면에 예외가 발생하면 프로그램은 예외를 throw하고 try 및 catch 블록을 사용하여 처리됩니다.
- 오류는 검사되지 않은 유형입니다. 즉, 오류는 컴파일러에 대한 지식이 아니지만 예외는 검사 된 것과 검사되지 않은 것으로 분류됩니다.
- 오류는 java.lang.Error 패키지에 정의되는 반면, 예외는 java.lang.Exception로 정의됩니다.


#### CheckedExcpetion
<pre>
Checked Exception은 바로 직역하면 알 수 있듯이, 체크가 가능한 예외라는 것이다.
체크란, compiler 단에서 체크가 가능한 에러를 말하는 것이다. 이는 어찌보면 Runtime Exception과 상반된다고 할 수 있다. 이 체크된 에러들, 즉 에러가 발생할 수 있을 때에는 예외처리를 진행해줘야 하는데, 자바에서 강제적으로 try catch문을 작성하도록 하게된다. 예를 들어보자.
</pre>

#### UnChecheckedException
<pre>
Unchecked Exception 이라 함은, 컴파일러 자체에서 예외를 찾아내지 못하는 걸 말한다. Checked Exception과 다르게 예외처리를 강제로 지저하지는 않는 특징이 있다. 
명시적으로 언제 try - catch 를 사용해야할지 컴파일러가 명시해주 않기 때문에, 개발자의 경험 또는 테스트를 통해서 예외처리를 해줄 수 있도록 해야한다.
</pre>


### RuntimeException과 RE가 아닌 것의 차이는?
<pre>
Exception 은 기본적으로 checked exception 이다. 하지만 RuntimeException을 상속하는 exception 들은 unchecked exception 으로 예외처리를 강제화하지 않는다.
</pre>


### 커스텀한 예외 만드는 방법 (실습해보기)
<pre>
필요한 경우 예외를 커스텀하게 만들어서 사용해도 되는데, Java의 상속을 활용하여 만들면 된다.
</pre>


### 예외 순서 (발생한다면 어찌실행되는지)
```java
public class ExceptionApp {
    public static void main(String[] args) {
        try {
            System.out.println(2/0);
            throw new CustomException("메시지 넣어");
            
        } catch (Exception e){
            e.printStackTrace();
        }
    }
}
```
예외가 발생되면 뒷부분은 실행되지 않는다. <br>



