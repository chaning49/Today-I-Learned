# π§π»βπ»λ©ν λ§ 1μ£Όμ°¨ - 1μ 7μΌ(ν )

μ½λμ€νμ΄μΈ  λ©μΈ νλ‘μ νΈ λ©ν λ§μ μ§ννλ©΄μ λ©ν λκ»μ ν΄μ£Όμ  μ§λ¬Έκ³Ό κ·Έμ λν λ΅λ³μ μ λ¦¬ν΄λ³΄λ €κ³  ν©λλ€. <br>
μ ννμ§ μμ λ΄μ©μ΄ μμ μλ μκΈ° λλ¬Έμ νΌλλ°±μ μμ  νμν©λλ€! ππ

<br>

## πλͺ©μ°¨
<br>

## π€μ§λ¬Έ μ λ¦¬!
### 1. νμ¬ μ¬μ©νλ SDKλ λ¬΄μμΈκ°μ?

π’ μ λ spring bootλ‘ κ°λ°νκ³  μκ³ , SDKλ azulμ OpenJDK 11 LTS λ²μ μ μ¬μ©νλ€.

<br>

### 1-1. ν΄λΉ λ²μ μ μ¬μ©νλ μ΄μ λ?

OpenJDK 11μ μλ° 11 λ²μ μλλ€. μ νν μ΄μ λ LTS λ²μ  μ€μμ μμ μ μ΄κ³ , μ±λ₯ κ°μ μ΄ λμ΄ μλ λ²μ μ΄κΈ° λλ¬Έμ μ¬μ©νλ€.
1. μλ° 11μ μλ‘ μΆκ°λ κΈ°λ₯μ μ΄μ©ν  μ μμ΅λλ€. String ν΄λμ€μ μλ‘μ΄ λ©μλ μΆκ°(isBlank, strip ...)
2. μμ€ νμΌ μ€νμ΄ javacλ₯Ό ν΅ν μ»΄νμΌ μμ΄ μ€ν¬λ¦½νΈλ‘ κ°λ₯νμ¬ νΈλ¦¬ν΄μ‘λ€.
3. GCμ μ±λ₯μ΄ κ°μ λλλ€. (Z GC, Epsilon λ±)
4. LTSμ΄κΈ° λλ¬Έμ λ²μ μ λν μ₯κΈ°μ μΈ μ§μμ΄ κ°λ₯νλ€.

<br>

### πμΆκ° μ§μ μκΈ°

- JDK 8 λ²μ (λ°μ΄λ μμ μ±μΌλ‘ μ§κΈκΉμ§λ λ§μ΄ μ¬μ©μ€μ΄λ€.)
  - λλ€μ λ° λ©μλ μ°Έμ‘° λμ
  - μ»¬λ μμ Stream API μ¬μ© κ°λ₯
  - μΈν°νμ΄μ€ λ΄λΆμ default λ©μλ μ μΈ κ°λ₯
  - Optional ν΄λμ€ λμ λ±

- JDK 17
  - νμ€νΈ λΈλ‘ μΆκ°
  - μμ¬ λμ μμ±κΈ° κΈ°λ₯ ν₯μ
  - switch λ¬Έ κΈ°λ₯ ν₯μ
  - λ΄μΈ ν΄λμ€ μΆκ° λ±

<br>

### 2. μ§κΈ μμ±νλ Applicationμ λ©ν° νλ‘μΈμ€λ‘ λμ λ κΉμ? λ©ν° μ€λ λλ‘ λμ λ κΉμ? 

Spring Boot(λ΄μ₯ Tomcat μΉ μλ²)μ κ²½μ° λ©ν° μ€λ λ λ°©μμΌλ‘ λμνλ€.
μΌλ°μ μΌλ‘ λ©ν° μ€λ λμμλ ν΄λΌμ΄μΈνΈ μμ²­ λ°μ > μ€λ λ μμ± > μμ²­ μ²λ¦¬ μμλ‘ λμνλ€. 
νμ§λ§ ν΄λΌμ΄μΈνΈκ° λ§μμ§λ©΄ μ€λ λλ₯Ό μμ±νκ³  μ κ±°νλ λ°μ λΉμ©κ³Ό μ€λ²ν€λκ° λ°μνλ€.

<br>

μ΄λ₯Ό ν΄κ²°ν΄κΈ° μν΄ Spring Bootμμλ __μ€λ λ ν(Thread Pool)__ λ°©μμ μ¬μ©νλ€. 
μ€λ λ ν λ°©μμ λ―Έλ¦¬ νΉμ  κ°μμ μ€λ λλ₯Ό μ€λ λ νμ λ§λ€μ΄λκ³  νμν  λλ§λ€ κ°μ Έλ€ μ¬μ©νλ€. 
ν΄λΌμ΄μΈνΈ μμ²­μ΄ μλ νμ κ²½μ°, νμ μλ μ€λ λ κ°μλ³΄λ€ μμ²­μ΄ λ§μμ§λ©΄ μ€λ λλ₯Ό μλ‘ μμ±νλ€. 
μ¬μ¬μ© κ°λ₯νλ€λ μ₯μ μ΄ μλ€. 
κ·Έλμ μ¬μ μ poolμ μ μ₯λ  μ€λ λμ κ°μλ₯Ό μ μ ν μμ±νλ κ²μ΄ μ€μλ€.

<br>

μ€νλ§μ κ²½μ°λ κΈ°λ³Έμ μΌλ‘ Thread-safe νμ§ μμ§λ§ μ€νλ§ λΉμ λ¬΄μνλ‘ μ€κ³νλ κ΄ν, μ€νλ§ λΉμ μ μ­ λ³μμλ finalμ μ¬μ©νλ κ΄νμ΄ μλ€. κ·Έλμ Thread-safe ν΄μ§ κ²μ΄λ€.

<br>

### 2-1. κ³΅μ λλ μμμ λ¬΄μμΌκΉμ?

- κ³΅μ μμ: μ€λ λκ° λμμ±μΌλ‘ μ€νλ  λ, μ¬λ¬ κ°μ μ€λ λκ° μ κ·Ό κ°λ₯ν μμμ κ³΅μ μμμ΄λΌκ³  νλ€.
- κ³΅μ  μμμ μ€λ λ μ¬λ¬ κ°κ° λμμ μ κ·Όνλ©΄ μλ¬κ° λ°μνλ€.
- μ€λ λλ νλ‘μΈμ€ λ΄μμ Stackμ λ°λ‘ ν λΉ λ°κ³ , Code, Data, Heap μμ­μ κ³΅μ νλ€.

<br>

### 2-2. κ³΅μ λλ μμμ μ΄λ€ λ¬Έμ μ μ΄ μμκΉμ?

- μ¬λ¬ κ°μ μ€λ λκ° λμΌν λ°μ΄ν° κ³΅κ°(Critical Section, μκ³ μμ­)μ κ³΅μ νλ©΄μ μ΄λ€μ μμ νλ€λ μ μ νμ°μ μΌλ‘ μκΈ°λ λ¬Έμ μ΄λ€.
- λ©ν° νλ‘μΈμ€μ νλ‘κ·Έλ¨μ λ¬Έμ κ° μκΈ°λ©΄ ν΄λΉ νλ‘μΈμ€κ° μ€λ¨λκ±°λ μ€λ¨ μν€κ³  λ€μ μμ νλ©΄λλ€. νμ§λ§ λ©ν° μ€λ λ λ°©μμ νλ‘κ·Έλ¨μμλ νλμ μ€λ λκ° μμ μ΄ μ¬μ©νλΒ λ°μ΄ν° κ³΅κ°μ λ§κ°λ¨λ¦°λ€λ©΄, ν΄λΉ λ°μ΄ν° κ³΅κ°μ κ³΅μ νλ λͺ¨λ  μ€λ λλ₯Ό λ§κ°λ¨λ¦΄Β μ μλ€.
- μκ³μμ­(κ³΅μ  λ³μ μμ­): λ μ΄μμ μ€λ λκ° λμμ μ κ·Όν΄μλ μλλ κ³΅μ  μμ(μλ£ κ΅¬μ‘° λλ μ₯μΉ)μ μ κ·Όνλ μ½λμ μΌλΆλ₯Ό λ§νλ€.

<br>

### πμΆκ° μ§μ μκΈ°
![αα¦α«αα©αα΅αΌ_1αα―α―_7αα΅α―](https://user-images.githubusercontent.com/79316402/212903723-0eba19c9-696f-42fd-8d4e-6c7d739c4fb3.png)

- νλ‘μΈμ€
  - νλ‘κ·Έλ¨μ΄ μ€νλμ΄ λμκ°λ μν, μ¬μ©μκ° μμ±ν νλ‘κ·Έλ¨μ΄ μ΄μμ²΄μ μ μν΄ λ©λͺ¨λ¦¬ κ³΅κ°μ ν λΉλ°μ μ€ν μ€μΈ κ²μ λ§νλ€. 
  - μ»΄ν¨ν°λ μ¬λ¬ νλ‘μΈμ€λ₯Ό ν¨κ» μ€νμν¨λ€. 
  - νλ‘μΈμ€ = νλ‘κ·Έλ¨μ μ¬μ©λλ λ°μ΄ν°μ λ©λͺ¨λ¦¬ λ±μ μμ + μ€λ λ
  - λμμ±(Concurrency): μ‘°κΈμ© μ¬λ¬ μμμ λμκ°λ©΄μ μ§ννλ λ°©λ², μ¬λμ΄ μκ°ν  μ μλ μλλ‘ Context Switching(μ§νμ€μΈ μμμ λ°κΎΈλ κ²)μ΄ μΌμ΄λ λμμ μΌμ΄λλ κ²μ²λΌ λκ»΄μ§λ€.
  - λ³λ ¬μ±(Parallelism): νλ‘μΈμ νλμ μ½μ΄ μ¬λ¬ κ°κ° λ¬λ €μ κ°κ° λμμ μμμ μννλ κ²(λμΌ, μ½μ΄, μΏΌλ μ½μ΄ λ±λ±)

- νλ‘μΈμ€μ λ©λͺ¨λ¦¬ κ΅¬μ‘°
  - code μμ­: νλ‘κ·Έλ¨ μ½λ
  - data μμ­: μ½λ μ€νμ μ¬μ©λλ λ°μ΄ν°(μ μ­ λ³μ, static λ³μ)
  - heap μμ­: λμ μΌλ‘ ν λΉλλ λ©λͺ¨λ¦¬
  - stack μμ­: μ§μ­ λ³μ, λ§€κ° λ³μ, λ¦¬ν΄ κ°

- λ©ν° νλ‘μΈμ€
  - νλμ μ νλ¦¬μΌμ΄μμ μ¬λ¬ κ°μ νλ‘μΈμ€λ‘ κ΅¬μ±νμ¬ κ° νλ‘μΈμ€κ° νλμ μμμ μ²λ¦¬νλλ‘ νλ κ²μ΄λ€.
  - μμ μ±: μ¬λ¬ κ°μ μμ νλ‘μΈμ€ μ€ νλμ λ¬Έμ κ° λ°μν΄λ, λ€λ₯Έ μμ νλ‘μΈμ€μ μν₯μ΄ νμ°λμ§ μλλ€.
  - κ΅¬νμ΄ λΉκ΅μ  κ°λ¨νκ³ , κ° νλ‘μΈμ€λ€μ΄ λλ¦½μ μΌλ‘ λμνλ©° μμλ μλ‘ λ€λ₯΄κ² ν λΉλλ€.
  - IPC: νλ‘μΈμ€ κ° ν΅μ  λ°©λ²(νλ‘μΈμ€ κ°μλ λ³λμ ν΅μ  λ°©λ²μ΄ νμνλ€.)
  - λ©λͺ¨λ¦¬ μ¬μ©λμ΄ λ§λ€.
  - μ€μΌμ₯΄λ§μ λ°λΌ Context Switchκ° λ§μμ§κ³ , μ±λ₯ μ νκ° μκΈΈ μ μλ€.

- μ€λ λ
  - νλ‘μΈμ€ λ΄μμ μ€μ λ‘ μμμ μννλ μ£Όμ²΄λ₯Ό μλ―Ένλ€. λͺ¨λ  νλ‘μΈμ€μλ ν κ° μ΄μμ μ€λ λκ° μ‘΄μ¬νμ¬ μμμ μννλ€.

- λ©ν° μ€λ λ
  - νλμ μ νλ¦¬μΌμ΄μμ μ¬λ¬ κ°μ μ€λ λλ‘ κ΅¬μ±νμ¬ νλμ μ€λ λκ° νλμ μμμ μ²λ¦¬νλλ‘ νλ κ²μ΄λ€. ν νλ‘μΈμ€ μμμλ μ¬λ¬ μμλ€μ΄ λμμ μ§νλλ κ²μ΄ λ©ν° μ€λ λμ΄λ€.
  - μΌλ°μ μΌλ‘ λ©ν°μ€λ λλ₯Ό μ¬μ©νλ μ΄μ λ μ¬μ©μμ μνΈμμ©νλ μ νλ¦¬μΌμ΄μμμ λ¨μΌ μ€λ λλ‘ Network λλ DB μ κ°μ κΈ΄ μμ(Long-running task) μ μννλ κ²½μ° ν΄λΉ μμμ μ²λ¦¬νλ λμ μ¬μ©μμ μνΈμμ©μ΄ λΆλ₯μΈ μνκ° λ  μ μκΈ° λλ¬Έμ΄λ€. (IOκ° μΌμ΄λ¬μ κ²½μ°μ λκ°λ€.)
  - κ΅μ°©μνκ° λ°μνμ§ μλλ‘ μ£Όμν΄μΌ νλ€. -> λκΈ°νλ‘ ν΄κ²° κ°λ₯!
  - μ€λ λλ νλ‘μΈμ€ λ΄μμ κ°κ° Stackλ§ λ°λ‘ ν λΉλ°κ³  Code, Data, Heap μμ­μ κ³΅μ νλ€.

- λ©ν° μ€λ λ μ₯μ 
  - μλ΅μ±μ΄ μ’λ€: νλ‘κ·Έλ¨μ μΌλΆλΆ(μμ μ€λ λ)μ΄ μ€λ₯ λλ κΈ΄ μμμΌλ‘ μΈν΄ μ€λ¨λμ΄λ νλ‘κ·Έλ¨μ΄ κ³μ μνλλ€.
  - μμ κ³΅μ κ° μ½λ€: μ€λ λλ€μ λΆλͺ¨ νλ‘μΈμ€μ μμκ³Ό λ©λͺ¨λ¦¬λ₯Ό κ³΅μ ν  μ μλ€.
  - νλ‘μΈμ€λ₯Ό ν λΉνλ κ²λ³΄λ€ μ€λ λλ₯Ό ν λΉνλ κ²μ΄ λΉμ©μ΄ μ λ€.
  - λ©ν° νλ‘μΈμ κ΅¬μ‘°μμ κ°κ°μ μ€λ λκ° λ€λ₯Έ νλ‘μΈμμμ λ³λ ¬λ‘ μνλ  μ μλ€.

- λ©ν° μ€λ λ λ¨μ 
  - κ΅¬ν λ° νμ€νΈ, λλ²κΉμ΄ μ΄λ ΅λ€.
  - λλ¬΄ λ§μ μ€λ λ μ¬μ©μ μ€λ²ν€λλ₯Ό λ°μμν¨λ€.
  - μμ μ€λ λ μ€ νλμ λ¬Έμ κ° μκΈ΄κ²½μ° μ μ²΄ νλ‘μΈμ€μ μν₯μ μ€ μ μλ€.
  - κ³΅μ  μμμ μ€λ λ μ¬λ¬ κ°κ° λμμ μ κ·Όνλ©΄ Errorβ Thread-safe(μ¬λ¬ μ€λ λλ‘λΆν° λμ μ κ·Όμ΄ λ°μν΄λ νλ‘κ·Έλ¨ μ€νμ λ¬Έμ κ° μλ κ²)λ₯Ό κ³ λ €νμ.

- νλ‘μΈμ€ vs μ€λ λ
  - νλ‘μΈμ€λ μ»΄ν¨ν° μμμ κ°μ λΆν ν΄μ μ¬μ©νλ λ°λ©΄, μ€λ λλ νλ‘μΈμ€λ§λ€ μ£Όμ΄μ§ μ μ²΄ μμμ ν¨κ» μ¬μ©νκΈ° λλ¬Έμ μλ, ν¨μ¨μμ λ°μ΄λλ€.
  - νλ‘μΈμ€λ μμμ κ³΅μ νμ§ μμ§λ§, μ€λ λλ μμμ κ³΅μ νλ€.

<br>

### 3. lang packageμμ Object ν΄λμ€λ λ¬΄μμΈκ°μ?

- μλ°μ μ΅μμ ν΄λμ€μ΄λ€.
- 11κ°μ λ©μλλ₯Ό κ°μ§κ³  μλ€. (toString, equals, clone, hashcode, finalize, wait, notify)

<br>

### 3-1. μ΅μμ ν΄λμ€λ‘ μκ³ λ€ κ³μ¨λλ°, μμμ μ¬μ©νλμ? μΈν°νμ΄μ€λ‘ κ΅¬ννλμ? 

- μμ, μ»΄νμΌλ¬κ° μλμΌλ‘ extends Objectλ₯Ό μΆκ°νλ€.

<br>

### 3-2. μ­ν μ λ¬΄μμΌκΉμ? 

- OSμ JVM μ¬μ΄μμ κ΄λ¦¬νλ μ­ν μ λ§‘λλ€.
- λͺ¨λ  ν΄λμ€μ μ΅κ³  μ‘°μ ν΄λμ€λ‘ Object ν΄λμ€μ λͺ¨λ  λ©€λ²λ λͺ¨λ  ν΄λμ€μμ λ°λ‘ μ¬μ©μ΄ κ°λ₯νλ€.

<br>

### 3-3. equalsμ hashCode μ°¨μ΄μ μ λ¬΄μμ΄κ³  κ΅¬νμ μ μμ μ λ¬΄μμΌκΉμ?

- equals: λ±κ° λΉκ΅ μ°μ°(==)κ³Ό λμΌνκ² μ€ν λ©λͺ¨λ¦¬ κ°(μ£Όμ)μ λΉκ΅, equals λ©μλλ μλ³Έκ³Ό λμ‘°νλ€. μ£Όμκ° κ°μΌλ©΄ trueλ₯Ό λ¦¬ν΄νλ€. μ½κ² λ§ν΄ μ°Έμ‘° λ³μ(μ£Όμλ₯Ό μ μ₯)λ₯Ό λΉκ΅νλ€.
- hashCode: κ°μ²΄μ μ£Όμκ°μ ν΄μμ½λλ‘ λ°ννλ€. λ©λͺ¨λ¦¬μ μ£Όμ, ν΄μμ ν€λ₯Ό λ§€κ°λ³μλ‘ κ°μ κ°μ Έμ¨λ€. 16μ§μ κ°μ ν λ©λͺ¨λ¦¬ μ£Όμμ΄λ€. λ©λͺ¨λ¦¬μ μ£Όμκ° κ°λ€λ κ²μ μΈμ€ν΄μ€κ° κ°λ€λ λ§μ΄λ€.

<br>

### 4. JVMμ λ©λͺ¨λ¦¬ νλ‘μΈμ€
![αα¦α«αα©αα΅αΌ_1αα―α―_7αα΅α―_1](https://user-images.githubusercontent.com/79316402/212911653-5be0fc7a-2acc-4132-aff1-3a5a8059f005.png)

- λ©μλ μμ­
    
    λ©μλ μμ­μ JVMμ΄ μμν  λ μμ±λκ³  λͺ¨λ  μ€λ λκ° κ³΅μ νλ μμ­μ΄λ€. λ©μλ μμ­μμλ μ½λμμ μ¬μ©λλ classλ€μ ν΄λμ€ λ‘λλ‘ μ½μ΄ ν΄λμ€ λ³λ‘ static fieldμ constant, method code, constructor code λ±μ λΆλ₯ν΄μ μ μ₯νλ€.
    
- ν μμ­
    
    ν μμ­μ κ°μ²΄μ λ°°μ΄μ΄ μμ±λλ μμ­μλλ€. μ¬κΈ°μ μμ±λ κ°μ²΄μ λ°°μ΄μ JVM μ€ν μμ­μ λ³μλ λ€λ₯Έ κ°μ²΄μ νλμμ μ°Έμ‘°νλ€. λ§μΌ μ°Έμ‘°νλ λ³μλ νλκ° μλ€λ©΄ μλ―Έμλ κ°μ²΄κ° λκΈ° λλ¬Έμ JVMμμλ garbage collectorλ‘ μ²λ¦¬λ₯Ό νλ€.
    
- JVM μ€ν μμ­
    
    JVM μ€νμ λ©μλλ₯Ό νΈμΆν  λλ§λ€ frameμ μΆκ°νκ³  λ©μλκ° μ’λ£λλ©΄ ν΄λΉ νλ μμ μ κ±°νλ λμμ μννλ€.

<br>

### 5. Garbage Collection

- μλ°μ λ©λͺ¨λ¦¬ κ΄λ¦¬ λ°©λ² μ€μ νλλ‘ JVM(μλ° κ°μ λ¨Έμ )μΒ **Heap μμ­**μμΒ **λμ μΌλ‘ ν λΉνλ λ©λͺ¨λ¦¬**Β μ€Β **νμ μκ² λ λ©λͺ¨λ¦¬ κ°μ²΄(garbage)λ₯Ό λͺ¨μ μ£ΌκΈ°μ μΌλ‘ μ κ±°**νλ νλ‘μΈμ€μ΄λ€.
- Heap μμ­μμ μ΄λμλ  μ°Έμ‘°νκ³  μμ§ μμ κ°μ²΄(Unreachable)λ€μ΄ λ°μνκ² λλ©΄ μ΄λ¬ν κ°μ²΄λ€μ μ£ΌκΈ°μ μΌλ‘ κ°λΉμ§ μ»¬λ ν°κ° μ κ±°ν΄μ£Όλ κ²μ΄λ€.
- Javaμμλ κ°λΉμ§ μ»¬λ ν°κ° λ©λͺ¨λ¦¬ κ΄λ¦¬λ₯Ό λνν΄μ£ΌκΈ° λλ¬ΈμΒ Java νλ‘μΈμ€κ° νμ λ λ©λͺ¨λ¦¬λ₯Ό ν¨μ¨μ μΌλ‘ μ¬μ©ν μ μκ² νκ³ ,Β κ°λ°μ μμ₯μμ λ©λͺ¨λ¦¬ κ΄λ¦¬, λ©λͺ¨λ¦¬ λμ(Memory Leak) λ¬Έμ μμ λν΄ κ΄λ¦¬νμ§ μμλ λμ΄ μ€λ‘―μ΄Β **κ°λ°μλ§ μ§μ€**ν  μ μλ€λ μ₯μ μ΄ μλ€.
- μλμΌλ‘ μ²λ¦¬ν΄μ€λ€ ν΄λΒ λ©λͺ¨λ¦¬κ° μΈμ  ν΄μ λλμ§ μ ννκ² μ μ μμ΄ μ μ΄νκΈ° νλ€λ©°,Β κ°λΉμ§ μ»¬λ μ(GC)μ΄ λμνλ λμμλΒ λ€λ₯Έ λμμ λ©μΆκΈ°Β λλ¬ΈμΒ **μ€λ²ν€λ**κ° λ°μλλ λ¬Έμ μ μ΄ μλ€.(STW)
- **STW (Stop The World)**
    
    GCλ₯Ό μννκΈ° μν΄ JVMμ΄ νλ‘κ·Έλ¨ μ€νμ λ©μΆλ νμμ μλ―Έ.
    
    GCκ° μλνλ λμ GC κ΄λ ¨ Threadλ₯Ό μ μΈν λͺ¨λ  Threadλ λ©μΆκ² λμ΄ μλΉμ€ μ΄μ©μ μ°¨μ§μ΄ μκΈΈ μ μλ€.

<br>

### 6. Stringκ³Ό StringBuffer(or StringBuilder)

- String
  - λΆλ³: String νμμ ν λ² ν λΉλ κ³΅κ°μ΄ λ³νμ§ μκΈ° λλ¬Έμ immutable μλ£νμ΄λΌκ³  νλ€.
  - String λ³μμ κ°μ λ°κΏ λ, κ°μ΄ 'λ³κ²½'λ κ²μ΄ μλλΌ μλ‘μ΄ String κ°μ²΄λ₯Ό μμ±νκ³  κ·Έ κ°μ²΄λ₯Ό μ°Έμ‘°νλ κ²μ΄λ€. κ·Έλ κ² λλ©΄ μ΄μ μ μμ±λμ΄ λ©λͺ¨λ¦¬μ μ μ¬λμ΄ μλ String κ°μ²΄μ λ©λͺ¨λ¦¬ μμ­μ Garbageμ μλ€κ° GCμ μν΄ ν΄μ λμ΄ μ¬λΌμ§λ€.
  - κ·Έλμ λ³κ²½λμ§ μλ λ¬Έμμ΄μ μμ£Ό μ°Έμ‘°νλ κ²½μ° μ μ©νλ€. νμ§λ§ μΆκ°, μμ , μ­μ  λ±μ μ°μ°μ΄ μμ£Ό μΌμ΄λμΌ νλ κ²½μ°μλ ν μμ­μ λ§μ Garbageκ° μμ±λμ΄ ν λ©λͺ¨λ¦¬ λΆμ‘±μΌλ‘ Applicationμ μ±λ₯ μ νλ₯Ό μΌμΌν¬ μλ μλ€.

- μλ° Stringμ λΆλ³μΌλ‘ μ€μ ν μ΄μ 
  1. μΊμ±: Stringμ λΆλ³μΌλ‘ λ§λ€μ΄ String poolμ κ° λ¦¬ν°λ΄ λ¬Έμμ΄μ νλλ§ μ μ₯νλ©° λ€μ μ¬μ©νκ±°λ μΊμ±μ μ΄μ© κ°λ₯νλ©° κ·Έ κ²°κ³Όλ‘ ν κ³΅κ°μ μ μ½ν  μ μλ€λ μ₯μ μ΄ μλ€.
  2. λ³΄μ: μ¬μ©μμ ν¬λ¦¬λ΄μ κ΄λ ¨λ λ΄μ©λ€μ λ³΄ν΅ Stringμ μ¬μ©νλλ°, λ§μ½ μ΄ κ°μ΄ λ³ν  μ μκ² λλ©΄ μ°Έμ‘°νκ³  μλ κ°μ λ³κ²½νμ¬ Applicationμ λ³΄μ λ¬Έμ λ₯Ό μΌμΌν¬ μ μλ€.
  3. λκΈ°ν : λΆλ³μ΄κΈ° λλ¬Έμ λμμ μ€νλλ μ¬λ¬ μ€λ λμμ μμ μ μ΄κ² κ³΅μ κ° κ°λ₯νλ€.

- StringBuffer / StringBuilder
  - λ¬Έμμ΄μ μ°μ°(μΆκ°νκ±°λ λ³κ²½) ν  λ μ£Όλ‘ μ¬μ©νλ μλ£νμ΄λ€.
  - κ°μ²΄μ κ³΅κ°μ΄ λΆμ‘±ν΄μ§λ κ²½μ° λ²νΌμ ν¬κΈ°λ₯Ό μ μ°νκ² λλ €μ£Όμ΄ mutableνκ² μ¬μ©ν  μ μλ€.
  - κ·Έλμ λ¬Έμμ΄μ μΆκ°,μμ ,μ­μ κ° λΉλ²νκ² λ°μν  κ²½μ°μ μ¬μ©νλ€.
  
- StringBufferμ StringBuilderμ μ°¨μ΄(Thread-safe)
  - StringBuffer: λ΄λΆμ μΌλ‘ λ²νΌ(buffer)λΌκ³  νλ λλ¦½μ μΈ κ³΅κ°μ κ°μ§κ² λμ΄, λ¬Έμμ΄μ λ°λ‘ μΆκ°ν  μ μμ΄ κ³΅κ°μ λ­λΉλ μμΌλ©° λ¬Έμμ΄ μ°μ° μλλ λ§€μ° λΉ λ₯΄λ€λ νΉμ§μ΄ μλ€. λκΈ°νλ₯Ό μ§μνκΈ° λλ¬Έμ Thread-safeνλ€.
  - StringBuilder: StringBufferμ κΈ°λ³Έ κΈ°λ₯μ κ°λ€. νμ§λ§ λ¨μΌ μ€λ λμμ μ±λ₯μ΄ κ°μ₯ λ°μ΄λκ³ , λκΈ°νλ₯Ό μ§μνμ§ μκΈ° λλ¬Έμ Thread-safeνμ§ μλ€.

- Stringκ³Ό StringBufferμ μ°¨μ΄
  - String μλ£νλ§ μΌλ‘λ, `+` μ°μ°μ΄λ `concat()` λ©μλλ‘ λ¬Έμμ΄μ μ΄μ΄λΆμΌμ μλ€.
    νμ§λ§ λ§μ(+) μ°μ°μλ₯Ό μ΄μ©ν΄ String μΈμ€ν΄μ€μ λ¬Έμμ΄μ κ²°ν©νλ©΄, λ΄μ©μ΄ ν©μ³μ§ μλ‘μ΄ String μΈμ€ν΄μ€λ₯Ό μμ±νκ² λμ΄, λ°λΌμ λ¬Έμμ΄μ λ§μ΄ κ²°ν©νλ©΄ κ²°ν©ν μλ‘ κ³΅κ°μ λ­λΉ λΏλ§ μλλΌ μλ λν λ§€μ° λλ €μ§κ² λλ€λ λ¨μ μ΄ μλ€.

- κ²°λ‘ : μμ£Ό λ³νμ§ μλ λ¬Έμμ΄μ μ¬μ©νλ€λ©΄ String κ°μ²΄λ₯Ό μ¬μ©νλ κ²μ΄ μ ν©νκ³ , μΆκ°, μμ , μ­μ  λ±μ μ°μ°μ΄ μμ£Ό νμνλ€λ©΄ StringBufferλ₯Ό μ¬μ©νλ κ²μ΄ μ΅μ μ΄λ€.

<br>

### 7. String ν΄λμ€κ° implement λ°λ Serializableκ³Ό Comparable<String>, **CharSequence**λ λ¬΄μμΈκ°?

- Serializable: java.io ν¨ν€μ§μ μΈν°νμ΄μ€μ΄λ€. ν΄λΉ μΈν°νμ΄μ€λ₯Ό κ΅¬ννλ ν΄λμ€μ μν΄μ μ§λ ¬νκ° κ°λ₯ν΄μ§λ€.
- Comparable<String>: Comparable μΈν°νμ΄μ€λ κ°μ²΄λ₯Ό μ λ ¬νλ λ° μ¬μ©λλ λ©μλμΈ compareTo() λ©μλλ₯Ό μ μνκ³  μλ€. μλ°μμ κ°μ νμμ μΈμ€ν΄μ€λ₯Ό μλ‘ λΉκ΅ν΄μΌλ§ νλ ν΄λμ€λ€μ λͺ¨λ Comparable μΈν°νμ΄μ€λ₯Ό κ΅¬ννκ³  μκΈ° λλ¬Έμ Stringμμλ κ΅¬ννκ³  μλ κ²μ΄λ€.(*κΈ°λ³Έ μ λ ¬ μμλ μ€λ¦μ°¨μ)
- CharSequence: char κ°μ΄ λμ΄λ μΈν°νμ΄μ€μ΄λ€. μ΄ μΈν°νμ΄μ€λ λ€μν μ’λ₯μ λ¬Έμ μνμ€μ λν΄ μ½κΈ° μ μ© μ‘μΈμ€λ₯Ό μ κ³΅νλ€. CharSequenceλ λ³κ²½μ΄ νμκ° μλλ€. λ°λΌμ, κ°λ³ ν΄λμ€μ λΆλ³ ν΄λμ€ λͺ¨λ μ΄ μΈν°νμ΄μ€λ₯Ό κ΅¬ννλ€.

<br>
  
### 7-1. equalsμ νλΌλ―Έν°κ° μ ObjectμΈμ§?

- μ΅μμ ν΄λμ€μΈ Object ν΄λμ€μ equalsκ° μ΄λ―Έ κ΅¬νλμ΄ μλ€. Object ν΄λμ€μ κ΅¬νλ equalsλ©μλλ λ κ°μ μ°Έμ‘°λ³μκ° κ°μ κ°μ²΄λ₯Ό μ°Έμ‘°νκ³  μλμ§λ§ νλ¨ν  μ μκΈ° λλ¬Έμ String ν΄λμ€μμ μ€λ²λΌμ΄λ©νμ¬ μ¬μ μνκΈ° λλ¬Έμ νλΌλ―Έν°λ Object νμμΈ κ²μ΄λ€.
  
<br>

### 7-2. μΈν°νμ΄μ€κ° 3κ°μΈ μ΄μ ?

1. String ν΄λμ€μ Serializableμ μ§λ ¬νλ₯Ό μν΄ μ¬μ©νλ€. νμΌμμ μ½κ±°λ μ°κ³ , λ€λ₯Έ μλ²λ‘ μ μ‘νκΈ° μν΄μλ μ§λ ¬νκ° νμνλ€.
2. Comparableμ κ°μ²΄λ₯Ό μ λ ¬νκΈ° μν΄ μ¬μ©νλλ°, String ν΄λμ€μμλ μ λ ¬μ νλ κΈ°λ₯μ΄ ν¬ν¨λκΈ° λλ¬Έμ μ¬μ©νλ€.
3. String κ°μ²΄λ charSequenceλ₯Ό κ΅¬ννμ¬ λ¬Έμμ΄μ ννλ₯Ό λ§λλ κ²μ΄κΈ° λλ¬Έμ νμνλ€.

<br>
  
### 7-3. String ν΄λμ€μ κ΅¬μ‘°λ?

- String ν΄λμ€λ Object ν΄λμ€μ μμ ν΄λμ€μ΄λ©΄μ Serializable, Comparable<String>, charSequence μΈν°νμ΄μ€λ₯Ό κ΅¬ννλ€.
- Stringμ μμ± λ°©μ
  - literal λ°©μ
  
    String λ³μμ μ§μ  "λ¬Έμμ΄"μ λ£κ² λλ©΄ μμ±ν λ³μλ Stack λ©λͺ¨λ¦¬ λ΄μ, String κ°μ Heap λ©λͺ¨λ¦¬ λ΄μ μλ String poolμ΄λΌλ κ³³μ μ μ₯λκ³ , ν΄λΉ λ¬Έμμ΄μ μ£Όμκ° String λ³μμ μ μ₯λλ€.
  
    String poolμ μ μ₯λ  λλ intern() λ©μλκ° μ€νλλλ°, κ°μ κ°μ΄ μμΌλ©΄ κΈ°μ‘΄ κ°μ λ©λͺ¨λ¦¬ μ£Όμλ₯Ό, λ€λ₯Έ κ°μΈ κ²½μ° μλ‘­κ² κ°μ²΄λ₯Ό μμ±ν΄μ κ°μ μ μ₯νκ³  λ©λͺ¨λ¦¬ μ£Όμλ₯Ό λ¦¬ν΄νλ€.
  
    HashMap ννλ‘ μ μ₯λκΈ° λλ¬Έμ λμΌν λ¬Έμμ΄μ λμΌν λ©λͺ¨λ¦¬ μ£Όμλ₯Ό κ°μ§κ² λλ κ²μ΄λ€. κ·Έλ κΈ° λλ¬Έμ λ©λͺ¨λ¦¬μ λ­λΉλ₯Ό μ€μΌ μ μλ€.
  
  - new ν€μλ λ°©μ
  
    λ³μλ stack μμ­μ μμ±λμ§λ§ μμ±λ λ¬Έμμ΄μ Heap μμ­μ κ°μ²΄κ° λ°λ³΅μ μΌλ‘ μμ±λλ€. 
  
  - String ν΄λμ€λ char νμμ λ°°μ΄ ννλ‘ μ μ₯λλλ°, μ΄λ μ»΄ν¨ν°κ° μΈμνλ 0κ³Ό 1(bitλ¨μ)λ‘ λ³ννκΈ° μν΄ μ λμ½λ(2byte λ¬Έμμ²΄κ³)λ₯Ό μ¬μ©νλ char νμΌλ‘ λ³νν΄μ μ μ₯λλ κ²μ΄λ€.
  
  - Stringμ μ°μ°
  
    λ¬Έμμ΄μ κ²°ν©μμλ `+` μ°μ°μ λλ concat() λ©μλλ₯Ό μ¬μ©νλ€. νμ§λ§ μ΄λ¬ν λ°©μμ κ²½μ° 2κ°μ λ¬Έμμ΄μ κ²°ν©νλ€κ³  νμ λ, μ΄ 3κ°μ κ°μ²΄κ° μμ±λκΈ° λλ¬Έμ μ°μ°μ΄ μ¦μ κ²½μ° λ©λͺ¨λ¦¬ λΆμ‘± νμμ΄ λ°μνλ€.
    
  μ΄λ¬ν λ¬Έμ λ₯Ό ν΄κ²°νκΈ° μν΄ StringBufferμ StringBuilderκ° μκ²Όλ€. μ΄ ν΄λμ€λ€μ appendλ₯Ό μ΄μ©νμ¬ λ¬Έμμ΄μ κ²°ν©ν΄μ£Όλλ° λ©λͺ¨λ¦¬ μ£Όμλ₯Ό νλλ§ μ¬μ©ν  μ μλ€. ~μ΄μ΄μ μμ±(StringBufferμ StringBuilderμ μ°¨μ΄)

<br>

### 7-4. charSequenceκ° μ μΈν°νμ΄μ€λ‘ κ΅¬νλΌ μμκΉ?

- charSequenceλ λ¬Έμμ μνμ€λ₯Ό λνλ΄λ μΈν°νμ΄μ€λ‘ Stringμ΄ charSequenceλ₯Ό μ§μ  κ΅¬ννλ κ΅¬νμ²΄λ‘μμ μ­ν μ μννκΈ° λλ¬Έμ΄λ€.

### πμΆκ° μ§μ μκΈ°
- Serializeμ Deserialize
  - Serialize(μλ° λ΄λΆ Object or Data β byte νμ)
    κ°μ²΄μ μ§λ ¬νλ₯Ό λ»νλ€. μλ° μμ€ν λ΄λΆμμ μ¬μ©λλ Object λλ Dataλ₯Ό μΈλΆμ μλ° μμ€νμμλ μ¬μ©ν  μ μλλ‘ byte ννλ‘ λ°μ΄ν°λ₯Ό λ³ννλ κΈ°μ μ΄λ€.
    λ©λͺ¨λ¦¬ κ΄μ μμ λ§νλ©΄ JVMμ λ©λͺ¨λ¦¬μ μμ£Ό(ν λλ μ€ν)νκ³  μλ κ°μ²΄ λ°μ΄ν°λ₯Ό λ°μ΄νΈ ννλ‘ λ³ννλ κΈ°μ μ λ»νλ€.
    
  - Deserializable(byte νμ β Object or Data)
    byteλ‘ λ³νλ Dataλ₯Ό μλλλ‘ Objectλ Dataλ‘ λ³ννλ κΈ°μ μ μ­μ§λ ¬ν(Deserialize)λΌκ³  νλ€.
    μ§λ ¬νλ λ°μ΄νΈ ννμ λ°μ΄ν°λ₯Ό κ°μ²΄λ‘ λ³νν΄μ JVMμΌλ‘ μμ£Όμν€λ ννμ΄λ€.

<br>

### 8. JPAλ?
- JPA(Java Persistence API)λ Java μ§μμμ μ¬μ©νλ ORM(Object-Relational Mapping) κΈ°μ μ νμ€ μ¬μ(λλ λͺμΈ, Specification)μ΄λ€. λ°μ΄ν° μ‘μΈμ€ κ³μΈ΅μ μλ¨μ μμΉνκ³  μλ€. λ°μ΄ν° μ μ₯, μ‘°ν λ±μ μμμ JPAλ₯Ό κ±°μ³ JPAμ κ΅¬νμ²΄μΈ Hibernate ORM(μ§μ  μ¬μ©ν JPAμ κ΅¬νμ²΄μλλ€.)μ ν΅ν΄μ μ΄λ£¨μ΄μ§λ©° Hibernate ORMμ λ΄λΆμ μΌλ‘ JDBC APIλ₯Ό μ΄μ©ν΄μ λ°μ΄ν°λ² μ΄μ€μ μ κ·Όνλ€.
 
- JPAμμλ νμ΄λΈκ³Ό λ§€νλλ μν°ν° κ°μ²΄ μ λ³΄λ₯Ό μμμ± μ»¨νμ€νΈ(Persistence Context)λΌλ κ³³μ λ³΄κ΄ν΄μ μ νλ¦¬μΌμ΄μ λ΄μμ μ€λ μ§μ λλλ‘ νλ€.
  
![αα΅α·αα§αΌαα‘α«αα΄ αα³αα³αα΅αΌ αα΅αΈαα?α«-014](https://user-images.githubusercontent.com/79316402/217281930-76a22a9e-e67f-4514-8b3f-3bbee049eb1e.png)

<br>

- 
