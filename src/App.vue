<script>
import axios from 'axios';
const endpoint = 'https://41tyokboji.execute-api.eu-central-1.amazonaws.com/dev/api/v1/pokemons';
import { store } from './data/store';
import AppMain from './components/AppMain.vue';
import AppLoader from './components/AppLoader.vue';

export default {
  components: { AppMain, AppLoader },

  computed: {
    isLoading() {
      return store.isLoading;
    }
  },

  methods: {
    fetchPokemons() {
      store.isLoading = true;
      if (store.isFilterDefault) {
        axios.get(endpoint).then(res => {
          store.pokemons = res.data.docs;
          store.isLoading = false;
        })
      }
      else {
        let pokemonsType1 = [];
        let pokemonsType2 = [];
        const finalPokemons = [];
        axios.get(`${endpoint}?eq[type1]=${store.filterType}`).then(res => {
          pokemonsType1 = res.data.docs;
          axios.get(`${endpoint}?eq[type2]=${store.filterType}`).then(res => {
            pokemonsType2 = res.data.docs;
            pokemonsType1.forEach(pokemonType1 => {
              let lowestPokemon = pokemonType1;
              pokemonsType2.forEach(pokemonType2 => {
                if (pokemonType2.number < lowestPokemon.number && !finalPokemons.includes(pokemonType2)) lowestPokemon = pokemonType2;
              })
              finalPokemons.push(lowestPokemon);
            });
            if (finalPokemons.length < 10) {
              pokemonsType2.forEach(pokemon => {
                if (!finalPokemons.includes(pokemon)) finalPokemons.push(pokemon)
              })
            }
            store.pokemons = finalPokemons;
            store.isLoading = false;
          })
        })
      }
    },
  },

  created() {
    this.fetchPokemons();
  }
}

</script>

<template>
  <AppLoader v-if="isLoading" />
  <AppMain @filter-changed="fetchPokemons" />
</template>

<style lang="scss">
@use './assets/scss/style.scss';
</style>