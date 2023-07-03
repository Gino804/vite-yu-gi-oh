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

  created() {
    store.isLoading = true;
    axios.get(endpoint).then(res => {
      store.pokemons = res.data.docs;
      store.isLoading = false;
    })
  }
}

</script>

<template>
  <AppLoader v-if="isLoading" />
  <AppMain />
</template>

<style lang="scss">
@use './assets/scss/style.scss';
</style>