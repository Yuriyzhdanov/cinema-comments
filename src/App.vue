<script>
  export default {
    data() {
      return {
        filmName: '',
        filmNames: [],
        username: '',
        text: '',
        comments: [],
        editingFilm: null,
        editingText: '',
      }
    },
    methods: {
      addFilmName() {
        this.filmNames.push(this.filmName)
        this.filmName = ''
      },
      addComment() {
        const existingComment = this.comments.find(
          c => c.filmName === this.filmName
        )
        if (existingComment) {
          existingComment.text = this.text
          existingComment.username = this.username
        } else {
          this.comments.push({
            filmName: this.filmName,
            username: this.username,
            text: this.text,
          })
        }
        this.username = ''
        this.text = ''
      },
      editComment(filmName) {
        const comment = this.comments.find(c => c.filmName === filmName)
        if (comment) {
          this.editingFilm = filmName
          this.editingUsername = comment.username
          this.editingText = comment.text
        } else {
          this.editingFilm = filmName
          this.editingUsername = ''
          this.editingText = ''
        }
      },
      saveEditedComment() {
        if (this.editingFilm) {
          const comment = this.comments.find(
            c => c.filmName === this.editingFilm
          )
          if (comment) {
            comment.text = this.editingText
            comment.username = this.editingUsername
          } else {
            this.comments.push({
              filmName: this.editingFilm,
              username: this.username,
              text: this.editingText,
            })
          }
          this.editingFilm = null
          this.username = ''
          this.editingText = ''
        }
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
        <li
          v-for="(film, idx) of filmNames"
          :key="idx"
          v-on:dblclick="editComment(film)"
        >
          {{ film }}
        </li>
      </ul>
      <h3>Добавить фильм</h3>
      <div class="wrap-input">
        <label for="">Название фильма</label>
        <input v-model="filmName" type="text" />
      </div>
      <div class="wrap-button">
        <button v-on:click="addFilmName">Добавить</button>
      </div>
    </div>

    <div class="rigth">
      <h2>Отзывы</h2>
      <ul class="comments">
        <li v-for="(comment, idx) of comments" :key="idx">
          <div>
            <b>{{ comment.username }}</b>
          </div>
          <div>
            <i>{{ comment.text }}</i>
          </div>
        </li>
      </ul>

      <h3 v-if="editingFilm">
        Редактировать комментарий к "{{ editingFilm }}"
      </h3>
      <div class="wrap-input">
        <label for="">Ваше имя</label>
        <input v-model="username" type="text" />
      </div>
      <div class="wrap-input">
        <label for="">Ваш отзыв</label>
        <textarea v-model="editingText"></textarea>
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
