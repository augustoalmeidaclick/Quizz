<script setup>
import { useRouter } from "vue-router";
const router = useRouter();

const { quizz } = defineProps(["quizz"]);

const navigateToQuizz = () => {
  router.push(`/quizz/${quizz.id}`)
}
</script>

<template>
  <div class="card" @click="navigateToQuizz">
    <img :src="quizz.img" alt="" />
    <div class="card-text">
      <h2>{{ quizz.name }}</h2>
      <p>3 Questões</p>
    </div>
  </div>
</template>

<style scoped>
.card {
  width: 310px;
  overflow: hidden;
  border-radius: 12px;
  box-shadow: 0px 2px 3px #888;
  margin-bottom: 35px;
  margin-right: 20px;
  cursor: pointer;
}

.card img {
  max-width: 100%;
  height: 190px;
  margin: 0;
}

.card .card-text {
  padding: 0 0 5px 10px;
}

.card .card-text h2 {
  font-weight: bold;
}
</style>
