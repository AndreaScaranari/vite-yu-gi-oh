<script>
import SelectMenu from "./SelectMenu.vue"
import { store } from "../data/store";

export default {
    name: "AppPokemenu",
    data: () => ({ store }),
    components: { SelectMenu },
    emit: ["type-change"]
}
</script>

<template>
    <div>
        <SelectMenu default-label="Tutti i Tipi" :options="store.types" @option-change="$emit('type-change', $event)" />
    </div>
</template>

<style lang="scss" scoped>
div {
    text-align: center;
    padding-top: 1rem;
}
</style>