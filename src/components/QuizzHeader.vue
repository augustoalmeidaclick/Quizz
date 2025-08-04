<script setup>
import { defineProps } from "vue";
const { questionStatus, barPercentage } = defineProps([
  "questionStatus",
  "barPercentage",
]);
import { RouterLink } from "vue-router";
</script>

<template>
  <header>
    <RouterLink class="link" to="/">Voltar para a página principal</RouterLink>
    <h4>Questão {{ questionStatus }}</h4>
    <div class="bar">
      <div class="completion" :style="{ width: barPercentage }"></div>
    </div>
  </header>
</template>

<style scoped>
header {
  margin-top: 20px;
}
header h4 {
  font-size: 1.25rem;
  margin-top: 20px;
}

.bar {
  width: 300px;
  height: 50px;
  border: 3px solid #5494c9;
  border-radius: 20px;
}

.completion {
  height: 100%;
  width: 0%;
  background-color: #5494c9;
  border-radius: 15px;
}

.link {
  color: #5494c9;
  text-decoration: none;
  font-size: 1rem;
}
</style>
