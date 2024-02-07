<script>
import { store } from "../data/store";
import AppPokelist from "./AppPokelist.vue";

export default {
    name: "AppMain",
    components: { AppPokelist },
    data: () => store,
}
</script>

<template>
    <main>
        <div class="container">
            <div class="pokedex">
                <div class="pokedex-screen ">
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
    }

    .pokedex-screen {
        overflow-y: auto;
    }

    .pokedex-screen.pokelist {
        display: flex;
        flex-wrap: wrap;
        width: 50%;
        background-color: rgb(195, 195, 195);
        border-radius: 10px;
    }
}
</style>
