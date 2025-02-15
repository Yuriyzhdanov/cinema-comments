<script>
import AdderComment from './AdderComment.vue'
import UiCommentTitle from './UiCommentTitle.vue'

export default {
  components: { UiCommentTitle, AdderComment },

  props: ['selectedFilm'],

  computed: {
    commentsByFilm() {
      return this.comments.filter(comment => comment.film === this.selectedFilm)
    },
  },

  data() {
    return {
      comments: [],
    }
  },

  methods: {
    addComment(comment) {
      this.comments.push({ ...comment })
    },
  },
}
</script>

<template>
  <div>
    <ui-comment-title></ui-comment-title>

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
    <adder-comment
      v-bind:selectedFilm="selectedFilm"
      v-on:onAddComment="addComment"
    ></adder-comment>
  </div>
</template>
