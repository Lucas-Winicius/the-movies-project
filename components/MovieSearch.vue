<template>
    <h1>fILME</h1>
</template>

<script>
export default {
    name: 'MovieSearch',
    props: {
        movieDetails: Object
    },
    mounted() {
        console.log(this.movieDetails)
    }
}
</script>