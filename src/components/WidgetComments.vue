<script>
export default {
  props: ['commentsByFilm'],
}
</script>

<template>
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
</template>
