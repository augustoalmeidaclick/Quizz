<script setup>
import Question from "@/components/Question.vue";
import QuizzHeader from "@/components/QuizzHeader.vue";
import { useRoute } from "vue-router";
import { ref, computed } from "vue";
import data from "@/data/data.json";
import Result from "@/components/Result.vue";

const route = useRoute();
const quizzId = parseInt(route.params.id);

const currentQuestionIndex = ref(0);

const quizz = data.find((q) => q.id === quizzId);

const questionStatus = computed(
  () => `${currentQuestionIndex.value}/${quizz.questions.length}`
);

const barPercentage = computed(
  () => `${(currentQuestionIndex.value / quizz.questions.length) * 100}%`
);

const numberOfCorrectAnswers = ref(0);
const onOptionSelected = (isCorrect) => {
  if (isCorrect) {
    numberOfCorrectAnswers.value++;
  }
  if (quizz.questions.length - 1 === currentQuestionIndex.value) {
    showResults.value = true;
  }
  currentQuestionIndex.value++;
};
const showResults = ref(false);
</script>

<template>
  <div>
    <QuizzHeader
      :questionStatus="questionStatus"
      :barPercentage="barPercentage"
    />
    <div v-if="quizz">
      <Question
        v-if="!showResults"
        :question="quizz.questions[currentQuestionIndex]"
        @selectOption="onOptionSelected"
      />
      <Result
        v-else
        :quizzQuestionLength="quizz.questions.length"
        :numberOfCorrectAnswers="numberOfCorrectAnswers"
      />
    </div>
    <div v-else>
      <p>Quizz não encontrado.</p>
    </div>
  </div>
</template>

<style scoped></style>
