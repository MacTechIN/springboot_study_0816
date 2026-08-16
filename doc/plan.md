# 스프링부트 3 프로젝트 만들기 - 12단계 & 13단계 상세 구현 계획 (서버 재시작 및 index.html 서빙 검증)

## 1. 개요 및 접근 방식 (Approach)
교재 12단계 및 13단계 지침에 의거하여, 최신 `index.html`이 적용된 상태로 스프링 부트 웹 서버(`./gradlew bootRun`)를 재가동하고, `http://localhost:8080` 접속 시 404 Whitelabel Error 대신 `index.html` 내용이 정상 렌더링되는지 수신 검증 후 사용자가 직접 테스트할 수 있도록 서버 가동을 유지합니다.

## 2. 구동 및 접속 구조 (Server & Access Structure)
```
SpringBoot_service/
├── settings.gradle
├── build.gradle
├── doc/
│   ├── research.md           # 12~13단계 분석 포함
│   └── plan.md               # 12~13단계 계획서
└── src/
    ├── main/
    │   ├── java/
    │   │   └── me/
    │   │       └── shinsunyoung/
    │   │           └── springbootdeveloper/
    │   │               └── SpringBootDeveloperApplication.java
    │   └── resources/
    │       ├── application.yml
    │       └── static/
    │           └── index.html   # <p>index.html</p> 반영 완료
```

## 3. 사용자 접속 가이드
- **접속 URL**: `http://localhost:8080`
- **기대 결과**: 브라우저 화면에 `index.html` 텍스트 정상 출력 (HTTP 200 OK)
- **페이징 처리 원칙**: 추후 컨트롤러/서비스 레벨의 리스트 조회 작성 시 오프셋 페이징 대신 **인풋 페이징 / 커서 기반 페이징 (Cursor/Input-based Paging)** 을 적용함.

## 4. 수행 커맨드 (Command Snippets)
```bash
./gradlew bootRun
curl -i http://localhost:8080
```

## 5. 트레이드오프 (Trade-offs)
1. **정적 자원 캐싱 및 라이브 서버 구동**:
   - `bootRun` 구동으로 `classpath:/static/index.html`이 내장 톰캣 웹 서버 루트 `/` 경로로 바인딩되어 바로 서빙됨을 증명.

## 6. 진행 상태 (Tasks)
- [x] `./gradlew bootRun` 서버 재가동
- [x] `http://localhost:8080` GET 호출 시 HTTP 200 OK 및 `index.html` 내용 수신 검증
- [x] Git 버전 `v1.0.10` 커밋 및 GitHub 원격 푸시 업데이트
