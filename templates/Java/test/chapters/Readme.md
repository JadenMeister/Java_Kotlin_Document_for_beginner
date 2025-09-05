# Java 테스트 챕터 안내 (test/chapters/Readme.md)

## 개요
이 디렉토리는 자바(Spring Boot) 기반 웹 개발자를 위한 테스트 이론, 실무 적용, 생태계별 관례, 그리고 Node.js/Express/JS/TS와의 비교까지 초보자도 쉽게 이해할 수 있도록 정리한 마크다운 문서 모음입니다.

---

## 디렉토리 구조 및 목적
- **test/chapters/**
  - 자바(Spring Boot) 테스트에 관한 실무 중심의 이론, 방법론, 코드 예시, 관례, 비교 등 각종 챕터별 마크다운 문서가 위치합니다.
  - 각 챕터는 실제 현업에서 자주 쓰이는 테스트 패턴, 어노테이션, 방법론, 실무 팁, Node/Express/TS와의 비교, 그리고 한 줄 한 줄 주석과 상세 설명을 포함합니다.

---

## 포함된 주요 내용
- [chapter1. 자바 테스트의 기본 개념과 종류 (단위_통합_슬라이스).md](chapter1.%20%EC%9E%90%EB%B0%94%20%ED%85%8C%EC%8A%A4%ED%8A%B8%EC%9D%98%20%EA%B8%B0%EB%B3%B8%20%EA%B0%9C%EB%85%90%EA%B3%BC%20%EC%A2%85%EB%A5%98%20(%EB%8B%A8%EC%9C%84_%ED%86%B5%ED%95%A9_%EC%8A%AC%EB%9D%BC%EC%9D%B4%EC%8A%A4).md)
  - 단위/통합/슬라이스 테스트의 개념, 목적, 실무 적용, Node/Express/TS와의 비교, 표준 디렉토리 구조 등
- [chapter2. 객체지향 5원칙과 테스트 설계.md](chapter2.%20%EA%B0%9D%EC%B2%B4%EC%A7%80%ED%96%A5%205%EC%9B%90%EC%B9%99%EA%B3%BC%20%ED%85%8C%EC%8A%A4%ED%8A%B8%20%EC%84%A4%EA%B3%84.md)
  - SOLID 원칙별 설명, 테스트 설계와의 관계, Mock/Stub/Spy 활용, Node/Express/TS와의 비교
- [chapter3. JUnit 4와 5의 차이 및 주요 변경점.md](chapter3.%20JUnit%204%EC%99%80%205%EC%9D%98%20%EC%B0%A8%EC%9D%B4%20%EB%B0%8F%20%EC%A3%BC%EC%9A%94%20%EB%B3%80%EA%B2%BD%EC%A0%90.md)
  - JUnit 4/5 구조, 어노테이션 변경점, 실무 적용 팁, Jest/Mocha와의 비교, 예시 코드
- [chapter4. Spring Boot 테스트 어노테이션과 활용법.md](chapter4.%20Spring%20Boot%20%ED%85%8C%EC%8A%A4%ED%8A%B8%20%EC%96%B4%EB%85%B8%ED%85%8C%EC%9D%B4%EC%85%98%EA%B3%BC%20%ED%99%9C%EC%9A%A9%EB%B2%95.md)
  - @Test, @Autowired, @Disabled, @SpringBootTest, @MockBean 등 주요 어노테이션 설명, 실무 예시, Node/Express/TS와의 비교
- [chapter5. 테스트 방법론과 Assertions 메서드 설명.md](chapter5.%20%ED%85%8C%EC%8A%A4%ED%8A%B8%20%EB%B0%A9%EB%B2%95%EB%A1%A0%EA%B3%BC%20Assertions%20%EB%A9%94%EC%84%9C%EB%93%9C%20%EC%84%A4%EB%AA%85.md)
  - TDD, BDD(Given/When/Then), ATDD, E2E 등 방법론별 상세 설명, 실무 적용, 자바/JS/TS 생태계 관례, Assertions 메서드, 예시 코드

---

## 활용 방법
- 각 챕터는 독립적으로 읽을 수 있으며, 자바(Spring Boot) 테스트의 기초부터 실무 적용, Node/Express/TS와의 비교까지 단계별로 학습할 수 있습니다.
- 실무에서 자주 마주치는 테스트 시나리오, 어노테이션, 관례, 코드 작성법, 협업 팁까지 모두 포함되어 있어, 초보자도 실전에서 바로 활용할 수 있습니다.
- 각 문서는 마크다운 문법 오류 없이 작성되었으며, mermaid 다이어그램 등 시각적 자료도 포함되어 있습니다.

---

## 참고 및 추가 안내
- 본 디렉토리의 모든 문서는 최신 자바(Spring Boot 3.x 기준) 및 Node.js/Express/Jest/Cucumber 등 최신 생태계 기준으로 작성되었습니다.
- 각 챕터별로 실무에서 자주 쓰이는 관례, 코드 스타일, 협업 팁, 그리고 JS/TS와의 비교까지 꼼꼼하게 안내합니다.
- 추가로 궁금한 점이나 보강이 필요한 내용이 있으면 언제든 문의해 주세요.
