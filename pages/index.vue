<template>
  <div>
    <HeaderComponent />
    <main class="movies">
      <!-- <EmptyMessage v-if="true" /> -->
      <LoadComponent class="temp" />
    </main>
    <FooterComponent />    
  </div>
</template>

<script>

export default {
  name: 'IndexPage',
  head: {
    title: 'Home'
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Dosis:wght@200;300;400;500;600;700;800&display=swap');

.temp {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}

* {
  padding: 0;
  margin: 0;
  font-family: 'Dosis', sans-serif;
  user-select: none;
}

body {
  background-color: black;
}

main.movies {
  height: calc(100vh - 115px);
}

</style>