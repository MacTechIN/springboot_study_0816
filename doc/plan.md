# 스프링부트 3 프로젝트 만들기 - 8단계 상세 구현 계획 (애플리케이션 구동 및 Started 로그 검증)

## 1. 개요 및 접근 방식 (Approach)
교재 08단계의 애플리케이션 실행 지침 [Run 'SpringBootDeveloperApplication.main()']에 의거하여, CLI 환경에서 `./gradlew bootRun` 명령을 통해 스프링 부트 3 애플리케이션을 구동하고 내장 Tomcat 웹서버(Port 8080) 시작 및 `Started SpringBootDeveloperApplication in ~ seconds` 구동 로그를 수집하여 완전성을 검증합니다.

## 2. 코드 및 구동 구조 상세 설명 (Application Run Structure)
```
SpringBoot_service/
├── settings.gradle
├── build.gradle
├── doc/
│   ├── research.md           # 08단계 분석 및 트러블슈팅 팁 포함
│   └── plan.md               # 08단계 계획서
└── src/
    ├── main/
    │   ├── java/
    │   │   └── me/
    │   │       └── shinsunyoung/
    │   │           └── springbootdeveloper/
    │   │               └── SpringBootDeveloperApplication.java   # 메인 실행 대상 클래스
    │   └── resources/
    │       └── application.yml
```

## 3. 기능별 명칭 및 구동 명령 정의
- **구동 클래스**: `SpringBootDeveloperApplication`
- **실행 명령**: `./gradlew bootRun`
- **구동 검증 로그 패턴**: `Started SpringBootDeveloperApplication in 2.597 seconds` (Tomcat 8080)
- **페이징 처리 원칙**: 향후 웹 컨트롤러 구동 시 오프셋 페이징 대신 **인풋 페이징 / 커서 기반 페이징 (Cursor/Input-based Paging)** 을 일관되게 지원하도록 구성.

## 4. 수행 명령어 (Command Snippets)
```bash
./gradlew bootRun
```

## 5. 트레이드오프 (Trade-offs)
1. **bootRun 실행 프로세스 제어**:
   - `bootRun`은 웹 서버를 계속 유지(Listen)하므로 백그라운드 태스크로 구동 후, 로그에서 `Started SpringBootDeveloperApplication` 메시지 확인 및 8080 포트 정상 수신 확인 후 정돈 처리함.
2. **IntelliJ 실행 오류 시 대처 (non-zero exit value 1)**:
   - `Settings > Build, Execution, Deployment > Gradle` 메뉴에서 `Build and run using` 및 `Run tests using` 설정을 `IntelliJ IDEA`로 변경.

## 6. 진행 상태 (Tasks)
- [x] `./gradlew bootRun` 구동을 통한 08단계 애플리케이션 시작 검증
- [x] `Started SpringBootDeveloperApplication in 2.597 seconds` 실행 성공 로그 확인
- [x] Git 버전 `v1.0.7` 커밋 및 GitHub 원격 푸시 업데이트
