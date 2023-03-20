<template>
  <div class="container" @click="handleClick">
    <img
      :src="fullImagePath"
      :alt="movieDetails.original_title"
      :title="movieDetails.original_title"
      class="image"
    />
  </div>
</template>

<script>
export default {
  name: 'MovieSearch',
  props: {
    movieDetails: Object,
  },
  computed: {
    fullImagePath() {
      return `${this.$config.IMAGE_URL}${this.movieDetails?.poster_path}`.toString()
    },
  },
  methods: {
    handleClick() {
      location.href = `/details/${this.movieDetails.id}`
    }
  }
}
</script>

<style scoped>
.container {
  color: white;
  font-weight: bolder;
  letter-spacing: 5px;
  margin: 30px 0px;
  transition: 1s;
  transition-delay: 300ms;
  cursor: pointer;
  box-sizing: border-box;
  padding: 10px;
}

.container .image {
  width: 20vw;
  height: 100%;
  background-color: rgb(27, 27, 27);
  display: flex;
  align-items: center;
  justify-content: center;
  width: 20vw;
  text-align: center;
  border-radius: 10px;
  border: 2px solid white;
}

.container:hover {
  transform: translateY(-30px);
}

@media (max-width: 645px) {

  .container .image {
    width: 25vw;
  }

} 

@media (max-width: 450px) {

  .container .image {
    width: 35vw;
  }
}

@media (max-width: 295px) {

  .container .image {
    width: 70vw;
  }

} 

</style>
