<template>
  <div v-if="movies.results" class="trandingContainer">
    <h1>{{ title }}</h1>
    <MovieShowcase
      v-for="movie in movies.results"
      :key="movie.id"
      :id_code="movie.id"
      :adult="movie.adult"
      :title="movie.title"
      :original_language="movie.original_language"
      :poster_path="movie.poster_path"
    />
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
}
</script>

<style scoped>
.trandingContainer {
  width: 100vw;
  box-sizing: border-box;
  margin: 15px;
}
.trandingContainer > h1 {
  color: rgb(255, 200, 0);
}
</style>