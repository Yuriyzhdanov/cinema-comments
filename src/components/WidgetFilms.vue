<script>
export default {
  props: ['films'],
  emits: ['onSelectFilm'],
}
</script>
<template>
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
</template>

<!-- class Car{}
const car = new Car()
car instanceof Car -->
