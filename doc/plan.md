# 스프링부트 3 프로젝트 만들기 - 1단계 상세 구현 계획 (그림 명세 반영)

## 1. 개요 및 접근 방식 (Approach)
교재 그림의 프로젝트 구조(`springboot-developer`, group: `me.shinsunyoung`, version: `1.0-SNAPSHOT`)와 일치하도록 기본 그레이들 프로젝트 구조를 구축하고, 이를 **Spring Boot 3.x 기반 프로젝트** 설정으로 확장합니다.

스프링 부트 3은 Java 17 이상을 지원하며, 그림에 제시된 기초 Gradle 빌드 스크립트(`build.gradle`)에 Spring Boot 3 플러그인과 의존성을 적용합니다.

## 2. 코드 구조 상세 설명 (Code Structure)
```
SpringBoot_service/ (또는 springboot-developer)
├── settings.gradle           # rootProject.name = 'springboot-developer'
├── build.gradle              # me.shinsunyoung 그룹 및 Spring Boot 3 설정
├── doc/
│   ├── research.md           # 코드 리서치 보고서
│   └── plan.md               # 상세 구현 계획서
└── src/
    ├── main/
    │   ├── java/
    │   │   └── me/
    │   │       └── shinsunyoung/
    │   │           └── springbootdeveloper/
    │   │               └── SpringBootDeveloperApplication.java  # 스프링 부트 메인 클래스
    │   └── resources/
    │       └── application.yml                                  # 설정 파일
    └── test/
        └── java/
            └── me/
                └── shinsunyoung/
                    └── springbootdeveloper/
                        └── SpringBootDeveloperApplicationTests.java  # 테스트 클래스
```

## 3. 기능별 명칭 및 페이징 방식 정의
- **프로젝트 명칭**: `springboot-developer`
- **그룹명 (Group)**: `me.shinsunyoung`
- **버전 (Version)**: `1.0-SNAPSHOT`
- **패키지 명칭**: `me.shinsunyoung.springbootdeveloper`
- **메인 클래스 명칭**: `SpringBootDeveloperApplication`
- **페이징 처리 원칙**: 향후 API / 게시판 등 데이터 조회 기능 구현 시 오프셋 페이징 대신 **인풋(커서) 페이징 (Cursor/Input-based Paging)** 방식으로 설계/구현함.

## 4. 파일 경로 및 코드 스니펫 (Code Snippets)

### [NEW] `settings.gradle`
```groovy
rootProject.name = 'springboot-developer'
```

### [NEW] `build.gradle` (그림 기반 Spring Boot 3 적용 스니펫)
```groovy
plugins {
    id 'java'
    id 'org.springframework.boot' version '3.2.0'
    id 'io.spring.dependency-management' version '1.1.4'
}

group = 'me.shinsunyoung'
version = '1.0-SNAPSHOT'

java {
    sourceCompatibility = JavaVersion.VERSION_17
}

repositories {
    mavenCentral()
}

dependencies {
    implementation 'org.springframework.boot:spring-boot-starter-web'
    testImplementation 'org.springframework.boot:spring-boot-starter-test'
}

tasks.named('test') {
    useJUnitPlatform()
}
```

### [NEW] `src/main/java/me/shinsunyoung/springbootdeveloper/SpringBootDeveloperApplication.java`
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

### [NEW] `src/main/resources/application.yml`
```yaml
spring:
  application:
    name: springboot-developer
```

## 5. 트레이드오프 (Trade-offs)
1. **그룹명 및 패키지 구조 맞춤**:
   - 그림에 지정된 `me.shinsunyoung` 그룹명을 적용하여 교재 예제와의 100% 호환성을 유지합니다.
2. **Java 17 버전 호환성**:
   - Spring Boot 3.x 실행을 위해 Java 17 이상 호환 빌드 옵션을 적용합니다.
3. **인풋 페이징 채택**:
   - 단순 `OFFSET/LIMIT` 대신 커서 기반 인풋 페이징을 고려하여 추후 데이터베이스 엔티티 설계 시 인덱싱 가능한 ID 및 생성일자 필드를 사전에 고려합니다.

## 6. 진행 상태 (Tasks)
- [x] `settings.gradle` 생성 (rootProject.name = 'springboot-developer')
- [x] `build.gradle` 생성 (group 'me.shinsunyoung', Spring Boot 3 적용)
- [x] `src/main/java/me/shinsunyoung/springbootdeveloper/SpringBootDeveloperApplication.java` 생성
- [x] `src/main/resources/application.yml` 생성
- [x] `src/test/java/me/shinsunyoung/springbootdeveloper/SpringBootDeveloperApplicationTests.java` 생성
- [x] 빌드 검증 및 테스트 통과 확인
