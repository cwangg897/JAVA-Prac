

## 목표
자바의 인터페이스에 대해 학습하세요. <br>
<https://velog.io/@zayson/%EB%B0%B1%EA%B8%B0%EC%84%A0%EB%8B%98%EA%B3%BC-%ED%95%A8%EA%BB%98%ED%95%98%EB%8A%94-Live-Study-8%EC%A3%BC%EC%B0%A8-%EC%9D%B8%ED%84%B0%ED%8E%98%EC%9D%B4%EC%8A%A4> <br>

## 학습할 것 (필수)
- 인터페이스 정의하는 방법
- 인터페이스 구현하는 방법
- 인터페이스 레퍼런스를 통해 구현체를 사용하는 방법
- 인터페이스 상속
- 인터페이스의 기본 메소드 (Default Method), 자바 8
- 인터페이스의 static 메소드, 자바 8
- 인터페이스의 private 메소드, 자바 9


### 인터페이스 정의하는 방법
<pre>
인터페이스를 정의하기 위해서는 interface 키워드를 이용하여 선언한다.
인터페이스는 반드시 상수와 추상 메소드만 사용이 가능하다.

인터페이스 장점
1. 동시적인 개발을 통한 개발 시간 단축
2. 틀을 인터페이스로 만들고 해당 인터페이스를 구현하여 확장이 용이
3. 관계가 없는 클래스 간의 공통적인 부분이 있는 경우, 인터페이스를 통해 공통 부분 관계 형성 가능
4. 인터페이스를 이용하여 선언과 구현을 분리함으로써 클래스 간의 변경(결합도)에 영향을 미치지 않도록한다.
</pre>


### 인터페이스 구현하는 방법
<pre>
인터페이스를 구현하기 위해서는 implements 키워드를 이용하여 구현한다.
인터페이스에 선언된 추상 메소드는 반드시 오버라이딩해서 사용해야하며, 인터페이스에 선언되어 있는 변수는 상수이므로 값을 변경할 수 없음에 유의한다.
</pre>


### 인터페이스 레퍼런스를 통해 구현체를 사용하는 방법
<pre>
Car 인터페이스 타입으로 CarImpl 구현체를 사용한다면 Car 인터페이스에 선언된 메소드들만 사용가능함을 확인할 수 있다.
그런데 사용할려면 형변환(Casting)을 통해서 사용할 수 있다.
</pre>

```java
public interface Car {

    void start();
    void end();
}

public class CarImpl implements Car {
    @Override
    public void start() {
        System.out.println("자동차 시동");
    }

    @Override
    public void end() {
        System.out.println("자동차 꺼짐");
    }

    public void bang(){
        System.out.println("빵빵");
    }
}

public class CarApp {
    public static void main(String[] args) {
        Car car = new CarImpl();
        CarImpl carImpl = new CarImpl();
        // 불가능 car.bang
        carImpl.bang();

    }
}
```

### 인터페이스 상속
<pre>
클래스가 단일 상속만 지원하는 반면에 인터페이스는 다중 상속을 지원한다.
만약 동일한 이름을 가진 메소드가 인터페이스에 존재한다면?
만약 다중 상속을 implements에서 동일한 이름의 중복된다는 컴파일 에러 메세지를 출력한다.
</pre>



### 인터페이스의 기본 메소드 (Default Method), 자바 8
<pre>
Java 8 부터는 인터페이스 내부에 default 접근제어자를 이용해 메소드를 정의해놓을 수 있는 default Method를 지원하기 시작하였다.
default method는 이미 구현되어 있기 때문에 하위 구현체에서 오버라이딩을 통해 재정의를 해도 되고 인터페이스에 정의된 그대로 사용해도 된다.
</pre>


### 인터페이스의 static 메소드, 자바 8
<pre>
Default Method와 마찬가지로 Java 8부터 지원하기 시작한 기능이며 인터페이스 내에 기능을 정의하여 사용할 수 있다.
또한, 클래스의 static 메소드가 클래스명.메소드명 형식으로 호출하는 것과 달리 인터페이스의 static method는 인터페이스명.메소드명 형식으로 호출해야한다.
</pre>


### 인터페이스의 private 메소드, 자바 9
<pre>
default, static method로 인해 인터페이스 내부에 코드를 구현할 수 있게 되면서 외부 구현체에서 필요한 메소드가 아닌 내부에서만 작동되기를 원하는 메소드도 노출이 되는 경우가 발생했다.
따라서, 이러한 문제점을 해결하기 위해 Java 9부터는 private method를 지원하여 코드의 중복을 피하고, 내부에서 작동하는 메소드에 대해서 캡슐화를 유지할 수 있게 하였다.
</pre>
