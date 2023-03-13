<template>
  <div>
    <HeaderComponent />
    <!-- <h1 style="color: white; margin: auto; display: block; width: 100vw;">Home</h1> -->
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

* {
  padding: 0;
  margin: 0;
  font-family: 'Dosis', sans-serif;
}

body {
  background-color: black;
}
</style>