<script setup>

const pokemon = defineProps(['name', 'id', 'url']);

</script>

<template>
    <div class="col-md-3 col-sm-6">
        <div class="card mb-4 p-2" data-bs-toggle="modal" data-bs-target="#exampleModal">
            <p class="text-center">{{ pokemon.id }}</p>
            <h5 class="card-title text-center">{{ pokemon.name.toUpperCase() }}</h5>
            <img :src="`https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/official-artwork/${pokemon.id}.png`" style="height: 200px; width:fit-content; margin: auto;" class="p-4" :alt="pokemon.name">
        </div>
    </div>

</template>

<style scoped>

</style>