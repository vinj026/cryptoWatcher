<script setup>
import CryptoCard from "./components/CryptoCard.vue";
import GridDot from "./components/bg/GridDot.vue";
import GradientBottom from "./components/bg/GradientBottom.vue";
</script>

<template>
  <div class="appWraper">
    <CryptoCard />
    <GridDot class="bg" />
    <GradientBottom class="bg" />
  </div>
</template>

<style scoped>
.appWraper {
  display: flex;
  align-items: center;
  justify-content: center;
  position: relative;
  min-height: 100vh;
  overflow: hidden;
}

.bg{
  z-index:0;
}
</style>
