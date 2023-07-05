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
      if (store.isFilterDefault) this.fetchPokemon(endpoint);
      else this.fetchPokemon(`${endpoint}?eq[type1]=${store.filterType}`);
    },

    fetchPokemon(uri) {
      axios.get(uri).then(res => {
        store.pokemons = res.data.docs;
        store.isLoading = false;
      })
    }
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