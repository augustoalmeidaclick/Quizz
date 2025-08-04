<script setup>
import { defineProps } from "vue";
import { RouterLink } from "vue-router";

const { numberOfCorrectAnswers } = defineProps([
  "quizzQuestionLength",
  "numberOfCorrectAnswers",
]);
</script>

<template>
  <div class="results">
    <p key="congrats">Parabéns!</p>
    <p key="score-text">Você acertou...</p>
    <h1 key="score">{{ numberOfCorrectAnswers }}/{{ quizzQuestionLength }}</h1>
    <RouterLink key="back" to="/" class="link">Voltar</RouterLink>
  </div>
</template>

<style scoped>
.link {
  color: #5494c9;
  text-decoration: none;
  font-size: 1.5rem;
}

.results {
  text-align: center;
  padding: 50px 0;
}

p {
  font-size: 1.56rem;
}

h1 {
  font-size: 5rem;
}
</style>
