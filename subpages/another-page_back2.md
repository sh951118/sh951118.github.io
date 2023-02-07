---
layout: default
---

### **람다함수란?**
람다 함수는 프로그래밍 언어에서 사용되는 개념으로 익명 함수(Anonymous functions)를 지칭하는 용어입니다.<br/>
즉, 함수를 보다 단순하게 표현하는 방법입니다.<br/>
일급 객체란 일반적으로 다를 객체들에 적용 가능한 연산을 모두 지원하는 개체를 가르킵니다.<br/>
함수를 값으로 사용 할 수도 있으며 파라메터로 전달 및 변수에 대입 하기와 같은 연산들이 가능합니다.

람다의 장점<br/>
1). 코드의 간결성 - 람다를 사용하면 불필요한 반복문의 삭제가 가능하며 복잡한 식을 단순하게 표현할 수 있습니다.<br/>
2). 지연연산 수행 - 람다는 지연연상을 수행 함으로써 불필요한 연산을 최소화 할 수 있습니다.<br/>
3). 병렬처리 가능 - 멀티쓰레드를 활용하여 병렬처리를 사용 할 수 있습니다.

람다의 단점<br/>
1). 람다식의 호출이 까다롭습니다. / 디버깅이 어렵다.<br/>
2). 람다 stream 사용 시 단순 for문 혹은 while문 사용 시 성능이 떨어집니다.(재귀 포함)<br/>
3). 불필요하게 너무 사용하게 되면 오히려 가독성을 떨어 뜨릴 수 있습니다.

<br/>

> **람다의 표현식**

```java
() -> {}
() -> 1
() -> { return 1; }

(int x, int y) -> x+y
(x, y) -> x+y
(x, y) -> { return x+y; }

(String lam) -> lam.length()
lam -> lam.length()
(Thread lamT) -> { lamT.start(); }
lamT -> { lamT.start(); }

//잘못된 유형 선언된 type과 선언되지 않은 type을 같이 사용 할 수 없다.
(x, int y) -> x+y
(x, final y) -> x+y

// 기존 자바 문법1.
new Thread(new Runnable() {
   @Override
   public void run() {
      System.out.println("Welcome Heejin blog");
   }
}).start();

// 람다식 문법
new Thread(()->{
      System.out.println("Welcome Heejin blog");
}).start();


// 기존 자바 문법2.
(매개변수, ...) -> { 실행문 ... }

new Test(new Rambda(){
    public void run(){
      System.out.println("람다식");
    }
})

new Test(()->{
  System.out.println("람다식");
})
```

> **함수형 인터페이스 @FunctionalInterface**

Functional Interface는 일반적으로 '구현해야 할 추상 메소드가 하나만 정의된 인터페이스'를 가리킵니다.<br/>
자바 컴파일러는 이렇게 명시된 함수형 인터페이스에 두 개 이상의 메소드가 선언되면 오류를 발생시킵니다.


```java
//구현해야 할 메소드가 한개이므로 Functional Interface이다.
@FunctionalInterface
public interface Math {
    public int Calc(int first, int second);
}

//구현해야 할 메소드가 두개이므로 Functional Interface가 아니다. (오류 사항)
@FunctionalInterface
public interface Math {
    public int Calc(int first, int second);
    public int Calc2(int first, int second);
}
```

> **Java의 함수형 인터페이스 4가지**

| 메소드                  | 설명                                  |
|:-----------------------|:--------------------------------------|
| Supplier<T>             | Supplier는 매개변수 없이 반환값 만을 갖는 함수형 인터페이스 |
| Consumer<T>             | Consumer는 객체 T를 매개변수로 받아서 사용하며, 반환값은 없는 함수형 인터페이스 |
| Function<T, R>          | Function은 객체 T를 매개변수로 받아서 처리한 후 R로 반환하는 함수형 인터페이스  |
| Predicate<T>            | Predicate는 객체 T를 매개 변수로 받아 처리한 후 Boolean을 반환  |

<br/>

### **Stream 이란?**
<br/>
스트림은 '데이터의 흐름’입니다. 배열 또는 컬렉션 인스턴스에 함수 여러 개를 조합해서 원하는 결과를 필터링하고 가공된 결과를 얻을 수 있습니다.  <br/>
또한 람다를 이용해서 코드의 양을 줄이고 간결하게 표현할 수 있습니다. 즉, 배열과 컬렉션을 함수형으로 처리할 수 있습니다.

| 선언문(예시)            | 설명                                  |
|:-----------------------|:--------------------------------------|
| stream()               | 스트림생성 |
| filter                 | 중간 연산 (가공하기) - 연속에서 수행 가능합니다. |
| count                  | 최종 연산 (결과) - 마지막에 단 한 번만 사용 가능합니다.  |

```java
example.stream().filter(x -> x < 2).count

// 실전 예제 1.
for(Model parent : itemMst) {
    parent.setItems(itemSdtl.stream() // 리스트 반복문
        .filter(child -> child.getEmp_no().equals(parent.getEmp_no())) // 특정 조건으로 거른다. child -> 람다표기법 반복문 이해
        .collect(Collectors.toList())); // 모은다 // 저장한다.
        //Collector 연산, Stream의 요소를 수집하여 요소를 그룹화 하거나 결과를 담아 반환하는데 사용한다.
}
// 실전 예제 2.
for(Model mstItem :mstList) {
    Map<String, List<Model>> mapChild = childList.stream()
        .filter(p-> p.getUp_dept_cd()!=null && !p.getUp_dept_cd().replace(" ", "").equals("") )
        .sorted(Comparator.comparing(p -> p.getDept_cd())) // comparing은 Function<T,R>을 인자로 받음.(정렬 변경)
        .collect(Collectors.groupingBy(p -> p.getUp_dept_cd())); // GroupingBy 를 이용하면 데이터 집합을 하나 이상의 특성으로 분류, 그룹화하는 연산
}
```
List<Fedu100VO> newModel = new ArrayList<Fedu100VO>();
            for(Fedu100VO data : dataList) {
            	if(data.getAddr1() == data.getAddr2()) {
            		newModel.add(data);
            	}
            }
            List<Fedu100VO> data = dataList.stream()
            		.filter(x -> x.getAddr1() == x.getAddr2())
            		.collect(Collectors.toList());

                    
> **Stream 가공하기 종류(중간연산)**
1. [ 필터링 - Filter ]
2. [ 데이터 변환 - Map ]
3. [ 정렬 - Sorted ]
4. [ 중복 제거 - Distinct ]
5. [ 특정 연산 ] -> sum 등등

> **Stream 결과 만들기(최종연산)**
1. [ 최댓값/최솟값/총합/평균/갯수 - Max/Min/Sum/Average/Count ]
2. [ 데이터 수집 - collect ]
3. [ 조건 검사 - Match ]

> **Stream Collectors 종류**
1. Collectors.toList() -> into a List
2. Collectors.toCollection(TreeSet::new) -> into a 특정 Collection(Tree, LinkedList 등.)
3. Collectors.toMap("key", String::length) -> into a Map (keyMapper, valueMapper)
4. Collectors.joining(", ") -> List가 아닌 String으로 붙여주거나 할 때
5. Collectors.groupingBy() -> group by



<br/><br/><br/>
출처: https://khj93.tistory.com/entry <br/>
출처: https://mangkyu.tistory.com/114 [MangKyu's Diary:티스토리]<br/>
