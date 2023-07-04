<script>
import axios from 'axios';
const endpoint = 'https://41tyokboji.execute-api.eu-central-1.amazonaws.com/dev/api/v1/pokemons';
import { store } from './store';
import PokemonCard from './components/PokemonCard.vue';
import Select from './components/Select.vue';

export default {
  components: { PokemonCard, Select },
  created() {
    axios.get(endpoint).then(res => {
      store.pokemons = res.data.docs;
    })
  },
  data() {
    return {
      store,
    }

  },
  methods: {
    selectType() {
      const filterEndpoint = `${endpoint}?eq[type1]=${this.typeSelected}`;
    }
  }
}
</script>



<template>
  <div class="container">
    <h1 class="text-center my-4">Pokemon</h1>
    <Select />
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
