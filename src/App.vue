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
            axios.get(endpoint).then(res => {
                const pokemons = res.data.docs;

                store.pokemons = pokemons.map(pokemon => {
                    const { name, number, type1, imageUrl } = pokemon;
                    return { name, number, mainType: type1, imageUrl };
                });
            })
        },
        fetchTypes() {
            axios.get(apiUri + "/types1").then(res => {
                store.types = res.data.map((type, i) => {
                    return {
                        id: i + 1,
                        label: type,
                        value: type
                    }
                })
            })

        }
    },
    created() {
        this.fetchPokemon();
        this.fetchTypes();
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
