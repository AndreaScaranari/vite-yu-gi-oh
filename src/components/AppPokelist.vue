<script>
export default {
    name: "AppPokelist",
    props: {
        imageUrl: String,
        name: String,
        number: Number,
        mainType: String
    },
    // computed: {
    //     bgColor() {
    //         return colorMap[this.mainType];
    //     }
    // }
}
</script>

<template>
    <div class="col">
        <div class="poke-card">
            <figure>
                <img :src="imageUrl" :alt="name" :title="name">
            </figure>
            <div># {{ number }}</div>
            <div><b>{{ name }}</b></div>
            <div><i>{{ mainType }}</i></div>
        </div>
    </div>
</template>

<style lang="scss" scoped>
.col {
    padding: 0.5rem;
    width: 50%;

}

.poke-card {
    text-align: center;
    background-color: white;
    border-radius: 10px;
    border: 1px solid black;
    padding: 0.5rem;


    img {
        aspect-ratio: 1 / 1;
        object-fit: contain;
    }
}
</style>
