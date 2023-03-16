<template>
  <div v-if="movies.results" class="moviesContainer">
    <h1>{{ title }}</h1>

    <div class="movies">
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
}
</script>

<style scoped>
.moviesContainer {
  width: 100vw;
  box-sizing: border-box;
  margin: 10px 0px;
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