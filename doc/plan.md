# 스프링부트 3 프로젝트 만들기 - 5단계 상세 구현 계획 (패키지 명세 규칙 me.shinsunyoung.springbootdeveloper 적용)

## 1. 개요 및 접근 방식 (Approach)
교재 05단계의 패키지命名 규칙 `<그룹_이름>.<프로젝트_이름>` 명세에 의거하여, 패키지명을 `me.shinsunyoung.springbootdeveloper`로 확정하고 소스 디렉토리(`src/main/java`) 및 테스트 디렉토리(`src/test/java`) 양쪽에 완벽히 정립되었는지 재검증 및 구성합니다.

## 2. 코드 구조 상세 설명 (Code Structure)
```
SpringBoot_service/
├── settings.gradle
├── build.gradle
├── doc/
│   ├── research.md           # 05단계 분석 덧붙임
│   └── plan.md               # 05단계 계획서
└── src/
    ├── main/
    │   ├── java/
    │   │   └── me/
    │   │       └── shinsunyoung/
    │   │           └── springbootdeveloper/   # <그룹_이름>.<프로젝트_이름> 패키지
    │   │               └── SpringBootDeveloperApplication.java
    │   └── resources/
    │       └── application.yml
    └── test/
        └── java/
            └── me/
                └── shinsunyoung/
                    └── springbootdeveloper/   # 테스트 대응 패키지
                        └── SpringBootDeveloperApplicationTests.java
```

## 3. 기능별 명칭 및 페이징 방식 정의
- **그룹 이름**: `me.shinsunyoung`
- **프로젝트 이름**: `springbootdeveloper`
- **전체 패키지 명칭**: `me.shinsunyoung.springbootdeveloper`
- **페이징 처리 원칙**: 데이터를 다루는 컨트롤러/서비스 개발 시 오프셋 페이징 대신 **인풋 페이징 / 커서 기반 페이징 (Cursor/Input-based Paging)** 을 적용함.

## 4. 파일 경로 및 패키지 구조 스니펫 (Code Snippets)

### 소스 패키지 메인 클래스 [VERIFY]
`src/main/java/me/shinsunyoung/springbootdeveloper/SpringBootDeveloperApplication.java`
```java
package me.shinsunyoung.springbootdeveloper;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;

@SpringBootApplication
public class SpringBootDeveloperApplication {
    public static void main(String[] args) {
        SpringApplication.run(SpringBootDeveloperApplication.class, args);
    }
}
```

### 테스트 패키지 메인 테스트 클래스 [VERIFY]
`src/test/java/me/shinsunyoung/springbootdeveloper/SpringBootDeveloperApplicationTests.java`
```java
package me.shinsunyoung.springbootdeveloper;

import org.junit.jupiter.api.Test;
import org.springframework.boot.test.context.SpringBootTest;

@SpringBootTest
class SpringBootDeveloperApplicationTests {
    @Test
    void contextLoads() {
    }
}
```

## 5. 트레이드오프 (Trade-offs)
1. **패키지 명명 규칙 엄수**:
   - `<그룹_이름>.<프로젝트_이름>` 명세(`me.shinsunyoung.springbootdeveloper`)를 철저히 지킴으로써 교재 이후 단원의 클래스 생성(컨트롤러, 엔티티, DTO 등) 시 발생할 수 있는 Import 에러 및 패키지 불일치를 사전에 예방.

## 6. 진행 상태 (Tasks)
- [x] `me.shinsunyoung.springbootdeveloper` 명세 규칙 충족 여부 검증
- [x] `./gradlew test` 수행을 통한 컴파일 및 100% 매칭 검증
- [x] Git 버전 `v1.0.4` 커밋 업데이트
