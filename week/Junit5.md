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
