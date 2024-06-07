<template>
  <div class="about">
    <h1 class="text">Here We Go!</h1>
    <p class="text">
      Let's mark down our important tasks and mark it according to it's updates!
    </p>
    <p class="text">Small Steps leads to a Great Success!</p>
  </div>
</template>

<style>
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

@media (min-width: 1024px) {
  .about {
    height: 100%;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    padding-top: 40px;
  }
}
</style>
