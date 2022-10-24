<template>
  <div class="pokedex">
    <div class="pokedex-left">
      <div class="pokedex-screen-container">
        <pokedex-screen v-bind:pokemon="pokemon[0]" v-bind:loading="loading" />
        <pokedex-screen v-bind:pokemon="pokemon[1]" v-bind:loading="loading" />
      </div>
    </div>
  </div>
</template>
<script>
import PokedexScreen from "./PokedexScreen.vue";

export default {
  name: "PokedexMain",
  components: {
    PokedexScreen,
  },
  data() {
    return {
      loading: true,
      pokemon: [null, null],
      pokemonId1: "pikachu",
      pokemonId2: "ledyba",
    };
  },
  created() {
    this.loading = true;
    this.getPokemon(this.pokemonId1, 0);
    this.getPokemon(this.pokemonId2, 1);
  },
  methods: {
    getPokemon(pokemonId, i) {
      fetch(`https://pokeapi.co/api/v2/pokemon/${pokemonId}`)
        .then((res) => res.json())
        .then((data) => {
          this.pokemon[i] = data;
          this.loading = false;
        })
        .catch((err) => {
          this.loading = false;
          console.log(err);
        });
    },
  },
};
</script>
<style>
.pokedex {
  height: 31rem;
  width: 23rem;
}
</style>
