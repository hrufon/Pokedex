<template>
  <div id="app">
    <Pokedex/>
  </div>
</template>

<script>

import Pokedex from "./components/Pokedex";

export default {
  components: {
      Pokedex,
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
