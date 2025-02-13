<script>
import UiComment from './UiComment.vue'

export default {
  compomemts: { UiComment },

  props: ['selectedFilm'],

  computed: {
    commentsByFilm() {
      return this.comments.filter(comment => comment.film === this.selectedFilm)
    },
  },

  data() {
    return {
      comments: [],
      newComment: {
        username: '',
        text: '',
        film: '',
      },
    }
  },

  methods: {
    addComment() {
      this.newComment.film = this.selectedFilm
      this.comments.push({ ...this.newComment })
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
    <ui-comment></ui-comment>
    <ul class="comments">
      <li v-for="(comment, idx) of commentsByFilm" :key="idx">
        <div>
          <b>{{ comment.username }}</b>
        </div>
        <div>
          <i>{{ comment.text }}</i>
        </div>
      </li>
    </ul>
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
      <button v-on:click="addComment">Добавить</button>
    </div>
  </div>
</template>
