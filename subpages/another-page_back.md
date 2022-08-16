---
layout: default
---

### **자료형 변환 정리( ~ to ~ )**

<br/>

## **In Java**
```java
// String to int
String to_str = "10";
int to_num = Integer.parseInt(to_str); // 기본 자료형
int to_num = Intege.valueOf(to_str);  // 객체
// double and float
double d_num = Double.valueOf(to_str);
float f_num = Float.valueOf(to_str);

// int to String
int to_num = 10;
String to_str = Integer.toString(to_num);
```

<br/>

## **In JavaScript**

```js
// JavaScript 예시
var to_int = parseInt("10"); // 정수
var to_int = Nember("10");   // 정수&실수
var to_float = parseFloat('100.99') // 실수
var to_str = String(10);
var to_str = 10 + "";

var x = 123;
var a = x.toFixed(1);    //문자형 123.0
```
