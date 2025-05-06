<template>
  <div class="itemContainer"></div>
</template>

<script setup></script>

<style lang="css" scoped>
.itemContainer {
  display: grid;
  grid-template-areas: "coin" "price" "1h" "24h" 7d "volume" "marketcap";
  width: 100%;
  height: 100vh;
}
</style>
