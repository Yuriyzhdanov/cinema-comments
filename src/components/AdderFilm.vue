<script setup>
import { ref } from 'vue'
import Sparkles from './InputSparkles.vue'

const sparkles = ref([])
const newFilm = ref('')

const randomColor = () => {
  const colors = ['#ff4d4d', '#ffb84d', '#4dff4d', '#4db8ff', '#b84dff']
  return colors[Math.floor(Math.random() * colors.length)]
}

const addSparkle = () => {
  for (let i = 0; i < 10; i++) {
    setTimeout(() => {
      sparkles.value.push({
        id: Date.now() + i,
        x: (Math.random() - 0.5) * 200,
        y: (Math.random() - 0.5) * 200,
        size: 5,
        color: randomColor(),
      })
    }, i * 50)
  }
  setTimeout(() => {
    sparkles.value.splice(0, 10) // Очищаем лишние элементы
  }, 1000)
}

const emit = defineEmits(['onAddFilm'])

const handleClickButton = () => {
  if (newFilm.value.trim()) {
    emit('onAddFilm', newFilm.value)
    newFilm.value = ''
  }
}
</script>

<template>
  <div>
    <h3>Добавить фильм</h3>
    <div class="wrap-input">
      <label for="newFilm">Название фильма</label>
      <input v-model.trim="newFilm" type="text" id="newFilm" />
    </div>
    <div class="wrap-button">
      <button @click="addSparkle(), handleClickButton()">Добавить</button>
    </div>
    <Sparkles :sparkles="sparkles" />
  </div>
</template>
