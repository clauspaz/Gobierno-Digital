<template>
  <div class="pokedex">
    <div class="pokedex-left">
      <div class="pokedex-screen-container">
        <pokedex-details v-bind:pokemon="pokemon" v-bind:loading="loading" />
      </div>
    </div>
  </div>
</template>
<script>
import PokedexDetails from "./PokedexDetails.vue";

export default {
  name: "PokedexAbout",
  components: {
    PokedexDetails,
  },
  data() {
    return {
      loading: true,
      pokemon: null,
      pokemonId: "ledyba",
    };
  },
  created() {
    this.loading = true;
    this.getPokemon(this.$route.params.pokemon);
  },
  methods: {
    getPokemon(pokemonId) {
      fetch(`https://pokeapi.co/api/v2/pokemon/${pokemonId}`)
        .then((res) => res.json())
        .then((data) => {
          this.pokemon = data;
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
