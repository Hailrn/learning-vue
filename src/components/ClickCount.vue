<template>
    <p>Tombol sudah diclick sebanyak {{ clicks }} kali</p>
    <button @click="clickCount">Click Aku!</button>
</template>

<script>
    export default {
        name: 'ClickCount',
        data() {
            return {
                clicks : 0
            }
        },
        methods : {
            clickCount() {
                this.clicks += 1
            }
        }
    }
</script>