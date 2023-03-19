<template>
    <div class="container">
        <img :src="fullImagePath" :alt="movieDetails.original_title" class="image">
        <h1 class="movieTitle">{{ movieDetails.original_title }}</h1>
    </div>
</template>

<script>
export default {
    name: 'MovieSearch',
    props: {
        movieDetails: Object
    },
    computed: {
        fullImagePath() {
            return `${this.$config.IMAGE_URL}${this.movieDetails?.poster_path}`.toString()
        }
    }
}
</script>

<style scoped>
.container {
    max-width: 20vw;
}

.container .image {
    width: 20vw;
}

.container .movieTitle {
    color: whitesmoke;
    font-size: 1em;
    text-align: center;
}

</style>