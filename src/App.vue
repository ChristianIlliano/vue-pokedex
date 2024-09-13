<script>
import axios from "axios";
import { store } from './store';
import SearchBar from './components/SearchBar.vue';
export default {
  data() {
    return {
    store,
    }
  },
  components: {
    SearchBar,
  },

  created() {

  },

  methods: {
    getPokemon() {
      const searchQuery = this.store.searchQuery;
      axios.get(`https://pokeapi.co/api/v2/pokemon/${searchQuery}`, {
        params: {
          searchQuery: this.store.searchQuery,
          
        }
    }).then((resp) => {
      console.log(resp);
      
    })
    } 
  }
};
</script>

<template>
  <div class="pokedex">
    <SearchBar @poke-search="getPokemon"/>

  </div>
</template>

<style scoped></style>
