<script>
export default {
  props: ['selectedFilm'],
  emits: ['onAddComment'],

  data() {
    return {
      newComment: {
        username: '',
        text: '',
        film: '',
      },
    }
  },
  methods: {
    handleAddComment() {
      this.newComment.film = this.selectedFilm
      this.$emit('onAddComment', { ...this.newComment })
      this.newComment = {
        username: '',
        text: '',
        film: '',
      }
    },
  },
}
</script>

<template>
  <div>
    <h3>Комментарий к фильму</h3>
    <span class="color-film-name">{{ selectedFilm }}</span>
    <div class="wrap-input">
      <label for="">Ваше имя</label>
      <input v-model.trim="newComment.username" type="text" />
    </div>
    <div class="wrap-input">
      <label for="">Ваш отзыв </label>
      <textarea v-model.trim="newComment.text"></textarea>
    </div>
    <div class="wrap-button">
      <button v-on:click="handleAddComment">Добавить</button>
    </div>
  </div>
</template>
