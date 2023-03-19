<template>
  <header>
    <NuxtLink id="headerTitle" to="/">
      <h1>Movies</h1>
    </NuxtLink>

    <span id="search" @keypress.enter="search">
      <input type="text" v-model="inputValue" />
      <i
        id="searchButton"
        class="fa-solid fa-magnifying-glass"
        @click="search"
      ></i>
    </span>
  </header>
</template>

<script>
export default {
  name: 'HeaderComponent',
  data() {
    return {
      inputValue: this.$route.params.search || '',
    }
  },
  methods: {
    search() {
      location.href = `/search/1/${this.inputValue}`
    },
  },
}
</script>

<style>
header {
  display: flex;
  justify-content: space-around;
  align-items: center;
  background-color: rgb(25, 25, 25);
  color: white;
  padding: 10px;
  border-bottom: 2px solid rgb(255, 0, 51);
}

#headerTitle {
  letter-spacing: 5px;
  user-select: none;
  cursor: pointer;
  color: whitesmoke;
  text-decoration: none;
}

#search {
  display: flex;
  align-items: center;
  background-color: rgb(35, 35, 35);
  padding: 9px;
  border-radius: 10px;
  border: 1.5px solid transparent;
}

#search input {
  background-color: transparent;
  border: none;
  outline: none;
  color: whitesmoke;
  width: 24vw;
  transition: 5s;
}

#search:focus-within {
  border: 2px solid rgb(255, 0, 51);
}

#searchButton {
  cursor: pointer;
  margin-left: 10px;
}
</style>
