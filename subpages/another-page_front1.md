---
layout: default
---

### **Promise란?**
프로미스는 자바스크립트 비동기 처리에 사용되는 객체<br/>
비동기 처리란 ‘특정 코드의 실행이 완료될 때까지 기다리지 않고 다음 코드를 먼저 수행하는 자바스크립트의 특성’을 의미<br/>
예를 들어, 서버에서 데이터를 요청하고 받아오기 위해 API를 실행하고 서버에 요청을 보내는데<br/>데이터를 받아오기도 전에 마치 데이터를 다 받아온 것 마냥 화면에 데이터를 표시하려고 하면 오류가 발생함으로<br/> 이와 같은 문제점을 해결하기 위한 방법 중 하나가 Promise임.

<br/>

> **Promise의 사용법**

```javascript
// 간단한 api 통신과 Promise

// JavaScript 사용법.
Test().then(function(){
  // resolve()를 탄 경우 함수 안에서 Promise 생성 시, .then으로 시행주기 잡아냄.
}).catch(function(){
  // reject()를 탄 경우
});
...
function Test(){
    return new Promise(function(resolve, reject) {
      api((~url){
        .....
      }).done(
        resolve();
      ).fail(){
        reject();
      }
    });
}

// jQuery 사용법
var deferred = $.Deferred();
api(url(~~~url), {
    data: {
        dsEvalTargetMst: JSON.stringify(checkedRows)
    }
}).done(function (data) {
    deferred.resolve();   //성공  -> 이후에 다른 API를 선언하고 호출해야 함.
}).fail(function (xhr, status, error) {
    deferred.reject();    //실패
});
return deferred.promise();
```

> **프로미스의 3가지 상태(states)**

| 메소드                  | 설명                                  |
|:------------------------|:--------------------------------------|
| Pending(대기)           | 비동기 처리 로직이 아직 완료되지 않은 상태 |
| Fulfilled(이행)         | 비동기 처리가 완료되어 프로미스가 결과 값을 반환해준 상태 |
| Rejected(실패)          | 비동기 처리가 실패하거나 오류가 발생한 상태  |

<br/>

### **여러 개의 프로미스 연결하기 (Promise Chaining)**

```javascript
// 넘긴 값에 대하여 이행 상태의 로직을 거쳐 최종값 반환.
new Promise(function(resolve, reject){
  // setTimeout(function() {
    resolve(1);
  // }, 2000);
})
.then(function(result) {
  console.log(result); // 1
  return result + 10;
})
.then(function(result) {
  console.log(result); // 11
  return result + 20;
})
.then(function(result) {
  console.log(result); // 31
});
```


<br/><br/><br/>
출처: https://joshua1988.github.io/web-development/javascript/promise-for-beginners/ <br/>
