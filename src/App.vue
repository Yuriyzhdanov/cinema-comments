<style src="../css/main_style.css"></style>

<script>
export default {
  computed: {
    filmComments() {
      return this.comments.filter(comment => comment.film === this.selectedFilm)
    },
  },

  data() {
    return {
      comments: [],
      films: [],
      newFilm: '',
      newCommentUsername: '',
      newCommentText: '',
      selectedFilm: '',
    }
  },

  methods: {
    addFilm() {
      this.films.push(this.newFilm)
      this.newFilm = ''
    },

    addComment() {
      this.comments.push({
        username: this.newCommentUsername,
        text: this.newCommentText,
        film: this.selectedFilm,
      })
      this.newCommentUsername = ''
      this.newCommentText = ''
    },
  },
}
</script>

<template>
  <div class="main flex">
    <div class="left">
      <div class="title">
        <h2>Фильмы</h2>
      </div>
      <ul class="films">
        <li v-for="(film, idx) of films" :key="idx">
          <input
            v-model="selectedFilm"
            type="radio"
            name="selectedFilm"
            v-bind:value="film"
          />
          {{ film }}
        </li>
      </ul>

      <h3>Добавить фильм</h3>
      <div class="wrap-input">
        <label for="">Название фильма</label>
        <input v-model.trim="newFilm" type="text" />
      </div>
      <div class="wrap-button">
        <button v-on:click="addFilm">Добавить</button>
      </div>
    </div>

    <div class="rigth">
      <h2>Отзыв</h2>
      <ul class="comments">
        <li v-for="(comment, idx) of filmComments" :key="idx">
          <div>
            <b>{{ comment.username }}</b>
          </div>
          <div>
            <i>{{ comment.text }}</i>
          </div>
        </li>
      </ul>

      <h3>Комментарий к фильму к {{ selectedFilm }}</h3>
      <div class="wrap-input">
        <label for="">Ваше имя</label>
        <input v-model.trim="newCommentUsername" type="text" />
      </div>
      <div class="wrap-input">
        <label for="">Ваш отзыв </label>
        <textarea v-model.trim="newCommentText"></textarea>
      </div>
      <div class="wrap-button">
        <button v-on:click="addComment">Добавить</button>
      </div>
    </div>
  </div>
</template>
