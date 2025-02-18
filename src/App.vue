<script>
import WidgetFilms from './components/WidgetFilms.vue'
import WidgetComments from './components/WidgetComments.vue'
import Sparkles from './components/InputSparkles.vue'

export default {
  components: { WidgetFilms, WidgetComments, Sparkles },

  data() {
    return {
      selectedFilm: '',
    }
  },
}
</script>

<template>
  <Sparkles></Sparkles>
  <div class="main flex">
    <div class="left">
      <widget-films
        v-bind:selectedFilm="selectedFilm"
        v-on:onSelectFilm="selectedFilm = $event"
      ></widget-films>
    </div>

    <div v-if="selectedFilm" class="right">
      <widget-comments v-bind:selectedFilm="selectedFilm"></widget-comments>
    </div>
  </div>
</template>

<style>
@import url(https://fonts.googleapis.com/css?family=Nunito+Sans:200,300,regular,500,600,700,800,900,200italic,300italic,italic,500italic,600italic,700italic,800italic,900italic);

* {
  box-sizing: border-box;
}

:root {
  --primary-color: #1e1e2e;
  --secondary-color: #282a36;
  --text-color: #f8f8f2;
  --accent-color: #8be9fd;
  --border-radius: 8px;
}

body {
  background: linear-gradient(135deg, #1e1e2e 0%, #282a36 100%);
  color: var(--text-color);
  font-family: 'Nunito Sans', sans-serif;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  margin: 0;
  overflow: hidden;
}
#app {
  width: 100%;
  max-width: 900px; /* Максимальная ширина */
  height: auto;
  background: var(--secondary-color);
  padding: 20px;
  border-radius: var(--border-radius);
  box-shadow: 0px 10px 30px rgba(0, 0, 0, 0.3);
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.flex {
  display: flex;
  gap: 20px;
  width: 100%;
  justify-content: space-between;
  flex-wrap: wrap;
}

.flex > * {
  flex: 1;
}

h2 {
  color: var(--accent-color);
  text-align: center;
  margin-bottom: 20px;
}

.left,
.right {
  flex: 1;
  background: rgba(255, 255, 255, 0.05);
  padding: 15px;
  border-radius: var(--border-radius);
  width: 48%;
  box-sizing: border-box;
  margin-bottom: 20px;
}

.right h3 {
  margin: 0;
}

/* div {
  padding: 5px;
  border: 1px solid #000;
} */

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
  padding: 0;
}

.films li {
  display: flex;
  align-items: center;
  padding: 8px 12px;
  background: rgba(255, 255, 255, 0.1);
  border-radius: var(--border-radius);
  margin-bottom: 8px;
  transition: background 0.3s;
}

.films li:hover {
  background: rgba(255, 255, 255, 0.2);
}

textarea {
  resize: none;
}

.comments li i {
  display: inline-block;
  text-indent: 12px;
  font-weight: 400;
}

.wrap-input label {
  display: block;
  margin-bottom: 5px;
  font-weight: 600;
  padding: 5px;
}

.wrap-input input,
.wrap-input textarea {
  width: 100%;
  padding: 10px;
  background: rgba(255, 255, 255, 0.1);
  border: 1px solid rgba(255, 255, 255, 0.2);
  border-radius: var(--border-radius);
  color: var(--text-color);
}

.wrap-button {
  text-align: center;
  padding: 10px;
}

button {
  padding: 10px 15px;
  border: none;
  background: var(--accent-color);
  color: var(--primary-color);
  font-weight: 600;
  border-radius: var(--border-radius);
  cursor: pointer;
  transition: background 0.3s, transform 0.2s;
}

button:hover {
  background: #50c4de;
  transform: translateY(-2px);
}

.comments li {
  background: rgba(255, 255, 255, 0.1);
  padding: 10px;
  border-radius: var(--border-radius);
  margin-bottom: 8px;
}

.comments li b {
  color: var(--accent-color);
}

.comments li i {
  font-style: normal;
  opacity: 0.8;
}

.color-film-name {
  color: fuchsia;
}
/* RADIO */
</style>
