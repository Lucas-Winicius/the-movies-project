<template>
  <div class="Movie">
    <img :src="fullImagePath" :alt="title" :title="title" />
    <p>{{ adult }}</p>
    <p>{{ title }}</p>
    <p>{{ original_language }}</p>
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

img {
  width: 23vw;
  max-width: 245px;
}

</style>