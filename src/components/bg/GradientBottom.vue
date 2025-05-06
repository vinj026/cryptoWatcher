<template>
  <div class="gradient-bottom"></div>
</template>

<script setup></script>

<style lang="css" scoped>
.gradient-bottom {
  width: 100%;
  height: 300px;
  background-image: linear-gradient(to bottom,
      #72ab76,
      #5f8f62,
      #4d734f,
      #3c593d,
      #2b402c);
  border-radius: 50%;
  position: absolute;
  filter: blur(8.5rem);
  bottom: -170px;
}
</style>
