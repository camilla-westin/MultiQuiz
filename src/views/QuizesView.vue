<script setup>
import q from '../data/quizes.json'
import { ref, watch } from 'vue'
import Card from '../components/Card.vue'

const quizes = ref(q)
const search = ref('')

watch(search, () => {
  quizes.value = q.filter((quiz) => quiz.name.toLowerCase().includes(search.value.toLowerCase()))
})
</script>

<template>
  <div>
    <header>
      <h1>Quizes</h1>
      <input type="text" placeholder="Search..." v-model.trim="search" />
    </header>
    <div class="options-container">
      <TransitionGroup name="list">
        <Card v-for="quiz in quizes" :key="quiz.id" :quiz="quiz" />
      </TransitionGroup>
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
}

header input {
  border: none;
  background-color: rgba(128, 128, 128, 0.1);
  padding: 10px;
  border-radius: 5px;
}

.options-container {
  display: flex;
  flex-wrap: wrap;
  margin-top: 40px;
}

.list-move,
.list-enter-active,
.list-leave-active {
  transition: 0.3s ease;
}

.list-enter-from,
.list-leave-to {
  opacity: 0;
  transform: translateY(10px);
}
</style>
