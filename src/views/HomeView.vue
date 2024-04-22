<script setup>
  import {onMounted, reactive, ref, computed} from 'vue';
  import PokemonsList from '../components/PokemonsList.vue';
  import PokemonCard from '../components/PokemonCard.vue';

  let pokemons = reactive(ref());
  let searchField = ref("");
  let pokemonSelected = reactive(ref());
  let loading = ref(false)

  onMounted(() => {
    fetch('https://pokeapi.co/api/v2/pokemon?limit=100000&offset=0')
    .then(response => response.json())
    .then(response => pokemons.value = response.results);
  });

  const pokemonsFiltered = computed(()=>{
    if(pokemons.value && searchField.value){
      return pokemons.value.filter(pokemon=>
        pokemon.name.toLowerCase().includes(searchField.value.toLowerCase())
      )
    }
    return pokemons.value;
  });
  
  function get_id(pokemon) {
      return pokemon.url.split("/")[6];
  }

  const selectPokemon = async (pokemon) => {
  loading.value = true;
  await fetch(pokemon.url)
  .then(res => res.json())
  .then(res => pokemonSelected.value = res)
  .catch(err => alert(err))
  .finally(()=> loading.value = false)

  console.log(pokemonSelected.value)
  
}

</script>

<template>
  <main>
    <div class="container">
      <div class="input-group mt-4">
        <input v-model="searchField" type="text" class="form-control" placeholder="Pesquise por id, nome, tipo ou espécie.">
      </div>
    </div>

      <div class="container mt-4">
        <div class="col">
          <div class="card-body row">
            <PokemonsList v-for="pokemon in pokemonsFiltered" :key="pokemon" :name="pokemon.name" :id="get_id(pokemon)" :url="pokemon.url"  @click="selectPokemon(pokemon)"/>
          </div>
        </div>
      </div>

      <!-- Modal -->
    <div class="modal fade" id="exampleModal" tabindex="-1" aria-labelledby="exampleModalLabel" aria-hidden="true">
    <div class="modal-dialog" style="overflow-y: initial">
        <div class="modal-content">
        <div class="modal-header">
            <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
        </div>
        <div class="modal-body" style="  height: 80vh; overflow-y: auto;">
            <PokemonCard
                :name="pokemonSelected?.name"
                :id="pokemonSelected?.id"
                :sprites="pokemonSelected?.sprites"
                :types="pokemonSelected?.types"
                :moves="pokemonSelected?.moves"
                :game_indices="pokemonSelected?.game_indices"
              />
        </div>
        </div>
    </div>
    </div>

  </main>
</template>
