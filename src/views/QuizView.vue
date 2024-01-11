<script setup>
import QuizHeader from '@/components/QuizHeader.vue'
import Question from '@/components/Question.vue'
import { useRoute } from 'vue-router'
import { ref, computed } from 'vue'
import quizes from '@/data/quizes.json'

const route = useRoute()
const quizId = parseInt(route.params.id)
const quiz = quizes.find((q) => q.id === quizId)
const currentQuestionIndex = ref(0)

const questionStatus = computed(() => `${currentQuestionIndex.value}/${quiz.questions.length}`)
const barProgress = computed(() => `${(currentQuestionIndex.value / quiz.questions.length) * 100}%`)
</script>

<template>
  <div>
    <QuizHeader :questionStatus="questionStatus" :barProgress="barProgress" />
    <div>
      <Question :question="quiz.questions[currentQuestionIndex]" />
    </div>
    <button @click="currentQuestionIndex++">Next question</button>
  </div>
</template>
