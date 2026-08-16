# 스프링부트 3 프로젝트 만들기 - 4단계 상세 구현 계획 (패키지 구조 구성)

## 1. 개요 및 접근 방식 (Approach)
교재 04단계의 "미리 생성된 패키지 `me.shinsunyoung` 하위에 새 패키지 생성" 지침에 따라, `src/main/java/me/shinsunyoung/springbootdeveloper` 패키지 디렉토리 구조를 명확히 정립하고 필요한 하위 패키지(예: `controller`, `domain`, `service`, `repository`) 구성 기틀을 마련합니다.

## 2. 코드 구조 상세 설명 (Code Structure)
```
SpringBoot_service/
├── settings.gradle
├── build.gradle
├── doc/
│   ├── research.md           # 04단계 분석 포함
│   └── plan.md               # 04단계 구현 계획서
└── src/
    ├── main/
    │   ├── java/
    │   │   └── me/
    │   │       └── shinsunyoung/
    │   │           └── springbootdeveloper/
    │   │               └── SpringBootDeveloperApplication.java
    │   └── resources/
    │       └── application.yml
    └── test/
        └── java/
            └── me/
                └── shinsunyoung/
                    └── springbootdeveloper/
                        └── SpringBootDeveloperApplicationTests.java
```

## 3. 기능별 명칭 및 페이징 방식 정의
- **그룹/루트 패키지**: `me.shinsunyoung`
- **애플리케이션 패키지**: `me.shinsunyoung.springbootdeveloper`
- **페이징 처리 원칙**: 게시물/리스트 API 설계 시 오프셋 페이징 대신 **인풋 페이징 / 커서 기반 페이징 (Cursor/Input-based Paging)** 을 적용하여 고성능 페이징 구조 설계.

## 4. 파일 경로 및 패키지 구조 스니펫 (Code Snippets)

### [NEW / VERIFY] `src/main/java/me/shinsunyoung/springbootdeveloper/SpringBootDeveloperApplication.java`
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

## 5. 트레이드오프 (Trade-offs)
1. **단일 레벨 패키지 vs 계층별 패키지 구성**:
   - `me.shinsunyoung` 하위에 `springbootdeveloper` 기본 패키지를 명확히 둠으로써 Spring Boot의 Component Scan(`@SpringBootApplication`) 범위가 루트 패키지 및 모든 하위 서브 패키지를 자동으로 커버하도록 구성.

## 6. 진행 상태 (Tasks)
- [x] `src/main/java/me/shinsunyoung/springbootdeveloper` 패키지 검증 및 정립
- [x] `./gradlew test` 로 정상 패키지 및 컴파일 검증
- [x] Git 버전 `v1.0.3` 업데이트 및 커밋
