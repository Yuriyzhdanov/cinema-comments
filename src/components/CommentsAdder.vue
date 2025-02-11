<script>
export default {
  props: ['selectedFilm'],
  emits: ['onAddComment'],

  data() {
    return {
      newCommentUsername: '',
      newCommentText: '',
    }
  },
}
</script>

<template>
  <h3>Комментарий к фильму к</h3>
  <span class="color-film-name">{{ selectedFilm }}</span>
  <div class="wrap-input">
    <label for="">Ваше имя</label>
    <input v-model.trim="newCommentUsername" type="text" />
  </div>
  <div class="wrap-input">
    <label for="">Ваш отзыв </label>
    <textarea v-model.trim="newCommentText"></textarea>
  </div>
  <div class="wrap-button">
    <button
      v-on:click="
        $emit('onAddComment', {
          username: newCommentUsername,
          text: newCommentText,
          film: selectedFilm,
        })
      "
    >
      Добавить
    </button>
  </div>
</template>
