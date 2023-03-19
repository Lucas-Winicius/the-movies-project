<template>
  <div
    v-if="movies.results"
    class="moviesContainer"
    @mouseup="handleMouseUp"
    @mouseleave="handleMouseUp"
  >
    <h1>{{ title }}</h1>

    <div
      class="movies"
      @mousedown="handleMouseDown"
      @mousemove="handleScrollClick"
    >
      <MovieShowcase
        v-for="movie in movies.results"
        :key="movie.id"
        :id_code="movie.id"
        :adult="movie.adult"
        :title="movie.title"
        :original_language="movie.original_language"
        :poster_path="movie.poster_path"
        :popular="true"
      />
    </div>
  </div>
</template>

<script>
export default {
  name: 'MoviesContainer',
  props: {
    title: { type: String, default: '' },
    movies: {
      type: Object,
      default() {
        return {}
      },
    },
  },
  data() {
    return {
      clicked: false,
    }
  },
  methods: {
    handleScrollClick(e) {
      if (!this.clicked) return
      let el

      if (e.target.classList.contains('movies')) el = e.target
      else if (e.target.parentElement.classList.contains('movies'))
        el = e.target.parentElement
      el.scrollLeft -= e.movementX
    },
    handleMouseDown(e) {
      this.clicked = true
    },
    handleMouseUp(e) {
      this.clicked = false
    },
  },
}
</script>

<style scoped>
.moviesContainer {
  width: 100vw;
  box-sizing: border-box;
  margin: 10px 0px;
  cursor: grab;
}

.moviesContainer:active {
  cursor: grabbing;
}
.moviesContainer > h1 {
  color: rgb(255, 200, 0);
  margin-left: 1vw;
}

div.movies {
  display: flex;
  overflow-x: scroll;
  overflow-y: hidden;
  scrollbar-width: thin;
  width: 100vw;
}
</style>
