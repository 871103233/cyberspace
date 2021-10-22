<template>
  <div class="log">
    <!-- <img alt="Vue logo" src="../assets/logo.png" /> -->
    <!-- <HelloWorld msg="Welcome to Your Vue.js App" /> -->
    <div class="left"></div>
    <div class="right">
      <div class="logInForm">
        <logInForm></logInForm>
      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
// import HelloWorld from "@/components/HelloWorld.vue";
import logInForm from "../components/logInForm.vue";
export default {
  name: "Home",
  components: {
    logInForm,
  },
  methods: {
    onSubmit() {
      console.log("submit!", this.form);
    },
  },
};
</script>

<style lang="less" scoped>
.log {
  height: 100%;
  display: flex;
  position: relative;
  overflow: hidden;
  .left {
    clip-path: polygon(0% 0, 61% 0, 41% 100%, 0% 100%);
    // background-color: lime;
    background-image: url("../assets/logBg.png");
    background-size: cover;
    height: 100%;
    width: 100%;
    position: absolute;
    border: none;
    animation: move 1s;
  }
  @keyframes move {
    0% {
      transform: translateX(-60%);
    }
    100% {
      transform: translateX(0%);
    }
  }
  .right {
    clip-path: polygon(60% 0%, 100% 0, 100% 100%, 40% 100%);
    // background-color: cyan;
    background-image: url("../assets/logBg.png");
    background-size: cover;
    height: 100%;
    width: 100%;
    right: 0;
    border: none;
    position: absolute;
    animation: moveRight 1s;
    .logInForm {
      height: 400px;
      width: 400px;
      position: absolute;
      right: 20%;
      top: 50%;
      transform: translateY(-50%);
      border: 2px solid red;
    }
  }
  @keyframes moveRight {
    0% {
      transform: translateX(60%);
    }
    100% {
      transform: translateX(0%);
    }
  }
}
</style>
