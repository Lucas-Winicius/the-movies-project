<template>
    <div class="Movie">
        <p>{{ adult }}</p>
        <p>{{ title }}</p>
        <p>{{ original_language }}</p>
        <p>{{ poster_path }}</p>
    </div>
</template>

<script>
export default {
    name: 'MovieShowcase',
    props: {
        adult: Boolean,
        title: String,
        original_language: String,
        poster_path: String
    }
}
</script>

<style scoped>
* {
    color: white;
}
</style>