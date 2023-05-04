# 스프링 빈과 의존관계
## 📌목차
- [컴포넌트 스캔과 자동 의존관계 설정](#컴포넌트-스캔과-자동-의존관계-설정)
- [자바 코드로 직접 스프링 빈 등록하기](#자바-코드로-직접-스프링-빈-등록하기)

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

## ✅자바 코드로 직접 스프링 빈 등록하기
- 자바 코드로 스프링 빈을 하나하나, 직접! 등록하는 방법을 배운다.

❗ 회원 서비스와 회원 리포지토리의 `@Service`, `@Repository`, `@Autowired` 애너테이션을 제거하고 진행한다.

```java
package hello.hellospring;

import hello.hellospring.repository.MemberRepository;
import hello.hellospring.repository.MemoryMemberRepository;
import hello.hellospring.service.MemberService;
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;

@Configuration
public class SpringConfig {

    @Bean
    public MemberService memberService() {
        return new MemberService(memberRepository());
    }

    @Bean
    public MemberRepository memberRepository() {
        return new MemoryMemberRepository();
    }
}
```
- 메서드, 생성자에 필요한 parameter를 모를 때는 `cmd + p` 를 누르면 알 수 있다.

> 참고: DI의 3가지 방법 필드 주입, setter 주입, 생성자 주입이 있다. 의존관계가 실행중에 동적으로 변하는 경우는 ~~거의~~ 아예 없으므로 생성자 주입을 권장한다. *만약 동적으로 변경된다면 Config 파일을 수정하고 서버를 다시 올린다.

❌ 필드 주입을 권장하지 않는 이유
```java
@Controller
public class MemberController {

    @Autowired private MemberService memberService; // 필드 주입
		
		...
}
```
→ 중간에 변경이 불가능하기 때문이다.

<br>

❌ setter 주입을 권장하지 않는 이유
```java
@Controller
public class MemberController {

    private MemberService memberService;
    
    @Autowired
    public void setMemberService(MemberService memberService) { // setter 주입
        this.memberService = memberService;
    }

}
```
→ setter를 통해서 주입하면 누군가 controller를 호출했을 때, public으로 열려있어야 한다. 그렇게 되면 중간에 변경할 필요가 없는데, public하게 노출되고 바뀌게 되면 Application에 문제가 생긴다. Application 세팅 초기 조립시에만 변경이 일어나고 이후로는 바꿀 일이 없다!  
→ 누군가 해당 메서드에 접근해서 변경할 수 있는 여지가 있기 때문에 변경할 필요가 없는 메서드의 경우 호출되지 않도록 setter를 사용하지 않아야 변경될 위험 요소가 줄어드는 것이다.

<br>

✅ 생성자 주입
```java
@Controller
public class MemberController {

    private final MemberService memberService;

    @Autowired
    public MemberController(MemberService memberService) { // 생성자 주입
        this.memberService = memberService;
    }
}
```
→ 처음에 Application이 조립되는 시점(스프링 컨테이너에 올라가는 시점)에 생성자로 한번 들어오고 끝난다.

<br>

> 참고: 실무에서는 주로 정형화된 컨트롤러, 서비스, 리포지토리 같은 코드는 컴포넌트 스캔을 사용한다. 그리고 정형화되지 않거나, 상황에 따라 구현 클래스를 변경해야 하면 설정을 통해 스프링 빈으로 등록한다. 

```java
package hello.hellospring;

import hello.hellospring.repository.MemberRepository;
import hello.hellospring.repository.MemoryMemberRepository;
import hello.hellospring.service.MemberService;
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;

@Configuration
public class SpringConfig {

    @Bean
    public MemberService memberService() {
        return new MemberService(memberRepository());
    }

    @Bean
    public MemberRepository memberRepository() {
        return new MemoryMemberRepository(); // 저장소가 정해지면 이 부분을 바꿔준다.
				// return new DbMemberRepository();
    }
}
```
- 앞선 수업에서 다음과 같은 상황이 주어졌다. → 아직 데이터 저장소가 선정되지 않음, 먼저 메모리를 만들고 교체하자!
- 그래서 MemberRepository를 인터페이스로 선언하고, MemoryMemberRepository를 구현체로 작성해준 것이다.
- 추후 데이터 저장소가 정해져서 MemoryMemberRepository를 다른 Repository로 코드에 손을 하나도 대지 않고 바꿔치기 하는 방법이 있다.
- SpringConfig 파일(설정 파일)에 있는 코드, 즉 빈에 등록될 때 올라가는 구현체만 바꿔주면 된다.

> 주의: `@Autowired` 를 통한 DI는 `helloController`, `MemberService` 등과 같이 스프링이 관리하는 객체에서만 동작한다. 스프링 빈으로 등록하지 않고 내가 직접 생성한 객체에서는 동작하지 않는다.

```java
package hello.hellospring;

import hello.hellospring.repository.MemberRepository;
import hello.hellospring.repository.MemoryMemberRepository;
import hello.hellospring.service.MemberService;
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;

@Configuration
public class SpringConfig {
		// 스프링 빈에 등록된 내용이 없다.
}
```
```java
public class MemberService {

    private final MemberRepository memberRepository;
		
        // 1. 스프링 빈에 등록하지 않고 @Autowired만 생성자에 붙여주는 경우
        // 해당 어노테이션을 붙여도 MemberService가 스프링 빈에 등록되어 있지 않기 때문에 실행되지 않는다.
        @Autowired 
        public MemberService(MemberRepository memberRepository) {
            this.memberRepository = memberRepository;
        }
		
        // 2. 직접 new로 MemberService의 객체를 생성하는 경우
        // 직접 생성했기 때문에 동작하지 않는다. 스프링 컨테이너에 등록된 것만 @Autowired가 동작!
        public static void main(String[] args) {
            MemberService memberService = new MemberService();
        }
        
        ...
}
```
> 스프링 컨테이너, DI 관련된 자세한 내용은 스프링 핵심 원리 강의에서 설명한다.
