<script>
export default {
    props: {
        pokemonData: {
            type: null,  // Assicurati che sia un oggetto
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
            <div class="info">
                <h2>{{ pokemonData.name }}</h2>
                <p>Type: {{ pokemonData.types[0].type.name }}</p>
            </div>
        </div>
        <div v-else>
            <p>Nessun Pokémon selezionato.</p>
        </div>

    </div>

    <div v-if="pokemonData" class="info-pokemon">
        <span>Name:</span> {{ pokemonData.name }}
        <div v-for="curType in pokemonData.types">
            <span>Type:</span> {{ curType.type.name }}
            <div> <span>Height:</span> {{ pokemonData.height }}" </div>
            <div> <span> Weight:</span> {{ pokemonData.weight }} Ibs.</div>
        </div>
    </div>
</template>

<style scoped>
.screen-sprite {
    margin-top: 20px;
    text-align: center;
    background-color: white;
    color: black;
    width: 60%;
    border: 40px solid #ced1d4;
    outline: 3px solid black;
    outline-offset: 0;
    position: relative;
}

.info-pokemon {
    margin-top: 20px;
    text-align: center;
    background-color: rgb(28, 158, 41);
    color: black;
    width: 60%;
    outline: 3px solid black;
    outline-offset: 0;
    position: relative;
    padding: 20px 0;
}


img {
    width: 150px;
    height: 150px;

}
</style>