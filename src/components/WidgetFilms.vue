<script>
export default {
  props: ['films'],
  emit: ['onSelectFilm'],
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
      />
      {{ film }}
    </li>
  </ul>
</template>

<!-- class Car{}
const car = new Car()
car instanceof Car -->
