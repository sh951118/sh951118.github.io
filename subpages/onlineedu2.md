---
layout: default
---

### **Vue.js 중급강좌**

>**설정관련 정리**

 <a href="https://start.spring.io">Spring 초기 프로젝트 생성 url</a>
 
 <p style="color: antiquewhite;">반응형 웹테그 검색 -> meta viewport</p> 
 
```
 프로젝트 시작 명령어

 vue init webpack-simple 프로젝트명 > 프로젝트 경로 이동 > npm i
 를 통해서 프로젝트 생성 시, webpack형식이며 package.json에 name/description 등 기초 데이터 입력 가능.

 npm i -g @vue/cli-init
 vue 버전 선택 후, 자동 생성 
```

>**App.vue 메인 페이지**

```js
<template>
  <div id="app">
    <TodoHeader></TodoHeader>
    <TodoInput></TodoInput>
    <TodoList></TodoList>
    <TodoFooter></TodoFooter>
  </div>
</template>

<script>
// react와 동일하게 페이지를 import하여 렌더링
import TodoHeader from './components/TodoHeader.vue'
import TodoInput from './components/TodoInput.vue'
import TodoList from './components/TodoList.vue'
import TodoFooter from './components/TodoFooter.vue'

// var my_cmp = {
//   template : '<div>my component</div>'
// };
// new Vue({
//   el: '',
//   components: {
//     'my_cmp': my_cmp
//   }
// });
// 위의 과정이 ES5

export default {
  components: {
      //컴포넌트 태그명 : 컴포넌트 내용
      'TodoHeader' : TodoHeader,
      'TodoInput' : TodoInput,
      'TodoList' : TodoList,
      'TodoFooter' : TodoFooter
  }
}
</script>

<style>

</style>

```