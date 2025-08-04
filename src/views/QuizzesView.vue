<script setup>
import q from "../data/data.json";
import { ref, watch } from "vue";
import Card from "../components/Card.vue";
import gsap from "gsap";

const quizzes = ref(q);
const search = ref("");

watch(search, () => {
  quizzes.value = q.filter((quizz) =>
    quizz.name.toLowerCase().includes(search.value.toLowerCase())
  );
});

const beforeEnter = (el) => {
  gsap.from(el, {
    y: -60,
    opacity: 0,
    delay: el.dataset.index * 0.2,
  });
};

const enter = (el) => {
  gsap.to(el, {
    y: 0,
    opacity: 1,
    duration: 0.2,
  });
};
</script>

<template>
  <div>
    <header>
      <h1>Quizzes</h1>
      <input
        v-model.trim="search"
        type="text"
        placeholder="Procurar Quizz..."
      />
    </header>
    <div class="options-container">
      <transition-group appear @before-enter="beforeEnter">
        <Card
          v-for="(quizz, index) in quizzes"
          :key="quizz.id"
          :quizz="quizz"
          :data-index="index"
        />
      </transition-group>
    </div>
  </div>
</template>

<style scoped>
header {
  margin-bottom: 10px;
  margin-top: 30px;
  display: flex;
  align-items: center;
}

header h1 {
  font-weight: bold;
  margin-right: 30px;
  font-size: 4rem;
}

header input {
  border: none;
  background-color: #f1f1f1;
  box-shadow: 0px 2px 2px #888;
  padding: 10px;
  border-radius: 10px;
  font-size: 0.9rem;
  outline: none;
}

.options-container {
  display: flex;
  flex-wrap: wrap;
  margin-top: 40px;
}
</style>
