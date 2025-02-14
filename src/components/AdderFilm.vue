<script>
export default {
  emits: ['onAddFilm'],

  data() {
    return {
      newFilm: '',
    }
  },
  methods: {
    handleClickButton() {
      this.$emit('onAddFilm', this.newFilm)
      this.newFilm = ''
    },
  },
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
      <button v-on:click="handleClickButton">Добавить</button>
    </div>
  </div>
</template>
