<template>
  <div class="pokemon">
    <article v-for="item in items .slice (0, itemToShow )">
      <img v-bind:src="imageUrl + item.id + '.png'" width="96" height="96"/>
      <h2>{{item.name}}</h2>
    </article>
    <article2>
    <button @click="itemToShow += 3">Load More</button>
    </article2>
  </div>
</template>

<script>
    import list from '/teamvoy/pokedex/list.json'

    export default {
        name: 'pokemon',
        data() {
            return {
                imageUrl: 'https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/shiny/',
                items: list,
                pokemonImage: '',
                itemToShow: 12
            }
        }
    }

</script>

<style scoped lang="scss">

  .pokemon{
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    width: 120vh;
  }

  button{
    width: 110vh;
    height: 10vh;
    color: #ffffff;
    font-size: large;
    font-weight:bolder;
    background-color: #196cea;
    border: none;
    cursor: pointer;
    margin-top: 30%;
    border-radius:10px;
}

  article {
    width: 30vh;
    height: 35vh;
    margin: 10%;
    position: relative;
    top:25%;
    background-color: #ffffff;
    text-align: center;
    border-radius: 5px;
    cursor: pointer;
    background-color: #dcaf8e;
    border: 3px solid #196cea;
  }

  article2 {
    width: 30vh;
    margin: 10%;
    position: relative;
  }

</style>
