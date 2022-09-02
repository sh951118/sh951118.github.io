---
layout: default
---

### **EFFECTIVE JAVA(이펙티브 자바) 3/E**
```
기술 용어(자바 8용 언어 명세)

Java 타입 -> 인터페이스, 클래스, 배열, 기본타입(4가지)
인터페이스 -> 어노테이션(annotation)
클래스 -> 열거타입(enum)

참조타입(reference type) -> 인터페이스, 클래스, 배열. 즉, 객체
```

> **1. 생성자 대신 static factory method를 고려하라**

```java
public class Test{
  int testi;

  public Test(int testi){
    this.testi = testi;
  }
  public static void main(String[] args){
      Test testdata = new Test(500);
  }
}

  // static method사용
public class Test{
  int testi;

  public Test(int testi){
    this.testi = testi;
  }
  public static Test staticMethod(int testi){
    this.testi = testi;
  }
  public static void main(String[] args){
      Test testdata1 = new Test(500);
      Test testdata2 = Test.staticMethod(500); // staticMethod라는 static메서드를 사용하여 의미를 전달
  }
}
```

> **2. 생성자에 매개변수가 많다면 빌더를 고려하라**

> - DTO, Model을 사용하는 경우에는 직접 빌더를 사용할 필요는 없으나 객체를 생성하는 대부분의 경우에는 빌더 패턴을 적용하는것이 좋다.

> **3. private 생성자나 열거 타입으로 싱글턴임을 보증하라**

> - 클래스를 싱글턴으로 만들면 이를 사용하는 클라이언트를 테스트하기 어려울 수 있다.
> - 싱글턴은 보통 두 방식 존재, 모두 생성자는 private로 감춰두고 유일한 인스턴스에 접근할 수 있는 수단으로 public static 멤버를 마련해둔다.

> **4. 인스턴스화를 막으려거든 private 생성자를 사용하라**

> - 인스턴스화란? 메소드와 변수를 모아놓은 것에 불과한 클래스를 사용할 수 있도록 Test tx = new Test()와 같이 선언을 통해 해당 클래스의 변수나 메소드를 사용 가능한 형태로 만드는 것.

> **5. 자원을 직접 명시하지 말고 의존 객체 주입을 사용하라**

> **핵심 정리**

- 클래스가 내부적으로 하나 이상의 자원에 의존하고, 그 자원이 클래스 동작에 영향을 준다면 싱글턴과 정적 유틸리티 클래스는 사용하지 않는것이 좋다. 이 자원들을 클래스가 직접 만들게 해서도 안된다.
- 필요한 자원들을 생성자 / 정적 팩터리 / 빌더 에게 넘겨주면 의존 객체 주입이라는 기법을 통해 유연성, 재사용성 등이 개선된다.

> **6. 불필요한 객체 생성을 피하라**

> **7. 다 쓴 객체 참조를 해제하라**
