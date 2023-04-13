# 스프링 빈과 의존관계
## 📌목차
- 컴포넌트 스캔과 자동 의존관계 설정
- 자바 코드로 직접 스프링 빈 등록하기

<br>

## ✅컴포넌트 스캔과 자동 의존관계 설정
회원 컨트롤러가 회원 서비스와 회원 리포지토리를 사용할 수 있게 의존관계를 준비하자.

*회원 컨트롤러 - 회원 서비스 - 회원 리포지토리 → 회원 컨트롤러는 회원서비스를 통해서 회원가입, 데이터를 조회할 수 있어야 한다. ⇒ 의존관계가 있다!*

<br>

**회원 컨트롤러에 의존관계 추가**
```java
package hello.hellospring.controller;

import hello.hellospring.service.MemberService;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Controller;

@Controller
public class MemberController {

    private final MemberService memberService;
    
    @Autowired
    public MemberController(MemberService memberService) {
        this.memberService = memberService;
    }
}
```
- 생성자에 `@Autowired` 가 있으면 스프링이 연관된 객체를 스프링 컨테이너에서 찾아서 넣어준다. 이렇게 객체 의존 관계를 외부에서 넣어주는 것을 DI(Dependency Injection, 의존성 주입)라고 한다.
- 이전 테스트에서는 개발자가 직접 주입했고, 여기서는 `@Autowired` 에 의해 스프링이 주입해준다.

- 컨트롤러 애너테이션을 붙이면 생기는 일!
    - 스프링이 실행되면 스프링 컨테이너(통)가 생긴다. 이 곳에 `@Controller`가 붙은 클래스(의 인스턴스를 생성해서 스프링 컨테이너에 넣어두고 관리한다. ⇒ 빈이 관리된다.

<br>

- `private final MemberService memberService = new MemberService();` 를 사용할 때 생기는 문제점
    - 다른 클래스에서도 인스턴스를 사용해야 하는데, new 키워드로 매번 인스턴스를 생성하는 것은 낭비이다. 그 이유는 memberService의 경우 MemberController 이외에도 사용할 곳이 많기 때문에 사용하는 클래스마다 객체를 생성하는 것 보다는 하나만 생성해 두고 공용으로 여기저기서 갖다 사용하는 것이 더 효율적이기 때문이다.
    - 이를 위해서는 스프링 컨테이너에 등록하고 사용하는 것이 좋다. → 생성자로 연결 후 `@AutoWired` 를 붙여주면 스프링 컨테이너에서 클래스를 스프링 컨테이너가 가져와서 연결시켜준다.
    - 예시 코드
    - `@Autowired` - 스프링이 스프링 컨테이너에 있는 memberService와 연결시켜준다.

```java
@Controller
public class MemberController {

    private final MemberService memberService;
    
    @Autowired
    public MemberController(MemberService memberService) {
        this.memberService = memberService;
    }
}
```

<br>

**오류 발생**
```text
...
Consider defining a bean of type 'hello.hellospring.service.memberService' in your configuration.
...
```

❗ 하지만 위 코드는 완전하지 않은 코드이다. 그 이유는 스프링 컨테이너에서 MemberService 클래스를 넣어두고 관리하는 상태가 아니기 때문이다. → `@Service` 애너테이션을 MemberService에 붙여주면 해결!

❗ Repository의 경우 `@Repository` 애너테이션을 구현체에 붙여주면 스프링 빈에 등록할 수 있다.

-> **memberService가 스프링 빈으로 등록되어 있지 않다.**
> 참고: helloController는 스프링이 제공하는 컨트롤러여서 스프링 빈으로 자동 등록된다. @Controller가 있으면 자동 등록됨

<br>

**스프링 빈을 등록하는 2가지 방법**

- 컴포넌트 스캔과 자동 의존관계 설정
- 자바 코드로 직접 스프링 빈 등록하기

<br>

⭐ 컨트롤러와 서비스를 연결시켜주어야 하는데, @Autowired 를 사용하면 컨트롤러가 생성될 때 스프링 컨테이너에 등록되어 있는 서비스의 객체를 연결시켜준다. 리포지토리도 마찬가지이다. ⇒ 이것이 **DI(Dependency Injection)**

⭐ `@Component`는 `@Controller`, `@Service`, `@Repository` 애너테이션의 상위 애너테이션이다. 그 이유는 스프링이 실행될 때, 컴포넌트와 관련되 애너테이션들이 스프링 컨테이너에 등록되기 때문이다.

⭐ `@SpringBootApplication` 애너테이션이 붙어있는 클래스의 디렉토리를 기준으로 스프링이 탐색하기 때문에 해당 디렉토리보다 상위 디렉토리인 경우 스프링 컨테이너에 포함되지 않는다.

>참고: 스프링은 스프링 컨테이너에 스프링 빈을 등록할 때, 기본으로 싱글톤으로 등록한다.(유일하게 하나만 등록해서 공유한다.) 따라서 같은 스프링 빈이면 모두 같은 인스턴스다. 설정을 통해 싱글톤이 아니게 설정할 수 있지만, 특별한 경우를 제외하면 대부분 싱글톤을 사용한다.
