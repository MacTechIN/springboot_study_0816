# 스프링부트 3 프로젝트 만들기 - 3.0 단원 프로젝트 구조 설명서 HTML 생성 상세 계획

## 1. 개요 및 접근 방식 (Approach)
교재 3.0 단원 "프로젝트 구조" 그림 및 텍스트 명세에 맞춰 Java 스프링 부트 계층형 아키텍처(Web Browser -> TestController -> TestService -> Member / MemberRepository -> H2 Database, 그리고 build.gradle 핵심 도구 JPA, Lombok, H2)를 시각적이고 직관적으로 이해할 수 있는 프리미엄 인터랙티브 HTML 설명서 문서를 생성합니다.

HTML 설명서는 두 경로에 생성하여 각각의 목적에 맞게 활용합니다:
1. `src/main/resources/static/architecture.html`: 스프링 부트 웹 서버 가동 시 `http://localhost:8080/architecture.html` 경로로 접속하여 직접 확인 가능하도록 서빙.
2. `doc/architecture_guide.html`: 프로젝트 기술 문서 저장용.

## 2. 코드 및 파일 구조 (File Structure)
```
SpringBoot_service/
├── settings.gradle
├── build.gradle
├── doc/
│   ├── research.md               # 3.0 단원 분석 포함
│   ├── plan.md                   # 3.0 단원 구현 계획서
│   └── architecture_guide.html   # [3.0 단원 대상] 프로젝트 구조 설명서 HTML
└── src/
    ├── main/
    │   ├── java/
    │   └── resources/
    │       └── static/
    │           ├── index.html
    │           └── architecture.html  # [3.0 단원 대상] 웹 상 접속 가능한 설명서 HTML
```

## 3. HTML 설명서 디자인 및 UI/UX 스펙
- **Core Stack**: HTML5, Vanilla CSS, Vanilla JavaScript (외부 프레임워크 최소화로 빠른 로딩)
- **Visual Diagram**: CSS Grid / Flexbox 기반 아키텍처 흐름 카드 시각화 (Web Browser -> Controller -> Service -> Repository/Entity -> H2 DB)
- **Interactive Component**:
  - 각 레이어(Controller, Service, Repository, Entity, DB, Build Tools) 선택 시 상세 역할과 예제 스니펫을 실시간 전환하여 보여주는 카테고리 카드/탭 인터랙션
  - `TestController` <-> `TestService` 간 역할 분담(어떤 요청인지 판단 vs 실제 작업 실행) 명확히 대비
  - JPA, Lombok, H2 의존성 라이브러리의 역할 시각적 정리
- **Typography & Color**: Pretendard / System Font, Indigo/Slate 계열 Modern Harmony CSS 토큰 적용
- **페이징 처리 원칙**: 데이터베이스 레이어 서술 시 오프셋 페이징 대신 **인풋 페이징 / 커서 기반 페이징 (Cursor/Input-based Paging)** 을 적용하도록 기술 규정 수록.

## 4. 코드 스니펫 예시 (HTML Structure Snippet)

```html
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Spring Boot 3 프로젝트 구조 설명서 (Section 3.0)</title>
    <style>
        /* Modern Design Tokens */
        :root {
            --primary: #4f46e5;
            --primary-hover: #4338ca;
            --bg: #f8fafc;
            --card-bg: #ffffff;
            --text-main: #0f172a;
            --text-muted: #64748b;
            --border: #e2e8f0;
            --accent-blue: #3b82f6;
            --accent-green: #10b981;
        }
        /* CSS Layout & Interactions */
    </style>
</head>
<body>
    <!-- Header & Architecture Visual Diagram & Detailed Layer Cards -->
</body>
</html>
```

## 5. 트레이드오프 (Trade-offs)
1. **단일 파일 독립성 (Single-file HTML)**:
   - 외부 별도 CSS/JS 파일 없이 단일 HTML 파일 내에 Style과 Script를 내장하여, 오프라인 환경이나 스프링 부트 정적 리소스 서빙 시 종속성 없이 100% 즉시 렌더링되도록 구현.

## 6. 진행 상태 (Tasks)
- [x] `src/main/resources/static/architecture.html` 및 `doc/architecture_guide.html` 생성
- [x] `./gradlew test` 수행으로 빌드 및 정적 자원 패키징 검증
- [x] Git 버전 `v1.1.0` 커밋 및 GitHub 원격 푸시 업데이트
