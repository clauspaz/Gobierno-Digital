<template>
  <div class="pokedex-screen">
    <div class="pokemon-info">
      <h2 class="pokemon-name">{{ pokemon.name }}</h2>
      <img
        class="pokemon-img"
        v-bind:src="pokemon.sprites.front_default"
        v-bind:alt="pokemon.name"
      />
      <ul class="pokemon-stats">
        <StatPokemon
          v-bind:item="item"
          v-for="item in pokemon.stats"
          v-bind:key="item.stat.name"
        />
      </ul>
    </div>
  </div>
</template>
<script>
import StatPokemon from "./Stat.vue";
export default {
  name: "PokedexDetails",
  components: {
    StatPokemon,
  },
  props: {
    // PropTypes on Vue
    pokemon: {
      type: Object,
      default: () => {},
    },
    error: {
      type: Boolean,
      default: () => false,
    },
    loading: {
      type: Boolean,
      default: () => false,
    },
  },
};
</script>
