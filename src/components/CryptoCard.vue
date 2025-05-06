<script setup>
import CryptoItem from "./CryptoItem.vue";
</script>

<template>
  <div class="cryptoCard">
    <CryptoItem />
  </div>
</template>

<style lang="css" scoped>
.cryptoCard {
  width: 75%;
  height: 50vh;
  background-color: rgba(113, 114, 113, 0.05);
  backdrop-filter: blur(2px);
  -webkit-backdrop-filter: blur(3px);
  box-shadow: 2px 2px 20px rgba(0, 0, 0, 0.3);
  z-index: 1;
  border-radius: 15px;
}
</style>
