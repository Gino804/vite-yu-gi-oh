<script>
import PokemonsList from '../components/PokemonsList.vue';
import DropdownComponent from '../components/DropdownComponent.vue';
import { store } from '../data/store';

export default {
    data() {
        return { store }
    },

    methods: {
        setFilterType(selectedOption) {
            store.filterType = selectedOption;
            if (selectedOption !== 'default') store.isFilterDefault = false;
            else store.isFilterDefault = true;
            this.$emit('filter-changed');
        }
    },

    components: { PokemonsList, DropdownComponent },

    emits: ['filter-changed']
}
</script>

<template>
    <div class="container">
        <div class="frame">
            <div class="filters">
                <DropdownComponent :defaultValue="'No filter'" :label="'Filter by type:'" :options="store.types"
                    @changed="setFilterType" />
            </div>
            <div class="screen">
                <PokemonsList />
            </div>
        </div>
    </div>
</template>

<style scoped>
.frame {
    background-color: #DEDEDE;
    padding: 50px 20px;
    padding-top: 0;
    margin-top: 150px;
    border-radius: 30px;
}

.filters {
    padding: 20px 0;
}

.screen {
    background-color: #666A6F;
    padding: 20px 10px;
}
</style>