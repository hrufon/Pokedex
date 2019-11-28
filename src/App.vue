<template>
  <div id="app">
    <h1>Pokedex</h1>
    <PokedexList/>
  </div>
</template>

<script>
import PokedexList from './components/PokedexList.vue'

export default {
  components: {
    PokedexList
  }
}

</script>

<style lang="scss">

  body,html{
    background-image: url('https://wallpaperaccess.com/full/20997.jpg');
    overflow-x:hidden;
    margin: 0;
    padding: 0;
  }

  #app {
  display: grid;
  width: 225vh;
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
}

  h1{
    border: 1px solid #000000;
    width: 60vh;
    height: 50px;
    margin: 0 auto;
    line-height: 50px;
    position: relative;
    top: 50px;
    background-color: #dcaf8e;
    border: 3px solid #196cea;
  }

</style>
