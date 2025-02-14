<script>
import AdderFilm from './AdderFilm.vue'
import UiFilmsTitle from './UiFilmsTitle.vue'

export default {
  components: { UiFilmsTitle, AdderFilm },

  emits: ['onSelectFilm'],
  data() {
    return {
      films: [],
    }
  },

  methods: {
    addFilm(film) {
      this.films.push(film)
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
    <adder-film v-on:onAddFilm="addFilm"></adder-film>
  </div>
</template>

<!-- <film-adder v-on:onAddNewFilm="addFilm($event)"></film-adder> -->
<!-- class Car{}
const car = new Car()
car instanceof Car -->
