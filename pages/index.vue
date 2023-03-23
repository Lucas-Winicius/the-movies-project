<template>
  <div>
    <HeaderComponent />
    <main class="moviesShowcase">
      <!-- ON ERROR -->
      <ErrorMessage
        v-if="(movies.length < 1 && !loading) || movies.success == false"
        :error-code="movies.status_code"
        :text-message="movies.status_message"
        class="center"
      />

      <div v-if="!loading" class="moviesShowcase">
        <!-- MOVIE SHOWCASE -->
        <MoviesContainer title="Tranding" :movies="movies" />

        <!-- Upcoming -->
        <MoviesContainer title="Upcoming" :movies="upcoming" />

        <!-- Top Rated -->
        <MoviesContainer title="Top Rated" :movies="topRated" />
      </div>

      <div class="popularMovies">
        <h1>Popular</h1>
        <MovieView
          v-for="(movie, index) in popularMovies.results"
          :key="index"
          :movieDetails="movie"
        />
      </div>

      <!-- Load -->
      <LoadComponent v-if="loading" class="center" />
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
      popularMovies: {},
      upcoming: {},
      topRated: {},
    }
  },
  head: {
    title: 'Home',
  },
  async mounted() {
    this.movies = await this.fetchMovies(
      `https://api.themoviedb.org/3/trending/all/day?api_key=${this.$config.API_KEY}`
    )

    this.popularMovies = await this.fetchMovies(
      `https://api.themoviedb.org/3/movie/popular?api_key=${this.$config.API_KEY}`
    )

    this.topRated = await this.fetchMovies(
      `https://api.themoviedb.org/3/movie/top_rated?api_key=${this.$config.API_KEY}`
    )

    this.upcoming = await this.fetchMovies(
      `https://api.themoviedb.org/3/movie/upcoming?api_key=${this.$config.API_KEY}`
    )
  },
  methods: {
    async fetchMovies(url) {
      try {
        try {
          const response = await fetch(url)
          return await response.json()
        } catch (error) {
          console.error(error)
        }
      } finally {
        this.loading = false
      }
    },
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
  scrollbar-width: thin;
}

body {
  overflow-x: hidden;
  background-color: black;
}

main.moviesShowcase {
  box-sizing: border-box;
  min-height: calc(100vh - 115px);
  margin: 10px;
  width: 90vw;
}

.popularMovies {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-around;
  width: 97vw;
}

.popularMovies > h1 {
  width: 90vw;
  color: white;
}
</style>
