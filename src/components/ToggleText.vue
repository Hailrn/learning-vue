<template>
    <h1>{{ greeting }}</h1>
    <button @click="toggleText">Click Aku!</button>
</template>

<script>
export default {
    name: 'ToggleText',
    data() {
        return {
            greeting : "Selamat datang di Vue.js"
        }
    },
    methods: {
        toggleText() {
            this.greeting = this.greeting === "" ? "Selamat datang di Vue.js" : ""
        }
    }
}
</script>
