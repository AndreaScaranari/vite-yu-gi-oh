<script>
export default {
    name: "AppHeader",
    data: () => ({
        imgName: "pokemon_header.jpg"
    }),
    methods: {
        createImagePath(imgName) {
            const url = new URL(`../assets/imgs/${imgName}`, import.meta.url);
            return url.href
        }
    }
}
</script>

<template>
    <header>
        <figure>
            <img :src="createImagePath(imgName)" :alt="imgName" :title="imgName">
        </figure>
    </header>
</template>

<style lang="scss" scoped>
header {

    figure {
        height: 200px;
        background-color: rgba($color: #ffffff, $alpha: 0.8);

        img {
            margin: 0 auto;
            max-height: 200px;
        }
    }

}
</style>
