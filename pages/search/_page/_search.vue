<template>
  <div>
    <HeaderComponent />
    <div class="results">
      <LoadComponent v-if="loading" />
      <div v-if="moviesData" class="movies">
        <MovieSearch
          v-for="(movie, index) in moviesData.results"
          :movieDetails="movie"
          :key="index"
        />
      </div>
    </div>
    <FooterComponent />
  </div>
</template>

<script>
export default {
  name: 'Search',
  data() {
    return {
      search: this.$route.params.search,
      page: this.$route.params.page,
      moviesData: null,
      loading: true,
    }
  },
  async mounted() {
    document.title = this.search.charAt(0).toUpperCase() + this.search.slice(1)
    try {
      const response = await fetch(
        `https://api.themoviedb.org/3/search/movie?api_key=${this.$config.API_KEY}&query=${this.search}&page=${this.page}`
      )
      const json = await response.json()
      this.moviesData = json
    } catch (e) {
      console.error(e.message)
    } finally {
      this.loading = false
    }
  },
}
</script>

<style scoped>
.results {
  min-height: calc(100vh - 115px);
}
</style>
