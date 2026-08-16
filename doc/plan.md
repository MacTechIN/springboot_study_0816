# 스프링부트 3 프로젝트 만들기 - 2단계 상세 구현 계획 (build.gradle 수정)

## 1. 개요 및 접근 방식 (Approach)
교재 02단계의 `build.gradle` 명세 이미지에 맞춰 `build.gradle` 파일을 정확하게 수정/업데이트합니다.

핵심 수정사항:
- `dependency-management` 플러그인 버전을 `1.1.0`으로 맞춤
- `version`을 `'1.0'`으로 명시
- `sourceCompatibility = '17'` 자바 17 컴파일 버전 지정
- `spring-boot-starter-web` 및 `spring-boot-starter-test` 의존성 확인

## 2. 코드 구조 상세 설명 (Code Structure)
```
SpringBoot_service/
├── settings.gradle           # rootProject.name = 'springboot-developer'
├── build.gradle              # 02단계 교재 명세(Spring Boot 3.2.0, dependency-management 1.1.0, version 1.0) 반영
├── doc/
│   ├── research.md           # 코드 리서치 보고서
│   └── plan.md               # 상세 구현 계획서
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
- **프로젝트 명칭**: `springboot-developer`
- **그룹명 (Group)**: `me.shinsunyoung`
- **버전 (Version)**: `1.0`
- **Java 컴파일 버전**: `17`
- **페이징 처리 원칙**: 데이터 조회 API 구현 시 오프셋 페이징 대신 **인풋 페이징 / 커서 기반 페이징 (Cursor/Input-based Paging)** 방식으로 일관되게 지원함.

## 4. 파일 경로 및 코드 스니펫 (Code Snippets)

### [MODIFY] [build.gradle](file:///Users/sl/Workspace/Java/SpringBoot_service/build.gradle)
```groovy
plugins {
    id 'java'
    id 'org.springframework.boot' version '3.2.0'
    id 'io.spring.dependency-management' version '1.1.0'
}

group 'me.shinsunyoung'
version '1.0'
sourceCompatibility = '17'

repositories {
    mavenCentral()
}

dependencies {
    implementation 'org.springframework.boot:spring-boot-starter-web'
    testImplementation 'org.springframework.boot:spring-boot-starter-test'
}

test {
    useJUnitPlatform()
}
```

## 5. 트레이드오프 (Trade-offs)
1. **dependency-management 버전 조정 (1.1.4 -> 1.1.0)**:
   - 교재 이미지의 `1.1.0` 버전에 정확히 맞춰 교재 실습 코드 및 동작과 100% 동일한 환경을 유지합니다.
2. **version 표기 변경 ('1.0-SNAPSHOT' -> '1.0')**:
   - 릴리즈 스펙에 준하는 단정적 버전 표기로 교재 가이드라인 준수.

## 6. 진행 상태 (Tasks)
- [x] 02단계 `build.gradle` 수정 적용 (dependency-management 1.1.0, version '1.0', sourceCompatibility = '17')
- [x] Gradle 빌드 및 `./gradlew test` 검증 수행
- [x] Git 버전 `v1.0.1` 업데이트 및 커밋
