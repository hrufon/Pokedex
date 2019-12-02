<template>
  <div class="detail">
    <div class="detail-view" v-if="show">
      <div v-if="pokemon" class="image">
        <img :src="imageUrl + pokemon.id + '.png'" alt="">
      </div>
      <div v-if="pokemon" class="data">
        <h2>{{ pokemon.name }}</h2>
        <div class="property">
          <div class="left">Base Experience</div>
          <div class="right">{{ pokemon.base_experience }} XP</div>
        </div>
        <div class="property">
          <div class="left">Height</div>
          <div class="right">{{ pokemon.height / 10 }} m</div>
        </div>
        <div class="property">
          <div class="left">Weight</div>
          <div class="right">{{ pokemon.weight / 10 }} kg</div>
        </div>
        <h3>Pokemon Types</h3>
        <div class="types">
          <div class="type"
               v-for="(value, index) in pokemon.types"
               :key="'value'+index">
            {{ value.type.name }}
          </div>
        </div>
      </div>
      <h2 v-else>The pokemon was not found</h2>
      <button class="close" @click="closeDetail">close</button>
    </div>
  </div>
</template>

<script>
    export default {
        props: [
            'pokemonUrl',
            'imageUrl'
        ],
        data: () => {
            return {
                show: false,
                pokemon: {}
            }
        },
        methods: {
            fetchData() {
                let req = new Request(this.pokemonUrl);
                fetch(req)
                    .then((resp) => {
                        if(resp.status === 200)
                            return resp.json();
                    })
                    .then((data) => {
                        this.pokemon = data;
                        this.show = true;
                    })
                    .catch((error) => {
                        console.log(error);
                    })
            },
            closeDetail() {
                this.$emit('closeDetail');
            }
        },
        created() {
            this.fetchData();
        }
    }
</script>

<style lang="scss" scoped>
  .detail {
    display: flex;
    justify-content: center;
    align-items: flex-start;
    position: fixed;
    top: 0;
    left: 0;
    padding: 200px 350px 10px;
    width:100%;
    .detail-view {
      display: flex;
      justify-content: center;
      align-items: center;
      flex-direction: column;
      position: relative;
      width: 100%;
      max-width: 510px;
      padding: 50px 0 0;
      background-color: #dcaf8e;
      height:460px;

      .image {
        display: flex;
        justify-content: center;
        align-items: center;
        position: absolute;
        top: 20px;
        width: 400px;
        height: 130px;
        overflow: hidden;
        border: 3px solid #196cea;
      }
      .data {
        display: flex;
        justify-content: flex-start;
        align-items: center;
        flex-direction: column;
        width: 100%;
        margin-top: 60px;
        .property {
          width: 90%;
          max-width: 400px;
          margin-bottom: 10px;
          .left { float: left; }
          .right { float: right; }
        }
        .types{
          display: flex;
          justify-content: flex-start;
          flex-wrap: wrap;
          width: 90%;
          max-width: 400px;
          .type {
            margin: 0 10px 10px 0;
            padding: 5px 10px;
            border-radius: 20px;
            color: #fff;
            font-size: 1rem;
            letter-spacing: 2px;
            text-transform: capitalize;
            word-break: keep-all;
          }
          .type { background-color: #dda902; }
        }
      }
      .close {
        outline: none;
        border: none;
        border-radius: 5px;
        background-color: #196cea;
        color: #efefef;
        padding: 10px 20px;
        margin-top: 30px;
        font-size: 1.2rem;
        cursor: pointer;
      }
    }
  }
</style>
