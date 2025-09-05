# chapter3. JUnit 4와 5의 차이 및 주요 변경점

## 개요
이 챕터에서는 JUnit 4와 JUnit 5의 주요 차이점, 변경된 어노테이션, 구조, 그리고 실무에서의 적용 방법을 다룹니다. Node.js/Express의 Jest, Mocha와의 비교도 포함합니다.

---

## 1. JUnit이란?
- **JUnit**은 자바 진영에서 가장 널리 쓰이는 테스트 프레임워크입니다.
- JUnit 4는 오랜 기간 표준이었으나, JUnit 5(=Jupiter)는 더 유연하고 확장성 있게 개선되었습니다.

---

## 2. JUnit 4 vs JUnit 5 주요 차이점

| 구분 | JUnit 4 | JUnit 5 |
|------|---------|---------|
| 어노테이션 | @Test, @Before, @After, @Ignore 등 | @Test, @BeforeEach, @AfterEach, @Disabled 등 |
| 구조 | 단일 jar | Platform, Jupiter, Vintage 3계층 구조 |
| 확장성 | 제한적 | 확장 API 제공 |
| 동적 테스트 | 불가 | @TestFactory로 가능 |
| 조건부 실행 | 불가 | @EnabledOnOs 등 지원 |

---

## 3. 주요 어노테이션 변경점
- `@Before` → `@BeforeEach`
- `@After` → `@AfterEach`
- `@Ignore` → `@Disabled`
- `@BeforeClass` → `@BeforeAll`
- `@AfterClass` → `@AfterAll`

### 예시 코드 (주석 포함)
```java
// JUnit 4
public class ExampleTest {
    @Before // 각 테스트 전에 실행
    public void setUp() {}
    @Test // 테스트 메서드
    public void testSomething() {}
    @After // 각 테스트 후에 실행
    public void tearDown() {}
}

// JUnit 5
class ExampleTest {
    @BeforeEach // 각 테스트 전에 실행
    void setUp() {}
    @Test // 테스트 메서드
    void testSomething() {}
    @AfterEach // 각 테스트 후에 실행
    void tearDown() {}
}
```

---

## 4. Node.js/Express와의 비교
- Jest, Mocha 등도 `beforeEach`, `afterEach`, `test`(또는 `it`) 등 유사한 구조를 가짐
- 자바와 JS/TS 모두 테스트 실행 전후 훅(Hook) 개념이 있음

---

## 5. 실무 적용 팁
- JUnit 5는 Spring Boot 2.2 이상에서 기본 지원
- Gradle/Maven에서 JUnit 5 의존성 추가 필요
- JUnit 4와 5를 동시에 사용할 수도 있음(Vintage Engine)

---

> **Tip:**
> - JUnit 5의 구조는 Platform(실행기), Jupiter(새 API), Vintage(구버전 호환)로 나뉩니다.
> - 테스트 코드는 `src/test/java`에 위치하며, JS/TS는 `__tests__` 또는 `test` 폴더를 사용합니다.
