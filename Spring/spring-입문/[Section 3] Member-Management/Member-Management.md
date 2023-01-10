# 회원 관리 예제 - 백엔드 개발
## 📌목차
- [비즈니스 요구사항 정리](#비즈니스-요구사항-정리)
- [회원 도메인과 리포지토리 만들기](#회원-도메인과-리포지토리-만들기)
- 회원 리포지토리 테스트 케이스 작성
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
    private static long sequence = 0L; // 동시성 문제를 고려하면 AtoimicLong 사용

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
                .findAny();
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
