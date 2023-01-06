# 스프링 웹 개발 기초
# 📌목차
- [정적 컨텐츠](#정적-컨텐츠)
- [mvc와 템플릿 엔진](#mvc와-템플릿-엔진)
- [api](#api)

<br>

## ✅정적 컨텐츠
- 스프링부트 정적 컨텐츠 기능
- 파일을 그대로 웹 브라우저에 전달
- http://localhost:8080/hello-static.html

<br>

**정적 컨텐츠 이미지**
![김영한 스프링 입문 - 2강(정적 컨텐츠)](https://user-images.githubusercontent.com/79316402/211048100-5610ace2-2bc0-4b48-9acd-8eb4cb52636f.png)

<br>

## ✅mvc와 템플릿 엔진
- 서버에서 html을 바꿔서 전달, 템플릿 엔진을 MVC 방식으로 나눠서 view를 템플릿 엔진으로 html을 렌더링해서 클라이언트에게 전달해주는 방식이다.
- MVC: Model, View, Controller

<br>

**Controller**
```java
@Controller
public class HelloController {
		
		@GetMapping("hello-mvc")
    public String helloMvc(@RequestParam(value = "name", required = false) String name, Model model) {
        model.addAttribute("name", name);
        return "hello-template";
    }
}
```

<br>

**View**
```html
<html xmlns:th="http://www.thymeleaf.org">
<body>
<p th:text="'hello ' + ${name}">hello! empty</p>
</body>
</html>
```

<br>

**실행**

- http://localhost:8080/hello-mvc?name=spring

<br>

**MVC, 템플릿 엔진 이미지**
![김영한 스프링 입문 - 2강(MVC, 템플릿 엔진 이미지)](https://user-images.githubusercontent.com/79316402/211049573-92a6c4d1-f760-4bab-b30e-f6673b34e9e3.png)

<br>

## ✅api
- JSON 데이터 포맷으로 클라이언트에게 데이터를 전달, Vue, React 등과 함께 사용, 서버끼리 통신할 때 사용
- 간단하게 말해서 HTTP Response Body에 객체를 반환하는 것!

<br>

**@ResponseBody 문자 반환**
```java
@Controller
public class HelloController {
		
		@GetMapping("hello-string")
    @ResponseBody // http의 응답 body 부분에 이 데이터를 직접 내려준다는 의미
    public String helloString(@RequestParam("name") String name) {
        return "hello" + name; // "hello spring"
    }
}
```
- `@RequestBody` 를 사용하면 뷰 리졸버(`viewResolver`) 를 사용하지 않음
- 대신에 HTTP의 BODY에 문자 내용을 직접 반환(HTML BODY TAG를 말하는 것이 아님)

<br>

**실행**
- `http://localhost:8080/hello-string?name=spring`

<br>

**@ResponseBody 객체 반환**
```java
@Controller
public class HelloController {
		
		@GetMapping("hello-api")
    @ResponseBody
    public Hello helloApi(@RequestParam("name") String name) {
        Hello hello = new Hello();
        hello.setName(name);
        return hello;
    }

    static class Hello {
        private String name;

        // getter와 setter는 java bean 규약이라고 한다. property 접근 방식
        public String getName() {
            return name;
        }

        public void setName(String name) {
            this.name = name;
        }
    }
}
```
- @ResponseBody 를 사용하고, 객체를 반환하면 객체가 JSON으로 변환됨

<br>

**실행**
- `http://localhost:8080/hello-api?name=spring`

<br>

**@ResponseBody 사용 원리**
![김영한 스프링 입문 - 2강(API)](https://user-images.githubusercontent.com/79316402/211052521-03b34a31-7077-4cb0-9a05-831752774563.png)
- `@ResponseBody` 를 사용
    - HTTP의 BODY에 문자 내용을 직접 반환
    - `viewResolver` 대신에 `HttpMessageConverter` 가 동작
    - 기본 문자처리: `StringHttpMessageConverter` → String
    - 기본 객체처리: `MappingJackson2HttpMessageConverter` → JSON
    - byte 처리 등등 기타 여러 HttpMessageConverter가 기본으로 등록되어 있음

<br>

> 참고: 클라이언트의 HTTP Accept 헤더와 서버의 컨트롤러 반환 타입 정보 둘을 조합해서 `HttpMessageConverter` 가 선택된다. 더 자세한 내용은 스프링 MVC 강의에서 설명한다.
> 

→ 어찌됐든 JSON을 쓴다. 객체는 무조건 JSON으로 반환
