<template>
  <div>
    <HeaderComponent />
    <LoadComponent v-if="loading"  />

    <div v-if="movieDetails && !loading" class="movieDetails">
      <div class="detailsImage">
        <img
          :src="fullImagePath"
          :alt="movieDetails.original_title"
          class="movieImage"
        />
      </div>
      <div class="detailsText">
        <h1>{{ movieDetails.original_title }}</h1>
        <p>{{ movieDetails.overview }}</p>
        <button @click="e => $router.go(-1)"><i class="fa-solid fa-arrow-left"></i> Go Back</button>
      </div>
    </div>

    <FooterComponent />
  </div>
</template>

<script>
export default {
  name: 'DetailsPage',
  data() {
    return {
      movieID: this.$route.params.id,
      movieDetails: null,
      loading: true,
    }
  },
  async mounted() {
    try {
      const response = await fetch(
        `https://api.themoviedb.org/3/movie/${this.movieID}?api_key=${this.$config.API_KEY}`
      )
      const data = await response.json()
      this.movieDetails = data

    } catch(e) {
      
    } finally { this.loading = false }

  },
  computed: {
    fullImagePath() {
      return `${this.$config.IMAGE_URL}${this.movieDetails?.poster_path}`.toString()
    },
  },
}
</script>
<style scoped>

</style>