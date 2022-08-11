---
layout: default
---

### **Iterator 란?**
Iterator는 자바의 컬렉션 프레임웍에서 컬렉션에 저장되어 있는 요소들을 읽어오는 방법을 표준화 하였는데 그 중 하나가 Iterator이다.<br/>
ArrayList, HashSet과 같은 컬렉션을 반복하는 데 사용할 수 있는 객체다. iterator는 반복의 기술 용어기 때문에 반복자라고 한다.

Iterator의 장점<br/>
1). 컬렉션에서 요소를 제어하는 기능<br/>
2). next() 및 previous()를 써서 앞뒤로 이동하는 기능<br/>
3). hasNext()를 써서 더 많은 요소가 있는지 확인하는 기능

<br/>

```java
import java.util.HashSet;
import java.util.List;

List<Integer> List = new List<Integer>();

List.add(4);
List.add(2);
List.add(3);
List.add(1);

// Iterator<E> 인터페이스
Iterator<Integer> iter = List.iterator();
while (iter.hasNext()) {
    System.out.print(iter.next() + " ");
}
// 실행결과 : 4 2 3 1


// ListIterator<E> 인터페이스
ListIterator<Integer> listiter = List.listIterator();
while (listiter.hasPrevious()) {  // 역순으로 출력
    System.out.print(listiter.previous() + " ");
}
// 실행결과 : 1 2 3 4


// 실전 예제 -> 데이터 조회 시 key값에 필요값을 조회한 경우 해당 값을 잘라내어 value에 넣음.
String keyValue;
for(Map<String, Object> item : updated) {
    iterator = item.keySet().iterator();
    while(iterator.hasNext()) {
      key = iterator.next();
      // key값을 담는다.
      if(key.indexOf("CHANGE_YN_") > -1) {
        keyValue = key.substring(10, key.length());
        parameters.put("P_EVAL_STEP_CD", keyValue);
      }
    }
}
```

### Iterator 인터페이스 메소드 ###

| 메소드                  | 설명                                  |
|:-----------------------|:--------------------------------------|
| boolean hasNext()      | 해당 이터레이션(iteration)이 다음 요소를 가지고 있으면 true를 반환하고, 더 이상 다음   요소를 가지고 있지 않으면 false를 반환함.                 |
| E next()               | 이터레이션(iteration)의 다음 요소를 반환함. |
| default void remove()  | 해당 반복자로 반환되는 마지막 요소를 현재 컬렉션에서 제거함. (선택적 기능)          |


### ListIterator 인터페이스 메소드 ###

| 메소드                  | 설명                                  |
|:-----------------------|:--------------------------------------|
| void add(E e)      | 해당 리스트(list)에 전달된 요소를 추가함. (선택적 기능)                 |
| boolean hasNext()               | 이 리스트 반복자가 해당 리스트를 "순방향"으로 순회할 때 다음 요소를 가지고 있으면 true를 반환하고, 더 이상 다음 요소를 가지고 있지 않으면 false를 반환함. |
| boolean hasPrevious()  | 이 리스트 반복자가 해당 리스트를 "역방향"으로 순회할 때 다음 요소를 가지고 있으면 true를 반환하고, 더 이상 다음 요소를 가지고 있지 않으면 false를 반환함.          |
| int nextIndex()  | 다음 next() 메소드를 호출하면 반환될 요소의 인덱스를 반환함.         |

<br/>

출처 : http://www.tcpschool.com/java/java_collectionFramework_iterator <br/>
출처: https://vaert.tistory.com/108 [Vaert Street:티스토리]
