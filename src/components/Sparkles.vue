<script setup>
import { ref, onMounted, watchEffect } from 'vue'

const sparkles = ref([])
const addSparkle = event => {
  const { clientX: x, clientY: y } = event
  sparkles.value.push({
    id: Date.now(),
    x,
    y,
    size: Math.random() * 6 + 4,
  })
  setTimeout(() => {
    sparkles.value.shift()
  }, 600)
}

onMounted(() => {
  document.addEventListener('input', addSparkle)
})
</script>

<template>
  <div class="sparkle-container">
    <div
      v-for="sparkle in sparkles"
      :key="sparkle.id"
      class="typing-effect"
      :style="{
        top: sparkle.y + 'px',
        left: sparkle.x + 'px',
        width: sparkle.size + 'px',
        height: sparkle.size + 'px',
      }"
    ></div>
  </div>
</template>
