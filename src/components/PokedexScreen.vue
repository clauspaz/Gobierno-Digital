<template>
  <div class="pokedex-screen">
    <img
      v-if="loading"
      src="../assets/pokedex-loading.png"
      alt="Estamos buscando tu pokemon"
      class="pokedex-no-screen"
    />
    <div class="pokemon-info" v-else>
      <h2 class="pokemon-name">{{ pokemon.name }}</h2>
      <img
        class="pokemon-img"
        v-bind:src="pokemon.sprites.front_default"
        v-bind:alt="pokemon.name"
      />
      <router-link :to="{ name: 'about', params: { pokemon: pokemon.name } }"
        >Detalles</router-link
      >
    </div>
  </div>
</template>
<script>
export default {
  name: "PokedexScreen",
  props: {
    // PropTypes on Vue
    pokemon: {
      type: Object,
      default: () => {},
    },
    loading: {
      type: Boolean,
      default: () => true,
    },
  },
};
</script>
