## 목표
자바의 상속에 대해 학습하세요.

## 학습할 것 (필수)
- 자바 상속의 특징
- super 키워드
- 메소드 오버라이딩
- 다이나믹 메소드 디스패치 (Dynamic Method Dispatch)
- 추상 클래스
- final 키워드
- Object 클래스


### 자바 상속의 특징
<pre>
상속이란? 한 클래스가 다른 클래스의 속성들을 획득하는 것. 상속을 통해 자식 클래스는 부모 클래스의 필드와 메서드를 재사용할 수 있다. OOP의 주요 개념이다. 
자바 상속의 특징
상속을 해주는 상위 클래스를 부모 클래스(Parent Class, Super Class)라고 부른다.
상속을 받는 하위 클래스를 자식 클래스(Child Class, Sub Class)라고 부른다.
다단계 상속이 가능하고, 다중 상속을 지원하지 않는다.
모든 클래스는 Object 클래스의 자식 클래스이다.
</pre>



### super 키워드
<pre>
 super 키워드는 자식 클래스에서 부모 클래스를 가리키는 키워드이다. 
 super 키워드를 통해 자식 클래스는 부모 클래스의 필드나 메서드를 호출할 수 있다.
 super 키워드와 헷갈릴 수도 있는 super() 메서드는 부모 클래스의 생성자 함수를 호출하는 메서드이다. 
 자식 클래스의 생성자 함수에는 기본적으로 super()를 호출해야 한다. 기입하지 않는 경우엔 컴파일러가 슬쩍 끼워 넣어 준다.
 
 super()는 부모 클래스의 기본 생성자이며, 인자가 추가되면 그에 맞는 생성자가 호출된다.
 만약 부모 클래스에 기본 생성자가 없다면, 컴파일러가 자동으로 끼워 넣어주던 혜택은 받지 못하고, 
 정의된 생성자 함수를 자식 클래스의 생성자 함수마다 일일이 찾아가며 호출해줘야 한다.
</pre>


### 메소드 오버라이딩
<pre>
오버 라이딩(Overriding)은 부모 클래스로부터 상속받은 메서드를 자식 클래스에서 재정의하는 것이다. 
인터페이스 implements를 잘활용하자 그래야 OOP가 잘지켜진다.
</pre>




### 다이나믹 메소드 디스패치 (Dynamic Method Dispatch)
<https://doompok.tistory.com/21>
<https://alkhwa-113.tistory.com/entry/%EB%94%94%EC%8A%A4%ED%8C%A8%EC%B9%98-%EB%8B%A4%EC%9D%B4%EB%82%98%EB%AF%B9-%EB%94%94%EC%8A%A4%ED%8C%A8%EC%B9%98-%EB%8D%94%EB%B8%94-%EB%94%94%EC%8A%A4%ED%8C%A8%EC%B9%98>

### 추상 클래스
<pre>
추상클래스는 인터페이스와는 다르다 그래서 만약에 사용한다면 계층적으로 상단위에 두어서 사용할것같다.
추상 클래스는 클래스인데 추상적인 클래스이다. 추상 메서드를 가질 수 있고, 온전한 메소드도 가질 수 있는 클래스이다.
</pre>


### final 키워드
<pre>
 final 키워드는 변수나 메소드 등을 immutable 하게 만들어 준다. final이 붙을 수 있는 곳은 클래스, 변수, 메서드가 있다.
 final이 어디에 붙느냐에 따라 다르다 메서드에 final을 붙이면 override를 제한하게 됩니다.
변수에 final을 붙이면 이 변수는 수정할 수 없다는 의미를 가집니다.
final 키워드를 클래스에 붙이면 상속 불가능 클래스가 됩니다.
</pre>


### Object 클래스
<pre>
자바에서 모든 클래스들의 상위 클래스이다. 내가 임의로 만든 클래스도 Object 클래스를 상속받고 있다.
extends Object를 써넣지 않았는데도 어떻게 이게 되는 걸까? 이것은 컴파일러가 컴파일 타임에 쓱 끼워 넣어 준다.
 내가 만든 클래스는 다른 클래스를 상속받고 있는데,
 다중 상속이 되지 않는 자바인데 어떻게 Object 상속 부분을 끼워 넣어줄까?
 이것은 컴파일러가 똑똑하게 가상 상위 클래스를 찾아 거기에 Object 상속을 슥 끼워넣어 준다.
 이렇게 해서 직접적으로나 간접적으로나 모든 클래스는 Object 클래스를 상속받는다.
</pre>






