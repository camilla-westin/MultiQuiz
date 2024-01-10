<script setup>
import { defineProps } from 'vue'
const { quiz } = defineProps(['quiz'])
</script>

<template>
  <div class="card">
    <div class="card-img">
      <img :src="quiz.img" />
    </div>
    <div class="card-text">
      <h2>{{ quiz.name }}</h2>
      <p>{{ quiz.questions.length }} questions</p>
    </div>
  </div>
</template>

<style scoped>
.card {
  width: 100%;
  overflow: hidden;
  border-radius: 2%;
  box-shadow: 0 4px 22px 0 rgba(0, 0, 0, 0.09);
  margin-bottom: 35px;
  margin-right: 20px;
  cursor: pointer;
}
@media (min-width: 768px) {
  .card {
    width: calc(50% - 20px);
  }
}
@media (min-width: 1000px) {
  .card {
    width: calc(33.3% - 20px);
  }
}

.card-img {
  overflow: hidden;
  display: flex;
  align-items: center;
  justify-content: center;
}

@media (min-width: 768px) {
  .card-img {
    max-height: 230px;
  }
}

@media (min-width: 1000px) {
  .card-img {
    max-height: 160px;
  }
}

.card img {
  width: 100%;
  height: auto;
  margin: 0;
}

.card-text {
  padding: 15px;
}

.card-text h2 {
  font-weight: bold;
}
</style>
