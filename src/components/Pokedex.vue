<template>
  <div class="container">
    <h1>Pokedex</h1>
    <PokedexList
      :imageUrl="imageUrl"
      :apiUrl="apiUrl"
      @setPokemonUrl="setPokemonUrl" />
    <PokedexDetail
      v-if="showDetail"
      :pokemonUrl="pokemonUrl"
      :imageUrl="imageUrl"
      @closeDetail="closeDetail" />
  </div>
</template>

<script>
    import PokedexList from './PokedexList.vue';
    import PokedexDetail from './PokedexDetail.vue';
    export default {
        data: () => {
            return {
                imageUrl: 'https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/shiny/',
                apiUrl: 'https://pokeapi.co/api/v2/pokemon?offset=0&limit=150',
                pokemonUrl: '',
                showDetail: false
            }
        },
        components: {
            PokedexList,
            PokedexDetail
        },
        methods: {
            setPokemonUrl(url) {
                this.pokemonUrl = url;
                this.showDetail = true;
            },
            closeDetail() {
                this.pokemonUrl = '';
                this.showDetail = false;
            }
        }
    }
</script>

<style lang="scss" scoped>
  @import url('https://fonts.googleapis.com/css?family=Acme');
  .container {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    padding: 10px;
    width: calc(100% - 20px);
    min-height: calc(100vh - 20px);
    background-image: url('https://wallpaperaccess.com/full/20997.jpg');
    font-size: 1rem;
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
