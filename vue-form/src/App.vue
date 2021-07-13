<template>
  <!-- 세번째로 할 일: 브라우저 기본 기능 취소하기 -->
  <form>
    <div>
      <!-- 두번째로 할 일: v-model is for two way bindings -->
      <label for="username">id: </label>
      <input id="username" type="text" v-model="username" />
    </div>
    <div>
      <label for="password">pw: </label>
      <input id="password" type="password" v-model="password" />
    </div>
    <button v-on:click="submitForm">login</button>
  </form>
</template>

<script>
// 네번째: axios를 써 보기
import axios from "axios";

// 첫번째로 할 일: 컴포넌트 간에 데이터가 공유되지 않게, 값이 참조가 되서 공유되지 않게, 함수를 이용해서 새 객체를 리턴하는 구문으로 작성
export default {
  data: function () {
    return {
      username: "",
      password: "",
    };
  },
  methods: {
    submitForm: function (e) {
      e.preventDefault();
      // 다섯번째: axios 적용
      const url = "https://jsonplaceholder.typicode.com/users";
      const data = {
        username: this.username,
        password: this.password,
      };
      axios
        .post(url, data)
        .then((res) => console.log(res))
        .catch((err) => console.log(err));
    },
  },
};
</script>

<style>
</style>