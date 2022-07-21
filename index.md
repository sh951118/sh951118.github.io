---
layout: default
---
<!-- MarkDown 텍스트 예시 : Text can be **bold**, _italic_, or ~~strikethrough~~. -->
### **경험 언어 Stack**
- Back-end item
  - Java 　　　　　　　　　　　　　　　　　　 　 　　　　![Octocat](https://img.shields.io/badge/JAVA-007396?style=flat&logo=java&logoColor=white)
  - Apache(Web Server) / Tomcat(WAS)　　　　　　　　　![Octocat](https://img.shields.io/badge/Apache-D22128?style=flat&logo=Apache&logoColor=white)
  - Spring / Spring Boot / MSA(공부중..)　　　　　　　　　![Octocat](https://img.shields.io/badge/Spring-6DB33F?style=flat&logo=Spring&logoColor=white) ![Octocat](https://img.shields.io/badge/Spring Boot-6DB33F?style=flat&logo=Spring Boot&logoColor=white)
  - DataBase(관계형)
    - MariaDB / MySql(same)　　　　　　　　　　　　![Octocat](https://img.shields.io/badge/MariaDB-003545?style=flat&logo=MariaDB&logoColor=white)
    - Oracel / Tibero(same?)　　　　　　　 　　　　　![Octocat](https://img.shields.io/badge/Oracle-F80000?style=flat&logo=Oracle&logoColor=white)
- Front-end item
  - JavaScript / HTML / CSS　　　　　　　　　　　　　　　![Octocat](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat&logo=JavaScript&logoColor=white) ![Octocat](https://img.shields.io/badge/HTML5-E34F26?style=flat&logo=HTML5&logoColor=white) ![Octocat](https://img.shields.io/badge/CSS3-1572B6?style=flat&logo=CSS3&logoColor=white)
    - Jquery　　　　　　　　　　　　　　　 　　　　　![Octocat](https://img.shields.io/badge/jQuery-0769AD?style=flat&logo=jQuery&logoColor=white)
    - Bootstrap　　　　　　　　　　　　　    　 　　　　![Octocat](https://img.shields.io/badge/Bootstrap-7952B3?style=flat&logo=Bootstrap&logoColor=white)
    - React.js　　　　　　　　　　　　　　    　 　　　　![Octocat](https://img.shields.io/badge/React-61DAFB?style=flat&logo=React&logoColor=white) ![Octocat](https://img.shields.io/badge/Redux-764ABC?style=flat&logo=Redux&logoColor=white)
      - Redux
  - node.js / Ruby(블로그 만들면서 사용 jekyll)　　 　　　　![Octocat](https://img.shields.io/badge/Node.js-339933?style=flat&logo=Node.js&logoColor=white) ![Octocat](https://img.shields.io/badge/Ruby-CC342D?style=flat&logo=Ruby&logoColor=white)
    - npm
- DevOps(CI/CD)
  - GitLab(Git)　　　　　　　　　　　　　　　　　　　　　![Octocat](https://img.shields.io/badge/GitLab-FC6D26?style=flat&logo=GitLab&logoColor=white) ![Octocat](https://img.shields.io/badge/GitHub-181717?style=flat&logo=GitHub&logoColor=white) ![Octocat](https://img.shields.io/badge/Git-F05032?style=flat&logo=Git&logoColor=white)
  - Jenkins　　　　　　　　　　　　　　　　　　　　　　　![Octocat](https://img.shields.io/badge/Jenkins-D24939?style=flat&logo=Jenkins&logoColor=white)

- Development tools
  - Eclipse(IntelliJ / AWS 사용해보고 싶다..)
  - VsCode
  - DBeaver

<br/>

### **개발 경력 List**

| 기 간             | 기 관 / 장 소                          |
|:------------------|:--------------------------------------|
| 2014-02 ~ 2020-02 | 인제대학교(컴퓨터공학)                 |
| 2020-01 ~ 2020-07 | 비트교육센터(Java-FullStack 전문가과정)|
| 2020-08 ~ 진행중  | 더존비즈온(HR 평가/급여, ERP)          |

<br/>

### **전공 독서 List**

| 책 이름                         | 저 자 / 내 용                                     |
|:-------------------------------|:--------------------------------------------------|
| Doit! 자바스크립트+제이쿼리 입문 | 정인용 / front-end 반응형 웹 개발 [자세히 보기(.md)](./subpages/book1.html)                 |
| 이펙티브 자바                   | 조슈아 블로크 / Java 관련 기초 문법 및 활용 [자세히 보기(.md)](./reference-page1.html)        |

<br/>

### 개발 자료실

> **기본. 자료형 변환 정리( ~ to ~ )**
 [자세히 보기(.html)](./reference-page1.html)

```java
// Java, String to Int 예시
String to_str = "10";
int to_num = Integet.parseInt(to_str); // 기본 자료형
int to_num = Integet.valueOf(to_str);  // 객체
```
```js
// JavaScript 예시
var to_int = parseInt("10"); // 정수
var to_int = Nember("10");   // 정수&실수
var to_str = String(10);
var to_str = 10 + "";
```

> **Back-end 기본. interface Iterator**
 [자세히 보기(.md)](./another-page2.html)

```java
public interface Iterator {
  boolean hasNext();
  Object next();
  void remove();
}
```

> **Back-end 기본. 람다식(Lambda) / 스트림(stream)**
 [자세히 보기(.md)](./another-page3.html)

```java
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

> **Front-end 기본. Promise**
 [자세히 보기(.md)](./another-page4.html)

```javascript
// 함수 안에서 Promise 생성 시, .then으로 시행주기 잡아냄.
Test().then(function(){
  // resolve()를 탄 경우
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
```

### Small image

![Octocat](https://github.githubassets.com/images/icons/emoji/octocat.png)

### Large image

![Branching](https://guides.github.com/activities/hello-world/branching.png)

```
Long, single-line code blocks should not wrap. They should horizontally scroll if they are too long. This line should be long enough to demonstrate this.
```

```
The final element.
```
