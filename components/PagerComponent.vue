<template>
    <div class="pager">
        <i class="fa-solid fa-arrow-left left arrow" @click="navigation"></i>
        <span class="page">{{ localPage }}</span>
        <i class="fa-solid fa-arrow-right right arrow" @click="navigation"></i>
    </div>
</template>

<script>
export default {
    name: 'PagerComponent',
    props: {
        pagesQuanty: Number,
    },
    data() {
        return {
            localPage: Number(this.$route.params.page),
            search: this.$route.params.search,
        }
    },
    methods: {
        navigation(e) {
            const el = e.target
            const back = el.classList.contains('left')
            if(back && this.localPage === 1) return; 
            
            if(!back) location.href = `/search/${this.localPage += 1}/${this.search}`
            if(back) location.href = `/search/${this.localPage -= 1}/${this.search}`
            if(this.localPage >= this.pagesQuanty) location.href = `/search/${this.pagesQuanty}/${this.search}`
        }
    }
}
</script>

<style scoped>

.pager {
    text-align: center;
    color: white;
    margin: 15px 0px;
}

.arrow {
    cursor: pointer;
}

.page {
    margin: 0px 15px;
}

.left:hover {
    animation: left 1s backwards infinite;
}

.right:hover {
    animation: right 1s backwards infinite;
}

@keyframes left {
    0% { transform: translateX(0px); }
    50% { transform: translateX(-5px); }
    100% { transform: translateX(0px); }
}

@keyframes right {
    0% { transform: translateX(0px); }
    50% { transform: translateX(5px); }
    100% { transform: translateX(0px); }
}

</style>