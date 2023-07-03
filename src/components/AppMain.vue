<script>
import PokemonsList from '../components/PokemonsList.vue';

export default {
    components: { PokemonsList }
}
</script>

<template>
    <div class="container">
        <div class="frame">
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
    margin-top: 150px;
    border-radius: 30px;
}

.screen {
    background-color: #666A6F;
    padding: 20px 10px;
}
</style>