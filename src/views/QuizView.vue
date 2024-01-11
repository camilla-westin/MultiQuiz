<script setup>
import QuizHeader from '@/components/QuizHeader.vue'
import Question from '@/components/Question.vue'
import Result from '@/components/Result.vue'
import { useRoute } from 'vue-router'
import { ref, computed } from 'vue'
import quizes from '@/data/quizes.json'

const route = useRoute()
const quizId = parseInt(route.params.id)
const quiz = quizes.find((q) => q.id === quizId)
const currentQuestionIndex = ref(0)
const numberOfCorrectAnswers = ref(0)
const showResult = ref(false)

const questionStatus = computed(() => `${currentQuestionIndex.value}/${quiz.questions.length}`)
const barProgress = computed(() => `${(currentQuestionIndex.value / quiz.questions.length) * 100}%`)
const onOptionsSelected = (isCorrect) => {
  if (isCorrect) {
    numberOfCorrectAnswers.value++
  }

  if (quiz.questions.length - 1 === currentQuestionIndex.value) {
    showResult.value = true
  }

  currentQuestionIndex.value++
}
</script>

<template>
  <div>
    <QuizHeader :questionStatus="questionStatus" :barProgress="barProgress" />
    <div>
      <Question
        v-if="!showResult"
        :question="quiz.questions[currentQuestionIndex]"
        @selectOption="onOptionsSelected"
      />
      <Result
        v-else
        :quizQuestionsLength="quiz.questions.length"
        :numberOfCorrectAnswers="numberOfCorrectAnswers"
      />
    </div>
  </div>
</template>
