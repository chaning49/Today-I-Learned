# 프로젝트 환경설정(작성중...)
## 목차

- [프로젝트 생성](#프로젝트-생성)
- [라이브러리 살펴보기](#라이브러리-살펴보기)
- View 환경설정
- 빌드하고 실행하기

### ✅ 프로젝트 생성
__사전 준비물__

- Java 11
- IDE: IntelliJ
- 스프링 부트 스타터 사이트에서 스프링 프로젝트 생성
- IntelliJ ultimate를 사용한다면 IDE에서 생성 가능
- 프로젝트 선택
    - Project: Gradle Project → 필요한 라이브러리를 땡겨와서 라이프 사이클까지 관리해주는 툴(gradle, maven)
    - Spring Boot: 23.1.4 기준 - 2.7.7(강의는 2.3.x)
    - Language: Java
    - Packaging: Jar
    - Java: 11
- Project Metadata
    - GroupId: 보통 기업 이름을 적어준다.
    - artifact: 빌드되어 나올 때의 결과물
- Dependencies: Spring boot 기반의 라이브러리를 추가하여 사용
    - Spring Web: web 프로젝트를 위해 사용
    - Thymeleaf: html을 만들어주는 템플릿 엔진

### build.gradle

- start.spring.io에서 설정 파일까지 제공
### ✅ 라이브러리 살펴보기
> Gradle은 의존 관계가 있는 라이브러리를 함께 다운로드 한다.
> 
- 특정 라이브러리를 땡겨오면 그 라이브러리에서 필요한 다른 라이브러리를 함께 가지고 온다. → 의존 관계로 엮인 라이브러리를 모두 땡겨오는 것이다.

**스프링 부트 라이브러리**

- spring-boot-starter-web
    - spring-boot-starter-tomcat: 톰캣(웹서버)
    - spring-boot-webmvc: 스프링 웹 MVC
- spring-boot-starter-thymeleaf: 타임리프 템플릿 엔진(View)
- spring-boot-starter(공통): 스프링 부트 + 스프링 코어 + 로깅
    - spring-boot
        - spring-core
    - spring-boot-starter-logging
        - logback, slf4j

**테스트 라이브러리**

- spring-boot-starter-test
    - junit: 테스트 프레임워크
    - mockito: 목 라이브러리
    - assertj: 테스트 코드를 좀 더 편하게 작성할 수 있도록 도와주는 라이브러리
    - spring-test: 스프링 통합 테스트 지원
