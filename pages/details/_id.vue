<template>
  <div>
    <HeaderComponent />
    <LoadComponent v-if="loading" />

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
        <button @click="() => $router.go(-1)" class="backButton">
          <i class="fa-solid fa-arrow-left arrowBack"></i> Go Back
        </button>
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
    } catch (e) {
    } finally {
      this.loading = false
      document.title = this.movieDetails.original_title || 'Movie Details'
    }
  },
  computed: {
    fullImagePath() {
      return `${this.$config.IMAGE_URL}${this.movieDetails?.poster_path}`.toString()
    },
  },
}
</script>

<style scoped>
.movieDetails {
  color: whitesmoke;
  min-height: calc(100vh - 115px);
  min-width: 100vw;
  display: flex;
  justify-content: space-around;
}

.detailsImage {
  width: 35vw;
  min-height: 75vh;
  display: flex;
  justify-content: center;
  align-items: center;
}

img.movieImage {
  width: 65%;
  max-height: auto;
}

.detailsText {
  box-sizing: border-box;
  width: 45%;
  margin-top: 30px;
  color: white;
}

.detailsText > h1 {
  margin-bottom: 15px;
}

.detailsText > p {
  text-align: justify;
}

.backButton {
  margin-top: 30px;
  background-color: rgb(255, 191, 0);
  border: none;
  padding: 10px 15px;
  border-radius: 10px;
  cursor: pointer;
}

.backButton:hover .arrowBack {
  animation: arrowBackAnimation 1.3s linear infinite;
}

@keyframes arrowBackAnimation {
  0% { transform: translateX(0px); }
  50% { transform: translateX(-7px); }
  100% { transform: translateX(1px); }
}

</style>