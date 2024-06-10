<script setup></script>

<template>
  <button>
    <slot> create </slot>
  </button>
</template>

<style lang="scss" scoped>
button {
  padding: 8px 16px;
  border: none;
  background-image: linear-gradient(
    rgba(4, 19, 156, 0.5),
    rgba(5, 235, 228, 0.5)
  );
}
</style>
