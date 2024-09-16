<script>
import axios from "axios";
import { store } from './store';
import SearchBar from './components/SearchBar.vue';
import SpritePokemon from "./components/SpritePokemon.vue";

export default {
  data() {
    return {
      store,
      pokemonData: null,  // Inizializza pokemonData come null
      error: null,  // Gestione di eventuali errori
    };
  },
  components: {
    SearchBar,
    SpritePokemon,
  },

  methods: {
    getPokemon() {
      const searchQuery = this.store.searchQuery;
      if (!searchQuery) return;  // Verifica che ci sia una query

      axios.get(`https://pokeapi.co/api/v2/pokemon/${searchQuery}`)
        .then((resp) => {
          this.pokemonData = resp.data;  // Salva i dati del Pokémon
          this.error = null;  // Resetta eventuali errori
        })
        .catch((error) => {
          console.error(error);
          this.error = "Il Pokémon cercato non è stato trovato.";  // Gestione dell'errore
          this.pokemonData = null;  // Resetta i dati se c'è un errore
        });
    }
  }
};
</script>

<template>
  <div class="pokedex">
    <div class="pokedex-left">
      <!-- Barra di ricerca per il Pokémon -->
      <SearchBar @poke-search="getPokemon"/>
      
      <!-- Mostra SpritePokemon passando i dati del Pokémon -->
      <SpritePokemon :pokemonData="pokemonData"/>

      <!-- Visualizza eventuali messaggi di errore -->
      <div v-if="error" class="error-message">{{ error }}</div>
    </div>
    <div class="pokedex-right"></div>
  </div>
</template>

<style scoped>
.pokedex {
  display: flex;
  align-items: center;
  justify-content: center;
}

.pokedex-left {
  width: 400px;
  height: 60vh;
  background-color: red;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.pokedex-right {
  width: 400px;
  height: 60vh;
  background-color: red;
}

</style>
