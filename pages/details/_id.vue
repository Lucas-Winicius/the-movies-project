<template>
  <h1>Movie id:{{ movieID }}</h1>
</template>
  
  <script>
export default {
  name: 'DetailsPage',
  data() {
    return {
      movieID: this.$route.params.id
    }
  }
}
</script>