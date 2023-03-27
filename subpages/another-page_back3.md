---
layout: default
---

### **JUnit이란?**
단위 테스트 프레임워크
Spring Boot 2.2 이상 부터는 JUnit5의존성 기본 제공

JUnit4 -> 하나의 jar 파일로 의존성을 불러와 다른 라이브러리를 참조해서 사용하는 구조
JUnit5 -> 자체로 모듈화가 되어 있음. (Platform, Jupiter, Vintage) 실행 런처 및 구현체 제공

<br/>

> **JUnit 시작하기 및 방법**

#### 1. Spring Boot 2.2 이상인 경우 바로 JUnit5사용 / 아닐 경우 dependency 의존성 추가
#### 2. Annotations - @Test (테스트 메서드라는 것을 나타냄

```java
// JUnit4
@Test(expected = Exception.class)
 void create() throws Exception {
    ~~~
 }
// JUnit5
@Test
 void create() {
    ~~~
 }
```

#### 3. Annotations - 생명주기(LifeCycle) 어노테이션 
    - @BeforeAll : 해당 클래스에 위치한 모든 테스트 메서드 실행 (전)에 딱 한 번 실행되는 메서드 (JUnit4, @BeforeClass)
    - @AfterAll : 해당 클래스에 위치한 모든 테스트 메서드 실행 (후)에 딱 한 번 실행되는 메서드 (JUnit4, @AfterClass)
    - @BeforeEach : 해당 클래스에 위치한 모든 테스트 메서드 실행 (전)에 실행되는 메서드 (JUnit4, @Before)
    - @AfterEach : 해당 클래스에 위치한 모든 테스트 메서드 실행 (후)에 실행되는 메서드 (JUnit4, @After)
 
(테스트가 조건들에 대해 영향을 절대 미치지 않는다면 @BeforeAll / @AfterAll, 영향을 끼칠 수 있다면 테스트 실행마다 조건이 초기화 되도록 @BeforeEach / @AfterEach 사용 )

#### 4. Annotations - @Disabled 
 - 테스트를 하고 싶지 않은 클래스나 메서드에 붙이는 어노테이션
 - JUnit4에서는 @Ignore과 유사

#### 5. Annotations - @DisplayName (JUnit5에서만 사용)
 - 어떤 테스트인지 쉽게 표현할 수 있도록 해주는 어노테이션(공백, 특수문자 등 모두 지원)

```java
@DisplayName("특수문자\입력u100\가능")
class DisplayNameExample {
    @Test
    @DisplayName("테스트중")
    void test(){

    }
}
```
#### 6. Annotations - @RepeatedTest 
 - 특정 테스트를 반복시키고 싶을 때 사용하는 어노테이션 / 반복 횟수와 테스트 이름을 설정가능

```java
@RepeatedTest(value = 10, name = "{displayName} / {currentRepetition} / {totalRpetitions}")
@DisplayName("반복")
void test(){

}
```

#### 7. Annotations - @Nested 
 - 테스트 클래스 안에서 내부 클래스를 정의해 테스트를 계츨화 할 때 사용
 - 내부클래스는 부모클래스의 멤버 필드에 접근가능
 - Before / After와 같은 테스트 생명주기에 관계된 메소드들도 계층에 맞춰 동작