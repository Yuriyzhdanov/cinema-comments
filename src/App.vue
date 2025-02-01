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

      <h3>Комментарий к фильму</h3>
      <div class="wrap-input">
        <label for="">Ваше имя</label>
        <input v-model.trim="newCommentUsername" type="text" />
      </div>
      <div class="wrap-input">
        <label for="">Ваш отзыв к "{{ selectedFilm || '...' }}"</label>
        <textarea v-model.trim="newCommentText"></textarea>
      </div>
      <div class="wrap-button">
        <button v-on:click="addComment">Добавить</button>
      </div>
    </div>
  </div>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
@import url(https://fonts.googleapis.com/css?family=Nunito+Sans:200,300,regular,500,600,700,800,900,200italic,300italic,italic,500italic,600italic,700italic,800italic,900italic);

* {
  box-sizing: border-box;
}

.flex {
  display: flex;
}

.flex > * {
  flex: 1;
}

div {
  padding: 5px;
  /* border: 1px solid #000; */
}

input,
textarea,
html {
  font-family: 'Nunito Sans';
  color: #234;
  font-size: 18px;
  font-weight: 600;
}

ul {
  list-style: none;
}

textarea {
  resize: none;
}

.comments li i {
  display: inline-block;
  text-indent: 12px;
  font-weight: 400;
}

.wrap-input input,
.wrap-input textarea {
  width: 100%;
}

.wrap-button {
  /* text-align: center; */
}
</style>
