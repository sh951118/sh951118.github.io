---
layout: default
---

### **Do it! 자바스크립트 + 제이쿼리 입문 스킬정리**
```
단축키 정리(VS Code) 책 외에 지식 포함
Ctrl + N -> 새문서
Ctrl + C -> 해당 경로에 해당 파일이름 편집
Ctrl + B -> 좌측, 파일 탐색기 제거/오픈

소스코드 (※ ~> 이 후)
html:5 ~> Tab -> body를 제외한 영역 자동입력
```

> Script와 HTML은 외부로 분리하여야 한다. 그 이유는 JS소스 손상 방지 및 프로젝트 관리를 원활하게 하기 위함.<br/>
> -> 회사 기준에 따라 다른것 같다. html파일만을 위주로 배포하는 회사의 경우 JS로 뺄 경우에 관리가 어렵게 느낌.(내부 플랫폼 사용)
```
<script src="JS파일 경로"></script>
```

> **while  vs  do while**

```javascript
//while은 조건식을 먼저 검사한 후에 코드 실행여부 결정
while(조건문){
  코드 / 증감식 등.
}

//do while은 반드시 한 번은 코드 실행 후에 조건식 검사.
do{
  코드 / 증감식 등.
}while(조건문)
```

> **브라우저 객체 모델(BOM) VS 문서 객체 모델(DOM)**

```
브라우저 객체 모델(BOM) -> 브라우저에 계층 구조로 내장되어 있는 객체.
                          window, location, history, navigator 등이 있으며 윈도우 상단의 옵션.
                  window.open("url", "창 이름", "옵션") = 페이지 새 창으로 나타냄
                  window.confirm("질문 내용") = 질문과 답변으로 질의응답 창을 나타냄
                  window.moveTo(x, y) = 새 창의 위치 이동
                  window.setTimeout(function(){코드}) = 한 번 일정한 시간 간격으로 함수 호출하여 코드 실행

                  location.href = 주소 영역의 참조 주소 설정 및 URL반환
                  location.host = URL의 호스트 이름과 포트 번호 반환
                  location.reload() = 브라우저 F5 키를 누른 것과 동일(새로고침)

                  history.back() = 이전 방문 사이트로 이동
                  history.forward() = 다음 방문 사이트로 이동
                  history.length = 방문 기록에 저장된 목록의 개수 반환

                  navigator는 접속한 브라우저의 속성 및 운영체제 등 정보 조회용

문서 객체 모델(DOM) -> HTML 구조를 의미, html의 모든 요소들을 문서 객체로 선택해서 자유롭게 속성 변경 가능
                      Jquery 문서 객체 모델 / javascript 문서 객체 모델이 있음.(Jquery를 많이 사용)
```

> **객체 생성자 함수**

```javascript
// 객체 생성자 함수명은 소문자로 시작해도 되지만 가능하면 단어별 첫문자는 대문자로 사용
ex.) var test = new GetTest(data1, data2);
```

> **메모리 절약을 위한 프로토타입(prototype) 사용**

```javascript
function GetTestSetting(id, password){
  this.userId = id;
  this.userPassword = password;
}

GetTestSetting.prototype.getId = function(){
  var str = "";
  str += "아이디는 " + this.userId;
  return str;
}

GetTestSetting.prototype.getPassword = function(){
  var str = "";
  str += "비밀번호는 " + this.userPassword + " 입니다.";
  return str;
}

var test1 = new GetTestSetting("1", "1234");
var test2 = new GetTestSetting("1", "4567");

test1.getId(); // "아이디는 1"
test1.getPassword(); // "비밀번호는 1234 입니다."

test1.getId() === test2.getId() // 해당 결과는 true, 두 객체가 같은 함수를 사용하고 있음을 의미.

```

> **함수 return 문의 역할**

```javascript
function 함수명(num1, num2){
  return num1 + num2;
}

var result = sum(10 + 20);
// result = 30;
```

> **즉시 실행 함수**

```javascript
// 즉시 실행 함수는 함수의 충돌을 방지하기 위해 해당 함수 안에서 지역함수로 호출 함.
(function(){
  var num = 100;

  function menu(){
    num += 100;
    console.log(num); // 200;
  }
  menu();
}());
```
