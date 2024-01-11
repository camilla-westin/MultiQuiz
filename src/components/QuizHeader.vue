<script setup>
import { defineProps } from 'vue'
const { questionStatus, barProgress } = defineProps(['questionStatus', 'barProgress'])
</script>

<template>
  <header>
    <p>{{ barProgress }}</p>
    <h2>Question {{ questionStatus }}</h2>
    <div class="bar">
      <div class="completion" :style="{ width: barProgress }"></div>
    </div>
  </header>
</template>

<style scoped>
header {
  margin-top: 20px;
}

header h2 {
  font-size: 30px;
}

.bar {
  width: 300px;
  height: 30px;
  border: 3px solid #79a875;
}

.completion {
  height: 100%;
  width: 0%;
  background-color: #79a875;
}
</style>
