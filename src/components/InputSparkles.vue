<script setup>
import { ref } from 'vue'

const sparkles = ref([])

const addSparkle = () => {
  for (let i = 0; i < 100; i++) {
    setTimeout(() => {
      sparkles.value.push({
        id: Date.now(),
        x: (Math.random() - 0.5) * 200,
        y: (Math.random() - 0.5) * 200,
        size: 5,
      })
    }, 200)
  }
  // setInterval(() => {
  //   sparkles.value?.shift()
  // }, 200)
}
</script>

<template>
  <div class="wrap-button">
    <button @click="addSparkle">PUSH</button>
    <div class="sparkle-container">
      <div
        v-for="sparkle in sparkles"
        :key="sparkle.id"
        class="typing-effect"
        style="background-color: crimson"
        :style="{
          top: sparkle.y + 'px',
          left: sparkle.x + 'px',
          width: sparkle.size + 'px',
          height: sparkle.size + 'px',
        }"
      ></div>
    </div>
  </div>
</template>

<style>
@keyframes typing-sparkles {
  0% {
    opacity: 1;
    transform: scale(1);
  }
  100% {
    opacity: 0;
    transform: scale(4.5);
  }
}

.wrap-button {
  position: relative;
  display: inline-block;
}

.sparkle-container {
  position: absolute;
  left: 0;
  top: 0;
}

.typing-effect {
  opacity: 0;
  transform: scale(4.5);
  position: absolute;
  background-color: var(--accent-color);
  width: 6px;
  height: 6px;
  border-radius: 50%;
  animation: alternate typing-sparkles 1s;
  animation-iteration-count: 1;
  pointer-events: none;
}
</style>
