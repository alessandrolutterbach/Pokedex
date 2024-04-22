<script setup>
import { onMounted } from 'vue';

const pokemon = defineProps(["name", "id", "types", "sprites", "moves", "game_indices"])

</script>

<template>
        <div class="card-body text-center">
            <p>{{ pokemon.id }}</p>
            <h5 class="card-title">{{ pokemon.name }}</h5>
            <img :src="`https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/official-artwork/${pokemon.id}.png`" style="height: 200px; width:fit-content; margin: auto;" class="p-4" :alt="pokemon.name">
        </div>
        <div>
            <h6 class="text-center">Tipos</h6>
            <ul>
                <li v-for="type in pokemon.types" :key="type.type.name"> {{ type.type.name }} </li>
            </ul>
            <h6 class="text-center">Sprites</h6>
            <div class="row text-center">
                <div class="col-4"><img :src="`https://img.pokemondb.net/sprites/red-blue/normal/${pokemon.name}.png`" style="height: 100px; width:fit-content;"></div>
                <div class="col-4"><img :src="`https://img.pokemondb.net/sprites/silver/normal/${pokemon.name}.png`" style="height: 100px; width:fit-content;"></div>
                <div class="col-4"><img :src="`https://img.pokemondb.net/sprites/ruby-sapphire/normal/${pokemon.name}.png`" style="height: 100px; width:fit-content;"></div>
            </div>
            <div class="row text-center mt-5">
                <div class="col-4"><img :src="`https://img.pokemondb.net/sprites/diamond-pearl/normal/${pokemon.name}.png`" style="height: 100px; width:fit-content;"></div>
                <div class="col-4"><img :src="`https://img.pokemondb.net/sprites/black-white/normal/${pokemon.name}.png`" style="height: 100px; width:fit-content;"></div>
                <div class="col-4"><img :src="`https://img.pokemondb.net/sprites/x-y/normal/${pokemon.name}.png`" style="height: 100px; width:fit-content;"></div>
            </div>
            <div class="row text-center">
                <div class="col-4"><img :src="`https://img.pokemondb.net/sprites/lets-go-pikachu-eevee/normal/${pokemon.name}.png`" style="height: 120px; width:fit-content;"></div>
                <div class="col-4"><img :src="`https://img.pokemondb.net/sprites/sword-shield/normal/${pokemon.name}.png`" style="height: 120px; width:fit-content;"></div>
                <div class="col-4"><img :src="`https://img.pokemondb.net/sprites/scarlet-violet/normal/${pokemon.name}.png`" style="height: 120px; width:fit-content;"></div>
            </div>
            </div>

            <h6 class="text-center">Ataques</h6>
            <br>
            <div class="row">
                <div class="col-6 text-center" v-for="move in pokemon.moves" :key="move.move.name"> {{ move.move.name }} </div>
            </div>
            <br>
            <h6 class="text-center">Jogos em que está presente:</h6>
            <br>
            <div class="row">
                <div class="col-6 text-center"v-for="game in pokemon.game_indices" :key="game.version.name"> {{ game.version.name }} </div>
            </div>
</template>