<template>
  <div>
    <HeaderComponent />

    <div v-if="movieDetails" class="movieDetails">
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
    }
  },
  async mounted() {
    const response = await fetch(
      `https://api.themoviedb.org/3/movie/${this.movieID}?api_key=${this.$config.API_KEY}`
    )

    const data = await response.json()

    this.movieDetails = data
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
  min-height: calc(100vh - 115px);
  display: flex;
  justify-content: space-around;
}

.detailsImage {
  width: 49vw;
  display: flex;
  justify-content: center;
  align-items: center;
}

.detailsText {
  width: 49vw;
  color: white;
  box-sizing: border-box;
  padding-top: 20px;
}

.detailsText > h1 {
  margin-bottom: 10px;
  user-select: text;
}

.detailsText > p {
  text-align: justify;
  padding-right: 30px;
  user-select: text;
}

img {
  width: 45%;
}
</style>