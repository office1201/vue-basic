<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png" />
    <HelloWorld msg="Welcome to Your Vue.js App" />
    <!-- 4. 컴포넌트 명명법 (케밥, 파스칼, 파스칼(진보됨) -->
    <!--  -무조건 2단어 이상, 불러왔을 때 HTML태그와 혼동을 피하기 위함 -->
    <!-- <hello-world></hello-world>  -->
    <!-- <HelloWorld></HelloWorld> -->
    <!-- <HelloWolrd /> -->

    <!-- 5. 5번 적용(데이터 바인딩~) -->
    {{ str }}
    <!-- 6. 컴포넌트 적용하기 -->
    <!-- <app-header></app-header> -->

    <!-- 7. 싱글 파일 컴포넌트에서 props 속성 적용방법 -->
    <!-- <app-header v-bind:프롭스 속성 이름="상위 컴포넌트의 데이터 이름"></app-header> -->
    <!-- - 8번, 하위 컴포넌트에서 올라온 이벤트 받기 => 인스턴스 데이터 건드리기, 실행할 메서드 이름 -->
    <app-header v-bind:propsdata="str" v-on:pass="passStr"></app-header>
  </div>
</template>

<script>
// 6. 컴포넌트 불러오기
import AppHeader from "./components/AppHeader.vue";

// 1. 싱글 파일 컴포넌트를 보면서 문법적으로 바뀐 부분 숙지
import HelloWorld from "./components/HelloWorld.vue";

// 3. 아래 props와 동일한 구조
// const content = {
//   props: ["propsdata"],
// };

// 5. 기존 방식의 컴포넌트 재사용이 너무 많아짐에 따라 객체가 아닌 아래의 함수형태로 또 함수가 새 객체를 반환 형식으로 작성
// new Vue({
//  data: {
//  }
// });

// 2. export default ==== new Vue({})
export default {
  name: "App",
  data: function () {
    return {
      str: "header",
    };
  },
  components: {
    HelloWorld, // "hello world": HelloWorld
    // 6. 컴포넌트 등록하기
    "app-header": AppHeader,
  },
  // 3. props: ["msg"]와 동일
  props: {
    msg: String, // 3. msg에 타입까지 들어있는 것 뿐
  },
  methods: {
    // 8번, v-on:pass="passStr"로 해당된 메서드 실행
    passStr: function () {
      this.str = "hi";
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
