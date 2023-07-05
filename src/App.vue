<script>
import axios from 'axios';
const endpoint = 'https://41tyokboji.execute-api.eu-central-1.amazonaws.com/dev/api/v1/pokemons';
import { store } from './store';
import PokemonCard from './components/PokemonCard.vue';
import BaseSelect from './components/BaseSelect.vue';

export default {
  components: { PokemonCard, BaseSelect },
  data() {
    return {
      store
    }
  },
  methods: {
    fetchPokemon(endpoint) {
      axios.get(endpoint).then(res => {
        store.pokemons = res.data.docs;
      })
    },
    fetchTypes() {
      axios.get(endpoint + '/types1').then(res => {
        store.types = res.data;
      })
    },
    filterPokemon(type) {
      const filterEndpoint = `${endpoint}?eq[type1]=${type}`;
      this.fetchPokemon(filterEndpoint);
    },
  },
  created() {
    this.fetchPokemon();
    this.fetchTypes();
  },
}
</script>



<template>
  <div class="container">
    <h1 class="text-center my-4">Pokemon</h1>

    <BaseSelect defaultLabel="All Types" :options="store.types" @option-change="filterPokemon" />

    <div class="row g-4 row-cols-5">
      <div class="col" v-for="pokemon in store.pokemons" :key="pokemon.number">
        <PokemonCard :name="pokemon.name" :type="pokemon.type1" :image="pokemon.imageUrl" />
      </div>
    </div>
  </div>
</template>



<style lang="scss">
@use './assets/scss/style.scss';
</style>
