# 회원 관리 예제 - 백엔드 개발
## 📌목차
- [비즈니스 요구사항 정리](#비즈니스-요구사항-정리)
- [회원 도메인과 리포지토리 만들기](#회원-도메인과-리포지토리-만들기)
- [회원 리포지토리 테스트 케이스 작성](#회원-리포지토리-테스트-케이스-작성)
- 회원 서비스 개발
- 회원 서비스 테스트

<br>

## ✅비즈니스 요구사항 정리
- 데이터: 회원ID, 이름
- 기능: 회원 등록, 조회
- 아직 데이터 저장소 미정(가상의 시나리오)

<br>

**일반적인 웹 애플리케이션 계층 구조**
![일반적인 웹 애플리케이션 계층 구조](https://user-images.githubusercontent.com/79316402/211205138-764ca1dd-8d67-4fd7-be63-5ae2418de0de.png)
- 컨트롤러: 웹 MVC의 컨트롤러 역할, API를 만드는 경우
- 서비스: 핵심 비즈니스 로직 구현(회원 중복가입 불가 등)
- 리포지토리: 데이터베이스에 접근, 도메인 객체를 DB에 저장하고 관리
- 도메인: 비즈니스 도메인 객체, 예) 회원, 주문, 쿠폰 등 주로 데이터베이스에 저장하고 관리됨

<br>

**클래스 의존관계** 
![클래스 의존관계](https://user-images.githubusercontent.com/79316402/211205443-acb40ef8-a265-4e01-b51f-8c9af8de4cad.png)
- 아직 데이터 저장소가 선정되지 않아서, 우선 인터페이스로 구현 클래스를 변경할 수 있도록 설계
- 데이터 저장소는 RDB, NoSQL 등 다양한 저장소를 고민중인 상황으로 가정
- 개발을 진행하기 위해서 초기 개발 단계에서는 구현체로 가벼운 메모리 기반의 데이터 저장소 사용

<br>

## ✅회원 도메인과 리포지토리 만들기
**Member**
```java
public class Member {

    private Long id; // 데이터를 구분하기 위한 용도
    private String name;

    public Long getId() {
        return id;
    }

    public void setId(Long id) {
        this.id = id;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }
}
```

<br>

**MemberRepository**
```java
import hello.hellospring.domain.Member;

import java.util.List;
import java.util.Optional;

public interface MemberRepository {
    Member save(Member member);
    Optional<Member> findById(Long id); // java 8에 들어간 것이고, id나 name이 null인 경우를 대비하여 사용한다.
    Optional<Member> findByName(String name);
    List<Member> findAll();
}
```
- Optional: java 8에서 생긴 것이다. id나 name이 null인 경우를 대비하여 사용한다.

<br>

**MemoryMemberRepository**
```java
import hello.hellospring.domain.Member;

import java.util.*;

public class MemoryMemberRepository implements MemberRepository{

    private static Map<Long, Member> store = new HashMap<>(); // 실제 개발을 할 때는 동시성 문제가 있어서 공유되는 변수인 경우 ConcurrentHashMap을 사용한다.
    private static long sequence = 0L; // 키 값을 생성해주기 위한 변수, 동시성 문제를 고려하면 AtoimicLong 사용

    @Override
    public Member save(Member member) {
        member.setId(++sequence);
        store.put(member.getId(), member);
        return member;
    }

    @Override
    public Optional<Member> findById(Long id) {
        return Optional.ofNullable(store.get(id)); // null을 대비하여 Optional 사용
    }

    @Override
    public Optional<Member> findByName(String name) {
        return store.values().stream()
                .filter(member -> member.getName().equals(name))
                .findAny(); // 하나라도 있으면 찾는다.
    }

    @Override
    public List<Member> findAll() {
        return new ArrayList<>(store.values());
    }
}
```
- HashMap: 실제 개발을 할 때는 동시성 문제가 있어서 공유되는 변수인 경우 ConcurrentHashMap을 사용한다.
- long: 동시성 문제를 고려하면 AtomicLong 사용한다.

<br>

## ✅회원 리포지토리 테스트 케이스 작성
개발한 기능을 실행해서 테스트 할 때 

1. 자바의 main 메서드를 통해서 실행하거나, 
2. 웹 애플리케이션의 컨트롤러를 통해서 해당 기능을 실행한다. 

이러한 방법은 준비하고 실행하는데 오래 걸리고, 반복 실행하기 어렵고 여러 테스트를 한 번에 실행하기 어렵다는 단점이 있다. 

→ 자바는 **JUnit**이라는 프레임워크로 테스트를 실행해서 이러한 문제를 해결한다.

**회원 리포지토리 메모리 구현체 테스트**

- 테스트용 패키지는 보통 실제 기능이 동작하는 패키지의 이름과 똑같이 만든다.
1. `src/test/java` 하위 폴더에 repository 패키지를 생성한다.
    - 테스트할 클래스의 이름 뒤에 Test를 붙여서 `~Test.java` 형태로 만드는 것이 관례이다.
    - public으로 하지 않아도 됨 → 다른데서 호출하지 않으니까!
2. `@Test` 어노테이션을 사용하면 기능을 실행할 수 있다.
3. `save()` 결과 확인하기
    1. `System.out.println("result = " + (result == member));` 으로 출력문을 통해 확인할 수 있지만 해당 방법은 비효율적이다.
    2. `Assertions.assertEquals(expected, actual);` 을 사용하면 결과를 확인할 수 있다. expected에 기대값을 넣고 actual과 비교하는 것이다. `org.junit.jupiter.api.Test;` 를 import 해서 사용한다.
    3. `Assertions.assertThat(member).isEqualTo(result);` 으로 사용하는 것이 문장 읽듯 읽혀서 이해가 빠르다. `org.assertj.core.api.Assertions;` 를 import해서 사용한다. Assertions 부분에 option + enter를 입력해서 static import를 사용하면 **`assertThat**(member).isEqualTo(result);` 형태로 사용이 가능하다.
    
    → 실무에서는 build 툴과 엮어서 빌드시 테스트케이스를 통과하지 못하면 다음 단계로 못 가도록 만든다.
    
4. `findByName()` 결과 확인하기

5. ⭐ Test Case는 순서와 상관없이 정상 동작하도록, 의존관계 없이 설계해야 한다. 즉 테스트가 하나 끝나면 데이터를 클리어할 수 있도록 해주어야 한다. → 하나의 테스트가 끝날 때마다 저장소나 공용 데이터를 깔끔하게 지워주어야 한다.
    1. *`@AfterEach`* 어노테이션을 붙여줘서 각 메소드 동작이 끝난 이후에 처리를 해줄 수 있다.
    2. MemoryMemberRepository 클래스에 clearStore()라는 메소드를 만들어 repository를 비워줄 수 있다.

→ Test Case의 장점은 클래스 레벨, 전체 클래스 레벨 단위로 테스트가 가능하다는 것이다.

→ 테스트 코드를 먼저 작성하고 클래스를 작성하는 것: TDD(테스트 주도 개발, Test Driven Development)

→ 테스트 클래스 전체를 돌려서 테스트 해보자!

→ 테스트 코드 작성은 중요한 부분이므로 꼭 깊게 공부할 것!

**MemoryMemberRepository**

```java
package hello.hellospring.repository;

import hello.hellospring.domain.Member;
import org.assertj.core.api.Assertions;
import org.junit.jupiter.api.AfterEach;
import org.junit.jupiter.api.Test;

import java.util.List;
import java.util.Optional;

import static org.assertj.core.api.Assertions.*;

class MemoryMemberRepositoryTest {

    MemoryMemberRepository repository = new MemoryMemberRepository(); // MemoryMemberRepository만 테스틑 하는 것이므로 인터페이스를 사용하지 않고 클래스를 사용한다.

    @AfterEach
    public void afterEach() {
        repository.clearStore();
    }

    @Test
    public void save() {
        Member member = new Member();
        member.setName("spring");

        repository.save(member);

        Member result = repository.findById(member.getId()).get(); // Optional의 경우 get()으로 바로 꺼낼 수 있지만 비추!
        assertThat(member).isEqualTo(result);
    }
    
    @Test
    public void findByName() {
        Member member1 = new Member();
        member1.setName("spring1");
        repository.save(member1);

        Member member2 = new Member();
        member2.setName("spring2");
        repository.save(member2);

        Member result = repository.findByName("spring1").get();

        assertThat(result).isEqualTo(member1);
    }

    @Test
    public void findAll() {
        Member member1 = new Member();
        member1.setName("spring1");
        repository.save(member1);

        Member member2 = new Member();
        member2.setName("spring2");
        repository.save(member2);

        List<Member> result = repository.findAll();
        assertThat(result.size()).isEqualTo(2);
    }
}
```

### 꿀팁 저장소
🍯 꿀팁: 다음 줄로 넘어가려면 커서를 끝으로 옮기지 말고 cmd + shift + enter로 바로 다음줄 갈 수 있다.
![image](https://user-images.githubusercontent.com/79316402/224724800-32411333-4f5f-44af-9481-359bab103cad.png)
![image](https://user-images.githubusercontent.com/79316402/224724850-6a1a0422-4694-4cd5-a8de-3784c67d4145.png)

🍯 꿀팁: 같은 내용을 복붙할 때, 변수 이름을 일괄적으로 변경하고 싶다면 shift + F6을 눌러 한꺼번에 변경할 수 있다.
![image](https://user-images.githubusercontent.com/79316402/224724996-35ca4709-b9ba-46d8-8d77-88b2f6b73617.png)

🍯 꿀팁: Optional 형태의 변수는 get()을 통해서 Optional을 없애줄 수 있다.
![image](https://user-images.githubusercontent.com/79316402/224725057-0123a5f7-e333-483a-8213-5cb6b8b28f81.png)

🍯 꿀팁: 특정 함수의 return 값을 변수에 저장하고 싶을 때는 option + cmd + v를 누르면 자동으로 생성된다. 단 커서가 맨 끝에 있어야 한다.
![image](https://user-images.githubusercontent.com/79316402/224725164-6df21d5b-3eed-4f3b-9e00-9ee0488f84bf.png)
<br>
![image](https://user-images.githubusercontent.com/79316402/224725213-2d56d6c6-92d4-491d-9afd-e21555511a02.png)


