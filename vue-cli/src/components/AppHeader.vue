<template>
  <header>
    <h1>header</h1>
    <!-- 8. 싱글 파일 컴포넌트에서 이벤트 에밋 구현하기 -->
    <!--  -클릭 이벤트 정의 -->
    <button v-on:click="sendEvent">이벤트 보내기 버튼</button>
  </header>
</template>

<script>
export default {
  props: ["propsdata"],
  methods: {
    sendEvent: function () {
      this.$emit("pass"); // -위쪽 컴포넌트로 이벤트 전달, $this.emit("보낼 이벤트의 이름"), 올렸을 때 props의 값을 바꿔볼 것
    },
  },
};
</script>

<style>
</style>