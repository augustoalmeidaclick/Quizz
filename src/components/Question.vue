<script setup>
import { defineProps, defineEmits } from "vue";

const { question } = defineProps(["question"]);

const emit = defineEmits(["selectOption"]);
const emitSelectedOption = (isCorrect) => {
  emit('selectOption', isCorrect)
}
</script>

<template>
  <div>
    <div class="question-container">
      <h1 class="question">{{ question.text }}</h1>
    </div>
    <div class="options-container">
      <div
        class="option"
        :key="option.id"
        v-for="option in question.options"
        @click="emitSelectedOption(option.isCorrect)"
      >
        <p class="option-label">{{ option.label }}</p>
        <div class="option-value">
          <p>{{ option.text }}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.question-container {
  margin-top: 20px;
}

.question {
  font-size: 2.5rem;
  margin-bottom: 20px;
}

.option {
  display: flex;
  margin-bottom: 20px;
  cursor: pointer;
}

.option-label {
  background-color: #5494c9;
  width: 50px;
  height: 50px;
  font-size: 1.87rem;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 20px 0 0 20px;
}

.option-value {
  background-color: #cbcfd3;
  border-radius: 0 20px 20px 0;
  width: 100%;
  font-size: 1.87rem;
  padding: 0 20px;
}
</style>
