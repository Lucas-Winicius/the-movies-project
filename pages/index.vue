<template>
  <div>
    <HeaderComponent />
    <main class="movies">
      <!-- ON ERROR -->
      <ErrorMessage
        :errorCode="movies.status_code"
        :textMessage="movies.status_message"
        v-if="(movies.length < 1 && !loading) || movies.success == false"
      />

      <!-- Load -->
      <LoadComponent v-if="loading" />

      <!-- MOVIE SHOWCASE -->
      <div>
        <h1>Tranding</h1>
        <MovieShowcase v-for="(movie, index) in movies.results" :key="index" :adult="movie.adult" :title="movie.title" :original_language="movie.original_language" :poster_path="movie.poster_path" />
      </div>
    </main>
    <FooterComponent />
  </div>
</template>

<script>
export default {
  name: 'IndexPage',
  data() {
    return {
      loading: true,
      movies: {},
    }
  },
  head: {
    title: 'Home',
  },
  async mounted() {
    try {
      // API call
      const response = await fetch(
        `https://api.themoviedb.org/3/trending/all/day?api_key=${this.$config.API_KEY}`
      )
      const json = await response.json()
      this.movies = json
      console.log(JSON.stringify(this.movies))
    } catch (err) {
      console.error(err.message)
    } finally {
      this.loading = false
    }
  },
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Dosis:wght@200;300;400;500;600;700;800&display=swap');

* {
  padding: 0;
  margin: 0;
  font-family: 'Dosis', sans-serif;
  user-select: none;
}

body {
  background-color: black;
}

main.movies {
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: calc(100vh - 115px);
}
</style>