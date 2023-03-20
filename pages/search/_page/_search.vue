<template>
  <div>
    <HeaderComponent />
    <div class="results">
      <div v-if="moviesData?.total_results" class="movies">
        <MovieSearch
          v-for="(movie, index) in moviesData.results"
          :movieDetails="movie"
          :key="index"
        />
      </div>
    </div>
    <ErrorMessage
      v-if="!loading && !moviesData?.total_results"
      textMessage="Try searching something else."
    />
    <LoadComponent v-if="loading" />
    <PagerComponent
      v-if="moviesData?.total_results"
      :pagesQuanty="moviesData.total_pages"
    />
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
    try {
      const response = await fetch(
        `https://api.themoviedb.org/3/search/movie?api_key=${this.$config.API_KEY}&query=${this.search}&page=${this.page}`
      )
      const json = await response.json()
      this.moviesData = json
    } catch (e) {
      console.error(e.message)
      document.title = 'Search Error'
    } finally {
      this.loading = false
      document.title = this.search
    }
    console.log(JSON.stringify(this.moviesData))
  },
}
</script>

<style scoped>
.results {
  min-height: calc(100vh - 115px);
}

.movies {
  display: flex;
  flex-wrap: wrap;
  align-content: center;
  justify-content: space-around;
  margin: 30px 20px;
}
</style>
