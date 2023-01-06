# 프로젝트 환경설정
## 📌목차

- [프로젝트 생성](#프로젝트-생성)
- [라이브러리 살펴보기](#라이브러리-살펴보기)
- [view 환경설정](#view-환경설정)
- [빌드하고 실행하기](#빌드하고-실행하기)

<br>

## ✅프로젝트 생성
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

__build.gradle__

- start.spring.io에서 설정 파일까지 제공

<br>

## ✅라이브러리 살펴보기
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

<br>

## ✅view 환경설정
### Welcome Page 만들기

- `resource/templates/index.html`
```html
<!DOCTYPE HTML>
<html>
<head>
    <title>Hello</title>
    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
</head>
<body>
Hello
<a href="/hello">hello</a>
</body>
</html>
```
- 스프링 부트가 제공하는 Welcome Page 기능
    - `static/index.html`을 올려두면 Welcome Page 기능을 제공한다.
    - 이 방법은 정적 페이지를 구성한 파일을 그대로 던져주는 방식이다.
    - [https://docs.spring.io/spring-boot/docs/2.3.1.RELEASE/reference/html/spring-boot-features.html#boot-features-spring-mvc-template-engines](https://docs.spring.io/spring-boot/docs/2.3.1.RELEASE/reference/html/spring-boot-features.html#boot-features-spring-mvc-template-engines) (2.7.7 쪽은 같은 내용의 컨텐츠를 찾지 못했다.)
    - **이것을 사용해보는 것이 좋은 이유는 spring 사이트의 매뉴얼에서 필요한 것을 검색해서 사용할 줄 알아야 하기 때문이다!**

<br>

### thymeleaf 템플릿 엔진

- thymeleaf 공식 사이트: [https://www.thymeleaf.org/](https://www.thymeleaf.org/)
- 스프링 공식 튜토리얼: [https://spring.io/guides/gs/serving-web-content/](https://spring.io/guides/gs/serving-web-content/)
- 스프링부트 매뉴얼: [https://docs.spring.io/spring-boot/docs/2.3.1.RELEASE/reference/html/spring-boot-features.html#boot-features-spring-mvc-template-engines](https://docs.spring.io/spring-boot/docs/2.3.1.RELEASE/reference/html/spring-boot-features.html#boot-features-spring-mvc-template-engines)
- 스프링부트의 Template Engines 중 하나가 thymeleaf이다.

<br>

**thymeleaf 템플릿 엔진 동작 확인**

- 실행: http://localhost:8080/hello

<br>

**동작 환경**
![김영한 스프링 입문 - 1강](https://user-images.githubusercontent.com/79316402/211053311-da9dc881-1e57-4581-8227-41f9c8cf03d3.png)


- 컨트롤러에서 리턴 값으로 문자를 반환하면 뷰 리졸버(`viewResolver`)가 화면을 찾아서 처리한다.
    - 스프링부트 템플릿 엔진 기본 viewName 매핑
    - `resources:templates/` + {viewName} + `.html`

> 참고: `spring-boot-devtools` 라이브러리를 추가하면, `html` 파일을 컴파일만 해주면 서버 재시작 없이 View 파일 변경이 가능하다. 
인텔리J 컴파일 방법: 메뉴 build → Recompile

<br>

## ✅빌드하고 실행하기
**콘솔로 이동(directory는 프로젝트 폴더로 이동한다.)**
<br>
<br>
<img width="471" alt="image" src="https://user-images.githubusercontent.com/79316402/210867069-df260033-a9fa-46ea-a167-90e423dce23a.png">

1. `./gradlew build`
2. `cd build/libs`
3. `java -jar hello-spring-0.0.1-SNAPSHOT.jar`
4. 실행 확인
