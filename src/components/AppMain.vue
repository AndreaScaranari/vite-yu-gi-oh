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
                <div class="pokedex-screen">
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
    }

    .pokedex-screen {
        display: flex;
        justify-content: space-between;
        grid-template-columns: repeat(2, 50%);
    }
}
</style>
