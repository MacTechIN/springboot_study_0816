# 스프링부트 3 프로젝트 만들기 - 9단계 상세 구현 계획 (localhost:8080 접속 테스트 및 Whitelabel Error Page 검증)

## 1. 개요 및 접근 방식 (Approach)
교재 09단계 지침 및 사용자 요청("내가 접속해서 테스할수 있도록 진행")에 따라, `./gradlew bootRun` 서버 프로세스를 실시간 가동하여 사용자가 브라우저에서 `http://localhost:8080` 으로 접속할 수 있도록 서버 환경을 제공하고, `Whitelabel Error Page (type=Not Found, status=404)` 동작을 검증합니다.

## 2. 구동 및 접속 검증 구조 (Server & Access Verification Structure)
```
SpringBoot_service/
├── settings.gradle
├── build.gradle
├── doc/
│   ├── research.md           # 09단계 웹 접속 분석 덧붙임
│   └── plan.md               # 09단계 계획서
└── src/
    ├── main/
    │   ├── java/
    │   │   └── me/
    │   │       └── shinsunyoung/
    │   │           └── springbootdeveloper/
    │   │               └── SpringBootDeveloperApplication.java
    │   └── resources/
    │       └── application.yml
```

## 3. 사용자 접속 테스트 가이드
- **접속 URL**: `http://localhost:8080`
- **기대 결과**: `Whitelabel Error Page` 화면 및 `There was an unexpected error (type=Not Found, status=404).` 메시지 출력 (정상 동작)
- **페이징 처리 원칙**: 추후 API 개발 시 오프셋 페이징 대신 **인풋 페이징 / 커서 기반 페이징 (Cursor/Input-based Paging)** 방식으로 일관되게 적용함.

## 4. 수행 커맨드 (Command Snippets)
```bash
./gradlew bootRun
```

## 5. 트레이드오프 (Trade-offs)
1. **서버 유지 프로세스 구동**:
   - 사용자가 직접 브라우저로 접속해 볼 수 있도록 백그라운드 태스크로 웹 서버(Tomcat 8080) 프로세스를 지속 실행 상태로 둡니다.

## 6. 진행 상태 (Tasks)
- [x] `./gradlew bootRun` 실행을 통한 localhost:8080 수신 서버 가동
- [x] HTTP GET `http://localhost:8080` 404 Whitelabel 응답 검증
- [x] Git 버전 `v1.0.8` 커밋 및 GitHub 원격 푸시 업데이트
