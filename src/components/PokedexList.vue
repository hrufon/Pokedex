<template>
  <div class="list">
    <article v-for="(pokemon, index) in pokemons .slice (0, pokemonToShow)"
             :key="'poke'+index"
             @click="setPokemonUrl(pokemon.url)">
      <img :src="imageUrl + pokemon.id + '.png'" width="96" height="96" alt="">
      <h3>{{ pokemon.name }}</h3>
    </article>
    <article2>
    <button @click="pokemonToShow += 3">Load More</button>
    </article2>
  </div>
</template>

<script>
    export default {
        props: [
            'imageUrl',
            'apiUrl'
        ],
        data: () => {
            return {
                pokemons: [],
                pokemonToShow: 12,
                nextUrl: '',
                currentUrl: ''
            }
        },
        methods: {
            fetchData() {
                let req = new Request(this.currentUrl);
                fetch(req)
                    .then((resp) => {
                        if(resp.status === 200)
                            return resp.json();
                    })
                    .then((data) => {
                        this.nextUrl = data.next;
                        data.results.forEach(pokemon => {
                            pokemon.id = pokemon.url.split('/')
                                .filter(function(part) { return !!part }).pop();
                            this.pokemons.push(pokemon);
                        });
                    })
                    .catch((error) => {
                        console.log(error);
                    })
            },
            next() {
                this.currentUrl = this.nextUrl;
                this.fetchData();
            },
            setPokemonUrl(url) {
                this.$emit('setPokemonUrl', url);
            }
        },
        created() {
            this.currentUrl = this.apiUrl;
            this.fetchData();
        },
    }
</script>

<style lang="scss" scoped>
  .list {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    grid-gap: 10px;
    width: 100%;
    max-width: 510px;
    margin: 15vh 130vh 0 0;
    article {
      width: 30vh;
      height: 35vh;
      margin: 5%;
      background-color: #ffffff;
      text-align: center;
      border-radius: 5px;
      cursor: pointer;
      background-color: #dcaf8e;
      border: 3px solid #196cea;
    }
    article2 {
      width: 30vh;
      margin: 5%;
      position: relative;
    }
  }
  button{
    width: 100vh;
    height: 10vh;
    color: #ffffff;
    font-size: large;
    font-weight:bolder;
    background-color: #196cea;
    border: none;
    cursor: pointer;
    border-radius:10px;
  }

</style>
