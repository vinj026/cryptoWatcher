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
  width: 70%;
  background-color: rgba(113, 114, 113, 0.05);
  backdrop-filter: blur(2px);
  -webkit-backdrop-filter: blur(3px);
  box-shadow: 2px 2px 20px rgba(0, 0, 0, 0.3);
  z-index: 1;
  border-radius: 15px;
}

/* ===== Medium Screen (Tablet, 768px - 1024px) ===== */
@media (max-width: 1024px) {
  .cryptoCard {
    width: 100%;
    padding: 16px;
  }
}

@media (max-width: 768px) {
  .cryptoCard {
    width: 100%;
    border-radius: 5px;
    background: #0a0a09;
  }
}
</style>
