<template>
    <h1 :class="{highlight : likes > 10}" :style="{backgroundColor : bgColor}">Judul ini akan diberi Highlight</h1>
    <button @click="beriLike">Like!</button>
    <p>Jumlah Likes Saat Ini : {{ likes }}</p>
    <span>Atur disini jika kamu tidak suka warnanya: </span>
    <input v-model="bgColor" type="color">
</template>

<script>
    export default {
        name: 'HighLight',
        data () {
            return {
                likes : 0,
                bgColor : "#EE82EE"
            }
        },
        methods: {
            beriLike() {
                this.likes += 1
            }
        }
    }
</script>

<style scoped>
    .highlight{
        text-decoration: underline;
    }
</style>