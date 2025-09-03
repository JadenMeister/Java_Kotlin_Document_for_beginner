chapter4. 클래스와 객체지향 - MVC 패턴의 이해

---

# 개요

이 챕터에서는 코틀린의 클래스와 객체지향 개념을 Node.js, JavaScript, TypeScript와 비교하며, MVC 패턴의 기본 구조와 실무 적용 방법을 초보자 관점에서 설명합니다.

---

## 1. 클래스 선언 방식 비교

| 언어 | 클래스 선언 키워드 | 예시 |
|------|------------------|------|
| Kotlin | class | class User(val name: String, val age: Int) {...} |
| JavaScript | class | class User {...} |
| TypeScript | class (타입 명시) | class User {...} |

---

## 2. 코틀린 클래스 선언 예시

```kotlin
class User(val name: String, val age: Int) { // 클래스 선언, 주생성자에 필드 선언
    fun getName(): String { // getter 메서드
        return name
    }
    fun getAge(): Int { // getter 메서드
        return age
    }
}
```

- 클래스는 객체의 설계도 역할
- 필드, 생성자, 메서드로 구성
- 코틀린은 주생성자에서 필드 선언 가능

---

## 3. JavaScript/TypeScript 클래스 선언 예시

### JavaScript
```javascript
class User {
    constructor(name, age) {
        this.name = name;
        this.age = age;
    }
    getName() {
        return this.name;
    }
    getAge() {
        return this.age;
    }
}
```

### TypeScript
```typescript
class User {
    name: string;
    age: number;
    constructor(name: string, age: number) {
        this.name = name;
        this.age = age;
    }
    getName(): string {
        return this.name;
    }
    getAge(): number {
        return this.age;
    }
}
```

---

## 4. MVC 패턴의 기본 구조

- Model: 데이터와 비즈니스 로직 담당 (예: User 클래스)
- View: 사용자 인터페이스 담당 (코틀린에서는 Compose, JS/TS에서는 React 등)
- Controller: 사용자 요청 처리 및 Model-View 연결

```mermaid
flowchart TD
    A[사용자] --> B[Controller]
    B --> C[Model]
    C --> B
    B --> D[View]
    D --> A
```

---

## 5. 코틀린 MVC 패턴 예시 파일 위치 및 패턴

- Model: `/src/main/kotlin/com/example/demo/model/User.kt`
- Controller: `/src/main/kotlin/com/example/demo/controller/UserController.kt`
- View: `/src/main/resources/templates/user.html` (Spring Boot 기준)
- 본 문서 예제는 `/templates/Kotlin/chapters/chapter4. 클래스와 객체지향 - MVC 패턴의 이해.md`에 위치
- 이유: 역할별로 파일을 분리하여 유지보수와 확장에 용이함

---

## 6. 실무에서 클래스/객체지향 활용 팁

- 필드와 메서드는 접근제어자를 명확히 지정
- 생성자와 getter/setter를 활용해 데이터 보호
- MVC 패턴을 적용하면 코드 구조가 명확해지고 협업에 유리

---

## 7. 참고

- 코틀린 공식 문서: https://kotlinlang.org/docs/home.html
- 스프링부트 MVC 공식 문서: https://docs.spring.io/spring-framework/reference/web/webmvc.html

---

## 8. 다음 챕터 예고

- 스프링부트와 코틀린의 실무 적용

