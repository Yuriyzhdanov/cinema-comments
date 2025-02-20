<script setup>
import { defineProps } from 'vue'

defineProps({
  sparkles: Array,
})
</script>

<template>
  <div class="sparkle-container">
    <div
      v-for="sparkle in sparkles"
      :key="sparkle.id"
      class="typing-effect"
      :style="{
        position: 'absolute',
        top: sparkle.y + 'px',
        left: sparkle.x + 'px',
        width: sparkle.size + 'px',
        height: sparkle.size + 'px',
        backgroundColor: sparkle.color,
        borderRadius: '50%',
        opacity: 0.8,
      }"
    ></div>
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
  position: relative;
  width: 100%;
  height: 50px;
  pointer-events: none;
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
