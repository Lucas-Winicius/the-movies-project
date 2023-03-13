<template>
    <footer>
    <p>
        <a :href="instagram" target="_blank" rel="noopener noreferrer"><i class="fa-sharp fa-regular fa-copyright"></i> {{ new Date().getFullYear() }} All Rights Reserved &centerdot; Lucas Winicius</a>
    </p>    
    </footer>
</template>

<script>
export default {
    name: 'FooterComponent',
    data() {
        return {
            instagram: null
        }
    },
    mounted: async function() {
        try {
            const response = await fetch('https://lucas-winicius.github.io/Lucas-Winicius/contacts.json')
            const data = await response.json()
            this.instagram = data
        } catch(e) {
            console.error('Não foi possivel localizar os contatos')
        } finally {
            this.instagram = this.instagram.instagram.url || 'https://i.kym-cdn.com/photos/images/newsfeed/002/486/154/c06.gif'
            console.log(this.instagram)
        }
    }
}
</script>

<style scoped>
footer {
    background-color: rgb(25, 25, 25);
    color: whitesmoke;
    text-align: center;
    padding: 15px;
    border-top: 2px solid rgb(255, 0, 51);
}
a {
    color: whitesmoke;
    text-decoration: none;
}
</style>