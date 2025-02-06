<script>
export default {
  emits: ['onAddNewFilm'],

  data() {
    return {
      newFilm: '',
    }
  },
}
</script>

<template>
  <h3>Добавить фильм</h3>
  <div class="wrap-input">
    <label for="newFilm">Название фильма</label>
    <input v-model.trim="newFilm" type="text" id="newFilm" />
  </div>
  <div class="wrap-button">
    <button v-on:click="$emit('onAddNewFilm', newFilm), (newFilm = '')">
      Добавить
    </button>
  </div>
</template>
