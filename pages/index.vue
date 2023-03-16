<template>
  <div>
    <HeaderComponent />
    <main class="movies">
      <!-- ON ERROR -->
      <ErrorMessage
      v-if="(movies.length < 1 && !loading) || movies.success == false"
      :error-code="movies.status_code"
      :text-message="movies.status_message"
      class="center"
      />

      <!-- Load -->
      <LoadComponent v-if="loading" class="center"/>
      
      <!-- MOVIE SHOWCASE -->
      <MoviesContainer title="Tranding" :movies="movies"/>

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
      this.movies = await json
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