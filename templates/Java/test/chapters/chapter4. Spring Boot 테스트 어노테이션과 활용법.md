# chapter4. Spring Boot 테스트 어노테이션과 활용법

## 개요
이 챕터에서는 Spring Boot에서 자주 사용하는 테스트 어노테이션(@Test, @Autowired, @Disabled 등)과 그 활용법, 그리고 Node.js/Express, JS/TS의 유사 개념과 비교를 다룹니다.

---

## 1. 주요 테스트 어노테이션

### 1.1 @Test
- **설명:** 테스트 메서드임을 표시
- **예시:**
```java
@Test // 이 메서드는 테스트로 실행됨
void testMethod() {
    // 테스트 코드 작성
}
```
- **Node/Express/TS 비교:** Jest의 `test()`, Mocha의 `it()`과 유사

### 1.2 @Autowired
- **설명:** 스프링 컨테이너에서 의존성 주입(DI) 받음
- **예시:**
```java
@Autowired // 테스트 클래스에 서비스 주입
private UserService userService;
```
- **Node/Express/TS 비교:** DI 라이브러리(awilix, typedi 등)에서의 의존성 주입과 유사

### 1.3 @Disabled
- **설명:** 해당 테스트를 임시로 비활성화
- **예시:**
```java
@Disabled("이유 설명")
@Test
void testDisabled() {
    // 이 테스트는 실행되지 않음
}
```
- **Node/Express/TS 비교:** Jest의 `test.skip()`, Mocha의 `it.skip()`과 유사

### 1.4 @SpringBootTest
- **설명:** 스프링 부트 전체 컨텍스트로 통합 테스트 실행
- **예시:**
```java
@SpringBootTest
class IntegrationTest {
    // 통합 테스트 코드
}
```
- **Node/Express/TS 비교:** Supertest 등으로 실제 서버 환경에서 테스트하는 것과 유사

### 1.5 @MockBean
- **설명:** 테스트에서 특정 빈(Bean)을 Mock 객체로 대체
- **예시:**
```java
@MockBean
private UserRepository userRepository;
```
- **Node/Express/TS 비교:** jest.mock(), sinon 등으로 의존성 Mocking

---

## 2. 실무 적용 예시
- 단위 테스트: @Test, @MockBean, @Autowired
- 통합 테스트: @SpringBootTest, @Autowired
- 슬라이스 테스트: @WebMvcTest, @DataJpaTest 등

---

## 3. 어노테이션 조합 예시
```java
@SpringBootTest // 통합 테스트 환경
class UserServiceTest {
    @Autowired // DI로 서비스 주입
    private UserService userService;

    @MockBean // Repository를 Mock으로 대체
    private UserRepository userRepository;

    @Test // 실제 테스트
    void testFindUser() {
        // given, when, then 패턴으로 테스트 작성
    }
}
```

---

## 4. Node.js/Express/TS와의 비교
- DI, Mocking, 테스트 스킵 등은 JS/TS에서도 동일하게 활용 가능
- 어노테이션 대신 함수 기반 API를 주로 사용

---

> **Tip:**
> - 테스트 어노테이션은 `src/test/java` 내 테스트 클래스에서 사용
> - JS/TS는 `describe`, `beforeEach`, `afterEach` 등 함수로 대체

