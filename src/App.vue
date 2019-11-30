<template>
  <div id="app">
    <Pokemon/>
  </div>
</template>

<script>

import Pokemon from "./components/Pokemon";

export default {
  components: {
      Pokemon,
  }
}

</script>

<style lang="scss">

  body,html{
    background-image: url('https://wallpaperaccess.com/full/20997.jpg');
    margin: 0;
    padding: 0;
  }

  #app {
  display: grid;
  width: 200vh;
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
}

</style>
