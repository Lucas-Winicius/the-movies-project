<template>
  <div class="posterContainer">
    <div :class="[ popular ? 'popular' : 'none' ]">Popular <i class="fa-solid fa-fire"></i></div>
    <img :src="fullImagePath" :alt="title" :title="title" />
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
  }
}
</script>

<style scoped>
* {
  color: white;
}

.posterContainer {
  margin: 10px 10px;
}

img {
  width: 23vw;
  max-width: 245px;
  border: 2px solid yellow;
  border-radius: 10px;
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

</style>