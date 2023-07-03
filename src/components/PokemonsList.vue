<script>
import PokemonCard from './PokemonCard.vue';
import { store } from '../data/store';

export default {
    components: { PokemonCard },
    data() {
        return { store };
    }
}
</script>

<template>
    <div class="row">
        <div class="col" v-for="pokemon in store.pokemons" :key="pokemon._id">
            <PokemonCard :image="pokemon.imageUrl" :number="pokemon.number" :name="pokemon.name" :type="pokemon.type1" />
        </div>
    </div>
</template>

<style scoped>
.row {
    display: flex;
    flex-wrap: wrap;
}

.col {
    flex-basis: 20%;
    padding: 10px;
}
</style>