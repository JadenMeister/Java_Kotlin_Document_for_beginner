# chapter5. 테스트 방법론(TDD, BDD 등)과 Assertions 메서드 설명

## 개요
이 챕터에서는 테스트 방법론(TDD, BDD 등)의 개념, 장단점, 그리고 자바(Spring Boot)에서 자주 사용하는 Assertions 메서드에 대해 다룹니다. Node.js/Express, JS/TS와의 비교도 포함합니다.

---

## 1. 테스트 방법론 개요

### 1.1 TDD(Test Driven Development)
- **정의:** 테스트를 먼저 작성하고, 그 테스트를 통과하는 코드를 구현하는 개발 방식
- **장점:**
  - 요구사항 명확화
  - 리팩토링 용이
  - 버그 감소
- **단점:**
  - 초기 개발 속도 저하
  - 테스트 코드 작성에 익숙해져야 함
- **Node/Express/TS 비교:** Jest, Mocha 등으로 동일하게 적용 가능

### 1.2 BDD(Behavior Driven Development)
- **정의:** 행동(시나리오) 중심으로 테스트를 작성하는 개발 방식
- **장점:**
  - 비즈니스 요구사항에 집중
  - 협업 및 문서화에 유리
- **단점:**
  - 도구/프레임워크 학습 필요
- **Node/Express/TS 비교:** Jest의 describe/it, Cucumber.js 등으로 BDD 스타일 지원

#### BDD의 Given, When, Then 구체적 설명 및 사용법
- **Given(준비/상태):** 테스트의 시작 상태, 사전 조건, 환경 설정을 명시합니다. (예: "사용자가 회원 가입 페이지에 접속했을 때")
- **When(행동/이벤트):** 사용자의 행동, 시스템에 발생하는 이벤트를 기술합니다. (예: "이름과 이메일을 입력하고 가입 버튼을 누르면")
- **Then(결과/검증):** 기대하는 결과, 시스템의 반응, 상태 변화를 명확히 기술합니다. (예: "회원 가입이 완료된다")
- **And/But:** 여러 조건이나 결과를 연결할 때 사용합니다.

##### 작성 방법 및 실무 팁
- 각 단계는 한 가지 의미만 담도록 명확하게 작성
- 실제 사용자/비즈니스 담당자가 이해할 수 있는 언어 사용
- 복잡한 시나리오는 여러 개의 Given, When, Then, And, But 조합 가능

##### 예시 (Gherkin, Cucumber)
```gherkin
Feature: 회원 가입
  Scenario: 정상적으로 회원 가입이 된다
    Given 사용자가 회원 가입 페이지에 접속했을 때
    And 이메일 입력란에 "test@email.com"을 입력하고
    And 이름 입력란에 "홍길동"을 입력했을 때
    When 가입 버튼을 클릭하면
    Then 회원 가입이 완료되었다는 메시지가 표시된다
```

##### 코드 매핑 예시 (자바, JS/TS)
- **자바(Cucumber):**
  ```java
  @Given("사용자가 회원 가입 페이지에 접속했을 때")
  public void 회원가입_페이지_접속() { /* ... */ }

  @When("가입 버튼을 클릭하면")
  public void 가입_버튼_클릭() { /* ... */ }

  @Then("회원 가입이 완료되었다는 메시지가 표시된다")
  public void 가입_완료_메시지_확인() { /* ... */ }
  ```
- **JS/TS(Cucumber.js):**
  ```js
  Given('사용자가 회원 가입 페이지에 접속했을 때', function () { /* ... */ });
  When('가입 버튼을 클릭하면', function () { /* ... */ });
  Then('회원 가입이 완료되었다는 메시지가 표시된다', function () { /* ... */ });
  ```

##### 실무 적용 팁
- BDD 시나리오는 테스트이자, 요구사항 명세서, 협업 문서 역할을 동시에 함
- 개발자, QA, 기획자가 함께 시나리오를 작성하면 요구사항 누락을 줄일 수 있음

### 1.3 기타 방법론 (ATDD, E2E) - 상세 설명

#### ATDD (Acceptance Test Driven Development, 인수 테스트 주도 개발)
- **정의:** 인수 기준(비즈니스 요구사항, 사용자 스토리 등)에 따라 테스트를 먼저 작성하고, 그 테스트를 통과하는 코드를 개발하는 방법론입니다.
- **특징:** 개발자, 테스터, 비즈니스 담당자가 함께 인수 기준을 정의하며, 테스트는 실제 사용자의 관점에서 작성됩니다.
- **장점:** 요구사항 누락 방지, 커뮤니케이션 강화, 실제 사용자 요구에 부합하는 소프트웨어 개발
- **단점:** 인수 기준 정의에 시간 소요, 협업 필요
- **자바(Spring Boot) 관례:** Cucumber, JBehave 등 BDD/ATDD 프레임워크를 활용해 Gherkin(기븐-언제-그러면) 문법으로 시나리오 작성
    - 예시 (Gherkin):
      ```gherkin
      Feature: 회원 가입
        Scenario: 정상적으로 회원 가입이 된다
          Given 사용자가 회원 가입 페이지에 접속했을 때
          When 이름과 이메일을 입력하고 가입 버튼을 누르면
          Then 회원 가입이 완료된다
      ```
- **Node.js/JS/TS 관례:** Cucumber.js, Jest-cucumber 등으로 Gherkin 기반 시나리오 작성
    - 예시:
      ```js
      // Cucumber.js 예시
      Given('사용자가 회원 가입 페이지에 접속했을 때', function () { /* ... */ });
      When('이름과 이메일을 입력하고 가입 버튼을 누르면', function () { /* ... */ });
      Then('회원 가입이 완료된다', function () { /* ... */ });
      ```

#### E2E (End-to-End Test, 엔드투엔드 테스트)
- **정의:** 실제 사용자의 행동을 시뮬레이션하여, 시스템 전체 플로우(프론트-백-DB 등)를 검증하는 테스트 방법론입니다.
- **특징:** 브라우저 자동화, API 호출, DB 연동 등 전체 시스템을 통합적으로 테스트
- **장점:** 실제 사용자 경험과 가장 유사, 배포 전 전체 품질 보장
- **단점:** 느리고, 환경 구축이 복잡할 수 있음, 디버깅이 어려움
- **자바(Spring Boot) 관례:** Selenium, RestAssured, Testcontainers 등으로 E2E 테스트 작성
    - 예시:
      ```java
      // RestAssured를 활용한 API E2E 테스트 예시
      @Test
      void 회원가입_엔드투엔드_테스트() {
          given()
              .contentType("application/json")
              .body("{\"name\":\"홍길동\", \"email\":\"test@email.com\"}")
          .when()
              .post("/api/signup")
          .then()
              .statusCode(201);
      }
      ```
- **Node.js/JS/TS 관례:** Cypress, Playwright, Puppeteer, Supertest 등으로 E2E 테스트 작성
    - 예시:
      ```js
      // Cypress 예시
      it('회원가입 E2E 테스트', () => {
        cy.visit('/signup');
        cy.get('input[name="name"]').type('홍길동');
        cy.get('input[name="email"]').type('test@email.com');
        cy.get('button[type="submit"]').click();
        cy.contains('회원 가입이 완료되었습니다');
      });
      ```

---

## 2. 주요 테스트 어노테이션과 Assertions 메서드 설명

### 2.1 JUnit 주요 테스트 어노테이션
- `@Test`: 테스트 메서드임을 표시 (Jest/Mocha의 `test()`/`it()`과 유사)
- `@BeforeEach`: 각 테스트 실행 전 준비 메서드 지정 (Jest/Mocha의 `beforeEach`와 유사)
- `@AfterEach`: 각 테스트 실행 후 정리 메서드 지정 (Jest/Mocha의 `afterEach`와 유사)
- `@Disabled`: 해당 테스트를 임시로 비활성화 (Jest의 `test.skip()`, Mocha의 `it.skip()`과 유사)
- `@BeforeAll`, `@AfterAll`: 전체 테스트 전/후 1회 실행 (Jest/Mocha의 `beforeAll`/`afterAll`)

#### 각 어노테이션별 상세 설명
- **@Test**: 해당 메서드를 테스트로 인식하여 실행합니다. (JS/TS: test(), it())
- **@BeforeEach**: 각 테스트 실행 전마다 실행되는 준비 메서드입니다. 주로 setUp()으로 명명합니다. (JS/TS: beforeEach)
- **@AfterEach**: 각 테스트 실행 후마다 실행되는 정리 메서드입니다. 주로 tearDown()으로 명명합니다. (JS/TS: afterEach)
- **@BeforeAll**: 모든 테스트 실행 전 한 번만 실행되는 메서드입니다. static이어야 하며, 주로 globalSetUp()으로 명명합니다. (JS/TS: beforeAll)
- **@AfterAll**: 모든 테스트 실행 후 한 번만 실행되는 메서드입니다. static이어야 하며, 주로 globalTearDown()으로 명명합니다. (JS/TS: afterAll)
- **@Disabled**: 해당 테스트를 임시로 비활성화할 때 사용합니다. (JS/TS: test.skip(), it.skip())

#### 예시 코드 (주석 포함)
```java
// JUnit 5의 대표적 테스트 어노테이션 관례 예시
@BeforeAll
static void globalSetUp() {
    // 전체 테스트 시작 전 1회 실행
}

@BeforeEach
void setUp() {
    // 각 테스트 실행 전 준비 코드
}

@Test
void testAssertions() {
    assertEquals(1, 1); // 값이 같은지 확인
    assertTrue(true); // true인지 확인
    assertFalse(false); // false인지 확인
    assertNull(null); // null인지 확인
    assertNotNull(new Object()); // null이 아닌지 확인
    assertThrows(IllegalArgumentException.class, () -> {
        throw new IllegalArgumentException(); // 예외 발생 확인
    });
}

@AfterEach
void tearDown() {
    // 각 테스트 실행 후 정리 코드
}

@AfterAll
static void globalTearDown() {
    // 전체 테스트 종료 후 1회 실행
}

@Disabled("임시 비활성화 예시")
@Test
void testDisabled() {
    // 이 테스트는 실행되지 않음
}
```

- **관례 설명:**
    - JUnit에서는 setUp, tearDown, globalSetUp, globalTearDown 등 명칭을 관례적으로 사용합니다.
    - JS/TS(Jest/Mocha)에서는 beforeEach, afterEach, beforeAll, afterAll 등 함수 기반으로 준비/정리 코드를 작성하며, 함수명은 자유하지만 setup/teardown 등 명칭이 자주 쓰입니다.

### 2.2 JUnit Assertions 주요 메서드
- `assertEquals(a, b)`: a와 b가 같은지 확인
- `assertTrue(condition)`: 조건이 true인지 확인
- `assertFalse(condition)`: 조건이 false인지 확인
- `assertNull(obj)`: 객체가 null인지 확인
- `assertNotNull(obj)`: 객체가 null이 아닌지 확인
- `assertThrows(Exception.class, () -> { ... })`: 예외 발생 확인

- **Node/Express/TS 비교:** Jest의 `expect().toBe()`, `toEqual()`, `toThrow()` 등과 유사

---

## 3. 실무 적용 및 팁
- TDD/BDD는 프로젝트 상황에 맞게 선택
- Assertions는 테스트의 핵심, 다양한 조건을 검증할 수 있음
- JS/TS도 expect/assert 등 다양한 assertion 메서드 제공

---

> **Tip:**
> - 테스트 방법론은 팀/프로젝트 상황에 맞게 유연하게 적용
> - Assertion 메서드는 테스트 코드의 가독성과 신뢰성을 높임
