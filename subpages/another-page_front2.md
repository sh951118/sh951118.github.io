---
layout: default
---

### **this란?**
대부분의 언어에서 'this'는 클래스가 인스턴스화 한 현재 객체에 대한 참조입니다.<br/>
반면, 자바스크립트에서 'this'는 일반적으로 함수를 호출하는 객체에 대한 참조입니다.

<br/>

> **this를 어떻게 호출했는가?**

```javascript
var car = '국산차';
var buy = {
  car : '외제차',
  buycar: buyCars
}

function buyCars() {
  console.log(`나는 ${this.car}를 탑니다.`);
}

// (1) 객체 method 호출
buy.buycar(); // 나는 외제차를 탑니다.

// (2) 함수 직접 호출
buyCars(); // 나는 국산차를 탑니다.

//home의 메서드로 호출한 this는 호출한 객체를 가리킴으로 this는 home이 되나,
//(2)와 같이 함수를 직접 호출하는 경우는 bind되어 있지 않기 때문에 전역 즉, this는 window를 가리킴.

// 추가 1.
// 이처럼 newCar라는 변수를 새로 선언 하여도 일반 함수 형태의 호출은 this는 window
var newCar = buy.buycar;
newCar();
```

- **번외1.**

```javascript
var car = '국산차';
var buy = {
  car : '외제차',
  buycar: function(){
    buyCars();
  }
}

function buyCars() {
  console.log(`나는 ${this.car}를 턉니다.`);
}

buy.buycar(); // 나는 국산차를 탑니다.
```

> buy.buycar()의 형태로 호출하긴 했지만, 호출된 함수는 buyCars()이 아닌 외부 함수입니다.<br/>
> 'this'를 사용하는 buyCars() 함수는 바인딩 없이 일반 함수의 형태로 호출되었습니다. 따라서 this는 window입니다.


- **번외2. 생성자 함수**
```javascript
var newcar = '아반떼';

function getcarname() {
  console.log(`제가 살 차는 ${this.newcar}입니다.`);
}

// 생성자 함수
function HyundaiCar(name) {
  this.newcar = name;
  this.reply = getcarname;
}

// 새로운 거울 생성
var newHyundaiCar = new HyundaiCar('투싼');

newHyundaiCar.reply(); // 제가 살 차는 투싼입니다.
```


<br/><br/><br/>
출처: https://paperblock.tistory.com/44 <br/>
