<script>
import { store } from '../store';
export default {

    emits: ["pokeSearch"],

    data() {
        return {
            store,
        }
    },
}
</script>

<template>
    <div class="search-bar">
        <!-- SearchBar -->
        <label for="">
            <input type="text" v-model="store.searchQuery">
        </label>
        <button class="btn-search" @click="$emit('pokeSearch')">Cerca</button>
    </div>

</template>

<style>
.search-bar {
    margin-top: 50px;
}
</style>