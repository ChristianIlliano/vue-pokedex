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
    <!-- SearchBar -->
    <label for="">
        <input type="text" v-model="store.searchQuery">
    </label>
    <button class="btn-search" @click="$emit('pokeSearch')">Cerca</button>

</template>

<style></style>