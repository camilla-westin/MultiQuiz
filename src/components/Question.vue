<script setup>
import { defineProps, defineEmits } from 'vue'

const emit = defineEmits(['selectOption'])
const { question } = defineProps(['question'])

const emitSelectedOption = (isCorrect) => {
  emit('selectOption', isCorrect)
}
</script>

<template>
  <div class="question-container">
    <h3 class="question">{{ question.text }}</h3>
    <ul class="options-container">
      <li
        v-for="option in question.options"
        :key="option.id"
        class="option"
        @click="emitSelectedOption(option.isCorrect)"
      >
        <p class="option-label">{{ option.label }}</p>
        <div class="option-value">
          <p>{{ option.text }}</p>
        </div>
      </li>
    </ul>
  </div>
</template>

<style scoped>
.question-container {
  margin-top: 20px;
}

.question {
  font-size: 40px;
  margin-bottom: 20px;
}

.options-container {
  list-style: none;
  padding: 0;
}

.option {
  display: flex;
  margin-bottom: 20px;
  cursor: pointer;
}

.option-label {
  background: #acd6ab;
  width: 50px;
  height: 50px;
  font-size: 30px;
  display: flex;
  align-items: center;
  justify-content: center;
}

.option-value {
  background-color: #ddeddc;
  width: 100%;
  font-size: 25px;
  padding: 0 0 0 15px;
  display: flex;
  align-items: center;
  justify-content: flex-start;
}
</style>
