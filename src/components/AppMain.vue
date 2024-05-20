<script>
import { store } from "../data/store";
import AppPokelist from "./AppPokelist.vue";
import AppPokemenu from "./AppPokemenu.vue";

export default {
    name: "AppMain",
    components: { AppPokelist, AppPokemenu },
    data: () => store,
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

        },
        filterPokemon(type) {
            const endpoint = `${apiUri}?eq[type1]=${type}`;
            this.fetchPokemon(endpoint)
        }
    }
}
</script>

<template>
    <main>
        <div class="container">
            <div class="pokedex">
                <div class="pokedex-screen ">
                    <AppPokemenu @type-change="filterPokemon" />
                </div>
                <div class="pokedex-screen pokelist">
                    <AppPokelist v-for="pokemon in pokemons" :key="pokemon._id" v-bind="pokemon" />
                </div>
            </div>
        </div>
    </main>
</template>

<style lang="scss" scoped>
main {
    .container {
        width: 60%;
        margin: 0 auto;
    }

    .pokedex {
        display: flex;
        height: 600px;
        background-color: red;
        border-radius: 10px;
        padding: 3rem;
        margin-top: 50px;
        gap: 1rem;
    }

    .pokedex-screen {
        overflow-y: auto;
        width: 50%;
        border-radius: 10px;
        background-color: rgb(195, 195, 195);
    }

    .pokedex-screen.pokelist {
        display: flex;
        flex-wrap: wrap;
    }
}
</style>
