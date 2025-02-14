<script>
import UiFilmsTitle from './UiFilmsTitle.vue'

export default {
  components: { UiFilmsTitle },

  emits: ['onSelectFilm'],
  data() {
    return {
      films: [],
      newFilm: '',
    }
  },
  methods: {
    addFilm() {
      this.films.push(this.newFilm)
      this.newFilm = ''
    },
  },
}
</script>
<template>
  <div>
    <ui-films-title></ui-films-title>
    <ul class="films">
      <li v-for="(film, idx) of films" :key="idx">
        <input
          v-bind:value="film"
          v-on:input="$emit('onSelectFilm', film)"
          type="radio"
          name="selectedFilm"
          v-bind:id="'film-' + idx"
        />
        <label v-bind:for="'film-' + idx">{{ film }}</label>
      </li>
    </ul>
    <div>
      <h3>Добавить фильм</h3>
      <div class="wrap-input">
        <label for="newFilm">Название фильма</label>
        <input v-model.trim="newFilm" type="text" id="newFilm" />
      </div>
      <div class="wrap-button">
        <button v-on:click="addFilm">Добавить</button>
      </div>
    </div>
  </div>
</template>

<!-- <film-adder v-on:onAddNewFilm="addFilm($event)"></film-adder> -->
<!-- class Car{}
const car = new Car()
car instanceof Car -->
