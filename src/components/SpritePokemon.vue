<script>
export default {
    props: {
        pokemonData: {
            type: Object,  // Assicurati che sia un oggetto
            required: true
        }
    }
}
</script>

<template>
    <div class="screen-sprite">
        <div v-if="pokemonData">
            <!-- Mostra lo sprite e altre info del Pokémon -->
            <img :src="pokemonData.sprites.front_default" alt="Sprite of {{ pokemonData.name }}" />
            <h2>{{ pokemonData.name }}</h2>
            <p>Type: {{ pokemonData.types[0].type.name }}</p>
        </div>
        <div v-else>
            <p>Nessun Pokémon selezionato.</p>
        </div>
    </div>
</template>

<style scoped>
.screen-sprite {
    text-align: center;
}

img {
    width: 150px;
    height: 150px;
}
</style>