<script setup>
import { defineProps } from 'vue'
import { RouterLink } from 'vue-router'
const { quizQuestionsLength, numberOfCorrectAnswers } = defineProps([
  'quizQuestionsLength',
  'numberOfCorrectAnswers'
])
</script>

<template>
  <div class="result">
    <p></p>
    <h4>Your result is {{ numberOfCorrectAnswers }}/{{ quizQuestionsLength }} correct.</h4>
    <RouterLink to="/">Go Back</RouterLink>
  </div>
</template>

<style scoped>
.result {
  text-align: center;
  padding: 100px 0;
}

p {
  font-size: 25px;
}
</style>
