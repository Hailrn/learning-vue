<template>
    <input v-model="nama" type="text" placeholder="Masukkan Nama Kamu!">
    <button @click="submitNama">Kirim!</button>
    <p>{{ greeting }}</p>
</template>

<script>
    export default {
        name: 'FormulirInput',
        data() {
            return {
                nama : "",
                greeting : ""
            }
        },
        methods : {
            submitNama(){
                this.greeting = this.nama !== "" ? `Halo ${this.nama}, selamat datang!` : ""
            }
        }
    }
</script>