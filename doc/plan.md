# 스프링부트 3 프로젝트 만들기 - 3장 01단계 상세 구현 계획 (TestController 생성 및 GET /test 구현)

## 1. 개요 및 접근 방식 (Approach)
교재 01단계 지침에 따라 `src/main/java/me/shinsunyoung/springbootdeveloper/` 패키지 하위에 `TestController.java` 클래스를 생성하고, `@RestController` 및 `@GetMapping("/test")` 어노테이션을 사용하여 사용자가 `/test` GET 요청 시 `"Hello, world!"` 문자열을 반환하는 컨트롤러를 작성합니다.

## 2. 코드 및 디렉토리 구조 (Code Structure)
```
SpringBoot_service/
├── settings.gradle
├── build.gradle
├── doc/
│   ├── research.md               # 3장 01단계 분석 덧붙임
│   └── plan.md                   # 3장 01단계 구현 계획서
└── src/
    ├── main/
    │   ├── java/
    │   │   └── me/
    │   │       └── shinsunyoung/
    │   │           └── springbootdeveloper/
    │   │               ├── SpringBootDeveloperApplication.java
    │   │               └── TestController.java    # [3장 01단계 대상 완료]
    │   └── resources/
    │       ├── application.yml
    │       └── static/
    │           ├── index.html
    │           └── architecture.html
```

## 3. 기능별 명칭 및 페이징 처리 방침
- **클래스명**: `TestController`
- **URL 엔드포인트**: `GET /test`
- **반환 데이터**: `"Hello, world!"` (String)
- **페이징 처리 원칙**: 추후 서비스 및 리포지토리 레이어와 연동하여 리스트 데이터를 조회하는 컨트롤러 확장 시 오프셋 페이징 대신 **인풋 페이징 / 커서 기반 페이징 (Cursor/Input-based Paging)** 을 적용함.

## 4. 파일 경로 및 소스 코드 스니펫 (Code Snippet)

### [NEW] `src/main/java/me/shinsunyoung/springbootdeveloper/TestController.java`
```java
package me.shinsunyoung.springbootdeveloper;

import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RestController;

@RestController
public class TestController {

    @GetMapping("/test")
    public String test() {
        return "Hello, world!";
    }
}
```

## 5. 트레이드오프 (Trade-offs)
1. **`@RestController` 어노테이션 사용**:
   - `@Controller` + `@ResponseBody`가 결합된 어노테이션으로, 뷰(View) 템플릿(HTML)을 반환하는 대신 JSON이나 문자열 응답 데이터를 직접 반환하여 RESTful API 구축에 가장 적합함.

## 6. 진행 상태 (Tasks)
- [x] `src/main/java/me/shinsunyoung/springbootdeveloper/TestController.java` 파일 생성 및 소스 작성
- [x] `./gradlew test` 수행으로 컴파일 및 단위 테스트 통과 검증
- [x] Git 버전 `v1.2.0` 커밋 및 GitHub 원격 푸시 업데이트
