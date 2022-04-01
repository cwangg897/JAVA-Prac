## 목표
JUnit 5 학습하세요.
<https://docs.google.com/document/d/1j6mU7Q5gng1mAJZUKUVya4Rs0Jvn5wn_bCUp3rq41nQ/edit>

### JUnit 5: 기본어노테이션
```java
class StudyTest {


    @Test
    void create(){
        Study study = new Study();
        assertNotNull(study);
        System.out.println("create");
    }

    @Test
    void create1(){
        System.out.println("create1");
    }
    
    @Test
    @Disabled // 메서드를 실행시키지 않음
    void disable(){
        System.out.println("disable");
    }

    @BeforeAll // 테스트 메서드 실행 이전에 수행된다.
    static void beforeAll(){
        System.out.println("beforeAll");
    }

    @BeforeEach // 각각의 테스트를 실행하기이전
    void beforeEach(){
        System.out.println("Before each");
    }

    @AfterAll
    static void afterAll(){
        System.out.println("afterAll");
    }


    @AfterEach // 각각의 테스트를 실행한 이후에
    void afterEach(){
        System.out.println("After each");
    }
}
```

### JUnit 5: 테스트 이름 표시하기
#### 기본적인 방법
```java
@Test
    void create_new_study(){ // Camel Case 보다 언더바를 이용하게 읽기편하게 이름을 표시할 수 있다.
        Study study = new Study();
        assertNotNull(study);
        System.out.println("create");
    }
```
#### @DisplayNameGeneration
```java
@DisplayNameGeneration(DisplayNameGenerator.ReplaceUnderscores.class) // 어느위치에 적용가능
class StudyTest {
```

#### @DisplayName
```java
@Test
    @DisplayName("스터디 만들기") // 이방법이 더 많이사용된다. (장점 이모지를 사용할수있다)
    void create_new_study(){ // Camel Case 보다 언더바를 이용하게 읽기편하게 이름을 표시할 수 있다.
        Study study = new Study();
        assertNotNull(study);
        System.out.println("create");
    }
```


### JUnit 5: Assertion (여러가지가 많아서 문서를 확인하자)
```java
    @Test
    @DisplayName("스터디 만들기")
    void create_new_study(){ // Camel Case 보다 언더바를 이용하게 읽기편하게 이름을 표시할 수 있다.
        Study study = new Study();
        assertNotNull(study);
//        study.setStatus(StudyStatus.DRAFT);
        assertEquals(StudyStatus.DRAFT, study.getStatus(), 
        "스터디를 처음만들면 상태값이 DRAFT 이어야한다."); // 이거는 성공실패와 상관없이 +연산을한다 그래서 log level +연산과 비슷한듯
    }
    
    assertEquals(StudyStatus.DRAFT, study.getStatus(), 
    ()->"스터디를 처음만들면 상태값이 DRAFT 이어야한다."); // 이렇게 람다의 장점은 문자열 + 연산을 실패한경우에만 해줍니다.
```
주의 사항은 만약 assert메소드 들이 줄지어있다면 깨진부분 뒤부터는 코드가 실행되지 않는다. <br>
그래서 나온 해결방법이 asssertAll로 묶어줘야하는데 이떄 주의사항은 람다식으로 묶어줘야한다.<br>

```java
@Test
    @DisplayName("스터디 만들기")
    void create_new_study(){ // Camel Case 보다 언더바를 이용하게 읽기편하게 이름을 표시할 수 있다.
        Study study = new Study();
        
        assertAll(
                ()-> assertNotNull(study),
                ()->assertEquals(StudyStatus.DRAFT, study.getStatus(),
                        ()->"스터디를 처음만들면 상태값이 DRAFT 이어야한다.")
        );
    }
```


### JUnit 5: 조건에 따라 테스트 실행하기
특정한 환경이나 OS에 따라 실행하거나 하지말아야할때 assume을 사용한다. <br>
```java
@Test
    @DisplayName("스터디 만들기")
    @EnabledOnOs(OS.MAC) // @DisabledOnOs
    void create_new_study(){ // Camel Case 보다 언더바를 이용하게 읽기편하게 이름을 표시할 수 있다.
//        assumeTrue("LOCAL".equalsIgnoreCase(System.getenv("TEST_ENV")));
        

    }
```


### JUnit 5: 태깅과 필터링
```java
@Test
    @DisplayName("스터디 만들기 fast")
    @Tag("fast")
    void create_new_study(){ 
        System.out.println("create new study");

    }

    @Test
    @DisplayName("스터디 만들기 slow")
    @Tag("slow")
    void create1(){
        System.out.println("create1");
    }
```
tag로 해놓으면 인텔리제이에서 기존에는 실행시키면 모든걸 다시키는데 설정을 하면 tag로 fast로만 해놓은것만 실행시키거나 slow로 적혀진 테그만 실행시키도록 할 수 있다.<br>


### JUnit 5: 커스텀 태그
```java
@Target(ElementType.METHOD)
@Retention(RetentionPolicy.RUNTIME)
@Test
@Tag("fast")
public @interface FastTest {
}
```

### JUnit 5: 테스트 반복하기 1부
```java
@DisplayName("스터디 만들기")
    @RepeatedTest(value = 10, name = "{DisplayName}, {currentRepetition}") // 이렇게 이름 만들 수 있음
    void repeatTest(RepetitionInfo repetitionInfo){
        System.out.println("repeatTest"+ repetitionInfo.getCurrentRepetition()
        +"-"+repetitionInfo.getTotalRepetitions());
    }    

@DisplayName("계절")
@ParameterizedTest(name = "{index} {displayName}")
@ValueSource(strings = {"봄", "여름", "가을", "겨울"})
    void parameterTest(String season){
        System.out.println(season);
    }
    
```
반복횟수를 가지고 가능하고 RepeatitionInfo를 통해 몇번이랑 총 몇번해야하는지 적을 수 있다. <br>



### JUnit 5: 테스트 인스턴스
<pre>
JUnit은 테스트 메소드 마다 테스트 인스턴스를 새로 만든다. 
이것이 기본 전략.
테스트 메소드를 독립적으로 실행하여 예상치 못한 부작용을 방지하기 위함이다. 
왜냐하면 테스트를 인스턴스를 어떤 테스트를 먼저하면 값이 변하기때문에 불안정하기때문에 이렇게 메소드 마다 인스턴스를 만들게된다.
그리고 테스트 순서는 예측을 할수없기떄문이다.
이 전략을 JUnit 5에서 변경할 수 있다. 
</pre>

```java
@TestInstance(TestInstance.Lifecycle.PER_CLASS)
class StudyTest {
```

### JUnit 5: 테스트 순서
@TestInstance(Lifecycle.PER_CLASS)와 함께 사용하면 상태도 공유하고 순서도 정할 수 있다.<br>
서로간에 상태를 공유하지 않는 단위테스트의경우는 굳이 순서를 줄필요는없을것같고 로그인하고 이제 다른로직을 실행하는 연속적인 과정에서 사용할것같다. 즉 LifeCycle이 한번인 경우에<br>
```java
@TestMethodOrder(MethodOrderer.OrderAnnotation.class)
class StudyTest {


    @Order(1)
    @Test
    @DisplayName("스터디 만들기 fast")
    @Tag("fast")
    void create_new_study(){
        System.out.println("create new study");

    }

    @Order(2)
    @Test
    @DisplayName("스터디 만들기 slow")
    @Tag("slow")
    void create1(){
        System.out.println("create1");
    }
```


