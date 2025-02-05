<script setup>
import { RouterLink } from "vue-router";
</script>

<template>
  <header>
    <nav class="container">
      <div class="branding">
        <h2 class="text">My Todos</h2>
      </div>
      <ul class="nav-routes">
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/about">About</RouterLink>
      </ul>
    </nav>
  </header>
</template>

<style lang="scss" scoped>
header {
  padding: 16px;
  background-color: #000;
  opacity: 50%;
  box-sizing:
    0 4px 8px 0 rgba(0, 0, 0, 0.2),
    0 6px 20px 0 rgba(0, 0, 0, 0.19);

  nav {
    display: flex;
    align-items: center;
    padding: 16px;

    .branding {
      display: flex;
      align-items: center;
      gap: 8px;

      img {
        max-width: 50px;
      }

      h2 {
        font-size: 32px;
        color: #fff;
      }
    }

    .nav-routes {
      color: white;
      display: flex;
      flex: 1;
      justify-content: flex-end;
      gap: 12px;
      list-style: none;

      a {
        text-decoration: none;
        color: inherit;
      }
    }
  }
}
</style>
