<script setup>
import { RouterView } from "vue-router";
import TodoHeader from "./components/TodoHeader.vue";
</script>

<template>
  <TodoHeader />
  <RouterView />
</template>

<style lang="scss">
@import url("https://fonts.googleapis.com/css2?family=Roboto:ital,wght@0,100;0,300;0,400;0,500;0,700;0,900;1,100;1,300;1,400;1,500;1,700;1,900&family=Rubik:ital,wght@0,300..900;1,300..900&display=swap");

* {
  font-family: "Rubik", sans-serif;
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  min-height: 100vh;
  background-image: linear-gradient(
      rgba(98, 112, 237, 0.5),
      rgba(174, 244, 241, 0.5)
    ),
    url("src/assets/feather.png");
}

.container {
  max-width: 1100px;
  margin: 0 auto;
  height: 100%;
}

h1,
p {
  background-clip: text;
  -webkit-background-clip: text;
  color: transparent;
  background: linear-gradient(
    90deg,
    rgba(2, 0, 36, 1) 0%,
    rgba(9, 9, 121, 1) 35%,
    rgba(0, 212, 255, 1) 100%
  );
}

h1 {
  padding-bottom: 8px;
}

p {
  padding-top: 8px;
  padding-bottom: 8px;
}

.text {
  background-clip: text;
  -webkit-background-clip: text;
  color: rgb(0 0 0 / 20%);
}
</style>
