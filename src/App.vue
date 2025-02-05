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
  background-size: cover;
  background-repeat: no-repeat;
  background-image: url("./assets/071.jpg");
}

.container {
  max-width: 1100px;
  margin: 0 auto;
  height: 100%;
}

h1,
p {
  color: white;
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
