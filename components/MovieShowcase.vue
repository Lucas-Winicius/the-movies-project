<template>
  <div class="posterContainer" @click="movieDetails">
    <div :class="[ popular ? 'popular' : 'none' ]">Popular <i class="fa-solid fa-fire"></i></div>
    <img :src="fullImagePath" :alt="title" :title="title" class="moviePoster" />
    <div :class="[ adult ? 'ageageMajority' : 'none' ]">18</div>
  </div>
</template>

<script>
export default {
  name: 'MovieShowcase',
  props: {
    adult: Boolean,
    title: String,
    original_language: String,
    poster_path: String,
    id_code: Number,
    popular: {type: Boolean, default: false},
  },
  computed: {
    fullImagePath() {
      return `${this.$config.IMAGE_URL}${this.poster_path}`.toString()
    },
  },
  methods: {
    movieDetails(e) {
      const currentURL = location.href;
      location.href = `${currentURL}details/${this.id_code}`
    }
  }
}
</script>

<style scoped>
* {
  color: white;
}

.posterContainer {
  margin: 10px 20px;
  transition: .5s;
  cursor: pointer;
}

img.moviePoster {
  width: 245px;
  border: 2px solid yellow;
  border-radius: 10px;
  
  pointer-events: none;
}

div.none { display: none; }

div.popular {
  box-sizing: border-box;
  display: flex;
  position: relative;
  top: 27px;
  align-items: center;
  color: black;
  background-color: yellow;
  width: max-content;
  font-weight: bolder;
  padding: 3px 5px;
  /* padding-left: 10px; */
  border-radius: 10px 0px 10px 0px;
}

div.popular > i {
  color:  black;
  margin-left: 3px;
}

.ageMajority {
  float: right;
  background-color: black;
  height: 20px;
  width: 20px;
  text-align: center;
  position: relative;
  top: -38px;
  right: 15px;
  border-radius: 5px;
}

.posterContainer:hover {
  transform: translateY(-20px);
}

</style>