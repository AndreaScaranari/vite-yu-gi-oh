<script>
import axios from "axios";
import AppHeader from "@/components/AppHeader.vue";
import AppMain from "@/components/AppMain.vue";
import { apiUri } from "./data";
import { store } from "./data/store";

export default {
    name: "App",
    components: { AppHeader, AppMain },
    methods: {
        fetchPokemon(endpoint = apiUri) {
            store.isLoading = true;
            axios.get(endpoint).then(res => {
                const pokemons = res.data.docs;

                store.pokemons = pokemons.map(pokemon => {
                    const { name, number, type1, imageUrl } = pokemon;
                    return { name, number, mainType: type1, imageUrl };
                });
            }).catch(err => { console.errorer(err) })
                .then(() => { store.isLoading = false })
        },
    },
    created() {
        this.fetchPokemon();
    }
}
</script>

<template>
    <div class="bg">
        <AppHeader />
        <AppMain />
    </div>
</template>

<style lang="scss">
@use "./scss/style.scss";

.bg {
    height: 100vh;
    background-image: url("./assets/imgs/pokemon_bg.jpg");
    background-size: cover;
}
</style>
