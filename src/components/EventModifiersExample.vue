<template>
    <div>
        <button @click="handleClick">Tanpa Modifier</button>
        <button @click.stop="handleClick">Dengan .stop</button>
        <form @submit.prevent="handleSubmit">
            <input type="text" placeholder="Tulis sesuatu" v-model="inputText" />
            <button type="submit">Kirim</button>
        </form>
    </div>

    <div @click="parentClick" style="padding: 20px; border: 2px solid blue;">
        <p>Ini Parent Div</p>
        <div @click="childClick" style="padding: 20px; border: 2px solid red;">
            <p>Ini Child Div (Tanpa .stop)</p>
        </div>
        <div @click.stop="childClick" style="padding: 20px; border: 2px solid green;">
            <p>Ini Child Div (Dengan .stop)</p>
        </div>
    </div>
</template>
<script>
export default {
    data() {
        return {
            inputText: ''
        };
    },
    methods: {
        handleClick() {
            alert('Button diklik!');
        },
        handleSubmit() {
            alert(`Kamu ngetik: ${this.inputText}`);
        },
        parentClick() {
            alert("Parent Div diklik!");
        },
        childClick() {
            alert("Child Div diklik!");
        }
    }
};
</script>