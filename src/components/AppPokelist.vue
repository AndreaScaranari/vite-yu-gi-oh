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
    <div className="poke-card">
        <figure>
            <img :src="imageUrl" :alt="name" :title="name">
        </figure>
        <div>{{ number }}</div>
        <div>{{ name }}</div>
        <div>{{ mainType }}</div>
    </div>
</template>

<style lang="scss" scoped></style>
