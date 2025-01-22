<template>
    <p>Hello, welcome {{ user }} to my Vue app!</p>
</template>

<script>
export default {
    name: 'GreetingUser',
    props: {
        user: String
    }
}
</script>

<style scoped>
p {
font-size: 20px;
color: green;
}
</style>
